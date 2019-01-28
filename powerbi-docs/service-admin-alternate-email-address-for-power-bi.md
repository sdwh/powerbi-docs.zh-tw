---
title: 使用備用電子郵件地址
description: 使用備用電子郵件地址
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 5998f4b63a168c3056a5464844d008bd657ef7c9
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54294239"
---
# <a name="using-an-alternate-email-address"></a>使用備用電子郵件地址

當您註冊 Power BI 時，您必須提供電子郵件地址。 根據預設，Power BI 使用此地址來傳送有關服務中活動的更新給您。 例如，當有人傳送共用邀請給您時，便會傳送到此地址。

在某些情況下，您可能想要讓這些電子郵件傳送到備用電子郵件地址，而非您用來註冊的電子郵件地址。 此文章說明如何在 Office 365 與在 PowerShell 中指定備用地址。 此文章也說明電子郵件地址在 Azure Active Directory (Azure AD) 中是如何解析的。

> [!NOTE]
> 指定備用電子郵件地址不會影響 Power BI 用於服務更新、電子報與其他促銷通訊的電子郵件地址。  那些通訊一律會傳送到您在註冊 Power BI 時使用的電子郵件地址。

## <a name="use-office-365"></a>使用 Office 365

若要在 Office 365 中指定備用電子郵件地址，請依照下列步驟執行。

1. 開啟 [Office 365 個人資訊頁面](https://portal.office.com/account/#personalinfo)。 如果出現提示，請以您用於 Power BI 的電子郵件地址和密碼進行登入。

1. 在左側功能表上，選取 [個人資訊]。

1. 在 [連絡人詳細資料] 區段中，選取 [編輯]。

    若無法編輯您的詳細資料，表示您的電子郵件地址是由您的 Office 365 系統管理員所管理。 與您的系統管理員連絡以更新您的電子郵件地址。

    ![連絡人詳細資料](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. 在 [替代電子郵件] 欄位中，輸入您想要收到 Power BI 更新的電子郵件地址。

## <a name="use-powershell"></a>使用 PowerShell

若要在 PowerShell 中指定備用電子郵件地址，請使用 [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/) 命令。

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Azure AD 中的電子郵件地址解析

擷取適用於 Power BI 的 Azure AD 內嵌權杖時，您可以使用三種不同的電子郵件：

* 與使用者 Azure AD 帳戶相關聯的主要電子郵件地址

* UserPrincipalName (UPN) 電子郵件地址

* *其他電子郵件地址*陣列屬性

Power BI 會根據下列順序選取要使用的電子郵件：

1. 如果 Azure AD 使用者物件中存在 mail 屬性，則 Power BI 會在電子郵件地址中使用該 mail 屬性。

1. 如果 UPN 電子郵件「不是」**\*.onmicrosoft.com** 網域電子郵件地址 ("\@" 符號後面的資訊)，則 Power BI 會在電子郵件地址中使用該 mail 屬性。

1. 如果 Azure AD 使用者物件中存在*其他電子郵件地址*陣列屬性，則會使用該清單中的第一個電子郵件 (因為這個屬性中會有一份電子郵件清單)。

1. 如果上述條件都不存在，則會使用 UPN 地址。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

