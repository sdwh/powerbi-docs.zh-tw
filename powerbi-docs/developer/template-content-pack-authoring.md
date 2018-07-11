---
title: 在 Power BI 中撰寫範本內容套件
description: 範本內容套件撰寫
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: 02c4725617960474cff7a9a1452861d1ab5d5b8d
ms.sourcegitcommit: 6407e053c2c6c6fdb212b059693e90fefbaaadec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36290867"
---
# <a name="author-template-content-packs-in-power-bi"></a>在 Power BI 中撰寫範本內容套件
撰寫範本內容套件會使用 Power BI Desktop 和 PowerBI.com。 您的內容套件具有四個元素︰

* 查詢可讓您[連接](../desktop-connect-to-data.md)和[轉換](../desktop-query-overview.md)資料，以及定義[參數](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)  
* 資料模型可建立[關聯性](../desktop-create-and-manage-relationships.md)、[量值](../desktop-measures.md)和問與答改進功能  
* 報表[頁面](../desktop-report-view.md)包含可讓您深入剖析資料的視覺效果和篩選器  
* 
  [儀表板](../service-dashboards.md)和[磚](../service-dashboard-create.md)可提供包含的深入剖析資訊概觀  

您可能以現有 Power BI 功能的角度熟悉每項元素。 在建置內容套件時，您需要針對每個層面考慮其他事項，請參閱下列各節以取得詳細資訊。

<a name="queries"></a>

## <a name="queries"></a>查詢
針對範本內容套件，在 Power BI Desktop 中開發的查詢會用來連接至資料來源和匯入資料。 系統需要這些查詢才能傳回一致的結構描述，並針對排程的資料重新整理支援這些查詢 (不支援直接查詢)。

範本內容套件針對每個內容套件僅支援一個資料來源，因此請仔細定義您的查詢。 單一資料來源定義為需要相同驗證的來源。 如果所有的呼叫對象都是相同的 API 端點並使用相同的驗證，您就可以在不同的查詢中進行多個 API 呼叫。 Power BI 內容套件不支援多個需要不同驗證的來源。

### <a name="connect-to-your-api"></a>連接到您的 API
若要開始，您需要從 Power BI Desktop 連接到您的 API，開始建置您的查詢。

您可以在 Power BI Desktop 中使用立即可用的資料連接器，連接到您的 API。 您可以使用 Web 資料連接器 (取得資料 -> Web) 連接到您的 Rest API，或使用 OData 連接器 (取得資料 -> OData 摘要) 連接到 OData 摘要。 請注意，只有當您的 API 支援基本驗證時，這些連接器才是立即可用。

> [!NOTE]
> 如果您的 API 使用任何其他驗證類型，例如 OAuth 2.0 或 Web API 金鑰，則您必須開發自己的資料連接器，才能讓 Power BI Desktop 順利連線並向您的 API 驗證。 如需如何為自己的內容套件開發專屬資料連接器的詳細資料，請參閱[這裡](https://aka.ms/DataConnectors)的資料連接器文件。 
> 
> 

### <a name="consider-the-source"></a>考慮來源
查詢會定義將包含在資料模型中的資料。 根據您的系統大小，這些查詢也應包含篩選器，以確定您的客戶正在處理符合商務案例且可管理的大小。

Power BI 內容套件可以平行方式針對多個使用者同時執行多個查詢。  事先規劃您的節流和並行策略，並詢問我們如何讓您的內容套件具備容錯功能。

### <a name="schema-enforcement"></a>結構描述強制執行
請確定您的查詢可在系統中彈性變更，重新整理時結構描述中的變更可能會中斷模型。 如果來源可能會針對某些查詢傳回 Null/遺失的結構描述結果，請考慮傳回空白資料表，或擲回對使用者有意義的自訂錯誤訊息。

### <a name="parameters"></a>參數
Power BI Desktop 中的[參數](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)可讓您的使用者提供輸入值，該值可自訂使用者擷取的資料。 預先考慮參數可避免在投入時間建置詳細查詢或報表之後的重新作業。

> [!NOTE]
> 範本內容套件目前僅支援文字參數。 您可以在開發期間使用其他參數類型，但在[測試](template-content-pack-testing.md#templates)部分期間，使用者所提供的所有值都會是常值。
> 
> 

### <a name="additional-query-tips"></a>其他查詢秘訣
* 請確定已適當輸入所有資料行  
* 資料行具有資訊性名稱 (請參閱問與答)  
* 針對共用邏輯，請考慮使用函數或查詢  
* 服務目前不支援隱私權等級，如果您收到有關隱私權等級的提示，您可能需要將查詢重新撰寫為使用相對路徑  

## <a name="data-model"></a>資料模型
妥善定義的資料模型可確定您的客戶可以更輕鬆直覺的方式與內容套件互動。 在 Power BI Desktop 中建立資料模型。

> [!NOTE]
> 您應該在[查詢](#queries)中完成大部分的基本模型 (鍵入、資料行名稱)。
> 
> 

### <a name="qa"></a>問與答
模型也會影響問與答可為客戶提供的結果品質。 請確定您將同義字新增至常用資料行，並在[查詢](#queries)中正確命名資料行。

### <a name="additional-data-model-tips"></a>其他資料模型秘訣
* 所有值資料行都已套用格式設定
    >[!NOTE]
    >您應該在查詢中套用類型。  
* 所有量值都已套用格式設定  
* 已設定預設摘要。 特別是「不摘要」(如果適用) (例如針對唯一值)  
* 已設定資料類別 (如果適用)  
* 已視需要設定關聯性  

## <a name="reports"></a>報表
報表頁面可針對內容套件中包含的資料提供其他深入剖析資訊。 使用報表頁面回答內容套件嘗試解決的關鍵商務問題。 使用 Power BI Desktop 建立報表。

> [!NOTE]
> 一個內容套件中只能包含一份報表，請利用不同頁面來呼叫案例的特定區段。
> 
> 

### <a name="additional-report-tips"></a>其他報表秘訣
* 在每頁中使用多個視覺特效以供交叉篩選  
* 仔細對齊視覺效果 (沒有重疊)  
* 將頁面設為 "4:3" 或 "16:9" 配置模式  
* 所有顯示的彙總都具有數字層面的意義 (平均值、唯一值)  
* 切割可產生合理的結果  
* 至少在頂端報表中顯示標誌  
* 盡可能以客戶的色彩配置設計項目  

<a name="dashboard"></a>

## <a name="dashboard"></a>儀表板
儀表板是與您的客戶與內容套件互動的重點。 其中應包含所包含內容的概觀，特別是商務案例的重要指標。

若要建立範本內容套件的儀表板，您只要透過 [取得資料] > [檔案] 上傳您的 PBIX，或直接從 Power BI Desktop 發行即可。

> [!NOTE]
> 範本內容套件目前針對每個內容套件需要單一報表和資料集。 請勿將內容從多個報表/資料集釘選到在內容套件中使用的儀表板。
> 
> 

### <a name="additional-dashboard-tips"></a>其他儀表板秘訣
* 在釘選時維持相同的佈景主題，讓儀表板上的磚具有一致性  
* 將標誌釘選到佈景主題，讓消費者了解套件來源  
* 可供大部分螢幕解析度使用的建議配置是 5-6 個小型磚的寬度  
* 所有儀表板磚都應該具有適當的標題/副標題  
* 針對水平或垂直等不同情況考慮儀表板中的群組  

<a name="restrictions"></a>

## <a name="summary-of-restrictions"></a>限制摘要
如以上各節所列，目前範本內容套件具有一些限制︰  

| 支援 | *不支援* |
| --- | --- |
| 在 PBI Desktop 中建置的資料集 |*來自其他內容套件或輸入的資料集，例如 Excel 檔案* |
| 針對雲端排程的資料重新整理支援的資料來源 |*不支援直接查詢或內部部署連線* |
| 適時傳回一致結構描述或錯誤的查詢 |*動態或自訂的結構描述* |
| 每個資料集一個資料來源 |*多個資料來源，例如偵測為多個資料來源的交互式 Web 應用程式 (Mashup) 或 URL* |
| 輸入文字的參數 |*其他參數類型 (例如日期) 或「允許的值清單」* |
| 一個儀表板、報表和資料集 |*多個儀表板、報表或資料集* |

## <a name="next-step"></a>下一個步驟
[內容套件測試和提交](template-content-pack-testing.md)

