---
title: 關於 Power BI Embedded 的常見問題集
description: 瀏覽 Power BI Embedded 相關的常見問題與回答清單。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/17/2018
ms.openlocfilehash: cd32b644205629ce62579f5a720d486f93073dea
ms.sourcegitcommit: ccbe76a0a43c5c5e87354a33e617bf3cb291608e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394725"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>關於 Power BI Embedded 的常見問題集

* 如果您有其他問題，請[嘗試詢問 Power BI 社群](http://community.powerbi.com/)。
* 仍有問題嗎？ 瀏覽 [Power BI 支援頁面](https://powerbi.microsoft.com/support/)。

## <a name="general"></a>一般

### <a name="what-is-power-bi-embedded"></a>什麼是 Power BI Embedded？

Microsoft Power BI Embedded (PBIE) 讓應用程式開發人員不必花費時間和金錢從頭開始建置自己的資料視覺效果及控制項，就能在應用程式中內嵌出色、完全互動式的報表。

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Power BI Embedded 的目標對象是誰？

自行製作應用程式的開發人員和軟體公司，亦即獨立軟體廠商 (ISV)。

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Power BI Embedded 和 Power BI 服務有何不同？

Power BI Embedded 專門供 ISV 或開發人員使用，他們建置應用程式並想要在其中內嵌視覺效果，以協助客戶不必從頭建置分析解決方案就能做出決策。 Embedded 分析讓企業用戶能夠存取商務資料及執行查詢，以在應用程式內使用這份資料產生深入解析。

Power BI 是軟體即服務分析解決方案，為組織提供最重要商務資料的單一檢視。

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Power BI Premium 與 Power BI Embedded 之間的差異為何？

Power BI Premium 是專為企業打造的容量，其單一檢視集結了組織、夥伴、客戶及供應商，適合想要完整 BI 解決方案的企業使用。 Power BI Premium 可協助您的組織制定決策。 Power BI Premium 是 SaaS 產品，隨附的功能可讓使用者透過 Power BI 入口網站、行動裝置應用程式及內部開發的應用程式取用內容。

Power BI Embedded 適用於建置應用程式並想在其中內嵌視覺效果的 ISV 或開發人員。 因為 Power BI Embedded 適用於應用程式開發人員，不論該應用程式的客戶是組織內部或外部的任何人員，都能取用儲存在 Power BI Embedded 容量中的內容，進而協助您的客戶制定決策。 Power BI Embedded 容量內容無法透過單鍵發佈到 Web 或 SharePoint 來共用，而且不支援 SSRS 報表。

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Microsoft 對於客戶購買 Power BI Premium 與 Power BI Embedded 的時機有什麼建議？

Microsoft 的建議是，企業購買 Power BI Premium (企業級的自助雲端 BI 解決方案)，ISV 則購買 Power BI Embedded (提供雲端技術的內嵌分析元件)。 不過，客戶要購買哪個產品並不會受到限制。

在某些情況下，ISV (通常規模較大) 會想要使用 P SKU，不僅在組織內獲得預先封裝 Power BI 服務的額外優勢，也能在應用程式內嵌。 有些企業只想建置企業營運應用程式並在其中內嵌分析，而不想使用預先封裝的 Power BI 服務，也可能決定使用 Azure 中的 A SKU。

### <a name="how-many-embed-tokens-can-i-create"></a>我可以建立多少內嵌權杖？

具有 PRO 授權的內嵌權杖適用於開發測試，所以 Power BI 主要帳戶可以產生的內嵌權杖數量有限。 您必須[購買容量](#technical)才可在生產環境中進行內嵌作業。 購買容量後，您可產生的內嵌權杖數量就不受限制。 請移至 [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) (可用功能) 來檢查指出目前內嵌使用情況百分比的使用情況值。

## <a name="technical"></a>技術

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Azure 中的 A SKU 和 Office 365 中的 EM SKU 有何差異？

PowerBI.com 是企業解決方案，在軟體即服務供應項目中提供社群共同作業、電子郵件訂閱等多項功能

Power BI Embedded 是一組可供開發人員用來在平台即服務供應項目中建立內嵌分析解決方案的 API。 若是 Embedded 分析案例，PowerBI.com 可協助 ISV 和開發人員管理他們的內嵌分析解決方案內容與租用戶層級設定。

以下是各項差異的部份清單。

| 功能 | Power BI Embedded | Power BI Premium 容量 | Power BI Premium 容量 |
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
|使用案例 | 在您自己的應用程式中內嵌內容 | <li> 在您自己的應用程式中內嵌內容 <br><br></br> <li> 在 MS Office 應用程式中內嵌內容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (行動裝置應用程式除外)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> 在您自己的應用程式中內嵌內容 <br><br></br> <li> 在 MS Office 應用程式中內嵌內容： <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (行動裝置應用程式除外)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br></br> <li> 透過 [Power BI 服務](https://powerbi.microsoft.com/en-us/)與 Power BI 使用者共用內容  |
|帳務 |每小時 |每月 |每月 |
|承諾用量  |無承諾用量 |每年  |每月/每年 |
|差異 |完整彈性 - 可以在 Azure 入口網站中，或透過 API 相應增加/減少、暫停/繼續資源  |可用於在 SharePoint Online 與 Microsoft Teams 中內嵌內容 (行動裝置應用程式除外) |在相同容量中結合應用程式內嵌及使用 Power BI 服務 |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>在 Azure 中建立 PBIE 容量的必要條件為何？

* 您必須登入您組織的目錄 (不支援 MSA 帳戶)。
* 您須有 Power BI 租用戶，也就是您目錄中至少須有一位使用者已註冊 Power BI。 
* 您在組織目錄中須有 Azure 訂用帳戶。

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>如何監視 Power BI Embedded 容量耗用量？

* [使用 Power BI 管理入口網站](../service-admin-portal.md#power-bi-embedded)。

* 下載 Power BI 中的[計量應用程式](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity)。

* 使用 [Azure 診斷記錄](azure-pbie-diag-logs.md)。

### <a name="will-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>我的容量規模會自動調整成應用程式的取用量嗎？

雖然目前沒有自動調整，但所有 API 都能隨時調整。

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>為什麼建立/調整/繼續容量會讓容量進入暫止狀態？

佈建容量 (調整/繼續/建立) 可能會失敗。 佈建呼叫的呼叫端應該使用「取得詳細資料 API」來檢查容量的 ProvisioningState：[Capacities - Get Details](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails) (容量 - 取得詳細資料)。

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>是否只能在特定區域中建立 Power BI Embedded 容量？

利用[多地理位置 (預覽)](embedded-multi-geo.md) 功能，您可以在不同於 Power BI 主租用戶位置的區域中購買 [Power BI Embedded 容量](azure-pbie-create-capacity.md)

### <a name="how-can-i-find-what-is-my-pbi-tenant-region"></a>如何尋找我的 PBI 租用戶區域？

您可以使用 PBI 入口網站了解您的 PBI 租用戶區域。

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > 關於 Power BI

![關於 Power BI](media/embedded-faq/about-01.png)
![租用戶區域](media/embedded-faq/tenant-location-01.png)

### <a name="what-is-supported-with-the-cloud-solution-provider-csp-channel"></a>雲端解決方案提供者 (CSP) 通道的支援項目？

* 您可以針對具有訂用帳戶類型 CSP 的租用戶建立 PBIE
* 夥伴帳戶可以登入客戶的租用戶，並為客戶租用戶購買 PBIE，以及指定客戶租用戶使用者為 Power BI 的容量管理員

### <a name="why-do-i-get-an-unsupported-account-message"></a>為什麼會收到不受支援帳戶的訊息？

Power BI 需要您使用組織帳戶註冊。 不支援使用 MSA (Microsoft 帳戶) 嘗試註冊 Power BI。

### <a name="can-i-use-apis-to-create--manage-azure-capacities"></a>我可以使用 API 來建立和管理 Azure 容量嗎？

是，您可以使用 Powershell Cmdlet 和 Azure Resource Manager API 來建立及管理 PBIE 資源。

* Rest API - https://docs.microsoft.com/rest/api/power-bi-embedded/
* Powershell Cmdlet - https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>PBI Embedded 解決方案中的 PBI Embedded 專用容量角色是什麼？

若要[將您的解決方案升階到生產環境](https://docs.microsoft.com/power-bi/developer/embedding-content#step-3-promote-your-solution-to-production)，您需要 Power BI 內容 (您在應用程式中使用且要指派給 Power BI Embedded (A SKU) 容量的應用程式工作區)。

### <a name="what-are-the-azure-regions-pbi-embedded-is-available"></a>PBI Embedded 可用的 Azure 區域是什麼？

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

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>Power BI Embedded 的驗證模型是什麼？

Power BI Embedded 會繼續使用 Azure AD 進行主使用者 (指定的 Power BI Pro 授權使用者) 驗證，並在 Power BI 中驗證應用程式。

應用程式使用者的驗證和授權會由 ISV 實作，ISV 可以為其應用程式實作自己的驗證。

如果您已經有 Azure AD 租用戶，可以使用現有目錄，也可以建立新的 Azure AD 租用戶，以達成內嵌應用程式內容的安全性。

若要取得 AAD 權杖，可以使用其中一個 Azure Active Directory 驗證程式庫 - https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries。 有適用於多種平台的用戶端程式庫。

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-an-user-owns-data-scenario"></a>我的應用程式已使用 AAD 來驗證使用者。 在「使用者擁有資料」的情況下，要如何在對 Power BI 驗證時使用此身分識別？

它是標準 OAuth 代理流程 (https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#web-application-to-web-api) 應用程式需要設定成要求 Power BI 服務的權限 (具有所需範圍)，而且在您擁有應用程式的使用者權杖之後，只需要使用使用者存取權杖來呼叫 ADAL API AcquireTokenAsync，並將 Power BI 資源 URL 指定為資源識別碼，請參閱以下顯示如何執行此作業的的程式碼片段：

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Power BI Embedded 和 Azure 服務有何不同？

ISV/開發人員必須先有 Power BI 帳戶，才能在 Azure 中購買 Power BI Embedded。 您的 Power BI Embedded 部署區域依您的 Power BI 帳戶而定。 在 Azure 中管理您的 Power BI Embedded 資源，能夠：

* 相應增加/減少
* 新增容量管理員
* 暫停/繼續服務

使用 PowerBI.com 對 Power BI Embedded 容量指派/解除指派工作區。

### <a name="what-deploy-regions-are-supported"></a>有哪些支援的部署區域？

澳洲東南部、巴西南部、加拿大中部、美國東部 2、印度西部、日本東部、美國中北部、北歐、美國中南部、東南亞、英國南部、西歐、美國西部及美國西部 2。

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>哪種內容套件資料可以內嵌？

從內容套件資料集建置的**儀表板**和**磚**「無法」內嵌，但是從內容套件資料集建置的**報表**「可以」內嵌。

### <a name="what-is-the-difference-between-using-rls-vs-javascript-filters"></a>使用 RLS 和 JavaScript篩選的差別在哪裡？

因為一種方法是關於控制特定使用者可看到的內容，而另一種則是關於將使用者的檢視最佳化，所以使用 RLS 和 JavaScript 篩選的時機常令人感到混淆。

對於 RLS，ISV 開發人員可控制屬於建立模型和產生內嵌權杖的資料篩選。 終端使用者只會看到 ISV 允許使用者看到的內容。 在此案例，使用者可選擇查看少於篩選結果的內容，但無法略過 RLS 設定並查看超出所允許的內容。

對於用戶端篩選 (JavaScript)，ISV 可能可決定終端使用者在初始檢視中看到的內容，但無法控制終端使用者可能會套用至檢視本身的變更。 即使資料篩選可以在後端發生，但因為其是由 JavaScript 用戶程式碼觸發，因此終端使用者可以將其變更，且並不安全。

請參考 [RLS 對 JavaScript 篩選](embedded-row-level-security.md#using-rls-vs-javascript-filters) 以取得詳細資料。

### <a name="what-are-the-best-practices-to-improve-performance"></a>提升效能的最佳做法為何？

[Power BI Embedded 效能](embedded-performance-best-practices.md)

## <a name="licensing"></a>授權

### <a name="how-do-i-purchase-power-bi-embedded"></a>如何購買 Power BI Embedded？

Power BI Embedded 透過 Azure 提供。

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>如果我已經購買 Power BI Premium，而現在想要 Azure 中 Power BI Embedded 的某些優勢，會發生什麼情況？

客戶會繼續為任何現有的 Power BI Premium 購買項目付費，直到目前合約期限結束為止；接著，如有必要，可在該時間點切換 Power BI Premium 購買項目。

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>我仍必須購買 Power BI Premium 才能存取 Power BI Embedded 嗎？

否，Power BI Embedded 即包含您將解決方案部署及散發到客戶時的必要容量 (以 Azure 為基礎)。

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Power BI Embedded 有什麼購買承諾？

客戶可以小時為單位變更使用量。 Power BI Embedded 服務沒有每月或年度承諾用量。

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Power BI Embedded 的使用量會如何在帳單上顯示？

Power BI Embedded 會依據部署的節點類型，以可預測的每小時費率開立帳單。 只要資源在使用中的狀態，即使您未使用，也會向您計費。 若要停止計費，您須主動暫停資源。

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>誰會需要 Power BI Pro 授權以使用 Power BI Embedded？為什麼？

任何需要將報表新增至 Power BI 工作區的分析師都必須有 Power BI 授權。 任何需要使用 REST API 的開發人員都需要有 Power BI Pro 授權。 任何需要管理 Power BI 租用戶和容量的租用戶系統管理員都必須有 Power BI Pro 授權。

由於 Power BI Embedded 允許使用 Power BI 入口網站來管理及驗證內嵌內容，因此必須有 Power BI Pro 授權才能在 PowerBI.com 中驗證應用程式，以取得正確存放庫中的報表存取。

不過，若要在自己的應用程式內 [creating/editing embedded reports](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) (建立/編輯內嵌報表)，終端使用者不需要 Pro 授權，因為該使用者根本不需要是 Power BI 使用者。

### <a name="can-i-get-started-for-free"></a>可以免費開始使用嗎？

是，您可以在 Power BI Embedded 使用 [Azure 點數](https://azure.microsoft.com/free/)。

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>可以取得 Azure 中的 Power BI Embedded 試用體驗嗎？

因為 Power BI Embedded 是 Azure 的一部份，所以您可以使用[註冊 Azure 時收到的美金 $200 元點數](https://azure.microsoft.com/free/)來使用服務。

### <a name="is-power-bi-embedded-available-for-sovereign-clouds-us-government-germany-china"></a>Power BI Embedded 是否可供主權雲端使用 (美國政府、德國、中國)？

Power BI Embedded 可供某些[主權雲端](embed-sample-for-customers-sovereign-clouds.md)使用。 中國雲端仍然**無法**使用。

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Power BI Embedded 是否可用於非營利及教育用途？

非營利及教育機構可以購買 Azure。 在 Azure 中，並無適用這幾種客戶的特殊定價。

## <a name="power-bi-workspace-collection"></a>Power BI 工作區集合

### <a name="what-is-power-bi-workspace-collection"></a>什麼是 Power BI 工作區集合？

**Power BI 工作區集合** (**Power BI Embedded** 第 1 版) 是一個以 **Power BI 工作區集合** Azure 資源為基礎的解決方案。 此解決方案可讓您透過使用「Power BI 工作區集合」解決方案底下的 Power BI 內容、專用 API 與工作區集合金鑰來向 Power BI 驗證應用程式，為客戶建立 **Power BI Embedded** 應用程式。

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>我是否可以從「Power BI 工作區集合」移轉至 Power BI Embedded？

1. 您可以使用移轉工具，將「Power BI 工作區集合」內容複製到 Power BI - https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration。

2. 從使用 Power BI 內容的 **Power BI Embedded** 應用程式 POC 開始著手。

3. 做好進入生產環境的準備之後，購買 **Power BI Embedded** 專用容量，然後將您的 Power BI 內容 (工作區) 指派給該容量。

    > [!Note]
    > 您可以在以 **Power BI Embedded** 解決方案平行進行建置的同時，繼續使用「Power BI 工作區集合」。 準備就緒之後，您便可以將客戶移至新的 **Power BI Embedded** 解決方案，然後淘汰「Power BI 工作區集合」解決方案。

如需詳細資訊，請參考[如何將 Power BI 工作區集合內容移轉至 Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded)

### <a name="is-power-bi-workspace-collection-on-a-path-to-be-deprecated"></a>「Power BI 工作區集合」是否即將被取代？

是，但已經在使用「Power BI 工作區集合」解決方案的客戶可以繼續使用它，直到它被取代為止。 客戶也可以建立新的工作區集合，以及任何仍然使用「Power BI 工作區集合」解決方案的 **Power BI Embedded** 應用程式。

不過，這也意謂著新功能不會新增到任何「Power BI 工作區集合」解決方案，而我們鼓勵客戶進行移轉至新 **Power BI Embedded** 解決方案的規劃。

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>何時會中止「Power BI 工作區集合」支援？

已經在使用「Power BI 工作區集合」解決方案的客戶可以繼續使用它，直到 2018 年 6 月底，或直到其支援合約終止為止。

### <a name="in-what-regions-can-pbi-workspace-collection-be-created"></a>可以在哪些區域建立「Power BI 工作區集合」？

可用的區域包括：澳大利亞東南部、巴西南部、加拿大中部、美國東部 2、日本東部、美國中北部、北歐、美國中南部、東南亞、英國南部、西歐、印度西部及美國西部。

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>為何我應該從「Power BI 工作區集合」移轉至 Power BI Embedded？

**Power BI Embedded** 解決方案引進了「Power BI 工作區集合」所沒有的新功能和處理能力。

一些功能包括：

* 與使用 **Power BI 工作區集合**只支援兩種資料來源相比，可支援所有 PBI 資料來源。 
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

您可以在[此處](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application)了解如何編輯已註冊 AAD 的應用程式。

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>如何編輯我的 Power BI 使用者設定檔或資料？

您可以在[此處](https://docs.microsoft.com/power-bi/service-basic-concepts)了解如何編輯您的 Power BI 資料。

如需詳細資訊，請參閱[為您的內嵌應用程式進行疑難排解](embedded-troubleshoot.md)。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)