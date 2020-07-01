---
title: 在 Excel 中存取 Power BI 的精選表格 (預覽)
description: 在 Excel 中，可在資料類型資源庫的 Power BI 資料集中，從精選表格中尋找資料。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226364"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>在 Excel 中存取 Power BI 的精選表格 (預覽)

在 Excel 中，可在資料類型資源庫的 Power BI 資料集中，從精選表格中尋找資料。 精選表格可供更輕鬆地將企業資料新增至 Excel 工作表。 使用 Power BI 已認證和升級的資料集功能，組織可讓更多使用者尋找並使用相關和可重新整理的資料，以做出更佳的決策。 若要深入了解如何使用 [Power BI 中的 Excel 資料類型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) (英文)，請參閱 Excel 文件。

資料類型資源庫只會顯示建模者已在 Power BI 資料集中策劃的精選表格。 您也可以在 Excel 中瀏覽任何可在 Power BI 中存取的資料集。 在 Excel 中，選取 [資料] 功能區上 [取得資料] 下的 [Power BI 資料集] 選項。

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>透過 Excel 資料類型資源庫存取 Power BI 資料
Power BI 資料集中精選表格會出現在 [資料] 功能區的 Excel 資料類型資源庫中。

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel [資料] 功能區":::

展開後，資源庫會顯示前幾種可用的資料類型。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel 資料類型資源庫":::
 
若要查閱 Power BI 精選表格中的資料，請選取 Excel 工作表中的儲存格或範圍。

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="選取儲存格":::
 
從資源庫中選取 [組織資料] 選項，以在您有權存取的認證資料集精選表格中搜尋資料。

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Excel [組織資料]":::
 
如果知道要搜尋的資料種類，或使用 [組織資料] 選項找不到相符資料列時，請選取特定的資料類型。

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="選取資料類型":::
 
搜尋時，如果找到具有高信賴度的相符資料列，儲存格就會立即連結至該資料列。 已連結項目圖示表示儲存格已連結至 Power BI 的資料列。

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="連結的項目圖示":::

如果儲存格有多個可能的相符資料列，即會顯示 [資料選取器] 窗格。 儲存格會顯示問號圖示，這可開啟該資料列的 [資料選取器] 窗格。 以下是使用者選取範圍 A2:A7 並搜尋 Power BI 精選表格之後的範例。

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="多個可能的相符資料列":::

[資料選取器] 窗格會顯示可能符合的資料列。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Excel [資料選取器] 窗格":::
 
[組織資料] 選項可傳回多種資料類型的資料列。 Excel 會依照來源的資料類型，分組可能符合的資料列。 Excel 會根據最有可能的相符資料列來排序資料類型。 使用＞形箭號來折疊及展開相符資料列的資料類型。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Excel [資料選取器] 窗格":::
 
為每個資料列選取資料列名稱來查看資料列內的詳細資料，以協助挑選正確的資料列。 找到資料列之後，請按 [選取] 來連結資料列和 Excel 的資料格。 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="[資料選取器] 詳細資料":::
 
選取資料列時，儲存格會連結至資料列，且其值為 Power BI 精選表格中的 [資料列標籤] 欄位值。 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Excel 已連結項目":::
 
選取**連結的儲存格**圖示會顯示一張卡片，其包含精選表格中所有欄位和計算欄位的資料。 卡片標題會顯示精選表格中 [資料列標籤] 欄位的值。
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="已連結項目詳細資料":::

選取**插入資料**圖示，將欄位值新增至方格中。

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="插入資料"::: 

從欄位清單中選取欄位名稱，將其值新增至方格中。  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="選取欄位名稱":::

欄位值放在相鄰儲存格中。 儲存格公式會參考所連結的儲存格及欄位名稱，因此可使用 Excel 函式中的資料。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel 儲存格公式":::
 
當將資料格式化為 Excel 資料表時，新增欄位會展開資料表，並設定資料行標題以符合欄位名稱。 連結至相同資料類型的資料列也會填入其個別值。

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="欄位是資料行名稱"::: 

## <a name="cell-formulas"></a>儲存格公式

當使用 Excel 資料表時，可參考所連結的資料表資料行，然後使用 `.` (句號) 參考來新增資料欄位。

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel 句號參考":::

同樣地，當使用儲存格時，可參考儲存格，並使用 `.` (句號) 參考來擷取欄位。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="儲存格句號參考":::
 
## <a name="data-caching-and-refresh"></a>資料快取和重新整理

當 Excel 將儲存格連結至 Power BI 精選表格中資料列時，即會擷取並儲存該 Excel 檔案中所有欄位的值。 與您共用檔案的所有人都可參考任一欄位，而不必向 Power BI 要求資料。  

使用 [資料] 功能區中的 [全部重新整理] 按鈕，以重新整理已連結儲存格中的資料。 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="全部重新整理":::
 
您也可以重新整理個別的儲存格。 以滑鼠右鍵按一下儲存格，然後選取 [資料類型] > [重新整理]。

## <a name="show-a-card-change-or-convert-to-text"></a>顯示卡片、變更或轉換為文字

連結的儲存格已新增快顯功能表選項。 以滑鼠右鍵按一下儲存格 > 選取 [資料類型] >  

- [顯示卡片]
- **重新整理**
- **變更** 
- [轉換為文字]。

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="以滑鼠右鍵按一下 [轉換為文字]":::
 
[轉換為文字] 會移除 Power BI 精選表格的資料列連結。 重要的是，儲存格中文字會是已連結儲存格的資料列標籤值。 如果將儲存格連結到不想連結的資料列，請在 Excel 中選取 [復原] 以還原初始的儲存格值。

## <a name="licensing"></a>授權
Excel 資料類型資源庫和 Power BI 精選表格的連線體驗僅供 Excel E5 和 G5 客戶使用。 

## <a name="security"></a>安全性

您在 Power BI 中只會看到有權存取資料集的精選表格。 重新整理資料時，您必須有權存取 Power BI 的資料集，才能擷取資料列。 這需要有資料集的建置或寫入權限。 Excel 會快取傳回的整列資料。 與您共用 Excel 檔案的所有人，都可以看到所有已連結儲存格中所有欄位的資料。

如果 Power BI 資料集已套用資料列層級安全性或 Microsoft 資訊保護的敏感度標籤，則 Excel 資料類型資源庫不會包含該資料集的精選表格。 這是初始預覽的限制。

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>在 Power BI Desktop 中策劃精選表格
Excel 資料類型資源庫會在上傳至 Power BI 服務的資料集中顯示精選表格。 使用 Power BI Desktop 在資料模型中策劃精選表格，然後上傳至 Power BI 服務。

### <a name="turn-on-the-featured-table-preview"></a>開啟精選表格預覽

1. 在 Power BI Desktop 中，選取 [檔案] > [選項及設定] > [選項] > [預覽功能]。
2. 選取 [Featured tables] \(精選表格\) 核取方塊。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="預覽 [Featured tables] \(精選表格\) 選項":::

### <a name="select-a-table"></a>選取資料表

1. 在 Power BI Desktop 中，移至 [模型] 檢視。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="[模型] 檢視":::
 
2. 選取資料表，然後將 [Is featured table] \(是否為精選表格\) 設為 [是]。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="將 [Is featured table] \(是否為精選表格\) 設為 [是]":::

4. 在 [Set up this featured table] \(設定此精選表格\) 中提供必要欄位：

    - [描述]。
    - Excel 會使用 [資料列標籤] 欄位值，所以使用者可輕鬆識別資料列。 其會顯示為已連結儲存格的資料格值，位於 [資料選取器] 窗格和 [資訊] 卡片中。 
    - [索引鍵資料行] 欄位值會提供資料列的唯一識別碼。 這個值可讓 Excel 將儲存格連結到資料表中的特定資料列。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="設定精選表格":::

在將資料集發佈至或匯入 Power BI 服務後，Excel 資料類型資源庫即會顯示精選表格。

- Excel 會快取資料類型的清單，所以必須重新啟動 Excel，才能看到新發佈的精選表格。
- 有些資料集不支援預覽功能，所以 Excel 不會顯示在這些資料集所定義的精選表格中。 如需詳細資訊，請參閱＜考量與限制＞。

## <a name="administrative-control"></a>系統管理控制

Power BI 系統管理員可管控組織中哪些人可使用 Excel 資料類型資源庫中的精選表格。 如需詳細資料，請參閱＜系統管理入口網站＞一文中的 [精選表格設定](../admin/service-admin-portal.md#featured-tables-settings)。 
 
### <a name="auditing"></a>稽核

管理稽核記錄檔會顯示精選表格的下列事件：

- **AnalyzedByExternalApplication**：讓系統管理員看到哪些使用者正在存取哪些精選表格。
- **UpdateFeaturedTables**：讓系統管理員看到哪些使用者正在發佈與更新精選表格。

如需稽核記錄事件的完整清單，請參閱[追蹤 Power BI 中的使用者活動](../admin/service-admin-auditing.md)。

## <a name="considerations-and-limitations"></a>考量與限制

以下是初始預覽的限制：

- 僅 Excel 測試人員版本提供此整合。
- Excel 資料類型資源庫包含可供具有 Power BI Desktop 和 Power BI 服務適當授權使用者使用的精選表格。 預覽版本可能不支援 Power BI 服務，但日後會新增。
- Excel 不會顯示使用下列功能的 Power BI 資料集精選表格： 

    - 資料列層級安全性資料集。
    - 啟用 Microsoft 資訊保護的資料集。
    - DirectQuery 資料集。
    - 具有即時連線的資料集。

- Excel 只會顯示精選表格資料行和計算結果欄中的資料。 初始預覽不提供下列內容：

    - 精選表格上定義的量值。
    - 相關資料表上定義的量值，以及從關聯性計算的隱含量值。

- Excel 只會顯示儲存在新 Power BI 工作區中的精選表格。 儲存在傳統工作區或 [我的工作區] 中的精選表格不會顯示為 Excel 資料類型。 您可在 Power BI 中[將傳統工作區升級為新工作區](service-upgrade-workspaces.md)。

Excel 中的資料類型體驗類似 lookup 函式。 其會接受 Excel 工作表提供的儲存格值，並會在 Power BI 精選表格中搜尋相符的資料列。 搜尋體驗具有下列行為：

- 使用 [組織資料] 按鈕來搜尋時，Excel 只會搜尋已認證資料集中的精選表格。
- 資料列比對是以精選表格中的文字資料行為基礎。 使用與 Power BI Q&A 功能相同的索引，其已最佳化英文搜尋。 以其他語言搜尋可能不會產生正確的相符項目。 比對時不考慮數值資料行。
- 個別搜尋字詞的比對是以完全相符和前置詞相符為基礎。 儲存格值的分割依據為空格或其他空白字元，例如定位點。 然後，每個單字都視為搜尋字詞。 資料列的文字欄位值會和每個搜尋字詞進行完全相符和前置詞相符比較。 如果資料列的文字欄位以搜尋字詞開頭，則會傳回前置詞相符。 例如，如果儲存格包含 “Orange County”，則 “Orange” 和 “County” 會視為不同的搜尋字詞。 

    - 傳回文字資料行值完全符合 “Orange” 或 “County” 的資料列。 
    - 傳回文字資料行值以 “Orange” 或 “County” 開頭的資料列。 
    - 重要的是，不會傳回包含 “Orange” 或 “County” 但其不為開頭的資料列。

- Power BI 為每個儲存格最多傳回 100 項資料列建議。
- XMLA 端點不支援設定或更新精選表格
- 具有資料模型的 Excel 檔案可用來發佈精選表格。 將資料載入至 Power BI 桌面，然後發佈精選表格。
- 變更精選表格的 [資料表名稱]、[資料列標籤] 或 [索引鍵資料行]，會影響儲存格連結到資料表資料列的 Excel 使用者。 
- Excel 會顯示從 Power BI 資料集擷取資料的時間。 這不一定是資料在 Power BI 中重新整理的時間，或資料集的最新資料點時間。 例如，假設 Power BI 的資料集在一週前重新整理過，而基礎來源資料在重新整理發生時已存在一週。 所以實際的資料時間是 2 週，但 Excel 所顯示資料擷取日期/時間會是在 Excel 中提取資料的日期/時間。

## <a name="next-steps"></a>後續步驟

- 有問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)

