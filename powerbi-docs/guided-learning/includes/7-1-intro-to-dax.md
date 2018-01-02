歡迎使用專為您介紹 **DAX** 而設計的 Power BI **引導式學習**一節。

**DAX** 代表**資料分析運算式**，且其是 Power BI 所使用的公式語言 (Power BI 也會在幕後加以使用)。 在 Microsoft 的其他供應項目中也可以找到 DAX，例如 Power Pivot 和 SSAS Tabular，但本引導式學習的主題集合聚焦在 DAX 在 Power BI 中的使用方式，以及您可以如何加以使用。

## <a name="dax-and-this-guided-learning-video-series"></a>DAX 和此引導式學習影片系列
本**引導式學習**一節的目標是教導您 DAX 的基本知識和基本概念，包括如何看待 DAX、其運作方式，以及由知名 DAX 專家 [Alberto Ferrari](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit) 所說明 (與透過眾多經驗所學習) 的最實用功能。

![Alberto Ferrari 的相片](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

本**引導式學習**一節中有關 **DAX** 的影片，從 DAX 公式語言運作方式的觀點教導您 DAX 的基本知識。 從頭建立 DAX 公式時，這相當實用，但同時非常適合您在**查詢編輯器**中建立查詢時了解 Power BI 如何建立該等 DAX 公式。

## <a name="in-this-video---introduction-to-dax"></a>本影片內容 - DAX 簡介
DAX 概念既簡單又直接，同時功能強大。 DAX 使用獨特的程式設計概念和模式，要完整加以使用及理解有相當的難度。 傳統的語言學習方式可能不適用於 DAX，因此本影片的目標在於教導您有助於您稍後的 Power BI 工作的概念以及理論。

DAX 是 *功能語言* ，這表示完整執行的程式碼包含在函數中。

在 DAX 中，函數可以包含其他巢狀函數、條件陳述式以及值的參考。 DAX 中的執行始於最內層的函數或參數，並向外運作。 在 Power BI 中，DAX 公式會以單一行撰寫，因此正確地將函數格式化對可讀性而言相當重要。

DAX 設計用於資料表，因此僅有兩個主要資料類型：**Numeric** 及 **Other**。 **Numeric** 可包含 *整數* 、 *小數* ，以及 *貨幣* 。 **Other** 可包含 *字串* 和 *二進位物件* 。 這表示，如果您將 DAX 函數建置為使用一種類型的數字，您得以確保其能夠用於任何其他 Numeric 資料。

DAX 會使用運算子多載，這表示您可以在計算中混合資料類型，而結果將會依據輸入中所使用的的資料類型變更。 轉換會自動執行。 雖然這表示您不必知道您在 Power BI 中所使用的資料行資料類型，但這也表示轉換有時可能會以非預期的方式發生。 最佳做法是了解您所使用的資料，以確保運算子的表現符合預期。

在 Power BI 中，尤有一項資料類型您可能會經常使用︰**DateTime**。 **DateTime** 會以浮點值的方式儲存，包含整數與小數部分。 DateTime 可用於精確地計算任何 1900 年 3 月 1 日之後的時間週期。

> 影片內容感謝下列提供者的協助 [Alberto Ferrari、SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

