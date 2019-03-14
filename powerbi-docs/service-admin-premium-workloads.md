---
title: 如何設定 Power BI Premium 中的工作負載
description: 了解如何設定 Power BI Premium 容量中的工作負載。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/11/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0baab138ee98d2ec96bc9f47e6e727525a57ed3e
ms.sourcegitcommit: f176ba9d52d50d93f264eca21bb3fd987dbf934b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57757238"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>設定 Premium 容量中的工作負載

本文描述如何啟用及設定 Power BI Premium 容量的工作負載。 根據預設，容量僅支援與執行 Power BI 查詢建立關聯的工作負載。 查詢工作負載針對 Premium 容量 SKU 決定的資源進行最佳化和限制。 Premium 容量也支援可以使用容量資源的其他工作負載。

## <a name="configure-workloads"></a>設定工作負載

您可以啟用及設定 AI、[資料流程](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)和[編頁報表](paginated-reports-save-to-power-bi-service.md)的其他工作負載。 這些工作負載之預設記憶體值是根據您 SKU 的可用容量節點。 最大記憶體設定不是累計的。 上限為指定最大值的記憶體，會以動態方式配置給 AI 及資料流程，但是以靜態方式配置給編頁報表。 

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>在 Power BI 管理入口網站設定工作負載

1. 在 [容量設定] > [PREMIUM 容量] 中選取容量。

1. 在 [更多選項] 底下，展開 [工作負載]。

1. 啟用一或多個工作負載，並設定 [最大記憶體] 的值。   

    
    ![啟用工作負載](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. 按一下 [套用]。

> [!NOTE]
> 如果啟用編頁報表工作負載，編頁報表可讓您在轉譯報表 (例如依據內容動態變更文字色彩) 時執行自己的程式碼。 Power BI Premium 在容量內的包含空間中執行編頁報表。 無論工作負載是否為作用中，都會使用您指定給此空間的最大記憶體。 如果您以相同容量使用 Power BI 報表或資料流程，請確定您沒有為編頁報表設定過大的記憶體，以避免對其他工作負載造成負面影響。 在罕見的情況下，編頁報表工作負載可能會變成無法使用。 此時，工作負載會在系統入口網站中顯示錯誤狀態，而且使用者會看到報表轉譯逾時。 若要緩解此問題，請停用工作負載，然後再次啟用它。


### <a name="rest-api"></a>REST API

使用[Capacities](https://docs.microsoft.com/rest/api/power-bi/capacities) (容量) REST API 可以啟用工作負載並將其指派給容量。


## <a name="next-steps"></a>後續步驟

[Power BI Premium 容量資源管理與最佳化](service-premium-understand-how-it-works.md)   
[Power BI 中的自助資料準備 (使用資料流程)](service-dataflows-overview.md)   
[什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)   

有其他問題嗎？ [詢問 Power BI 社群](http://community.powerbi.com/)