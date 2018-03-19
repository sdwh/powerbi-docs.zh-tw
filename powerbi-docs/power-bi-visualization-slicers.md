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
ms.date: 03/05/2018
ms.author: v-thepet
LocalizationGroup: Visualizations
ms.openlocfilehash: cfa4c0f17c67a036b7d01744da1b5247345c493a
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="slicers-in-power-bi-tutorial"></a>Power BI 中的交叉分析篩選器 (教學課程)
銷售副總裁希望能夠查看整個部門和各分區經理的多項指標。 其可以為每位經理分別建立報表，或者可以使用交叉分析篩選器。 交叉分析篩選器會縮小報表中其他視覺效果中顯示的資料集部分。 交叉分析篩選器是篩選的替代方式。

本教學課程使用免費的[零售分析範例](sample-retail-analysis.md)，逐步引導您建立及格式化交叉分析篩選器並使用它來篩選報表。 享受探索格式化及使用交叉分析篩選器的樂趣。 

![交叉分析篩選器](media/power-bi-visualization-slicers/slicer2.gif)

## <a name="when-to-use-a-slicer"></a>使用交叉分析篩選器的時機
當您想要執行下列作業時，交叉分析篩選器是很棒的選擇：

* 在報表畫布上顯示常用或重要篩選，以方便存取。
* 不需要開啟下拉式清單，即可輕鬆查看目前篩選的狀態。 
* 依資料行篩選不必要的資料，並隱藏在資料表中。
* 將交叉分析篩選器放在重要的視覺效果旁邊，以建立更多重點報表。

Power BI 交叉分析篩選器具有下列限制：

- 交叉分析篩選器不支援輸入欄位。
- 交叉分析篩選器無法釘選到儀表板。
- 交叉分析篩選器不支援向下鑽研。
- 交叉分析篩選器不支援視覺效果等級篩選。

## <a name="create-a-slicer"></a>建立交叉分析篩選器

本教學課程會使用清單交叉分析篩選器。 數值和日期/時間資料類型可以有範圍交叉分析篩選器。 如需建立及使用範圍交叉分析篩選器的詳細資訊，請參閱[在 Power BI Desktop 中使用數字範圍交叉分析篩選器](desktop-slicer-numeric-range.md)或下列影片。
<iframe width="560" height="315" src="https://www.youtube.com/embed/zIZPA0UrJyA" frameborder="0" allowfullscreen></iframe>

1. 在 Power BI Desktop 或 Power BI 服務 中，開啟 [編輯檢視](service-interact-with-a-report-in-editing-view.md) 的 [零售分析範例](sample-retail-analysis.md)，然後[新增報表頁面](power-bi-report-add-page.md)。
2. 從 [欄位] 窗格的 [行政區] 中，選取 [District Manager] (區經理) 來建立新的視覺效果。
    
    ![新圖表](media/power-bi-visualization-slicers/1-new-vis.png)
    
3. 在 [視覺效果] 窗格中選取**交叉分析篩選器**圖示![交叉分析篩選器圖示](media/power-bi-visualization-slicers/slicer-icon.png)，將新的視覺效果轉換成交叉分析篩選器。 
    
    ![轉換成交叉分析篩選器](media/power-bi-visualization-slicers/2-slicer.png)

您也可以選取交叉分析篩選器圖示來建立新的交叉分析篩選器，然後選取資料欄位或將它拖曳到 [欄位] 方塊來填入它。

>[!TIP]
>您可以按資料值排序清單交叉分析篩選器項目。 若要依字母反向順序排序交叉分析篩選器項目，請選取交叉分析篩選器右上角的省略符號 (...)，選擇 [Sort by District Manager] (依區經理排序)。 此設定預設為依字母序排列，但可切換正向和反向。 

## <a name="format-the-slicer"></a>設定交叉分析篩選器的格式
將視覺效果格式套用至區經理交叉分析篩選器。
1. 在已選取交叉分析篩選器的情況下，在 [視覺效果] 窗格中選取格式圖示 ![](media/power-bi-visualization-slicers/power-bi-paintroller.png)，以顯示格式化控制項。 
    
    ![格式化](media/power-bi-visualization-slicers/3-format.png)
    
2. 按一下每個類別旁的下拉式清單箭頭來顯示和編輯選項。 

### <a name="general-options"></a>一般選項
1. 在 [外框色彩] 下選取紅色，並將 [外框寬度] 變更為 "2"。 這會在啟用時，設定標頭和項目外框或底線的色彩和粗細。 
2. 在 [方向] 下，[垂直] 是預設值，會建立項目前面有選取方塊的垂直清單交叉分析篩選器。 選取 [水平] 會產生以水平方式排列項目的交叉分析篩選器。 水平方向可以產生文字、按鈕或磚的各種排列方式，視交叉分析篩選器的大小和形狀以及項目格式化而定。 
    
    ![水平](media/power-bi-visualization-slicers/4-horizontal.png)
    
3. 開啟 [回應式] 版面配置，這會變更水平交叉分析篩選器項目的大小和排列方式，以符合交叉分析篩選器的大小和形狀。 在非常小的大小時，交叉分析篩選器會變成篩選圖示。 
    
    ![回應式](media/power-bi-visualization-slicers/5-responsive.png)
    
    >[!NOTE]
    >回應式配置變更可能會覆寫您設定的特定標題和項目格式。 
    
4. 使用 [X 位置]、[Y 位置]、[寬度] 和 [高度] 下的數值有效位數設定交叉分析篩選器的位置和大小，或直接在畫布上移動交叉分析篩選器和調整其大小，產生不同的項目大小和排列方式，例如水平列按鈕。 

    ![水平按鈕](media/power-bi-visualization-slicers/6-buttons.png)

如需水平方向與回應式格式的詳細資訊，請參閱[在 Power BI 中建立可以調整大小的回應式交叉分析篩選器](power-bi-slicer-filter-responsive.md)。

### <a name="selection-controls-options"></a>選取控制項選項
1. 預設顯示 [全選] 為 [關閉]。 將其切換為 [開啟]，以將 [全選] 項目新增至交叉分析篩選器，切換選取或取消選取所有項目。 當選取所有項目時，按一下一個項目會取消選取它並允許 "is-not"-type 篩選條件。 
    
    ![全選](media/power-bi-visualization-slicers/7-select-all.png)
    
2. [單一選取] 預設為 [開啟]。 按一下每個項目會選取它，按住 CTRL 鍵同時按一下可選取多個項目。 將 [單一選取] 切換為 [關閉]，不按住 CTRL 鍵就可以選取多個項目。 再按一下每個項目會取消選取它。 

### <a name="header-options"></a>標頭選項
標頭預設為 [開啟]，在交叉分析篩選器上方顯示資料欄位名稱。 
1. 將標頭文字格式化為 [字型色彩] 為紅色、[文字大小] 為 14 pt 和 [字型家族] 為 Arial Black。 
2. 在 [外框] 下，選擇 [僅底端]，以您在 [一般] 選項下設定的大小和色彩產生底線。 

### <a name="item-options"></a>項目選項
1. 將項目文字和背景格式化為 [字型色彩] 為黑色、[背景] 為淺紅色、[文字大小] 為 10 pt 和 [字型家族]  為 Arial。 
2. 在 [外框] 下選擇 [框架] ，使用您在 [一般] 選項中設定的大小和色彩繪製每個項目的外框。 
    
    ![格式化](media/power-bi-visualization-slicers/8-formatted.png)
    
    >[!TIP]
    >- 使用 [Horizontal Orientation] (水平方向)，取消選取的項目會顯示所選文字和背景色彩，而選取的項目則使用系統預設值，通常是黑色背景搭配白色文字。 
    >- 使用 [Vertical Orientation] (垂直方向)，項目一律顯示設定的色彩，選項方塊在選取時也一律為黑色。 

### <a name="other-formatting-options"></a>其他格式化選項
其他格式化選項預設關閉。 轉換為 [開啟] 時： 
- **標題：**在交叉分析篩選器的上方新增並格式化標題 (除標頭外，且不受標頭影響)。 
- **背景：**新增整體交叉分析篩選器的背景色彩，並設定其透明度。
- **鎖定長寬：**如果調整大小，保留交叉分析篩選器的形狀。
- **框線：**新增交叉分析篩選器的 1 像素框線，並設定其色彩。 (此交叉分析篩選器框線和 [General Outline] (一般外框) 設定不同，不受其影響。) 

## <a name="sync-and-use-the-slicer-on-other-pages"></a>同步處理交叉分析篩選器並在其他網頁上使用它
從 2018 年 2 月版的 Power BI 更新開始，您可以同步交叉分析篩選器並在報表的任何或所有頁面上使用它。 
1. 在 [檢視] 功能表上選取區經理交叉分析篩選器後，請選取 Power BI Desktop 的 [同步交叉分析篩選器] 或開啟 Power BI 服務的 [同步交叉分析篩選器] 窗格。 [同步交叉分析篩選器] 窗格隨即出現。 
    
    ![同步交叉分析篩選器](media/power-bi-visualization-slicers/9-sync-slicers.png)
    
2. 在第一個資料行中，選取 [概觀] 以及您想要交叉分析篩選器同步處理的任何其他頁面，或按一下 [Add to all] (新增至全部) 讓交叉分析篩選器同步處理所有的報表頁面。  
3. 在下一個資料行中，選取 [概觀] 以及您希望顯示交叉分析篩選器的任何其他頁面。 
4. 切換至 [概觀] 頁面，記下交叉分析篩選器和它對其他頁面視覺效果的影響。 
    - 建立與移除不同的項目選取項目，並注意頁面上的其他視覺效果如何隨之變更。 任何頁面上的項目選取項目都會反映所有經過同步處理的頁面。
    - 變更 [概觀] 頁面上交叉分析篩選器的大小、圖形、位置及/或格式化。 其他經過同步處理頁面上的交叉分析篩選器格式不會變更。 

### <a name="control-which-page-visuals-are-affected-by-the-slicer"></a>控制受交叉分析篩選器影響的頁面視覺效果
根據預設，報表頁面上的交叉分析篩選器會影響該頁面的所有其他視覺效果。 使用 [視覺互動] 防止某些頁面的視覺效果受到影響。

1. 在 [概觀] 頁面上，利用選取的交叉分析篩選器：
    - 在 Power BI Desktop 中，按一下 [視覺效果工具] 下的 [格式] 功能表，然後選取 [編輯互動]。
    - 在 Power BI 服務中，從功能表列向下拉開 [視覺互動] 並開啟 [編輯互動]。 
    
    篩選控制項會出現在頁面上其他所有視覺效果的上方。 ![篩選控制項](media/power-bi-visualization-slicers/filter-controls.png)
    
2. 選取視覺效果上方的**無**圖示，讓篩選交叉分析篩選器停止篩選它。 選取**篩選**圖示，讓交叉分析篩選器再次開始篩選視覺效果。 

如需編輯互動的詳細資訊，請參閱 [Power BI 報表中的視覺互動](service-reports-visual-interactions.md)。

## <a name="next-steps"></a>後續步驟
[請試用 - 完全免費！](https://powerbi.com/)

您對如何改進 Power BI 有任何想法嗎？ [送出想法](https://ideas.powerbi.com/forums/265200-power-bi-ideas)。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

[將視覺效果新增至報表](power-bi-report-add-visualizations-i.md)

[Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Power BI - 基本概念](service-basic-concepts.md)

