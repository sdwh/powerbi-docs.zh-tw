---
title: 在安全入口網站或網站中內嵌報告
description: Power BI 內嵌功能可讓使用者輕鬆並安全地在內部網路入口網站中內嵌報表。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222248"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>在安全入口網站或網站中內嵌報告

與新**內嵌**選項適用於 Power BI 報表，您可以輕鬆且安全地將報表內嵌在內部網路入口網站中。 可以是這些入口網站**雲端**或**裝載於內部**，例如 SharePoint 2019。 內嵌的報表採用所有項目權限和資料安全性透過[資料列層級安全性 (RLS)](service-admin-rls.md)。 它們提供無程式碼將內嵌至任何接受 URL 或 iFrame 的入口網站。 

**內嵌**選項支援[URL 篩選](service-url-filters.md)和 URL 設定。 它可讓您使用入口網站使用低階程式碼方法需要基本的 HTML 和 JavaScript 知識整合。

## <a name="how-to-embed-power-bi-reports-into-portals"></a>如何將 Power BI 報告**內嵌**到入口網站

1. 您可以在 Power BI 服務之報告中的 [檔案]  功能表找到新的 [內嵌]  選項。

    ![[安全內嵌] 選項下拉式選項](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. 選取 **內嵌**選項來開啟一個對話方塊，提供的連結和可用來安全地將報告內嵌在 iFrame。

    ![[內嵌] 選項對話方塊](media/service-embed-secure/secure-embed-code-dialog.png)

3. 無論使用者開啟報表 URL 直接，或其中一個內嵌在 web 入口網站中，報表存取需要驗證。 如果使用者已無法登入至 Power BI 在其瀏覽器工作階段中，就會出現下列畫面。 當選取**登入**，無法開啟新的瀏覽器視窗或索引標籤。 可將這些檢查的快顯封鎖程式，如果它們不提示登入。

    ![登入以檢視此報告](media/service-embed-secure/secure-embed-sign-in.png)

4. 使用者已登入之後，報表會開啟，顯示的資料，並讓頁面導覽和篩選設定。 只有擁有檢視權限的使用者可以看到 Power BI 中的報表。 所有[資料列層級安全性 (RLS)](service-admin-rls.md)也會套用規則。 最後，使用者必須正確地取得授權：他們需要 Power BI Pro 授權，或報告必須位於 Power BI Premium 容量的工作區中。 使用者需要登入每次開啟新的瀏覽器視窗。 不過，登入之後，其他報表自動載入。

    ![內嵌報告](media/service-embed-secure/secure-embed-report.png)

5. 當使用 iFrame，您可能需要編輯**高度**並**寬度**，讓它符合您的入口網站網頁中。

    ![設定高度與寬度](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>報表存取權授與

**內嵌**選項不會自動允許使用者檢視報表。 在 Power BI 服務中設定檢視權限。

在 Power BI 服務中，您可以與需要存取的使用者共用內嵌的報表。 如果您使用 Office 365 群組，您可以將使用者列為應用程式工作區成員。 如需詳細資訊，請參閱如何[管理您的應用程式工作區，Power BI 和 Office 365 中](service-manage-app-workspace-in-power-bi-and-office-365.md)。

## <a name="licensing"></a>授權

若要檢視內嵌的報表，使用者需要 Power BI Pro 授權或內容必須位於工作區中處於[（EM 或 P SKU） 的 Power BI Premium 容量](service-admin-premium-purchase.md)。

## <a name="customize-your-embed-experience-using-url-settings"></a>使用 URL 設定自訂您的內嵌體驗

您可以自訂使用內嵌 URL 的輸入的設定的使用者體驗。 提供的 iFrame 中，您可以更新的 URL **src**設定。

| 屬性  | 描述  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | 您可以使用**pageName**查詢字串參數，若要設定哪一個報表頁面，即可開啟。 您可以找到此值在報表 URL 的結尾在 Power BI 服務中，檢視報表時，如下所示。 |  |  |  |
| URL 篩選  | 您可以使用[URL 篩選](service-url-filters.md)您從 Power BI UI 來篩選的內嵌內容的內嵌 URL 中收到。 透過這種方式，只需要基本 HTML 與 JavaScript 體驗，就可以建置只需要使用少數程式碼的整合。  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>設定哪些頁面隨即開啟內嵌的報表 

您可以找到**pageName**在 Power BI 服務中檢視報表時的報表 URL 的結尾值。

1. 從 Power BI 服務，在您的 web 瀏覽器中開啟報表，然後複製 網址列 URL。

    ![[報告] 區段](media/service-embed-secure/secure-embed-report-section.png)

2. 將 **pageName** 設定附加到 URL。

    ![附加 pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>使用 URL 篩選來篩選報告內容 

您可以使用[URL 篩選](service-url-filters.md)提供不同的報表檢視。 例如，下面的 URL 會篩選報告以顯示能源產業的資料。

使用 **pageName** 與 [URL Filters](service-url-filters.md) 的組合功能強大。 您可以使用基本 HTML 與 JavaScript 來建置體驗。

例如，以下是您可以將加入 HTML 網頁按鈕：

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

選取時，按鈕會呼叫的函式，來更新使用更新的 URL，包括能源產業篩選的 iFrame。

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![篩選](media/service-embed-secure/secure-embed-filter.png)

您可以視需要新增所要的按鈕數目，以建立不需要撰寫太多程式碼的自訂體驗。 

## <a name="considerations-and-limitations"></a>考量與限制

* Azure 企業對企業 (B2B) 不支援外部使用者。

* 安全內嵌適用於發行到 Power BI 服務的報告。

* 使用者需要登入以檢視報表，每當開啟新的瀏覽器視窗。

* 有些瀏覽器會要求您登入之後, 重新整理頁面，尤其是當使用 InPrivate 或 Incognito 模式。

* 達成單一登入體驗、 使用內嵌在 SharePoint Online 選項，或建置自訂整合，使用[使用者擁有資料](developer/embed-sample-for-your-organization.md)內嵌方法。 

* 隨著 [內嵌]  選項提供的自動驗證功能無法搭配 Power BI JavaScript API 使用。 Power BI JavaScript api，使用[使用者擁有資料](developer/embed-sample-for-your-organization.md)內嵌方法。 

## <a name="next-steps"></a>後續步驟

* [共用您在 Power BI 中的工作方式](service-how-to-collaborate-distribute-dashboards-reports.md)

* [在 URL 中使用查詢字串參數篩選報表](service-url-filters.md)

* [在 SharePoint Online 中內嵌報表網頁組件](service-embed-report-spo.md)

* [從 Power BI 發佈至網路](service-publish-to-web.md)