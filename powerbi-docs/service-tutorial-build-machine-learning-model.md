---
title: 教學課程：在 Power BI 中建置機器學習模型 (預覽)
description: 在本教學課程中，您會在 Power BI 中建置機器學習模型。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406578"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>教學課程：在 Power BI 中建置機器學習模型 (預覽)

在本教學課程文章中，您會使用**自動化機器學習服務**，在 Power BI 中建立二進位預測模型並且套用。 教學課程包含建立 Power BI 資料流程，以及使用資料流程中所定義的實體，直接在 Power BI 中定型及驗證機器學習模型的指導。 我們接著會使用該模型去評分，產生預測。

首先，您會建立二進位預測機器學習模型，根據線上顧客的一組線上工作階段屬性，預測他們的購買意圖。 效能評定機器學習服務資料集會用於此演練。 定型模型後，Power BI 會自動產生驗證報表，解釋模型結果。 您接著可以檢視驗證報表，並將模型套用到您的資料以進行評分。

本教學課程由下列步驟組成：

> [!div class="checklist"]
> * 使用輸入資料建立資料流程
> * 建立及定型機器學習模型
> * 檢閱模型驗證報表
> * 將模型套用到資料流程實體
> * 在 Power BI 報表中使用模型的評分輸出

## <a name="create-a-dataflow-with-the-input-data"></a>使用輸入資料建立資料流程

本教學課程的第一個部分是使用輸入資料建立資料流程。 該流程包含數個步驟，如下列各節所示，並會從取得資料開始。

### <a name="get-data"></a>取得資料

建立資料流程的第一個步驟，是將您的資料來源準備就緒。 在我們的案例中，我們會使用來自一組線上工作階段的機器學習服務資料集，其中有些最後會形成購買。 資料集包含一組與這些工作階段相關的屬性，而我們會使用這些屬性來定型我們的模型。

您可以從 UC Irvine 網站下載資料集。  針對本教學課程，我們也在以下連結提供此資料集：[online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv)。

### <a name="create-the-entities"></a>建立實體

若要在資料流程中建立實體，登入 Power BI 服務，並瀏覽至您已啟用 AI 預覽版的專用容量上的工作區。

如果您還沒有工作區，您可以在 Power BI 服務的左側導覽功能表中選取 [工作區]  建立一個工作區，然後在出現的面板底部選取 [建立應用程式工作區]  。 如此會在右側開啟一個面板，輸入工作區詳細資料。 輸入工作區名稱，然後選取 [進階]  。 透過圓形按鈕，確認工作區使用專用容量，並且指派給已開啟 AI 預覽的專用容量執行個體。 接著，選取 [儲存]  。

![建立工作區](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

建立工作區後，您可以選取 [歡迎] 畫面右下角的 [略過]  ，如下圖所示。

![若您已有工作區，請略過](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

選取 [資料流程 (預覽)]  索引標籤。選取工作區右上角的 [建立]  按鈕，然後選取 [資料流程]  。

![建立資料流程](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

選取 [新增實體]  。 這會在瀏覽器中啟動 **Power Query** 編輯器。

![新增實體](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

選取 [文字/CSV 檔案]  作為資料來源，如下圖所示。

![已選取 [文字/CSF 檔案]](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

在接下來出現的 [連線到資料來源]  中，將以下 *online_shoppers_intention.csv*的連結貼入 [檔案路徑或 URL]  方塊，然後選取 [下一步]  。

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![檔案路徑](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Power Query 編輯器會從 CSV 檔案中顯示資料的預覽。 從命令功能區選取 [轉換資料表]  ，然後從出現的功能表中選取 [使用第一個資料列作為標頭]  。 這會將 [已升階標頭]  查詢步驟新增到畫面右側的 [套用的步驟]  區段。 您可以透過變更右側窗格中 [名稱]  方塊內的值，將查詢重新命名為較易記的名稱。 例如，您可以將查詢的名稱變更為「線上訪客」  。

![變更為易記名稱](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

此資料集中的有些屬性資料類型為「數值」  或「布林值」  ，雖然 **Power Query** 可能會將這些解譯為字串。 選取每個資料行標頭頂端的屬性類型圖示，將以下列出的資料行變更為下列類型：

* **十進位數字：** Administrative_Duration；Informational_Duration；ProductRelated_Duration；BounceRates；ExitRates；PageValues；SpecialDay
* **True/False：** Weekend；Revenue

![變更資料類型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

我們定型的**二進位預測**模型需要布林值欄位作為標籤，來識別過去觀察的結果。 在此資料集中，_Revenue_ 屬性會指出購買，且此屬性已經可以作為布林值使用。 因此，我們無須為標籤新增計算結果欄。 在其他資料集中，您可能需要將現有標籤屬性轉換成布林值資料行。

選取 [完成]  按鈕，關閉 Power Query 編輯器。 這會顯示實體清單，其中包含我們新增的「線上訪客」  資料。 選取右上角的 [儲存]  、為資料流程提供名稱，然後在對話方塊上選取 [儲存]  ，如下圖所示。

![儲存資料流程](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>重新整理資料流程

儲存資料流程會顯示通知，表示您的資料流程已儲存。 選取 [立即重新整理]  ，將來源的資料內嵌至資料流程。

![立即重新重理](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

選取右上角的 [關閉]  ，然後等待資料流程重新整理完成。

您也可以使用 [動作]  命令，重新整理資料流程。 資料流程會在重新整理完成時顯示時間戳記。

![重新整理的時間戳記](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>建立及定型機器學習模型

在重新整理完成後，選取資料流程。 若要新增機器學習模型，請在包含您定型資料及標籤資訊基底實體的 [動作]  清單中，選取 [套用 ML 模型]  按鈕，然後選取 [新增機器學習模型]  。

![新增機器學習模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

建立我們機器學習模型的第一個步驟是識別歷史資料，包含您要預測的標籤欄位。 模型的建立將從學習此資料而來。

針對我們正在使用的資料集，這是 **Revenue** 欄位。 選取 **Revenue** 作為「歷史結果欄位」值，然後選取 [下一步]  。

![選取歷史資料](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

接下來，我們必須選取要建立的機器學習模型類型。 Power BI 會分析您所識別歷史結果欄位中的值，並建議可建立並用來預測欄位的機器學習模型類型。

在此案例中，因為我們正在預測使用者是否會購買的二進位結果，請針對模型類型選取 [二進位預測]  ，然後選取 [下一步]。

![已選取二進位預測](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

接下來，Power BI 會進行資料的初步掃描，建議模型可以使用的輸入。 您可以選擇自訂用於模型的輸入欄位。 在我們管理的資料集中，若要選取所有欄位，請選取實體名稱旁邊的核取方塊。 選取 [下一步]  ，接受輸入。

![選取 [下一步] 核取方塊](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

在最後一個步驟中，我們必須為我們的模型提供名稱，以及為結果提供易記標籤；這些結果會用於自動產生報表，摘要模型驗證的結果。 接下來，我們必須將模型命名為「購買意圖預測」  ，並將 True 和 False 標籤命名為「購買」  和「不購買」  。 接著，選取 [儲存]  。

![儲存模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

我們的機器學習模型現在已準備好進行定型。 請選取 [立即重新整理]  ，啟動定型模型。

![立即重新重理](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

定型處理序會從取樣及正常化您的歷史資料開始，並將您的資料集分成兩個新實體：「購買意圖預測定型資料」  及「購買意圖預測測試資料」  。

取決於資料集的大小，定型處理序所花費的時間可能自數分鐘到幾個小時不等。 此時，您可以在資料流程的 [機器學習模型]  索引標籤中看見模型。 「準備就緒」  狀態表示模型已排入佇列，準備定型或正在定型。

![準備定型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

定型模型時，您將無法檢視或編輯資料流程。 您可以透過資料流程的狀態來確認模型正在定型或正在進行驗證。 這會在工作區的 [資料流程]  索引標籤中，顯示為正在進行的資料重新整理。

![正在處理](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

模型定型完成後，資料流程會顯示更新後的重新整理時間。 您可以巡覽至資料流程中的 [機器學習模型]  索引標籤，來確認模型已定型。 您建立的模型應會顯示狀態為 [已定型]  ，且 [上次定型]  時間現在應該已經更新。

![上次定型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>檢閱模型驗證報表

若要檢閱模型驗證報表，請在 [機器學習模型]  中，選取模型 [動作]  資料行中的 [檢視效能報表及套用模型]  按鈕。 此報表會描述您機器學習模型可能執行的方式。

在報表的 [模型效能]  頁面中，選取 [關鍵影響因素]  ，檢視您模型最關鍵的預測。 您可以選取其中一個預測，查看結果分佈與該預測相關聯的方式。

![模型效能](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

您可以使用 [模型效能] 頁面上的 [可能性閾值]  交叉分析篩選器，檢查其對模型精確度和回收的影響。

![機率閾值](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

報表的其他頁面會描述模型的統計效能計量。

報表也會包含 [定型詳細資料] 頁面，描述已執行的不同反覆運算、從輸入擷取特徵的方式，以及針對最終模型使用的超參數。

## <a name="apply-the-model-to-a-dataflow-entity"></a>將模型套用到資料流程實體

選取報表頂端的 [套用模型]  按鈕，在重新整理資料流程時叫用此模型。 在 [套用]  對話方塊中，您可以指定擁有應套用模型來源資料的目標實體。

![套用模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

出現提示時，您必須 [重新整理]  資料流程，以便預覽您模型的結果。

套用模型將會建立新的實體，並會將 **enriched <model_name>** 後置詞附加到您套用模型的實體。 在我們的案例中，將模型套用到 **OnlineShoppers** 實體會建立 **OnlineShoppers 豐富購買意圖預測**，其中包含從模型預測的輸出。

套用二進位預測模型會新增三個資料行，其中包含預測結果、可能性分數，以及針對預測最關鍵的記錄限定影響因素，且每個都會加上所指定的資料行名稱前置詞。

![三個結果資料行](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

由於已知問題，豐富實體中的評分輸出資料行只能從 Power BI Desktop 存取。 若要在服務中預覽這些項目，您必須使用特殊的預覽實體。

在完成資料流程重新整理後，您可以選取 **OnlineShoppers 豐富購買意圖預測預覽**實體，檢視結果。

![檢視結果](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>在 Power BI 報表中使用模型的評分輸出

若要使用您機器學習模型的評分輸出，您可以從 Power BI Desktop 使用資料流程連接器，連線到您的資料流程。 **OnlineShoppers 豐富購買意圖預測**實體現在可以用來將您模型的預測併入 Power BI 報表。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已使用這些步驟，在 Power BI 中建立並套用二進位預測模型：

* 使用輸入資料建立資料流程
* 建立及定型機器學習模型
* 檢閱模型驗證報表
* 將模型套用到資料流程實體
* 在 Power BI 報表中使用模型的評分輸出

如需 Power BI 中機器學習服務自動化的詳細資訊，請參閱 [Power BI 中的自動化機器學習服務 (預覽)](service-machine-learning-automated.md)。
