---
title: "使用 Power BI 連接到 Zuora"
description: Zuora for Power BI
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
ms.openlocfilehash: 22d490a58fd522b805d9709a1e697d1d2e89df6c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-zuora-with-power-bi"></a>使用 Power BI 連接到 Zuora
Zuora for Power BI 可讓您以視覺化方式顯示重要的營收、帳單與訂閱資料。 使用預設儀表板與報表來分析使用狀況趨勢、追蹤帳單與付款，以及監視週期性營收，或根據您自己的獨特儀表板與報告需求進行自訂。 

連接到 [Zuora](https://app.powerbi.com/getdata/services/Zuora) for Power BI。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
   ![](media/service-connect-to-zuora/getdata.png)
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![](media/service-connect-to-zuora/services.png)
3. 選取 [Zuora] \> [取得]。
   
   ![](media/service-connect-to-zuora/zuora.png)
4. 指定您的 Zuora URL。 這通常是 "https://www.zuora.com" ，請參閱以下關於[尋找這些參數](#FindingParams)的詳細資料。
   
   ![](media/service-connect-to-zuora/params.png)
5. 在 [ **驗證方法**] 選取 [ **基本** ]，然後輸入使用者名稱及密碼，再選取 [ **登入**]。
   
    ![](media/service-connect-to-zuora/creds.png)
6. 一經核准，匯入程序會自動開始。 完成時，新的儀表板、報表和模型會出現在瀏覽窗格中。 選取儀表板以檢視匯入的資料。
   
     ![](media/service-connect-to-zuora/dashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](service-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="whats-included"></a>包含的內容
此內容套件使用 Zuora AQUA API 來提取下列資料表︰

| 資料表 |  |  |
| --- | --- | --- |
| Account |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Product |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Usage |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

它也包含下列導出量值︰

| 量值 | 描述 | 虛擬計算 |
| --- | --- | --- |
| 帳戶︰付款 |根據付款有效日期之時間週期內的總付款金額。 |SUM (Payment.Amount) <br>WHERE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| 帳戶︰退款 |根據退款日期之時間週期內的總退款金額。 金額會以負數回報。 |-1*SUM(Refund.Amount)<br>WHERE<br>Refund.RefundDate =< TimePeriod.EndDate<br>AND    Refund.RefundDate >= TimePeriod.StartDate |
| 帳戶：付款淨值 |時間週期內的帳戶付款加上帳戶退款。 |Account.Payments + Account.Refunds |
| 帳戶：使用中的帳戶 |時間週期內的使用中帳戶計數。 訂閱必須已在時間週期開始日期當天或之前啟動。 |COUNT (Account.AccountNumber)<br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) –evergreen subscription |
| 帳戶：平均週期性營收 |每個使用中帳戶在時間週期內的總 MRR。 |Gross MRR / Account.ActiveAccounts |
| 帳戶：取消的訂閱 |時間週期內取消訂閱的帳戶計數。 |COUNT (Account.AccountNumber)<br>WHERE<br>Subscription.Status = "Cancelled"<br>AND    Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>AND    Subscription.CancelledDate >= TimePeriod.StartDate |
| 帳戶︰付款失敗 |付款失敗的總值。 |SUM (Payment.Amount)<br>WHERE<br>Payment.Status = "Error" |
| 營收排程項目︰已辨識的營收 |會計週期內已辨識的總營收。 |SUM (RevenueScheduleItem.Amount)<br>WHERE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| 訂閱：新訂閱 |時間週期內的新訂閱計數。 |COUNT (Subscription.ID)<br>WHERE<br>Subscription.Version = "1"<br>AND    Subscription.CreatedDate <= TimePeriod.EndDate<br>AND    Subscription.CreatedDate >= TimePeriod.StartDate |
| 發票︰發票項目 |發票項目費用金額在時間週期內的總計。 |SUM (InvoiceItem.ChargeAmount)<br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| 發票：課稅項目 |課稅項目課稅金額在時間週期內的總計。 |SUM (TaxationItem.TaxAmount)<br>WHERE<br>Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| 發票︰發票項目調整 |發票項目調整金額在時間週期內的總計。 |SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceItemAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceItemAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| 發票︰發票調整 |發票調整金額在時間週期內的總計。 |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.AdjustmentDate <= TimePeriod.EndDate<br>AND    InvoiceAdjustment.AdjustmentDate >= TimePeriod.StartDate |
| 發票︰帳目淨值 |發票項目、課稅項目、發票項目調整和發票調整在時間週期內的總和。 |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| 發票︰發票過時結餘 |已過帳的發票餘額總和。 |SUM (Invoice.Balance) <br>WHERE<br>    Invoice.Status = "Posted" |
| 發票︰帳目總值 |已過帳發票的發票項目費用金額在時間週期內的總和。 |SUM (InvoiceItem.ChargeAmount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate <= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate >= TimePeriod.StartDate |
| 發票︰調整總計 |與已過帳發票建立關聯之已處理的發票調整和發票項目調整總和。 |SUM (InvoiceAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>WHERE<br>    Invoice.Status = "Posted"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| 費率方案費用︰總 MRR |來自訂閱的每月週期性營收在時間週期內的總和。 |SUM (RatePlanCharge.MRR) <br>WHERE<br>    Subscription.Status != "Expired"<br>AND    Subscription.Status != "Draft"<br>AND    RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OR    RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>系統需求
需要 Zuora API 存取權。

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>尋找參數
提供您通常用來登入以存取 Zuora 資料的 URL。 有效的選項為：  

* https://www.zuora.com  
* https://www.apisandbox.zuora.com  
* 對應至服務執行個體的 URL  

## <a name="troubleshooting"></a>疑難排解
Zuora 內容套件會提取 Zuora 帳戶的許多不同層面。 如果您未使用某些功能，可能會看到對應的磚/報表空白。 如果載入時發生任何問題，請連絡 Power BI 支援人員。

## <a name="next-steps"></a>後續步驟
[開始使用 Power BI](service-get-started.md)

[取得 Power BI 中的資料](service-get-data.md)

