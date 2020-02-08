---
title: 使用 Azure AD B2B 將內容散發給外部來賓使用者
description: Power BI 會與 Azure Active Directory 企業對企業 (Azure AD B2B) 整合，以便能夠安全地將 Power BI 內容散發給組織外部的來賓使用者。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 2a17e4963d4607b67279f65205579e115df2e550
ms.sourcegitcommit: 75300b3f53f438ed7d3bd4edc93b9eb5925bf3af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2020
ms.locfileid: "77026638"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者

Power BI 會與 Azure Active Directory 企業對企業 (Azure AD B2B) 整合，讓 Power BI 內容能以安全散發的方式提供給組織外的來賓使用者，同時維持對內部資料的控制能力。 此外，您可以允許外部來賓使用者編輯和管理組織中的內容。

本文提供 Power BI 中 Azure AD B2B 的基本簡介。 如需詳細資訊，請參閱[使用 Azure Active Directory B2B 將 Power BI 內容散發給外部來賓使用者](whitepaper-azure-b2b-power-bi.md)。

## <a name="enable-access"></a>啟用存取

在邀請來賓使用者之前，請務必確認已在 Power BI 管理入口網站中啟用[與外部使用者共用內容](service-admin-portal.md#export-and-sharing-settings)的功能。 即使已啟用此選項，使用者在 Azure Active Directory 中必須具有邀請使用者的權限，這可以透過來賓邀請者角色授與。 

您也可以使用[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能。 這能讓您挑選出可在工作區中看見並建立內容的來賓，這些來賓也能瀏覽您組織的 Power BI。

> [!NOTE]
> [與外部使用者共用內容](service-admin-portal.md#export-and-sharing-settings)設定能控制是否可以透過 Power BI 邀請外部使用者到您的組織。 當外部使用者接受邀請時，他們便會成為您組織中的 Azure AD B2B 來賓使用者。 他們會出現在 Power BI 體驗中的所有人員選擇器中。 停用此設定時，您組織中的現有來賓使用者將能繼續存取他們先前可存取的所有項目，並繼續列在人員選擇器體驗中。 此外，如果來賓是透過計劃性邀請方法新增，他們也會出現在人員選擇器中。 若要防止來賓使用者存取 Power BI，可以使用 Azure AD 條件式存取原則。

## <a name="who-can-you-invite"></a>您可以邀請哪些人？

您可以邀請大多數電子郵件地址的來賓使用者，包括 gmail.com、outlook.com 和 hotmail.com 等個人帳戶。 Azure AD B2B 會將這些地址稱為「社交身分識別」  。

您無法邀請與政府雲端建立關聯的使用者，例如[適用於美國政府的 Power BI](service-govus-overview.md)。

## <a name="invite-guest-users"></a>邀請來賓使用者

您只需在首次邀請來賓使用者存取您組織時傳送邀請給他們。 邀請使用者的方法有兩種：計劃性邀請和臨時邀請。

您可以在 Power BI 中透過下列功能邀請來賓使用者：
* 報表和儀表板共用
* 應用程式存取清單

如果您需要將尚未成為您 Azure AD 中來賓的外部使用者新增到工作區，您可以使用下列建議的計劃性邀請。 

### <a name="planned-invites"></a>計劃性邀請

如果您知道要邀請哪些使用者，可以使用計劃性邀請。 您可以使用 Azure 入口網站或 PowerShell 來傳送邀請。 您必須是租用戶系統管理員才能邀請人員。

請遵循下列步驟，以在 Azure 入口網站中傳送邀請。

1. 在 [Azure 入口網站](https://portal.azure.com) 中，選取 [Azure Active Directory]  。

1. 在 [管理]  底下，選取 [使用者]   > [所有使用者]   > [新增來賓使用者]  。

    ![顯示 [新增來賓使用者] 選項的 Azure 入口網站螢幕擷取畫面。](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. 輸入 [電子郵件地址]  和 [個人訊息]  。

    ![Azure AD 入口網站 [新增來賓使用者] 對話方塊的螢幕擷取畫面。](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. 選取 [邀請]  。

若要邀請多位來賓使用者，請使用 PowerShell。 如需詳細資訊，請參閱 [Azure AD B2B 共同作業程式碼和 PowerShell 範例](/azure/active-directory/b2b/code-samples/)。

來賓使用者必須在其收到的電子郵件邀請中選取 [開始使用]  。 系統便會將來賓使用者新增至租用戶。

![來賓使用者電子郵件邀請的螢幕擷取畫面。](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>臨時邀請

若要隨時邀請外部使用者，請透過共用 UI 將他們新增至您的儀表板或報表，或透過存取頁面新增至您的應用程式。 以下範例是邀請外部使用者使用應用程式時該執行的作業。

![將外部使用者新增至 Power BI 中應用程式存取清單的螢幕擷取畫面。](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

來賓使用者將會收到電子郵件，指出您已與他們共用應用程式。

![已與來賓使用者共用應用程式的電子郵件螢幕擷取畫面](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

來賓使用者必須使用其組織電子郵件地址來登入。 系統會在他們登入之後提示他們接受邀請。 登入之後，系統會為來賓使用者開啟應用程式。 若要返回應用程式，他們可將連結加入書籤，或儲存電子郵件。


## <a name="licensing"></a>授權

來賓使用者必須有適當授權才能檢視您所共用的內容。 有三種選項可以確定使用者具有適當授權：使用 Power BI Premium、指派 Power BI Pro 授權，或使用來賓的 Power BI Pro 授權。

使用[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能時，來賓使用者必須具備 Power BI Pro 授權才能提供工作區的內容，或與其他人共用內容。

### <a name="use-power-bi-premium"></a>使用 Power BI Premium

將工作區指派給 [Power BI Premium 容量](service-premium-what-is.md)能讓來賓使用者使用應用程式，而不需要 Power BI Pro 授權。 Power BI Premium 還可讓應用程式充分利用其他功能，像是增加重新整理頻率、專用容量和大型模型等。

![搭配 Power BI Premium 之來賓使用者體驗的圖表。](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>將 Power BI Pro 授權指派給來賓使用者

將 Power BI Pro 授權指派給您租用戶中的來賓使用者，可讓該來賓使用者在租用戶中檢視內容。 如需指派授權的詳細資訊，請參閱[在 [授權] 頁面上將授權指派給使用者](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page)。 將 Pro 授權指派給來賓使用者之前，請連絡您的 Microsoft 帳戶代表，以確保您符合 Microsoft 合約條款的規範。

![從您的租用戶指派 Pro 授權之來賓使用者體驗的圖表。](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>來賓使用者帶來自己的 Power BI Pro 授權

來賓使用者已在其租用戶內獲派 Power BI Pro 授權。

![來賓使用者攜帶自己的授權時之體驗的圖表。](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>可以編輯和管理內容的來賓使用者

使用[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能時，所指定的來賓使用者將能獲得您組織的 Power BI 存取權。 他們可以查看自己具有權限的任何內容。 他們可以存取首頁、瀏覽工作區、安裝應用程式、查看自己在存取清單上的位置，並為工作區貢獻內容。 針對使用新工作區體驗的工作區，他們可以建立工作區管理員，或是成為工作區管理員。 適用某些限制。 ＜考量與限制＞一節會列出那些限制。
 
若要協助這些使用者登入 Power BI，請將租用戶 URL 提供給他們。 若要尋找租用戶 URL，請遵循下列步驟。

1. 在 Power BI 服務的頂端功能表中，選取說明 ( **?** )，然後選取 [關於 About Power BI]  。

2. 尋找 [租用戶 URL]  旁邊的值。 此值是您可以與來賓使用者共用的租用戶 URL。

    ![顯示來賓使用者租用戶 URL 之 [關於 Power BI] 對話方塊的螢幕擷取畫面。](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>考量與限制

* 根據預設，外部 Azure AD B2B 會將來賓限制為僅能使用內容。 外部 Azure AD B2B 來賓可以檢視應用程式、儀表板、報表、匯出資料，並針對儀表板和報表建立電子郵件訂閱。 他們無法存取工作區或發行其專屬內容。 不過，如果來賓使用者是透過[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能來獲得存取權，即不適用這些限制。

* 若要邀請來賓使用者，則需要 Power BI Pro 授權。 Pro 試用版使用者無法在 Power BI 中邀請來賓使用者。

* 如果來賓使用者是透過[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization)功能來啟用，則無法使用某些體驗。 若要更新或發佈報表，他們需要使用 Power BI 服務 Web UI，包括 [取得資料] 以上傳 Power BI Desktop 檔案。  不支援下列體驗：
    * 從 Power BI Desktop 直接發佈至 Power BI 服務
    * 來賓使用者無法使用 Power BI Desktop 來連線至 Power BI 服務中的服務資料集
    * 繫結至 Office 365 群組的典型工作區：
        * 來賓使用者無法建立這些工作區，或是成為這些工作區的管理員
        * 來賓使用者可以成為成員
    * 工作區的存取清單不支援傳送臨時邀請
    * Power BI Publisher for Excel 不支援來賓使用者
    * 來賓使用者無法安裝 Power BI Gateway，並將它連線至您的組織
    * 來賓使用者無法安裝應用程式並發佈到整個組織
    * 來賓使用者無法使用、建立、更新或安裝組織內容套件
    * 來賓使用者無法使用 [使用 Excel 分析]
    * 無法在註解中對來賓使用者進行 @mentioned
    * 來賓使用者無法使用訂用帳戶
    * 如果來賓使用者要使用這項功能，則應具備工作或學校帳戶。 
    
* 基於登入限制，使用個人帳戶的來賓使用者將會受到更多限制。
    * 來賓使用者可以透過網頁瀏覽器來使用 Power BI 服務中的使用體驗
    * 其無法使用 Power BI 行動版應用程式。
    * 他們將無法登入來提供需要公司或學校帳戶的認證。

* Power BI SharePoint Online 報表網頁組件目前不提供此功能。

* Active Directory 的設定可能會限制外部來賓使用者所能在整體組織內完成的作業。 那也適用於您的 Power BI 環境。 下列文件會討論這些設定：
    * [管理外部共同作業設定](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [允許或封鎖對特定組織 B2B 使用者的邀請](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)
    * [允許或封鎖來賓使用者存取 Power BI 服務](/azure/active-directory/conditional-access/overview)
    
* 國家雲端不支援在組織外部共用。 相反地，請在組織中建立使用者帳戶，以供外部使用者用來存取內容。 

## <a name="next-steps"></a>後續步驟

如需詳細資訊，包括資料列層級安全性的運作方式，請參閱白皮書：[使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者](https://aka.ms/powerbi-b2b-whitepaper)。

如需有關 Azure AD B2B 的相關資訊，請參閱[什麼是 Azure AD B2B 共同作業？](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/)。
