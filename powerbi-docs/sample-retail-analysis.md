---
title: 適用於 Power BI 的零售分析範例：觀看導覽
description: 適用於 Power BI 的零售分析範例：觀看導覽
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 04676ee789b90eb09cbed3bafb623e8e9b89e4e4
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66720866"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>適用於 Power BI 的零售分析範例：觀看導覽

這個產業範例的儀表板、基礎資料集和報表，會分析在多個門市和區域售出之品項的零售資料。 計量會比較今年與去年在以下領域的表現：銷售、單位、毛利率和變異數，以及新門市分析。 此為來自 obviEnce 的匿名真實資料 ([www.obvience.com](http://www.obvience.com))。

![](media/sample-retail-analysis/retail1.png)

## <a name="prerequisites"></a>先決條件

 您必須先將範例下載為[內容套件](https://docs.microsoft.com/power-bi/sample-datasets#get-and-open-a-sample-content-pack-in-power-bi-service)、[.pbix 檔案](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)或 [Excel 活頁簿](http://go.microsoft.com/fwlink/?LinkId=529778)，才能使用範例。


### <a name="get-the-content-pack-for-this-sample"></a>取得此範例的內容套件

1. 開啟 Power BI 服務 (app.powerbi.com) 並登入。
2. 在左下角選取 [取得資料]  。
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. 在顯示的 [取得資料] 頁面上，選取 [範例]  。
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. 選取 [零售分析範例]  ，然後選擇 [連線]  。  
  
   ![零售分析範例](media/sample-retail-analysis/retail16.png)
   
5. Power BI 會匯入內容套件，並將新的儀表板、報表及資料集新增到您目前的工作區。 新的內容會以黃色星號標示。 
   
   ![零售分析範例](media/sample-retail-analysis/retail17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>取得此範例的 .pbix 檔案

或者，您可以下載此範例為 .pbix 檔案，其設計目的是要用於 Power BI Desktop。 

 * [零售分析範例](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>取得此範例的 Excel 活頁簿
您也可以[只下載此範例的資料集 (Excel 活頁簿)](http://go.microsoft.com/fwlink/?LinkId=529778)。 活頁簿包含的 Power View 工作表可供您檢視及修改。 若要查看未經處理的資料，請選取 [Power Pivot] > [管理]  。

## <a name="start-on-the-dashboard-and-open-the-report"></a>進入儀表板，然後開啟報表
1. 在儀表板中選取 [所有門市] 磚：

   ![](media/sample-retail-analysis/retail-analysis-7.png)  

   這會帶您前往報表中的 [銷售門市概觀] 頁面。 您會看到我們總共有 104 個門市，其中 10 個為新門市。 我們有兩種連鎖店：Fashions Direct 和 Lindseys。 Fashions Direct 的門市通常比較大。
2. 在圓形圖中選取 [Fashions Direct]  。

   ![](media/sample-retail-analysis/retail3.png)  

   請注意泡泡圖中的結果：

   ![](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   FD-01 區有每平方英呎最高的平均銷售額，FD-02 區與去年相比的變異數最低，FD-03 區和 FD-04 區的整體表現最差。
3. 選取個別泡泡或其他圖表，即可查看交叉醒目提示，呈現您選取範圍的影響。
4. 若要返回儀表板，請從上方導覽列 (階層連結) 選取其名稱。

   ![](media/sample-retail-analysis/power-bi-breadcrumbs.png)
5. 在儀表板中選取標題為「本年度銷售量」的磚。

   ![](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   這等同於在問題方塊中輸入「本年度銷售量」。

   您會看到這個畫面：

   ![](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>檢閱為 Power BI 問與答所建立的磚
讓我們詳加說明。

1. 在問題中加入「 **依區域**的本年度銷售量」。 觀察結果：您會發現答案自動呈現在橫條圖中，並建議其他片語：

   ![](media/sample-retail-analysis/retail8.png)
2. 現在將問題改為「 **依郵遞區號和連鎖店**的本年度銷售量」。

   請注意當您輸入適當的圖表時，它會如何回答。
3. 試問更多問題，看看會得到何種結果。
4. 當您準備好時，請返回儀表板。

## <a name="dive-deeper-into-the-data"></a>深入探索資料
現在探討更詳細的層面，我們來查看區域的表現。

1. 在儀表板上，選取比較本年度和去年度銷售量的圖格。

   ![](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   請注意去年在差異 % 上有很大的變動，1 月、4 月和 7 月都是狀況特別不好的月份。

   ![](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   現在來看看是否可以縮小範圍，找出問題所在。
2. 選取泡泡圖，然後選擇 [020-Mens]  。

   ![](media/sample-retail-analysis/retail11.png)  

   您會觀察到，男性類別在 4 月並沒有像整體生意那樣受到嚴重影響，但 1 月和 7 月仍是有問題的月份。
3. 現在選取 [010-Womens]  泡泡。

   ![](media/sample-retail-analysis/retail12.png)

   請注意，女性類別在所有月份的表現都比整體生意更差，而且每個月的表現幾乎也都不如去年。
4. 再次選取泡泡即可清除篩選條件。

## <a name="try-out-the-slicer"></a>試用交叉分析篩選器
我們來看一看特定區域的表現。

1. 在左上方的交叉分析篩選器中選取 [Allan Guinot]。

   ![](media/sample-retail-analysis/retail13.png)

   請注意 Allan 的區域在 3 月和 6 月的表現優於去年。
2. 現在在已選取 Allan 的狀態下，按一下女性的泡泡。

   ![](media/sample-retail-analysis/power-bi-allan.png)

   請注意對於女性類別，他的區域從未達到去年營業額。
3. 探索其他區域的經理和商品類別狀況 – 您可找出其他的深入資訊嗎？
4. 當您準備好時，請返回儀表板。

## <a name="what-is-our-data-telling-us-about-sales-growth-this-year"></a>從資料中，我們了解到本年度銷售成長隱藏了哪些含意？
我們要探討的最後一個領域是我們的成長 – 本年度新開的門市。

1. 選取 [本年度新開門市] 圖格。

   ![](media/sample-retail-analysis/retail15.png)

   如圖格顯示，本年度開張的 Fashions Direct 門市比 Lindseys 門市更多。
2. 觀察「依名稱的每平方英尺銷售量」圖表：

   ![](media/sample-retail-analysis/retail14.png)

    各家新門市在「平均每平方英尺銷售量」上的差異相當大。
3. 按一下右上方圖表中的 Fashions Direct 圖例項目。 請注意即使是同一系列的連鎖店，最佳門市 (Fashions Direct 溫徹斯特店) 的表現顯著優於最差門市 (Fashions Direct 辛辛那提 2 號店)，分別是 $21.22 美元及 $12.86 美元。

   ![](media/sample-retail-analysis/power-bi-lindseys.png)
4. 按一下交叉分析篩選器中的 Fashions Direct 溫徹斯特店，然後觀察折線圖。 第一個銷售數字在二月報告。
5. 按一下交叉分析篩選器中的 Fashions Direct 辛辛那提 2 號店，折線圖中顯示該門市於 6 月開幕，似乎是表現最差的門市。
6. 請和之前一樣，在其他長條、折線和泡泡上按一下，看看您可以找到哪些深入資訊。

這是安全的作業環境。 您一律可以選擇不儲存變更。 但如果儲存了變更，您也可以隨時移至 [取得資料]，重新複製此範例。

## <a name="connect-to-your-data"></a>連線到您的資料
希望本教學已讓您了解 Power BI 儀表板、問與答和報表能夠如何提供零售資料的深入資訊。 現在輪到您了 — 連接到您自己的資料。 您可以透過 Power BI 連接到各式各樣的資料來源。 深入了解[開始使用 Power BI](service-get-started.md).

## <a name="next-steps"></a>後續步驟
* [下載零售分析範例的內容套件](sample-tutorial-connect-to-the-samples.md)
* [下載所有範例檔案的 zip 檔案](http://go.microsoft.com/fwlink/?LinkId=535020)    
* [下載這個 Power BI 範例中的 Excel 活頁簿](http://go.microsoft.com/fwlink/?LinkId=529778)    
* [取得 Power BI 的資料](service-get-data.md)    
* [Power BI 服務中的設計工具基本概念](service-basic-concepts.md)    
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
