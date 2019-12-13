---
title: Power BI 視覺效果概念
description: 本文描述視覺效果如何與 Power BI 整合
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700838"
---
# <a name="power-bi-visual-concept"></a>Power BI 視覺效果概念

本文說明使用者和視覺效果如何與 Power BI 互動，而使用者又如何與 Power BI 視覺效果互動。 在圖表中，您會看到哪些動作直接影響視覺效果，或透過 Power BI (例如使用者選取書籤) 影響。

![Power BI 視覺效果](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>視覺效果從 Power BI 取得更新

視覺效果具有 `update` 方法，而此方法通常會包含視覺效果的主要邏輯，並負責轉譯圖表或將資料視覺化。

呼叫 `update` 方法會取得大多數更新。

### <a name="user-interacts-with-visual-through-power-bi"></a>使用者透過 Power BI 與視覺效果互動

* 使用者開啟視覺屬性面板。

    Power BI 會從視覺效果的 `capabilities.json` 擷取支援的物件和屬性；若要接收屬性的實際值，Power BI 會呼叫視覺效果的 `enumerateObjectInstances` 方法。

    視覺效果必須傳回屬性的實際值。

    如需詳細資訊，[請參閱視覺效果的功能](capabilities.md)。

* [使用者在格式面板中變更視覺效果的屬性](../../visuals/power-bi-visualization-customize-title-background-and-legend.md)。

    變更屬性值之後，Power BI 會呼叫視覺效果的 `update` 方法，並將新的 `options` 與物件的新值一併傳入 update 方法中。

    如需詳細資訊，[請參閱視覺效果的物件和屬性](objects-properties.md)。

* 使用者調整視覺效果的大小。

    當使用者變更視覺效果的大小時，Power BI 會使用新的 `option` 物件來呼叫 `update` 方法。 選項具有使用視覺效果新寬度和高度的巢狀 `viewport` 物件。

* 使用者套用報表、頁面或視覺效果層級篩選。

    Power BI 會根據篩選條件來篩選資料，並呼叫視覺效果的 `update` 方法，將新的資料提供給視覺效果。

    視覺效果會使用其中一個巢狀物件中的新資料來取得 `options` 的新更新。 這取決於視覺效果的資料檢視對應設定。

    如需詳細資訊，[請參閱資料檢視對應](dataview-mappings.md)。

* 使用者在報表的另一個視覺效果中選取資料點。

    Power BI 會篩選或醒目提示選取的資料點，並呼叫視覺效果的 `update` 方法。

    視覺效果會取得新的篩選資料，或具有醒目提示陣列的相同資料。

    如需詳細資訊，[請參閱如何在視覺效果中醒目提示資料點](highlight.md)。

* 使用者在報表的書籤面板上選取書籤。

    可能會發生兩個動作：

    1. Power BI 會呼叫透過 `registerOnSelectionCallback` 方法註冊的已傳遞函式，而回呼函數會取得對應書籤的選取項目陣列。

    2. Power BI 會使用 `options` 內的對應篩選物件來呼叫 `update` 方法。

    在這兩種情況下，視覺效果都必須根據收到的選取項目或篩選物件來變更視覺效果狀態。

    如需書籤的詳細資訊，[請參閱如何處理書籤](filter-api.md)。

    如需篩選的詳細資訊，[請參閱 Power BI 視覺效果如何篩選其他視覺效果中的資料](filter-api.md)。

### <a name="user-interacts-with-visual-directly"></a>使用者直接與視覺效果互動

* 使用者將滑鼠停留在資料元素上

    視覺效果可以透過 Power BI 工具提示 API 顯示資料點的其他資訊。
    使用者將滑鼠停留在視覺元素上：視覺效果可以處理事件，並顯示工具提示元素的相關資料。

    視覺效果可以顯示標準工具提示或報表頁面工具提示。

    如需詳細資訊，請參閱[如何新增工具提示](add-tooltips.md)指南。

* 使用者變更視覺屬性 (例如，使用者展開樹狀結構，而視覺效果會在屬性中儲存狀態)

    視覺效果可以透過 Power BI API 儲存屬性值。 例如，當使用者與視覺效果互動時。 而視覺效果必須儲存或更新屬性值。 視覺效果可以呼叫 `presistProperties` 方法來完成。

* 使用者按一下 URL 連結。

    根據預設，視覺效果無法開啟 URL。 若要在新的索引標籤中開啟 URL，則視覺效果應呼叫 `launchURL` 方法，並傳遞 URL 作為參數。

    如需詳細資訊，請參閱[啟動 URL API](launch-url.md)。

* 使用者透過視覺效果套用篩選

    視覺效果呼叫 `applyJSONFilter` 並傳遞篩選條件，以篩選其他視覺效果中的篩選資料。

    視覺效果可以使用數種類型的篩選，例如基本篩選、進階篩選、Tuple 篩選。

    如需篩選的詳細資訊，[請參閱 Power BI 視覺效果如何篩選其他視覺效果中的資料](filter-api.md)。

* 使用者按一下/選取視覺效果上的元素。

    如需選取項目的詳細資訊，[請參閱視覺效果如何互動](selection-api.md)。

### <a name="the-visual-interacts-with-power-bi"></a>視覺效果與 Power BI 互動

* 視覺效果向 Power BI 要求更多資料。

    視覺效果可以逐項處理資料。 FetchMoreData API 方法會要求資料集的下一個片段。

    如需 `fetchMoreData` 的詳細資訊，[請參閱如何從 Power BI 擷取更多資料](fetch-more-data.md)

* 事件服務

    Power BI 可以將報表匯出至 PDF，或透過電子郵件傳送 (僅支援認證的視覺效果)。 為了通知 Power BI 轉譯已完成並準備擷取 PDF/電子郵件，視覺效果應呼叫轉譯事件 API。

    如需詳細資訊，[請參閱從 Power BI 將報表匯出至 PDF](../../consumer/end-user-pdf.md)

    深入了解[事件服務](event-service.md)

## <a name="next-steps"></a>後續步驟

您是否為 Web 開發人員，而且有興趣將自己建立的視覺效果發佈到 AppSource 呢？ 請參閱[開發 Power BI 視覺效果](./custom-visual-develop-tutorial.md)，並了解如何[將 Power BI 視覺效果發佈至 AppSource](../office-store.md)。
