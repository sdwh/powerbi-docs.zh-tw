---
title: 針對任何大小最佳化 Power BI 視覺效果
description: 了解如何為 Power BI 手機應用程式將 Power BI Desktop 與 Power BI 服務中現有報表的視覺效果最佳化。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 4372f37cf6afc8fe51d6650ddd888bd41d3ea678
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280117"
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>針對任何大小最佳化 Power BI 視覺效果
根據預設，每當您建立新報表時，視覺效果都是「回應式」的：無論螢幕的大小，它們都會動態地變更，以顯示最大量的資料和見解。 對於較舊的報表，您可以設定其視覺效果以動態方式調整大小。

視覺效果的大小變更時，Power BI 會排定資料檢視的優先順序，例如自動移除邊框，並將圖例移至視覺效果頂部，如此一來即使視覺效果變小，也能充分表達資訊。 對於手機上 Power BI 行動應用程式中的視覺效果而言，回應能力特別實用。

![調整回應式視覺效果大小](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

任何使用 X 和 Y 軸的視覺效果及交叉分析篩選器都可回應式調整大小。

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>在 Power BI Desktop 中開啟回應能力
1. 在 Power BI Desktop 舊版報表中的 [檢視] 索引標籤上，確定您是在 [桌面配置] 中。
   
    ![電腦版面配置圖示](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. 選取視覺效果，然後在 [視覺效果] 窗格中選取 [格式] 部分。
3. 展開 [一般] > 將 [回應式] 切換為 [開啟]。
   
    ![回應式開啟](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     現在，當您[建立已為手機最佳化的報表](../desktop-create-phone-report.md)並新增此視覺效果時，它就會適當調整大小。

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>在 Power BI 服務中開啟回應能力
您可以在 Power BI 服務中，開啟舊版報表視覺效果的回應能力。 您必須能夠編輯報表。

1. 在 Power BI 服務的報表中 ([https://powerbi.com](https://powerbi.com))，選取 [編輯報表]。
2. 選取視覺效果，然後在 [視覺效果] 窗格中選取 [格式] 部分。
3. 展開 [一般] > 將 [回應式] 切換為 [開啟]。
   
    ![回應式開啟](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     現在，當您[建立此報表的手機檢視](../desktop-create-phone-report.md)並新增此視覺效果時，它就會適當調整大小。

## <a name="next-steps"></a>後續步驟
* [建立為 Power BI 手機應用程式最佳化的報表](../desktop-create-phone-report.md)
* [檢視為手機最佳化的 Power BI 報表](../consumer/mobile/mobile-apps-view-phone-report.md)
* 有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

