---
title: 管理 Power BI - 常見問題集 (FAQ)
description: 了解 Power BI 註冊、租用戶管理和其他管理工作常見問題的解答。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 4c8601e15a415e680028b2259a4c2b8e56dbd3b4
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34297231"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>管理 Power BI - 常見問題集 (FAQ)

本文可解決 Power BI 管理的常見問題。 如需 Power BI 管理的概觀，請參閱[什麼是 Power BI 管理？](service-admin-administering-power-bi-in-your-organization.md)。

## <a name="whats-in-this-article"></a>本文內容
**註冊 Power BI**

* [使用者如何註冊 Power BI？](#how-do-users-sign-up-for-power-bi)
* [個人使用者如何在我的組織中註冊？](#how-do-individual-users-in-my-organization-sign-up)
* [我該如何防止使用者加入現有的 Office 365 租用戶？](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [我該如何允許使用者加入現有的 Office 365 租用戶？](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [我該如何確認租用戶是否開啟了封鎖？](#how-do-i-verify-if-i-have-the-block-on-in-the-tenant)
* [我該如何不讓現有的使用者開始使用 Power BI？](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [我要如何允許現有的使用者註冊 Power BI？](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

**管理 Power BI**

* [這會怎麼改變我目前管理組織中使用者身分識別的方式？](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [要如何管理 Power BI？](#how-do-we-manage-power-bi)
* [管理 Microsoft 為使用者所建之租用戶的程序為何？](#what-is-the-process-to-manage-a-tenant-created-by-Microsoft-for-my-users)
* [如果有多個網域，我可以控制使用者新增的 Office 365 租用戶嗎？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)
* [如何移除已註冊使用者的 Power BI？](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [我如何知道有新的使用者加入我的租用戶？](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [我還應該準備什麼？](#are-there-any-additional-things-i-should-be-prepared-for)
* [這是免費的嗎？這些授權要收費嗎？](#is-this-free-will-i-be-charged-for-these-licenses)
* [我的 Power BI 租用戶位於何處？](#where-is-my-power-bi-tenant-located)
* [什麼是 Power BI SLA (服務等級協定)？](#what-is-the-power-bi-sla)

**Power BI 的安全性**

* [Power BI 是否符合國家、地區和業界的特定法規要求？](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Power BI 安全性如何運作？](#how-does-security-work-in-power-bi?)

## <a name="sign-up-for-power-bi"></a>註冊 Power BI
### <a name="how-do-users-sign-up-for-power-bi"></a>使用者如何註冊 Power BI？
您可以透過 [Power BI 網站](https://powerbi.microsoft.com)註冊 Power BI。 您也可以透過 Office 365 系統管理中心的購買服務頁面註冊。 當系統管理員註冊 Power BI 時，他們可以將使用者授權指派給應該有存取權的使用者。

貴組織中的個人使用者也可以透過 [Power BI 網站](https://powerbi.microsoft.com)註冊 Power BI。 當貴組織有使用者註冊 Power BI 時，Power BI 授權就會自動指派給該使用者。 [深入了解](service-self-service-signup-for-power-bi.md)

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>個人使用者如何在我的組織中註冊？
貴組織使用者有三種適用案例︰

案例 1︰貴組織已有現成的 Office 365 環境，且註冊 Power BI 的使用者已有 Office 365 帳戶。
在這個案例中，如果使用者在租用戶中已經有工作或學校帳戶 (例如，contoso.com)，但尚未有 Power BI，則 Microsoft 只會啟用該帳戶的計劃，並自動通知使用者如何使用 Power BI 服務。

案例 2︰貴組織有現成的 Office 365 環境，但註冊 Power BI 的使用者沒有 Office 365 帳戶。
在這個案例中，使用者有貴組織網域的電子郵件地址 (例如，contoso.com)，但還沒有 Office 365 帳戶。 在這個情況下，使用者可以註冊 Power BI，並會自動獲得帳戶。 這可讓使用者存取 Power BI 服務。 例如，如果員工 Nancy 使用她的工作電子郵件地址註冊 (例如 Nancy@contoso.com)，Microsoft 就會自動將 Nancy 新增為 Contoso 的 Office 365 環境使用者，並為該帳戶啟用 Power BI。

案例 3︰貴組織沒有連接到您電子郵件網域的 Office 365 環境。
貴組織不需要執行任何管理動作來利用 Power BI。 使用者會新增至僅限雲端的新使用者目錄中，而您可以選擇是否接管成為租用戶系統管理員並管理使用者。

> [!IMPORTANT]
> 如果貴組織有多個電子郵件網域，而您希望所有的電子郵件地址擴充功能都在相同的租用戶中，請先將所有電子郵件地址網域新增至 Azure Active Directory 租用戶中，再讓使用者註冊。 使用者建立後，不會自動在租用戶之間移動。 如需這個程序的詳細資訊，請參閱下文的 [如果有多個網域，我可以控制使用者新增的 Office 365 租用戶嗎？](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to)，以及線上文章[將您的使用者與網域新增至 Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)。
> 
> 

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>我該如何防止使用者加入現有的 Office 365 租用戶？
身為系統管理員，您可以採取幾個步驟不讓使用者加入現有的 Office 365 租用戶。 如果您封鎖了這項功能，使用者就會註冊失敗，而且系統會指示他們連絡組織的系統管理員。如果您已停用自動授權發佈 (例如 Office 365 教育版、學生版和教職員版)，就不需要重複這個程序。

這些步驟需要使用 Windows PowerShell。 若要開始使用 Windows PowerShell，請參閱 [PowerShell 快速入門指南](http://go.microsoft.com/fwlink/p/?LinkID=286814)。

若要執行下列步驟，您必須安裝最新的 64 位元版 [Windows PowerShell Azure Active Directory 模組](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

在選取連結之後，請選取 [執行] 執行 Installer 套件。

**停用自動加入租用戶**︰使用這個 Windows PowerShell 命令不讓新的使用者加入受管理的租用戶︰

* 停用新使用者的自動加入租用戶︰
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
* 啟用新使用者的自動加入租用戶︰
  
    $msolcred = get-credential   connect-msolservice -credential $msolcred
  
    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

> [!NOTE]
> 這會防止貴組織的新使用者註冊 Power BI。 在您停用組織的新註冊前即已註冊 Power BI 的使用者，仍然保留其授權。 如需如何移除已註冊服務之使用者的 Power BI 存取指示，請參閱＜如何移除授權？＞一節。
> 
> 

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>我該如何允許使用者加入現有的 Office 365 租用戶？
若要允許使用者加入您的租用戶，請執行與上述問題相反的命令。

若要執行下列步驟，您必須安裝最新的 64 位元版 [Windows PowerShell Azure Active Directory 模組](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Set-MsolCompanySettings -AllowEmailVerifiedUsers $true

### <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>我該如何確認租用戶是否開啟了封鎖？
使用下列 PowerShell 指令碼。

若要執行下列步驟，您必須安裝最新的 64 位元版 [Windows PowerShell Azure Active Directory 模組](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

    $msolcred = get-credential
    connect-msolservice -credential $msolcred

    Get-MsolCompanyInformation | fl allow*

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>我該如何不讓現有的使用者開始使用 Power BI？
身為系統管理員，您可以採取幾個步驟不讓使用者註冊 Power BI。 如果您封鎖了這項功能，使用者就會註冊失敗，而且系統會指示他們連絡組織的系統管理員。如果您已停用自動授權發佈 (例如 Office 365 教育版、學生版和教職員版)，就不需要重複這個程序。 [深入了解](service-admin-service-free-in-your-organization.md#enable-or-disable-individual-user-sign-up-in-azure-active-directory)

控制此項的 AAD 設定是 **AllowAdHocSubscriptions**。 大多數的租用戶必須將此設定為 true，表示已啟用此設定。 如果您透過合作夥伴取得 Power BI，根據預設，這可能設為 false，表示已停用。

若要執行下列步驟，您必須安裝最新的 64 位元版 [Windows PowerShell Azure Active Directory 模組](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

1. 您首先需要使用 Office 365 認證登入 Azure Active Directory。 第一行會提示您輸入認證。 第二行連接到 Azure Active Directory。
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. 當您登入之後，您可以發出下列命令，查看您的租用戶目前設定那些項目。
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. 您可以使用此命令啟用 ($true) 或停用 ($false) AllowAdHocSubscriptions。
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> AllowAdHocSubscriptions 旗標可用以控制貴組織的數個使用者功能，包括使用者註冊 Azure Rights Management Service 的能力。 變更這個旗標會影響所有這些功能。
> 
> 

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>我要如何允許現有的使用者註冊 Power BI？
若要讓現有的使用者註冊 Power BI，請執行上述問題所列的命令，但傳遞 true 不傳遞 false。

若要執行下列步驟，您必須安裝最新的 64 位元版 [Windows PowerShell Azure Active Directory 模組](http://go.microsoft.com/fwlink/p/?LinkID=236297)。

1. 您首先需要使用 Office 365 認證登入 Azure Active Directory。 第一行會提示您輸入認證。 第二行連接到 Azure Active Directory。
   
     $msolcred = get-credential   connect-msolservice -credential $msolcred
2. 當您登入之後，您可以發出下列命令，查看您的租用戶目前設定那些項目。
   
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
3. 您可以使用此命令啟用 ($true) 或停用 ($false) AllowAdHocSubscriptions。
   
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true

> [!NOTE]
> AllowAdHocSubscriptions 旗標可用以控制貴組織的數個使用者功能，包括使用者註冊 Azure Rights Management Service 的能力。 變更這個旗標會影響所有這些功能。
> 
> 

## <a name="administration-of-power-bi"></a>管理 Power BI
### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>這會怎麼改變我目前管理組織中使用者身分識別的方式？
如果貴組織已有現成的 Office 365 環境，而且組織中所有的使用者都有 Office 365 帳戶，身分識別管理就不會變更。

如果貴組織已有現成的 Office 365 環境，但組織中並非所有使用者都有 Office 365 帳戶，我們會在租用戶中建立使用者，然後根據使用者的工作或學校電子郵件地址指派授權。 這表示，您在任何特定時間內管理的使用者數目，會成長為貴組織註冊服務的使用者。

如果貴組織沒有連接到您電子郵件網域的 Office 365 環境，身分識別管理方式就不會有任何變更。 使用者會新增至僅限雲端的新使用者目錄中，而您可以選擇是否接管成為租用戶系統管理員並管理使用者。

### <a name="how-do-we-manage-power-bi"></a>要如何管理 Power BI？
Power BI 提供的管理入口網站，可讓您檢視使用量統計資料、連結到 Office 365 系統管理中心來管理使用者和群組，以及控制租用戶的各種設定。 

> [!NOTE]
> 您的帳戶必須在 Office 365或 Azure Active Directory 中標示為**全域管理員**，或已指派 Power BI 服務系統管理員角色，才能存取 Power BI 管理入口網站。 如需 Power BI 服務系統管理員角色的詳細資訊，請參閱[了解 Power BI 系統管理員角色](service-admin-role.md)。
> 
> 

如需詳細資訊，請參閱 [Power BI 管理入口網站](service-admin-portal.md)。

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>管理 Microsoft 為使用者所建之租用戶的程序為何？
如果租用戶之前是由 Microsoft 所建立，您可以遵循下列步驟宣告並管理該租用戶︰

1. 註冊 Power BI，使用符合您想要管理的租用戶網域的電子郵件地址網域，即可加入租用戶。 例如，如果 Microsoft 建立了 contoso.com 租用戶，您需要使用以 @contoso.com 結尾的電子郵件地址加入租用戶。
2. 透過驗證網域擁有權可以宣告系統管理控制權︰只要位在租用戶中，即可透過驗證網域擁有權將自己升級成 *全域管理員* 角色。 請遵循下列步驟執行此項作業：
   
   1. 前往 [https://portal.office.com](https://portal.office.com)。
   2. 選取左上角的應用程式啟動器圖示，然後選擇 [系統管理員]。
   3. 閱讀 \[Become the admin] \(成為系統管理員) 頁面中的指示，然後選擇 \[Yes, I want to be the admin] \(是，我想要成為系統管理員)。
      
      > [!NOTE]
      > 如果這個選項沒有出現，即表示已有 Office 365 系統管理員。
      > 
      > 

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>如果有多個網域，我可以控制使用者新增的 Office 365 租用戶嗎？
如果不執行任何動作，就會為每個使用者電子郵件網域和子網域建立租用戶。

如果不論電子郵件地址擴充功能為何，希望所有使用者都在相同的租用戶中︰

* 請預先建立目標租用戶，或使用現有的租用戶，新增您想要合併到該租用戶內的所有現有網域與子網域。 然後，電子郵件地址以這些網域與子網域結尾的所有使用者，就會在註冊時自動加入目標租用戶中。

> [!IMPORTANT]
> 使用者一經建立，就不會自動在租用戶之間移動。 若要深入了解將網域新增至單一 Office 365 租用戶中，請參閱[將您的使用者與網域新增至 Office 365](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)。
> 
> 

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>如何移除已註冊使用者的 Power BI？
如果使用者已註冊 Power BI，但您不希望他們繼續存取 Power BI，您可以移除該使用者的 Power BI 授權。

1. 瀏覽至 Office 365 系統管理中心。
2. 在左側的導覽列中，選取 [使用者] > [作用中使用者]。
3. 找到您想要移除其授權的使用者，然後選取其名稱 > [編輯]。
4. 在 [使用者詳細資料] 頁面上的左側導覽列中，選取 [授權]。
5. 取消核取 [Power BI (免費)] 或 [Power BI Pro]，視其帳戶所套用之授權而定。
6. 選取 [儲存]。

> [!NOTE]
> 您也可以對使用者執行大量授權管理。 若要這樣做，請選取多個使用者並選取 [編輯]。
> 
> 

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>我怎麼知道有新的使用者加入我的租用戶？
已加入這個程式租用戶的使用者會獲派唯一的授權，您可以在系統管理儀表板的 [作用中使用者] 窗格內篩選。

若要建立這個新的檢視，請在 Office 365 系統管理中心移至 [使用者] > [作用中使用者]，然後選取 [選取檢視] 功能表的 [新檢視]。 命名新的檢視，然後在 [指派的授權] 下選取 [Power BI (免費)] 或 [Power BI Pro]。 每個檢視只能選取一個授權。 如果貴組織同時有 [Power BI (免費)] 和 [Power BI Pro] 授權，您就必須建立兩個檢視。 一旦建立新的檢視，您就可以看到租用戶中所有已註冊這個程式的使用者。

### <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>我還應該準備什麼？
您可能會遇到密碼重設要求增加的情況。 如需這個程序的詳細資訊，請參閱[在 Office 365 重設使用者密碼](https://support.office.com/article/Reset-a-users-password-7a5d073b-7fae-4aa5-8f96-9ecd041aba9c)。

您可以透過 Office 365 系統管理中心的標準程序，移除租用戶的使用者。 不過，如果使用者仍有貴組織的使用中電子郵件地址，除非您封鎖所有使用者加入，否則他們就可以重新加入。

### <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>這是免費的嗎？ 這些授權要收費嗎？
**Power BI (免費)** 授權適用於 Power BI 免費版。 如對其他功能有興趣，請參閱 [Power BI Pro 版本](service-premium.md)。

### <a name="where-is-my-power-bi-tenant-located"></a>我的 Power BI 租用戶位於何處？
若要了解如何尋找您的 Power BI 租用戶所在位置，也稱為資料區域，請參閱 [Where is my Power BI tenant located?](service-admin-where-is-my-tenant-located.md) (我的 Power BI 租用戶位於何處？)。

### <a name="what-is-the-power-bi-sla"></a>什麼是 Power BI SLA？
如需 Power BI SLA (服務等級協定) 的相關資訊，請參閱 Microsoft Licensing 網站**授權**一節中的[授權條款及文件](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37)文章。

## <a name="security-in-power-bi"></a>Power BI 的安全性
### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Power BI 是否符合國家、地區和業界的特定法規要求？
若要深入了解 Power BI 相容性，請參閱 [Microsoft 信任中心](http://go.microsoft.com/fwlink/?LinkId=785324)。

### <a name="how-does-security-work-in-power-bi"></a>Power BI 安全性如何運作？
Power BI 是建置在 Office 365 的基礎之上，而 Office 365 則是建置在 Azure Active Directory 等 Azure 服務之上。 如需 Power BI 架構的概觀，請參閱 [Power BI 安全性](service-admin-power-bi-security.md)。 

## <a name="next-steps"></a>後續步驟
[Power BI 管理入口網站](service-admin-portal.md)  
[了解 Power BI 系統管理員角色](service-admin-role.md)  
[Power BI 的自助式註冊](service-self-service-signup-for-power-bi.md)  
[組織的 Power BI (免費)](service-admin-service-free-in-your-organization.md)  
[購買 Power BI Pro](service-admin-purchasing-power-bi-pro.md)  
[Power BI Premium - 這是什麼？](service-premium.md)  
[如何購買 Power BI Premium](service-admin-premium-purchase.md)  
[Office 365 使用者帳戶管理](https://technet.microsoft.com/library/office-365-user-account-management.aspx)  
[Office 365 群組管理](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)  
[管理 Power BI 和 Office 365 中的群組](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Power BI Premium 技術白皮書](https://aka.ms/pbipremiumwhitepaper)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)