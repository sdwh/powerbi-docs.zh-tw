---
title: "檢視為手機最佳化的 Power BI 報表"
description: "了解與報表頁面進行互動，該頁面已針對在 Power BI 手機應用程式中檢視進行最佳化。"
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
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 54a1b81cc4281db7a622668ba205c1c57d5e396d
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>檢視為手機最佳化的 Power BI 報表
當您在 Power BI Desktop 建立 Power BI 報表時，您也可以建立新版的[針對在手機上的 Power BI 應用程式中檢視進行最佳化的報表](desktop-create-phone-report.md)。

然後，當您在手機上開啟 Power BI 報表時，Power BI 會偵測報表是否已針對手機進行最佳化，並自動以直向檢視開啟已經過最佳化的報表。

![直向模式中的報表](media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

如果為手機最佳化的報表不存在，報表仍會開啟，但會使用非最佳化的橫向檢視。 即使在為手機最佳化的報表中，如果您將手機橫放，報表也會以非最佳化的檢視開啟，並顯示原始報表配置。 如果只有部分頁面經過最佳化，您會在直向檢視中看到訊息指出報表可以橫向呈現。

![未將報表頁面最佳化](media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Power BI 報表的其他所有功能都仍可在為手機最佳化的報表中運作。 深入了解您可以在下列項目執行的作業︰

* [iPhone 上的報表](mobile-reports-in-the-mobile-apps.md)。 
* [Android 手機上的報表](mobile-reports-in-the-mobile-apps.md)。

## <a name="filter-the-report-page-on-an-iphone"></a>在 iPhone 上篩選報表頁面
如果為手機最佳化的報表已定義篩選，當您在 iPhone 上檢視報表時，就可以使用這些篩選。 

1. 點選篩選圖示 ![手機篩選圖示](media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) 在頁面底部。 
2. 使用基本或進階篩選，查看您感興趣的結果。
   
    ![Power BI 電話報表進階篩選器](media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>跨醒目提示視覺效果
手機報表的跨醒目提示視覺效果運作方式與在 Power BI 服務中，以及手機上橫向檢視的報表相同︰當您選取一個視覺效果的資料時，即會醒目提示該頁面上其他視覺效果中的相關資料。

深入了解 [Power BI 中進行篩選和醒目提示](power-bi-reports-filters-and-highlighting.md)的相關事項。

## <a name="select-visuals"></a>選取視覺效果
在手機報表中，當您選取視覺效果時，手機報表會醒目提示該視覺效果並聚焦於其上，抵銷畫布筆勢。

選取視覺效果時，您便可執行在視覺效果中捲動等動作。 若要將視覺效果取消選取，只要觸碰視覺效果區域外的任何一處。

## <a name="open-visuals-in-focus-mode"></a>以焦點模式開啟視覺效果
手機報表也具備焦點模式，讓您能夠放大檢視單一視覺效果，以及探索該視覺效果與報表。

* 在手機報表中，點選視覺效果右上角的省略符號 (**...**) > [展開為焦點模式]。
  
    ![展開為焦點模式](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

您在焦點模式所執行的動作會沿用至報表畫布，反之亦然，提供您順暢的探索體驗。 比方說，如果您將視覺效果中的值醒目提示，然後返回整份報表，整個報表會篩選至您在視覺效果中醒目提示的值。

有鑑於螢幕大小限制，某些動作只有在焦點模式中才可進行︰

* **向下切入**視覺效果中顯示的資訊。 在下方深入了解如何在手機報表中[向下和向上切入](mobile-apps-view-phone-report.md#drill-down-in-a-visual)。
* **排序**視覺效果中的值。
* **還原**︰清除您已在視覺效果上執行的探索步驟，並還原至報表建立時設定的定義。
  
    若要清除視覺效果中的所有探索，請點選省略符號 (**...**) > [還原]。
  
    ![還原](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    報表層級可進行還原，進而清除所有視覺效果的探索；而視覺效果層級，可清除所選特定視覺效果的所有探索。   

## <a name="drill-down-in-a-visual"></a>在視覺效果中向下切入
如果視覺效果中定義了階層層級，您就可以向下切入視覺效果中顯示的詳細資訊，然後返回。 您可以在 Power BI 服務或 Power BI Desktop 中[新增視覺效果的向下切入](power-bi-visualization-drill-down.md)。 當您在手機上檢視已為手機最佳化的 Power BI 報表時，才能使用向下切入。 

1. 在手機上報表中，點選右上角的省略符號 (**...**) > [展開為焦點模式]。
   
    ![展開為焦點模式](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    在本例中，橫條會顯示各州的值。
2. 點選左下角的 ![探索圖示](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) 探索圖示。
   
    ![探索模式](media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. 點選 [顯示下一個層級] 或 [展開至下一個層級]。
   
    ![展開至下一個層級](media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    現在，橫條會顯示城市的值。
   
    ![展開的層級](media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. 如果您點選左上角的箭號，會回到手機報表，但值仍是展開到較低層級的狀態。
   
    ![保持展開至較低層級](media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. 若要回到原本層級，請再次點選省略符號 (**...**) > [還原]。
   
    ![還原](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="next-steps"></a>後續步驟
* [建立為 Power BI 手機應用程式最佳化的報表](desktop-create-phone-report.md)
* [在 Power BI 中建立儀表板的手機檢視](service-create-dashboard-mobile-phone-view.md)
* [建立適用於任何大小的回應式視覺效果](desktop-create-responsive-visuals.md)
* 有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

