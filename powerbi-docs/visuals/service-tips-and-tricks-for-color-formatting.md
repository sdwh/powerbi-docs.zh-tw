---
title: 在報表中設定色彩格式的祕訣和訣竅
description: 在 Power BI 報表中設定色彩格式的祕訣和訣竅
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/04/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 006288cd380a56ba57697ed285b04b38985b69db
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831582"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>在 Power BI 中色彩格式化的秘訣和訣竅
Power BI 提供許多不同的方式，用來自訂您的儀表板和報表。 本文詳細說明一系列秘訣，讓您的 Power BI 視覺效果更吸引人、更加有趣，且視您的需求自訂。

這裡提供下列秘訣。 有其他絕佳的秘訣嗎？ 太棒了！ 請寄給我們，我們會考慮將您的秘訣加入這個清單。

* 將主題套用至整個報表
* 變更單一資料點的色彩
* 根據數值設定圖表的色彩
* 根據欄位值設定資料點的色彩
* 自訂色階中所使用的色彩
* 使用發散色階
* 如何在 Power BI 中復原

若要進行任何變更，您必須正在編輯報表。 開啟報表並從功能表列選取 [編輯報表]  ，如下圖所示。

![哪裡可以找到 [編輯] 功能表](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-report.png)

當 [篩選]  和 [視覺效果]  窗格顯示於報表畫布右側時，即可開始進行自訂。 如果窗格沒有顯示，請選取右上角的箭號予以開啟。

![在 [編輯檢視] 中的報表畫布](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

## <a name="apply-a-theme"></a>套用佈景主題
透過報表主題，您可以將設計變更套用至整個報表，例如使用公司色彩、變更圖示集，或套用新的預設視覺效果格式。 當您套用報表主題時，報表中的所有視覺效果都會使用所選主題中的色彩和格式。 若要深入了解，請參閱[使用報表主題](../desktop-report-themes.md)

![功能表列中的切換主題圖示](media/service-tips-and-tricks-for-color-formatting/power-bi-theme.png)

在這裡，我們已將 [創新]  主題套用至銷售與行銷報表。

![已套用 [創新] 主題](media/service-tips-and-tricks-for-color-formatting/power-bi-theme-innovate.png)

## <a name="change-the-color-of-a-single-data-point"></a>變更單一資料點的色彩
有時候您會想要醒目顯示一個特定的資料點。 可能是新產品上市的銷售數字，或推行新計畫之後提升的品質分數。 您可以使用 Power BI 來變更其色彩，進而醒目顯示特定資料點。

下列視覺效果會依產品區段來排列單位銷售的次序。 

![將資料色彩變更為灰色](media/service-tips-and-tricks-for-color-formatting/power-bi-data.png)

假設您想要使用色彩來凸顯 [Convenience]  \(方便\) 區段，以強調這個全新區段的良好表現。 以下是步驟：

展開 [資料色彩]  區段並開啟 [全部顯示]  的滑桿。 這會顯示視覺效果中每個資料項目的色彩。 修改任何資料點。

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show.png)

將 [Convenience]  \(方便\) 設為橘色。 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

選取之後，[Convenience]  \(方便\) 資料點便成為美觀的橘色，而且肯定會凸顯出來。

即使您變更了視覺效果類型，然後返回，Power BI 仍會記住您的選擇，並將 [Convenience]  \(方便\) 保持為橘色。

您可以針對視覺效果中的單一、數個或所有資料元素變更資料點的色彩。 也許您想要讓視覺效果模擬黃色、綠色和藍色的公司色彩。 

![含有綠色、黃色和藍色橫條的橫條圖](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

有各式各樣可以用色彩變出的花樣。 在下一節，我們要來看看漸層。

## <a name="conditional-formatting-for-visualizations"></a>視覺效果的條件式格式設定
根據欄位數值來動態設定色彩，對於視覺效果用途很大。 這樣一來，除了用於設定橫條大小之外，您還可以顯示不同的值，並在單一圖表上顯示兩個值。 或者，您可以使用這個，醒目顯示超過 (或低於) 某個值的資料點 - 也許可以醒目顯示獲利率較低的區域。

下列章節將說明不同的方式，用來依據數值設定色彩。

### <a name="base-the-color-of-data-points-on-a-value"></a>根據值設定資料點的色彩
若要根據值變更色彩，請選取要啟用的視覺效果。 選取油漆滾筒圖示並展開 [資料色彩]  卡片，來開啟 [格式化] 窗格。 將滑鼠停留在卡片上，並選取出現的三個垂直點，然後選擇 [條件式格式設定]  。  

![按一下三個垂直點以選取 [條件式格式設定] 選項](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting.gif)

在 [預設色彩]  窗格中，使用下拉式清單來識別要用於條件式格式設定的欄位。 在此範例中，我們已選取 [銷售事實]   > [總單位]  欄位，並為 [最小值]  選取淺藍色，以及為 [最大值]  選取深藍色。 

![依資料色彩設定條件式格式設定](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![套用預設色彩的直條圖](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

您也可以使用不屬於視覺效果的欄位來格式化視覺效果色彩。 在下圖中，正在使用 [市佔率 SPLY YTD]  。 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


如您所見，雖然我們針對 [生產力]  和 [極端]  皆售出更多單位 (其直條較高)，但 [仲裁]  仍具有較大的 [市佔率 SPLY YTD]  (其直條色彩更加飽和)。

### <a name="customize-the-colors-used-in-the-color-scale"></a>自訂色階中所使用的色彩
您也可以變更這些值對應至這些色彩的方式。 在下圖中， **最小值** 和 **最大值** 的色彩分別設定為橙色和綠色。

在第一張影像中，請注意圖表中的長條如何反映在列中的漸層；最大值為綠色，最小值為橙色，且兩者之間的每個長條顏色深淺介於綠色和橙色。

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

現在讓我們來看看，如果在 [最小值]  和 [最大值]  方塊中提供數值會發生什麼事。 針對 [最小值]  和 [最大值]  ，從下拉式方塊選取 [數字]  ，然後將 [最小值]  設定為 3,500，並將 [最大值]  設定為 6,000。

![依據數字的條件式格式設定](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting-number.png)

藉由設定這些值，漸層不再套用至 **最小值** 以下或 **最大值**以上的圖表；任何超過 **最大值** 的長條色彩皆以綠色顯示，而任何低於 **最小值** 的長條皆以紅色顯示。

![依據數字的條件式格式設定結果](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

### <a name="use-diverging-color-scales"></a>使用發散色階
有時候您的資料可能會有自然發散色階。 例如溫度範圍在冰點有自然的中心，而獲益率分數有自然的中點 (零)。

若要使用發散色階，請選取 [發散]  核取方塊。 當 [發散]  設為開啟後，另一個色彩選取器隨即出現，稱為 [中心]  ，如下圖所示。

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging2.png)

當 [發散]  滑桿設為開啟後，您可以分別設定 [最小值]  、[最大值]  和 [中心]  的色彩。 在下圖中，[中心]  針對 [市佔率 SPLY YTD]  設為 .2，因此值超過 .2 的列是綠色漸層，而低於 1 的長條是紅色。

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

## <a name="how-to-undo-in-power-bi"></a>如何在 Power BI 中復原
如同許多其他 Microsoft 服務和軟體，Power BI 提供簡單的方法，用來復原您的上一個命令。 例如，讓我們假設您變更資料點或一系列資料點的色彩，但您不喜歡視覺效果中出現的色彩。 您不記得之前所用的色彩了，但知道您想要回復該色彩！

若要**復原**上一個動作，或最後幾個動作，您只需要鍵入 CTRL+Z。

## <a name="feedback"></a>意見反應
您有想要分享的秘訣嗎？ 請寄給我們，我們會考慮將您的秘訣加入這裡。

>[!NOTE]
>當選取 [格式]  圖示時，Power BI Desktop 也會提供這些可用的色彩、軸和相關的自訂項目。

## <a name="next-steps"></a>後續步驟
[開始使用色彩格式和軸屬性](service-getting-started-with-color-formatting-and-axis-properties.md)

