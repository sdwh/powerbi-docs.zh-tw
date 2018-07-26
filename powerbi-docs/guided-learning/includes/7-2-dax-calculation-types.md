您可以使用 DAX 來建立兩種主要的計算結果︰

* **計算結果欄**
* **導出量值**

在深入探討建立任何計算結果之前，最好能確實掌握資料表和資料行的 DAX 語法，您在建立**計算結果欄**或**導出量值**時會使用此等語法。

## <a name="dax-table-and-column-name-syntax"></a>DAX 資料表和資料行名稱語法
無論您是建立新的資料行或量值，皆請務必了解 DAX 中資料表名稱的一般格式︰

    'Table Name'[ColumnName]

如果資料表名稱中有空格 (如上所示)，資料表名稱必須強制括上單引號。 如果資料表名稱不包含任何空格，可以省略單引號，因此語法看起來如下所示︰

    TableName[ColumnName]

下圖顯示正在 Power BI 中建立 DAX 公式︰

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

您也可以完全省略資料表名稱，並只使用資料行名稱，但這對於撰寫清楚的函數 (以及清楚的 DAX 碼) 而言是不良做法。 資料行名稱必須一律包含方括弧。

最佳做法是一律執行下列動作︰

* 資料表名稱中不含空格
* 一律將資料表名稱包含在公式中 (即使 DAX 允許您加以省略，也不要這麼做)

## <a name="creating-calculated-columns"></a>建立計算結果欄
當您想要分割或篩選值，或如果您想要計算您的資料表中的每個資料列時，**計算結果欄**很有用。

您也可以透過選取 [模型] 索引標籤中的 [新增資料行]，在 Power BI Desktop 中建立計算結果欄。最好位於 [資料] 檢視 (而非 [報表] 或 [關聯性]檢視)，因為您可以看到新建立的資料行，且 [公式列] 已填入並可用於您的 DAX 公式。

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

一旦您選取 [新的資料行] 按鈕，[公式列] 會填入基本資料行名稱 (當然，您會變更此名稱以符合您的公式) 與 **=** 運算子，而新的資料行會出現在資料格中，如下圖所示。

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

計算結果欄所需的項目如下所示︰

* 新的資料行名稱
* 至少一個函數或運算式

如果您在計算結果欄公式中參考資料表或資料行，您並不需要指定資料表中的資料列，Power BI 每次計算都會計算目前資料列的資料行。

## <a name="creating-calculated-measures"></a>建立導出量值
當您在計算百分比或比例，或當您需要複雜彙總時，使用**導出量值**。 使用 DAX 公式建立量值時，請選取 [模型] 索引標籤中的 [新增量值] 按鈕。同樣地，最好位於 Power BI Desktop 的 [資料] 檢視，因為其會顯示 [公式列]，並可讓您更輕易地撰寫 DAX 公式。

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

使用**量值**，您會看到帶有量值名稱的新量值圖示出現在 [欄位] 窗格中。 **公式列**也會填入您的 DAX 公式名稱 (這次是您的量值)。

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

導出量值的必要項目與計算結果欄相同：

* 新的量值名稱
* 至少一個函數或運算式

> 影片內容感謝下列提供者的協助 [Alberto Ferrari、SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

