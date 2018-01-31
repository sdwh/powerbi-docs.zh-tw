---
title: "開發人員可如何利用 Power BI？"
description: "Power BI 提供各種開發人員選項。 範圍包括內嵌、自訂視覺效果和串流資料集。"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 07/20/2017
ms.author: maghan
ms.openlocfilehash: b310562ac31694f398a659018743b8fa7aa46e35
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2018
---
# <a name="what-can-developers-do-with-power-bi"></a>開發人員可如何利用 Power BI？
Power BI 提供各種開發人員選項。 範圍包括內嵌、自訂視覺效果和串流資料集。

## <a name="embedding"></a>內嵌
Azure 中的 Power BI 服務和 Power BI Embedded 合併使用，以提供單一 API 來內嵌儀表板和報表。 這表示，在內嵌內容時，您會有一個 API 介面、一組一致的功能以及最新 Power BI 功能的存取權 (例如儀表板、閘道和應用程式工作區)。 如需詳細資訊，請參閱[內嵌在 Power BI 之中](embedding.md)。

![](media/what-can-you-do/powerbi-embed-sample.png)

## <a name="custom-visuals"></a>自訂視覺效果
自訂視覺效果可讓您建立專屬視覺效果，以用於 Power BI 報表內。 自訂視覺效果是以 TypeScript 來撰寫，其為 JavaScript 的超集合並支援一些進階功能且可優先存取 ES6/ES7 功能。 系統會使用階層式樣式表 (css) 來處理視覺效果樣式。 為了方便使用，我們會使用可支援一些進階功能 (例如巢狀結構、變數、mixin、條件、迴圈等等) 的 Less 預先編譯器。如果您不想使用上述任何功能，只需在 Less 檔案中撰寫一般 CSS 即可。

如需如何開發並發佈自訂視覺效果的詳細資訊，請參閱[將自訂視覺效果發佈至 Office 市集](office-store.md)。

![](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>將資料推送至 Power BI
您可以使用 Power BI API 以將資料推送至資料集。 這可讓您將資料列新增至資料集內的資料表。 新資料接著會反映在儀表板的磚中，以及報表的視覺效果內。

如需詳細資訊，請參閱[將資料推送至儀表板](walkthrough-push-data.md)。

## <a name="next-steps"></a>後續步驟
[內嵌在 Power BI 之中](embedding.md)  
[如何將 Power BI Embedded 工作區集合內容移轉至 Power BI](migrate-from-powerbi-embedded.md)  
[JavaScript API Git 存放庫](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git 存放庫](https://github.com/Microsoft/PowerBI-CSharp)  
[將自訂視覺效果發佈至 Office 市集](office-store.md)  
[Power BI Visuals Git 存放庫](https://github.com/Microsoft/PowerBI-visuals)  
[JavaScript 內嵌示範](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Power BI Premium 技術白皮書](https://aka.ms/pbipremiumwhitepaper)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

