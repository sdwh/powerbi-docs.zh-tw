---
title: 使用中的彙總 （sum、 average、 等等） 的 Power BI 服務
description: 了解如何變更圖表 （總和、 平均、 最大值，而且等）。 在 Power BI 服務中的彙總。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710572"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>使用中的彙總 （sum、 average、 等等） 的 Power BI 服務

## <a name="what-is-an-aggregate"></a>什麼是彙總？

有時候您會想要以數學方式結合資料中的值。 數學運算可能是加總、 平均、 最大值、 計數等等。 當您結合資料中的值時，它會呼叫*彙總*。 數學運算的結果是「彙總值」  。

Power BI 服務和 Power BI Desktop 建立視覺效果時，可能會彙總資料。 通常彙總就是所需要的結果，但有時候您可能想要以不同方式來彙總值。  例如，總和與平均值。 有數個不同的方式來管理和變更 Power BI 視覺效果中使用的彙總。

首先，讓我們看看資料*型別*因為資料類型會決定如何及是否，Power BI 可以進行彙總。

## <a name="types-of-data"></a>資料類型

大部分的資料集有多個資料類型。 在最基本的層級的資料是數值或它不是。 Power BI 可以彙總使用總和、 平均值、 計數、 最小值、 變異數和其他更多的數值資料。 此服務甚至可以彙總文字資料，通常稱為*類別*資料。 如果您嘗試將其放在純數字的值區，例如彙總類別欄位**值**或是**工具提示**，Power BI 會計算每個類別的出現次數或計算每個相異的出現次數類別目錄。 特殊類型的資料，例如日期，有幾個自己的彙總選項： 最早、 最新、 第一個和最後一個。

在下列範例中：

- [銷售單位]  與 [製造價格]  是包含數值資料的資料行

- [業別]  、[國家/地區]  、[產品]  、[月份]  和 [月份名稱]  包含類別目錄資料

   ![範例資料集的螢幕擷取畫面。](media/service-aggregates/power-bi-aggregate-chart.png)

在 Power BI 中建立視覺效果，服務會彙總的數值欄位 (預設值是*總和*) 對某個類別欄位。  比方說，"Units Sold***依產品***"，"Units Sold***依月份***」 和 「 製造價格***區段所***"。 Power BI 做為一些數值欄位是指**量值**。 就可以輕鬆地識別在 Power BI 報表編輯器中，量值**欄位**清單會顯示以 ∑ 符號旁邊的量值。 請參閱[報表編輯器...瀏覽](service-the-report-editor-take-a-tour.md)如需詳細資訊。

![螢幕擷取畫面的 Power BI 的 [欄位] 清單所呼叫。](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>為什麼彙總運作的方式和我想要的不同？

使用 Power BI 中的彙總服務可能會造成混淆的。 或許您有數值欄位時，Power BI 不會讓您變更的彙總。 或是您有一個欄位，例如年份，您不想彙總它，只想要計算發生次數。

一般而言，基本的問題是在資料集中的欄位定義。 可能的資料集擁有者會定義欄位為文字，並說明 Power BI 無法加總或平均的原因。 不幸的是，[只有資料集擁有者可以變更欄位的分類方式](desktop-measures.md)。 因此如果您有資料集，請在 Desktop 或用來建立資料集 (例如 Excel) 的程式的擁有者權限，您可以修正這個問題。 否則，您必須連絡資料集擁有者以取得協助。  

沒有在呼叫這篇文章結尾的特殊區段[**考量與疑難排解**](#considerations-and-troubleshooting)。 它提供的秘訣和指引。 如果找不到您的答案，將問題張貼在[Power BI 社群論壇](http://community.powerbi.com)。 您會直接從 Power BI 小組，以取得快速的回應。

## <a name="change-how-a-numeric-field-is-aggregated"></a>變更數值欄位的彙總方式

假設您有加總不同產品銷售單位的圖表，但您比較想要平均值。

1. 建立**群組直條圖**中使用的量值和分類。 在此範例中，我們會使用「依產品的銷售單位」。  根據預設，Power BI 會建立加總銷售單位的圖表 (拖曳到量值**值**也) 針對每個產品 (拖曳到類別目錄**軸**也)。

   ![圖表、 視覺效果 窗格和欄位清單的螢幕擷取畫面，總和與叫出。](media/service-aggregates/power-bi-aggregate-sum.png)

1. 在 [**視覺效果**] 窗格中，以滑鼠右鍵按一下量值，然後選取您需要的彙總類型。 在此情況下，我們要選取**平均**。 如果您沒有看到彙總您需要請參閱[**考量與疑難排解**](#considerations-and-troubleshooting)一節。

   ![選取的彙總清單的螢幕擷取畫面，平均，並叫出。](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > 下拉式清單中可用的選項取決於所選 1） 的欄位，以及 2） 的方式為資料集擁有者分類該欄位。

1. 您的視覺效果現在使用依平均值彙總。

   ![現在依產品顯示 平均的單位銷售圖表的螢幕擷取畫面。](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>彙總資料的方式

彙總欄位可用的某些選項：

- **不加總**。 選擇此選項，Power BI 會分別將該欄位中的每個值，並不會進行摘要。 如果您有服務不應該加總的數值識別碼資料行，請使用此選項。

- **加總**。 加總該欄位中的所有值。

- **平均**。 求出值的算術平均值。

- **最小值**。 顯示最小的值。

- **最大值**。 顯示最大的值。

- **計數 (沒有空格)。** 計算該欄位中不是空白的值數目。

- **計數 (相異)。** 計算該欄位中不同值的數目。

- **標準差。**

- **變異數**。

- **中位數**。  顯示中間值。 此值之上和之下具有相同的項目數。  如果有兩個中位數，Power BI 會取其平均值。

例如，下列資料：

| 國家/地區 | 數量 |
|:--- |:--- |
| 美國 |100 |
| 英國 |150 |
| 加拿大 |100 |
| 德國 |125 |
| 法國 | |
| 日本 |125 |
| 澳洲 |150 |

會得到下列結果：

- **不摘要**：分別顯示每個值

- **加總**：750

- **平均**：125

- **最大值**：150

- **最小值**：100

- **計數 (沒有空格)** ：6

- **計數 (相異)** ：4

- **標準差**：20.4124145...

- **變異數**：416.666...

- **中位數**：125

## <a name="create-an-aggregate-using-a-category-text-field"></a>建立使用類別 (文字) 欄位的彙總

您也可以彙總非數值欄位。 例如，如果有產品名稱欄位，您可以將它新增為值，然後將它設定為 [計數]  、[相異計數]  、[第一個]  或 [最後一個]  。

1. 拖曳**產品**欄位至**值**良好。 **值**也通常用於數值欄位。 此欄位是一個文字欄位、 設定彙總，power BI 會辨識**不摘要**，，您會使用單欄資料表。

   ![在 [值] 和 [Product] 欄位的螢幕擷取畫面。](media/service-aggregates/power-bi-aggregate-value.png)

1. 如果您變更預設彙總**不摘要**要**計數 （相異）** ，Power BI 就會計算不同的產品數目。 在此情況下，有四個。
  
   ![相異計數產品的螢幕擷取畫面。](media/service-aggregates/power-bi-aggregate-count.png)

1. 如果您將彙總變更為 [計數]  ，Power BI 就會計算總數。 在此情況下，有七個項目**產品**。

   ![螢幕擷取畫面的產品計數。](media/service-aggregates/power-bi-aggregate-count-2.png)

1. 藉由拖曳相同的欄位 (在此情況下**產品**) 成**值**，並維持預設彙總**不摘要**，細分計數所依據的 Power BI產品。

   ![產品，產品計數的螢幕擷取畫面。](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

問：為什麼沒有 [不摘要]  選項？

答：您所選取的欄位可能是在 Excel 或 [Power BI Desktop](desktop-measures.md) 中建立的導出量值或進階量值。 每個導出量值都有自己的硬式編碼公式。 您無法變更 Power BI 使用的彙總。 例如，如果是總和，就只能是總和。 **欄位**清單中顯示*導出量值*與計算機符號。

問：我的欄位**是**數值，為何我只能選擇 [計數]  和 [相異計數]  ？

答 1：可能的原因為資料集擁有者*不*分類的數字欄位。 例如，如果資料集**年份**欄位中，資料集擁有者可能會分類為文字值。 就越有可能，將會計入 Power BI**年份**欄位 （例如在 1974年出生的人的數目）。 就比較不可能，Power BI 會加總或平均。 如果您是擁有者，您可以在 Power BI Desktop 中開啟資料集，並使用**模型化**變更資料類型的索引標籤。

答 2：如果欄位有計算機圖示，這表示它是*導出量值*。 每個導出量值都有自己的資料集擁有者可以變更的硬式編碼公式。 Power BI 使用的計算可能是簡單的彙總，例如平均或加總。 它也可能是項目會比較複雜，例如"百分比的父類別所佔比重 」 或 「 加總因為 開始一年 」。 Power BI 並不會加總或平均的結果。 相反地，它將只重新計算 （使用硬式編碼公式） 每個資料點。

答 3：另一個可能的原因是，您將欄位放到了只允許類別值的「值區」  。  在此情況下，您只能選擇計數與相異計數。

答 4：而第四個可能的原因是，您使用欄位作為座標軸。 例如，在橫條圖的軸上，Power BI 會針對每個相異值顯示一個橫條，它完全不會彙總欄位值。

>[!NOTE]
>此規則的例外狀況是散佈圖，「需要」  彙總 X 軸和 Y 軸的值。

問：為何我無法針對 SQL Server Analysis Services (SSAS) 資料來源對文字欄位進行彙總？

答：SSAS 多維度模型的即時連線不允許任何用戶端彙總，包括 first、last、avg、min、max 和 sum。

問：我有散佈圖，而且我希望我的欄位「不要」  彙總。  怎麼做？

答：將欄位新增至 [詳細資料]  值區，而不是 X 或 Y 軸的值區。

問：當我新增數值欄位至視覺效果時，它們大部分都預設為加總，但有些會預設為平均或計數，而其他則會預設為彙總。  為什麼預設彙總不一律相同？

答：資料集擁有者可以設定每個欄位的預設摘要。 如果您是資料集擁有者時，變更中的預設摘要**模型化**的 Power BI Desktop 索引標籤。

問：我是資料集擁有者，我想確保欄位永遠不會進行彙總。

答：在 Power BI Desktop 中，請在 [模型]  索引標籤中，將 [資料類型]  設為 [文字]  。

問：我沒看到**不摘要**為我的下拉式清單中的選項。

答：請嘗試移除欄位，並將其新增回去。

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)