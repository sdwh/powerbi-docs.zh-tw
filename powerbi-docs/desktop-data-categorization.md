---
title: Power BI Desktop 中的資料分類
description: Power BI Desktop 中的資料分類
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9fa7310b3d0a20a588b2cc26fc0df177f3d0ab70
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "34285408"
---
# <a name="data-categorization-in-power-bi-desktop"></a>Power BI Desktop 中的資料分類
在 **Power BI Desktop** 中，您可以指定資料行的資料類別，讓 Power BI Desktop 知道如何在視覺效果中處理其值。

當 Power BI Desktop 匯入資料時，不只會取得資料本身，也會取得資料表和資料行名稱等資訊，像是主索引鍵等。有了該資訊之後，Power BI Desktop 便可做出某種程度的假設，讓您在建立視覺效果時可以有最佳的預設體驗。 

以下舉例説明：當 Power BI Desktop 偵測到某個資料行具有數值時，您可能會想要以某種方式進行彙總，因此會將資料行置於 [值] 區域。 或者，如果資料行具有日期時間值，它會假設您可能要以此資料行做為折線圖上的時間階層軸。

不過有些情況較具挑戰性，例如地理位置。 請考慮以下來自 Excel 工作表的資料表：

![](media/desktop-data-categorization/datacategorizationtable.png)

Power BI Desktop 應該將 GeoCode 資料行中的代碼視為國家/地區或美國州名的縮寫？  由於這種代碼可能代表任何意思，因此並不清楚。  例如，AL 可能表示阿拉巴馬州或阿爾巴尼亞，AR 可能表示阿肯色州或阿根廷，CA 可能表示加州或加拿大。 當我們在地圖上繪製 GeoCode 欄位時，則需要加以區別。  Power BI Desktop 應該顯示醒目提示國家/地區的世界圖片，或醒目提示各州的美國圖片？  您可以為此指定資料的資料類別。 資料分類會進一步精簡 Power BI Desktop 可用來提供最佳視覺效果的資訊。  

**指定資料類別**

1. 在 [報表檢視] 或 [資料檢視] 的 [欄位]  清單中，選取您要依不同分類排序的欄位。
2. 在功能區的 [模型化] 索引標籤中，按一下 [資料類別] 下拉式清單。  這會顯示您可以為資料行選擇的所有可能資料類別清單。  如果某些選項不適用於資料行的目前資料類型，則可能會停用這些選項。  例如，如果資料行是二進位資料類型，Power BI Desktop 將無法讓您選擇地理資料類別。 

![](media/desktop-data-categorization/datacategorization.gif)

這樣就大功告成了！  通常導致視覺效果的任何行為現在會自動運作。  

您可能也會想要了解 [Power BI 行動裝置應用程式的地理篩選](desktop-mobile-geofiltering.md)。

