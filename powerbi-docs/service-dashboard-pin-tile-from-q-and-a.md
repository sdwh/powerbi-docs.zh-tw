---
title: "從問與答將磚釘選到 Power BI 儀表板"
description: "說明如何從問與答的問題方塊將磚釘選至 Power BI 儀表板"
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
ms.date: 09/09/2017
ms.author: mihart
ms.openlocfilehash: f37c0f9e433f1ac8c6bb8f7f3fa4b513fb4b4652
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>從問與答將磚釘選到儀表板
## <a name="how-to-pin-a-tile-from-qa"></a>如何從問與答釘選磚
問與答是 Power BI 隨選報表工具。 需要尋找特定的深入剖析資訊嗎？ 提出與您的資料有關的問題，然後以視覺效果的形式接收回應。

> **注意**：如果要跟著做，請開啟[零售分析範例](sample-retail-analysis.md)。
> 
> 

1. 開啟[儀表板](service-dashboards.md)，其中至少有一個從報表釘選的磚。 當您提問時，Power BI 會在具有釘選到該儀表板之磚的任何資料集中尋找解答。  若要深入了解，請參閱[取得資料](service-get-data.md)。
2. 在儀表板頂端的問題方塊中，開始輸入您想要知道的資料相關問題。  
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. 例如，當您輸入「去年各月份和地區的銷售額」...   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)
   
   問題方塊可提供您建議。
4. 若要將圖表加入儀表板作為磚，請選取畫布右上角的釘選圖示 ![](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png)。
5. 將磚釘選至現有的儀表板或新的儀表板上。 
   
   * 現有儀表板：從下拉式清單中選取儀表板的名稱。 您只能選擇具有目前工作區的儀表板。
   * 新的儀表板︰輸入新儀表板的名稱，它就會新增至目前工作區。
6. 選取 [釘選] 。
   
   靠近右上角的成功訊息讓您知道，視覺效果已當成磚加入儀表板。  
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. 選取 [移至儀表板] 以查看新磚。 於該處，您可以在儀表板上[重新命名、調整大小、加入超連結和重新置放磚等等](service-dashboard-edit-tile.md)。 
   
   ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
* 當您開始輸入問題時，問與答會立即開始從與目前儀表板相關聯的所有資料集搜尋最佳回應。  「目前儀表板」是列在上方導覽列中的儀表板。 例如，這個問題將會在 [零售分析範例] 儀表板中提出，而此儀表板是 **mihart** 應用程式工作區的一部分。
  
  ![](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **問與答如何知道要使用哪些資料集**？  問與答可存取具有已釘選至儀表板之視覺效果的所有資料集。

## <a name="next-steps"></a>後續步驟
[重新命名、調整大小、新增超連結和重新置放磚等等](service-dashboard-edit-tile.md)    
[以焦點模式顯示儀表板磚](service-focus-mode.md)     
[返回 Power BI 中的問與答](service-q-and-a.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

