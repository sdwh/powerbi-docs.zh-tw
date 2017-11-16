---
title: "在 Power BI 報表伺服器中存取共用資料集作為 OData 摘要"
description: "Power BI 報表可以連線到不同的資料來源。 根據使用資料的方式而定，可以使用不同的資料來源。"
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 11/01/2017
ms.author: asaxton
ms.openlocfilehash: f31d37b6fe9c0e4695719b9bbaa13a2c8deabc75
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="accessing-shared-datasets-as-odata-feeds-in-power-bi-report-server"></a>在 Power BI 報表伺服器中存取共用資料集作為 OData 摘要
您可以從 Power BI Desktop 使用 OData 摘要存取共用資料集。

1. 您可以使用 OData 摘要 URL 連線到 OData 來源。
   
    ![報表伺服器 OData 摘要來源](media/access-dataset-odata/report-server-odata-feed.png)
2. 您將資料帶入 Power BI Desktop 之後，可以在 [查詢編輯器] 中對它進行修改。
   
    ![Power BI Desktop 查詢編輯器與 OData 摘要](media/access-dataset-odata/report-server-odata-results-query-editor.png)
3. 現在您可以使用資料來設計報表。
   
    ![Power BI Desktop 報表設計與 OData 摘要](media/access-dataset-odata/report-server-odata-power-bi-desktop-report-design.png)

務必使用 [進階選項]，以便開啟 [開啟類型資料行]，並且據以在 Power Query 中格式化資料行以符合您的需求。

深入了解[在 Power BI Desktop 中連線到 OData 欄位](../desktop-connect-odata.md)。

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

