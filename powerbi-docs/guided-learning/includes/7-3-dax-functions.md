---
ms.openlocfilehash: 06ee6ad7ade46d811c6340d905150c6dd3810c55
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273236"
---
使用 DAX，有許多函數可用於形成、塑造，或分析您的資料。 這些函數可分為數個類別︰

* **彙總**函數
* **計算**函數
* **邏輯**函數
* **資訊**函數
* **文字**函數
* **日期**函數

類似於 Excel，當您開始將公式輸入 Power BI Desktop **公式列**時，可用的函數清單隨即出現，協助您決定您想要選取哪些可用的函數。 您還可透過使用鍵盤上的**上**和**下**方向鍵，將任何可用的函數反白顯示，即會顯示一段簡短描述。

Power BI 會顯示符合您到目前為止輸入的字母的函數，因此如果您輸入 *S* ，只有 *S* 開頭的函數會出現在清單中。 如果您輸入 *Su* ，只有名稱中 *包含* *Su* 字母順序的函數會出現在清單中 (函數不需要以 *Su* 開頭，其只需要包含該字母順序)。

![](media/7-3-dax-functions/dax-functions_1.png)

可以輕易以此方式試驗 DAX，並找出 Power BI 中可用的各種 DAX 函數。 您只需要開始輸入，Power BI 就會協助您順利進行。

既然我們已經知道如何啟動該 DAX 公式，我們應該逐一看看這些函數類別。

## <a name="aggregation-functions"></a>彙總函數
DAX 擁有若干**彙總**函數，包括下列常用函數︰

* SUM
* AVERAGE
* MIN
* MAX
* SUMX (和其他 *X* 函數)

這些函數只能用於數值資料行，且通常一次只能彙總一個資料行。

不過，以 **X** 結尾的特殊彙總函數，例如 **SUMX**，可以處理多個資料行。 這些函數會逐一查看資料表，並評估每個資料列的運算式。

## <a name="counting-functions"></a>計算函數
DAX 中常用的**計算**函數包括下列︰

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

這些函數會計算不同的項目，例如相異值、非空白值及資料表的資料列。

## <a name="logical-functions"></a>邏輯函數
DAX 中的**邏輯**函數集合包括︰

* AND
* OR
* NOT
* IF
* IFERROR

這些特殊函數也可以使用運算子表示。  例如，您 DAX 公式中的 **AND** 可以輸入為 (取代為) **&&** 。

當您的公式需要兩個以上的條件時，您可以使用運算子 (例如 **&&** )，否則，為了您的 DAX 碼的可讀性，使用函數本身的名稱是最佳做法 (例如 **AND**)。

## <a name="information-functions"></a>資訊函數
DAX 中的**資訊**函數包括︰

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

雖然這些函數可能在特定方面很有用，但事先知道您資料行中的資料類型仍有其價值，而不是依賴這些函數來提供資料類型。

DAX 會使用 MAX 和 MIN 函數彙總並比較值。    

## <a name="text-functions"></a>文字函數
DAX 中的**文字**函數包括下列︰

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

這些**文字**與相同名稱的 Excel 函數的作用非常雷同，因此如果您熟悉 Excel 如何處理文字函數，您已經超前一步。 若否，您隨時都可以在 Power BI 中試驗這些函數，並深入了解其行為。

## <a name="date-functions"></a>日期函數
DAX 包括下列**日期**函數︰

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

雖然這些函數用來計算和擷取日期值的資訊很實用，他們並不適用於使用日期資料表的時間智慧。 

> 影片內容感謝下列提供者的協助 [Alberto Ferrari、SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

