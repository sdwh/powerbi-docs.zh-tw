---
title: jPower BI Premium 中的查詢快取
description: jPower BI Premium 中的查詢快取
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: c981a3e2a05129a470c8d26675226bfb42c1bb68
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769548"
---
# <a name="query-caching-in-power-bi-premium"></a>jPower BI Premium 中的查詢快取

使用 Power BI Premium 的組織可以利用「查詢快取」  來加速與資料集建立關聯的報表。 查詢快取會指示 Premium 容量使用其本機快取服務來維護查詢結果，避免讓基礎資料來源計算這些結果。

> [!IMPORTANT]
> 查詢快取僅適用於 Power BI Premium。 不適用於運用 Azure Analysis Services 或 SQL Server Analysis Services 的 LiveConnect 資料集。

快取的查詢結果特定於使用者和資料集內容，且一律遵循安全性規則。 目前，服務僅會對您登陸的初始頁面進行查詢快取。 換句話說，當您與報表互動時，查詢並不會快取。 快取會反映個人書籤和永續性篩選。 查詢完成快取後，由相同查詢提供的[儀表板圖格](service-dashboard-tiles.md)也會受益。 頻繁存取資料集且不需要經常重新整理時，會特別有益於效能。 查詢快取也可以減少查詢總數來降低 Premium 容量的負載。

您可以在 Power BI 服務中資料集的 [設定]  頁面上控制查詢快取行為。 它有兩個可能的設定：

- **關閉**：不為此資料集使用查詢快取。

- **開啟**：為此資料集使用查詢快取。

![查詢快取對話方塊](media/power-bi-query-caching/power-bi-query-caching.png)

> [!NOTE]
> 當您將快取設定從 [開啟]  變更為 [關閉]  時，先前所有已儲存的資料集查詢結果都會從容量快取中移除。 您可以用明確方式，或是還原至系統管理員設定為 [關閉]  的容量預設設定來關閉快取。 將其關閉可能會在下一次任何報表針對此資料集執行查詢時造成小量延遲。 延遲是因隨需執行的報表查詢所造成，而不是因利用已儲存的結果。 此外，必要的資料集可能需要先載入至記憶體，才能提供查詢。


