---
title: 開始設定 Power BI 視覺效果的格式
description: 自訂視覺化標題、背景和圖例
author: mihart
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 011e2b6d3bf5cc998f7db76e96536d2ddab09888
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880853"
---
# <a name="customize-visualization-titles-legends-and-backgrounds"></a>自訂視覺效果標題、圖例及背景

在本教學課程中，您將學到一些不同的方法，可以用來自訂視覺效果。 有很多選項可讓您自訂視覺效果。 深入了解它們的最佳方式就是探索 [格式]  窗格 (選取油漆滾筒圖示)。 為了讓您快速入門，本文向您示範如何自訂視覺效果標題、圖例和背景。

您無法自訂所有視覺效果。 如需詳細資料，請參閱視覺效果的[完整清單](#visualization-types-that-you-can-customize)。

向前快轉到影片的 4:50 處，以取得如何自訂視覺效果的示範：

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

現在，遵循以下指示，用您自己的資料試試看。

## <a name="prerequisites"></a>先決條件

- Power BI 服務或 Power BI Desktop

- 零售分析範例報表

## <a name="customize-visualization-titles-in-reports"></a>自訂報表中的視覺效果標題

若要跟著做，請登入 [Power BI 服務](https://app.powerbi.com)，然後在[編輯報表](../service-interact-with-a-report-in-editing-view.md)檢視中開啟[零售分析範例報表](../sample-datasets.md)。

> [!NOTE]
> 當您將視覺效果釘選至儀表板時，它會變成儀表板圖格。 您也可以使用[新的標題和副標題、超連結和調整大小](../service-dashboard-edit-tile.md)，來自訂圖格本身。

1. 移至 [零售分析範例]  報表的 [新門市]  頁面。

1. 選取 [依開張月份和鏈結的開張門市計數]  群組直條圖。

1. 在 [視覺效果]  窗格中，選取滾筒刷圖示以顯示格式選項。

1. 選取 [標題]  以展開該區段。

   ![[格式] 窗格的螢幕擷取畫面，其中標示油漆滾筒圖示，並具有指向 [標題] 下拉式清單的箭號。](media/power-bi-visualization-customize-title-background-and-legend/power-bi-formatting-menu.png)

1. 將 [標題]  滑桿移至 [開啟]  。

   ![[開啟] 滑桿的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/onoffslider.png)

1. 若要變更標題，請在 [標題文字]  欄位中輸入 [依開張月份的門市計數]  。

1. 將 [字型色彩]  變更為橙色，並將 [背景色彩]  變更為黃色。

    1. 選取下拉式清單，並從 [佈景主題色彩]  、[最近使用的色彩]  ，或 [自訂色彩]  選擇色彩。

        ![字型色彩和背景色彩選項的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/customizecolorpicker.png)

    1. 選取下拉式清單來關閉色彩視窗。

       儲存您所做的變更。

       如果您需要還原所有變更，您可以選取色彩視窗中的 [還原為預設值]  ，回到預設色彩。

1. 將文字大小放大到 [12 點]  。

1. 您要對圖表標題所做的最後一項自訂，是要讓視覺效果對齊中央。

    ![對齊控制項已選取 [置中] 選項的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/customizealign.png)

此時教學課程中，群組直條圖標題看起來類似這樣：

![新設定的群組直條圖的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/tutorialprogress1.png)

儲存您所做的變更，然後移至下個區段。

如果需要還原所有變更，請選取 [標題]  自訂窗格底部的 [還原為預設值]  。

![[還原為預設值] 選項的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/revertall.png)

## <a name="customize-visualization-backgrounds"></a>自訂視覺效果的背景

選取相同的群組直條圖之後，展開 [背景]  選項。

1. 將 [背景]  滑桿移至 [開啟]  。

1. 選取下拉式清單並選擇灰色。

1. 將 [透明度]  變更為 **74%** 。

此時教學課程中，群組直條圖背景看起來類似這樣：

![背景色彩已更新的群組直條圖的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/power-bi-customize-background.png)

儲存您所做的變更，然後移至下個區段。

如果需要還原所有變更，請選取 [背景]  自訂窗格底部的 [還原為預設值]  。

## <a name="customize-visualization-legends"></a>自訂視覺效果的圖例

1. 開啟 [概觀]  報表頁面，然後選取 [依 FiscalMonth 和區域經理的總銷售額差異]  圖表。

1. 在 [視覺效果]  索引標籤中，選取油漆滾筒圖示來開啟 [格式] 窗格。

1. 展開 [圖例]  選項：

      ![[圖例] 選項的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/legend.png)

1. 將 [圖例]  滑桿移至 [開啟]  。

1. 將圖例移到視覺效果的左側。

1. 將 [標題]  切換為 [開啟]  來新增圖例標題。

1. 在 [圖例名稱]  欄位中輸入「經理」  。

此時教學課程中，群組直條圖圖例看起來類似這樣：

![群組直條圖中已更新圖例的螢幕擷取畫面。](media/power-bi-visualization-customize-title-background-and-legend/legend-move.png)

儲存您所做的變更，然後移至下個區段。

如果需要還原所有變更，請選取 [圖例]  自訂窗格底部的 [還原為預設值]  。

## <a name="visualization-types-that-you-can-customize"></a>您可以自訂的視覺效果類型

以下清單列出視覺效果，以及可供每一個視覺效果使用的自訂選項：

| 視覺效果 | 標題 | 背景 | 圖例 |
|:--- |:--- |:--- |:--- |
| 區域 | 可以 | 是 |可以 |
| 橫條圖 | 可以 | 是 |可以 |
| card | 可以 | 是 |n/a |
| 多列卡片 | 可以 | 是 | n/a |
| 資料行 | 可以 | 是 | 可以 |
| 組合圖 | 可以 | 是 | 可以 |
| 環圈圖 | 可以 | 是 | 可以 |
| 區域分布圖 | 可以 | 是 | 可以 |
| 漏斗圖 | 可以 | 是 | n/a |
| 量測計 | 可以 | 是 | n/a |
| KPI | 可以 | 是 | n/a |
| 線條 | 可以 | 是 | 可以 |
| 地圖 | 可以 | 是 | 可以 |
| 矩陣圖 | 可以 | 是 | n/a |
| 圓形圖 | 可以 | 是 | 可以 |
| 散佈圖 | 可以 | 是 | 可以 |
| 交叉分析篩選器 | 可以 | 是 | n/a |
| 資料表 | 可以 | 是 | n/a |
| 文字方塊 | 不可以 | 是 | n/a |
| 樹狀圖 | 可以 | 是 | 可以 |
| 瀑布圖 | 可以 | 是 | 可以 |

## <a name="next-steps"></a>後續步驟

- [自訂 X 軸和 Y 軸屬性](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [開始使用色彩格式和軸屬性](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Power BI 服務取用者的基本概念](../consumer/end-user-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
