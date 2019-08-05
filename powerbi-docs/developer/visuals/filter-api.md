---
title: 視覺效果篩選 API
description: Power BI 視覺效果如何篩選其他視覺效果
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425037"
---
# <a name="power-bi-visual-filters-api"></a>Power BI 視覺效果篩選 API

篩選覺效果允許篩選資料。 與選取項目的主要差異在於，儘管其他視覺效果支援醒目提示，但其他視覺效果會以任何方式進行篩選。

若要啟用視覺效果的篩選，視覺效果應在 capabilities.json 內容的 `general` 區段中包含 `filter` 物件。

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

[`powerbi-models`](https://www.npmjs.com/package/powerbi-models) 套件中提供篩選 API 介面。 此套件也包含用來建立篩選執行個體的類別。

```cmd
npm install powerbi-models --save
```

如果您使用舊版工具 (版本小於 3.x.x)，則您應該將 `powerbi-models` 包含在視覺效果套件中。 [如何包含套件的簡短指南](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

所有篩選都會擴充 `IFilter` 介面。

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` - 是資料來源上的資料表資料行。

## <a name="basic-filter-api"></a>基本篩選 API

基本篩選介面是

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` - 是具有 "In"、"NotIn"、"All" 值的列舉

`values` - 是條件的值

基本篩選的範例：

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

此篩選準表示「給我 `col1` 等於 1、2 或 3 值其中之一的所有資料列」。

SQL 對等項目是

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

若要建立篩選，您可以使用 `powerbi-models` 中的 BasicFilter 類別。

如果使用舊版工具，您應該透過 `window['powerbi-models']` 在視窗物件中取得模型的執行個體：

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

視覺效果會在提供給建構函式視覺效果的 IVisualHost 主機介面上，使用 applyJsonFilter() 方法來叫用篩選。

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>進階篩選 API

[進階篩選 API](https://github.com/Microsoft/powerbi-models) 可根據多個準則 (例如 "LessThan"、"Contains"、"Is"、"IsBlank" 等) 來啟用複雜的交叉視覺效果資料點選取/篩選查詢。

此篩選是在視覺效果 API 1.7.0 中引進。

進階篩選 API 也需要具有 `table` 和 `column` 名稱的 `target`。 但是，進階篩選 API 運算子為 `"And" | "Or"`。 

此外，篩選會使用條件，而不是具有介面的值：

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

`operator` 參數的條件運算子為 `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

SQL 對等項目是

```sql
SELECT * FROM table WHERE col1 < 0;
```

您可以在[`Sampleslicer visual`存放庫](https://github.com/Microsoft/powerbi-visuals-sampleslicer)中找到使用進階篩選 API 的完整範例程式碼。

## <a name="tuple-filter-api-multi-column-filter"></a>Tuple 篩選 API (多個資料行篩選)

Tuple 篩選 API 是在視覺效果 API 2.3.0 中引進。

Tuple 篩選 API 類似於基本篩選，但它可讓您定義數個資料行和資料表的條件。

且篩選具有介面： 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` 是包含資料表名稱的資料行陣列：

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  篩選可以處理來自不同資料表的資料行。

`$schema` 是 "http://powerbi.com/product/schema#tuple"

`filterType` 是 `FilterType.Tuple`

`operator` 僅允許使用 `"In"` 運算子

`values` 是值 Tuple 的陣列，其中每個 Tuple 都代表一個允許的目標資料行值組合 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

完整範例：

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**資料行名稱和條件值的順序是敏感性項目。**

SQL 對等項目是

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>從 DataView 還原 JSON 篩選

從 API 2.2 開始，您可以從 **VisualUpdateOptions** 還原 **JSON 篩選**

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

當使用切換書籤功能且視覺效果取得對應的 `filter` 物件時，Power BI 會呼叫視覺效果的 `update` 方法。
請[深入了解書籤支援](bookmarks-support.md)

### <a name="sample-json-filter"></a>範例 JSON 篩選

![螢幕擷取畫面 JSON 篩選](./media/json-filter.png)

### <a name="clear-json-filter"></a>清除 JSON 篩選

篩選 API 在重設或清除時接受篩選的 `null` 值。

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
