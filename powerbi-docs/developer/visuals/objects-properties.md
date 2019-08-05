---
title: 物件與屬性
description: Power BI 視覺效果的可自訂屬性
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424600"
---
# <a name="object-and-properties"></a>物件與屬性

物件會描述與視覺效果建立關聯的可自訂屬性。
每個物件都可以有多個屬性，且每個屬性都有一個與其建立關聯的類型。
類型指的是屬性的內容。 如需類型的詳細資訊，請參閱下文。

`myCustomObject` 是在 `dataView` 和 `enumerateObjectInstances` 中用來參考物件的內部名稱

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>顯示名稱

`displayName` 是將會顯示在 [屬性] 窗格中的名稱。

## <a name="properties"></a>屬性

`properties` 是開發人員所定義的屬性對應。

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` 是啟用參數來切換物件的特殊屬性。

範例：

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>屬性類型

屬性類型有兩種類型：`ValueTypeDescriptor` 和 `StructuralTypeDescriptor`。

#### <a name="value-type-descriptor"></a>實值型別描述項

`ValueTypeDescriptor` 大多是基本類型，通常作為靜態物件使用。
以下是一些常見的 `ValueTypeDescriptor`

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>結構類型描述項

`StructuralTypeDescriptor` 主要用於資料繫結物件。
Fill 是最常見的 `StructuralTypeDescriptor`

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>漸層屬性

漸層屬性是無法設定為標準屬性的屬性。 相反地，您必須設定要替代色彩選擇器屬性 (fill 類型) 的規則。
請參閱下列範例：

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

請注意 `"fill"` 和 `"fillRule"` 屬性。 第一個是色彩選擇器，第二個是漸層的替代規則，其會在符合規則條件時將 "fill" 替代為 `visually`。

fill 屬性與替代規則之間的這個連結是在 `"fillRule"` 屬性 `"rule"`->`"output"` 區段中設定。

`"Rule"`->`"InputRole"` 設定哪一個資料角色會觸發規則 (條件)。 在此範例中，如果資料角色 `"Gradient"` 包含資料，則會針對 `"fill"` 屬性套用規則。

您可以在下方看到觸發 fill 規則 (`the last item`) 的資料角色範例。

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="enumerateobjectinstances-method"></a>`enumerateObjectInstances` 方法

若要有效地使用物件，您必須在自訂視覺效果中使用稱為 `enumerateObjectInstances` 的函式。 此函式會在屬性窗格中填入物件，也會決定應在 dataView 內繫結物件的位置。  

一般設定如下所示：

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>屬性

`enumerateObjectInstances` 中的屬性會反映您在功能中定義的屬性。 請參閱頁面底部的範例。

### <a name="objects-selector"></a>物件選取器

`enumerateObjectInstances` 中選取器會決定每個物件在 dataView 中的繫結位置。 有四個不同的選項。

#### <a name="static"></a>靜態

此物件會繫結到中繼資料 `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>資料行

此物件會繫結到具有相符 `QueryName` 的資料行。

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>選取器

此物件會繫結到我們為其建立 `selectionID` 的項目。 在此範例中，我們假設我們已針對某些 dataPoints 建立 `selectionID`，且我們會反覆執行它們。

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>範圍識別

此物件會繫結到群組交集處的特定值。 例如，如果我有類別 `["Jan", "Feb", "March", ...]` 和序列 `["Small", "Medium", "Large"]`，我可能想要在符合 `Large` 和 `Feb` 的值交集處有一個物件。 為了達到這個目的，我可以取得這兩個資料行的 `DataViewScopeIdentity`，將其推送至 `identities` 變數，並將此語法與選取器搭配使用。

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>範例

在此範例中，我們會針對具有一個屬性 `fill` 的 customColor 物件顯示一個 objectEnumeration 可能外觀。 我們希望此物件以靜態方式繫結到 `dataViews[index].metadata.objects`

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
