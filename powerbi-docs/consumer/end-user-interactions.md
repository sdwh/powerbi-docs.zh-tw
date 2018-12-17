---
title: 如何在報表中相互進行視覺效果交叉篩選 (適用於報表取用者)
description: 適用於 Power BI 終端使用者的文件，說明視覺效果在報表頁面上的互動方式。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 838b881622dd19eb881aa53ac895f223cf9bc460
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180499"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>如何在 Power BI 報表中相互進行視覺效果交叉篩選
Power BI 的其中一項絕佳功能，是報表頁面上所有視覺效果互連的方式。 如果您選取其中一個視覺效果的資料點，頁面上包含該資料的其他視覺效果就會全部根據該選取項目而變更。 

![視覺效果互動的影片](media/end-user-interactions/interactions.gif)

根據預設，報表頁面上的視覺效果可用於交叉篩選和交叉醒目提示，以及切入頁面上的其他視覺效果。 例如，選取地圖視覺效果上的一個州，會醒目提示直條圖，並將折線圖篩選為只顯示適用於那個州的資料。

請參閱[關於篩選及醒目提示](../power-bi-reports-filters-and-highlighting.md)。 而如果您有支援[切入](../power-bi-visualization-drill-down.md)的視覺效果，根據預設，切入某個視覺效果不會影響報表頁面上的其他視覺效果。 

頁面上視覺效果的確切互動方式由報表「設計者」建立。 設計者會有可以開啟和關閉視覺效果互動，以及變更預設交叉篩選、交叉醒目提示及切入行為的選項。
  
> [!NOTE]
> 「交叉篩選」與「交叉醒目提示」這兩個詞彙用於區分本文所述，當您使用 [篩選] 窗格來篩選視覺效果及將其醒目提示時的這兩項行為。  

### <a name="next-steps"></a>後續步驟
[如何使用報表篩選](../power-bi-how-to-report-filter.md)
