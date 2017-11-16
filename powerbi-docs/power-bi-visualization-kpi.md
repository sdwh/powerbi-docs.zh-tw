---
title: "KPI 視覺效果 (教學課程)"
description: "在 Power BI 中建立 KPI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: xmja6EpqaO0
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/09/2017
ms.author: mihart
ms.openlocfilehash: 23b322c9fbc4c203a5b20aa45bb41c2cb6cb7f0f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="kpi-visuals-tutorial"></a>KPI 視覺效果 (教學課程)
關鍵效能指標 (KPI) 是一種視覺提示，指出對於可測量目標已達成的進度。 如需 KPI 的詳細資訊，請參閱 [Microsoft Developer Network](https://msdn.microsoft.com/library/hh272050)

## <a name="when-to-use-a-kpi"></a>使用 KPI 的時機
KPI 極適合：

* 測量進度 (超前或落後了那些項目？)
* 測量離目標的距離 (超前或落後了多少？)   

## <a name="kpi-visual-requirements"></a>KPI 視覺效果需求
關鍵效能指標 (KPI) 根據特定量值，設計來協助您評估針對定義目標的目前值和指標狀態。 因此，KPI 視覺效果需要評估為值的「基底」量值和「目標」量值或值，以及臨界值或目標。

> [!NOTE]
> 目前的 KPI 資料集必須包含 KPI 目標值。 若您的資料集未包含目標值，可透過將具有目標的 Excel 工作表新增至您的資料模型或 PBIX 檔案，以建立目標。
> 
> 

## <a name="how-to-create-a-kpi"></a>如何建立 KPI
如果要跟著做，請登入 Power BI 並選取 [取得資料] > [範例] > [零售分析範例]。 我們將建立 KPI，測量我們對業務目標已達成的進度。

或觀看 Will 說明如何建立單一計量的視覺效果︰量測計、卡片及 KPI。

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. 選取 [銷售額] > [本年度的總單位]。  這會是指標。
2. 新增 [時間] > [月份]。  這會顯示趨勢。
3. 重要：依照**月份**進行圖表排序。 將視覺效果轉換為 KPI 之後，即沒有選項可供排序。
4. 從 [視覺效果] 窗格中選取 KPI 圖示，將視覺效果轉換為 KPI。
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-icon.png)
5. 新增目標。 新增去年銷售為目標。 將 [去年度的總單位] 拖放至 [目標] 欄位。
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi.png)
6. (選擇性) 選取畫刷圖示可開啟 [格式化] 窗格來格式化 KPI。
   
   * **指標**：控制指標的顯示單位和小數位數。
   * **趨勢軸**：若設定為 [開啟]，就會顯示趨勢軸，作為 KPI 視覺效果的背景。  
   * **目標**：若設定為 [開啟]，視覺效果會顯示目標，並以百分比顯示離目標的距離。
   * **狀態**：某些 KPI 的值較高可視為「更好」，而某些則是值較低可視為「更好」。 例如，盈餘和 等待時間。 通常盈餘值較高代表「更好」，而等待時間更高通常代表「更糟」。 如此切換可讓您選取 KPI 的行為。 狀態選項預設為 **high is better** (越高越好).
7. 當您建立了想要的 KPI 後，請[將其釘選到儀表板](service-dashboard-pin-tile-from-report.md).

KPI 在行動裝置上也可供使用，讓您可隨時連接到貴企業的活動訊號

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
* 若您的 KPI 看起來不像上述說明，可能是因為您需要依照月份排序。 因為 KPI 沒有排序選項，所以將視覺效果轉換為 KPI *之前*，必須先依照月份排序。

## <a name="next-steps"></a>後續步驟
[Power BI 中的報表](service-reports.md)

[Power BI 報表的視覺效果](power-bi-report-visualizations.md)

[Power BI - 基本概念](service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

