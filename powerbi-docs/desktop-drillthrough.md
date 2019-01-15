---
title: 在 Power BI Desktop 中使用鑽研
description: 了解如何在 Power BI Desktop 的新報表頁面上鑽研資料
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: dffcf8fb3daa7559abd4d3b999ea3a73392d0eb9
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54283108"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>在 Power BI Desktop 中使用鑽研
使用 **Power BI Desktop** 中的**鑽研**，您可以在報表中建立頁面，著重在特定實體，例如供應商、客戶或製造商。 使用者能以滑鼠右鍵按一下其他報表頁面中的資料點。 然後他們可以鑽研至焦點頁面，取得篩選為該內容的詳細資料。

![使用鑽研](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>使用鑽研
1. 若要使用**鑽研**，請建立報表頁面，其中包含您想要提供鑽研之實體類型的視覺效果。 

    例如，假設您想要提供製造商的鑽研。 則您建立的鑽研頁面所含的視覺效果，可能會顯示總銷售額、總出貨單位、依類別的銷售額、依區域的銷售額等。 如此一來，當您鑽研至該頁面時，就會顯示您所選取製造商特定的視覺效果。

2. 然後在該鑽研頁面上，在 [視覺效果] 窗格的 [欄位] 區段中，將您想要啟用鑽研的欄位拖曳到 [鑽研篩選] 部分中。

    ![[鑽研] 部分](media/desktop-drillthrough/drillthrough_02.png)

    當您將欄位新增至 [鑽研篩選] 時，**Power BI Desktop** 會自動建立「返回」按鈕視覺效果。 該視覺效果會成為已發行報表中的按鈕。 在 **Power BI 服務**中使用您報表的使用者，可使用此按鈕返回上一個報表頁面。

    ![鑽研影像](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>使用您自己的影像作為返回按鈕    
 因為返回按鈕是影像，所以您可以使用任何您想要的影像來取代該視覺效果的影像。 它仍然會當作返回按鈕，讓報表使用者可以返回原本的頁面。 若要使用自己的影像作為返回按鈕，請執行下列步驟：

1. 在 [常用] 索引標籤上，選取 [影像]。 然後找出您的影像，並將它放在鑽研頁面上。

2. 在鑽研頁面上選取您新的影像。 在 [格式化影像] 區段下，將 [連結] 滑桿設定為 [開啟]，然後將 [類型] 設定為 [返回]。 您的影像現在已當作返回按鈕。

    ![使用影像返回](media/desktop-drillthrough/drillthrough_05.png)

    
     現在使用者能以滑鼠右鍵按一下您報表中的資料點，並取得支援鑽研至該頁面的操作功能表。 

    ![鑽研功能表](media/desktop-drillthrough/drillthrough_04.png)

    當報表使用者選擇要鑽研時，系統將會針對以滑鼠右鍵按一下的資料點，以篩選過的頁面來顯示相關資訊。 例如，假設他們以滑鼠右鍵按一下有關 Contoso (製造商) 的資料點，並選取 [鑽研]。 他們移至的鑽研頁面會篩選為僅顯示 Contoso 的資料。

## <a name="pass-all-filters-in-drillthrough"></a>鑽研中的通過所有篩選

從 **Power BI Desktop** 的 2018 年 5 月版開始，您可以將所有已套用的篩選傳遞給鑽研視窗。 例如，您可以只選取特定的產品類別，而視覺效果就會根據該篩選到該類別，然後選取 [鑽研]。 您可能對鑽研在套用所有這些篩選之後的情況感興趣。

若要保留所有已套用的篩選條件，請在 [視覺效果] 窗格的 [鑽研] 區段中，將 [傳遞所有篩選] 切換開關設定為 [開啟]。 

![保留所有篩選](media/desktop-drillthrough/drillthrough_06.png)

在 2018 年 5 月之前發行的 **Power BI Desktop** 版本中，系統的行為即如同將此切換開關設定為 [關閉]。

當您接著鑽研視覺效果時，可看到套用哪些篩選條件，是根據套用至來源視覺效果的暫時篩選條件而套用的。 在鑽研視窗中，這些暫時性篩選會顯示為斜體。 

![以斜體顯示的暫時性篩選條件](media/desktop-drillthrough/drillthrough_07.png)

您可以使用工具提示頁面這麼做，但那會是奇怪的體驗，因為工具提示可能不會正常運作。 因此，不建議您使用工具提示這麼做。

## <a name="add-a-measure-to-drillthrough"></a>將量值新增至鑽研

除了將所有篩選條件傳遞到鑽研視窗之外，您也可以將量值 (或彙總的數值資料行) 新增至鑽研區域。 將鑽研欄位拖曳到鑽研卡就能套用它。 

![將量值新增至鑽研](media/desktop-drillthrough/drillthrough_08.png)

當您新增量值 (或彙總的數值資料行) 時，若該欄位是用於視覺效果的「值」區域中，即可鑽研至該頁面。

以上就是在報表中使用**鑽研**的相關資訊。 這是取得您為鑽研篩選選取的實體資訊之展開檢視的好方法。

## <a name="next-steps"></a>後續步驟

您可能也會對下列文章感興趣：

* [使用 Power BI Desktop 交叉分析篩選器](visuals/desktop-slicers.md)

