---
title: "基本區域圖 (教學課程)"
description: "教學課程：基本區域圖。"
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
ms.openlocfilehash: 42e068b11c22c32f1a6736a6ca8f9020594fb40a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="basic-area-chart-tutorial"></a>基本區域圖 (教學課程)
基本區域圖 (也稱為多層次區域圖表) 的基礎為折線圖。 軸和行之間的區域填滿色彩，以表示數量。 

區域圖強調隨著時間的變化大小，而且可用來強調跨趨勢的總計值。 例如，代表收益隨時間變化的資料，可以在區域圖中繪製，藉此強調總收益。

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>使用基本區域圖的時機
基本區域圖極適合：

* 如果您要查看和比較時間序列中的數量趨勢 
* 如果個別數列代表實質上可數的集合

## <a name="create-a-basic-area-chart"></a>建立基本區域圖
如果要跟著做，請登入 Power BI 並選取 [取得資料] \> [範例] \> [零售分析範例]。 

1. 從 [零售分析範例] 儀表板，選取 [所有門市]  圖格，開啟 [零售分析範例] 報表。
2. 選取 [編輯報表]  ，在編輯檢視中開啟報表。
3. 加入新的報表頁面。
4. 建立依月份顯示本年度和去年度銷售額的區域圖。
   
   a.  從 [欄位] 窗格中選取 [銷售額] \> [This Year Sales] (去年度銷售額)，以及 [This Year Sales > Value] (本年度銷售額 > 值)。
   
   b.  將圖表轉換成基本區域圖。    
   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  選取 [時間] \> [月] 以將它加入 [軸] 部分。   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  若要依照月份顯示圖表，請選取省略符號 \(視覺效果的右上角)，並選擇 \[Sort by month] \(按月份排序)。

## <a name="highlighting-and-cross-filtering"></a>反白顯示和交叉篩選
如需使用 [篩選] 窗格的資訊，請參閱[將篩選加入報表](power-bi-report-add-filter.md)。

若要選取一個區域，請按一下該區域的內部或頂端線條。  基本區域圖不會交叉篩選報表頁面上的其他視覺效果。 不過，對報表頁面上的其他視覺效果來說，區域圖是觸發交叉篩選的目標。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
* 基本區域圖不適用於比較值，原因是多層次區域會受阻擋。 Power BI 使用透明效果來表示重疊的區域。 不過，它只適用於兩個或三個不同的區域。 當您需要比較三個以上量值的趨勢時，請試著使用折線圖。 當您需要比較三個以上量值的數量時，請試著使用樹狀圖。

## <a name="next-steps"></a>後續步驟
[Power BI 中的報表](service-reports.md)  
[Power BI 報表的視覺效果](power-bi-report-visualizations.md)  
[Power BI - 基本概念](service-basic-concepts.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

