---
title: 教學課程：在 Power BI Desktop 中建立您自己的量值
description: 教學課程：在 Power BI Desktop 中建立您自己的量值
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 306738f4df765638c591c9612adf885facdceda0
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65513859"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>教學課程：在 Power BI Desktop 中建立您自己的量值
您可以在 Power BI Desktop 中使用量值來建立一些最強大的資料分析方案。 當您與報表互動時，量值會在您的資料上執行計算，藉此提供協助。 本教學課程將引導您了解量值，並在 Power BI Desktop 中建立自己的基本量值。

### <a name="prerequisites"></a>先決條件
- 本教學課程適用於已經熟悉使用 Power BI Desktop，用來建立更進階模型的 Power BI 使用者。 您應該已經很熟悉使用 [取得資料] 和 [查詢編輯器] 匯入資料、使用多個相關資料表，以及將欄位加入報表畫布。 如果您剛開始使用 Power BI Desktop，請務必參閱[開始使用 Power BI Desktop](desktop-getting-started.md)。
  
- 下載[適用於 Power BI Desktop 的 Contoso 銷售範例](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip)檔案，其中包含虛構公司 Contoso, Inc. 的線上銷售資料。此資料是從資料庫匯入，因此您無法連線到該資料來源或在 [查詢編輯器] 中檢視它。 在您自己的電腦上將此檔案解壓縮，然後在 Power BI Desktop 中開啟它。

## <a name="understand-measures"></a>了解量值

量值最常為您自動建立。 在 Contoso 銷售範例檔案中，於 [欄位] 中選取 **Sales** 資料表 **SalesAmount** 欄位旁的核取方塊，或將 **SalesAmount** 拖曳至報表畫布。 新的資料行圖表視覺效果隨即出現，並顯示 Sales 資料表之 SalesAmount 資料行中所有值的總和。

![SalesAmount 圖表](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

出現在 [欄位] 中具有標準差圖示 ![標準差圖示](media/desktop-tutorial-create-measures/meastut_sigma.png) 的任何欄位均為數值，其值可加以彙總。 Power BI Desktop 會偵測到一個數值資料類型並自動建立和計算量值來彙總資料，而不會顯示一個含有所有兩百萬筆 SalesAmount 值的資料表。 總和是數值資料類型的預設彙總，但您可以輕鬆地套用不同的彙總，例如平均或計數。 了解彙總是了解量值的基礎，因為每個量值都會執行某種類型的彙總。 

若要將圖表彙總變更為平均，在 [視覺效果] 窗格的 [值] 區域中，按一下 **SalesAmount** 旁的向下箭號，然後選取 [平均]。 視覺效果會變更為 SalesAmount 欄位中所有銷售值的平均。

![SalesAmount 平均圖表](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

您可以根據想要的結果來變更彙總類型，但並非所有類型的彙總都可套用至每一個數值資料類型。 例如，對於 SalesAmount 欄位而言，總和與平均具有意義。 最小值和最大值也有其意義。 但是計數對於 SalesAmount 欄位而言並沒有多大意義，原因在於雖然其值為數值，但它們其實是貨幣。

從量值計算得來的值會隨著您與報表的互動而變更。 例如，將 **RegionCountryName** 欄位從 **Geography** 資料表拖曳至圖表，就會顯示每個國家/地區的平均銷售金額。

![依國家/地區顯示的 SaleAmount](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

當量值的結果因為與您的報表互動而變更時，就會影響到量值的「內容」。 每次您與報表視覺效果互動時，就會變更量值計算並顯示其結果的內容。

## <a name="create-and-use-your-own-measures"></a>建立和使用自己的量值

在大部分情況下，Power BI 會依據您選擇的欄位和彙總類型自動計算並傳回值，但在某些情況下，您可能想要建立自己的量值來執行更複雜且獨特的計算。 有了 Power BI Desktop，您就可以使用資料分析運算式 (DAX) 公式語言來建立自己的量值。 

DAX 公式使用許多與 Excel 公式相同的函數、運算子和語法。 不過，當您與報表互動時，DAX 函數主要用來處理關聯式資料，以及執行更加動態的計算。 有超過 200 種 DAX 函數可執行各種計算，從像是總和與平均的簡單彙總，到更複雜的統計和篩選函數皆有。 有許多資源可以協助您深入了解 DAX。 當您完成本教學課程之後，請務必參閱 [Power BI Desktop 的 DAX 基本概念](desktop-quickstart-learn-dax-basics.md)。

當您建立自己的量值時，就會將它新增至所選取資料表的 [欄位] 清單中，並稱為「模型」量值。 模型量值的部分優點是，您可以使用任何想要的名稱來為其命名，使其更容易識別；您可以使用它們作為其他 DAX 運算式中的引數；而且您可以讓它們非常快速地執行複雜的計算。

>[!TIP]
>從 Power BI Desktop 的 2018 年 2 月版本開始，許多常用計算都可用來作為**快速量值**，其會根據您在對話方塊中的輸入來撰寫 DAX 公式。 這些快速且功能強大的計算也很適合用於學習 DAX 或植入您自己的自訂量值。 若要建立或探索快速量值，在資料表的 [更多選項] 清單中，或功能區 [常用] 索引標籤中的 [計算] 下方，選取 [新增快速量值]。 如需建立及使用快速量值的詳細資訊，請參閱[使用快速量值](desktop-quick-measures.md)。

### <a name="create-a-measure"></a>建立量值

您想要藉由從總銷售金額中減去折扣和退貨來分析淨銷售額。 針對任何存在於您視覺效果中的內容，您需要會從 SalesAmount 總和減去 DiscountAmount 和 ReturnAmount 總和的量值。 [欄位] 清單中沒有任何適用於淨銷售額的欄位，但是您可以使用建置組塊來建立自己的量值，以計算淨銷售額。 

1.  以滑鼠右鍵按一下 [欄位] 中的 **Sales** 資料表，或將滑鼠停留在該資料表並選取**更多選項**省略符號 (...)，然後選取 [新增量值]。 這樣會將您的新量值儲存於 Sales 資料表中，在那裡將會比較容易找到。
    
    ![新增量值](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    您也可以在 Power BI Desktop 功能區 [常用] 索引標籤上的 [計算] 群組中選取 [新增量值]，藉以建立新的量值。
    
    ![從功能區新增量值](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >當您從功能區建立量值時，可在任何資料表中建立它，但是如果您在打算使用它的地方建立它，將會更容易找到它。 在此案例中，先選取 Sales 資料表以使其呈現作用中狀態，然後選取 [新增量值]。 
    
    公式列會出現在報表畫布上方，您可以在其中將量值重新命名，並輸入 DAX 公式。
    
    ![公式列](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
2.  根據預設，新的量值名稱就是 Measure。 如果您未將它重新命名，其他的新量值將會命名為 Measure 2、Measure 3，依此類推。 您會希望量值更容易識別，因此可在公式列中反白顯示 **Measure**，然後輸入 **Net Sales**。
    
3.  現在您可以開始輸入公式。 在等號之後，開始輸入 **Sum**。 當您輸入時，下拉式建議清單隨即出現，其中會顯示以您所輸入字母開頭的所有 DAX 函數。 視需要向下捲動，以便從清單中選取 **SUM**，然後按 Enter 鍵。
    
    ![選擇 SUM](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    左括弧隨即出現，並出現另一個下拉式建議清單，其中包含您可傳遞至 SUM 函數的所有可用資料行。
    
    ![選擇資料行](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    運算式一律會出現在左右括弧之間。 您的運算式將包含要傳遞至 SUM 函數的單一引數：SalesAmount 資料行。 開始輸入 "SalesAmount"，直到清單中只剩一個值為止：Sales(SalesAmount)。 前面加上資料表名稱的資料行名稱會稱為資料行的「完整格式名稱」。 完整格式的資料行名稱可讓您的公式更容易閱讀。 
    
    ![選取 SalesAmount](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
4. 選取 [Sales [SalesAmount]]，然後鍵入右括弧。
    
    > [!TIP]
    > 語法錯誤通常因遺失或錯置右括弧所導致。
    
    
    
5.  減去其他兩個資料行：
    1. 在第一個運算式的右括弧之後，依序輸入一個空格、一個減號運算子 (**-**) 及另一個空格。 
    2. 輸入另一個 SUM 函數，並開始輸入 "DiscountAmount"，直到您可以選擇 **Sales[DiscountAmount]** 資料行作為引數為止。 加上右括號。 
    3. 依序輸入一個空格、另一個減號運算子、空格、另一個含有 **Sales[ReturnAmount]** 作為引數的 SUM 函數及右括號。
    
    ![完成公式](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
6.  按下 Enter 鍵或按一下公式列中的核取記號，以完成並驗證公式。 經過驗證的量值現在已準備好在 Sales 資料表的欄位清單中使用。 
    
    ![欄位清單中的量值](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
如果您沒有空間可輸入公式，或者想要使其位於個別行上，請選取公式列右側的向下＞形箭號，以開啟更多空間。

![公式的＞形箭號](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

您可以按下 **Alt-Enter** 鍵來將公式的各個部分分隔於不同行上，或使用 **Tab** 鍵來移動各個部分。

![展開的公式](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>在報表中使用您的量值
現在您可以將 Net Sales 量值加入至報表畫布，並依據您加入至報表的任何其他欄位來計算淨銷售額。 依國家/地區查閱淨銷售額：

1. 從 **Sales** 資料表選取 **Net Sales** 量值，或將它拖曳至報表畫布。
    
2. 從 **Geography** 資料表選取 **RegionCountryName** 欄位，或將它拖曳至圖表。
    
    ![依國家/地區顯示的淨銷售額](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
若要依國家/地區查看淨銷售額與總銷售額之間的差異，請選取 **SalesAmount** 欄位，或將它拖曳至圖表。 

![依國家/地區顯示的銷售額和淨銷售額](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

圖表現在會使用兩個量值：已自動加總的 SalesAmount，和您建立的 Net Sales 量值。 每個量值都會在另一個欄位 (RegionCountryName) 的內容中加以計算。
    
### <a name="use-your-measure-with-a-slicer"></a>搭配交叉分析篩選器使用量值

您可以加入交叉分析篩選器，依日曆年度進一步篩選淨銷售額與銷售額。
    
1.  按一下圖表旁邊的空白區域，然後在 [視覺效果] 中選取 [資料表] 視覺效果。 這會在報表畫布上建立空白的資料表視覺效果。
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
2.  將 **Year** 欄位從 **Calendar** 資料表拖曳至新的空白資料表視覺效果。 因為 Year 是數值欄位，所以 Power BI Desktop 會加總其值，但對其進行彙總並無太大意義。 
    
    ![Year 彙總](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3.  在 [視覺效果] 窗格的 [值] 中，選取 **Year** 旁的向下箭號，然後選取 [不摘要]。 資料表現在會列出個別年度。
    
    ![不摘要](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  在 [視覺效果] 窗格中選取**交叉分析篩選器**圖示，將資料表轉換成交叉分析篩選器。

    ![變更為交叉分析篩選器](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  選取 **Year** 交叉分析篩選器中的任何值，據以篩選**依國家/地區顯示的淨銷售額與銷售金額**圖表。 Net Sales 和 SalesAmount 量值會重新計算，並在所選取 Year 欄位的內容中顯示結果。 
    
    ![依 Year 配量的圖表](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>在另一個量值中使用您的量值

您想要了解哪些產品在售出的每個單位中具有最高的淨銷售額，因此您需要一個使用淨銷售額除以已售出單位數量的量值。 您可以建立新的量值，其會使用 Net Sales 量值的結果除以 Sales[SalesQuantity] 的總和。

1.  在 Sales 資料表中建立名為 **Net Sales per Unit** 的新量值。
    
2.  在公式列中，開始輸入 **Net Sales**。 建議清單將會顯示您可以加入的項目。 選取 **Net Sales**。
    
    ![使用 Net Sales 的公式](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    只要輸入左括號 (**[**)，您也能參考量值。 建議清單將只會顯示要加入至您公式的量值。
    
    ![括號只會顯示量值](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  依序輸入一個空格、除法運算子 (**/**)、另一個空格、SUM 函數，然後輸入 **Quantity**。 建議清單會顯示名稱中具有 Quantity 的所有資料行。 選取 **Sales[SalesQuantity]**、輸入右括號，然後按 ENTER 鍵或選取核取記號來驗證您的公式。 公式看起來應該像這樣：
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
4. 從 Sales 資料表選取 **Net Sales per Unit** 量值，或將它拖曳至報表畫布中的空白區域。 圖表會顯示已售出的所有產品中每個單位的淨銷售額，其資訊價值不高。 
    
    ![每個單位的整體淨銷售額](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
5. 如需不同外觀，請將圖表視覺效果類型變更為 **樹狀圖**。
    
    ![變更為樹狀圖](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. 選取 **Product Category** 欄位，或者將它拖曳至樹狀圖或 [視覺效果] 窗格的 [群組] 欄位。 現在您擁有一些良好資訊！
    
    ![依產品類別顯示的樹狀圖](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. 嘗試移除 **ProductCategory** 欄位，並改為將 **ProductName** 欄位拖曳至圖表。 
    
    ![依產品名稱顯示的樹狀圖](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
好，現在我們只是熱身而已，但您必須承認，這很酷！ 使用其他方式進行實驗來篩選視覺效果並加以格式化。

## <a name="what-youve-learned"></a>您學到的內容
量值讓您有充分的動力，能夠從資料中取得所需的深入資訊。 您已經學會如何使用公式列建立量值、為它們指定任何最有意義的名稱，以及使用 DAX 建議清單來尋找和選取右邊的公式元素。 您也已經了解內容，其中量值的計算結果會根據其他欄位或公式中的其他運算式進行變更。

## <a name="next-steps"></a>後續步驟
- 若要深入了解 Power BI Desktop 快速量值 (可為您提供多個常用的量值計算)，請參閱[使用快速量值，輕鬆執行常用及功能強大的計算](desktop-quick-measures.md)。
  
- 如果您想要深入剖析 DAX 公式並建立某些更進階的量值，請參閱 [Power BI Desktop 的 DAX 基本概念](desktop-quickstart-learn-dax-basics.md)。 本文著重在 DAX 中的基本概念，例如語法、函數，並且更徹底了解內容。
  
- 請務必將[資料分析運算式(DAX) 參考](https://msdn.microsoft.com/library/gg413422.aspx)加入我的最愛中。 您可以在此找到 DAX 語法、運算子和超過 200 種 DAX 函數的詳細資訊。

