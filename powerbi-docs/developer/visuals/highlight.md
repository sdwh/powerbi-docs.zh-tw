---
title: 醒目提示
description: Power BI 視覺效果中的資料點選取項目醒目提示
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424807"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>在 Power BI 視覺效果中醒目提示資料點

根據預設，每當選取一個元素時，都會篩選 `dataView` 物件中的 `values` 陣列只顯示選取的值。 這會導致頁面上所有其他視覺效果只顯示選取的資料。

![醒目提示 `dataview` 預設行為](./media/highlight-dataview.png)

如果您將 `capabilities.json` 中的 `supportsHighlight` 屬性設定為 `true`，則會收到未篩選的完整 `values` 陣列及 `highlights` 陣列。 `highlights` 陣列的長度會與 values 陣列相同，且任何非選取的值都會設定為 `null`。 啟用此屬性時，視覺效果會負責將 `values` 陣列與 `highlights` 陣列進行比較，以醒目提示適當的資料。

![醒目提示 `dataview` supportshighlight](./media/highlight-dataview-supports.png)

在此範例中，您會注意到選取了 1 個直條。 這是 highlights 陣列中唯一的值。 另請務必注意，可能會有多個選取項目和部分醒目提示。 這些 values 和 highlights 陣列中會有對應但不同的數值。
