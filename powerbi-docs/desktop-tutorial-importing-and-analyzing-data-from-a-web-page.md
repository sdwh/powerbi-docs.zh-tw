---
title: "教學課程： 使用 Power BI Desktop 從網頁匯入和分析資料"
description: "教學課程： 使用 Power BI Desktop 從網頁匯入和分析資料"
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: c5139c6f9f7b2098b51a608fb7719f371173c291
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="analyzing-web-page-data-using-power-bi-desktop-tutorial"></a>使用 Power BI Desktop 分析網頁資料 (教學課程)
在本教學課程中，您將學習如何從網頁上匯入資料的資料表，和建立報表以視覺化方式檢視這項資料。 做為此程序的一部分，您可以在網頁上可用的資料表之間瀏覽，並套用資料轉換步驟，將資料表轉換為新的圖形。

 本文內容：

* **工作 1：**連接到 Web 資料來源
* **工作 2：**在查詢檢視中塑造資料
  * 步驟 1：移除其他資料行，只顯示感興趣的資料行
  * 步驟 2：替換值以清除選取資料行的值
  * 步驟 3：篩選資料行中的值
  * 步驟 4：重新命名資料行
  * 步驟 5：篩選資料行中的 null 值
  * 步驟 6：重新命名 查詢
  * 已建立的查詢步驟
* **工作 3：**使用報表檢視建立視覺效果
  * 步驟 1：載入查詢至報表
  * 步驟 2：建立地圖視覺效果

## <a name="task-1-connect-to-a-web-data-source"></a>工作 1：連接到 Web 資料來源
 在工作 1 中，您會從下列位置的 UEFA 歐洲足球錦標賽 Wikipedia 頁面匯入聯賽摘要資料表：http://en.wikipedia.org/wiki/UEFA\_European\_Football\_Championship

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

### <a name="add-a-wikipedia-page-data-source"></a>加入 Wikipedia 頁面資料來源
1. 在 [開始使用] 對話方塊或 [常用] 功能區索引標籤中，選取 [取得資料]。
2. 這會帶出 [取得資料]  對話方塊，以便您從各種資料來源挑選，將資料匯入 Power BI Desktop。 我們將會選取 [Web]  ，它位在 [所有]  或 [其他]  群組。
3. 在 [Web 內容] 對話方塊的 [URL] 文字方塊中，貼上 Wikipedia URL (http://en.wikipedia.org/wiki/UEFA\_European\_Football\_Championship)。
4. 按一下 [確定] 。

建立網頁的連線後，您可在 [導覽器]  對話方塊看到此 Wikipedia 上的可用資料表清單。 您可以按一下每個資料表以預覽資料。

在 [導覽器]  左窗格中選取此聯賽摘要結果的 [結果 [編輯]]  資料表，或選取 [結果 [編輯]]  資料表，然後選取 [編輯] 。 這可讓我們要重新塑造這份資料表，然後才載入至報表，因為資料不在我們分析所需的圖形之內。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)

這會讓資料表預覽處在 [查詢] 檢視中，我們可以在其中套用一組轉換步驟來清除資料。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)

## <a name="task-2-shape-data-in-the-subject-table"></a>工作 2：主題資料表中的圖形資料
現在您已經針對資料查詢選取了主題資料表，您會了解如何執行各種資料圖形和清理步驟。

**步驟 1：**移除其他資料行，只顯示感興趣的資料行

在此步驟中，您會移除所有資料行，除了 [年]  和 [最終得獎者] 以外。

1. 在 **查詢預覽** 方格中，選取 **Year** 和 **Final Winners** 資料行 (使用 **CTRL** + **按一下滑鼠左鍵**)。
2. 以滑鼠右鍵按一下 [查詢預覽]  方格中的資料行標頭，然後按一下 [移除其他資料行]  來移除未選取的資料行。 請注意這項作業也適用於 [管理資料行]  群組的 [主資料夾]  功能區索引標籤 。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

**步驟 2：**取代值以整理選取資料行中的值

在此步驟中，您會取代 [年]  資料行的 [詳細資料] 後置詞。 請注意這個後置詞位於新行，使其在資料表預覽中無法見到。 不過，如果您在 [年] 資料行具有數值的資料格按一下，您會在詳細檢視中看到完整值。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage5.png)

1. 選取 [年]  資料行。
2. 在 [查詢檢視]  功能區上，按一下 [主資料夾]  索引標籤的 [取代值]  ，或以滑鼠右鍵按一下 [年]  直條圖，然後按一下 [取代值]  將詳細資料取代為空白文字。
3. 在 [取代值]  對話方塊的 [要尋找的值]  文字方塊輸入詳細資料，並將 [取代為]  文字方塊保留空白。
4. 按一下 [確定] 。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

 **步驟 3：**篩選資料行中的值

在此步驟中，您篩選 [年]  資料行，顯示不包含「年」的資料列。

1. 按一下 [年]  資料行之篩選下拉式清單的箭號。
2. 在 [篩選]  下拉式清單中，清除 [年]  選項。
3. 按一下 [確定] 。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

**步驟 4：**重新命名資料行

現在我們已清除在 [年]  資料行中的資料，我們會使用 [最終得獎者]  資料行。

因為我們只會查看得獎者清單，所以我們可以重新命名此資料行為 **國家/地區**。

1. 選取 [查詢] 預覽中的 [最終得獎者]  資料行。
2. 在 [查詢檢視]  功能區的 [轉換]  索引標籤和 [任何資料行]  群組，您會找到 [重新命名] 。
3. 如此可讓資料行名稱可以編輯。 我們會重新命名此資料行為 **國家/地區**。

**步驟 5：**篩選資料行中的 Null 值

我們也要篩選出 [國家/地區]  資料行的 null 值。 若要這樣做，我們可以使用在步驟 3 中看到的篩選條件功能表，或者我們可以：

1. 在 [國家/地區]  資料行，以滑鼠右鍵按一下其中一個包含 null 值的資料格。
2. 在內容功能表中選取 [文字篩選] **\> [不等於]**。
3. 這會建立新的篩選步驟來移除 [國家/地區]  資料行中有 null 值的資料列。

**步驟 6：**命名查詢

在此步驟中，您將最終查詢命名為 **歐洲盃得獎者**。

1. 在 [查詢設定]  窗格的 [名稱]  文字方塊中輸入 **歐洲盃得獎者**。
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

## <a name="task-3-create-visualizations-using-the-report-view"></a>工作 3：建立使用報表檢視的視覺效果
現在我們已將資料轉換為圖形，供我們的分析所用，我們可以將產生的資料表載入報表，並建立一些視覺效果。

**步驟 1** ：載入查詢到您的報表

若要將查詢結果載入至 Power BI Desktop 並建立報表，我們要從 [常用] 功能區選取 [關閉並載入]。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)

這樣會觸發查詢的評估和將資料表輸出傳送至報表。 在 Power BI Desktop 選取 **報表** 圖示，以查看在 [報表] 檢視中的 Power BI Desktop。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage10.png)

您可以在 [報表檢視]  右邊的 [欄位窗格] 看到產生的資料表欄位。

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)

**步驟 2：**建立地圖視覺效果

若要建立視覺效果，我們可以將欄位從 [欄位清單]  拖曳到 [報表畫布] 。

1. 將 [國家/地區]  欄位拖曳至 [報表畫布] 。 如此會在 [報表畫布] 建立新的視覺效果。 在此情況下，由於我們有一份國家/地區清單，所以它會建立 [地圖視覺效果] 。
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage12.png)
2. 我們可以在 [視覺效果]  窗格按一下不同的圖示，輕鬆變更視覺效果的類型。
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage13.png)
3. 我們要跟著 [地圖]  的地圖視覺效果類型，我們也可以藉由拖曳其中一個視覺效果的邊角到所需大小，來調整視覺效果大小。
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)
4. 請注意目前地圖中所有點的大小相同。 我們想要變更為贏了較多場歐洲盃聯賽的國家/地區會在地圖中以較大的點顯示。 為了這樣做，我們可以將 [欄位清單]  中的 [年]  欄位拖曳至 [欄位窗格]  下半部的 [值] 方塊。
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)

如您所見，自訂報表中的視覺效果很容易，以便依您想要的方式呈現資料。 Power BI Desktop 提供流暢的端對端體驗，包括從各種資料來源取得資料，調整以符合您的分析需求，乃至於以豐富且互動的方式將此資料視覺化。 準備好報表之後，您可以[將其上傳至 Power BI](desktop-upload-desktop-files.md) 並建立以此為基礎的儀表板，您可以與其他 Power BI 使用者共用該儀表板。

這是 **從 Web 匯入資料** 教學課程的總結。 您可以從[這裡](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Data_From_The_Web.pbix)下載完整 Power BI Desktop 檔案.

## <a name="where-else-can-i-get-more-information"></a>還可以從何處取得更多資訊？
* [閱讀其他 Power BI Desktop 教學課程](http://go.microsoft.com/fwlink/?LinkID=521937)
* [觀看 Power BI Desktop 影片](http://go.microsoft.com/fwlink/?LinkID=519322)
* [瀏覽 Power BI 論壇](http://go.microsoft.com/fwlink/?LinkID=519326)
* [閱讀 Power BI 部落格](http://go.microsoft.com/fwlink/?LinkID=519327)

