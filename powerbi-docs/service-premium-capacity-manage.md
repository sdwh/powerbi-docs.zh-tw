---
title: 管理 Microsoft Power BI Premium 容量
description: 描述 Power BI Premium 容量的管理工作。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565233"
---
# <a name="managing-premium-capacities"></a>管理 Premium 容量

管理 Power BI Premium，牽涉到建立、 管理和監視 Premium 容量。

## <a name="creating-and-managing-capacities"></a>建立及管理容量

**容量設定**的 Power BI 管理入口網站的頁面會顯示購買的 v 核心和可用的 Premium 容量的數目。 頁面可讓 Office 365 全域管理員或 Power BI 服務系統管理員來建立進階容量，從可用的 v 核心，或修改現有的 Premium 容量。

在建立進階容量時，系統管理員必須定義：

- 容量名稱 （租用戶內是唯一的）。
- 容量 admin(s)。
- 容量大小。
- 資料存放區的區域。

必須指派至少一個容量管理員。 使用者指派為容量管理員可以：

- 將工作區指派給容量。
- 管理使用者的權限，以新增額外的容量管理員或具有指派權限 （若要讓他們能夠將工作區指派給容量） 的使用者。
- 管理工作負載，來設定用於分頁的報表及資料流程工作負載的最大記憶體使用量。
- 重新啟動的容量，以重設所有的作業，因為系統超載。

容量管理員無法存取工作區內容，除非明確指派在工作區的權限。 它們也不需要所有的 Power BI 管理區域的存取權 （除非明確指派） 例如使用量計量、 稽核記錄檔或租用戶設定。 重要的是，容量管理員沒有權限來建立新的容量，或調整現有的容量。 系統管理員會指派每個容量為基礎，確保他們可以只檢視和管理指派給容量。

可用的 SKU 選項清單，這會受到可用的 v 核心集區中的數目，從選取容量大小。 就可以從集區，可以從其中一個來源建立多個容量，或購買更多的 Sku。 比方說，P3 SKU （32 個 v 核心） 無法用來建立三個的容量： 一個 P2 （16 個 v 核心），和兩個 P1 （2 x 8 個 v 核心）。 提升的效能和規模可藉由建立較小的大小調整大小的容量，如中所述[最佳化 Premium 容量](service-premium-capacity-optimize.md)文章。 下圖顯示範例設定在虛構的 Contoso 組織，五個的 Premium 容量所組成 (P1 和 2 x 3 x P3) 與每個包含的應用程式工作區，並在共用容量中的數個工作區。

![在虛構的 Contoso 組織範例設定](media/service-premium-capacity-manage/contoso-organization-example.png)

進階容量可以指派給稱為多地理位置的 Power BI 租用戶住家所在區域以外的區域中。 多地理位置提供定義您的 Power BI 內容所在的地理區域內的哪個資料中心的系統管理控制權。 是合乎常理的多地理位置部署通常是針對企業或政府合規性，而不是效能和規模。 報表和儀表板載入仍然包含中繼資料的主要區域的要求。 若要進一步了解，請參閱[Power BI premium 的多地理位置支援](service-admin-premium-multi-geo.md)。

Power BI 服務系統管理員和 Office 365 全域系統管理員可以修改進階容量。 具體來說，他們可以：

- 變更容量大小，以相應增加或相應減少資源。
- 新增或移除容量管理員。
- 新增或移除具有指派權限的使用者。
- 新增或移除額外的工作負載。
- 變更區域。

指派權限，才能將工作區指派給特定的 Premium 容量。 權限可以授與整個組織、 特定使用者或群組。

根據預設，Premium 容量會支援與執行 Power BI 查詢相關聯的工作負載。 Premium 容量也支援其他的工作負載：**AI （認知服務）** ，**編頁報表**，以及**資料流程**。 每個工作負載需要設定可供工作負載的記憶體上限 （以總可用記憶體的百分比表示）。 請務必了解可能影響增加最大記憶體配置，可裝載的作用中模型的數目和重新整理的輸送量。 

記憶體以動態方式配置給資料流程，但以靜態方式配置給分頁報表。 靜態配置的最大記憶體的原因是已編頁的報表執行受保護的自主空間的容量內。 設定分頁報表的記憶體，因為它會減少可用的記憶體載入模型時請務必小心。 若要進一步了解，請參閱[預設記憶體設定](service-admin-premium-workloads.md#default-memory-settings)。

刪除 Premium 容量可能並不會刪除其工作區和內容。 相反地，它將任何指派的工作區移至共用容量。 不同的區域中建立的 Premium 容量時，工作區會移至共用容量的主要區域中。

### <a name="assigning-workspaces-to-capacities"></a>將工作區指派給容量

工作區可以指派給進階容量在 Power BI 管理入口網站或應用程式工作區中**工作區**窗格。

容量管理員，以及 Office 365 全域系統管理員或 Power BI 服務系統管理員，可以大量指派工作區，在 Power BI 系統管理員入口網站中。 大量指派可以套用至：

- **使用者的工作區**-這些包括個人的工作區的使用者所擁有的所有工作區指派給 Premium 容量。 已指派給不同的 Premium 容量時，這將包含工作區重新的指派。 此外，使用者也會指派工作區指派權限。

- **特定工作區**
- **整個組織的工作區**-包括個人的工作區的所有工作區指派給 Premium 容量。 工作區指派權限時，會指定所有目前和未來的使用者。 不建議這種方法。 最好使用更具針對性的方法。

工作區可以利用加入至進階容量**工作區**窗格提供使用者的工作區管理員，而且有指派權限。

![使用 [工作區] 窗格工作區指派給進階容量](media/service-premium-capacity-manage/assign-workspace-capacity.png)

工作區系統管理員可以移除從容量 （以共用的容量） 的工作區，而不需要指派權限。 有效地移除專用容量的工作區時，重新放置工作區到共用的容量。 請注意，從 Premium 容量移除工作區可能會有負面的後果，導致，例如，共用的內容變成無法使用 Power BI 免費授權的使用者或暫停排定的重新整理在超過支援的額度時藉由共用容量。

在 Power BI 服務中，指派給進階容量的工作區輕鬆地識別工作區名稱的裝飾的菱形圖示。

![識別工作區指派給進階容量](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>監視容量

監視 Premium 容量提供系統管理員了解如何執行容量。 會監視容量，請使用 Power BI 管理入口網站或**Power BI Premium 容量計量**(Power BI) 應用程式。

### <a name="power-bi-admin-portal"></a>Power BI 管理入口網站

在管理入口網站中，針對每個容量，**健全狀況** 索引標籤會提供摘要的度量容量和每個啟用的工作負載。 計量會顯示平均值在過去七天。  

在容量層級度量資訊是累計的所有啟用的工作負載。 提供下列計量：

- **CPU 使用率**-提供的可用總 CPU 百分比平均 CPU 使用率的容量。  
- **記憶體使用量**-提供平均記憶體使用量 （以 gb 為單位） 的可用記憶體的容量總計。 

對於每個啟用的工作負載，CPU 使用率和記憶體使用量會提供，以及多個工作負載特定的衡量標準。 例如，針對資料流程工作負載中，**總數**顯示總計每個資料流程中，重新整理並**平均持續時間**顯示資料流程的重新整理的平均持續時間。

![在入口網站中的容量健全狀況 索引標籤](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

若要深入了解所有可用的計量，每個工作負載，請參閱[監視系統管理入口網站中的容量](service-admin-premium-monitor-portal.md)。

在 Power BI 系統管理員入口網站中的監視功能被設計來提供索引鍵的容量度量的快速摘要。 如需詳細監視時，建議您使用**Power BI Premium 容量計量**應用程式。

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium 容量度量的應用程式

[Power BI Premium 容量度量的應用程式](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview)可用容量管理員 Power BI 應用程式和安裝等任何其他 Power BI 應用程式。 它包含儀表板和報表。

![Power BI Premium 容量度量的應用程式](media/service-premium-capacity-manage/capacity-metrics-app.png)

當應用程式開啟時，載入儀表板呈現許多透過使用者的容量管理員的所有容量表達的彙總的檢視的圖格儀表板版面配置包含五個主要區段：

- **概觀**-應用程式版本、 容量和工作區的數目
- **系統摘要**-記憶體和 CPU 度量
- **資料集摘要**-數字的資料集、 DQ/LC、 重新整理和查詢度量
- **資料流程摘要**-數字的資料流程，以及資料集指標
- **編頁報表摘要**-重新整理，並檢視度量

可以存取基礎報表，從中釘選儀表板磚，在任何儀表板磚上按一下。 它提供的儀表板各節更詳細的檢視方塊，並支援互動式篩選。 

篩選可藉由設定交叉分析篩選器，依日期範圍、 容量、 工作區和工作負載 （報表、 資料集，資料流程），並選取報表內的項目視覺效果交叉篩選報表頁面。 交叉篩選會縮小至特定時間週期、 容量、 工作區、 資料集等強大的技術，而且執行根本原因分析時可以很有幫助。

如需應用程式中的儀表板和報告度量的詳細資訊，請參閱[使用應用程式的監視 Premium 容量](service-admin-premium-monitor-capacity.md)。

### <a name="interpreting-metrics"></a>解譯計量

應該監視計量，以建立基本了解資源使用狀況和工作負載活動。 如果容量速度變慢，請務必了解，所要監視哪些計量，而且可以作結論。

在理想情況下，查詢應該傳遞給報表使用者的回應性體驗，並啟用更高的查詢輸送量秒內完成。 這通常是較小者值得關注時 （包括重新整理） 的背景程序需要較長的時間才能完成。

一般情況下，速度緩慢的報表可以是過度暖氣容量的指示。 當報表無法載入時，這會是容量的過度熱烈的指示。 在任一情況下，根本原因可能是能歸因於許多因素，包括：

- **無法查詢**當然表示記憶體不足的壓力，及模型無法載入到記憶體。 Power BI 服務會嘗試載入模型，而失敗之前的 30 秒。

- **過多的查詢等候時間**可以是由多種原因造成：
  - Power BI 服務的第一個需要收回模型，並再將要查詢的模型 （請記得，較高的資料集的收回速率單獨不是容量壓力的情況下表示除非伴隨長時間查詢等候時間，表示記憶體過度置換）。
  - 模型載入時間 （特別是大型模型載入到記憶體等候）。
  - 長時間執行的查詢。
  - 太多 LC\DQ 連線 （超過容量限制）。
  - CPU 飽和。
  - 在頁面上 （請記得每個視覺效果是查詢） 的複雜報表與視覺效果數目過多設計。

- **長時間查詢的持續時間**可能表示，模型設計沒有最佳化，特別是當多個資料集裡所有作用中的容量，而且只有一個資料集產生長時間查詢的持續時間。 這可能表示，也充分資源容量，並在問題資料集是次佳或只是速度很慢。 長時間執行的查詢可能會造成問題，因為它們可以封鎖其他處理序所需的資源的存取權。
- **長時間重新整理的等候時間**指出沒有足夠的記憶體，因為許多作用中的模型使用的記憶體，或有問題的重新整理會封鎖其他重新整理 （超過平行重新整理限制）。

說明如何使用計量的詳細的說明[最佳化的 Premium 容量](service-premium-capacity-optimize.md)文章。

## <a name="acknowledgements"></a>通知

撰寫本文時已由 Peter Myers、 資料平台 MVP 和獨立 BI 專家[位元解決方案](https://www.bitwisesolutions.com.au/)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [最佳化的 Premium 容量](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [設定進階容量中的工作負載](service-admin-premium-workloads.md)   

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

||||||
