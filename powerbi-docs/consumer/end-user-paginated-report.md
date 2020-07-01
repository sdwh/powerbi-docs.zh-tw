---
title: Power BI 服務中的編頁報表
description: 描述編頁報表及如何在 Power BI 服務中檢視的文件
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: b5c9b36f003d22d4b1fda3ff11227d7f4c77f241
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236500"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Power BI 服務中的編頁報表

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

您已了解 [Power BI 報表](end-user-reports.md)，這些是您最可能遇到的報表類型。 不過，還有另一種類型的報表，稱為「編頁報表」  。 報表「設計師」  可以在 Premium 容量的工作區或該工作區的應用程式中與您共用編頁報表。 

## <a name="what-is-a-paginated-report"></a>什麼是編頁報表？

這些報表之所以稱為「編頁」  ，是因為其格式設定為適當符合列印頁面大小。 優點之一是即使資料表跨越多個頁面，這些報表也會以一個資料表來顯示所有資料。 編頁報表有時稱為「完美像素」，因為報表「設計師」  可以完全控制報表頁面配置。

在建立編頁報表時，報表「設計師」  實際上是在建立「報表定義」  。 它不包含資料。 它會指定要取得資料的位置、要取得哪些資料，以及如何顯示資料。 當您執行報表時，報表處理器會採用報表定義、擷取資料，並結合報表配置來產生報表。 有時候，報表會顯示預設資料。 其他時候，您必須先輸入參數，報表才會顯示任何資料。 

   ![報表的參數](./media/end-user-paginated-report/power-bi-report-parameters.png)

這通常屬於互動範圍 - 設定參數。 如果您是計費分析師，則可使用編頁報表來建立或列印發票。 如果您是銷售經理，則可使用編頁報表來依商店或銷售人員檢視訂單。 

這個簡單的編頁報表會在選取 [年]  參數之後，產生該年度收益。 

![簡單的單一參數報表](./media/end-user-paginated-report/power-bi-report-simple.png)

相較於編頁報表，Power BI 報表的互動性較高。 Power BI 報表允許隨選報表，並支援更多類型的視覺效果，包括 Power BI 視覺效果。

## <a name="identify-a-paginated-report"></a>識別編頁報表

在內容清單中及 [首頁] 登陸頁面上，編頁報表可以透過其圖示 ![編頁報表圖示](media/end-user-paginated-report/power-bi-report-icon.png) 加以識別。  編頁報表可以直接與您共用，或作為 [Power BI 應用程式](end-user-apps.md)的一部分共用。 如果報表「設計師」  授與您權限，則您將能夠重新共用編頁報表，並為您自己和其他人訂閱。

![顯示不同圖示的報表清單](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>與編頁報表互動

您與編頁報表互動的方式不同於其他報表。 您可以執行列印、書籤、匯出和註解之類的動作，但互動性較低。 通常，編頁報表需要您的輸入才能填入報表畫布。  其他時候，報表會顯示預設資料，且您可以輸入參數來查看不同的資料。

### <a name="print-a-paginated-report"></a>列印編頁報表

「編頁」  報表的格式設定為適當符合頁面大小並可適當進行列印。 您在瀏覽器中看到的內容，就是您在列印時所看到的內容。 此外，如果報表有一個很長的資料表，則即使該資料表跨越多個頁面也會列印整個資料表。 

編頁報表可以有許多頁面。 例如，此報表有 563 頁。 每頁都有精確的版面配置，每個發票一頁並重複頁首和頁尾。 當列印此報表時，您會在發票之間進行分頁。

   ![Tailspin Toys 編頁報表的第一頁](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>巡覽編頁報表

在此銷售訂單報表中，有三個參數：[商務類型]、[轉銷商] 和 [訂單號碼]。 

![具有三個參數的報表](./media/end-user-paginated-report/power-bi-parameter.png)

若要變更所顯示的資訊，請針對這三個參數輸入新的值，然後選取 [檢視報表]  。 在這裡，我們選取了 [Specialty bike shop] \(專業自行車店\)  、[Alpine Ski House]  和訂單號碼 [SO46085]  。 選取 [檢視報表]  會使用這個新的銷售訂單來重新整理報表畫布。

![變更參數](./media/end-user-paginated-report/power-bi-order.png)

新的銷售訂單會使用我們所選取的參數來隨即顯示。 

![新的銷售訂單](./media/end-user-paginated-report/power-bi-new-order.png)

某些編頁報表會有許多頁面。  您可以使用頁面控制項來巡覽報表。 

![頁面控制項](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>匯出編頁報表
您有各種匯出編頁報表的選項，包括 PDF、Word、XML、PowerPoint、Excel 等。 匯出時，會盡可能保留大部分的格式。 例如，匯出至 Excel、Word、PowerPoint、MHTML 和 PDF 的編頁報表會保留「完美像素」格式。 

![新的銷售訂單](./media/end-user-paginated-report/power-bi-exporting.png)

![四種不同的匯出類型](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>訂閱編頁報表
當您訂閱編頁報表時，Power BI 會傳送內含報表附件的電子郵件給您。 在您的訂閱設定中，選擇希望收到電子郵件的頻率：每天、每週、每小時或每月。 訂閱會包含整個報表輸出的附件，大小上限為 25 MB。 匯出整個報表或事先選擇參數。 從許多不同的附件類型中選擇，包括 Excel、PDF、PowerPoint 等。  

![訂閱的格式](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

- 在選取參數並選擇 [檢視報表]  之前，編頁報表可能會顯示為空白。

- 如果您沒有任何編頁報表，可能是因為沒有人與您共用這種類型的報表。 也可能表示系統管理員尚未為您啟用編頁報表。 

 

## <a name="next-steps"></a>後續步驟
- [Power BI 報表](end-user-reports.md)
- 有其他問題嗎？ 試試 [Power BI 社群](https://community.powerbi.com/)。

