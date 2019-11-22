---
title: Power BI 互動功能公用程式
description: 此文章說明如何使用互動功能公用程式，將選取項目新增至 Power BI 視覺效果中
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8a9218085b0da655d1ce4b3ece0b2666c4826c86
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061860"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Microsoft Power BI 視覺效果互動功能公用程式

InteractivityUtils 是一組函式和類別，可簡化 Power BI 自訂視覺效果的交叉選取和交叉篩選的實作。

## <a name="installation"></a>安裝

> [!NOTE]
> 如果您繼續使用舊版本的 powerbi-visuals-tools (版本號碼小於 3.x.x)，請安裝新版工具 (3.x.x)。

> [!IMPORTANT]
> 互動功能公用程式的新更新將僅支援最新版本的工具。 [深入了解如何更新視覺效果程式碼以搭配最新的工具使用](migrate-to-new-tools.md)

若要安裝套件，您應該在具有目前自訂視覺效果的目錄中執行下列命令：

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

從 3.0 版或更新版本，您也需要安裝 ```powerbi-models``` 來解析相依性。

```bash
npm install powerbi-models --save
```

針對使用者互動功能公用程式，您必須在視覺效果原始程式碼中匯入必要的元件。

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>將 CSS 成品包含在自訂視覺效果中

若要將套件與您的自訂視覺效果搭配使用，您應該將下列 CSS 檔案匯入 `your.less` 檔案：

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

因此，您將會有下列檔案結構：

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> 您應該將 .css 檔案匯入為 .less 檔案，因為 Power BI 視覺效果工具會包裝外部 CSS 規則。

## <a name="usage"></a>使用量

### <a name="define-interface-for-data-points"></a>定義資料點的介面

通常資料點會包含選取項目和值。 該介面會擴充 `SelectableDataPoint` 介面。 `SelectableDataPoint` 已包含屬性：

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

使用互動功能公用程式的第一個步驟是建立互動功能公用程式的執行個體，並將物件另存為視覺效果的屬性

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

第二個步驟是擴充基底行為類別：

> [!NOTE]
> [互動功能公用程式的 5.6.x 版本](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0) \(英文\) 中引入了 BaseBehavior。 如果您使用舊版本，請從下列範例建立行為類別 (`BaseBehavior` 類別相同)：

定義行為類別的選項介面：

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

定義 `visual behaviour` 的類別。 負責處理 `click`、`contextmenu` 滑鼠事件的類別。
當您按下資料元素時，視覺效果會呼叫選取項目處理常式來選取資料點。 或清除選取項目 (如果使用者按一下視覺效果的背景元素)。 且類別有對應的方法：`bindClick`、`bindClearCatcher`、`bindContextMenu`。

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

或者，您也可以擴充 `BaseBehavior` 類別：

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

若要處理按一下元素，請呼叫 D3 選取項目物件的 `on` 方法 (也適用於 elementsSelection 和 clearCatcherSelection)：

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

為 `contextmenu` 事件新增類似的處理常式，以呼叫選取項目管理員的 `showContextMenu` 方法：

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

互動功能公用程式會呼叫 `bindEvents` 方法，將函式指派給處理常式、將 `bindClick`、`bindClearCatcher`和 `bindContextMenu` 的呼叫加入至 `bindEvents` 方法中：

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

`renderSelection` 方法，負責更新圖表中元素的視覺狀態。

`renderSelection` 方法實作的範例：

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

最後一個步驟是建立 `visual behavior` 的執行個體，以及互動功能公用程式執行個體 `bind` 方法的呼叫：

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` 是 D3 選取項目物件，代表視覺效果上所有可選取的元素。

* `select(this.target)` 是 D3 選取項目物件，代表視覺效果的主要 DOm 元素。

* 包含元素的 `this.categories` 資料點，其中介面為 `VisualDataPoint` (或 `categories: VisualDataPoint[];`)

* `this.behavior` 是 `visual behavior` 的新執行個體

  在視覺效果的建構函式中建立：

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

現在，您的視覺效果已準備好處理選取項目。

## <a name="next-steps"></a>後續步驟

* [了解如何處理書籤切換上的選擇](bookmarks-support.md#visuals-with-selection)

* [了解如何為視覺效果資料點新增操作功能表](context-menu.md)

* [了解如何使用選取項目管理員將選取項目新增至 Power BI 視覺效果中](selection-api.md)
