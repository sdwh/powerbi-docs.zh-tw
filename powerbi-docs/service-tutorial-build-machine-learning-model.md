---
title: 教學課程：建立 Power BI （預覽） 中的機器學習服務模型
description: 在本教學課程中，您會建置在 Power BI 中的機器學習模型。
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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406578"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>教學課程：建立 Power BI （預覽） 中的機器學習服務模型

在本教學課程的文章中，您可以使用**自動化 Machine Learning**來建立和套用在 Power BI 中的二進位的預測模型。 本教學課程包含適用於建立 Power BI 資料流程，指引和訓練和驗證的機器學習模型直接在 Power BI 中的資料流程中使用的實體定義。 我們再使用該模型進行評分來產生預測。

首先，您將建立二元預測機器學習服務模型，可用來預測購買的意圖線上購物者根據一組其線上工作階段屬性。 基準測試機器學習服務資料集可針對此練習。 一旦已定型的模型，Power BI 會自動產生說明模型結果的驗證報告。 然後，您可以檢閱驗證報表，並將模型套用到您的資料進行評分。

本教學課程包含下列步驟：

> [!div class="checklist"]
> * 使用輸入資料來建立資料流程
> * 建立並定型機器學習服務模型
> * 檢閱模型驗證報表
> * 將模型套用至資料流程實體
> * 在 Power BI 報表中使用的評分的模型輸出

## <a name="create-a-dataflow-with-the-input-data"></a>使用輸入資料來建立資料流程

本教學課程的第一個部分是使用輸入資料來建立資料流程。 該處理程序會採用幾個步驟，如示下列章節中，從取得資料。

### <a name="get-data"></a>取得資料

建立資料流程的第一個步驟是已準備好您的資料來源。 在我們的案例中，我們會使用一組的線上課程，其中有些成果包含購買的 machine learning 資料集。 資料集包含一組有關這些工作階段，我們將用來定型模型的屬性。

您可以從 UC Irvine 網站下載的資料集。  我們也有此可用，進行本教學課程，從下列連結： [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv)。

### <a name="create-the-entities"></a>建立實體

若要在資料流程中建立實體，登入 Power BI 服務，並瀏覽至您已啟用 AI 預覽版的專用容量上的工作區。

如果您還沒有工作區，您可以建立一個方法是選取**工作區**Power BI 服務，然後選取左的導覽功能表中**建立應用程式工作區**底部的 [面板] 中，隨即出現。 這會開啟一個面板上輸入工作區詳細資料的權限。 輸入工作區名稱，然後選取**進階**。 確認工作區會使用專用容量使用的選項按鈕，並為其指派至已開啟的 AI 預覽版的專用的容量執行個體。 接著，選取 [儲存]  。

![建立工作區](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

工作區建立之後，您可以選取**略過**右下角的 [歡迎] 畫面中，如下圖所示。

![如果您的工作區，請略過](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

選取 [**資料流程 （預覽）** ] 索引標籤。選取 [ **Create** ] 按鈕，在右邊的工作區，然後再選取**資料流程**。

![建立資料流程](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

選取 [新增實體]  。 這會啟動**Power Query**瀏覽器中的編輯器。

![新增實體](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

選取  **Text/CSV 檔案**做為資料來源，顯示在下圖中。

![選取的文字/CSF 檔案](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

在**連接到資料來源**出現下一步 中，貼上下列連結，以*online_shoppers_intention.csv*成**檔案路徑或 URL**方塊，然後按**下一步**。

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![檔案路徑](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Power Query 編輯器會顯示從 CSV 檔案資料的預覽。 選取 **轉換表**命令的功能區，然後選取**使用做為標頭的第一個資料列**從出現的功能表。 這會新增_升級標頭_查詢進入**套用的步驟**區段在畫面的右側。 您可以更容易使用的名稱重新命名查詢，藉由變更中的值**名稱**右窗格中找到的方塊。 例如，您可以變更的查詢名稱_線上訪客_。

![將變更為易記名稱](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

某些屬性資料型別，此資料集中_數值_或是_布林_，但是這些可能會解譯為字串的**Power Query**。 選取頂端的各個資料行標頭，變更下列類型的下面所列的資料行的屬性類型圖示：

* **十進位數字：** Administrative_Duration;Informational_Duration;ProductRelated_Duration;BounceRates;ExitRates;PageValues;SpecialDay
* **True/False:** 週末;營收

![變更資料類型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

**二元預測**我們要訓練的模型需要布林值欄位做為標籤，找出過去的觀察值的結果。 在此資料集_營收_屬性表示購買，而這個屬性已有為布林值。 因此，我們不需要加入導出資料行標籤。 其他資料集中，您可能要將現有的標籤屬性轉換成布林值的資料行。

選取 **完成**按鈕以關閉 Power Query 編輯器。 這會顯示實體清單_線上訪客_我們新增的資料。 選取 **儲存**右上角的資料流程中，為提供的名稱，然後按**儲存**在對話方塊中，如下圖所示。

![儲存資料流程](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>重新整理資料流程

儲存資料流程中的結果所顯示的通知，指出 已儲存至資料流程。 選取 **立即重新整理**若要從來源將資料擷取到資料流程。

![立即重新重理](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

選取右上角的 [關閉]  ，然後等待資料流程重新整理完成。

您可以也使用重新整理您的資料流程**動作**命令。 重新整理完成時，資料流程顯示的時間戳記。

![重新整理的時間戳記](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>建立並定型機器學習服務模型

重新整理完成之後，請選取資料流程。 若要新增機器學習模型，請選取**套用的 ML 模型**按鈕**動作**列出基底實體，其中包含您的訓練資料和標籤資訊，，然後選取**新增機器學習服務模型**。

![新增機器學習模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

建立我們的機器學習服務模型的第一個步驟是識別歷程記錄資料，包括您想要預測的標籤欄位。 從資料學習，將會建立模型。

如果我們使用的資料集，這是**營收**欄位。 選取 [**營收**作為 '歷程記錄的結果欄位' 值，然後選取**下一步]** 。

![選取歷程記錄資料](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

接下來，我們必須選取機器學習模型來建立型的別。 Power BI 分析您已經識別了歷史的結果欄位中的值，並建議可由預測該欄位的機器學習服務模型的類型。

在此情況下，由於我們要預測二進位結果的是否可將進行購買與否，選取**二元預測**的模型類型，然後再選取下一步。

![選取的二元預測](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

接下來，Power BI 會進行初步掃描的資料，並建議之輸入的模型無法使用。 您可以自訂用於模型的輸入的欄位。 在我們策劃的資料集，若要選取的所有欄位，請都選取實體名稱旁邊的核取方塊。 選取 [**下一步]** 接受輸入。

![選取 [下一步] 的核取方塊](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

在最後一個步驟中，我們必須提供我們的模型的名稱以及要用於自動產生將摘要說明的模型驗證結果的報表結果的好記的標籤。 接下來，我們必須將模型_採購意圖預測_，，則為 true 和 false 的標籤設定為_購買_並_否購買_。 接著，選取 [儲存]  。

![儲存模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

我們的機器學習服務模型已準備好進行訓練。 選取 **立即重新整理**開始定型模型。

![立即重新重理](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

在定型程序會開始藉由取樣和正規化將歷程記錄資料，以及將您的資料集分割成兩個新的實體*採購意圖預測訓練資料*和*購買意圖預測測試資料*。

根據資料集的大小，定型程序可以花費數分鐘到幾個小時。 此時，請參閱中的模型**機器學習服務模型**的 [資料流程] 索引標籤。 _準備_狀態表示已加入佇列的訓練或低於訓練的模型。

![準備好進行訓練](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

訓練模型時，您將無法檢視或編輯的資料流程。 您可以確認正在模型受過訓練，並透過資料流程的狀態進行驗證。 這會顯示為資料重新整理中正在**資料流程** 索引標籤的工作區。

![在 處理程序](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

一旦完成模型訓練，資料流程會顯示更新的重新整理的時間。 您可以確認模型已定型，瀏覽至**機器學習服務模型**在資料流程中的索引標籤。 您所建立的模型應該會顯示狀態為**Trained**並**最後一個定型**時間現在應該已更新。

![上次進行訓練](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>檢閱模型驗證報表

若要檢閱模型驗證報表中，在**機器學習服務模型，s**選擇**檢視效能報告，並將模型套用**按鈕**動作**模型資料行. 這份報告描述您的機器學習服務模型有何容易執行。

在**模型的效能**頁面上的報表中，選取**關鍵影響因數**若要檢視最上層的預測值，為您的模型。 您可以選取其中一個預測值，以查看結果的分佈如何與該預測工具產生關聯。

![模型效能](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

您可以使用**機率臨界值**交叉分析篩選器的模型效能上檢查模型精確度與回收上的產生影響。

![機率閾值](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

在報表的其他頁面描述模型的統計效能度量。

此報告還包括訓練詳細資料頁面，其中說明不同的反覆項目所執行，如何從輸入與最後一個模型使用的超參數擷取功能。

## <a name="apply-the-model-to-a-dataflow-entity"></a>將模型套用至資料流程實體

選取 **套用模型**時要叫用此模型中的資料流程會重新整理報表頂端的按鈕。 在 [**套用**] 對話方塊中，您可以指定具有將模型應該套用的來源資料的目標實體。

![套用模型](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

出現提示時，您必須**重新整理**資料流程，以便預覽您的模型的結果。

套用模型會建立新的實體後, 置詞**豐富 < model_name >** 附加至您套用至模型的實體。 在我們的案例中，將套用至模型**OnlineShoppers**會建立實體**OnlineShoppers 豐富購買意圖預測**，其中包含從模型預測的輸出。

套用二元預測模型加入預測的結果、 機率分數與預測最上層的特定記錄的影響因數的三個資料行，每個前面會加上指定的資料行名稱。

![三個資料行的結果](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

由於已知的問題，才可以從 Power BI Desktop 存取豐富的實體中經過評分的輸出資料行。 若要預覽這些服務中，您必須使用特殊的預覽實體。

資料流程重新整理完成之後，您可以選取**OnlineShoppers 豐富購買意圖預測預覽**實體以檢視結果。

![檢視結果](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>在 Power BI 報表中使用的評分的模型輸出

若要使用您的機器學習模型的評分的輸出，您可以從連線到您資料流程 Power BI desktop 中，使用資料流程的連接器。 **OnlineShoppers 豐富購買意圖預測**現在可以使用實體納入您的模型，Power BI 報表中的預測。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您可以建立並套用二進位的預測模型，在 Power BI 中使用下列步驟：

* 使用輸入資料來建立資料流程
* 建立並定型機器學習服務模型
* 檢閱模型驗證報表
* 將模型套用至資料流程實體
* 在 Power BI 報表中使用的評分的模型輸出

如需 Power BI 中的 Machine Learning 自動化的詳細資訊，請參閱[自動在 Power BI （預覽） 中的 Machine Learning](service-machine-learning-automated.md)。
