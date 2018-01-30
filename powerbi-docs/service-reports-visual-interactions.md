---
title: "變更報表中的視覺效果互動方式"
description: "說明如何設定 Microsoft Power BI 服務報表和 Power BI Desktop 報表中的視覺效果互動。"
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
ms.date: 01/10/2018
ms.author: mihart
ms.openlocfilehash: a7c4db0044772c28a3cb7a62649de3001945246c
ms.sourcegitcommit: afd6e9e6f8b192b26486cd04d2cbc9de046911b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="visualization-interactions-in-a-power-bi-report"></a>在 Power BI 報表中與視覺效果互動
如果您有報表的編輯權限，可以使用 [視覺效果互動] 變更報表頁面上視覺效果相互影響的方式。 

報表頁面上的視覺效果預設可用於交叉篩選和交叉醒目提示頁面上的其他視覺效果。
例如，選取地圖視覺效果的狀態，會醒目提示直條圖，並將折線圖篩選為只顯示適用於該狀態的資料。
請參閱[關於篩選及醒目提示](power-bi-reports-filters-and-highlighting.md)。 而如果您有支援[切入](power-bi-visualization-drill-down.md)的視覺效果，根據預設，切入某個視覺效果不會影響報表頁面上的其他視覺效果。 但您可依每個視覺效果覆寫這兩種預設行為，及設定其互動。

本文會示範如何在 Power BI 服務[編輯檢視](service-interact-with-a-report-in-editing-view.md)和 Power BI Desktop 中使用 [視覺效果互動]。 如已有人與您共用報表，您就不能變更視覺效果互動設定。

> [!NOTE]
> 「交叉篩選」與「交叉醒目提示」這兩個詞彙用於區分本文所述，當您使用 [篩選] 窗格來篩選視覺效果及將其醒目提示時的這兩項行為。  
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/N_xYsCbyHPw?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. 選取要啟用的視覺效果。  
2. 顯示 [視覺效果互動] 選項。
    - 在 Power BI 服務中，從 [報表] 功能表列上選取下拉式清單。

       ![](media/service-reports-visual-interactions/power-bi-visual-interaction.png)

    - 在 Desktop 中，選取 [格式] > [互動]。

        ![](media/service-reports-visual-interactions/pbi-visual-interaction-desktop.png)

3. 若要開啟視覺效果互動控制項，請選取 [編輯互動]。 Power BI 會將交叉篩選及交叉醒目提示圖示新增至報表頁面上所有其他視覺效果。
   
    ![](media/service-reports-visual-interactions/power-bi-icons-on.png)
3. 決定所選視覺效果對其他視覺效果的影響。  並也對報表頁面上所有其他視覺效果重複執行動作 (選用)。
   
   * 如應交叉篩選視覺效果，請選取**篩選**圖示 ![](media/service-reports-visual-interactions/pbi-filter-icon-outlined.png)。
   * 如應交叉醒目提示視覺效果，請選取**醒目提示**圖示 ![](media/service-reports-visual-interactions/pbi-highlight-icon-outlined.png)。
   * 若不應有任何影響，請選取**無影響**圖示 ![](media/service-reports-visual-interactions/pbi-noimpact-icon-outlined.png)。

4. 若要開啟切入控制項，請選取 [切入篩選其他視覺效果]。  現在當您向下 (和向上) 切入視覺效果時，報表頁面上的其他視覺效果會變更，以反映目前的切入選取項目。 

   ![](media/service-reports-visual-interactions/drill2.gif)

### <a name="next-steps"></a>後續步驟
[如何使用報表篩選](power-bi-how-to-report-filter.md)

[報表的篩選和醒目提示](power-bi-reports-filters-and-highlighting.md)

[Power BI - 基本概念](service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
