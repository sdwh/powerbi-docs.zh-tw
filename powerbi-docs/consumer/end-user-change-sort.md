---
title: 變更報表中的圖表排序方式
description: 變更 Power BI 報表中的圖表排序方式
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852375"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>變更 Power BI 報表中的圖表排序方式

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

在 Power BI 服務中，您可以依不同資料欄位進行排序來變更視覺效果外觀。 變更視覺效果的排序方式，即可反白顯示您想要傳達的資訊，並確定視覺效果反映出該趨勢 (或強調)。

無論您是使用數值資料 (例如銷售數據) 或文字資料 (如州名稱)，都能以您希望的方式排序視覺效果，變成您要的樣子。 Power BI 提供更多的排序彈性，以及可供您使用的快速功能表。 在任何視覺效果上，選取 [其他動作]  (...)，然後選取您要用來排序的欄位。

![依 X 軸以英文字母排序的橫條圖](media/end-user-change-sort/power-bi-more-actions.png)

儀表板上的視覺效果無法排序，但是在 Power BI 報表中，您可以依圖表類別名稱的字母順序排序大部分視覺效果，或依每個類別的數值排序。 例如，這張圖表是依照 [門市名稱]  類別的字母順序排序。

![依 X 軸以英文字母排序的橫條圖](media/end-user-change-sort/pbi-chartsortcategory.png)

可以輕鬆地將排序從類別 (商店名稱) 變更為值 (每平方英尺銷售額)。

1. 選取 [其他動作]  (...)，並選擇 [排序依據] > [每平方英呎銷售額]  。
2. 如有必要，請再次選取**其他動作** (...)，然後選擇 [遞減排序]  。 用來排序的欄位是以粗體顯示，且具有黃色橫條。

   ![顯示選取排序方式並選取遞增或遞減的影片](media/end-user-change-sort/sort.gif)

> [!NOTE]
> 並非所有的視覺效果都可以排序。 例如，下列視覺效果無法排序：樹狀圖、地圖、區域分布圖、散佈圖、量表圖、卡片、瀑布圖。

## <a name="saving-changes-you-make-to-sort-order"></a>儲存您對排序次序的變更
Power BI 報表保留篩選、交叉分析篩選器、排序和您進行的的其他資料檢視變更。 因此如果您離開報表並稍後再回來時，會儲存您的變更。  如果您想要將所做的變更還原至報表設計師的設定，請從頂端功能表列選取 [重設為預設值]  。 

![永續性排序](media/end-user-change-sort/power-bi-reset.png)

但是，如果 [重設為預設值]  按鈕呈現灰色，則表示報表設計師已停用儲存 (保留) 變更的功能。

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>使用其他準則排序
有時候，您會想要使用不同欄位 (未包含在視覺效果中的欄位) 或其他準則來排序視覺效果。  例如，您可能想要依月份 (而不是字母順序) 排序，或您可以想要依整個數值而不是數字排序 (例如 0、 1、 9、 20，而不是 0、 1、 20、 9)。  報表設計師將能夠更新資料集，以啟用這種類型的排序。 從標頭列選取報表名稱，即可找到設計師的連絡資訊。

![顯示連絡資訊的下拉式清單](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>後續步驟
深入了解 [Power BI 報表中的視覺效果](end-user-visualizations.md)。

[Power BI - 基本概念](end-user-basic-concepts.md)
