---
title: Power BI Desktop 報告中的協助工具
description: 用於建立可存取之 Power BI Desktop 報告的功能和建議
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: bd0565420382fc22af67b1363b41f6d8ed6e92ab
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34290744"
---
# <a name="accessibility-in-power-bi-desktop-reports"></a>Power BI Desktop 報告中的協助工具
**Power BI Desktop** 有功能可讓行動不便人士更輕鬆地使用 **Power BI Desktop** 報告並與之互動。 這些功能包括能夠利用鍵盤或螢幕助讀程式來使用報告、利用 Tab 鍵聚焦於頁面上的不同物件，以及在視覺效果中貼心地使用標記。

![在折線圖和區域圖中使用不同的標記來改善協助工具](media/desktop-accessibility/accessibility_01.png)

> [!NOTE]
> 2017 年 6 月 **Power BI Desktop** 和更新版本提供這些協助工具功能。 未來的版本也預計還有其他協助工具功能。
> 
> 

## <a name="consuming-a-power-bi-desktop-report-with-a-keyboard-or-screen-reader"></a>利用鍵盤或螢幕助讀程式來使用 Power BI Desktop 報告
自 2017 年 9 月起的 **Power BI Desktop** 版本開始，您即可按 **?** 鍵，以顯示描述 **Power BI Desktop** 所提供之協助工具鍵盤快速鍵的視窗。

![在  Power BI Desktop 中的按鍵以顯示協助工具鍵盤快速鍵](media/desktop-accessibility/accessibility_03.png)

透過協助工具增強功能，您可以利用鍵盤或螢幕助讀程式，並搭配下列技巧來使用 **Power BI Desktop** 報告：

您可以使用 **Ctrl+F6**，在報告頁面索引標籤之間或給定報告頁面上的物件之間切換焦點。

* 當焦點在「報告頁面索引標籤」時，可使用*Tab* 鍵或「方向」鍵將焦點從一個報告頁面移至下一個報告頁面。 不論目前是否已選取報告頁面的標題，螢幕助讀程式都會讀出標題。 若要載入焦點目前所在的報告頁面，請使用 *Enter* 鍵或「空格」鍵。
* 當焦點在載入的「報告頁面」時，請使用*Tab* 鍵將焦點移至頁面上的每個物件，包括所有文字方塊、影像、圖形和圖表。 螢幕助讀程式會朗讀物件的類型，以及作者為該物件提供的描述。 

您可以按 **Alt+Shift+F10**，將焦點移至 [視覺效果] 功能表。

您可以按 **Alt+Shift+F11**，呈現 [See Data]\ (查閱資料) 視窗的可存取版本。

![在 Power BI Desktop 中，按 Alt+Shift+F11，以顯示視覺效果可存取的 [See Data] \(查閱資料) 視窗](media/desktop-accessibility/accessibility_04.png)

建立這些協助工具新增項目的目的，是為了讓使用者可以藉由螢幕助讀程式和鍵盤瀏覽，完整取用 **Power BI Desktop** 報表。

## <a name="tips-for-creating-accessible-reports"></a>建立可存取之報告的秘訣
下列秘訣可協助您建立更容易存取的 **Power BI Desktop**報告。

* 對於**線條**、**區域**和**組合**視覺效果，以及**散佈圖**和**泡泡圖**，請開啟標記，並針對每個線條使用不同的「標記圖形」。
  
  * 若要開啟「標記」，請在 [視覺效果] 窗格中選取 [格式]，展開 [圖形] 區段，然後向下捲動找出 [標記] 開關，並切換到 [開啟]。
  * 然後，在該 [圖形]區段中，從下拉式清單方塊選取每個條線的名稱 (或區域名稱，如果您使用**區域**圖的話)。 在下拉式清單底下，針對選取之線條所使用的標記，您可以調整許多層面，包括其形狀、色彩和大小。
  
  ![在折線圖和區域圖中使用不同的標記來改善協助工具](media/desktop-accessibility/accessibility_01.png)
  
  * 針對每個線條使用不同的「標記圖形」時，報告取用者可以更容易區分不同的線條 (或區域)。
* 延續上一個項目符號內容，請勿依賴色彩來傳達資訊。 使用線條上的標記 (如先前項目符號內容所述的標記) 會很有幫助。
* 從佈景主題資源庫中，選取高對比和色盲無礙的「佈景主題」，然後使用[**佈景主題設定**預覽功能](desktop-report-themes.md)來匯入。
* 對於報告上的每個物件，提供「替代文字」。 這樣可確保報告取用者了解您試著透過視覺效果傳達的內容，即使他們看不到視覺效果、影像、圖形或文字方塊也無妨。 若要針對 **Power BI Desktop** 報告上的任何物件提供「替代文字」，您可以選取物件 (例如視覺效果、圖形等)，然後在 [視覺效果] 窗格中，選取 [格式] 區段，展開 [一般]，然後捲動至底部，並填入 [替代文字] 文字方塊。
  
  ![在 [視覺效果] > [格式] > [一般] > [替代文字] 方塊中可以為報告中的任何物件新增替代文字](media/desktop-accessibility/accessibility_02.png)
* 確定您的報表在文字與任何背景色彩之間有足夠的對比。
* 使用可輕鬆閱讀的文字大小和字型。 文字大小或字型若太小而難以閱讀，則為無用的協助工具。
* 在所有視覺效果中包含標題、軸標籤和資料標籤。

## <a name="considerations-and-limitations"></a>考量與限制
協助工具功能已知有一些問題和限制，如下列清單所述：

* JAWS 適用於在 **Power BI 服務**中檢視的報表，包括任何內嵌報表。 **Power BI Desktop** 也支援 JAWS，但您必須先開啟螢幕助讀程式才能開啟 **Power BI Desktop** 檔案，以使螢幕朗讀功能正常運作。

## <a name="next-steps"></a>後續步驟
* [在 Power BI Desktop 中使用報告佈景主題 (預覽)](desktop-report-themes.md)

