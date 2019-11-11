---
title: 在 Power Query 編輯器中使用 R
description: 在 Power BI Desktop 查詢編輯器中使用 R 以進行進階分析
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d2ba33e18701ad147cb38072461804b4528101ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877934"
---
# <a name="use-r-in-query-editor"></a>在查詢編輯器中使用 R

[**R**](https://mran.microsoft.com/documents/what-is-r) 是一種強大的程式語言，許多統計學家、資料科學家和資料分析師都會使用這種語言。 您可以在 Power BI Desktop 的 [查詢編輯器]  中使用 **R** 來：

* 準備資料模型

* 建立報表

* 清理資料、進行進階的資料塑造和資料集分析，其中包括遺漏資料完成、預測叢集等。  

## <a name="install-r"></a>安裝 R

您可以從 [Revolution Open 下載頁面](https://mran.revolutionanalytics.com/download/)和 [CRAN 存放庫](https://cran.r-project.org/bin/windows/base/)免費下載 **R**。

### <a name="install-mice"></a>安裝 mice

您需要在您的 R 環境中安裝 [**mice** 程式庫](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice)。 若沒有 **mice**，範例指令碼將無法正常運作。 **mice** 套件會實作處理遺漏資料的方法。

安裝 **mice**：

1. 啟動 R.exe 程式 (例如 C:\Program Files\Microsoft\R Open\R-3.5.3\bin\R.exe)  

2. 執行安裝命令：

   ``` 
   >  install.packages('mice') 
   ```

## <a name="use-r-in-query-editor"></a>在查詢編輯器中使用 R

為了示範在 [查詢編輯器]  中使用 **R**，我們會使用包含在 .csv 檔案中的範例股市資料集，並逐步完成下列步驟：

1. [下載 **EuStockMarkets_NA.csv** 檔案](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv)。 請記住您儲存的位置。

1. 將檔案載入 **Power BI Desktop**：從 [常用]  功能區中，選取 [取得資料] > [文字/CSV]  。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. 選取檔案，然後選取 [開啟]  。 CSV 資料隨即顯示在 [文字/CSV 檔案]  對話方塊中。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. 載入資料後，您可以在 [欄位]  窗格中看見它。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. 若要開啟 [查詢編輯器]  ，請從 [常用]  功能區中，選取 [編輯查詢]  。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. 在 [轉換]  功能區中，選取 [執行 R 指令碼]  。 隨即出現 [執行 R 指令碼]  編輯器。  

   資料列 15 和 20 包含遺漏資料，其他您在影像中看不到的資料列也包含遺漏資料。 下列步驟會示範 R 為您完成這些資料列的方式。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. 針對此範例，請輸入下列指令碼。 請務必將 '&lt;您的檔案路徑&gt;' 替換成您本機檔案系統上指向 **EuStockMarkets_NA.csv** 的路徑，例如 C:/Users/John Doe/Documents/Microsoft/EuStockMarkets_NA.csv

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > 您可能需要覆寫名為 *output* 的變數，以適當地建立已套用篩選的新資料集。

7. 選取 [確定]  之後，**查詢編輯器**會顯示有關資料隱私權的警告。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. 若要讓 R 指令碼在 Power BI 服務中正常運作，您需要將所有資料來源設為 [公開]  。 如需隱私權設定及其含意的詳細資訊，請參閱[隱私權等級](desktop-privacy-levels.md)。

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   在選取 [儲存]  後，指令碼會隨即執行。 請注意 [欄位]  窗格中稱為 **completedValues** 的新資料行。 請注意，這裡有多個遺失的資料項目，像是第 15 和 18 列。 請參閱下一節，看 R 如何處理該狀況。

   在 R 指令碼只有五行的情況下，**查詢編輯器**透過預測模型填入遺失的值。

## <a name="create-visuals-from-r-script-data"></a>從 R 指令碼資料建立視覺效果

現在我們可以建立視覺效果，以了解 R 指令碼如何使用 **mice** 程式庫補足遺失的值，如下圖所示：

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

您可以在一個 **Power BI Desktop** .pbix 檔案中儲存所有完成的視覺效果，然後在 Power BI 服務中使用資料模型和它的 R 指令碼。

> [!NOTE]
> 您可以[下載已完成所有步驟的 .pbix 檔案](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix)。

在您將 .pbix 檔案上傳到 Power BI 服務後，您需要採取額外步驟來啟用服務資料重新整理和更新後的視覺效果：  

* **為資料集啟用排程重新整理** - 若要為包含資料集和 R 指令碼的活頁簿啟用排程重新整理，請參閱[設定排程重新整理](refresh-scheduled-refresh.md)，其中也包括**個人閘道**相關資訊。

* **安裝個人閘道** - 您需要在檔案和 **R** 所在的電腦上安裝**個人閘道**。 Power BI 服務會存取該活頁簿，並重新轉譯任何更新後的視覺效果。 如需詳細資訊，您可以查看[安裝和設定個人閘道](service-gateway-personal-mode.md)。

## <a name="limitations"></a>限制

建立於**查詢編輯器**並含有 R 指令碼的查詢有幾項限制：

* 所有 R 資料來源設定都必須設為 [公開]  。 所有 [查詢編輯器]  查詢中的其他步驟也都必須是公開。 若要進行資料來源設定，請在 **Power BI Desktop** 中，選取 [檔案] > [選項和設定] > [資料來源設定]  。

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  在 [資料來源設定]  對話方塊中，選取資料來源，然後選取 [編輯權限...]  。將 [隱私權層級]  設為 [公開]  。

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* 若要啟用 R 視覺效果或資料集的排程重新整理，您必須啟用 [排程重新整理]  ，並在包含活頁簿與 **R** 的電腦上安裝**個人閘道**。如需這兩者的詳細資訊，請參閱本文前一節，其中提供了深入了解各項的連結。

R 和自訂查詢有各種用途，您可以用想要的呈現方式探索資料並使其成形。

## <a name="next-steps"></a>後續步驟

* [Introduction to R](https://mran.microsoft.com/documents/what-is-r) (R 簡介) 

* [在 Power BI Desktop 中執行 R 指令碼](desktop-r-scripts.md) 

* [在 Power BI 使用外部 R IDE](desktop-r-ide.md) 

* [Power BI 服務中的 R 套件](service-r-packages-support.md)
