---
title: 第 1 部分：在 Power BI 報表中新增視覺效果
description: 第 1 部分：在 Power BI 報表中新增視覺效果
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299309"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>第 1 部分：在 Power BI 報表中新增視覺效果

本文提供在報表中建立視覺效果的快速簡介。 它適用於 Power BI 服務和 Power BI Desktop。 如需更進階的內容，[請參閱本系列的第 2 部分](power-bi-report-add-visualizations-ii.md)。 觀看 Amanda 示範數種不同方式，以在報表畫布上建立、編輯和格式化視覺效果。 接著，自己試著使用[銷售和行銷範例](../sample-datasets.md)來建立專屬報表。

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>開啟報表並新增頁面

1. [在 [編輯檢視] 中開啟報表](../service-interact-with-a-report-in-editing-view.md)。

    本教學課程使用[銷售與行銷範例](../sample-datasets.md)。

1. 如果看不到 [欄位]  窗格，請選取箭號圖示予以開啟。

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. 在報表中新增空白頁面。

## <a name="add-visualizations-to-the-report"></a>將視覺效果新增至報表

1. 從 [欄位]  窗格選取欄位來建立視覺效果。

    從數值欄位開始，像是 [銷售事實]   > [銷售額]  。 Power BI 會建立具有單一直條的直條圖。

    ![具有單一直條的直條圖螢幕擷取畫面。](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    或是以類別欄位開始，例如 [名稱]  或 [產品]  。 Power BI 會建立資料表，並將該欄位新增至 [值]  區。

    ![GIF 顯示人員先選取 [產品]，然後選取類別目錄來建立資料表。](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    或從地理位置欄位開始，例如 [地理位置]   > [城市]  。 Power BI 與 Bing 地圖服務會建立地圖視覺效果。

    ![地圖視覺效果的螢幕擷取畫面。](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. 建立視覺效果，然後變更其類型。 選取 [產品]   > [類別]  ，然後選取 [產品]   > [產品計數]  ，將兩者新增至 [值]  區。

   ![[欄位] 窗格的螢幕擷取畫面，[值] 區也已標示。](media/power-bi-report-add-visualizations-i/part1table1.png)

1. 選取**堆疊直條圖**圖示將視覺效果變更為直條圖。

   ![標示堆疊直條圖圖示的 [視覺效果] 窗格螢幕擷取畫面。](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. 當您在報表中建立視覺效果時，您可以[把它們釘選至儀表板](../service-dashboard-pin-tile-from-report.md)。 若要釘選視覺效果，請選取釘選圖示![釘選圖示的螢幕擷取畫面](media/power-bi-report-add-visualizations-i/pinnooutline.png)。

   ![標示釘選圖示的資料行圖表視覺效果螢幕擷取畫面。](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>後續步驟

 繼續前往：

* [第 2 部分：在 Power BI 報表中加入視覺效果](power-bi-report-add-visualizations-ii.md)

* 在報表中[與視覺效果互動](../consumer/end-user-reading-view.md)。

* [執行更多的視覺效果](power-bi-report-visualizations.md)。

* [儲存報表](../service-report-save.md)。
