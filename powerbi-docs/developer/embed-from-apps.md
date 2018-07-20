---
title: 從應用程式內嵌報表或儀表板
description: 了解如何從 Power BI 應用程式，而不是從應用程式工作區，整合或內嵌報表或儀表板。
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 2817ccb25fc9aa6d3e8150c776558366dcf0ccb6
ms.sourcegitcommit: 0c870a006e525447497e678484874a2f137b9abd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088831"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>從應用程式內嵌報表或儀表板

在 **Power BI** 中，您可以建立應用程式，以將相關的**儀表板**和**報表**一起帶到同一處，然後發佈給組織中一大群人。 當所有使用者皆為 Power BI 使用者時，使用這些應用程式會彼此相關，所以您可以使用 Power BI 應用程式與這些使用者共用內容。 我們打算提供一些快速步驟，讓您了解如何將內容從發佈的 Power BI 應用程式內嵌至協力廠商應用程式。

## <a name="how-to-grab-report-embed-url-for-embedding"></a>如何擷取用於內嵌的報表內嵌 URL

1. 與自己共用或引導其他使用者進行此流程，以在使用者工作區 (「我的工作區」) 中將應用程式具現化。

2. 在 Power BI 服務中開啟所需報表。

3. 前往 [檔案] -> [內嵌在 SharePoint Online 中]，並從該處擷取報表內嵌 URL (顯示於下面的快照中) 或呼叫 GetReports/GetReport REST API，並從回應擷取對應的報表 embedURL 欄位 (請注意，應用程式在使用者的工作區中具現化時，REST 呼叫的 URL 中不應有工作區識別碼)。

4. 以在步驟 3 中擷取的內嵌 URL 搭配 JS SDK 使用。

    ![從應用程式內嵌](media/embed-from-apps/embed-from-app.png)

## <a name="how-to-grab-dashboard-embed-url-for-embedding"></a>如何擷取用於內嵌的儀表板內嵌 URL

1. 與自己共用或引導其他使用者進行此流程，以在使用者工作區 (「我的工作區」) 中將應用程式具現化。

2. 呼叫 GetDashboards REST API，並從回應擷取對應的儀表板 embedURL 欄位 (請注意，應用程式在使用者的工作區中具現化時，REST 呼叫的 URL 中不應有工作區識別碼)。

3. 以在步驟 4 中擷取的內嵌 URL 搭配 JS SDK 使用。

## <a name="next-steps"></a>後續步驟

另外也檢閱如何從應用程式工作區為協力廠商客戶和組織內嵌。

> [!div class="nextstepaction"]
>[為協力廠商客戶內嵌](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[為組織內嵌](embed-sample-for-your-organization.md)