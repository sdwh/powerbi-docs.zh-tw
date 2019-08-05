---
title: 使用 Power BI Desktop 中的導出資料表
description: Power BI Desktop 中的導出資料表
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 641d1ac2c1bbcb9d143afdc04652b4c12b6e775f
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68522221"
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>使用 Power BI Desktop 中的導出資料表
透過導出資料表，您可以將新的資料表加入模型。 您會建立定義資料表值的資料分析運算式 (DAX) 公式，而不是從資料來源查詢值並將其載入新的資料表資料行。 在 Power BI Desktop 中，導出資料表是透過 [報表檢視] 或 [資料檢視] 中的 [新增資料表] 功能來建立。

大多時候，您會從外部資料來源將資料匯入模型。 不過，導出資料表提供一些優點。 導出資料表通常最適用於中繼計算及要當做模型一部分儲存的資料，而不是即時計算的資料表或做為查詢一部分的資料表。

不同於建立做為查詢一部分的資料表，在 [報表檢視] 或 [資料檢視] 中建立的導出資料表會依據您已經載入模型的資料。 例如，您可能會選擇聯集或交叉聯結兩個資料表。

導出資料表就像是一般資料表，可以與其他資料表建立關聯。 導出資料表中的資料行具有資料類型、格式，並可能屬於某種資料類別。 您可以為資料行指定任何名稱，並將其加入報表視覺效果，就像是其他欄位一樣。 如果以任何方式重新整理或更新提取資料的任何來源資料表，則會重新計算導出資料表。

導出資料表使用[資料分析運算式](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) 來計算結果，這是可處理類似 Power BI Desktop 中關聯式資料的公式語言。 DAX 所包含的程式庫是由 200 個以上的函數、運算子和建構函式所組成，為建立公式提供極大的彈性，可計算幾乎所有資料分析需求的結果。

## <a name="lets-look-at-an-example"></a>以下舉例說明
Contoso 專案經理 Jeff 有一個內含西北部員工資訊的資料表，以及另一個內含西南部員工資訊的資料表。 Jeff 想要將這兩個資料表放到一個資料表中。

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SouthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

將這兩個資料表放到一個導出資料表相當容易。 Jeff 可以在 [報表檢視] 或 [資料檢視] 中建立導出資料表，不過在 [資料檢視] 中執行這項作業比較容易，因為 Jeff 可以立即看到新的導出資料表。

Jeff 在 [資料檢視]  的 [模型化]  索引標籤上，按一下 [新增資料表]  。 公式列會隨即出現。

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff 接著輸入下列公式：

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

即會建立名為 Western Region Employees 的新資料表。

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

Jeff 的新 [Western Region Employees] 資料表會出現在 [欄位] 清單中，就像是其他任何資料表一樣。 如同其他任何資料表，Jeff 甚至可以建立與其他資料表的關聯性、新增導出資料行和量值，並將任何欄位新增至報表。

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>導出資料表的函數
導出資料表可以透過任何傳回資料表的 DAX 運算式來定義，包括另一個資料表的簡單參照。 例如：

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

您可以搭配 DAX 使用導出資料表，來解決許多分析問題。 我們在此僅快速介紹導出資料表。 當您開始使用導出資料表時，以下是可能對您很有幫助的一些較常見的 DAX 資料表函數：

* DISTINCT
* 值
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

如需這些函數及 DAX 函數的其他資料表，請參閱 [DAX 函數參考](https://msdn.microsoft.com/ee634396.aspx)。

