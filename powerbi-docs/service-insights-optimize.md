---
title: "最佳化 Power BI 快速深入剖析的資料"
description: "最佳化 Power BI 快速深入剖析的資料。 如果 Power BI 在您的資料中找不到深入剖析資訊，您可以執行下列一些作業"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/02/2017
ms.author: mihart
ms.openlocfilehash: 61901d0055c22540ec2f10bedbbb8cf641d606e9
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="optimize-your-data-for-power-bi-quick-insights"></a>最佳化 Power BI 快速深入剖析的資料
想要改善快速深入剖析結果嗎？  如果您是資料集擁有者，請嘗試下列︰

* 隱藏或取消隱藏資料集中的資料行。 Power BI 深入資訊摘要不會搜尋隱藏的資料行。  因此，請隱藏重複或不必要的資料行，並取消隱藏相關資料行。
* 使用混合的資料類型，例如名稱、時間、日期和數字。
* 避免 (或隱藏) 具有重複資訊的資料行。  這會浪費搜尋有意義模式的寶貴時間。  例如，一個資料行具有州名的完整拼法，而另一個資料行具有州名的縮寫。
* 您是否收到錯誤訊息，指出您的資料不具統計顯著性？  陽春型模型、資料不多的模型或不具日期或數值資料行的模型，就有可能發生這種情況。 若要產生深入解析，您的資料集至少必須有一個維度和一個量值。

### <a name="next-steps"></a>後續步驟
[Power BI 深入資訊摘要](service-insights.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

