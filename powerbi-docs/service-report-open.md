---
title: 在 Power BI 中，以 [閱讀檢視] 或 [編輯檢視] 開啟報表
description: 以閱讀檢視或編輯檢視來開啟 Power BI 報表
services: powerbi
documentationcenter: ''
author: mihart
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/01/2018
ms.author: mihart
ms.openlocfilehash: 17921d1fe28a1b4c0640748123efe4b70982b18d
ms.sourcegitcommit: ae4d771b883b654358a6a94dd784ea9bdf3d3aa3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="open-a-report-in-power-bi-service-apppowerbicom"></a>在 Power BI 服務 (app.powerbi.com) 中開啟報表
報表提供於 Power BI 服務、Power BI Desktop、Power BI Mobile，甚至是 Power BI Embedded。 本文適用於在 ***Power BI 服務***中開啟報表。

在 Power BI 服務中，有兩種模式可與報表互動：[閱讀檢視和編輯檢視](service-reading-view-and-editing-view.md)。 [閱讀檢視] 適用於所有的使用者，且特別是針對報表「取用者」而設計，[編輯檢視] 則僅適用於報表「建立者」和擁有者。 

## <a name="open-a-report-from-a-workspace-via-the-reports-content-view-list"></a>從工作區中開啟報表 (透過 [報表] 內容檢視清單)

1. 從工作區開始，然後選取 [報表] 索引標籤以顯示該工作區中的所有報表。  
   
   ![工作區的 [報表] 索引標籤](media/service-report-open/power-bi-open-report.png)
2. 選取報表名稱，以 [閱讀檢視] 開啟報表。  
   
    ![[閱讀檢視] 中的報表](media/service-report-open/power-bi-reading-view.png)
3. [在 [閱讀檢視] 中有許多可用功能](service-reading-view-and-editing-view.md)。  這個範例報表有多個頁面，因此請選取報表畫布底部的每個索引標籤來開始探索。 

## <a name="open-a-report-from-a-dashboard"></a>從儀表板開啟報表
有許多其他方式可以開啟報表；例如，您可以在儀表板上啟動，然後選取已從報表建立的磚。  選取磚時會以閱讀檢視開啟報表。 如果要跟著做，[請開啟 [銷售與行銷範例] 儀表板](sample-datasets.md)。

1. 開啟儀表板，並選取磚。

   如果您選取的磚是[使用問與答建立](service-dashboard-pin-tile-from-q-and-a.md)，問與答畫面將會開啟。 如果您選取的磚是[使用儀表板 [新增磚] 小工具所建立](service-dashboard-add-widget.md)，您就會開啟精靈來編輯該小工具。  

2.  在此範例中，我們已選取 [總單位 YTD...] 直條圖磚。

    ![已選取磚的儀表板](media/service-report-open/power-bi-dashboard.png)

3.  相關報表會在 [閱讀檢視] 中開啟。 請注意，我們在「YTD 類別」頁面上。 此報表頁面包含我們從儀表板選取的直條圖。

    ![在 [閱讀檢視] 中開啟報表](media/service-report-open/power-bi-report.png)

4. 留在 [閱讀檢視]，或選取 [編輯報表]，在 [編輯檢視] 中開啟報表。 請記住，只有具有該報表編輯權限的人可以在 [編輯檢視] 中開啟它。

    ![報表編輯器顯示編輯報表圖示](media/service-report-open/power-bi-edit-report.png)

## <a name="create-a-brand-new-report-from-a-dataset"></a>從資料集建立全新的報表
開啟報表的另一個方法是從資料集。 當您從資料集開始時，報表畫布會是空白的，所以方法建議用於想要根據他們擁有之資料集建立新報表的報表「建立者」。 如上面的範例，若要跟著做，請下載[銷售與行銷範例應用程式](sample-datasets.md)。

1. 在包含您想要作為報表基礎之資料集的工作區中開始。

   ![左側瀏覽窗格顯示應用程式工作區](media/service-report-open/power-bi-workspace.png)

2. 選取 [資料集] 索引標籤，顯示該工作區中所有資料集的清單。 這稱為**資料集**內容檢視清單。
   
   ![資料集清單](media/service-report-open/power-bi-dataset.png)

1. 找出資料集並選取**建立報表**圖示，在編輯檢視中開啟資料集。 如果您沒有編輯資料集的權限，您將無法開啟它。 
   
    ![具有建立報表圖示的資料集](media/service-report-open/power-bi-create-report.png)

3. 資料集會在報表編輯器中開啟。 您會看到右邊顯示資料欄位，等著您開始瀏覽和建立視覺效果。 

   ![報表畫布](media/service-report-open/power-bi-blank-canvas.png)

##  <a name="still-more-ways-to-open-a-report"></a>仍然有更多方法來開啟報表
當您更熟悉巡覽 Power BI 服務之後，便會找出最適合您的工作流程。 還有一些其他方法可存取報表：
- 從左側功能窗格使用 [我的最愛]、[最近]、[應用程式] 和 [與我共用]。 
- 使用[檢視相關項目](service-related-content.md)
- 有人[與您共用](service-share-reports.md)或您[設定警示](service-set-data-alerts.md)時使用電子郵件。    
- 從您的[通知中心](service-notification-center.md)    
- 以及更多

## <a name="next-steps"></a>後續步驟
深入了解 [Power BI 中的報表](service-reports.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)  

