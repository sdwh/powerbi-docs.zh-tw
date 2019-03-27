---
title: 尋找已登入的 Power BI 使用者
description: 如果您是租用戶系統管理員，而且想要查看誰已登入 Power BI，可以使用 Azure Active Directory 存取和使用情況報告來了解情形。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 26cf9b10d2a7bfffca151fe36cd45626487b6eef
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383638"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>尋找已登入的 Power BI 使用者

如果您是租用戶系統管理員，而且想要查看誰已登入 Power BI，可以使用 [Azure Active Directory 存取和使用情況報告](/azure/active-directory/reports-monitoring/concept-sign-ins)來了解情形。

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> 活動報告可提供有用的資訊，但它無法識別每個使用者擁有的授權類型。 請使用 Microsoft 365 系統管理中心來檢視授權。

## <a name="requirements"></a>需求

任何使用者 (包括非系統管理員) 都能看到他們自己的登入報告，但您必須符合下列要求，才能看到所有使用者的報告。

* 您的租用戶必須與 Azure AD Premium 授權相關聯。

* 您必須是下列角色之一：全域管理員、安全性管理員或安全性讀取者。

## <a name="use-the-azure-portal-to-view-sign-ins"></a>使用 Azure 入口網站來檢視登入

若要檢視登入活動，請遵循這些步驟。

1. 在 [Azure 入口網站] 中，選取 [Azure Active Directory]。

1. 在 [監視] 底下，選取 [登入]。
   
    ![Azure AD 登入](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. 依 [Microsoft Power BI] 或 [Power BI Gateway] 來篩選應用程式，然後選取 [套用]。

    [Microsoft Power BI] 會篩選出與服務相關的登入活動，而 [Power BI Gateway] 會篩選出特定於內部部署資料閘道的登入活動。
   
    ![篩選登入](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>匯出資料

您有兩個選項可以匯出登入資料：下載 csv 檔案，或使用 PowerShell。 在登入報告的頂端，選取下列選項之一：

* [下載] 可下載目前篩選之資料的 csv 檔案。

* [指令碼] 可下載目前篩選之資料的 PowerShell 指令碼。 您可以視需要更新指令碼中的篩選條件。

![下載 csv 檔案或指令碼](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>資料保留

登入相關的資料保留最多 30 天。 如需詳細資訊，請參閱 [Azure Active Directory 報告保留原則](/azure/active-directory/reports-monitoring/reference-reports-data-retention)。

## <a name="next-steps"></a>後續步驟

[在組織內使用稽核](service-admin-auditing.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

