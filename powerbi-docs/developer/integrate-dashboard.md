---
title: "將儀表板整合至組織的應用程式"
description: "了解如何使用 Power BI API，將儀表板整合或內嵌至 Web 應用程式。"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: f3968fd9fb89e868754bb6025a23fdbd028a3965
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="integrate-a-dashboard-into-an-app-for-your-organization"></a>將儀表板整合至組織的應用程式
了解如何在對組織進行內嵌時，使用 REST API 呼叫配合 Power BI JavaScript API 將儀表板整合或內嵌至 Web 應用程式。

![內嵌的儀表板](media/integrate-dashboard/powerbi-embed-dashboard.png)

若要遵循此逐步解說進行整合，您需要一個 **Power BI** 帳戶。 如果您沒有帳戶，可以[註冊免費 Power BI 帳戶](../service-self-service-signup-for-power-bi.md)，或建立您自己的 [Azure Active Directory 租用戶](create-an-azure-active-directory-tenant.md)用於測試用途。

> [!NOTE]
> 想要改用 embedtoken 內嵌客戶的儀表板嗎？ 請參閱[將客戶的儀表板、磚或報表整合至應用程式](embed-sample-for-customers.md)。
> 
> 

若要將儀表板整合至 Web 應用程式，請使用 **Power BI** REST API 或 Power BI C# SDK，以及 Azure Active Directory (AD) 授權**存取權杖**，以取得儀表板。 然後，使用相同的存取權杖載入儀表板。 **Power BI** API 為特定 **Power BI** 資源提供程式設計存取。 如需詳細資訊，請參閱 [Overview of Power BI REST API](https://msdn.microsoft.com/library/dn877544.aspx) (Power API REST 概觀) 及 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)。

## <a name="download-the-sample"></a>下載範例
本文示範 GitHub 上的 [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) 中所使用的程式碼。 若要依照本逐步解說進行，您可以下載範例。

## <a name="step-1---register-an-app-in-azure-ad"></a>步驟 1 - 在 Azure AD 中註冊應用程式
您必須在 Azure AD 中註冊應用程式，才能進行 REST API 呼叫。 如需詳細資訊，請參閱[註冊 Azure AD 應用程式以內嵌 Power BI 內容](register-app.md)。

若您已經下載[整合儀表板範例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app)，就能使用註冊後取得的**用戶端識別碼**和**用戶端祕密**，以便範例向 Azure AD 驗證。 若要設定範例，請在 *cloud.config* 檔案中，變更**用戶端識別碼**及**用戶端祕密**。

![](media/integrate-dashboard/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>步驟 2 - 從 Azure AD 取得存取權杖
在您的應用程式中，您必須先從 Azure AD 取得**存取權杖**，才能對 Power BI REST API 進行呼叫。 如需詳細資訊，請參閱 [Authenticate users and get an Azure AD access token for your Power BI app](get-azuread-access-token.md) (驗證使用者，並為 Power BI 應用程式取得 Azure AD 存取權杖)。

## <a name="step-3---get-a-dashboard"></a>步驟 3 - 取得儀表板
若要取得 **Power BI** 儀表板，請使用 [取得儀表板](https://msdn.microsoft.com/library/mt465739.aspx) 作業以查看 **Power BI** 儀表板清單。 您可以從儀表板清單中取得儀表板識別碼。

![](media/integrate-dashboard/powerbi-embed-dashboard-get-dashboards.png)

### <a name="get-dashboards-using-an-access-token"></a>使用存取權杖取得儀表板
有了您在[步驟 2](#step-2-get-an-access-token-from-azure-ad) 中擷取的**存取權杖**，即可呼叫[取得儀表板](https://msdn.microsoft.com/library/mt465739.aspx)作業。 [取得儀表板](https://msdn.microsoft.com/library/mt465739.aspx) 作業會傳回一份儀表板清單。 您可以從儀表板清單中取得單一儀表板。 以下是用於取得儀表板的完整 C# 方法。 如需有關如何使用 Power BI REST API 的範例，請參閱 [ARYAPIARY 上的 Power BI REST API](http://docs.powerbi.apiary.io/)。

若要進行 REST API 呼叫，您必須使用 *Bearer {access token}* 的格式包含 *Authorization* 標頭。

#### <a name="get-dashboards-with-the-rest-api"></a>利用 REST API 取得儀表板
**Default.aspx.cs**

```
protected void getDashboardsButton_Click(object sender, EventArgs e)
{
    string responseContent = string.Empty;

    //Configure dashboards request
    System.Net.WebRequest request = System.Net.WebRequest.Create(String.Format("{0}dashboards", baseUri)) as System.Net.HttpWebRequest;
    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", authResult.AccessToken));

    //Get dashboards response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            responseContent = reader.ReadToEnd();

            //Deserialize JSON string
            PBIDashboards PBIDashboards = JsonConvert.DeserializeObject<PBIDashboards>(responseContent);

            if (PBIDashboards != null)
            {
                var gridViewDashboards = PBIDashboards.value.Select(dashboard => new {
                    Id = dashboard.id,
                    DisplayName = dashboard.displayName,
                    EmbedUrl = dashboard.embedUrl
                });

                this.GridView1.DataSource = gridViewDashboards;
                this.GridView1.DataBind();
            }
        }
    }
}

//Power BI Dashboards used to deserialize the Get Dashboards response.
public class PBIDashboards
{
    public PBIDashboard[] value { get; set; }
}
public class PBIDashboard
{
    public string id { get; set; }
    public string displayName { get; set; }
    public string embedUrl { get; set; }
    public bool isReadOnly { get; set; }
}
```

#### <a name="get-dashboards-using-the-net-sdk"></a>利用 .NET SDK 取得儀表板
您可以使用 .NET SDK 擷取儀表板清單，而不必直接呼叫 REST API。

```
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It will be used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get a list of dashboards your "My Workspace"
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    var embedUrl = dashboard.EmbedUrl
}
```

## <a name="step-4---load-a-dashboard-using-javascript"></a>步驟 4 - 使用 JavaScript 載入儀表板
您可以使用 JavaScript 將儀表板載入到網頁上的 div 項目中。

**Default.aspx**

```
<!-- Embed Dashboard-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a dashboard</div>

            <div>Enter an embed url for a dashboard from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedDashboardAction" value="Embed Dashboard" />
        </div>

        <div id="dashboardContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected dashboard.
    var el = document.getElementById("bEmbedDashboardAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedDashboard, false);
    } else {
        el.attachEvent('onclick', updateEmbedDashboard);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded dashboard if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedDashboard();
    }
};

// update embed dashboard
function updateEmbedDashboard() {

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
        type: 'dashboard',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the dashboard.
    var dashboardContainer = document.getElementById('dashboardContainer');

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("tileClicked", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });

    // dashboard.on will add an event handler which prints to Log window.
    dashboard.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

若您已下載並執行[整合儀表板範例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app)，範例看起來會類似下方所示。

![](media/integrate-dashboard/powerbi-embed-dashboard.png)

## <a name="tile-clicked-events"></a>按一下磚事件
在上述範例中，您可能已經注意到，您可以在儀表板上按一下磚時處理事件。 如需事件的詳細資訊，請參閱 [JavaScript API 中的處理事件](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events)。

```
// dashboard.on will add an event handler which prints to Log window.
dashboard.on("tileClicked", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Tile Clicked<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});

// dashboard.on will add an event handler which prints to Log window.
dashboard.on("error", function (event) {
    var logView = document.getElementById('logView');
    logView.innerHTML = logView.innerHTML + "Error<br/>";
    logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
    logView.innerHTML = logView.innerHTML + "---------<br/>";
});
```

如果您下載並執行[整合儀表板範例](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/PowerBI.com%20Integrate/integrate-dashboard-web-app)，按一下磚即會在儀表板下輸出文字。 它看起來如下所示。 這會讓您記錄已按一下一個磚，然後將使用者瀏覽至下一個合適的位置。

```
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "", "navigationUrl": "https://app.powerbi.com/dashboards/fcff76f9-15ff-4a8e-8242-275ac9c25b90/qna?q=count%20of%20new%20hires%20from%20July%202014%20to%20December%202014", "tileId": "0e99b45c-9b53-4920-b239-cee7d37d2369" }
---------
Tile Clicked
{ "event": "TileClick", "reportEmbedUrl": "https://app.powerbi.com/reportEmbed?reportId=ab199308-80b1-4626-9823-43a84623bd9c", "navigationUrl": "https://app.powerbi.com/reports/ab199308-80b1-4626-9823-43a84623bd9c/ReportSection1", "tileId": "ffc30447-674a-4511-944f-79e182d719de", "pageName": "ReportSection1" }
---------
```

## <a name="working-with-groups-app-workspaces"></a>使用群組 (應用程式工作區)
若要從群組 (應用程式工作區) 內嵌儀表板，建議您使用下列 REST API 呼叫在群組中取得所有可用儀表板的清單。 若要尋找此 REST API 呼叫的詳細資訊，請參閱[取得儀表板](https://msdn.microsoft.com/library/mt465739.aspx)。 您必須擁有群組中的權限，要求才能傳回結果。

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards
```

上述的 API 會傳回可用儀表板的清單。 每個儀表板都有一個已經建構來支援群組內嵌的 EmbedUrl 屬性。

```
https://app.powerbi.com/dashboardEmbed?dashboardId={dashboardId}&groupId={groupId}
```

## <a name="limitations"></a>限制
* 存取內嵌儀表板的終端使用者必須擁有 Power BI 帳戶，且具備儀表板的存取權。 他們可能擁有儀表板，或儀表板已與使用者共用。
* 目前 Q&A 不支援內嵌儀表板。
* 有一項暫時性的限制，在與安全性群組共用儀表板時，使用者必須先存取 PowerBI.com 中的儀表板，然後才能看到它為內嵌。

## <a name="next-steps"></a>後續步驟
GitHub 上有範例應用程式可供您檢閱。 上述範例皆以該範例為基礎。 如需詳細資訊，請參閱 [integrate-dashboard-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app)。

您可以參閱 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) 取得更多 JavaScript API 的資訊。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

