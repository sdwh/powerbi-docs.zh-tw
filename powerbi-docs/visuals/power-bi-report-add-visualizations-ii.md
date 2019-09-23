---
title: 第 2 部分：在 Power BI 報表中新增視覺效果
description: 第 2 部分：在 Power BI 報表中新增視覺效果
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c42d96fea37a6309908dd357425c3d0504e18397
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61410083"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>第 2 部分：在 Power BI 報表中新增視覺效果
在[第 1 部分](power-bi-report-add-visualizations-ii.md)，您選取了欄位名稱旁邊的核取方塊來建立基本的視覺效果。  在第 2 部分，您會學習如何使用拖放及充分利用 [欄位]  和 [視覺效果]  窗格來建立和修改視覺效果。

### <a name="prerequisites"></a>先決條件
- [第 1 部分](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop - 使用 Power BI 服務或 Power BI Desktop 能將視覺效果新增至報表。 此教學課程使用 Power BI Desktop。 
- [零售分析範例](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>建立新的視覺效果
本教學課程中，我們要深入探討零售分析資料集，並建立幾個重要的視覺效果。

### <a name="open-a-report-and-add-a-new-blank-page"></a>開啟報表並加入新的空白頁面。
1. 在 Power BI Desktop 中開啟零售分析範例 .PBIX 檔案。 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2. 選取畫布底部的黃色加號圖示以新增頁面。

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>加入視覺效果，查看本年度與去年度的比較銷售額。
1. 從 [銷售]  資料表中選取 [本年度銷售額]   >  [值]  和 [去年度銷售額]  。 Power BI 建立了直條圖。  這個有點意思，而您想要更進一步探討。 每月的銷售額又會是如何呢？  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. 從 [時間]資料表中將 [會計月份]  拖曳到 [軸]  區域。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [將視覺效果變更](power-bi-report-change-visualization-type.md)為區域圖。  有許多視覺效果類型可從中選擇，請參閱[其中各項說明、最佳做法的秘訣和教學課程](power-bi-visualization-types-for-reports-and-q-and-a.md)，協助您決定要使用哪種類型。 從 [視覺效果] 窗格中選取區域圖圖示 ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png)。
4. 選取省略符號，然後選擇 [依會計月份排序]  ，來排序視覺效果。
5. 選取視覺效果、抓取一個圓形外框，然後拖曳以[調整視覺效果大小](power-bi-visualization-move-and-resize.md)。 讓它寬到消除捲軸，但提供足夠的空間以新增另一個視覺效果。
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [儲存報表](../service-report-save.md)。

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>加入地圖視覺效果來依位置查看銷售
1. 從 [門市]  資料表中選取 [領域]  。 Power BI 能夠辨識「領域」是一個位置，並建立地圖視覺效果。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. 將 [門市總額]  拖曳到 [大小] 區域。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. 加入圖例。  若要依門市名稱查看資料，請將 [連鎖店]  拖曳到 [圖例] 區域。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>後續步驟
* 深入了解 [Power BI 報表中的視覺效果](power-bi-report-visualizations.md)。  
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

