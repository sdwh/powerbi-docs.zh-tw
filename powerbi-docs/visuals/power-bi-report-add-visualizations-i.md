---
title: 第 1 部分：在 Power BI 報表中新增視覺效果
description: 第 1 部分：在 Power BI 報表中新增視覺效果
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: f2edbd7b0b977b378d25634a0f9505101350d73b
ms.sourcegitcommit: e17fc3816d6ae403414cf5357afbf6a492822ab8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829795"
---
# <a name="part-i-add-visualizations-to-a-power-bi-report"></a>第 1 部分：在 Power BI 報表中新增視覺效果
此文章提供在報表中使用 Power BI 服務或 Power BI Desktop 建立視覺效果的快速簡介。  如需更進一步的內容，請[參閱第二部分](power-bi-report-add-visualizations-ii.md)。 觀看 Amanda 示範數種不同方式，以在報表畫布上建立、編輯和格式化視覺效果。 接著，自己試著使用[銷售和行銷範例](../sample-datasets.md)來建立專屬報表。

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>開啟報表並新增頁面
1. [在 [編輯檢視] 中開啟報表](../consumer/end-user-reading-view.md)。 此教學課程使用[銷售與行銷範例](../sample-datasets.md)。
2. 如果看不到 [欄位] 窗格，請選取箭號圖示開啟它。 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. 在報表中新增空白頁面。

## <a name="add-visualizations-to-the-report"></a>將視覺效果新增至報表
1. 從 [欄位]  窗格選取欄位來建立視覺效果。  
   
   **從數值欄位開始**，像是 [銷售事實] > [銷售額]。 Power BI 會建立具有單一直條的直條圖。
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **或從類別欄位開始**，例如 [名稱] 或 [產品]：Power BI 會建立資料表，並將該欄位新增到 [值]。
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   **或從地理位置欄位開始**，例如 [地理位置] > [城市]。 Power BI 與 Bing 地圖服務會建立地圖視覺效果。
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. 建立視覺效果，然後變更其類型。 選取 [產品] > [類別]，然後選取 [產品] > [產品計數]，以將兩者新增至 [值]。
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. 選取直條圖圖示將視覺效果變更為直條圖。
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. 當您在報表中建立視覺效果時，您可以[把它們釘選至儀表板](../service-dashboard-pin-tile-from-report.md)。 若要釘選視覺效果，請選取釘選圖示 ![](media/power-bi-report-add-visualizations-i/pinnooutline.png)。
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
  

## <a name="next-steps"></a>後續步驟
 繼續[第 2 部分：在 Power BI 報表中加入視覺效果](power-bi-report-add-visualizations-ii.md)
   
   在報表中[與視覺效果互動](../consumer/end-user-reading-view.md)。
   
   [執行更多的視覺效果](power-bi-report-visualizations.md)。
   
   [儲存報表](../service-report-save.md)。
