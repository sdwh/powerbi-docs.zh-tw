---
title: "Power BI 中的交叉分析篩選器 (教學課程)"
description: "教學課程：Power BI 中的交叉分析篩選器"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: zIZPA0UrJyA
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/30/2017
ms.author: mihart
ms.openlocfilehash: b6ce0c396f4a189489b97fe5cd86ab5cd8dbcc35
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="slicers-in-power-bi-service-tutorial"></a>Power BI 服務中的交叉分析篩選器 (教學課程)
您的銷售副總裁希望能夠查看整個部門和各分區經理的多項指標。 她可以為每個經理分別建立報表頁面，或者可以使用交叉分析篩選器。 交叉分析篩選器會縮小頁面上其他視覺效果中顯示的資料集部分。  交叉分析篩選器是篩選的替代方式。

![](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>使用交叉分析篩選器的時機
交叉分析篩選器在下列情況中是絕佳選擇。

* 在報表畫布上顯示常用或重要篩選，以方便存取。
* 讓您不需要開啟下拉式清單尋找篩選詳細資料，即可輕鬆查看目前篩選的狀態。
* 如果您想隱藏不需要但仍可用以篩選的資料列，這能讓資料表變得更簡潔、清楚。
* 建立更容易聚焦的報表 - 由於交叉分析篩選器是浮動物件，您可以將其放在報表上精彩部分的旁邊，引導您的使用者聚焦於此。

## <a name="create-a-slicer"></a>建立交叉分析篩選器
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>


1. 在[編輯檢視](service-interact-with-a-report-in-editing-view.md)中開啟[零售分析範例](sample-retail-analysis.md)，然後[新的報表頁面](power-bi-report-add-page.md)。
2. 從 [欄位] 窗格中選取 [區域] > [區域經理]。
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_chartfirst.png)
3. 將視覺效果轉換成交叉分析篩選器。 在 [視覺效果] 窗格中選取交叉分析篩選器圖示。
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_select.png)

## <a name="format-the-slicer"></a>設定交叉分析篩選器的格式
1. 在已選取交叉分析篩選器的情況下，在 [視覺效果] 窗格中選取滾筒刷圖示 ![](media/power-bi-visualization-slicers/power-bi-paintroller.png)，以顯示 [格式] 選項。
2. 選取 [一般] > [外框色彩]，然後選擇深藍色，並將 [寬度] 變更為 **6**。
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_outline2.png)
3. 在 [選取控制項] 下，[全選]  預設為 [關閉]  ，而 [單選]  預設為 [開啟] 。 這表示必須使用 CTRL 鍵才能同時選取多個名稱。 請將 [全選]  改成 [開啟]  ，[單選]  改成 [關閉] 。
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_selectioncontrols2.png)
   
   * 請注意，交叉分析篩選器的清單頂端現在出現了 [全選]  選項。 切換 [全選]  以選取所有名稱，或不選取任何名稱。
   * 而且您現在不需要使用 CTRL 鍵，就可以選取多個名稱。
4. 在 [項目] 下，將文字大小放大到 14 pt。  我們想要確保同事注意到此交叉分析篩選器。
5. 最後，將 [字型色彩]  設為深紅色。  這樣就能從交叉分析篩選器中未選取的名稱，將已選取的名稱區別出來。
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_font2.png)
6. 好好探索交叉分析篩選器適用的其他選項吧。

## <a name="use-the-slicer-in-a-report"></a>在報表中使用交叉分析篩選器
1. 將其他幾個視覺效果新增至報表頁面，或開啟[零售分析範例報表](sample-retail-analysis.md)並選取 [區域每月銷售額] 索引標籤。
   
    ![](media/power-bi-visualization-slicers/power-bi-retail-sample.png)
2. 切割 Carlos 的報表頁面。 請注意其他視覺效果如何更新以反映這些選取項目。
   
    ![](media/power-bi-visualization-slicers/slicer2.gif)
3. 依照區域經理的姓氏，以字母順序來排序交叉分析篩選器。  選取交叉分析篩選器右上角的省略符號 (...)，然後選擇 [區域經理] 。
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sort2.png)
   
    ![](media/power-bi-visualization-slicers/pbi_slicer_sorted.png)

## <a name="control-what-effect-the-slicer-has-on-other-visuals-on-the-page"></a>控制交叉分析篩選器對頁面上其他視覺效果的作用
您想要讓交叉分析篩選器只篩選報表頁面上的某些視覺效果嗎？  使用 [視覺效果互動] 控制項可對此進行設定。

**注意**：如果您沒有看到 [視覺效果互動]，請改為尋找其圖示 ![](media/power-bi-visualization-slicers/power-bi-slicer-visual-interactions.png)。 如果兩者都沒看到，請確認您已進入報表[編輯檢視](service-reading-view-and-editing-view.md)。

1. 選取 [交叉分析篩選器] 加以啟動，並從功能表列選擇 [視覺效果互動]。
   
    ![](media/power-bi-visualization-slicers/pbi-slicer-interactions.png)
2. 篩選控制項會出現在頁面上其他所有視覺效果的上方。 如果交叉分析篩選器應篩選某個視覺效果，請選取 [篩選] 圖示。  如果交叉分析篩選器不應對該視覺效果產生任何作用，請選取 [無] 圖示。
   
    ![](media/power-bi-visualization-slicers/filter-controls.png)

如需詳細資訊，請參閱[在 Power BI 報表中與視覺效果互動](service-reports-visual-interactions.md)。

## <a name="considerations-and-troubleshooting-slicers-in-power-bi"></a>Power BI 中的考量和對交叉分析篩選器進行疑難排解
在 Power BI 中使用交叉分析篩選器有以下限制︰

1. 交叉分析篩選器不支援輸入欄位。
2. 單一的交叉分析篩選器無法用於整份報表。 交叉分析篩選器只會影響目前的頁面。
3. 交叉分析篩選器無法釘選到儀表板。
4. 交叉分析篩選器不支援向下鑽研。    
5. 交叉分析篩選器不支援視覺效果等級篩選。

您對如何改進 Power BI 有任何想法嗎？ [送出想法](https://ideas.powerbi.com/forums/265200-power-bi-ideas)。

## <a name="next-steps"></a>後續步驟
 [將視覺效果新增至報表](power-bi-report-add-visualizations-i.md)

 [Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)

 [Power BI - 基本概念](service-basic-concepts.md)

[請試用 - 完全免費！](https://powerbi.com/)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

