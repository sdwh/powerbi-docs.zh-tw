---
title: 管理 Power BI - 常見問題集 (FAQ)
description: 了解 Power BI 註冊、 租用戶管理，以及其他管理工作的相關常見問題的答案。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2e51017333a940bd9d7838e6a903c1a66ce2e342
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100766"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>管理 Power BI - 常見問題集 (FAQ)

本文可解決 Power BI 管理的常見問題。 如需 Power BI 管理的概觀，請參閱[什麼是 Power BI 管理？](service-admin-administering-power-bi-in-your-organization.md)。

## <a name="whats-in-this-article"></a>本文內容

### <a name="sign-up-for-power-bi-section"></a>註冊 Power BI 小節

* [使用 PowerShell](#using-powershell)
* [使用者如何註冊 Power BI？](#how-do-users-sign-up-for-power-bi)
* [個人使用者如何在我的組織中註冊？](#how-do-individual-users-in-my-organization-sign-up)
* [我該如何防止使用者加入現有的 Office 365 租用戶？](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [我該如何允許使用者加入現有的 Office 365 租用戶？](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [如何檢查如果我開啟了封鎖租用戶？](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [我該如何不讓現有的使用者開始使用 Power BI？](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [我要如何允許現有的使用者註冊 Power BI？](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Power BI 的系統管理小節

* [這會怎麼改變我目前管理組織中使用者身分識別的方式？](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [要如何管理 Power BI？](#how-do-we-manage-power-bi)
* [管理 Microsoft 為使用者所建之租用戶的程序為何？](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [如果有多個網域，我可以控制使用者新增至 Office 365 租用戶？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [如何移除已註冊使用者的 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [我如何知道有新的使用者加入我的租用戶？](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [有我應該準備的任何其他項目嗎？](#are-there-any-additional-things-i-should-prepare-for)
* [我的 Power BI 租用戶位於何處？](#where-is-my-power-bi-tenant-located)
* [什麼是 Power BI SLA (服務等級協定)？](#what-is-the-power-bi-sla)
* [Power BI 如何處理高可用性和容錯移轉？](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Power BI 中的安全性小節

* [Power BI 是否符合國家、地區和業界的特定法規要求？](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Power BI 安全性如何運作？](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>註冊 Power BI

### <a name="using-powershell"></a>使用 PowerShell

此節中的一些程序需要 Windows PowerShell 指令碼。 如果您不熟悉 PowerShell，我們建議您參閱 [PowerShell 入門手冊](http://go.microsoft.com/fwlink/p/?LinkID=286814)。 若要執行指令碼，請先安裝[適用於 Graph 的 Azure Active Directory PowerShell](/powershell/azure/active-directory/) 的最新 64 位元版本。

### <a name="how-do-users-sign-up-for-power-bi"></a>使用者如何註冊 Power BI？

身為管理員，您可以註冊 Power BI 透過[Power BI 網站](https://powerbi.microsoft.com)或[購買服務](https://admin.microsoft.com/AdminPortal/Home#/catalog)頁面上的 Microsoft 365 系統管理中心。 當系統管理員註冊 Power BI 時，他們可以指派使用者授權，應該可以存取的使用者。

貴組織中的個人使用者也可以透過 [Power BI 網站](https://powerbi.microsoft.com)註冊 Power BI。 當您的組織中的使用者註冊 Power BI 時，服務會自動指派 Power BI 授權給使用者。 如需詳細資訊，請參閱 <<c0> [ 註冊 Power BI 以個人身分](service-self-service-signup-for-power-bi.md)並[Power BI 授權您組織中](service-admin-licensing-organization.md)。

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>個人使用者如何在我的組織中註冊？

貴組織使用者有三種適用案例︰

* **案例 1**︰您的組織已有現有的 Office 365 環境，且註冊 Power BI 的使用者已有 Office 365 帳戶。
    在此案例中，如果使用者已經有工作或學校帳戶，在租用戶 (例如，contoso.com) 但還具有 Power BI，Microsoft 只會啟用該帳戶的計劃。 有關如何使用 Power BI 服務的資訊會自動通知使用者。

* **案例 2**︰您的組織有現有的 Office 365 環境，但註冊 Power BI 的使用者沒有 Office 365 帳戶。
    在此案例中，使用者會在貴組織的網域 (例如，contoso.com) 中有電子郵件地址，但還沒有 Office 365 帳戶。 在此情況下，使用者可以註冊 Power BI，且會自動獲得帳戶。 此動作可讓使用者存取 Power BI 服務。 例如，如果員工 nancy 使用她的工作電子郵件地址 (例如nancy@contoso.com) 若要註冊，Microsoft 會自動將 Nancy 新增為 Contoso 的 Office 365 環境中的使用者與該帳戶啟用 Power BI。

* **案例 3**︰您的組織沒有連接到您的電子郵件網域的 Office 365 環境。
    沒有您利用 Power BI 的組織所需的系統管理動作。 服務會將使用者加入新的、 僅限雲端使用者的目錄。 您也可以選擇以租用戶系統管理員身分接管，並加以管理。

> [!IMPORTANT]
> 如果貴組織有多個電子郵件網域，而您希望所有的電子郵件地址擴充功能都在相同的租用戶中，請先將所有電子郵件地址網域新增至 Azure Active Directory 租用戶中，再讓使用者註冊。 一旦您已建立使用者，沒有任何自動化的機制，以租用戶之間移動。 如需此程序的詳細資訊，請參閱[如果我有多個網域，我可以控制使用者新增至 Office 365 租用戶？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)本文稍後並[將網域新增至 Office 365](/office365/admin/setup/add-domain/)。

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>我該如何防止使用者加入現有的 Office 365 租用戶？

身為系統管理員，您可以採取幾個步驟不讓使用者加入現有的 Office 365 租用戶。 如果您封鎖存取，使用者嘗試登入失敗，並出現訊息，引導他們連絡組織的系統管理員。您不需要重複此程序，如果您已停用自動授權發佈 （例如，透過 Office 365 教育學生、 教職人員及員工)。

您可以使用下列 PowerShell 指令碼來防止新使用者加入受控租用戶。 ([深入了解 PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> 封鎖存取會防止您組織的新使用者註冊 Power BI。 在您停用組織的新註冊前即已註冊 Power BI 的使用者，仍然保留其授權。 若要移除使用者，請參閱此文章稍後的[如何移除已註冊使用者的 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)。

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>我該如何允許使用者加入現有的 Office 365 租用戶？

您可以使用下列 PowerShell 指令碼，讓新使用者加入受管理的租用戶。 ([深入了解 PowerShell][1])。

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>如何檢查如果我開啟了封鎖租用戶？

您可以使用下列 PowerShell 指令碼來檢查設定。 *AllowEmailVerifiedUsers* 應為 false。 ([深入了解 PowerShell][1])。

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>我該如何不讓現有的使用者開始使用 Power BI？

控制此項的 Azure AD 設定是 **AllowAdHocSubscriptions**。 大多數的租用戶已設定為 true，這表示它已啟用此行為。 如果您透過合作夥伴取得 Power BI，這會設定為 false，這表示它已停用。

您可以使用下列 PowerShell 指令碼來停用特定訂閱。 ([深入了解 PowerShell][1])。

1. 使用 Office 365 認證登入 Azure Active Directory。 下列 PowerShell 指令碼的第一行會提示您輸入您的認證。 第二行連接到 Azure Active Directory。

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![透過 PowerShell 的螢幕擷取畫面的 Azure Active Directory 登入](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. 一旦您登入，執行下列命令以查看您的租用戶的目前設定方式。

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. 執行下列命令，以啟用 (`$true`) 或停用 (`$false`) **AllowAdHocSubscriptions**。

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> 使用**AllowAdHocSubscriptions**旗標，以控制您的組織，包括可讓使用者登入，以 Azure Rights Management service 中的數個使用者功能。 變更此旗標會影響所有這些功能。

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>我要如何允許現有的使用者註冊 Power BI？

若要讓現有使用者註冊 Power BI 中，執行命令列的上一個問題，但傳遞`$true`而不是`$false`最後一個步驟。

## <a name="administration-of-power-bi"></a>管理 Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>這會怎麼改變我目前管理組織中使用者身分識別的方式？

貴組織使用者有三種適用案例︰

* **案例 1**︰如果貴組織已有現有的 Office 365 環境，並在您的組織中的所有使用者都擁有 Office 365 帳戶，則不會變更您如何管理身分識別。

* **案例 2**︰如果貴組織已有現有的 Office 365 環境，但您組織中並非所有的使用者擁有 Office 365 帳戶，我們會在租用戶中建立使用者，並根據使用者的工作或學校電子郵件地址指派授權。

    如此一來，您在任何特定時間管理的使用者數目成長，因為您的組織中的使用者註冊服務。

* **案例 3**︰如果貴組織沒有連接到您的電子郵件網域的 Office 365 環境，則不會變更您如何管理身分識別。

    服務會將使用者加入新的、 僅限雲端使用者的目錄。 此外，您可以選擇以租用戶系統管理員身分接管，並加以管理。

### <a name="how-do-we-manage-power-bi"></a>要如何管理 Power BI？

Power BI 提供的管理入口網站，可讓您檢視使用量統計資料，提供 Microsoft 365 系統管理中心來管理、 使用者和群組的連結，並讓您能夠控制整個租用戶設定。

若要使用 Power BI 管理入口網站，您必須將您的帳戶作為標記**全域管理員**在 Office 365 或 Azure Active Directory 或其他人必須指派 Power BI 服務系統管理員角色給您的使用者帳戶。 如需詳細資訊，請參閱 <<c0> [ 了解 Power BI 系統管理員角色](service-admin-role.md)並[Power BI 管理入口網站](service-admin-portal.md)。

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>管理 Microsoft 為使用者所建之租用戶的程序為何？

當自助使用者可註冊使用 Azure AD 的雲端服務時，服務就會將它們新增至未受管理的 Azure AD 目錄會根據其電子郵件網域。 您可以宣告並管理的其他人使用這道程序所建立的租用戶*管理員接管*。 接管您的類型取決於是否有現有受控網域相關聯的租用戶：

* 使用「內部接管」  為網域建立新的受控租用戶。

* 使用「外部接管」  將網域移動到現有的受控租用戶。

如需詳細資訊，請參閱 < [Azure Active Directory 中的系統管理員身分接管非受控目錄](/azure/active-directory/users-groups-roles/domains-admin-takeover)。

當您執行外部接管時，服務會放 Power BI 內容，在接管之前建立[Power BI 封存工作區](service-admin-power-bi-archived-workspace.md)。 您必須手動將想要使用的任何內容移轉到新租用戶。

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>如果有多個網域，我可以控制使用者新增至 Office 365 租用戶？

如果您不執行任何動作，服務會建立每個使用者電子郵件網域和子網域的租用戶。 如果不論電子郵件地址擴充功能為何，希望所有使用者都在相同的租用戶中︰建立目標租用戶預先完成，或使用現有的租用戶。 然後加入所有現有的網域和您想要合併到該租用戶內的子網域。 每個使用者電子郵件地址結尾為這些網域和子網域會自動加入目標租用戶，當他們註冊。

> [!IMPORTANT]
> 一旦您已建立使用者，沒有任何支援的自動化的機制，以租用戶之間移動。 若要深入了解將網域新增至單一 Office 365 租用戶中，請參閱[將您的使用者與網域新增至 Office 365](/office365/admin/setup/add-domain/)。

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>如何移除已註冊使用者的 Power BI？

如果使用者已註冊 Power BI，但您不希望他們繼續存取 Power BI，您可以移除該使用者的 Power BI 授權。

1. 移至 [MIcrosoft 365 系統管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在左側的導覽列中，選取 [使用者]   > [作用中使用者]  。

1. 找到您要移除授權的使用者，然後選取其名稱。

    您也可以對使用者執行大量授權管理。 若要這樣做，請選取多個使用者，然後選取 [編輯產品授權]  。

1. 在使用者詳細資料頁面上的 [產品授權]  旁邊，選取 [編輯]  。

1. 取決於您授權功能套用至其帳戶，設定**Power BI （免費）** 或是**Power BI Pro**來**關閉**。

1. 選取 [儲存]  。

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>我怎麼知道有新的使用者加入我的租用戶？

已加入您的租用戶，此程式的一部分的使用者指派唯一的授權，您可以管理儀表板在您作用中使用者 窗格內篩選。 若要建立這個新檢視，請依照下列步驟執行。

1. 巡覽至 [MIcrosoft 365 系統管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在左側的導覽列中，選取 [使用者]   > [作用中使用者]  。

1. 在 [檢視]  功能表上，選取 [新增自訂檢視]  。

1. 為新的檢視命名，然後在 [已指派的產品授權]  下選取 [Power BI (免費)]  或 [Power BI Pro]  。

    每個檢視只能選取一個授權。 如果您的組織同時有 [Power BI (免費)]  與 [Power BI Pro]  授權，則您可以建立兩個檢視。

1. 輸入您想要的任何其他條件，然後選取 [新增]  。

1. 建立新的檢視之後，便可從**檢視**功能表。

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>有我應該準備的任何其他項目嗎？

您可能會遇到密碼重設要求增加的情況。 此程序的相關資訊，請參閱[重設使用者的密碼](/office365/admin/add-users/reset-passwords)。

您可以透過 Microsoft 365 系統管理中心的標準程序來移除租用戶使用者。 不過，如果使用者仍有您組織的有效電子郵件地址，除非您封鎖所有使用者加入，否則他們可以重新加入。

### <a name="where-is-my-power-bi-tenant-located"></a>我的 Power BI 租用戶位於何處？

Power BI 租用戶是中的資料區的相關資訊，請參閱[我的 Power BI 租用戶位於何處？](service-admin-where-is-my-tenant-located.md)。

### <a name="what-is-the-power-bi-sla"></a>什麼是 Power BI SLA？

如需 Power BI SLA （服務等級協定） 資訊，請參閱[授權的條款及文件](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37)文章中**授權**Microsoft Licensing 網站一節。

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Power BI 如何處理高可用性和容錯移轉？

如需高可用性和容錯移轉的資訊，請參閱[Power BI 的高可用性、 容錯移轉和災害復原常見問題集](service-admin-failover.md)。

## <a name="security-in-power-bi"></a>Power BI 的安全性

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI 是否符合國家、地區和業界的特定法規要求？

若要深入了解 Power BI 相容性，請參閱 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx)。

### <a name="how-does-security-work-in-power-bi"></a>Power BI 安全性如何運作？

Microsoft Power BI 為基礎的 Office 365，接著是根據 Azure Active Directory 等 Azure 服務。 如需 Power BI 架構的概觀，請參閱 [Power BI 安全性](service-admin-power-bi-security.md)。

## <a name="next-steps"></a>後續步驟

[Power BI 管理入口網站](service-admin-portal.md)  
[了解 Power BI 系統管理員角色](service-admin-role.md)  
[Power BI 的自助式註冊](service-self-service-signup-for-power-bi.md)  
[購買 Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[什麼是 Power BI Premium？](service-premium-what-is.md)  
[如何購買 Power BI Premium](service-admin-premium-purchase.md)  
[Power BI Premium 技術白皮書](https://aka.ms/pbipremiumwhitepaper)  
[管理 Power BI 和 Office 365 中的群組](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Office 365 使用者帳戶管理](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/)  
[Office 365 群組管理](/office365/admin/email/create-edit-or-delete-a-security-group/)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview