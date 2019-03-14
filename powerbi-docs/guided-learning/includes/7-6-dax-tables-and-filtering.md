---
ms.openlocfilehash: d7f30dd43fe875380939520f3dc54fcbbe2f4c9c
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555963"
---
**DAX** 及 Excel 公式語言之間的一個重大差異，是 DAX 可讓您在運算式之間傳遞 *整個資料表* ，而不是限制在單一值。 其中一個功能強大的作用是 DAX 可讓您在其運算式中篩選資料表，然後使用已篩選的一組值。

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

使用 DAX，您可以建立全新的計算資料表，然後將其視為任何其他資料表，包括建立其和您資料模型中其他資料表的關聯性。

## <a name="dax-table-functions"></a>DAX 資料表函數
DAX 擁有一組豐富的**資料表**函數，包括下列︰

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

這些函式會傳回完整資料表，而不是值。 通常您會將**資料表**函數的結果用在更高的運算式中進行進一步分析，而非將傳回的資料表當作終值。 請特別注意，當您使用資料表函數時，結果會繼承其資料行之間的關聯性。

只要每一個函數都使用資料表並傳回資料表，您便可以在運算式中混合資料表函數。 例如，以下列 DAX 運算式為例︰

    FILTER (ALL (Table), Condition)

運算式會將篩選套用至整個 *資料表* ，並忽略任何目前篩選內容。

DISTINCT 函數會針對目前內容中亦可見的資料行，傳回該資料行的相異值。 因此若要使用上述的 DAX 運算式範例，在該運算式中使用 **ALL** 會忽略篩選，而以 **DISTINCT** 取代 **ALL** 則會加以遵守。

## <a name="counting-values-with-dax"></a>使用 DAX 計算值
其中一項 Power BI 報表產生器要回答的常見問題如下︰

* 此資料行有多少值？

當資料表顯示在面前時這可能是個簡單的問題，但 DAX 以不同的方式處理，特別是當資料表之間有關連性時。

例如，Power BI 和 DAX 會包含未正確相互檢索的值。 如果內送關聯性已損毀，DAX 會將新的資料列新增至每個欄位皆為空白的相關資料表中，並將該新資料列連結至未編製索引的資料列，以確保參考完整性。 如果您的函數包含空白資料列，例如，通常是在使用 **ALL** 時，該等空白資料列就會包括在為該資料行傳回的值數目中。

您也可以使用 DAX 函數建立整個計算資料表。 使用 DAX 建立的計算資料表都需要 **NAME** 和 **TABLE** 函數。 計算資料表可像任何其他資料表般使用，包括建立關聯性。

> 影片內容感謝下列提供者的協助 [Alberto Ferrari、SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

