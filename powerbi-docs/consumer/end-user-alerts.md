---
title: 教學課程：為 Power BI 服務儀表板上的資料設定警示
description: 在此教學課程中，您將了解如何設定警示，在儀表板上的資料變更超出您在 Microsoft Power BI 服務中設定的限制時通知您。
author: mihart
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 04/18/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 4cad37b9d4a7bf9e74a29312786a02b26fce5463
ms.sourcegitcommit: faa8cfb66e79ea16ba46605f752cc9ca57924d0e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83382753"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>教學課程：設定 Power BI 儀表板的警示

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

設定警示，在您儀表板上的資料變更，超出或低於您設定的限制時通知您。 只可在從報表視覺效果釘選的磚上，為量測計、KPI 和卡片設定警示。 

「取用者」可以將警示新增至其在 [我的工作區] 中所建立儀表板上的圖格。 「取用者」也可以將警示新增至儀表板 (已在 [Premium 容量](end-user-license.md)中與其共用) 上的圖格。 如果有 Power BI Pro 授權，您也可以在任何其他工作區的磚上設定警示。
此功能仍在持續改進之中，請參閱下方的[提示與疑難排解小節](#tips-and-troubleshooting)。

![圖格、卡片、KPI](media/end-user-alerts/card-gauge-kpi.png)

即使將儀表板分享給他人共用，仍只有您才能查看您所設定的警示。 資料警示會在平台之間完全同步處理；請在 [ Power BI 行動裝置應用程式](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)和 Power BI 服務中設定和檢視資料警示。 

> [!WARNING]
> 這些警示會提供您資料相關的資訊。 若您在行動裝置上檢視 Power BI 資料而裝置遭竊，建議您使用 Power BI 服務關閉所有警示。
> 

本教學課程涵蓋下列內容。
> [!div class="checklist"]
> * 誰可以設定警示
> * 哪些視覺效果支援警示
> * 誰可以看到我的警示
> * 警示是否可以在 Power BI Desktop 和行動版上運作
> * 如何建立警示
> * 我會在何處收到警示

如果您尚未註冊 Power BI，請先進行[免費註冊](https://app.powerbi.com/signupredirect?pbi_source=web)再開始。

此範例使用業務與行銷範例應用程式中的儀表板卡片磚。 [Microsoft AppSource](https://appsource.microsoft.com) 中有供應此應用程式。 如需協助您取得此應用程式，請參閱[安裝及使用「銷售與行銷」應用程式](end-user-app-marketing.md)。

1. 選取儀表板量測計、KPI 或卡片磚中的省略符號。
   
   ![卡片磚](media/end-user-alerts/power-bi-cards.png)
2. 選取鈴鐺圖示![警示圖示](media/end-user-alerts/power-bi-bell-icon.png)或 [管理警示]，以為 [單位市場佔有率百分比] 新增一或多個警示。

   ![選取了內含橢圓形的卡片磚](media/end-user-alerts/power-bi-ellipses.png)

   
1. 在 [管理警示] 窗格上選取 [+ 新增警示規則]。  確認滑桿設定為 [開啟]，並為警示提供標題。 磚可幫助您輕鬆地辨識警示。
   
   ![[管理警示] 視窗](media/end-user-alerts/power-bi-manage-alert.png)
4. 向下捲動並輸入警示的詳細資料。  在此範例中，我們將建立警示，在我們的市佔率提高到 35 或更高時通知我們。 警示會出現在我們的通知中心內。 我們也同樣設定讓 Power BI 傳送電子郵件給我們。
   
   ![在 [管理警示] 視窗中設定 [臨界值]](media/end-user-alerts/power-bi-manage-alert-details.png)
5. 選取 [儲存並關閉]。
 
   > [!NOTE]
   > 警示只對重新整理的資料有作用。 當資料重新整理時，Power BI 會檢查該資料有無設定警示。 若資料已達警示臨界值，便會觸發警示。 
   > 

## <a name="receiving-alerts"></a>接收警示
當正在追蹤的資料達到您所設定的其中一個臨界值時，會出現一些連鎖反應。 首先，Power BI 會檢查自上次傳送警示起，是否已超過 1 小時或 24 小時 (取決於您選取的選項)。 只要資料超過臨界值，您就會收到警示。

接下來，Power BI 會傳送警示到您的通知中心，或是寄發電子郵件。 每個警示都包含資料的直接連結。 選取連結以查看相關的磚。  

1. 您如有設定傳送電子郵件警示，將會在收件匣中看到類似如下所述的狀況。 這是我們對不同儀表板設定的警示。此儀表板會追蹤 Usability 小組完成的工作。
   
   ![警示電子郵件](media/end-user-alerts/power-bi-alert-email.png)
2. Power BI 會在您的**通知中心**新增一則訊息，並將新的警示圖示加入適用的磚 。
   
   ![Power BI 服務中的通知圖示](media/end-user-alerts/power-bi-task-alert.png)
3. 若要查看警示詳細資料，請開啟您的通知中心。
   
    ![讀取警示](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>管理警示

有許多方式可以管理您的警示：從儀表板的圖格本身、從 Power BI 的 [設定] 功能表、在 [iPhone 的 Power BI 行動裝置應用程式](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)，或 [Windows 10 的 Power BI 行動裝置應用程式](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)個別的圖格上。

### <a name="from-the-tile-itself"></a>從磚本身

1. 當您需要變更或移除磚的警示時，請選取鈴鐺圖示 ![警示圖示](media/end-user-alerts/power-bi-bell-icon.png)，以重新開啟 [管理警示] 視窗。 您為該磚設定的所有警示皆會顯示。
   
    ![[管理警示] 視窗](media/end-user-alerts/power-bi-manage-alerts.png).
2. 若要修改警示，請選取警示名稱左側的箭號。
   
    ![警示名稱旁的箭號](media/end-user-alerts/power-bi-modify-alert.png).
3. 若要刪除警示，請選取警示名稱右側的垃圾桶。
   
      ![已選取垃圾桶圖示](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>從 Power BI 的 [設定] 功能表

1. 從 Power BI 功能表列選取齒輪圖示。
   
    ![齒輪圖示](media/end-user-alerts/powerbi-gear-icon.png).
2. 選取 [設定] 下的 [警示]。
   
    ![[設定] 視窗的 [警示] 索引標籤](media/end-user-alerts/power-bi-alert-settings.png)
3. 您可以在此處開啟及關閉警示、開啟 [管理警示] 視窗執行變更，或是刪除警示。

## <a name="tips-and-troubleshooting"></a>提示與疑難排解 

* 若無法為量測計、KPI 或卡片設定警示，請連絡您的租用戶管理員以尋求協助。 有時儀表板或特定類型儀表板磚的警示可能會關閉或無法使用。
* 警示只對重新整理的資料有作用。 警示對靜態資料毫無作用。 Microsoft 大多提供靜態範例。 
* 需有 Power BI Pro 或 Premium 授權才能接收及檢視共用的內容。 如需詳細資訊，請閱讀[我有哪些授權？](end-user-license.md)。
* 您可以對建立自串流資料集 (從報表釘選到儀表板) 的視覺效果設定警示。 但不可對使用 [新增磚] > [自訂串流資料] 直接在儀表板上所建立串流磚設定警示。


## <a name="clean-up-resources"></a>清除資源
刪除警示的指示已在上方說明。 簡單來說，請從 Power BI 功能表列選取齒輪圖示。 在 [設定] 下，選取 [警示]，然後刪除警示。

> [!div class="nextstepaction"]
> [在行動裝置上設定資料警示](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


