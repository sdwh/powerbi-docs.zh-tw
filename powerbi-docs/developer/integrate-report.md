---
title: 將 Power BI 報表整合至組織的應用程式
description: 了解如何使用 Power BI API，將報表整合或內嵌至 Web 應用程式。
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 530dcffa998a80b88b1cb15ae1d22a14eba6c620
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36944414"
---
# <a name="integrate-a-report-into-an-app-for-your-organization"></a>將報表整合至組織的應用程式
了解如何在對組織進行內嵌時，使用 REST API 呼叫配合 Power BI JavaScript API 將報表整合或內嵌至 Web 應用程式。

![內嵌報表的範例](media/integrate-report/powerbi-embedded-report.png)

若要遵循此逐步解說進行整合，您需要一個 **Power BI** 帳戶。 如果您沒有帳戶，則可以[註冊免費 Power BI Pro 試用](../service-self-service-signup-for-power-bi.md)，或建立您自己的 [Azure Active Directory 租用戶](create-an-azure-active-directory-tenant.md)用於測試用途。

> [!NOTE]
> 想要改用 embedtoken 內嵌客戶的報表嗎？ 請參閱[將客戶的儀表板、磚或報表整合至應用程式](embed-sample-for-customers.md)。
> 
> 

若要將報表整合至 Web 應用程式，請使用 **Power BI** REST API 或 Power BI C# SDK，以及 Azure Active Directory (AD) 授權**存取權杖**，以取得報表。 然後，使用相同的存取權杖載入報表。 **Power BI** API 為特定 **Power BI** 資源提供程式設計存取。 如需詳細資訊，請參閱 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 及 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)。

## <a name="download-the-sample"></a>下載範例
本文示範 GitHub 上的 [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app) 中所使用的程式碼。 若要依照本逐步解說進行，您可以下載範例。

您也可以完成[上線體驗工具](https://aka.ms/embedsetup/UserOwnsData)以快速開始使用並下載應用程式範例。

不過，若您選擇手動設定環境，可以繼續進行下方步驟。

## <a name="step-1---register-an-app-in-azure-ad"></a>步驟 1 - 在 Azure AD 中註冊應用程式
您必須在 Azure AD 中註冊應用程式，才能進行 REST API 呼叫。 如需詳細資訊，請參閱[註冊 Azure AD 應用程式以內嵌 Power BI 內容](register-app.md)。

若您已經下載 [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app)，就能使用註冊後取得的**用戶端識別碼**和**用戶端密碼**來設定範例，以便向 Azure AD 驗證。 若要設定範例，請在 *cloud.config* 檔案中，變更**用戶端識別碼**及**用戶端祕密**。

![](media/integrate-report/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>步驟 2 - 從 Azure AD 取得存取權杖
在您的應用程式中，您必須先從 Azure AD 取得**存取權杖**，才能對 Power BI REST API 進行呼叫。 如需詳細資訊，請參閱 [Authenticate users and get an Azure AD access token for your Power BI app](get-azuread-access-token.md) (驗證使用者，並為 Power BI 應用程式取得 Azure AD 存取權杖)。

## <a name="step-3---get-a-report"></a>步驟 3 - 取得報表
若要取得 **Power BI** 報表，請使用[取得報表](https://docs.microsoft.com/rest/api/power-bi/reports/getreports)作業以查看 **Power BI** 報表清單。 您可以從報表的清單中取得報表識別碼。

### <a name="get-reports-using-an-access-token"></a>使用存取權杖取得報表
有了您在[步驟 2](#step-2-get-an-access-token-from-azure-ad) 中擷取的**存取權杖**，即可呼叫[取得報表](https://docs.microsoft.com/rest/api/power-bi/reports/getreports)作業。 [取得報表](https://docs.microsoft.com/rest/api/power-bi/reports/getreports)作業會傳回報表清單。 您可以從報表清單中取得單一報表。 以下是用於取得報表的完整 C# 方法。 

若要進行 REST API 呼叫，您必須使用 *Bearer {access token}* 的格式包含 *Authorization* 標頭。

#### <a name="get-reports-with-the-rest-api"></a>利用 REST API 取得報表
**Default.aspx.cs**

```
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
您可以使用 .NET SDK 擷取報表清單，而不必直接呼叫 REST API。

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

## <a name="step-4---load-a-report-using-javascript"></a>步驟 4 - 使用 JavaScript 載入報表
您可以使用 JavaScript 將報表載入網頁上的 div 元素中。

**Default.aspx**

```
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

```
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
    });
}
```

若您已下載並執行 [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app)，範例看起來會類似下方所示。

![內嵌報表的範例](media/integrate-report/powerbi-embedded-report.png)

## <a name="working-with-groups-app-workspaces"></a>使用群組 (應用程式工作區)
若要從群組 (應用程式工作區) 內嵌報表，建議您使用以下 REST API 呼叫取得群組儀表板中所有可用報表的清單。 若要尋找此 REST API 呼叫的詳細資訊，請參閱[取得報表](https://docs.microsoft.com/rest/api/power-bi/reports/getreports)。 您必須擁有群組中的權限，要求才能傳回結果。

```
https://api.powerbi.com/v1.0/myorg/groups/{group_id}/reports
```

上述 API 會傳回可用報表的清單。 每個報表都有一個已經建構來支援群組內嵌的 EmbedUrl 屬性。

```
https://app.powerbi.com/reportEmbed?reportId={report_id}&groupId={group_id}
```

## <a name="next-steps"></a>後續步驟
GitHub 上有範例應用程式可供您檢閱。 如需詳細資訊，請參閱 [integrate-report-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app)。

您可以參閱 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) 取得更多 JavaScript API 的資訊。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

