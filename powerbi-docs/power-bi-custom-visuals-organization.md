---
title: "在 Power BI 中使用組織自訂視覺效果"
description: "在 Power BI 中使用、管理和建立組織自訂視覺效果"
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 02/06/2018
ms.author: maghan
ms.openlocfilehash: 2c90ea4a7e95c354b6dfaec04cff7e5e4009b55f
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>在 Power BI 中使用組織自訂視覺效果 (預覽)

您可以在 Power BI 中使用自訂視覺效果，為自己量身打造，或是針對要傳達的資料深入解析，建立獨特的視覺效果類型。 這些自訂視覺效果通常是由開發人員建立，當 Power BI 中包含的多種視覺效果不符合他們的需求時，他們經常會建立自訂視覺效果。 

在某些組織中，自訂視覺效果則更為重要，必須有它們才能傳達組織特有的特定資料或深入解析，它們也可能有特殊的資料需求，或凸顯私用商務方法。 此類組織需要開發自訂視覺效果、在整個組織中分享它們，並確保它們被妥善地維護。 Power BI 自訂視覺效果 (目前為預覽階段) 可讓組織達到此目的。 

下列影像所顯示的程序說明 Power BI 流程中的組織自訂視覺效果 (預覽) 如何從系統管理員開始，經過開發及維護，最後到資料分析師手上。

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>如何啟用組織自訂視覺效果 (預覽)

組織自訂視覺效果目前為預覽階段，因此您必須在 Power BI Desktop 中啟用該功能。 若要啟用這個預覽功能，請從功能區選取 [檔案] > [選項及設定] > [選項]，然後在左側窗格中選取 [預覽功能]，接著選取 [我的組織自訂視覺效果] 旁的核取方塊，如下面的影像所示。

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

組織視覺效果是由 Power BI 系統管理員從系統管理入口網站中部署及管理的。 一旦部署到組織存放庫，組織中的使用者就可以輕鬆地探索組織自訂視覺效果，並直接從 Power BI Desktop 將它們匯入至其報告中。

## <a name="using-organizational-custom-visuals"></a>使用組織自訂視覺效果

若要深入了解如何在您建立的報告中使用組織自訂視覺效果，請參閱下列文章：[深入了解如何將組織視覺效果匯入自己的報告](power-bi-custom-visuals.md)。
 
## <a name="administering-organizational-custom-visuals"></a>管理組織自訂視覺效果

若要深入了解如何管理、部署組織內的組織自訂視覺效果，請參閱下列文章：[深入了解組織自訂視覺效果的部署和管理](https://go.microsoft.com/fwlink/?linkid=866790)。

> [!WARNING]
> 自訂視覺效果可能包含有安全性或隱私權風險的程式碼。 將任何自訂視覺效果部署到組織存放庫之前，請確定您信任其作者和來源。 
> 

## <a name="considerations-and-limitations"></a>考量與限制
 
由於組織自訂視覺效果目前為預覽階段，有少數考量和限制您必須留意並納入考量。
 
系統管理員：

* 不支援舊版自訂視覺效果 (例如並非基於新版本 API 所建立的自訂視覺效果)

* 不支援就地更新。 若要更新視覺效果，您必須將新版的視覺效果上傳到組織存放庫 (也請確定其 PBIVIZ 檔案中具有相同的視覺效果識別碼)。 報告作者接著可將新版視覺效果匯入至其報告，並就地取代其報告中目前的視覺效果版本。

* 如果從存放庫刪除某個自訂視覺效果，使用已刪除之視覺效果的任何現有報告將會停止轉譯。 存放庫的刪除作業是無法復原的。
 
使用者：

* 不支援使用來自公用 Marketplace (AppSource) 和來自組織存放庫的相同視覺效果 (相同的視覺效果識別碼)。 在該情況下，將會使用最後匯入的視覺效果。

* 不支援對外部共用儀表板和報告中的組織視覺效果。 組織外部的使用者檢視含有組織自訂視覺效果的儀表板時，將會看到空白的視覺效果。 

* Power BI 工作區集合不支援組織視覺效果

* 發佈至 Web 之報告中的組織自訂視覺效果將不會轉譯

* 來自 AppSource Marketplace 的 Visio 視覺效果、PowerApps 視覺效果和 GlobeMap 視覺效果，若透過組織存放庫部署，將不會轉譯

* 如果系統管理員從存放庫刪除自訂視覺效果，而該視覺效果已用於報告中，則它會停止轉譯，且必須將它從報告中移除，才能儲存報告