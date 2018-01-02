---
title: "大型資料集的 Power BI Premium 支援"
description: "Power BI Premium 現在最多支援 10 GB 的資料集。"
services: powerbi
documentationcenter: 
author: MarkMcGeeAtAquent
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/11/2017
ms.author: v-mamcge
ms.openlocfilehash: 82ac4382fe80d83b60705f135b50738718f28876
ms.sourcegitcommit: 7eb15c813a0d14322cb1316bb7aab23cbc13aae6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2017
---
# <a name="power-bi-premium-support-for-large-datasets"></a>大型資料集的 Power BI Premium 支援

Power BI Premium 支援上傳大小最多為 10 GB 的 Power BI Desktop (.pbix) 檔案。 若要使用大型資料集，請將它發行至指派給 Premium 容量的工作區。
 
## <a name="best-practices"></a>最佳作法

本節描述使用大型資料集的最佳做法。

針對您的容量，**大型模型可能需要極大量資源**；建議任何大於 1 GB 的模型至少要有 P1 SKU。 下表描述各種 .pbix 大小的建議 SKU：


   |SKU  |.pbix 大小   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3    | 最多 10 GB   |



**.pbix 檔案以高度壓縮狀態呈現資料**。 載入至記憶體時，資料可能會展開多次，而且從該處，在資料重新整理期間，資料可能會再展開幾次。

**排程重新整理大型資料集可能需要很長的時間**，而且需要極大量資源。 因此，請不要排程太多重疊重新整理。 另請注意，針對此容量的所有資料集，排程重新整理作業的逾時已加倍到四個小時。

如果自上次使用資料集以來已有一段時間，則**大型資料集的初始報表負載可能需要很長的時間**，因為會將模型載入至 Premium 容量的記憶體。 較長載入之報表的載入列會顯示載入進度。

**如果您從 Premium 容量中移除工作區**，則模型與所有相關聯報表和儀表板將無法運作。

**雖然 Premium 容量中的每個查詢記憶體和時間條件約束較高**，但是強烈建議您使用篩選和交叉分析篩選器來限制視覺效果只顯示必要項目。

## <a name="next-steps"></a>後續步驟
[何謂 Power BI Premium](service-premium.md)  
[Power BI Premium 版本資訊](service-premium-release-notes.md)  
[Microsoft Power BI Premium 白皮書](https://aka.ms/pbipremiumwhitepaper)  
[Planning a Power BI Enterprise Deployment (規劃 Power BI 企業部署) 技術白皮書](https://aka.ms/pbienterprisedeploy)  
[Pro 延長試用版啟用](service-extended-pro-trial.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
