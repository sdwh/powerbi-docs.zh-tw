---
title: "變更報表中的視覺效果互動方式"
description: "說明如何設定 Microsoft Power BI 報表中的視覺效果互動方式。"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: N_xYsCbyHPw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 126bd40e98a88138a2732155f9792d65666e52c7
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>在 Power BI 報表中與視覺效果互動
報表頁面上的視覺效果預設可用於交叉篩選和交叉醒目提示頁面上的其他視覺效果。
例如，選取地圖視覺效果的狀態，會醒目提示直條圖，並將折線圖篩選為只顯示適用於該狀態的資料。
請參閱[關於篩選及醒目提示](power-bi-reports-filters-and-highlighting.md)。

若要變更此預設行為，請使用**視覺效果互動**控制項。 只有[編輯檢視](service-interact-with-a-report-in-editing-view.md)提供視覺效果互動。 如果報表已與您共用，您就不能存取視覺效果互動。

> [!NOTE]
> 「交叉篩選」與「交叉醒目提示」這兩個詞彙用於區分本文所述，當您使用 [篩選] 窗格來篩選視覺效果及將其醒目提示時的這兩項行為。  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. 選取要啟用的視覺效果。  
2. 從頂端功能表列中選取 [視覺互動]  加以開啟。 請注意，當您將滑鼠停留在報表頁面的其他視覺效果上時，篩選與醒目提示圖示就會出現。
   
    ![](media/service-reports-visual-interactions/pbi-visual-interaction-icon.png)
3. 決定所選視覺效果對其他視覺效果的影響。  
   
   * 如應交叉篩選其他視覺效果，請選取**篩選**圖示　![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png)。
   * 如應交叉醒目提示該視覺效果，請選取**醒目提示**圖示 ![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png)。
   * 若不應有任何影響，請選取**無影響**圖示 ![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png)。
4. 或者對報表頁面上的所有其他視覺效果重複執行。

### <a name="next-steps"></a>後續步驟
[如何使用報表篩選](power-bi-how-to-report-filter.md)

[報表的篩選和醒目提示](power-bi-reports-filters-and-highlighting.md)

[Power BI - 基本概念](service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

