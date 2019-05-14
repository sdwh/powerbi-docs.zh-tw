---
title: 閘道的效能監視 （公開預覽）
description: 本文章提供有關監視內部部署資料閘道活動的效能資訊。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535359"
---
# <a name="gateway-performance-monitoring-public-preview"></a>閘道的效能監視 （公開預覽）

若要監視的效能，閘道系統管理員有傳統上會相依於手動監視效能計數器，透過 Windows 效能監視器工具。 我們現在提供額外的查詢記錄和[閘道效能 PBI 範本檔案](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit)呈現結果。 這項功能提供新的深入了解閘道使用量，並可讓您疑難排解執行緩慢的查詢。

> [!NOTE]
> 這項功能目前已推出僅針對在內部部署資料閘道，在標準模式下，不能用於個人的模式。

## <a name="enable-performance-logging"></a>啟用效能記錄

若要啟用這項功能，進行下列變更*Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*檔案中 「 \Program Files\On-內部部署資料閘道 」 資料夾：

1. 更新**QueryExecutionReportOn**要 _，則為 True_來啟用其他記錄使用閘道器所執行的查詢。 啟用此選項會建立查詢執行的報表和查詢執行彙總報告檔案。

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. 更新**SystemCounterReportOn**要 _，則為 True_啟用記憶體和 CPU 系統計數器的其他記錄功能。 啟用此選項會建立系統計數器彙總報告檔案。

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. 您可以視需要更新的組態檔中有其他的值。

    - **ReportFilePath**:判斷儲存三個記錄檔的路徑。 根據預設，這個路徑會是"\Users\PBIEgwService\AppData\Local\Microsoft\On-premises 資料 gateway\Report"或"Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On 內部部署資料 gateway\Report 」，根據 OS 版本。 如果您使用的服務帳戶閘道以外_PBIEgwService_，使用的服務帳戶名稱取代此路徑的一部分。
    - **ReportFileCount**:決定要保留每種類型的記錄檔數目。 預設值為 10。
    - **ReportFileSizeInBytes**:決定要維護的檔案大小。 預設值是 104857600。
    - **QuerExecutionAggregationTimeInMinutes**:決定會彙總與查詢執行資訊的分鐘數。 預設值為 5。
    - **SystemCounterAggregationTimeInMinutes**:決定會彙總與系統計數器的分鐘數。 預設值為 5。

1. 您已對組態檔中的變更之後，重新啟動閘道，這些設定值，才會生效。 您現在就開始會看到在您指定的位置中產生的報表檔案**ReportFilePath**。

    > [!NOTE]
    > 可能需要最多 10 分鐘的時間再加上設定的時間量**QuerExecutionAggregationTimeInMinutes**組態檔，直到檔案開始顯示在資料夾中。

## <a name="understand-performance-logs"></a>了解效能記錄檔

當您開啟這項功能時，我們會建立三個新的記錄檔：

- 查詢執行報表
- 查詢執行彙總報告
- 系統的計數器彙總報告

查詢執行的報表包含詳細的查詢執行資訊。 我們會擷取下列屬性：

|屬性 |描述 |
| ---- | ---- |
|**GatewayObjectId** |閘道器的唯一識別碼。 |
|**RequestId** |閘道要求的唯一識別碼。 可能是相同的多個查詢。 |
|**DataSource** |包含資料來源類型和資料來源。 |
|**QueryTrackingId** |查詢的唯一識別碼。 |  
|**QueryExecutionEndTimeUTC** |當查詢執行完成時的時間。 |
|**QueryExecutionDuration**(ms) |查詢執行的持續時間。 |
|**QueryType** |輸入的查詢-例如，Power BI 重新整理 DirectQuery 或從 PowerApps 和 Microsoft Flow 的查詢，可能是傳遞查詢。 |
|**DataProcessingEndTimeUTC** |時間資料處理活動，例如多工緩衝處理、 資料擷取、 壓縮、 資料處理和已完成的等等。 |
|**DataProcessingDuration**(ms) |資料處理活動，例如多工緩衝處理、 資料擷取、 壓縮、 資料處理和等等的持續時間。 |
|**Success** |表示是否查詢成功或失敗。 |
|**ErrorMessage** |如果查詢失敗，表示錯誤訊息。 |
| | |

查詢執行彙總報告包含的查詢資訊的時間間隔內彙總**GatewayObjectId**， **DataSource**，**成功**，以及**QueryType**。 預設值為 5 分鐘，但您可以調整它，如下所述。 我們會擷取下列屬性：

|屬性 |描述 |
| ---- | ---- |
|**GatewayObjectId** |閘道器的唯一識別碼。 |
|**AggregationStartTimeUTC** |已彙總與查詢屬性的時間範圍的開頭。 |
|**AggregationEndTimeUTC** |對於查詢所彙總屬性的時間間隔的結尾。 |
|**DataSource** |包含資料來源類型和資料來源。 |
|**Success** |表示是否查詢成功或失敗。 |
|**AverageQueryExecutionDuration**(ms) |彙總時間間隔的平均查詢執行時間。 |
|**MaxQueryExecutionDuration**(ms) |針對彙總的時間範圍的最大的查詢執行時間。 |
|**MinQueryExecutionDuration**(ms) |針對彙總的時間範圍的最小的查詢執行時間。 |
|**QueryType** |輸入的查詢-例如，Power BI 重新整理 DirectQuery 或從 PowerApps 和 Microsoft Flow 的查詢，可能是傳遞查詢。 |
|**AverageDataProcessingDuration**(ms) |平均等多工緩衝處理、 資料擷取、 壓縮、 資料處理的資料處理活動等的彙總時間間隔的時間。 |
|**MaxDataProcessingDuration**(ms) |最長時間的資料處理活動，例如多工緩衝處理、 資料擷取、 壓縮、 資料處理等彙總時間間隔。 |
|**MinDataProcessingDuration**(ms) |最小時間的資料處理活動，例如多工緩衝處理、 資料擷取、 壓縮、 資料處理等彙總時間間隔。 |
|**Count** |查詢數目。 |
| | |

系統的計數器彙總報告包含系統計數器的值時間間隔內彙總。 預設值為 5 分鐘，但您可以調整它，如下所述。 我們會擷取下列屬性：

|屬性 |描述 |
| ---- | ---- |
|**GatewayObjectId** |閘道器的唯一識別碼。 |
|**AggregationStartTimeUTC** |為其系統計數器已彙總的時間範圍的開頭。 |
|**AggregationEndTimeUTC** |哪些系統計數器已彙總的時間間隔的結尾。 |
|**CounterName** |系統計數器，包括閘道、 混搭程式的記憶體和 CPU 使用量，以及整體機器主控閘道。 |
|**Max** |彙總時間間隔的 [系統] 計數器的最大值。 |
|**Min** |彙總時間間隔的 [系統] 計數器的最小值。 |
|**Average** |彙總時間間隔的 [系統] 計數器的平均值。 |
| | |

## <a name="visualize-gateway-performance"></a>以視覺化方式檢視閘道效能

現在，您可以將記錄檔中的資料視覺化。

1. 下載[閘道效能 PBI 範本](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit)使用 Power BI desktop 加以開啟。

1. 在開啟的對話方塊中，檢查 資料夾路徑的值符合**ReportFilePath**。

    ![快顯視窗中的資料夾路徑](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. 選取 **負載**，而範本檔案可讓您開始從您的記錄檔載入資料。 所有視覺效果則應該在報表中使用的資料會填入。

1. 選擇性地將此檔案儲存為 PBIX，並將它發行到您的服務，自動重新整理。

此外，您可以自訂此範本檔案，以符合您的需求。 如需有關 Power BI 範本的詳細資訊，請參閱此[Microsoft Power BI 部落格文章](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/)。