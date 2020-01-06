---
title: 在 Power BI Desktop 中自訂工具提示
description: 使用拖放功能建立視覺效果的自訂工具提示
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: efbae4250b7b3cab18892cf519bfac5da3a88e1b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2020
ms.locfileid: "73868657"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>在 Power BI Desktop 中自訂工具提示
工具提示很適合用來為視覺效果的資料點提供更多關聯式資訊和詳細資料。 下圖顯示套用至 Power BI Desktop 中圖表的工具提示。

![預設工具提示](media/desktop-custom-tooltips/custom-tooltips-1.png)

建立視覺效果時，預設的工具提示會顯示資料點的值與類別。 在許多情況下，自訂工具提示資訊會很有用，而且可為檢視視覺效果的使用者提供額外的內容和資訊。 自訂工具提示可讓您指定額外的資料點，以當做工具提示的一部分顯示。

## <a name="how-to-customize-tooltips"></a>如何自訂工具提示
若要建立自訂工具提示，請在 [視覺效果]  窗格的 [欄位]  部分，將欄位拖曳到 [工具提示]  貯體即可，如下圖所示。 在下圖中，已將兩個欄位放入 [工具提示]  值區。

![新增工具提示欄位](media/desktop-custom-tooltips/custom-tooltips-2.png)

在工具提示新增到下層欄位之後，當滑鼠暫留在視覺效果的資料點上時，就會顯示工具提示中這些欄位的值。

![自訂工具提示](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>使用彙總或快速計算來自訂工具提示
您可以選取彙總函數或 [快速計算]  來進一步自訂工具提示，方法是選取 [工具提示]  值區中欄位旁邊的箭號，然後從可用的選項中進行選取。

![具快速計算功能的工具提示](media/desktop-custom-tooltips/custom-tooltips-4.png)

您可以使用資料集中任何可用的欄位，透過許多方式自訂 [工具提示]  ，以便將資訊和見解快速傳遞給檢視儀表板或報表的使用者。

