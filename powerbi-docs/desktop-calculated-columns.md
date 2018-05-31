---
title: 使用 Power BI Desktop 中的導出資料行
description: Power BI Desktop 中的導出資料行
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
LocalizationGroup: Model your data
ms.openlocfilehash: 79d72cefbf6c6e5cf27aa0e4f90b4a1eb3114013
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810912"
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>使用 Power BI Desktop 中的導出資料行
透過導出資料行，您可以將新資料加入模型中已有的資料表。 您會建立定義資料行值的資料分析運算式 (DAX) 公式，而不是從資料來源查詢值並將其載入新的資料行。 在 Power BI Desktop 中，導出資料行是透過 [報表檢視] 中的 [新增資料行] 功能來建立。

與在 [查詢編輯器] 中使用 [新增自訂資料行] 建立做為查詢一部分的自訂資料行不同，在 [報表檢視] 或 [資料檢視] 中建立的導出資料行會依據您已經載入模型的資料。 例如，您可能會選擇串連不同但相關的兩個資料表之兩個不同資料行中的值、執行加法，或擷取子字串。

您所建立的導出資料行會出現在 [欄位] 清單中，就像是其他任何欄位一樣，但這些資料行會有特殊圖示，顯示其值為公式的結果。 您可以為資料行指定任何名稱，並將其加入報表視覺效果，就像是其他欄位一樣。

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

導出資料行使用[資料分析運算式](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) 來計算結果，這是可處理類似 Power BI Desktop 中關聯式資料的公式語言。 DAX 所包含的程式庫是由 200 個以上的函數、運算子和建構函式所組成，為建立公式提供極大的彈性，可計算幾乎所有資料分析需求的結果。 若要深入了解 DAX，請參閱本文結尾的＜深入了解＞一節。

DAX 公式類似 Excel 公式。 事實上，DAX 有許多函數與 Excel 相同。 不過，DAX 函數是為了處理報表中以互動方式交叉篩選或篩選的資料，就像是在 Power BI Desktop 中一樣。 當您為新資料行建立 DAX 公式時，它會計算資料表中每個資料列的結果，這與 Excel 不同；在 Excel 中，資料表中的每個資料列可以有不同的公式。 系統會視需要重新計算資料行值，例如當基礎資料重新整理及值變更時。

## <a name="lets-look-at-an-example"></a>以下舉例說明
Jeff 是 Contoso 的出貨經理。 他想要建立報表，以顯示不同城市的出貨編號。 他有一個 [Geography] 資料表，內含代表城市和州的個別欄位。 但是，Jeff 希望報表能夠顯示為同一個資料列上的單一值 [City, State]。 目前，Jeff 的 [Geography] 資料表沒有他想要的欄位。

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

但透過導出資料行，Jeff 可以將 [City] 資料行中的城市與 [State] 資料行中的州直接放在一起，或串連在一起。

Jeff 以滑鼠右鍵按一下 [Geography] 資料表，然後按一下 [新增資料行]。 接著在公式列中輸入下列 DAX 公式：

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

這個公式會直接建立名為 CityState 的新資料行；針對 [Geography] 資料表中的每個資料列，它會擷取 [City] 資料行中的值、加入逗號和空格，再串連 [State] 資料行中的值。

現在 Jeff 會有他想要的欄位。

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

他可以將該欄位連同出貨編號一起加入報表畫布。 不出一會兒功夫，Jeff 就得到了能夠新增至任何類型視覺效果的 [City]、[State] 欄位。 Jeff 會在建立地圖視覺效果時看到這些項目，Power BI Desktop 甚至了解如何讀取新資料行中的 City、State 值。

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>深入了解
我們在此僅快速介紹導出資料行。 請務必參閱[教學課程：在 Power BI Desktop 中建立計算結果欄](desktop-tutorial-create-calculated-columns.md)教學課程，您可以從中下載範例檔案，並取得有關如何建立更多資料行的逐步解說課程。 

若要深入了解 DAX，請參閱 [Power BI Desktop 中的 DAX 基本概念](desktop-quickstart-learn-dax-basics.md).

若要深入了解您建立作為查詢一部分的資料行，請參閱 [Power BI Desktop 中的常見查詢工作](desktop-common-query-tasks.md)中的＜建立自訂資料行＞一節。  

