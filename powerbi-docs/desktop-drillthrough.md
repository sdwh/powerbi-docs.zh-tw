---
title: "在 Power BI Desktop 中使用鑽研"
description: "了解如何在 Power BI Desktop 的新報表頁面上鑽研資料"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: c4482b8a8b7510b54b317ef9731057a52501d47c
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>在 Power BI Desktop 中使用鑽研
使用 **Power BI Desktop** 中的**鑽研**，您可以在報表中建立頁面，著重於特定的實體 - 例如供應商、客戶或製造商。 使用該焦點報表頁面，使用者可以滑鼠右鍵按一下其他報表頁面中的資料點，然後鑽研至著重頁面，取得經過篩選為該內容的詳細資料。

![](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>使用鑽研
若要使用**鑽研**，請建立報表頁面，其中包含您想要查看您將為其提供鑽研之實體類型的視覺效果。 例如，如果您想要為製造商提供鑽研，您可能會建立鑽研頁面，並使用顯示總銷售額、總出貨單位數、依類別分類的銷售額、依區域分類的銷售額等等的視覺效果。 這樣一來，當您鑽研至該頁面時，視覺效果將專屬於您按一下並選取鑽研的製造商。

然後在該鑽研頁面上，[視覺效果] 窗格的 [欄位] 區段中，拖曳您想要鑽研的欄位至 [鑽研篩選]。

![](media/desktop-drillthrough/drillthrough_02.png)

當您將欄位新增至 [鑽研篩選] 時，**Power BI Desktop** 會自動建立「返回」按鈕視覺效果。 該視覺效果會變成已發行報表中的按鈕，且讓正在 **Power BI 服務**中使用報表的使用者輕鬆地回到來源報表頁面 (他們在其中選取鑽研的頁面)。

![](media/desktop-drillthrough/drillthrough_03.png)

因為「返回」按鈕是個影像，您可以使用任何想要的影像來取代視覺效果的影像，它將仍會正常運作為按鈕，讓報表使用者能回到其原始頁面。 若要使用自己的影像作為返回按鈕，只要在鑽研頁面上放一個影像視覺效果，然後選取視覺效果，並開啟「返回按鈕」滑桿。 如此可讓您的影像運作為「返回」按鈕。

![](media/desktop-drillthrough/drillthrough_05.png)

**鑽研**頁面完成之後，當使用者以滑鼠右鍵按一下您的報表中的資料點，而它使用您放入鑽研頁面上之 [鑽研篩選] 的欄位時，隨即出現操作功能表，讓使用者鑽研至該頁面。

![](media/desktop-drillthrough/drillthrough_04.png)

當他們選擇鑽研時，頁面會篩選為顯示他們以滑鼠右鍵按一下之資料點的相關資訊。 比方說，如果他們以滑鼠右鍵按一下與 Contoso (製造商) 有關的資料點，然後選取要鑽研，則他們到達的鑽研頁面會篩選為 Contoso。

> [!NOTE]
> 只有**鑽研篩選**中的欄位會傳遞至鑽研報表分頁。 不會傳遞其他任何內容資訊。
> 
> 

以上就是在報表中使用**鑽研**的相關資訊。 這是取得您為鑽研篩選選取的實體資訊之展開檢視的好方法。

