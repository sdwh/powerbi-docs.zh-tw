---
title: 讓使用者個人化報表中的視覺效果
description: 讓讀者無須編輯報表，即可建立自己的報表檢視。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: ab232d4e5b6d17e7f20ed8a41875ca47693eb285
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407604"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>讓使用者個人化報表中的視覺效果

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

當您與廣大的受眾共用報表時，某些使用者可能會想查看略有不同的特定視覺效果檢視。 這些使用者可能會想要切換軸上的內容、變更視覺效果類型，或將某些內容新增至工具提示中。 一個視覺效果不能滿足所有人的要求。 透過這項新功能，您可以讓取用者在報表閱讀檢視中，探索及個人化視覺效果。 請者可以依自己想要的方式調整視覺效果，並將其儲存為書籤，以返回查看。 不需要有報表的編輯權限，也不用要求報表作者變更。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="個人化視覺效果":::
 
## <a name="what-report-consumers-can-change"></a>報表取用者可以變更的內容

這項功能允許取用者透過臨機操作探索 Power BI 報表視覺效果，獲取深入見解。 若要了解如何以取用者身分使用這項功能，請參閱[在報表中將視覺效果個人化](../consumer/end-user-personalize-visuals.md)。 此功能非常適合想讓報表讀者研究基本案例的報表建立者。 以下是報表讀者可以進行的修改：

- 變更視覺效果類型
- 切換量值或維度
- 新增或移除圖例
- 比較兩個或多個量值
- 變更彙總等等

這項功能不僅允許探索新功能。 也能讓取用者以各種方式擷取及共用其變更：

- 擷取變更
- 共用變更
- 重設報表的所有變更
- 重設視覺效果的所有變更
- 清除最近的變更

## <a name="turn-on-the-preview-feature"></a>開啟預覽功能

因為這是預覽版的功能，所以您必須先開啟功能切換。 請移至 [檔案] > [選項及設定] > [選項]。 確認選取 [全域] 設定 > [預覽功能] 中的 [個人化視覺效果]。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="開啟個人化視覺效果":::

您可能必須重新啟動 Power BI Desktop，才能在目前檔案的設定中看到此選項。

## <a name="enable-personalization-in-a-report"></a>在報表中啟用個人化

開啟預覽切換之後，您必須特別針對希望取用者能夠個人化視覺效果的報表，啟用此功能。

您可以在 Power BI Desktop 或 Power BI 服務中啟用此功能。

### <a name="in-power-bi-desktop"></a>在 Power BI Desktop 中

若要在 Power BI Desktop 中啟用此功能，請前往 [檔案] > [選項及設定] > [選項] > [目前檔案] > [報表設定]。 確認開啟 [個人化視覺效果 (預覽)]。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="在報表中啟用個人化":::

### <a name="in-the-power-bi-service"></a>在 Power BI 服務中

若要改在 Power BI 服務中啟用此功能，請前往您報表的 [設定]。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Power BI 服務中的報表設定":::

開啟 [個人化視覺效果 (預覽)] > [儲存]。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="在服務中開啟個人化視覺效果":::

## <a name="select-visuals-that-can-be-personalized"></a>選取可以個人化的視覺效果

根據預設，當您為指定的報表啟用此設定時，您可以個人化該報表中的所有視覺效果。 若不想將所有視覺效果都設為個人化，您可以逐一開啟或關閉視覺效果的設定。

選取該視覺效果 > 選取 [視覺效果] 窗格中的 [格式] > 展開 [視覺效果標頭]。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="選取視覺效果標頭":::
 
滑動 [個人化視覺效果] >  [開啟] 或 [關閉]。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="個人化視覺效果":::


## <a name="limitations-and-known-issues"></a>限制與已知問題

此功能目前有一些要注意的限制。

- 這項功能不支援內嵌案例，包括發佈至 Web。
- 不會自動保存使用者的探索。 您需要將檢視儲存為個人書籤，才能擷取您的變更。
- 使用 Power BI 行動裝置應用程式時無法變更視覺效果。 但使用 Power BI 服務儲存在個人書籤中的任何視覺效果變更，都會呈現在行動裝置應用程式中。

另外還有一些正在處理的已知問題：

- 不支援新增階層，您必須新增個別的子項目。
- 您無法將日期階層變更為日期，反之亦然。 
- 使用個人書籤時，結果會因選取的序列略有不同。 因為我們不擷取報表的完整狀態，只擷取修改過的部分，所以可能有差別。 因應措施為選取 [重設為預設]，然後選取您想要檢視的書籤。 

## <a name="next-steps"></a>後續步驟

[在報表中將視覺效果個人化](../consumer/end-user-personalize-visuals.md)。     

試試看新的視覺效果個人化體驗。 請在 [Power BI Ideas 網站](https://ideas.powerbi.com/forums/265200-power-bi)上，針對此功能及如何繼續改善此體驗，提供意見反應給我們。 

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
