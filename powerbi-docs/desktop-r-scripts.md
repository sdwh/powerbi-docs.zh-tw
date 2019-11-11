---
title: 在 Power BI Desktop 中執行 R 指令碼
description: 在 Power BI Desktop 中執行 R 指令碼
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b69f701e0a5b9030a1f4469d6b09b189759debc
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876188"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>在 Power BI Desktop 中執行 R 指令碼
您可以直接在 **Power BI Desktop** 執行 R 指令碼，並將產生的資料集匯入 Power BI Desktop 資料模型。

## <a name="install-r"></a>安裝 R
若要在 Power BI Desktop 執行 R 指令碼，您需要在本機電腦上安裝 **R** 。 您可以從許多位置免費下載並安裝 **R**，包括 [Revolution Open 下載頁面](https://mran.revolutionanalytics.com/download/)以及 [CRAN 儲存機制](https://cran.r-project.org/bin/windows/base/)。 Power BI Desktop 目前版本的 R 指令碼支援安裝路徑中的 Unicode 字元和空格 (空白字元)。

## <a name="run-r-scripts"></a>執行 R 指令碼
只需 Power BI Desktop 中的幾個步驟，您就可以執行 R 指令碼和建立資料模型，從中您可以建立報表，並在 Power BI 服務共用。 Power BI Desktop的 R 指令碼現在支援包含小數點 (.) 和逗號 (，) 的數字格式。

### <a name="prepare-an-r-script"></a>準備 R 指令碼
若要在 Power BI Desktop 執行 R 指令碼，請在本機 R 開發環境中建立指令碼，並確定已順利執行。

若要在 Power BI Desktop 執行該指令碼，請確定該指令碼可在新的和未修改的工作區中順利執行。 這表示，所有套件和相依性都必須明確地載入並執行。 您可以使用 *source ()* 執行相依的指令碼。

在 Power BI Desktop 準備和執行 R 指令碼時，會有一些限制：

* 只有資料框架會匯入，因此請確定您要匯入至 Power BI 的資料都位於資料框架中
* 類型為 [複雜] 和 [向量] 的資料行不會匯入，並會在建立的資料表中以錯誤值取代
* N/A 值會轉譯為 Power BI Desktop 中的 NULL 值
* 任何 R 指令碼若執行時間超過 30 分鐘就會逾時
* 在 R 指令碼中的互動式呼叫 (例如等待使用者輸入) 會中止指令碼執行
* 在 R 指令碼中設定工作目錄時，您「必須」  定義工作目錄的完整路徑，而非相對路徑

### <a name="run-your-r-script-and-import-data"></a>執行 R 指令碼並匯入資料
1. 在 Power BI Desktop 中，R 指令碼資料連接器可在 [取得資料]  中找到。 若要執行 R 指令碼，請選取 [取得資料] &gt; [其他...]  ，然後選取 [其他] &gt; [R 指令碼]  ，如下圖所示：
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. 如果您的本機電腦上安裝 R，就會選取已安裝最新的版本做為 R 引擎。 只要將您的指令碼複製到指令碼視窗，然後選取 [確定]  。
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. 如果 R 未安裝、無法識別，或者如果在本機電腦上有多個安裝，請展開 [R 安裝設定]  以顯示安裝選項，或選取您想要用來執行 R 指令碼的安裝是哪一個。
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   如果 R 已安裝但無法識別，則您可以在展開 [R 安裝設定]  提供的文字方塊中明確輸入其位置。 在上圖中，已在文字方塊中明確輸入路徑 *C:\Program Files\R\R-3.2.0* 。
   
   R 安裝設定集中位於 [選項] 對話方塊的 R 指令碼區段。 若要指定 R 安裝設定，請選取 [檔案] > [選項和設定]  ，然後選取 [選項] > [R 指令碼]  。 如果有多個 R 安裝程式，則會顯示下拉式功能表，讓您選取要使用的安裝程式。
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. 選取 [確定]  來執行 R 指令碼。 當指令碼順利執行時，您可以選擇要加入 Power BI 模型之產生的資料框架。

### <a name="refresh"></a>重新整理
您可以在 Power BI Desktop 中重新整理 R 指令碼。 當您重新整理的 R 指令碼時，Power BI Desktop 會在 Power BI Desktop 環境中再次執行 R 指令碼。

## <a name="next-steps"></a>後續步驟
請看看下列有關 Power BI 中 R 的其他資訊。

* [在 Power BI Desktop 中建立 R 視覺效果](desktop-r-visuals.md)
* [在 Power BI 使用外部 R IDE](desktop-r-ide.md)

