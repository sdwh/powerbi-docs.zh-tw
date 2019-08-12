---
title: 在 Power BI 報表產生器中規劃報表
description: Power BI 分頁報表產生器可讓您建立各式各樣的分頁報表。 若要建立有用且易於了解的報表，最好先進行規劃。
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 33cdb53ab411e0d2f4686f7cc9a41bb3f0fe4cb6
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68623859"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>在 Power BI 報表產生器中規劃報表

Power BI 分頁報表產生器可讓您建立各式各樣的分頁報表。 例如，您可以建立顯示摘要或詳細銷售資料、行銷和銷售趨勢、營運報表或儀表板的報表。 您也可以建立利用豐富格式化文字的報表，例如銷售訂單、產品目錄或套印信件。 所有報表都是在報表產生器中使用同一個基本建置組塊的不同組合所建立。 若要建立有用且易於了解的報表，最好先進行規劃。 以下是開始之前可能需要考量的一些事項：  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>您想要以何種格式來呈現報表？
  
您可以在瀏覽器 (例如 Power BI 入口網站) 中線上轉譯報表，或將其匯出為其他格式 (例如 Excel、Word 或 PDF)。 報表所採用最終格式是很重要的考量，因為並非所有功能都適用於所有匯出格式。 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>您想要以何種結構來呈現資料？
  
您可以選擇表格式、矩陣 (類似於交叉分析或樞紐分析表報表)、圖表、自由格式結構或這些格式的任意組合來呈現資料。 如需詳細資訊，請參閱 [Power BI 報表產生器中的資料表、矩陣和清單](report-builder-tables-matrices-lists.md)。  
  
## <a name="how-do-you-want-your-report-to-look"></a>您想要如何呈現報表？
  
報表產生器提供許多報表項目，可讓您新增至報表來使報表更容易閱讀、強調重要資訊、協助您的讀者巡覽報表等。 了解您想要如何呈現報表可確定您是否需要文字方塊、矩形、影像和線條等報表項目。 您也可能想要顯示或隱藏項目、新增文件引導模式、包含鑽研報表或子報表，或是連結至其他報表。   
  
## <a name="should-the-data-be-filtered"></a>應該篩選資料嗎？
  
您可能想要將報表範圍縮小到特定使用者或位置，或縮小到特定時段。 若要篩選報表資料，請使用參數只擷取和顯示您想要的資料。 如需詳細資訊，請參閱 [Power BI 報表產生器中的報表參數](paginated-reports-parameters.md)。  
  
## <a name="do-you-need-to-create-calculations"></a>您需要建立計算嗎？ 
  
有時候，您的資料來源和資料集不會包含報表所需確切欄位。 在這種情況下，您可能必須建立自己的計算欄位。 例如，您可能想要將每個單位的價格乘以數量，以獲得明細項目銷售量。 運算式也可用於提供條件式格式與其他進階功能。 如需詳細資訊，請參閱 [Power BI 報表產生器中的運算式](report-builder-expressions.md)。  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>您想要一開始就隱藏報表項目嗎？
  
請考慮您是否想要在報表第一次執行時隱藏報表項目，包括資料區域、群組和資料行。 例如，您可以一開始先呈現摘要資料表，然後向下切入到詳細資料。 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>您想要如何傳遞報表？  
  
您可以將報表儲存至本機電腦並繼續處理，也可以在本機執行以用於您自己的資訊。 不過，若要與其他人共用您的報表，您需要將報表儲存至 Power BI。 將其儲存至 Power BI，可讓其他人在需要時執行。 或者您也可以設定訂閱，並將報表透過電子郵件傳遞給其他人。 如果您想要的話，可以使用特定的匯出格式來傳遞報表。 
  
## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
