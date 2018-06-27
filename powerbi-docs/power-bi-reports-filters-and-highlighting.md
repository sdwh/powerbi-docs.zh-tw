---
title: 在 Power BI 報表中進行篩選和醒目提示的相關事項
description: 在 Power BI 報表中進行篩選和醒目提示的相關事項
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/26/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7239351a7a9486aeeab53e4ab7fc5c3c3e877ff6
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "34561440"
---
# <a name="about-filters-and-highlighting-in-power-bi-reports"></a>在 Power BI 報表中進行篩選和醒目提示的相關事項
***篩選***會保留您最關切的資料，而將其他所有資料移除。  ***醒目提示***與篩選不同，它不會移除資料，而會將一部分可見資料醒目提示，未醒目提示的資料會保持可見但呈現暗灰色。

若要篩選 Power BI 中的報表並將其醒目提示，有許多種不同的方式。 將所有該類資訊放在同篇文章中會容易混淆，因此我們已加以細分如下︰

* 篩選及反白顯示簡介 (您現正閱讀的文章)
* 若要[在您擁有的 [編輯檢視]/報表中建立及使用篩選並加以反白顯示](power-bi-report-add-filter.md)，可以使用的方式。 若您具有報表的編輯權限，即可建立、修改及刪除報表中的篩選和反白顯示。
* 若要[在與您共用的報表中或報表的 [讀取檢視] 中使用篩選和反白顯示](service-reading-view-and-editing-view.md)，可以使用的方式。 您可執行的動作較少，但 Power BI 仍提供您廣泛的篩選及反白顯示選項。  
* [[編輯檢視] 中可用的篩選及反白顯示控制項詳細介紹](power-bi-how-to-report-filter.md)內含多種篩選類型的深入探討 (例如日期與時間、數值、文字)，以及基本與進階選項之間的差異。
* 既然您已了解篩選及反白顯示的預設運作方式，接著再[了解如何變更頁面上的視覺效果篩選及反白顯示彼此的方式](service-reports-visual-interactions.md)

> [!TIP]
> Power BI 如何得知資料相關聯的方式？  Power BI 會在基礎[資料模型](https://support.office.com/article/Create-a-Data-Model-in-Excel-87e7a54c-87dc-488e-9410-5c75dbcb0f7b?ui=en-US&rs=en-US&ad=US)下使用不同資料表和欄位之間的關聯性，讓報表頁面上的項目彼此互動。
> 
> 

## <a name="introduction-to-filters-and-highlighting-in-reports-using-the-filters-pane"></a>在報表中使用 [篩選] 窗格進行篩選及反白顯示簡介
 本文介紹如何在 Power BI 服務中進行篩選和醒目提示。  但其體驗幾乎與 Power BI Desktop 完全相同。  

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

您可使用 [篩選] 窗格套用篩選和反白顯示，或直接從報表本身選取 (臨機操作，請參閱頁面底部)。 [篩選] 窗格會顯示報表中使用的資料表及欄位，以及已套用的篩選 (如果有的話)。 篩選會劃分成 [頁面層級]、[報表層級]、[鑽研] 和 [視覺效果層級]。  只有在您已選取報表畫布上的視覺效果時，才會看到視覺效果層級篩選。

> [!TIP]
> 若篩選條件旁邊有**全部**字組，這表示篩選條件涵蓋整個欄位。  例如，下方螢幕擷取畫面中的 [Chain(All)] 表示此報表頁面包含所有連鎖店的相關資料。  相反地，[FiscalYear is 2013 or 2014] 的報表層級篩選表示報表只包含會計年度 2013 年及 2014 年的資料。
> 
> 

## <a name="filters-in-reading-view-versus-editing-view"></a>閱讀檢視與編輯檢視中的篩選比較
您可使用下列兩種模式與報表互動：[閱讀檢視和編輯檢視](service-reading-view-and-editing-view.md)。  而篩選功能會依據您使用的模式來提供。

* 在 [編輯檢視] 中，您可以新增報表、頁面、鑽研和視覺效果篩選。 當您儲存報表時，篩選會與報表一起儲存，即使您在行動裝置應用程式中開啟它亦然。 在 [閱讀檢視] 中檢視報表的人員可以與您新增的篩選互動，但無法新增篩選。
* 在 [閱讀檢視] 中，您可以與報表中已存在的任何篩選互動，並儲存您做的選擇。  但您無法新增篩選。

### <a name="the-filters-pane-in-reading-view"></a>[讀取檢視] 中的 [篩選] 窗格
如果您只有在 [閱讀檢視] 中才可存取報表，[篩選] 窗格看起來會像這樣︰

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

所以報表的此頁面具有 6 個頁面層級篩選及 1 個報表層級篩選。

若要查看是否有任何視覺效果層級篩選，選取 [視覺效果]。 在下圖中，泡泡圖套用了 6 個篩選。

![](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

在 [讀取檢視] 中，透過修改現有的篩選來瀏覽資料。 即使您在行動裝置應用程式中開啟報表，您所做的變更也會與報表一起儲存。 在 [Power BI 服務中的閱讀檢視和編輯檢視](service-reading-view-and-editing-view.md)一文中了解做法

### <a name="the-filters-pane-in-editing-view"></a>[編輯檢視] 中的 [篩選] 窗格
若您具備報表的擁有者權限，並以 [編輯檢視] 加以開啟，則會看到 [篩選] 只是可用的數個編輯窗格中的一項。

![](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

於 \[讀取檢視] \(上述) 中，我們發現報表的此頁面具有 6 個頁面層級篩選及 1 個報表層級篩選。 且透過選取泡泡圖，我們看見其已套用 6 個視覺效果層級篩選。

但在 [編輯檢視] 中，還有更多可搭配篩選及反白顯示進行的項目。 主要的差異在於我們可以新增新的篩選。 在[將篩選新增至報表](power-bi-report-add-filter.md)這篇文章了解如何執行此項並完成更多項目

## <a name="ad-hoc-filtering-and-highlighting"></a>臨機操作篩選及醒目提示
選取報表畫布上的欄位，進而篩選頁面的其餘部分並加以反白顯示。 選取相同視覺效果的任意空白區域，即可加以移除。 此類的篩選及醒目提示對於快速瀏覽資料的影響而言是項有趣的方式。 若要微調此類交叉篩選及交叉顯目提示的運作方式，請參閱[視覺效果互動](service-reports-visual-interactions.md)。

![](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

當您結束報表時，則會儲存您的變更。 若要復原您的篩選並返回至預設篩選、切割、鑽研並依報表作者排序：請從頂端功能表列選取 [重設為預設]。

![](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

## <a name="next-steps"></a>後續步驟
[與篩選互動和醒目提示 (在 [閱讀檢視] 中)](service-reading-view-and-editing-view.md)

[將篩選新增至報表 (在 [編輯檢視] 中)](power-bi-report-add-filter.md)

[報表篩選概觀](power-bi-how-to-report-filter.md)

[變更報表視覺效果相互交叉篩選及交叉醒目提示的方式](service-reports-visual-interactions.md)

深入了解 [Power BI 中的報表](service-reports.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

