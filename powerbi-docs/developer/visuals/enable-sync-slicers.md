---
title: 啟用同步交叉分析篩選器
description: 如何為 Power BI 視覺效果新增同步交叉分析篩選器功能
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425014"
---
# <a name="sync-slicers"></a>同步交叉分析篩選器

若要支援[同步交叉分析篩選器](https://docs.microsoft.com/power-bi/desktop-slicers)，您的自訂交叉分析篩選器視覺效果必須使用 API 1.13 或更高版本。

第二個必要條件是啟用 `capabilities.json` 中的選項 (請參閱以下範例)。

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

變更 `capabilities.json` 之後，當您按一下自訂交叉分析篩選器視覺效果時，就可以看到 [同步交叉分析篩選器] 選項面板。

> [!NOTE]
> 如果您的交叉分析篩選器具有多個欄位 (類別或量值)，則會停用此功能，因為同步交叉分析篩選器不支援多個欄位。

![[同步交叉分析篩選器] 面板](./media/sync-slicers-panel.png)

在面板中，您可以看到交叉分析篩選器可見度及其篩選可能套用至數個報表頁面。
