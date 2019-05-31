---
title: 運用內嵌式分析為客戶將 Power BI 內容內嵌至應用程式
description: 了解如何使用內嵌式分析的 Power BI API，為客戶將報表、儀表板或磚整合或內嵌至應用程式。 了解如何使用內嵌式分析軟體、內嵌式分析工具，或內嵌式商業智慧工具，將 Power BI 整合到應用程式中。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: nishalit
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 04/02/2019
ms.openlocfilehash: e945e19505d7342cf3ba2236b4811e87a69730ab
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710964"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-customers"></a>教學課程：將客戶的 Power BI 內容內嵌至應用程式

使用 **Azure 中的 Power BI Embedded**，可利用應用程式擁有的資料，將報表、儀表板或磚內嵌至應用程式。 **應用程式擁有的資料**即是應用程式使用 Power BI 作為其內嵌的分析平台。 身為 **ISV 開發人員**，您可以建立會顯示應用程式 (完全整合且互動) 中報表、儀表板或磚的 Power BI 內容，而使用者完全不需要有 Power BI 授權。 本教學課程示範如何使用 **Azure 中的 Power BI Embedded**，利用 Power BI .NET SDK 搭配 Power BI JavaScript API，為客戶將報表整合至應用程式。

![Power BI 內嵌報表](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

在本教學課程中，您會了解如何：
> [!div class="checklist"]
> * 在 Azure 中註冊應用程式。
> * 將 Power BI 報表內嵌到應用程式中。

## <a name="prerequisites"></a>先決條件

若要開始，您必須具備：

* [Power BI Pro 帳戶](../service-self-service-signup-for-power-bi.md) (主帳戶，即用來登入 Power BI Pro 帳戶的使用者名稱和密碼)，或[服務主體 (僅限應用程式權杖)](embed-service-principal.md)。
* [Microsoft Azure](https://azure.microsoft.com/) 訂用帳戶。
* 您必須設定自己的 [Azure Active Directory 租用戶](create-an-azure-active-directory-tenant.md)。

如果您尚未註冊 **Power BI Pro**，請先[註冊免費試用](https://powerbi.microsoft.com/pricing/)，再開始進行。

如果您沒有 Azure 訂用帳戶，請先建立[免費帳戶](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)，再開始進行。

## <a name="set-up-your-embedded-analytics-development-environment"></a>設定您的內嵌分析開發環境

在您開始將報表、儀表板或磚內嵌至您的應用程式之前，必須先確定您的環境允許使用 Power BI 內嵌。

您可以瀏覽[內嵌設定工具](https://aka.ms/embedsetup/AppOwnsData)，即可快速開始使用及下載範例應用程式，協助您逐步建立環境及內嵌報表。

不過，若您選擇手動設定環境，可以繼續進行下方步驟。

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>在 Azure Active Directory (Azure AD) 中註冊應用程式

請向 Azure Active Directory [註冊您的應用程式](register-app.md)，以允許該應用程式存取 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)。 註冊您的應用程式可讓您為應用程式建立身分識別，並指定對 Power BI REST 資源的權限。 根據您想要使用主帳戶還是[服務主體](embed-service-principal.md)，決定如何開始註冊應用程式。

根據您採取的方法，這會影響您在 Azure 中註冊的應用程式類型。

如果您繼續使用主帳戶，請繼續註冊**原生**應用程式。 因為正在使用非互動式登入，所以您會使用原生應用程式。

不過，如果您繼續使用服務主體，則需要繼續註冊**伺服器端 Web 應用程式**。 您註冊伺服器端 Web 應用程式，以建立應用程式祕密。

## <a name="set-up-your-power-bi-environment"></a>設定您的 Power BI 環境

### <a name="create-an-app-workspace"></a>建立應用程式工作區

如果您要為客戶內嵌報表、儀表板或磚，就必須將您的內容放在應用程式工作區內。 有不同類型的工作區可供您設定：[傳統工作區](../service-create-workspaces.md)或[新工作區](../service-create-the-new-workspaces.md)。 如果您是使用*主要*帳戶，則您使用哪種類型的工作區都無所謂。 不過，如果您使用 *[服務主體](embed-service-principal.md)* 登入您的應用程式，則需要使用新的工作區。 在任一案例中，*主要*帳戶或*服務主體*都必須是您應用程式隨附的應用程式工作區管理員。

### <a name="create-and-publish-your-reports"></a>建立並發佈報表

您可以使用 Power BI Desktop 建立報表和資料集，接著將這些報表發佈到應用程式工作區。 有兩種完成此工作的方式：身為使用者，您可以將報表發佈至具有主帳戶 (Power BI Pro 授權) 的傳統應用程式工作區。 如果您是使用服務主體，則可以使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/imports/postimportingroup)，將報表發佈至使用新的工作區。

下列步驟逐步解說如何將您的 PBIX 報表發佈至您的 Power BI 工作區。

1. 從 GitHub 下載範例[部落格示範](https://github.com/Microsoft/powerbi-desktop-samples)。

    ![報表範例](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. 在 **Power BI Desktop** 中開啟範例 PBIX 報表。

   ![PBI Desktop 報表](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. 發佈至**應用程式工作區**。 此程序視您是使用主帳戶 (Power Pro 授權) 還是服務主體而有所不同。 如果您是使用主帳戶，則可以透過 Power BI Desktop 發佈您的報表。  現在，如果您是使用服務主體，則必須使用 Power BI REST API。

## <a name="embed-content-using-the-sample-application"></a>使用範例應用程式來內嵌內容

此範例刻意保持簡單以供示範之用。 保護應用程式祕密或主帳戶認證是您或開發人員的責任。

請遵循下列步驟，使用範例應用程式開始內嵌您的內容。

1. 下載 [Visual Studio](https://www.visualstudio.com/) (版本 2013 或更新版本)。 務必下載最新 [NuGet 套件](https://www.nuget.org/profiles/powerbi)。

2. 從 GitHub 下載[應用程式擁有資料範例](https://github.com/Microsoft/PowerBI-Developer-Samples)來開始進行。

    ![「應用程式擁有資料」應用程式範例](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

3. 開啟範例應用程式中的 **Web.config** 檔案。 您需要填寫幾個欄位，才能執行應用程式。 您可以選擇 **MasterUser** 或 **ServicePrincipal** 作為 **AuthenticationType**。 根據您選擇的驗證方法類型，有不同的填寫欄位。

    > [!Note]
    > 此範例中的預設 **AuthenticationType** 是 MasterUser。

    <center>

    | **MasterUser** <br> (Power BI Pro 授權) | **ServicePrincipal** <br> (僅限應用程式權杖)|
    |---------------|-------------------|
    | [applicationId](#application-id) | [applicationId](#application-id) |
    | [workspaceId](#workspace-id) | [workspaceId](#workspace-id) |
    | [reportId](#report-id) | [reportId](#report-id) |
    | [pbiUsername](#power-bi-username-and-password) |  |
    | [pbiPassword](#power-bi-username-and-password) |  |
    |  | [applicationsecret](#application-secret) |
    |  | [tenant](#tenant) |

   </center>

    ![Web 組態檔](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

### <a name="application-id"></a>應用程式識別碼

這兩個 AuthenticationType (主帳戶和[服務主體](embed-service-principal.md)) 都需要此屬性。

使用從 **Azure** 取得的**應用程式識別碼**填入 **applicationId** 資訊。 應用程式會使用 **applicationId** 來向您要求權限的使用者表明其身分。

若要取得 **applicationId**，請遵循下列步驟：

1. 登入[Azure 入口網站](https://portal.azure.com)。

2. 在左側的功能窗格中，選取 [所有服務]  及 [應用程式註冊]  。

    ![應用程式註冊搜尋](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. 選取需要 **applicationId** 的應用程式。

    ![選擇應用程式](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

4. 有一個以 GUID 形式列出的「應用程式識別碼」  。 請使用此**應用程式識別碼**作為應用程式的 **applicationId**。

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

### <a name="workspace-id"></a>工作區識別碼

這兩個 AuthenticationType (主帳戶和[服務主體](embed-service-principal.md)) 都需要此屬性。

在 **workspaceId** 資訊中，填入來自 Power BI 的應用程式工作區 (群組) GUID。 您可以在登入 Power BI 服務時從 URL，或使用 Powershell 取得這項資訊。

URL <br>

![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

Powershell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test"
```

   ![來自 powershell 的 workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031-ps.png)

### <a name="report-id"></a>報表識別碼

這兩個 AuthenticationType (主帳戶和[服務主體](embed-service-principal.md)) 都需要此屬性。

在 **reportId** 資訊中，填入來自 Power BI 的報表 GUID。 您可以在登入 Power BI 服務時從 URL，或使用 Powershell 取得這項資訊。

URL<br>

![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

Powershell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test" | Get-PowerBIReport
```

![來自 powershell 的 reportId](media/embed-sample-for-customers/embed-sample-for-customers-032-ps.png)

### <a name="power-bi-username-and-password"></a>Power BI 使用者名稱及密碼

僅主帳戶和 AuthenticationType 需要這些屬性。

如果您是使用[服務主體](embed-service-principal.md)進行驗證，則不需要填寫使用者名稱或密碼屬性。

* 在 **pbiUsername** 中，填入 Power BI 主帳戶。
* 在 **pbiPassword** 中，填入 Power BI 主帳戶的密碼。

### <a name="application-secret"></a>應用程式祕密

僅[服務主體](embed-service-principal.md) AuthenticationType 需要此屬性。

在 **Azure** 之 [應用程式註冊]  區段的 [金鑰]  區段中，填入 **ApplicationSecret** 資訊。  使用[服務主體](embed-service-principal.md)時，此屬性即會運作。

若要取得 **ApplicationSecret**，請遵循下列步驟：

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 在左側瀏覽窗格中，選取 [所有服務]  ，然後選取 [應用程式註冊]  。

    ![應用程式註冊搜尋](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. 選取需要使用 **ApplicationSecret** 的應用程式。

    ![選擇應用程式](media/embed-sample-for-customers/embed-sample-for-customers-0038.png)

4. 選取 **憑證和祕密**下方**管理**。

5. 選取 **新的用戶端祕密**。

6. 在 [描述]  方塊中輸入名稱，並選取期間。 然後選取 [儲存]  來取得您應用程式的**值**。 當您在儲存金鑰值後關閉 [金鑰]  窗格時，[值] 欄位只會以隱藏方式顯示。 此時，您即無法擷取金鑰值。 如果您遺失金鑰值，就必須在 Azure 入口網站中建立一個新的。

    ![金鑰值](media/embed-sample-for-customers/embed-sample-for-customers-042.png)

### <a name="tenant"></a>租用戶

僅[服務主體](embed-service-principal.md) AuthenticationType 需要此屬性。

在 **tenant** 資訊中，填入您的 azure 租用戶識別碼。 您可以在登入 Power BI 服務時從 [Azure AD 系統管理中心](/onedrive/find-your-office-365-tenant-id)，或使用 Powershell 取得此資訊。

### <a name="run-the-application"></a>執行應用程式

1. 在 **Visual Studio** 中選取 [執行]  。

    ![執行應用程式](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

2. 接著，選取 [內嵌報表]  。 視您選擇要進行測試之內容的不同 (報表、儀表板或磚)，接著在應用程式中選取該選項。

    ![選取內容](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

3. 現在，您已可以在範例應用程式中檢視該報表。

    ![檢視應用程式](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-content-within-your-application"></a>在應用程式中內嵌內容

即使使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 可以完成內嵌您內容的步驟，本文描述的範例程式碼仍是使用 **.NET SDK** 撰寫。

在應用程式中為您的客戶內嵌項目，需要從 **Azure AD** 取得您主帳戶或[服務主體](embed-service-principal.md)的**存取權杖**。 您需要先為您的 Power BI 應用程式取得 [Azure AD 存取權杖](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data)，才可呼叫 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)。

為了使用**存取權杖**建立 Power BI 用戶端，您可以建立 Power BI 用戶端物件，以讓您與 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 互動。 你可以將 **AccessToken** 與 ***Microsoft.Rest.TokenCredentials*** 物件包裝在一起來建立 Power BI 用戶端物件。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>取得您想要內嵌的內容項目

您可以使用 Power BI 用戶端物件，擷取您想要內嵌之項目的參考。

下列程式碼範例示範如何從指定工作區中擷取第一份報表。

*取得您要內嵌的報表、儀表板或圖格的內容項目範例，位於[範例應用程式](https://github.com/Microsoft/PowerBI-Developer-Samples)的 Services\EmbedService.cs 檔案內。*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>建立內嵌權杖

產生可從 JavaScript API 使用的內嵌權杖。 內嵌權杖專屬於您內嵌的項目。 因此，每次您內嵌 Power BI 內容時，都必須為其建立一個新的內嵌權杖。 如需更多詳細資訊，包括要使用的 **accessLevel**，請參閱 [GenerateToken API](https://msdn.microsoft.com/library/mt784614.aspx)。

*為您要內嵌的報表、儀表板或圖格建立內嵌權杖的範例，位於[範例應用程式](https://github.com/Microsoft/PowerBI-Developer-Samples)的 Services\EmbedService.cs 檔案內。*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

這會針對 **EmbedConfig** 及 **TileEmbedConfig** 建立類別。 您可以在 **Models\EmbedConfig.cs** 檔案和 **Models\TileEmbedConfig.cs** 檔案中找到範例。

### <a name="load-an-item-using-javascript"></a>使用 JavaScript 載入項目

您可以使用 JavaScript 將報表載入網頁上的 div 元素中。

如需使用 JavaScript API 的完整範例，您可以使用[測試網工具](https://microsoft.github.io/PowerBI-JavaScript/demo)。 遊樂場工具是一個可測試不同類型 Power BI Embedded 範例的快速方式。 您也可以瀏覽 [PowerBI-JavaScript Wiki](https://github.com/Microsoft/powerbi-javascript/wiki) 頁面，取得 JavaScript API 的詳細資訊。

此範例使用 **EmbedConfig** 模型和 **TileEmbedConfig** 模型以及報表檢視。

*新增報表、儀表板或圖格檢視的範例，位於[範例應用程式](#embed-content-using-the-sample-application)的 Views\Home\EmbedReport.cshtml、Views\Home\EmbedDashboard.cshtml 或 Views\Home\Embedtile.cshtml 檔案內。*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>移至生產環境

現在您已完成應用程式的開發，就可以為您的應用程式工作區配置專用容量。 

> [!Important]
> 需要專用容量才可移到生產環境。

### <a name="create-a-dedicated-capacity"></a>建立專用容量

建立專用容量，您的客戶即可用到專用資源。 您可以在 [Microsoft Azure 入口網站](https://portal.azure.com)內購買專用容量。 如需如何建立 Power BI Embedded 容量的詳細資料，請參閱 [Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md) (在 Azure 入口網站中建立 Power BI Embedded 容量)。

使用下表來判斷最符合您需求的 Power BI Embedded 容量。

| 節點容量 | 核心總數<br/>(後端 + 前端)  | 後端核心 | 前端核心 | DirectQuery/即時連線限制|
| --- | --- | --- | --- | --- | --- |
| A1 |1 個虛擬核心 |0.5 個核心，3-GB 的 RAM |0.5 個核心 |每秒 0.5 |
| A2 |2 個虛擬核心 |1 個核心，5-GB 的 RAM |1 個核心 | 每秒 10 個 |
| A3 |4 個虛擬核心 |2 個核心，10-GB 的 RAM |2 個核心 | 每秒 15 個 |
| A4 |8 個虛擬核心 |4 個核心，25-GB 的 RAM |4 個核心 |每秒 30 個 |
| A5 |16 個虛擬核心 |8 個核心，50-GB 的 RAM |8 個核心 |每秒 60 個 |
| A6 |32 個虛擬核心 |16 個核心，100-GB 的 RAM |16 個核心 |每秒 120 個 |

**_在 A SKU 中，您無法使用免費的 Power BI 授權存取 Power BI 內容。_ **

使用具有 PRO 授權的內嵌權杖適用於開發測試，因此 Power BI 主帳戶或服務主體可產生的內嵌權杖數量有限。 需有專用容量，才可在生產環境中進行內嵌作業。 若有專用容量，即不會限制您可產生的內嵌權杖數量。 請移至 [Available Features](https://docs.microsoft.com/rest/api/power-bi/availablefeatures/getavailablefeatures) (可用功能) 來檢查指出目前內嵌使用情況百分比的使用情況值。 使用量以每個主帳戶為基礎。

如需詳細資訊，請參閱[內嵌的分析容量規劃白皮書](https://aka.ms/pbiewhitepaper)。

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>將應用程式工作區指派至專用容量

建立了專用容量之後，您可以將應用程式工作區指派到該專用容量。

若要使用[服務主體](embed-service-principal.md)，將專用容量指派工作區，請使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/capacities/groups_assigntocapacity)。 使用 Power BI REST API 時，請務必使用[服務主體物件識別碼](embed-service-principal.md#how-to-get-the-service-principal-object-id)。

請遵循下列步驟，使用**主帳戶**將專用容量指派給工作區，。

1. 在 **Power BI 服務**中，展開 工作區，然後選取用於內嵌內容之工作區的省略符號。 然後選取 [編輯工作區]  。

    ![編輯工作區](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. 展開 [進階]  ，接著啟用 [專用容量]  ，然後選取您所建立的專用容量」。 接著，選取 [儲存]  。

    ![指派專用容量](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. 在您選取 [儲存]  後，應該會在應用程式工作區名稱的旁邊看到一個**鑽石**。

    ![繫結至容量的應用程式工作區](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何為客戶將 Power BI 內容內嵌至應用程式。 您也可以嘗試為組織內嵌 Power BI 內容。

> [!div class="nextstepaction"]
>[為組織內嵌](embed-sample-for-your-organization.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
