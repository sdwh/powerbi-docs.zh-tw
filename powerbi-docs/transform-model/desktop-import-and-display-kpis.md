---
title: 在 Power BI 中匯入和顯示 KPI
description: 匯入和顯示 KPI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 41289fbfb76dc2453ccb871f93cf1cb4e18de7f7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237105"
---
# <a name="import-and-display-kpis-in-power-bi"></a>在 Power BI 中匯入和顯示 KPI
透過 **Power BI Desktop**，您可以在資料表、矩陣和卡片中匯入和顯示 KPI。

請遵循下列步驟來匯入和顯示 KPI。

1. 啟動具有 Power Pivot 模型和 KPI 的 Excel 活頁簿。 這項練習使用名為 *KPI* 的活頁簿。

1. 使用 [檔案] -> [匯入] -> [Excel 活頁簿內容]  ，將 Excel 活頁簿匯入至 Power BI。 您也可以[了解如何匯入活頁簿](../connect-data/desktop-import-excel-workbooks.md)。 

1. 匯入至 Power BI 之後，您的 KPI 會出現在 [欄位]  窗格中，並且以![號誌燈](media/desktop-import-and-display-kpis/traffic.png)圖示標示。 若要在您的報表中使用 KPI，請務必展開其內容，將 [值]  、[目標]  和 [狀態]  欄位公開。

    ![](media/desktop-import-and-display-kpis/desktoppreviewfeatureon2.png)

1. 匯入的 KPI 最適合在標準視覺效果類型中使用，例如 [資料表]  類型。 Power BI 也包含 [KPI]  視覺效果類型，而它只應該用於建立新的 KPI。
   
    ![](media/desktop-import-and-display-kpis/desktoppreviewfeatureon3.png)

就是這麼簡單。 您可以使用 KPI 來強調趨勢、進度或其他重要指標。
