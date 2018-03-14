---
title: "檢視 Power BI 服務中的相關內容"
description: "瀏覽變得更容易，檢視儀表板、報表及資料集中的相關內容"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: B2vd4MQrz4M
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/01/2018
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 43dffab862173779068f1180f83bc6c92bf98013
ms.sourcegitcommit: 0a16dc12bb2d39c19e6b0002b673a8c1d81319c9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2018
---
# <a name="view-related-content-in-power-bi-service"></a>檢視 Power BI 服務中的相關內容
[相關內容] 窗格會顯示您的 Power BI 服務內容 (儀表板、報表及資料集) 如何互連。  這個窗格經過了改良，讓您可以從中執行重新整理、重新命名、產生深入資訊等常用工作。 選取相關報表或儀表板，其隨即在您的 Power BI 工作區中開啟。   

您可能已經發現，報表以資料集為基礎、報表視覺效果接著會釘選到儀表板，而儀表板視覺效果會連回報表。 但您要如何知道，哪些儀表板裝載了來自「行銷」報表的視覺效果？ 要怎麼找到那些儀表板？ 您的「採購」儀表板有沒有使用來自多個資料集的視覺效果？ 如果有，儀表板名稱為何、如何加以開啟和編輯？ 您的 HR 資料集有沒有用在任何報表或資料集，該資料集是否能在不造成任何連結中斷的情況下移動？ 在 [相關內容] 窗格，這類問題都能獲得解答。  該窗格不僅顯示相關內容，還能讓您對內容採取動作，並在相關內容之間輕鬆瀏覽。

![相關內容](media/service-related-content/power-bi-view-related-dashboard-new.png)

> [!NOTE]
> [相關內容] 功能不適用於串流資料集。
> 
> 

## <a name="view-related-content-for-a-dashboard"></a>檢視儀表板相關內容
觀看 Will 檢視儀表板相關內容。 然後遵循影片下方的逐步指示，使用「採購分析」範例資料集親自試試看。

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M#t=3m05s" frameborder="0" allowfullscreen></iframe>


您至少必須有儀表板的「檢視」權限，才能開啟 [相關內容] 窗格。 在本例中，我們使用的是[採購分析範例](sample-procurement.md)。

**方法 1**

在工作區中選取 [儀表板] 索引標籤，然後選取**檢視相關項目**圖示 ![檢視相關項目圖示](media/service-related-content/power-bi-view-related-icon-new.png)。

![[儀表板] 索引標籤](media/service-related-content/power-bi-view-related-dash-newer.png)

<br>

**方法 2**

在儀表板開啟的情況下，從頂端功能表列選取   ![檢視相關項目圖示](media/service-related-content/power-bi-view-related-new.png) 。

[相關內容] 窗格隨即開啟。 其中會顯示有視覺效果釘選到儀表板的所有報表，及其相關聯的資料集。 這個儀表板釘選了來自 3 個不同報表的視覺效果，而這些報表以 3 個不同資料集為基礎。

![[相關內容] 窗格](media/service-related-content/power-bi-view-related-dashboard-new.png)

您可以從這裡直接對相關內容採取動作。  例如選取報表名稱加以開啟。  若是列出的報表，選取圖示即可[使用 Excecl 分析](service-analyze-in-excel.md)、[重新命名](service-rename.md)或[取得深入資訊](service-insights.md)。 若是資料集，選取圖示即可[建立新報表](service-report-create-new.md)、[重新整理](refresh-data.md)、重新命名、[在 Excel 中分析](service-analyze-in-excel.md)、[取得深入資訊](service-insights.md)或開啟資料集的 [設定] 視窗。  

## <a name="view-related-content-for-a-report"></a>檢視報表相關內容
您至少必須有報表的「檢視」權限，才能開啟 [相關內容] 窗格。 在本例中，我們使用的是[採購分析範例](sample-procurement.md)。

**方法 1**

在工作區中選取 [報表] 索引標籤，然後選取**檢視相關項目**圖示 ![檢視相關項目圖示](media/service-related-content/power-bi-view-related-icon-new.png)。

![[報表] 索引標籤](media/service-related-content/power-bi-view-related-report-newer.png)

<br>

**方法 2**

在[閱讀檢視](service-reading-view-and-editing-view.md)中開啟報表，然後從頂端功能表列選取![檢視相關項目圖示](media/service-related-content/power-bi-view-related-new.png)。

[相關內容] 窗格隨即開啟。 其中顯示已建立關聯的資料集，以及至少從該報表釘選了一個磚的所有儀表板。 這份報表有釘選到 2 個不同儀表板的視覺效果。

![[相關內容] 窗格](media/service-related-content/power-bi-view-related-report.png)

您可以從這裡直接對相關內容採取動作。  例如選取儀表板名稱加以開啟。  若是清單中的儀表板，選取圖示即可[與他人共用儀表板](service-share-dashboards.md)，或開啟儀表板的 [設定] 視窗。 若是資料集，選取圖示即可[建立新報表](service-report-create-new.md)、[重新整理](refresh-data.md)、重新命名、[在 Excel 中分析](service-analyze-in-excel.md)、[取得深入資訊](service-insights.md)或開啟資料集的 [設定] 視窗。  

## <a name="view-related-content-for-a-dataset"></a>檢視資料集相關內容
您至少必須有資料集的「檢視」權限，才能開啟 [相關內容] 窗格。 在本例中，我們使用的是[採購分析範例](sample-procurement.md)。

在工作區中選取 [資料集] 索引標籤，然後找出**檢視相關項目**圖示 ![檢視相關項目圖示](media/service-related-content/power-bi-view-related-icon-new.png)。

![[資料集] 索引標籤](media/service-related-content/power-bi-view-related-dataset-newer.png)

選取圖示以開啟 [相關內容] 窗格。

![](media/service-related-content/power-bi-datasets.png)

您可以從這裡直接對相關內容採取動作。  例如選取儀表板或報表名稱加以開啟。  若是清單中的儀表板，選取圖示即可[與他人共用儀表板](service-share-dashboards.md)，或開啟儀表板的 [設定] 視窗。 若是報表，選取圖示即可[使用 Excecl 分析](service-analyze-in-excel.md)、[重新命名](service-rename.md)或[取得深入資訊](service-insights.md)。  

## <a name="limitations-and-troubleshooting"></a>限制與疑難排解
* 如果您的瀏覽器空間不足，就不會看到 [檢視相關項目] 的選項，但還是會看到檢視相關項目圖示 ![檢視相關項目圖示](media/service-related-content/power-bi-view-related-icon-new.png)。 選取圖示以開啟 [相關內容] 窗格。
* 若要開啟報表的 [相關內容]，必須使用[閱讀檢視](service-reading-view-and-editing-view.md)。
* 在 Power BI Desktop 中無法使用 [相關內容]。
* [相關內容] 功能不適用於串流資料集。

## <a name="next-steps"></a>後續步驟
* [開始使用 Power BI 服務](service-get-started.md)
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

