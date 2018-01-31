---
title: "將 Power BI 磚整合至組織的應用程式"
description: "將磚整合到應用程式的逐步解說，程式碼範例"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 12/19/2017
ms.author: maghan
ms.openlocfilehash: fd33908f907ffac6cbff765e01e4a4321d399ca8
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2018
---
# <a name="integrate-a-tile-into-an-app-user-owns-data"></a>將磚整合至應用程式中 (使用者擁有資料)
了解如何在對組織進行內嵌時，使用 REST API 呼叫配合 Power BI JavaScript API 將磚整合或內嵌至 Web 應用程式。

![在 Web 應用程式中內嵌磚](media/integrate-tile/powerbi-embedded-tile.png)

若要遵循此逐步解說進行整合，您需要一個 **Power BI** 帳戶。 如果您沒有帳戶，可以[註冊免費 Power BI 帳戶](../service-self-service-signup-for-power-bi.md)，或建立您自己的 [Azure Active Directory 租用戶](create-an-azure-active-directory-tenant.md)用於測試用途。

> [!NOTE]
> 想要改用 embedtoken 內嵌客戶的磚嗎？ 請參閱[將客戶的儀表板、磚或報表整合至應用程式](embed-sample-for-customers.md)。
> 
> 

若要將磚整合至 Web 應用程式，請使用 **Power BI** REST API 或 Power BI C# SDK，以及 Azure Active Directory (AD) 授權**存取權杖**，以取得磚。 然後，使用相同的存取權杖載入磚。 **Power BI** API 為特定 **Power BI** 資源提供程式設計存取。 如需詳細資訊，請參閱 [Overview of Power BI REST API](https://msdn.microsoft.com/library/dn877544.aspx) (Power API REST 概觀) 及 [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)。

## <a name="download-the-sample"></a>下載範例
本文示範 GitHub 上的 [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) 中所使用的程式碼。 若要依照本逐步解說進行，您可以下載範例。

## <a name="step-1---register-an-app-in-azure-ad"></a>步驟 1 - 在 Azure AD 中註冊應用程式
您必須在 Azure AD 中註冊應用程式，才能進行 REST API 呼叫。 如需詳細資訊，請參閱[註冊 Azure AD 應用程式以內嵌 Power BI 內容](register-app.md)。

若您已經下載 [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app)，就能使用註冊後取得的**用戶端識別碼**和**用戶端密碼**來設定範例，以便向 Azure AD 驗證。 若要設定範例，請在 *cloud.config* 檔案中，變更**用戶端識別碼**及**用戶端祕密**。

![](media/integrate-tile/powerbi-embed-dashboard-register-app4.png)

## <a name="step-2---get-an-access-token-from-azure-ad"></a>步驟 2 - 從 Azure AD 取得存取權杖
在您的應用程式中，您必須先從 Azure AD 取得**存取權杖**，才能對 Power BI REST API 進行呼叫。 如需詳細資訊，請參閱 [Authenticate users and get an Azure AD access token for your Power BI app](get-azuread-access-token.md) (驗證使用者，並為 Power BI 應用程式取得 Azure AD 存取權杖)。

## <a name="step-3---get-a-tile"></a>步驟 3 - 取得磚
若要取得 **Power BI** 磚，請使用[取得磚](https://msdn.microsoft.com/library/mt465741.aspx)作業，以從提供的儀表板中取得 **Power BI** 磚的清單。 從磚的清單中，您可以取得磚識別碼及內嵌 URL。

您必須先擷取儀表板識別碼，才能取得磚。 如需如何擷取儀表板的資訊，請參閱[將儀表板整合到應用程式 (使用者擁有資料)](integrate-dashboard.md)。

### <a name="get-tiles-using-an-access-token"></a>使用存取權杖取得磚
有了您在[步驟 2](#step-2-get-an-access-token-from-azure-ad) 中擷取的**存取權杖**，即可呼叫[取得磚](https://msdn.microsoft.com/library/mt465741.aspx)作業。 [取得磚](https://msdn.microsoft.com/library/mt465741.aspx)作業會傳回磚清單。 您可以從磚清單中取得單一磚。 以下是用於取得磚的完整 C# 方法。 

若要進行 REST API 呼叫，您必須使用 *Bearer {access token}* 的格式包含 *Authorization* 標頭。

#### <a name="get-tiles-with-the-rest-api"></a>利用 REST API 取得磚
**Default.aspx.cs**

```
using Newtonsoft.Json;

//Get a tile from a dashboard. In this sample, you get the first tile.
protected void GetTile(string dashboardId, int index)
{
    //Configure tiles request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}Dashboards/{1}/Tiles",
        baseUri,
        dashboardId)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get tiles response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBITiles tiles = JsonConvert.DeserializeObject<PBITiles>(reader.ReadToEnd());

            //Sample assumes at least one Dashboard with one Tile.
            //You could write an app that lists all tiles in a dashboard
            if (tiles.value.Length > 0)
                tileEmbedUrl.Text = tiles.value[index].embedUrl;
        }
    }
}

//Power BI Tiles used to deserialize the Get Tiles response.
public class PBITiles
{
    public PBITile[] value { get; set; }
}
public class PBITile
{
    public string id { get; set; }
    public string title { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-tiles-using-the-net-sdk"></a>利用 .NET SDK 取得磚
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
    ODataResponseListDashboard tiles = client.Dashboards.GetDashboards();

    // Get a list of dashboards from a group (app workspace)
    ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(groupId);

    Dashboard dashboard = dashboards.Value.FirstOrDefault();

    // Get the first tile from the above dashbaord
    ODataResponseListTile tiles = client.Dashboards.GetTiles(dashboard.Id);

    Tile tile = tiles.Value.FirstOrDefault();
}
```

## <a name="step-4---load-a-tile-using-javascript"></a>步驟 4 - 使用 JavaScript 載入磚
您可以使用 JavaScript 將磚載入網頁上的 div 元素中。

**Default.aspx**

```
<!-- Embed Tile-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a tile</div>

            <div>Enter an embed url for a tile from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedTileAction" value="Embed Tile" />
        </div>

        <div id="tileContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```
window.onload = function () {
    // client side click to embed a selected tile.
    var el = document.getElementById("bEmbedTileAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedTile, false);
    } else {
        el.attachEvent('onclick', updateEmbedTile);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded tile if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedTile();
    }
};

// update embed tile
function updateEmbedTile() {

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
        type: 'tile',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the tile.
    var tileContainer = document.getElementById('tileContainer');

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);

    // tile.on will add an event handler which prints to Log window.
    tile.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    });
}
```

若您已下載並執行 [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app)，範例看起來會類似下方所示。

![在 Web 應用程式中內嵌磚](media/integrate-tile/powerbi-embedded-tile.png)

## <a name="working-with-groups-app-workspaces"></a>使用群組 (應用程式工作區)
若要從群組 (應用程式工作區) 內嵌磚，建議您使用以下 REST API 呼叫取得群組儀表板中所有可用磚的清單。 若要尋找此 REST API 呼叫的詳細資訊，請參閱[取得磚](https://msdn.microsoft.com/library/mt465741.aspx)。 您必須擁有群組中的權限，要求才能傳回結果。

```
https://api.powerbi.com/v1.0/myorg/groups/{groupId}/dashboards/{dashboard_id}/tiles
```

上述 API 會傳回可用磚的清單。 每個磚都有一個已經建構來支援群組內嵌的 EmbedUrl 屬性。

```
https://app.powerbi.com/embed?dashboardId={dashboard_id}&tileId={tile_id}&groupId={group_id}
```

## <a name="next-steps"></a>後續步驟
PowerBI-JavaScript Wiki 上的[圖格內嵌](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Tile-Embed)

[Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript).

GitHub 上的 [integrate-tile-web-app](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app) 範例。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

