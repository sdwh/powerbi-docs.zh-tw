---
title: "向下鑽研 Power BI 的視覺效果"
description: "本文說明如何向下鑽研 Microsoft Power BI 服務和 Power BI Desktop 的視覺效果。"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: MNAaHw4PxzE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/08/2018
ms.author: mihart
ms.openlocfilehash: 22dc1c9b703b500625a5aed23b6187fd3f616dde
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="drill-down-in-a-visualization-in-power-bi"></a>向下鑽研 Power BI 的視覺效果
## <a name="drill-down-requires-a-hierarchy"></a>向下鑽研需要階層
當視覺效果有階層時，您可以向下鑽研以顯示其他詳細資料。 例如，您可能必須有一個視覺效果，它會以運動、專業領域和活動所構成的階層，查看奧運獎牌計數。 根據預設，視覺效果會依運動 (體操、滑雪、水上運動等) 顯示獎牌計數。但是因為它有階層，選取其中一個視覺項目 (例如列、線條或泡泡圖) 會顯示越來越多的詳細圖片。 選取 [水上運動] 項目，查看游泳、跳水和水球的資料。  選取 [跳水] 項目，查看跳板、平台和同時跳水活動的詳細資料。

您可以新增階層到您擁有的報表，但是不能新增到與您共用的報表。
不確定哪些 Power BI 視覺效果包含階層？  將滑鼠停駐在視覺效果上，如果您在上方角落看到這些鑽研控制項，您的視覺效果即具有階層。

![](media/power-bi-visualization-drill-down/power-bi-drill-icon4.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon3.png)
![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) ![](media/power-bi-visualization-drill-down/power-bi-drill-icon6.png)  

日期是獨特的階層類型。 當您將日期欄位新增到視覺效果時，Power BI 會自動新增包含年、季、月和日的時間階層。 如需詳細資訊，請參閱[視覺效果階層和向下鑽研行為](guided-learning/visualizations.yml#step-18)或觀看以下影片。

  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> 若要了解如何使用 Power BI Desktop 來建立階層，請觀賞影片 - [如何建立及新增階層](https://youtu.be/q8WDUAiTGeU)
> 
> 

## <a name="two-methods-to-drill-down"></a>兩種向下鑽研的方法
您有兩種不同的方法，可以向下鑽研 (及向上鑽研) 視覺效果。  本文將說明這兩種方法。 這兩種方法能達到相同的結果，因此您可以使用最喜愛的任何一種方法。

> [!NOTE]
> 如果要跟著做，請在 Power BI 服務中[開啟零售分析範例](sample-datasets.md)並建立矩形式樹狀結構圖，依**國家/地區**、**城市**、**郵遞區號**和**名稱** (群組) 來查看**今年的總單位數** (值)。  
> 
> 

## <a name="method-1-for-drill-down"></a>向下鑽研的方法 1
這個方法會使用視覺效果本身上方角落出現的鑽研圖示。

1. 在 Power BI 中，以[閱讀檢視或編輯檢視](service-reading-view-and-editing-view.md)開啟報表。 鑽研的視覺效果需要有階層。 
   
   階層會顯示在下列動畫中。  視覺效果具有由國家/地區、城市、郵遞區號和城市名稱組成的階層。 每個國家/地區有一或多個城市，每個城市有一或多個郵遞區號等等。根據預設，視覺效果只會顯示國家/地區資料，因為「國家/地區」最先出現在清單中。
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. 若要啟用向下鑽研，請選取視覺效果右上角的箭號圖示。 深色圖示表示已啟用鑽研。 如果您不開啟鑽研，則選取視覺項目 (例如橫條圖和泡泡圖) 將會交叉篩選報表頁面上的其他圖表。    
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-icon.png)
3. 若要***一次向下鑽研一個欄位***，請在視覺效果中按一下其中一個項目，在橫條圖中這表示按一下其中一個橫條，在矩形式樹狀結構圖中則表示按一下其中一個「葉子」。 請注意當您向下鑽研並重新往回時，標題會變更。 在此動畫中，它會從「國家/地區的今年總單位數」變更到「國家/地區和城市的今年總單位數」、「國家/地區、城市和郵遞區號的今年總單位數」最後到「國家/地區、城市、郵遞區號和名稱的今年總單位數」。 若要回頭向上鑽研，請選取視覺效果左上角的向上鑽研圖示![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png)，如下所示。
   
   ![](media/power-bi-visualization-drill-down/drill.gif)
4. 若要***一次向下鑽研所有欄位***，請選取視覺效果左上角的雙箭號。
   
   ![](media/power-bi-visualization-drill-down/pbi_drillall.png)
5. 若要回頭向上鑽研，請選取視覺效果左上角的向上箭號。
   
   ![](media/power-bi-visualization-drill-down/pbi_drillup2.png)

## <a name="method-2-for-drill-down"></a>向下鑽研的方法 2
這個方法會使用上方 Power BI 功能表列的 [瀏覽] 下拉式清單。

1. 在 Power BI 中，以[閱讀檢視或編輯檢視](service-reading-view-and-editing-view.md)開啟報表。 鑽研的視覺效果需要有階層。 
   
   階層會顯示在下圖中。  視覺效果具有由國家/地區、城市、郵遞區號和城市名稱組成的階層。 每個國家/地區有一或多個城市，每個城市有一或多個郵遞區號等等。根據預設，視覺效果只會顯示國家/地區資料，因為「國家/地區」最先出現在清單中。
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. 若要啟用向下鑽研，請選取視覺效果，讓它成為使用中，然後從 Power BI 上方功能表列選取 [瀏覽] > [向下鑽研]。 視覺效果右上角的向下鑽研圖示會變更為黑色背景。 ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  
   
   ![](media/power-bi-visualization-drill-down/power-bi-explore2.png)
3. 啟用後，選取其中一個矩形式樹狀結構圖葉子，即可一次向下鑽研一個欄位。 在此範例中，我已選取名為 **NC** 的國家/地區，依城市查看今年北卡羅來那州的總銷售單位數。
   
   ![](media/power-bi-visualization-drill-down/power-bi-drilldown-1.png)
4. 若要一次向下鑽研所有欄位，請選取 [瀏覽] > [顯示下一個層級]。
   
   ![](media/power-bi-visualization-drill-down/power-bi-show-next-level.png)
5. 若要回頭向上鑽研，請選取 [瀏覽] > [向上鑽研]。
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-up2.png)
6. 若要查看用來建立視覺效果的資料，請選取 [查看資料]。 資料會顯示在視覺效果下方的窗格中。 當您繼續鑽研視覺效果時，此窗格會保持開啟。 如需詳細資訊，請參閱[顯示用來建立視覺效果的資料](service-reports-show-data.md)。

## <a name="considerations-and-limitations"></a>考量與限制
* 如果將日期欄位新增至視覺效果不會建立階層，可能是因為「日期」欄位實際上不是儲存為日期。 如果您擁有資料集，請在 Power BI Desktop 的 [資料] 檢視中開啟它，選取包含日期的資料行，然後在 [模型] 索引標籤中將 [資料類型] 變更為 [日期] 或 [日期/時間]。 如果報表已與您共用，請連絡擁有者以要求變更。  
  
  ![](media/power-bi-visualization-drill-down/power-bi-change-data-type2.png)

## <a name="next-steps"></a>後續步驟
[Power BI 報表的視覺效果](power-bi-report-visualizations.md)

[Power BI 報表](service-reports.md)

[Power BI - 基本概念](service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

