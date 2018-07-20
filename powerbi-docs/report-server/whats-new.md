---
title: Power BI 報表伺服器的新功能
description: 了解 Power BI 報表伺服器的新功能。 其涵蓋主要功能範圍，並會隨著新項目發行而更新。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: maggies
ms.openlocfilehash: 07c393425d2a04376a4fcf81c2c35a0e115eeaee
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34481943"
---
# <a name="whats-new-in-power-bi-report-server"></a>Power BI 報表伺服器的新功能
了解 Power BI 報表伺服器的新功能。 其涵蓋主要功能範圍，並會隨著新項目發行而更新。

若要下載 Power BI 報表伺服器，以及針對 Power BI 報表伺服器最佳化的 Power BI Desktop，請移至[使用 Power BI 報表伺服器的內部部署報表](https://powerbi.microsoft.com/report-server/)。

此外，也請查看下列來源來掌握「Power BI 報表伺服器」新功能的最新動態。

* [Microsoft Power BI 部落格](https://powerbi.microsoft.com/blog/)
* [SQL Server Reporting Services 小組部落格](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Guy in a Cube YouTube 頻道](https://aka.ms/guyinacube)

如需相關的 Power BI「新功能」資訊，請參閱︰

* [Power BI 服務的新功能](../service-whats-new.md)
* [Power BI Desktop 的新功能](../desktop-latest-update.md)
* [Power BI 行動裝置 App 的新功能](../mobile-whats-new-in-the-mobile-apps.md)

## <a name="may-2018"></a>2018 年 5 月

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>針對報表伺服器遠端設定 Power BI iOS 行動應用程式

身為 IT 系統管理員，您現在可以使用您組織的 MDM 工具來遠端設定 Power BI iOS 行動裝置應用程式對報表伺服器的存取。 如需詳細資料，請參閱[從遠端設定 Power BI iOS 行動裝置應用程式對報表伺服器的存取權](configure-powerbi-mobile-apps-remote.md)。

## <a name="march-2018-release"></a>2018 年 3 月版本

2018 年 3 月，我們在針對 Power BI 報表伺服器最佳化的 Power BI Desktop 版本中新增了許多功能。 這些功能可依區域細分如下： 
- [視覺效果](#visuals-updates)
- [報告](#reporting)
- [分析](#analytics)
- [效能](#performance)
- [報表伺服器](#report-server)
- [其他](#other-improvements)

### <a name="highlights-of-this-release"></a>本版重點

在這整個很長的新功能清單中，以下是特別值得關注的功能。

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[資料表和矩陣之以規則為基礎的條件式格式設定](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)
 
建立規則，根據您資料表或矩陣中的特定商務邏輯，來視情況著色資料行的背景或字型色彩。

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[顯示和隱藏頁面](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

您希望讀者可存取您的報表，但某些頁面尚未完成。 現在您可以隱藏這些頁面，直到就緒為止。 或者，您可以從一般瀏覽隱藏頁面，而且讀者可以透過書籤或鑽研到達頁面。

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[標記書籤](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

標記書籤是指建立書籤，透過您報表中的資料來述說故事。

- [書籤的交叉醒目提示](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting)：書籤會在您建立書籤時，維護並顯示報表頁面的交叉醒目提示狀態。
- [更多書籤彈性](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility)：書籤會反映您在報表中設定的屬性，而且只會影響您選擇的視覺效果。

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[跨多個圖表複選資料點](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

在多個圖表中選取多個資料點，並將交叉篩選套用至整個頁面。

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[跨報表的多個頁面同步交叉分析篩選器](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

交叉分析篩選器可套用至一個、兩個或多個報表頁面。

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[快速量值](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

根據資料表中的現有量值和數值資料行，建立新的量值。

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[向下切入篩選其他視覺效果](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

當您在某個視覺效果的指定類別中向下切入時，您可以讓它依該相同的類別篩選頁面上的所有視覺效果。

### <a name="visuals-updates"></a>視覺效果更新

- [資料表和矩陣的資料格對齊](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [顯示資料表和矩陣資料行的單位和精確度控制](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [橫條圖和直條圖的資料標籤溢位](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [控制笛卡兒座標和地圖視覺效果的資料標籤背景色彩](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [橫條/直條邊框間距控制項](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [增加用於圖表中軸標籤的面積](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [從 X 和 Y 軸群組的散佈圖視覺效果](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [根據緯度和經度之地圖的高密度取樣](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [回應式交叉分析篩選器](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [新增相對日期交叉分析篩選器的錨點日期](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>報告

- [關閉報表讀取模式的視覺效果標頭](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [慢速資料來源的報表選項](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [改善的預設視覺效果放置](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [透過選取窗格控制視覺效果排序](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [鎖定報表上的物件](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [搜尋格式設定和分析窗格](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [欄位屬性窗格和欄位描述](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>分析

- [UTCNOW() 和 UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [標記自訂日期資料表](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [鑽研篩選其他視覺效果](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [多列卡片之多維度 AS 模型的資料格層級格式](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)
 
### <a name="performance"></a>Performance

- [篩選效能提升](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [DirectQuery 效能改善](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [開啟和儲存效能改善](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [[顯示沒有資料的項目] 改善](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)
 
### <a name="report-server"></a>報表伺服器 

#### <a name="export-to-accessible-pdf"></a>匯出至可存取的 PDF

當您將編頁報表 (RDL) 匯出至 PDF 時，您現在可以取得可存取/標記的 PDF 檔案。 雖然其大小更大，但更方便螢幕助讀程式和其他輔助技術讀取和巡覽。 您可以將 **AccessiblePDF** 裝置資訊設定設為 **True**，來啟用可存取的 PDF。 請參閱 [PDF 裝置資訊設定](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings)和[變更裝置資訊設定](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings)。


### <a name="other-improvements"></a>其他功能改進

- [從範例新增資料行改善](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [諮詢服務快速連結](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [改善的錯誤報告](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [檢視之前發生的錯誤](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

 
## <a name="october-2017-release"></a>2017 年 10 月版本
### <a name="power-bi-report-data-sources"></a>Power BI 報表資料來源
Power BI 報表伺服器中的 Power BI 報表可以連線到各種資料來源。 您可以匯入資料及排程資料重新整理，或使用 DirectQuery 或即時連線到 SQL Server Analysis Services，直接進行查詢。 請參閱支援排程重新整理的資料來源清單，以及支援「Power BI 報表伺服器中 Power BI 報表資料來源」中 DirectQuery 的資料來源清單。

### <a name="scheduled-data-refresh-for-imported-data"></a>針對匯入的資料排程資料重新整理
在 Power BI 報表伺服器中，您可以設定排程資料重新整理，讓 Power BI 報表中的資料保持與內嵌模型的最新狀態，而不是即時連線或 DirectQuery。 您使用內嵌模型來匯入資料，所以會與原始資料來源中斷連線。 它必須更新以將資料保持在最新狀態，排程重新整理是執行此作業的一種方式。 深入了解「Power BI 報表伺服器中 Power BI 報表的排程重新整理」。

### <a name="editing-power-bi-reports-from-the-server"></a>編輯來自伺服器的 Power BI 報表
您可以從伺服器開啟和編輯 Power BI 報表 (.pbix) 檔案，但是您會回到您上傳的原始檔案。  這表示**如果資料已由伺服器重新整理，當您第一次開啟檔案時，不會重新整理資料**。 您必須手動在本機重新整理，才能看到變更。

### <a name="large-file-uploaddownload"></a>大型檔案上傳/下載
您可以上傳最大 2 GB 大小的檔案，但是預設情況下，在 SQL Server Management Studio (SSMS) 的報表伺服器設定中，這項限制設為 1 GB。  這些檔案會儲存在資料庫中，如同適用於 SharePoint 一般，不需要 SQL Server 目錄的特殊設定。  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>存取共用資料集作為 OData 摘要
您可以從 Power BI Desktop 使用 OData 摘要存取共用資料集。 如需詳細資訊，請參閱[在 Power BI 報表伺服器中存取共用資料集作為 OData 摘要](access-dataset-odata.md)。

### <a name="scale-out"></a>相應放大
這個版本支援相應放大。使用負載平衡器並設定伺服器親和性，以獲得最佳體驗。 請注意，案例尚未針對相應放大最佳化，因此您會看到模型可能會在多個節點之間複寫。 沒有網路負載平衡器和黏性工作階段，案例也能夠運作。 不過，您不只會看到因為模型載入 N 次導致記憶體跨節點過度使用，也會看到因為每次模型在要求之間觸及新節點都會串流，導致連線之間的效能變慢。  

### <a name="administrator-settings"></a>系統管理員設定
系統管理員可以在伺服器陣列的 SSMS 進階屬性中設定下列屬性：

* EnableCustomVisuals：True/False
* EnablePowerBIReportEmbeddedModels：True/False
* EnablePowerBIReportExportData：True/False
* MaxFileSizeMb：預設值現在為 1000
* ModelCleanupCycleMinutes：檢查以從記憶體收回模型的頻率
* ModelExpirationMinutes：根據上一次的使用，模型到期和收回之前還有多少時間
* ScheduleRefreshTimeoutMinutes：模型的資料重新整理需要多少時間。 預設為兩小時。  沒有硬性上限。

**設定檔 rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>開發人員 API
針對 SSRS 2017 引進的開發人員 API (REST API) 已針對 Power BI 報表伺服器擴充，以與 Excel 檔案和 .pbix 檔案搭配運作。 一個可能的使用案例是以程式設計方式從伺服器下載檔案、重新整理，然後重新發佈。 舉例來說，這是重新整理 Excel 活頁簿與 PowerPivot 模型的唯一方式。

請注意，對於大型檔案有一個新的個別 API，它會在 Power BI 報表伺服器版本的 Swagger 中更新。 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) 和 Power BI 報表伺服器記憶體使用量
Power BI 報表伺服器現在於內部裝載 SQL Server Analysis Services (SSAS)。 這不是排程重新整理特有的。 裝載 SSAS 會大幅擴充報表伺服器記憶體使用量。 AS.ini 設定檔可以在伺服器節點上使用，因此如果您熟悉 SSAS，也許會想要更新設定，包括最大記憶體限制和磁碟快取等等。如需詳細資訊，請參閱 [Analysis Services 中的伺服器屬性](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services)。

### <a name="viewing-and-interacting-with-excel-workbooks"></a>檢視 Excel 活頁簿並與之互動
Excel 和 Power BI 包含產業中特有的工具組合。 此外，它們可讓商務分析師更輕鬆地收集、塑形、分析並以視覺化方式探索其資料。 除了在入口網站中檢視 Power BI 報表之外，商務使用者現在也可以在 Power BI 報表伺服器中執行與 Excel 活頁簿相同的作業，讓他們有一個位置可以發佈和檢視其自助 Microsoft BI 內容。

我們已發佈[如何將 Office Online Server (OOS) 新增至 Power BI 報表伺服器 Preview 環境的逐步解說](excel-oos.md)。 具有大量授權帳戶的客戶可以免費從大量授權服務中心下載 OOS，並且具有僅限檢視功能。 設定之後，使用者可以檢視 Excel 活頁簿，並與之互動，而 Excel 活頁簿：

* 沒有任何外部資料來源相依性
* 即時連線至外部 SQL Server Analysis Services 資料來源
* 具有 PowerPivot 資料模型

### <a name="support-for-new-table-and-matrix-visuals"></a>新資料表和矩陣視覺效果的支援
Power BI 報表伺服器現在支援新的 Power BI 資料表和矩陣視覺效果。 若要使用這些視覺效果來建立報表，您需要 2017 年 10 月版本的已更新 Power BI Desktop 版本。 它無法與 Power BI Desktop (2017 年 6 月) 版本並存安裝。 如需最新版本的 Power BI Desktop，請在 [Power BI 報表伺服器下載分頁](https://powerbi.microsoft.com/report-server/)上選取 [進階下載選項]。

## <a name="june-2017"></a>2017 年 6 月
* Power BI 報表伺服器正式推出 (GA)。

## <a name="may-2017"></a>2017 年 5 月
* Power BI 報表伺服器預覽版已正式運作
* 可在內部發行 Power BI 報表
  * 支援自訂視覺效果
  * Analysis Services 即時連線的支援必須等待更多資料來源。
  * Power BI 行動裝置應用程式已更新，以顯示 Power BI 報表伺服器裝載的 Power BI 報表
* 增強報表中使用註解的共同作業

## <a name="next-steps"></a>後續步驟
[什麼是 Power BI 報表伺服器？](get-started.md) 
[管理員手冊](admin-handbook-overview.md)  
[安裝 Power BI 報表伺服器](install-report-server.md)  
[安裝報表產生器](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[下載 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

