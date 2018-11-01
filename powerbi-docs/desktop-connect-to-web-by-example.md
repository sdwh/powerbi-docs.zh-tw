---
title: 藉由 Power BI Desktop 中的範例從網頁擷取資料
description: 提供所要提取內容的範例，以便從網頁擷取資料
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f90f2ea4737fc5c98df4d171f8e1e65c2704607d
ms.sourcegitcommit: b8461c1876bfe47bf71c87c7820266993f82c0d3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336798"
---
# <a name="get-data-from-a-web-page-by-providing-an-example"></a>藉由提供範例來從網頁取得資料

從網頁取得資料讓使用者輕鬆就能從網頁擷取資料，並將該資料匯入 **Power BI Desktop**。 不過，網頁上的資料通常不容易擷取，因為它們不是在整齊的資料表中，所以從這樣的頁面中取得資料會是一項挑戰，即使該頁面是結構化且一致的。 

有一個解決方案。 您可以使用**藉由範例從 Web 取得資料**功能，在連接器對話方塊中提供一或多個範例，以便向 **Power BI Desktop** 顯示您想要擷取的資料，而後它會收集頁面上其他符合您範例的資料。 使用此解決方案，您可以從網頁擷取各種資料，包括在表格中的資料*和*其他非表格的資料。 

![藉由範例從 Web 取得資料](media/desktop-connect-to-web-by-example/web-by-example_01.png)



## <a name="using-get-data-from-web-by-example"></a>使用「藉由範例從 Web 取得資料」

若要使用「藉由範例從 Web 取得資料」，請從 [常用] 功能區功能表選取 [取得資料]。 在出現的視窗中，從左側窗格的類別中選取 [其他]，然後選取 [Web]。

![從 [取得資料] 選取 [Web]](media/desktop-connect-to-web-by-example/web-by-example_03.png)

針對所要擷取資料的網頁，於該處輸入網頁的 URL。 在本文中我們會使用「Microsoft 市集」網頁，並顯示此連接器的運作方式。 

如果您想要按照本文操作，可以使用我們在本文中使用的 [Microsoft 市集 URL](https://www.microsoft.com/en-us/store/top-paid/games/xbox?category=classics)：

    https://www.microsoft.com/en-us/store/top-paid/games/xbox?category=classics

![Web 對話方塊](media/desktop-connect-to-web-by-example/web-by-example_04.png)

當您選取 [確定] 時，就會出現 [導覽器] 對話方塊，其中會顯示所有自動偵測到的網頁資料表。 以下影像中所顯示的情況，未找到任何表格，但頁面底部有一個稱為 [使用範例擷取資料表] 的按鈕，可讓您提供範例。


![[導覽器] 視窗](media/desktop-connect-to-web-by-example/web-by-example_05.png)

選取 [使用範例擷取資料表] 會出現互動式視窗，您可以在其中預覽網頁的內容，以及輸入所要擷取資料的範例值。 

在此範例中，我們會擷取頁面上每個遊戲的 [名稱] 和 [價格]。 我們可以藉由為每個資料行指定幾個來自頁面的範例，如以下影像所示。 當輸入這些範例時，**Power Query** (從網頁擷取資料的基礎技術) 就能使用智慧資料擷取演算法，擷取符合範例項目模式的資料。

![範例資料](media/desktop-connect-to-web-by-example/web-by-example_06.png)

一旦我們已經滿意從網頁擷取的資料，請選取 [確定] 以移至 [查詢編輯器]，我們可以在其中套用更多轉換或塑造資料，例如將此資料與其的他資料來源結合。

![範例資料](media/desktop-connect-to-web-by-example/web-by-example_07.png)

之後，您可以建立視覺效果，或是在建立您的 **Power BI Desktop** 報表時使用網頁資料。


## <a name="next-steps"></a>後續步驟
您可以使用 **Power BI Desktop** 連線至各式各樣的資料。 如需有關資料來源的詳細資訊，請參閱下列資源︰

* [藉由範例新增資料行](desktop-add-column-from-example.md)
* [連線至網頁](desktop-connect-to-web.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中連接至 Excel 活頁簿](desktop-connect-excel.md)   
* [連接至 Power BI Desktop 中的 CSV 檔案](desktop-connect-csv.md)   
* [直接將資料輸入 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   

