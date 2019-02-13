---
title: 使用系統管理入口網站來監視 Power BI Premium 容量
description: 您可以使用 Power BI 系統管理入口網站來監視您的 Premium 容量。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 59097c07719e4bb8db188e8a86db377076aea7a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794109"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>在系統管理入口網站中監視容量

本文說明如何在系統管理入口網站中使用容量設定區域，來取得容量效能的快速檢視。  若要取得有關容量的最深入計量，最好使用 [Power BI Premium 容量計量](service-admin-premium-monitor-capacity.md)應用程式。

## <a name="capacity-metrics"></a>容量計量

系統管理入口網站的 [容量設定] 區域提供四個量測計，這些量測計指出過去七天內您的容量所產生的負載與使用的資源量。 這四個圖格每小時更新一次，而且會指出過去七天內對應的計量超過 80% 的時數。 此計量指出可能的使用者體驗降級。

![7 天內的使用狀況](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **計量** | **描述** |
| --- | --- |
| CPU |CPU 超過 80% 使用率的次數。 |
| 記憶體過度置換 |代表後端核心的記憶體壓力。 具體而言，這個計量是因使用多個資料集的記憶體壓力而從記憶體收回資料集的次數。 |
| 記憶體使用量 |平均記憶體使用量，以吉位元組 (GB) 表示。 |
| DQ/s | 「直接查詢」和「即時連線」計數超過 80% 限制的次數。 <br>  限制每秒的 DirectQuery 和即時連線查詢總數。 P1 的限制為 30/s、P2 為 60/s，而 P3 為 120/s。  「直接查詢」和即時連線查詢計數會新增至上面的節流。 例如，如果您每秒有 15 個 DirectQuery 和 15 個即時連線，您就達到節流標準。<br> 這會平均套用至內部部署和雲端連線。 |
|  |  |

計量會反映過去一週的使用率。  如果您想要看到更詳細的計量檢視，則可以按一下任何摘要磚。  這會將您帶往進階容量之每個計量的詳細圖表。 下圖顯示 CPU 計量的詳細資料。

![詳細使用量圖表 CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

這些圖表在過去一週每小時都會彙總一次，並有助於找出您何時可能已有進階容量的特定效能相關事件。

您也可以將任何計量的基礎資料匯出至 csv 檔案。  這項匯出會依每三分鐘的間隔提供過去一週每天的詳細資訊。

## <a name="next-steps"></a>後續步驟

現在您已了解如何監視 Power BI Premium 容量，請繼續學習如何最佳化容量。

> [!div class="nextstepaction"]
> [Power BI Premium 容量資源管理與最佳化](service-premium-understand-how-it-works.md)
