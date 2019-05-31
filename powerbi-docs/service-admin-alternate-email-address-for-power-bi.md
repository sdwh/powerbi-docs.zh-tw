---
title: 使用備用電子郵件地址
description: 使用備用電子郵件地址
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906672"
---
# <a name="use-an-alternate-email-address"></a>使用備用電子郵件地址

當您註冊 Power BI 時，您必須提供電子郵件地址。 根據預設，Power BI 使用此地址來傳送有關服務中活動的更新給您。 例如，當有人傳送共用邀請給您時，便會傳送到此地址。

在某些情況下，您可能想要讓這些電子郵件傳送到備用電子郵件地址，而非您用來註冊的電子郵件地址。 此文章說明如何在 Office 365 與在 PowerShell 中指定備用地址。 本文也說明 Azure Active Directory (Azure AD) 如何解析電子郵件地址。

> [!NOTE]
> 指定備用電子郵件地址不會影響 Power BI 用於服務更新、電子報與其他促銷通訊的電子郵件地址。 這些通訊會一律傳送至電子郵件地址註冊 Power BI 時所使用。

## <a name="use-office-365"></a>使用 Office 365

若要在 Office 365 中指定備用電子郵件地址，請依照下列步驟執行。

1. 開啟 [Office 365 個人資訊頁面](https://portal.office.com/account/#personalinfo)。 如果應用程式會提示您，請登入的電子郵件地址和您用於 Power BI 的密碼。

1. 在左側功能表上，選取 [個人資訊]  。

1. 在 [連絡人詳細資料]  區段中，選取 [編輯]  。

    如果您不能編輯您的詳細資料，這表示您的 Office 365 系統管理員管理您的電子郵件地址。 請連絡您的系統管理員，以更新您的電子郵件地址。

    ![連絡人詳細資料](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. 在 **備用電子郵件**欄位中，輸入您想要使用 Power BI 更新的 Office 365 電子郵件地址。

## <a name="use-powershell"></a>使用 PowerShell

若要在 PowerShell 中指定備用電子郵件地址，請使用 [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/) 命令。

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Azure AD 中的電子郵件地址解析

若要擷取 Azure AD 的內嵌權杖適用於 Power BI，您可以使用其中一個電子郵件地址的三種不同類型：

* 使用者的 Azure AD 帳戶相關聯的主要電子郵件地址

* UserPrincipalName (UPN) 電子郵件地址

* *其他電子郵件地址*陣列屬性

Power BI 會根據下列順序選取要使用的電子郵件：

1. 如果 Azure AD 使用者物件中存在 mail 屬性，則 Power BI 會在電子郵件地址中使用該 mail 屬性。

1. 如果 UPN 電子郵件「不是」  **\*.onmicrosoft.com** 網域電子郵件地址 ("\@" 符號後面的資訊)，則 Power BI 會在電子郵件地址中使用該郵件屬性。

1. 如果*其他電子郵件地址*陣列屬性，在 Azure AD 使用者物件中的已存在，則 Power BI 會使用該清單中的第一個電子郵件 （因為可能有一份在這個屬性中的電子郵件）。

1. 如果上述條件都存在，Power BI 會使用 UPN 位址。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)