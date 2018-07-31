---
title: 開發人員可如何利用 Power BI？
description: Power BI 提供各種開發人員選項。 範圍包括內嵌、自訂視覺效果和串流資料集。
author: markingmyname
ms.author: maghan
ms.date: 05/25/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 07fb8d365a6fe4a874b057a71a90a99fc8a9e5fa
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34564688"
---
# <a name="what-can-developers-do-with-power-bi"></a>開發人員可如何利用 Power BI？

開發人員有各種不同選項可嘗試將 Power BI 內容包含在應用程式中。 這些選項包括**使用 Power BI 進行內嵌**、**自訂視覺效果**，以及**將資料推送至 Power BI**。

## <a name="embedding"></a>內嵌
Power BI 服務 (SaaS) 和 Azure 中的 Power BI Embedded 服務 (PaaS) 都有 API 可供內嵌您的儀表板和報表。 這意謂著在內嵌內容時，您會有一組功能可供使用，並可存取最新的 Power BI 功能，例如儀表板、閘道及應用程式工作區。

您可以完成[上線體驗工具](https://aka.ms/embedsetup)以快速開始使用並下載應用程式範例。

選擇最適合您的方案：
* [對客戶進行內嵌](embedding.md#embedding-for-your-customers)，可讓您將儀表板和報告內嵌至沒有 Power BI 帳戶的使用者。 執行[對客戶進行內嵌](https://aka.ms/embedsetup/AppOwnsData)解決方案。
* [對組織進行內嵌](embedding.md#embedding-for-your-organization)可讓您擴充 Power BI 服務。 執行[對組織進行內嵌](https://aka.ms/embedsetup/UserOwnsData)解決方案。

![PBIE 範例](media/what-can-you-do/what-can-you-do-02.png)

## <a name="develop-custom-visuals"></a>開發自訂視覺效果
自訂視覺效果可讓您建立專屬視覺效果，以用於 Power BI 報表內。 自訂視覺效果會以 TypeScript 撰寫，這是 JavaScript 的超集。 TypeScript 支援一些進階功能，並可優先存取 ES6/ES7 功能。 系統會使用階層式樣式表 (css) 來處理視覺效果樣式。 為了您的方便，我們會使用可支援一些進階功能 (例如巢狀結構、變數、條件、迴圈等) 的 Less 預先編譯器。如果您不想使用上述任何功能，只需在 Less 檔案中撰寫一般 CSS 即可。

![CV 範例](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>將資料推送至 Power BI
您可以使用 Power BI API 以將資料推送至資料集。 這可讓您將資料列新增至資料集內的資料表。 新資料接著會反映在儀表板的磚中，以及報表的視覺效果內。

![推送資料範例](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>後續步驟
[內嵌在 Power BI 之中](embedding.md)  
[將自訂視覺效果發佈至 Office 市集](office-store.md)  
[將資料推入儀表板中](walkthrough-push-data.md)
