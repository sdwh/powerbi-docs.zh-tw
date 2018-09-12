---
title: Power BI 效能最佳做法
description: 本文提供如何在 Power BI 中建置快速且可靠報表的指引
author: MarkMcGeeAtAquent
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: kfile
LocalizationGroup: Reports
ms.openlocfilehash: 08ead2570602538218085327c6d385c36e0d7e8c
ms.sourcegitcommit: 8bad5ed58e9e406aca53996415b1240c2972805e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44343315"
---
# <a name="power-bi-performance-best-practices"></a>Power BI 效能最佳做法 
本文提供如何在 Power BI 中建置快速且可靠報表的指引。  

## <a name="use-filters-to-limit-report-visuals-to-display-only-whats-needed"></a>使用篩選來限制報表視覺效果只顯示需要的項目 

視覺效果所需顯示的資料越多，要載入的視覺效果就越慢。 雖然此原則看起來很明顯，但卻很容易忘記。 例如：假設您有大型資料集。 此外，您使用資料表的資料表來建置報表。 終端使用者會在頁面上使用交叉分析篩選器來取得想要的資料列，而且通常只會對數十個資料列感興趣。

常見的錯誤是不篩選資料表的預設檢視，即所有 100M+ 個資料列。 在每次重新整理時，都必須將這些資料列的資料載入至記憶體，並進行解壓縮。 這已建立大量記憶體載入。 解決方案：減少資料表使用「前 N 個」篩選所顯示的最大項目數。 最大項目數可能大於使用者需要的項目數 (例如 10,000)。 因此，終端使用者體驗不會變更，但報表的記憶體使用量會卸除多個數量級，並據以改善效能。

強烈建議將與上述類似的方法用於報表上的所有視覺效果。 問問自己，需要這個視覺效果中的所有資料嗎？ 有方式可以進行篩選，讓視覺效果中顯示較少的資料量而且對終端使用者體驗的影響最低嗎？ 請注意，特別是資料表可能十分耗費資源。 
 
## <a name="limit-visuals-on-report-pages"></a>限制報表頁面上的視覺效果 
上述原則同樣適用於特定報表上的視覺效果數目。 強烈建議您限制特定報表上只顯示必要的視覺效果數目。 鑽研頁面十分適合提供其他詳細資料，而不會將更多視覺效果塞滿報表。  
 
## <a name="optimize-your-model"></a>最佳化模型 
一些最佳做法： 
 
- 可能的話，請移除未使用的資料表或資料行。 
- 請避免具有高基數之欄位的相異計數，即數百萬個相異值。  
- 請採取步驟，避免具有不必要有效位數和高基數的欄位。 例如，您可以將高唯一日期時間值分割成個別資料行 (例如月、年、日期等等)。或者，如果可行，請對高有效位數欄位使用捨入，以減少基數 (例如 13.29889 -> 13.3)。 
- 如果可行，請使用整數，而非字串。 
- 請留意需要測試資料表中每個資料列的 DAX 函式 (例如 RANKX)；在最壞的情況下，這些函式會使執行階段和記憶體需求呈指數成長，但資料表大小是線性成長。 
- 透過 DirectQuery 連線至資料來源時，請考慮重新對經常篩選或交叉分析的資料行編製索引，這將大幅改善報表回應性。  
 

如需最佳化 DirectQuery 資料來源的詳細指引，請參閱 [SQL Server 2016 Analysis Services 中的 DirectQuery](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/)。 
 
## <a name="directquery-and-live-connection-understand-underlying-data-source-performance"></a>DirectQuery 和即時連線：了解基礎資料來源效能 

在 DirectQuery 或即時連線案例中，使用者瀏覽 Power BI 報表時，Power BI 會即時將查詢傳送至基礎資料來源。 傳回資料來源和查詢資料之後，接著會轉譯報表。 因此，在這些情況下，您的報表效能主要取決於基礎資料來源的效能。

在這些情況下，務必了解您基礎資料來源的效能。 不同的資料來源會有不同的工具可了解查詢效能。 例如，SQL Server 和 Azure SQL 提供「查詢存放區」，以擷取查詢和其執行階段統計資料的歷程記錄。

根據經驗，部署根據 DirectQuery 和即時連線所建置的 Power BI 報表時，請嘗試終端使用者將在 Power BI Desktop 中執行的作業。 如果 Power BI Desktop 中的報表載入速度緩慢，則幾乎確定在終端使用者的服務中載入速度也會緩慢。 
 
## <a name="directquery-best-practices"></a>DirectQuery 最佳做法 
下節描述透過 DirectQuery 連線的一般最佳做法。
  
### <a name="db-design-guidance"></a>資料庫設計指引 
- 如果可行，請將計算結果欄和量值推送至來源；越接近來源，效能的可能性就越高。 
- 最佳化！ 了解您查詢的執行計畫、新增經常篩選之資料行的索引等等。 

### <a name="modeling-guidance"></a>模型指南 
- 在 Power BI Desktop 中啟動。 
- 避免 [查詢編輯器] 中有複雜的查詢。 
- 請勿在 [查詢編輯器] 中使用相對資料篩選。  
- 一開始保持簡單量值，並以累加方式新增複雜度。 
- 避免與計算結果欄和唯一識別碼資料行的關聯性。 
- 嘗試對關聯性設定 [採用參考完整性]；在許多情況下，這可以大幅改善查詢效能。  

### <a name="general"></a>一般 
- 先套用篩選。 
- 請考慮關閉視覺效果之間的互動，這在使用者交叉強調顯示時可降低查詢負載。 
- 限制視覺效果數目以及每個視覺效果的資料，如上所述。 
- 啟用資料列層級安全性，可能會導致效能大幅變更。 請務必測試您的使用者將採用的不同資料列層級安全性角色。 
- 請注意，服務會強制執行查詢層級逾時，確保長時間執行的查詢無法獨佔系統資源。 時間超過 225 秒的查詢將會逾時，並導致視覺效果層級錯誤。 

## <a name="understanding-dashboards-and-query-caches"></a>了解儀表板和查詢快取 
載入儀表板時，查詢快取會提供釘選到儀表板的視覺效果。 相反地，瀏覽報表時，會對資料來源即時進行查詢：Power BI 服務 (匯入時) 或您指定的資料來源 (DirectQuery 或即時連線時)。  
 
> [!NOTE]
> 當您將即時報表磚釘選到儀表格時，無法從查詢快取提供它們 - 而且它們會像報表一樣地運作，並即時對後端核心進行查詢。 
 

正如其名，從查詢快取中擷取資料所提供的效能，會比依賴資料來源更佳且更一致。 利用這項功能的其中一種方式是讓儀表板成為您使用者的第一個登陸頁面。 將常用和高度要求的視覺效果釘選到儀表板。 如此一來，儀表板會成為重要的「第一線防護」，提供容量負載較少的一致效能。 使用者仍然可以按一下報表，以深入探索詳細資料。  
 

請注意，針對 DirectQuery 和即時連線，會查詢資料來源來定期更新此查詢快取。 根據預設，這會每個小時發生，但它可以設定於資料集設定中。 每個查詢快取更新都會將查詢傳送至基礎資料來源，以更新快取。 產生的查詢數目取決於釘選到依賴該資料來源之儀表板的視覺效果數目。 請注意，如果啟用資料列層級安全性，則會為每個不同的安全性內容產生查詢。 例如，如果您有使用者所屬的兩個不同角色，而且資料有兩個不同的檢視，則在查詢快取重新整理期間，會產生兩組查詢。 
 
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

   使用系統管理員權限執行命令提示字元或 PowerShell，以及使用 netstat 找到 Power BI Desktop 用於分析的連接埠：

   `> netstat -b -n` 

   例如，輸出應該是應用程式和其已開啟連接埠的一份清單：  

   `TCP    [::1]:55786            [::1]:55830            ESTABLISHED`

   [msmdsrv.exe] 

   尋找 msmdsrv.exe 所使用的連接埠，並寫下它，以供稍後使用。 在此情況下，您可以使用連接埠 55786。 
3. **將 SQL Server Profiler 連線至 Power BI Desktop** 

   - 從 [開始] 功能表中，啟動 SQL Server Profiler 
   - [檔案] > [新增追蹤] 
   - 伺服器類型：Analysis Services 
   - 伺服器名稱：localhost:[在上面找到的連接埠號碼] 
   - 在下一個畫面中，選取 [執行] 
   - 現在 SQL Profiler 為即時，並且主動分析 Power BI Desktop 所傳送的查詢。 
   - 執行查詢時，您可以看到其各自的持續時間和 CPU 時間；使用此資訊，您可以判斷哪些查詢是瓶頸。  

透過 SQL Profiler，您可以識別佔用最長 CPU 時間的查詢，其接著可能就是效能瓶頸。 然後，執行這些查詢的視覺效果應該會是持續最佳化的焦點。 

## <a name="gateway-best-practices"></a>閘道最佳做法 

內部部署資料閘道是不錯的工具，可使用內部部署資料來連線 Power BI 服務。 同時，規劃若不佳，也可能會成為報表效能瓶頸。 這特別適用於 DirectQuery/即時連線資料集；其中，所有查詢和查詢回應都會通過閘道。 以下是一些確保高效能閘道的最佳做法： 
 
- **使用企業模式**，與個人模式相反。 
- **閘道的建議硬體規格** - 8 個 CPU 核心、16 GB RAM. 
- **設定監視** - 設定閘道電腦的效能監視可了解閘道是否變成超載以及變成瓶頸。 如需詳細資訊，請參閱[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)。
- **相應增加或相應放大** - 如果閘道確實成為瓶頸，則請考慮進行相應增加 (亦即，將閘道移至具有更多 CPU 和 RAM 的功能更強大電腦) 或相應放大 (例如，將資料集分割為不同閘道)。 
- **不同匯入與DirectQuery** - 如果是相應放大，請考慮區隔負責匯入的閘道與負責 DirectQuery 的閘道。 
 
## <a name="network-latency"></a>網路延遲 
網路延遲可能會因要求到達 Power BI 服務所需時間增加以及傳遞回應所需時間增加而影響報表效能。 Power BI 中的租用戶會獲指派特定區域。 您可以檢視租用戶的「起始」區域，方法是巡覽至 powerbi.com，並選取右上方的 **?**， 然後選取 [關於 Power BI]。 租用戶中的使用者存取 Power BI 服務時，其要求一律會路由傳送至此區域。 要求到達 Power BI 服務之後，服務可能會接著將其他要求傳送至基礎資料來源或閘道 (舉例來說)，而這些要求也受限於網路延遲。 

[Azure Speed Test](http://azurespeedtest.azurewebsites.net/) 這類工具可以指出用戶端與 Azure 區域之間的網路延遲。 一般而言，若要將網路延遲的影響降到最低，請盡量將資料來源、閘道和 Power BI 叢集保留在最接近的位置。 如果網路延遲是問題，您可以嘗試放置閘道和資料來源，使其更接近 Power BI 叢集，而方法是將它們放置在虛擬機器上。 

若要進一步改善網路延遲，請考慮使用 [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/)，其可在用戶端與 Azure 資料中心之間建立更快速、可靠的網路連線。 

## <a name="next-steps"></a>後續步驟
- [規劃 Power BI 企業部署](https://aka.ms/pbienterprisedeploy)，以及大規模 Power BI 部署的全面指引 
- [SQL Server 2016 Analysis Services 中的 DirectQuery](https://blogs.msdn.microsoft.com/analysisservices/2017/04/06/directquery-in-sql-server-2016-analysis-services-whitepaper/) 
- [[YouTube] 在 Power BI 中建置快速且可靠的報表](https://www.youtube.com/watch?v=GhiJABR7XX0) 
- [[YouTube] Power BI 企業部署](https://www.youtube.com/watch?v=K-zEWICvICM)  
 
 
