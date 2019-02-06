---
title: 取得驗證存取權杖
description: 推送資料逐步解說─取得驗證存取權杖
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: 2d4e59badf394153dcb6877a270d2ecea63f5df6
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55761953"
---
# <a name="step-2-get-an-authentication-access-token"></a>步驟 2：取得驗證存取權杖

本文屬於[將資料推送至資料集](walkthrough-push-data.md)逐步解說的一部分。

在＜將資料推送至資料集＞的**步驟 1** [使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)中，您在 Azure AD 中註冊了用戶端應用程式。 在此步驟中，您會收到驗證存取權杖。 Power BI 應用程式會與 **Azure AD** 整合，以提供應用程式的安全登入和授權。 您可以使用權杖來向 **Azure AD** 驗證，並取得 Power BI 資源的存取權。

以下是取得驗證存取權杖的方式。

## <a name="get-an-authentication-access-token"></a>取得驗證存取權杖

> **注意**：開始使用之前，請確定您已經執行過先前[將資料推送至資料集](walkthrough-push-data.md)逐步解說中的先前步驟。
> 
> 

1. 在 Visual Studio 2015 中，建立 **主控台應用程式** 專案。
2. 安裝 [.NET NuGet 套件的 Azure AD 驗證程式庫](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)。 若要取得 .NET 應用程式中的驗證安全性權杖，您可以使用此套件。 安裝套件的方法如下：

     a. 在 Visual Studio 2015 中，選擇 **工具**  > **NuGet 套件管理員**  >  **套件管理器主控台**。

     b. 在 **套件管理器主控台**中，輸入 Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612。
3. 將下列程式碼加入類別 Program {...}。
4. 將 "{ClientID}" 取代為註冊應用程式時所得的 **用戶端識別碼** 。 請參閱[使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)。
5. 安裝 Microsoft.IdentityModel.Clients.ActiveDirectory 套件之後，將 **using Microsoft.IdentityModel.Clients.ActiveDirectory;** 加入 Program.cs。
6. 執行主控台應用程式，然後登入您的 Power BI 帳戶。 您應該會在 [主控台視窗] 中看到權杖字串。

**取得驗證安全性權杖的範例程式碼**

將此程式碼加入 Program {...}。

* 呼叫作業的權杖變數：
  
  ```
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* 在 static void Main(string[] args) 中：
  
  ```
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* 加入 GetToken() 方法：

```
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

取得驗證權杖之後，您可以呼叫任何 Power BI 作業。 下一個步驟將為您示範如何呼叫 [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) 作業，以建立將資料推送至儀表板的資料集。

下一個步驟將為您示範如何[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)。

以下是[完整程式碼清單](#code)。

<a name="code"/>

## <a name="complete-code-listing"></a>完整程式碼清單

    using System;
    using Microsoft.IdentityModel.Clients.ActiveDirectory;

    namespace walkthrough_push_data
    {
        class Program
        {
            private static string token = string.Empty;

            static void Main(string[] args)
            {

                //Get an authentication access token
                token = GetToken();

            }

            #region Get an authentication access token
            private static string GetToken()
            {
                // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
                // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

                //The client id that Azure AD created when you registered your client app.
                string clientID = "{Client_ID}";

                //RedirectUri you used when you register your app.
                //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
                // You can use this redirect uri for your client app
                string redirectUri = "https://login.live.com/oauth20_desktop.srf";

                //Resource Uri for Power BI API
                string resourceUri = "https://analysis.windows.net/powerbi/api";

                //OAuth2 authority Uri
                string authorityUri = "https://login.microsoftonline.net/common/";

                //Get access token:
                // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
                // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
                // To install the Active Directory Authentication Library NuGet package in Visual Studio,
                //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

                // AcquireToken will acquire an Azure access token
                // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
                AuthenticationContext authContext = new AuthenticationContext(authorityUri);
                string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

                Console.WriteLine(token);
                Console.ReadLine();

                return token;
            }

            #endregion

        }
    }

[下一步 >](walkthrough-push-data-create-dataset.md)

## <a name="next-steps"></a>後續步驟

[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)  
[使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)  
[Azure AD Authentication Library for .NET NuGet 套件](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)  
[將資料推送至 Power BI 資料集](walkthrough-push-data.md)  
[Power BI REST API 概觀](overview-of-power-bi-rest-api.md)  
[Power BI REST API 參考](https://docs.microsoft.com/rest/api/power-bi/)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)