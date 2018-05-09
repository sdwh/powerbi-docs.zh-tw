---
title: 在 Power BI Desktop 中新增自訂資料行
description: 在 Power BI Desktop 中快速建立新的自訂資料行
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f982ba613bef66514aab39b43cf0fe92b1b7b81c
ms.sourcegitcommit: bdb1fee3612bcc66153dcad8c4db2e99fb041014
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>在 Power BI Desktop 中新增自訂資料行
您可以使用 **Power BI Desktop** 中的**查詢編輯器**，輕鬆將資料的新自訂資料行新增到模型。 您可以使用簡單的按鈕建立定義自訂資料行的 [M 公式](https://msdn.microsoft.com/library/mt270235.aspx)，建立自訂資料行並為其重新命名。 M 公式有[完整的函式參考內容集](https://msdn.microsoft.com/library/mt779182.aspx)。 

![](media/desktop-add-custom-column/add-custom-column_01.png)

建立自訂資料行是您在**查詢編輯器**中建立的另一個**套用的步驟**，表示其可以隨時變更、稍早或稍後移動及修改。

## <a name="use-query-editor-to-add-a-new-custom-column"></a>使用查詢編輯器新增自訂資料行
若要建立新的自訂資料行，請啟動**查詢編輯器**。 您也可以從 **Power BI Desktop** 的 [常用] 功能區選取 [編輯查詢] 以完成這個動作。

![](media/desktop-add-custom-column/add-column-from-example_02.png)

在**查詢編輯器**已啟動，而您也載入一些資料後，就可以依序選取功能區的 [新增資料行] 索引標籤和 [自訂資料行]，以新增自訂資料行。

![](media/desktop-add-custom-column/add-custom-column_02.png)

[新增自訂資料行] 隨即顯示，這會在下一節中討論。

## <a name="the-add-custom-column-window"></a>[新增自訂資料行] 視窗
在 [新增自訂資料行] 視窗中，您會在右方窗格中看到可用欄位的清單，您的自訂資料行名稱位於頂端 (只要在文字方塊中鍵入新名稱，即可為其重新命名)，以及您依據從右側插入的欄位、新增運算子或建立公式而建立 (或撰寫) 的 [**M** 公式](https://msdn.microsoft.com/library/mt779182.aspx)，新的自訂資料行會依此定義。 

![](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>為您的自訂資料行建立公式
您可以從右側 [可用的資料行:] 清單中選取欄位，然後選取 [<< 插入] 將其新增到自訂資料行公式。 只要按兩下清單中的資料行，也可以加以新增。

在您鍵入公式及建立資料行的同時，會在視窗底部看到指標，即時 (在您鍵入時) 讓您知道是否偵測到任何語法錯誤。 如果一切正常，您會看到綠色勾號。

![](media/desktop-add-custom-column/add-custom-column_04.png)

但如果您的語法中有某種錯誤，會看到黃色的警告圖示以及偵測到的錯誤，還有會在偵測到錯誤的位置放上游標 (在公式中) 的連結。

![](media/desktop-add-custom-column/add-custom-column_05.png)

當您選取 [確定] 時，自訂資料行即新增到模型，而 [已新增自訂] 步驟會新增到查詢的 [套用的步驟]。

![](media/desktop-add-custom-column/add-custom-column_06.png)

如果您在 [套用的步驟] 窗格中按兩下 [已新增自訂] 步驟，[新增自訂資料行] 最會再次顯示，並已載入您建立的自訂資料行公式，準備好讓您在必要時修改。

## <a name="using-the-advanced-editor-for-custom-columns"></a>在自訂資料行使用進階編輯器
您也可以使用**進階編輯器**建立自訂資料行 (也可以修改任何查詢步驟)。 在**查詢編輯器**中選取 [檢視] 索引標籤，然後選取 [進階編輯器] 以顯示**進階編輯器**。

![](media/desktop-add-custom-column/add-custom-column_07.png)

**進階編輯器**可讓您完整控制查詢。

## <a name="next-steps"></a>後續步驟
建立自訂資料行還有其他多種方式，包括依據您提供給**查詢編輯器**的範例建立資料行。 如需從範例建立自訂資料行的詳細資訊，請參閱下列文章：

* [在 Power BI Desktop 中從範例新增資料行](desktop-add-column-from-example.md)
* [M 公式語言簡介](https://msdn.microsoft.com/library/mt270235.aspx)
* [M 函式參考](https://msdn.microsoft.com/library/mt779182.aspx)  

