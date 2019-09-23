---
title: 了解報表中的視覺效果互動方式
description: 適用於 Power BI 終端使用者的文件，說明視覺效果在報表頁面上的互動方式。
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 7148a52d7c7475fbe685f83b1e1cc325521460db
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2019
ms.locfileid: "66413164"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>如何在 Power BI 報表中相互進行視覺效果交叉篩選
Power BI 的其中一項絕佳功能，是報表頁面上所有視覺效果互連的方式。 如果您選取其中一個視覺效果的資料點，頁面上包含該資料的其他視覺效果就會全部根據該選取項目而變更。 

![視覺效果互動的影片](media/end-user-interactions/interactions.gif)

根據預設，選取報表頁面上某個視覺效果中的資料點將會交叉篩選、交叉醒目提示，以及切入頁面上的其他視覺效果。 

這有助於識別資料中某個值對另一個值的貢獻度。 例如，選取環圈圖中的 [合適性] 區段，會醒目提示該區段對依月份之單位總量圖表中每個資料行的貢獻度，並篩選出右側的折線圖。

![視覺效果互動的影像](media/end-user-interactions/power-bi-interactions.png)

請參閱[關於篩選及醒目提示](../power-bi-reports-filters-and-highlighting.md)。 

頁面上視覺效果的確切互動方式由報表「設計者」  建立。 設計者會有可以開啟和關閉視覺效果互動，以及變更預設交叉篩選、交叉醒目提示及切入行為的選項。 
  
> [!NOTE]
> 「交叉篩選」  與「交叉醒目提示」  這兩個詞彙用於區分本文所述，當您使用 [篩選]  窗格來篩選視覺效果及將其醒目提示時的這兩項行為。  

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
- 如果報表具有支援[切入](../power-bi-visualization-drill-down.md)的視覺效果，則根據預設，切入某個視覺效果不會影響報表頁面上的其他視覺效果。     
- 如果您使用 visualA 與 visualB 互動，則 visualA 中的視覺效果層級篩選將會套用至 visualB。

## <a name="next-steps"></a>後續步驟
[如何使用報表篩選](../power-bi-how-to-report-filter.md)
