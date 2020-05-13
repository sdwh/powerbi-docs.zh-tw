---
title: 將增強型計算引擎與資料流程搭配使用
description: 了解如何在 Power BI Premium 中將增強型計算引擎與資料流程搭配使用
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: e126451bf016bf4e9dcce7b7a4df51db9ed20386
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83320507"
---
# <a name="the-enhanced-compute-engine"></a>增強型計算引擎

Power BI 中增強型計算引擎可讓 Power BI Premium 訂閱者使用其容量來最佳化資料流程的使用。 使用增強型計算引擎可提供下列優點：

* 大幅減少長時間執行的 ETL 步驟在計算實體上所需重新整理時間，例如執行「聯結」  、「相異」  、「篩選」  和「分組方式」 
* 在實體上執行 DirectQuery 查詢 (在 2020 年 2 月)

下列各節描述如何啟用增強型計算引擎，並回答常見問題。


## <a name="using-the-enhanced-compute-engine"></a>使用增強型計算引擎

增強型計算引擎可從 Power BI 服務內 [容量設定]  頁面的 [資料流程]  區段中啟用。 增強型計算引擎預設為 [關閉]  。 若要開啟增強型計算引擎，請將切換按鈕切換為 [開啟]  (如下圖所示)，然後儲存您的設定。 

![開啟增強型計算引擎](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

當您開啟增強型計算引擎之後，請返回資料流程，您應該會在任何針對資料流程 (從相同容量的現有連結實體建立) 執行複雜作業 (例如「聯結」  或「分組方式」  作業) 的計算實體中看到效能改善。 

若要充分利用計算引擎，您應該以下列方式將 ETL 階段分割成兩個不同的資料流程：

* **資料流程 1** - 此資料流程只應從資料來源內嵌所有必要內容，並將其放入資料流程 2。
* **資料流程 2** - 在此第二個資料流程中執行所有 ETL 作業，但請確定您參考的是資料流程 1，其應位於相同的容量。 此外，請務必先執行可摺疊的作業 (篩選、分組方式、相異、聯結)，再執行任何其他作業，以確保使用計算引擎。

## <a name="common-questions-and-answers"></a>常見問題與答案

**問：** 我已啟用增強型計算引擎，但重新整理的速度較慢。 為什麼？

**答：** 如果您啟用了增強型計算引擎，有兩種可能的情況會導致重新整理時間較慢：

 - 啟用增強型計算引擎時，需要一些記憶體才能正常運作。 因此，可用來執行重新整理的記憶體會減少，因此增加了資料流程重新整理排入佇列的可能性，進而減少可同時重新整理的資料流程數。 若要解決這種情況，請在啟用增強型計算時，增加指派給資料流程的記憶體，以確保可用於同時重新整理資料流程的記憶體保持不變。

 - 另一個您可能遇到重新整理速度較慢的原因是，計算引擎只能在現有實體之上運作，如果資料流程參考的資料來源不是資料流程，您就不會看到任何改善。 效能不會提高，因為在某些巨量資料案例中，由於資料必須傳遞至增強型計算引擎，因此資料來源的初始讀取會變慢。  

**問：** 我看不到增強型計算引擎的切換按鈕。 為什麼？

**答：** 增強型計算引擎會分階段發行到全球各地。 我們預期在 2020 年底前為所有區域提供支援。

**問：** 適用於計算引擎的支援資料類型有哪些？

**答：** 增強型計算引擎和資料流程目前支援下列資料類型。 如果您的資料流程未使用下列其中一種資料類型，重新整理期間就會發生錯誤：

* 日期/時間
* 十進位數字
* 文字
* 整數
* 日期/時間/時區
* True/False
* 日期
* 時間

## <a name="next-steps"></a>後續步驟

本文提供針對資料流程使用增強型計算引擎的相關資訊。 下列文章可能也很實用：

* [使用資料流程的自助資料準備](service-dataflows-overview.md)
* [在 Power BI 中建立及使用資料流程](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用計算實體](service-dataflows-computed-entities-premium.md)
* [Power BI 資料流程的開發人員資源](service-dataflows-developer-resources.md)

如需 Power Query 和排程重新整理的詳細資訊，您可以閱讀下列文章：
* [Power BI Desktop 中的查詢概觀](desktop-query-overview.md)
* [設定排定的重新整理](../connect-data/refresh-scheduled-refresh.md)

如需 Common Data Service 的詳細資訊，您可以閱讀它的概觀文章：
* [Common Data Service - 概觀](https://docs.microsoft.com/powerapps/common-data-model/overview)
