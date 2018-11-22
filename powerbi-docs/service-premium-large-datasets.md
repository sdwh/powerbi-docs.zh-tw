---
title: 大型資料集的 Power BI Premium 支援
description: Power BI Premium 現在最多支援 10 GB 的資料集。
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 0449d7953b5cefb4c76d89f05ec5b3fa70e9c0da
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679345"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>大型資料集的 Power BI Premium 支援

Power BI Premium 支援上傳大小最多為 10 GB 的 Power BI Desktop (.pbix) 檔案。 上傳之後，資料集可以重新整理，最多 12 GB 的大小。 若要使用大型資料集，請將它發行至指派給 Premium 容量的工作區。
 
## <a name="best-practices"></a>最佳作法

本節描述使用大型資料集的最佳做法。

對於您的容量，**大型模型可能非常耗用資源**。 我們建議任何大於 1 GB 的模型至少要有 P1 SKU。 雖然 A SKU 最多可支援發佈大型模型到工作區 (最多到 A3)，但重新整理它們之後即無法支援。

下表描述各種 .pbix 大小的建議 SKU：

   |SKU  |.pbix 大小   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3、P4、P5    | 最多 10 GB   |

Power BI Embedded A4 SKU 等同於 P1 SKU、A5 = P2 及 A6 = P3。 請注意，將大型模型發行到 A 和 EM SKU，可能會傳回錯誤，且為非專屬於共用容量中模型大小限制的錯誤。 A 和 EM SKU 中，大型模型的重新整理錯誤，很可能指向逾時。 我們正努力改善這些情況下的錯誤訊息。

**.pbix 檔案以高度壓縮狀態呈現資料**。 載入至記憶體時，資料可能會展開多次，而且從該處，在資料重新整理期間，資料可能會再展開幾次。

**排程重新整理大型資料集可能需要很長的時間**，而且需要極大量資源。 因此，請不要排程太多重疊重新整理。 另請注意，針對此容量的所有資料集，排程重新整理作業的逾時已加倍到四個小時。 我們建議[累加式重新整理](service-premium-incremental-refresh.md)，因為更快、更可靠，而且耗用較少的資源。

如果自上次使用資料集以來已有一段時間，則**大型資料集的初始報表負載可能需要很長的時間**，因為會將模型載入至 Premium 容量的記憶體。 較長載入之報表的載入列會顯示載入進度。

**如果您從 Premium 容量中移除工作區**，則模型與所有相關聯報表和儀表板將無法運作。

**雖然 Premium 容量中的每個查詢記憶體和時間條件約束較高**，但是強烈建議您使用篩選和交叉分析篩選器來限制視覺效果只顯示必要項目。

**後續步驟**

[什麼是 Power BI Premium？](service-premium.md)
[Power BI Premium 版本資訊](service-premium-release-notes.md)
[Microsoft Power BI Premium 白皮書](https://aka.ms/pbipremiumwhitepaper)
[規劃 Power BI Enterprise 部署白皮書](https://aka.ms/pbienterprisedeploy)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
