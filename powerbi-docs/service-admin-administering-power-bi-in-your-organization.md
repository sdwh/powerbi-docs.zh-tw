---
title: 什麼是 Power BI 管理？
description: 了解 Power BI 控管原則的設定、使用狀況監控，以及授權容量及組織資源的佈建。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: overview
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 57819765b156baac2a86b8144e86770a0117adfd
ms.sourcegitcommit: d5de66b591c2e1de979ce0e3ce5e5b6e1f2a08db
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548576"
---
# <a name="what-is-power-bi-administration"></a>什麼是 Power BI 管理？

Power BI 管理是 Power BI 租用戶的管理，包括控管原則的設定、使用狀況監控，以及授權、容量及組織資源的佈建。 本文提供管理角色、工作、工具的概觀，以及深入探討細節的文章連結。

![Power BI 管理入口網站](media/service-admin-administering-power-bi-in-your-organization/admin-portal.png)

Power BI 是針對自助商業智慧而設計，而系統管理員是 Power BI 租用戶中資料、程序和原則的守護者。 針對包含 BI 開發人員、分析師和其他角色的小組，Power BI 系統管理員是小組中的重要成員。 系統管理員可協助組織，確保達成重要目標：

- 了解使用者_實際_需要的 KPI 和計量
- 減少傳送 IT 導向公司報告的時間
- 增加採用並從 Power BI 部署獲得投資報酬

該工作是負責提升商務使用者的生產力，並確保安全性和對法律與規定的合規性。 責任可能包括說明及支援，在許多情況下，還要協助商務使用者做正確的事。

## <a name="administrator-roles-related-to-power-bi"></a>與 Power BI 相關的系統管理員角色

有數個角色與 Power BI 管理相關，如下表所示。

| **系統管理員的類型** | **管理範圍** | **Power BI 範圍** |
| --- | --- | --- |
| Office 365 全域管理員 | Office 365 | 可管理 Power BI 租用戶的各個層面及其他服務。 |
| Office 365 計費管理員 | Office 365 | 可透過 Office 365 訂閱取得 Power BI 授權。 |
| Power BI 服務管理員 | Power BI 租用戶 | 對 Power BI 租用戶和其系統管理功能 (除了授權以外) 有完整的控制權。 |
| Power BI Premium 容量管理員 | 單一 Premium 容量 | 對於 Premium 容量和其系統管理功能有完整的控制權。 |
| Power BI Embedded 容量管理員 | 單一 Embedded 容量 | 對於 Embedded 容量和其系統管理功能有完整的控制權。 |

Office 365 或 Azure Active Directory 中的全域管理員，在 Power BI 中有系統管理員權限。 Office 365 全域管理員可以將 Power BI 服務系統管理員角色指派給其他使用者，這樣只會授與 Power BI 的系統管理權限。

Power BI 服務系統管理員可以存取 Power BI 管理入口網站，其中包含有關功能、安全性和監視等各種租用戶層級的設定。 服務系統管理員擁有 Power BI 租用戶所有資源的完整存取權。 在大部分情況下，服務系統管理員會識別問題，然後追蹤資源擁有者以採取更正動作。

Power BI 服務系統管理員角色不會將指派授權的能力授與使用者，或在 Office 365 中檢視稽核記錄的能力。 因此，僅是 Power BI 服務系統管理員角色的使用者，目前無法執行管理 Power BI 的工作。

## <a name="administrative-tasks"></a>管理工作

系統管理員會執行許多工作，以支援其組織的 Power BI 租用戶，下表包含這些工作。

| **工作區域** | **一般工作** |
| --- | --- |
| 管理 Power BI 租用戶 |<ul><li>啟用和停用 Power BI 重要功能<br><li>報告使用狀況和效能<br><li>檢閱及管理事件的稽核</ul>|
| 取得及指派 Power BI 授權 |<ul><li>管理使用者註冊<br><li>購買及指派 Pro 授權<br><li>封鎖使用者對 Power BI 的存取</ul>|
| 管理 Premium 容量 |<ul><li>取得及使用 Premium 容量<br><li>確保服務品質|
| 管理 Embedded 容量 |<ul><li>取得 Embedded 容量以簡化 ISV 和開發人員使用 Power BI 功能的方式</ul>|
| 確定對內部原則、法律和規定的合規性 | <ul><li>管理商務資料的分類<br><li>協助執行內容發佈和共用原則</ul>|
| 管理 Power BI 資源 |<ul><li>管理工作區<br><li>發行自訂視覺效果<br><li>驗證用來在其他應用程式中嵌入 Power BI 的程式碼|
| 為租用戶使用者提供說明和支援 |<ul><li>針對資料存取和其他問題進行疑難排解</ul>|
| 其他工作 |<ul><li>部署 Power BI Desktop (例如：使用 Microsoft Endpoint Configuration Manager)<br><li>使用 Intune 管理 Power BI 行動應用程式部署<br><li>管理資料隱私權和安全性，例如來源資料安全性</ul>|

## <a name="administrative-tools"></a>系統管理工具

有數個工具與 Power BI 管理相關，如下表所示。 系統管理員通常將大部分時間花在 Power BI 管理入口網站中，並視需要使用其他工具。

| **工具** | **一般工作** |
| --- | --- |
| Power BI 管理入口網站 |<ul><li>取得及使用 Premium 容量</li><li>確保服務品質</li><li>管理商務資料的分類</li><li>協助執行內容發佈和共用原則</li><li>管理工作區<br><li>發行自訂視覺效果</li><li>驗證用來在其他應用程式中嵌入 Power BI 的程式碼</li><li>針對資料存取和其他問題進行疑難排解</li></ul>|
| MIcrosoft 365 系統管理中心 |<ul><li>管理使用者註冊</li><li>購買及指派 Pro 授權</li><li>封鎖使用者對 Power BI 的存取</li></ul>|
| Office 365 安全性與合規性中心 |<ul><li>檢閱及管理事件的稽核</li></ul>|
| Azure 入口網站中的 Azure Active Directory (AAD) |<ul><li>透過 AAD 設定對 Power BI 的條件式存取</li><li>佈建 Power BI Embedded 容量</li></ul>|
| PowerShell Cmdlet |<ul><li>透過指令碼管理工作區和 Power BI 的其他層面</li></ul>|
| 系統管理 API 和 SDK |<ul><li>建置自訂的系統管理工具，以協助 Power BI 系統管理員的工作。例如，Power BI Desktop 可以使用這些 API 來建立以系統管理相關資料為基礎的報表</li></ul>|

## <a name="next-steps"></a>後續步驟

我們希望本文能提供您對 Power BI 系統管理員工作，以及相關特定角色、工作與工具的快速深入剖析。 我們推薦以下兩個文章主題，讓您更深入了解。

[使用 Power BI 管理入口網站](service-admin-portal.md)

[使用 PowerShell Cmdlet](/powershell/power-bi/overview)

[Power BI 管理常見問題集](service-admin-faq.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)