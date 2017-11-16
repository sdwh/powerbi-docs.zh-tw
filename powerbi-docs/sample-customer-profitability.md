---
title: "Power BI 的客戶獲利率範例：導覽"
description: "Power BI 的客戶獲利率範例：導覽"
services: powerbi
documentationcenter: 
author: amandacofsky
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
ms.date: 10/29/2017
ms.author: mihart
ms.openlocfilehash: 9a100b7d13c11a8bd066b72a570f45d0c2bc08be
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Power BI 的客戶獲利率範例：導覽
「客戶獲利率範例」內容套件包含製作行銷資料的公司儀表板、報表和資料集。 CFO 建立這個儀表板是為了查看轄下 5 個業務單位經理 (或主管)、產品、客戶和毛利 (GM) 的關鍵度量。 她一眼即可看出影響獲利率的因素。

此範例是系列中的一部分，該系列說明您可如何使用 Power BI 的商業導向資料、報表及儀表板。 此為來自 obviEnce 的匿名真實資料 ([www.obvience.com](http://www.obvience.com/))。

您也可以[只下載此範例的資料集 (Excel 活頁簿)](http://go.microsoft.com/fwlink/?LinkId=529781).  
![](media/sample-customer-profitability/power-bi-dash.png)

## <a name="what-is-our-dashboard-telling-us"></a>儀表板告訴我們什麼？
### <a name="company-wide-dashboard-tiles"></a>全公司的儀表板圖格
這些圖格讓 CFO 看到對她而言很重要的高階公司度量。  當她看到值得關注的項目時，她可以選取圖格深入探究資料。

1. 本公司的毛利為 42.5%。
2. 我們有 80 位客戶。
3. 我們銷售 5 種不同的產品。
4. 我們對預算的收益差異 % 在二月為最低，但在三月來到最高。
5. 我們的營收大部分來自東部和北部地區。 毛利從未超過預算，ER-0 和 MA-0 則需要進一步調查。
6. 年度總收益接近預算。

### <a name="manager-specific-dashboard-tiles"></a>經理特定儀表板圖格
這些圖格提供小組計分卡。 CFO 需要追蹤其轄下經理，而這些圖格能讓她使用 GM% 全面掌握收益狀況。 如果任一經理的 GM% 趨勢不盡人意，她就可以進一步調查。

Annelie 的 GM% 最低，但我們可以看到它三月之後穩定增加。 相反地，Valery 的 GM% 卻巨幅下滑。 而 Andrew 這一年的變動劇烈。 按一下任何經理特定圖格，開啟其基礎報表。 報表有 3 頁，開啟了「產業利潤分析」頁面。

## <a name="explore-the-pages-in-the-report"></a>瀏覽報表的頁面
我們的報表有 3 頁：

* 「小組計分卡」著重於 5 位管理員的效能和他們的「客戶個資清冊」。
* 「產業利潤分析」提供一種方法，用以分析相較於整個產業現況的我方獲利率。
* 「主管計分卡」提供可用 Cortana 檢視的格式化各主管檢視。

### <a name="team-scorecard-page"></a>[小組計分卡] 頁面
![](media/sample-customer-profitability/customer2.png)

讓我們仔細觀察兩個小組成員，看看有什麼發現。 在左側的交叉分析篩選器中選取 Andrew 的名字來篩選報表頁面，只顯示與他有關的資料。

* 如需快速查看 KPI，請查看 Andrew 的**營收狀態**：他的狀態為綠色。 他的業績很好。
* 「按月對預算的營收差異 %」區域圖顯示，除了二月份下跌，Andrew 整年的表現都很不錯。 他負責的區域在東部，手上有 49 位客戶和 5 項產品 (共 7 項)。 他的 GM% 不是最高或最低。
* 「總稅收和按月對預算的營收差異 %」顯示平穩甚至有獲利。但是當您按一下區域樹狀結構圖 [中部] 的方塊篩選資料時，您會發現 Andrew 只有三月份在印第安納州有營收。 這是故意為之，還是有什麼需要一探究竟嗎？

現在來看看 Valery。 在交叉分析篩選器中，選取 Valery 的名字來篩選報表頁面，只顯示與她有關的資料。  
![](media/sample-customer-profitability/customer3.png)

* 請注意 [總稅收狀態] 的紅色 KPI。 這肯定需要進一步探查。
* 她的營收差異也十分令人擔憂，她連自己的邊際收益都達不到。
* Valery 手上只有 9 位客戶、負責 2 項產品，而且幾乎只和北部的客戶打交道。 這個特點能夠說明其度量的巨幅波動。
* 在樹狀結構圖中選取 [北部]  方塊，顯示 Valery 在北部的毛利與她整體的毛利一致。
* 選取其他的 [區域]  方塊會發現一個有趣的現象：她的 GM% 從 23% 到 79%，而她的營收數字在北部以外的所有區域，都是絕對季節性的。

繼續探究為什麼 Valery 的區域業績不佳。 看看區域、其他業務單位和報表的下一頁：「產業利潤分析」。

### <a name="industry-margin-analysis"></a>產業利潤分析
這個報表頁面提供不同的資料面。 它著眼於整個產業的毛利，按區段切分。 CFO 用這個頁面比較公司暨業務單位的度量與產業度量，幫助她解釋趨勢和獲利率。 您可能會納悶為什麼「每月毛利和主管姓名」的區域圖放在這個頁面，因為它是小組特定的。 它在這裡有助於我們依業務單位主管篩選頁面。  
![](media/sample-customer-profitability/customer6.png)

獲利率如何依產業變化？ 如何依產業切分產品和客戶？ 請從左上角選取一或多個產業。 (從 CPG 產業開始) 若要清除篩選器，選取橡皮擦圖示。

在泡泡圖中，CFO 會尋找最大的泡泡，因為它們對營收的影響最大。 在區域圖中的主管姓名上按一下，依主管篩選頁面，讓您更容易依產業區段查看每一位經理的影響力。

* Andrew 影響的區域遍及許多不同的產業區段，其 GM% (多為好的一面) 和差異 % 的變化也極大。 
* Annelie 的圖表很類似，除了她專注於少數幾個產業區段，聚焦於聯邦區段及短劍產品。 
* Carlos 目標明確，在服務區段取得豐厚的利潤。 他在高科技區段及對他而言嶄新的工業區段的差異 % 成長驚人，與預算相較，表現十分突出。 
* Tina 負責少數幾個區段且擁有最高的 GM%，但她的泡泡都不大，這表示她對公司營收的影響最小。 
* Valery 只負表一種產品，只處理 5 個產業區段。 她的產業影響力有季節性，但一直都是大型的泡泡，這表示她對公司營收的影響巨大。 產業可否說明她不盡人意的表現？

### <a name="executive-scorecard"></a>主管計分卡
這個頁面會格式化為 Answer Card for Cortana。 若要深入了解，請參閱[建立 Answer Card for Cortana](service-cortana-answer-cards.md)。

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>利用問與答問來提問以深入探索資料
我們的分析有助於判斷哪些產業讓 Valery 產生最多收益。 讓我們使用問與答。

1. 選取導覽列頂端的 **Power BI** ，返回儀表板。
2. 請在儀表板頂端選取問與答的問題方塊。
   
    ![](media/sample-customer-profitability/customer4.png)
3. 輸入 **Valery 依各項產業分列的總營收**。 請注意當您輸入問題時，視覺效果更新的方式。
   
    ![](media/sample-customer-profitability/customer5.png)
   
   配銷是 Valery 最大的收益區域。

### <a name="dig-deeper-by-adding-filters"></a>加入篩選器更深入探究
讓我們看看 [配銷]  產業。  

1. 返回儀表板並選取有 Andrew 毛利趨勢的區域圖表。 這會開啟報表的「產業利潤分析」頁面。
2. 展開右側的篩選窗格，而不要在報表頁面上選取任何視覺效果。 [篩選] 窗格應該只會顯示頁面層級篩選。  
   
   ![](media/sample-customer-profitability/power-bi-filters.png)
3. 找到 [產業] 的篩選，然後選取箭號來展開清單。 讓我們新增 [配銷] 產業的頁面篩選。 首先，清除 [全選] 核取方塊，以清除所有選取項目。 然後選取 [配銷]。  
   
   ![](media/sample-customer-profitability/customer7.png)
4. 「每月毛利和主管姓名」區域圖告訴我們，只有 Valery 和 Tina 在此產業有客戶，而且 Valery 只有在六月到十一月這段時間才需要處理這項產業的業務。   
5. 在「每月毛利和主管」區域圖圖例中，依序選取 [Tina] 和 [Valery]。 請注意，和 Valery 相比，Tina 的「產品總收益」部分真的很小。 
6. 若要查看實際的營收，請返回儀表板並使用問與答要求**依主管及案例顯示配銷的總營收**。  
   
   ![](media/sample-customer-profitability/customer8.png)

我們可以類似的方法瀏覽其他產業，甚至加入客戶，以在視覺效果中了解 Valery 績效的成因。

這是安全的作業環境。 您一律可以選擇不儲存變更。 但如果儲存了變更，您也可以隨時移至 [取得資料]  ，重新複製此範例。

## <a name="next-steps-connect-to-your-data"></a>下一步：連接到您的資料
我們希望本教學已示範 Power BI 儀表板、問與答和報表如何讓您深入了解客戶的資料。 現在換您登場 — 連接到您自己的資料。 您可以透過 Power BI 連接到各式各樣的資料來源。 深入了解[開始使用 Power BI](service-get-started.md).

[返回 Power BI 中的範例](sample-datasets.md)  

