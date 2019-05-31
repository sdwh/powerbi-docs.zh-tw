---
title: Power BI Desktop 中的運算式為基礎的標題
description: Power BI Desktop 中變更，根據以程式設計方式的運算式，使用 以程式設計方式設定格式化的條件建立動態的標題
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769754"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Power BI Desktop 中的運算式為基礎的標題

您可以建立動態的自訂您的 Power BI 視覺效果的標題。 藉由建立 Data Analysis Expressions (DAX) 欄位、 變數或其他程式設計項目為基礎，視需要自動可以調整視覺效果的標題。 這些變更根據篩選條件、 選取項目，或其他使用者互動和組態而定。

![條件式格式化選項時，Power BI Desktop 的螢幕擷取畫面](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

建立動態的標題，有時也稱為*運算式為基礎的標題*，很簡單。 

## <a name="create-a-field-for-your-title"></a>建立標題欄位

建立以運算式為基礎的標題的第一個步驟是建立在您的模型用於標題中的欄位。 

有各種創意的方法，可讓您反映您想要它顯示，或您想要表達的視覺效果標題。 讓我們看看一些範例。

您可以建立的變更是根據視覺效果所收到的產品品牌名稱的篩選內容的運算式。 下圖顯示這類欄位的 DAX 公式。

![螢幕擷取畫面的 DAX 公式](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

另一個範例使用動態的標題，變更會根據使用者的語言或文化特性。 您也可以使用 DAX 量值中建立特定語言的標題`USERCULTURE()`函式。 此函數會傳回使用者，其作業系統或瀏覽器設定為基礎的文化特性代碼。 您可以使用下列 DAX switch 陳述式來選取正確的已翻譯的值。 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

或者，您可以從包含所有翻譯的查閱資料表中擷取的字串。 您可以將該資料表放在您的模型。 

這些是只需要幾個您可以使用 Power BI Desktop 中建立動態、 以運算式為基礎的項目，您的視覺效果的範例。 您可以與您的遊戲只受限於您的想像力和您的模型。


## <a name="select-your-field-for-your-title"></a>選取標題欄位

您已建立您在模型中建立欄位的 DAX 運算式之後，您需要將它套用到您的視覺效果標題。

若要選取的欄位，並將它套用，請前往**視覺效果**窗格。 在 **格式**區域中，選取**標題**以顯示視覺效果標題選項。 

當您以滑鼠右鍵按一下**標題文字**，內容會出現一個功能表，可讓您選取 ***fx * 條件式格式化**。 當您選取該功能表項目中，**標題文字** 對話方塊隨即出現。 

![螢幕擷取畫面的標題文字 對話方塊](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

您可以從該視窗中，選取您建立要用於您的標題欄位。

## <a name="limitations-and-considerations"></a>限制與考量

有幾項限制目前的實作之以運算式為基礎的視覺效果的項目：

* 運算式為基礎的格式目前不支援 Python 的視覺效果、 R 視覺效果或關鍵影響因數視覺效果上。
* 您建立標題欄位必須是字串資料類型。 傳回數字或日期/時間 （或任何其他資料類型） 的量值目前不支援。

## <a name="next-steps"></a>後續步驟

這篇文章說明如何建立 DAX 運算式轉換成可以與報表互動的使用者所變更的動態欄位的 視覺效果的標題。 您可能會發現下列文件以及。

* [在 Power BI Desktop 中使用跨報表鑽研](desktop-cross-report-drill-through.md)
* [在 Power BI Desktop 中使用鑽研](desktop-drillthrough.md)