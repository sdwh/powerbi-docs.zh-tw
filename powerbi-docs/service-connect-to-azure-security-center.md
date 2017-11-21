---
title: "使用 Power BI 連接到 Azure 資訊安全中心"
description: Azure Security Center for Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
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
ms.author: yshoukry
ms.openlocfilehash: d052bc054e55eabfab53ad3b1ac9229f0a750785
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-azure-security-center-with-power-bi"></a>使用 Power BI 連接到 Azure 資訊安全中心
將您的 Azure 安全性資料與 Power BI 連接，以深入了解您的 Azure 工作負載安全性。 Power BI 會自動建立以 Azure 資訊安全中心資料為基礎的儀表板與報表，讓您分析及瀏覽資料。

連接到 Power BI 的 [Azure 資訊安全中心內容套件](https://app.powerbi.com/getdata/services/azure-security-center)。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
   ![](media/service-connect-to-azure-security-center/getdata.png)
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![](media/service-connect-to-azure-security-center/services.png)
3. 選取 [Azure 資訊安全中心] \> [取得]。
   
   ![](media/service-connect-to-azure-security-center/asc.png)
4. 指定您的訂用帳戶 ID。 請參閱以下關於[尋找這些參數](#FindingParams)的詳細資訊。
   
   ![](media/service-connect-to-azure-security-center/params.png)
5. 針對 [驗證方法] 選取 [oAuth2] \> [登入]。 出現提示時，請輸入您的 Azure 認證。
   
    ![](media/service-connect-to-azure-security-center/creds.png)
6. 一經核准，匯入程序會自動開始。 完成時，新的儀表板、報表和模型會出現在瀏覽窗格中。 選取儀表板以檢視匯入的資料。
   
     ![](media/service-connect-to-azure-security-center/dashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](service-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="whats-included"></a>包含的內容
內容套件包含資源安全性狀態、警示分析與預防分析的深入資訊。

## <a name="system-requirements"></a>系統需求
此內容套件需要有已啟用 Azure 資訊安全中心之訂用帳戶 ID 的存取權。 如需詳細資訊，請參閱 Azure 入口網站的 [Azure 資訊安全中心](https://portal.azure.com/#blade/Microsoft_Azure_Security/SecurityDashboardStartBladeV2)。

內容套件也需要使用者以組織帳戶 (而不是個人帳戶) 進行連線。

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>尋找參數
有兩個簡單的方法可尋找您的訂用帳戶 ID。

1. 從 https://portal.azure.com -&gt; [瀏覽] -&gt; [訂閱] -&gt; [訂閱識別碼]。
2. 從 https://manage.windowsazure.com -&gt; [設定] -&gt; [訂閱識別碼]。

您的訂閱識別碼會是一組很長的數字和字元，類似上述步驟 \#4 中的範例。 

## <a name="troubleshooting"></a>疑難排解
視帳戶的大小而定，資料可能需要一些時間來載入。 如果您在登入期間遇到錯誤，請確認您的參數，並確認帳戶已啟用 Azure 資訊安全中心。

如果內容套件能載入，但未顯示任何資料，請確認您使用組織帳戶進行連線。 雖然 Azure 資訊安全中心支援個人帳戶，但如果使用者以非組織的帳戶進行連線，API (以及內容套件) 不會傳回預期的值。 請提供組織帳戶存取權，然後再次嘗試連線。

## <a name="next-steps"></a>後續步驟
[開始使用 Power BI](service-get-started.md)

[取得 Power BI 中的資料](service-get-data.md)

