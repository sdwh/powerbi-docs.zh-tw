---
title: 動態繫結
description: 了解如何使用動態繫結來內嵌報表。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776229"
---
# <a name="dynamic-binding"></a>動態繫結

動態繫結可讓您在內嵌報表時動態選取資料集。 報表和資料集不需要位於相同的工作區。 視選取的資料集而定，終端使用者會看到不同的結果。

這兩個工作區 (一個包含報表，另一個包含資料集) 必須指派給一個容量。

使用動態繫結內嵌報表可分為兩個階段：
1. 產生權杖
2. 調整設定物件

## <a name="generating-a-token"></a>產生權杖
若要產生權杖，請使用 [API 為多個項目產生內嵌權杖](embed-sample-for-customers.md#multiEmbedToken)。

動態繫結支援以下二個內嵌案例：「針對組織進行內嵌」  ，以及「針對客戶進行內嵌」  。

| 解決方案                   | 權杖                               | 需求                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 針對組織進行內嵌  | Power BI 使用者的存取權杖     | 其 Azure AD 權杖遭到使用之使用者必須具有所有成品的適當權限。                                                                    |
| 針對客戶進行內嵌     | 非 Power BI 使用者的存取權杖 | 必須同時包含報表和動態繫結資料集的權限。 使用新 API 來產生支援多個成品的內嵌權杖。 |

## <a name="adjusting-the-config-object"></a>調整設定物件
將 `datasetBinding` 新增至設定物件。 使用頁面底部的範例作為參考。

如果您不熟悉如何在 Power BI 中內嵌，請檢閱這些教學課程，以了解如何內嵌您的 Power BI 內容：
* [將客戶的 Power BI 內容內嵌至應用程式](embed-sample-for-customers.md)
* [教學課程：針對組織將 Power BI 內容內嵌至應用程式](embed-sample-for-your-organization.md)

 ### <a name="example"></a>範例
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```