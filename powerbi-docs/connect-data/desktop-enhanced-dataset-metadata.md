---
title: 使用 Power BI Desktop (預覽) 中的增強型資料集中繼資料
description: 本文描述如何使用 Power BI 中的增強型資料集中繼資料。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 389de5d34b00afbe70a1489dfc61e760530590a9
ms.sourcegitcommit: 642b0c04d3ff3aa4d5422ca5054a5a158fb01b22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88512877"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>使用增強型資料集中繼資料 (預覽)

當 Power BI Desktop 建立報表時，也會在對應的 PBIX 和 PBIT 檔案中建立資料集中繼資料。 之前中繼資料是儲存在 Power BI Desktop 特定的格式中。 其先前使用了 Base 64 編碼 M 運算式及資料來源，並假設了儲存中繼資料的方式。

隨著**增強型資料集中繼資料**功能的發行，我們克服了許多其中的限制。 啟用**增強型資料集中繼資料**功能，由 Power BI Desktop 所建立中繼資料即會使用與用於 Analysis Services 表格式模型格式相似的格式，以[表格式物件模型](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)為基礎。


**增強型資料集中繼資料**功能是一種策略性及基礎功能，因為未來的 Power BI 功能都會以這項中繼資料為基礎建置。 其中一部分可獲益於增強型資料集中繼資料的額外功能，包括 Power BI 資料集管理的 [XMLA 讀取/寫入](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)，以及將 Analysis Services 工作負載移轉至 Power BI，使其獲益於下一代的功能。



## <a name="enable-enhanced-dataset-metadata"></a>啟用增強型資料集中繼資料

**增強型資料集中繼資料**功能目前處於預覽階段。 若要啟用增強型資料集中繼資料，請在 Power BI Desktop 中選取 [檔案] > [選項和設定] > [選項] > [預覽功能]，然後選取 [Store datasets using enhanced metadata format] \(使用增強型中繼資料格式儲存資料集\) 核取方塊，如下圖所示。 

![啟用預覽功能](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

您可能會收到提示，要求重新啟動 Power BI Desktop。

![重新啟動提示](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

啟用預覽功能後，Power BI Desktop 即會嘗試升級使用先前中繼資料格式的 PBIX 和 PBIT 檔案。 

> [!IMPORTANT]
> 啟用**增強的資料集中繼資料**功能，會導致無法復原的報表升級。 一旦啟用**增強的資料集中繼資料**，任何使用 Power BI Desktop 載入或建立的 Power BI 報表，都將無法逆轉為增強的資料集中繼資料格式。

## <a name="report-backup-files"></a>報表備份檔案

更新報表以使用**增強型資料集中繼資料**功能無法復原。 然而，更新期間會建立報表的備份檔案，儲存原始 (更新前) 格式版的報表。 備份檔案會在 30 天後移除。 

若要找出備份報表檔案，請執行下列動作：

1. 巡覽至下列位置：```C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\TempSaves\Backup```。 若使用 Microsoft Store 版本的 Power BI Desktop，請使用下列位置：```C:\Users\<user>\Microsoft\Power BI Desktop Store App\TempSaves\Backups``` 

2. 以原始檔案的名稱和時間戳記來尋找報表複本。

3. 將檔案複製到偏好的位置，以便保留。

4. 如果選擇開啟或使用該原始檔案，請確定 Power BI Desktop 中的 [Enhanced metadata format] \(增強型中繼資料格式\) 預覽功能已停用。 

備份檔案會在升級報表時建立，因此不會包含升級之後所做的任何變更。 啟用 [Enhanced metadata format] \(增強型中繼資料格式\) 功能時所建立的新報表沒有備份檔案。


## <a name="considerations-and-limitations"></a>考量與限制

在預覽版本中，當啟用預覽功能時即適用下列限制。

### <a name="unsupported-features-and-connectors"></a>不支援的功能和連接器

適用下列限制：

在開啟尚未升級的現有 PBIX 和 PBIT 檔案時，若資料集包含任何下列功能或連接器，升級將會失敗。 若發生這類錯誤，應不會對使用者體驗造成立即的影響，且 Power BI Desktop 會繼續使用先前的中繼資料格式。

* 所有自訂連接器 (2020 年 5 月版本限制)
* Python 指令碼
* Azure DevOps Server
* BI 連接器
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* 包含特定字元組合的 (例如在資料行名稱中包含 “\\n”) M 運算式
* 在啟用**增強型資料集中繼資料**功能並使用資料集時，無法在 Power BI 服務中設定單一登入 (SSO) 資料來源

如果您使用的是 **2020 年 6 月**版本的 Power BI Desktop (或更新版本)，則 Power BI Desktop 和 Power BI 服務支援所有自訂連接器和所有內建連接器。 在使用 2020 年 6 月版本或更新版本時的發佈程序期間，如果閘道遇到問題，則資料集將會成功發佈，但使用者必須重新發佈報表，才能重新整理資料。 [資料來源設定] 對話方塊是發佈程序發生問題的唯一指標。

若報表使用不支援的連接器或功能，則其將不會升級為新格式。 已經升級或在啟用這項新功能之後所建立的報表，將不支援新增所列出不支援的功能或連接器。 

不支援具有動態資料來源的查詢。 具有動態資料來源的報表將不會升級為新格式，且已升級或新建立的報表若已啟用功能，將不支援新增動態資料來源。 如果來源根據參數、函式輸入或動態函式而變更，則查詢具有動態資料來源。 

不支援上游步驟或分支中發生錯誤的查詢。 

此外，已經成功升級為使用**增強型資料集中繼資料**的 PBIX 和 PBIT 檔案「無法」使用上述功能 (或任何不支援的連接器)。

### <a name="lineage-view"></a>譜系檢視
使用新中繼資料格式的資料集目前不會在 Power BI 服務內譜系檢視中顯示資料流程的連結。

## <a name="next-steps"></a>後續步驟

您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 的新功能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop 的查詢概觀](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的資料類型](desktop-data-types.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常見查詢工作](../transform-model/desktop-common-query-tasks.md)
