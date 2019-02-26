---
title: Microsoft Power BI Premium 是什麼？
description: Power BI Premium 是您的組織或小組的專用容量，給您更可靠的效能和更大的資料磁碟區，不需要您購買每個使用者授權。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/15/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: a048f589b19acd1a7c38a5b81cf781d1e76b7b5b
ms.sourcegitcommit: 187d20180d9bae5a2ec53748cede9e7301e0343e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56725332"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Microsoft Power BI Premium 是什麼？

Microsoft Power BI Premium 可為您的組織提供專門用來執行 Power BI 服務的資源。 它提供您更可靠的效能並啟用更大的資料磁碟區。 Premium 也可讓您廣泛發佈內容，不需要您為內容取用者購買每個使用者 Pro 授權。  

## <a name="premium-capacity-and-shared-capacity"></a>Premium 容量和共用容量

您可以將工作區指派至「Premium 容量」來利用 Power BI Premium。 Premium 容量是您的組織專用資源。 未指派至 Premium 容量的工作區會放在「共用容量」中。 使用共用容量，您的工作負載可在其他客戶共用的計算資源上執行。

下圖顯示 Premium 容量和共用容量間的關聯性，使用 Contoso 組織作為範例。

![Power BI Premium 的圖例](media/service-premium/premium-chart.png)

| 區域 | 描述 |
| --- | --- |
| **(1)** Premium 容量中的項目 | <ul><li>需要有 Power BI Pro 授權才能 (以成員或管理員身分) 存取應用程式工作區並發佈應用程式。<li>共用應用程式時需要 Pro 授權，但使用應用程式時不需要。<li>所有儀表板收件者都可以設定資料警示，而不論獲指派的授權為何。<li>用於內嵌的 REST API 會搭配使用服務帳戶與 Pro 授權，而不是使用者帳戶。</ul> |
| **(2)** 共用容量中的「我的工作區」 | <ul><li>共用和使用應用程式都需要 Pro 授權。</ul> |
| **(3)** 共用容量中的應用程式工作區 | <ul><li>使用任何應用程式都需要 Pro 授權。</ul>|
| | |

在共用容量中，為了確保所有使用者的體驗品質，Power BI 對於個別使用者有較多限制。 根據預設，您的工作區是在共用容量，包括您個人的「我的工作區」和應用程式工作區。

下表提供共用容量和 Premium 容量間差異的摘要：

|  | 共用容量 | Power BI Premium 容量 |
| --- | --- | --- |
| **重新整理的頻率** |8/日 |48/日 |
| 使用專用的硬體隔離 |![無法使用](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| 對所有使用者的企業散發 | | |
| 應用程式和共用 |![無法使用](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| 內嵌的 API 和控制項 |![無法使用](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| 在內部部署發佈 Power BI 報表 |![無法使用](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> Power BI Premium 未來的增強功能。



### <a name="premium-capacity-nodes"></a>進階容量節點

Power BI Premium 適用於有不同 v 核心容量的節點設定。 如需特定 SKU 供應項目和成本的詳細資訊，請參閱 [Power BI 定價](https://powerbi.microsoft.com/pricing/)。 也提供[成本計算機](https://powerbi.microsoft.com/calculator/)。 如需內嵌的分析容量規劃的相關資訊，請參閱[規劃 Power BI 企業部署白皮書](https://aka.ms/pbienterprisedeploy)。 摘要：

* P 節點可用於內嵌部署或服務部署。

* EM 節點只能用於內嵌部署。 EM 節點無法存取 Premium 功能，像是將應用程式分享給沒有 Power BI Pro 授權的使用者。

| 節點容量 | V 核心總數<br/>(後端+前端)  | 後端 V 核心 <sup>[1](#fn1)</sup> | 前端 V 核心 <sup>[2](#fn2)</sup> | DirectQuery/即時連線限制 | 最大並行重新整理 |  可用性
| --- | --- | --- | --- | --- | --- | --- | --- |
| EM1 (逐月) |1 個 V 核心 |0.5 個 V 核心，2.5 GB RAM |0.5 個 V 核心 |每秒 3.75 個 |  1 | 可用 |
| EM2 (逐月) |2 個 v 核心 |1 個 V 核心，5 GB RAM |1 個 V 核心 |每秒 7.5 個 |  2 | 可用 |
| EM3 (逐月) |4 個 v 核心 |2 個 V 核心，10 GB RAM |2 個 v 核心 | | 3 |  可用 |
| P1 |8 個 v 核心 |4 個 V 核心，25 GB RAM |4 個 v 核心 |每秒 30 個 | 6 | 可用 (也提供逐月) |
| P2 |16 個 v 核心 |8 個 V 核心，50 GB RAM |8 個 v 核心 |每秒 60 個 | 12 | 可用 |
| P3 |32 個 v 核心 |16 個 V 核心，100 GB RAM |16 個 v 核心 |每秒 120 個 | 24 | 可用 |
| | | | | | | |

<a name="fn1">1</a>：前端 V 核心負責 Web 服務。 例如，儀表板和報告文件管理、存取權限管理、排程、API、上傳和下載，大致上就是與使用者經驗有關的一切作業。 

<a name="fn2">2</a>：後端 V 核心承擔重任：例如查詢處理、快取管理、執行 R 伺服器、資料重新整理、自然語言處理、即時摘要，以及在伺服器端轉譯報表和影像。 為了配合後端 V 核心，也會保留一定數量的記憶體。 在處理大型資料模型，或大量的使用中資料集時，有足夠的記憶體就變得特別重要。

## <a name="workloads-in-premium-capacity"></a>Premium 容量中的工作負載

可以把 Power BI 中的工作負載想成是您可以向使用者公開的多個服務其中之一。 根據預設，適用於 **Power BI Premium** 和 **Power BI Embedded** 的容量只支援雲端上與執行中 Power BI 查詢相關聯的工作負載。

我們現在針對兩個額外的工作負載提供預覽支援：**編頁報表**和**資料流程**。 您可以在 Power BI 管理入口網站，或透過 Power BI REST API 啟用這些工作負載。 也可以設定每個工作負載可使用的記憶體大小上限，因此可以控制不同的工作負載會如何彼此影響。 如需詳細資訊，請參閱[設定工作負載](service-admin-premium-manage.md#configure-workloads)。

### <a name="default-memory-settings"></a>預設記憶體設定

下表根據提供的不同[容量節點](#premium-capacity-nodes)，顯示預設及最小記憶體值。 記憶體會以動態方式配置給資料流程，但會以靜態方式配置給編頁報表。 如需詳細資訊，請參閱下一節，[編頁報表考量](#considerations-for-paginated-reports)。

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>軟體即服務 (SaaS) 案例的 Microsoft Office SKU

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| 編頁報表 | N/A | 20% 預設值；10% 最小值 | 20% 預設值；5% 最小值 | 20% 預設值；2.5% 最小值 |
| 資料流程 | 預設 20%；最小 8%  | 預設 20%；最小 4%  | 預設 20%；最小 2% | 預設 20%；最小 1%  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>平台即服務 (PaaS) 案例的 Microsoft Azure SKU

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| 編頁報表 | N/A                      | N/A                      | N/A                     | 20% 預設值；10% 最小值 | 20% 預設值；5% 最小值 | 20% 預設值；2.5% 最小值 |
| 資料流程         | 預設 27%；最小 27% | 預設 20%；最小 16% | 預設 20%；最小 8% | 預設 20%；最小 4%  | 預設 20%；最小 2% | 預設 20%；最小 1%   |

### <a name="considerations-for-paginated-reports"></a>編頁報表考量

如果使用分頁報表工作負載，請記住編頁報表可讓您在轉譯報表 (例如依據內容動態變更文字色彩) 時執行自己的程式碼。 這表示我們透過在容量內包含的空間中執行編頁報表，以保護 Power BI Premium 容量。 無論工作負載是否在作用中，我們都會將您指定的最大記憶體指派給此空間。 如果您以相同容量使用 Power BI 報表或資料流程，請確定您沒有為編頁報表設定過大的記憶體，以避免對其他工作負載造成負面影響。

在罕見的情況下，編頁報表工作負載可能會變成無法使用。 此時，工作負載會在系統入口網站中顯示錯誤狀態，而且使用者會看到報表轉譯逾時。 若要緩解此問題，請停用工作負載，然後再次啟用它。

## <a name="power-bi-report-server"></a>Power BI 報表伺服器

Power BI Premium 也能夠在組織內部執行 Power BI 報表伺服器。 若要深入了解，請參閱[開始使用 Power BI 報表伺服器](report-server/get-started.md)。

## <a name="next-steps"></a>後續步驟

[Power BI Premium 常見問題集](service-premium-faq.md)
[如何購買 Power BI Premium](service-admin-premium-purchase.md)
[管理 Power BI Premium](service-admin-premium-manage.md)
[Microsoft Power BI Premium 白皮書](https://aka.ms/pbipremiumwhitepaper) \(英文\)
[規劃 Power BI Enterprise 部署白皮書](https://aka.ms/pbienterprisedeploy) \(英文\)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
