---
title: "教學課程：使用 Power BI Desktop 的 Facebook 分析"
description: "教學課程：使用 Power BI Desktop 的 Facebook 分析"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 3642a252467d504b61eb81f82d0b96f64a24f22b
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>教學課程：使用 Power BI Desktop 的 Facebook 分析
本教學課程中，您將了解如何將資料從 **Facebook**匯入並視覺化。 在本教學課程中，您將學習如何連接到特定的 Facebook 頁面 (Power BI 頁面)、套用資料轉換步驟，並建立一些視覺效果。

以下是您要執行的步驟：

* **工作 1：** 連接至 Facebook 網頁
* **工作 2**：使用報表檢視建立視覺效果
  
  * **步驟 1**：建立樹狀圖視覺效果
* **工作 3**：在查詢檢視中塑造資料
  
  * **步驟 1**：將日期時間資料行分成兩個
  * **步驟 2**：加入相關資料表中的彙總值
* **工作 4**：使用報表檢視建立其他視覺效果
  
  * **步驟 1**：載入查詢到您的報表
  * **步驟 2**：建立折線圖和橫條圖

## <a name="task-1-connect-to-a-facebook-page"></a>**工作 1：連線至 Facebook 網頁**
在這項工作中，您要從 [Microsoft Power BI Facebook](https://www.facebook.com/microsoftbi) 網站 (URL 是：*https://www.facebook.com/microsoftbi) 匯入資料*.

任何人都可以連接到該頁面上，並遵循下列步驟 - 不需要任何特殊的認證 (除了您自己的 Facebook 帳戶以外，您在此步驟中會用到)。

![](media/desktop-tutorial-facebook-analytics/1.png)

1. 在 [開始使用] 對話方塊或 [常用] **功能區索引標籤**中，選取 [取得資料]。
2. [取得資料]  對話方塊隨即出現，讓您從各種資料來源中選取。 從 [其他]  群組選取 [Facebook]  。
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   當您選取 [連接] 時，對話方塊隨即出現，警示您使用協力廠商服務的風險。
   
   ![](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
3. 當您選取 [繼續] 後， **Facebook** 對話方塊隨即出現，您可將頁面名稱 (**microsoftbi**) 貼到 [使用者名稱]  文字方塊。 從 [連線]  下拉式清單選取 [貼文]  。
   
   ![](media/desktop-tutorial-facebook-analytics/2.png)
4. 按一下 [確定] 。
5. 當系統提示您輸入認證時，請使用您的 Facebook 帳戶登入，並允許 Power BI 存取您的帳戶。
   
   ![](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

建立對於頁面連線後，您會看到模型載入資料。 

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)

其中 **查詢編輯器** 會顯示資料。 **查詢編輯器** 是 Power BI Desktop 的一部分，但在個別視窗中載入，也是在資料連線上執行轉換的地方。

![](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)

當資料為您所需時，您可以將它載入 Power BI Desktop。 從 [常用] 功能區選取 [載入並關閉]。

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

您會看到一個對話方塊，顯示將資料載入 Power BI Desktop 資料模型的進度。

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)

載入之後，您將會進入 [報表]  檢視，其中會在右邊的 [欄位]  清單列出資料表的資料行。

![](media/desktop-tutorial-facebook-analytics/fbdesigner1.png)

## <a name="task-2-create-visualizations-using-the-report-view"></a>**工作 2：使用報表檢視建立視覺效果**
現在您已從頁面載入資料，您可以使用視覺效果，快速且輕鬆地深入了解您的資料。

**步驟 1** ：建立樹狀圖視覺效果

建立視覺效果不難，我們只要從 [欄位清單] 拖曳欄位，並放置在 [報表畫布]。

將 [type] 欄位拖曳到 [報表] 畫布。 Power BI Desktop 會在 [報表畫布] 中建立新的視覺效果。 接下來，將 \[type] 從 \[欄位] \(您剛才拖曳至 \[報表] 畫布的相同欄位) 拖曳至 [值] 區域，以建立 \[橫條圖] 視覺效果。

![](media/desktop-tutorial-facebook-analytics/fbdesigner2.png)

我們可以從 [視覺效果]  窗格選取不同的圖示，輕鬆變更視覺效果的類型。 讓我們將類型變更為 [樹狀圖]  ，方法是從 [視覺效果] 選取其圖示，如下圖所示。

![](media/desktop-tutorial-facebook-analytics/fbdesigner3.png)

接下來讓我們加入圖例，然後變更資料點的色彩。 在 [視覺效果]  窗格中選取 [格式]  圖示；[格式]  圖示看起來像畫刷。

![](media/desktop-tutorial-facebook-analytics/fbdesigner3a.png)

當您選取 [圖例] 旁的向下箭號時，此區段會展開，以顯示如何自訂所選取視覺效果的圖例。 在本案例中，我們執行下列選項：

* 將 [圖例]  滑桿移動至 [開啟]  讓圖例出現
* 從 [圖例位置]  下拉式清單選取 [右邊] 
* 將 [標題]  滑桿移動至 [開啟]  ，讓圖例的標題出現
* 在 [類型]  輸入圖例的標題

在下圖中，已經進行這些設定，且會在視覺效果中反映。

![](media/desktop-tutorial-facebook-analytics/fbdesigner3b.png)

接下來讓我們變更其中一個資料點的色彩。 這個連結資料點應該是藍色，所以很接近超連結的常見色彩。

選取 [資料色彩]  旁邊的箭頭，以展開該區段。 資料點隨即顯示，同時在每個顏色旁都有選取項目箭頭，讓我們為每個資料點選取不同色彩。

![](media/desktop-tutorial-facebook-analytics/fbdesigner3c.png)

當您按一下任何資料點旁 [色彩] 方塊的向下箭號時，[色彩選擇] 對話方塊隨即出現，讓您選擇色彩。 在此情況下，我們將選擇淺藍色。

![](media/desktop-tutorial-facebook-analytics/fbdesigner3d.png)

這樣看起來好多了。 在下圖中，您可以看到色彩如何套用至視覺效果中的資料點，且圖例也會自動更新，如同其在 [資料色彩]  區段的色彩一樣。

![](media/desktop-tutorial-facebook-analytics/fbdesigner3e.png)

## <a name="task-3-shape-data-in-the-table"></a>**工作 3：將資料表中的資料定形**
現在您已匯入選取的資料表，而且您開始以視覺化方式檢視，您可能會發現您需要執行各種資料圖形和清理步驟，以充分運用您的資料。

**步驟 1** ：將日期時間資料行分成兩個

在此步驟中，您將分割 **created\_time** 資料行，以取得日期和時間值。 每當您進入 Power BI Desktop，並且想要修改現有的查詢，您就需要啟動 [查詢編輯器] 。 若要這樣做，請從 [主資料夾]  索引標籤選取 [編輯查詢]  。

![](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)

1. 在 [查詢編輯器] 方格中，捲動至右方，直到您找到 **created\_time** 資料行
2. 以滑鼠右鍵按一下 [查詢預覽] 方格中的資料行標頭，然後按一下 [分割資料行]**\> [依分隔符號]** 以分割資料行。 在分隔符號下拉式清單中選擇 [自訂]，然後輸入 **"T"**。請注意這項作業也適用於 [常用] 功能區索引標籤的 [管理資料行] 群組。
   
   ![](media/desktop-tutorial-facebook-analytics/9.png)
   
   ![](media/desktop-tutorial-facebook-analytics/10.png)
3. 將建立的資料行分別重新命名為 **created\_date** 和 **created\_time**。
4. 選取新的資料行 **created\_time**，**** 然後在 [查詢檢視] 功能區中，瀏覽至 [加入資料行] 索引標籤，並在 [日期和時間] 群組下選取 [時間] **\> [小時]**。 這會新增新的資料行，其中只有時間的小時部分。
   
   ![](media/desktop-tutorial-facebook-analytics/11.png)
5. 將新的 **Hour** 資料行類型變更為 [整數]，方法是瀏覽至 [常用] 索引標籤，並選取 [資料類型] 下拉式清單，或以滑鼠右鍵按一下資料行，並選取 [轉換] **\> [整數]**。
   
   ![](media/desktop-tutorial-facebook-analytics/12.png)

**步驟 2** ：加入相關資料表中的彙總值

在此步驟中，您會加入巢狀值的共用計數，以便您使用於視覺效果中。

1. 繼續向右捲動，直到您看到 [shares]  資料行。 巢狀的值表示我們需要做其他轉換才能取得實際的值。
2. 在資料行標頭右上角選取 ![](media/desktop-tutorial-facebook-analytics/14.png) 圖示以開啟 [展開/彙總] 產生器。 選取 [計數]  並點擊 [確定] 。 這會在資料表新增每個資料列的共用計數。
   
   ![](media/desktop-tutorial-facebook-analytics/15.png)
   
   資料載入之後，將資料行重新命名為 **shares** ，方法是用滑鼠右鍵按一下資料行名稱，以滑鼠右鍵在資料行或在 [查詢檢視]  功能區上按一下，選取 [轉換]  索引標籤和 [任何資料行]  群組下的 [重新命名]  。
3. 最後，變更新的 **shares** 資料行類型為 **整數**。 您可以選取資料行並變更類型，方法是以滑鼠右鍵按一下資料行，並選取 [轉換] **\>[整數]** 或 **** 瀏覽至 [常用] 索引標籤，並選取 [資料類型] 下拉式清單。

### <a name="query-steps-created"></a>已建立的查詢步驟
當您在查詢檢視中執行轉換時，會建立查詢步驟並列於 [查詢設定]  窗格的 [適用步驟]  清單中。 每個查詢步驟都有對應的查詢公式，也稱為 "M" 語言。

![](media/desktop-tutorial-facebook-analytics/16.png)

| 工作 | 查詢步驟 | 公式 |
| --- | --- | --- |
| 連接至 Facebook 來源 |來源 |Facebook.Graph (&quot;https://graph.facebook.com/microsoftbi/posts&quot;) |
| **分割資料行** 以取得您需要的值 |依分隔符號分割資料行 |Table.SplitColumn (Source,&quot;created_time&quot;,Splitter.SplitTextByDelimiter(&quot;T&quot;),{&quot;created_time.1&quot;, &quot;created_time.2&quot;}) |
| **變更新資料行的類型** (自動步驟) |變更的類型 |Table.TransformColumnTypes (#&quot;依分隔符號分割資料行&quot;,{{&quot;created_time.1&quot;, type date}, {&quot;created_time.2&quot;, type time}}) |
| **為**資料行**重新命名** |重新命名的資料行 |Table.RenameColumns (#&quot;變更的類型&quot;,{{&quot;created_time.1&quot;, &quot;created_date&quot;}, {&quot;created_time.2&quot;, &quot;created_time&quot;}}) |
| **插入**資料行**** |插入的小時 |Table.AddColumn (#&quot;重新命名的資料行&quot;, &quot;Hour&quot;, each Time.Hour([created_time]), type number) |
| **變更類型** |變更的類型 1 |Table.TransformColumnTypes (#&quot;插入的小時&quot;,{{&quot;Hour&quot;, type text}}) |
| **展開**巢狀表格中的值**** |展開 [shares] |Table.ExpandRecordColumn (#&quot;變更的類型 1&quot;, &quot;shares&quot;, {&quot;count&quot;}, {&quot;shares.count&quot;}) |
| **為**資料行**重新命名** |重新命名資料行1 |Table.RenameColumns (#&quot;展開 shares&quot;,{{&quot;shares.count&quot;, &quot;shares&quot;}}) |
| **變更類型** |已變更的類型 2 |Table.TransformColumnTypes (#&quot;重新命名的資料行 1&quot;,{{&quot;shares&quot;, Int64.Type}}) |

## <a name="task-4-create-additional-visualizations-using-the-report-view"></a>**工作 4：使用報表檢視建立其他視覺效果**
現在我們已將資料轉換為圖形，供我們接下來的分析所用，我們可以將產生的資料表載入報表，並建立其他視覺效果。

**步驟 1** ：載入查詢到您的報表

若要將查詢結果載入至報表，我們要從 [查詢編輯器] 選取 [載入並關閉]。 這會將我們所做的變更載入 Power BI Desktop，並關閉 [查詢編輯器] 。

![](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)

在 Power BI Desktop，必須確定我們是否位於 [報表]  檢視。 從 Power BI Desktop 中的左工具列選取上方圖示。

![](media/desktop-tutorial-facebook-analytics/17.png)

**步驟 2** ：建立折線圖和橫條圖

若要建立視覺效果，我們可以將欄位從 [欄位清單]  拖曳到 [報表畫布] 。

1. 將 [共用]  欄位拖曳到 [報表]  畫布，建立橫條圖。 然後將 created\_date 拖曳到圖表上，而 Power BI Desktop 會將視覺效果變更為 [折線圖]。
   
   ![](media/desktop-tutorial-facebook-analytics/19.png)
2. 下一步，將 [共用]  欄位拖曳至 [報表畫布] 。 現在將 [小時]  欄位拖曳到 [欄位清單]  下的 [軸] 區段。
   
   ![](media/desktop-tutorial-facebook-analytics/20.png)
3. 我們可以在 [視覺效果]  窗格按一下不同的圖示，輕鬆變更視覺效果的類型。 下圖的箭號指向**橫條圖**圖示。
   
   ![](media/desktop-tutorial-facebook-analytics/21.png)
4. 請將視覺效果類型變更為 [橫條圖] 。
5. [橫條圖]  隨即建立，但軸卻不是我們所要的 - 我們想要從另一方向 (從高到低) 進行排序。 選取 [Y 軸]  旁邊的向下箭頭，以展開該區段。 我們要將軸的類型從 [連續]  變更為 [類別] ，因此它將依我們所需方式排序 (下圖顯示我們選擇之前的軸 - 請看後續的圖，了解我們想要的樣子)。

![](media/desktop-tutorial-facebook-analytics/22.png)

這樣看起來好多了。 現在我們在此頁面上有三個視覺效果，我們可以視需要設定大小以填滿報表頁面。

![](media/desktop-tutorial-facebook-analytics/23.png)

如您所見，自訂報表中的視覺效果很容易，所以可以依您想要的方式呈現資料。 Power BI Desktop 提供流暢的端對端體驗，包括從各種資料來源取得資料，調整以符合您的分析需求，乃至於以豐富且互動的方式將此資料視覺化。 準備好報表之後，您可以[將其上傳至 Power BI](desktop-upload-desktop-files.md) 並建立以此為基礎的儀表板，您可以與其他 Power BI 使用者共用該儀表板。

您可以在[這裡](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/FacebookAnalytics.pbix)下載本教學課程的最終結果

### <a name="where-else-can-i-get-more-information"></a>還可以從何處取得更多資訊？
* [閱讀其他 Power BI Desktop 教學課程](http://go.microsoft.com/fwlink/?LinkID=521937)
* [觀看 Power BI Desktop 影片](http://go.microsoft.com/fwlink/?LinkID=519322)
* [瀏覽 Power BI 論壇](http://go.microsoft.com/fwlink/?LinkID=519326)
* [閱讀 Power BI 部落格](http://go.microsoft.com/fwlink/?LinkID=519327)



