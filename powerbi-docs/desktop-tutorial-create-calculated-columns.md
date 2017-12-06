---
title: "教學課程：在 Power BI Desktop 中建立您自己的導出資料行"
description: "教學課程：在 Power BI Desktop 中建立您自己的導出資料行"
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
ms.openlocfilehash: 9ea93980a095ca4e626b6f8071d044448af59635
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>教學課程：在 Power BI Desktop 中建立您自己的導出資料行
有時候您分析中的資料，恰好未包含想取得結果的特定欄位。 這是 [計算結果欄] 所在之處。 計算結果欄使用資料分析運算式 (DAX) 公式，藉此定義資料行的值。 這些值可以與任何項目有關，可以是放在一起的文字值，來自模型中其他位置的幾個不同資料行，或者可以是從其他值計算所得的數值。 例如，假設您的資料具有 [城市] 與 [縣市] 的資料行 (像是在欄位清單中的欄位)，但您要的是單一 [位置] 欄位，是同時具有兩者的單一值，例如佛羅里達州邁阿密。 這正是計算結果欄的目的。

計算結果欄類似於兩者根據 DAX 公式所計算的量值，但它們所使用的方式又不同。 在視覺效果的 [值] 區域最常使用量值，藉此根據您在資料表中資料列的其他欄位，或根據視覺效果的 [軸]、[圖例] 或 [群組] 區域，來計算結果。 另一方面，當您需要在資料表上的資料列、或在 [軸]、[圖例] 或 [群組] 區域中資料行的結果時，便會使用計算結果欄。

本教學課程將引導您了解，並在 Power BI Desktop 中建立一些您自己的計算結果欄。 本文適用於已經熟悉使用 Power BI Desktop，用來建立更進階模型的 Power BI 使用者。 您應該已經很熟悉使用 [查詢] 匯入資料、使用多個相關資料表，以及將欄位加入報表畫布。 如果您剛開始使用 Power BI Desktop，請務必參閱[開始使用 Power BI Desktop](desktop-getting-started.md)。

若要完成本教學課程中的步驟，您將需要下載 [Power BI Desktop 的 Contoso 銷售範例](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip)檔案。 這是[在 Power BI Desktop 中建立您自己的量值](desktop-tutorial-create-measures.md)教學課程中所使用的相同範例檔案。 它已經包含虛構公司 Contoso, Inc. 的銷售資料。因為檔案中的資料是從資料庫所匯入，所以您無法連接到資料來源或在查詢編輯器中檢視。 當您自己的電腦上具備此檔案時，請直接在 Power BI Desktop 中開啟它。

## <a name="lets-create-a-calculated-column"></a>讓我們來建立計算結果欄
假設我們想要在資料列的單一值中，顯示產品類別目錄與產品子類別目錄，例如行動電話 – 配件、行動電話 – 智慧型手機和 PDA 等等。 在 [報表檢視] 或 [資料檢視] \(我們這裡使用 [報表檢視])，如果我們查看 [欄位] 清單中的產品資料表，就會發現提供的欄位不是我們要的欄位。 不過，我們確實有 [ProductCategory] 和 [ProductSubcategory] 欄位，各自位於其自己的資料表中。

 ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_nonewcol.png)

我們將建立新的計算結果欄，將這兩個資料行的值結合成新資料行的新值。 有趣的是，我們需要將兩個不同資料表的資料結合成單一資料行。 因為我們將使用 DAX 來建立新的資料行，所以我們可以充分利用既有模型的功能，包括現有不同資料表之間的關聯性。

### <a name="to-create-a-productfullcategory-column"></a>建立 [ProductFullCategory] 資料行
1.  以滑鼠右鍵按一下，或按一下 [欄位] 清單中的 [ProductSubcategory] 資料表向下箭號，然後按一下 [新增資料行]。 這樣可確保將我們新的資料行加入 [ProductSubcategory] 資料表。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumn.png)
    
    報表畫布或資料格上方會出現公式列。 我們可以在其中將資料行重新命名，並輸入 DAX 公式。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumnformula.png)
    
    根據預設，新的計算結果欄名稱就是「資料行」。 如果我們沒有重新命名，則當我們建立另一個量值時，它就會命名為資料行 2、資料行 3，依此類推。 我們會想要讓資料行更容易識別，所以會將新的資料行重新命名。
    
2.  因為 [資料行] 名稱已反白顯示在公式列中，所以只要輸入 **ProductFullCategory**。
    
    現在我們可以開始輸入公式。 我們想要新資料行中的值開頭為 [ProductCategory] 資料表中的 [ProductCategory] 名稱。 因為這個資料行位於不同但相關的資料表中，所以我們要使用 [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) 函數來幫助我們取得資料行。
    
3.  在等號後面輸入 **R**。您會看到下拉式建議清單隨即出現，列出所有開頭字母為 R 的 DAX 函數。當我們輸入更多字母，建議清單就更能調整至接近我們所需的函數。 在函數旁可看到函數的描述。 向下捲動以選取 [RELATED]，然後按 Enter 鍵。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_1.png)
    
    左括弧隨即出現，並出現另一個建議清單，其中有我們可傳遞至 RELATED 函數的可用資料行。 同時也顯示預期參數的描述和詳細資訊。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_2.png)
    
    運算式一律出現在左右括弧之間。 在此情況下，我們的運算式將包含傳遞至 RELATED 函數的單一引數；也就是要從中傳回值的相關資料行。 資料行清單會自動縮小範圍，以便只顯示相關資料行。 在此情況下，我們想要的是在 [ProductCategory] 資料表的 [ProductCategory] 資料行。
    
    選取 [ProductCategory [ProductCategory]] ，然後輸入右括弧。
    
    > [!TIP]
    > 語法錯誤通常因遺失或錯置右括弧所導致。 但如果您忘記，Power BI Desktop 通常會加入右括弧。
    > 
    > 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_3.png)
    
4. 我們想要新增虛線符號來分隔每個值，因此請在第一個運算式的右括號之後，輸入空格、& 符號、引號、空格、虛線 (-)、另一個空格、右引號和另一個 & 符號。 您的公式現在看起來應該像這樣：
    
    **ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &**
    
    > [!TIP]
    > 按一下公式列右側的向下Ｖ形箭號，以展開工式編輯器。 按 Alt 鍵和 Enter 下移一行，然後按 Tab 來移動項目。
    > 
    > 
    
5.  最後，輸入另一個左括弧，然後選取 **[ProductSubcategory]** 資料行以完成公式。 您的公式看起來應該像這樣：
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_5.png)
    
    您會發現我們在呼叫 [ProductSubcategory] 資料行的第二個運算式中並未使用另一個 RELATED 函數。 這是因為這個資料行所在的資料表，與我們建立新資料行的資料表相同。 我們可以輸入 [ProductCategory]，包含資料表名稱 (完整名稱) 或不含 (非限定)。
    
6.  按下 Enter 或在公式列中按一下核取記號以完成公式。 公式會進行驗證並加入 [ProductSubcategory]  資料表中的欄位清單。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_6.png)
    
    您會發現在欄位清單中計算結果欄具有特殊的圖示。 這顯示出它們包含公式。 在 Power BI Desktop 的外觀就只會如此顯示。 PowerBI 服務 (Power BI 網站) 中沒有變更公式的方式，所以計算結果欄欄位不會有圖示。
    
## <a name="lets-add-our-new-column-to-a-report"></a>讓我們在報表中加入新的資料行
現在我們可以將新的 [ProductFullCategory] 資料行加入報表畫布。 讓我們依 [ProductFullCategory] 查看 [SalesAmount]。

將 [ProductFullCategory]  資料行從 [ProductSubcategory]  資料表拖曳至報表畫布，然後將 [SalesAmount]  欄位從 [Sales]  資料表拖曳至此圖表。

![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_report_1.png)

## <a name="lets-create-another"></a>讓我們來建立另一個計算結果欄
您現在知道如何建立計算結果欄，讓我們來建立另一個。

Power BI Desktop 的 Contoso Sales 範例模型包含營運中和非營運中商店的銷售資料。 我們希望將針對非營運中商店所顯示的資料清楚識別出來。 事實上，我們需要名為 Active StoreName 的欄位。 若要這樣做，我們要建立另一個資料行。 在此情況下，如果商店非營運中，我們要新的 [Active StoreName] 資料行 (做為欄位) 將此商店的名稱顯示為「非營運中」，但是當其為營運中的商店時，則顯示商店的實際名稱。

幸好 [Store] 資料表有名為 [Status] 的資料行，如果商店為營運中，其值為 On，如果商店為非營運中，其值為 Off。 我們可以測試 [Status] 資料行中每個資料列的值，藉此在新的資料行中建立新的值。

### <a name="to-create-an-active-storename-column"></a>建立 [Active StoreName] 資料行
1.  在 [Store] 資料表建立新的計算結果欄，名為 **Active StoreName**。
    
    在這個資料行中，我們的 DAX 公式會檢查每間商店的狀態。 如果商店狀態是 On，則我們的公式會傳回商店名稱。 如果是 Off，則名稱為「非營運中」。 若要這樣做，我們將使用邏輯 [IF](https://msdn.microsoft.com/library/ee634824.aspx) 函數，若結果為 True 或 False，則會測試商店狀態，然後傳回特定的值。
    
2.  開始輸入 **IF**。 建議清單會顯示我們可以加入的項目。 選取 [IF] 。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_1.png)
    
    IF 的第一個引數是邏輯測試。 我們想要測試商店狀態是否為 “On”。
    
3.  輸入左括號 **[**，可以讓我們從 [Store] 資料表選取資料行。 選取 [Status] 。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_2.png)
    
4.  在 [Status] 後緊接著輸入 **="On"**，然後輸入逗號 (**,**)，以輸入第二個引數。 工具提示會建議我們，需要加入當結果為 True 時的值。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_3.png)
    
5.  如果商店是 On，我們想要顯示此商店名稱。 輸入左括號 **[** ，並選取 [StoreName]  資料行，然後輸入另一個逗號，讓我們可以輸入第三個引數。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step5.png)
    
6.  我們需要加入當結果為 False 時的值，在此情況下我們想要這個值為 **“Inactive”**。
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step6.png)
    
7.  按下 Enter 或在公式列中按一下核取記號以完成公式。 公式會進行驗證並加入 [Stores] 資料表中的欄位清單。
    
    就像任何其他欄位，我們可以在視覺效果使用新的 [Active StoreName] 資料行。 在此圖中，狀態為 On 的商店會各自依名稱顯示，但會將狀態為 Off 的商店分在同一組，並顯示為非營運中。 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_viz.png)
    
## <a name="what-weve-learned"></a>我們所學的內容
計算結果欄可以充實我們的資料，並且更易於了解。 我們學到如何使用公式列建立計算結果欄、如何使用建議清單，以及如何為新的資料行命名最合適的名稱。

## <a name="next-steps"></a>後續步驟
如果您想要深入剖析 DAX 公式，並使用更進階的 DAX 公式建立計算結果欄，請參閱 [Power BI Desktop 的 DAX 基本概念](desktop-quickstart-learn-dax-basics.md)。 本文著重在 DAX 中的基本概念，例如語法、函數，並且更徹底了解內容。

請務必將[資料分析運算式(DAX) 參考](https://msdn.microsoft.com/library/gg413422.aspx)加入我的最愛中。 您可以在此找到 DAX 語法、運算子和超過 200 種 DAX 函數的詳細資訊。

