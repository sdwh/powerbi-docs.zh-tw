---
title: "Power BI Desktop 的 DAX 基本概念"
description: "Power BI Desktop 的 DAX 基本概念"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 4c1ddee96d82af446256d812f5b982a1802a6c30
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="dax-basics-in-power-bi-desktop"></a>Power BI Desktop 的 DAX 基本概念
本文適用對象為剛開始使用 Power BI Desktop 的使用者。 其目的在於以快速且容易了解的方式，為您介紹如何使用資料分析運算式 (DAX)，以便解決一些基本計算和資料分析問題。 我們將逐一探討一些概念性資訊、一系列您可以完成的工作，以及用來測試所學內容的幾項測驗。 完成本文之後，您便可充分了解 DAX 最重要的基本概念。

## <a name="what-is-dax"></a>何謂 DAX？
DAX 是公式或運算式中，可用來計算並傳回一或多個值的函數、運算子和常數集合。 簡單來說，DAX 可協助您透過模型中現有的資料來建立新資訊。

## <a name="why-is-dax-so-important"></a>為什麼 DAX 很重要？
建立新的 Power BI Desktop 檔案並匯入一些資料，是相當容易的工作。 您甚至可以建立報表，以顯示重要的深入資訊，而完全不需要用到任何 DAX 公式。 但如果您需要分析所有產品類別不同日期範圍的成長百分比， 又或者需要計算相較於市場趨勢的每年成長量，該怎麼辦？ DAX 公式可提供這項功能，以及其他許多重要的功能。 了解如何建立有效的 DAX 公式可協助您充分利用資料。 當您取得所需的資訊之後，即可開始解決影響營收的實際商務問題。 這便是 Power BI 的強大功能，而 DAX 將協助您達成目的。

## <a name="prerequisites"></a>先決條件
您可能已經熟悉如何在 Microsoft Excel 中建立公式。 該知識有助於了解 DAX，但即使您沒有使用 Excel 公式的經驗，此處描述的概念也將協助您開始立即建立 DAX 公式，並解決真實世界的 BI 問題。

我們將著重於介紹計算中所使用的 DAX 公式，更明確地說，也就是量值和導出資料行中所使用的 DAX 公式。 您應該已經熟悉 Power BI Desktop、匯入資料、將欄位加入報表中，而且也應該熟悉[量值](desktop-measures.md)和[計算結果欄](desktop-calculated-columns.md)的基本概念。

**範例活頁簿**

了解 DAX 的最佳方式是建立一些基本公式、用來處理一些實際資料，並親自查看結果。 此處的範例和工作使用適用於 Power BI Desktop Preview 的 Contoso Sales 範例檔案。 這是＜教學課程：在 Power BI Desktop 中建立您自己的量值＞一文中所使用的相同範例檔案。 您可以從[這裡](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip)下載。

## <a name="lets-begin"></a>現在就開始進行！
我們將分成下列三個基本概念來介紹 DAX：「語法」 、「函數」 和「內容」 。 DAX 當然還有其他重要概念，不過了解這三個概念將為您的 DAX 技能奠定最佳基礎。

### <a name="syntax"></a>語法
在您建立自己的公式之前，請先了解 DAX 公式語法。 語法包含組成公式的各種元素，簡單來說就是公式的撰寫方式。 舉例來說，以下是某個量值的簡單 DAX 公式。

![](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

這個公式包含下列語法元素：

**A.** 量值名稱 **Total Sales**。

**B.** 等號運算子 (**=**) 表示公式的開頭。 一旦計算，即會傳回結果。

**C.** DAX 函數 **SUM** 會加總 **Sales[SalesAmount]** 資料行中的所有數值。 稍後您將進一步了解函數。

**D.** 括弧 **()** 會括住內含一或多個引數的運算式。 所有函數都至少需要一個引數。 一個引數會傳遞一個值給函數。

**E.** 參考資料表 **Sales**。

**F.** Sales 資料表中的參考資料行 **[SalesAmount]**。 有了這個引數，SUM 函數便知道哪個資料行要加以彙總總和。

嘗試了解 DAX 公式時，將每個元素解析成您平日思考及說出的話語會很有幫助。 例如，您可以將這個公式讀成：

> *針對名為 Total Sales 的量值，計算 (=) Sales 資料表的 [SalesAmount ] 資料行中的值總和。*
> 
> 

這個量值在加入報表後，會加總我們所包含的其他每個欄位的銷售額 (例如美國的行動電話)，以計算並傳回值。

您可能會想：「這個量值的功能，不是與直接將 SalesAmount 欄位加入我的報表中一樣嗎？ 」 沒錯。 但建立自己的量值來加總 SalesAmount 欄位中的值有個好處：那就是可以將這個量值當做引數用於其他公式。 雖然現在可能有點難以理解，但隨著您愈來愈熟練於 DAX 公式，了解這點可讓您的公式和模型更有效率。 事實上，您稍後將會看到 Total Sales 量值如何顯示為其他公式中的引數。

接著我們將探討這個公式的其他幾點。 我們將特別介紹 [SUM](https://msdn.microsoft.com/library/ee634387.aspx) 函數。 函數是預先撰寫的公式，以便簡化數值、日期、時間、文字等複雜的計算和操作。 稍後您將進一步了解函數。

您也會看到資料行 [SalesAmount] 前面加上資料行所屬的資料表 Sales。 這就是所謂的完整資料行名稱，因為它包含資料行名稱，並且前面加上了資料表名稱。 同一個資料表所參考的資料行不需要在公式中包含資料表名稱。 因此可縮短參考許多資料行的冗長公式，也讓公式更容易閱讀。 不過，最好能夠在您的量值公式中包含資料表名稱，即使在同一個資料表中亦然。

> [!NOTE]
> 如果資料表名稱包含空格、保留的關鍵字或不允許的字元，則您必須以單引號括住資料表名稱。 如果資料表名稱包含 ANSI 英數字元範圍以外的任何字元，則不論您的地區設定是否支援該字元集，您也需要以引號括住名稱。
> 
> 

您的公式語法必須正確。 在大多數情況下，如果語法不正確，便會傳回語法錯誤。 在其他情況下，語法可能正確，但傳回的值可能不是您預期的值。 Power BI Desktop 中的 DAX 編輯器提供了建議，這項功能可用來協助您選取正確的元素，以建立語法正確的公式。

一起來建立一個簡單的公式。 這項工作將協助您進一步了解公式語法，以及公式列中的建議功能如何協助您。

### <a name="task-create-a-measure-formula"></a>工作：建立量值公式
若要完成這項工作，您需要開啟 Contoso Sales 範例 Power BI Desktop 檔案。
    
1.  在 [報表] 檢視的 [欄位] 清單中，以滑鼠右鍵按一下 **Sales** 資料表，然後按一下 [新增量值]。
    
2.  在公式列中，輸入新量值名稱 **Previous Quarter Sales** 來取代 [量值]。
    
3.  在等號後面輸入 **SUM**，後面接著左括弧。
    
    我們不會輸入資料行名稱直接加總，而是輸入另一個函數，來篩選  要加總的資料。
    
4.  在括弧之間輸入 **CALCULATE**，後面接著左括弧。
    
    您將透過我們傳遞給 CALCULATE 函數的引數，使用 CALCULATE 函數來篩選要加總的金額。 這就是所謂的巢狀函數。 CALCULATE 函數至少有兩個引數。 第一個引數是要評估的運算式，第二個引數是篩選條件。
   
5.  在 **CALCULATE** 函數的括弧 **()** 之間輸入 **Sales[SalesAmount]**。 這是 CALCULATE 函數的第一個運算式引數。
    
6.  鍵入逗號 (**,**) 以指定第一個篩選條件，然後鍵入 **PREVIOUSQUARTER**，後面接著左括弧。
    
    您將使用 PREVIOUSQUARTER 時間智慧函數，依上一季來篩選總和結果。
    
7.  在 PREVIOUSQUARTER 函式的括弧 **()** 之間鍵入 **Calendar[DateKey]**。
    
    PREVIOUSQUARTER 函數有一個引數，那就是包含連續日期範圍的資料行。
    >
    
8.  確定這兩個引數都已傳遞至 PREVIOUSQUARTER 函式，並以兩個左括弧 **))** 來結束 CALCULATE 函數。
    
   您的公式現在看起來應該像這樣：
    
    **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
9. 按一下公式列中的核取記號 ![](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) 或按 Enter 鍵，以驗證公式並將其加入模型。

大功告成！ 您剛才使用 DAX 建立的量值並不簡單。 這個公式將根據報表中套用的篩選條件來計算上一季的總銷售額。 例如，如果我們將 SalesAmount 和新的 Previous Quarter Sales 量值置於圖表中，再加入 Year 和 QuarterOfYear 做為交叉分析篩選器，則會得到類似下面的結果：

![](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

以上為您介紹了 DAX 公式的幾個重要層面。 首先，這個公式包含兩個函數。 請注意，[PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx) 時間智慧函數會以巢狀引數形式傳遞至 [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx) 篩選函數。 DAX 公式最多可以包含 64 個巢狀函數。 一個公式不大可能會包含這麼多的巢狀函數。 事實上，這類公式可能很難加以建立及偵錯，而且可能也不會太快。

在這個公式中，您也會使用篩選條件。 篩選條件可縮小要計算的範圍。 在本例中，您選取了一個篩選條件做為引數，實際上是另一個函數的結果。 稍後您將進一步了解篩選條件。

最後，您使用了 CALCULATE 函數。 這是 DAX 中最強大的函數之一。 當您撰寫模型並建立更複雜的公式時，可能會多次使用這個函數。 CALCULATE 函數不在本文討論範圍內，不過隨著您愈來愈了解 DAX，請特別注意這個函數。

### <a name="syntax-quickquiz"></a>語法快速測驗
1. 公式列上這個按鈕的功能為何？
   
   > ![](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. DAX 公式中的資料行名稱一律會用什麼括住？

本文結尾將提供解答。

### <a name="functions"></a>函數
函數是預先定義的公式，使用特定值和呼叫的引數，依特定順序或結構來執行計算。 引數可以是其他函數、另一個公式、運算式、資料行參考、數值、文字、TRUE 或 FALSE 等邏輯值，或常數。

DAX 包含下列函數類別：[日期和時間](https://msdn.microsoft.com/library/ee634786.aspx)、[時間智慧](https://msdn.microsoft.com/library/ee634763.aspx)[、](https://msdn.microsoft.com/library/ee634552.aspx)[資訊](https://msdn.microsoft.com/library/ee634552.aspx)、[邏輯](https://msdn.microsoft.com/library/ee634365.aspx)[、](https://msdn.microsoft.com/library/ee634365.aspx)[數學](https://msdn.microsoft.com/library/ee634241.aspx)、[統計](https://msdn.microsoft.com/library/ee634822.aspx)、[文字](https://msdn.microsoft.com/library/ee634938.aspx)、[父子式](https://msdn.microsoft.com/library/mt150102.aspx)和[其他](https://msdn.microsoft.com/library/mt150101.aspx)函數。 如果您熟悉 Excel 公式中的函數，DAX 中的許多函數看起來會很類似；不過，DAX 函數在下列方面是獨一無二的：

* DAX 函數一律會參考完整的資料行或資料表。 如果您只想使用某個資料表或資料行中的特定值，您可以將篩選條件加入公式。
* 如果您需要逐列自訂計算，DAX 提供函數，讓您使用目前的資料列值或相關值做為一種引數，以執行因內容而異的計算。 稍後您將進一步了解內容。
* DAX 包含許多會傳回資料表而不是值的函數。 該資料表不會顯示出來，但會用來提供其他函數的輸入。 例如，您可以擷取資料表，然後計算其中的相異值；或者計算所篩選的不同資料表或資料行的動態總和。
* DAX 包含各種時間智慧函數。 這些函數可讓您定義或選取日期範圍，並以此為依據來執行動態計算。 例如，您可以比較不同平行區間的總和。
* Excel 有一個非常受歡迎的函數 VLOOKUP。 不同於 Excel 的 VLOOKUP，DAX 函數不會以資料格或資料格範圍做為參考。 DAX 函數會以資料行或資料表做為參考。 請記住，在 Power BI Desktop 中，您會使用關聯式資料模型。 查閱另一個資料表中的值其實相當簡單，而且在大多數情況下，您完全不需要建立任何公式。
  
  如您所見，DAX 函數可協助您建立非常強大的公式。 我們其實只接觸到函數的基本概念。 隨著您愈來愈熟練 DAX，您將會使用許多不同的函數來建立公式。 [DAX 函數參考](https://msdn.microsoft.com/library/ee634396.aspx)是您進一步了解每個 DAX 函數的其中一個最佳地點。

### <a name="functions-quickquiz"></a>函數快速測驗
1. 函數一律會參考的項目為何？
2. 一個公式是否可以包含多個函數？
3. 您可以使用哪個函數類別將兩個文字字串串連成一個字串？

本文結尾將提供解答。

### <a name="context"></a>內容
內容是其中一項需要了解的重要 DAX 概念。 DAX 有兩種內容類型：資料列內容和篩選內容。 我們將先探討資料列內容。

**資料列內容**

最簡單的做法是將資料列內容想成目前的資料列。 每當公式有套用篩選條件以識別資料表中某一資料列的函數時，便適用此內容。 函數會套用所篩選之資料表中每個資料列的固有資料列內容。 這種類型的資料列內容最常應用於量值。

**篩選內容**

篩選內容比資料列內容稍微難理解。 最簡單的做法是將篩選內容想成：計算中用來決定一個結果或值所套用的一或多個篩選條件。

篩選內容並非原本就在資料列內容中，而是另外套用至資料列內容。 例如，若要進一步縮小要包含在計算中的值，您可以套用篩選內容，使該篩選內容不只指定資料列內容，也指定只使用該資料列內容中的特定值 (篩選條件)。

報表中經常會看到篩選內容。 例如，當您將 TotalCost 加入視覺效果，再加入 Year 和 Region 時，您所定義的篩選內容會根據指定的年份和地區來選取一小組資料。

篩選內容為什麼對 DAX 而言很重要？ 因為您不僅可以將欄位加入視覺效果中，不費吹灰之力就能套用篩選條件，也可以使用 ALL、RELATED、FILTER、CALCULATE 等函數，以及依關聯性、其他量值和資料行來定義篩選條件，以在 DAX 公式中套用篩選內容。 以 Store Sales 量值中的下列公式為例：

![](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

為了進一步了解這個公式，我們可以像是處理其他公式一樣將它分解。

這個公式包含下列語法元素：

**A.** 量值名稱 **Store Sales**。

**B.** 等號運算子 (**=**) 表示公式的開頭。

**C.** **CALCULATE** 函數會在指定篩選條件所修改的內容中，作為引數來評估運算式。

**D.** 括弧 **()** 會括住內含一或多個引數的運算式。

**E.** 同一個資料表中作為運算式的量值 [Total Sales]。 Total Sales 量值的公式為：=SUM(Sales[SalesAmount])。

**F.** 逗號 (**,**) 會隔開第一個運算式引數和篩選引數。

**G.** 完整的參考資料行 **Channel[ChannelName]**。 這是我們的資料列內容。 這個資料行中的每一個資料列各指定一個通路：Store、Online 等。

**H.** 以特定值 **Store** 作為篩選條件。 這是我們的篩選內容。

這個公式可確保只會針對以 “Store” 值為篩選條件的 Channel[ChannelName] 資料行中的資料列，計算 Total Sales 量值所定義的銷售額值。

您可以想像得到，能夠在公式內定義篩選內容是多麼龐大且強大的功能。 能夠只參考相關資料表中的特定值不過是其中一例。 如果您目前不完全了解內容，別擔心。 當您建立自己的公式時，您將進一步了解內容及其在 DAX 中很重要的原因。

### <a name="context-quickquiz"></a>內容快速測驗
1. 內容有哪兩種類型？
2. 什麼是篩選內容？
3. 什麼是資料列內容？

本文結尾將提供解答。

## <a name="summary"></a>摘要
在您對 DAX 中最重要的概念有了基本了解之後，即可開始建立 DAX 公式來處理自己的量值。 DAX 確實有點難了解，但有許多資源可供您使用。 讀完本文並實驗幾個自己的公式之後，您可以進一步了解可協助您解決自身商務問題的其他 DAX 概念和公式。 有許多 DAX 資源可供您使用；最重要的是[資料分析運算式 (DAX) 參考](https://msdn.microsoft.com/library/gg413422.aspx)。

DAX 在 Power Pivot 和 Analysis Services 表格式模型等其他 Microsoft BI 工具中已行之有年，因此有許多實用的資訊可用。 您可以在 Microsoft 和領先 BI 專業人員所提供的書籍、技術白皮書和部落格中找到更多資訊。 [TechNet 上的 DAX 資源中心 Wiki](http://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) 也是很好的起點。

### <a name="quickquiz-answers"></a>快速測驗解答
語法：

1. 驗證量值並將其輸入模型中。
2. 括號 []。

函數：

1. 資料表和資料行。
2. 是。 公式最多可以包含 64 個巢狀函數。
3. [文字函數](https://msdn.microsoft.com/library/ee634938.aspx)。

內容：

1. 資料列內容和篩選內容。
2. 計算中用來決定單一值的一或多個篩選條件。
3. 目前的資料列。

