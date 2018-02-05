---
title: "探索 Power BI 行動裝置應用程式中的報表"
description: "了解如何在手機或平板電腦上的 Power BI 行動裝置應用程式中檢視報表，並與其互動。 您可以使用 Power BI 服務或 Power BI Desktop 來建立報表，然後在 Mobile Apps 中與其互動。 "
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 01/25/2018
ms.author: maggies
ms.openlocfilehash: 51006f70d0be13f08de7047f0097f7530d32a470
ms.sourcegitcommit: be5223b62e9a5d57c52f8588d4e539d814751dd6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>探索 Power BI 行動裝置應用程式中的報表
適用於︰

| ![iPhone](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Android 手機](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Android 平板電腦](media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Windows 10 裝置](media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android 手機 |Android 平板電腦 |Windows 10 裝置 |

Power BI 報表是資料的互動式檢視，以視覺效果顯示資料的各種發現與洞見及需要深入了解的事項。 在 Power BI 行動裝置應用程式中檢視報表是三步驟程序中的第三個步驟。

1. [在 Power BI Desktop 中建立報表](desktop-report-view.md)。 您甚至還可以在 Power BI Desktop 中[為手機最佳化報表](mobile-apps-view-phone-report.md)。 
2. 將這些報表發行到 Power BI 服務 [(https://powerbi.com)](https://powerbi.com) 或 [Power BI 報表伺服器](report-server/get-started.md)。  
3. 然後在 Power BI 行動裝置應用程式中與這些報表互動。

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>在行動裝置應用程式中開啟 Power BI 報表
Power BI 報表會根據您取得的位置，儲存在行動裝置應用程式中的不同位置。 這些報表可能會在 [應用程式]、[與我共用]、[工作區]\(包括 [我的工作區]) 中，或在報表伺服器上。 有時您會經過相關的儀表板才能抵達某個報表，有時會列出這些報表。

* 在儀表板中，點選磚右上角的省略符號 (...) > [開啟報表]。
  
  ![開啟報表](media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  不是所有的磚都有在報表中開啟的選項。 例如，點選藉由在問與答方塊中提問所建立的磚時不會開啟報表。 
  
  在手機上，報表會以橫向模式開啟，除非[已最佳化成適合在手機上檢視](mobile-reports-in-the-mobile-apps.md#view-reports-optimized-for-phones)。
  
  ![以橫向模式顯示的手機報表](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-landscape.png)

## <a name="view-reports-optimized-for-phones"></a>檢視為手機最佳化的報表
Power BI 報表作者可以建立專為手機最佳化的報表版面配置。 針對手機最佳化的報表頁面已新增功能：例如，您可以向下鑽研，並在焦點模式中排序視覺效果，且可以存取[報表作者新增至報表頁面的篩選條件](mobile-apps-view-phone-report.md#filter-the-report-page-on-a-phone)。 在報表清單中，最佳化的報表會有特殊圖示 ![手機報表圖示](media/mobile-reports-in-the-mobile-apps/power-bi-phone-report-icon.png)：

![開啟手機報表](media/mobile-reports-in-the-mobile-apps/power-bi-android-phone-report.png)

當您在手機上檢視該報表時，它會以直向檢視開啟。

![以直向檢視顯示的報表](media/mobile-reports-in-the-mobile-apps/07-power-bi-phone-report-portrait.png)

 報表可能會有為手機最佳化與未最佳化的混合頁面。 如果是這種情況，當您翻閱報表時，檢視會針對每一頁從直向切換為橫向。

深入了解[為手機檢視最佳化的報表](mobile-apps-view-phone-report.md)。

## <a name="use-slicers-to-filter-a-report-page"></a>使用交叉分析篩選器來篩選報表頁面
在 Power BI Desktop 或 Power BI 服務中設計報表時，請考慮[將交叉分析篩選器加入報表頁面中](power-bi-visualization-slicers.md)。 您和您的同事可以在瀏覽器的頁面中和行動裝置應用程式中，使用交叉分析篩選器來篩選頁面。 當您在手機上檢視報表時，可以在橫向模式中，以及針對手機直向模式的最佳化頁面中，查看交叉分析篩選器並與它互動。

* 當您在報表頁面上的交叉分析篩選器中選取值時，會篩選頁面上的其他視覺效果。
  
  ![報表交叉分析篩選器](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-slicer.png)
  
  在此圖中，交叉分析篩選器會篩選直條圖，只顯示 7 月的值。

## <a name="cross-filter-and-highlight-a-power-bi-report-page"></a>交叉篩選和醒目提示 Power BI 報表頁面
當您選取視覺效果中的值時，並不會篩選其他視覺效果， 而是會醒目提示其他視覺效果中的相關值。

* 點選視覺效果中的值。
  
  ![交叉篩選頁面](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-highlight.png)
  
  點選一個視覺效果中的 [大] 資料行，會醒目提示其他視覺效果中的相關值。 

## <a name="sort-a-visual-on-an-ipad-or-a-tablet"></a>在 iPad 或平板電腦上排序視覺效果
* 依序點選圖表、省略符號 (**...**) 及欄位名稱。
  
   ![為視覺效果排序](media/mobile-reports-in-the-mobile-apps/power-bi-android-tablet-report-sort.png)
* 若要反轉排序次序，請再點選一次省略符號 (**...**)，然後再點選一次相同的欄位名稱。

## <a name="drill-down-and-up-in-a-visual-on-an-ipad-or-a-tablet"></a>在 iPad 或平板電腦上向下切入和向上切入視覺效果
如果報表作者已將此功能新增至視覺效果，您可以在 iPad 或平板電腦上向下切入視覺效果，以查看組成視覺效果的值。 您可以在 Power BI Desktop 或 Power BI 服務中[新增視覺效果的向下切入](power-bi-visualization-drill-down.md)。 

> [!NOTE]
> 目前向下切入不適用於 iPad 或平板電腦的地圖。
> 
> 

* 點選一個視覺效果。 如果上方角落出現向上和向下箭號 ![向上切入、向下切入圖示](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up-down.png)，您就可以向下切入。 若要向下切入一個值，請點選右上角的箭號，然後點選視覺效果中的值 &#151; 在本例中，請點選深藍色 FD-04 泡泡。
  
  ![在視覺效果中向下切入](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-down-one.png)
* 若要回頭向上切入，請點選左上角的向上箭號。
  
  ![向上切入](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-drill-up.png)

## <a name="go-back-to-my-workspace"></a>回到我的工作區
* 點選報表名稱旁的箭號 > 點選 [我的工作區]。
  
  ![返回上層](media/mobile-reports-in-the-mobile-apps/power-bi-iphone-report-back.png)

## <a name="next-steps"></a>後續步驟
* [檢視為您的手機最佳化的 Power BI 報表，並與其互動](mobile-apps-view-phone-report.md)
* [建立為手機最佳化的報表版本](desktop-create-phone-report.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

