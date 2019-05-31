---
title: Power BI 服務報表中的書籤的概觀
description: Power BI 問與答自然語言查詢的文件概觀主題。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/10/2019
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 55fafb00135908dc4f82151b96ed04d2cf2568da
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65608318"
---
# <a name="what-are-bookmarks"></a>書籤有哪些？
書籤擷取目前設定的報表頁面上，包括篩選、 交叉分析篩選器，以及視覺效果的狀態檢視。 當您選取書籤時，Power BI 會帶您回到該檢視。 有兩種類型的書籤-與您建立您自己和所建立的報表*設計工具*。

## <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>在 Power BI 中使用書籤來共用深入解析並建立故事 
有許多用途，書籤。 假設您發現有趣的深入解析，而且想要保留--建立書籤，因此您可以稍後再回來。 要保留，而且想要保留您目前的工作、 建立書籤。 您甚至可以讓您的報表，因此每次您的預設檢視傳回，會首先開啟報表頁面檢視的書籤。 

您也可以建立集合的書籤，排列它們的順序，並逐步執行至反白顯示一系列的故事的深入解析的簡報中的每個書籤。  

![選取從功能區顯示書籤窗格。](media/end-user-bookmarks/power-bi-bookmarks-pane.png)

## <a name="using-bookmarks"></a>使用書籤
若要開啟 [書籤] 窗格中，選取**書籤**從功能表列。 若要回到原始報表的已發行的檢視，請選取**重設為預設**。

### <a name="report-bookmarks"></a>報表的書籤
如果報表*設計工具*包含報表的書籤，您會發現下**報告書籤**標題。 

![顯示報表的書籤。](media/end-user-bookmarks/power-bi-report-bookmark.png)

選取要切換至該報表檢視的書籤。 

![顯示報表的視訊設定為書籤被選取。](media/end-user-bookmarks/power-bi-bookmarks.gif)

### <a name="personal-bookmarks"></a>個人的書籤

當您建立書籤時，下列項目會與書籤一起儲存：

* 目前頁面
* 篩選
* 交叉分析篩選器，包括交叉分析篩選器類型 (例如，下拉式清單或清單) 和交叉分析篩選器狀態
* 視覺效果選取狀態 (例如交叉醒目提示篩選條件)
* 排序次序
* 鑽研位置
* 可見度 (使用 [選取]  窗格之物件的可見度)
* 任何可見物件的焦點或**聚焦**模式

以您想要在書籤中顯示的方式來設定報表頁面。 將報表頁面和視覺效果排列成您想要的方式之後，從 [書籤]  窗格中選取 [新增]  以新增書籤。 在此範例中，我們已新增某些地區和日期的篩選器。 

![新增個人的書籤。](media/end-user-bookmarks/power-bi-add-personal.png)

**Power BI**建立書籤，並為其提供泛型名稱或您所輸入的名稱。 您可以*重新命名*，*刪除*，或*更新*選取書籤名稱旁的省略符號，然後從出現的功能表中選取一個動作的書籤。

一旦您有一個書籤時，可以顯示，只要選取中的書籤**書籤**窗格。 

![新增個人的書籤。](media/end-user-bookmarks/power-bi-personal-bookmark.png)


<!--
## Arranging bookmarks
As you create bookmarks, you might find that the order in which you create them isn't necessarily the same order you'd like to present them to your audience. No problem, you can easily rearrange the order of bookmarks.

In the **Bookmarks** pane, simply drag-and-drop bookmarks to change their order, as shown in the following image. The yellow bar between bookmarks designates where the dragged bookmark will be placed.

![Change bookmark order by drag-and-drop](media/desktop-bookmarks/bookmarks_06.png)

The order of your bookmarks can become important when you use the **View** feature of bookmarks, as described in the next section. 

-->

## <a name="bookmarks-as-a-slide-show"></a>以投影片放映書籤
若要顯示或書籤，檢視訂單中，選取**檢視**從**書籤**窗格，即可開始投影片放映。

在 [檢視]  模式中，有一些需要注意的功能：

1. 書籤的名稱會出現在畫布底部的書籤標題列中。
2. 書籤標題列的箭號可讓您移至下一個或上一個書籤。
3. 您可以從 [書籤]  窗格中選取 [結束]  ，或選取可在書籤標題列中找到的 **X**，來結束 [檢視]  模式。 

![書籤投影片放映](media/end-user-bookmarks/power-bi-bookmark-slideshow.png)

當您在 [檢視]  模式時，您可以關閉 [書籤]  窗格 (藉由按一下該窗格上的 X)，為您的簡報提供更多空間。 此外，在 [檢視]  模式中，所有視覺效果都是互動式，並可用於交叉醒目提示，就像是與其互動一樣。 

<!--
## Visibility - using the Selection pane
With the release of bookmarks, the new **Selection** pane is also introduced. The **Selection** pane provides a list of all objects on the current page and allows you to select the object and specify whether a given object is visible. 

![Enable the Selection pane](media/desktop-bookmarks/bookmarks_08.png)

You can select an object using the **Selection** pane. Also, you can toggle whether the object is currently visible by clicking the eye icon to the right of the visual. 

![Selection pane](media/desktop-bookmarks/bookmarks_09.png)

When a bookmark is added, the visible status of each object is also saved based on its setting in the **Selection** pane. 

It's important to note that **slicers** continue to filter a report page, regardless of whether they are visible. As such, you can create many different bookmarks, with different slicer settings, and make a single report page appear very different (and highlight different insights) in various bookmarks.


## Bookmarks for shapes and images
You can also link shapes and images to bookmarks. With this feature, when you click on an object, it will show the bookmark associated with that object. This can be especially useful when working with buttons; you can learn more by reading the article about [using buttons in Power BI](desktop-buttons.md). 

To assign a bookmark to an object, select the object, then expand the **Action** section from the **Format Shape** pane, as shown in the following image.

![Add bookmark link to an object](media/desktop-bookmarks/bookmarks_10.png)

Once you turn the **Action** slider to **On** you can select whether the object is a back button, a bookmark, or a Q&A command. If you select bookmark, you can then select which of your bookmarks the object is linked to.

There are all sorts of interesting things you can do with object-linked bookmarking. You can create a visual table of contents on your report page, or you can provide different views (such as visual types) of the same information, just by clicking on an object.

When you are in editing mode you can use ctrl+click to follow the link, and when not in edit mode, simply click the object to follow the link. 


## Bookmark groups

Beginning with the August 2018 release of **Power BI Desktop**, you can create and use bookmark groups. A bookmark group is a collection of bookmarks that you specify, which can be shown and organized as a group. 

To create a bookmark group, hold down the CTRL key and select the bookmarks you want to include in the group, then click the ellipses beside any of the selected bookmarks, and select **Group** from the menu that appears.

![Create a bookmark group](media/desktop-bookmarks/bookmarks_15.png)

**Power BI Desktop** automatically names the group *Group 1*. Fortunately, you can just double-click on the name and rename it to whatever you want.

![Rename a bookmark group](media/desktop-bookmarks/bookmarks_16.png)

With any bookmark group, clicking on the bookmark group's name only expands or collapses the group of bookmarks, and does not represent a bookmark by itself. 

When using the **View** feature of bookmarks, the following applies:

* If the selected bookmark is in a group when you select **View** from bookmarks, only the bookmarks *in that group* are shown in the viewing session. 

* If the selected bookmark is not in a group, or is on the top level (such as the name of a bookmark group), then all bookmarks for the entire report are played, including bookmarks in any group. 

To ungroup bookmarks, just select any bookmark in a group, click the ellipses, and then select **Ungroup** from the menu that appears. 

![Ungroup a bookmark group](media/desktop-bookmarks/bookmarks_17.png)

Note that selecting **Ungroup** for any bookmark from a group takes all bookmarks out of the group (it deletes the group, but not the bookmarks themselves). So to remove a single bookmark from a group, you need to **Ungroup** any member from that group, which deletes the grouping, then select the members you want in the new group (using CTRL and clicking each bookmark), and select **Group** again. 
-->





## <a name="limitations-and-considerations"></a>限制與考量
在本版的**書籤**中，有幾點限制和考量要留意。

* 大部分的自訂視覺效果都可以和書籤搭配使用。 如果您在使用書籤和自訂視覺效果時遇到問題，請連絡該自訂視覺效果的建立者，並請他們將書籤的支援新增到其視覺效果。 
* 如果您在建立書籤之後將視覺效果新增至報表頁面，視覺效果就會以其預設狀態顯示。 換句話說，如果您在先前建立書籤的頁面中引進交叉分析篩選器，交叉分析篩選器就會以其預設狀態運作。
* 在建立書籤之後移動視覺效果的結果會反映在書籤中。 
* 一般而言，您的書籤不會影響如果報表*設計工具*更新或重新發行報表。 不過，如果設計工具會對報表，例如移除書籤，所使用的欄位中的重大變更然後您會收到一則錯誤訊息，下次您嘗試開啟該書籤。 

<!--
## Next steps
spotlight?
-->
