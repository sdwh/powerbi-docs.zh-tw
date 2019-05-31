---
title: 關於 Power BI Embedded 的常見問題集
description: 瀏覽 Power BI Embedded 相關的常見問題與回答清單。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 1bdc31d550573b926d45776307b8fcade95f0dc0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222185"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>關於 Power BI Embedded 的常見問題集

* 如果您有其他問題，請[嘗試詢問 Power BI 社群](http://community.powerbi.com/)。
* 仍有問題嗎？ 瀏覽 [Power BI 支援頁面](https://powerbi.microsoft.com/support/)。

## <a name="general"></a>一般

### <a name="what-is-power-bi-embedded"></a>什麼是 Power BI Embedded？

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md)可讓應用程式開發人員在他們的應用程式內嵌令人讚嘆、 具全面互動性的報表，而不必建置自己的資料視覺效果和全新的控制項。

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Power BI Embedded 的目標對象是誰？

開發人員和軟體公司，也就是獨立軟體廠商 (Isv) 撰寫程式碼應用程式。

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Power BI Embedded 和 Power BI 服務有何不同？

Power BI 是軟體即服務分析解決方案，為組織提供最重要商務資料的單一檢視。

Microsoft 開發了 Power BI Embedded 適用於 Isv 想要將視覺效果內嵌到他們的應用程式，以協助客戶進行分析的決策。 這可以 Isv 節省不必自行建置自己的分析解決方案。 [內嵌分析](embedding.md)可讓商務使用者能夠存取商務資料，並針對它產生深入解析應用程式內執行查詢。


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Power BI Premium 與 Power BI Embedded 之間的差異為何？

Power BI Premium 是專為企業想提供其組織、 夥伴、 客戶和供應商的單一檢視的完整 BI 解決方案的容量。 Power BI Premium 可協助您的組織制定決策。 Power BI Premium 是 SaaS 產品，可讓使用者使用行動應用程式，內部開發的應用程式，或在 Power BI 入口網站的內容。

Power BI Embedded 適用於 Isv 想要將視覺效果內嵌到應用程式。 因為 Power BI Embedded 適用於應用程式開發人員，不論該應用程式的客戶是組織內部或外部的任何人員，都能取用儲存在 Power BI Embedded 容量中的內容，進而協助您的客戶制定決策。 您無法共用 Power BI Embedded 容量內容會流過單鍵發佈至網路或單鍵發行至 SharePoint。

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Microsoft 對於客戶購買 Power BI Premium 與 Power BI Embedded 的時機有什麼建議？

Microsoft 建議企業購買 Power BI Premium，企業級的自助雲端 BI 解決方案。 我們建議您針對其雲端技術的內嵌的分析元件 Isv 購買 Power BI Embedded。 不過，客戶有購買的產品沒有限制。

可能有某些情況的下，ISV （通常是大型的），除了應用程式內嵌，想要使用 P SKU，以取得預先封裝 Power BI 服務在其組織中的其他優點。 有些企業只想建置企業營運應用程式並在其中內嵌分析，而不想使用預先封裝的 Power BI 服務，也可能決定使用 Azure 中的 A SKU。

### <a name="how-many-embed-tokens-can-i-create"></a>我可以建立多少內嵌權杖？

內嵌權杖具有 PRO 授權僅供開發測試，因此 Power BI 主要帳戶或[服務主體](embed-service-principal.md)只能產生有限的數目的語彙基元。 [購買容量](#technical)以在生產環境中進行內嵌作業。 內嵌的權杖，您可以將購買容量時產生數量沒有限制。 請移至 [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) (可用功能) 來檢查指出目前內嵌使用情況百分比的使用情況值。

## <a name="technical"></a>技術

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Azure 中的 A SKU 和 Office 365 中的 EM SKU 有何差異？

PowerBI.com 是企業的軟體即服務 (SaaS) 解決方案具有許多功能，例如社交共同作業、 電子郵件訂用帳戶，以及其他功能。 PowerBI.com 中，可協助 Isv 管理其內容的內嵌的分析解決方案和租用戶層級的設定。

Power BI Embedded 是一個平台服務 (PaaS) 設定的 Api 開發人員可以用來建立內嵌的分析解決方案。

以下是部分清單的功能差異。

| 特徵 | Power BI Embedded | Power BI Premium 容量 | Power BI Premium 容量 |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (A SKU) | (EM SKU) | (P SKU) |
| 從 Power BI 應用程式工作區內嵌成品 | Azure 容量 | Office 365 容量 | Office 365 容量 |
| 在 Embedded 應用程式中取用 Power BI 報表 | 是 | 是 | 是 |
| 在 SharePoint 中取用 Power BI 報表 | 否 | 是 | 是 |
| 在 Dynamics 中取用 Power BI 報表 | 否 | 是 | 是 |
| 在 Teams 中取用 Power BI 報表 (行動裝置應用程式除外) | 否 | 是 | 是 |
| 使用 Powerbi.com 和 Power BI 行動版中的免費 Power BI 授權存取內容 | 否 | 否 | 是 |
| 使用內嵌在 MS Office 應用程式中的免費 Power BI 授權存取內容 | 否 | 是 | 是 |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI 現在提供三種 SKU 以供內嵌：A SKU、EM SKU 及 P SKU。 我該為案例購買哪一種？

|  |A SKU (Power BI Embedded)  |EM SKU (Power BI Premium)  |P SKU (Power BI Premium)  |
|---------|---------|---------|---------|
|購買  |Azure 入口網站 |Office |Office |
|使用案例 | 在您自己的應用程式中內嵌內容 | <li> 在您自己的應用程式中內嵌內容 <br><br><br> <li> 在 MS Office 應用程式中內嵌內容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (行動裝置應用程式除外)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> 在您自己的應用程式中內嵌內容 <br><br><br> <li> 在 MS Office 應用程式中內嵌內容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (行動裝置應用程式除外)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> 透過 [Power BI 服務](https://powerbi.microsoft.com/)與 Power BI 使用者共用內容  |
|計費 |每小時 |每月 |每月 |
|承諾用量  |無承諾用量 |每年  |每月/每年 |
|差異 |完整彈性 - 可以在 Azure 入口網站中，或透過 API 相應增加/減少、暫停/繼續資源  |您可以使用將內容內嵌在 SharePoint Online 和 Microsoft Teams （不包括行動裝置應用程式） |在相同容量中結合應用程式內嵌及使用 Power BI 服務 |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>在 Azure 中建立 PBIE 容量的必要條件為何？

* 登入您組織的目錄 (Microsoft 不支援帳戶)。
* 您需要有 Power BI 租用戶，也就是您目錄中的至少一個使用者已註冊 Power bi。 
* 您在組織目錄中須有 Azure 訂用帳戶。

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>如何監視 Power BI Embedded 容量耗用量？

* [使用 Power BI 管理入口網站](../service-admin-portal.md#power-bi-embedded)。

* 下載 Power BI 中的[計量應用程式](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity)。

* 使用 [Azure 診斷記錄](azure-pbie-diag-logs.md)。

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>可以我容量調整自動調整到我的應用程式使用？

雖然沒有自動縮放比例現在，所有 Api 都能隨時調整。

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>為什麼建立/調整/繼續容量會讓容量進入暫止狀態？

容量佈建 （刻度/繼續/建立） 可能會失敗。 您可以使用 「 取得詳細資料 API 來檢查容量的 ProvisioningState:[Capacities - Get Details](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails) (容量 - 取得詳細資料)。

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>是否只能在特定區域中建立 Power BI Embedded 容量？

利用[多地理位置 (預覽)](embedded-multi-geo.md) 功能，您可以在不同於 Power BI 主租用戶位置的區域中購買 [Power BI Embedded 容量](azure-pbie-create-capacity.md)

### <a name="how-can-i-find-my-pbi-tenant-region"></a>如何找到我的 PBI 租用戶所在區域？

您可以使用 PBI 入口網站來尋找您 PBI 租用戶的區域。

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > 關於 Power BI

![關於 Power BI](media/embedded-faq/about-01.png)
![租用戶區域](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>雲端解決方案提供者 (CSP) 通道支援是什麼？

* 您可以針對具有訂用帳戶類型 CSP 的租用戶建立 PBIE
* 夥伴帳戶可以登入客戶的租用戶，並為客戶租用戶購買 PBIE，以及指定客戶租用戶使用者為 Power BI 的容量管理員

### <a name="why-do-i-get-an-unsupported-account-message"></a>為什麼會收到不受支援帳戶的訊息？

Power BI 需要您使用組織帳戶註冊。 嘗試註冊使用 Microsoft 帳戶的 Power BI 不支援。

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>可以使用 Api 來建立和管理 Azure 容量嗎？

是，有 Powershell cmdlet 和 Azure Resource Manager REST Api 可用來建立和管理 PBIE 資源。

* [Rest Api](https://docs.microsoft.com/rest/api/power-bi-embedded/)
* [Powershell cmdlet](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>PBI Embedded 解決方案中的 PBI Embedded 專用容量角色是什麼？

若要[升階到生產環境方案](embed-sample-for-customers.md#move-to-production)，您需要將您的應用程式會使用 Power BI 內容 （應用程式工作區） 指派給 Power BI Embedded (SKU) 的容量。

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>在哪些 Azure 區域可內嵌 PBI？

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) - 請參閱產品可用性管理員

可用區域 (16 - 與 Power BI 相同的區域)

* 美國 (6) - 美國東部、美國東部 2、美國中北部、美國中南部、美國西部、美國西部 2
* 歐洲 (2) - 北歐、西歐
* 亞太地區 (2) - 東南亞、東亞
* 巴西 (1) - 巴西南部
* 日本 (1) - 日本東部
* 澳大利亞 (1) - 澳大利亞東南部
* 印度 (1) - 印度西部
* 加拿大 (1) - 加拿大中部
* 英國 (1) - 英國南部

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Power BI Embedded 的驗證模型是什麼？

Power BI Embedded 會繼續使用 Azure AD 進行主使用者 （指定的 Power BI Pro 授權使用者） 驗證，或使用[服務主體](embed-service-principal.md)驗證 Power BI 內的應用程式。  

 ISV 可以實作自己的驗證與授權給他們的應用程式。

如果您已經有 Azure AD 租用戶，您可以使用您現有的目錄。 您也可以建立新的 Azure AD 租用戶的您內嵌的應用程式內容的安全性。

若要取得 AAD 權杖，可以使用其中一個 [Azure Active Directory 驗證程式庫](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)。 有適用於多種平台的用戶端程式庫。

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>我的應用程式已使用 AAD 來驗證使用者。 在「使用者擁有資料」情節中，驗證到 Power BI 時，如何使用此身分識別？

它是標準 OAuth 上的代理者流程 (<https://docs.microsoft.com/azure/active-directory/develop/web-api>)。 您需要設定您的應用程式需要 Power BI 服務 （有必要的範圍） 的權限。 一旦您有使用者權杖至您的應用程式時，只要呼叫至 ADAL 使用的使用者存取的 API AcquireTokenAsync 權杖，並作為資源識別碼中指定的 Power BI 資源的 URL:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>什麼物件識別碼是服務主體物件識別碼嗎？

*物件識別碼*從註冊的應用程式的主畫面是 應用程式的物件識別碼。

識別碼中所找到的物件*受管理的本機目錄中的應用程式 > 內容*區段是您要使用的服務主體物件識別碼。 此物件識別碼是以參考作業的服務主體，或是變更服務主體物件識別碼。 例如身為系統管理員的服務主體套用至工作區中。

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Power BI Embedded 和 Azure 服務有何不同？

您必須有 Power BI 帳戶，才能購買 Power BI Embedded 在 Azure 中。 您的 Power BI Embedded 部署區域會決定您的 Power BI 帳戶。 在 Azure 中管理您的 Power BI Embedded 資源，能夠：

* 相應增加/減少
* 新增容量管理員
* 暫停/繼續服務

使用 PowerBI.com 對 Power BI Embedded 容量指派/解除指派工作區。

### <a name="what-are-the-supported-deploy-regions"></a>什麼是支援部署區域？

澳洲東南部、巴西南部、加拿大中部、美國東部 2、印度西部、日本東部、美國中北部、北歐、美國中南部、東南亞、英國南部、西歐、美國西部及美國西部 2。

### <a name="what-content-pack-data-types-can-you-embed"></a>您可以將內嵌何種內容套件資料類型？

您*無法*內嵌**儀表板**並**磚**建置內容套件資料集。 不過，您*可以*內嵌**報表**建置內容套件資料集。

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>什麼是使用資料列層級安全性 (RLS) 與之間的差異。篩選的差別在哪裡？

時通常會混淆與 JavaScript 的篩選器，使用 RLS，因為其中一個方法是控制功能的相關特定使用者所見，和另一個是關於最佳化的使用者檢視。

對於 RLS，ISV 開發人員可控制屬於建立模型和產生內嵌權杖的資料篩選。 終端使用者只會看到 ISV 允許使用者看到的內容。 在此案例，使用者可選擇查看少於篩選結果的內容，但無法略過 RLS 設定並查看超出所允許的內容。

適用於用戶端篩選 (JavaScript)，ISV 可能會決定使用者會看到初始的檢視，但他們無法控制終端使用者可能會套用至檢視本身的變更。 使用者的 Javascript 用戶端程式碼可以觸發程序的後端進行篩選的資料，因為它無法被視為安全。

請參考 [RLS 對 JavaScript 篩選](embedded-row-level-security.md#using-rls-vs-javascript-filters) 以取得詳細資料。

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>如何使用 Power BI 管理服務主體的使用權限？

一旦您啟用[服務主體](embed-service-principal.md)若要使用 Power BI，應用程式的 AD 權限才會生效不再。 然後，應用程式的使用權限會透過 Power BI 系統管理入口網站管理。

服務主體會從其安全性群組繼承所有 Power BI 租用戶設定的使用權限。 若要限制權限，建立服務主體的專用的安全性群組，並將它加入**特定安全性群組除外**相關，已啟用的 Power BI 設定的清單。

以「管理員」  身分將服務主體新增至新的新工作區時，此情況很重要。 您可以透過 [API](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) 或使用 Power BI 服務管理這項工作。

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>何時使用應用程式識別碼與服務主體物件識別碼？

**[應用程式識別碼](embed-sample-for-customers.md#application-id)** 用來在傳遞應用程式識別碼進行驗證時建立存取權杖。

若要參考作業的服務主體或進行變更，請使用 **[服務主體物件識別碼](embed-service-principal.md#how-to-get-the-service-principal-object-id)** — 例如，以管理員身分將服務主體套用至工作區。

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>可以使用服務主體管理內部部署資料閘道嗎？

您無法如同使用主帳戶一般，使用[服務主體](embed-service-principal.md)來管理內部部署資料閘道 (資料閘道)。

有了主帳戶，您可以安裝資料閘道、將使用者新增至閘道、連接到資料來源，以及執行其他系統管理工作。

有了服務主體，您可以使用 SQL Server Analysis Services (SSAS) 內部部署即時連線資料來源，設定[資料列層級安全性 (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview)。 如此一來，在與 **Power BI Embedded** 整合時，您可以使用服務主體來管理使用者，以及其對 SSAS 中資源的存取。

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>可以使用服務主體登入 Power BI 服務嗎？

否 - 您無法使用服務主體登入 Power BI 入口網站。

此外，您也無法以外部應用程式 (SaaS 內嵌) 中的使用者身分使用內容，只在您產生內嵌權杖時才可以。

### <a name="what-are-the-best-practices-to-improve-performance"></a>提升效能的最佳做法為何？

[Power BI Embedded 效能](embedded-performance-best-practices.md)

## <a name="licensing"></a>授權

### <a name="how-do-i-purchase-power-bi-embedded"></a>如何購買 Power BI Embedded？

Power BI Embedded 透過 Azure 提供。

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>如果我已購買 Power BI Premium，而現在我想有些 Power BI Embedded 中的 Azure 權益，會發生什麼事？

客戶繼續支付任何現有的 Power BI Premium 購買項目，直到目前合約期限結束為止，然後，此時，可能會其 Power BI Premium 購買項目為必要。

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>我仍必須購買 Power BI Premium 才能存取 Power BI Embedded 嗎？

否，Power BI Embedded 即包含您將解決方案部署及散發到客戶時的必要容量 (以 Azure 為基礎)。

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Power BI Embedded 有什麼購買承諾？

客戶可以小時為單位變更使用量。 Power BI Embedded 服務沒有每月或年度承諾用量。

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Power BI Embedded 的使用量會如何在帳單上顯示？

Power BI Embedded 會依據部署的節點類型，以可預測的每小時費率開立帳單。 只要您的資源正在使用中，即使未使用，就會向您收費。 您要暫停您的資源，若要停止計費。

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>誰會需要 Power BI Pro 授權以使用 Power BI Embedded？為什麼？

您需要 Power BI Pro 授權，或[服務主體](embed-service-principal.md)使用 REST Api。 若要將報表加入至 Power BI 工作區中，分析師必須在 Power BI Pro 授權或服務主體。 若要管理 Power BI 租用戶及容量，系統管理員則需要有 Power BI Pro 授權。

Power BI Embedded 可讓 Power BI 入口網站中的使用來管理及驗證內嵌的內容，因為 Power BI Pro 授權才可驗證的正確的存放庫中取得報表的存取權的 PowerBI.com 內的應用程式。

不過，若要在您的應用程式內[建立/編輯內嵌報表](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View)，使用者不需要 Pro 授權，因為該使用者根本不需要是 Power BI 使用者。

### <a name="can-i-get-started-for-free"></a>可以免費開始使用嗎？

是，您可以在 Power BI Embedded 使用 [Azure 點數](https://azure.microsoft.com/free/)。

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>可以取得 Azure 中的 Power BI Embedded 試用體驗嗎？

由於 Power BI Embedded 是 Azure 的一部份，就可以使用的服務[註冊 azure 時收到 $200 元信用額度](https://azure.microsoft.com/free/)。

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>國家/地區雲端 (美國政府、德國、中國) 是否提供 Power BI Embedded？

Power BI Embedded 也是可供[國家/地區雲端](embed-sample-for-customers-national-clouds.md)。

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded 是否可用於非營利及教育用途？

沒有任何特殊的 Azure 非營利及教育機構的價格。

## <a name="power-bi-workspace-collection"></a>Power BI 工作區集合

### <a name="what-is-power-bi-workspace-collection"></a>什麼是 Power BI 工作區集合？

**Power BI 工作區集合**(**Power BI Embedded**第 1 版) 為基礎的解決方案**Power BI 工作區集合**Azure 資源。 此解決方案可讓您透過使用「Power BI 工作區集合」  解決方案底下的 Power BI 內容、專用 API 與工作區集合金鑰來向 Power BI 驗證應用程式，為客戶建立 **Power BI Embedded** 應用程式。

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>我是否可以從「Power BI 工作區集合」移轉至 Power BI Embedded？

1. 您可以使用移轉工具，將「Power BI 工作區集合」  內容複製到 Power BI - https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration。

2. 從使用 Power BI 內容的 **Power BI Embedded** 應用程式 POC 開始著手。

3. 做好進入生產環境的準備之後，購買 **Power BI Embedded** 專用容量，然後將您的 Power BI 內容 (工作區) 指派給該容量。

    > [!Note]
    > 您可以在以 **Power BI Embedded** 解決方案平行進行建置的同時，繼續使用「Power BI 工作區集合」  。 準備就緒之後，您便可以將客戶移至新的 **Power BI Embedded** 解決方案，然後淘汰「Power BI 工作區集合」  解決方案。

如需詳細資訊，請參考[如何將 Power BI 工作區集合內容移轉至 Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded)

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>是取代路徑上的 Power BI 工作區集合？

可以，但已使用的客戶**Power BI 工作區集合**解決方案可以繼續使用它，直到已被取代。 客戶也可以建立新的工作區集合，以及任何仍然使用「Power BI 工作區集合」  解決方案的 **Power BI Embedded** 應用程式。

不過，這也表示任何不加入新功能**Power BI 工作區集合**解決方案。 我們鼓勵客戶規劃移轉到新**Power BI Embedded**解決方案。

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>何時會中止「Power BI 工作區集合」支援？

已經在使用「Power BI 工作區集合」  解決方案的客戶可以繼續使用它，直到 2018 年 6 月底，或直到其支援合約終止為止。

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>哪些區域中建立 PBI 工作區集合？

可用的區域包括：澳大利亞東南部、巴西南部、加拿大中部、美國東部 2、日本東部、美國中北部、北歐、美國中南部、東南亞、英國南部、西歐、印度西部及美國西部。

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>為何我應該從「Power BI 工作區集合」移轉至 Power BI Embedded？

有新**Power BI Embedded**解決方案的功能和功能，您無法透過執行**Power BI 工作區集合**。

一些功能包括：
* 支援所有 PBI 的資料來源。 只有兩個**Power BI 工作區集合**支援資料來源。 
* 問與答、重新整理、書籤、內嵌儀表板與圖格以及自訂功能表等新功能只有在 **Power BI Embedded** 解決方案中才有支援。
* 容量計費模型。

## <a name="embedding-setup-tool"></a>內嵌安裝工具

### <a name="what-is-the-embedding-setup-tool"></a>什麼是內嵌安裝工具？

[內嵌安裝工具](https://aka.ms/embedsetup)可讓您快速開始使用及下載應用程式範例，以開始使用 Power BI 進行內嵌。

### <a name="which-solution-should-i-choose"></a>我可以選擇什麼解決方案？

* [對客戶進行內嵌](embedding.md#embedding-for-your-customers)，可讓您將儀表板和報告內嵌至沒有 Power BI 帳戶的使用者。 執行[對客戶進行內嵌](https://aka.ms/embedsetup/AppOwnsData)解決方案。
* [對組織進行內嵌](embedding.md#embedding-for-your-organization)可讓您擴充 Power BI 服務。 執行[對組織進行內嵌](https://aka.ms/embedsetup/UserOwnsData)解決方案。

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>我已經下載了應用程式範例，要選擇哪個解決方案？

若您使用**為客戶進行內嵌**體驗，請儲存並解壓縮 *PowerBI-Developer-Samples.zip* 檔案。 接著開啟 *PowerBI-Developer-Samples-master\App Owns Data*資料夾，然後執行 *PowerBIEmbedded_AppOwnsData.sln* 檔案。

若您使用**為組織進行內嵌**體驗，請儲存並解壓縮 *PowerBI-Developer-Samples.zip* 檔案。 接著開啟 *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* 資料夾，然後執行 *pbi-saas-embed-report.sln* 檔案。

### <a name="how-can-i-edit-my-registered-application"></a>如何編輯已註冊的應用程式？

若要了解如何編輯 Azure AD 註冊的應用程式，請參閱[快速入門：更新 Azure Active Directory 中註冊應用程式](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app)。

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>如何編輯我的 Power BI 使用者設定檔或資料？

您可以在[此處](https://docs.microsoft.com/power-bi/service-basic-concepts)了解如何編輯您的 Power BI 資料。

如需詳細資訊，請參閱[為您的內嵌應用程式進行疑難排解](embedded-troubleshoot.md)。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
