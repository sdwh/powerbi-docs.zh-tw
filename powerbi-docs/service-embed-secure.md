---
title: 在安全入口網站或網站中內嵌報告
description: 使用 Power BI 安全內嵌功能時，您可以讓使用者輕鬆、安全地在內部 Web 入口網站中內嵌報告。
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 81f6d77543ec53ac790f5c5183da32bde80fd6b9
ms.sourcegitcommit: b3af4f7ef486c95cea173caea5a31d0472816ddd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54136683"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>在安全入口網站或網站中內嵌報告

Power BI 中報告的新安全 [內嵌] 選項可讓使用者輕鬆、安全地在內部 Web 入口網站中內嵌報告，不論該入口網站是**雲端式**或**裝載在內部部署環境** (例如 SharePoint 2019)。 以此方式內嵌的報告會尊重資料列層級安全性 (RLS) 的所有項目權限與資料安全性。 此功能是設計來允許不使用程式碼內嵌到接受要內嵌之 URL 或 iFrame 的任何入口網站。

[內嵌] 選項也支援 [URL 篩選](service-url-filters.md)與 URL 設定。 [內嵌] 選項可讓您使用幾乎不需要任何程式碼的方式 (但要求您具備基本 HTML 與 JavaScript 知識) 來與入口網站整合。

## <a name="how-to-embed-power-bi-reports-into-portals"></a>如何將 Power BI 報告**內嵌**到入口網站

1. 您可以在 Power BI 服務之報告中的 [檔案] 功能表找到新的 [內嵌] 選項。

    ![[安全內嵌] 選項下拉式選項](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. 選取 [內嵌] 選項以開啟對話方塊，此對話方塊提用來安全地內嵌報告的供連結與 iFrame。

    ![[內嵌] 選項對話方塊](media/service-embed-secure/secure-embed-code-dialog.png)

3. 在您的 Web 入口網站內嵌您的 URL 或直接開啟 URL 之後，使用者必須通過驗證才能存取報告。 在下面，使用者未在瀏覽器工作階段中登入 Power BI。 當他們按下 [登入] 時，可能必須開啟新的瀏覽器視窗或索引標籤。 若您沒有看到登入提示，請檢查快顯封鎖程式。

    ![登入以檢視此報告](media/service-embed-secure/secure-embed-sign-in.png)

4. 在使用者登入之後，報告將會開啟並顯示資料，而且允許使用者在頁面之間瀏覽及設定篩選。 報告只會針對有在 Power BI 中檢視報告之權限的使用者顯示。 也會套用所有資料列層級安全性 (RLS) 規則。 最後，使用者必須正確地取得授權：他們需要 Power BI Pro 授權，或報告必須位於 Power BI Premium 容量的工作區中。 使用者妹次開啟新的瀏覽器視窗時都必須登入，但只要他們登入，系統就會自動載入其他報告。

    ![內嵌報告](media/service-embed-secure/secure-embed-report.png)

5. 當使用 iFrame 選項時，最好編輯提供的 HTML 以指定適合您入口網站網頁的寬度與高度。

    ![設定高度與寬度](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-access-to-reports"></a>授與報表存取權

[內嵌] 選項不會自動允許使用者檢視報告。 在 Power BI 服務中，具有檢視報表所需的權限。

若要提供對 Power BI 服務內之報告的存取權，您可以將報告與需要內嵌報告存取權的使用者共用。 如果您使用 Office 365 群組，可以將使用者列為 Power BI 服務內的應用程式工作區成員。 如需詳細資訊，請參閱如何[管理應用程式工作區](service-manage-app-workspace-in-power-bi-and-office-365.md)。

## <a name="licensing"></a>授權

檢視報告的使用者需要 Power BI Pro 授權，或者內容需要位於 [Power BI Premium 容量 (EM 或 P SKU)](service-admin-premium-purchase.md) 的工作區中。

## <a name="customize-your-embed-experience-using-url-settings"></a>使用 URL 設定自訂您的內嵌體驗

內嵌 URL 支援數個輸入設定，這些設定可協助您自訂您的使用者體驗。 若您使用提供的 iFrame，請確認您已在 iFrame 的來源設定中更新 URL。

| 屬性  | 描述  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | 您可以使用 **pageName** 查詢字串參數來設定要開啟報告的哪一個頁面。 **pageName** 值對應到報告 URL 結尾 (當在 Power BI 服務中檢視報告時)，如下所示。 |  |  |  |
| URL 篩選  | 您可以在接收自 Power BI UI 的內嵌 URL 中使用 [URL 篩選](service-url-filters.md)以篩選內嵌的內容。 透過這種方式，只需要基本 HTML 與 JavaScript 體驗，就可以建置只需要使用少數程式碼的整合。  |  |  |  |

## <a name="set-which-page-opens-when-the-report-is-embedded"></a>設定當內嵌報告時要開啟的頁面

*pageName* 設定中提供的值對應到報告 URL 的結尾 (當在 Power BI 服務中檢視報告時)。

1. 在您的網頁瀏覽器中從 Power BI 服務開啟報告，然後從網址列複製 URL。

    ![[報告] 區段](media/service-embed-secure/secure-embed-report-section.png)

2. 將 *pageName* 設定附加到 URL。

    ![附加 pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>使用 URL 篩選來篩選報告內容

如需進階功能，您可以使用 [URL 篩選](service-url-filters.md)來使用報告建置更豐富的體驗。 例如，下面的 URL 會篩選報告以顯示能源產業的資料。

使用 **pageName** 與 [URL Filters](service-url-filters.md) 的組合功能強大。 您可以使用基本 HTML 與 JavaScript 來建置體驗。

例如，以下說明如何新增按鈕到 HTML 頁面：

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

當按下該按鈕時，系統會呼叫函式以使用更新的 URL 來更新 iFrame，這包括能源產業的篩選。

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

* 每當使用者開啟新的瀏覽器視窗時，都必須登入以檢視報告。

* 在登入之後，某些瀏覽器會要求您重新整理頁面，特別是使用 InPrivate 或無痕模式時。

* 為獲得單一登入體驗，請使用 [內嵌於 SharePoint Online 中] 選項，或使用[使用者擁有資料](developer/embed-sample-for-your-organization.md)方式建置自訂整合。 深入了解[使用者擁有資料](developer/embed-sample-for-your-organization.md)。

* 隨著 [內嵌] 選項提供的自動驗證功能無法搭配 Power BI JavaScript API 使用。 針對 Power BI JavaScript API，請使用[使用者擁有資料](developer/embed-sample-for-your-organization.md)方式來內嵌。 深入了解[使用者擁有資料](developer/embed-sample-for-your-organization.md)。

## <a name="next-steps"></a>後續步驟

* [共用成品的方式](service-how-to-collaborate-distribute-dashboards-reports.md)

* [URL 篩選](service-url-filters.md)

* [SharePoint Online 報告 Web 組件](service-embed-report-spo.md)

* [發行至 Web](service-publish-to-web.md)