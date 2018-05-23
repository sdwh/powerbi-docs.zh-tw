---
title: 使用 Power BI 連接到 Adobe Analytics
description: 從 Power BI 連線到 Adobe Analytics，以使用在儀表板和報表中顯示您帳戶資料的應用程式。
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e8e9b21e62f0a91234fccf78977a696e321ed8dc
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-adobe-analytics-with-power-bi"></a>使用 Power BI 連接到 Adobe Analytics
透過 Power BI 連接到 Adobe Analytics 時，一開始會連接到 Adobe Analytics 行銷雲端帳戶。 您會看到應用程式與 Power BI 儀表板和一組 Power BI 報表，供您深入了解網站流量和使用者維度。 資料會自動每天重新整理一次。 您可以與儀表板和報表互動，但無法儲存變更。

連線到 [Adobe Analytics](https://app.powerbi.com/getdata/services/adobe-analytics) 或深入了解 Power BI 與 [Adobe Analytics 的整合](https://powerbi.microsoft.com/integrations/adobe-analytics)。

## <a name="how-to-connect"></a>如何連接
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

1. 選取 [Adobe Analytics] \> [取得]。
   
   ![](media/service-connect-to-adobe-analytics/adobe.png)
2. Power BI 會連線到特定 Adobe Analytics 公司和報表套件識別碼 (而非報表套件名稱)。 請參閱以下關於[尋找這些參數](#FindingParams)的詳細資訊。
   
   ![](media/service-connect-to-adobe-analytics/parameters.png)
3. 針對 [驗證方法] 選取 [oAuth2] \> [登入]。 出現提示時，請輸入您的 Adobe Analytics 認證。 
   
    ![](media/service-connect-to-adobe-analytics/creds.png)
   
    ![](media/service-connect-to-adobe-analytics/adobe_signin.png)
4. 按一下 [接受]  允許 Power BI 存取 Adobe Analytics 資料。
   
   ![](media/service-connect-to-adobe-analytics/adobe_authorize.png)
5. 核准之後，匯入程序會自動開始。 

## <a name="view-the-adobe-analytics-dashboard-and-reports"></a>檢視 Adobe Analytics 儀表板和報表
[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-open-app.md)]

      ![Adobe Analytics dashboard](media/service-connect-to-adobe-analytics/dashboard.png)

[!INCLUDE [powerbi-service-apps-open-app](./includes/powerbi-service-apps-what-now.md)]

## <a name="whats-included"></a>包含的內容
Power BI 使用 Adobe Analytics 報告 API 來定義並執行下列資料表的報表：

| **資料表名稱** | **資料行詳細資料** |
| --- | --- |
| 產品 |elements=  "product" (top 25) </br> metrics="cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| 瀏覽器 |elements= "browser" (top 25)</br>  metrics="bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "pageviews" |
| 頁面 |elements= "page" (top 25)</br>  metrics="cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "visits", "uniquevisitors", "pageviews", "bounces", "bouncerate", "totaltimespent" |
| 已啟用 JavaScript |elements=  "javascriptenabled”, “browser” (top 25) |
| 行動裝置 OS |elements= "mobileos"(top 25)</br> metrics="bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "checkouts", "revenue", "units", "pageviews" |
| 搜尋引擎關鍵字 |elements= "searchengine" "searchenginekeyword"</br>  metrics="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| 產品搜尋引擎 |elements= "searchengine", "product"</br>  metrics="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| 參考頁面 |elements= "referrer" (top 15), “page" (top 10)</br>  metrics="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Geocountry 頁面 |elements= "geocountry" (Top 20), "page"</br>  metrics="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units", "pageviews" |
| Geocountry 產品 |elements= "geocountry" (Top 20), "product"</br> metrics="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| 國家及地區查閱 |elements= "geocountry" (Top 200)</br>  metrics="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| 語言 |elements= "language", "browser" (Top 25)</br>  metrics="bounces", "bouncerate", "visitors", "visits", "uniquevisitors", "totaltimespent", "pageviews", "cartadditions", "cartremovals", "checkouts", "carts", "cartviews" |
| 搜尋引擎查閱 |elements= "searchengine" (top 100)</br>  metrics="bounces", "bouncerate", "visitors", "visits", "entries", "uniquevisitors", "totaltimespent", "cartadditions", "cartremovals", "carts", "cartviews", "checkouts", "revenue", "units" |
| 瀏覽器查閱 |elements= "browser" (top 25) |

## <a name="system-requirements"></a>系統需求
需要 [Adobe Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html) 的存取權，包括正確參數的存取權，如下所述。

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>尋找參數
**公司**

一旦您登入帳戶，便可以在帳戶右上方找到公司值。 值會區分大小寫和間距。 請完全依照在帳戶中看到的樣子輸入它。

![](media/service-connect-to-adobe-analytics/adobe_companies.png)

**報表套件識別碼**

建立報表套件時會建立套件識別碼。 您可以連絡您的系統管理員以確認識別碼值。 請注意這不是報表套件名稱。

在 Adobe [文件](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html)：

![](media/service-connect-to-adobe-analytics/reportsuiteid.png)

## <a name="troubleshooting"></a>疑難排解
如果您在提供認證之後看到錯誤，指出您沒有權限，請與您的系統管理員確認是否有權存取 Adobe Analytics API。 另請確認所提供的 Adobe 識別碼已連結到行銷雲端組織 (與 Adobe Analytics 公司相關聯)。

如果您成功通過認證畫面之後遇到錯誤，有可能是因為報表佔用太多時間來完成所造成。 常見的錯誤格式為「無法從 Adobe 分析報表取得資料。內容包含 &quot;查閱者、頁面&quot;，持續時間約為 xx 秒」。 請檢閱＜包含的內容＞章節，並與您的 Adobe 執行個體大小相比較。 不幸的是目前無法解決此逾時。 不過我們正在考慮進行更新，以為較大的執行個體提供更佳的支援，請為 Power BI 小組提供您的意見反應，網址為 https://ideas.powerbi.com

## <a name="next-steps"></a>後續步驟
* [Power BI 中的應用程式是什麼？](service-install-use-apps.md)
* [取得 Power BI 中的資料](service-get-data.md)
* 有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

