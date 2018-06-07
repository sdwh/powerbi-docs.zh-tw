---
title: 在 Power BI Desktop 中自訂工具提示
description: 使用拖放功能建立視覺效果的自訂工具提示
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5dfd22f8b45253ece4ed8f699adec9abcaa1a8ed
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721148"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>在 Power BI Desktop 中自訂工具提示
工具提示很適合用來為視覺效果的資料點提供更多關聯式資訊和詳細資料。 下圖顯示套用至 Power BI Desktop 中圖表的工具提示。

![預設工具提示](media/desktop-custom-tooltips/custom-tooltips-1.png)

建立視覺效果時，預設的工具提示會顯示資料點的值與類別。 在許多情況下，能夠自訂工具提示資訊會很有用，而且可為檢視視覺效果的使用者提供額外的內容和資訊。 自訂工具提示可讓您指定額外的資料點，以當做工具提示的一部分顯示。

## <a name="how-to-customize-tooltips"></a>如何自訂工具提示
若要建立自訂工具提示，只要在 [視覺效果] 窗格的 [欄位] 部分，將欄位拖曳到 [工具提示] 值區即可，如下圖所示。 在下圖中，已將兩個欄位放入 [工具提示] 值區。

![新增工具提示欄位](media/desktop-custom-tooltips/custom-tooltips-2.png)

在工具提示新增到下層欄位之後，當滑鼠暫留在視覺效果的資料點上時，就會顯示工具提示中這些欄位的值。

![自訂工具提示](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>使用彙總或快速計算來自訂工具提示
您可以選取彙總函數或 [快速計算] 來進一步自訂工具提示，方法是選取 [工具提示] 值區中欄位旁邊的箭號，然後從可用的選項中進行選取。

![具快速計算功能的工具提示](media/desktop-custom-tooltips/custom-tooltips-4.png)

您可以使用資料集中的任何可用欄位，透過許多方式來自訂 [工具提示]，以便將資訊和深入解析快速傳遞給檢視儀表板或報表的使用者。

