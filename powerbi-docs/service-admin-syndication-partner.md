---
title: 無法將 Power BI 加入 O365 合作夥伴中
description: 無法將 Power BI 加入 Office 365 同步發行合作夥伴中。 同步發行模型是 Office 365 使用的購買模型。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 635a64c08056e82539d33904d4cce60d4cfc00cd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187915"
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>無法將 Power BI 加入 Office 365 合作夥伴訂閱

Office 365 可讓公司將 Office 365 與其自有的解決方案進行搭配整合並轉售，讓客戶只需透過一個連絡窗口，就能處理購買、帳單和支援等事宜。

如果您想在購買 Office 365 訂閱時一併取得 Power BI，我們建議您連絡您的合作夥伴來選購。 如果您的合作夥伴目前不提供 Power BI，您有可以購買 Power BI 的其他選項。

## <a name="work-with-your-partner-to-purchase-power-bi"></a>與您的合作夥伴合作以購買 Power BI

如果想要購買 Power BI Pro 或 Power BI Premium 訂閱，請與合作夥伴討論您可購買的選項：

* 合作夥伴若同意將 Power BI 加入商品組合，即可向其購買。

* 您的合作夥伴可以將您的購買模式轉變成直接向 Microsoft 或其他提供 Power BI 的合作夥伴購買 Power BI。

## <a name="purchase-from-microsoft-or-another-channel"></a>從 Microsoft 或其他管道購買

根據與您合作夥伴關係，您或許可以直接向 Microsoft 或其他合作夥伴購買 Power BI。 您可以確認您是否能在 Microsoft 365 系統管理中心中新增 Power BI 訂閱 (需要全域管理員或計費管理員腳色成員資格)。

1. 移至 [MIcrosoft 365 系統管理中心](https://admin.microsoft.com/AdminPortal/Home#/homepage)。

1. 在左側功能表中，開啟 [計費]  ：

    * 如果您看到 [訂閱]  ，您可以直接向 Microsoft 取得服務，您也可以連絡提供 Power BI 的其他合作夥伴。

        ![[計費] - 顯示 [訂閱]](media/service-admin-syndication-partner/billingsub.png)

    * 如果您沒有看到 [訂閱]  ，則您無法直接向 Microsoft 或其他合作夥伴購買。

如果您的合作夥伴不提供 Power BI，且您無法直接向 Microsoft 或其他合作夥伴購買，請考慮註冊免費試用版。

## <a name="sign-up-for-a-free-trial"></a>註冊免費試用版

您可以註冊 Power BI Pro 的免費試用版。 如果您在試用期結束時未購買 Power BI Pro，您仍然擁有提供許多 Power BI 功能的免費授權。 如需詳細資訊，請參閱[各授權類型的 Power BI 功能](service-features-license-type.md)。

### <a name="enable-ad-hoc-subscriptions"></a>啟用特定訂閱

根據預設，系統會停用個人註冊 (又稱為特定訂閱)。 在此情況下，您會在嘗試註冊時看到下列訊息：「您的 IT 部門已經關閉 Microsoft Power BI 的註冊功能。」 

![[很抱歉] 影像](media/service-admin-syndication-partner/sorry.png)

若要啟用特定訂閱，您可以連絡合作夥伴，請他們開啟。 如果您是租用戶系統管理員，而且知道如何使用 Azure Active Directory PowerShell 命令，您可以自行啟用特定訂閱。 [適用於 Graph 的 Azure Active Directory PowerShell](/powershell/azure/active-directory/install-adv2/)

1. 使用 Office 365 認證登入 Azure Active Directory。 以下指令碼的第一行會提示您輸入認證。 第二行連接到 Azure Active Directory。

    ```powershell
    $msolcred = get-credential
    connect-msolservice -credential $msolcred
    ```

    ![輸入您的認證](media/service-admin-syndication-partner/aad-signin.png)

1. 登入之後，請執行下列命令來檢查 `AllowAdHocSubscriptions` 的目前設定。

    ```powershell
    Get-MsolCompanyInformation
    ```

1. 執行下列命令來啟用免費註冊。

    ```powershell
    Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

## <a name="next-steps"></a>後續步驟

[組織中的 Power BI 授權](service-admin-licensing-organization.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)