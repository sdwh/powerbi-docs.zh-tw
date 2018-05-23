---
title: 變更 Power BI 報表中的圖表排序方式
description: 變更 Power BI 報表中的圖表排序方式
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/20/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6b70a9ef7774d1ba49bc5bf825a5c1cde47197f2
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>變更 Power BI 報表中的圖表排序方式
在 Power BI 報告中，您可以依圖表類別名稱的字母順序排序大部分的視覺效果，或依每個類別的數值排序。 例如，這張圖表是依照門市名稱排序。

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

可以輕鬆地將排序從類別 (商店名稱) 變更為值 (每平方英尺銷售額)。

1. 選取省略符號 (...) 並選擇 [排序依據為每平方英尺銷售額]。
2. 如有需要，請選取排序圖示 ![](media/power-bi-report-change-sort/sorticon.png) 以變更為 [遞減]。

   ![](media/power-bi-report-change-sort/sortby.gif)

   **注意**：並非所有的視覺效果都可以排序。  例如，下列視覺效果無法排序：樹狀圖、地圖、區域分布圖、散佈圖、量表圖、卡片、多列卡片、瀑布圖。

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>使用其他準則排序
有時候，您會想要使用不同的欄位或其他準則來排序您的視覺效果。  例如，您可能想要依月份 (而不是字母順序) 排序，或您可以想要依整個數值而不是數字排序 (例如 0、 1、 9、 20，而不是 0、 1、 20、 9)。  

在某些情況下，您可以依想要的方式排序視覺效果 (例如，依月份)。  但是，否則原因可能是報表後面的資料集需要一些變化。 您可以選用下列幾種解決方法：

* 在 Power BI Desktop 中，可以[使用 [Data Tools 模型] 索引標籤依不同的資料行進行排序](desktop-sort-by-column.md)。
* 在 Excel 中，如果您就是資料集的擁有者，可以新增串連月份名稱及數字的資料行。 接著再重新整理或重新匯入，確認新的資料行位在 [欄位] 區域中。
* 在 Excel 中，確認已將您的數值資料行標示為「整數」或「小數點」，而不是「文字」。

## <a name="next-steps"></a>後續步驟
深入了解 [Power BI 報表中的視覺效果](power-bi-report-visualizations.md)。

[Power BI - 基本概念](service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
