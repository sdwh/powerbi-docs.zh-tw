---
title: "Power BI 支援的深入解析類型"
description: "使用 Power BI 快速深入解析和檢視深入解析。"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/20/2017
ms.author: mihart
ms.openlocfilehash: 53e5e67da9bacd9fc9dcbb770747823647aa3a3c
ms.sourcegitcommit: 6ea8291cbfcb7847a8d7bc4e2b6abce7eddcd0ea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-insights-supported-by-power-bi"></a>Power BI 支援的深入解析類型
## <a name="how-does-insights-work"></a>深入解析如何運作？
Power BI 可快速地搜尋資料集的不同子集，同時套用一組複雜的演算法來探索潛在相關的深入剖析資訊。 Power BI 會在分配的時間內盡可能掃描資料集。

您可以針對資料集或儀表板圖格執行深入解析。   

## <a name="what-types-of-insights-can-we-find"></a>我們可以尋找哪些類型的深入剖析資訊？
以下是我們所使用的一些演算法：

## <a name="category-outliers-topbottom"></a>類別極端值 (上/下)
針對模型中的量值，醒目提示維度的一或兩個成員值大於維度的其他成員值的情況。  

![](media/service-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>變更時間序列中的點
醒目提示資料時間序列中的趨勢明顯變更的情況。

![](media/service-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>相互關聯
偵測當根據資料集中的某個維度繪製多個量值時，多個量值彼此之間顯示相互關聯的情況。

![](media/service-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>低變異數
偵測到資料點距離平均值不遠的情況。

![](media/service-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>多數 (主要因素)
尋找當總值由另一個維度分解時，其多數可能歸因於單一因素的情況。  

![](media/service-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>時間序列中的整體趨勢
偵測時間序列資料中的向上或向下趨勢。

![](media/service-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>時間序列中的季節性
尋找時間序列資料中的週期模式，例如每週、每月或每年的季節性。

![](media/service-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>穩定佔有率
醒目提示子值的部分相對於跨連續變數的整體父值有父子相互關聯的情況。

![](media/service-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>時間序列極端值
針對跨時間序列的資料，偵測特定日期或時間值明顯不同於其他日期/時間值的情況。

![](media/service-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>後續步驟
[Power BI 深入解析](service-insights.md)

如果您擁有資料集，請[針對深入解析將它最佳化](service-insights-optimize.md)。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

