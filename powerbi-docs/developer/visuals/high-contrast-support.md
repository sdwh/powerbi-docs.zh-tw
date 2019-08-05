---
title: 高對比模式支援
description: 如何將高對比模式支援新增至 Power BI 視覺效果
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cb77ea012fdfdbd5be62c58c6f9b94a0355db1a9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424922"
---
# <a name="high-contrast-mode-support"></a>高對比模式支援

Windows [高對比]  設定使用更相異的色彩，讓您更容易看清楚文字與應用程式。
請深入了解 [high-contrast support in Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast) (Power BI 中的高對比支援)。

將高對比支援新增至您的視覺效果，需要下列各項：

1. 在初始化時：偵測 Power BI 是否處於高對比模式；如果是，則取得目前的高對比色彩。
2. 每次更新：變更視覺效果呈現的方式，讓您更容易看到。

PowerBI-visuals-sampleBarChart visual 已實作高對比支援。

如需詳細資訊，請參閱 [PowerBI-visuals-sampleBarChart 視覺效果存放庫](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6)

## <a name="on-init"></a>在初始化時

`options.host` 的 colorPalette 成員有數個高對比模式的屬性。 使用這些屬性可判斷高對比模式是否為使用中；如果是，要使用哪些色彩。

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>偵測到 Power BI 處於高對比模式

如果 `host.colorPalette.isHighContrast` 為 `true`，則高對比模式為使用中，且視覺效果應據此繪製本身。

### <a name="get-high-contrast-colors"></a>取得高對比色彩

在高對比模式中，您的視覺效果應該將其本身限制為下列色彩：

* **前景**色彩用來繪製任何線條、圖示、文字和框線，或填滿圖形。
* **背景**色彩用於背景，作為外框圖形的填滿色彩。
* **前景 - 已選取**色彩用來表示選取的或使用中的元素。
* **超連結**色彩僅用於超連結文字。

> [!NOTE]
> 如果需要次要色彩，前景色彩可能會與某些不透明度搭配使用 (Power BI 的原生視覺效果使用 40% 不透明度)。 請謹慎使用此功能，讓視覺效果詳細資料易於查看。

您可以在初始化期間儲存這些值：

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

或者，您可以在初始化期間儲存 `host` 物件，並在更新期間存取相關的 `colorPalette` 屬性。

## <a name="on-update"></a>在更新時

高對比支援的特定實作會因視覺效果而異，且取決於圖形設計的詳細資料。 高對比模式所需的設計通常與預設稍有不同，讓重要的詳細資料容易與有限色彩區別。

以下是 Power BI 原生視覺效果所遵循的一些指導方針：

* 所有資料點都會使用相同的色彩 (前景)。
* 所有文字、軸、箭號、線條等。 使用前景色彩。
* 粗圖形會繪製為外框，並使用粗筆觸 (至少兩個像素) 和背景色彩填滿。
* 當相關時，資料點會以不同的標記圖形來區分，而資料線條則是以不同的虛線來區分。
* 醒目提示資料元素時，所有其他元素都會將其不透明度變更為 40%。
* 若為交叉分析篩選器，使用中篩選元素會使用前景選取的色彩。

例如，在範例橫條圖中，所有橫條都會以兩個像素的粗前景外框和背景填滿來進行繪製。 請比較它使用預設色彩與使用幾個高對比主題的外觀：

![使用標準色彩的範例橫條圖](./media/hc-samplebarchart-standard.png)
![使用*深色 #2* 色彩主題的範例橫條圖](./media/hc-samplebarchart-dark2.png)
![使用*白色*色彩主題的範例橫條圖](./media/hc-samplebarchart-white.png)

以下是 `visualTransform` 函式中已變更為支援高對比的一個位置，它會在 `update` 期間作為轉譯的一部分進行呼叫：

### <a name="before"></a>之前

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>之後

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
