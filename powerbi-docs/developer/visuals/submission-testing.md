---
title: Power BI 視覺效果的提交測試
description: 此文章描述您的視覺效果在發佈至 AppSource 之前必須通過的測試案例。 也有選擇性測試案例。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 65e00fa5311ea12c9fe0011c6aa7c3e779f33dc5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131127"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Power BI 視覺效果的提交測試

在您將視覺效果發佈至 [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) 之前，其必須先通過這些測試案例。 請先測試您的視覺效果再提交。 如果您的視覺效果未通過必要的測試案例，則會予以拒絕。

如需發佈程序的詳細資訊，請參閱[將 Power BI 視覺效果發佈至合作夥伴中心](./office-store.md)。

## <a name="general-test-cases"></a>一般測試案例

| 測試案例 | 預期的結果
| --------- | ----------------
| 使用 [類別] 與 [值] 建立**堆疊直條圖**。 將其轉換成您的視覺效果，然後轉換回直條圖。 | 進行這些轉換之後沒有出現錯誤。 |
| 使用三個量值建立**量測計**。 將其轉換成您的視覺效果，然後轉換回**量測計**。 | 進行這些轉換之後沒有出現錯誤。 |
| 在您的視覺效果中進行選取。 | 其他視覺效果會反映選取。 |
| 在其他視覺效果中選取元素。 | 您的視覺效果會根據其他視覺效果中的選取來顯示已篩選的資料。 |
| 檢查最小值/最大值 **dataViewMapping** 條件。 | 欄位貯體可以接受多個欄位、單一欄位，或由其他貯體決定。 最小值/最大值 **dataViewMapping** 條件必須在您視覺效果的功能中正確設定。 |
| 以不同順序移除所有欄位。 | 以任意順序移除欄位時，視覺效果會適當地加以清除。 主控台或瀏覽器中沒有錯誤。 |
| 使用每個可能的貯體設定來開啟 [格式] 窗格。 | 此測試不會觸發 Null 參考例外狀況。 |
| 使用 [篩選] 窗格在視覺效果、頁面與報表層級篩選資料。 | 套用篩選之後，工具提示是正確的。 工具提示顯示已篩選的值。 |
| 使用 [交叉分析篩選器] 篩選資料。 | 套用篩選之後，工具提示是正確的。 工具提示顯示已篩選的值。 |
| 使用已發佈的視覺效果篩選資料。 例如，選取圓形圖塊量或直條。 | 套用篩選之後，工具提示是正確的。 工具提示顯示已篩選的值。 |
| 如果支援交叉篩選，請確認篩選會正常地運作。 | 已套用的選取會篩選報表此頁面上的其他視覺效果。 |
| 使用 Ctrl、Alt 與 Shift 鍵來選取。 | 沒有出現未預期的行為。 |
| 將 [檢視模式] 變更為 [實際大小]、[符合一頁大小] 與 [符合寬度]。 | 滑鼠座標是正確的。 |
| 調整您的視覺效果大小。 | 視覺效果會正確地回應大小調整。 |
| 將報表大小設定為最小值。 | 沒有顯示錯誤。 |
| 確定捲軸正常運作。 | 如有需要，捲軸應該存在。 檢查捲軸大小。 捲軸不應太寬或太高。 捲軸的位置與大小必須符合您視覺效果的其他元素。 確認視覺效果的不同大小都需要捲軸。 |
| 將您的視覺效果釘選到 [儀表板]。 | 視覺效果應該正確地顯示。 |
| 將您視覺效果的多個版本新增至單一報表頁面。 | 視覺效果的所有版本都已顯示並正常地運作。 |
| 將您視覺效果的多個版本新增至多個報表頁面。 | 視覺效果的所有版本都已顯示並正常地運作。 |
| 在報表頁面之間切換。 | 視覺效果正確地顯示。 |
| 測試您視覺效果的 [閱讀檢視] 與 [編輯檢視]。 | 所有功能都正常地運作。 |
| 如果您的視覺效果使用動畫，請新增、變更及刪除您視覺效果的元素。 | 視覺效果元素的動畫正確地運作。 |
| 開啟 [屬性] 窗格。 開啟並關閉屬性、輸入自訂文字、強調選項可用，以及輸入不正確的資料。 | 視覺效果正確地回應。 |
| 儲存報表並重新開啟。 | 所有屬性設定都會保存。 |
| 在報表中切換頁面，然後切換回原頁面。 | 所有屬性設定都會保存。 |
| 測試您視覺效果的所有功能，包括視覺效果提供的不同選項。 | 所有顯示和功能都能正常地運作。 |
| 測試所有數值、日期和字元資料類型，如下列測試所示。 | 所有資料的格式都正確。 |
| 檢閱工具提示值、軸標籤、資料標籤，以及其他視覺效果元素 (有格式) 的格式。 | 所有元素的格式都正確。 |
| 確認資料標籤使用格式字串。 | 所有資料標籤的格式都正確。 |
| 針對工具提示中的數值開啟並關閉自動格式設定。 | 工具提示正確地顯示值。 |
| 測試來自模型包含不同資料類型的資料項目，包括數值、文字、日期時間，以及不同格式字串。 測試不同的資料量，例如數千個資料列、一個資料列與兩個資料列。 | 所有顯示和功能都能正常地運作。 |
| 將不正確的資料提供給您的視覺效果，例如 Null、無限大、負值與錯誤的值類型。 | 所有顯示和功能都能正常地運作。 |

## <a name="optional-browser-testing"></a>選擇性瀏覽器測試

AppSource 小組會在最新的 Windows 版 Google Chrome、Microsoft Edge 與 Mozilla Firefox 瀏覽器上驗證視覺效果。
您可以選擇在下列瀏覽器中測試您的視覺效果。

| 測試案例 | 預期的結果
| --------- | ----------------
| **Windows** |
| Google Chrome (前一版) | 所有顯示和功能都能正常地運作。 |
| Mozilla Firefox (前一版) | 所有顯示和功能都能正常地運作。 |
| Microsoft Edge (前一版) | 所有顯示和功能都能正常地運作。 |
| Microsoft Internet Explorer 11 (選擇性) | 所有顯示和功能都能正常地運作。 |
| **macOS** |
| Chrome (前一版) | 所有顯示和功能都能正常地運作。 |
| Firefox (前一版) | 所有顯示和功能都能正常地運作。 |
| Safari (前一版) | 所有顯示和功能都能正常地運作。 |
| **Linux** |
| Firefox (前一版和最新版) | 所有顯示和功能都能正常地運作。 |
| **行動裝置 iOS** |
| Apple Safari iPad (前一版 Safari) | 所有顯示和功能都能正常地運作。 |
| Chrome iPad (最新版 Safari) | 所有顯示和功能都能正常地運作。 |
| **行動裝置 Android** |
| Chrome (前一版和最新版) | 所有顯示和功能都能正常地運作。 |

## <a name="desktop-testing"></a>電腦測試

在最新版本的 [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) 中，測試您的視覺效果。

| 測試案例 | 預期的結果
| --------- | ----------------
| 測試您視覺效果的所有功能。 | 所有顯示和功能都能正常地運作。 |
| 透過使用 Power BI Desktop 中的 [發佈] 按鈕，來匯入、儲存、開啟檔案，以及發佈至 Power BI web 服務。 | 所有顯示和功能都能正常地運作。 |
| 透過增加或減少精確度，將數值格式字串變更為有零個小數位數或三個小數位數。 | 視覺效果正確地顯示。 |

## <a name="performance-testing"></a>效能測試

您的視覺效果應該在可接受的層級執行。 使用開發人員工具來驗證效能。 不要依賴視覺提示與主控台時間記錄。

| 測試案例 | 預期的結果
| --------- | ----------------
| 建立包含許多視覺效果元素的視覺效果。 | 視覺效果應該會正常執行，而且不會使應用程式凍結。 不應該有元素相關的效能問題，像是動畫速度、大小調整、篩選及選取。

## <a name="next-steps"></a>後續步驟

如需發佈程序的詳細資訊，請參閱[將 Power BI 視覺效果發佈至合作夥伴中心](./office-store.md)。

有其他問題嗎？ [詢問 Power BI 社群](https://community.powerbi.com/) \(英文\)。
