---
title: "使用 Power BI 連接到 Office365Mon"
description: Office365Mon for Power BI
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
ms.openlocfilehash: ffff9747e9c24efd51c3ae3d10714de590170523
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-office365mon-with-power-bi"></a>使用 Power BI 連接到 Office365Mon
有了 Power BI 與 Office365Mon 內容套件，便能輕鬆分析您的 Office 365 中斷和健康狀況效能資料。 Power BI 會擷取您的資料 (包括中斷與健康狀況探查)，然後根據該資料建置現成的儀表板與報表。

連接至適用於 Power BI 的 [Office365Mon 內容套件](https://app.powerbi.com/groups/me/getdata/services/office365mon)。

>[!NOTE]
>需要 Office365Mon 管理帳戶，才能連接並載入 Power BI 內容套件。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. 選取 [Office365Mon] \> [取得]。
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. 針對 [驗證方法] 選取 [oAuth2] \> [登入]。
   
   出現提示時，輸入 Office365Mon 管理認證，並遵循驗證程序。
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Power BI 匯入資料之後，您會在左側瀏覽窗格中看到新的儀表板、報表和資料集。 新的項目會以黃色星號 \* 標示，選取 Office365Mon 項目。
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](power-bi-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="troubleshooting"></a>疑難排解
如果您使用 Office365Mon 訂用帳戶認證登入之後收到 **「登入失敗」** 的錯誤，則您使用的帳戶沒有權限可從您的帳戶擷取 Office365Mon 訂用帳戶資料。 請確認它是系統管理員帳戶，然後重試一次。

## <a name="next-steps"></a>後續步驟
[開始使用 Power BI](service-get-started.md)

[取得 Power BI 的資料](service-get-data.md)

