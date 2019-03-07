---
title: 在 SharePoint Online 中嵌入報表網頁組件
description: 你可以使用 SharePoint Online 的 Power BI 新報表網頁組件，輕鬆地在 SharePoint Online 的網頁中內嵌互動式 Power BI 報表。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 11/01/2018
ms.openlocfilehash: b24bde73c4f0e5f30c8baad7910fe9d9d924c3dc
ms.sourcegitcommit: 364ffa1178cdfb0a20acffc0fd79922ebc892d72
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57226150"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>在 SharePoint Online 中嵌入報表網頁組件

你可以使用 SharePoint Online 的 Power BI 新報表網頁組件，輕鬆地在 SharePoint Online 的網頁中內嵌互動式 Power BI 報表。

當使用新的 [內嵌在 SharePoint Online 中] 選項時，內嵌的報表受會到全面性的防護，所以您可以輕鬆地建立安全的內部入口網站。

## <a name="requirements"></a>需求

為了讓**內嵌在 SharePoint Online 中**的報表運作，必須達成幾項需求。

* 您需要 Power BI Pro 授權，或是具有 Power BI 授權的 [Power BI Premium 容量 (EM 或 P SKU)](service-premium.md#premium-capacity-nodes)。
* SharePoint Online 的 Power BI Web 組件需要[新式網頁](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)。

## <a name="embed-your-report"></a>內嵌報表

若要將報表嵌入 SharePoint Online，您必須先取得報表的 URL，然後在 SharePoint Online 中的新 Power BI 網頁組件使用該 URL。

### <a name="get-a-url-to-your-report"></a>取得報表的 URL

1. 在 Power BI 服務中檢視報表。

2. 選取 [檔案] 功能表項目。

3. 選取 [內嵌於 SharePoint Online]。

    ![[檔案] 功能表](media/service-embed-report-spo/powerbi-file-menu.png)

4. 從對話方塊複製 URL。

    ![內嵌連結](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>將 Power BI 報表新增至 SharePoint Online 頁面

1. 在 SharePoint Online 中開啟要使用的頁面，然後選取 [編輯]。

    ![SP 編輯頁面](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    或者藉由選取 SharePoint Online 內的 [+ 新增]，以建立新的新式網站頁面。

    ![SP 新增頁面](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. 選取 **+** 然後選取 [Power BI] Web 組件。

    ![SP 新增網頁組件](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. 選取 [新增報告] 。

    ![SP 新報表](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)

4. 將報表 URL 貼到屬性窗格。 此報表 URL 是您從上述步驟所複製的 URL。 報表會自動載入。

    ![SP 新增網頁組件屬性](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. 選取 [發佈]，讓 SharePoint Online 使用者能看見您所做的變更。

    ![載入的 SP 報表](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>授與報告存取權

在 SharePoint Online 中內嵌報表，並不會自動授予使用者檢視報表的權限。 在 Power BI 服務中，具有檢視報表所需的權限。

> [!IMPORTANT]
> 請務必檢閱可以看到 Power BI 服務內報表的成員，並將存取權授與未列出的成員。

有兩個方法可提供 Power BI 服務內報表的存取權。 如果您使用 Office 365 群組來建置 SharePoint Online 小組網站，則要將使用者列為 **Power BI 服務內的應用程式工作區**成員，及列出 **SharePoint 頁面**。 如需詳細資訊，請參閱如何[管理應用程式工作區](service-manage-app-workspace-in-power-bi-and-office-365.md)。

或者，您可以透過在應用程式中內嵌報表來直接與使用者共用報表。 若要在應用程式中內嵌報表，請按照幾個步驟操作。  

1. 應用程式的作者是 Pro 使用者。

2. 該作者在應用程式工作區中建立了報表。 若要與 **Power BI 免費使用者** 共用，您需要將該應用程式工作區設定為 **Premium 工作區**。

3. 作者發行應用程式，然後安裝它。 作者需要確保應用程式會安裝成可存取報告 URL (用於在內嵌在 SharePoint Online 中)。

4. 現在，所有使用者也都需要安裝應用程式。 不過，您可以使用 [自動安裝應用程式] 功能，將應用程式設定成替使用者預先安裝，您可以在 [Power BI 管理入口網站](service-admin-portal.md) 中啟用它。

   ![自動安裝應用程式](media/service-embed-report-spo/install-app-automatically.png)

5. 作者開啟應用程式，並移至報表。

6. 作者從應用程式安裝的報表複製內嵌報表 URL。 請勿使用來自應用程式工作區的原始報表 URL。

7. 在 SharePoint Online 中建立新的小組網站。

8. 將從步驟 6 複製的 URL，新增到 Power BI 網頁組件。

9. 新增要使用您建立的 Power BI 應用程式中 SharePoint Online 頁面上之資料的所有使用者和/或群組。

    > [!NOTE]
    > **使用者或群組需要存取 SharePoint Online 頁面，及 Power BI 應用程式中的報表，才能看到 SharePoint 頁面上的報表。**

10. 現在使用者可以移至 SharePoint Online 中的小組網站，並在頁面上檢視報表。

## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

如果您的 Power BI 環境需要您使用多重要素驗證進行登入，您可能會受要求使用安全性裝置進行登入，以驗證您的身分識別。 如果您沒有使用多重要素驗證登入 SharePoint.Online，但您的 Power BI 環境需要使用安全性裝置來驗證的帳戶，就會發生此情況。

> [!NOTE]
> Azure Active Directory 2.0 尚不支援多重要素驗證。 使用者會收到指出「錯誤」的訊息。 如果使用者使用其安全性裝置再次登入 SharePoint Online ，則可以檢視報表。

## <a name="web-part-settings"></a>網頁組件設定

以下是 SharePoint Online 的 Power BI 網頁組件之可調整設定的描述。

![SP 網頁組件屬性](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| 屬性 | 描述 |
| --- | --- |
| 頁面名稱 |設定網頁組件所顯示的預設頁面。 從下拉式清單中選取一個值。 如果沒有顯示任何頁面，可能是您的報表只有一個頁面，或您所貼上的 URL 包含頁面名稱。 從 URL 移除報表區段，以選取特定頁面。 |
| 顯示 |調整報表如何被納入 SharePoint Online 頁面的選項。 |
| 顯示功能窗格 |顯示或隱藏頁面功能窗格。 |
| 顯示篩選窗格 |顯示或隱藏篩選窗格。 |

## <a name="reports-that-do-not-load"></a>不會載入的報表

您的報表可能未在 Power BI Web 組件中載入，並可能顯示下列訊息。

*此內容無法使用。*

![找不到報表的訊息](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

有兩個常見的原因會導致此訊息的出現。

1. 您沒有存取此儀表板的權限。
2. 報表已刪除。

請連絡 SharePoint Online 頁面的擁有者，以協助您解決問題。

## <a name="licensing"></a>授權

在 SharePoint 中檢視報表的使用者需要 **Power BI Pro 授權**，或者內容需要位於 **[Power BI Premium 容量 (EM 或 P SKU)](service-admin-premium-purchase.md)** 的工作空間中。

## <a name="known-issues-and-limitations"></a>已知的問題及限制

* 錯誤：「An error occurred, please try logging out and back in and then revisiting this page. (發生錯誤。請登出再登入，然後再次前往此頁面。) 相互關聯識別碼: 未定義，http 回應狀態:400，伺服器錯誤碼 10001，訊息:遺漏重新整理權杖」
  
  如果您收到這個錯誤，請嘗試下列其中一個疑難排解步驟。
  
  1. 登出再登入 SharePoint。 請務必關閉所有瀏覽器視窗，然後再重新登入。

  2. 若您的使用者帳戶需要多重要素驗證 (MFA)，請確定您是使用多重要素驗證裝置 (手機應用程式、智慧卡等等) 登入 SharePoint。
  
  3. 不支援 Azure B2B 來賓使用者帳戶。 使用者看到的 Power BI 標誌會顯示載入的部分，但不會顯示報表。

* Power BI 與 SharePoint Online 支援的當地語系化語言不盡相同。 因此，您可能會在內嵌報表中看到未適當當地語系化的內容。

* 您若使用 Internet Explorer 10，可能會遇到問題。 您可以參閱 [Power BI](consumer/end-user-browsers.md) 及 [Office 365](https://products.office.com/office-system-requirements#Browsers-section) 的瀏覽器支援。

* [主權雲端](https://powerbi.microsoft.com/clouds/)不提供 Power BI Web 組件。

* 此 Web 組件不支援傳統的 SharePoint 伺服器。

* [URL 篩選](service-url-filters.md)不受到 SPO Web 組件支援。

## <a name="next-steps"></a>後續步驟

* [允許或防止終端使用者建立新式網站頁面](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [在 Power BI 中建立和散發應用程式](service-create-distribute-apps.md)  
* [Share a dashboard with colleagues and others](service-share-dashboards.md) (與同事和其他人共用儀表板)  
* [什麼是 Power BI Premium？](service-premium.md)
* [在安全入口網站或網站中內嵌報告](service-embed-secure.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)