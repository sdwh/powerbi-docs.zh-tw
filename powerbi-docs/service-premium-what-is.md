---
title: Microsoft Power BI Premium 是什麼？
description: Power BI Premium 提供專用的容量，為您的組織，為您提供更可靠的效能與更大的資料磁碟區，而不需要您購買每位使用者授權。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/22/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e5ffa624bf69cf470aade076c80ac37028a55456
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565269"
---
# <a name="what-is-power-bi-premium"></a>什麼是 Power BI Premium？

Power BI Premium 提供專用和增強的資源，來執行您的組織的 Power BI 服務。 例如：

- 提升規模和效能
- 彈性的容量的授權
- 自助和企業 BI 整合
- 擴充使用 Power BI 報表伺服器的內部部署 BI
- 依區域 （多地理位置） 的資料存放區支援
- 與任何人共用資料，而不必購買每位使用者授權

這篇文章不是實際上提供有關 Power BI premium-每一項功能的詳細資料，它只接觸到的表面。 必要時，會提供更詳細的資訊與其他文章連結。

## <a name="subscriptions-and-licensing"></a>訂用帳戶和授權

Power BI Premium 是租用戶層級 Office 365 訂用帳戶可用的 SKU （庫存單位） 的兩個系列：

- **EM** Sku (EM1-EM3) 內嵌，需要每年的承諾用量，依按月計費。
- **P** Sku (P1-P3) 如需內嵌和企業功能，需要每月或每年承諾用量，每月結算，和包含安裝 Power BI 報表伺服器內部部署授權。

替代方法是購買**Azure Power BI Embedded**訂用帳戶，後者具有單一**A** (A1-A6) SKU 系列，用於內嵌和容量測試之用。 所有 Sku 都提供建立容量的 v 核心，但 EM Sku 僅能用於較小的規模內嵌。 EM1、 EM2，A1 和 A2 Sku 具有少於四個 v 核心不會執行專用的基礎結構上。

雖然這篇文章的焦點是 P Sku，所述的許多無關也 A Sku。 相較於 Premium 訂用帳戶 Sku、 Azure Sku 需要沒有綁約時間及每小時計費。 它們提供完整的彈性，啟用相應增加、 相應減少、 暫停、 繼續及刪除。 

Azure 的 Power BI Embedded 多半不屬於範圍在本文中，但它所述[測試方法](service-premium-capacity-optimize.md#testing-approaches)做為實際且經濟的選項，測試和測量工作負載最佳化的 Premium 容量文章一節。 若要深入了解 Azure Sku，請參閱[Azure Power BI Embedded 文件](https://azure.microsoft.com/services/power-bi-embedded/)。

### <a name="purchasing"></a>購買

由系統管理員在 Microsoft 365 系統管理中心購買 power BI Premium 訂用帳戶。 具體來說，只有 Office 365 全域管理員或計費系統管理員可以購買的 Sku。 當購買，租用戶會收到相對數目的 v 核心可指派給容量，稱為*v 核心集區*。 例如，購買 P3 SKU 可提供 32 個 v 核心與租用戶。 若要進一步了解，請參閱[如何購買 Power BI Premium](service-admin-premium-purchase.md)。

## <a name="dedicated-capacities"></a>專用的容量

利用 Power BI Premium，您可享有*專用容量*。 相較於共用容量中工作負載與其他客戶共用計算資源執行的地方，專用的容量是由組織的獨佔使用。 其具有專用的計算資源可提供裝載內容的可靠且一致效能隔離。 

工作區位於容量。 每個 Power BI 使用者都有個人的工作區，稱為**我的工作區**。 可以建立額外的工作區，以啟用共同作業和部署，以及這些值稱為**應用程式工作區**。 預設工作區，包括個人工作區，會建立在共用的容量。 當您有進階容量時，我的工作區和應用程式工作區可以指派給 Premium 容量。

### <a name="capacity-nodes"></a>容量的節點

中所述[訂用帳戶和授權](#subscriptions-and-licensing)區段中，有兩個 Power BI Premium SKU 系列：**EM**並**P**。所有 Power BI Premium Sku 都可用作容量*節點*、 每個均代表處理器、 記憶體和儲存體所組成的資源集數量。 除了資源外，每個 SKU 都有每秒的 DirectQuery 和即時連線的連線數目操作的限制，和平行的模型數目會重新整理。

處理固定數目的 v 核心後, 端與前端之間平均分配，即可達成。

**後端 v 核心**負責核心 Power BI 功能，包括查詢處理、 快取管理、 執行 R services、 模型重新整理、 自然語言處理 （問與答），以及伺服器端轉譯的報表和影像。 後端 v 核心會指派給主機模型，也就是作用中的資料集的固定的主要使用的記憶體數量。

**前端 v 核心**負責 web 服務、 儀表板和報表文件管理、 存取權限管理、 排程、 Api、 上傳和下載，並通常用於與使用者相關的所有項目體驗。

若要設定儲存體**100 TB，每個容量節點**。

資源和每個進階 SKU 的限制 （和對等程式碼大小 SKU） 下表所述：

| 容量的節點 | V 核心總數 | 後端 V 核心 | RAM (GB) | 前端 V 核心 | （每秒） 的 DirectQuery/即時連線 | 模型重新整理平行處理原則 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="capacity-workloads"></a>容量的工作負載

容量的工作負載是向使用者提供的服務。 根據預設，Premium 和 Azure 容量支援只有資料集的工作負載與執行 Power BI 查詢相關聯。 無法停用資料集的工作負載。 您可以啟用其他的工作負載[AI （認知服務）](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/)，[資料流程](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)，並[編頁報表](paginated-reports-save-to-power-bi-service.md)。 Premium 的訂用帳戶僅支援這些工作負載。 

每個額外的工作負載可讓您設定可供工作負載的記憶體上限 （以總可用記憶體的百分比表示）。 記憶體的最大的預設值取決於 SKU。 您可以使用它們時，啟用這些其他工作負載，以最大化您的容量可用的資源。 而且，您可以變更設定，只有在您決定的預設設定時，才不符合您的容量資源需求的記憶體。 可啟用及設定適用於容量的容量系統管理員使用的工作負載**容量設定**中[系統管理員入口網站](service-admin-portal.md)或透過[容量 REST Api](https://docs.microsoft.com/rest/api/power-bi/capacities)。  

![啟用工作負載](media/service-admin-premium-workloads/admin-portal-workloads.png)

若要進一步了解，請參閱[設定工作負載，進階容量中](service-admin-premium-workloads.md)。 

### <a name="how-capacities-function"></a>如何容量函式

在所有的時間，Power BI 服務可讓最佳容量時使用資源不超過容量加諸的限制。

容量的作業會分類為 「*互動式*或是*背景*。 互動式作業包括轉譯要求和回應使用者互動 （篩選、 問與答查詢等）。 一般而言，匯入模型查詢時，記憶體資源密集型查詢 DirectQuery 和即時連線的模型是需要大量 CPU 的。 背景作業包含資料流程，並匯入模型重新整理，和儀表板查詢快取。

請務必了解，互動式作業一律優先於背景作業，以確保最可能的使用者體驗。 如果有資源不足，背景作業加入佇列以便處理時的資源釋出。 背景作業，例如資料集重新整理，可能是由 Power BI 服務已停止中間的程序，並新增至佇列。

匯入模型必須是完全載入記憶體，因此它們可以進行查詢，或重新整理。 Power BI 服務會管理使用使用方式的複雜演算法，以確保充分使用可用的記憶體，而且可能會導致過度認可容量的記憶體：雖然有可能的容量來存放許多匯入模型 (多達 100 TB 每 Premium 容量)，其結合的磁碟儲存體超過支援的記憶體 （與額外的記憶體和所需的查詢重新整理），然後所有無法載入它們寫入記憶體中相同的時間。

因此，匯入模型就會載入並從根據使用的記憶體中移除。 匯入模型時查詢的 （互動式作業） 和尚不在記憶體中，或載入時重新整理 （背景作業）。

模型，以從記憶體移除就所謂*收回*。 這是 Power BI 根據模型的大小可以快速地執行作業。 如果容量在未發生任何記憶體不足的壓力，則模型會直接載入到記憶體，並保留在。 不過，當記憶體不足，無法載入模型可用時，Power BI 服務必須先釋出記憶體。 它藉由偵測已成為非作用中搜尋模型，在過去三分鐘內未使用的模型會釋放記憶體\[ [1](#endnote-1)\]，並接著將收回。 如果不有任何非作用中的模型，以收回，Power BI 服務會試圖收回背景作業載入的模型。 最後的手段，在 30 秒的失敗嘗試後\[ [1](#endnote-1)\]，是要讓互動式作業失敗。 在此情況下，報表使用者會收到通知的失敗的建議，請稍後再試。 在某些情況下，模型可能是因為服務作業的記憶體中卸載。

它是特別要強調的資料集收回是正常且符合預期的行為。 它會致力於最大化記憶體使用量，透過載入和卸載其合併的大小可能會超過可用記憶體的模型。 這是根據設計，以及報表使用者完全透明。 高收回率並不一定代表過去資源容量。 不過，如果查詢或重新整理回應性高的收回速率因為發生問題，他們可以成為問題。

匯入模型的重新整理永遠會耗用大量記憶體，因為模型必須載入到記憶體。 需要處理額外的記憶體。 完整的重新整理可以使用大約兩倍的模型所需的記憶體數量。 這可確保模型可進行查詢時，即使正在處理，因為查詢會傳送到現有的模型，直到重新整理已完成，而且新的模型資料可供使用。 累加式重新整理都會需要較少的記憶體和更快，無法完成，因此可大幅降低容量資源的壓力。 重新整理也可以是需要大量 CPU 的模型，特別是具有複雜的 Power Query 轉換或導出的資料表/資料行的複雜或大型的資料表為基礎。

重新整理，例如查詢，需要模型載入記憶體。 如果沒有足夠記憶體，Power BI 服務會嘗試收回非作用中的模型，並不可行 （為所有模型都是作用中），如果重新整理作業已排入佇列。 重新整理會通常需要大量 CPU 的即使，而不是查詢。 基於這個理由，有的並行重新整理，設定為 1.5 x 的後端 v 核心，無條件進位數目數目的容量限制。 如果有太多的並行重新整理，排程的重新整理將會排入佇列。 這些情況下發生時，花較長時間重新整理完成。 依需求重新整理，例如那些由使用者要求所觸發或 API 呼叫將會重試三次\[ [1](#endnote-1)\]。 如果仍然沒有足夠的資源，即會失敗的重新整理。

一節的注意事項：   
<a name="endnote-1"></a>\[1\]有所變更。

### <a name="regional-support"></a>區域的支援

當建立新的容量、 Office 365 全域管理員和 Power BI 服務系統管理員可以指定將位於工作區指派給容量的區域。 這就所謂**Multi-geo**。 使用多地理位置，組織可以符合資料落地需求是將內容部署到資料中心在特定區域中，即使它是不同於 Office 365 訂用帳戶所在的區域。 若要進一步了解，請參閱[Power BI premium 的多地理位置支援](service-admin-premium-multi-geo.md)。

### <a name="capacity-management"></a>容量管理

管理 Premium 容量牽涉到建立或刪除容量、 指派系統管理員，將工作區指派、 設定工作負載，監視及進行調整，最佳化處理能力效能。 

Office 365 全域系統管理員和 Power BI 服務系統管理員可以從可用的 v 核心，建立進階容量，或修改現有的 Premium 容量。 建立容量時，未指定容量大小和地理區域，並指派至少一個容量管理員。 

容量建立時，可在中完成大部分的系統管理工作[管理入口網站](service-admin-portal.md)。

![管理入口網站](media/service-premium-what-is/premium-admin-portal.png)

容量管理員可將工作區指派給容量、 管理使用者權限，並指派其他系統管理員。 容量管理員也可以設定工作負載，調整記憶體配置，並視需要重新啟動的容量，重設時的容量多載的作業。

![管理入口網站](media/service-premium-what-is/premium-admin-portal-mgmt.png)

容量管理員可以也確保容量可以順利執行。 應用程式可以監視容量健全狀況權限在管理入口網站中，或使用 Premium 容量計量應用程式。

若要了解更多關於建立容量、 指派系統管理員，以及指派工作區，請參閱[管理 Premium 容量](service-premium-capacity-manage.md)。 若要深入了解角色，請參閱[系統管理員角色與 Power BI 相關](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)。

### <a name="monitoring"></a>監視

監視 Premium 容量提供系統管理員了解如何執行容量。 使用管理入口網站也可以監視容量和[Power BI Premium 容量度量的應用程式](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics)。

在入口網站中監視提供高層級的度量，表示放置的載入和使用您的容量，平均值過去七天的資源的快速檢視。 

![管理入口網站](media/service-premium-what-is/premium-admin-portal-health.png)

**Power BI Premium 容量計量**應用程式會提供如何執行您的容量最深入資訊。 應用程式提供高層級的儀表板及更詳細的報表。

![度量應用程式儀表板](media/service-admin-premium-monitor-capacity/app-dashboard.png)

從應用程式的儀表板中，您可以按一下以開啟的深入報告的計量資料格。 報表會提供深入的計量和篩選功能，以向下鑽研最重要的資訊在您要保留順暢執行您的容量。

![定期的尖峰，查詢的等候計數表示潛在的 CPU 飽和的時間](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

若要深入了解監視容量，請參閱[在 Power BI 管理入口網站中監視](service-admin-premium-monitor-portal.md)並[使用 Power BI Premium 容量度量的應用程式監視](service-admin-premium-monitor-capacity.md)。

### <a name="optimizing-capacities"></a>最佳化的容量

充分利用您的容量是確保使用者取得效能的關鍵，而且您正在為 Premium 上的投資最大價值。 藉由監視關鍵計量，系統管理員可以判斷如何進行疑難排解的瓶頸，並採取必要措施。 若要進一步了解，請參閱[最佳化的進階容量](service-premium-capacity-optimize.md)並[Premium 容量案例](service-premium-capacity-scenarios.md)。

### <a name="capacities-rest-apis"></a>容量 REST Api

Power BI REST Api 包含一組集合[容量 Api](https://docs.microsoft.com/rest/api/power-bi/capacities)。 與 Api，管理員可以透過程式設計方式管理您的進階容量，包括啟用和停用工作負載，將工作區指派給容量，以及其他的許多層面。

## <a name="large-datasets"></a>大型資料集

根據 SKU，Power BI Premium 支援最多的 Power BI Desktop (.pbix) 模型檔案上傳**10GB**的大小。 載入時，模型接著可以發行至工作區指派給進階容量。 資料集可以再重新整理，最多**12GB**的大小。

### <a name="size-considerations"></a>大小的考量

大型模型可能需要大量資源。 您應該有任何大於 1 GB 的模型至少要有 P1 SKU。 雖然將大型模型發佈至工作區受到最 A3 的 A Sku 無法重新整理它們的工作，則不會。

下表描述各種 .pbix 大小的建議 SKU：

   |SKU  |.pbix 大小   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3、P4、P5    | 最多 10 GB   |

Power BI Embedded A4 SKU 等同於 P1 SKU、A5 = P2 及 A6 = P3。 請注意，將大型模型發行到 A 和 EM SKU，可能會傳回錯誤，且為非專屬於共用容量中模型大小限制的錯誤。 A 和 EM SKU 中，大型模型的重新整理錯誤，很可能指向逾時。 

您的.pbix 檔案中的資料表示*高度壓縮狀態*。 載入至記憶體時，資料可能會展開多次，而且從該處，在資料重新整理期間，資料可能會再展開幾次。

排程的重新整理大型資料集可以花很長的時間，並需要大量資源。 請務必太多重疊重新整理排程。 建議您使用[累加式重新整理](service-premium-incremental-refresh.md)設定，因為它是更快、 更可靠，並且會耗用較少的資源。

如果已在上次使用資料集的一段時間，大型資料集的初始報表負載可能需要很長的時間。 較長載入之報表的載入列會顯示載入進度。

更進階容量中的每個查詢的記憶體和時間條件約束時，建議您可以使用篩選和交叉分析篩選器來限制顯示只是必要的視覺效果。

## <a name="incremental-refresh"></a>累加式重新整理

累加式重新整理提供擁有和維護大型資料集，Power BI Premium 中的不可或缺的一部分。 累加式重新整理有許多好處，例如，重新整理快因為只有資料，有變更的需要重新整理。 重新整理會更可靠，因為它是不必要維持長時間執行變動性的資料來源的連線。 因為較少的資料重新整理會減少整體的記憶體和其他資源的耗用量，就會減少資源耗用量。 累加式重新整理原則定義在**Power BI Desktop**，並發佈至進階容量中的工作區時套用。 

![重新整理詳細資料](media/service-premium-incremental-refresh/refresh-details.png)

若要進一步了解，請參閱[累加式重新整理 Power BI Premium 中](service-premium-incremental-refresh.md)。

## <a name="paginated-reports"></a>編頁報表

P1-P3 和 A4_A6 Sku 上支援的分頁的報表是以 SQL Server Reporting Services 中的報表定義語言 (RDL) 技術為基礎。 RDL 技術為基礎，而它不是 Power BI 報表伺服器，也就是一個可下載的報告平台，以您可以安裝在內部，使用 Power BI Premium 也包含相同。 編頁的報表會經過格式化，以容納也可以列印或共用的頁面。 資料會顯示在資料表中，即使資料表跨越多個頁面。 使用免費[ **Power BI 報表產生器**](https://go.microsoft.com/fwlink/?linkid=2086513) Windows 桌面應用程式，使用者作者編頁報告，並將其發行至服務。

在 Power BI Premium 中，Paginated 報表是使用系統管理員入口網站必須啟用容量的工作負載。 容量管理員可以啟用，而且然後整體記憶體資源的容量的百分比指定的記憶體數量。 不同於其他類型的工作負載，Premium 會執行分頁的報表中包含的空間容量內。 指定的工作負載作用中，會使用此工作區的記憶體上限。 預設值為 20%。 

若要進一步了解，請參閱[編頁報表，Power BI Premium 中的](paginated-reports-report-builder-power-bi.md)。 若要深入了解啟用 Paginated 報表工作負載，請參閱[設定工作負載](service-admin-premium-workloads.md)。

## <a name="power-bi-report-server"></a>Power BI 報表伺服器
 
使用 Power BI Premium，Power BI 報表伺服器隨附*內部*使用 web 入口網站的報表伺服器。 您可以建置您的 BI 環境內部，並發佈您的組織防火牆後面的報表。 報表伺服器可讓使用者存取豐富的互動式和 SQL Server Reporting Services 的企業報表功能。 使用者可以瀏覽視覺化資料，並快速找出模式以更好、 更快做出決策。 報表伺服器會提供您自己專屬的控管。 時的時候 Power BI 報表伺服器可讓您輕鬆地移轉至雲端，其中您的組織可以充分利用所有的 Power BI Premium 功能。

若要進一步了解，請參閱[Power BI 報表伺服器](report-server/get-started.md)。

## <a name="unlimited-content-sharing"></a>無限制的內容共用

Premium 中，任何人，不論它們是您組織內部或外部可以檢視 Power BI 內容包括分頁和互動式報表，而不必購買個別的授權。 

![內容共用](media/service-premium-what-is/premium-sharing.png)

Premium 會啟用廣泛發佈 Pro 使用者的內容，而不需要 Pro 授權的收件者檢視內容。 內容創作者的需要 pro 授權。 建立者連接到資料來源，模型資料，並建立報表和儀表板，會封裝為工作區的應用程式。 

若要進一步了解，請參閱[Power BI 授權](service-admin-licensing-organization.md)。

## <a name="tool-connectivity-preview"></a>工具連線 （預覽）

實際上，經過實證的 Microsoft 企業**Analysis Services Vertipaq 引擎**提供 Power BI 資料集。 Analysis Services 會提供可程式性，並透過用戶端程式庫和 Api 支援的開放式標準 XMLA 通訊協定支援的用戶端應用程式和工具。 目前，Power BI Premium 的資料集的支援*唯讀*作業，從 Microsoft 和協力廠商用戶端應用程式和工具，透過**XMLA 端點**。 

Microsoft 工具，例如 SQL Server Management Studio 和 SQL Server Profiler 和第三方應用程式，例如 DAX Studio 和資料視覺效果應用程式，可以連接到，並使用 XMLA、 DAX、 MDX、 Dmv、 和追蹤的事件查詢優質資料集。 

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)

若要進一步了解，請參閱[連接到資料集與用戶端應用程式和工具](service-premium-connect-tools.md)。

## <a name="acknowledgements"></a>通知

Peter Myers、 資料平台 MVP 和獨立 BI 專家[位元解決方案](https://www.bitwisesolutions.com.au/)，Microsoft Power BI 客戶諮詢團隊 (CAT)，而 這篇文章主要參與者。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [管理 Premium 容量](service-premium-capacity-manage.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

||||||
