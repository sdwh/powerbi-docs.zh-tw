---
title: 如何設定 Power BI Premium 中的工作負載
description: 了解如何設定 Power BI Premium 容量中的工作負載。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564873"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>設定 Premium 容量中的工作負載

本文描述如何啟用及設定 Power BI Premium 容量的工作負載。 根據預設，容量僅支援與執行 Power BI 查詢建立關聯的工作負載。 您也可以啟用及設定 **[AI (認知服務)](service-cognitive-services.md)** 、 **[資料流程](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** 和 **[分頁報表](paginated-reports-save-to-power-bi-service.md)** 的其他工作負載。

## <a name="default-memory-settings"></a>預設記憶體設定

查詢工作負載針對 Premium 容量 SKU 決定的資源進行最佳化和限制。 Premium 容量也支援可以使用容量資源的其他工作負載。 這些工作負載之預設記憶體值是根據您 SKU 的可用容量節點。 最大記憶體設定不是累計的。 上限為指定最大值的記憶體，會以動態方式配置給 AI 及資料流程，但是以靜態方式配置給編頁報表。 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>軟體即服務 (SaaS) 案例的 Microsoft Office SKU

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N/A | N/A | 20%的預設值;最小的 20% | 20% 預設值；10% 最小值 | 20% 預設值；5% 最小值 |
| 資料流程 | N/A |20% 預設值；12% 最小值  | 20% 預設值；5% 最小值  | 20% 預設值；3% 最小值 | 預設 20%；最小 2%  |
| 編頁報表 | N/A |N/A | 20% 預設值；10% 最小值 | 20% 預設值；5% 最小值 | 20% 預設值；2.5% 最小值 |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>平台即服務 (PaaS) 案例的 Microsoft Azure SKU

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N/A                      | 20%的預設值;最小值的 100%                     | 20%的預設值;最小的 50%                     | 20%的預設值;最小的 20% | 20% 預設值；10% 最小值 | 20% 預設值；5% 最小值 |
| 資料流程         | 40% 預設值；40% 最小值 | 24% 預設值；24% 最小值 | 20% 預設值；12% 最小值 | 20% 預設值；5% 最小值  | 20% 預設值；3% 最小值 | 預設 20%；最小 2%   |
| 編頁報表 | N/A                      | N/A                      | N/A                     | 20% 預設值；10% 最小值 | 20% 預設值；5% 最小值 | 20% 預設值；2.5% 最小值 |
| | | | | | |

## <a name="workload-settings"></a>工作負載設定

### <a name="ai-preview"></a>AI （預覽）

除了**的最大記憶體**設定，AI 工作負載都有一個額外的設定**允許使用方式，從 Power BI Desktop**。 預設值是**關閉**。 此設定保留供日後使用，且可能不會出現在所有租用戶中。

### <a name="datasets-preview"></a>資料集 （預覽）

根據預設，資料集的工作負載已啟用，而且無法停用。 此工作負載包含一個額外的設定， **XMLA 端點**。 預設值是**1**，啟用的意義。 此設定會指定從用戶端應用程式的連線接受設定工作區和應用程式層級的安全群組成員資格。 若要進一步了解，請參閱[連接到資料集與用戶端應用程式和工具](service-premium-connect-tools.md)。

### <a name="dataflows"></a>資料流程

除了**的最大記憶體**設定時，資料流程工作負載都有一個額外的設定**容器大小**。 此設定可讓您最佳化來處理更複雜、 大量計算的資料流程的資料流程工作負載效能。

當重新整理資料流程，資料流程工作負載會產生在資料流程中的每個實體的容器。 每個容器，可能需要最多的磁碟區的記憶體中的容器大小設定所指定。 所有 Sku 的預設值是**700 MB**。 您可能想要變更此設定，如果：

- 資料流程花費太長的時間重新整理，或在逾時的資料流程重新整理失敗。
- 資料流程實體包括計算步驟，例如，聯結。  

它的建議您使用[Power BI Premium 容量計量](service-admin-premium-monitor-capacity.md)分析資料流程工作負載效能的應用程式。 

在某些情況下，增加容器大小可能無法改善效能。 比方說，如果資料流程只從來源取得資料而不需要執行大量計算，變更容器的大小可能不會幫助。 如果它可讓資料流程工作負載，以重新整理作業的實體配置更多記憶體，可能有助於增加容器大小。 擁有更多的記憶體配置，就可以減少重新整理大量計算的實體所花費的時間。 

容器大小值不能超過資料流程工作負載的最大記憶體。 例如，P1 容量有 25 GB 的記憶體。 如果資料流程工作負載的最大記憶體 （%）設定為 20%，容器大小 (MB) 不能超過 5000。 在所有情況下，容器大小不能超過最大記憶體，即使您設定較高的值。 

### <a name="paginated-reports-preview"></a>編頁的報表 （預覽）

編頁的報表可讓自訂程式碼來轉譯報表時執行。 例如，以動態方式變更內容為基礎的文字色彩，這就可能需要額外的記憶體。 Power BI Premium 在容量內的包含空間中執行編頁報表。 使用指定的最大記憶體*zda bude*工作負載正在作用。 如果變更的最大記憶體設定的預設值，請確定您設定低不夠，就不會造成負面影響其他工作負載。

在某些情況下，分頁的報表工作負載可能會變得無法使用。 在此情況下，工作負載會在系統管理員入口網站中，錯誤狀態，而且使用者會看到報表轉譯的逾時。 若要解決這個問題，停用工作負載並再次啟用它。

## <a name="configure-workloads"></a>設定工作負載

透過只在使用時才啟用工作負載，最大限度地提高容量的可用資源。 請只在已確定預設設定不符合您的容量資源需求時，才變更記憶體設定。  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>在 Power BI 管理入口網站設定工作負載

1. 在 [容量設定]   > [PREMIUM 容量]  中選取容量。

1. 在 [更多選項]  底下，展開 [工作負載]  。

1. 啟用一或多個工作負載，並設定 [最大記憶體]  的值。   

    
    ![啟用工作負載](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. 按一下 [套用]  。

### <a name="rest-api"></a>REST API

使用[Capacities](https://docs.microsoft.com/rest/api/power-bi/capacities) (容量) REST API 可以啟用工作負載並將其指派給容量。

## <a name="monitoring-workloads"></a>監視工作負載

[Power BI Premium 容量計量應用程式](service-admin-premium-monitor-capacity.md)提供資料集、資料流程，以及分頁報表計量，以監視針對您的容量啟用的工作負載。 

## <a name="next-steps"></a>後續步驟

[最佳化 Power BI Premium 容量](service-premium-capacity-optimize.md)     
[Power BI 中的自助資料準備 (使用資料流程)](service-dataflows-overview.md)   
[什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)   

有其他問題嗎？ [詢問 Power BI 社群](http://community.powerbi.com/)