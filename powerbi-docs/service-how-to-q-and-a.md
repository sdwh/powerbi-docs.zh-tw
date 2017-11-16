---
title: "如何使用 Power BI 問與答"
description: "如何使用 Power BI 問與答"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
editor: 
tags: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: a6736916a4bb2e94c1f5e1e3c3c3e5339cf990ec
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-use-power-bi-qa"></a>如何使用 Power BI 問與答
## <a name="ask-questions-of-your-data-using-natural-language"></a>使用自然語言詢問資料相關的問題
啟動儀表板。 [問與答] 方塊是您使用自然語言來輸入問題的地方。 問與答辨識您輸入的文字，然後找出哪裡 (哪個資料集) 可尋找解答。 問與答也可以用自動完成、重新描述，和其他文字及視覺輔助工具，協助您建立問題。

![](media/service-how-to-q-and-a/powerbi-qna.png)

您問題的答案會顯示為互動式的視覺效果，而且每當您修改問題時便會更新。

問與答易於互動，甚至充滿樂趣，而且，一個問題多半會帶來更多其他問題，原因在於視覺效果會顯示可探索的有趣路徑。 觀看 Amanda 示範使用問與答來建立視覺效果、深入探討這些視覺效果，以及將其釘選至儀表板。

> [!NOTE]
> 現在 [iPad、iPhone 及 iPod Touch 裝置上的 iOS 版 Microsoft Power BI 應用程式](mobile-apps-ios-qna.md)也提供問與答。
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="use-natural-language-to-ask-questions-about-your-data"></a>使用自然語言詢問您資料的相關問題
1. 請將游標放在 [問題] 方塊中。 即使您還沒開始輸入，問與答也會顯示包含建議的新畫面，以協助您提出問題。
   
   ![](media/service-how-to-q-and-a/powerbi-qna-cursor.png)  
   
   此清單包含：  
   a.  用以建立[磚](service-dashboard-tiles.md)的問題 (此類磚已釘選到儀表板)，以及  
   b.  在[基礎資料集](service-get-data.md)中的資料表名稱。  
   
   您一律可以選擇這些問題的其中一個做為起點，並繼續精簡問題，藉此尋找您要的特定解答。 或者，使用資料表名稱來幫助您撰寫新的問題。
2. 從下拉式清單中選取，或輸入您自己的問題。  
   
   ![](media/service-how-to-q-and-a/powerbi-qna-list.png)
3. 當您輸入了問題後，Power BI 問與答會挑選最佳的[視覺效果](power-bi-visualization-types-for-reports-and-q-and-a.md)來顯示您的答案；而當您修改這個問題時，視覺效果就會動態改變。 問與答也可以透過自動完成、重新描述您的問題，以及利用其他文字和視覺輔助工具，協助您建立問題。  
   ![](media/service-how-to-q-and-a/powerbi-qna-viz.png)
4. 當您輸入查詢時，Power BI 會在儀表板上有圖格之任何資料集尋找解答。  如果所有的圖格都來自 *datasetA* ，則您的答案將來自 *datasetA* 。  如果有磚來自 *datasetA* 和 *datasetB* ，則問與答就會搜尋這 2 個資料集的最佳回應。
   
   > [!TIP]
   > 所以要小心，如果只有一個磚來自 *datasetA* ，而您從儀表板中移除了，問與答將不再有權存取 *datasetA* 。
   > 
   > 
5. 如果您很滿意結果，請[將視覺效果釘選到儀表板](service-dashboard-pin-tile-from-q-and-a.md)，方法是選取在右上角的釘選圖示。 如果儀表板已與您共用或為應用程式的一部分，您就無法釘選。
   
   ![](media/service-how-to-q-and-a/pbi_qna_finish-typing-question.jpg)

### <a name="tell-qa-which-visualization-to-use"></a>告訴問與答要使用的視覺效果。
在使用問與答的時候，您不只可以要求要說明資料，也可以告訴它要如何顯示。 只需在問題結尾加上「為<visualization type>」。  例如「依工廠顯示庫存量為地圖」和「顯示總庫存為卡片」。  請自己試試看吧。

## <a name="how-does-qa-know-how-to-answer-questions"></a>問與答如何知道要怎麼回答問題？
### <a name="which-datasets-does-qa-use"></a>問與答使用了哪些資料集？
問與答怎知道要如何回答特定資料的問題？ 它依賴基礎資料集中的資料表、資料行與導出欄位的名稱。 因此您 (或資料集擁有者) 為其命名的方式相當重要！ 

例如，假設您有一個名為「銷售」的 Excel 資料表，其資料行標題為「產品」、「月」、「單位銷售」、「銷售毛額」和「利潤」。 您可以詢問有關任何這些實體的問題。  您可以詢問「顯示銷售」、「各月份的總收益」、「依單位銷售排序產品」等等問題。

問與答可以回答的問題，取決於您的資料集是如何組織的。 在 Salesforce 中的資料也能使用問與答嗎？ 當您連線到 salesforce.com 帳戶時，Power BI 會自動產生儀表板。  開始使用問與答詢問問題之前，請先查看在儀表板視覺效果中顯示的資料，以及問與答下拉式清單中顯示的資料。

* 如果視覺效果軸的標籤和值包含「銷售」、「客戶」、「月」與「商機」，您可以放心地詢問：哪位「客戶」的「商機」最大等問題，或顯示每月「銷售」的橫條圖。
* 如果下拉式清單中包含「銷售人員」、「州」及「年」，您可以放心地詢問：「2013  年時，佛羅里達州  哪位銷售人員  的銷售量 最低」等問題。

如果您在 Google Analytics 網站有效能資料，您或許可以詢問問與答有關花在網頁的時間、特定網頁瀏覽次數和使用者參與率。 或者，如果您要查詢人口統計資料，您可能會想詢問各地區年齡和家庭收入的相關問題。

### <a name="which-visualization-does-qa-use"></a>問與答會使用哪一種視覺效果？
問與答會根據要顯示的資料挑選最佳視覺效果。 有時在基礎資料集中資料的定義是特定類型或類別目錄，這就有助於問與答知道要如何加以顯示。 例如，如果將資料定義為日期類型，則較有可能顯示為折線圖。 分類為城市的資料比較有可能顯示為地圖。

您也可以告知問與答要使用哪一種視覺效果，方法是將視覺效果類型加入您的問題中。 但是請記住，以您要求的視覺效果類型讓問與答顯示資料，並不一定可行。

如需問與答可辨識的關鍵字相關資訊，請參閱[詢問問題的秘訣](service-q-and-a-tips.md)。

## <a name="next-steps"></a>後續步驟
回到 [Power BI 中的問與答](service-q-and-a.md)  
[教學課程：在零售分析範例使用問與答](power-bi-visualization-introduction-to-q-and-a.md)  
[在問與答中詢問問題的秘訣](service-q-and-a-tips.md)  
[準備適用於問與答的活頁簿](service-prepare-data-for-q-and-a.md)  
[從問與答將磚釘選至儀表板](service-dashboard-pin-tile-from-q-and-a.md)  

