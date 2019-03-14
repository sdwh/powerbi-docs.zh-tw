---
title: 使用 Azure AD B2B 將內容散發給外部來賓使用者
description: Power BI 會與 Azure Active Directory 企業對企業 (Azure AD B2B) 整合，以便能夠安全地將 Power BI 內容散發給組織外部的來賓使用者。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0eba54212ff9349ed75d9d9fb18878b39d5cd29a
ms.sourcegitcommit: 378265939126fd7c96cb9334dac587fc80291e97
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/07/2019
ms.locfileid: "57580189"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者

Power BI 會與 Azure Active Directory 企業對企業 (Azure AD B2B) 整合，讓 Power BI 內容能以安全散發的方式提供給組織外的來賓使用者，同時維持對內部資料的控制能力。  

此外，您可以允許外部來賓使用者編輯和管理組織中的內容。

## <a name="enable-access"></a>啟用存取

在邀請來賓使用者之前，請先確認已在 Power BI 管理入口網站中啟用[與外部使用者共用內容](service-admin-portal.md#export-and-sharing-settings)的功能。

此外，[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#export-and-sharing-settings)功能可讓您選取哪些來賓使用者可以在工作區中查看與建立內容，包括瀏覽您組織的 Power BI。

## <a name="who-can-you-invite"></a>您可以邀請哪些人？

您可以邀請使用任何電子郵件地址的來賓使用者，包括 gmail.com、outlook.com 和 hotmail.com 等個人帳戶。 在 Azure AD B2B 中，這些地址稱為「社交身分識別」。

## <a name="invite-guest-users"></a>邀請來賓使用者

只有第一次邀請外部來賓使用者到您的組織時，才需要邀請。 邀請使用者的方法有兩種：計劃性邀請和臨時邀請。

### <a name="planned-invites"></a>計劃性邀請

如果您知道要邀請哪些使用者，可以使用計劃性邀請。 您可以使用 Azure 入口網站或 PowerShell 來傳送邀請。 您必須是租用戶系統管理員才能邀請人員。

請遵循下列步驟，以在 Azure 入口網站中傳送邀請。

1. 在 [Azure 入口網站](https://portal.azure.com) 中，選取 [Azure Active Directory]。

1. 在 [管理] 底下，移至 [使用者] > [所有使用者] > [新增來賓使用者]。

    ![Azure AD 入口網站 - 新增來賓使用者](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. 輸入 [電子郵件地址] 和 [個人訊息]。

    ![Azure AD 入口網站 - 新增來賓使用者邀請訊息](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. 選取 [邀請]。

若要邀請多位來賓使用者，請使用 PowerShell。 如需詳細資訊，請參閱 [Azure AD B2B 共同作業程式碼和 PowerShell 範例](/azure/active-directory/b2b/code-samples/)。

來賓使用者必須在其收到的電子郵件邀請中選取 [開始使用]。 系統便會將來賓使用者新增至租用戶。

![來賓使用者的電子郵件邀請](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>臨時邀請

若要隨時執行邀請，請透過共用 UI 將外部使用者新增至您的儀表板或報表，或透過存取頁面新增至您的應用程式。 以下範例是邀請外部使用者使用應用程式時該執行的作業。

![外部使用者新增至應用程式的存取清單](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

來賓使用者會收到電子郵件，內容指出您已將應用程式與他們共用。

![指出已與來賓使用者共用應用程式的電子郵件](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

來賓使用者必須使用其組織電子郵件地址來登入。 登入之後，系統會提示他們接受邀請。 來賓使用者登入之後，系統會將其重新導向至應用程式內容。 若要返回應用程式，他們可將連結加入書籤，或儲存電子郵件。

## <a name="licensing"></a>授權

來賓使用者必須有適當授權才能檢視共用的內容。 有三種選項可以符合此條件：使用 Power BI Premium、指派 Power BI Pro 授權，或使用來賓的 Power BI Pro 授權。

使用[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#export-and-sharing-settings)功能時，來賓使用者必須具備 Power BI Pro 授權才能提供工作區的內容，或與其他人共用內容。

### <a name="use-power-bi-premium"></a>使用 Power BI Premium

將應用程式工作區指派給 [Power BI Premium 容量](service-premium.md)會讓來賓使用者能夠使用應用程式，而不需要 Power BI Pro 授權。 Power BI Premium 還可讓應用程式充分利用其他功能，像是增加的重新整理頻率、專用的容量和大型模型大小等。

![使用 Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>將 Power BI Pro 授權指派給來賓使用者

將 Power BI Pro 授權指派給您租用戶中的來賓使用者，可讓該來賓使用者在租用戶中檢視內容。

![從租用戶指派 Pro 授權](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>來賓使用者帶來自己的 Power BI Pro 授權

來賓使用者已在其租用戶內獲派 Power BI Pro 授權。

![來賓使用者帶來自己的授權](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>可以編輯和管理內容的來賓使用者 

使用[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#export-and-sharing-settings)時，所指定來賓使用者可獲得您組織的 Power BI 存取權，並查看他們有權查看的任何內容。 他們可以存取首頁、瀏覽工作區、安裝存取清單上的應用程式，並提供工作區的內容。 針對使用新工作區體驗的工作區，他們可以建立工作區管理員，或是成為工作區管理員。 ＜考量與限制＞一節列出套用的部分限制。

若要協助這些使用者登入 Power BI，請將租用戶 URL 提供給他們。 若要尋找租用戶 URL，請遵循下列步驟。

1. 在 Power BI 服務的頂端功能表中，選取說明 (**?**)，然後選取 [關於 About Power BI]。

2. 尋找 [租用戶 URL] 旁邊的值。 這是您可以與來賓使用者共用的租用戶 URL。

![來賓使用者租用戶 URL](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>考量與限制

* 根據預設，外部 B2B 來賓限制為僅能使用內容。 外部 B2B 來賓可以檢視應用程式、儀表板和報表、匯出資料，並建立儀表板和報表的電子郵件訂用帳戶。 他們無法存取工作區或發行其專屬內容。 不過，如果來賓使用者是透過[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#export-and-sharing-settings)租用戶設定來獲得允許，即不適用這些限制。

* 如果來賓使用者是透過[允許外部來賓使用者編輯和管理組織中的內容](service-admin-portal.md#export-and-sharing-settings)租用戶設定來啟用，則無法使用某些體驗。 若要更新或發佈報表，他們需要使用 Power BI 服務 Web UI，包括 [取得資料] 以上傳 Power BI Desktop 檔案。  不支援下列體驗：
    * 從 Power BI Desktop 直接發佈至 Power BI 服務
    * 來賓使用者無法使用 Power BI Desktop 連接到 Power BI 服務中的服務資料集
    * 繫結至 Office 365 群組的典型工作區：來賓使用者無法建立這些工作區的管理員，或成為這些工作區的管理員。 他們可以是成員。
    * 工作區的存取清單不支援傳送臨時邀請
    * Power BI Publisher for Excel 不支援來賓使用者
    * 來賓使用者無法安裝 Power BI Gateway，並將它連接到您的組織
    * 來賓使用者無法安裝應用程式並發佈到整個組織
    * 來賓使用者無法使用、建立、更新或安裝組織內容套件
    * 來賓使用者無法使用 [使用 Excel 分析]
    * 來賓使用者不可為註解中的 @mentioned
    * 來賓使用者不能使用訂用帳戶
    * 如果來賓使用者要使用這項功能，則應具備工作或學校帳戶。 由於有登入限制，因此使用個人帳戶的來賓使用者會受限更多。

* Power BI SharePoint Online 報表網頁組件目前不提供這項功能。

* Active Directory 設定可能會限制外部來賓使用者得以在整體組織內完成哪些作業，而這些設定也適用於您的 Power BI 環境。 下列文件會討論這些設定：
    * [管理外部共同作業設定](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [允許或封鎖對特定組織 B2B 使用者的邀請](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>後續步驟

如需詳細資訊，包括資料列層級安全性的運作方式，請參閱白皮書：[使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者](https://aka.ms/powerbi-b2b-whitepaper)。

如需有關 Azure AD B2B 的資訊，請參閱[什麼是 Azure AD B2B 共同作業？](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/)。
