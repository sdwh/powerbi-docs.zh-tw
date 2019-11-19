---
title: Power BI 問與答的限制
description: Power BI 問與答的目前限制
author: mohaali
manager: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: fc4a605f1258bcd93e0b49b596cc3a1691ce2edb
ms.sourcegitcommit: 26123c6bb24c8174beb390f4e06fb938d31238ea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72717931"
---
# <a name="limitations-of-power-bi-qa"></a>Power BI 問與答的限制

Power BI 問與答目前有一些限制。

## <a name="data-sources"></a>資料來源

### <a name="supported-data-sources"></a>支援的資料來源

Power BI 問與答支援 Power BI 服務中的下列資料來源設定：

- 匯入模式
- 即時連接到 Azure Analysis Services
- 即時連接到 SQL Server Analysis Services (使用閘道)
- Power BI 資料集。 使用 Power BI 資料集時，Power BI Desktop 會以問與答回報錯誤。 不過，當您將報表發佈至 Power BI 服務時，錯誤會消失。

在上述每項設定中，也支援資料列層級安全性。

### <a name="data-sources-not-supported"></a>不支援的資料來源

Power BI 問與答目前不支援下列設定：

- 任何資料來源類型的物件層級安全性
- 對任何來源進行 DirectQuery。 支援此設定的因應措施是對 Azure Analysis Services 使用即時連接，這會使用 DirectQuery。
- 複合模型
- Reporting Services 

## <a name="tooling-limitations"></a>工具限制

新工具對話方塊可讓使用者自訂和改善問與答中的自然語言。 若要深入了解工具，請參閱[問與答工具簡介](q-and-a-tooling-intro.md)。

## <a name="review-question-limitations"></a>檢閱問題限制

檢閱問題最多只會將針對資料模型所詢問的問題儲存 28 天。 使用新的檢閱問題功能時，您可能注意到不會記錄某些問題。 這是依據設計，因為自然語言引擎會執行一連串的資料清理步驟，以確保不會記錄或顯示使用者的每個按鍵輸入。

租用戶系統管理員可以使用租用戶系統管理員設定來管理儲存問題的能力。 權限是以安全性群組為基礎。 

使用者也可以選取 [設定]   > [一般]  ，然後取消選取 [Allow Q&A to record my utterance] \(允許問與答記錄我的表達\)  來避免記錄其問題。 

## <a name="teach-qa-limitations"></a>教學 Q&A 限制

教學 Q&A 可讓您修正兩種錯誤類型：

- 將文字指派給欄位。
- 為文字指派篩選條件。

目前不支援重新定義已辨識的字詞，或定義其他類型的條件或片語。 此外，定義篩選條件時只能使用有限的語言子集，包括：

- 「國家/地區」是「美國」
- 「國家/地區」不是「美國」
- 「重量」> 2000
- 「重量」= 2000
- 「重量」< 2000

> [!NOTE]
> 問與答工具僅支援匯入模式。 目前尚不支援連接到內部部署或 Azure Analysis Services 資料來源。 Power BI 的後續版本中將會移除此目前限制。

### <a name="statements-not-supported"></a>不支援陳述式

- 目前不支援在條件中使用量值。 請改將量值轉換為計算結果欄，使其正常運作。
- 不支援多個條件。 因應措施是建立 DAX 計算結果欄以評估多個條件的陳述式布林值，並改用此欄位。
- 如果您未在問與答提示輸入資料子集時指定篩選條件，則無法儲存定義，即使整個陳述式沒有紅色底線也一樣。
