---
title: 尋找已登入的 Power BI 使用者
description: 如果您是租用戶系統管理員且想要查看誰已登入 Power BI 時，您可以使用 Azure Active Directory 存取和使用方式報表來了解。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906706"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>尋找已登入的 Power BI 使用者

如果您是租用戶系統管理員且想要查看誰已登入 Power BI 中，使用[Azure Active Directory 存取和使用方式報告](/azure/active-directory/reports-monitoring/concept-sign-ins)來了解。

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> **登入**報表會提供有用的資訊，但它不會識別每個使用者擁有的授權類型。 請使用 Microsoft 365 系統管理中心來檢視授權。

## <a name="requirements"></a>需求

任何使用者 (包括非系統管理員) 都能看到他們自己的登入報告，但您必須符合下列要求，才能看到所有使用者的報告。

* 您的租用戶必須有與其相關聯的 Azure Active Directory Premium 授權。

* 您必須是下列角色之一：全域管理員、安全性管理員或安全性讀取者。

## <a name="use-the-azure-portal-to-view-sign-ins"></a>使用 Azure 入口網站來檢視登入

若要檢視登入活動，請遵循這些步驟。

1. 在 [Azure 入口網站]  中，選取 [Azure Active Directory]  。

1. 在 [監視]  底下，選取 [登入]  。
   
    ![Azure 使用者介面，以反白顯示 Azure Active Directory 和 登入選項的螢幕擷取畫面。](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. 依 [Microsoft Power BI]  或 [Power BI Gateway]  來篩選應用程式，然後選取 [套用]  。

    **Microsoft Power BI**與服務，而相關的登入活動的篩選條件**Power BI Gateway**篩選器，以登入活動特有的內部部署資料閘道。
   
    ![反白顯示的應用程式欄位的登入篩選器的螢幕擷取畫面。](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>匯出資料

您可以[下載登入報表](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report)兩種格式之一： CSV 檔案或 JSON 檔案。

![[下載] 按鈕的螢幕擷取畫面。](media/service-admin-access-usage/download-sign-in-data-csv.png)

在頂端**登入**報表中，選取**下載**，然後選取下列選項之一：

* **CSV**下載目前篩選之資料的 CSV 檔案。

* **JSON**下載目前篩選之資料的 JSON 檔案。

## <a name="data-retention"></a>資料保留

登入相關的資料保留最多 30 天。 如需詳細資訊，請參閱 < [Azure Active Directory 報告保留原則](/azure/active-directory/reports-monitoring/reference-reports-data-retention)。

## <a name="next-steps"></a>後續步驟

[在組織內使用稽核](service-admin-auditing.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)