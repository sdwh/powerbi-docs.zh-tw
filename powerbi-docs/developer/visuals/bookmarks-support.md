---
title: 書籤
description: Power BI 視覺效果可以處理書籤切換
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425497"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>新增 Power BI 視覺效果的書籤支援

Power BI 報表書籤允許擷取報表頁面的設定視圖、視覺效果的選取項目狀態、篩選狀態。 但它需要從自訂視覺效果執行其他動作，以支援書籤並正確地回應變更。

請在[文件](https://docs.microsoft.com/power-bi/desktop-bookmarks)中深入了解書籤

## <a name="report-bookmarks-support-in-your-visual"></a>視覺效果中的報表書籤支援

如果您的視覺效果與其他視覺效果互動、選取資料點或篩選其他視覺效果，則必須從屬性還原狀態。

## <a name="how-to-add-report-bookmarks-support"></a>如何新增報表書籤支援

1. 安裝 (或更新) 所需的 util：`powerbi-visuals-utils-interactivityutils`https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) 3.0.0 版或更高版本。 它包含要使用狀態選取項目或篩選進行操作的其他類別。 篩選視覺效果和任何使用 `InteractivityService` 的視覺效果都需要它。

2. 將視覺效果 API 更新為 1.11.0，以在 `SelectionManager` 的執行個體中使用 `registerOnSelectCallback`。 使用一般 `SelectionManager` 而不是 `InteractivityService` 的非篩選視覺效果需要這麼做。

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>自訂視覺效果如何在報表書籤案例中與 Power BI 互動

讓我們考慮下列範例：使用者在報表頁面中建立數個書籤，每個書籤的選取項目狀態都不同。

首先，使用者會選取視覺效果中的資料點。 視覺效果可藉由將選取項目傳遞至主機來與 Power BI 和其他視覺效果互動。 然後，使用者在 `Bookmark panel` 中選取 [新增]，Power BI 就會儲存新書籤的目前選取項目。

當使用者變更選取項目並新增書籤時，就會重複發生此狀況。
建立後，使用者就可以在書籤之間切換。

當使用者選取書籤時，Power BI 會還原已儲存的篩選或選取項目狀態，並傳遞至視覺效果。 其他視覺效果將根據儲存在書籤中的狀態進行醒目提示或篩選。 Power BI 主機負責執行動作。 您的視覺效果負責正確反映新選取項目狀態 (例如，變更所呈現資料點的色彩)。

新的選取項目狀態會透過 `update` 方法傳達給視覺效果。 `options` 引數將包含特殊屬性：`options.jsonFilters`。 它是 JSONFilter，屬性可以包含 `Advanced Filter` 和 `Tuple Filter`。

視覺效果應還原篩選值，以顯示所選取書籤的視覺效果狀態。

或者，如果視覺效果僅使用選取項目，請使用 ISelectionManager 的特殊回呼函式呼叫已註冊 `registerOnSelectCallback` 方法。

### <a name="visuals-with-selections"></a>含有選取項目的視覺效果

如果您的視覺效果使用[選取項目](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md)來與其他視覺效果互動， 您有兩種新增書籤的方法。

* 如果您之前在視覺效果中**未使用 [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** ，則可以使用 `FilterManager.restoreSelectionIds` 方法。

* 如果您的視覺效果已使用 **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** 來管理選取項目， 您應該在 `InteractivityService` 的執行個體中使用 `applySelectionFromFilter` 方法。

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>使用 `ISelectionManager.registerOnSelectCallback`

當使用者按一下書籤時，Power BI 會使用對應的選取項目來呼叫視覺效果 `callback` 方法。 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

假設您在以 [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74) 方法建立的視覺效果中有一個資料點。

而且 `datapoints` 看起來像這樣：

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

因此，您會使用 `visualDataPoints` 作為資料點，並將 `ids` 陣列傳遞至 `callback` 函式。

此時，視覺效果應該將 `ISelectionId[]` 的陣列與 `visualDataPoints` 陣列中的選取項目進行比較，並將對應的資料點標記為已選取。

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

更新資料點之後，它們會反映儲存在 `filter` 物件中的目前選取項目狀態。 然後，在呈現資料點時，自訂視覺效果的選取項目狀態會符合書籤狀態。

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>使用 `InteractivityService` 來控制視覺效果中的選取項目

如果您的視覺效果使用 `InteractivityService`，則不需要執行任何其他動作來支援視覺效果中的書籤。

當使用者選取書籤時，util 將會處理視覺效果的選取項目狀態。

### <a name="visuals-with-filter"></a>含有篩選的視覺效果

假設視覺效果會建立依日期範圍的資料篩選。 因此，我們使用 `startDate` 和 `endDate` 作為範圍的開始和結束。
視覺效果會建立一個進階篩選並呼叫主機方法 `applyJsonFilter`，以依據相關條件來篩選資料。
`target` 是用於篩選的資料表。

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

每次使用者按一下書籤時，自訂視覺效果就會收到 `update` 呼叫。

自訂視覺效果應檢查物件中的篩選：

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

如果 `filter` 物件不是 Null，則視覺效果應從物件還原篩選條件：

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

之後，視覺效果應變更其內部狀態 (資料點和視覺化物件 (線條、矩形等)) 以反映目前的條件。

> [!IMPORTANT]
> 在報表書籤案例中，視覺效果不應呼叫 `applyJsonFilter` 來篩選其他視覺效果，它們已由 Power BI 進行篩選。

時間軸交叉分析篩選器視覺效果會將範圍選取器變更為對應的資料範圍。

如需詳細資訊，請參閱[時間軸交叉分析篩選器存放庫](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df)。

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>用來在書籤中儲存視覺效果屬性的篩選狀態

`filterState` 屬性可讓屬性成為篩選的一部分。 視覺效果可以在書籤中儲存不同的值。

若要將屬性值儲存為篩選狀態，物件屬性應該在 `capabilities.json` 中標記為 `"filterState": true`。

範例：`Timeline Slicer` 將 `Granularity` 屬性值儲存在篩選中。 而且它可讓您在使用者變更書籤時，變更目前的資料粒度。

如需詳細資訊，請參閱[時間軸交叉分析篩選器存放庫](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334)。
