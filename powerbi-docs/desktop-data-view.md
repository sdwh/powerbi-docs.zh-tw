---
title: Power BI Desktop 中的資料檢視
description: Power BI Desktop 中的資料檢視
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a82465adb5b0c7fe8be0e6e724c5eda1bfcf7ec0
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538633"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>在 Power BI Desktop 中使用資料檢視

「資料檢視」  可協助您檢查、探索及了解 *Power BI Desktop* 模型中的資料。 這與您在「Power Query 編輯器」  中檢視資料表、資料行和資料的方式不同。 透過資料檢視，您看到的是載入模型「之後」  的資料。

當您建立資料模型時，有時會想要在報表畫布上沒有建立視覺效果的情況下查看資料表或資料行中實際內容。 您可能想要向下查看資料列層級。 此功能特別適用於當您要建立量值和計算結果欄，或需要識別資料類型或資料類別時。

讓我們探討資料檢視中找到的某些項目。

![Power BI Desktop 中的資料檢視](media/desktop-data-view/dataview_fullscreen.png)

1. **資料檢視圖示**。 選取此圖示以進入資料檢視。

2. **資料格**。 這個區域顯示選取的資料表，以及其中的所有資料行和資料列。 「報表」  檢視中隱藏的資料行會呈現灰色。以滑鼠右鍵按一下資料行，顯示選項。

3. **模型化功能區**。 您可以在此處管理關聯性；建立計算；變更資料行的資料類型、格式、資料類別。

4. **公式列**。 輸入量值和計算結果欄的資料分析運算式 (DAX) 公式。

5. **搜尋**。 在模型中搜尋資料表或資料行。

6. **欄位清單**。 選取要在資料格中檢視的資料表或資料行。

## <a name="filtering-in-data-view"></a>資料檢視中的篩選

您也可以在資料檢視中篩選和排序資料。 每個資料行顯示的圖示會識別排序方向 (若已套用)。

![在 Power BI Desktop 中的資料檢視中排序和篩選](media/desktop-data-view/dataview_sort-and-filter.png)

您可以篩選個別值，或依據資料行中的資料使用進階篩選。

> [!NOTE]
> 當 Power BI 模型在與您目前使用者介面不同的文化特性 (Culture) 中建立時，除了文字欄位以外，資料檢視使用者介面中不會出現搜尋方塊。 例如，這適用於以美式英文建立並以西班牙文檢視的模型。
