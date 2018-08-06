---
title: 教學課程：在 Power BI Desktop 中結合來自 Excel 和 OData 摘要的資料
description: 教學課程：結合來自 Excel 和 OData 摘要的資料
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 0ec22bd142f7509935691ff7bfcd38cb51a04fb2
ms.sourcegitcommit: fbb7924603f8915d07b5e6fc8f4d0c7f70c1a1e1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39280102"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>教學課程：結合來自 Excel 和 OData 摘要的銷售資料

資料通常會分散在多個資料來源，例如產品資訊可能位於某個資料庫中，而銷售資訊可能位於另一個資料庫中。 使用 **Power BI Desktop** 時，您可以合併不同來源的資料，以建立有趣、 吸引人的資料分析和視覺效果。 

在本教學課程中，您將了解如何合併兩個不同來源的資料：一個是包含產品資訊的 Excel 活頁簿，另一個是包含訂單資料的 OData 摘要。 匯入每個資料集並執行轉換和彙總步驟之後，就可以使用這兩個來源的資料產生一份能呈現互動視覺效果的銷售分析報表。 這些技術也可以套用至 SQL Server 查詢、CSV 檔案以及 Power BI Desktop 中的任何其他資料來源。

>[!NOTE]
>在 Power BI Desktop 中，完成同一件工作的方法通常有好幾種。 比方說，在資料行或資料格上按一下滑鼠右鍵或者選取 [更多選項]，同樣也會有很多的功能區選項。 以下步驟描述幾種替代方法。 

## <a name="import-the-product-data-from-excel"></a>從 Excel 匯入產品資料

首先，從 Excel Products.xlsx 活頁簿，將產品資料匯入 Power BI Desktop。

1. [下載 Products.xlsx Excel 活頁簿](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)，然後儲存為 **Products.xlsx**。
   
2. 在 Power BI Desktop 功能區中，到 [首頁] 索引標籤的 [取得資料]，選取旁邊的下拉式箭號，然後從 [最常用] 下拉式清單 選取 **Excel**。 
   
   ![取得資料](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >您也可以選取 [取得資料] 項目本身，或從 Power BI [開始] 對話方塊選取 [取得資料]，然後選取 **Excel** 或者在 [取得資料] 對話方塊中依序選取 [檔案] > **Excel**，然後選取 [連接]。
   
3. 在 [開啟]對話方塊中，瀏覽至並選取 **Products.xlsx** 檔案，然後選取 [開啟]。
   
4. 在 [導覽器]  窗格中，選取 **Products** 資料表，然後選取 [編輯] 。
   
   ![Excel 的導覽器窗格](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
**Power Query 編輯器**中會開啟資料表的預覽，您可以在其中套用各種轉換來清除資料。 
   
![Power Query 編輯器](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>您也可以從 Power BI Desktop 的 [首頁] 功能區依序選取 [編輯查詢] > [編輯查詢]，或者在 [報表檢視] 中的任何查詢旁邊按一下滑鼠右鍵或選取 [更多選項]，接著選取 [編輯查詢]，同樣可以開啟 **Power Query 編輯器**。

## <a name="clean-up-the-products-columns"></a>清除產品資料行

結合的報表只會使用 Excel 活頁簿的 **ProductID**、**ProductName**、**QuantityPerUnit** 和 **UnitsInStock** 資料行，因此您可以移除其他資料行。 

1. 在 **Power Query 編輯器**中，選取 **ProductID**、**ProductName**、**QuantityPerUnit** 和 **UnitsInStock** 資料行 (使用 **Ctrl**+**按一下**來選取多個資料行，或使用 **Shift**+**+按一下**來選取相鄰的資料行)。
   
2. 在任何選取的標題上按一下滑鼠右鍵，然後從下拉式清單中選取 [移除其他資料行]，除了選取的資料行外，資料表中其他的資料行一律移除。 
   您也可以從 [首頁] 功能區索引標籤的 [管理資料行] 群組，依序選取 [刪除資料行] > [移除其他資料行]。 
   
   ![移除其他資料行](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>從 OData 摘要匯入訂單資料

接下來，從範例 Northwind 銷售系統 OData 摘要，匯入訂單資料。 

1. 在 **Power Query 編輯器**中，選取 [新來源]，然後從 [最常用]下拉式清單選取 [OData 摘要]。 
   
   ![取得 OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. 在 [OData 摘要] 對話方塊中，貼上 Northwind OData 摘要的 URL - `http://services.odata.org/V3/Northwind/Northwind.svc/` 然後選取 [確定]。
   
   ![OData 摘要對話方塊](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. 在 [導覽器] 窗格中，選取 [訂單]資料表，然後選取 [確定] 並將資料載入 **Power Query 編輯器**。
   
   ![OData 的導覽器窗格](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >在 [導覽器] 窗格中，您可以按一下資料表名稱來查看預覽，無須勾選核取方塊。

## <a name="expand-the-order-data"></a>展開訂單資料

當連線的資料來源擁有多個資料表，例如關聯式資料庫或 Northwind OData 摘要，您可以使用資料表之間的參考來建立自己的查詢。 **訂單**資料表包含數個關聯資料表的參考。 您可以使用**展開**作業，將 **ProductID**、**UnitPrice** 以及 **Quantity** 資料欄，從關聯的 **Order_Details** 資料表新增至主題 (**Orders**) 資料表。 

1. 往**訂單**資料表右方捲動，直到可以看到 **Order_Details** 資料行為止。 請注意，這個資料行不包含資料，它包含另一個資料表的參考。
   
   ![Order_Details column](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. 在 **Order_Details** 資料行標題中，選取 [展開]圖示 (![展開圖示](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png))。 
   
3. 在 [展開]  下拉式清單中：
   
   1. 選取 [(選取所有資料行)]  以清除所有資料行。
      
   2. 選取 **ProductID**、**UnitPrice** 和 **Quantity**，然後選取 [確定]。
      
      ![展開對話方塊](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

展開 **Order_Details** 資料表之後，**Order_Details** 資料行會被巢狀資料表的三個新資料行所取代，而且資料表中會有新的資料列，用來填寫每一個訂單新增的資料。 

![展開的資料行](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>建立一個自訂的計算結果欄

Power Query 編輯器可讓您建立各種計算式和自訂的欄位，讓您的資料具備多樣性。 您會建立一個自訂的資料行，然後它會將單價乘以商品數量，以此得出訂單中每一單項產品的總價。

1. 在 Power Query 編輯器的 [新增資料行] 功能區中，選取 [自訂資料行]。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. 在 [自訂資料行] 對話方塊的 [新資料行名稱] 欄位輸入 **LineTotal**。

3. 在 **=** 之後的 [自訂資料行公式] 欄位中，輸入 **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]**。 (您也可以從 [可用的資料行] 捲動方塊中選取欄位名稱，然後選取 [<< 插入]，而不用逐個輸入)。 
3. 選取 [確定] 。
   
   ![自訂的資料行對話方塊](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

新的 **LineTotal** 欄位會顯示為 **Orders** 資料表的最後一個資料行。

## <a name="set-the-data-type-for-the-new-field"></a>設定新欄位的資料類型

當 Power Query 編輯器連接到資料時，它會決定每個欄位的最佳資料類型，並據此顯示資料。 您可以根據標題中的圖示，或在 [首頁] 功能區索引標籤的 [轉換] 群組中的 [資料類型] 下方，看到指派至各欄位的資料類型。 

新 **LineTotal** 資料行的資料類型為**任何**，但其值為貨幣。 若要指派一種資料類型，請在 **LineTotal** 資料行標題按一下滑鼠右鍵，接著從下拉式清單中選取 [變更資料類型]，然後選取 [固定的小數位數]。 

![變更資料類型](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>您也可以選取 **LineTotal** 資料行，然後到 [首頁] 功能區索引標籤的 [轉換] 區域，選取 [資料類型]，接著選取 [固定的小數位數]。

## <a name="clean-up-the-orders-columns"></a>清除訂單資料行

若想在報表中更輕鬆地使用您的模型，可以刪除、重新命名和重新排列某些資料行。

您報表只會使用 **OrderDate**、**ShipCity**、**ShipCountry**、**Order_Details.ProductID**、**Order_Details.UnitPrice** 以及 **Order_Details.Quantity** 資料行。 您可以選取這些資料行，並使用 [移除其他資料行]，這和您在 Excel 中的操作完全相同。或者，除了列出的資料行之外，您可以選取其他的資料行，然後在其中一個選取的資料行上按一下滑鼠右鍵，最後選取 [移除資料行]，全部予以移除。 

您可以移除 *Order_Details* 資料行，這樣 **Order_Details.ProductID**、**Order_Details.UnitPrice** 和 **Order_Details.Quantity** 資料行就更容易識別了。 在資料行名稱前面加上前置詞。 若要將資料行分別重新命名為 **ProductID**、**UnitPrice** 和 **Quantity**：

1. 按兩下或點選並按住每個資料行的標題，或者在資料行標題按一下滑鼠右鍵，然後選取下拉式清單中的 [重新命名]。 
2. 刪除 *Order_Details.* 在每個名稱前加上的前置詞，然後按下 **Enter**。

最後，為了讓 **LineTotal** 存取更容易，請將它往左側拖曳，一直到 **ShipCountry** 資料行右側才停止。

![清除資料表](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>檢閱查詢步驟

當您在 Power Query 編輯器中塑造以及轉換資料時，每個步驟都會記錄至 Power Query 編輯器右側 [查詢設定] 窗格的 [套用的步驟] 區域中。 您可以反向逐步執行「套用的步驟」，以重新檢查您做了哪些變更，並視需要編輯、刪除或重新排列它們 (雖然這可能會有風險，因為變更前面的步驟可能中斷接下來的步驟)。 

在 Power Query 編輯器左側的 [查詢] 清單中選取每一個查訽，然後在 [查詢設定] 中重新檢查 [套用的步驟]。 套用之前的資料轉換後，兩個查詢的「套用的步驟」應該類似如下：

![產品查詢套用的步驟](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![訂單查詢套用的步驟](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>套用的步驟本質上是以 **Power Query 語言** (亦稱為 **M** 語言) 所撰寫的公式。 若要查看和編輯公式，請選取功能區 [首頁] 索引標籤之 [查詢] 群組中的 [進階編輯器]。 

## <a name="import-the-transformed-queries"></a>匯入轉換的查詢

當您處理完資料之後，請在 [首頁] 功能區索引標籤的 [關閉] 群組中依序選取 [關閉並套入] > [關閉並套入]，將資料匯入 Power BI Desktop。 

![關閉並套用](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

載入資料後，查詢會出現在 Power BI Desktop 報表檢視的 [欄位] 清單中。

![欄位清單中的資料行](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>管理資料集之間的關聯性

Power BI Desktop 不需要您結合查詢來建立報表。 不過，您可以根據資料集共有的欄位，利用它們之間的關聯性來擴充及豐富您的報表。 Power BI Desktop 會自動偵測關聯性，或您可以在 Power BI Desktop [管理關聯] 對話方塊建立它們。 若要深入了解 Power BI Desktop 中的關聯性，請參閱[建立和管理關聯性](desktop-create-and-manage-relationships.md)。

此教學課程中的 Orders 和 Products 資料集有一個共同的 *ProductID* 欄位，所以它們會因為這個資料行而產生一種關聯性。 

1. 在 Power BI Desktop 報表檢視中，在 [首頁] 功能區的 [關聯性] 區域中，選取 [管理關聯]。
   
   ![管理關聯性功能區](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. 在 [管理關聯性]對話方塊中，請注意，Power BI Desktop 已偵測到並列出 Products 和 Orders 資料表之間的作用中關聯性。 若要檢視關聯性，請選取 [編輯]。 
   
   ![管理關聯性對話方塊](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   [編輯關聯性] 對話方塊隨即開啟，顯示關聯性的細節。  
   
   ![編輯關聯性對話方塊](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. Power BI Desktop 已正確偵測到關聯性，因此您可以選取 [取消]，然後選取 [關閉] 來離開關聯性對話方塊。

您也可以在 Power BI Desktop 視窗左側選取 [關聯性] 檢視，即可檢視並管理所選查詢之間的關聯性。 按兩下連接兩個查詢，以開啟線的箭號**編輯關聯性**對話方塊和檢視或變更關聯性。 

![關聯性檢視](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

若要從關聯性檢視回到報表檢視，請選取 [報表檢視] 圖示。 

![報表檢視圖示](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>使用您的資料建立視覺效果

Power BI Desktop 報表檢視讓您建立各種視覺效果，以便深入探索您的資料。 您可以建立多頁報表，而且每一頁可以有多種視覺效果。 您和其他人可以與視覺效果互動，以協助分析及了解您的資料。 如需深入了解如何在 Power BI 服務 (您的站台) 中檢視和編輯報表，請參閱[編輯報表](service-interact-with-a-report-in-editing-view.md)。

您可以使用這兩個資料集以及它們之間的關聯性，協助視覺化並分析您的銷售資料。 

首先，使用這兩個查詢的欄位來建立堆疊直條圖，顯示每個訂購產品的數量。 

1. 從右側 [欄位] 窗格的 **Orders** 選取 **Quantity** 欄位，或者將它拖曳至畫布上的空白處。 這樣會建立堆疊直條圖，顯示所有訂購產品的總數量。 
   
2. 從 [欄位] 窗格的 [Products] 選取 **ProductName**，中或將它拖曳到圖表，以顯示每個訂購產品的數量。 
   
3. 若要按照訂購量高低順序排列產品，請選取視覺效果右上角的 [更多選項] 省略符號 (**...**)，然後選取 [排序依據 Quantity]。
   
4. 使用在圖表邊角的控點，將它放大，這樣可以看到更多的產品名稱。 
   
   ![Quantity by ProductName 橫條圖](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

接下來，建立一張圖表來顯示一段時間 (**OrderDate**) 的訂單金額 (**LineTotal**)。 

1. 在沒有選取任何內容的畫布上，從 [欄位] 窗格的 **Orders** 中選取 **LineTotal**，或將它拖曳到畫布上的空白處。 堆疊直條圖會顯示所有訂單的總金額。 
   
2. 在選取的圖表中，從 **Orders** 選取 **OrderDate**，或者將它拖曳至圖表。 圖表現在會顯示針對每個訂單日期的產品線總數。 
   
3. 拖曳每個角落來調整視覺效果，即可看到更多的資料。 
   
   ![LineTotals by OrderDate 折線圖](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >如果您在圖表上只看到 Years (只有三個資料點)，請到 [視覺效果] 窗格的 **Axis** 欄位中，按一下 **OrderDate** 旁邊的向下箭頭，然後選取 **OrderDate** 而不是 **Date Hierarchy**。 

最後，建立一個地圖視覺效果，顯示每個國家/地區的訂單金額。 

1. 在沒有選取任何內容的畫布上，從 [欄位] 窗格的 **Orders** 中選取 **ShipCountry**，或將它拖曳到畫布上的空白處。 Power BI Desktop 會偵測到資料是國家/地區名稱，並自動建立地圖視覺效果，只要有國家/地區下訂單，便用一個資料點表示。 
   
2. 若要讓資料點的大小反映每個國家/地區的訂單數量，可以將 **LineTotal** 欄位拖曳到地圖 (或將它拖曳至 [視覺效果] 窗格 [大小] 底下的 [將資料欄位拖曳到此處])。 現在在地圖上圓圈的大小會反映每個國家/地區的訂單金額。 
   
   ![依 ShipCountry 的 LineTotals 地圖視覺效果](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>與報表視覺效果互動以進一步分析

Power BI Desktop 可讓您與視覺效果 (交叉醒目提示並相互篩選) 互動，以發掘進一步的趨勢。 如需詳細資訊，請參閱[在報表中進行篩選和醒目提示](power-bi-reports-filters-and-highlighting.md)。 

因為您的查詢之間存在關聯性，所以與某一個視覺效果的互動，會影響在頁面上所有其他的視覺效果。 

在地圖視覺效果中，選取以**加拿大**為中心的圓圈。 請注意，其他兩個視覺效果篩選會反白顯示的加拿大地區的商品總計和訂單數量。

![篩選出加拿大地區的銷售資料](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

如果您在 **Quantity by ProductName** 圖表中選取一個產品，則地圖和日期圖表篩選器會反映該產品的資料，另外如果您在 **LineTotal by OrderDate** 圖表中選取一個日期，地圖和產品圖表篩選器會顯示該日期的資料。 
>[!TIP]
>若要取消選取某個視覺效果，請再選取視覺效果一次，或選取另一個視覺效果。 

## <a name="complete-the-sales-analysis-report"></a>完成銷售分析報表

您完成的報表會合併 Products.xlsx Excel 檔案中的資料以及 Northwind OData 摘要，形成各種視覺效果，這有助於分析不同國家/地區、時間範圍以及產品的訂單資訊。 準備好報表之後，您可以[將其上傳至 Power BI 服務](desktop-upload-desktop-files.md)並與其他 Power BI 使用者共用。

## <a name="next-steps"></a>後續步驟
* [閱讀其他 Power BI Desktop 教學課程](http://go.microsoft.com/fwlink/?LinkID=521937)
* [觀看 Power BI Desktop 影片](http://go.microsoft.com/fwlink/?LinkID=519322)
* [瀏覽 Power BI 論壇](http://go.microsoft.com/fwlink/?LinkID=519326)
* [閱讀 Power BI 部落格](http://go.microsoft.com/fwlink/?LinkID=519327)