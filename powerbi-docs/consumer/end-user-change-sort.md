---
title: 變更報表中的圖表排序方式
description: 變更 Power BI 報表中的圖表排序方式
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 98a91b0651e7a357f0ba0462f6ba8734c64ab162
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2019
ms.locfileid: "70302725"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>變更 Power BI 報表中的圖表排序方式
在 Power BI 報告中，您可以依圖表類別名稱的字母順序排序大部分的視覺效果，或依每個類別的數值排序。 例如，這張圖表是依照類別**商店名稱**排序。

![依 X 軸以英文字母排序的橫條圖](media/end-user-change-sort/pbi_chartsortcategory.png)

可以輕鬆地將排序從類別 (商店名稱) 變更為值 (每平方英尺銷售額)。

1. 選取省略符號 (...) 並選擇 [排序依據] > [每平方英尺銷售額]  。
2. 如有必要，請再次選取省略符號，然後選擇 [遞減排序]  。

   ![顯示選取排序方式並選取遞增或遞減的影片](media/end-user-change-sort/sort.gif)

> [!NOTE]
> 並非所有的視覺效果都可以排序。 例如，下列視覺效果無法排序：樹狀圖、地圖、區域分布圖、散佈圖、量表圖、卡片、瀑布圖。

## <a name="saving-changes-you-make-to-sort-order"></a>儲存您對排序次序的變更
Power BI 報表保留篩選、交叉分析篩選器、排序和您進行的的其他資料檢視變更。 因此如果您離開報表並稍後再回來時，會儲存您的變更。  如果您想要將所做的變更還原至報表設計師的設定，請從頂端功能表列選取 [重設為預設值]  。 

![永續性排序](media/end-user-change-sort/power-bi-reset.png)

但是，如果 [重設為預設值]  按鈕呈現灰色，則表示報表設計師已停用儲存 (保留) 變更的功能。

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>使用其他準則排序
有時候，您會想要使用不同的欄位或其他準則來排序您的視覺效果。  例如，您可能想要依月份 (而不是字母順序) 排序，或您可以想要依整個數值而不是數字排序 (例如 0、 1、 9、 20，而不是 0、 1、 20、 9)。  

在某些情況下，您可以依想要的方式排序視覺效果 (例如，依月份)。  但是，否則原因可能是報表後面的資料集需要一些變化。 要求報表設計師更新資料集。

## <a name="next-steps"></a>後續步驟
深入了解 [Power BI 報表中的視覺效果](end-user-visualizations.md)。

[Power BI - 基本概念](end-user-basic-concepts.md)
