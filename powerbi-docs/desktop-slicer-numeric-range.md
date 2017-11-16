---
title: "在 Power BI Desktop 中使用數值範圍交叉分析篩選器"
description: "了解如何在 Power BI Desktop 中使用交叉分析篩選器來限制數值範圍"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 713497c8c684b34cbaaeafab84a7db1fc7d14c2a
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>在 Power BI Desktop 中使用數值範圍交叉分析篩選器
透過 [數值範圍交叉分析篩選器]，您可以將各式各樣的篩選器套用至資料模型中的任何數值資料行。 您可以選擇篩選兩個數字**之間**、**小於或等於**某個數字，或是**大於或等於**某個數字。 這聽起來或許很簡單，但卻是篩選資料的強大方式。

![](media/desktop-slicer-numeric-range/slicer-numeric-range_2.png)

## <a name="using-the-numeric-range-slicer"></a>使用數值範圍交叉分析篩選器
您可以將數值範圍交叉分析篩選器當作任何其他交叉分析篩選器來使用。 只要建立報表的 [交叉分析篩選器] 視覺效果，然後選取一個數值作為 [欄位] 值即可。 在下圖中，已選取 [UnitPrice] 欄位。

![](media/desktop-slicer-numeric-range/slicer-numeric-range_3.png)

選取 [數值範圍交叉分析篩選器] 右上角的插入號，即會出現一個功能表。

![](media/desktop-slicer-numeric-range/slicer-numeric-range_4.png)

針對數值範圍，您可以從下列三個選項中進行選取：

* 之間
* 小於或等於
* 大於或等於

當您從功能表選取 [之間] 時，會出現一個滑桿，以供您篩選落於兩個數字之間的數值。 除了使用滑動軸本身，您還可以按一下任一方塊，然後輸入值。 當您想要配量特定整數時，此方法十分方便，但移動滑動軸的精細度很難剛好落在該數字上。

在下圖中，會針對範圍介於 500 到 1500 之間的 [UnitPrice] 值篩選報表頁面。

![](media/desktop-slicer-numeric-range/slicer-numeric-range_5.png)

當我們選取 [小於或等於] 時，滑動軸的左控點 (下限值) 會消失，而我們只能調整滑動軸的上限。 在下圖中，我們會將滑動軸設定為 497.17。

![](media/desktop-slicer-numeric-range/slicer-numeric-range_6.png)

最後，如果我們選取 [大於或等於]，則滑動軸的右控點 (上限值) 會消失，而我們可以調整下限值，如下圖所示。 現在，只有 [UnitPrice] 大於或等於 750.56 的項目會顯示在報表頁面的視覺效果中。

![](media/desktop-slicer-numeric-range/slicer-numeric-range_7.png)

## <a name="limitations-and-considerations"></a>限制與考量
[數值範圍交叉分析篩選器] 目前適用下列限制與考量

* [數值範圍交叉分析篩選器] 目前會篩選資料中的每個基礎資料列，而不是任何彙總值。 例如，如果使用 [Sales Amount] 欄位，則會根據 [Sales Amount] 篩選每筆交易，而不是根據視覺效果之每個資料點的 [Sales Amount] 總和。
* 目前無法搭配量值使用
* 目前只能在 **Power BI Desktop** 中使用 [數值範圍交叉分析篩選器]。 如果將使用 [數值範圍交叉分析篩選器] 的報表發佈至 **Power BI 服務**，還是會套用此篩選器，但會顯示為清單交叉分析篩選器。

