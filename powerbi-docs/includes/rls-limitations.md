## <a name="limitations"></a>限制
以下是雲端模型的資料列層級安全性目前限制清單。

* 如果先前已在 Power BI 服務中定義了角色與規則，就必須在 Power BI Desktop 中重新加以建立。
* 您只能在使用 Power BI Desktop 用戶端建立的資料集上定義 RLS。 如果您想要針對使用 Excel 建立的資料集啟用 RLS，則必須先將檔案轉換成 PBIX 檔案。 [深入了解](../desktop-import-excel-workbooks.md)
* 只支援 ETL 和 DirectQuery 連線。 Analysis Services 即時連接是在內部部署模型中處理。
* RLS 目前不支援問與答及 Cortana。 如果所有模型都已設定 RLS，您將不會看到儀表板的 [問與答] 輸入方塊。 這已在規劃中，但未建立時間軸。
* 使用 RLS 的資料集目前不支援外部共用。
* 對於任何給定的模型，可以指派給安全性角色的 Azure AD 主體 (也就是個別使用者或安全性群組) 的最大數目是 1,000。 若要將大量使用者指派給角色，請務必指派安全性群組，而不是個別使用者。

## <a name="known-issues"></a>已知問題
已知問題：如果嘗試從 Power BI Desktop 發行已發行過的內容，會產生錯誤訊息。 案例如下。

1. Anna 有個發佈到 Power BI 服務的資料集，並已設定 RLS。
2. Anna 更新了 Power BI Desktop 中的報表，然後重新發行。
3. Anna 收到錯誤。

**因應措施︰** 從 Power BI 服務重新發行 Power BI Desktop 檔案，直到此問題解決為止。 您可以選取 [取得資料] > [檔案] 以執行此動作。 

