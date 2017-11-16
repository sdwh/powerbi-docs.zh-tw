---
title: "Power BI 中的 DirectQuery for SAP HANA"
description: "搭配使用 DirectQuery 與 SAP HANA 時的考量"
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: d6f863df59d7374c792f1e1ac16db3a04ad99d87
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="directquery-and-sap-hana"></a>DirectQuery 和 SAP HANA
您可以使用 **DirectQuery** 直接連接到 **SAP HANA** 資料來源。

使用 **SAP HANA** 時，務必了解如何處理連接的某些層面，確保：

* SAP HANA 檢視包含非加法類量值 (例如，相異計數或平均值，而非簡單總和) 時，結果會如預期。
* 產生的查詢有效。

[Get Data]\(取得資料) 或 [查詢編輯器] 中所定義的查詢執行彙總時，最好先花一點時間釐清關聯式來源的行為 (例如 **SQL Server**)。 在下列範例中，[查詢編輯器] 中所定義的查詢會依 **ProductID** 傳回平均價格。

![](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

如果要將資料匯入至 Power BI (與使用 DirectQuery 比較)，會產生下列情況：

* 將資料匯入彙總層級，而彙總層級是由 [查詢編輯器] 中所建立的查詢所定義。 例如，產品的平均價格。 這會導致表格包含兩個可在視覺效果中使用的資料行 *ProductID* 和 *AveragePrice*。
* 在視覺效果中，會對該匯入的資料執行任何後續彙總 (例如 *Sum*、*Average*、*Min* 等)。  例如，在視覺效果上包括 *AveragePrice* 預設會使用 *Sum* 彙總，而且會傳回每個 *ProductID* 的 *AveragePrice* 的總和，在此情況下為 13.67。 這同樣適用於視覺效果上所使用的任何替代彙總函式 (例如 *Min*、*Average* 等)。 例如，*AveragePrice* 的 *Average* 傳回平均值 6.66、4 和 3 (這等同於 4.56)，而「不」是基礎資料表中 6 筆記錄的 *Price* 平均值 (這是 5.17)。

如果使用 **DirectQuery**，而非 Import，則會套用相同語意，而且結果完全相同：

* 如果是相同的查詢，則會向報告層呈現邏輯上完全相同的資料，即使未實際匯入資料也是一樣。
* 在視覺效果中，會再次從查詢對該邏輯資料表執行任何後續彙總 (*Sum*、*Average*、*Min* 等)。 同樣地，包含 *AveragePrice* 之 *Average* 的視覺效果一樣會傳回 4.56。

因此，現在讓我們考慮一下 **SAP HANA**。 Power BI 可以在 SAP HANA 中使用「分析檢視」和「計算檢視」，這兩者都可以包含量值。 但是，SAP HANA 的方法現在遵循先前所述的相同原則：[Get Data]\(取得資料) 或 [查詢編輯器] 中所定義的查詢將判斷資料可用，然後視覺效果中的任何後續彙總都是針對該資料，而且同樣適用於 Import 和 DirectQuery。

不過，基於 HANA 的本質，初始 [Get Data]\(取得資料) 對話方塊或 [查詢編輯器] 中所定義的查詢一律是彙總查詢，而且一般會包括將使用 HANA 檢視所定義之實際彙總的量值。

上述 SQL Server 範例的對等項就是有一個 HANA 檢視包含 **ID**、**ProductID**、**DepotID**，以及數個包含 **AveragePrice** 的量值 (檢視中定義為 [Average of Price]\(價格平均值))。

![](media/desktop-directquery-sap-hana/directquery-sap-hana_02.png)

在 [Get Data]\(取得資料) 體驗中，如果選取 **ProductID** 和 **AveragePrice** 量值，則會對檢視定義查詢，並要求該彙總資料 (在上述範例中，為求簡化，會使用不符合確切 HANA SQL 語法的虛擬 SQL)。 然後，在視覺效果中定義的任何進一步彙總都會進一步彙總這類查詢的結果。 同樣地，與上述針對 **SQL Server** 所述，這同時適用於 Import 和 DirectQuery 案例。 請注意，在 DirectQuery 案例中，從 [Get Data]\(取得資料) 或 [查詢編輯器] 的查詢將會用於傳送至 HANA 之單一查詢內的子選擇，因此在進一步彙總之前，不會實際讀入所有資料。

對 HANA 使用 DirectQuery 時，這會造成下列重要考量：

* 只要 HANA 中的量值是非加法類 (例如，而不是簡單 *Sum*、*Min* 或 *Max*)，就必須注意視覺效果中所執行的任何進一步彙總。
* 在 [Get Data]\(取得資料) 或 [查詢編輯器] 中，只應該包括必要資料行來擷取必要資料，並反映結果將是查詢的事實，而查詢必須是可傳送至 HANA 的合理查詢。 例如，如果選取許多資料行，但考量到後續視覺效果上可能需要這些資料行，則甚至針對 DirectQuery，簡單視覺效果將表示子選擇中所使用的彙總查詢將會包含這幾個資料行，而這樣的執行效果一般會非常差。

以下舉例說明。 在下列範例中，於 [Get Data]\(取得資料) 對話方塊中選取五個資料行 (CalendarQuarter、Color、LastName、ProductLine、SalesOrderNumber) 以及量值 OrderQuantity，表示稍後建立包含 Min OrderQuantity 的簡單視覺效果就會導致 HANA 的下列 SQL 查詢。 陰影部分是子選擇，其中包含 [Get Data]\(取得資料) / [查詢編輯器] 中的查詢。 如果這個子選擇提供極高的基數結果，則產生的 HANA 效能可能不佳。

![](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

因此，建議應該將 [Get Data]\(取得資料) 或 [查詢編輯器] 中所選取的項目限制為所需的項目，同時仍然會產生 HANA 的合理查詢。

### <a name="next-steps"></a>後續步驟
如需 DirectQuery 的詳細資訊，請參閱下列資源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [內部部署資料閘道](service-gateway-onprem.md)

