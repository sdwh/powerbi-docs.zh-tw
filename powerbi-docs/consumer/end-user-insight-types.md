---
title: Power BI 支援的深入解析類型
description: 使用 Power BI 快速深入解析和檢視深入解析。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/2/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 507d49ba6cdb894667bf66f8f35c5c325b9ff25e
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71943915"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Power BI 支援的深入解析類型

Power BI 服務可以自動在您的儀表板或報表中尋找見解。

## <a name="how-does-insights-work"></a>深入解析如何運作？
Power BI 可快速搜尋資料集的不同子集， 並在搜尋時套用一組複雜的演算法來探索潛在相關見解。 Power BI 會在分配的時間內盡可能掃描資料集。

您可以針對資料集或儀表板圖格執行深入解析。   

## <a name="what-types-of-insights-can-we-find"></a>我們可以尋找哪些類型的深入剖析資訊？
以下是我們所使用的一些演算法：

## <a name="category-outliers-topbottom"></a>類別極端值 (上/下)
針對模型中的量值，醒目提示維度的一或兩個成員值大於維度的其他成員值的情況。  

![類別極端值範例](./media/end-user-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>變更時間序列中的點
醒目提示資料時間序列中的趨勢明顯變更的情況。

![變更時間序列中的點範例](./media/end-user-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>相互關聯
偵測當根據資料集中的某個維度繪製多個量值時，多個量值彼此之間顯示相互關聯的情況。

![相互關聯範例](./media/end-user-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>低變異數
偵測到資料點距離平均值不遠的情況。

![低差異範例](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>多數 (主要因素)
尋找當總值由另一個維度分解時，其多數可能歸因於單一因素的情況。  

![主要因素範例](./media/end-user-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>時間序列中的整體趨勢
偵測時間序列資料中的向上或向下趨勢。

![時間序列中的整體趨勢範例](./media/end-user-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>時間序列中的季節性
尋找時間序列資料中的週期模式，例如每週、每月或每年的季節性。

![季節性範例](./media/end-user-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>穩定佔有率
醒目提示子值的部分相對於跨連續變數的整體父值有父子相互關聯的情況。

![穩定佔有率範例](./media/end-user-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>時間序列極端值
針對跨時間序列的資料，偵測特定日期或時間值明顯不同於其他日期/時間值的情況。

![時間序列極端值範例](./media/end-user-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>後續步驟
[Power BI 深入解析](end-user-insights.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

