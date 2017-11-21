---
title: "教學課程：在 Power BI Desktop 中分析來自 Excel 和 OData 摘要的銷售資料"
description: "教學課程：分析來自 Excel 和 OData 摘要的銷售資料"
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
ms.openlocfilehash: 03c5afae78e1688cadfdef9c0a96ca9f24247e12
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="tutorial-analyzing-sales-data-from-excel-and-an-odata-feed"></a>教學課程：分析來自 Excel 和 OData 摘要的銷售資料
有了 **Power BI Desktop**，您便可以連接到各種不同的資料來源，然後以有趣、具信服力的資料分析和視覺效果，來結合資料使其成形。 在本教學課程中，您將了解如何結合來自兩個資料來源的資料。 

資料通常會分散在多個資料來源，例如產品資訊可能位於某個資料庫中，而銷售資訊可能位於另一個資料庫中。 您在本文中會學到的技術包含 Excel 活頁簿和 OData 摘要，而這些技術也適用於其他資料來源，例如 SQL Server 查詢、CSV 檔案或 Power BI Desktop 中的任何資料來源。

在本教學課程中，您將匯入來自 Excel (包含產品資訊) 和 OData 摘要 (包含訂單資料) 的資料。 您將會執行轉換和彙總步驟，並結合來自這兩個來源的資料，以產生呈現互動式視覺效果的 **Total Sales per Product and Year** 報表。 

最終報表看起來會像是這樣：

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

若要遵循本教學課程中的步驟進行，您需要 Products 活頁簿，其下載方式為**：**[按一下](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)[這裡](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)[來下載 ](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**[Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)**[.](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx)

在 [另存新檔]  對話方塊中，將檔案命名為 **Products.xlsx**。

## <a name="task-1-get-product-data-from-an-excel-workbook"></a>工作 1：從 Excel 活頁簿取得產品資料
在這項工作中，您會將 Products.xlsx 檔案內的產品匯入 Power BI Desktop 中。

### <a name="step-1-connect-to-an-excel-workbook"></a>步驟 1：連接到 Excel 活頁簿
1. 啟動 Power BI Desktop。
2. 從 [常用] 功能區選取 [取得資料]。 Excel 是其中一個**最常用**的資料連線，因此您可以直接從 [取得資料] 功能表中加以選取。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
3. 如果您直接選取 [取得資料] 按鈕，您也可以選取 [檔案] **\> [Excel]**，然後選取 [連接]。
4. 在 [開啟檔案]  對話方塊中，選取 **Products.xlsx** 檔案。
5. 在 [導覽器]  窗格中，選取 **Products** 資料表，然後選取 [編輯] 。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)

### <a name="step-2-remove-other-columns-to-only-display-columns-of-interest"></a>步驟 2：移除其他資料行，只顯示感興趣的資料行
在這個步驟中，您會移除所有其他資料行，而只保留 **ProductID**、 **ProductName**、 **UnitsInStock**和 **QuantityPerUnit**。 在 Power BI Desktop 中，完成同一個工作的方法通常有好幾種。 例如，許多功能區中按鈕的功能，也可以透過資料行或資料格的快顯功能表來完成。

Power BI Desktop 包含查詢編輯器，可讓您使資料連接成形並加以轉換。 當您從 [導覽器]  選取 [編輯] 時，查詢編輯器會隨即自動開啟。 您也可以從 Power BI Desktop 的 [常用]  功能區選取 [編輯查詢]  ，以開啟查詢編輯器。 在查詢編輯器中，執行下列步驟。

1. 在查詢編輯器中，選取 **ProductID**、 **ProductName**、 **QuantityPerUnit**和 **UnitsInStock** 資料行 (使用 **Ctrl+Click** 選取多個資料行，或使用 **Shift+Click** 選取相鄰的資料行)。
2. 從功能區選取 [移除資料行] \> [移除其他資料行]，或以滑鼠右鍵按一下資料行標頭，然後按一下 [移除其他資料行]。

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_removeothercolumns.png)

### <a name="step-3-change-the-data-type-of-the-unitsinstock-column"></a>步驟 3：變更 UnitsInStock 資料行的資料類型
當查詢編輯器連接到資料時，它會檢閱每個欄位並決定最佳資料類型。 若是 Excel 活頁簿，則庫存產品數量一律為整數，因此在這個步驟中，您會確認 **UnitsInStock** 資料行的資料類型是否為整數。

1. 選取 **UnitsInStock** 資料行。
2. 在 [常用]  功能區中，選取 [資料類型]  下拉按鈕。
3. 如果還不是整數，請從下拉式清單選取 [整數]  做為資料類型 ([資料類型:]  按鈕也會顯示目前選取範圍的資料類型)。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_wholenumber.png)      

### <a name="power-bi-desktop-steps-created"></a>建立的 Power BI Desktop 步驟
當您在查詢編輯器中執行查詢作業時，會建立查詢步驟並列於 [查詢設定]  窗格內的 [套用的步驟]  清單中。 每個查詢步驟都有對應的公式，又稱為 "M" 語言。 如需 "M" 公式語言的詳細資訊，請參閱[了解 Power BI 公式](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f).

| 工作 | 查詢步驟 | 公式 |
| --- | --- | --- |
| 連接到 Excel 活頁簿 |來源 |Source{[Name="Products"]}[Data] |
| 將第一個資料列升級為資料表資料行標頭 |FirstRowAsHeader |[Table.PromoteHeaders](https://support.office.com/Article/TablePromoteHeaders-b8eaeb95-042a-42e1-9164-6d3c646acadc "Table.PromoteHeaders") <br /> (Products) |
| 移除其他資料行，只顯示感興趣的資料行 |RemovedOtherColumns |[Table.SelectColumns](https://support.office.com/Article/TableSelectColumns-20bb9e28-9fd3-4cd2-a21b-97972c82ec22 "Table.SelectColumns")  <br />(FirstRowAsHeader,{"ProductID", "ProductName", "QuantityPerUnit", "UnitsInStock"}) |
| 變更資料類型 |變更的類型 |Table.TransformColumnTypes(\#"Removed Other Columns",{{"UnitsInStock", Int64.Type}}) |

## <a name="task-2-import-order-data-from-an-odata-feed"></a>工作 2：從 OData 摘要匯入訂單資料
在這項工作中，您將匯入訂單資料。 這個步驟代表連接到銷售系統。 您會將位於下列 URL 之範例 Northwind OData 摘要中的資料匯入 Power BI Desktop，而您可以在下列步驟中複製 (然後貼上) 這個 URL：<http://services.odata.org/V3/Northwind/Northwind.svc/> 

### <a name="step-1-connect-to-an-odata-feed"></a>步驟 1：連接到 OData 摘要
1. 從查詢編輯器的 [常用] 功能區索引標籤選取 [取得資料]
2. 瀏覽至 [OData 摘要]  資料來源。
3. 在 [OData 摘要]  對話方塊中，貼上 Northwind OData 摘要的 **URL** 。
4. 選取 [確定] 。
5. 在 [導覽器]  窗格中，選取 **Orders** 資料表，然後選取 [編輯] 。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/anlayzingsalesdata_odatafeed.png)

>[!NOTE]
>您可以按一下資料表名稱來查看預覽，而無須選取核取方塊。

### <a name="step-2-expand-the-orderdetails-table"></a>步驟 2：展開 Order\_Details 資料表
**Orders** 資料表包含 **Details** 資料表的參考，其中包含每筆訂單中的個別產品。 當您連接到具有多個資料表的資料來源時 (例如關聯式資料庫)，您便可以使用這些參考來建立查詢。 

在這個步驟中，展開與 **Orders** 資料表相關的 **Order\_Details** 資料表，以將 **Order\_Details** 中的 **ProductID**、**UnitPrice** 和 **Quantity** 資料行合併到 **Orders** 資料表。 以下是這些資料表中的資料表示法：

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/orderdetails.png)

**展開** 作業會將相關資料表中的資料行合併到主體資料表。 執行查詢時，相關資料表 (**Order\_Details**) 中的資料列會合併到主體資料表 (**Orders**) 中的資料列。

展開 **Order\_Details** 資料表之後，會將三個新資料行和其他資料列加入 **Orders** 資料表中，分別用於巢狀或相關資料表中的每個資料列。

1. 在 [查詢檢視] 中，捲動至 **Order\_Details** 資料行。
2. 在 **Order\_Details** 資料行中，選取展開圖示 (![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png))。
3. 在 [展開]  下拉式清單中：
   1. 選取 [(選取所有資料行)]  以清除所有資料行。
   2. 選取 **ProductID**、 **UnitPrice**和 **Quantity**。
   3. 按一下 [確定] 。
      ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)

### <a name="step-3-remove-other-columns-to-only-display-columns-of-interest"></a>步驟 3：移除其他資料行，只顯示感興趣的資料行
在這個步驟中，您會移除所有其他資料行，而只保留 **OrderDate、ShipCity**、**ShipCountry**、**Order\_Details.ProductID**、**Order\_Details.UnitPrice** 和 **Order\_Details.Quantity** 資料行。 在先前的工作中，您使用了 [移除其他資料行] 。 在這項工作中，您會移除選取的資料行。

1. 在 [查詢檢視] 中，完成 a. 和 b. 以選取所有資料行：
   1. 按一下第一個資料行 (**OrderID**)。
   2. 在最後一個資料行 (**Shipper**) 上按一下 Shift + 滑鼠左鍵。
   3. 選取所有資料行之後，使用 Ctrl + 按一下滑鼠左鍵來取消選取下列資料行：**OrderDate**、**ShipCity**、**ShipCountry**、**Order\_Details.ProductID**、**Order\_Details.UnitPrice** 和 **Order\_Details.Quantity**。
2. 只選取要移除的資料行之後，以滑鼠右鍵按一下任何選取的資料行標頭，然後按一下 [移除資料行] 。

### <a name="step-4-calculate-the-line-total-for-each-orderdetails-row"></a>步驟 4：計算每個 Order\_Details 資料列的項目總計
Power BI Desktop 可讓您根據所匯入的資料行建立計算方式，以加強要連接的資料。 在這個步驟中，您會建立 [自訂資料行] 來計算每個 **Order\_Details** 資料列的項目總計。

計算每個 **Order\_Details** 資料列的項目總計：

1. 在 [加入資料行]  功能區索引標籤中，按一下 [加入自訂資料行]  。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. 在 [新增自訂資料行] 對話方塊的 [自訂資料行公式] 文字方塊中，輸入 **[Order\_Details.UnitPrice] \* [Order\_Details.Quantity]**。
3. 在 [新資料行名稱]  文字方塊中，輸入 **LineTotal**。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)
4. 按一下 [確定] 。

### <a name="step-5-set-the-datatype-of-the-linetotal-field"></a>步驟 5：設定 LineTotal 欄位的資料類型
1. 以滑鼠右鍵按一下 **LineTotal** 資料行。
2. 選取 [變更類型]  ，然後選擇 [十進位數字]。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

### <a name="step-6-rename-and-reorder-columns-in-the-query"></a>步驟 6：重新命名和重新排列查詢中的資料行
最後，在這個步驟中，您會重新命名最終資料行並變更其順序，以讓模型更容易用於建立報表。

1. 在 [查詢編輯器] 中，將 **LineTotal** 資料行向左拖曳到 **ShipCountry**之後。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
2. 移除 *Order\_Details。* 從 **Order\_Details.ProductID**、**Order\_Details.UnitPrice** 和 **Order\_Details.Quantity** 資料行中移除前置詞，方法是在各個資料行標頭上按兩下，然後從資料行名稱中刪除該文字。

### <a name="power-bi-desktop-steps-created"></a>建立的 Power BI Desktop 步驟
當您在查詢編輯器中執行查詢作業時，會建立查詢步驟並列於 [查詢設定]  窗格內的 [套用的步驟]  清單中。 每個查詢步驟都有對應的 Power Query 公式，又稱為 "M" 語言。 如需這個公式語言的詳細資訊，請參閱[了解 Power BI 公式](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f "了解 Power Query 公式").

| 工作 | 查詢步驟 | 公式 |
| --- | --- | --- |
| 連接到 OData 摘要 |來源 |Source{[Name="Orders"]}[Data] |
| 展開 Order\_Details 資料表 |展開 Order\_Details |[Table.ExpandTableColumn](https://support.office.com/Article/TableExpandTableColumn-54903f25-75a2-4a44-a9a3-52a9d895ee98 "Table.ExpandTableColumn") <br /> (Orders, "Order\_Details", {"ProductID", "UnitPrice", "Quantity"}, {"Order\_Details.ProductID", "Order\_Details.UnitPrice", "Order\_Details.Quantity"}) |
| 移除其他資料行，只顯示感興趣的資料行 |RemovedColumns |[Table.RemoveColumns](https://support.office.com/Article/TableRemoveColumns-6265190e-2f58-4300-85b8-df88fc1a67d3 "Table.RemoveColumns") <br />(\#"Expand Order\_Details",{"OrderID", "CustomerID", "EmployeeID", "RequiredDate", "ShippedDate", "ShipVia", "Freight", "ShipName", "ShipAddress", "ShipCity", "ShipRegion", "ShipPostalCode", "ShipCountry", "Customer", "Employee", "Shipper"}) |
| 計算每個 Order\_Details 資料列的項目總計 |InsertedColumn |[Table.AddColumn](https://support.office.com/Article/TableAddColumn-6c64d0a5-9654-4d15-bfb6-9cc380aaf3c0 "Table.AddColumn") <br /> (RemovedColumns, "Custom", each [Order\_Details.UnitPrice] \* [Order\_Details.Quantity]) |

## <a name="task-3-combine-the-products-and-total-sales-queries"></a>工作 3：結合 Products 和 Total Sales 查詢
Power BI Desktop 不需要您結合查詢來建立報表。 相反地，您可以建立兩個資料集之間的 **關聯性** 。 您可以在資料集通用的任何資料行上建立這些關聯性。 如需詳細資訊，請參閱[建立和管理關聯性](desktop-create-and-manage-relationships.md).

在本教學課程中，Orders 和 Products 資料共用一個通用的 'ProductID' 欄位，因此我們需要確保在搭配 Power BI Desktop 使用的模型中有這兩項資料的關聯性。 您可以直接在 Power BI Desktop 中指定這兩個資料表的資料行彼此相關 (也就是資料行具有相同的值)。 Power BI Desktop 會為您找出關聯性的方向和基數。 在某些情況下，它甚至還會自動偵測關聯性。

在這項工作中，您會確認 Power BI Desktop 中已建立 **Products** 和 **Total Sales** 查詢的關聯性。

### <a name="step-1-confirm-the-relationship-between-products-and-total-sales"></a>步驟 1：確認 Products 和 Total Sales 之間的關聯性
1. 首先，我們需要將在查詢編輯器中建立的模型載入 Power BI Desktop 中。 從查詢編輯器的 [常用] 功能區選取 [關閉並載入]。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)
2. Power BI Desktop 會從這兩個查詢載入資料。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)      
3. 載入資料之後，選取 [常用]  功能區中的 [管理關聯性]  按鈕。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
4. 選取 [新增...] 按鈕
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
5. 當我們嘗試建立關聯性時，我們會看到已經存在一個關聯性！ 如 [建立關聯性]  對話方塊所示，每個查詢的 [ProductsID]  欄位 (加網底的資料行) 都已經建立關聯性。
   
    ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)
6. 選取 [取消] ，然後選取 Power BI Desktop 中的 [關聯性]  檢視。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
7. 如下圖所示，查詢之間的關聯性會以視覺化方式顯示。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)
8. 當您按兩下連接查詢之線條上的箭號時，[編輯關聯性]  對話方塊會隨即出現。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)
9. 由於不需要進行任何變更，因此我們將直接選取 [取消]  來關閉 [編輯關聯性]  對話方塊。

## <a name="task-4-build-visuals-using-your-data"></a>工作 4：使用您的資料建立視覺效果
Power BI Desktop 可讓您建立各種視覺效果，來深入探索您的資料。 您可以建立多頁報表，而且每一頁可以有多種視覺效果。 您可以與視覺效果互動，以協助分析及了解您的資料。 如需編輯報表的詳細資訊，請參閱[編輯報表](service-interact-with-a-report-in-editing-view.md).

在這項工作中，您會根據先前載入的資料建立報表。 您可以使用 [欄位] 窗格來選取要從中建立視覺效果的資料行。

### <a name="step-1-create-charts-showing-units-in-stock-by-product-and-total-sales-by-year"></a>步驟 1：建立圖表以顯示產品的庫存單位數量和年度總銷售額
將 [UnitsInStock]  從 [欄位] 窗格 ([欄位] 窗格位於畫面最右側) 拖曳到畫布上的空白處。 即會建立一種資料表視覺效果。 接著將 [ProductName] 拖曳到 [視覺效果] 窗格下半部的 [軸] 方塊中。 然後使用視覺效果右上角的圖示來選取 [排序依據] **\> [UnitsInStock]**。

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

將 [OrderDate]  拖曳到第一個圖表下方的畫布上，然後將 \[LineTotal] \(同樣從 \[欄位] 窗格中) 拖曳到視覺效果上，再選取折線圖。 即會建立下列視覺效果。

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png)

 接著將 [ShipCountry]  拖曳到右上方畫布的空白處。 由於您已選取地理欄位，因此會自動建立地圖。 現在將 [LineTotal]  拖曳到 [值]  欄位；地圖上代表每個國家/地區的圓形現在會依運送至該國家/地區之訂單的 [LineTotal]  調整大小。

![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

### <a name="step-2-interact-with-your-report-visuals-to-analyze-further"></a>步驟 2：與報表視覺效果互動以進一步分析
Power BI Desktop 可讓您與交互醒目提示並彼此篩選的視覺效果互動，以發掘進一步的趨勢。 如需詳細資訊，請參閱[在報表中進行篩選和醒目提示](power-bi-reports-filters-and-highlighting.md)

1. 按一下位於**加拿大**中心的淺藍色圓形。 注意其他視覺效果如何經過篩選，只顯示加拿大的庫存 (**ShipCountry**) 和訂單總數 (**LineTotal**)。
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="complete-sales-analysis-report"></a>完成銷售分析報表
執行上述所有步驟之後，即會有一份結合 Products.xlsx 檔案和 Northwind OData 摘要資料的銷售報表。 這個報表會以視覺化方式顯示，以協助分析來自不同國家/地區的銷售資訊。 您可以從[這裡](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Sales_Data.pbix)下載本教學課程的完整 Power BI Desktop 檔案.

## <a name="next-steps"></a>後續步驟
* [閱讀其他 Power BI Desktop 教學課程](http://go.microsoft.com/fwlink/?LinkID=521937)
* [觀看 Power BI Desktop 影片](http://go.microsoft.com/fwlink/?LinkID=519322)
* [瀏覽 Power BI 論壇](http://go.microsoft.com/fwlink/?LinkID=519326)
* [閱讀 Power BI 部落格](http://go.microsoft.com/fwlink/?LinkID=519327)



