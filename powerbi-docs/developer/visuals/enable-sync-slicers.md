---
title: 在 Power BI 視覺效果中啟用同步交叉分析篩選器功能
description: 此文章說明如何將同步交叉分析篩選器功能新增至 Power BI 視覺效果。
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4d7b73a5d06f34fd197464d4444d0e19d6c1c026
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237201"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Power BI 中的同步交叉分析篩選器

若要支援[同步交叉分析篩選器](https://docs.microsoft.com/power-bi/desktop-slicers) \(部分機器翻譯\) 功能，您的自訂交叉分析篩選器視覺效果必須使用 API 1.13 版或更新版本。

此外，您也必須啟用 *capabilities.json* 檔案中的選項，如下列程式碼所示：

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

更新 *capabilities.json* 檔案之後，當您選取您的自訂交叉分析篩選器視覺效果時，就能檢視 [同步交叉分析篩選器]  選項窗格。

> [!NOTE]
> 同步交叉分析篩選器功能不支援多個欄位。 如果交叉分析篩選器有多個欄位 (**Category** 或 **Measure**)，系統會停用該功能。

![[同步交叉分析篩選器] 窗格](./media/sync-slicers-panel.png)

在 [同步交叉分析篩選器]  窗格中，您可以看到交叉分析篩選器可見度及其篩選可以套用至數個報表頁面。
