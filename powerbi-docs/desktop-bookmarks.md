---
title: "使用 Power BI 中的書籤 (預覽)"
description: "Power BI Desktop 中的書籤可讓您儲存報表中的檢視和設定，然後建立類似故事的簡報"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: e60ff6d06e4ac0cddf398ccfc1d30e4d97e0773c
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi-preview"></a>在 Power BI 中使用書籤來分享深入解析並建立故事 (預覽)
您可以使用 Power BI 中的**書籤**來擷取目前設定的報表頁面檢視 (包括視覺效果的篩選和狀態)，稍後只要選取儲存的書籤，就可以返回該狀態。 

您也可以建立書籤集合，依您想要的順序加以排列，然後在簡報中逐步執行每個書籤，以醒目提示一系列深入解析，或您想要透過視覺效果和報表述說的故事。 

![Power BI 中的書籤](media/desktop-bookmarks/bookmarks_01.png)

書籤有許多用途。 您可以使用書籤來追蹤自己建立報表的進度 (新增、刪除和重新命名書籤都很容易)，您也可以建立書籤來建立依序逐步執行書籤之類似 PowerPoint 的簡報，以便透過報表述說故事。 此外，根據您認為書籤最適合使用的方式，可能還有其他用途。

### <a name="enable-the-bookmarks-preview"></a>啟用書籤預覽
從 **2017 年 10 月**版的 **Power BI Desktop** 開始，您可以試用新的**書籤**功能，您也可以針對 **Power BI 服務**中已啟用書籤的報表來試用這項功能。 若要啟用這項預覽功能，請選取 [檔案] > [選項及設定] > [選項] > [預覽功能]，然後選取 [書籤] 旁的核取方塊。 您完成選取後必須重新啟動 Power BI Desktop。

![啟用 [選項] 視窗中的 [書籤]](media/desktop-bookmarks/bookmarks_02.png)

完成選取後，必須重新啟動 **Power BI Desktop**。

## <a name="using-bookmarks"></a>使用書籤
若要使用書籤，請選取 [檢視] 功能區，然後選取 [書籤窗格] 方塊。 

![在 [檢視] 功能區中開啟並顯示 [書籤窗格]。](media/desktop-bookmarks/bookmarks_03.png)

當您建立書籤時，下列項目會與書籤一起儲存：

* 目前頁面
* 篩選
* 交叉分析篩選器
* 排序次序
* 鑽研位置
* 可見度 (使用 [選取] 窗格之物件的可見度)
* 任何可見物件的焦點或**聚焦**模式

書籤目前無法儲存交叉醒目提示狀態。 

以您想要在書籤中顯示的方式來設定報表頁面。 將報表頁面和視覺效果排列成您想要的方式之後，從 [書籤] 窗格中選取 [新增] 以新增書籤。 

![新增書籤](media/desktop-bookmarks/bookmarks_04.png)

**Power BI Desktop** 會建立書籤，並為其提供泛型名稱。 您可以輕鬆地「重新命名」書籤、將它「刪除」或「更新」書籤，方法是選取書籤名稱旁的省略符號，然後從出現的功能表中選取一個動作。

![使用省略符號來選取書籤的子功能表](media/desktop-bookmarks/bookmarks_05.png)

一旦有了書籤，只要在 [書籤] 窗格中按一下書籤，就可以將它顯示。 

## <a name="arranging-bookmarks"></a>排列書籤
當您建立書籤時，您可能會發現您建立的順序不一定是您想要呈現給對象的相同順序。 沒問題，您可以輕鬆地重新排列書籤的順序。

在 [書籤] 窗格中，只要拖放書籤就可以變更其順序，如下圖所示。 書籤之間的黃色列可指定所拖曳的書籤將要放置的位置。

![藉由拖放動作來變更書籤順序](media/desktop-bookmarks/bookmarks_06.png)

當您使用書籤的 [檢視] 功能時，書籤的順序可能會變得很重要，如下一節所述。

## <a name="bookmarks-as-a-slide-show"></a>以投影片放映書籤
當您想要依序呈現一組書籤時，您可以從 [書籤] 窗格中選取 [檢視] 以開始投影片放映。

在 [檢視] 模式中，有一些需要注意的功能：

1. 書籤的名稱會出現在畫布底部的書籤標題列中。
2. 書籤標題列的箭號可讓您移至下一個或上一個書籤
3. 您可以從 [書籤] 窗格中選取 [結束]，或選取位於書籤標題列中的 **X**，以結束 [檢視] 模式。 

![書籤的書籤標題列功能](media/desktop-bookmarks/bookmarks_07.png)

當您在 [檢視] 模式時，您可以關閉 [書籤] 窗格 (藉由按一下該窗格上的 X)，為您的簡報提供更多空間。 此外，在 [檢視] 模式中，所有視覺效果都是互動式，並可用於交叉醒目提示，就像是與其互動一樣。 

## <a name="visibility---using-the-selection-pane"></a>可見度 - 使用 [選取] 窗格
在此版書籤中，也引進了新的 [選取] 窗格。 [選取] 窗格提供目前頁面上的所有物件清單，可讓您選取物件並指定該物件是否為可見。 

![啟用 [選取] 窗格](media/desktop-bookmarks/bookmarks_08.png)

您可以使用 [選取] 窗格來選取物件。 此外，您可以按一下視覺效果右邊的眼睛圖示，來切換物件目前是否為可見。 

![[選取] 窗格](media/desktop-bookmarks/bookmarks_09.png)

新增書籤之後，也會根據其在[選取] 窗格中的設定來儲存每個物件的可見狀態。 

請務必注意，不論是否可見，**交叉分析篩選器**都會繼續篩選報表頁面。 因此，您可以使用不同的交叉分析篩選器設定來建立許多不同的書籤，然後在不同的書籤中，以非常不同的方式來顯示各個報表頁面 (並醒目提示不同的深入解析)。

## <a name="bookmarks-for-shapes-and-images"></a>圖案和影像的書籤
您也可以將圖案和影像連結至書籤。 透過這項功能，當您按一下物件時，就會顯示與該物件建立關聯的書籤。 

若要對物件指派書籤，請選取物件，然後從 [格式化圖案] 窗格中選取 [連結]，如下圖所示。

![將書籤連結新增至物件](media/desktop-bookmarks/bookmarks_10.png)

一旦您將 [連結] 滑桿移至 [開啟]，就可以選取物件為連結或為書籤。 如果您選取 [書籤]，您可以接著選取哪些書籤會與物件連結。

您可以使用物件連結書籤執行各式各樣有趣的作業。 只要按一下物件，就可以在報表頁面上建立視覺目錄，或提供不同方式 (例如視覺效果類型) 來檢視相同資訊。

當您處於編輯模式時，您可以按住 Ctrl 鍵再按一下滑鼠來追蹤連結；當您不在編輯模式時，只要按一下物件即可追蹤連結。 

## <a name="using-spotlight"></a>使用聚焦
隨書籤發行的另一項功能是**聚焦**。 使用**聚焦**，您可以提高特定圖表的注意力；例如，在 [檢視] 模式中呈現您的書籤。

讓我們來比較**聚焦**模式與**焦點**模式，看看這兩種模式有何不同。

1. 在**焦點**模式中，您可以選取**焦點模式**圖示，讓某個視覺效果填滿整個畫布。
2. 使用**聚焦**，您可以讓頁面上所有其他視覺效果淡化成近乎透明，以原始大小來醒目提示某個視覺效果。 

![比較焦點模式與聚焦模式](media/desktop-bookmarks/bookmarks_11.png)

當上圖中的視覺效果按下其**焦點**圖示時，頁面看起來如下所示：

![焦點模式](media/desktop-bookmarks/bookmarks_12.png)

相反地，當您從視覺效果的省略符號功能表中選取**聚焦**時，頁面看起來如下所示：

![聚焦模式](media/desktop-bookmarks/bookmarks_13.png)

如果在新增書籤之後選取任一模式，書籤中會保留該模式 (焦點或聚焦)。

## <a name="bookmarks-in-the-power-bi-service"></a>Power BI 服務中的書籤
當您將至少含有一個書籤的報表發行至 **Power BI 服務**時，您可以在 **Power BI 服務**中檢視這些書籤並與其互動。 針對您發行的每個報表，您必須先在報表中建立至少一個書籤，再發行報表，才能在 **Power BI 服務**中使用書籤功能。

當報表中有可用的書籤時，您可以選取 [檢視] > [選取窗格] 或 [檢視] > [書籤窗格] 來顯示個別窗格。

![在 Power BI 服務中檢視 [書籤窗格] 和 [選取窗格]](media/desktop-bookmarks/bookmarks_14.png)

在 **Power BI 服務**中，[書籤窗格] 的運作方式就像是在 **Power BI Desktop** 中一樣，包括能夠選取 [檢視] 以類似投影片放映的方式依序顯示書籤。

請注意，您必須使用灰色書籤標題列來巡覽書籤，而不是黑色箭號 (黑色箭號可讓您在報表頁面而非書籤之間移動)。

## <a name="limitations-and-considerations"></a>限制與考量
在此預覽版的**書籤**中，有幾點限制和考量要留意。

* 如果自訂視覺效果是篩選「來源」，則無法與書籤搭配使用。 如果您使用自訂視覺效果來篩選頁面上的項目 (例如標籤方塊交叉分析篩選器)，然後使用書籤返回該頁面，頁面可能會經過篩選，但不會更新自訂視覺效果以顯示頁面的篩選方式。 
* 當您建立書籤時，「不會」儲存報表窗格的交叉醒目提示狀態。 
* 如果您在建立書籤之後將視覺效果新增至報表頁面，視覺效果就會以其預設狀態顯示。 換句話說，如果您在先前建立書籤的頁面中引進交叉分析篩選器，交叉分析篩選器就會以其預設狀態運作。
* 在建立書籤之後移動視覺效果的結果會反映在書籤中。 
* 當您將報表發佈至 **Power BI 服務**時，報表中「必須」至少有一個書籤，才能在服務中使用書籤。 每個發行的報表都必須符合這項條件。
* 由於書籤目前是預覽功能，它們在[**適用於報表伺服器的 Power BI Desktop**](report-server/quickstart-create-powerbi-report.md) 上還無法使用。

## <a name="next-steps"></a>後續步驟
如需類似功能或與書籤互動的詳細資訊，請參閱下列文章：

* [在 Power BI Desktop 中使用鑽研](desktop-drillthrough.md)
* [以焦點模式顯示儀表板磚或報表視覺效果](service-focus-mode.md)

