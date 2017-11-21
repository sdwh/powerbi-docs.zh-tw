---
title: "查看 Power BI Desktop 視覺效果中的資料和記錄"
description: "使用 Power BI Desktop 的查看資料和查看記錄功能向下鑽研詳細資料"
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
ms.date: 10/09/2017
ms.author: davidi
ms.openlocfilehash: c43ec48d1bd34a5df2578c6cc117dd3e3bbdb64f
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>使用 Power BI Desktop 中的查看資料和查看記錄
在 **Power BI Desktop** 中，您可以向下鑽研任何視覺效果的詳細資料，並查看所選視覺效果資料或個別資料元素的文字表示。 這些功能有時稱為「點選」，或「鑽研」或「鑽研到詳細資料」。

您可以使用 [查看記錄] 檢視某視覺效果一個所選資料元素的基礎資料列，或使用 [查看資料] 檢視視覺效果中所用值的文字版本。 使用 [查看資料] 和 [查看記錄] 有一些限制，會在這篇文章的結尾討論。

![](media/desktop-see-data-see-records/see-data-see-records_1.png)

## <a name="using-see-data-in-power-bi-desktop"></a>在 Power BI Desktop 中使用查看資料
[查看資料] 按鈕位於功能區 [視覺效果工具] 的 [資料/鑽研] 索引標籤。

![](media/desktop-see-data-see-records/see-data-see-records_2.png)

您也可以在視覺效果按一下滑鼠右鍵，然後從出現的功能表選取 [查看資料]，來**查看資料**。

![](media/desktop-see-data-see-records/see-data-see-records_3.png)

> [!NOTE]
> 您的滑鼠必須在視覺效果的資料點暫留，才能使用滑鼠右鍵功能表。
> 
> 

當您選取 [查看資料] 時，**Power BI Desktop** 著重於您選取的視覺效果和資料，並將畫布空間專用於顯示視覺效果和資料的文字表示。 視覺效果會顯示在畫布上的上半部，資料會顯示在下半部，如下圖所示。 這是「水平」檢視。

![](media/desktop-see-data-see-records/see-data-see-records_4.png)

您也可以選取右上角的圖示切換到「垂直檢視」 (或回到「水平檢視」)。

![](media/desktop-see-data-see-records/see-data-see-records_5.png)

若要回到報表，請選取畫布左上角的 [< 回到報表]。

![](media/desktop-see-data-see-records/see-data-see-records_6.png)

## <a name="using-see-records-in-power-bi-desktop"></a>在 Power BI Desktop 中使用查看記錄
您也可以將焦點放在視覺效果中的一個資料元素，並向下鑽研其背後的資料。 一旦選取了視覺效果，有兩種方式可使用 [查看記錄]：您可以在 [資料/鑽研] 功能區啟用 [查看記錄] 切換按鈕，然後按一下資料元素，或者您可以用滑鼠右鍵按一下資料元素，並從出現的功能表選取 [查看記錄]。

![](media/desktop-see-data-see-records/see-data-see-records_7.png)

> [!NOTE]
> 如果選取的視覺效果不支援 [查看記錄]，則功能區上的按鈕會呈現灰色。
> 
> 

選取 [查看記錄] 之後，**Power BI Desktop** 會著重在該個別資料元素，並將畫布空間專用於顯示該元素的資料，如下圖所示。

![](media/desktop-see-data-see-records/see-data-see-records_8.png)

若要回到報表，請選取畫布左上角的 [< 回到報表] 按鈕。

## <a name="limitations"></a>限制
使用 [查看資料] 或 [查看記錄] 時有幾項限制要考慮：

* 只支援下列視覺效果類型︰
  * **橫條圖**
  * **直條圖**
  * **地圖**
  * **樹狀圖**
  * **區域分布圖**
  * **圓形圖**
  * **環圈圖**
  * **漏斗圖**
* 當視覺效果使用導出量值時，則無法使用 [查看記錄]\(See Records)
* 連接到即時多維度模型 (MD) 時，您不能使用 [查看記錄]\(See Records)

## <a name="next-steps"></a>後續步驟
**Power BI Desktop** 有各種報表格式和資料管理功能。 請查看下列資源以取得一些範例︰

* [在 Power BI Desktop 中使用群組和收納](desktop-grouping-and-binning.md)
* [在 Power BI Desktop 報表中使用格線、貼齊格線、堆疊順序、對齊及相等間距](desktop-gridlines-snap-to-grid.md)

