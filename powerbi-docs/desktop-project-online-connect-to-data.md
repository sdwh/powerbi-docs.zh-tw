---
title: "Project Online：透過 Power BI Desktop 連接到資料"
description: "Project Online：透過 Power BI Desktop 連接到資料"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 745e474e9585c743406daa956220a9958cfeedca
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="project-online-connect-to-data-through-power-bi-desktop"></a>Project Online：透過 Power BI Desktop 連接到資料
您可以透過 Power BI Desktop 連接到 Project Online 中的資料。

### <a name="step-1-download-power-bi-desktop"></a>步驟 1：下載 Power BI Desktop
1. [下載 Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662)，然後執行安裝程式，在電腦上安裝 **Power BI Desktop**。

### <a name="step-2-connect-to-project-online-with-odata"></a>步驟 2：透過 OData 連接到 Project Online
1. 開啟 **Power BI Desktop**。
2. 在 [歡迎] 畫面上，選取 [取得資料]。
3. 選擇 [OData 摘要]，然後選取 [連接]。
4. 在 [URL] 方塊中，輸入您的 OData 摘要位址，然後按一下 [確定]。
   
   如果您的 Project Web App 網站位址類似 https://\<租用戶名稱\>.sharepoint.com/sites/pwa，您所輸入的 OData 摘要位址會是 https://\<租用戶名稱\>.sharepoint.com/sites/pwa/\_api/Projectdata。
   
   在此範例中，我們使用的是 https://contoso.sharepoint.com/sites/pwa/default.aspx
5. Power BI Desktop 會提示您驗證 Office 365 帳戶。 請選取組織帳戶，然後輸入您的認證。
   
   ![](media/desktop-project-online-connect-to-data/image.png)

從這裡，您可以選擇要連接的資料表並建立查詢。  要了解如何開始進行嗎？  下列部落格文章示範如何從 Project Online 資料建立燃盡圖。  該部落格文章使用 Power Query 連接到 Project Online，不過也適用於 Power BI Desktop。

[使用 Power Pivot 和 Power Query 為專案建立燃盡圖](http://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

