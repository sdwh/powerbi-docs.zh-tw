---
title: 關於 Power BI 自訂視覺效果的常見問題集
description: 瀏覽 Power BI 自訂視覺效果相關的常見問題與回答清單
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: d17a5875569f29da41d62ca61efcbdae3b9242e9
ms.sourcegitcommit: f176ba9d52d50d93f264eca21bb3fd987dbf934b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57757315"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>關於 Power BI 自訂視覺效果的常見問題集

## <a name="organizational-custom-visuals"></a>組織自訂視覺效果

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>系統管理員如何管理組織自訂視覺效果？

在管理入口網站中的 [組織自訂視覺效果] 索引標籤底下，系統管理員可以查看並[管理企業中的所有組織自訂視覺效果](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals)：新增、停用、啟用及刪除。
無需再透過電子郵件或共用資料夾來共用這些視覺效果！ 將組織的自訂視覺效果部署到組織存放庫之後，組織中的使用者就可以輕鬆地尋找這些視覺效果，並直接從 Power BI Desktop 或服務將它們匯入報表中。 您可以在 [我的組織] 索引標籤下的內建存放區 (在 Desktop 與服務中) 找到組織自訂視覺效果。一旦系統管理員上傳新的組織自訂視覺效果版本後，組織中的每個人都會獲得相同的更新版本。 報表作者不需要刪除報表中的視覺效果即可獲取這些視覺效果的新版本，因為使用這些視覺效果的所有報表都會自動更新！ 更新機制類似於 Marketplace 視覺效果。

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>如果系統管理員將自訂視覺效果從公用 Marketplace 上傳到組織存放區，那麼一旦供應商在公用 Marketplace 中更新視覺效果，它是否會自動更新？

否，公用 Marketplace 沒有自動更新功能。
系統管理員應負責更新組織自訂視覺效果的版本。

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>有停用組織存放區的方法嗎？

否，使用者一定會看到 Power BI Desktop 和服務中的 [我的組織 ] 索引標籤。 系統管理員可以從管理入口網站停用或刪除所有的組織自訂視覺效果，而組織的存放區是空的。
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>如果系統管理員從管理入口網站 ([租用戶設定]) 停用自訂視覺效果，使用者是否仍可以存取組織自訂視覺效果？

是，如果系統管理員從管理入口網站停用自訂視覺效果，不會影響組織的存放區。 某些組織會停用自訂視覺效果，並僅啟用由 Power BI 系統管理員匯入與上傳到組織的存放區的精選視覺效果。 Power BI Desktop 並未強制停用管理入口網站中的自訂視覺效果。 Desktop 使用者仍可在其報表中新增並使用公用 Marketplace 中的自訂視覺效果。 但是，這些公用的自訂視覺效果會在發行至 Power BI 服務後停止轉譯，並發出適當的錯誤訊息。 使用 Power BI 服務時，您無法從公用 Marketplace 匯入自訂視覺效果。 只能匯入組織的存放區中的視覺效果，因為管理入口網站中的自訂視覺效果設定，在 Power BI 服務中是強制執行的。

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>為什麼組織的存放區和組織自訂視覺效果是最理想的企業解決方案？

* 每個人都取得相同的視覺效果版本，由 Power BI 系統管理員所控制。 系統管理員在管理入口網站中更新視覺效果版本後，組織中的所有使用者會自動取得更新版本。

* 無需再透過電子郵件或共用資料夾共用視覺效果檔案！ 同一位置，登入的所有成員都可以看到。

* 安全性和可支援性，組織自訂視覺效果的新版本會在類似於 Marketplace 視覺效果的所有報表中自動更新。

* 組織中使用組織自訂視覺效果的使用者必須登入才能查看及使用組織自訂視覺效果，也就是組織的安全性元素。

* 系統管理員可以控制組織中可用的自訂視覺效果。

* 系統管理員可以從管理入口網站啟用/停用視覺效果以進行測試。 更好的安全性強制，因為僅允許組織成員使用這些視覺效果。

## <a name="certified-custom-visuals"></a>認證的自訂視覺效果

### <a name="what-are-certified-custom-visuals"></a>什麼是經認證的自訂視覺效果？

認證的自訂視覺效果是[市集](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中的視覺效果，符合某些[指定](power-bi-custom-visuals-certified.md)程式碼需求並由 Power BI 小組進行測試。  執行的測試設計為檢查不會存取外部服務或資源的視覺效果。 不過，Microsoft「不是」協力廠商自訂視覺效果的作者，我們建議客戶直接連絡作者以驗證這類視覺效果的功能。

### <a name="what-tests-are-done-during-the-certification-process"></a>認證流程期間會完成哪些測試？

認證流程測試包括但不限於：程式碼檢閱、靜態程式碼分析、資料外洩、資料模糊測試、滲透測試、存取 XSS 測試、惡意資料插入、輸入驗證和功能測試。
 
### <a name="do-you-certify-visuals-every-submission"></a>每次提交都會認證視覺效果嗎？

是。 每當經認證的視覺效果有新版本提交至市集時，視覺效果的版本更新都會經過相同的認證檢查。

開發人員請注意：如果您要提交經認證視覺效果的版本更新，並不需要另外傳送[初次認證要求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification)電子郵件。 版本更新的認證會自動進行，只要有任何違規導致拒絕，系統都會傳送電子郵件說明有哪些地方需要修正。 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>經認證的視覺效果可能會在新的更新後失去認證嗎？

不會，並不會發生這樣的事。 新的更新不會使經認證的視覺效果失去認證。 該更新會受到拒絕。
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>如果我要向認證流程進行提交，那麼是否需要在公用存放庫共用我的程式碼？

不用，您不必公開共用自己的程式碼。 但您必須授與我們檢查視覺效果程式碼的讀取權限。 例如： GitHub 中的私人存放庫。
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>我必須在[市集](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中[發行](https://docs.microsoft.com/power-bi/developer/office-store)視覺效果才能加以認證嗎？

是。 您必須先將視覺效果發行至市集，這是認證的必要需求。
自訂視覺效果必須在我們的伺服器內，我們才能加以認證。 我們無法認證私人視覺效果。
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>認證我的視覺效果需要多少時間？

如果是更新版本，最多需要 2 週的時間。 如果是新的提交項目 (首次認證)，最多需要 3 週的時間。 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>你們能保證認證流程不會發生資料外洩嗎？

執行的測試設計為檢查不會存取外部服務或資源的視覺效果。 不過，Microsoft「不是」協力廠商自訂視覺效果的作者，我們建議客戶直接連絡作者以驗證這類視覺效果的功能。
 
### <a name="are-uncertified-custom-visuals-safe-to-use"></a>使用未經認證的自訂視覺效果是否安全？

未經認證的自訂視覺效果不一定不安全。
有些視覺效果未經過認證，因為它們不符合一或多個[認證需求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)。 例如，連接到地圖視覺效果或使用商業程式庫的視覺效果等外部服務。
 
## <a name="visuals-with-additional-purchases"></a>需要另外購買的視覺效果

### <a name="what-is-a-visual-with-additional-purchases"></a>什麼是需要另外購買的視覺效果？

需要另外購買的視覺效果類似於 Marketplace 中的應用程式內購買 (IAP) 增益集，而這些增益集均具有**可能需要另外購買**的價格標籤。

IAP 自訂視覺效果是免費、可下載的自訂視覺效果，使用者不需付費即可從 Marketplace 下載這些自訂視覺效果。 IAP 視覺效果可讓您選擇在應用程式內購買進階功能。  

### <a name="whats-the-benefit-to-developers"></a>這對開發人員有何優勢？

每天許多訪客得以探索 AppSource 中的 IAP 自訂視覺效果，一方面帶來寶貴的流量，又可增加 IAP 自訂視覺效果與開發人員的曝光率。

如果您之前是透過網站來管理這些視覺效果，現在則可以將它們提交至 AppSource。 這可提升 IAP 視覺效果在 Power BI 社群中的曝光度與矚目度。

使用 IAP 自訂視覺效果的客戶可透過存放區中的檢閱和評等系統，對 AppSource 中的視覺效果提供直接的意見反應。  

一旦 IAP 視覺效果由 AppSource 驗證小組核准之後，您也可以提交這些視覺效果以進行認證。 這是選擇性的程序。  

視覺效果通過認證後，IAP 自訂視覺效果就可以匯出至 PowerPoint，並顯示在使用者訂閱報表頁面時所收到的電子郵件中。 因此，現在將 IAP 自訂視覺效果提交至 Marketplace，即可驗證 IAP 視覺效果，並支援額外的功能集。  

### <a name="do-iap-visuals-need-to-be-certified"></a>IAP 視覺效果需要通過認證嗎？

認證程序是選擇性的。 和免費的視覺效果相同，開發人員可自行決定其 IAP 自訂視覺效果要不要進行認證。

### <a name="what-is-changing-in-the-submission-process"></a>提交程序將有何變更？

將 IAP 自訂視覺效果提交至 Marketplace 的程序與免費視覺效果的程序相同。 提交程序會透過賣方儀表板進行。  提交程序的唯一變更是，開發人員應該在賣方儀表板的開發人員備註中註明： 「需要在應用程式內購買的視覺效果」。 如果需要驗證付費/進階功能，您也必須提供授權金鑰/權杖。  

賣方儀表板中除了「免費應用程式內購買」外，不會有任何新選項，因此您必須將您的 IAP 視覺效果提交為「免費」視覺效果。

此外，您可以在存放區中提供完整描述，說明哪些功能免費，而哪些功能需要另外購買才能運作，讓使用者有所預期。  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>該如何提交 IAP 自訂視覺效果？

如果您正在處理 IAP 自訂視覺效果或已完成，請確認它符合方針。  

如果您的自訂視覺效果中有標誌，請確認它符合標誌方針 (色彩、位置、大小和動作觸發)。

您也可以在方針中找到最佳做法的注意事項。  
> [!Note]
> 所有免費視覺效果應保有等同先前提供的免費功能。 您可以在舊的免費功能之上新增選用進階付費功能。 我們建議將附有進階功能的 IAP 視覺效果作為新視覺效果提交，而不更新舊的免費項目。

### <a name="can-i-get-my-iap-custom-visual-certified"></a>IAP 自訂視覺效果可以獲得認證嗎？

可以，做法和免費的視覺效果相同。  一旦 AppSource 小組核准您的 IAP 自訂視覺效果之後，您即可將視覺效果提交至認證程序。

若要認證您的視覺效果，它應該符合認證需求，例如：視覺效果不得存取外部服務以進行授權驗證。

撤銷認證是選擇性的程序，您可自行決定是否要讓您的 IAP 視覺效果進行認證。

## <a name="additional-questions"></a>其他問題

### <a name="how-to-get-support"></a>如何取得支援？

如果您有任何問題或意見，歡迎連絡自訂視覺效果支援小組： *pbicvsupport@microsoft.com* 。  

## <a name="next-steps"></a>後續步驟

如需詳細資訊，請參閱[針對您的 Power BI 自訂視覺效果進行疑難排解](power-bi-custom-visuals-troubleshoot.md)。
