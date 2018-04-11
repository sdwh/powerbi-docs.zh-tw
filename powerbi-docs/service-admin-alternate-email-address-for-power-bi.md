---
title: 使用備用電子郵件地址
description: 使用備用電子郵件地址
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/08/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ca7fe8f91a7d70740435af9c044f1cd57c01d8a5
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2018
---
# <a name="using-an-alternate-email-address"></a>使用備用電子郵件地址
預設會使用您用來註冊 Power BI 的電子郵件地址，來傳送有關 Power BI 中活動的更新給您。  例如，當有人傳送共用邀請給您時，便會傳送至這個地址。

有時候，您可能會想要將這些電子郵件傳送至替代電子郵件地址，而不是原先用來註冊 Power BI 的電子郵件地址。

## <a name="updating-through-office-365-personal-info-page"></a>透過 Office 365 個人資訊頁面更新
1. 前往您的 [Office 365 個人資訊頁面](https://portal.office.com/account/#personalinfo)。  如果出現提示，請以您用於 Power BI 的電子郵件地址和密碼進行登入。
2. 按一下 [連絡人詳細資料] 區段中的 [編輯] 連結。  
   
   > [!NOTE]
   > 如果看不到 [編輯] 連結，表示您的電子郵件地址是由 Office 365 系統管理員所管理，因此您需要與其連絡以更新電子郵件地址。
   > 
   > 
   
   ![](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)
3. 在 [替代電子郵件] 欄位中，輸入您想要收到 Power BI 更新的電子郵件地址。

> [!NOTE]
> 變更這項設定不會影響用來傳送服務更新、電子報和其他促銷通訊的電子郵件地址。  這些項目一律會傳送至您原本用來註冊 Power BI 的電子郵件地址。
> 
> 

## <a name="updating-through-azure-active-directory"></a>透過 Azure Active Directory 更新
擷取適用於 Power BI 的 Active Azure Directory (AAD) 內嵌權杖時，您可以使用三種不同的電子郵件。 這三種不同類型為：

* 與使用者 AAD 帳戶相關聯的主要電子郵件地址
* UserPrincipalName (UPN) 電子郵件地址
* “other” 電子郵件地址陣列屬性

Power BI 會會根據下列準則選取要使用的電子郵件：
1.  如果 AAD 租用戶的使用者物件中存在 mail 屬性，則 Power BI 會在電子郵件地址中使用該 mail 屬性
2.  如果 UPN 電子郵件「不是」**\*.onmicrosoft.com** 網域的電子郵件地址 ("\@" 符號後面的資訊)，則 Power BI 會在電子郵件地址中使用該 mail 屬性
3.  如果 AAD 租用戶的使用者物件中存在 “other” 電子郵件陣列屬性，則會使用該清單中的第一個電子郵件 (因為這個屬性中會有一份電子郵件清單)
4. 如果上述條件都不存在，則會使用 UPN 位址

## <a name="updating-with-powershell"></a>透過 PowerShell 更新
您也可以透過適用於 Azure Active Directory 的 PowerShell 來更新備用電子郵件地址。 做法是使用 [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser) 命令。

```
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

如需詳細資訊，請參閱 [Azure Active Directory PowerShell Version 2](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (Azure Active Directory PowerShell 版本 2)。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

