---
title: Power BI 問與答的限制
description: Power BI 問與答的目前限制
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
ms.openlocfilehash: b71fd2986fb79adf88493416ac8234f2656aefa9
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866763"
---
# <a name="limitations-of-power-bi-qa"></a>Power BI 問與答的限制

Power BI 問與答目前有一些限制。

## <a name="data-sources"></a>資料來源

### <a name="supported-data-sources"></a>支援的資料來源

Power BI 問與答支援 Power BI 服務中的下列資料來源設定：

- 匯入模式
- 即時連接到 Azure Analysis Services
- 即時連線到 SQL Server Analysis Services (使用閘道)
- Power BI 資料集。

在上述每項設定中，也支援資料列層級安全性。

### <a name="data-sources-not-supported"></a>不支援的資料來源

Power BI 問與答目前不支援下列設定：

- 任何資料來源類型的物件層級安全性
- 對任何來源進行 DirectQuery。 其因應措施是透過 Azure Analysis Services 使用即時連線，這會用到 DirectQuery。
- 複合模型
- Reporting Services 

## <a name="tooling-limitations"></a>工具限制

新工具對話方塊可讓使用者自訂和改善問與答中的自然語言。 若要深入了解工具，請參閱[問與答工具簡介](q-and-a-tooling-intro.md)。

## <a name="review-question-limitations"></a>檢閱問題限制

檢閱問題最多只會將針對資料模型所詢問的問題儲存 28 天。 使用新的檢閱問題功能時，您可能注意到不會記錄某些問題。 根據設計不予記錄，因為自然語言引擎會執行一連串的資料清理步驟，確保不會記錄或顯示使用者每一次的按鍵輸入。

租用戶系統管理員可以使用租用戶系統管理員設定來管理儲存問題的能力。 權限是以安全性群組為基礎。 

使用者也可以選取 [設定]   > [一般]  ，然後取消選取 [Allow Q&A to record my utterance] \(允許問與答記錄我的表達\)  來避免記錄其問題。 

## <a name="teach-qa-limitations"></a>教學 Q&A 限制

教學 Q&A 可讓您修正兩種錯誤類型：

- 將文字指派給欄位。
- 為文字指派篩選條件。

目前不支援重新定義已辨識的字詞，或定義其他類型的條件或片語。 此外，定義篩選條件時只能使用有限的語言子集，包括：

- 國家/地區是美國
- 國家/地區不是美國
- 產品 > 100
- 產品大於 100
- 產品 = 100
- 產品等於 100
- 產品 < 100
- 產品小於 100

> [!NOTE]
> 問與答工具僅支援匯入模式。 目前尚不支援連接到內部部署或 Azure Analysis Services 資料來源。 Power BI 的後續版本中將會移除此目前限制。

### <a name="statements-not-supported"></a>不支援陳述式

- 目前不支援在條件中使用量值。 請改將量值轉換為計算結果欄，使其正常運作。
- 不支援多個條件。 因應措施是建立 DAX 計算結果欄以評估多個條件的陳述式布林值，並改用此欄位。
- 如果您未在問與答提示輸入資料子集時指定篩選條件，則無法儲存定義，即使整個陳述式沒有紅色底線也一樣。

## <a name="next-steps"></a>後續步驟

有一些最佳做法可以改善自然語言引擎。 如需詳細資訊，請參閱 [Q&A 最佳做法](q-and-a-best-practices.md)。