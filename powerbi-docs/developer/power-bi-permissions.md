---
title: Power BI 權限
description: Power BI 權限
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 06901a484ca53881f30cc71d9a7404807ac6cd57
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73429129"
---
# <a name="power-bi-permissions"></a>Power BI 權限

## <a name="permission-scopes"></a>權限範圍

Power BI 權限可賦予應用程式代表使用者採取某些動作。 所有權限必須經由使用者核准才會生效。

| 顯示名稱 | 描述 | 範圍值 |
| --- | --- | --- |
| 檢視所有資料集 |應用程式可以檢視已登入使用者的所有資料集，和使用者可存取的資料集。 |Dataset.Read.All |
| 讀取和寫入所有資料集 |應用程式可以檢視與寫入已登入使用者的所有資料集，和使用者可存取的資料集。 |Dataset.ReadWrite.All |
| 將資料新增至使用者的資料集 |賦予應用程式新增或刪除使用者之資料集資料列的存取權。 此權限不會授權應用程式存取使用者的資料。 |Data.Alter_Any |
| 建立內容 |應用程式可以自動為使用者建立內容和資料集。 |Content.Create |
| 檢視使用者群組 |應用程式可以檢視已登入使用者所屬的所有群組。 |Group.Read |
| 檢視所有群組 |應用程式可以檢視已登入使用者所屬的所有群組。 |Group.Read.All |
| 讀取和寫入所有群組 |應用程式可以檢視和寫入已登入使用者的所有群組，以及使用者可存取的任何群組。 |Group.ReadWrite.All |
| 檢視所有儀表板 |應用程式可以檢視已登入使用者的所有儀表板，和使用者可存取的儀表板。 |Dashboard.Read.All |
| 檢視所有報表 |應用程式可以檢視已登入使用者的所有報表，和使用者可存取的報表。 應用程式也可以查看報表內的資料以及其結構。 |Report.Read.All |
| 讀取和寫入所有報告 |應用程式可以檢視和寫入已登入之使用者的所有報告，以及使用者可存取的任何報告。 這不提供建立新報告的權限。 |Report.ReadWrite.All |
| 讀取和寫入所有容量 |應用程式可以檢視和寫入已登入使用者的所有容量，以及使用者可存取的任何容量。 這不提供建立新容量的權限。 |Capacities.ReadWrite.All |
| 讀取所有容量 |應用程式可以檢視和寫入已登入使用者的所有容量，以及使用者可存取的任何容量。 這不提供建立新容量的權限。 |Capacities.Read.All |
| 讀取和寫入租用戶中的所有內容 |應用程式可以檢視和寫入 Power BI 中的所有成品，例如群組、報表、儀表板和資料集。 若登入的使用者是 Power BI 服務系統管理員。 |Tenant.ReadWrite.All |
| 檢視租用戶中的所有內容 |應用程式可以檢視 Power BI 中的所有成品，例如群組、報表、儀表板和資料集。 若登入的使用者是 Power BI 服務系統管理員。 |Tenant.Read.All |

應用程式可以在第一次嘗試登入使用者頁面時，藉由在呼叫的範圍參數中，傳遞所要求權限來要求權限。 若授與權限，將會傳回存取權杖給應用程式，供後續的 API 呼叫使用。 只有特定應用程式才可使用此存取權。

> [!NOTE]
> Power BI API 仍然將工作區稱為群組。 任何對群組的參考都表示您正在使用工作區。

## <a name="requesting-permissions"></a>要求權限

雖然您可以呼叫 API 來驗證使用者名稱及密碼，以便能代表其他使用者採取動作，他們仍須先要求權限，待使用者核准之後，才會傳送產生的存取權杖，供後續的所有呼叫之用。 在處理序中，我們會遵循標準 [OAuth 2.0](http://oauth.net/2/) 通訊協定。 實際實作可能有所不同，Power BI 的 OAuth 流程包含下列項目：

* **登入 UI** - 這是開發人員可以呼叫來要求權限的 UI。 如果使用者尚未登入，將會要求使用者登入。 使用者也必須核准應用程式所要求的權限。 登入視窗會回傳所提供之重新導向 URL 的存取碼或錯誤訊息。
  * 標準的重新導向 URL 應該由 Power BI 提供，以供原生應用程式使用。
* **授權碼** - 當透過重新導向 URL 中的 URL 參數登入之後，會將授權碼傳回給 Web 應用程式。 因為授權碼包含在參數中，所以仍有一些安全性風險存在。 Web 應用程式必須使用授權碼來交換授權權杖
* **授權權杖** - 這會用來代表另一位使用者驗證 API 呼叫。 只有特定應用程式才可使用這些權杖。 權杖有既定的壽命，當其時限屆滿時，就必須更新。
* **更新權杖** - 當權杖到期時，將會執行更新程序。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)