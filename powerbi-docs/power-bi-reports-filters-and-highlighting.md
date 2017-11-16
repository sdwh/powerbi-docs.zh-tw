---
title: "在 Power BI 報表中進行篩選和醒目提示的相關事項"
description: "在 Power BI 報表中進行篩選和醒目提示的相關事項"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/29/2017
ms.author: mihart
ms.openlocfilehash: 57960c3ca46e48f399e0492192c10cba2cfa7ea9
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="about-filters-and-highlighting-in-power-bi-reports"></a>在 Power BI 報表中進行篩選和醒目提示的相關事項
***篩選***會保留您最關切的資料，而將其他所有資料移除。  ***醒目提示***與篩選不同，它不會移除資料，而會將一部分可見資料醒目提示，未醒目提示的資料會保持可見但呈現暗灰色。

若要篩選 Power BI 中的報表並將其反白顯示，有許多種不同的方式。 將所有該類資訊放在同篇文章中會容易混淆，因此我們已加以細分如下︰

* 篩選及反白顯示簡介 (您現正閱讀的文章)
* 若要[在您擁有的 [編輯檢視]/報表中建立及使用篩選並加以反白顯示](power-bi-report-add-filter.md)，可以使用的方式。 若您具有報表的編輯權限，即可建立、修改及刪除報表中的篩選和反白顯示。
* 若要[在與您共用的報表中或報表的 [讀取檢視] 中使用篩選和反白顯示](service-interact-with-a-report-in-reading-view.md)，可以使用的方式。 您可執行的動作較少，但 Power BI 仍提供您廣泛的篩選及反白顯示選項。  
* [[編輯檢視] 中可用的篩選及反白顯示控制項詳細介紹](power-bi-how-to-report-filter.md)內含多種篩選類型的深入探討 (例如日期與時間、數值、文字)，以及基本與進階選項之間的差異。
* 既然您已了解篩選及反白顯示的預設運作方式，接著再[了解如何變更頁面上的視覺效果篩選及反白顯示彼此的方式](service-reports-visual-interactions.md)

> [!TIP]
> Power BI 如何得知資料相關聯的方式？  Power BI 會在基礎[資料模型](https://support.office.com/article/Create-a-Data-Model-in-Excel-87e7a54c-87dc-488e-9410-5c75dbcb0f7b?ui=en-US&rs=en-US&ad=US)下使用不同資料表和欄位之間的關聯性，讓報表頁面上的項目彼此互動。
> 
> 

## <a name="introduction-to-filters-and-highlighting-in-reports-using-the-filters-pane"></a>在報表中使用 [篩選] 窗格進行篩選及反白顯示簡介
![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

您可使用 [篩選] 窗格套用篩選和反白顯示，或直接從報表本身選取 (臨機操作，請參閱頁面底部)。 [篩選] 窗格會顯示報表中使用的資料表及欄位，以及已套用的篩選 (如果有的話)。 篩選會劃分成 [頁面層級篩選]、[報表層級篩選] 以及 [視覺效果層級篩選]。  只有在您已選取報表畫布上的視覺效果時，才會看到視覺效果層級篩選。

> [!TIP]
> 若篩選條件旁邊有**全部**字組，這表示篩選條件涵蓋整個欄位。  例如，下方螢幕擷取畫面中的 [Chain(All)] 表示此報表頁面包含所有連鎖店的相關資料。  相反地，[FiscalYear is 2013 or 2014] 的報表層級篩選表示報表只包含會計年度 2013 年及 2014 年的資料。
> 
> 

## <a name="filters-in-reading-view-versus-editing-view"></a>閱讀檢視與編輯檢視中的篩選比較
您可使用下列兩種模式與報表互動：[閱讀檢視](service-interact-with-a-report-in-reading-view.md) 和 [編輯檢視](service-interact-with-a-report-in-editing-view.md)。  而篩選功能會依據您使用的模式來提供。

* 在 [編輯檢視] 中，您可以新增報表、頁面和視覺效果篩選。 當您儲存報表時，也會將篩選一起儲存。 而在 [閱讀檢視] 中檢視報表的人可以與您加入的篩選互動，但不能儲存他們所做的變更。
* 在 [閱讀檢視] 中，您可以與報表中已存在的任何頁面和視覺效果篩選互動，但無法儲存您的篩選變更。

### <a name="the-filters-pane-in-reading-view"></a>[讀取檢視] 中的 [篩選] 窗格
如果您只有在 [閱讀檢視] 中才可存取報表，[篩選] 窗格看起來會像這樣︰

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

所以報表的此頁面具有 6 個頁面層級篩選及 1 個報表層級篩選。

若要查看是否有任何視覺效果層級篩選，選取 [視覺效果]。 在下圖中，泡泡圖套用了 6 個篩選。

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

在 [讀取檢視] 中，透過修改現有的篩選來瀏覽資料。 於[在 [讀取檢視] 中與篩選互動](service-interact-with-a-report-in-reading-view.md)這篇文章中了解如何做到

### <a name="the-filters-pane-in-editing-view"></a>[編輯檢視] 中的 [篩選] 窗格
若您具備報表的擁有者權限，並以 [編輯檢視] 加以開啟，則會看到 [篩選] 只是可用的數個編輯窗格中的一項。

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

於 \[讀取檢視] \(上述) 中，我們發現報表的此頁面具有 6 個頁面層級篩選及 1 個報表層級篩選。 且透過選取泡泡圖，我們看見其已套用 6 個視覺效果層級篩選。

但在 [編輯檢視] 中，還有更多可搭配篩選及反白顯示進行的項目。 主要的差異在於我們可以新增新的篩選。 在[將篩選新增至報表](power-bi-report-add-filter.md)這篇文章了解如何執行此項並完成更多項目

## <a name="ad-hoc-filterting-and-highlighting"></a>臨機操作篩選及反白顯示
選取報表畫布上的欄位，進而篩選頁面的其餘部分並加以反白顯示。 選取相同視覺效果的任意空白區域，即可加以移除。 此類的篩選及反白顯示並不會與報表一起儲存，但對於快速瀏覽資料的影響而言是項有趣的方式。 若要微調此類交叉篩選及交叉反白顯示的運作方式，請參閱[互動](service-reports-visual-interactions.md)

![](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

## <a name="next-steps"></a>後續步驟
[與篩選互動和醒目提示 (在 [閱讀檢視] 中)](service-interact-with-a-report-in-reading-view.md)

[將篩選新增至報表 (在 [編輯檢視] 中)](power-bi-report-add-filter.md)

[報表篩選概觀](power-bi-how-to-report-filter.md)

[變更報表視覺效果相互交叉篩選及交叉醒目提示的方式](service-reports-visual-interactions.md)

深入了解 [Power BI 中的報表](service-reports.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

