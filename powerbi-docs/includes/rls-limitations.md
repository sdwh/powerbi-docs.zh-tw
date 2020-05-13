---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: 912b0213c328c623e7881f7f30fe7d67f6d889b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274621"
---
## <a name="limitations"></a>限制

雲端模型目前的資料列層級安全性限制如下：

* 如果先前已在 Power BI 服務中定義了角色與規則，就必須在 Power BI Desktop 中重新建立。

* 您只能在使用 Power BI Desktop 建立的資料集上定義 RLS。 如果您想要針對以 Excel 建立的資料集啟用 RLS，必須先將檔案轉換成 Power BI Desktop (PBIX) 檔案。 [深入了解](../connect-data/desktop-import-excel-workbooks.md)。

* 只支援匯入和 DirectQuery 連線。 Analysis Services 即時連接是在內部部署模型中處理。

## <a name="known-issues"></a>已知問題

已知問題：若嘗試從 Power BI Desktop 發佈先前已發佈過的內容，則會產生錯誤訊息。 案例如下：

1. Anna 有個已發佈到 Power BI 服務的資料集，且已設定了 RLS。

1. Anna 在 Power BI Desktop 中更新了報表，然後重新發行。

1. Anna 收到錯誤。

**因應措施︰** 從 Power BI 服務重新發佈 Power BI Desktop 檔案，直到此問題解決為止。 您可以選取 [取得資料]   > [檔案]  以執行此動作。

