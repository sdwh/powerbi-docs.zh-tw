---
title: Power BI Embedded 問與答
description: Power BI Embedded 提供您一種將問與答併入應用程式的方式，讓您的使用者使用自然語言提問。
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/20/2017
ms.author: maghan
ms.openlocfilehash: 208c1e2a0e188622f989faa6ba391d9742dd7967
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277961"
---
# <a name="qa-in-power-bi-embedded"></a>Power BI Embedded 問與答
Power BI Embedded 提供您一種將問與答併入應用程式的方式，讓您的使用者使用自然語言提問，並立即收到類似圖表或圖形視覺效果的表單回應。

![內嵌框架中的問與答互動式問題](media/qanda/embedded-qanda.gif)

內嵌在應用程式中的問與答有兩種模式：**互動式**和**只產生結果**。 **互動式**模式讓您輸入問題，並在視覺效果中顯示。 如想要顯示事先準備好的問題，您可以在內嵌組態中擴展問題，使用**只產生結果**模式。

JavaScript 程式碼看起來會像下面這樣。

```
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnAMode.Interactive | models.QnAMode.ResultOnly,
    question:    optional parameter for Explore mode (QnAMode.Interactive) and mandatory for Render Result mode (QnAMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>事先準備好的問題
如果對事先準備好的問題使用**結果模式**，您可以在框架中插入其他問題，讓它們立即獲得解答，取代原先的結果。 符合新問題的新視覺效果隨即呈現。

常見問題集清單即是這種使用方式的一例。 使用者可以瀏覽問題，讓它們在相同的內嵌組件內獲得解答。

**JS SDK 使用方式的程式碼片段：**  

```        
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>視覺化呈現的事件
若為**互動式**模式，每次呈現的視覺效果以正在鍵入的更新輸入查詢為目標變更時，應用程式就會收到資料變更事件通知。

接聽 *visualRendered* 事件可讓您儲存問題以供之後使用。 

**JS SDK 使用方式的程式碼片段：**  

```
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>內嵌的權杖
建立移出資料集的內嵌權杖，以便開始問與答的一部分。 如需詳細資訊，請參閱 [Generate token](https://docs.microsoft.com/rest/api/power-bi/embedtoken) (產生權杖)。

## <a name="next-steps"></a>後續步驟
若要嘗試問與答內嵌，請參閱 [JavaScript 內嵌範例](https://microsoft.github.io/PowerBI-JavaScript/demo/)。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

