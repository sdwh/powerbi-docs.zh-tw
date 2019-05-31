---
title: 使用 URL 中的查詢字串參數篩選報表
description: 使用 URL 查詢字串參數篩選報表，甚至對多個欄位進行篩選。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
LocalizationGroup: Reports
ms.openlocfilehash: cf640be131e1bffb571ad3c2ae2713dee1c4c0ca
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051297"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>使用 URL 中的查詢字串參數篩選報表

當您在 Power BI 服務中開啟報表時，每頁報表各有其唯一的 URL。 若要篩選該報表頁面，您可以使用報表畫布上的 [篩選] 窗格。  或者您也可以將查詢字串參數新增至 URL，以預先篩選報表。 您可能有想要向同事展示的報表，並想要預先為他們篩選。 其中一個篩選方式是從報表的預設 URL 著手、將篩選參數新增至 URL，然後用電子郵件將整個新的 URL 寄送給他們。

![服務中的 Power BI 報表](media/service-url-filters/power-bi-report2.png)

## <a name="uses-for-query-string-parameters"></a>用於查詢字串參數

假設您在 Power BI Desktop 中工作。 您想要建立一個可連結至其他 Power BI 報表的報表，但只想要在其他報表中顯示部分資訊。 請先使用查詢字串參數來篩選報表並儲存 URL。 接下來，在 Desktop 中使用這些新的報表 URL 來建立資料表。  然後發佈並共用報表。

查詢字串參數的另一個用法是讓使用者建立進階 Power BI 解決方案。  使用 DAX，使用者可以建立報表，根據其客戶在目前報表中所做的選取範圍，動態產生篩選的報表 URL。 當客戶選取 URL 時，他們只會看到預期的資訊。 

## <a name="query-string-parameter-syntax-for-filtering"></a>用於篩選的查詢字串參數

透過參數，您可以篩選報表以取得一或多個值，即使這些值包含空格或特殊字元也一樣。 基本語法相當簡單；只要從報表 URL 著手、新增問號，然後新增您的篩選語法即可。

URL?filter=***資料表***/***欄位*** eq '***值***'

![具篩選的 URL](media/service-url-filters/power-bi-filter-urls7b.png)

* **資料表**和**欄位**名稱區分大小寫，**值**則無。
* 從報表檢視中隱藏的欄位仍可篩選。

### <a name="reports-in-apps"></a>應用程式中的報表

如果要將 URL 篩選器新增至應用程式的報表中，則格式會略有不同。 應用程式中報表的連結具有新增至 URL 的查詢參數 (ctid)。 使用連字號分隔的查詢參數 (&)。 保留 「？ 篩選 ="移至 URL 的結尾的 ctid 參數前面會加上連字號 (&)。 

如下列範例中：

app.powerbi.com/groups/me/apps/*應用程式識別碼*/reports/*報表識別碼*/ReportSection？ filter =*表格*/*欄位*eq '*值*（& s)' ctid =*ctid*

### <a name="field-types"></a>欄位類型

欄位類型可以是數字、日期時間或字串，而且使用的類型必須符合資料集中設定的類型。  例如，如果您想要將資料集資料行中的日期時間或數值設定為日期，指定「字串」類型的資料表資料行將無法運作 (例如 Table/StringColumn eq 1)。

* **字串**的前後必須加上單引號 - 'manager name'。
* **數字**不需要特殊格式設定
* **日期及時間**的前後必須加上單引號。 在 OData v3 中，前面必須再加上「日期時間」一詞，但在 OData v4 中則不需要。

如果仍感到困惑，請繼續閱讀，我們會詳加解說。  

## <a name="filter-on-a-field"></a>篩選欄位

假設報表的 URL 如下所示。

![起始 URL](media/service-url-filters/power-bi-filter-urls6.png)

而我們可以從地圖視覺效果 (上方) 看到，我們有門市位於北卡羅萊納州。

>[!NOTE]
>本範例以[零售分析範例](sample-datasets.md)為依據。
> 

若要篩選報表，使其只顯示 "NC" (北卡羅萊納州) 門市的資料，請將下列內容加到 URL 後；

?filter=Store/Territory eq 'NC'

![具篩選的 URL](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>NC  是儲存在 [Store]  資料表 [Territory]  欄位中的值。
> 

我們的報表已篩選出北卡羅萊納州；報表頁面上的所有視覺效果都只會顯示北卡羅萊納州的資料。

![篩選出北卡羅萊納州的報表](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-multiple-fields"></a>篩選多個欄位

您也可以將額外參數新增至 URL，以篩選多個欄位。 讓我們回到原始的篩選參數。

```
?filter=Store/Territory eq 'NC'
```

若要篩選其他欄位，請新增 '**and**'，然後以上述相同格式新增另一個欄位。 範例如下。

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/0sDGKxOaC8w?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="operators"></a>運算子

除了 '**and**' 以外，Power BI 還支援許多運算子。 下表列出這些運算子及其支援的內容類型。

|運算子  | 定義 | 字串  | 數字 | 日期 |  範例|
|---------|---------|---------|---------|---------|---------|
|**and**     | 和 |  可以      | 是 |  可以|  product/price le 200 and price gt 3.5 |
|**eq**     | 等於 |  可以      | 是   |  可以       | Address/City eq 'Redmond' |
|**ne**     | 不等於 |   可以      | 是  | 可以        |  Address/City ne 'London' |
|**ge**     |  大於或等於       | 不可以 | 是 |可以 |  product/price ge 10
|**gt**     | 大於        |不可以 | 是 | 可以  | product/price gt 20
|**le**     |   小於或等於      | 不可以 | 是 | 可以  | product/price le 100
|**lt**     |  小於       | 不可以 | 是 | 可以 |  product/price lt 20
|**in\*\***     |  含       | 可以 | 是 |  可以 | Student/Age in (27, 29)


\*\* 使用 **in** 時，**in** 右側的值可為以括弧括住的逗號分隔清單，或傳回集合的單一運算式。

### <a name="numeric-data-types"></a>數值資料類型

Power BI URL 篩選可包含下列格式的數字。

|數字類型  |範例  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5 L 或 5 l      |
|**double**     |   5.5 或 55e-1 或 0.55e+1 或 5D 或 5d 或 0.5e1D 或 0.5e1d 或 5.5D 或 5.5d 或 55e-1D 或 55e-1d     |
|**decimal**     |   5 M 或 5 m 或 5.5 M 或 5.5 m      |
|**float**     | 5 F 或 5 f 或 0.5e1 F 或 0.5e-1 d        |

### <a name="date-data-types"></a>日期資料類型

Power BI 針對 **Date** 和 **DateTimeOffset** 資料類型支援 OData V3 和 V4。  使用 EDM 的格式表示日期 (2019年-02-12T00:00:00)，因此當您指定的日期 '-YYYY-MM-DD' 時，Power BI 會將它做為解譯 ' YYYY-MM-DDT00:00:00'。

此差異為何很重要？ 假設您建立的查詢字串參數**日期資料表/g ' 2018年-08-03'** 。  結果會包含 2018 年 8 月 3 日，還是從 2018 年 8 月 4 日開始？ 因為 Power BI 會將轉譯的查詢，以**日期資料表/g '2018年-08-03T00:00:00'** ，您的結果包含具有非零時間部分，因為這些日期會是大於任何日期 **' 2018年-08-03T00:00:00'** .

## <a name="special-characters-in-url-filters"></a>URL 篩選中的特殊字元

特殊字元和空格需要一些額外的格式設定。 當您的查詢包含空格、破折號或其他非 ASCII 字元時，請在這些特殊字元前面加上「逸出代碼」  ，開頭為底線，並加上一個 X ( **_x**) 和四位數 **Unicode**，再接上另一個底線。 如果 Unicode 少於四個字元，您必須以零填補。 以下是一些範例。

|識別碼  |Unicode  | 適用於 Power BI 的編碼  |
|---------|---------|---------|
|**資料表名稱**     | 空格是 0x20        |  Table_x0020_Name       |
|**Column**@**Number**     |   @ 是 0x40     |  Column_x0040_Number       |
|**[Column]**     |  [ 是 0x0058] 是 0x0050       |  _x0058_Column_x0050_       |
|**Column+Plus**     | + 是 0x2B        |  Column_x002B_Plus       |

Table_x0020_Name/Column_x002B_Plus eq 3 ![呈現特殊字元的資料表視覺效果](media/service-url-filters/power-bi-special-characters1.png)


Table_x0020_Special/_x005B_Column_x0020_Brackets_x005D_ eq '[C]' ![呈現特殊字元的資料表視覺效果](media/service-url-filters/power-bi-special-characters2.png)

## <a name="use-dax-to-filter-on-multiple-values"></a>使用 DAX 篩選多個值

篩選多個欄位的另一種方法是建立計算結果欄，將兩個欄位串連成單一值。 接著您就可以篩選該值。

例如，我們有兩個欄位：Territory 和 Chain。 在 Power BI Desktop 中[建立新的計算結果欄](desktop-tutorial-create-calculated-columns.md) (欄位)，名稱為 TerritoryChain。 請記住，**欄位**名稱不能有任何空格。 以下是該資料行的 DAX 公式。

TerritoryChain = [Territory] & " - " & [Chain]

將報表發佈到 Power BI 服務，然後使用 URL 查詢字串篩選成只顯示 NC 的 Lindseys 門市資料。

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC – Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>從篩選的報表釘選磚

在您使用查詢字串參數篩選報表後，可以將視覺效果從該報表釘選到儀表板。  儀表板上的圖格會顯示經篩選資料，而選取該儀表板圖格會開啟用來建立該圖格的報表。  不過，您使用 URL 進行的篩選不會與報表一起儲存。 當您選取儀表板圖格時，報表會以未經篩選的狀態開啟。  因此，儀表板圖格中顯示的資料與報表視覺效果中所顯示資料不相符。

此差異在您想要查看不同結果時很實用；在儀表板上已篩選，在報表則未篩選。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

使用查詢字串參數時，有幾件點事項要注意。

* 使用 *in* 運算子時，*in* 右方的值必須是前後加上括弧的逗點分隔清單。    
* 在 Power BI 報表伺服器，[傳遞報表參數](https://docs.microsoft.com/sql/reporting-services/pass-a-report-parameter-within-a-url?view=sql-server-2017.md)的方法可以是將其包含在報表 URL 中。 這些 URL 參數不會有前置詞，因為會直接傳遞到報表處理引擎。
* 查詢字串篩選不適用於[發佈至網路](service-publish-to-web.md)或是[匯出至 PDF](consumer/end-user-pdf.md)。
* [在 SharePoint Online 中內嵌報表 Web 組件](service-embed-report-spo.md)不支援 URL 篩選。
* 由於 JavaScript 限制，Long 資料類型為 (2^53-1)。
* 報表 URL 篩選條件有 10 個運算式的限制 (以 AND 連接的 10 個篩選條件)。

## <a name="next-steps"></a>後續步驟

[將視覺效果釘選至儀表板](service-dashboard-pin-tile-from-report.md)  
[註冊以免費試用](https://powerbi.microsoft.com/get-started/)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
