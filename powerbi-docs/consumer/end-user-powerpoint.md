---
title: 從適用於取用者的 Power BI 將報表匯出至 PowerPoint
description: 了解如何將 Power BI 報表匯出至 PowerPoint。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/13/2018
ms.author: mihart
LocalizationGroup: Share your work
ms.openlocfilehash: a865c98a5bacd526a553354ea828e86fa0155a79
ms.sourcegitcommit: 4f46d71ff6026c1c158f007425aefdcb501f48ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2018
ms.locfileid: "52979252"
---
# <a name="export-reports-from-power-bi-to-powerpoint"></a>從 Power BI 將報表匯出至 PowerPoint
有了 Power BI，您就可以將報表發佈至 **Microsoft PowerPoint**，並根據 Power BI 報表輕鬆地建立投影片組。 當您**匯出至 PowerPoint** 時會發生下列狀況︰

* Power BI 報表中的每個頁面都會變成 PowerPoint 的個別投影片
* Power BI 報表中的每個頁面都會匯出成 PowerPoint 中的單一高解析度影像 <!-- * The filters and slicers settings that you added to the report are preserved. -->
* PowerPoint 中會建立連結至 Power BI 報表的連結 

將 **Power BI 報表**匯出到 **PowerPoint** 的程序非常簡單快速。 只要遵循下一節中列出的步驟即可。

## <a name="how-to-export-your-power-bi-report-to-powerpoint"></a>如何將 Power BI 報表匯出至 PowerPoint
在 Power BI 服務中，選取要顯示在畫布上的報表。 也可以從您的 [首頁] 頁面、[應用程式]，或左側瀏覽窗格上的其他區段選取報表。

![](media/end-user-powerpoint/power-bi-publish.png)

當畫布上顯示您要匯出至 PowerPoint 的報表時，請從 Power BI 服務的功能表列選取 [檔案] > [匯出至 PowerPoint] 。

![](media/end-user-powerpoint/powerbi_to_powerpoint_1.png)

您會在 Power BI 服務瀏覽器視窗的右上角，看到報表正匯出至 PowerPoint 的通知橫幅。 這可能需要幾分鐘的時間，而您可以在報表匯出時繼續使用 Power BI 工作。

![](media/end-user-powerpoint/powerbi_to_powerpoint_2.png)

完成後，通知橫幅隨即變更，讓您知道 Power BI 服務已完成匯出程序。

![](media/end-user-powerpoint/powerbi_to_powerpoint_3.png)

您可以在瀏覽器顯示下載檔案的位置取得檔案。 在下圖中，是以瀏覽器視窗底部的下載橫幅方式顯示。

![](media/end-user-powerpoint/powerbi_to_powerpoint_4.png)

就是這麼簡單。 您可以下載檔案、使用 PowerPoint 開啟檔案，然後像您處理任何其他 PowerPoint 簡報一樣修改或加強檔案。

## <a name="checking-out-your-exported-powerpoint-file"></a>查看已匯出的 PowerPoint 檔案
當您開啟 Power BI 匯出的 PowerPoint 檔案時，您會發現一些很棒又實用的元素。 請看下圖，然後查看下方說明其中幾項優異功能的編號項目。

![](media/end-user-powerpoint/powerbi_to_powerpoint_5.png)

1. 投影片組的第一頁包含您的報表名稱及連結，讓您**在 Power BI 中檢視**作為投影片組基礎的報表。
2. 您也會獲得一些有關報表的實用資訊，包括匯出報表所依據的「上次資料重新整理」，以及「下載於」時間和日期，也就是 Power BI 報表匯出為 PowerPoint 檔案的日期和時間。
3. 每張報表頁面都是一張個別的投影片，如左導覽窗格中所示。 
4. 已發行的報表會根據您 Power BI 設定中的語言來進行轉譯，否則會根據您的瀏覽器地區設定來進行轉譯。 若要查看或設定語言喜好設定，請選取齒輪圖示 ![](media/end-user-powerpoint/power-bi-settings-icon.png) **> [設定] > [一般] > [語言]**。 如需地區設定的資訊，請參閱 [Power BI 支援的語言與國家/地區](../supported-languages-countries-regions.md)。
5. PowerPoint 簡報包含了一張封面投影片，其中有正確時區的匯出時間。

當您瀏覽個別的投影片時，您會發現每個報表頁面都是獨立的影像。

>[!NOTE]
> 每個報表頁面擁有一個視覺效果是新的行為。 先前的行為 (針對每個視覺效果提供獨立的影像) 已不再實作。 
 

![](media/end-user-powerpoint/powerbi_to_powerpoint_6.png)

您可在此隨意處理 PowerPoint 簡報或任何高解析度影像！

## <a name="limitations"></a>限制
使用 [匯出至 PowerPoint] 功能時，需牢記幾項考量與限制。

* 匯出至 PowerPoint 時，尚未支援工作階段內互動，例如反白顯示和篩選、向下切入等等。 匯出的 PowerPoint 會顯示原來儲存在報表中的視覺效果。 如果您已套用篩選和交叉分析篩選器，並想要在匯出時保留，請儲存報表，然後進行匯出。
* 目前不支援 **R 視覺效果**。 任何這類的視覺效果都會作為空白影像匯出至 PowerPoint，並顯示一個錯誤訊息，指出目前並不支援該視覺效果。
* 目前已支援**經認證**的**自訂視覺效果**。 如需認證自訂視覺效果，包括如何使自訂視覺效果獲得認證的詳細資訊，請參閱[認證自訂視覺效果](../power-bi-custom-visuals-certified.md)。 任何未經認證的自訂視覺效果目前都不支援，其將會作為空白影像匯出至 PowerPoint，並顯示一個錯誤訊息，指出目前並不支援該視覺效果。
* 目前無法匯出超過 30 頁的報表。
* 將報表匯出至 PowerPoint 的程序需時數分鐘，請耐心等候。 影響所需時間的因素，包括報表結構及 Power BI 服務目前的負載。
* 如果 Power BI 服務中沒有 [匯出至 PowerPoint] 功能表項目，可能是因為租用戶系統管理員停用了此功能。 如需詳細資訊，請連絡您的租用戶系統管理員。
* 背景影像會按圖表的周框區域剪裁。 強烈建議您先移除背景影像，再匯出至 PowerPoint。
* PowerPoint 中的頁面一律會以標準的 9:16 大小建立，而不論 Power BI 報表中的原始頁面大小或維度為何。
* Power BI 租用戶網域外部使用者擁有的報表 (例如，組織外部某人所擁有並與您共用的報表) 無法發行至 PowerPoint。
* 如果您與組織外部的某人 (也就是不在您 Power BI 租用戶中的使用者) 共用儀表板，該使用者會無法將與共用儀表板的相關報表匯出至 PowerPoint。 舉例來說，如果您是 aaron@contoso.com，您可以和 david@cohowinery.com 共用。 但是 david@cohowinery.com 無發將相關報表匯出至 PowerPoint。
* 如先前所述，每個報表頁面會匯出為 PowerPoint 檔中的單一影像。
* Power BI 服務會使用您的 Power BI 語言設定作為 PowerPoint 的輸出語言。 若要查看或設定語言喜好設定，請選取齒輪圖示 ![](media/end-user-powerpoint/power-bi-settings-icon.png) **> [設定] > [一般] > [語言]**。
* 匯出的 PowerPoint 檔案，其封面投影片上的**下載於**時間，會設定為匯出當時您電腦的時區。

## <a name="next-steps"></a>後續步驟
[列印報表](end-user-print.md)