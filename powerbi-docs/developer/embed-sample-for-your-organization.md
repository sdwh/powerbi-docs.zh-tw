---
title: 為組織將 Power BI 內容內嵌至應用程式
description: 了解如何使用 Power BI API，為組織將報表、儀表板或磚整合或內嵌至 Web 應用程式。
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: cfc450216202f332f518955d28cb71df6aa0b800
ms.sourcegitcommit: f2b106b5eb338a64f903e8ce6793bccb07f9440a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105261"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-organization"></a>教學課程：為組織將 Power BI 報表、儀表板或磚內嵌至應用程式
本教學課程示範如何在為組織將 **Power BI** 內嵌至應用程式時，利用 **Power BI .NET SDK** 搭配 **Power BI JavaScript API**，將報表整合至應用程式。 使用 **Power BI**，可利用**使用者擁有資料**，將報表、儀表板或磚內嵌至應用程式。 **使用者擁有資料**可讓應用程式延伸 Power BI 服務。

![檢視應用程式](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

在本教學課程中，您會了解如何：
>[!div class="checklist"]
>* 在 Azure 中註冊應用程式。
>* 將 Power BI 報表內嵌到應用程式中。

## <a name="prerequisites"></a>先決條件
若要開始使用進行，您需要 **Power BI Pro** 帳戶和 **Microsoft Azure** 訂用帳戶。

* 如果您尚未註冊 **Power BI Pro**，請先[註冊免費試用](https://powerbi.microsoft.com/en-us/pricing/)，再開始進行。
* 如果您沒有 Azure 訂用帳戶，請先建立[免費帳戶](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)，再開始進行。
* 您必須設定自己的 [Azure Active Directory 租用戶](create-an-azure-active-directory-tenant.md)。
* 您必須安裝 [Visual Studio](https://www.visualstudio.com/) (2013 版或更新版本)。

## <a name="setup-your-embedded-analytics-development-environment"></a>設定您的內嵌分析開發環境

在您開始將報表、儀表板或磚內嵌至您的應用程式之前，必須先確定已將環境設定成允許內嵌。 在安裝時，您必須執行下列作業。

您可以瀏覽[上線體驗工具](https://aka.ms/embedsetup/UserOwnsData)，快速開始使用及下載應用程式範例，協助您完成建立環境及內嵌報表的程序。

不過，若您選擇手動設定環境，可以繼續進行下方步驟。
### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>在 Azure Active Directory (Azure AD) 中註冊應用程式

請向 Azure Active Directory 註冊您的應用程式，以允許該應用程式存取 Power BI REST API。 這可讓您為應用程式建立身分識別，並指定對 Power BI REST 資源的權限。

1. 接受 [Microsoft Power BI API 條款](https://powerbi.microsoft.com/api-terms)。

2. 登入[Azure 入口網站](https://portal.azure.com)。

    ![Azure 入口網站主畫面](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

3. 在左側導覽窗格中，選擇 [所有服務]，選取 [應用程式註冊]，然後選取 [新增應用程式註冊]。

    ![應用程式註冊搜尋](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)</br>
    ![新增應用程式註冊](media/embed-sample-for-your-organization/embed-sample-for-your-organization-004.png)

4. 遵循提示並建立新的應用程式。 針對**使用者擁有資料**，您的應用程式類型必須使用 **Web 應用程式/API**。 您還必須提供 [登入 URL]，供 **Azure AD** 用來傳回權杖回應。 輸入您應用程式特定的值 (例 如 http://localhost:13526/).

    ![建立應用程式](media/embed-sample-for-your-organization/embed-sample-for-your-organization-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>在 Azure Active Directory 內將權限套用至應用程式

除了應用程式註冊頁面上所提供的權限之外，您還需要為應用程式啟用額外的權限。 您需要使用「全域系統管理員」帳戶登入，才可啟用權限。

### <a name="use-the-azure-active-directory-portal"></a>使用 Azure Active Directory 入口網站

1. 瀏覽至 Azure 入口網站內的[應用程式註冊](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade)，然後選取您要用於內嵌的應用程式。

    ![選擇應用程式](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

2. 選取 [設定]，然後在 [API 存取權] 底下，選取 [必要權限]。

    ![必要權限](media/embed-sample-for-your-organization/embed-sample-for-your-organization-008.png)

3. 選取 [Windows Azure Active Directory]，然後確定選取 [以登入使用者身分存取目錄]。 選取 [儲存]。

    ![Windows Azure AD 權限](media/embed-sample-for-your-organization/embed-sample-for-your-organization-011.png)

4. 選取 [加入] 。

    ![新增權限](media/embed-sample-for-your-organization/embed-sample-for-your-organization-012.png)

5. 選取 [選取 API]。

    ![新增 API 存取權](media/embed-sample-for-your-organization/embed-sample-for-your-organization-013.png)

6. 選取 [Power BI 服務]，然後選取 [選取]。

    ![選取 PBI 服務](media/embed-sample-for-your-organization/embed-sample-for-your-organization-014.png)

7. 選取 [委派的權限] 下方的所有權限。 您必須逐一選取它們，才能儲存選取項目。 完成時，請選取 [儲存]。

    ![選取委派的權限](media/embed-sample-for-your-organization/embed-sample-for-your-organization-015.png)

## <a name="setup-your-power-bi-environment"></a>設定您的 Power BI 環境

### <a name="create-an-app-workspace"></a>建立應用程式工作區

如果您要為客戶內嵌報表、儀表板或圖格，就必須將您的內容放在應用程式工作區內。

1. 開始建立工作區。 選取 [工作區] > [建立應用程式工作區]。 這是放置應用程式所需存取內容的位置。

    ![建立工作區](media/embed-sample-for-your-organization/embed-sample-for-your-organization-020.png)

2. 提供工作區的名稱。 如果對應的 [工作區識別碼] 無法使用，請編輯它，使其具有唯一識別碼。 這也需要成為應用程式的名稱。

    ![為工作區命名](media/embed-sample-for-your-organization/embed-sample-for-your-organization-021.png)

3. 您可以設定幾個選項。 如果您選擇 [公用]，則組織中的所有人都可以看到工作區中的內容。 相反地，[私用] 則表示只有工作區的成員才能看到其內容。

    ![公用/私人](media/embed-sample-for-your-organization/embed-sample-for-your-organization-022.png)

    建立群組之後，您無法變更公用/私人設定。

4. 您也可以選擇成員是否可以**編輯**還是具有**僅限檢視**存取權。

    ![新增成員](media/embed-sample-for-your-organization/embed-sample-for-your-organization-023.png)

5. 新增想要讓他們存取工作區之人員的電子郵件地址，然後選取 [新增]。 您無法新增群組別名，只能新增個人。

6. 決定每一個人是成員還是系統管理員。系統管理員可以編輯工作區本身，包括新增其他成員。 除非成員具有僅限檢視存取權，否則成員可以編輯工作區中的內容。 管理員和成員都可以發佈應用程式。

    現在，您已可以檢視新的工作區。 Power BI 會建立並開啟工作區。 它會出現在您所屬工作區的清單中。 因為您是系統管理員，所以您可以選擇省略符號 (…) 返回，並透過新增成員或變更其權限來進行變更。

    ![建立工作區](media/embed-sample-for-your-organization/embed-sample-for-your-organization-025.png)

### <a name="create-and-publish-your-reports"></a>建立並發佈報表

您可以使用 Power BI Desktop 建立報表和資料集，接著將這些報表發佈到應用程式工作區。 發佈報表的一般使用者必須有 Power BI Pro 授權，才能發佈至應用程式工作區。

1. 從 GitHub 下載範例[部落格示範](https://github.com/Microsoft/powerbi-desktop-samples)。

    ![報表範例](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026-1.png)

2. 在 **Power BI Desktop** 中開啟範例 PBIX 報表

   ![PBI Desktop 報表](media/embed-sample-for-your-organization/embed-sample-for-your-organization-027.png)

3. 發佈至「應用程式工作區」

   ![PBI Desktop 報表](media/embed-sample-for-your-organization/embed-sample-for-your-organization-028.png)

    現在，您可在線上 Power BI 服務中檢視該報表。

   ![PBI Desktop 報表](media/embed-sample-for-your-organization/embed-sample-for-your-organization-029.png)

## <a name="embed-your-content-using-the-sample-application"></a>使用範例應用程式來內嵌內容

請遵循下列步驟，使用範例應用程式開始內嵌您的內容。

1. 從 GitHub 下載[使用者擁有資料範例](https://github.com/Microsoft/PowerBI-Developer-Samples)以開始使用。  範例應用程式有 3 種不同類型，分別為[報表](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app)、[儀表板](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app)和[磚](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app)。  本文說明的是**報表**應用程式，步驟討論如下。

    ![使用者擁有資料應用程式範例](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026.png)

2. 開啟範例應用程式中的 Cloud.config 檔案。 您需要填入一些欄位，才能成功執行應用程式。 **ClientID** 和 **ClientSecret**。

    ![Cloud 組態檔](media/embed-sample-for-your-organization/embed-sample-for-your-organization-030.png)

    使用從 **Azure** 取得的**應用程式識別碼**填寫 **ClientID** 資訊。 應用程式會使用 **ClientID** 來向您要求權限的使用者表明其身分。

    若要取得 **ClientID**，請遵循下列步驟：

    登入[Azure 入口網站](https://portal.azure.com)。

    ![Azure 入口網站主畫面](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

    在左側導覽窗格中，選擇 [所有服務]，然後選取 [應用程式註冊]。

    ![應用程式註冊搜尋](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)

    選取需要使用 **ClientID** 的應用程式。

    ![選擇應用程式](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

    您應該會看到以 GUID 形式列出的「應用程式識別碼」。 請使用此**應用程式識別碼**作為應用程式的 **ClientID**。

    ![用戶端識別碼](media/embed-sample-for-your-organization/embed-sample-for-your-organization-007.png)

    從 **Azure** 中 [應用程式註冊] 區段的 [金鑰] 區段，填寫 **ClientSecret** 資訊。

    若要取得 **ClientSecret**，請遵循下列步驟：

    登入[Azure 入口網站](https://portal.azure.com)。

    ![Azure 入口網站主畫面](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

    在左側導覽窗格中，選擇 [所有服務]，然後選取 [應用程式註冊]。

    ![應用程式註冊搜尋](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)

    選取需要使用 **ClientSecret** 的應用程式。

    ![選擇應用程式](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

    選取 [設定] 。

    ![設定](media/embed-sample-for-your-organization/embed-sample-for-your-organization-038.png)

    選取 [金鑰]。

    ![金鑰](media/embed-sample-for-your-organization/embed-sample-for-your-organization-039.png)

    以名稱填寫 [描述]，然後選取 [持續時間]，再選取 [儲存] 以取得應用程式的 [值]。 當您在儲存**金鑰值** 後關閉 [金鑰] 刀鋒視窗，值欄位僅會顯示為 [隱藏]，且您此時無法擷取**金鑰值**。 如果您遺失**金鑰值**，就必須在 [Azure 入口網站] 中建立一個新的。

    ![金鑰](media/embed-sample-for-your-organization/embed-sample-for-your-organization-031.png)

     在 **groupId** 資訊中，填入來自 Power BI 的「應用程式工作區 GUID」。

    ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    在 **reportId** 資訊中，填入來自 Power BI 的「報表 GUID」。

    ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

3. 執行應用程式！

    首先，在 **Visual Studio** 中選取 [執行]。

    ![執行應用程式](media/embed-sample-for-your-organization/embed-sample-for-your-organization-033.png)

    然後選取 [取得報表]。

    ![選取內容](media/embed-sample-for-your-organization/embed-sample-for-your-organization-034.png)

    現在，您已可以在範例應用程式中檢視該報表。

    ![檢視應用程式](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

## <a name="embed-your-content-within-your-application"></a>在應用程式中內嵌內容
即使使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 可以完成內嵌您內容的步驟，還是可以使用 **.NET SDK** 來撰寫本文中所述的範例程式碼。

若要將報表整合至 Web 應用程式，請使用 **Power BI REST API** 或 **Power BI C# SDK**，以及 Azure Active Directory (AD) 授權**存取權杖**，以取得報表。 然後，使用同一個**存取權杖**載入報表。 **Power BI Rest API** 可讓您以程式設計方式存取特定的 **Power BI** 資源。 如需詳細資訊，請參閱 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 及 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)。

### <a name="get-an-access-token-from-azure-ad"></a>從 Azure AD 取得存取權杖
在您的應用程式中，您必須先從 Azure AD 取得**存取權杖**，才能呼叫 Power BI REST API。 如需詳細資訊，請參閱 [Authenticate users and get an Azure AD access token for your Power BI app](get-azuread-access-token.md) (驗證使用者，並為 Power BI 應用程式取得 Azure AD 存取權杖)。

### <a name="get-a-report"></a>取得報表
若要取得 **Power BI** 報表，請使用 [取得報表](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) 作業來取得 **Power BI** 報表清單。 您可以從報表的清單中取得報表識別碼。

### <a name="get-reports-using-an-access-token"></a>使用存取權杖取得報表
[取得報表](https://docs.microsoft.com/rest/api/power-bi/reports/getreports)作業會傳回報表清單。 您可以從報表清單中取得單一報表。

若要進行 REST API 呼叫，您必須使用 *Bearer {access token}* 的格式包含 *Authorization* 標頭。

#### <a name="get-reports-with-the-rest-api"></a>利用 REST API 取得報表

下列程式碼範例示範如何使用 **REST API** 擷取報表。

「[範例應用程式](#embed-your-content-using-the-sample-application)的 **_Default.aspx.cs_** 檔案內具有範例，可讓您取得要內嵌的內容項目 (報表、儀表板或磚)。」

```csharp
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-using-the-net-sdk"></a>利用 .NET SDK 取得報表
您可以使用 .NET SDK 擷取報表清單，而不必直接呼叫 REST API。 下列程式碼範例示範如何列出報表。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It is used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

### <a name="load-a-report-using-javascript"></a>使用 JavaScript 載入報表
您可以使用 JavaScript 將報表載入網頁上的 div 元素中。

下列程式碼範例示範如何從指定工作區擷取報表。

「[範例應用程式](#embed-your-content-using-the-sample-application)的 **_Default.aspx_** 檔案內具有範例，可讓您載入要內嵌的內容項目 (報表、儀表板或磚)。」

```javascript
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```javascript
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReporte, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    }
  );
}
```

## <a name="using-a-power-bi-premium-dedicated-capacity"></a>使用 Power BI Premium 專用容量

既然您已完成應用程式的開發，就可以為您的應用程式工作區配置專用容量。

### <a name="create-a-dedicated-capacity"></a>建立專用容量
建立專用容量，您應用程式工作區中的內容即可享有專用資源。 若未指派專用容量給工作區，則視為共用容量。 您可以使用 [Power BI Premium ](../service-admin-premium-purchase.md) 建立專用容量。

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>將應用程式工作區指派至專用容量

建立了專用容量之後，您可以將應用程式工作區指派到該專用容量。 若要完成此動作，請遵循下列步驟。

1. 在 **Power BI 服務**中，展開 工作區，然後選取用於內嵌內容之工作區的省略符號。 然後選取 [編輯工作區]。

    ![編輯工作區](media/embed-sample-for-your-organization/embed-sample-for-your-organization-036.png)

2. 展開 [進階]，接著啟用 [專用容量]，然後選取您所建立的專用容量」。 接著，選取 [儲存]。

    ![指派專用容量](media/embed-sample-for-your-organization/embed-sample-for-your-organization-024.png)

3. 在您選取 [儲存] 後，應該會在應用程式工作區名稱的旁邊看到一個**鑽石**。

    ![繫結至容量的應用程式工作區](media/embed-sample-for-your-organization/embed-sample-for-your-organization-037.png)

## <a name="next-steps"></a>後續步驟
在本教學課程中，您已了解如何使用 **Power BI 組織帳戶**將 Power BI 內容內嵌至應用程式。 您現在可以嘗試使用應用程式將 Power BI 內容內嵌至應用程式。  您也可以嘗試為協力廠商客戶內嵌 Power BI 內容。

> [!div class="nextstepaction"]
> [從應用程式內嵌](embed-from-apps.md)

> [!div class="nextstepaction"]
>[為協力廠商客戶內嵌](embed-sample-for-customers.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
