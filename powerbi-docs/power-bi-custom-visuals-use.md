---
title: "在報表中新增自訂視覺效果 (Desktop)"
description: "在 Desktop 的報表中新增自訂視覺效果"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 03/15/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: b3a3e34fac546ee57cd66924e72a2c93aa647850
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="add-a-custom-visual-to-a-report-desktop"></a>在報表中新增自訂視覺效果 (Desktop)
您已經[下載自訂的視覺效果範本](service-custom-visuals-office-store.md)，並將其儲存至電腦或其他位置。  下個步驟是將該自訂視覺效果範本匯入報表，將這個範本新增為 [視覺效果] 窗格的選項。

![](media/power-bi-custom-visuals-use/pbi-custom-viz-icon.png)

自訂視覺效果範本在匯入後會加入特定的報表中。 如果想在另一份報表中使用這個視覺效果範本，您必須將其也匯入該報表。 使用 [另存新檔]  選項儲存具有自訂視覺效果的報表時，自訂視覺效果範本的複本就會與新報表一起儲存。

1. 開啟 Power BI Desktop，然後選取要加入自訂視覺效果的報表。   
2. 有兩個選項可以匯入自訂視覺效果範本：從 [檔案]  功能表或從 [視覺效果]  窗格。
   
    **從 Desktop 的 [檔案] 功能表**
   
    在報表的 [檔案] 功能表上，選擇 [匯入] &gt; [Power BI 自訂視覺效果]。 您必須使用編輯檢視。    
   
      ![](media/power-bi-custom-visuals-use/power-bi-import.png)
   
    **從視覺效果窗格**
   
    在 [視覺效果]  窗格中選擇 [插入 (...)] 。    
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
   
    選取 [匯入自訂視覺效果]。  
   
      ![](media/power-bi-custom-visuals-use/insertpane.png)
3. **檢閱警告**。
   
    自訂視覺效果可以存取報表中的資料，而且當您共用包含自訂視覺效果的報表時，您的同事也可以存取相同的資料。 請小心檢閱自訂視覺效果，以確定其來自可信任的來源。 如果不確定是否要使用取自 Office 線上商店、透過電子郵件或來自其他來源的特定自訂視覺效果，Microsoft 建議您和 IT 部門合作。
   
    ![](media/power-bi-custom-visuals-use/caution.png)
4. 巡覽至儲存自訂視覺效果 .pbiviz 檔案的位置，然後開啟它。
5. 有圖示 (也稱為*範本*) 會新增至您的 [視覺效果] 窗格中。
   
    ![](media/power-bi-custom-visuals-use/visualuse.png)
6. 選取自訂視覺效果範本，以如同使用 [視覺效果] 窗格中任何其他範本的方式，將其新增至報表。 新增欄位和篩選條件，並建立您的視覺效果。
7. 以您將其他任何視覺效果格式化的方式應用於自訂視覺效果。  從 [視覺效果] 窗格中，選取油漆滾筒圖示。 可用的格式化選項會根據視覺效果類型而有所不同。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
* 若要在[匯出至 PowerPoint](service-publish-to-powerpoint.md) 時支援自訂視覺效果，或[將其顯示在客戶訂閱報表頁面時收到的電子郵件中](service-report-subscribe.md)，則需要將它們定義為已通過 Microsoft 自訂視覺效果認證程序的「經認證的自訂視覺效果」。  若要查看「經認證的自訂視覺效果」清單，以及深入了解認證程序，請參閱[經認證的自訂視覺效果](power-bi-custom-visuals-certified.md)

## <a name="next-steps"></a>後續步驟
[下載並使用 Office 市集的自訂視覺效果](service-custom-visuals-office-store.md)  
[在 Power BI 服務的報表中新增自訂視覺效果](power-bi-report-add-custom-visual.md)  
[將自訂視覺效果發佈至 Office 市集](developer/office-store.md)  
[Power BI 中的自訂視覺效果](power-bi-custom-visuals.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

