---
title: Power BI Embedded 效能最佳做法
description: 本文提供內嵌式分析最佳做法的指引
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: d0f4ca29e30e5f6e6176f036dc535601eb580471
ms.sourcegitcommit: 298db44200b78b1281b3ae6dfe7cce7a89865ec9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2018
ms.locfileid: "53329870"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Power BI Embedded 效能最佳做法

本文提供能更快速轉譯應用程式中的報表、儀表板及磚的建議

## <a name="embed-parameters"></a>內嵌參數

Powerbi.embed() 方法可接收用來內嵌報表、儀表板或磚的幾個參數。 這些參數會影響效能。

### <a name="embed-url"></a>內嵌 URL

請避免自行產生內嵌 URL。 反之，請務必透過呼叫[取得報表](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Freports%2Fgetreportsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=22lkqRM2w1MQfrM8dooedaPqqIU8PufTq9TT4VDzRo0%3D&reserved=0)、[取得儀表板](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgetdashboardsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=nfWRgbSoXVF42Rg%2Ba9491u19uksXp%2FAyz%2Fa%2Ba7%2FCtdA%3D&reserved=0)，或[取得磚](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgettilesingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256178318&sdata=LgZ27TynNpqQJDrb3aHWGQXIS%2FzichAO9De5M2uhF1Q%3D&reserved=0) API 來取得內嵌 URL。 我們已將名稱為 **_config_** 的新參數新增至 URL，可用來提升效能。

### <a name="permissions"></a>權限

如果您不想在**編輯模式**中內嵌報表，請提供**檢視**權限。 如此一來，內嵌程式碼就不會初始化用於編輯模式的元件。

### <a name="filters-bookmarks-and-slicers"></a>篩選條件、書籤和交叉分析篩選器

通常，報表視覺效果會與快取資料一起儲存。 快取資料可用來提供有感效能。 報表會在執行查詢時轉譯快取的資料。 如果其中提供篩選條件、書籤或交叉分析篩選器，快取資料就會有不相關的情況。 這樣一來，系統就只會在執行視覺化查詢之後才轉譯視覺效果。

如果您在報表中內嵌相同的篩選條件，為了避免將篩選條件清單傳遞至載入設定，請儲存已套用至報表的篩選條件。

## <a name="preload"></a>預先載入

使用 *preload* JavaScript API，以提升終端使用者效能。
Powerbi.preload() 可下載 javascript、css 檔案和其他成品，以便稍後用於報表內嵌。

如果您不需立即內嵌至報表，請呼叫 preload。 比方說，如果您要在按下按鈕時內嵌報表，最好在載入上一個頁面時呼叫 preload。 這樣一來，當應用程式使用者按一下按鈕時，就能更快速轉譯。

## <a name="measure-performance"></a>測量效能

若要測量效能，請使用：

1. 載入：初始化報表所需的時間 (使用者不會察覺到干擾)。
2. 轉譯：使用實際資料轉譯報表所需的時間。 每次重新轉譯報表時 (也就是套用篩選條件之後)，都會引發轉譯事件。 若要先測量報表，請務必在第一個引發的事件中執行計算。

快取資料會在可用時轉譯，但我們目前尚無這項資料的事件。

## <a name="update-tools-and-sdk-packages"></a>更新工具和 SDK 套件

保持工具和 SDK 套件的最新狀態。

* 請一律使用最新版本的 [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/)。

* 安裝最新版本的 [Power BI 用戶端 SDK](https://github.com/Microsoft/PowerBI-JavaScript)。 我們持續發行更多增強功能，因此請務必隨時掌握最新狀態。

* 要安裝的套件：
    * Npm 套件：powerbi-client
    * NuGet 套件：Microsoft.PowerBI.JavaScript

> [!Note]
> 請注意，載入時間主要取決於報表和資料本身的相關項目。 例如視覺效果的數量、資料大小，以及查詢和導出量值的複雜度。 請遵循[最佳做法](../power-bi-reports-performance.md)，以改善報表的載入時間。

## <a name="next-steps"></a>後續步驟

* [報表效能](../power-bi-reports-performance.md)
* [如何針對 Power BI Embedded 的問題進行疑難排解](embedded-troubleshoot.md)
* [Power BI Embedded 常見問題集](embedded-faq.md)
