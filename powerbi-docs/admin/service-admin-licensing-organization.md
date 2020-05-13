---
title: 組織中的 Power BI 授權
description: 概述 Power BI 中可用的各種不同授權類型，以及管理員如何為其組織購買和管理授權。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 1bd3af61bb7c1fe525a4e5822724ccb07c57eace
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344288"
---
# <a name="power-bi-licensing-in-your-organization"></a>組織中的 Power BI 授權

使用者能夠在 Power BI 服務中執行的動作取決於他們所具備的個別使用者授權，以及他們所操作的內容是否位於指派給 Power BI Premium 容量的工作區中。 Power BI 服務的所有使用者都必須具備授權。

使用者可透過兩種方式取得授權。 使用者可以使用自助式註冊功能及其工作或學校帳戶，來取得自己的免費或 Pro 授權。 或是管理員可以取得 Power BI 訂用帳戶，然後將授權指派給使用者。

此文章著重於從管理員觀點購買服務和個別使用者授權。 如需有關使用者如何取得自己授權的詳細資訊，請參閱[以個人身分註冊 Power BI](../fundamentals/service-self-service-signup-for-power-bi.md)。

## <a name="who-can-purchase-and-assign-licenses"></a>誰可以購買及指派授權？

您必須獲指派管理員角色，才能為您的組織購買或指派授權。 指派管理員角色時，會使用 Azure Active Directory 管理中心或 Microsoft 365 系統管理中心來指派。 下表顯示執行購買和授權相關工作所需的角色。 如需有關 Azure Active Directory 中管理員角色的詳細資訊，請參閱[在 Azure Active Directory 中檢視和指派管理員角色](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal) \(部分機器翻譯\)。 若要深入了解 Microsoft 365 中的系統管理員角色 (包括最佳做法)，請參閱[關於系統管理員角色](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide)。

| 誰可以購買服務和授權？ | 誰可以管理使用者授權？ |
| --------------- | --------------- |
| 計費管理員 | 授權管理員 |
| 全域管理員 | 使用者管理員 |
|  | 全域管理員 |

這些角色可管理組織。 如需有關 Power BI 服務管理員角色的資訊，請參閱[了解 Power BI 服務管理員角色](service-admin-role.md)。

## <a name="get-power-bi-for-your-organization"></a>為您的組織取得 Power BI

全域管理員或計費管理員可以註冊 Power BI 服務，並為其組織中的使用者購買授權。 如果您尚未做好購買準備，請選取 Power BI Pro 試用版。 您將獲得 25 個可使用一個月的授權。 如需有關如何註冊的逐步指示，請參閱[為組織取得 Power BI 訂用帳戶](service-admin-org-subscription.md)。

## <a name="about-self-service-sign-up"></a>關於自助式註冊

個別使用者可以使用其工作或學校帳戶來進行註冊，以取得自己的 Power BI 授權。 使用免費授權時，使用者可以使用 [我的工作區] 來探索 Power BI 以檢視個人資料分析和視覺效果，但無法起始與其他使用者的共同作業。 必要具備 Power BI Pro 授權，才能共用內容。 如果組織使用商務雲端，則使用者可將其授權類型升級至 Pro 或直接註冊 Pro。 直接購買或升級至 Pro 並不適用於教育組織，或部署至政府或主權雲端執行個體的組織。

如果您不想讓組織中的使用者使用自助式註冊，請參閱[啟用或停用自助式註冊](service-admin-disable-self-service.md)，以了解如何關閉此功能。

如果您想要查看組織中哪些使用者可能已經具備授權，請參閱[檢視和管理使用者授權](service-admin-manage-licenses.md)以了解做法。

## <a name="license-types-and-capabilities"></a>授權類型與功能

Power BI 個別使用者授權有兩種：免費和 Pro。 使用者需要哪種類型的授權，取決於內容的儲存位置及他們將與該內容互動的方式。 內容可儲存在哪裡，取決於您組織的[訂用帳戶類型](#subscription-types)。

其中一種訂用帳戶類型 [Power BI Premium](service-admin-premium-purchase.md) 可讓具備免費授權的使用者操作已指派給 Premium 容量之工作區中的內容。 在 Premium 容量之外，具備免費授權的使用者則只能使用 Power BI 服務來連線到資料，然後在個人工作區中建立報表和儀表板。 他們無法與其他人共用內容，或將內容發佈至應用程式工作區。

標準 Power BI 訂用帳戶會使用共用容量。 當內容儲存在共用容量中時，獲指派 Power BI Pro 授權的使用者只能與其他 Power BI Pro 使用者共同作業。 他們可以取用其他使用者所共用的內容、將內容發佈到應用程式工作區、共用儀表板，以及訂閱儀表板和報表。  當工作區在 Premium 容量中時，Pro 使用者可將內容散發給沒有 Power BI Pro 授權的使用者。

下表摘要說明每個授權類型的基本功能。 如需每一授權類型的詳細功能可用性明細，請參閱[依授權類型排列的功能](../fundamentals/service-features-license-type.md)。

| 授權類型 | 工作區在共用容量中時的功能 | 工作區在 Premium 容量中時的額外功能 |
| --------- | ----------- | ----------- |
| Power BI (免費) | 存取我的工作區中的內容 | 取用與其共用的內容 |
| Power BI Pro | 將內容發佈到應用程式工作區、共用儀表板、訂閱儀表板和報表、與具備 Pro 授權的使用者共用 | 將內容散發給具備免費授權的使用者 |

## <a name="subscription-types"></a>訂用帳戶類型

所有來自 Microsoft 的使用者型商業授權訂用帳戶都是以 Azure Active Directory 身分識別為基礎。 這意謂著您必須使用 Azure Active Directory 支援的商業授權身分識別來進行登入。 您可以將 Power BI 訂用帳戶新增至任何使用 Azure Active Directory 作為身分識別服務的 Microsoft 訂用帳戶。 某些訂用帳戶 (例如 Office 365 E5) 包含 Power BI Pro 授權，因此無須個別註冊 Power BI。

有兩種適用於組織的 Power BI 訂用帳戶：自助 BI 搭配的是 Power BI Pro，進階分析則搭配 Power BI Premium。

使用標準自助 Power BI Pro 訂用帳戶時，管理員可以指派個別使用者授權。 Power BI Pro 授權有個別使用者月費，可啟用共同作業、發佈、共用及臨機操作分析。 內容會儲存到完全由 Microsoft 管理的共用儲存體容量。

Power BI Premium 訂用帳戶會為組織配置專用容量。 Premium 適用於企業 BI、巨量資料分析及雲端與內部部署報告，可提供進階的管理和部署控制。 專用計算與儲存體資源是由您組織中的容量管理員所管理。 此專用環境有每月費用。 除了其他 Premium 優點之外，儲存在 Premium 容量中的內容還可供沒有 Power BI Pro 授權的使用者存取，以及散發給這些使用者。 必須至少有一位使用者獲指派 Power BI Pro 授權，才能使用 Premium，而內容建立者與開發人員則仍然需要 Power BI Pro 授權。

這兩種訂用帳戶類型並不互斥。 您可以同時具備 Power BI Premium 和 Power BI Pro。 在此組態中，儲存在 Premium 容量中的內容可以與所有使用者共用，且共用容量也可供使用。 如需有關容量限制的資訊，請參閱[管理 Power BI 工作區中的資料儲存體](service-admin-manage-your-data-storage-in-power-bi.md)。

若要比較產品功能與定價，請參閱 [Power BI 定價](https://powerbi.microsoft.com/pricing)。

## <a name="guest-user-access"></a>來賓使用者存取權

您可能會想要將內容散發給組織外的使用者。 您可以透過邀請外部使用者以來賓身分檢視內容，與他們共用內容。 透過 Azure Active Directory 企業對企業 (Azure AD B2B) 可與外部來賓使用者進行共用。 若要與外部使用者共用，必須符合下列先決條件：

- 必須啟用與外部使用者共用內容的功能

- 來賓使用者必須具備可檢視共用內容的適當授權

如需有關來賓使用者存取權的詳細資訊，請參閱[使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者](service-admin-azure-ad-b2b.md)。

## <a name="purchase-power-bi-pro-licenses"></a>購買 Power BI Pro 授權

身為管理員，您可以透過 Microsoft Office 365 或 Microsoft 合作夥伴購買 Power BI Pro 授權。 購買授權之後，您可以將它們指派給個別使用者。 如需詳細資訊，請參閱[購買及指派 Power BI Pro 授權](service-admin-purchasing-power-bi-pro.md)。

### <a name="power-bi-pro-license-expiration"></a>Power BI Pro 授權到期

在 Power BI Pro 授權到期後有一段寬限期。 若是屬於大量授權購買的授權，寬限期為 90 天。 如果您直接購買授權，則寬限期為 30 天。

Power BI Pro 具有與 Office 365 相同的訂用帳戶生命週期。 如需詳細資訊，請參閱[當商務用 Office 365 訂閱結束時，我的資料與存取權會發生什麼情況？](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3) \(部分機器翻譯\)。


## <a name="next-steps"></a>後續步驟

- [購買及指派 Power BI Pro 授權](service-admin-purchasing-power-bi-pro.md)
- [Microsoft 365 商務訂閱與計費文件](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)
- [尋找已登入的 Power BI 使用者](service-admin-access-usage.md)
- 有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
