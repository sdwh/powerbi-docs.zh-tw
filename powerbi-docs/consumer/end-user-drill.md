---
title: 在視覺效果中向下切入及向上切入
description: 本文說明如何向下切入 Microsoft Power BI 服務和 Power BI Desktop 的視覺效果。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 6/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 29823a2f1ca7f1448df54282e0ce081310974eb3
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2019
ms.locfileid: "67265658"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Power BI 視覺效果中的鑽研模式

本文說明如何向下切入 Microsoft Power BI 服務和 Power BI Desktop 的視覺效果。 Power BI 報表允許多個階層的資料，讓您可以深入解析資料。 在您的資料點上使用向下切入和向上切入，您可以深入探索資料。 您甚至可以在小巧的行動裝置上利用它。

## <a name="drill-requires-a-hierarchy"></a>鑽研需要階層

當視覺效果有階層時，您可以向下切入以顯示其他詳細資料。 例如，您可能必須有一個視覺效果，它會以運動、專業領域和活動所構成的階層，查看奧運獎牌計數。 根據預設，視覺效果會依運動 (體操、滑雪、水上運動等) 顯示獎牌計數。 但是因為它有階層，選取其中一個視覺效果項目 (例如橫條、線條或泡泡) 會顯示越來越詳細的圖片。 選取 [水上運動]  項目，查看游泳、跳水和水球的資料。  選取 [跳水]  項目，查看跳板、平台和同時跳水活動的詳細資料。

您可以新增階層到您擁有的報表，但是不能新增到與您共用的報表。
不確定哪些 Power BI 視覺效果包含階層嗎？ 將滑鼠停駐在視覺效果上。 如果您在上方角落看到這些切入控制項，您的視覺效果即具有階層。

![向下切入一個層級圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon4.png)  ![開啟和關閉向下切入圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon2.png)  ![一次向下切入所有欄位圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon3.png)
![向上切入圖示](./media/end-user-drill/power-bi-drill-icon5.png) ![向下展示圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon6.png)  

日期是獨特的階層類型。 當您將日期欄位新增到視覺效果時，Power BI 會自動新增包含年、季、月和日的時間階層。 如需詳細資訊，請參閱[視覺效果階層和向下切入行為](../guided-learning/visualizations.yml?tutorial-step=18)或觀看以下影片。

<iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> 若要了解如何使用 Power BI Desktop 來建立階層，請觀賞影片 - [如何建立及新增階層](https://youtu.be/q8WDUAiTGeU)。

## <a name="prerequisites"></a>先決條件

1. 在 Power BI 服務或 Desktop 中，鑽研需要有階層的視覺效果。

1. 若要跟著做，請開啟[零售分析範例](../sample-datasets.md)。 建立查看下列項目的 [樹狀圖]  視覺效果：

    | 區 | 欄位 |
    | ---- | ----- |
    | 值 |銷售額<br>\|\_ 今年總單位數 |
    | 分組 | 商店<br>\|\_ 國家/地區<br>\|\_ 城市<br>\|\_ 郵遞區號<br>\|\_ 名稱

    樹狀圖具有由國家/地區、城市、郵遞區號和城市名稱組成的階層。 每個國家/地區有一或多個城市，每個城市有一或多個郵遞區號等等。 根據預設，視覺效果只會顯示國家/地區資料，因為「國家/地區」  最先出現在清單中。

    ![標示國家/地區欄位的 [視覺效果] 窗格螢幕擷取畫面。](media/end-user-drill/power-bi-hierarcy-list.png)

1. 了解不同的切入圖示如何一起運作可能會造成混淆。 讓我們篩選樹狀圖以只顯示兩個較小的國家/地區：**KY** 與 **TN**。 選取樹狀圖，在 [視覺效果層級篩選]  下展開 [國家/地區]  ，並選取 [KY]  和 [TN]  。

    ![篩選 KY 和 TN 的 [視覺效果] 窗格螢幕擷取畫面。](./media/end-user-drill/power-bi-filter.png)

    現在只有兩個地區會顯示於樹狀圖中。

    ![標示 KY 和 TN 的視覺效果螢幕擷取畫面。](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-use-the-drill-features"></a>有三種方式可使用切入功能

您有可存取向下切入、向上切入，以及展開具有階層的視覺效果功能的多個選項。 本文示範如何使用以下第一個選項。 一旦您了解向下切入和展開的基本概念，就會知道如何使用這三者。 它們全都完成相同的事物。 請試用它們，並挑選您最喜歡的。

- 將滑鼠停留在視覺效果，以查看並使用圖示。  

    ![停留範例的螢幕擷取畫面。](./media/end-user-drill/power-bi-hover.png)

- 以滑鼠右鍵按一下視覺效果以顯示及使用功能表。

    ![按一下滑鼠右鍵範例的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-menu.png)

- 從 Power BI 功能表列中選取 [探索]  按鈕。

   ![選取 [探索] 以顯示向下切入圖示和選項的螢幕擷取畫面。](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>鑽研路徑

### <a name="drill-down"></a>向下切入

有數種方式來向下切入至您的視覺效果。 [向下切入]  會帶您前往階層中的下一個層級。 如果您正在查看 [國家/地區]  層級，您可以向下切入至城市層級、郵遞區號層級與最後的名稱層級。 路徑中的每個步驟都會顯示新的資訊。

![此圖顯示切入路徑](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>展開

「展開」  會將其他階層層級新增至目前的檢視。 因此，如果您正在查看 [國家/地區]  層級，您可以將城市、郵遞區號和名稱的詳細資料展開並新增至您的樹狀圖。 路徑中的每個步驟都會顯示相同的資訊，並在每一個層級新增新的資訊。

![此圖顯示展開路徑](./media/end-user-drill/power-bi-expand-path.png)

您也可以選擇要一次對一個欄位或是一次對所有欄位向下切入或展開。

## <a name="drill-down-all-fields-at-once"></a>一次向下切入所有欄位

1. 在樹狀圖的最上層顯示 KY 與 TN 的資料。 透過選擇其中一個控點並向右拖曳來擴大您的樹狀圖。

    ![顯示 KY 和 TN 的樹狀圖視覺效果螢幕擷取畫面](./media/end-user-drill/power-bi-drill-down.png)

1. 若要「一次向下切入所有欄位」  ，請選取視覺效果左上角的雙箭號 ![雙向下切入圖示](./media/end-user-drill/power-bi-drill-icon3.png)。 您的樹狀圖現在會顯示肯塔基州和田納西州的城市資料。

    ![顯示向下切入至城市的樹狀圖視覺效果螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-down1.png)

1. 再次向下切入至階層的郵遞區號層級。

    ![顯示向下切入至郵遞區號的樹狀圖視覺效果螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-down2.png)

1. 若要回頭向上切入，請選取視覺效果左上角的向上箭號 ![向下切入一個層級圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon5.png).

## <a name="drill-down-one-field-at-a-time"></a>一次向下切入一個欄位

這個方法會使用視覺效果本身右上角出現的向下切入圖示。

1. 選取向下切入圖示將它開啟 ![已開啟向下切入開啟/關閉圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon2.png).

    現在您有向下切入「一次一個欄位」  選項。

    ![箭號指向向下切入開啟/關閉圖示已開啟的視覺效果螢幕擷取畫面。](media/end-user-drill/power-bi-drill-icon-new.png)

    如果您未開啟向下切入，選取視覺效果項目 (例如橫條圖、泡泡圖或分葉圖) 並不會向下切入。 相反地，它會交叉篩選報表頁面上的其他圖表。

1. 針對 **TN** 選取分葉。 現在您的樹狀圖會顯示在田納西州中具有商店的所有城市。

    ![僅顯示 TN 資料的樹狀圖螢幕擷取畫面。](media/end-user-drill/power-bi-drill-down-one1.png)

1. 目前，您可以：

    1. 繼續針對田納西州向下切入。

    1. 針對田納西州中的特定城市向下切入。

    1. 反之展開 (請參閱下方的 [一次展開所有欄位]  )。

    繼續一次向下切入一個欄位。  選取 [Knoxville, TN]  。 現在樹狀圖會顯示您在 Knoxville 之商店的郵遞區號。

    ![顯示郵遞區號 37919 的樹狀圖螢幕擷取畫面。](media/end-user-drill/power-bi-drill-down-one2.png)

    請注意當您向下鑽研並重新往回時，標題會變更。

## <a name="expand-all-and-expand-one-field-at-a-time"></a>一次全部展開欄位和一次展開一個欄位

只顯示郵遞區號的樹狀圖無法提供足夠的資訊。  所以讓我們在階層中向下展開一個層級。  

1. 在樹狀圖使用中的情況下，選取「向下展開」  圖示 ![向下展開圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon6.png)。 您的樹狀圖現在顯示兩個層級的階層：郵遞區號與商店名稱。

    ![顯示郵遞區號和商店名稱的樹狀圖螢幕擷取畫面](./media/end-user-drill/power-bi-expand1.png)

1. 若要看到田納西州所有四個階層層級的資料，請選取向上切入箭號直到您到達第二個層級，樹狀圖中的 [依國家/地區和城市的今年總單位數]  。

    ![顯示所有 TN 資料的樹狀圖螢幕擷取畫面。](media/end-user-drill/power-bi-drill-down-one1.png)

1. 請確定向下切入仍然開啟 ![已開啟向下切入開啟/關閉圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon2.png) 並選取「向下展開」  圖示 ![向下展開圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon6.png)。 您的樹狀圖現在會顯示一些其他的詳細資料。 除了城市與州之外現在也會顯示郵遞區號。

    ![顯示城市、州和郵遞區號的視覺效果螢幕擷取畫面。](./media/end-user-drill/power-bi-expand-one3.png)

1. 再次選取 [向下展開]  以在樹狀圖上顯示田納西州詳細資料的所有四個階層層級。 將滑鼠停留在分葉以查看更多詳細資料。

    ![顯示工具提示與分葉特定資料的樹狀圖螢幕擷取畫面。](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>鑽研篩選其他視覺效果

隨著您在 [鑽研] 模式中作業，您可以決定向下切入和展開如何影響頁面上的其他視覺效果。

根據預設，切入不會篩選報表中的其他視覺效果。 您可以在 Power BI Desktop 和 Power BI 服務中啟用此功能。

1. 在 Desktop 中，選取 [格式]  索引標籤，然後選取 [鑽研篩選其他視覺效果]  核取方塊。

    ![顯示切入篩選 Power BI Desktop 中其他視覺效果設定的螢幕擷取畫面](./media/end-user-drill/power-bi-drill-filters-desktop.png)

1. 現在，當您在具有階層的視覺效果中向下切入、向上切入或展開時，該動作會篩選頁面上的其他視覺效果。

    ![Desktop 中結果的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-filters.png)

    ![Desktop 中另一個結果的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> 若要在 Power BI 服務中啟用此功能，請從頂端功能表列選取 [視覺效果互動]   >  [切入篩選其他視覺效果]  。
>
> ![顯示切入篩選 Power BI 服務中其他視覺效果設定的螢幕擷取畫面](./media/end-user-drill/power-bi-drill-filters-service.png)

## <a name="learn-about-the-hierarchy-axis-and-hierarchy-group"></a>了解階層軸和階層群組

您可以將階層軸和階層群組視為可用來增加及減少您想要檢視的資料之資料粒度的機制。 您可以組織成類別和子類別的任何資料都適合具有階層，包括日期和時間。

您可以在 Power BI 中建立具有階層的視覺效果，方法是選取一或多個要新增至 [軸]  區或 [群組]  區的資料欄位。 然後，在 [值]  區中新增要作為資料欄位查看的資料。 您可以透過視覺效果左上角和右上角是否出現「切入模式」  圖示，來判斷資料是否為階層式。

基本上，您可以將階層式資料簡單分為兩種類型：

- 日期和時間資料 - 如果您有 DateTime 資料類型的資料欄位，則表示您已有階層式資料。 Power BI 會自動針對任何資料欄位建立階層。 您可以將值剖析為 [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx) 結構。 您只需要將一個 DateTime 欄位新增至 [軸]  或 [群組]  區。

- 類別目錄資料 - 如果 Power BI 從包含子集合的集合衍生您的資料，或具有共用通用值的資料列，則表示您已有階層式資料。

Power BI 可讓您一次展開一個子集，或一次展開所有子集。 您可以向下切入資料，以查看每個層級的單一子集，也可以向下切入，同時查看每個層級的所有子集。 例如，您可以向下切入特定年份，或在階層中一面往下一面查看每年的所有結果。

您也可以利用相同的方式向上切入。

下列各節描述從最高層檢視向下切入到中間層檢視，再到最底層檢視。

### <a name="hierarchical-data-and-time-data"></a>階層式資料和時間資料

在此範例中：

1. 遵循[零售分析範例](../sample-datasets.md)，並建立查看下列項目的堆疊直條圖視覺效果：

    | 區 | 欄位 |
    | ---- | ----- |
    | 軸 | 時間<br>\|\_ 月份 |
    | 值 | 銷售額<br>\|\_ TotalSales |

    即使 [軸] 資料欄位是 [月份]  ，它仍會在 [軸]  區中建立 [年份]  類別。 這是因為 Power BI 針對所讀取的所有值，都會提供完整的 DateTime 結構。 階層最上層會顯示該年的資料。

    ![顯示依年份分組資料的單一橫條螢幕擷取畫面](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

1. 開啟向下切入模式後，選取圖表中的橫條即可下移一層階層。 您會看到三個橫條代表可用季度的資料。

1. 然後從左上方圖示，選擇 [向下一個階層等級展開全部]  。

1. 再執行一次，抵達階層的最底層，以顯示每個月的結果。

    ![查看每月橫條的橫條圖螢幕擷取畫面](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

除了視覺效果，我們還會看到每份報表呈現資料中所反映的階層。 在右上角選取省略符號，然後選取 [顯示資料]  。 下表顯示從單一月份或所有月份向下切入的結果：

|展開模式|年度|季|月|日|
| --- |:---:|:---:|:---:|---|
|單一|![單一年](./media/end-user-drill/power-bi-hierarchical-year.png)|![單一季](media/end-user-drill/power-bi-hierarchical-quarter.png)|![單一月](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![單日](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|全部|![所有年](./media/end-user-drill/power-bi-hierarchical-year.png)|![所有季](media/end-user-drill/power-bi-hierarchical-quarter.png)|![所有月](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![所有日](media/end-user-drill/power-bi-hierarchical-all-day.png)|

請注意，[季]  和 [年度]  報表的資料相同。 在向下切入至針對 [值]  指定的詳細資料層級之後，您可以看到單一報表變得更具體的方式，而且「所有月」 報表具有更多資料。

### <a name="hierarchical-category-data"></a>階層式類別目錄資料

來自集合與子集合的模型化資料是階層式資料。

位置資料是很好的範例。 假設資料來源中有一個資料表，其資料行包括國家/地區、州/省、城市和郵遞區號。 共用相同國家/地區、州/省和城市的資料是階層式資料。

在此範例中：

1. 遵循[零售分析範例](../sample-datasets.md)進行。 建立查看下列項目的堆疊直條圖視覺效果：

    | 區 | 欄位 |
    | ---- | ----- |
    | 值 |銷售額<br>\|\_ 今年總單位數 |
    | 軸 | 商店<br>\|\_ 國家/地區<br>\|\_ 城市 - 您可能需要將城市從 [圖例]  區拖曳至 [軸]  區。<br>\|\_ 郵遞區號<br>\|\_ 名稱 |

    ![依國家/地區顯示今年總單位數的橫條圖螢幕擷取畫面。](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

1. 開啟向下切入模式後，從左上方圖示，選擇 [向下一個階層等級展開全部]  三次。

    您會抵達階層的最底層，以顯示國家/地區、城市和郵遞區號的結果。

    ![顯示階層的最低層級 (最詳細) 的橫條圖螢幕擷取畫面。](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

除了視覺效果，我們還會看到每份報表呈現資料中所反映的階層。 在右上角選取省略符號，然後選取 [顯示資料]  。 下表顯示向下切入單一國家/地區或所有國家/地區的結果。

| 展開模式|國家/地區|城市|郵遞區號|名稱|
| ---|:---:|:---:|:---:|---|
|單一|![單一國家/地區](./media/end-user-drill/power-bi-hierarchical-territory.png)|![單一縣/市](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![單一郵遞區號](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![單一名稱](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|全部|![所有國家/地區](./media/end-user-drill/power-bi-hierarchical-territory.png)|![所有縣/市](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![所有郵遞區號](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![所有名稱](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|

 當您向下切入時，您會看到 [單一]  報表變得更具體，而 [所有]  國家/地區報表則有更多資料。

## <a name="considerations-and-limitations"></a>考量與限制

如果將日期欄位新增至視覺效果不會建立階層，可能是因為「日期」欄位實際上不是儲存為日期。 如果您擁有資料集：

1. 在 Power BI Desktop 的 [資料]  檢視中開啟它。

1. 選取具有日期的資料行。

1. 在 [模型化]  索引標籤上，將 [資料類型]  變更為 [日期]  或 [日期/時間]  。

![選取資料檢視，並在右上角您可以看到日期類型的螢幕擷取畫面。](media/end-user-drill/power-bi-change-data-type2.png)

如果報表已與您共用，請連絡擁有者以要求變更。

## <a name="next-steps"></a>後續步驟

[Power BI 報表的視覺效果](../visuals/power-bi-report-visualizations.md)

[Power BI 報表](end-user-reports.md)

[Power BI - 基本概念](end-user-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
