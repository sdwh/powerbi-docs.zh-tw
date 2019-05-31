---
title: 使用 Power BI 問與答建立的視覺效果
description: 了解如何使用問與答中建立視覺效果，在 Power BI 服務中使用零售分析範例
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 580b387f8c763b0457bd32a71bfbccd90d4040a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625162"
---
# <a name="create-a-visual-with-power-bi-qa"></a>使用 Power BI 問與答建立的視覺效果

有時若要從您的資料獲得解答，最快的方法是使用自然語言詢問問題。  在本文中，我們探討兩種不同的方式建立的相同視覺效果： 首先，使用問與答、 提問和第二，在報表中建立。 我們來建立視覺效果在報表中，使用 Power BI 服務，但程序幾乎完全相同使用 Power BI Desktop。

![Power BI 的區域分布圖](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

若要跟著做，您必須使用您可以編輯的報表，因此我們將使用 Power BI 提供的其中一個範例。

## <a name="create-a-visual-with-qa"></a>問與答中建立視覺效果

我們如何建立此折線圖，來使用問與答？

1. 從您的 Power BI 工作區選取 [Get Data] (取得資料)  \> [範例]  \> [零售分析範例]   >  [連接]  。

1. 開啟 零售分析範例儀表板，並將游標放在問與答方塊中，**詢問資料相關問題**。

    ![將游標放在問與答方塊](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. 在 問與答方塊中，輸入類似此問題：
   
    **本年度銷售額和去年各月份，以區域圖的**
   
    當您輸入您的問題後，問與答會挑選最佳的視覺效果來顯示您的答案；而當您修改這個問題時，視覺效果就會動態改變。 問與答也可以用建議、自動完成及拼字校正，協助您建立問題。 問與答建議的小型文字變更: 「 本年度銷售額和去年銷售額*時間月*以區域圖 」。  

    ![問與答已更正的措辭](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. 選取要接受建議的句子。 
   
   當您完成問題輸入後時，結果會是您在儀表板中看到相同的圖表。
   
   ![問與答的填滿的區域圖](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. 若要將圖表釘選至儀表板，請選取釘選圖示 ![釘選圖示](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) 報表圖示。

## <a name="create-a-visual-in-the-report-editor"></a>在報表編輯器中建立視覺效果

1. 巡覽回 [零售分析範例] 儀表板。
   
2. 儀表板包含相同的區域圖表 圖格 」 去年度銷售額和本年度銷售量 」。  選取此圖格。 請勿選取您所建立的問與答磚 選取開啟問與答。 讓報表會開啟含有這個視覺效果的頁面在報表中，建立原始的區域圖表圖格。

    ![[零售分析範例] 儀表板](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. 選取 [編輯報表]  ，在 [編輯檢視] 中開啟報表。  如果您不是報表的擁有者，就不會有在 [編輯] 檢視中開啟報表的選項。
   
    ![[編輯報表] 按鈕](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. 選取區域圖，然後在 [欄位]  窗格中檢閱設定。  報表建立者選取這三個值建立此圖表 (**去年度銷售額**並**本年度銷售額 > 值**從**銷售**資料表，和**FiscalMonth**從**時間**資料表) 和中組織這些**軸**並**值**井。
   
    ![[視覺效果] 窗格](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    您會看到它們最終會有相同的視覺效果。 這種建立方式不太複雜了。 但建立問與答更容易 ！

## <a name="next-steps"></a>後續步驟

- [在儀表板和報表中使用問與答](power-bi-tutorial-q-and-a.md)  
- [問與答的取用者](consumer/end-user-q-and-a.md)
- [讓資料適用於 Power BI 的問與答](service-prepare-data-for-q-and-a.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

