---
title: 使用 Power BI 報表伺服器中的 REST API 進行開發
description: REST API 提供以程式設計方式存取 Power BI 報表伺服器目錄中的物件。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 9b8e795c4a55f9efd6fd534d92d95b36c93cf2c0
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874068"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>使用 Power BI 報表伺服器中的 REST API 進行開發

Power BI 報表伺服器支援具象狀態傳輸 (REST) API。 REST API 是服務端點，會支援一組 HTTP 作業 (方法)，該作業提供報表伺服器內資源的建立、擷取、更新或刪除存取權。

REST API 提供以程式設計方式存取 Power BI 報表伺服器目錄中的物件。 物件範例包括資料夾、報表、KPI、資料來源、資料集、重新整理計劃、訂用帳戶等等。 例如，您可以使用 REST API 來瀏覽資料夾階層、探索資料夾內容，或下載報表定義。 您也可以建立、更新及刪除物件。 使用物件的範例為上傳報表、執行重新整理計劃、刪除資料夾等等。

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>REST API 要求/回應的元件

REST API 要求/回應配對可以分成五個元件：

* **要求 URI**，它包含：`{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`。 雖然要求 URI 包含在要求訊息標頭中，我們在這裡會單獨呼叫，因為大部分語言或架構需要您從要求訊息單獨傳遞它。
  
  * URI 配置：指出用來傳送要求的通訊協定。 例如：`http` 或 `https`。
  * URI 主機：指定網域名稱或伺服器的 IP 位址，在其中裝載 REST 服務端點，例如 `myserver.contoso.com`。
  * 資源路徑：指定資源或資源集合，其中可能包含多個區段，服務會用來決定這些資源的選取。 例如：`CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` 可用來取得 CatalogItem 中指定的屬性。
  * 查詢字串 (選用)：提供其他簡單參數，例如 API 版本或資源選取準則。
* HTTP 要求訊息標頭欄位：
  
  * 必要的 [HTTP 方法](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (也稱為作業或動詞)，這會告知服務您要求的作業是什麼類型。 Reporting Services REST API 支援 DELETE、GET、HEAD、PUT、POST 和 PATCH 方法。
  * 選擇性額外標頭欄位，指定 URI 和 HTTP 方法需要這些欄位。
* 選擇性 HTTP **要求訊息本文**欄位，以支援 URI 和 HTTP 作業。 例如，POST 作業包含 MIME 編碼的物件，作為複雜參數傳遞。 針對 POST 或 PUT 作業，本文的 MIME 編碼類型也應該在 `Content-type` 要求標頭中指定。 有些服務需要您使用特定的 MIME 類型，例如 `application/json`。
* HTTP **回應訊息標頭**欄位：
  
  * [HTTP 狀態碼](https://www.w3.org/Protocols/HTTP/HTRESP.html)，範圍從 2xx 成功碼到 4xx 或 5xx 錯誤碼。 或者，可能會傳回定義服務的狀態碼，如同 API 文件中所示。
  * 選擇性額外標頭欄位，是支援要求的回應所需項目，例如 `Content-type` 回應標頭。
* 選擇性的 HTTP **回應訊息主體**欄位：
  
  * MIME 編碼回應物件會在 HTTP 回應本文中傳回，例如來自 GET 方法 (傳回資料) 的回應。 一般而言，這些物件會以結構化格式 (例如 JSON 或 XML) 傳回，如 `Content-type` 回應標頭所示。

## <a name="api-documentation"></a>API 文件

新式 REST API 需要新式 API 文件。 REST API 的建置根據是 OpenAPI 規格 (也稱為 swagger 規格)，文件可於 [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) 取得。 除了記錄 API 以外，SwaggerHub 還有助於以選擇的語言產生用戶端程式庫 – JavaScript、TypeScript、C#、Java、Python、Ruby 等等。

## <a name="testing-api-calls"></a>測試 API 呼叫

用於測試 HTTP 要求/回應訊息的工具之一是 [Fiddler](https://www.telerik.com/fiddler)。 Fiddler 是免費的 Web 偵錯 Proxy，可以攔截 REST 要求，以便輕鬆地診斷 HTTP 要求/回應訊息。

## <a name="next-steps"></a>後續步驟

在 [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) 上檢閱可用的 API。

可以在 [GitHub](https://github.com/Microsoft/Reporting-Services) 上取得範例。 範例包含以 TypeScript、React 和 webpack 以及 PowerShell 範例建置的 HTML5 應用程式。

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)