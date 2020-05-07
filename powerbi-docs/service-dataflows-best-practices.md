---
title: 適用於 Power BI 資料流程的最佳做法
description: 適用於 Power BI 資料流程的最佳做法
author: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 4bbc8b71455d01405854304dd4b889f664ce8575
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "73877282"
---
# <a name="dataflows-best-practice"></a>資料流程最佳做法

本文提供在 Power BI 中設計資料流程的最佳做法。 您可以使用本指南來了解如何建立資料流程，並將這些做法套用到您自己的資料流程中。

> [!NOTE]
> 本文中的建議是指導方針。 針對本文中的每個最佳做法，可能會有不完全遵循本指南內容的合理原因。 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>對擷取和轉換進行分割以使用增強計算引擎

建立資料流程時，您可能會想要建立單一資料流程，並使所有實體、轉換、聯結及增強功能都位於單一位置。 對於較小的資料集來說，單一資料流程可能是有效的。 但在處理較大資料量的情況下，執行聯結或某些轉換時可能會遇到節流或記憶體限制。 為了解決那些問題，已針對 Power BI Premium 使用者推出增強引擎，以便針對較大的資料量調整規模。 增強計算引擎僅適用於已連結或計算的實體，因此建立適用於擷取的個別資料流程，以及用來執行所有複雜合併及轉換的已連結資料流程，將可受益於增強引擎。

對資料流程進行分割也能為重新整理問題的診斷及偵錯有益，特別是在使用具有節流限制的來源時。

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>執行可以使用增強計算引擎的動作

透過先在計算實體中執行聯結和篩選轉換，再執行其他類型的轉換，來確保可以運用增強計算引擎。

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>在連線至 SharePoint 時分割資料流程

使用 SharePoint 並連線至多個檔案時，您可能會注意到偶爾發生的失敗。 SharePoint 會對要求進行節流，以確保它能保持可靠並快速回應。 因此，從 SharePoint 連線至 Excel 檔案時，您可能會將所有檔案下載到單一資料流程中。 如果您正在下載許多檔案 (超過 20 個)，請建立兩個或更多的資料流程來分割重新整理負載，並克服 SharePoint 節流。

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>避免針對相同工作區內的連結實體進行重新整理的排程

如果您經常被封鎖在包含連結實體的資料流程之外，這可能是因為相同工作區內的相對應相依資料流程，在資料流程重新整理期間被鎖定所導致。 此類鎖定能提供交易精確度，並確保資料流程都能順利重新整理，但它可能會使您無法編輯。 

如果您針對已連結的資料流程設定個別排程，資料流程可能會進行不必要的重新整理，並封鎖您編輯該資料流程的能力。 有兩個建議可避免此問題： 

* 避免針對和來源資料流程相同之工作區中的已連結資料流程設定重新整理排程
* 如果您想要個別設定重新整理排程，並想要避免鎖定行為，請將該資料流程移至個別的工作區中。

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>針對擷取、轉換建立個別工作區

若要為許多使用者提供對基礎資料的存取，同時不允許他們存取基礎來源系統的原始資料，請建立具有您需要共用之所有資料的個別工作區，並指派權限。 目前不支援個別的資料流程權限。

### <a name="ensure-capacity-is-in-the-same-region"></a>確定容量位於相同區域中

資料流程目前不支援多地理區域。 Premium 容量必須位於與您的 Power BI 租用戶相同的區域中。

### <a name="separate-on-premises-sources-from-cloud-sources"></a>將內部部署來源與雲端來源區分開來

除了先前所述的最佳做法之外，您可以針對每種類型的來源 (例如內部部署、雲端、SQL Server、Spark、Dynamics 等) 建立個別的資料流程。 強烈建議您依資料來源類型來分割您的資料流程。 依來源類型進行分割有助於快速進行疑難排解，並能在重新整理資料流程時避免內部限制。

### <a name="separate-dataflows-into-a-separate-capacity"></a>將資料流程區分至個別容量

如果您遇到節流限制，或是因容量上的記憶體限制而經常遇到資料流程失敗，請考慮將資料流程分開，或是相應增加 Premium 容量以獲得額外記憶體。

## <a name="next-steps"></a>後續步驟

本文已提供適用於資料流程之最佳做法的相關資訊。 如需資料流程的詳細資訊，下列文章可能很實用：

* [使用資料流程的自助資料準備](service-dataflows-overview.md)
* [建立 Power BI 中的資料流程](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用計算實體](service-dataflows-computed-entities-premium.md)
* [搭配內部部署資料來源使用資料流程](service-dataflows-on-premises-gateways.md)

如需 CDM 開發和教學課程資源的相關資訊，請參閱下列各項：
* [Common Data Service - 概觀](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM 資料夾](https://go.microsoft.com/fwlink/?linkid=2045304) \(英文\)
* [CDM 模型檔案定義](https://go.microsoft.com/fwlink/?linkid=2045521) \(英文\)


如需 Power Query 和排程重新整理的詳細資訊，您可以閱讀下列文章：
* [Power BI Desktop 中的查詢概觀](desktop-query-overview.md)
* [設定排定的重新整理](refresh-scheduled-refresh.md)
