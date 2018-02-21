---
title: "使用 Power BI 連接到 Planview Enterprise"
description: Planview Enterprise for Power BI
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
ms.openlocfilehash: cd7026fe72bff40fd28aadf4ed3d2f9ee2b5d2fe
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>使用 Power BI 連接到 Planview Enterprise
使用 Planview Enterprise 內容套件，您可以全新的方式，直接在 Power BI 中視覺化資源和工作管理資料。 請使用 Planview Enterprise 登入認證以互動方式查看投資組合的費用、了解超出預算及預算不足的部分，以及清楚專案如何配合公司的策略優先順序。 您也可以擴充立即可用的儀表板和報表，取得對您而言最重要的深入資訊。

連接到 [Power BI 的 Planview Enterprise 內容套件](https://app.powerbi.com/getdata/services/planview-enterprise)

>[!NOTE]
>若要將 Planview Enterprise 資料匯入 Power BI，您必須是啟用 Reporting 入口網站檢視器功能之角色的 Planview Enterprise 使用者。 請參閱下列其他需求。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
    ![](media/service-connect-to-planview/get.png)
2. 在 [服務]  方塊中，選取 [取得] 。
   
    ![](media/service-connect-to-planview/services.png)
3. 在 Power BI 頁面上，選取 [Planview Enterprise]，然後選取 [取得]：  
    ![](media/service-connect-to-planview/planview.png)
4. 在 [Planview Enterprise URL] 文字方塊中，輸入您要使用的 Planview Enterprise 伺服器的 URL。 在 [Planview Enterprise 資料庫] 文字方塊中，輸入 Planview Enterprise 資料庫名稱，然後按一下 [下一步]。  
    ![](media/service-connect-to-planview/params.png)
5. 在 [驗證方法] 清單中，如未選取請選取 [Basic]  。 輸入帳戶的 [使用者名稱]  和 [密碼]  ，再選取 [登入] 。  
   ![](media/service-connect-to-planview/creds.png)
6. 在左窗格中，從儀表板清單中選取 [Planview Enterprise]。  
     Power BI 將 Planview Enterprise 資料匯入儀表板。 請注意，載入資料可能需要一些時間。  
    ![](media/service-connect-to-planview/dashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](power-bi-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="system-requirements"></a>系統需求
若要將 Planview Enterprise 資料匯入 Power BI，您必須是啟用 Reporting 入口網站檢視器功能之角色的 Planview Enterprise 使用者。 請參閱下列其他需求。

這個程序假設您已使用 Power BI 帳戶登入 Microsoft Power BI 的首頁。 如果您還沒有 Power BI 帳戶，請在 Power BI 的首頁建立新的免費 Power BI 帳戶，然後按一下 [取得資料]。

## <a name="next-steps"></a>後續步驟：

[開始使用 Power BI](service-get-started.md)

[取得 Power BI 的資料](service-get-data.md)