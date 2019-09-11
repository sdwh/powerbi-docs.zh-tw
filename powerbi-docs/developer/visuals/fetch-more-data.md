---
title: 從 Power BI 擷取更多資料
description: 此文章討論如何為 Power BI 視覺效果啟用大型資料集的分段擷取。
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7e5ecc0e317a21d10e76e9413926822ac4d6760b
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237129"
---
# <a name="fetch-more-data-from-power-bi"></a>從 Power BI 擷取更多資料

此文章討論如何載入更多資料，以克服 30-KB 資料點的硬性限制。 此方法以區塊形式提供資料。 若要改善效能，您可以將區塊大小設定為適合您使用案例的大小。  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>啟用大型資料集的分段擷取

若為 `dataview` 區段模式，請在視覺效果的 *capabilities.json* 檔案中，為所需的 dataViewMapping 定義 dataReductionAlgorithm 的視窗大小。 `count` 會決定視窗大小，這會限制每個更新中可以附加至 `dataview` 的新資料列數目。

在 *capabilities.json* 檔案中新增下列程式碼：

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

新的區段會附加至現有 `dataview`，並提供給視覺效果作為 `update` 呼叫。

## <a name="usage-in-the-power-bi-visual"></a>Power BI 視覺效果中的使用方式

若要判斷資料是否存在，您可以檢查 `dataView.metadata.segment` 的存在與否：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

您也可以藉由檢查 `options.operationKind`，來查看它是第一個更新還是後續更新。 在下列程式碼中，`VisualDataChangeOperationKind.Create` 參考第一個區段，而 `VisualDataChangeOperationKind.Append` 參考後續區段。

如需範例實作，請參閱下列程式碼片段：

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

您可以從 UI 事件處理常式叫用 `fetchMoreData` 方法，如下所示：

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

作為呼叫 `this.host.fetchMoreData` 方法的回應，Power BI 會使用新資料區段呼叫視覺效果的 `update` 方法。

> [!NOTE]
> 為了避免用戶端記憶體限制，Power BI 目前將擷取資料總數限制為 100 MB。 當 fetchMoreData () 傳回 `false` 時，您可以看到已達到此限制。
