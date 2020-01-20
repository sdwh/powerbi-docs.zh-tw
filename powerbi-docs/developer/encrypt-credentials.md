---
title: 加密認證
description: 逐步解說 - 加密內部部署閘道資料來源的認證
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836614"
---
# <a name="encrypt-credentials"></a>加密認證

當您在**企業內部部署閘道**下使用 [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/) 呼叫[建立資料來源](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource)或[更新資料來源](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)時，需要使用閘道的公用金鑰來加密認證值。

請參閱下列程式碼範例，了解如何在 .NET 中加密認證。

提供給下面 EncodeCredentials 方法的認證應該採用下列其中一種格式，視認證類型而定：

**基本 / Windows 認證**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**金鑰認證**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**OAuth2 認證**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**匿名認證**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**加密認證**

使用閘道的公開金鑰來加密認證值。 不同閘道版本可能有不同的公開金鑰大小。

請參閱 SDK 程式碼中的範例 (可從 PowerBI-CSharp GitHub 存放庫取得：[PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2))。

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)