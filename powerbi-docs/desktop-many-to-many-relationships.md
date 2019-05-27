---
title: Power BI Desktop 中的多對多關聯性
description: 在 Power BI Desktop 中搭配多對多基數使用關聯性
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 97718ee6411d0063aa145e768fd20d3ebb6024b6
ms.sourcegitcommit: c9080e77ab705f1814a352c0dda6b10910a5018e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2019
ms.locfileid: "65941451"
---
# <a name="relationships-with-a-many-many-cardinality-in-power-bi-desktop"></a>Power BI Desktop 中的多對多基數關聯性

使用 Power BI Desktop 中的「多對多基數關聯性」功能，您可以聯結使用「多對多」基數的資料表。 您可以更輕鬆並更直覺的建立包含兩個或多個資料來源的資料模型。 「複合模型」功能是 Power BI Desktop 中的大型功能，而「多對多基數關聯性」功能則是其中的一部分。

![在 [編輯關聯性] 窗格中的多對多關聯性](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Power BI Desktop 之「多對多基數關聯性」功能是三個相關功能的其中之一：

* **複合模型**：允許報表可有兩 (含) 個以上任意組合的資料連線，包括 DirectQuery 連線或匯入。 如需詳細資訊，請參閱 [Power BI Desktop 的複合模型](desktop-composite-models.md)。

* **多對多基數關聯性**：您可以使用「複合模型」在資料表之間建立「多對多基數關聯性」。 此方法會移除資料表中唯一值的需求。 此方法也會移除先前的因應措施，像是只為建立關聯性而導入新的資料表。 本文中進一步說明此功能。

* **儲存模式**：您現在可以指定哪些視覺效果必須查詢後端資料來源。 不需要查詢的視覺效果，即便是使用 DirectQuery，也同樣會匯入。 此功能可提升效能，並減輕後端的負載。 以往，即使像是交叉分析篩選器這類的簡單視覺效果，也會起始傳送到後端來源的查詢。 如需詳細資訊，請參閱 [Power BI Desktop 的儲存模式 (預覽)](desktop-storage-mode.md)。

## <a name="what-relationships-with-a-many-many-cardinality-solves"></a>「多對多基數關聯性」解決的問題

在可使用「多對多基數關聯性」之前，兩個資料表間的關聯性是在 Power BI 中定義的。 關聯性中必須至少有一個資料表資料行包含唯一的值。 但是通常不會有任何資料行包含唯一的值。 

例如，兩個資料表可能都有一個標記為 *Country* 的資料行，但 *Country* 的值在任一資料表中都不是唯一的。 若要聯結這類資料表，必須建立因應措施。 其中一個因應措施，是在模型中引進具有必要唯一值的其他資料表。 使用「多對多基數關聯性」功能，您可以透過使用附帶**多對多**基數的關聯性，直接聯結這類資料表。  

## <a name="use-relationships-with-a-many-many-cardinality"></a>使用「多對多基數關聯性」

當您定義 Power BI 中兩個資料表之間的關聯性時，您必須定義關聯性的基數。 例如，*ProductSales* 和 *Product* 之間的關聯性&mdash;使用資料行 *ProductSales[ProductCode]* 和 *Product[ProductCode]*&mdash;便會定義為「多對一」。 我們會以此方式定義關聯性，因為每一項產品都有多項銷售，而 *Product* 資料表中的資料行 *(ProductCode)* 是唯一的。 當您將關聯性基數定義為「多對一」、「一對多」，或「一對一」時，Power BI 會驗證它，協助確保您選取的基數符合實際資料。

例如，請查看下圖的簡單模型：

![關聯性檢視](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

現在，想像 *Product* 資料表只會顯示兩個資料列，如下所示：

![只有兩個資料列的 Product 資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

另外，想像 *Sales* 資料表只有四個資料列，其中包含產品 C 的資料列。因為參考完整性錯誤，產品 C 資料列在 *Product* 資料表上並不存在。

![擁有四個資料列的 Sales 資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

*ProductName* 與 *Price* (來自 *Product* 資料表) 以及每種產品 *Qty* 總計 (來自 *ProductSales* 資料表) 會顯示如下： 

![顯示產品名稱、價格和數量的視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

如同先前影像中所示，有一個空白的 *ProductName* 資料列與產品 C 銷售相關聯。此空白資料列會導致如下情況：

* *ProductSales*資料表中的任何資料列沒有存在於 *Product* 資料表中的對應資料列。 發生參考完整性問題，如同我們在此範例中所見到的產品 *C*。

* *ProductSales* 資料表中任何資料列的外部索引鍵資料行為 Null。 

基於上述原因，兩個案例中的空白資料行都會導致 *ProductName* 和 *Price* 未知的銷售。

有時候的情況是資料表由兩個資料行聯結，但沒有任何一個是唯一的資料行。 例如，以下列兩個資料表為例：

* *Sales* 資料表會依 *State* 顯示銷售資料，每個資料列都包含該州某個銷售類型的銷售量。 州包括加州 (CA)、華盛頓州 (WA)、德州 (TX)。 

    ![銷售資料表，依州顯示銷售](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* *CityData* 資料表會顯示城市的資料，包括人口與州 (包括加州 (CA)、華盛頓州 (WA) 及紐約州 (New York) 等州)。

    ![銷售資料表，顯示城市、州和人口](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

雖然兩個資料表中都有 *State* 資料行，且合理推測可以依州來報告總計銷售以及各州的總人口，但有一個問題：*State* 資料行在任一資料表中都不是唯一的。 

## <a name="the-previous-workaround"></a>先前的因應措施

在 2018 年 7 月以前發行的 Power BI Desktop 版本中，使用者無法建立這些資料表之間的直接關聯性。 常見因應措施是執行下列動作：

* 建立第三個資料表，其中只包含唯一的 *State* 識別碼。 資料表可以是下列項目中的任何一項或全部：
  * 計算資料表 (使用資料分析運算式 [DAX] 定義)。
  * 以查詢編輯器中定義查詢為基礎的資料表，可顯示從其中一個資料表取得的唯一識別碼。
  * 合併的完整集。

* 透過使用常見的多對一關聯性，將兩個原始資料表與新的資料表建立關聯。

您可以讓因應措施資料表保持在可見狀態或是隱藏它，使其不會顯示在 [欄位] 清單中。 若您隱藏資料表，「多對一」關聯性常會設為雙向篩選，並且您可使用來自任一個資料表的 *State* 欄位。 後續的交叉篩選會散佈至另一個資料表。 以下影像會顯示該方法：

![關聯性檢視](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

接著，顯示 *State* (來自 *CityData* 資料表) 以及 *Population* 總計與 *Sales* 總計的視覺效果會出現如下：

![資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> 由於此因應措施中使用來自 *CityData* 資料表的州，因此只會列出該資料表中的州 (因此會排除德州 (TX))。 此外，和多對一關聯性不同，雖然總計資料列包含所有 *Sales* (包括德州 (TX) 的銷售量)，但詳細資料不包括涵蓋這類不相符資料列的空白資料列。 同樣地，也不會有空白資料列涵蓋 *State* 值為 Null 的任何 *Sales*。

若您也將 *City* 新增至該視覺效果，雖然已知每個 *City* 的人口，為 *City* 顯示的 *Sales* 卻只會重複對應 *State* 的 *Sales*。 這通常是資料行中進行的群組與某些彙總量值不相關時會發生的情形，如以下影像所示：

![資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

若我們將新的 *Sales* 資料表定義為此因應措施中所有 *States* 的合併，並且我們將它在 [欄位] 清單中設為可見，相同視覺效果便會顯示 *State* (位於新資料表) 和 *Population* 總計，以及 *Sales* 總計，如以下影像所示：

![資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

如您所見，*TX*&mdash;其附帶 *Sales* 資料但 *Population* 資料未知&mdash;及 *New York*&mdash;其 *Population* 已知但沒有任何 *Sales* 資料&mdash;會包含在其中。 此因應措施並非最佳方法，且有許多問題。 建立多對多基數關聯性，可以解決所產生的問題，如下一節中所述。

## <a name="use-relationships-with-a-many-many-cardinality-instead-of-the-workaround"></a>使用「多對多基數關聯性」取代因應措施

從 Power BI Desktop 的 2018 年 7 月版本開始，您可以直接關聯資料表 (例如我們先前所述的資料表) 而無須訴諸類似的因應措施。 現在可以將關聯性基數設為「多對多」。 此設定指出沒有任何資料表包含唯一值。 針對這類關聯性，您仍可控制要以哪個資料表來篩選另一個資料表，或套用雙向篩選，讓兩個資料表相互篩選。  

在 Power BI Desktop 中，當確定資料表在關聯性中的資料行無一包含唯一的值時，基數會預設為「多對多」。 在這類情況下，就會顯示警告，確認該關聯性設定是您的預期行為，而不是因資料問題造成的非預期效果。 

例如，當您直接建立 *CityData* 與 *Sales* 之間的關聯性時&mdash;其中的篩選條件應從 *CityData* 流至 *Sales*&mdash;ower BI Desktop 會顯示 [編輯關聯性] 視窗，如以下影像所示：

![[編輯關聯性] 視窗](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

產生的 [關聯性] 檢視會顯示兩個資料表之間的直接多對多關聯性。 [欄位] 清單中資料表的外觀及其在建立視覺效果之後的後續行為，都會與我們套用因應措施時相似。 在因應措施中，顯示相異 *State* 資料的額外資料表並未設為可見。 例如，如先前章節中所述，顯示 *State*、*Population* 和 *Sales* 資料的視覺效果會顯示如下：

![資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

「多對多基數關聯性」和更典型的「多對一」關聯性，兩者的主要差異如下：

* 顯示的值不包含導致另一個資料表中不相符資料列的空白資料列。 也不會包含在另一個資料表中關聯性內使用的資料行為 Null 時，代表資料列的值。
* 無法使用 `RELATED()` 函式，因為可和超過一個資料列建立關聯。
* 在其中一個資料表上使用 `ALL()` 函式不會移除套用到另一個以多對多關聯性相關資料表的篩選條件。 在先前範例中，下列指令碼中顯示的定義量值不會移除相關 *CityData* 資料表中資料行上的篩選條件：

    ![指令碼範例](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    顯示 *State*、*Sales* 及 *Sales total* 資料的視覺效果會產生：

    ![資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

考慮上述差異，請務必確認使用 `ALL(\<Table>)` 的計算 (例如 *% of grand total*) 傳回的是所要的結果。 


## <a name="limitations-and-considerations"></a>限制與考量

這一版的「多對多基數關聯性」和複合模型有一些限制。

下列 Live Connect (多維度) 來源不能與複合模型搭配使用：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 資料集
* Azure Analysis Services

當您使用 DirectQuery 連線到這些多維度來源時，將無法連線到其他 DirectQuery 來源，也無法合併匯入的資料。

使用「多對多基數關聯性」時，使用 DirectQuery 的現有限制仍然適用。 這其中有許多限制現在會依個別資料表的儲存模式而異。 例如，已匯入資料表上的計算結果欄可以參考其它資料表，但 DirectQuery 資料表上的計算結果欄仍僅能參考相同資料表上的資料行。 如果模型內有任何資料表為 DirectQuery，則其它限制會套用至整個模型。 例如，如果某個模型內的任何資料表具有 DirectQuery 的儲存模式，則該模型不提供 QuickInsights 和問與答功能。 

## <a name="next-steps"></a>後續步驟

如需複合模型及 DirectQuery 的詳細資訊，請參閱下列文章：
* [Power BI Desktop 中的複合模型](desktop-composite-models.md)
* [Power BI Desktop 中的儲存模式 (預覽)](desktop-storage-mode.md)
* [在 Power BI Desktop 中使用 DirectQuery](desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
