---
title: "使用 Power BI 連接到 Microsoft Azure 企業版"
description: "Power BI 的 Microsoft Azure 企業版"
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
ms.openlocfilehash: 040b72422b3267fcc4e909244b1a51fb48edfc81
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="connect-to-microsoft-azure-enterprise-with-power-bi"></a>使用 Power BI 連接到 Microsoft Azure 企業版
使用 Power BI 內容套件探索並監控 Power BI 中的 Microsoft Azure 企業版資料。 資料會自動每天重新整理一次。

連接到 Power BI 的 [Microsoft Azure 企業版內容套件](https://app.powerbi.com/getdata/services/azure-enterprise)。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
    ![](media/service-connect-to-azure-enterprise/getdata.png)
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![](media/service-connect-to-azure-enterprise/services.png)
3. 選取 [Microsoft Azure 企業版] \> [取得]。
   
   ![](media/service-connect-to-azure-enterprise/mazureenterprise.png)
4. 提供 Azure 環境 URL、要匯入的月份數資料和 Azure 企業版的註冊號碼。 Azure 環境 URL 會是 `https://ea.azure.com` 或 `https://ea.windowsazure.cn`。 請參閱以下關於[尋找這些參數](#FindingParams)的詳細資訊。
   
    ![](media/service-connect-to-azure-enterprise/params.png)
5. 提供連接用的存取金鑰。 註冊金鑰位於 Azure EA 入口網站。
   
    ![](media/service-connect-to-azure-enterprise/creds.png)
6. 匯入程序會自動開始。 完成時，新的儀表板、報表和模型會出現在瀏覽窗格中。 選取儀表板以檢視匯入的資料。
   
   ![](media/service-connect-to-azure-enterprise/dashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](power-bi-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="whats-included"></a>包含的內容
Azure Enterprise 內容套件包含每月報告資料，其範圍是連接流程期間所提供的月數。 範圍是移動的視窗，以便重新整理資料集時，將會更新包含的日期。

## <a name="system-requirements"></a>系統需求
內容套件需要存取 Azure 入口網站中的 企業版功能。

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>尋找參數
能夠檢視帳單資訊的 EA Direct、合作夥伴和間接客戶都可以取得 Power BI 報表。 請閱讀下文以取得尋找連接流程所有預期值的詳細資料。

**Azure 環境 URL**

* 這個值通常是 https://ea.azure.com，但只要確認登入之後就可以檢查 URL。
  
    ![](media/service-connect-to-azure-enterprise/params3.png)

**月份數**

* 這應該是介於 1 到 36 的數字，代表您要匯入的資料月數 (從今天起算)。

**註冊號碼**

* 這是您的 Azure 企業版註冊號碼，位於 [Azure 企業版入口網站](https://ea.azure.com/)主畫面的 [註冊詳細資料] 底下。
  
    ![](media/service-connect-to-azure-enterprise/params2.png)

**存取金鑰**

* 金鑰位在 Azure 企業版入口網站的 [下載使用量] > [API 存取金鑰]。
  
    ![](media/service-connect-to-azure-enterprise/creds2.png)

**其他說明**

* 如需設定 Azure 企業版 Power BI 套件的其他說明，請登入 Azure Enterprise 入口網站，以檢視 ＜說明＞下的 API 說明檔案，以及在 [報表] -> [下載使用量] -> [API 存取金鑰] 下取得其他指示。

## <a name="next-steps"></a>後續步驟
[開始使用 Power BI](service-get-started.md)

[取得 Power BI 中的資料](service-get-data.md)

