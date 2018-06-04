---
title: 使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者
description: Power BI 會與 Azure Active Directory 企業對企業 (Azure AD B2B) 整合，以便能夠安全地將 Power BI 內容散發給組織外部的來賓使用者。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 6e1665b6e9c9ff0a756d9ccdaf9e6feb4ed9eb39
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722216"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者

Power BI 會與 Azure Active Directory 企業對企業 (Azure AD B2B) 整合，以便能夠安全地將 Power BI 內容散發給組織外部的來賓使用者，同時維持對內部資料的控制能力。

> [!VIDEO https://www.youtube.com/embed/xxQWEQ1NnlY]

> [!NOTE]
> 您需要先 [啟用] Power BI 管理員入口網站租用戶設定中的[匯出及共用設定](service-admin-portal.md#export-and-sharing-settings)功能，再邀請來賓使用者。

> [!NOTE]
> Power BI 行動應用程式目前無法提供這項功能。 在行動裝置上，您可以在瀏覽器中檢視使用 Azure AD B2B 所共用的 Power BI 內容。 

## <a name="who-can-you-invite"></a>您可以邀請哪些人？

您可以邀請使用任何電子郵件地址的來賓使用者，包括 gmail.com、outlook.com 或 hotmail.com 等個人帳戶。 在 Azure B2B 中，這些稱為「社交識別碼」。 如需詳細資訊，請參閱 [Azure B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)。

## <a name="invite-guest-users"></a>邀請來賓使用者

有兩種方式可邀請來賓使用者前往您的 Power BI 租用戶：計劃性邀請或臨時邀請。 第一次邀請外部使用者前往您的組織時才需要提出邀請。

### <a name="planned-invites"></a>計劃性邀請

計劃性邀請會在 Microsoft Azure 入口網站中，於 Azure AD 中或使用 PowerShell 來進行。 如果您知道必須邀請的使用者有哪些人，便可使用此選項。 

**若要在 Azure AD 入口網站中建立來賓使用者，您必須是租用戶管理員。**

1. 瀏覽至 [Azure 入口網站](https://portal.azure.com)，然後選取 [Azure Active Directory]。

2. 瀏覽至 [使用者和群組] > [所有使用者] > [新增來賓使用者]。

    ![Azure AD 入口網站 - 新增來賓使用者](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

3. 輸入 [電子郵件地址] 和 [個人訊息]。

    ![Azure AD 入口網站 - 新增來賓使用者邀請訊息](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

4. 選取 [邀請]。

若要邀請多位來賓使用者，請使用 PowerShell。 如需詳細資訊，請參閱 [Azure Active Directory B2B 共同作業程式碼和 PowerShell 範例](https://docs.microsoft.com/azure/active-directory/b2b/code-samples)。

來賓使用者必須在其收到的電子郵件邀請中選取 [開始使用]。 系統便會將來賓使用者新增至租用戶。

![來賓使用者的電子郵件邀請](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>臨時邀請

若要隨時執行邀請，請透過共用 UI 將外部使用者新增至您的儀表板或報表，或透過存取頁面新增至您的應用程式。

以下範例是邀請外部使用者使用應用程式時該執行的作業。
![新增至應用程式存取清單的外部使用者](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

來賓使用者會收到電子郵件，內容指出您已與其共用應用程式。

![指出已與來賓使用者共用應用程式的電子郵件](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

來賓使用者必須使用其組織電子郵件地址來登入。 登入之後，系統會提示他們接受邀請。 來賓使用者登入之後，系統會將其重新導向至應用程式內容。 若要返回應用程式，請將連結加入書籤，或儲存電子郵件。

## <a name="licensing"></a>授權

來賓使用者必須備有適當授權才能檢視共用的應用程式。 您有三個選項可供完成這項作業。

### <a name="use-power-bi-premium"></a>使用 Power BI Premium

將應用程式工作區指派給 Power BI Premium 容量會讓來賓使用者能夠使用應用程式，而不需要 Power BI Pro 授權。 Power BI Premium 還可讓應用程式充分利用其他功能，像是增加的重新整理頻率、專用的容量和大型模型大小等。

![使用 Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-power-bi-pro-license-to-guest-user"></a>將 Power BI Pro 授權指派給來賓使用者

將 Power BI Pro 授權指派給您租用戶中的來賓使用者，可讓該來賓使用者檢視內容。

> [!NOTE]
> 只有在來賓使用者存取您租用戶中的內容時，來自您租用戶的 Power BI Pro 授權才會適用於來賓使用者。

![從租用戶指派 Pro 授權](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>來賓使用者帶來自己的 Power BI Pro 授權

來賓使用者已在其租用戶內獲派 Power BI Pro 授權。

![來賓使用者帶來自己的授權](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>考量與限制

* 當您邀請使用 gmail.com、outlook.com 或 hotmail.com 等個人電子郵件帳戶的來賓使用者時，您可以觀看這段示範[內嵌影片](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-redemption-experience)了解使用者如何註冊。
* 外部 B2B 來賓限制於僅限內容耗用。 外部 B2B 來賓可以檢視應用程式、儀表板和報表、匯出資料，並建立儀表板和報表的電子郵件訂用帳戶。 他們無法存取工作區或發行其專屬內容。
* Power BI 行動應用程式目前無法提供這項功能。 在行動裝置上，您可以在瀏覽器中檢視使用 Azure AD B2B 所共用的 Power BI 內容。
* Power BI SharePoint Online 報表網頁組件目前不提供這項功能。

## <a name="next-steps"></a>後續步驟

如需詳細資訊 (包括資料列層級安全性的運作方式)，請參閱[白皮書](https://aka.ms/powerbi-b2b-whitepaper)。

如需有關 Azure Active Directory B2B 的資訊，請參閱[什麼是 Azure AD B2B 共同作業？](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)
