---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: davidi
ms.openlocfilehash: 6d1a239954a64da1c92cc68b56912e6f4ab67228
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "74882810"
---
## <a name="limitations"></a>限制

以下是雲端模型的資料列層級安全性目前限制清單。

* 如果先前已在 Power BI 服務中定義了角色與規則，就必須在 Power BI Desktop 中重新建立。

* 您只能在使用 Power BI Desktop 建立的資料集上定義 RLS。 如果您想要針對以 Excel 建立的資料集啟用 RLS，必須先將檔案轉換成 Power BI Desktop (PBIX) 檔案。 [深入了解](../desktop-import-excel-workbooks.md)

* 只支援匯入和 DirectQuery 連線。 Analysis Services 即時連接是在內部部署模型中處理。

## <a name="known-issues"></a>已知問題

已知問題：若嘗試從 Power BI Desktop 發佈先前已發佈過的內容，會產生錯誤訊息。 案例如下。

1. Anna 有個已發佈到 Power BI 服務的資料集，且已設定了 RLS。

1. Anna 在 Power BI Desktop 中更新了報表，然後重新發行。

1. Anna 收到錯誤。

**因應措施：** 從 Power BI 服務重新發佈 Power BI Desktop 檔案，直到此問題解決為止。 您可以選取 [取得資料] > [檔案] 以執行此動作。
