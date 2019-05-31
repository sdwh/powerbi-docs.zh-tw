---
title: 搭配 Power BI 使用內嵌式分析
description: Power BI 提供 API 讓您在應用程式中針對儀表板和報表使用內嵌式分析。 深入了解在 PaaS 和 SaaS 環境中使用內嵌式分析軟體、內嵌式分析工具，或內嵌式商業智慧工具搭配 Power BI 執行內嵌作業的相關資訊。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051074"
---
# <a name="embedded-analytics-with-power-bi"></a>搭配 Power BI 使用內嵌式分析

Power BI 服務 (SaaS) 和 Azure 中的 Power BI Embedded 服務 (PaaS) 都有 API 可供內嵌您的儀表板和報表。 當內嵌內容，這可讓您存取最新的 Power BI 功能，例如儀表板、 閘道和應用程式工作區。

您可以完成[內嵌安裝工具](https://aka.ms/embedsetup)以快速開始使用並下載應用程式範例。

選擇最適合您的方案：

* [對組織進行內嵌](embedding.md#embedding-for-your-organization)可讓您擴充 Power BI 服務。 若要這樣做，請實作[內嵌為您的組織](https://aka.ms/embedsetup/UserOwnsData)解決方案。
* [對客戶進行內嵌](embedding.md#embedding-for-your-customers)可讓您內嵌儀表板和報表還沒有 Power BI 帳戶的使用者。 若要這樣做，請實作[內嵌為您的客戶](https://aka.ms/embedsetup/AppOwnsData)解決方案。

![PBIE 範例](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>使用 Api

有兩個內嵌 Power BI 內容的主要案例：
- 內嵌的貴組織的使用者 （Power BI 授權）。 
 
- 對您的使用者並不需要 Power BI 授權的客戶進行內嵌。 

[Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)可讓這兩個案例。

針對沒有 Power BI 授權的客戶和使用者，將儀表板和報告內嵌至您的自訂應用程式，並使用相同的 API 來服務組織或客戶。 您的客戶會看到應用程式管理的資料。 此外，貴組織的 Power BI 使用者有其他選項，以檢視*其資料*直接在 Power BI 或內嵌的應用程式內容中。 您可以針對內嵌需求而完整利用 JavaScript 和 REST API。

若要了解內嵌運作方式，請參閱[JavaScript 內嵌範例](https://microsoft.github.io/PowerBI-JavaScript/demo/)。

## <a name="embedding-for-your-organization"></a>對組織進行內嵌

**對組織進行內嵌**可讓您擴充 Power BI 服務。 此內嵌需要應用程式的使用者登入 Power BI 服務，以檢視內容。 貴組織中有人登入之後，他們只能在 Power BI 服務中存取他們自己的和某人已經與他們共用的儀表板和報表。

包含內部應用程式，例如組織內嵌範例[SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/)， [（您必須具有系統管理員權限） 的 Microsoft Teams 整合](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/)，和[Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

若要將內嵌為您的組織，請參閱[教學課程：將 Power BI 內容內嵌至應用程式為您的組織](embed-sample-for-your-organization.md)。

針對 Power BI 使用者內嵌時，可透過 [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) 來使用自助功能，例如編輯、儲存等。

您可以瀏覽[嵌入安裝工具](https://aka.ms/embedsetup/UserOwnsData)至快速入門與下載的範例應用程式會引導您完成整合您的組織的報表。

## <a name="embedding-for-your-customers"></a>對客戶進行內嵌

**對客戶進行內嵌**可讓您內嵌儀表板和報表還沒有 Power BI 帳戶的使用者。 此內嵌是所謂*Power BI Embedded*。

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md)已**Microsoft Azure**服務，可讓獨立軟體廠商 (Isv) 和開發人員快速地將視覺效果、 報表和儀表板內嵌至應用程式。 此內嵌是透過容量為基礎、 每小時計量付費的模型。

![對客戶進行內嵌的內嵌流程](media/embedding/powerbi-embed-flow.png)

Power BI Embedded 可為 ISV、其開發人員及客戶帶來好處。 例如，ISV 可以免費使用 Power BI Desktop 開始建立視覺效果。 藉由減少視覺分析開發工作，Isv 縮短上市時間，並透過差異化的資料體驗的競爭對手之間脫穎而出。 Isv 也可以選擇收取 premium 他們建立內嵌分析的額外價值。

使用 Power BI Embedded，您的客戶完全不需要了解 Power BI。 您可以使用兩個不同的方法來建立內嵌的應用程式：
- Power BI Pro 帳戶 
- 服務主體 

Power BI Pro 帳戶將成為您的應用程式的主帳戶 （將其想像為 proxy 帳戶）。 此帳戶可讓您產生內嵌權杖，以提供您的應用程式的 Power BI 儀表板和報表的存取權。

[服務主體](embed-service-principal.md)可以使用「僅限應用程式」  權杖，將 Power BI 內容內嵌至應用程式。 它也可讓您產生內嵌權杖，以提供您的應用程式的 Power BI 儀表板和報表的存取權。

使用 Power BI Embedded 的開發人員可以花時間專注於建置其應用程式的核心功能，而非消費時間在開發視覺效果和分析。 它們可以快速符合客戶報表和儀表板需求，並使用完整記載的 Api 和 Sdk 輕鬆內嵌。 透過在應用程式中啟用輕鬆巡覽資料探勘，ISV 可讓客戶在來自任何裝置的內容中進行資料驅動的快速決策。

> [!IMPORTANT]
> 雖然內嵌需要 Power BI 服務，您的客戶不需要有 Power BI 帳戶，才能檢視您的應用程式內嵌的內容。 

當您準備好進入生產環境時，必須將應用程式工作區指派給專用容量。 Microsoft Azure 中的 Power BI Embedded 提供與您應用程式搭配使用的[專用容量](azure-pbie-create-capacity.md)。

內嵌的詳細資料，請參閱[如何內嵌 Power BI 內容](embed-sample-for-customers.md)。

## <a name="next-steps"></a>後續步驟

現在，您可以嘗試將 Power BI 內容內嵌至應用程式，或嘗試對您的客戶內嵌 Power BI 內容。

> [!div class="nextstepaction"]
> [為組織內嵌](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [什麼是 Power BI Embedded？](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[對客戶進行內嵌](embed-sample-for-customers.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
