---
title: 視覺效果工具提示
description: Power BI 視覺效果可以顯示工具提示
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 286c5eef2c341ad77c351008b321992597bef292
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425635"
---
# <a name="power-bi-visuals-tooltips"></a>Power BI 視覺效果工具提示

視覺效果現在可以利用 Power BI 的工具提示支援。 Power BI 工具提示會處理下列互動：

顯示工具提示。
隱藏工具提示。
移動工具提示。

工具提示可以顯示含有標題的文字項目、特定色彩的值以及指定座標集的不透明度。 此資料會提供給 API。 而 Power BI 主機呈現它的方式，與其呈現原生視覺效果工具提示的方式相同。

例如，範例 BarChart 中的工具提示。

![範例 BarChart 工具提示](./media/tooltips-in-samplebarchart.png)

上述工具提示說明單一橫條的類別和值。 它可以進行擴充，以便在單一工具提示中顯示多個值。

## <a name="handling-tooltips"></a>處理工具提示

您用來管理工具提示的介面是 'ITooltipService'。 這個介面可用來通知主機必須顯示、移除或移動工具提示。

```typescript
    interface ITooltipService {
        enabled(): boolean;
        show(options: TooltipShowOptions): void;
        move(options: TooltipMoveOptions): void;
        hide(options: TooltipHideOptions): void;
    }
```

您的視覺效果必須接聽視覺效果內滑鼠事件，以及視需要呼叫 `show()`、`move()` 和 `hide()` 委派，並在 `Tooltip****Options` 物件中填入適當的內容。
`TooltipShowOptions` 和 `TooltipHideOptions` 依次定義要顯示的內容，以及在這些事件中的運作方式。
因為呼叫這些方法會牽涉到使用者事件 (例如滑鼠移動或觸控事件)，所以最好是為這些事件建立接聽程式，進而叫用 `TooltipService` 成員。
範例會在稱為 `TooltipServiceWrapper` 的類別中彙總。

### <a name="tooltipservicewrapper-class"></a>TooltipServiceWrapper 類別

這個類別背後的基本概念是保存 `TooltipService` 的執行個體、接聽相關元素上的 D3 滑鼠事件，然後在需要時呼叫 `hide()` 和 `show()`。
類別會保存及管理這些事件的任何相關狀態和邏輯，主要用於與基礎 D3 程式碼互動。 D3 互動和轉換超出本文件的範圍。

您可以在 [SampleBarChart 視覺效果存放庫](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/981b021612d7b333adffe9f723ab27783c76fb14)中找到完整的範例程式碼

### <a name="creating-tooltipservicewrapper"></a>建立 TooltipServiceWrapper

BarChart 建構函式現在有一個 `tooltipServiceWrapper` 成員，它會在建構函式中使用主機 `tooltipService` 執行個體進行具現化。

```typescript
        private tooltipServiceWrapper: ITooltipServiceWrapper;

        this.tooltipServiceWrapper = createTooltipServiceWrapper(this.host.tooltipService, options.element);
```

`TooltipServiceWrapper` 類別會保存 `tooltipService` 實例，也會作為視覺效果和觸控參數的根 D3 元素。

```typescript
    class TooltipServiceWrapper implements ITooltipServiceWrapper {
        private handleTouchTimeoutId: number;
        private visualHostTooltipService: ITooltipService;
        private rootElement: Element;
        private handleTouchDelay: number;

        constructor(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay: number) {
            this.visualHostTooltipService = tooltipService;
            this.handleTouchDelay = handleTouchDelay;
            this.rootElement = rootElement;
        }
        .
        .
        .
    }
```

`addTooltip` 方法是這個類別用來註冊事件接聽程式的單一進入點。

### <a name="addtooltip-method"></a>addTooltip 方法

```typescript
        public addTooltip<T>(
            selection: d3.Selection<Element>,
            getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[],
            getDataPointIdentity: (args: TooltipEventArgs<T>) => ISelectionId,
            reloadTooltipDataOnMouseMove?: boolean): void {

            if (!selection || !this.visualHostTooltipService.enabled()) {
                return;
            }
        ...
        ...
        }
```

* **selection: d3.Selection<Element>**
* 用來處理工具提示的 D3 元素
* **getTooltipInfoDelegate: (args:TooltipEventArgs<T>) => VisualTooltipDataItem[]**
* 用於按照上下文填入工具提示內容 (要顯示的內容) 的委派
* **getDataPointIdentity: (args:TooltipEventArgs<T>) => ISelectionId**
* 用於擷取資料點識別碼的委派 - 未在此範例中使用 
* **reloadTooltipDataOnMouseMove?: boolean**
* 指出是否要在 mouseMove 事件期間重新整理工具提示資料的布林值 - 未在此範例中使用

如您所見，如果已停用 `tooltipService` 或沒有真正的選取項目，`addTooltip` 將會結束而不採取任何動作。

### <a name="call-of-show-method-to-display-a-tooltip"></a>呼叫 show 方法以顯示工具提示

`addTooltip` 接下來會接聽 D3 `mouseover` 事件。

```typescript
        ...
        ...
        selection.on("mouseover.tooltip", () => {
            // Ignore mouseover while handling touch events
            if (!this.canDisplayTooltip(d3.event))
                return;

            let tooltipEventArgs = this.makeTooltipEventArgs<T>(rootNode, true, false);
            if (!tooltipEventArgs)
                return;

            let tooltipInfo = getTooltipInfoDelegate(tooltipEventArgs);
            if (tooltipInfo == null)
                return;

            let selectionId = getDataPointIdentity(tooltipEventArgs);

            this.visualHostTooltipService.show({
                coordinates: tooltipEventArgs.coordinates,
                isTouchEvent: false,
                dataItems: tooltipInfo,
                identities: selectionId ? [selectionId] : [],
            });
        });
```

* **makeTooltipEventArgs**
* 將 D3 所選取元素的內容擷取至 tooltipEventArgs。 它也會計算座標。
* **getTooltipInfoDelegate**
* 然後從 tooltipEventArgs 建置工具提示內容。 這是 BarChart 類別的回呼，因為它是視覺效果的邏輯。 這是要在工具提示中顯示的實際文字內容。
* **getDataPointIdentity**
* 未在此範例中使用
* **this.visualHostTooltipService.show**
* 要顯示工具提示的呼叫  

您可以在 `mouseout` 和 `mousemove` 事件的範例中找到其他處理。

如需詳細資訊，請參閱 [SampleBarChart 視覺效果存放庫](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/981b021612d7b333adffe9f723ab27783c76fb14)。

### <a name="populating-the-tooltip-content-by-gettooltipdata-method"></a>透過 getTooltipData 方法填入工具提示內容

以成員 `getTooltipData` 新增 `BarChart`，該成員只會將資料點的分類、值和色彩擷取至 VisualTooltipDataItem[] 元素。

```typescript
        private static getTooltipData(value: any): VisualTooltipDataItem[] {
            return [{
                displayName: value.category,
                value: value.value.toString(),
                color: value.color,
                header: 'ToolTip Title'
            }];
        }
```

在上述實作中，`header` 成員是常數，但可用於需要動態值的更複雜實作。 您可以使用多個元素填入 `VisualTooltipDataItem[]`，這會將多行新增至工具提示。 這在視覺效果 (例如堆疊橫條圖) 中很有用，其中工具提示可能會顯示來自多個單一資料點的資料。

### <a name="calling-addtooltip-method"></a>呼叫 addTooltip 方法

最後一個步驟是在實際資料可能變更時呼叫 `addTooltip`。 這個呼叫會在 `BarChart.update()` 方法中進行。 因此，會進行呼叫來監視所有 'bar' 元素的選取項目，只傳遞如上所述的 `BarChart.getTooltipData()`。

```typescript
        this.tooltipServiceWrapper.addTooltip(this.barContainer.selectAll('.bar'),
            (tooltipEvent: TooltipEventArgs<number>) => BarChart.getTooltipData(tooltipEvent.data),
            (tooltipEvent: TooltipEventArgs<number>) => null);
```

## <a name="adding-report-page-tooltips"></a>新增報表頁面工具提示

為了新增報表頁面工具提示支援，大部分的變更都位於 capabilities.json 中。

範例結構描述為

```json
{
    "tooltips": {
        "supportedTypes": {
            "default": true,
            "canvas": true
        },
        "roles": [
            "tooltips"
        ]
    }
}
```

報表頁面工具提示定義可以在 [格式] 窗格上完成。

![報表頁面工具提示](media/report-page-tooltip.png)

`supportedTypes` 是視覺效果所支援的工具提示設定，且會反映在欄位上。 `default` 指定是否支援透過資料欄位繫結的「自動」工具提示。 畫布指定是否支援報表頁面工具提示。

`roles` 為選擇性項目。 定義之後，指示哪些資料角色會繫結至欄位中選取的工具提示選項。

如需詳細資訊，請參閱報表頁面工具提示使用指導方針的[報表頁面工具提示](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#tooltips)

為了顯示報表頁面工具提示，在呼叫 `ITooltipService.Show(options: TooltipShowOptions)` 或 `ITooltipService.Move(options: TooltipMoveOptions)` 時，Power BI 主機會取用 selectionId (上述 `options` 引數的 `identities` 屬性)。 SelectionId 應該代表您在上方停留以供工具提示擷取的項目所選取的資料 (類別、數列等)。

將 selectionId 傳送至工具提示顯示呼叫的範例：

```typescript
    this.tooltipServiceWrapper.addTooltip(this.barContainer.selectAll('.bar'),
        (tooltipEvent: TooltipEventArgs<number>) => BarChart.getTooltipData(tooltipEvent.data),
        (tooltipEvent: TooltipEventArgs<number>) => tooltipEvent.data.selectionID);
```
