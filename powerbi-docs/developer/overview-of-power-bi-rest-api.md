---
title: Power BI API 可以做些什麼
description: Power BI API 可以做些什麼
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 3b19740616e7b9a390a883fde2fd96320de7b94a
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973578"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>開發人員可如何利用 Power BI API？

Power BI 顯示互動式儀表板，可即時從不同的資料來源建立及更新。 您可以使用任何支援 REST 呼叫的程式設計語言，建立即時整合 Power BI 儀表板的應用程式。 您也可以將 Power BI 磚和報告整合到應用程式中。

開發人員也可以建置自己專屬的資料視覺效果，並將其用於互動式報表及儀表板。

以下是一些您可以使用 Power BI API 進行的操作。

| **若要這樣做** | **請前往這裡** |
| --- | --- |
| 為 Power BI 使用者和非 Power BI 使用者 (應用程式擁有資料) 內嵌儀表板、報告及圖格 |[如何內嵌 Power BI 儀表板、報表和圖格](embedding-content.md) |
| 擴充現有商務工作流程，將關鍵資料推送至 Power BI 儀表板。 |[將資料推入儀表板中](walkthrough-push-data.md) |
| 向 Power BI 驗證。 |[向 Power BI 驗證](get-azuread-access-token.md) |
| 建立自訂視覺效果。 |[使用開發人員工具建立自訂視覺效果](../service-custom-visuals-getting-started-with-developer-tools.md) |

> [!NOTE]
> Power BI API 仍然將應用程式工作區稱為群組。 任何對群組的引述都表示您處理的是應用程式工作區。

## <a name="power-bi-developer-samples"></a>Power BI 開發人員範例

Power BI 開發人員範例包含用來內嵌儀表板、報告和圖格的項目。

[Power BI 開發人員範例](https://github.com/Microsoft/PowerBI-Developer-Samples)

* **應用程式擁有資料**內的範例適用於針對非 Power BI 使用者內嵌。
* **使用者擁有資料**內的範例適用於針對 Power BI 使用者內嵌。

## <a name="github-repositories"></a>GitHub 存放庫

* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)
* [自訂視覺效果](https://github.com/Microsoft/PowerBI-visuals)

## <a name="developer-tools"></a>開發人員工具

以下是可用來協助您開發 Power BI 項目的工具。

您可以完成[內嵌安裝工具](https://aka.ms/embedsetup)以快速開始使用並下載關於如何內嵌 Power BI 內容的應用程式範例。

選擇最適合您的方案：

* [對客戶進行內嵌](embedding.md#embedding-for-your-customers)，可讓您將儀表板和報告內嵌至沒有 Power BI 帳戶的使用者。 執行[對客戶進行內嵌](https://aka.ms/embedsetup/AppOwnsData)解決方案。

* [對組織進行內嵌](embedding.md#embedding-for-your-organization)可讓您擴充 Power BI 服務。 執行[對組織進行內嵌](https://aka.ms/embedsetup/UserOwnsData)解決方案。

如需使用 JavaScript API 的完整範例，您可以使用[測試網工具](https://microsoft.github.io/PowerBI-JavaScript/demo)。 此工具是一個可測試不同類型 Power BI Embedded 範例的快速方式。 您也可瀏覽 [PowerBI-JavaScript Wiki](https://github.com/Microsoft/powerbi-javascript/wiki) 頁面，取得有關 JavaScript API 的詳細資訊。

## <a name="push-data-into-power-bi"></a>將資料推送至 Power BI

您可以使用 Power BI API 以將資料推送至資料集。 此功能可讓您將資料列新增至資料集內的資料表。 新資料接著會反映在儀表板的磚中，以及報表的視覺效果內。

![推送資料範例](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>後續步驟

[將資料推送至資料集](walkthrough-push-data.md)  
[開始使用自訂視覺效果開發人員工具](../service-custom-visuals-getting-started-with-developer-tools.md)  
[Power BI REST API 參考](https://docs.microsoft.com/rest/api/power-bi/)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
