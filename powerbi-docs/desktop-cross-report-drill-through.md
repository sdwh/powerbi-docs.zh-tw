---
title: 在 Power BI Desktop 中使用跨報表鑽研
description: 了解如何在 Power BI Desktop 中，從一個報表鑽研至另一個
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7189ef77446446b56b1dcb55b43b022d0fc5c057
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2020
ms.locfileid: "73868766"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>在 Power BI Desktop 中使用跨報表鑽研

您可以使用 Power BI Desktop 中的跨報表鑽研功能，依據內容從一個報表跳到另一個報表。 只要報表位於 Power BI 服務中的相同工作區或應用程式內，就能使用此功能。 使用跨報表鑽研來連接具有相關內容的兩個或多個報表，並且隨跨報表連線傳遞篩選內容。 在本文中，您將了解如何設定 Power BI 報表的跨報表鑽研，以及使用者在使用跨報表鑽研時會得到的體驗。

![Power BI Desktop 鑽研選項的螢幕擷取畫面](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

在開始設定和使用跨報表鑽研之前，請務必先了解下列定義：

* **來源視覺效果：** 藉由使用視覺效果操作功能表叫用鑽研動作的視覺效果。
* **來源報表：** 包含跨報表鑽研來源視覺效果的報表。
* **目標頁面：** 使用者起始鑽研動作之後會登陸的頁面。
* **目標報表：** 包含跨報表鑽研目標頁面的報表。


> [!NOTE]
> 您可以使用 Power BI Desktop 中的跨報表鑽研功能，依據內容從一個報表跳到另一個報表。 只要報表位於 Power BI 服務中的相同工作區或應用程式內，就能使用此功能。 這不適用於在 [我的工作區]  中存取個別的共用報表時 ([與我共用報表](service-share-dashboards.md#share-a-dashboard-or-report))；而是必須在原先共用報表的工作區中存取報表。


## <a name="enable-cross-report-drillthrough"></a>啟用跨報表鑽研

若要讓報表成為跨報表鑽研的目標，您必須在 [選項]  視窗中為該報表啟用此功能。 移至 [檔案]   > [選項及設定]   > [選項]  ，然後移至頁面左邊底端附近的 [報表設定]  。

選取 [允許此報表中的視覺效果使用其他報表中的鑽研目標]  核取方塊，如下列影像所示。

![[選項] 視窗的螢幕擷取畫面，其中 [報表設定] 已醒目提示](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

現在已啟用跨報表鑽研。

## <a name="set-up-cross-report-drillthrough"></a>設定跨報表鑽研

設定跨報表鑽研類似於在報表中設定鑽研。 在目標頁面上啟用鑽研，即可讓其他視覺效果將該頁面設定為鑽研目標。 如需在單一報表內建立鑽研的步驟，請參閱[在 Power BI Desktop 中使用鑽研](desktop-drillthrough.md)。

若要開始設定程序，您必須採取幾個初始步驟：

* 設定可以從工作區或應用程式中其他報表存取的鑽研目標頁面。
* 允許報表在自己的報表外查看鑽研頁面。

在 [視覺效果]  窗格的 [欄位]  區段中尋找鑽研選項，如下列影像所示。

![[視覺效果] 窗格的螢幕擷取畫面，其中 [鑽研] 選項已醒目提示](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

為頁面啟用鑽研的第一個步驟是驗證來源和目標報表的資料模型。 請確定： 

* 您想要傳遞的欄位存在於這兩個資料模型中。
* 欄位名稱，以及它們所屬資料表的名稱是相同的 (字串也必須相符，而且區分大小寫)。

例如，如果您想要在「地理位置」  資料表的「國家/地區」  欄位上傳遞篩選，則兩個模型都必須有「地理位置」  資料表和「國家/地區」  欄位。 否則，您必須更新基礎模型中的欄位名稱或資料表名稱。 只更新欄位的顯示名稱，無法讓跨報表鑽研正常運作。 (請注意，每個報表中的結構描述不一定要完全相同)。

若要開始設定，您必須準備好目標頁面。 在 Power BI Desktop 中，移至頁面，並確定 [跨報表]  鑽研開關設定為 [開啟]  。 

![[跨報表] 開關設定為 [開啟] 的螢幕擷取畫面](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

接下來，將您想要用來作為鑽研目標的欄位拖曳到畫布上。 選取您要將欄位當作類別使用，或當作摘要像是量值。 此時，您可以選取是否要停用視覺效果的 [保留所有篩選]  開關。 如果您不想要將其他已套用篩選從來源視覺效果傳遞至目標鑽研視覺效果，請選取 [關閉]  。

> [!NOTE]
> 如果您只將頁面用於跨報表鑽研，則應該刪除自動新增的 [上一頁]  按鈕。 [上一頁]  按鈕僅適用於單一報表內導覽。 

設定視覺效果之後，如果您是在 Power BI 服務中，請務必儲存報表，如果您是使用 Power BI Desktop，請儲存並發行報表。

上一節描述如何啟用 Power BI Desktop 的跨報表鑽研 (在 [選項]  視窗中)。 如果您使用 Power BI 服務建立跨報表鑽研目標，必須執行下列步驟才能啟用跨報表鑽研： 

1. 選取您的目標報表和來源報表所在的工作區。
2. 選取 [報表]  。
3. 選取來源報表的**設定**圖示。
4. 確認跨報表鑽研開關為 [開啟]  。
5. 儲存您的報表。

這樣就大功告成了！ 您的報表已經可使用跨報表鑽研體驗。 

在下節中，我們會從使用者的觀點來看體驗。

## <a name="cross-report-drillthrough-experience"></a>跨報表鑽研體驗

當您在設定報表的跨報表鑽研體驗時，可以讓該功能可供使用。

在 Power BI 服務中選取來源報表，然後選取使用您在設定目標頁面時所指定的方式來使用該欄位的視覺效果。 接下來，以滑鼠右鍵按一下資料點以開啟視覺效果操作功能表，然後選取 [鑽研]  。

![Power BI 服務中來源報表的螢幕擷取畫面，其中 [鑽研] 已醒目提示](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

您接著會在目標跨報表鑽研頁面中看到結果，就和您在建立目標時所設定的一樣。 系統會根據鑽研設定來篩選結果。

> [!IMPORTANT]
> Power BI 會快取跨報表鑽研目標。 如果您進行變更之後，鑽研目標沒有如預期般顯示，請務必重新整理瀏覽器。 

跨報表目標會以下列方式格式化： 

`Target Page Name [Target Report Name]`

選取您想要鑽研的目標頁面之後，Power BI 會移至該頁面。 它會根據目標頁面的設定，將篩選內容一起傳遞至頁面。 

來自來源視覺效果的篩選內容可能包含下列項目： 

* 影響來源視覺效果的報表、頁面和視覺效果層級篩選。 
* 會影響來源視覺效果的交叉篩選和交叉醒目提示。 
* 頁面上的交叉分析篩選器和同步交叉分析篩選器。
* URL 參數。

當您進行鑽研登陸目標報表時，Power BI 只會將篩選套用到所找到欄位名稱和資料表名稱字串完全相符的欄位。 Power BI 不會套用來自目標報表的粘性篩選。 不過，它會套用您的預設個人書籤 (如果有)。 例如，如果您的預設個人書籤包含「國家/地區 = 美國」  的報表層級篩選，Power BI 會先套用該篩選，然後再套用來自來源視覺效果的篩選內容。 

針對跨報表鑽研，Power BI 會將篩選內容傳遞至目標報表中的所有標準頁面。 Power BI 不會傳遞工具提示頁面的篩選內容，因為工具提示頁面是根據叫用工具提示的來源視覺效果進行篩選。

如果您想要在跨報表鑽研動作之後返回來源報表，請使用瀏覽器的**上一頁**按鈕。 

## <a name="next-steps"></a>後續步驟

您可能也會對下列文章感興趣：

* [使用 Power BI Desktop 交叉分析篩選器](visuals/power-bi-visualization-slicers.md)
* [在 Power BI Desktop 中使用鑽研](desktop-drillthrough.md)

