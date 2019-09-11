---
title: 編頁報表中的 URL 參數 - Power BI 報表產生器
description: 本主題描述 Power BI 分頁報表產生器報表參數的常見使用案例、您可以設定的屬性等。
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: bda35bfb4690d8109f7bd611e3d319278d235f33
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302664"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Power BI 編頁報表中的 URL 參數

您可以將參數新增至 URL，來將命令傳送至 Power BI 中的編頁報表。 例如，您可能使用了一組特定的報表參數值來檢視報表。 您可以使用預先定義的 URL 存取參數，來將這項資訊封裝在 URL 中。 您可以藉由內嵌參數來轉譯格式，或針對報表工具列的外觀及操作，進一步自訂 Power BI 處理報表的方式。 然後，您可以將此 URL 直接貼到電子郵件或網頁中，讓其他人在瀏覽器中以相同方式體驗您的報表。 

以下是您可以透過 URL 存取參數執行的動作： 

- 將報表參數傳送至報表。 
- 以所支援檔案格式起始報表內容的匯出。 
- 隱藏或檢視參數窗格。 
- 指定 DeviceInfo 設定。 

如需可透過 URL 存取使用的命令和設定完整清單，請參閱此文章稍後的  [URL 存取參數參考](#url-access-parameter-reference)。 

## <a name="url-access-concepts"></a>URL 存取概念 

Power BI 的 URL 要求包含服務所處理參數。 服務處理 URL 要求的方式取決於 URL 中所包含參數、參數前置詞和項目類型。 編頁報表 URL 功能與大部分支援標準 URL 定址的瀏覽器和應用程式相容。 

## <a name="url-access-syntax"></a>URL 存取語法 

URL 要求可以包含多個參數 (依任何順序列出)。 參數是以 & 符號分隔。 名稱/值對是以等號 (=) 分隔。 例如：

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>語法描述 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Power BI 租用戶的 Web 服務 URL。 例如： 

**&** ：用來分隔 URL 存取參數的名稱/值對。

**前置詞**：URL 參數的前置詞 (例如 rp: 或  rdl:)，可指定 Power BI 服務中的動作。 

> [!NOTE]
> 報表參數需要參數前置詞，且會區分大小寫。 

**parameter**：參數名稱。 

### <a name="value"></a>value 

對應至所使用參數值的 URL 文字。 

如需在 URL 上傳遞報表參數的範例，請參閱 [在 URL 中傳遞報表參數](report-builder-url-pass-parameters.md)。

## <a name="url-access-parameter-reference"></a>URL 存取參數參考

您可以使用下列參數作為 URL 的一部分，以設定 Power BI 中編頁報表的外觀及操作。 本節列出最常見的參數。 這些參數不會區分大小寫，如果與輸出格式相關，則會以參數前置詞  `rdl:`  開頭。  

### <a name="report-commands-rdl"></a>報表命令 (`rdl:`) 

**匯出格式**：指定用來轉譯和匯出報表的格式。 可用值為： 
- PPTX (PowerPoint)
- MHTML 
- 影像 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>後續步驟

- [針對 Power BI 中的編頁報表在 URL 中傳遞報表參數](report-builder-url-pass-parameters.md)
- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
