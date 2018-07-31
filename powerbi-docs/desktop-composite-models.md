---
title: 使用 Power BI Desktop 中的複合模型 (預覽)
description: 在 Power BI Desktop 中透過多個資料連線與多對多關聯性來建立資料模型
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/23/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 4f882865271411d04a99c9213a68df24d000677d
ms.sourcegitcommit: 6faeb642721ee5abb41c04a8b729880c01c4d40e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39210669"
---
# <a name="composite-models-in-power-bi-desktop-preview"></a>Power BI Desktop 中的複合模型 (預覽)

先前在 **Power BI Desktop** 中，當您在報表中使用 DirectQuery 時，該報表都不允許其他 DirectQuery 或「匯入」資料連線。 **複合模型**可以移除該限制，讓報表能以各種組合，完美地包含來自多個 DirectQuery 或匯入資料連線的資料連線。

![Power BI Desktop 中的複合模型](media/desktop-composite-models/composite-models_01.png)

**Power BI Desktop** 中的**複合模型**功能包含三種相關功能：

* **複合模型**：讓報表能夠具有任意組合的多個資料連線，包括 DirectQuery 連線或匯入。
* **多對多關聯性**：您可以透過**複合模型**，在資料表之間建立**多對多關聯性**、移除資料表中對於唯一值的需求，以及移除先前的因應措施，例如，只為建立關聯性而導入新的資料表。 
* **儲存模式**：您現在可以指定需要查詢後端資料來源的視覺效果，並匯入不需要查詢後端資料來源的視覺效果 (即使是以 DirectQuery 為基礎的視覺效果也一樣)，以提升效能並減少後端負載。 以往，即使像是交叉分析篩選器之類的簡單視覺效果，也會起始要傳送到後端來源的查詢。 

有關**複合模型**三個相關功能的集合，分別會在個別文章中加以說明：

* 本文將詳細說明**複合模型**。
* **多對多關聯性**會在它們自己的文章 [Power BI Desktop 中的多對多關聯性 (預覽)](desktop-many-to-many-relationships.md) 中加以說明。
* **儲存模式**會在它自己的文章 [Power BI Desktop (預覽) 中的儲存模式](desktop-storage-mode.md)中加以說明。

## <a name="enabling-the-composite-models-preview-feature"></a>啟用複合模型預覽功能

**複合模型**功能處於預覽狀態，且必須在 **Power BI Desktop** 中加以啟用。 若要啟用**複合模型**，請選取 [檔案] > [選項及設定] > [選項] > [預覽功能]，然後選取 [複合模型] 核取方塊。 

![正在啟用預覽功能](media/desktop-composite-models/composite-models_02.png)

您必須重新啟動 **Power BI Desktop**，功能才會啟用。

![需要重新啟動，才能使變更生效](media/desktop-composite-models/composite-models_03.png)


## <a name="using-composite-models"></a>使用複合模型

您可以藉由**複合模型**，在使用 **Power BI Desktop** 或 **Power BI 服務**時連線到各種不同的資料來源，而且可以利用不同的方法來進行這些資料連線。 您可以將資料匯入 Power BI (這是取得資料的最常見方法)，也可以使用 DirectQuery 直接連線到原始來源存放庫中的資料。 您可以在[使用 Power BI 中的 DirectQuery](desktop-directquery-about.md) 一文中深入了解 DirectQuery 的詳細資料。

當使用 DirectQuery 時，透過**複合模型**能建立可執行下列作業的 Power BI 模型 (例如，單一 .pbix Power BI Desktop 檔案)：

* 結合來自一或多個 DirectQuery 來源的資料，和/或
* 結合來自 DirectQuery 來源的資料與匯入資料

例如，使用**複合模型**時，建立的模型就可以結合來自企業資料倉儲的銷售資料、部門 SQL Server 資料庫中的銷售目標相關資料，以及從試算表匯入的一些資料。 結合多個 DirectQuery 來源的資料或結合 DirectQuery 與所匯入資料的模型，就稱為*複合模型*。

> [!NOTE]
> 在複合模型處於預覽狀態時，無法將複合模型發行至 Power BI 服務。 

您能如往常一般，建立資料表之間的關聯性 (即使這些資料表來自不同的來源)，但有下列限制：不論實際基數為何，跨來源的關聯性都必須定義為有**多對多**基數。 這類關聯性的行為之後會和正常的**多對多**關聯性一樣，如 [Power BI Desktop 中的多對多關聯性 (預覽)](desktop-many-to-many-relationships.md) 中所述。 請注意，在複合模型內容中，所有匯入的資料表便有如單一來源，不論實際匯入的實際基礎資料來源為何。   

## <a name="example-of-using-composite-models"></a>使用複合模型範例

以**複合模型**的範例來說，假設報表使用 DirectQuery 連線到公司資料倉儲 (在 SQL Server 中)，該資料倉儲包含「依國家/地區顯示銷售額」、「季」及「腳踏車 (產品)」的資料，如下圖所示。

![複合模型的關聯性檢視](media/desktop-composite-models/composite-models_04.png)

此時，您可以使用此來源中的欄位，以建置簡單的視覺效果。 例如，下列視覺效果會依 *ProductName* 顯示所選季度的總銷售量。 

![根據資料的視覺效果](media/desktop-composite-models/composite-models_05.png)

但是，假設您對各項產品的「產品經理」擁有某些資訊，還有資料位於 Excel 試算表的行銷策略，那該怎麼做？ 您可能想要依「產品經理」來查看「銷售額」，但要將這項本機資料加入公司資料倉儲可能並不可行，或至少要花費數個月的時間。 雖然可能從資料倉儲匯入該銷售資料 (而不是使用 DirectQuery)，再與從試算表匯入的資料結合，但該方法並不合理，理由包括會結合基礎來源中強制執行的安全性規則、能夠查看最新資料的需求，以及資料的龐大規模等等，因此一開始就該使用 DirectQuery。 

這就是**複合模型**派上用場的地方。 複合模型可讓您選擇使用 DirectQuery 連線到資料倉儲，然後也可對其他來源使用 GetData。 在這種情況下，我們會對公司資料倉儲建立 DirectQuery 連線，然後使用 GetData 並選擇 Excel、瀏覽至包含本機資料的試算表，並匯入包含 *ProductNames*、所指派 *SalesManager* 及 *Priority* 的工作表。  

![[導覽器] 視窗](media/desktop-composite-models/composite-models_06.png)

現在，我們可在 [欄位] 清單中看到原始「腳踏車」資料表 (來自 SQL Server) 與新的「產品經理」 資料表 (含有從 Excel 匯入的資料)。 

![資料表的欄位檢視](media/desktop-composite-models/composite-models_07.png)

同樣地，在 **Power BI Desktop** 的 [關聯性檢視] 中，現在可看到稱為「產品經理」的額外資料表。 

![資料表的關聯性檢視](media/desktop-composite-models/composite-models_08.png)

我們現在需要如往常一般，將這些資料表與模型中的其他資料表建立關聯，方法是在「腳踏車」資料表 (在 SQL Server 中) 與「產品經理」資料表 (匯入) 之間建立關聯性，例如在 *Bike[ProductName]* 與 *ProductManagers[ProductName]* 之間。 如本文稍早所述，跨來源的所有關聯性都必須要有**多對多**基數，因此也是選取的預設基數。 

![建立關聯性對話方塊](media/desktop-composite-models/composite-models_09.png)

建立此關聯性之後，就會如我們所預期，在 **Power BI Desktop** 的 [關聯性檢視] 中顯示該關聯性。

![新的關聯性檢視](media/desktop-composite-models/composite-models_10.png)

建立這些資料表關聯性後，我們現在可使用 [欄位] 清單中的任何欄位來建立視覺效果，完美地混合多個來源的資料。 例如，下面的視覺效果顯示每個「產品經理」的「銷售額」總計。 

![顯示視覺效果與 [欄位] 窗格](media/desktop-composite-models/composite-models_11.png)

此範例顯示利用從他處匯入的一些額外資料來擴充「維度」資料表 (例如「產品」或「客戶」) 的常見情況，也可以讓資料表使用 DirectQuery 連線到不同來源。 為了擴充我們的範例，假設每個 *Country* 與 *Period* 的 *SalesTargets* 都儲存在個別的部門資料庫中。 您可以照常使用 **GetData** 連線到該資料，如下圖所示。 

![導覽器對話方塊](media/desktop-composite-models/composite-models_12.png)

接著，和我們稍早在此範例中所執行的動作類似，可在新的資料表與模型中的其他資料表之間建立關聯性，然後建立可結合兩方資料的視覺效果。 讓我們再次查看 [關聯性檢視]，我們已在此於擴充範例案例中建立了新的關聯性。

![含有許多資料表的關聯性檢視](media/desktop-composite-models/composite-models_13.png)

如下圖根據新資料與剛建立的關聯性所示，左下角的視覺效果顯示「銷售額」總計與「目標」，還有變異數計算顯示來自兩個不同 SQL Server 資料庫的「銷售額」與「目標」差異。 

![顯示更多資料的視覺效果](media/desktop-composite-models/composite-models_14.png)

## <a name="setting-storage-mode"></a>設定儲存模式

**複合模型**中的每個資料表都有**儲存模式**，指出該資料表示以 DirectQuery 或匯入為根據。 **儲存模式**可在 [屬性] 窗格中檢視和修改。 若要前往該處，請在操作功能表的 [欄位] 清單上按一下滑鼠右鍵，選取 [屬性] 即可。 下圖顯示**儲存模式** (因為窗格寬度，導致在圖中縮短為 [儲存...])。

![儲存模式設定](media/desktop-composite-models/composite-models_15.png)

每個資料表的工具提示上也可看到**儲存模式**。

![含有儲存模式的工具提示](media/desktop-composite-models/composite-models_16.png)

對於包含來自 DirectQuery 的一些資料表與一些匯入資料表的任何 **Power BI Desktop** 檔案 ( .pbix 檔案)，狀態列顯示的**儲存模式**為 [混合]。 您可以按一下狀態列中的該字詞，然後將所有資料表輕鬆地切換為匯入。

**儲存模式**的詳細資料會在 [Power BI Desktop 中的儲存模式 (預覽)](desktop-storage-mode.md) 一文中完整說明。  

## <a name="calculated-tables"></a>計算資料表

計算資料表可加入使用 DirectQuery 的模型中，而定義計算資料表的 DAX 可參考匯入的或 DirectQuery 資料表，或這兩者的組合。 

計算資料表一律為匯入，而且會在重新整理資料表時，重新整理這些資料表中的資料。 同樣地，如果計算資料表參考 DirectQuery 資料表，則參考 DirectQuery 資料表的視覺效果一律會顯示基礎來源中最新的值，但參考計算資料表的視覺效果會顯示計算資料表上次重新整理時的值。

## <a name="security-implications"></a>安全性影響 

複合模型對安全性會有一些影響。 傳送至某個資料來源的查詢，可能包含從其他不同來源所擷取的資料值。 如本文稍早所述的範例，依「產品經理」顯示「銷售額」的視覺效果會導致將 SQL 查詢傳送至**銷售**關聯式資料庫，而該 SQL 查詢可能包含「產品經理」與其相關聯「產品」的名稱。 

![顯示安全性影響的指令碼](media/desktop-composite-models/composite-models_17.png)

因此，傳送至關聯式資料庫的查詢現在會包含試算表中儲存的資訊。 如果這是機密資訊，則應考慮這樣做的安全性影響。 您應該特別考慮下列影響：

* 任何可查看追蹤或稽核記錄的資料庫管理員，即使在原始來源中沒有該資料的權限 (在本案例中為 Excel 檔案的權限)，也都能查看這項資訊。

* 應要考慮每個來源的加密設定，避免將使用加密連線從某一來源擷取的資訊，之後不小心包含在使用未加密連線傳送至其他來源的查詢中。 

採取建立複合模型的動作時，**Power BI Desktop** 會顯示一則警告訊息，確認您已經考慮過所有安全性影響。  

基於類似原因，當開啟從不受信任來源所傳送的 **Power BI Desktop** 檔案時，請務必格外小心。 如果該檔案包含複合模型，這表示從某一來源擷取的資訊 (利用開啟該檔案使用者的認證)，可能會成為查詢的一部分而傳送到其他資料來源 (惡意的 Power BI Desktop 檔案作者可能會看見)。 因此，當第一次開啟 Power BI Desktop 檔案時，如果當中包含多個來源，就會顯示警告。 此警告和開啟的檔案包含原生 SQL 查詢時所顯示的警告類似。  

## <a name="performance-implications"></a>效能影響  

當使用 DirectQuery 時，應該一律考量效能，主要是為了確保後端來源會有充足的資源，以便為使用者提供良好的體驗。 良好的體驗表示應可在 5 秒內重新整理視覺效果。 您也應該遵守[使用 Power BI 中的 DirectQuery](desktop-directquery-about.md) 一文中的效能建議。 使用複合模型會增加額外的效能考量，因為單一視覺效果可能導致將查詢傳送到多個來源，而經常將某個查詢的結果傳遞至第二個來源。 這種情況會導致下列可能的執行形式：

* **SQL 查詢包含大量常值**：例如，要求一組所選擇「產品經理」(來自從試算表匯入的相關資料表) 的「銷售額」總計 (來自 SQL 資料庫) 視覺效果時，必須先找到產品經理所管理的「產品」，然後再傳送 *WHERE* 子句中包含所有產品識別碼的 SQL 查詢。

* **SQL 查詢會藉由較低的細微度層級來查詢，然後在本機彙總資料**：使用的範例和本清單中前一個項目符號相同，由於符合「產品經理」篩選條件的「產品」數目非常龐大，全部包含在 *WHERE* 子句中變得沒有效率或不可行。 相反地，有必要以較低的「產品」層級來查詢關聯式來源，然後在本機彙總結果。 如果「產品」的基數超過 1 百萬的上限，查詢就會失敗。

* **依值分組，每個群組一個的多個 SQL 查詢**：當彙總使用的 **DistinctCount** 是依據另一來源的某資料行來分組時，如果外部來源不支援有效傳遞定義群組的許多常值，就有必要依值分組，每個群組傳送一個 SQL 查詢。 例如，視覺效果要依「產品經理」(來自從試算表匯入的相關資料表) 要求 *CustomerAccountNumber* (來自 SQL Server 資料表) 的相異計數，就需要在傳送至 SQL Server 的查詢中傳遞來自「產品經理」資料表的詳細資料。 針對其他來源 (例如 Redshift)，這並不可行，而是改為每個「銷售經理」傳送一個 SQL 查詢 (最多以實際限制為限，超過就會查詢失敗)。 

上述每一種情況對於效能各有其影響，確切的細節也會隨每個資料來源而異。 根據經驗，在聯結兩個來源的關聯性中，最好維持使用低資料行基數 (數千個)，那麼效能應不會受太大影響。 這個基數越高，就越需要考量對最終效能的影響。 

此外，使用**多對多**關聯性時，表示必須針對每個總計/小計層級，將個別查詢傳送至基礎來源，而不是在本機彙總詳細的值。 因此，一個包含總計的簡單資料表視覺效果會傳送兩個 SQL 查詢，而不是一個。 

## <a name="limitations-and-considerations"></a>限制與考量

這一版的**複合模型**有一些限制。

下列多維度來源不能與**複合模型**搭配使用：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 資料集

使用 DirectQuery 連線到這些多維度來源時，將無法同時連線到其他 DirectQuery 來源，也無法結合匯入的資料。

使用**複合模型**時，仍然受限於 DirectQuery 的現有使用限制。 這其中有許多限制現在會依個別資料表的**儲存模式**而異。 例如，已匯入資料表上的計算結果欄可以參考其他資料表，但 DirectQuery 資料表上的計算結果欄仍僅限於參考相同資料表上的資料行。 如果模型內有任何資料表為 DirectQuery，則其他限制會套用至整個模型。 例如，如果某個模型內的任何資料表具有 DirectQuery 的**儲存模式**，則該模型不提供 **QuickInsights** 和**問與答**功能。 

## <a name="next-steps"></a>後續步驟

下列文章會詳細說明複合模型與 DirectQuery。

* [Power BI Desktop 中的多對多關聯性 (預覽)](desktop-many-to-many-relationships.md)
* [Power BI Desktop 中的儲存模式 (預覽)](desktop-storage-mode.md)

DirectQuery 文章：

* [使用 Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)

