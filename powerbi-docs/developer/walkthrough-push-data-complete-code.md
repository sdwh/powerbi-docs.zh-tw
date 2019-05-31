---
title: 完整程式碼清單
description: 推送資料的逐步解說 - 完整程式碼清單
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: cdf6bf157a3d8fe1f865c610238e3cd1f829ef9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710298"
---
# <a name="push-data-to-a-dataset-complete-code-listing"></a>將資料推送至資料集的完整程式碼清單

本文屬於[將資料推送至資料集](walkthrough-push-data.md)逐步解說的一部分。

執行**將資料推送至資料集**中的步驟 2 到 5 之後，完整的程式碼應該如下所示。

## <a name="push-data-to-dataset-code"></a>將資料推送到資料集程式碼

```csharp
      using System;
      using Microsoft.IdentityModel.Clients.ActiveDirectory;
      using System.Net;
      using System.IO;
      using Newtonsoft.Json;

      namespace walkthrough_push_data
      {
          class Program
          {
              private static string token = string.Empty;

              static void Main(string[] args)
              {

                  //Get an authentication access token
                  token = GetToken();

                  //Create a dataset in Power BI
                  CreateDataset();

                  //Get a dataset to add rows into a Power BI table
                  string datasetId = GetDataset();

                  //Add rows to a Power BI table
                  AddRows(datasetId, "Product");

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
                  string authorityUri = "https://login.microsoftonline.com/common/";

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

              #region Create a dataset in Power BI
              private static void CreateDataset()
              {
                  //TODO: Add using System.Net and using System.IO

                  string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                  //POST web request to create a dataset.
                  //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                  HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                  request.KeepAlive = true;
                  request.Method = "POST";
                  request.ContentLength = 0;
                  request.ContentType = "application/json";

                  //Add token to the request header
                  request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                  //Create dataset JSON for POST request
                  string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                      "[{\"name\": \"Product\", \"columns\": " +
                      "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                      "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                      "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                      "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                      "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                      "]}]}";

                  //POST web request
                  byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
                  request.ContentLength = byteArray.Length;

                  //Write JSON byte[] into a Stream
                  using (Stream writer = request.GetRequestStream())
                  {
                      writer.Write(byteArray, 0, byteArray.Length);

                      var response = (HttpWebResponse)request.GetResponse();

                      Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                      Console.ReadLine();
                  }
              }
              #endregion

              #region Get a dataset to add rows into a Power BI table
              private static string GetDataset()
              {
                  string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
                  //POST web request to create a dataset.
                  //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
                  HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
                  request.KeepAlive = true;
                  request.Method = "GET";
                  request.ContentLength = 0;
                  request.ContentType = "application/json";

                  //Add token to the request header
                  request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                  string datasetId = string.Empty;
                  //Get HttpWebResponse from GET request
                  using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
                  {
                      //Get StreamReader that holds the response stream
                      using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
                      {
                          string responseContent = reader.ReadToEnd();

                          //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                          //and add using Newtonsoft.Json
                          var results = JsonConvert.DeserializeObject<dynamic>(responseContent);

                          //Get the first id
                          datasetId = results["value"][0]["id"];

                          Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                          Console.ReadLine();

                          return datasetId;
                      }
                  }
              }
              #endregion

              #region Add rows to a Power BI table
              private static void AddRows(string datasetId, string tableName)
              {
                  string powerBIApiAddRowsUrl = String.Format("https://api.powerbi.com/v1.0/myorg/datasets/{0}/tables/{1}/rows", datasetId, tableName);

                  //POST web request to add rows.
                  //To add rows to a dataset in a group, use the Groups uri: https://api.powerbi.com/v1.0/myorg/groups/{group_id}/datasets/{dataset_id}/tables/{table_name}/rows
                  //Change request method to "POST"
                  HttpWebRequest request = System.Net.WebRequest.Create(powerBIApiAddRowsUrl) as System.Net.HttpWebRequest;
                  request.KeepAlive = true;
                  request.Method = "POST";
                  request.ContentLength = 0;
                  request.ContentType = "application/json";

                  //Add token to the request header
                  request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

                  //JSON content for product row
                  string rowsJson = "{\"rows\":" +
                      "[{\"ProductID\":1,\"Name\":\"Adjustable Race\",\"Category\":\"Components\",\"IsCompete\":true,\"ManufacturedOn\":\"07/30/2014\"}," +
                      "{\"ProductID\":2,\"Name\":\"LL Crankarm\",\"Category\":\"Components\",\"IsCompete\":true,\"ManufacturedOn\":\"07/30/2014\"}," +
                      "{\"ProductID\":3,\"Name\":\"HL Mountain Frame - Silver\",\"Category\":\"Bikes\",\"IsCompete\":true,\"ManufacturedOn\":\"07/30/2014\"}]}";

                  //POST web request
                  byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(rowsJson);
                  request.ContentLength = byteArray.Length;

                  //Write JSON byte[] into a Stream
                  using (Stream writer = request.GetRequestStream())
                  {
                      writer.Write(byteArray, 0, byteArray.Length);

                      var response = (HttpWebResponse)request.GetResponse();

                      Console.WriteLine("Rows Added");

                      Console.ReadLine();
                  }
              }

              #endregion
          }
      }
```

## <a name="next-steps"></a>後續步驟

[將資料推送至 Power BI 資料集](walkthrough-push-data.md)  
[逐步解說 - 將資料推送至 Power BI 資料集](walkthrough-push-data.md)  
[使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)  
[取得驗證存取權杖](walkthrough-push-data-get-token.md)  
[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)  
[取得資料集，以便將資料列新增至 Power BI 資料表](walkthrough-push-data-get-datasets.md)  
[將資料列新增至 Power BI 資料表](walkthrough-push-data-add-rows.md)  
[Power BI REST API 參考](https://docs.microsoft.com/rest/api/power-bi/)  
[Power BI REST API 概觀](overview-of-power-bi-rest-api.md)  

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)