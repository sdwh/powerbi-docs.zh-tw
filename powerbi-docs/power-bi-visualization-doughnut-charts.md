---
title: "Power BI 中的環圈圖 (教學課程)"
description: "教學課程：Power BI 中的環圈圖"
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
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 2f428095eb57c5358770f1d6d8572316d2b84c37
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="doughnut-charts-in-power-bi-tutorial"></a>Power BI 中的環圈圖 (教學課程)
環圈圖類似於圓形圖之處，在於它會顯示部分與整體的關聯性。 唯一的差別在於，中央為空白，且保留空間給標籤或圖示。

## <a name="create-a-doughnut-chart"></a>建立環圈圖
如果要跟著做，請登入 Power BI 並選取 [取得資料] \> [範例] \> [零售分析範例] \> [連接]。 

1. 從此儀表板，選取 [所有門市] 磚，開啟 [零售分析範例] 報表。
2. 選取 [編輯報表]  ，在編輯檢視中開啟報表。
3. [加入新的報表頁面](power-bi-report-add-page.md)。
4. 建立依類別顯示今年度銷售量的環圈圖。
   
   * 從 **欄位** 窗格中，選取 **銷售額**\> **去年度銷售額**。
   * 轉換成環圈圖。 如果 [值]  區域中沒有 [去年度銷售額]，請將其拖曳到該區域。
     
       ![](media/power-bi-visualization-doughnut-charts/convertdonut.png)
   * 選取 [項目] \> [類別]，將其加入 [圖例] 區域。 
     
       ![](media/power-bi-visualization-doughnut-charts/doughnuttutorial.png)

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
* 環圈圖圖表值的總和必須達 100%。
* 太多的類別讓您難以讀取和解譯。
* 環圈圖最適合用來比較特定部分與整體，而不是在個別部分彼此之間比較。 

## <a name="next-steps"></a>後續步驟
[Power BI 中的報表](service-reports.md)

[Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI 報表的視覺效果](power-bi-report-visualizations.md)

[Power BI - 基本概念](service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

