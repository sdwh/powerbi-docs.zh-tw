---
title: Power BI 中的自動化機器學習 (預覽)
description: 了解如何使用 Power BI 中的自動化機器學習 (AutoML)
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236268"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Power BI 中的自動化機器學習 (預覽)

適用於資料流程的自動化機器學習 (AutoML) 可讓商務分析師直接在 Power BI 中定型、驗證和叫用機器學習模型。 它包含建立新 ML 模型的簡單體驗，讓分析師可以使用其資料流程來指定用於定型模型的輸入資料。 此服務會自動擷取最相關的功能、選取適當的演算法，並調整和驗證 ML 模型。 在模型定型之後，Power BI 會自動產生一份含驗證結果的報表，以向分析師說明效能和結果。 接著，您即可針對資料流程內的任何新資料或更新資料來叫用模型。

![機器學習畫面](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

自動化機器學習僅適用於 Power BI Premium 和 Power BI Embedded 容量上裝載的資料流程。 在此預覽中，AutoML 可讓您為二元預測、分類和迴歸模型進行機器學習模型的定型。

## <a name="working-with-automl"></a>使用 AutoML

[Power BI 資料流程](service-dataflows-overview.md)提供適用於巨量資料的自助資料準備。 AutoML 可讓您直接在 Power BI 內利用資料準備工作來建立機器學習模型。

Power BI 中的 AutoML 可讓資料分析師單純使用 Power BI 的技能，透過簡化體驗來使用資料流程建立機器學習模型。 Power BI 會將建立 ML 模型所需的大部分資料科學自動化、透過邊界來確保產生的模型具有良好品質，並讓您取得 ML 模型建立所用程序的完整見解。

AutoML 支援建立資料流程的**二元預測**、**分類**和**迴歸**模型。 上述是監督式機器學習模型的類型，這表示它們會從過去觀察的已知結果中學習，以預測其他觀察的結果。 您會使用一組含已知結果**標示**的記錄，作為定型 AutoML 模型的輸入資料集。

Power BI 中的 AutoML 會整合 [Azure Machine Learning 服務](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml)的[自動化 ML](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml)，以建立您的 ML 模型。 不過，您不需要 Azure 訂用帳戶，就能在 Power BI 中使用 AutoML。 ML 模型的定型和裝載程序完全由 Power BI 服務來管理。

在 ML 模型定型之後，AutoML 會自動產生 Power BI 報表，說明您 ML 模型可能的效能情況。 AutoML 會醒目提示您輸入中影響模型所傳回預測的關鍵影響因數，以強調可解釋性。 這份報表也會包含模型的關鍵計量 (視 ML 模型類型而定)。

在產生的報表中，其他頁面會顯示模型的統計摘要和定型詳細資料。 如果使用者想要查看模型效能的標準資料科學量值，則可以參閱統計摘要。 定型詳細資料會摘要所有執行的反覆運算，並使用相關聯的模型參數，以建立您的模型。 它也會描述如何使用每項輸入來建立 ML 模型。

接著，您可以對 ML 模型套用資料以進行評分。 重新整理資料流程時，系統即會將 ML 模型的預測自動套用至資料。 Power BI 也會個別說明 ML 模型所產生的每個特定預測分數。

## <a name="creating-a-machine-learning-model"></a>建立機器學習模型

本節描述如何建立 AutoML 學習模型。 

### <a name="data-prep-for-creating-an-ml-model"></a>建立 ML 模型的資料準備

若要在 Power BI 中建立機器學習模型，您必須先使用歷史結果資訊來建立資料的資料流程，以用於定型 ML 模型。 如需設定資料流程的詳細資料，請參閱 [Power BI 中的自助資料準備](service-dataflows-overview.md)。

在目前版本中，Power BI 只會使用單一實體的資料來定型 ML 模型。 因此，如果您的歷史結果資料是由多個實體所組成，您就必須手動將資料聯結到單一資料流程實體中。 針對您嘗試預測的結果，您也應該為任何可能是強式預測的業務計量新增計算結果欄。

AutoML 具備用來定型機器學習模型的特定資料需求。 下列各節會根據各自的模型類型來描述這些需求。

### <a name="configuring-the-ml-model-inputs"></a>設定 ML 模型輸入

若要建立 AutoML 模型，請選取資料流程實體 (含歷史資料) [動作]  資料行中的 ML 圖示，然後選取 [新增機器學習模型]  。

![新增機器學習模型](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

我們已推出簡化的體驗，其中所包含精靈會引導您完成建立 ML 模型的程序。 此精靈包含下列簡單的步驟。

1. 選取含歷史結果資料的實體，以及您想要預測的欄位
2. 根據您想要查看的預測類型來選擇模型類型
3. 選取您想要讓模型作為預測性訊號的輸入
4. 命名您的模型並儲存設定

[歷史結果] 欄位會識別用來定型 ML 模型的標籤屬性，如下圖所示。

![選取歷史結果資料](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

當您指定 [歷史結果] 欄位時，AutoML 會分析標籤資料，以識別可針對該資料定型的 ML 模型類型，並建議最可能成功定型的 ML 模型類型。 

> [!NOTE]
> 某些模型類型可能不支援您選取的資料。

AutoML 也會分析所選實體中的所有欄位，以建議可用來定型 ML 模型的輸入。 此程序是以統計分析為基礎的約略情況，因此您應該檢查所使用的輸入。 您不應該使用任何相依於 [歷史結果] 欄位 (或標籤欄位) 的輸入來定型 ML 模型，因為它們會影響其效能。

![自訂輸入欄位](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

在最後一個步驟中，您可以為模型命名並儲存其設定。

在這個階段，系統會提示您重新整理資料流程，以開始 ML 模型的定型程序。

### <a name="ml-model-training"></a>ML 模型定型

AutoML 模型的定型是資料流程重新整理的一部分。 AutoML 會先準備您的資料以進行定型。

AutoML 會將您提供的歷史資料分割成訓練和測試資料集。 測試資料集是一種鑑效組，可用來驗證模型訓練後的效能。 這些項目會在資料流程中以**訓練和測試**實體呈現。 AutoML 會使用交叉驗證來進行模型驗證。

接下來，系統會分析每個輸入欄位並套用插補，以將任何遺漏值取代為替代值。 AutoML 會使用幾種不同的插補策略， 並對資料套用任何必要的取樣和正規化。

AutoML 會根據每個所選輸入欄位的資料類型以及統計屬性，對其套用數種轉換。 AutoML 會使用這些轉換來擷取功能，以用來訓練您的 ML 模型。

AutoML 模型的訓練程序包含高達 50 個反覆運算，其中具有不同的模型化演算法和超參數設定，以找出效能最佳的模型。 其中每個模型的效能都是透過鑑效組的測試資料集驗證來進行評估。 在此訓練步驟中，AutoML 會建立數個管線來訓練和驗證這些反覆運算。 評估模型效能的程序可能需要一些時間 (從數分鐘到幾個小時)，視您的資料集大小和可用專用容量資源而定。

在某些情況下，最終產生的模型可能會使用集成學習，以使用多個模型來提供更佳的預測效能。

### <a name="automl-model-explainability"></a>AutoML 模型的可解釋性

模型定型之後，AutoML 會分析輸入功能和模型輸出之間的關聯性。 它會針對每個輸入功能的鑑效組測試資料集，評估模型輸出的變化大小和方向。 這就是所謂的「功能重要性」  。

![功能重要性](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>AutoML 模型報表

AutoML 會產生 Power BI 報表，以摘要出驗證期間的模型效能與全域功能重要性。 此報表摘要說明對 ML 模型套用鑑效組測試資料，並將預測與已知結果值進行比較的結果。

您可以檢閱模型報表來了解其效能。 您也可以驗證模型之關鍵影響因素是否符合已知結果的商業見解。

報表中用來描述模型效能的圖表和量值是依據模型類型而定。 下列各節將描述這些效能圖表和量值。

報表中其他頁面可能會從資料科學角度來描述模型的相關統計量值。 例如，**二元預測**報表包含模型的增益圖和 ROC 曲線。

這些報表也包括 [定型詳細資料]  頁面，其中含有模型定型方式的描述，並包含一個圖表，描述每個反覆運算執行下的模型效能。

![定型詳細資料](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

此頁面上另一個區段描述如何使用插補方法來填入輸入欄位的遺漏值，以及如何轉換每個輸入欄位以擷取模型中所使用的功能。 它也包括最終模型所使用的參數。

![模型的詳細資訊](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

如果產生的模型使用集成學習，則 [定型詳細資料]  頁面也會包含一個區段，描述集成中每個組成模型的權數，以及其參數。

![集成中的權數](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>套用 AutoML 模型

如果您對所建立的 ML 模型效能感到滿意，可以在重新整理資料流程時，對其套用新資料或更新的資料。 您可以選取模型報表右上角的 [套用]  按鈕，來執行此動作。

若要套用 ML 模型，您必須指定要對其套用的實體名稱，以及要針對模型輸出新增至此實體的資料行前置詞。 資料行名稱的預設前置詞是模型名稱。 *Apply* 函式可能包含模型類型特定的其他參數。

當您套用 ML 模型時，即會建立新的資料流程實體，後置詞為 **enriched <model_name>** 。 例如，如果您將 _PurchaseIntent_ 模型套用至 _OnlineShoppers_ 實體，輸出將會產生 **OnlineShoppers enriched PurchaseIntent**。

目前，您無法在 Power Query 編輯器中使用輸出實體來預覽 ML 模型結果。 輸出資料行一律會顯示 null 作為結果。 為了檢視結果，系統會在套用模型時建立第二個輸出實體，後置詞為 **enriched <model_name> Preview**。

您必須重新整理資料流程，以在查詢編輯器中預覽結果。

![查詢編輯器](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

當您套用模型時，AutoML 一律會在重新整理資料流程時，將您的預測保持在最新狀態。

AutoML 也會包含輸出實體中所評分每個資料列的個別說明。

若要在 Power BI 報表中使用 ML 模型的見解和預測，您可以使用**資料流程**連接器從 Power BI Desktop 連接到輸出實體。

## <a name="binary-prediction-models"></a>二元預測模型

二元預測模型的正式名稱為**二元分類模型**，可用來將資料集分類成兩個群組。 它們可用來預測可能具有二元結果的事件，例如銷售商機是否轉換、帳戶是否會變換、發票是否能準時支付、交易是否為詐騙等。

由於結果是二元，因此 Power BI 預期二元預測模型的標籤必須是布林值，且已知的結果會標示 **true** 或 **false**。 例如，銷售商機轉換模型會將已獲得的銷售商機標示為 true，將已流失的商機標示為 false，並將開放的銷售商機標示為 null。

二元預測模型的輸出是機率分數，它會識別可達成對應至 true 標籤值之結果的可能性。

### <a name="training-a-binary-prediction-model"></a>定型二元預測模型

若要建立二元預測模型，您的輸入實體 (包含定型資料) 必須將布林值欄位作為歷史結果欄位，以識別過去已知的結果。

必要條件：

* 您必須將布林值欄位作為歷史結果欄位
* 每個結果類別都需要最少 50 個資料列的歷史資料

一般來說，如果過去結果是由不同資料類型的欄位所識別，您可以新增計算結果欄，以使用 Power Query 將它們轉換成布林值。

建立二元預測模型的程序步驟與其他 AutoML 模型相同，如上方＜設定 ML 模型輸入＞  一節中所述。

### <a name="binary-prediction-model-report"></a>二元預測模型報表

二元預測模型會產生一個機率結果，其為可達到 True 布林值標籤值所定義結果的記錄。 這份報表包含機率臨界值的交叉分析篩選器，它會影響高於和低於機率臨界值的分數解讀方式。

報表會以「確判為真」  、「誤判為真」  、「確判為否」  和「誤判為否」  的角度來描述模型的效能。 「確判為真」和「確判為否」可針對結果資料中的兩種類別正確預測結果。 「誤判為真」是指實際布林值標籤值為 False，但預測為 True 的結果。 相反地，「誤判為否」是實際布林值標籤值為 True，但預測為 False 的結果。

量值 (例如精確度和召回率) 可描述預測結果的機率臨界值效果。 您可以使用機率臨界值交叉分析篩選器選取臨界值，以在精確度和召回率之間達到平衡的折衷。

![正確性預覽](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

模型報表的 [正確性報表]  頁面包括模型的「累計增益」  圖表和 ROC 曲線。 這些是模型效能的統計量值。 報表包含所示圖表的描述。

![正確性報表畫面](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>套用二元預測模型

若要套用二元預測模型，您必須指定實體，其中包含您想要對其套用 ML 模型預測的資料。 其他參數包括輸出資料行名稱前置詞與機率臨界值，以用來分類預測結果。

![預測輸入](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

當您套用二元預測模型時，系統會將三個輸出資料行新增至擴充的輸出實體。 這些分別是 **PredictionScore**、**PredictionOutcome** 和 **PredictionExplanation**。 實體中的資料行名稱會使用套用模型時所指定前置詞。

**PredictionOutcome** 資料行包含預測的結果標籤。 系統會將機率超過臨界值的記錄預測為可能達到結果，並將下列情況預測為不太可能達到結果。

**PredictionExplanation** 資料行包含說明，以及輸入功能對 **PredictionScore** 的特定影響。 這是用於預測之輸入功能權數的 JSON 格式化集合。

## <a name="classification-models"></a>分類模型

分類模型可用來將資料集分類為多個群組或類別。  它們是用來預測可能有多個可能結果之一的事件，例如客戶是否可能有非常高、高、中或低的存留期值；預設的風險是高、中、低或非常低等。

分類模型的輸出是機率分數，可識別記錄將達到特定類別之準則的可能性。

### <a name="training-a-classification-model"></a>訓練分類模型

輸入實體 (包含分類模型的定型資料) 必須將字串或數值欄位作為歷史結果欄位，以識別過去已知的結果。

必要條件：

* 每個結果類別都需要最少 50 個資料列的歷史資料

建立分類模型的程序步驟與其他 AutoML 模型相同，如上方＜設定 ML 模型輸入＞  一節中所述。

### <a name="classification-model-report"></a>分類模型報表

分類模型報表的產生方式是對 ML 模型套用鑑效組測試資料，並將記錄的預測類別與實際已知類別進行比較。

模型報表包含一個圖表，其中包含每個已知類別的正確和不正確分類記錄明細。

![模型報表](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

類別特定之深入向下鑽研可讓您分析已知類別的預測分佈情況。 這包括其他類別，其中包含可能會將該已知類別分錯類別的記錄。

![分析報表](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

報表中的模型說明也包含每個類別的最上層預測指標。

分類模型報表也包含 [定型詳細資料] 頁面 (類似於其他模型類型的頁面)，如本文稍早的＜AutoML 模型報表＞  一節中所述。

### <a name="applying-a-classification-model"></a>套用分類模型

若要套用分類 ML 模型，您必須使用輸入資料和輸出資料行名稱前置詞來指定實體。

當您套用類別模型時，系統會將三個輸出資料行新增至擴充的輸出實體。 這些分別是 **PredictionScore**、**PredictionClass** 和 **PredictionExplanation**。 實體中的資料行名稱會使用套用模型時所指定前置詞。

**PredictionClass** 資料行包含最可能的記錄預測類別。 **PredictionScore** 資料行包含每個可能類別的記錄機率分數清單。

**PredictionExplanation** 資料行包含說明，以及輸入功能對 **PredictionScore** 的特定影響。 這是用於預測之輸入功能權數的 JSON 格式化集合。

## <a name="regression-models"></a>迴歸模型

迴歸模型可用來預測值，例如可能從銷售交易實現的收益、帳戶的存留期值、可能收取的應收發票金額、可能的發票支付日期等等。

迴歸模型的輸出是預測值。

### <a name="training-a-regression-model"></a>定型迴歸模型

輸入實體 (包含迴歸模型的定型資料) 必須將數值欄位作為歷史結果欄位，以識別過去已知的結果。

必要條件：

* 每個回歸模型都需要最少 100 個資料列的歷史資料

建立迴歸模型的程序步驟與其他 AutoML 模型相同，如上方＜設定 ML 模型輸入＞  一節中所述。

### <a name="regression-model-report"></a>迴歸模型報表

如同其他 AutoML 模型報表一樣，迴歸報表是以對模型套用鑑效組測試資料的結果為基礎。

模型報表包含比較預測值與實際值的圖表。 在此圖表中，對角線的距離會指出預測誤差。

剩餘誤差圖表會顯示鑑效組測試資料集中不同值的平均誤差百分比分佈情況。 水平軸代表群組實際值的平均值，而泡泡大小則顯示該範圍內值的頻率或計數。 垂直軸是平均剩餘誤差。

![剩餘誤差圖表](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

迴歸模型報表也包含 [定型詳細資料] 頁面 (類似於其他模型類型的頁面)，如上方＜AutoML 模型報表＞  一節中所述。

### <a name="applying-a-regression-model"></a>套用迴歸模型

若要套用迴歸 ML 模型，您必須使用輸入資料和輸出資料行名稱前置詞來指定實體。

![套用迴歸](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

當您套用迴歸模型時，系統會將兩個輸出資料行新增至擴充的輸出實體。 這兩個資料行是 **PredictionValue** 和 **PredictionExplanation**。 實體中的資料行名稱會使用套用模型時所指定前置詞。

**PredictionValue** 資料行包含的預測值，是以記錄的輸入欄位為依據。 **PredictionExplanation** 資料行包含說明，以及輸入功能對 **PredictionValue** 的特定影響。 這是輸入功能權數的 JSON 格式化集合。

## <a name="next-steps"></a>後續步驟

本文提供 Power BI 服務的資料流程自動化機器學習概觀。 下列文章可能也很實用。

* [教學課程：在 Power BI 中建置機器學習模型 (預覽)](service-tutorial-build-machine-learning-model.md)
* [教學課程：在 Power BI 中使用認知服務](service-tutorial-use-cognitive-services.md)
* [教學課程：在 Power BI 中叫用 Machine Learning Studio 模型 (預覽)](service-tutorial-invoke-machine-learning-model.md)
* [Power BI 中的認知服務 (預覽)](service-cognitive-services.md)
* [Power BI 與 Azure Machine Learning 的整合 (預覽)](service-machine-learning-integration.md)

如需有關資料流程的詳細資訊，您可以閱讀下列文章：
* [在 Power BI 中建立及使用資料流程](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用計算實體](service-dataflows-computed-entities-premium.md)
* [搭配內部部署資料來源使用資料流程](service-dataflows-on-premises-gateways.md)
* [Power BI 資料流程的開發人員資源](service-dataflows-developer-resources.md)
* [資料流程與 Azure Data Lake 的整合 (預覽)](service-dataflows-azure-data-lake-integration.md)


