---
title: Microsoft Power BI Premium 是什麼？
description: Power BI Premium 是您的組織或小組的專用容量，給您更可靠的效能和更大的資料磁碟區，不需要您購買每個使用者授權。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/11/2018
LocalizationGroup: Premium
ms.openlocfilehash: 0723ddb57131fed499d4ac86666b3cd6d8bcbd2d
ms.sourcegitcommit: 833cf1252807721fb1b3000487bd032bfd6c8c98
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48271800"
---
# <a name="what-is-microsoft-power-bi-premium"></a>Microsoft Power BI Premium 是什麼？

Microsoft Power BI Premium 為您的組織或小組提供專門用來執行 Power BI 服務的資源。 它提供您更可靠的效能並啟用更大的資料磁碟區。 Premium 也可讓您廣泛發佈內容，不需要您為檢視者購買每個使用者 Pro 授權。

您可以將工作區指派至 *Premium 容量*來利用 Power BI Premium。 Premium 容量是您的組織專用資源。 未指派至 Premium 容量的工作區會放在「共用容量」中。 使用共用容量，您的工作負載可在其他客戶共用的計算資源上執行。 

在共用容量中，為了確保所有使用者的體驗品質，Power BI 對於個別使用者有較多限制。 根據預設，您的工作區是在共用容量，包括您個人的「我的工作區」和應用程式工作區。

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>容量層

以下是共用容量和 Premium 容量之間差異的摘要。

|  | 共用容量 | Power BI Premium 容量 |
| --- | --- | --- |
| **重新整理的頻率** |8/日 |48/日 |
| **使用專用的硬體隔離** |![](media/service-premium/not-available.png "無法使用") |![](media/service-premium/available.png "可用") |
| **企業散發至*****所有使用者*** | | |
| 應用程式和共用 |![](media/service-premium/not-available.png "無法使用") |![](media/service-premium/available.png "可用")<sup>1</sup> |
| 內嵌的 API 和控制項 |![](media/service-premium/not-available.png "無法使用") |![](media/service-premium/available.png "可用")<sup>2</sup> |
| **在內部部署發佈 Power BI 報告** |![](media/service-premium/not-available.png "無法使用") |![](media/service-premium/available.png "可用") |

*<sup>1</sup> 如需詳細資訊，請參閱[依授權類型排列的功能](service-features-license-type.md)。*  
*<sup>2</sup> Power BI Premium 的未來增強功能。*

若要開始使用 Power BI Premium 容量，請將工作區指派至容量。 當 Premium 容量支援工作區時，您會：

* **排程重新整理**：使用共用容量，匯入模型資料集的排程重新整理上限為每天八次。 Premium 工作區的資料集排程重新整理上限為每天 48 次。 在 Premium 容量中，DirectQuery 快取重新整理仍限制為每天八次。

* **使用專用硬體的隔離**：在共用容量中，其他工作負載的資源需求可能會影響您的報表和儀表板效能。 相反地，Premium 容量會隔離您的工作負載和非相關工作負載，以提供更一致又可靠的效能。

如果應用程式有 Premium 容量作為後盾 (也就是，從目前已指派至 Premium 的應用程式工作區發佈)，則組織中的任何使用者都可以使用已發佈應用程式，而不論已指派給他們的授權。

若要深入了解將工作區指派給 Premium 容量，請參閱[管理 Power BI Premium](service-admin-premium-manage.md)。

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>進階容量節點

Power BI Premium 適用於有不同 v 核心容量的節點設定。 如需特定 SKU 供應項目和成本的詳細資訊，請參閱 [Power BI 定價](https://powerbi.microsoft.com/pricing/)。 也提供[成本計算機](https://powerbi.microsoft.com/calculator/)。 如需內嵌的分析容量規劃的相關資訊，請參閱[規劃 Power BI 企業部署白皮書](https://aka.ms/pbienterprisedeploy)。

* P 節點可用於內嵌部署或服務部署。

* EM 節點只能用於內嵌部署。 EM 節點無法存取 Premium 功能，像是將應用程式分享給沒有 Power BI Pro 授權的使用者。

>[!NOTE]
>只有身為 Office 365 全域系統管理員的使用者，此資料表中的連結才能正常運作。 其他人會收到 404 錯誤。

| 節點容量 | V 核心總數<br/>(後端 + 前端) | 後端 V 核心 | 前端 V 核心 | DirectQuery/即時連線限制 | 尖峰時間的頁面呈現上限 | 可用性 |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (逐月)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 個 V 核心 |0.5 個 V 核心，2.5 GB RAM |0.5 個 V 核心 |每秒 3.75 個 |150-300 |可用 |
| [EM2 (逐月)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 個 v 核心 |1 個 V 核心，5 GB RAM |1 個 V 核心 |每秒 7.5 個 |301-600 |可用 |
| [EM3 (逐月)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 個 v 核心 |2 個 V 核心，10 GB RAM |2 個 v 核心 | |601-1,200 |可用 |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 個 v 核心 |4 個 V 核心，25 GB RAM |4 個 v 核心 |每秒 30 個 |1,201-2,400 |可用 (也提供[逐月](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1)) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 個 v 核心 |8 個 V 核心，50 GB RAM |8 個 v 核心 |每秒 60 個 |2,401-4,800 |可用 |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 個 v 核心 |16 個 V 核心，100 GB RAM |16 個 v 核心 |每秒 120 個 |4,801-9600 |可用 |

* 前端 V 核心負責 Web 服務、儀表板和報表文件管理、存取權限管理、排程、API、上傳和下載，大致上就是與使用者體驗有關的一切作業。

* 後端 V 核心承擔重任：查詢處理、快取管理、執行 R 伺服器、資料重新整理、自然語言處理、即時摘要，以及在伺服器端轉譯報表和影像。 為了配合後端 V 核心，也會保留一定數量的記憶體。 在處理大型資料模型，或大量的使用中資料集時，有足夠的記憶體就變得特別重要。

## <a name="power-bi-report-server"></a>Power BI 報表伺服器
Power BI Premium 也能夠在組織內部執行 Power BI 報表伺服器。 若要深入了解，請參閱[開始使用 Power BI 報表伺服器](report-server/get-started.md)。

## <a name="next-steps"></a>後續步驟
[Power BI Premium 常見問題集](service-premium-faq.md)  
[Power BI Premium 版本資訊](service-premium-release-notes.md)  
[如何購買 Power BI Premium](service-admin-premium-purchase.md)  
[管理 Power BI Premium](service-admin-premium-manage.md)  
[Microsoft Power BI Premium 白皮書](https://aka.ms/pbipremiumwhitepaper)  
[規劃 Power BI 企業部署白皮書](https://aka.ms/pbienterprisedeploy)  
[管理貴組織中的 Power BI](service-admin-administering-power-bi-in-your-organization.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
