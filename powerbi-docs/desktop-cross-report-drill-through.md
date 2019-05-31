---
title: 在 Power BI Desktop 中使用跨報表鑽研
description: 了解如何從鑽研報表至 Power BI Desktop 中的另一個
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375202"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>在 Power BI Desktop 中使用跨報表鑽研

使用 Power BI Desktop 中跨報表的鑽研功能，您可以內容從跳一份報表至另一個報表。 只要報表位於相同的工作區或在 Microsoft Power BI 服務中的應用程式，也是如此。 連線已建立關聯的內容，兩個或多個報表，並傳遞以及跨報表連接的篩選內容，請使用跨報表鑽研。 在本文中，您了解如何設定跨報表鑽研 Power BI 報表，以及哪些使用者體驗自行使用跨報表鑽研時。

![Power BI Desktop 的螢幕擷取畫面鑽研選項](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

下列定義一定要了解，我們開始之前設定並使用跨-報表鑽研：

* **來源視覺效果：** 使用 visual 的操作功能表叫用的鑽研動作的視覺效果。
* **來源報表：** 包含來源視覺效果，跨報表鑽研報表。
* **目標頁面：** 使用者登陸起始鑽研動作後的頁面。
* **目標報表：** 報表包含跨報表鑽研目標 頁面。

## <a name="enable-cross-report-drillthrough"></a>啟用跨報表的鑽研

若要啟用跨報表鑽研的目標報表，您必須啟用該報表的功能**選項**視窗。 移至**檔案** > **選項和設定** > **選項**，然後移至**報告設定**附近頁面底部的左側。

選取 **允許使用從其他報表的鑽研目標的這份報表中的視覺效果**核取方塊，如下圖所示。

![選項的螢幕擷取畫面 視窗，其中反白顯示的報表設定](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

跨報表鑽研現在已啟用。

## <a name="set-up-cross-report-drillthrough"></a>設定跨報表鑽研

設定跨報表鑽研是類似於設定鑽研報表內。 上啟用鑽研目標 頁面中，允許為目標的已啟用的鑽研頁面其他視覺效果。 如需建立在單一報表的鑽研的步驟，請參閱[在 Power BI Desktop 中使用鑽研](desktop-drillthrough.md)。

若要開始安裝程序，您必須採取幾個初始步驟：

* 設定鑽研目標頁面上，從其他報表中的工作區或應用程式可供存取。
* 允許報表以查看來自外部它自己的報表的鑽研頁面。

尋找中的鑽研選項**欄位**一節**視覺效果** 窗格中，如下圖所示。

![螢幕擷取畫面的視覺效果 窗格中，反白顯示的鑽研選項](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

啟用鑽研頁面的第一個步驟是驗證來源和目標報表的資料模型。 請確定： 

* 您想要傳遞的欄位會存在於這兩種資料模型。
* 欄位的名稱和其所屬的資料表的名稱完全相同 （字串也必須相符，而且區分大小寫）。

比方說，如果您想要在欄位上傳遞篩選條件*國家/地區*資料表中*Geography*，這兩種模型必須具有*Geography*資料表，和*國家/地區*資料表中的欄位。 如果沒有，您必須更新的欄位名稱或基礎模型中的資料表名稱。 只要更新欄位的顯示名稱就無法正常運作的跨報表鑽研。 （請注意，每份報表中的結構描述不一定要完全相同）。

若要開始使用安裝程式，您需要準備目標頁面。 在 Power BI Desktop 中，移至頁面，並確定**跨報表**鑽研切換設定為**上**。 

![跨報表切換設定為上的螢幕擷取畫面](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

接下來，拖曳您想要做為拖曳到畫布上的鑽研目標的欄位。 選取您想要用來做為類別目錄，或等量值彙總的欄位。 此時，您可以在其中選取您是否想要停用**保留所有篩選**切換視覺效果。 如果您不想將其他套用的篩選來源的視覺目標鑽研 visual，選取**關閉**。

> [!NOTE]
> 如果您使用頁面只能跨報表鑽研，您應該刪除**回**會自動新增的按鈕。 **回**按鈕只適用於在單一報表 nagivation 的。 

設定視覺效果之後，請確定您儲存報表，如果您是在 Power BI 服務中，或儲存並發行報表，如果您使用 Power BI Desktop。

上一節說明如何為 Power BI Desktop 中啟用跨報表的鑽研 (在**選項**視窗)。 如果您使用 Power BI 服務來建立跨報表鑽研目標，以啟用跨報表鑽研，您必須： 

1. 選取您的目標報表和來源報表所在的工作區。
2. 選取 **報表**。
3. 選取 **設定**來源報表的圖示。
4. 請確定跨報表鑽研切換**上**。
5. 儲存報表。

這樣就大功告成了！ 您的報表可供跨報表鑽研體驗。 

在下一步 區段中，我們看看從使用者的觀點來看的體驗。

## <a name="cross-report-drillthrough-experience"></a>跨報表鑽研體驗

當您設定報表的跨報表鑽研體驗時，您可以輸入要使用的功能。

在 Power BI 服務中，選取來源報表，然後選取 視覺效果會在您指定當您設定 目標 頁面的方式中的欄位。 接下來，以滑鼠右鍵按一下資料點，以開啟視覺化的操作功能表，然後選取**鑽研**。

![在 Power BI 服務中，來源報表的鑽研反白顯示與螢幕擷取畫面](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

就像將它們設定您在建立目標時，您接著會看到目標的跨報表鑽研頁面上，將結果。 根據鑽研設定篩選結果。

> [!IMPORTANT]
> Power BI 會快取跨報表鑽研目標。 如果您進行變更，請確定您重新整理瀏覽器，如果您沒有看到 鑽研目標，如預期般運作。 

跨報表的目標是以下列方式格式化： 

`Target Page Name [Target Report Name]`

選取您要鑽研的目標頁面之後，Power BI 就會前往該頁面。 它會傳送目標頁面設定為基礎的篩選內容。 

自來源視覺效果的篩選內容可包含下列各項： 

* 報表、 頁面和視覺效果層級的篩選會影響來源視覺效果。 
* 交叉篩選及交叉醒目提示會影響來源視覺效果。 
* 交叉分析篩選器上的頁面和同步處理交叉分析篩選器。
* URL 參數。

當您進入目標報表的鑽研時，Power BI 僅適用於篩選器，它找到確切的字串比對欄位名稱] 和 [資料表名稱的欄位。 Power BI 不會從目標報表套用自黏便箋的篩選條件。 不過，如果有的話，它，套用預設個人書籤。 例如，如果您的預設個人書籤包含的報表層級篩選*國家/地區 = 美國*，Power BI 會套用該篩選第一次，自來源視覺效果套用篩選內容之前。 

跨報表鑽研 Power BI 會將篩選內容傳遞給目標報表中的所有標準網頁。 Power BI 未通過篩選內容的工具提示頁面，因為工具提示頁面上叫用的工具提示來源視覺效果篩選基礎。

如果您想要跨報表鑽研動作之後，回到來源報表，使用的瀏覽器**回** 按鈕。 

## <a name="next-steps"></a>後續步驟

您可能也會對下列文章感興趣：

* [使用 Power BI Desktop 交叉分析篩選器](visuals/power-bi-visualization-slicers.md)
* [在 Power BI Desktop 中使用鑽研](desktop-drillthrough.md)

