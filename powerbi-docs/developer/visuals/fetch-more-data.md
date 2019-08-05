---
title: 擷取更多資料
description: 為 Power BI 視覺效果啟用大型資料集的分段擷取
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425060"
---
# <a name="fetch-more-data-from-power-bi"></a>從 Power BI 擷取更多資料

載入更多資料 API 克服了 30-K 資料點的硬性限制。 它會以區塊方式引進資料。 區塊大小可根據使用案例來進行設定，以改善效能。  

## <a name="enable-segmented-fetch-of-large-datasets"></a>啟用大型資料集的分段擷取

若為 `dataview` 區段模式，請在視覺效果的 `capabilities.json` 中為所需的 dataViewMapping 定義 "window" dataReductionAlgorithm。
`count` 會決定視窗大小，這會限制每個更新中附加至 `dataview` 的新資料列數目。

要在 capabilities.json 中新增

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

## <a name="usage-in-the-custom-visual"></a>自訂視覺效果中的使用方式

透過檢查 `dataView.metadata.segment` 的存在與否，即可判斷指示資料是否存在：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

您也可以藉由檢查 `options.operationKind`，檢查它是第一個更新還是後續更新。

`VisualDataChangeOperationKind.Create` 表示第一個區段，而 `VisualDataChangeOperationKind.Append` 則表示後續區段。

請參閱以下程式碼片段，以取得範例實作：

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

也可以從 UI 事件處理常式叫用 `fetchMoreData` 方法

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI 將會以新資料區段來呼叫視覺效果的 `update` 方法,，以作為呼叫 `this.host.fetchMoreData` 方法的回應。

> [!NOTE]
> Power BI 目前會將所有擷取的資料限制為 **100 MB**，以避免用戶端記憶體限制。 當 fetchMoreData () 傳回 'false' 時，您會偵測到已達到此限制。*
