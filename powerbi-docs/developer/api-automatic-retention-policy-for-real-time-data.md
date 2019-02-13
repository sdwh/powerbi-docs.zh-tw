---
title: Power BI API 使用即時資料的自動保留原則
description: 了解 Power BI 服務中的自動保留原則
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 246feb1cb15d1688cab044151b50ba62db45c453
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762390"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>即時資料的自動保留原則

在 Power BI 服務的自動保留原則是查詢字串參數，讓預設保留原則可自動清除舊資料，同時保持新資料持續進入您的儀表板。 第一個保留原則稱為*先進先出 (FIFO)*。 當這原則啟用時，直到達到 200,000 個資料列之前，會將資料收集在資料表中。 一旦資料超過 200,000 個資料列，最舊的資料列將從資料集中移除。 這使得 200,000 和 210,000 個資料列之間只保留最新的資料。  
  
<center>

![保留原則](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

當您第一次建立資料集時，即啟用保留原則。 您所要做的就是將 “default retention policy” 查詢參數新增至您的 POST 資料集呼叫，並將其設為 *basicFIFO*。  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}