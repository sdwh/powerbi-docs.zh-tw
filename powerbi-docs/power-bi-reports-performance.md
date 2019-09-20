---
title: Power BI 效能最佳做法
description: 本文提供如何在 Power BI 中建置快速且可靠報表的指引
author: Bhavik-MSFT
ms.author: bhmerc
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/30/2018
LocalizationGroup: Reports
ms.openlocfilehash: 736c1ee1b1998ec7f991167352313a05061b3f3c
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2019
ms.locfileid: "70841492"
---
# <a name="power-bi-performance-best-practices"></a>Power BI 效能最佳做法

本文提供如何在 Power BI 中建置快速且可靠報表的指引。  

## <a name="choose-an-appropriate-storage-mode-import-directquery"></a>選擇適當的儲存模式：匯入、DirectQuery

在大部分情況下，匯入模式是最佳選擇，因為它會利用使用單欄式儲存體壓縮的本機快取記憶體內部資料，提供最高速的速度。 匯入模式也允許完整的 DAX 功能。 當來源資料磁碟區太大而無法納入您的 Power BI 容量時，請考慮 DirectQuery (和複合模型)。 當您必須在每次載入報表時都從來源提取最新的資料，DirectQuery 也很有用。 如果您沒有這些需求，而且使用者只需要查看每天 (或更少) 更新幾次的資料 (例如從公司資料倉儲)，則強烈建議使用匯入模式。 在 DirectQuery 模式中，使用者可能會嘗試重新整理報表，而不會意識到他們從來源中擷取完全相同的資料。      

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>使用篩選來限制報表視覺效果只顯示需要的項目 

視覺效果所需顯示的資料越多，要載入的視覺效果就越慢。 雖然此原則看起來很明顯，但卻很容易忘記。 例如：假設您有大型資料集。 並且除了該資料集外，您還使用了資料表的資料表來建置報表。 終端使用者會在頁面上使用交叉分析篩選器來取得想要的資料列，且通常只會對數十個資料列感興趣。

一個常見錯誤是在不篩選的情況下保留資料表預設檢視，亦即全部超過 1 億筆資料列。 在每次重新整理時，都會將這些資料列的資料載入記憶體，並進行解壓縮。 這種處理會造成龐大的記憶體負載。 解決方式：使用「前 N 筆」篩選來減少資料表顯示的最大項目數。 您可以將最大項目設為超過使用者需要的數量，例如 10,000 筆。 結果是不但終端使用者的體驗不會變更，記憶體的用量還會大幅下降。 效能也會因此獲得改善。

建議您將上述的類似方法用於報表上的所有視覺效果。 問問自己，需要這個視覺效果中的所有資料嗎？ 是否有任何方式可以進一步篩選視覺效果中顯示的資料量，並將對終端使用者體驗的影響降至最低？ 資料表特別耗費資源。

## <a name="limit-visuals-on-report-pages"></a>限制報表頁面上的視覺效果

上述原則同樣適用於特定報表上的視覺效果數目。 強烈建議您限制特定報表上只顯示必要的視覺效果數目。 鑽研頁面十分適合提供其他詳細資料，而不會將更多視覺效果塞滿報表。  

## <a name="optimize-your-model"></a>最佳化模型

一些最佳做法：

- 盡可能地移除未使用的資料表或資料行。 
- 請避免具有高基數之欄位的相異計數，亦即數百萬個相異值。  
- 請採取步驟，避免具有不必要有效位數和高基數的欄位。 例如，您可以將高度唯一的日期時間值分成個別資料行 (例如月、年、日期等)。 或者，對高精確度欄位使用進位，以降低基數 (例如 13.29889 -> 13.3)。
- 如果可行，請使用整數，而非字串。
- 請留意，DAX 函式 (例如 RANKX) 需要測試資料表中的每個資料列；在最壞的情況下，這些函式會使執行階段和記憶體需求呈指數成長，但資料表大小是線性成長。
- 當透過 DirectQuery 連線至資料來源時，請考慮重新對經常篩選或交叉分析的資料行編製索引。 編製索引可大幅改善報表的回應性。  

如需最佳化 DirectQuery 資料來源的詳細資訊，請參閱 [SQL Server 2016 Analysis Services 中的 DirectQuery](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)。

## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery 和即時連線：了解基礎資料來源效能

在 DirectQuery 或即時連線案例中，當使用者瀏覽 Power BI 報表時，Power BI 會即時將查詢傳送至基礎資料來源。 資料來源傳回查詢資料後，報表便會進行轉譯。 因此，報表效能主要取決於基礎資料來源的效能。

針對這些案例，請務必了解您基礎資料來源的效能。 不同資料來源會有不同工具，其可讓您了解查詢效能。 例如，SQL Server 和 Azure SQL 提供「查詢存放區」，以擷取查詢和其執行階段統計資料的歷程記錄。

根據 DirectQuery 和即時連線所建置的 Power BI 報表進行部署時，請嘗試終端使用者將在 Power BI Desktop 中執行的作業。 如果 Power BI Desktop 中的報表載入速度緩慢，則終端使用者在使用服務時，其載入速度也會緩慢。 

## <a name="directquery-best-practices"></a>DirectQuery 最佳做法

下節描述透過 DirectQuery 連線的一般最佳做法。

### <a name="db-design-guidance"></a>資料庫設計指引

- 盡可能地將計算結果欄和導出量值推送到來源。 與來源越接近，改善效能的可能性越高。
- 最佳化！ 了解您查詢的執行計畫、新增經常篩選資料行的索引等。

### <a name="modeling-guidance"></a>模型指南

- 在 Power BI Desktop 中啟動。
- 避免 [查詢編輯器] 中有複雜的查詢。
- 不要在查詢編輯器中使用相對日期篩選。  
- 一開始保持簡單量值，並以累加方式新增複雜度。
- 避免與計算結果欄和唯一識別碼資料行的關聯性。
- 嘗試對關聯性設定 [採用參考完整性]；在許多情況下，此設定可以大幅改善查詢效能。  

### <a name="general"></a>一般

- 先套用篩選。
- 考慮關閉視覺效果間的互動，這在使用者交叉醒目提示時可降低查詢負載。
- 限制視覺效果數目以及每個視覺效果的資料，如上所述。
- 啟用資料列層級安全性，可能會導致效能大幅變更。 請務必測試您的使用者將採用的不同資料列層級安全性角色。
- 服務會強制執行查詢層級逾時，確保長時間執行的查詢無法獨佔系統資源。 時間超過 225 秒的查詢將會逾時，並導致視覺效果層級錯誤。

## <a name="understand-dashboards-and-query-caches"></a>了解儀表板和查詢快取

載入儀表板時，查詢快取會提供釘選到儀表板的視覺效果。 相反地，瀏覽報表時，會對資料來源即時進行查詢：Power BI 服務 (匯入時) 或您指定的資料來源 (DirectQuery 或即時連線時)。  

> [!NOTE]
> 當您將即時報表磚釘選到儀表板時，它們便不會由查詢快取提供，而是會像報表一樣地運作，並即時對後端核心進行查詢。

正如其名，從查詢快取中擷取資料所提供的效能，會比依賴資料來源更佳且更一致。 利用這項功能的其中一種方式是讓儀表板成為您使用者的第一個登陸頁面。 將常用和經常要求的視覺效果釘選到儀表板。 如此一來，儀表板會成為重要的「第一線防護」，提供容量負載較少的一致效能。 使用者仍然可以按一下報表，以深入探索詳細資料。  
 

針對 DirectQuery 和即時連線，系統會查詢資料來源以定期更新此查詢快取。 根據預設，這在每個小時會發生一次，但您可以在資料集設定中進行設定。 每個查詢快取更新都會將查詢傳送至基礎資料來源，以更新快取。 產生的查詢數目取決於釘選到依賴該資料來源儀表板的視覺效果數。 請注意，如果啟用資料列層級安全性，則會為每個不同的安全性內容產生查詢。 例如，若您的使用者分別屬於兩個不同角色，且他們都擁有不同的資料檢視，則在查詢快取重新整理期間，Power BI 便會產生兩組查詢。 

## <a name="understand-custom-visual-performance"></a>了解自訂視覺效果效能 

請務必以其步調放入每個自訂視覺效果，以確保高效能。 最佳化不佳的自訂視覺效果可能會對整個報表的效能造成負面影響。 

## <a name="deep-dive-into-query-performance-with-sql-profiler-and-power-bi-desktop"></a>深入探討 SQL Profiler 和 Power BI Desktop 的查詢效能

若要深入探討佔用最多時間和資源的視覺效果，您可以將 SQL Profiler 連線至 Power BI Desktop，以取得查詢效能的所有完整檢視。

> [!NOTE]
> Power BI Desktop 支援連線到診斷連接埠。 其他工具可連線到診斷連接埠，並為診斷目的而執行追蹤。 *不支援對模型進行任何變更！對模型進行變更可能會導致損毀以及資料遺失。*

指示如下：
  
1. **安裝 SQL Server Profiler 並執行 Power BI Desktop**

   SQL Server Profiler 是 SQL Server Management Studio 的一部分。

2. **判斷 Power BI Desktop 正在使用的連接埠**

   使用系統管理員權限執行命令提示字元或 PowerShell。 然後，使用 netstat 來尋找 Power BI Desktop 正在用於分析的連接埠：

   `> netstat -b -n`

   例如，輸出應該是應用程式和其已開啟連接埠的一份清單：  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe]

   尋找 msmdsrv.exe 所使用的連接埠，並寫下它，以供稍後使用。 在此情況下，您會使用連接埠 55786。
3. **將 SQL Server Profiler 連線至 Power BI Desktop**

   - 從 [開始]  功能表中，啟動 SQL Server Profiler
   - [檔案]   > [新增追蹤] 
   - 伺服器類型：Analysis Services
   - 伺服器名稱：localhost:[在上面找到的連接埠號碼]
   - 在下一個畫面中，選取 [執行] 
   - 現在 SQL Profiler 為即時，並且主動分析 Power BI Desktop 所傳送的查詢。 
   - 執行查詢時，您可以看到其各自的持續時間和 CPU 時間；使用此資訊，您可以判斷哪些查詢是瓶頸。  

透過 SQL Profiler，您可以識別所需 CPU 時間最長的查詢。 很有可能就是這些查詢造成效能瓶頸。 為了達到持續最佳化，建議您將焦點放在執行這些查詢的視覺效果上。

## <a name="gateway-best-practices"></a>閘道最佳做法

內部部署資料閘道是不錯的工具，可使用內部部署資料來連線 Power BI 服務。 同時，規劃若不佳，也可能會成為報表效能瓶頸。 這特別適用於 DirectQuery/即時連線資料集；其中，所有查詢和查詢回應都會通過閘道。 以下是一些確保高效能閘道的最佳做法： 

- **使用企業模式**，與個人模式相反。
- **閘道的建議硬體規格** - 8 個 CPU 核心、16 GB RAM。
- **設定監視** ‒ 設定閘道電腦的效能監視，以了解閘道是否超載及形成瓶頸。 如需詳細資訊，請參閱[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)。
- **相應增加或向外延展** ‒ 若閘道確實形成瓶頸，請考慮進行相應增加 (亦即將閘道移至具有更多 CPU 和 RAM 且功能更強大的電腦) 或向外延展 (例如將資料集分到不同閘道)。 
- **不同匯入與DirectQuery** ‒ 若您選擇進行向外延展，請考慮區隔負責匯入與負責 DirectQuery 的閘道。

## <a name="network-latency"></a>網路延遲

網路延遲可能會因要求到達 Power BI 服務所需時間增加以及傳遞回應所需時間增加而影響報表效能。 Power BI 中的租用戶會獲指派特定區域。 您可以檢視租用戶的「起始」區域，方法是巡覽至 powerbi.com，並選取右上方的 **?** ， 然後在右上角選擇 [關於 Power BI]  。 租用戶中的使用者存取 Power BI 服務時，他們的要求一律會路由至此區域。 舉例來說，當要求到達 Power BI 服務之後，服務可能會將其他要求傳送至基礎資料來源或閘道，而這些要求也受限於網路延遲。

[Azure Speed Test](http://azurespeedtest.azurewebsites.net/) 這類工具可以指出用戶端與 Azure 區域之間的網路延遲。 一般而言，若要將網路延遲的影響降到最低，請盡量將資料來源、閘道和 Power BI 叢集保留在最接近的位置。 如果網路延遲是問題，則您可以透過將它們放置在虛擬機器上，嘗試將閘道和資料來源放置在更接近 Power BI 叢集的位置。

若要進一步改善網路延遲，請考慮使用 [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/)，其可在用戶端與 Azure 資料中心之間建立更快速、可靠的網路連線。

## <a name="next-steps"></a>後續步驟

- [規劃 Power BI 企業部署](https://aka.ms/pbienterprisedeploy)，以及大規模 Power BI 部署的全面指引
- [SQL Server 2016 Analysis Services 中的 DirectQuery](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)
- [[YouTube] 在 Power BI 中建置快速且可靠的報表](https://www.youtube.com/watch?v=GhiJABR7XX0)
- [[YouTube] Power BI 企業部署](https://www.youtube.com/watch?v=K-zEWICvICM)
