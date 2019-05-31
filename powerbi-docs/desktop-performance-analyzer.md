---
title: 若要檢查 Power BI Desktop 中的報表項目的效能使用 Performance Analyzer
description: 了解如何執行資源使用狀況和回應性方面的視覺效果和報表項目
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854405"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>使用 Performance Analyzer 來檢查報表項目的效能

在  **Power BI Desktop**可以找到的外報表元素，例如視覺效果和 DAX 公式的每個執行的方式。 使用**Performance Analyzer**、 您所見，並記錄記錄的測量每個您的報表項目執行時使用者與它們互動的方式和其效能的哪一面會耗用大量的大部分 （或最少） 資源。

![效能分析程式](media/desktop-performance-analyzer/performance-analyzer-01.png)

Performance Analyzer 會檢查及顯示更新或重新整理所有視覺效果所需的持續時間起始，該使用者互動，並呈現資訊，因此您可以檢視、 向下鑽研，或將結果匯出。 Performance Analyzer 可協助您識別會影響您的報表的效能的視覺效果，並找出影響的原因。

## <a name="displaying-the-performance-analyzer-pane"></a>顯示 [Performance Analyzer] 窗格

在  **Power BI Desktop**選取**檢視**功能區。 在**顯示**區域**檢視**您也可以選取此核取方塊旁的功能區**Performance Analyzer**以顯示 [Performance Analyzer] 窗格。

![選取 檢視 功能區中的 Performance analyzer](media/desktop-performance-analyzer/performance-analyzer-02.png)

一旦選取，Performance Analyzer 會顯示在它自己窗格中，於報表畫布右方。

## <a name="using-performance-analyzer"></a>使用效能分析程式

效能分析程式量值 （包括建立或更新視覺效果的時間） 的處理時間才能更新起始，因為執行查詢會產生任何使用者互動的報表項目。 比方說，調整交叉分析篩選器需要的交叉分析篩選器視覺效果，以進行修改，要傳送至資料模型中，查詢和受影響的視覺效果，必須更新，因為新的設定。 

若要開始錄製的 Performance Analyzer，只需選取**開始錄製**

![開始錄製](media/desktop-performance-analyzer/performance-analyzer-03.png)

會顯示您在報表中採取任何動作，並登入 Performance Analyzer] 窗格的 [視覺效果由 Power BI 載入的順序。 比方說，或許您有使用者說會很長的時間，若要重新整理報表。 或在報表中的某些視覺效果需要更長的時間，以顯示調整滑桿時。 效能分析師可以告訴您哪些視覺效果是罪魁禍首，並識別視覺效果的哪一面正在處理的最長持續時間。 

一旦您開始錄製**開始錄製**按鈕會變為灰色外 （非使用中，因為您已經開始錄製） 和**停止**按鈕才有作用。 

效能分析程式會收集，並即時顯示的效能度量資訊。 因此每次您按一下視覺效果，移動交叉分析篩選器，或以其他方式互動 Performance Analyzer 立即其窗格中顯示的效能結果。

如果窗格具有數多於可以顯示的詳細資訊，，出現捲軸來瀏覽至 其他資訊。

每個互動有在窗格中，描述起始記錄項目之動作的區段的識別碼。 下圖中，在互動會是使用者變更交叉分析篩選器。

![互動的型別為基礎的區段](media/desktop-performance-analyzer/performance-analyzer-04.png)

每個視覺效果的記錄資訊會包括花費的時間 （持續時間） 完成的工作類別如下：

* **DAX 查詢**-需要 DAX 查詢時，這是之間視覺效果傳送查詢，並傳回結果的 Analysis services 的時間。
* **視覺效果顯示**-的畫面，包括擷取任何 web 映像或進行地理編碼所需的時間上繪製視覺效果所需的時間。 
* **其他**-視覺效果一樣的準備查詢、 等待其他視覺效果，才能完成，或執行其他背景處理所需的時間。

![記錄資訊的項目](media/desktop-performance-analyzer/performance-analyzer-06.png)

您已與您想要測量與效能分析報表的項目互動之後，您可以選取**停止** 按鈕。 效能資訊會保留在窗格中，選取後**停止**供您分析。

若要清除 [Performance Analyzer] 窗格中的資訊，請選取**清除**。 所有資訊都會清除，並不會儲存當您選取**清除**。 請參閱下一節以了解如何將資訊儲存在記錄檔。 

## <a name="refreshing-visuals"></a>重新整理視覺效果

您可以選取**重新整理視覺效果**在 Performance Analyzer 窗格中，重新整理報表的目前頁面上的所有視覺效果，並藉此讓 Performance Analyzer 收集這類的所有視覺效果的相關資訊。

您也可以重新整理個別視覺效果。 Performance Analyzer 錄影時，您可以選取**重新整理此視覺效果**位於右上角，每個視覺效果，以重新整理該視覺效果，並擷取它的效能資訊。

![重新整理個別的視覺效果](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>儲存效能資訊

您可以藉由選取儲存 Performance Analyzer 會建立有關報表的資訊**匯出** 按鈕。 選取**匯出**Performance Analyzer 窗格中的資訊建立.json 檔案。 

![儲存記錄檔中的效能分析程式](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>後續步驟
如需 **Power BI Desktop** 的詳細資訊，以及如何開始使用，請參閱下列文章。

* [Power BI Desktop 是什麼？](desktop-what-is-desktop.md)
* [Power BI Desktop 的查詢概觀](desktop-query-overview.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [連接至 Power BI Desktop 中的資料](desktop-connect-to-data.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常見查詢工作](desktop-common-query-tasks.md)   

