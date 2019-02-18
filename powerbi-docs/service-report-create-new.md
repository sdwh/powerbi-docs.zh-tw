---
title: '從資料集建立新的報表 '
description: 從資料集建立新的 Power BI 報表。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/24/2018
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: b46896a06c9d7ed66e643aa218ec7dbd3da8c9ee
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216945"
---
# <a name="create-a-new-report-in-power-bi-service-by-importing-a-dataset"></a>匯入資料集以在 Power BI 服務中建立新的報表
您已閱讀 [Power BI 中的報表](consumer/end-user-reports.md)，現在想要建立自己的報表。 有許多不同的方式可建立報表，在本文中，我們一開始是使用 Power BI 服務從 Excel 資料集建立非常基本的報表。 了解建立報表的基本概念之後，底部的＜後續步驟＞會將您導向更進階的報表主題。  

## <a name="prerequisites"></a>先決條件
> - Power BI 服務 (若要使用 Power BI Desktop 建立報表，請參閱 [Desktop 的報表檢視](desktop-report-view.md))  
> - 零售分析範例資料集

## <a name="import-the-dataset"></a>匯入資料集
這種建立報表的方法會從資料集和空白報表畫布開始。 如果要跟著做，請[下載零售分析範例 Excel 資料集](http://go.microsoft.com/fwlink/?LinkId=529778)，並將它儲存至商務用 OneDrive (慣用) 或本機。

1. 我們會在 Power BI 服務工作區中建立報表，因此請選取現有工作區或建立新工作區。
   
   ![應用程式工作區清單](media/service-report-create-new/power-bi-workspaces2.png)
2. 在左側導覽窗格底部，選取 [取得資料]。
   
   ![取得資料](media/service-report-create-new/power-bi-get-data3.png)
3. 選取 [檔案]，然後導覽至您已儲存零售分析範例的位置。
   
    ![選取 [檔案]](media/service-report-create-new/power-bi-select-files.png)
4. 在此練習中請選取 [匯入]。
   
   ![選取 [匯入]](media/service-report-create-new/power-bi-import.png)
5. 匯入資料集之後，請選取 [檢視資料集]。
   
   ![選取 [檢視儀表板]](media/service-report-create-new/power-bi-view-dataset.png)
6. 檢視資料集其實就是開啟報表編輯器。  您會看到空白的畫布和報表編輯工具。
   
   ![報表編輯器](media/service-report-create-new/power-bi-blank-report.png)

> **提示**︰如果您不熟悉報表編輯畫布，或需要複習一下，請先[導覽報表編輯器](service-the-report-editor-take-a-tour.md)，再繼續進行。
> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>將星形量測計新增至報表
既然已匯入我們的資料集，就讓我們開始回答一些問題。  我們的行銷長 (CMO) 想要知道我們距離本年度的銷售目標還有多遠。 量測計是[不錯的視覺效果選擇](visuals/power-bi-report-visualizations.md)，可顯示這種類型的資訊。

1. 在 [欄位] 窗格中，選取 [銷售] > [This Year Sales]\(本年度銷售額) > [值]。
   
    ![報表編輯器中的橫條圖](media/service-report-create-new/power-bi-report-step1.png)
2. 從 [視覺效果] 窗格選取量測計範本 ![量測計圖示](media/service-report-create-new/powerbi-gauge-icon.png)，將視覺效果轉換成量測計。
   
    ![報表編輯器中的量測計視覺效果](media/service-report-create-new/power-bi-report-step2.png)
3. 將 \[銷售] > \[This Year Sales]\(本年度銷售額) > \[目標] 拖曳至 \[目標值] 庫。 看起來我們非常接近我們的目標。
   
    ![目標為目標值的量測計視覺效果](media/service-report-create-new/power-bi-report-step3.png)
4. 現在是[儲存報表](service-report-save.md)的好時機。
   
   ![[檔案] 功能表](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>將區域圖和交叉分析篩選器新增至報表
我們的 CMO 已回答一些其他問題。 她想要知道今年與去年的銷售額比較。 而且，她想要依區域查看發現結果。

1. 首先，清出畫面上的一些空間。 選取 [量測計]，然後將它移至右上角。 接著抓取並拖曳其中一個角落，將它設為較小。
2. 取消選取量測計。 在 [欄位] 窗格中，選取 [銷售] > [This Year Sales]\(本年度銷售額) > [值]，然後選取 [銷售] > [Last Year Sales]\(去年度銷售額)。
   
    ![具有量測計和橫條圖的報表編輯器](media/service-report-create-new/power-bi-report-step4.png)
3. 從 [視覺效果] 窗格選取區域圖範本 ![圖表圖示](media/service-report-create-new/power-bi-areachart-icon.png)，以將視覺效果轉換成區域圖。
4. 選取 [時間] > [期間] 以將它新增至 [軸] 井。
   
    ![具有作用中區域圖的報表編輯器](media/service-report-create-new/power-bi-report-step5.png)
5. 若要依時間期間排序視覺效果，請選取省略符號，然後選擇 [依據期間排序]。
6. 現在讓我們新增交叉分析篩選器。 選取畫布上的空白區域，然後選擇交叉分析篩選器 ![交叉分析篩選器圖示](media/service-report-create-new/power-bi-slicer-icon.png)    範本。 這樣會將空白交叉分析篩選器新增至畫布。
   
    ![報表畫布](media/service-report-create-new/power-bi-report-step6.png)    
7. 從 [欄位] 窗格中，選取 [區域] > [區域]。 移動和調整交叉分析篩選器大小。
   
    ![在報表編輯器中新增區域](media/service-report-create-new/power-bi-report-step7.png)  
8. 使用交叉分析篩選器，依區域尋找模式和深入資訊。
   
   ![使用交叉分析篩選器的影片](media/service-report-create-new/power-bi-slicer-video2.gif)  

繼續探索資料，並新增視覺效果。 當您找到特別有趣的深入解析時，請[將它們釘選到儀表板](service-dashboard-pin-tile-from-report.md)。

## <a name="next-steps"></a>後續步驟

* 了解如何[將視覺效果釘選到儀表板](service-dashboard-pin-tile-from-report.md)   
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

