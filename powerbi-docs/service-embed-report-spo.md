---
title: 在 SharePoint Online 中嵌入報表網頁組件
description: 你可以使用 SharePoint Online 的 Power BI 新報表網頁組件，輕鬆地在 SharePoint Online 的網頁中內嵌互動式 Power BI 報表。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051274"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>在 SharePoint Online 中嵌入報表網頁組件

你可以使用 SharePoint Online 的 Power BI 新報表網頁組件，輕鬆地在 SharePoint Online 的網頁中內嵌互動式 Power BI 報表。

當使用新**內嵌在 SharePoint Online**選項時，內嵌的報表是完全安全的因此您可以輕鬆地建立安全的內部入口網站。

## <a name="requirements"></a>需求

針對**內嵌在 SharePoint Online**報表運作，需要滿足下列條件：

* Power BI Pro 授權或[（EM 或 P SKU） 的 Power BI Premium 容量](service-premium-what-is.md)與 Power BI 授權。
* SharePoint Online 的 Power BI Web 組件需要[新式網頁](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)。

## <a name="embed-your-report"></a>內嵌報表
若要將報表嵌入 SharePoint Online，您需要取得報表的 URL，並將它與 SharePoint Online 的新的 Power BI web 組件。

### <a name="get-a-report-url"></a>取得報表的 URL

1. Power BI 中檢視報表。

2. 選取 **檔案**下拉式功能表中，然後選取**內嵌於 SharePoint Online**。

    ![[檔案] 功能表](media/service-embed-report-spo/powerbi-file-menu.png)

3. 從對話方塊複製報表 URL。

    ![內嵌連結](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>將 Power BI 報表新增至 SharePoint Online 頁面

1. 在 SharePoint Online 中開啟 [目標] 頁面，然後選取**編輯**。

    ![SP 編輯頁面](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    或者，在 Sharepoint Online 中，選取 **+ 新增**來建立新的新式網站頁面。

    ![SP 新增頁面](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. 選取  **+** 下拉式清單中，然後選取**Power BI**。

    ![SP 新增網頁組件](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. 選取 [新增報告]  。

    ![SP 新報表](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. 貼上先前複製的報表 URL 傳送至**Power BI 報告連結**窗格。 報表會自動載入。

    ![SP 新增網頁組件屬性](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. 選取 [發佈]  ，讓 SharePoint Online 使用者能看見您所做的變更。

    ![載入的 SP 報表](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>授與報告存取權

在 SharePoint Online 中內嵌報表不會自動讓使用者檢視報表的權限，您需要設定 Power BI 中的檢視權限。

> [!IMPORTANT]
> 請務必檢閱可以看到 Power BI 服務內報表的成員，並將存取權授與未列出的成員。

有兩種方式可提供在 Power BI 中的報表存取權。 第一種方式，如果您使用 Office 365 群組來建置 SharePoint Online 小組網站，是要將使用者列為隸屬**Power BI 服務中的應用程式工作區**並**SharePoint 頁面**。 如需詳細資訊，請參閱如何[管理應用程式工作區](service-manage-app-workspace-in-power-bi-and-office-365.md)。

第二種方式是內嵌在報表中的應用程式，並直接與使用者共用：  

1. 應用程式工作區中的作者 （必須為 Pro 使用者） 建立報表。 若要將分享**Power BI 免費使用者**，應用程式工作區必須設為**Premium 工作區**。

2. 作者發行應用程式，並將其安裝。 作者必須確定安裝應用程式能夠存取 SharePoint Online 中內嵌報表 URL。

3. 現在，所有使用者也都需要安裝應用程式。 您也可以使用**自動安裝應用程式**功能，您可以在啟用[Power BI 管理入口網站](service-admin-portal.md)，以預先安裝的終端使用者應用程式。

   ![自動安裝應用程式](media/service-embed-report-spo/install-app-automatically.png)

4. 作者開啟應用程式，並移至報表。

5. 作者會複製報表安裝的應用程式中內嵌報表 URL。 **請勿使用原始的報表 URL 從應用程式工作區。**

6. 在 SharePoint Online 中建立新的小組網站。

7. 將先前複製的報表 URL 新增至 Power BI web 組件中。

8. 新增要使用您建立的 Power BI 應用程式中 SharePoint Online 頁面上之資料的所有使用者和/或群組。

    > [!NOTE]
    > **使用者或群組需要存取 SharePoint Online 頁面，及 Power BI 應用程式中的報表，才能看到 SharePoint 頁面上的報表。**

現在使用者可以移至 SharePoint Online 中的小組網站，並在頁面上檢視報表。

## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

如果您的 Power BI 環境需要您使用多重要素驗證進行登入，您可能會受要求使用安全性裝置進行登入，以驗證您的身分識別。 會發生這種情況是如果您未登入 SharePoint online 使用多重要素驗證，但您的 Power BI 環境需要安全性裝置來驗證帳戶。

> [!NOTE]
> Azure Active Directory 2.0 不支援多重要素驗證-使用者會看到一則錯誤訊息。 如果使用者使用其安全性裝置再次登入 SharePoint Online ，則可以檢視報表。

## <a name="web-part-settings"></a>網頁組件設定

以下是您可以調整 SharePoint Online 的 Power BI web 組件的設定。

![SP 網頁組件屬性](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| 屬性 | 描述 |
| --- | --- |
| 頁面名稱 |設定 web 組件的預設頁面。 從下拉式清單中選取一個值。 如果沒有顯示任何頁面，可能是您的報表只有一個頁面，或您所貼上的 URL 包含頁面名稱。 從 URL 移除報表區段，以選取特定頁面。 |
| 顯示 |調整報表如何符合 SharePoint Online 的頁面。 |
| 顯示瀏覽窗格 |顯示或隱藏頁面功能窗格。 |
| 顯示篩選窗格 |顯示或隱藏篩選窗格。 |

## <a name="reports-that-do-not-load"></a>不會載入的報表

如果您的報表不會載入 Power BI 網頁組件內，您可能會看到下列訊息：

![此內容不是可用的訊息](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

有兩個常見的原因會導致此訊息的出現。

1. 您無法存取報表。
2. 報表已刪除。

請連絡 SharePoint Online 頁面擁有者，以協助您解決問題。

## <a name="licensing"></a>授權

在 SharePoint 中檢視報表的使用者需要 **Power BI Pro 授權**，或者內容需要位於 **[Power BI Premium 容量 (EM 或 P SKU)](service-admin-premium-purchase.md)** 的工作空間中。

## <a name="known-issues-and-limitations"></a>已知的問題及限制

* 錯誤：「An error occurred, please try logging out and back in and then revisiting this page. (發生錯誤。請登出再登入，然後再次前往此頁面。) 相互關聯識別碼: 未定義，http 回應狀態:400，伺服器錯誤碼 10001，訊息:遺漏重新整理權杖」
  
  如果您收到這個錯誤，請嘗試下列其中一個疑難排解步驟。
  
  1. 登出再登入 SharePoint。 請務必關閉所有瀏覽器視窗，然後再重新登入。

  2. 如果您的使用者帳戶需要多重要素驗證 (MFA)，然後登入 SharePoint 使用 MFA 裝置 （手機應用程式、 智慧卡等）。
  
  3. 不支援 Azure B2B 來賓使用者帳戶。 使用者看到的 Power BI 標誌會顯示載入的部分，但不會顯示報表。

* Power BI 與 SharePoint Online 支援的當地語系化語言不盡相同。 因此，您可能會在內嵌報表中看到未適當當地語系化的內容。

* 您若使用 Internet Explorer 10，可能會遇到問題。 您可以參閱 [Power BI](consumer/end-user-browsers.md) 及 [Office 365](https://products.office.com/office-system-requirements#Browsers-section) 的瀏覽器支援。

* [國家/地區雲端](https://powerbi.microsoft.com/clouds/)不提供 Power BI Web 組件。

* 此 Web 組件不支援傳統的 SharePoint 伺服器。

* [URL 篩選](service-url-filters.md)不受到 SPO Web 組件支援。

## <a name="next-steps"></a>後續步驟

* [允許或防止終端使用者建立新式網站頁面](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [在 Power BI 中建立和散發應用程式](service-create-distribute-apps.md)  
* [Share a dashboard with colleagues and others](service-share-dashboards.md) (與同事和其他人共用儀表板)  
* [什麼是 Power BI Premium？](service-premium-what-is.md)
* [在安全入口網站或網站中內嵌報告](service-embed-secure.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)