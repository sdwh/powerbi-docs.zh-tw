---
title: 尋找已登入的 Power BI 使用者
description: 如果您是租用戶系統管理員，且想要查看誰已登入 Power BI，可以使用 Azure Active Directory 存取和使用情況報告來了解情形。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 4f9b69e863b71fda0cece06df7065740bd55463e
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85228896"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>尋找已登入的 Power BI 使用者

如果您是租用戶系統管理員，且想要查看誰已登入 Power BI，可以使用 [Azure Active Directory 存取和使用情況報告](/azure/active-directory/reports-monitoring/concept-sign-ins)來了解情形。

> [!NOTE]
> **登入**報告可提供有用的資訊，但它無法識別每個使用者擁有的授權類型。 請使用 Microsoft 365 系統管理中心來檢視授權。

## <a name="requirements"></a>要求

任何使用者 (包括非系統管理員) 都能看到他們自己的登入報告，但您必須符合下列要求，才能看到所有使用者的報告。

* 您的租用戶必須與 Azure Active Directory Premium 授權建立關聯。

* 您必須是下列角色之一：全域管理員、安全性管理員或安全性讀取者。

## <a name="use-the-azure-portal-to-view-sign-ins"></a>使用 Azure 入口網站來檢視登入

若要檢視登入活動，請遵循這些步驟。

1. 在 [Azure 入口網站]  中，選取 [Azure Active Directory]  。

1. 在 [監視]  底下，選取 [登入]  。
   
    ![醒目提示 [Azure Active Directory] 和 [登入] 選項的 Azure UI 螢幕擷取畫面。](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. 依 [Microsoft Power BI]  或 [Power BI Gateway]  來篩選應用程式，然後選取 [套用]  。

    **Microsoft Power BI** 會篩選出與服務相關的登入活動，而 **Power BI Gateway** 會篩選出特定於內部部署資料閘道的登入活動。
   
    ![醒目提示 [應用程式] 欄位的登入篩選螢幕擷取畫面。](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>匯出資料

您可以[下載兩種格式的登入報告](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report)：CSV 檔案或 JSON 檔案。

![[下載] 按鈕的螢幕擷取畫面。](media/service-admin-access-usage/download-sign-in-data-csv.png)

在**登入**報告的頂端，選取 [下載]  ，然後選取下列選項之一：

* [CSV]  可下載目前篩選資料的 CSV 檔案。

* [JSON]  可下載目前篩選資料的 JSON 檔案。

## <a name="data-retention"></a>資料保留

登入相關的資料保留最多 30 天。 如需詳細資訊，請參閱 [Azure Active Directory 報告保留原則](/azure/active-directory/reports-monitoring/reference-reports-data-retention)。

## <a name="next-steps"></a>後續步驟

[在組織內使用稽核](service-admin-auditing.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)