---
title: 訂閱 Power BI 服務中的分頁報表
description: 在本文中，您將了解在 Power BI 服務中訂閱編頁報表的注意事項。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 08/29/2019
ms.openlocfilehash: 4b0ead5697dc94497609ac925a0a46142584f0ba
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185604"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>為您自己和其他人訂閱 Power BI 服務中的分頁報表 

您現在可以為您自己和其他人設定 Power BI 服務中分頁報表的電子郵件訂閱。 在一般情況下，流程與[訂閱 Power BI 服務中的報表與儀表板](service-report-subscribe.md)相同。 本文詳細說明差異和考量。 

在訂閱設定中，選擇您希望收到電子郵件的頻率：每天、每週、每月或每小時。 您也可以選擇想要執行訂閱的時間。 總之，針對每份報表，您可以設定最多 24 個不同的訂閱。 

## <a name="considerations-for-paginated-report-subscriptions"></a>分頁報表訂閱考量 

- 不同於儀表板或 Power BI 報表訂閱，您的訂閱會包含完整報表輸出附件。  支援下列附件類型︰PDF、PowerPoint 簡報 (PPTX)、Excel 活頁簿 (XLSX)、Word 文件 (DOCX)、CSV 檔案和 XML。

- 您可以在電子郵件內文中包含報表的預覽影像。  這是選擇性的，且視所選的附件格式，其會與您附加報表文件的第一頁有些不同。 

- 報表附件大小上限為 25 MB。 

- 您可以為其他使用者訂閱與任何目前支援之資料來源連線的分頁報表，包括 Azure Analysis Services 或 Power BI 資料集。 請注意，報表附件會根據您的權限反映於資料上，如同目前的 SQL Server Reporting Services。 

- 電子郵件訂閱可以您針對報表的目前選取項目或預設參數來進行傳送。  您可以為每個您為報表建立的訂閱設定不同的參數值。 

- 若報表作者有設定以運算式為基礎的參數 (例如預設是今天的日期)，訂閱便會使用它作為預設值。 您可以變更其他參數值並選擇使用目前的值，但除非您也明確變更該值，否則訂閱會使用以運算式為基礎的參數。

- 分頁報表不具有**在資料重新整理後**頻率選項。 您將一律從基礎資料來源取得最新的值。 

## <a name="next-steps"></a>後續步驟

[為您自己和其他人訂閱 Power BI 服務中的報表和儀表板](service-report-subscribe.md)

[什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
