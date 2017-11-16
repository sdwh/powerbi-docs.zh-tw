---
title: "在 Power BI Desktop 中合併二進位檔案"
description: "在 Power BI Desktop 中輕鬆合併二進位資料來源"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 0909056569bb353a720ddd4e8563a37542b90cca
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="combine-binaries-in-power-bi-desktop"></a>在 Power BI Desktop 中合併二進位檔案
將多個具有相同結構描述的檔案合併成單一邏輯資料表，是一種將資料匯入 **Power BI Desktop** 中的強大方法。 這個便利又熱門的方法在 **Power BI Desktop** 的 2016 年 11 月版本 (及後續版本) 中獲得了便利性及擴充能力的提升，如本文所述。

若要啟動合併同一個資料夾中二進位檔的處理序，請選取 [取得資料] > [檔案] > [資料夾]。

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-binaries-behavior"></a>先前的合併二進位檔案行為
在 **Power BI Desktop** 的 2016 年 11 月版本之前，您可以用 [合併二進位檔案] 轉換來合併特定檔案類型，但有幾項限制：

* 在檔案合併成單一資料表之前，並不是每一個個別檔案都會轉換。 因此，您通常需要合併檔案，然後在編輯程序中篩選資料列，以篩選出「標頭值」。
* [合併二進位檔案] 轉換僅適用於「文字」或 *CSV* 檔案，而不適用於其他支援的檔案格式，例如 Excel 活頁簿、JSON 檔案等。

客戶要求更直覺式的 [合併二進位檔案] 作業，因此我們加強了轉換功能。

## <a name="current-combine-binaries-behavior"></a>目前的合併二進位檔案行為
**Power BI Desktop** 現在能夠更有效率地處理 [合併二進位檔案]。 您可以從 [查詢編輯器] 中的 [首頁] 功能區索引標籤或資料行本身選取 [合併二進位檔案]。

![](media/desktop-combine-binaries/combine-binaries_2a.png)

[合併二進位檔案] 轉換現在的行為如下：

* [合併二進位檔案] 轉換會分析每個輸入檔案，並判斷要使用的正確檔案格式，例如「文字」或「Excel 活頁簿」或 *JSON* 檔案。
* 轉換可讓您從第一個檔案 (例如「Excel 活頁簿」) 選取要擷取的特定物件。
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* [合併二進位檔案] 接著會自動執行下列動作：
  
  * 建立在單一檔案中執行所有必要擷取步驟的範例查詢。
  * 建立「函數查詢」，以將檔案/二進位檔案輸入參數化成「範例查詢」。 範例查詢和函數查詢會建立連結，因此範例查詢的變更會反映在函數查詢中。
  * 將「函數查詢」套用到具有輸入二進位檔案 (例如「資料夾」) 的原始查詢，使其在每個資料列上對二進位檔案輸入套用函數查詢，然後將產出的資料擷取展開為頂層資料行。
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

透過 [合併二進位檔案] 的新行為，只要二進位檔案的檔案類型和結構相同 (例如相同的資料行)，您就可以輕鬆將其全部合併到指定的資料夾中。

此外，您可以藉由修改自動建立的「範例查詢」輕鬆套用額外轉換或擷取步驟，而不需要花費心力修改或建立額外「函數查詢」步驟；對「範例查詢」進行的任何變更都會在已連結的「函數查詢」中自動產生。

## <a name="next-steps"></a>後續步驟
您可以使用 Power BI Desktop 連接至各式各樣的資料。 如需有關資料來源的詳細資訊，請參閱下列資源︰

* [開始使用 Power BI Desktop](desktop-getting-started.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [連接至 Power BI Desktop 中的 CSV 檔案](desktop-connect-csv.md)   
* [直接將資料輸入 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   

