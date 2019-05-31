---
title: Tips for authoring template apps in Power BI (preview) (在 Power BI 中撰寫範本應用程式的提示 (預覽))
description: 有關如何撰寫查詢、資料模型、報表和儀表板，來製作高品質範本應用程式的提示
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/19/2019
ms.author: maggies
ms.openlocfilehash: 83049a16ecd42b41375da57a5a99a374596a9846
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514853"
---
# <a name="tips-for-authoring-template-apps-in-power-bi-preview"></a>Tips for authoring template apps in Power BI (preview) (在 Power BI 中撰寫範本應用程式的提示 (預覽))

當您在 Power BI 中[撰寫自己的範本應用程式](service-template-apps-create.md)時，有一部分重點是建立工作區、進行測試和生產的邏輯。 而另一個重點則明顯是撰寫報表和儀表板。 撰寫程序可以細分成四大部分。 在這幾個部分投入心力能讓您建立最佳的範本應用程式：

* 您可利用**查詢**來將資料[連線](desktop-connect-to-data.md)和[轉換](desktop-query-overview.md)，以及定義[參數](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)。 
* 您可在**資料模型**中建立[關聯性](desktop-create-and-manage-relationships.md)、[量值](desktop-measures.md)和問與答改善項目。  
* **[報表頁面](desktop-report-view.md)** 包含可提供資料見解的視覺效果和篩選。  
* **[儀表板](consumer/end-user-dashboards.md)** 和[磚](service-dashboard-create.md)能為包含的見解提供概觀。
* 範例資料可讓您的應用程式設定為可探索在安裝之後立即。

您可能以現有 Power BI 功能的角度熟悉每項元素。 在建置範本應用程式時，每項元素都有應考量的其他事項。 如需更多詳細資料，請參閱以下各節。

<a name="queries"></a>

## <a name="queries"></a>查詢
針對範本應用程式，在 Power BI Desktop 中開發的查詢會用來連線至資料來源和匯入資料。 系統需要這些查詢才能傳回一致的結構描述，並針對排程的資料重新整理支援這些查詢 (不支援 DirectQuery)。

### <a name="connect-to-your-api"></a>連接到您的 API
若要開始，您需要從 Power BI Desktop 連線到您的 API，開始建置您的查詢。

您可以在 Power BI Desktop 中使用立即可用的資料連接器，連接到您的 API。 您可以使用 Web 資料連接器 (取得資料 -> Web) 連接到您的 Rest API，或使用 OData 連接器 (取得資料 -> OData 摘要) 連接到 OData 摘要。 只有當您的 API 支援基本驗證時，這些連接器才具現成可用性。

> [!NOTE]
> 如果您的 API 使用任何其他驗證類型，例如 OAuth 2.0 或 Web API 金鑰，則您必須開發自己的資料連接器，才能讓 Power BI Desktop 順利連線並向您的 API 驗證。 您的自訂連接器必須加入 PBI 服務確實範本應用程式安裝程式的存取。 <br> 如需如何為自己的範本應用程式開發專屬資料連接器的詳細資料，請參閱[資料連接器文件](https://aka.ms/DataConnectors)。 
>
>

### <a name="consider-the-source"></a>考慮來源
查詢會定義將包含在資料模型中的資料。 根據您的系統大小，這些查詢也應包含篩選器，以確定您的客戶正在處理符合商務案例且可管理的大小。

Power BI 範本應用程式可以平行方式針對多個使用者同時執行多個查詢。  事先規劃您的節流和並行策略，並詢問我們如何讓您的範本應用程式具備容錯功能。

### <a name="schema-enforcement"></a>結構描述強制執行
請確定您的查詢可在系統中彈性變更，重新整理時結構描述中的變更可能會中斷模型。 如果來源可能會針對某些查詢傳回 Null 或遺失的結構描述結果，請考慮傳回空白資料表或有意義的自訂錯誤訊息。

### <a name="parameters"></a>參數
Power BI Desktop 中的[參數](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)可讓您的使用者提供輸入值，該值可自訂使用者擷取的資料。 預先考慮參數可避免在投入時間建置詳細查詢或報表之後的重新作業。

> [!NOTE]
> 範本應用程式支援 Any 和 Binary 以外的所有參數。
>

### <a name="additional-query-tips"></a>其他查詢秘訣

* 確認鍵入所有資料行的內容均正確。
* 資料行具有資訊性名稱 (請參閱[問與答](#qa))。  
* 針對共用邏輯，請考慮使用函式或查詢。  
* 服務目前不支援隱私權等級。 如果您收到有關隱私權等級的提示，則可能必須重寫查詢以使用相對路徑。  

## <a name="data-models"></a>資料模型

妥善定義的資料模型可確保您的客戶可以更輕鬆直覺的方式與範本應用程式互動。 在 Power BI Desktop 中建立資料模型。

> [!NOTE]
> 您應該在[查詢](#queries)中完成大部分的基本模型 (鍵入、資料行名稱)。

### <a name="qa"></a>問與答
模型也會影響問與答可為客戶提供的結果品質。 請確定您將同義字新增至常用資料行，並在[查詢](#queries)中正確命名資料行。

### <a name="additional-data-model-tips"></a>其他資料模型秘訣

確認您已：

* 將格式化套用到所有值資料行。 套用查詢中的類型。  
* 將格式化套用到所有量值。
* 設定預設摘要。 特別是「不摘要」(如果適用) (例如針對唯一值)。  
* 設定資料類別 (如果適用)。  
* 設定關聯性 (如有需要)。  

## <a name="reports"></a>報表
報表頁面可針對範本應用程式中包含的資料提供其他見解。 使用報表頁面回答範本應用程式嘗試解決的關鍵商務問題。 使用 Power BI Desktop 建立報表。


### <a name="additional-report-tips"></a>其他報表秘訣

* 在每頁中使用多個視覺特效以供交叉篩選。  
* 仔細對齊視覺效果 (沒有重疊)。  
* 將頁面設為 "4:3" 或 "16:9" 配置模式。  
* 顯示的所有彙總都具有數字層面的意義 (平均值、唯一值)。  
* 切割可產生合理的結果。  
* 至少在頂端報表中顯示標誌。  
* 盡可能以客戶的色彩配置設計項目。  

<a name="dashboard"></a>

## <a name="dashboards"></a>儀表板
儀表板是與您的客戶與範本應用程式互動的重點。 其中應包含所包含內容的概觀，特別是商務案例的重要指標。

若要建立範本應用程式的儀表板，您只要透過 [取得資料] > [檔案] 上傳您的 PBIX，或直接從 Power BI Desktop 發佈即可。


### <a name="additional-dashboard-tips"></a>其他儀表板秘訣

* 在釘選時維持相同的佈景主題，讓儀表板上的磚具有一致性。  
* 將標誌釘選到佈景主題，讓消費者了解套件來源。  
* 可供大部分螢幕解析度使用的建議配置是 5-6 個小型磚的寬度。  
* 所有儀表板磚都應該具有適當的標題/副標題。  
* 針對水平或垂直等不同情況考慮儀表板中的群組。  

## <a name="sample-data"></a>範例資料
範本應用程式，應用程式的建立階段，過程包裝快取資料的應用程式工作區中：

* 可讓安裝程式，以了解的功能和應用程式的用途，再將資料連接。
* 建立磁碟機要進一步探索應用程式功能，這樣會導致連接的應用程式資料集的安裝程式的體驗。

我們建議品質範例資料建立應用程式之前。 請確定應用程式報表和儀表板填入資料。

## <a name="publishing-on-appsource"></a>在 AppSource 上發佈
範本的應用程式可以在 AppSource 上發佈，應用程式提交至 AppSource 之前，請遵循下列方針：

* 請確定您建立的範本應用程式更吸引人的範例資料，以了解應用程式可以執行安裝程式 （空的報表和儀表板不核准）。
範本的應用程式支援的範例資料的唯一應用程式，請務必檢查靜態應用程式的核取方塊。 [深入了解](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* 已驗證的小組遵循其中包括認證和連接到資料所需參數的指示。
* 應用程式必須包含應用程式圖示，在 Power BI，並在 CPP 供應項目。 [深入了解](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* 設定登陸頁面。 [深入了解](https://docs.microsoft.com/power-bi/service-template-apps-create#create-the-test-template-app)
* 請務必遵循文件[Power BI 應用程式供應項目](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer)。
* 如果儀表板是您的應用程式的一部分，請確定它不是空白。
* 安裝應用程式使用的應用程式連結，送出之前，請確定您可以將資料集的連接，而您計劃是應用程式體驗。
* 上傳之前 bpix 到範本的應用程式工作區，請確定要卸除任何不必要的連接。
* 請依照下列 Power BI[報表和視覺效果的最佳設計做法](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-best-practices)以達到最大的影響，在您的使用者及獲准發佈。

## <a name="known-limitations"></a>已知的限制

| 特徵 | 已知的限制 |
|---------|---------|
|內容：資料集   | 只應剛好出現一個資料集。 只允許 Power BI Desktop (.pbix 檔案) 中建置的資料集。 <br>不支援：來自其他範本應用程式的資料集、跨工作區資料集、編頁報表、Excel 活頁簿 |
|內容：儀表板 | 不允許即時磚 （亦即，不支援推播或串流資料集） |
|內容：資料流程 | 不支援：資料流程 |
|來自檔案的內容 | 只允許 PBIX 檔案。 <br>不支援：.rdl 檔案 (編頁報表)、Excel 活頁簿   |
| 資料來源 | 允許針對雲端排程的資料重新整理支援的資料來源。 <br>不支援： <li> DirectQuery</li><li>即時連線 (非 Azure AS)</li> <li>在內部部署資料來源 （個人和企業閘道不支援）</li> <li>即時 （推送資料集不支援）</li> <li>複合模型</li></ul> |
| 資料集：跨工作區 | 不允許跨工作區資料集  |
| 查詢參數 | 不支援：資料集類型區塊重新整理作業的 "Any" 和 "Binary" 類型參數 |
| 自訂視覺效果 | 只支援公開可用的自訂視覺效果。 不支援[組織自訂視覺效果](power-bi-custom-visuals-organization.md) |

## <a name="next-steps"></a>後續步驟

[What are Power BI template apps? (preview)](service-template-apps-overview.md) (什麼是 Power BI 範本應用程式 (預覽))
