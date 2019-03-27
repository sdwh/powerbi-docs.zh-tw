---
title: 組織中的 Power BI 授權
description: 了解 Power BI 中提供的不同授權類型：免費授權、Power BI Pro 和 Power BI Premium。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/30/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 5da6b465adc544bf64fd4dfb090a2e1faabee59d
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383230"
---
# <a name="power-bi-licensing-in-your-organization"></a>組織中的 Power BI 授權

[!INCLUDE [license-capabilities](includes/license-capabilities.md)]

本文著重於從系統管理員觀點的每位使用者授權。

## <a name="manage-power-bi-pro-licenses"></a>管理 Power BI Pro 授權

身為系統管理員，您可以購買和指派 Power BI Pro 授權，也可以為您的組織註冊 Power BI Pro 試用版。 個人也可以註冊 Power BI Pro 試用版。

### <a name="purchasing-power-bi-pro"></a>購買 Power BI Pro

您透過 Microsoft Office 365 或透過認證的 Microsoft 合作夥伴，來購買 Power BI Pro 授權。 購買授權之後，請將它們指派給個別使用者。 如需詳細資訊，請參閱[購買及指派 Power BI Pro 授權](service-admin-purchasing-power-bi-pro.md)。

### <a name="power-bi-pro-trial-for-individuals"></a>Power BI Pro 個人試用版

在您組織中的個人可以註冊 Power BI Pro 試用。 如需詳細資訊，請參閱[以個人身分註冊 Power BI](service-self-service-signup-for-power-bi.md)。

利用產品中 Power BI Pro 試用版的使用者，不會在 Microsoft 365 系統管理中心顯示為 Power BI Pro 試用版使用者 (他們會顯示為 Power BI 免費版使用者)。 不過在 Power BI [管理儲存體] 頁面中會顯示為 Power BI Pro 試用版使用者。

### <a name="power-bi-pro-trial-for-organizations"></a>Power BI Pro 組織試用版

如果想要取得並部署 Power BI 試用版授權至組織中的多個使用者，而不需要讓個別使用者個別接受試用版條款，請註冊 Power BI Pro 組織試用版。

遵循註冊步驟之前，請記住下列事項：

* 若要註冊，您必須是 Office 365 中[**全域管理員**或**計費管理員**](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)角色的成員。

* 每個租用戶只限使用一個組織試用版。 這表示，如果有人已將 Power BI Pro 試用版套用至您的租用戶，您就無法再次套用。 如果您需要這方面的協助，請連絡 [Office 365 帳單支援](https://support.office.microsoft.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b?CorrelationId=552bbf37-214f-4202-80cb-b94240dcd671)。

1. 巡覽至 [MIcrosoft 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)。

1. 在左邊的功能窗格中，依序選取 [帳單]、[訂閱]。

   ![帳單及訂閱](media/service-admin-licensing-organization/service-power-bi-pro-in-your-organization-05.png)

1. 在右邊，選取 [新增訂閱]。

   ![新增訂用帳戶](media/service-admin-licensing-organization/service-power-bi-pro-in-your-organization-06.png)

1. 在 [其他方案] 下，將滑鼠停留在 Power BI Pro 的省略符號 (**. . .**)，然後選取 [開始免費試用]。

   ![開始免費試用](media/service-admin-licensing-organization/service-power-bi-pro-in-your-organization-07.png) 

1. 在 [訂單確認] 畫面上，選取 [立即試用]。

1. 在 [訂單收據] 上，選取 [繼續]。

現在您可以[在 Office 365 中指派授權](https://support.office.com/article/assign-licenses-to-users-in-office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)。

## <a name="manage-power-bi-free-licenses"></a>管理 Power BI 免費授權

組織中的使用者可以使用兩種不同方式存取 Power BI 免費授權：

* 您可以在 Microsoft 365 系統管理中心內，為他們指派 Power BI 授權。

* 如果使用者[註冊 Power BI Pro 試用版](service-self-service-signup-for-power-bi.md)且試用版到期，則會取得免費授權。

### <a name="requesting-and-assigning-free-licenses"></a>要求及指派免費授權

如果您打算集中管理授權要求和指派，請先檢查是否已有無限制的 Power BI (免費) 授權區塊。

在首次有人以個人身分註冊 Power BI 之後，便可使用此區塊的授權。 在此過程中，這個授權區塊會附加到您的組織，並將授權指派給註冊的使用者。

1. 在 Microsoft 365 系統管理中心的 [帳單] > [授權] 底下，檢查是否為**無限制**。

    ![無限制的免費授權區塊](media/service-admin-licensing-organization/unlimited-licenses.png)

1. 如果有可用的區塊，您現在可以[在 Office 365 中指派授權](https://support.office.com/article/assign-licenses-to-users-in-office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)。 如果沒有可用的區塊，您會有兩個選擇：

    * 讓組織的成員以個人身分註冊，這樣會觸發無限制區塊的建立。

    * 移至下一個程序，您可以在該處註冊固定數目的授權。

如果無法使用無限制的 Power BI (免費) 授權區塊，而且您不想要進行個人註冊，請遵循此程序。

1. 巡覽至 [MIcrosoft 365 系統管理中心](https://portal.office.com/admin/default.aspx)。

1. 在左邊的瀏覽窗格中，選取 [帳單] > [訂閱]。

1. 在右邊，選取 [新增訂閱 +]。

1. 在 [其他方案] 下，將滑鼠停留在 Power BI (免費) 的省略符號 (**. . .**)，然後選取 [立即購買]。

    ![立即購買 - Power BI (免費)](media/service-admin-licensing-organization/buy-powerbi-free.png)

1. 輸入您想要新增的授權數量，然後選取 [立即結帳] 或 [新增至購物車]。

1. 在結帳流程中，輸入所需的資訊。

    使用這種方法時，不會購買任何產品，但是您必須輸入信用卡帳單資訊，或選擇開立發票。

1. 現在您可以[在 Office 365 中指派授權](https://support.office.com/article/assign-licenses-to-users-in-office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)。

1. 如果您稍後決定您想要新增更多授權，您可以移回至 \[新增訂閱]，然後對 Power BI \(免費) 選取 \[Change license quantity] \(變更授權數量)。

    ![變更授權數量](media/service-admin-licensing-organization/change-license-quantity.png)

### <a name="enable-or-disable-individual-user-sign-up-in-azure-active-directory"></a>在 Azure Active Directory 中啟用或停用個人使用者註冊

身為系統管理員，您可以選擇透過 Azure Active Directory (AAD) 啟用或停用個人使用者註冊。 文章的本節會示範如何使用 PowerShell 命令管理註冊。 如需 Azure PowerShell 的詳細資訊，請參閱 [Azure PowerShell 概觀](/powershell/azure/overview)。

控制註冊的 AAD 設定為**AllowAdHocSubscriptions**。 在大多數的租用戶，此會設定為 *true*，表示已啟用此設定。 如果您透過合作夥伴取得 Power BI，這可能設為 *false*，表示已停用此設定。 如果您將設定從 *true* 變更為 *false*，則組織中的新使用者會遭到封鎖，無法以個人身分註冊。 在設定變更前已註冊 Power BI 的使用者，會保留其授權。

1. 使用 Office 365 認證登入 Azure Active Directory。 下列 PowerShell 指令碼的第一行會提示您輸入您的認證。 第二行連接到 Azure Active Directory。

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Azure Active Directory 登入](media/service-admin-licensing-organization/aad-signin.png)

1. 當您登入之後，請執行下列命令，查看租用戶目前的設定情形。

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```
1. 請執行下列命令啟用 ($true) 或停用 ($false) **AllowAdHocSubscriptions**。

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

> [!NOTE]
> AllowAdHocSubscriptions 旗標可用以控制貴組織的數個使用者功能，包括使用者註冊 Azure Rights Management Service 的能力。 變更此旗標會影響所有這些功能。

## <a name="next-steps"></a>後續步驟

[Power BI 的自助式註冊](service-self-service-signup-for-power-bi.md)  

[購買及指派 Power BI Pro 授權](service-admin-purchasing-power-bi-pro.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)