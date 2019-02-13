---
title: 為應用程式驗證使用者及取得 Azure AD 存取權杖
description: 了解如何在 Azure Active Directory 註冊應用程式，以用來內嵌 Power BI 內容。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 7b2249964f2fff26bc68fea19fd0010d8990110b
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762528"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>為 Power BI 應用程式取得 Azure AD 存取權杖

了解如何在 Power BI 應用程式驗證使用者，以及擷取要與 REST API 搭配使用的存取權杖。

您必須先取得 Azure Active Directory (Azure AD) **驗證存取權杖** (存取權杖)，才能呼叫 Power BI REST API。 **存取權杖**可供您的應用程式存取 **Power BI** 儀表板、磚和報表。 若想深入了解 Azure Active Directory **存取權杖** 授與流程，請參閱 [Azure AD 授權碼授與流程](https://msdn.microsoft.com/library/azure/dn645542.aspx)。

根據您內嵌內容的方式，擷取的存取權杖會有所不同。 本文中使用了兩種不同的方法。

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Power BI 使用者 (使用者擁有資料) 的存取權杖

當使用者使用組織登入來手動登入 Azure AD 時適用此範例。 為 Power BI 使用者內嵌可以存取 Power BI 服務的內容時，會使用這項工作。

### <a name="get-an-authorization-code-from-azure-ad"></a>從 Azure AD 取得授權碼

取得**存取權杖**的第一個步驟，是從 **Azure AD** 取得授權碼。 請利用下列屬性建構查詢字串，並重新導向至 **Azure AD**。

#### <a name="authorization-code-query-string"></a>授權碼查詢字串

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "http://localhost:13526/Redirect"}
};
```

建構查詢字串之後，請重新導向至 **Azure AD** 以取得**授權碼**。  以下是用於建構**授權碼**查詢字串和重新導向至 **Azure AD** 的完整 C# 方法。 取得授權碼之後，您會使用**授權碼**來取得**存取權杖**。

在 redirect.aspx.cs 內，呼叫 [AuthenticationContext.AcquireTokenByAuthorizationCode](https://msdn.microsoft.com/library/azure/dn479531.aspx) 來產生權杖。

#### <a name="get-authorization-code"></a>取得授權碼

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "http://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.net/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>從授權碼取得存取權杖

您現在應該已從 Azure AD 取得授權碼。 一旦 **Azure AD** 以**授權碼**重新導向回您的 Web 應用程式，您就可使用**授權碼**來取得存取權杖。 以下是 C# 範例，可用於 default.aspx 頁面的重新導向頁面及 Page_Load 事件。

**Microsoft.IdentityModel.Clients.ActiveDirectory** 命名空間可從 [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet 套件中擷取。

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>非 Power BI 使用者 (應用程式擁有資料) 的存取權杖

此方法通常會用於擁有資料存取權的 ISV 類型應用程式。 使用者不一定要是 Power BI 使用者，而應用程式會控制終端使用者的驗證及存取。

### <a name="access-token-with-a-master-account"></a>搭配主帳戶的存取權杖

對於此方法，您可以使用單一*主*帳戶，即 Power BI Pro 使用者。 此帳戶的認證會儲存在應用程式。 應用程式會利用這些儲存的認證來對 Azure AD 進行驗證。 下列顯示的範例程式碼來自 [App owns data 範例](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>搭配服務主體的存取權杖

對於此方法，您可以使用[服務主體](embed-service-principal.md)，即「僅限應用程式」權杖。 應用程式會使用服務主體來對 Azure AD 進行驗證。 下列顯示的範例程式碼來自 [App owns data 範例](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="next-steps"></a>後續步驟

取得存取權杖後，即可呼叫 Power BI REST API 以內嵌內容。 如需如何內嵌內容的資訊，請參閱[如何內嵌 Power BI 內容](embed-sample-for-customers.md#embed-content-within-your-application)。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)