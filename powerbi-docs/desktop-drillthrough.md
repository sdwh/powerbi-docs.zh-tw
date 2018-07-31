---
title: 在 Power BI Desktop 中使用鑽研
description: 了解如何在 Power BI Desktop 的新報表頁面上鑽研資料
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 66222eb773d70afcfcf361fba49118363a670e7f
ms.sourcegitcommit: f01a88e583889bd77b712f11da4a379c88a22b76
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39329337"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>在 Power BI Desktop 中使用鑽研
使用 **Power BI Desktop** 中的**鑽研**，您可以在報表中建立頁面，著重於特定的實體 - 例如供應商、客戶或製造商。 使用該焦點報表頁面，使用者可以滑鼠右鍵按一下其他報表頁面中的資料點，然後鑽研至著重頁面，取得經過篩選為該內容的詳細資料。

![使用鑽研](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>使用鑽研
1. 若要使用**鑽研**，請針對您要鑽研的實體類型，以建立包含所要視覺效果的報表頁面。 

    例如，如果您想要為製造商提供鑽研，您可能會建立鑽研頁面，並使用顯示總銷售額、總出貨單位數、依類別分類的銷售額、依區域分類的銷售額等等的視覺效果。 如此一來，當您鑽研至該頁面時，會顯示您所選取製造商特定的視覺效果。

2. 然後在該鑽研頁面上，[視覺效果] 窗格的 [欄位] 區段中，拖曳您想要鑽研的欄位至 [鑽研篩選]。

    ![鑽研良好](media/desktop-drillthrough/drillthrough_02.png)

    當您將欄位新增至 [鑽研篩選] 時，**Power BI Desktop** 會自動建立「返回」按鈕視覺效果。 該視覺效果會變成已發行報表中的按鈕，且讓正在 **Power BI 服務**中使用報表的使用者輕鬆地回到來源報表頁面 (他們在其中選取鑽研的頁面)。

    ![鑽研影像](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>使用您自己的影像作為返回按鈕    
 因為返回按鈕是影像，您可以使用任何想要的影像來取代視覺效果的影像，它將仍會正常運作為返回按鈕，讓報表使用者能回到其原始頁面。

1. 在 [首頁] 索引標籤上按一下 [映像]，然後找出您的映像，並將它放在 [鑽研] 頁面。
2. 在 [鑽研] 頁面中選取您的新映像，然後在 [格式化映像] 區段下方，將 [連結] 滑桿設成 [開啟]，將 [類型] 設成 [上一步]。 您的影像現在已當作返回按鈕。

    ![使用影像進行備份](media/desktop-drillthrough/drillthrough_05.png)

    **鑽研**頁面完成之後，當使用者以滑鼠右鍵按一下報表中的資料點，且該資料點使用您放入 [鑽研篩選] 的欄位時，隨即出現支援鑽研至該頁面的操作功能表。

    ![鑽研功能表](media/desktop-drillthrough/drillthrough_04.png)

    當報表使用者選擇鑽研時，將會針對以滑鼠右鍵按一下的資料點，以篩選頁面來顯示相關的資訊。 例如，如果他們以滑鼠右鍵按一下與 Contoso (製造商) 有關的資料點，然後選取要鑽研，則他們到達的鑽研頁面會篩選為 Contoso。

## <a name="pass-all-filters-in-drillthrough"></a>鑽研中的通過所有篩選

從 **Power BI Desktop** 的 2018 年 5 月版開始，您可以將所有已套用的篩選傳遞給鑽研視窗。 例如，您可以只選取特定類別的產品以及篩選為該類別的視覺效果，然後選取鑽研。 您可能對鑽研在套用所有這些篩選之後的情況感興趣。

若要保留所有套用的篩選，在 [視覺效果] 窗格的 [鑽研] 區段中，只需要將 [Pass all filters] \(通過所有篩選\) 切換至 [開啟]。 

![保留所有篩選](media/desktop-drillthrough/drillthrough_06.png)

在 2018 年 5 月之前的 **Power BI Desktop** 版本中，行為相當於將此切換設定為「關閉」。

當您接著鑽研視覺效果時，即可看到因暫時套用篩選之來源視覺效果而套用的篩選。 在鑽研視窗中，這些暫時性篩選會顯示為斜體。 

![斜體的暫時性篩選](media/desktop-drillthrough/drillthrough_07.png)

請注意，您可以使用工具提示頁面來執行此作業，但這是奇怪的體驗 (工具提示似乎未正常運作)，因此不建議使用工具提示這麼做。

## <a name="add-a-measure-to-drillthrough"></a>將量值新增至鑽研

除了將所有篩選條件傳遞到鑽研視窗之外，您也可以將量值 (或彙總的數值資料行) 新增至鑽研區域。 只要將鑽研欄位拖曳到鑽研卡，即可加以套用。 

![將量值新增至鑽研](media/desktop-drillthrough/drillthrough_08.png)

當您新增量值 (或彙總的數值資料行) 時，若視覺效果的*值*區域中使用欄位，即可展開至該頁面。

以上就是在報表中使用**鑽研**的相關資訊。 這是取得您為鑽研篩選選取的實體資訊之展開檢視的好方法。

## <a name="next-steps"></a>後續步驟

您可能也會對下列文章感興趣：

* [使用 Power BI Desktop 交叉分析篩選器](desktop-slicers.md)

