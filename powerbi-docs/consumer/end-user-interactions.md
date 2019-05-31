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
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413164"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>如何在 Power BI 報表中相互進行視覺效果交叉篩選
Power BI 的其中一項絕佳功能，是報表頁面上所有視覺效果互連的方式。 如果您選取其中一個視覺效果的資料點，頁面上包含該資料的其他視覺效果就會全部根據該選取項目而變更。 

![視覺效果互動的影片](media/end-user-interactions/interactions.gif)

依預設，選取一個報表頁面上的視覺效果中的資料點會交叉篩選、 交叉醒目提示，並向下鑽研頁面上的其他視覺效果。 

這可用來識別資料中的一個值中，提供給另一個。 比方說，在環圈圖中，選取 [合適性] 市場區段反白顯示該區段比重的總單位數月份圖表中的每個資料行，且它具有篩選右邊的折線圖。

![映像的視覺效果互動](media/end-user-interactions/power-bi-interactions.png)

請參閱[關於篩選及醒目提示](../power-bi-reports-filters-and-highlighting.md)。 

頁面上視覺效果的確切互動方式由報表「設計者」  建立。 設計者會有可以開啟和關閉視覺效果互動，以及變更預設交叉篩選、交叉醒目提示及切入行為的選項。 
  
> [!NOTE]
> 「交叉篩選」  與「交叉醒目提示」  這兩個詞彙用於區分本文所述，當您使用 [篩選]  窗格來篩選視覺效果及將其醒目提示時的這兩項行為。  

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
- 如果您的報表有支援的視覺效果[切入](../power-bi-visualization-drill-down.md)，根據預設，切入某個視覺效果在報表頁面上的其他視覺效果上沒有任何影響。     
- 如果您使用 visualA visualB 與互動時，從 visualA 的視覺效果層級篩選會套用至 visualB。

## <a name="next-steps"></a>後續步驟
[如何使用報表篩選](../power-bi-how-to-report-filter.md)
