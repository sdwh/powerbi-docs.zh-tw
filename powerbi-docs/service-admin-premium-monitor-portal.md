---
title: 使用系統管理入口網站來監視 Power BI Premium 容量
description: 您可以使用 Power BI 系統管理入口網站來監視您的 Premium 容量。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564903"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>在系統管理入口網站中監視容量

**健全狀況**索引標籤中**容量設定**在管理入口網站中的區域會提供您容量且已啟用的工作負載的相關摘要計量。  

![在入口網站中的容量健全狀況 索引標籤](media/service-admin-premium-monitor-portal/admin-portal-health.png)

如果您需要更完整的度量資訊，請使用[Power BI Premium 容量計量](service-admin-premium-monitor-capacity.md)應用程式。 應用程式提供向下鑽研及篩選，並最詳細的度量接近容量效能影響的各個層面。 若要進一步了解，請參閱[使用應用程式的監視 Premium 容量](service-admin-premium-monitor-capacity.md)。

## <a name="system-metrics"></a>系統計量

在 **健全狀況**索引標籤，在最高的層級，CPU 使用率和記憶體使用量提供最重要的計量容量的快速檢視。 這些度量會累計，包括所有已啟用工作負載的容量。

| **計量** | **描述** |
| --- | --- |
| CPU 使用率 | 平均 CPU 使用率、 可用總 cpu 百分比。 |
| 記憶體使用量 | 平均記憶體使用量 (gb)。|

## <a name="workload-metrics"></a>工作負載度量

每個工作負載的容量已啟用。 會顯示 CPU 使用率和記憶體使用量。

| **計量** | **描述** |
| --- | --- |
| CPU 使用率 | 平均 CPU 使用率、 可用總 cpu 百分比。 |
| 記憶體使用量 | 平均記憶體使用量 (gb)。|

### <a name="detailed-workload-metrics"></a>詳細的工作負載度量

每個工作負載會有其他度量。 顯示的度量資訊的類型取決於工作負載。 若要查看工作負載的詳細的計量，按一下展開 （下） 箭號。

![展開 工作負載的健全狀況](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>資料流程

##### <a name="dataflow-operations"></a>資料流程作業

| **計量** | **描述** |
| --- | --- |
| 總計數 | 每個資料流程的重新整理次數總計。 |
| 成功計數 | 重新整理每個資料流程中成功的總計。|
| 平均持續時間 （分鐘） | 重新整理資料流程的平均持續時間 (以分鐘為單位) |
| 持續時間上限 （分鐘） | 重新整理資料流程的最長持續時間 (以分鐘為單位)。 |
| 平均等候時間 （分鐘） | 已排程的時間與開始重新整理資料流程之間的平均延隔時間 (以分鐘為單位)。 |
| 最長等候時間 （分鐘） | 資料流程的等候時間上限 (以分鐘為單位)。  |

#### <a name="datasets"></a>資料集

##### <a name="refresh"></a>重新整理

| **計量** | **描述** |
| --- | --- |
| 總計數 | 每個資料集的重新整理次數總計。 |
| 成功計數 | 每個資料集，重新整理成功的總計。 |
| 失敗計數 | 每個資料集的重新整理失敗的總數。 |
| 成功率  | 成功重新整理除以總的重新整理，以測量的數目。 可靠性。 |
| 平均持續時間 （分鐘） | 重新整理資料集的平均持續時間 (以分鐘為單位)。  |
| 持續時間上限 （分鐘） | 重新整理資料集的最長持續時間 (以分鐘為單位)。 |
| 平均等候時間 （分鐘） | 已排程的時間與開始重新整理資料集之間的平均延隔時間 (以分鐘為單位)。 |
| 最長等候時間 （分鐘） | 資料集的等候時間上限 (以分鐘為單位)。 |

##### <a name="query"></a>查詢

| **計量** | **描述** |
| --- | --- |
| 總計數 | 針對資料集執行的查詢總數。 |
| 平均持續期間 (毫秒) |資料集的平均查詢持續時間 (以毫秒為單位)|
| 持續時間上限 (毫秒) |資料集中執行查詢的最長持續時間 (以毫秒為單位)。 |
| 平均等候時間 (毫秒) |資料集的平均查詢等候時間 (以毫秒為單位)。 |
| 最長等候時間 （毫秒） |資料集中等候查詢的最長持續時間 (以毫秒為單位)。 |

##### <a name="eviction"></a>收回

| **計量** | **描述** |
| --- | --- |
| 模型計數 | 這個容量的資料集區收回總數。 當容量面臨記憶體壓力時，節點就會從記憶體「收回」一或多個資料集。 非使用中的資料集 (沒有任何正在執行的查詢/重新整理作業) 會優先收回。 然後，依據「最近最少使用的」(LRU) 量值來決定收回的順序。 |

#### <a name="paginated-reports"></a>編頁報表

##### <a name="report-execution"></a>報表執行

| **計量** | **描述** |
| --- | --- |
| 執行計數  | 在執行報表的次數，而且檢視的使用者。|

##### <a name="report-usage"></a>報表使用情況

| **計量** | **描述** |
| --- | --- |
| 成功計數 | 使用者檢視報表的次數。 |
| 失敗計數 |使用者檢視報表的次數。|
| 資料列計數 |報告中資料的資料列數。 |
| 資料擷取持續時間 （毫秒） |擷取報表資料所需的平均時間量 (以毫秒為單位)。 持續時間很長，可能表示查詢速度緩慢或其他資料來源的問題。  |
| 處理持續時間 （毫秒） |處理報告資料所需的平均時間量 (以毫秒為單位)。 |
| 轉譯持續時間 （毫秒） |在瀏覽器中轉譯報告所需的平均時間量 (以毫秒為單位)。 |

> [!NOTE]
> 詳細的度量**AI**工作負載尚無法使用。

## <a name="next-steps"></a>後續步驟

現在您已了解如何監視 Power BI Premium 容量，請繼續學習如何最佳化容量。

> [!div class="nextstepaction"]
> [最佳化 Power BI Premium 容量](service-premium-capacity-optimize.md)
