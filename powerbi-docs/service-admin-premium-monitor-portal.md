---
title: 使用系統管理入口網站來監視 Power BI Premium 容量
description: 您可以使用 Power BI 系統管理入口網站來監視您的 Premium 容量。
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0d1e0da498a7a2c78e86b643b8a86cb87d6d095a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856855"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>在系統管理入口網站中監視容量

在系統管理員入口網站中，[容量設定]  區域的 [健康情況]  索引標籤會提供有關您的容量和已啟用工作負載的計量摘要。  

![入口網站中的 [容量健康情況] 索引標籤](media/service-admin-premium-monitor-portal/admin-portal-health.png)

如果您需要更完整的計量，請使用 [Power BI Premium 容量計量](service-admin-premium-monitor-capacity.md)應用程式。 應用程式會提供向下切入和篩選，以及會影響容量效能、近乎每個層面的最詳細計量。 若要深入了解，請參閱[使用應用程式監視 Premium 容量](service-admin-premium-monitor-capacity.md)。

## <a name="system-metrics"></a>系統計量

在 [健康情況]  索引標籤上，CPU 使用率和記憶體使用量可提供容量最重要計量的快速檢視。 這些計量是累計的，包括針對容量所有已啟用的工作負載。

| **計量** | **描述** |
| --- | --- |
| CPU 使用率 | 平均 CPU 使用率 (以總可用 CPU 的百分比表示)。 |
| 記憶體使用量 | 平均記憶體使用量 (GB)。|

## <a name="workload-metrics"></a>工作負載計量

針對容量啟用的每個工作負載。 CPU 使用率和記憶體使用量隨即顯示。

| **計量** | **描述** |
| --- | --- |
| CPU 使用率 | 平均 CPU 使用率 (以總可用 CPU 的百分比表示)。 |
| 記憶體使用量 | 平均記憶體使用量 (GB)。|

### <a name="detailed-workload-metrics"></a>詳細工作負載計量

每個工作負載都有額外的計量。 顯示的計量類型取決於工作負載。 若要查看工作負載的詳細計量，請按一下展開 (向下) 箭號。

![工作負載健康情況展開](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>資料流程

##### <a name="dataflow-operations"></a>資料流程作業

| **計量** | **描述** |
| --- | --- |
| 總計數 | 每個資料流程的重新整理次數總計。 |
| 成功計數 | 每個資料流程成功的重新整理次數總計。|
| 平均持續期間 (分鐘) | 重新整理資料流程的平均持續時間 (以分鐘為單位) |
| 持續時間上限 (分鐘) | 重新整理資料流程的最長持續時間 (以分鐘為單位)。 |
| 平均等候時間 (分鐘) | 已排程的時間與開始重新整理資料流程之間的平均延隔時間 (以分鐘為單位)。 |
| 最大等候時間 (分鐘) | 資料流程的等候時間上限 (以分鐘為單位)。  |

#### <a name="datasets"></a>資料集

##### <a name="refresh"></a>重新整理

| **計量** | **描述** |
| --- | --- |
| 總計數 | 每個資料集的重新整理次數總計。 |
| 成功計數 | 每個資料集成功的重新整理次數總計。 |
| 失敗計數 | 每個資料集的重新整理失敗次數總計。 |
| 成功率  | 成功重新整理的次數除以要測量的重新整理總數。 可靠性。 |
| 平均持續期間 (分鐘) | 重新整理資料集的平均持續時間 (以分鐘為單位)。  |
| 持續時間上限 (分鐘) | 重新整理資料集的最長持續時間 (以分鐘為單位)。 |
| 平均等候時間 (分鐘) | 已排程的時間與開始重新整理資料集之間的平均延隔時間 (以分鐘為單位)。 |
| 最大等候時間 (分鐘) | 資料集的等候時間上限 (以分鐘為單位)。 |

##### <a name="query"></a>查詢

| **計量** | **描述** |
| --- | --- |
| 總計數 | 針對資料集執行的查詢總數。 |
| 平均持續期間 (毫秒) |資料集的平均查詢持續時間 (以毫秒為單位)|
| 持續時間上限 (毫秒) |資料集中執行查詢的最長持續時間 (以毫秒為單位)。 |
| 平均等候時間 (毫秒) |資料集的平均查詢等候時間 (以毫秒為單位)。 |
| 等候時間上限 (毫秒) |資料集中等候查詢的最長持續時間 (以毫秒為單位)。 |

##### <a name="eviction"></a>收回

| **計量** | **描述** |
| --- | --- |
| 模型計數 | 此容量的資料集收回總數。 當容量面臨記憶體壓力時，節點就會從記憶體「收回」一或多個資料集。 非使用中的資料集 (沒有任何正在執行的查詢/重新整理作業) 會優先收回。 然後，依據「最近最少使用的」(LRU) 量值來決定收回的順序。 |

#### <a name="paginated-reports"></a>編頁報表

##### <a name="report-execution"></a>報表執行

| **計量** | **描述** |
| --- | --- |
| 執行計數  | 使用者執行和檢視報表的次數。|

##### <a name="report-usage"></a>報表使用量

| **計量** | **描述** |
| --- | --- |
| 成功計數 | 使用者已檢視報告的次數。 |
| 失敗計數 |使用者已檢視報告的次數。|
| 資料列計數 |報告中資料的資料列數。 |
| 資料擷取持續期間 (毫秒) |擷取報表資料所需的平均時間量 (以毫秒為單位)。 持續時間很長，可能表示查詢速度緩慢或其他資料來源的問題。  |
| 處理持續期間 (毫秒) |處理報告資料所需的平均時間量 (以毫秒為單位)。 |
| 轉譯持續期間 (毫秒) |在瀏覽器中轉譯報告所需的平均時間量 (以毫秒為單位)。 |

> [!NOTE]
> 尚未提供 **AI** 工作負載的詳細計量。

## <a name="next-steps"></a>後續步驟

現在您已了解如何監視 Power BI Premium 容量，請繼續學習如何最佳化容量。

> [!div class="nextstepaction"]
> [將 Power BI Premium 容量最佳化](service-premium-capacity-optimize.md)
