---
title: 教學課程：使用 Power BI 的 [使用 EXCEL 分析]，從 Excel 開始
description: 在本教學課程中，您會從 Excel 開始，然後連線至 Power BI 的 [資料集] 頁面，以將資料集匯入至 Excel。
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/13/2020
ms.author: tekulka
LocalizationGroup: Connect to services
ms.openlocfilehash: 9a8dd1eb7aa6b239cc542884ab3fae3679997017
ms.sourcegitcommit: 3c51431d85793b71f378c4b0b74483dfdd8411b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2020
ms.locfileid: "80464616"
---
# <a name="tutorial-use-power-bi-analyze-in-excel-starting-in-excel"></a>教學課程：使用 Power BI 的 [使用 EXCEL 分析]，從 Excel 開始

您的組織使用 Power BI 來共用資料存取權。 從 Excel 啟動 Power BI 的 [使用 EXCEL 分析] 功能，以建立 Excel 的樞紐分析表和樞紐分析圖。 其可將額外內容帶入您的分析，或縮短尋找和匯入相關資料集的時間。

若要開始使用 Power BI 資料集，請在 Excel 中選取 [使用 EXCEL 分析]。 系統會引導您建立使用該資料的樞紐分析表。  

您可以返回 [資料集] 頁面來找到您組織所共用的其他資料集。

如果您在任何時間點遇到問題，請在下列流程中的適當步驟選取 [否]  ，並在連結的表單中提供意見反應。  

在本教學課程中，您會了解如何：

> [!div class="checklist"]
> * 從 Power BI [資料集] 頁面下載 ODC 檔案。
> * 允許從 Excel 存取您的資料集。
> * 開始使用資料集來建立樞紐分析表、圖表和工作表

## <a name="prerequisites"></a>必要條件

若要完成本教學課程，您需要：

* 一個 Power BI 帳戶。 如果您尚未註冊 Power BI，請先進行[免費註冊](https://app.powerbi.com/signupredirect?pbi_source=web)再開始。

* 確定您已熟悉[開始使用 Power BI 服務](https://docs.microsoft.com/power-bi/service-get-started)教學課程中所列的所有步驟。

* 您需要 Power BI Premium 資料集和 Power BI Pro 授權，請瀏覽[什麼是 Power BI Premium？](https://docs.microsoft.com/power-bi/service-premium-what-is)以取得詳細資訊。

* 您可以在詳盡的[使用 Excel 分析](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements)文件中找到先決條件的完整清單。

* 有效的 [Microsoft Office E5 訂閱](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab)

## <a name="get-started"></a>開始使用

一開始在 Excel 中，選取使用 Power BI 共用資料建立樞紐分析表的選項，並瀏覽至 Power BI [資料集] 頁面。

![[資料集] 頁面](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

使用 [使用 Excel 分析] 工作流程時，您將會看到數個引導您的提示；請指出您是否已完成每個步驟以繼續進行。 如果您在任何步驟遇到問題，請選取 [否]  ，並在相對應的表單中提供意見反應。

![工作流程指示](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>下載並開啟 ODC 檔案

從相對應的清單及相關聯的工作區中選擇您的資料集，然後按一下 [使用 Excel 分析]。 Power BI 會建立 ODC 檔案，然後從瀏覽器將其下載到您的電腦。

![選取資料集](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

當您在 Excel 中開啟檔案時，您會看到一個空白的樞紐分析表和欄位清單，其中具有來自 Power BI 資料集的資料表、欄位和量值。 如同您可以在 Excel 中使用本機資料集工作一樣，您可以建立樞紐分析表、 圖表和分析該資料集。

## <a name="enable-data-connections"></a>啟用資料連線

若要在 Excel 中分析 Power BI 資料，系統可能會提示您信任連線。 系統管理員可以從 Power BI 管理入口網站停用對 Analysis Services 資料庫上的內部部署資料集使用 [使用 Excel 分析] 的功能。

![啟用連線](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>安裝更新並驗證

當您首次開啟新的 ODC 檔案時，您也可能需要使用您的 Power BI 帳戶進行驗證。  如果您遇到問題，請瀏覽詳盡的[使用 Excel 分析](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi )文件以取得詳細資訊，或在工作流程期間按一下 [否]。

![啟用連線](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>分析為離開

[使用 Excel 分析] 與其他本機活頁簿類似，可讓您建立樞紐分析表及圖表、新增資料，以及建立能檢視您資料的不同工作表。 [使用 Excel 分析] 會將所有詳細等級的資料公開給任何具有資料集權限的使用者。 您可以儲存此活頁簿，但不能將其發佈或匯入回 Power BI，或是與組織中其他使用者共用。 如需詳細資訊和其他使用案例，請瀏覽[使用 Excel 分析](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away)。

## <a name="clean-up-resources"></a>清除資源

與 Power BI 服務和 [資料集] 頁面的互動應僅限於下載 ODC 檔案，以及按一下以繼續工作流程。 如果您在這些步驟中遇到問題，請在適當的步驟指出 [否]  ，並在連結的表單中提供意見反應。 表單會包含可提供問題詳細資訊的連結。 重新瀏覽 [資料集] 頁面以重試該程序，或是選取另一個資料集。

## <a name="next-steps"></a>後續步驟

您可能也會對下列文章感興趣：

* [在 Power BI Desktop 中使用跨報表鑽研](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through)

* [使用 Power BI Desktop 交叉分析篩選器](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
