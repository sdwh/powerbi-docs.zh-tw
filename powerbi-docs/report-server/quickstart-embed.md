---
title: "使用 iFrame 來內嵌報告"
description: "安裝 Power BI 報表伺服器本身非常快速。 無論是下載還是安裝及設定，您應都可在幾分鐘內即啟動並執行。"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 11/09/2017
ms.author: maghan
ms.openlocfilehash: 56835bfb25c8c930099fadf710137f69fa89fc2e
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2018
---
# <a name="quickstart-embed-a-power-bi-report-using-an-iframe-and-url-parameters"></a>快速入門：使用 iFrame 及 URL 參數內嵌 Power BI 報表

您可以在應用程式中使用 iFrame 來內嵌任何報告。 

## <a name="url-parameter"></a>URL 參數

在報告的任何 URL 中，您可以新增 `?rs:Embed=true` 的查詢字串參數。

例如：

```
http://myserver/reports/powerbi/Sales?rs:embed=true
```

這適用於 Power BI 報表伺服器內的所有報告類型。

## <a name="iframe"></a>iFrame

取得您的 URL 之後，您可以在網頁內建立 iFrame 來放置報告。

例如：

```
<iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
```

## <a name="url-filter"></a>URL 篩選

您可以在 URL 中新增查詢字串參數，以篩選 Power BI 報表中所傳回的資料。

語法很簡單；只要從報表 URL 著手、新增問號，然後新增此篩選語法即可。

URL?filter=***資料表***/***欄位*** eq '***值***'

請記住這些考量：

- **資料表**和**欄位**名稱區分大小寫，**值**則無。
- 您可以使用報表檢視中隱藏的欄位來篩選報表。
- **值**的前後必須加上單引號。
- 欄位類型必須是字串。
- 資料表和欄位名稱不能有空格。

###  <a name="example-filter-on-a-field"></a>範例：篩選欄位

以[零售分析範例](../sample-datasets.md)為例。 假設這是名為「power-bi」的資料夾中報表伺服器上報表的 URL：

```
https://report-server/reports/power-bi/Retail-Analysis-Sample
```

您會看到「零售分析範例」中的地圖視覺效果顯示北卡羅來那州以及其他州的門市。

![零售分析範例的地圖視覺效果](media/quickstart-embed/report-server-retail-analysis-sample-map.png)

*NC* 是儲存在 [Store] 資料表 [Territory] 欄位中的值。 因此若要篩選報表，使其只顯示北卡羅萊納州門市的資料，請將下列內容加到 URL 後：

?filter=Store/Territory eq 'NC'

現在，報表已篩選出北卡羅萊納州；報表頁面上的所有視覺效果都只會顯示北卡羅萊納州的資料。

![零售分析範例的篩選後視覺效果](media/quickstart-embed/report-server-retail-analysis-sample-filtered-map.png)

### <a name="create-a-dax-formula-to-filter-on-multiple-values"></a>建立 DAX 公式以篩選多個值

篩選多個欄位的另一種方法是在 Power BI Desktop 中建立計算結果欄，將兩個欄位串連成單一值。 接著您就可以篩選該值。

例如，零售分析範例有兩個欄位：Territory 和 Chain。 在 Power BI Desktop 中，您可以[建立計算結果欄](../desktop-tutorial-create-calculated-columns.md) (欄位)，名稱為 TerritoryChain。 請記住，**欄位**名稱不能有任何空格。 以下是該資料行的 DAX 公式。

TerritoryChain = [Territory] & "-" & [Chain]

將報表發佈到 Power BI 報表伺服器，然後使用 URL 查詢字串篩選成只顯示 NC 的 Lindseys 門市資料。

```
https://report-server/reports/power-bi/Retail-Analysis-Sample?filter=Store/TerritoryChain eq 'NC-Lindseys'

```

## <a name="next-steps"></a>後續步驟

[快速入門︰建立 Power BI 報表伺服器的 Power BI 報表](quickstart-create-powerbi-report.md)  
[快速入門︰建立 Power BI 報表伺服器的編頁報告](quickstart-create-paginated-report.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)