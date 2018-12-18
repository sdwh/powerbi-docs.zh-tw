---
title: 教學課程：在 Power BI 服務中設定資料警示
description: 在本教學課程中，了解如何設定警示，在儀表板中的資料變更超出您在 Microsoft Power BI 服務中所設定的限制時通知您。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: tutorial
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 0d614b6028fa4d7e11ac5bf82e05d44a95e4f234
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280849"
---
# <a name="tutorial-set-data-alerts-in-power-bi-service"></a>教學課程：在 Power BI 服務中設定資料警示
設定警示，以在儀表板中的資料變更時超出您所設定的限制時通知您。 

如果您擁有 Power BI Pro 授權，或已從 [Premium容量](../service-premium.md)與您共用儀表板，則可以設定圖格的警示。 只可在從報告視覺效果釘選的圖格上，為量測計、KPI 和卡片設定警示。 可以對從報表釘選到儀表板的串流資料集上所建立的視覺效果，設定警示，但不可對使用 [新增磚] >  [自訂串流資料] 直接於儀表板上建立的串流圖格，設定警示。 

即使將儀表板分享給他人共用，仍只有您才能查看您所設定的警示。 資料警示會在平台之間完全同步處理；請在 [ Power BI 行動裝置應用程式](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)和 Power BI 服務中設定和檢視資料警示。 

![圖格](../media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> 資料驅動的警示通知會提供資料的相關資訊。 如果您在行動裝置上檢視 Power BI 資料，而該裝置遭竊，建議您使用 Power BI 服務關閉所有資料驅動的警示規則。
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

## <a name="set-data-alerts-in-power-bi-service"></a>在 Power BI 服務中設定資料警示
觀看 Amanda 在她的儀表板上將某些警示新增至圖格。 然後遵循影片下方的逐步指示親自試試看。

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

此範例使用來自[零售分析範例](http://go.microsoft.com/fwlink/?LinkId=529778)儀表板的卡片圖格。

1. 選取儀表板量測計、KPI 或卡片圖格中的省略符號。
   
   ![[商店數總計] 圖格](media/end-user-alerts/powerbi-card.png)
2. 選取鈴鐺圖示，![警示圖示](media/end-user-alerts/power-bi-bell-icon.png)或 [管理警示]，以為 [商店總數] 新增一或多個警示。
   
1. 在 [管理警示] 窗格上選取 [+ 新增警示規則]。  確認滑桿設定為 [開啟]，並為警示提供標題。 圖格可幫助您輕鬆地辨識警示。
   
   ![[管理警示] 視窗](media/end-user-alerts/powerbi-alert-title.png)
4. 向下捲動並輸入警示的詳細資料。  在此範例中，我們要建立警示，在商店數總計超過 100 家時通知我們。 警示會出現在我們的通知中心內。 我們也同樣設定讓 Power BI 傳送電子郵件給我們。
   
   ![在 [管理警示] 視窗中設定 [臨界值]](media/end-user-alerts/power-bi-set-alert-details.png)
5. 選取 [儲存並關閉]。

## <a name="receiving-alerts"></a>接收警示
當正在追蹤的資料達到您所設定的其中一個臨界值時，會出現一些連鎖反應。 首先，Power BI 會檢查自上次傳送警示起，是否已超過 1 小時或 24 小時 (取決於您選取的選項)。 只要資料超過臨界值，您就會收到警示。

接下來，Power BI 會傳送警示到您的通知中心，並選擇性寄送電子郵件。 每個警示都包含資料的直接連結。 選取連結以查看相關的圖格。  

1. 您如有設定傳送電子郵件警示，將會在收件匣中看到類似如下所述的狀況。
   
   ![警示電子郵件](media/end-user-alerts/powerbi-alerts-email.png)
2. Power BI 會在您的**通知中心**新增一則訊息，並將新的警示圖示加入適用的圖格。
   
   ![Power BI 服務中的通知圖示](media/end-user-alerts/powerbi-alert-notifications.png)
3. 若要查看警示詳細資料，請開啟您的通知中心。
   
    ![讀取警示](media/end-user-alerts/powerbi-alert-notification.png)
   
   > [!NOTE]
   > 警示只對重新整理的資料有作用。 當資料重新整理時，Power BI 會檢查該資料有無設定警示。 若資料已達警示臨界值，便會觸發警示。
   > 
   > 

## <a name="managing-alerts"></a>管理警示
有許多方式可以管理您的警示：從儀表板的圖格本身、從 Power BI 的 [設定] 功能表、在 [iPhone 的 Power BI 行動裝置應用程式](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)或 [Windows 10 的 Power BI 行動裝置應用程式](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)個別的圖格上。

### <a name="from-the-tile-itself"></a>從圖格本身
1. 當您需要變更或移除圖格的警示時，請選取鈴鐺圖示 ![警示圖示](media/end-user-alerts/power-bi-bell-icon.png)，以重新開啟 [管理警示] 視窗。 您為該圖格設定的所有警示皆會顯示。
   
    ![[管理警示] 視窗](media/end-user-alerts/powerbi-see-alerts.png).
2. 若要修改警示，請選取警示名稱左側的箭號。
   
    ![警示名稱旁的箭號](media/end-user-alerts/powerbi-see-alerts-arrow.png).
3. 若要刪除警示，請選取警示名稱右側的垃圾桶。
   
      ![已選取垃圾桶圖示](media/end-user-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>從 Power BI 的 [設定] 功能表
1. 從 Power BI 功能表列選取齒輪圖示。
   
    ![齒輪圖示](media/end-user-alerts/powerbi-gear-icon.png).
2. 選取 [設定] 下的 [警示]。
   
    ![[設定] 視窗的 [警示] 索引標籤](media/end-user-alerts/powerbi-alert-settings.png)
3. 您可以在此處開啟及關閉警示、開啟 [管理警示] 視窗執行變更，或是刪除警示。

## <a name="tips-and-troubleshooting"></a>提示與疑難排解
* 目前警示對於具有日期/時間量值的 Bing 圖格或卡片圖格無效。
* 警示只適用於數值資料類型。
* 警示只對重新整理的資料有作用。 警示對靜態資料毫無作用。
* 如果已建置了 KPI/卡片/量測計報表視覺效果，然後又將該視覺效果釘選至儀表板，則警示只會對串流資料集產生作用。

## <a name="clean-up-resources"></a>清除資源
刪除警示的指示已在上方說明。 簡單來說，請從 Power BI 功能表列選取齒輪圖示。 在 [設定] 下，選取 [警示]，然後刪除警示。

> [!div class="nextstepaction"]
> [在行動裝置上設定資料警示](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


