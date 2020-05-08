---
title: 變更報表中的圖表排序方式
description: 變更 Power BI 報表中的圖表排序方式
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 02/19/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 1a59618ea27944314465d8e08d5f0c249c3bed0b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "77496487"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>變更 Power BI 報表中的圖表排序方式

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]


> [!IMPORTANT]
> **此文章適用於沒有報表或資料集編輯權限，且僅使用 Power BI 線上版本 (Power BI 服務) 的 Power BI 使用者。如果您是報表「設計師」  或「系統管理員」  或「擁有者」  ，此文章可能不包含您所需的所有資訊。相反地，請參閱[在 Power BI Desktop 中依資料行排序](../desktop-sort-by-column.md)** 。

在 Power BI 服務中，您可以依不同資料欄位進行排序來變更視覺效果外觀。 您可以藉由變更視覺效果的排序方式來強調所要傳達的資訊。 無論您是使用數值資料 (例如銷售數字) 或文字資料 (例如州名稱)，都能以想要的方式來排序視覺效果。 Power BI 提供更多的排序彈性，以及可供您使用的快速功能表。 

您無法排序儀表板上的視覺效果，但可以在 Power BI 報表中排序大部分視覺效果 

## <a name="get-started"></a>開始使用

首先，請開啟任一與您共用的報表。 選取一項 (可以排序的) 視覺效果，然後選擇 [更多選項]  (...)。有三個排序選項：[遞減排序]  、[遞增排序]  和 [排序依據]  。 
    

![依 X 軸以英文字母排序的橫條圖](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>依字母或數值順序排序

您可以依視覺效果類別文字名稱的字母順序來排序視覺效果，或依每個類別的數值來排序。 例如，此圖表是依 X 軸商店**名稱**類別的字母順序排序。

![依 X 軸以英文字母排序的橫條圖](media/end-user-change-sort/powerbi-sort-category.png)

可以輕鬆地將排序從類別 (商店名稱) 變更為值 (每平方英尺銷售額)。 選取 [其他動作]  (...)，然後選擇 [排序依據]  。 選取用於視覺效果的數值。  在此範例中，我們選取了 [每平方英呎的銷售額]  。

![顯示依序選取 [排序依據] 和某個值的螢幕擷取畫面](media/end-user-change-sort/power-bi-sort-value.png)

如有必要，請在遞增和遞減之間變更排序次序。  再次選取 [其他動作]  (...)，然後選擇 [遞減排序]  或 [遞增排序]  。 用來排序的欄位是以粗體顯示，且具有黃色橫條。

   ![顯示選取排序方式並選取遞增或遞減的影片](media/end-user-change-sort/sort.gif)

> [!NOTE]
> 並非所有的視覺效果都可以排序。 例如，下列視覺效果無法排序：樹狀圖、地圖、區域分布圖、散佈圖、量表圖、卡片、瀑布圖。

## <a name="saving-changes-you-make-to-sort-order"></a>儲存您對排序次序的變更
Power BI 報表會保留您所做的篩選、交叉分析篩選器、排序與其他資料檢視變更 -- 即使您是在[閱讀檢視](end-user-reading-view.md)中工作也一樣。 因此如果您離開報表並稍後返回，系統會儲存您的排序變更。  如果您想要將所做的變更還原至報表設計師  的設定，請從頂端功能表列選取 [重設為預設值]  。 

![永續性排序](media/end-user-change-sort/power-bi-reset.png)

不過，如果 [重設為預設值]  按鈕呈現灰色，則表示報表「設計師」  已停用儲存 (保留) 變更的功能。

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

### <a name="sorting-using-other-criteria"></a>使用其他準則排序
有時候，您會想要使用不同欄位 (未包含在視覺效果中的欄位) 或其他準則來排序視覺效果。  例如，您可能想要依月份循序 (而不是依字母順序) 排序，或您可能想要依整個數值而不是數字排序 (例如 0、1、9、20，而不是 0、1、20、9)。  

只有設計報表的人員可以為您進行這些變更。 從標頭列選取報表名稱，即可找到「設計師」  的連絡資訊。

![顯示連絡資訊的下拉式清單](media/end-user-change-sort/power-bi-contact.png)

如果您是設計師  並擁有內容的編輯權限，請閱讀 [Power BI Desktop 中的依資料行排序](../desktop-sort-by-column.md)，以了解如何更新資料集並啟用此類型的排序。

## <a name="next-steps"></a>後續步驟
深入了解 [Power BI 報表中的視覺效果](end-user-visualizations.md)。

[Power BI - 基本概念](end-user-basic-concepts.md)
