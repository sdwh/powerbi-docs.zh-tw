---
title: Power BI 中的環圈圖
description: Power BI 中的環圈圖
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0e870163552e64594e574669ed8dea6937633282
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "75757707"
---
# <a name="create-and-use-doughnut-charts-in-power-bi"></a>在 Power BI 中建立和使用環圈圖

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

環圈圖類似於圓形圖之處，在於它會顯示部分與整體的關聯性。 唯一的差別在於，中央為空白，且保留空間給標籤或圖示。

## <a name="prerequisite"></a>必要條件

本教學課程使用[零售分析範例 PBIX 檔案](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)。

1. 從功能表列的左上方區段中，選取 [檔案]   > [開啟] 
   
2. 尋找您的**零售分析範例 PBIX 檔案**複本

1. 在報表檢視 **報表檢視圖示的螢幕擷取畫面** 中開啟![零售分析範例 PBIX 檔案](media/power-bi-visualization-kpi/power-bi-report-view.png)。

1. Select ![黃色索引標籤的螢幕擷取畫面。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) 新增頁面。


## <a name="create-a-doughnut-chart"></a>建立環圈圖

1. 從空白報表頁面開始，並從 [欄位] 窗格中選取 [銷售額]  \>[去年度銷售額]  。  
   
3. 從 [視覺效果] 窗格中，選取環圈圖的圖示 ![環圈圖圖示](media/power-bi-visualization-doughnut-charts/power-bi-icon.png)，以將橫條圖轉換成環圈圖。 如果 [值]  區域中沒有 [去年度銷售額]  ，請將其拖曳到該區域。
     
   ![已選取環圈圖的 [視覺效果] 窗格](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. 選取 [項目]  \> [類別]  ，將其新增至 [圖例]  區域。 
     
    ![[欄位] 窗格旁邊的環圈圖](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. 選擇性地[調整圖表文字的大小和色彩](power-bi-visualization-customize-title-background-and-legend.md)。 

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
* 環圈圖圖表值的總和必須達 100%。
* 太多的類別讓您難以讀取和解譯。
* 環圈圖最適合用來比較特定部分與整體，而不是在個別部分彼此之間比較。 

## <a name="next-steps"></a>後續步驟
[Power BI 中的漏斗圖](power-bi-visualization-funnel-charts.md)

[Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)


