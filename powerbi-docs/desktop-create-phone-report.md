---
title: 為 Power BI 行動裝置應用程式最佳化報表
description: 了解如何專為手機與平板電腦建立直向版報表，將 Power BI 行動應用程式的報表頁面最佳化。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2dca4094ed0c21c421aa2fef89353e6f210b3ea4
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761471"
---
# <a name="optimize-power-bi-reports-for-the-mobile-app"></a>為行動裝置應用程式最佳化 Power BI 報表
您可以透過建立直向版面配置，改善在行動裝置應用程式中檢視報表的體驗。 在 Power BI Desktop 和 Power BI 服務中，您可以重新排列和重新調整報表視覺效果的大小，來取得直向模式中的最佳體驗。  

正在尋找在行動裝置上檢視報表的資訊嗎？ 請嘗試此快速入門：[探索 Power BI 行動裝置應用程式中的儀表板和報表](consumer/mobile/mobile-apps-quickstart-view-dashboard-report.md)。

![手機上的最佳化報表](media/desktop-create-phone-report/desktop-create-phone-report-1.png)

您可以建立[回應式視覺效果](#optimize-a-visual-for-any-size)和[回應式交叉分析篩選器](#enhance-slicers-to-work-well-in-phone-reports)，以便在任何地方都能重新調整大小。 如果您將篩選條件新增至報表，他們會自動顯示在最佳化報表中。

## <a name="lay-out-a-portrait-version-of-a-report-page"></a>報表頁面的直向版面配置版本

當您建立報表後，即可針對手機與平板電腦進行最佳化。

1. 在 Power BI Desktop [報表]  檢視的 [檢視]  索引標籤上，選取 [手機配置]  。  
   
    ![手機版面配置圖示](media/desktop-create-phone-report/desktop-create-phone-report-3.png)
   
    在 Power BI 服務中，選取 [編輯報表]   > [行動裝置版面配置]  。

    您會看到形狀像手機的空白畫布。 原始報表的所有視覺效果均列於右側 [視覺效果]  窗格中。

1. 若要將視覺效果新增至手機配置，請將其從 [視覺效果]  窗格拖曳至手機畫布。
   
    手機報表使用方格版面配置。 當您將視覺效果拖曳至手機畫布時，它們會貼齊該方格。
   
    ![拖放視覺效果](media/desktop-create-phone-report/desktop-create-phone-report-4.gif)
   
    您可以將部分或所有主要報表頁面的視覺效果新增至手機報表頁面。 您只能新增每個視覺效果一次，且不需要包含所有視覺效果。

1. 您可以在方格調整視覺效果的大小，方法如同儀表板及行動儀表板上的磚。
   
   手機報表方格會隨不同大小的手機縮放，因此您的報表在小螢幕及大螢幕手機上都很適合。
   
   ![調整視覺效果大小](media/desktop-create-phone-report/desktop-create-phone-report-5.gif)

## <a name="optimize-a-visual-for-any-size"></a>為任何大小將視覺效果最佳化
您可以將儀表板或報表中的視覺效果設定成「回應式」  。 無論螢幕的大小，視覺效果都會動態地變更，以顯示最大量的資料和見解。 

視覺效果的大小變更時，Power BI 會以資料檢視為優先。 例如，它可以自動移除邊框間距，並將圖例移至視覺效果頂端，如此一來即使視覺效果變小，也能充分表達資訊。

![調整回應式視覺效果大小](media/desktop-create-phone-report/desktop-create-phone-report-6.gif)

您可以選擇是否要開啟各個視覺效果的回應能力。 請參閱[最佳化視覺效果](visuals/desktop-create-responsive-visuals.md)。

## <a name="considerations-when-creating-phone-report-layouts"></a>建立手機報表版面配置的注意事項
* 若是多頁報表，您可以將所有頁面最佳化，也可以只對幾頁執行。 
* 如已定義報表頁面的背景色彩，則手機報表就會有相同的背景色彩。
* 不能只對手機修改格式設定。 格式設定在主要及手機版面配置上是一致的。 例如，字型大小會相同。
* 若要變更視覺效果，例如變更其格式設定、資料集或其他任何屬性，請回到一般報表撰寫模式。
* Power BI 會在行動裝置應用程式中，為手機報表提供預設標題與頁面名稱。 如果您已在報表中建立標題及頁面名稱的文字視覺效果，請考慮不要將其新增至您的手機報表。     

## <a name="remove-a-visual-from-the-phone-layout"></a>從手機版面配置移除視覺效果
* 若要移除視覺效果，請選取手機畫布上視覺效果右上角的 **X**，或加以選取後按 [刪除]  。
  
   移除此處的視覺效果只會將其自手機配置畫布中移除。 而視覺效果與原始報表則不會受到影響。
  
   ![移除視覺效果](media/desktop-create-phone-report/desktop-create-phone-report-7.gif)

## <a name="enhance-slicers-to-work-well-in-phone-reports"></a>增強交叉分析篩選器使其在手機報表中正常運作
交叉分析篩選器提供在畫布上篩選報表資料的功能。 在一般報表撰寫模式下設計交叉分析篩選器時，您可以修改部分交叉分析篩選器設定，使其更適用於手機報表：

* 決定報表讀者只能選取一個項目或多個項目。
* 在交叉分析篩選器周圍加上方塊，讓報表更容易掃描。
* 將交叉分析篩選器設為垂直、水平或回應式  。 

如果您將交叉分析篩選器設為回應式，則在變更其大小和形狀時會顯示較多或較少選項。 它可以是高、短、寬或窄。 如果您將它設得夠小，則它只會變成報表頁面上的篩選圖示。 

![Power BI 回應式交叉分析篩選器](media/desktop-create-phone-report/desktop-create-phone-report-8.png)

深入了解如何[建立回應式交叉分析篩選器](power-bi-slicer-filter-responsive.md)。

## <a name="publish-a-phone-report"></a>發行手機報表
若要發行手機版的報表，請[從 Power BI Desktop 將主要報表發行至 Power BI 服務](desktop-upload-desktop-files.md)，手機版即同時發行。
  
深入了解 [Power BI 中的共用與權限](service-how-to-collaborate-distribute-dashboards-reports.md)。

## <a name="view-optimized-and-unoptimized-reports-on-a-phone-or-tablet"></a>在手機或平板電腦上檢視最佳化與未最佳化的報表
在手機上的行動裝置應用程式中，Power BI 會自動偵測最佳化及未最佳化的手機報表。 如果有已為手機最佳化的報表，Power BI 手機應用程式會自動以手機報表模式開啟該報表。

如果沒有已為手機最佳化的報表，報表則會以未經過最佳化的橫向檢視開啟。  

使用手機報表時，若將手機橫放，則無論報表是否已經過最佳化，都會在未經過最佳化的檢視中，以原始報表版面配置開啟報表。

如果只將部分頁面最佳化，則讀者會在縱向檢視中看到訊息，其指出報表可以橫向呈現。

![未經過最佳化的手機頁面](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

報表讀者可以將手機或平板電腦轉向側邊，以橫向模式查看頁面。 深入了解[與為直向模式最佳化的 Power BI 報表互動](consumer/mobile/mobile-apps-view-phone-report.md)。

## <a name="next-steps"></a>後續步驟
* [在 Power BI 中建立儀表板的手機檢視](service-create-dashboard-mobile-phone-view.md)。
* [檢視針對手機最佳化的 Power BI 報表](consumer/mobile/mobile-apps-view-phone-report.md)。
* [建立適用於任何大小的回應式視覺效果](visuals/desktop-create-responsive-visuals.md)。
* 有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)。

