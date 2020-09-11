---
title: 適用於美國政府客戶的 Power BI - 概觀
description: 美國政府客戶可以將 Power BI Pro 訂用帳戶新增至其 Microsoft 365 政府方案。 了解如何在此服務描述中註冊及檢閱功能可用性。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/02/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: 2b5481e3d0b84f81a9cdee827df27c90e32a7e84
ms.sourcegitcommit: ae9e698b082598f37242080a3ad3dd0b3be08478
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89474786"
---
# <a name="power-bi-for-us-government-customers"></a>適用於美國政府客戶的 Power BI

本文適用於要在 Microsoft 365 政府方案中部署 Power BI 的美國政府客戶。 政府方案是針對必須符合美國合規性和安全性標準的組織獨特需求而設計。 為美國政府客戶設計的 Power BI 服務與商業版 Power BI 服務不同。 下列各節說明這些功能差異和功能。

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>將 Power BI 新增至 Microsoft 365 政府方案

您必須先註冊 Microsoft 365 政府方案，才能取得 Power BI 美國政府訂閱，並將授權指派給使用者。 如果組織已有 Microsoft 365 政府方案，請直接跳至[購買適用於政府客戶的 Power BI Pro 訂閱](#buy-a-power-bi-pro-subscription-for-government-customers)。

### <a name="enroll-in-a-microsoft-365-government-plan"></a>註冊 Microsoft 365 政府方案

如果是新客戶，即必須先驗證組織的資格，才能註冊 Microsoft 365 政府方案。  從填寫 [Microsoft 365 政府版資格驗證表單](https://www.microsoft.com/microsoft-365/government/eligibility-validation)開始。 為確保選取適用於組織的正確方案，請參閱 [Microsoft 365 美國政府服務說明](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government) (機器翻譯)。

> [!NOTE]
> 如果已經將 Power BI 部署到商業環境，且想要移轉至美國政府雲端，則必須將新的 Power BI Pro 訂閱新增至 Microsoft 365 政府方案。 接下來，將商業資料複寫到適用於美國政府的 Power BI 服務，從使用者帳戶中移除商業授權指派，然後將 Power BI Pro 政府授權指派給使用者帳戶。
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>購買適用於政府客戶的 Power BI Pro 訂用帳戶

當部署 Microsoft 365 之後，即可新增 Power BI Pro 訂閱。 請依照[註冊美國政府組織](service-govus-signup.md)中的逐步指導方針來購買 Power BI Pro 政府服務。 為需要使用 Power BI 的所有使用者購買足夠授權，然後將這些授權指派給個別使用者帳戶。

> [!IMPORTANT]
> Power BI 美國政府版本並未以「免費」授權形式提供。 若要存取政府社群雲端，就必須為每位使用者指派 *Pro* 授權。 如果已為使用者帳戶指派免費授權，則只授權該使用者存取商業雲端，而且將會遇到驗證和存取問題。 如果已購買 Power BI Premium，即無須指派 Pro 授權來啟用使用者存取。  只要將報表發佈至 Premium 容量，組織中的使用者就可以存取共用的報表。 若要檢閱授權類型之間的差異，請參閱[依授權類型分類的 Power BI 服務功能](../fundamentals/service-features-license-type.md)。
>

## <a name="government-cloud-instances"></a>政府雲端執行個體

Microsoft 365 為政府機關提供不同環境，以符合不同的合規性需求。 如需每個環境的詳細資訊，請參閱：

* [Microsoft 365 政府社群雲端 (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) (機器翻譯) 是專為聯邦、州和地方政府所設計。

* [Microsoft 365 政府社群雲端進階版 (GCC High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) (機器翻譯) 是專為各聯邦機關、國防產業、航太產業和其他持有管控非機密資訊的組織所設計。 此環境適用於有國際武器貿易條例 (ITAR) 資料或國防聯邦採購條例補充 (DFARS) 需求的國家/地區安全性組織和公司。

* [Microsoft 365 DoD 環境](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) (機器翻譯) 是專為美國國防部所設計。

## <a name="connect-to-power-bi-for-us-government"></a>連線到 Power BI for US Government

用來連線到 Power BI 的 URL 會因政府使用者和商業使用者而有所不同。 若要登入 Power BI，請使用下列 URL：

| 商用版本  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

您的帳戶可能設定於多個雲端中。 如果您的帳戶是以那種方式設定的，則當您在 Power BI Desktop 登入時，可以選擇要連線的雲端。

## <a name="connect-government-and-global-azure-cloud-services"></a>連線政府和全球 Azure 雲端服務

Azure 分散於多個雲端。 根據預設，您可以啟用防火牆規則來開啟與雲端特定執行個體的連線，但是跨雲端網路不同。  若要在公用雲端中的服務與政府社群雲端中的服務之間進行通訊，您必須設定特定防火牆規則。 例如，如果您想要從 Power BI 的政府雲端部署存取 SQL 資料庫的公用雲端執行個體，則在 SQL 資料庫中需要有防火牆規則。 設定適用於 SQL 資料庫的特定防火牆規則，以允許連線到下列資料中心的 Azure Government 雲端：

* USGov 愛荷華
* USGov 維吉尼亞
* USGov 德州
* USGov 亞歷桑那

在公用雲端中，有可用的 IP 範圍。 若要取得美國政府雲端 IP 範圍，請下載 [Azure IP 範圍和服務標籤 – 美國政府雲端](https://www.microsoft.com/download/details.aspx?id=57063)檔案。

若要針對 SQL 資料庫設定防火牆，請參閱[建立和管理 IP 防火牆規則](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules) \(部分機器翻譯\)。

## <a name="power-bi-feature-availability"></a>Power BI 功能可用性

為了符合政府雲端客戶的需求，政府方案與商業方案之間有一些差異。 我們的目標是要在正式運作後 30 天內，讓政府雲端中的所有功能皆可供使用。 在某些情況下，基礎相依性會導致我們無法提供功能。

下列資料表列出特定政府環境中無法使用的功能，以及規劃發行時預估的可用性：

|特徵 |GCC |GCC High |DoD|
|------|------|------|------|
|[政府與商業雲端之間的 Azure B2B 共同作業](service-admin-azure-ad-b2b.md) <sup>1</sup>|![可供使用](../media/yes.png)|![無法使用](../media/no.png)|![無法使用](../media/no.png)|
|[使用 Power BI 網頁組件內嵌在 SharePoint Online 中](https://docs.microsoft.com/esharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![可供使用](../media/yes.png)|![可用](../media/yes.png)|![無法使用](../media/no.png)|
|[適用於資料驅動警示的 Power Automate 連線能力](../connect-data/power-bi-data-sources.md)|![可供使用](../media/yes.png)|![可供使用](../media/yes.png)|![無法使用](../media/no.png)|
|[Teams 中的 Power BI 索引標籤](../collaborate-share/service-collaborate-microsoft-teams.md) <sup>2</sup>|![可供使用](../media/yes.png)|![無法使用](../media/no.png)|![無法使用](../media/no.png)|
|[容量計量](../admin/service-admin-premium-monitor-portal.md)|2020 年第 3 季 |2020 年第 3 季|2020 年第 3 季|
|[大型模型](service-premium-large-models.md) | 2020 年第 4 季 |2020 年第 4 季| ![無法使用](../media/no.png) |
|[資料流程 - SQL 計算引擎最佳化](../transform-model/service-dataflows-enhanced-compute-engine.md) | 2020 年第 4 季 |2020 年第 4 季| ![無法使用](../media/no.png) |
|[資料流程 - 直接查詢](../transform-model/service-dataflows-directquery.md) | 2020 年第 4 季 |2020 年第 4 季|![無法使用](../media/no.png)|
|[服務中斷通知](service-premium-large-models.md)|2020 年第 4 季 |2020 年第 4 季|2020 年第 4 季|
|[資料保護 (MIP 標籤)](service-security-sensitivity-label-overview.md)|2020 年第 4 季|2020 年第 4 季 |2020 年第 4 季|
|[範本應用程式](../connect-data/service-template-apps-overview.md) <sup>3</sup>|2020 年第 4 季 |2020 年第 4 季| 2020 年第 4 季|
|[自訂視覺效果](../developer/visuals/power-bi-custom-visuals.md) <sup>3</sup>|2020 年第 4 季 |2020 年第 4 季| 2020 年第 4 季|
|[QR 代碼產生](../create-reports/service-create-qr-code-for-tile.md)|![無法使用](../media/no.png)|![無法使用](../media/no.png)|![無法使用](../media/no.png)|

<sup>1</sup> 雖然 B2B 共同作業適用於 GCC，但必須在該環境中對外部使用者發出授權。 GCC 中的商業雲端授權無效。 如需適用於美國政府的 B2B 共同作業已知限制其詳細資訊，請[比較 Azure Government 及全域 Azure](https://docs.microsoft.com/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2) (英文)

<sup>2</sup> 適用於 GCC 的 Teams 其 Power BI 體驗受到限制，只能在傳統工作區上運作，且不包含[在 Microsoft Teams 中內嵌 Power BI 內容](../collaborate-share/service-embed-report-microsoft-teams.md)所述的增強功能。

<sup>3</sup> 範本應用程式功能與發行的自訂視覺效果將受到政府雲端限制。 更多特定限制的資訊將於發行時發佈。

## <a name="next-steps"></a>後續步驟

* [註冊 Power BI for US Government](service-govus-signup.md)
* [Microsoft Power Apps 美國政府](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate 美國政府](https://docs.microsoft.com/power-automate/us-govt)
* [Power BI US Gov 示範](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)
