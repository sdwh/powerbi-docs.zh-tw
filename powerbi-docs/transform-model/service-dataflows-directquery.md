---
title: 在 Power BI 中使用資料流程的 DirectQuery 功能 (預覽)
description: 了解在 Power BI 中搭配資料流程使用 DirectQuery
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 469b8b13f77c56f9371ae8c1c81dcb94278c62e0
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83794005"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>在 Power BI 中使用資料流程的 DirectQuery 功能 (預覽)

您可使用 DirectQuery 直接連線到資料流程，並因此直接連線到資料流程，而無須匯入其資料。 

搭配資料流程使用 DirectQuery 可為 Power BI 和資料流程處理序帶來下列增強功能：

* **避免個別的重新整理排程** - DirectQuery 會直接連線到資料流程，移除建立匯入資料集的需求。 因此，搭配資料流程使用 DirectQuery 表示您不再需要針對資料流程和資料集具備個別的重新整理流程來確保資料同步。

* **篩選資料** - 在資料流程內部使用篩選資料檢視時，DirectQuery 相當實用。 若想要篩選資料，並因此在資料流程內使用較小部分的資料，您可使用 DirectQuery (以及計算引擎) 來篩選資料流程資料及使用所需的篩選子集。


## <a name="using-directquery-for-dataflows"></a>針對資料流程使用 DirectQuery

搭配資料流程使用 DirectQuery 是一項預覽功能，從 Power BI Desktop 2020 年五月版本開始提供使用。 

搭配資料流程使用 DirectQuery 也有先決條件：

* 資料流程必須位於啟用 Power BI Premium 的工作區內
* 必須開啟**計算引擎**。 如需計算引擎的詳細資訊，請參閱[增強型計算引擎](service-dataflows-enhanced-compute-engine.md)。

## <a name="enable-directquery-for-dataflows"></a>針對資料流程啟用 DirectQuery

為了確保資料流程可供 DirectQuery 存取使用，增強型計算引擎必須處於最佳化狀態。 若要針對資料流程啟用 DirectQuery，請將新的 [增強型計算引擎設定] 選項設為 [開啟]。 下圖顯示設定已適當選取。

![為資料流程啟用增強型計算引擎](media/service-dataflows-directquery/dataflows-directquery-01.png)

在套用設定後，請重新整理資料流程，以讓最佳化生效。 


## <a name="considerations-and-limitations"></a>考量與限制

DirectQuery 和資料流程有些已知限制，這些限制會在下列清單中解釋。

* 資料流程的 DirectQuery 無法搭配啟用的**增強型中繼資料預覽**功能使用。 這項排除預期會在之後的每月 Power BI Desktop 版本中移除。

* 在此功能的預覽期間，有些客戶可能會在搭配資料流程使用 DirectQuery 時遇到逾時或效能問題。 我們正在這段預覽期間積極解決這些問題。

* 目前不支援具有匯入和 DirectQuery 資料來源的複合/混合模式。

* 大型資料流程在觀賞視覺效果時，可能會遇到逾時問題。 此項功能正式發行時，會將此限制移除。 同時，遇到逾時問題的大型資料流程應該使用 [匯入] 模式。

* 在資料來源設定底下，如果您要使用 DirectQuery，資料流程連接器會顯示無效認證。 這不會影響行為，且資料集會正常運作。 此問題將會在我們接近正式發行時移除。



## <a name="next-steps"></a>後續步驟

下列文章可在您使用資料流程時，提供更詳細的資訊與案例：

* [使用資料流程的自助資料準備](service-dataflows-overview.md)
* [在 Power BI Premium 上使用計算實體](service-dataflows-computed-entities-premium.md)
* [搭配內部部署資料來源使用資料流程](service-dataflows-on-premises-gateways.md)
* [Power BI 資料流程的開發人員資源](service-dataflows-developer-resources.md)
* [資料流程與 Azure Data Lake 的整合 (預覽)](service-dataflows-azure-data-lake-integration.md)

如需 Common Data Service 的詳細資訊，您可以閱讀它的概觀文章：
* [Common Data Model - 概觀](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [深入了解 Common Data Model 結構描述和 GitHub 上的實體](https://github.com/Microsoft/CDM)

相關的 Power BI Desktop 文章：

* [從 Power BI Desktop 連線到 Power BI 服務中的資料集](../connect-data/desktop-report-lifecycle-datasets.md)
* [Power BI Desktop 中的查詢概觀](desktop-query-overview.md)

相關的 Power BI 服務文章：
* [設定排定的重新整理](../connect-data/refresh-scheduled-refresh.md)
