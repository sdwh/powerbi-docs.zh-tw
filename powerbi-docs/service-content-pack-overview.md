---
title: Power BI 服務內容套件計劃概觀
description: 內容套件認證計劃
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2018
ms.author: maggies
ms.openlocfilehash: c5c69bab7fb0a47e5e546dfe1b3143a13428d4bc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54285220"
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>Power BI 服務內容套件計劃概觀
內容套件是一組全新內容，可讓使用者立即從來源取得深入剖析資訊。 內容套件通常著重於可提供角色、網域或工作流程深入剖析資訊的特定商務案例。

ISV 可建置範本內容套件，讓客戶透過自己的帳戶連線並實例化。 身為網域專家，其可解除鎖定資料，讓商務使用者都能輕鬆使用。 內容套件可為您的客戶提供臨機操作監視和分析，而不需要大量投資報表基礎結構。

這些 ISV 建置的範本內容套件可以提交給 Power BI 小組，在 Power BI 內容套件庫 (app.powerbi.com/getdata/services) 和 Microsoft AppSource (appsource.microsoft.com) 中提供公眾使用。 如需公用內容套件體驗的範例，請參閱[這裡](template-content-pack-experience.md)。

## <a name="overview"></a>概觀
開發和提交範本內容套件的一般程序牽涉到多個步驟。

 ![程序](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [檢閱需求](#requirements)並確定您達到需求
2. 在 Power BI Desktop 中[建置內容](template-content-pack-authoring.md#queries)
3. 在 PowerBI.com 中[建立儀表板](template-content-pack-authoring.md#dashboard)
4. 在您的組織內自行[測試內容套件](template-content-pack-testing.md)
5. 將內容[送出](template-content-pack-testing.md#submission)至 Power BI 以供發行

<a name="requirements"></a>

## <a name="requirements"></a>需求
若要建置並提交要在 PowerBI 服務和 AppSource 中發行的內容套件，您必須符合下列需求︰

* 您有商務使用者所使用的 SaaS 應用程式。
* 您的 SaaS 應用程式具有可在 Power BI 中視覺化的使用者資料。
* 您的 SaaS 應用程式具有可透過公用網際網路存取的 API。 理想情況下，此 API 是 REST 型 API 或 OData 摘要。 Power BI 內容套件支援多種驗證類型，例如基本驗證、OAuth 2.0 和 API 金鑰。 
* 已核准您的 SaaS 應用程式發佈內容套件。 請提交要求給 pbiservicesapps@microsoft.com。 我們將會檢閱每份提交的相關性與預期使用量。 
* 簽署的夥伴協議。 您會在[提交步驟](template-content-pack-testing.md#submission)執行此作業。

如需技術需求的詳細資料，請檢閱[撰寫](template-content-pack-authoring.md)一節。

## <a name="business-scenario"></a>商務案例
內容套件可提供著重於特定商務案例的深入剖析資訊和指標。 了解您的對象及其受益於內容套件的內容，有助於確保使用者可透過您提供的內容邁向成功。

### <a name="tips"></a>祕訣
* 識別您的對象及其嘗試完成的工作  
* 專注於特定時間週期 (過去 90 天) 或最後 N 個結果  
* 僅匯入與案例相關的資料表/資料行  
* 考慮針對個別特殊情況提供多個內容套件  

## <a name="frequently-asked-questions"></a>常見問題集
**我可以作為協力廠商為非我所有的 SaaS 應用程式建置 Power BI 服務內容套件嗎？**

我們需要先和 SaaS 應用程式的擁有者簽署夥伴協議，才能在服務中發行內容套件。 作為第三方，您需要協助和 SaaS 應用程式擁有者簽署夥伴協議。

**我的服務沒有公用的開發人員 API。仍然可以建置 Power BI 服務內容套件，直接從資料存放區提取資料嗎？**

否，Power BI 服務內容套件需要可透過公用網際網路存取的開發人員 API。

**服務內容套件支援何種 API？它們可搭配使用何種驗證類型？**

Power BI 服務內容套件支援任何 REST API 或 OData 摘要。 Power BI 可以使用多種驗證類型，包括基本驗證、OAuth2.0 和 Web API 金鑰。 如需技術需求的詳細資料，請參閱[撰寫](template-content-pack-authoring.md#dashboard)一文。

**我在 Power BI 中已發行內容套件。如何更新它？**

已發行的內容套件一個月可更新一次。 請在當月最後一天以前將更新要求提交給 [pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com)，該更新將會在下個月的第一週發行。

**我有很多關於服務內容套件的問題。如何連絡您？**

歡迎您使用電子郵件提出問題：[pbiservicesapps@microsoft.com](mailto:pbiservicesapps@microsoft.com)

## <a name="support"></a>支援
如需在開發期間的支援，請使用 [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support)。 讓適當的小組可快速開始處理客戶事件。

## <a name="next-step"></a>下一個步驟
[撰寫](template-content-pack-authoring.md)