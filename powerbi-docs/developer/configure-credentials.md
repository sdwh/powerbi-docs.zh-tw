---
title: 以程式設計的方式為 Power BI 設定認證
description: 如何針對自動化以程式設計的方式為 Power BI 設定認證
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836581"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>以程式設計的方式為 Power BI 設定認證

請遵循以下步驟來以程式設計的方式為 Power BI 設定認證。

## <a name="configure-a-credential-flow-for-data-sources"></a>為資料來源設定認證流程

1. 呼叫 [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) 來找到資料集的資料來源。 各資料來源的回應本文中會有類型、連線詳細資料、閘道和資料來源識別碼。

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. 依照認證類型，根據[更新資料來源範例](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)來建置認證字串。

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. 建置認證詳細資料。

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. 呼叫 [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)來設定認證，使用步驟 1 的閘道和資料來源，以及步驟 4 的認證詳細資料。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>到期的內部部署資料來源認證流程

1. [遵循前述的步驟 1 和 2](#configure-a-credential-flow-for-data-sources)。

2. 呼叫 [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways)來擷取閘道公開金鑰。

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. 以閘道公開金鑰加密認證字串。 不同的閘道版本可能有不同的公用金鑰大小。
    
    請參閱 SDK 程式碼中的範例 (可從 PowerBI-CSharp GitHub 存放庫取得：[PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2))。
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. 使用加密的認證來建置認證。

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. 呼叫 [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)來設定認證。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>為資料閘道設定新的資料來源

1. 在您的電腦上安裝[內部部署資料閘道](https://powerbi.microsoft.com/gateway/)。

2. 呼叫 [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways)來擷取閘道識別碼和公開金鑰。

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. 使用在步驟[到期的內部部署資料來源認證流程](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway)中擷取到的閘道公開金鑰，來建置類似上述情境的認證詳細資料。

4. 建置要求本文

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
    dataSourceType: "SQL",
    connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
    credentialDetails: credentialDetails,
    dataSourceName: "my sql datasource");
    ```

5. 呼叫 [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) API。

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="troubleshooting"></a>疑難排解

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>呼叫 get data sources 時未找到任何閘道和資料來源識別碼

這項問題代表資料集未繫結至閘道。 建立新的資料集時，對每個雲端連線而言，沒有認證的資料來源都會自動建立在使用者的雲端閘道上。 這個閘道會用來儲存雲端連線的認證。

在您建立資料集後，會自動完成資料集和合適閘道的繫結，其中包括所有連線的相符資料來源。 如果沒有該種閘道或有多個合適的閘道，則自動繫結會失敗。

建立缺少的內部部署資料來源 (如果缺少的話)，並使用 [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) 手動將資料集繫結至閘道。

如果要探索可繫結的閘道，請使用 [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways)。