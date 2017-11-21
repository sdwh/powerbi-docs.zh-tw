---
title: "Power BI 服務中的分析窗格"
description: "為 Power BI 服務中的視覺效果建立動態參考線"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 05/02/2017
ms.author: mihart
ms.openlocfilehash: 30fc0731f819f063aa04e856e8acc75a69f64a59
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="analytics-pane-in-power-bi-service"></a>Power BI 服務中的分析窗格
有了 **Power BI 服務**的 [分析] 窗格，您就可以將動態「參考線」新增至視覺效果，為重要的趨勢或深入解析提供焦點。

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> [分析] 窗格只會在您選取報表畫布上的視覺效果時顯示。
> 
> 

## <a name="using-the-analytics-pane"></a>使用 [分析] 窗格
透過 [分析] 窗格，您可以建立下列類型的動態參考線 (並非所有線都是用於所有視覺效果類型)：

* X 軸常數線
* Y 軸常數線
* 最小值線
* 最大值線
* 平均值線
* 最小值線
* 中間值線

下列章節示範可以如何在視覺效果中使用 [分析] 窗格及動態參考線。

若要檢視視覺效果可用的動態參考線，請遵循下列步驟：

1. 選取或建立視覺效果，然後從 [視覺效果] 窗格選取分析圖示 ![](media/service-analytics-pane/power-bi-analytics-icon.png)。
2. 針對您要建立的線類型選取向下箭號，以展開其選項。 在這個案例中，我們選取 [平均值線]。
   
   ![](media/service-analytics-pane/power-bi-add.png)
3. 若要建立新的線，請選取 [+ 新增]。 您接著可以為線指定名稱，方法是按兩下文字方塊，然後鍵入名稱。
   
   您可以對線使用各種選項，例如選取其「色彩」、「透明度」、「樣式」及「位置」(相對於視覺效果的資料項目)，以及是否要包含標籤。 重要的是，您可以選取線要以視覺效果中的哪個 [量值] 為依據，方法是選取 [量值] 下拉式清單，其中已自動填入視覺效果中的資料項目。 在這個案例中，我們選取「開啟商店計數」作為量值，加上「平均開啟商店數」的標籤，然後自訂其他幾個選項，如下所示。
   
   ![](media/service-analytics-pane/power-bi-average-line.png)
4. 如果您希望資料標籤出現，請將 [資料標籤] 滑桿移為開啟。 當您這樣做時，即取得資料標籤的其他所有選項。
5. 請注意顯示在 [分析] 窗格中，[平均值線] 項目旁的數字。 這告訴您視覺效果上目前有多少條動態線及其類型。 如果我們新增 [常數線] 作為商店計數目標 9，您就會看到 [分析] 窗格顯示我們也對這個視覺效果套用了 [常數線] 參考線。
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   
   如果您選取的視覺效果無法套用動態參考線 (在這個案例中為 [地圖] 視覺效果)，您就會在選取 [分析] 窗格時看到下列內容。
   
   ![](media/service-analytics-pane/power-bi-no-lines.png)

透過 [分析] 窗格，您可以藉由建立動態參考線，醒目提示您感興趣的各種深入解析。

我們正在規劃更多功能，包括讓視覺效果有更多動態參考線可以套用，因此請時常回來查看新功能。

## <a name="limitations"></a>限制
使用動態參考線的能力取決於使用的視覺效果類型。 下表顯示目前有哪些視覺效果可以使用哪種動態線：

下列視覺效果可以完整使用動態線：

* 區域圖
* 折線圖
* 散佈圖
* 群組直條圖
* 群組橫條圖

下列視覺效果只可從 [分析] 窗格使用「常數線」：

* 堆疊區域圖
* 堆疊橫條圖
* 堆疊直條圖
* 100% 堆疊橫條圖
* 100% 堆疊直條圖

下列視覺效果目前只有「趨勢線」選項：

* 非堆疊折線圖
* 群組直條圖

最後，非笛卡兒視覺效果目前無法從 [分析] 窗格套用動態線，例如：

* 矩陣圖
* 圓形圖
* 環圈圖
* 資料表

## <a name="next-steps"></a>後續步驟
[Power BI Desktop 中的分析窗格](desktop-analytics-pane.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

