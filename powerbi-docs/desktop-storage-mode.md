---
title: 使用 Power BI Desktop 中的儲存模式
description: 使用儲存模式控制是否要在 Power BI Desktop 中，將報表資料快取到記憶體內
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7b2d3975ba6bcea7b1294c1432f9278908a33ea4
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760012"
---
# <a name="manage-storage-mode-in-power-bi-desktop"></a>管理 Power BI Desktop 中的儲存模式

在 Microsoft Power BI Desktop 中，您可以指定資料表的儲存模式  。 儲存模式  可讓您控制 Power BI Desktop 是否要將報表資料快取到記憶體內。 

![Power BI Desktop 中的儲存模式](media/desktop-storage-mode/storage-mode-01.png)

設定儲存模式有許多好處。 您可以個別為模型中的每個資料表設定儲存模式。 此動作會啟用單一資料集，而且具有下列優點：

* **查詢效能**：當使用者與 Power BI 報表中的視覺效果互動時，會將資料分析運算式 (DAX) 查詢提交至資料集。 適當地設定儲存模式，將資料快取到記憶體，可以大幅提升報表的查詢效能及互動效果。

* **大型資料集**：未快取的資料表不會因為快取的用途而耗用記憶體。 針對太大或太過昂貴而無法完全快取到記憶體的大型資料集，您可以啟用互動式分析。 您可以選擇值得與不值得快取的資料表。

* **資料重新整理最佳化**：沒有快取的資料表不需要重新整理。 您可以只快取符合您服務等級協定及商務需求的資料，從而減少重新整理的時間。

* **近乎即時的需求**：有近乎即時需求的資料表可能適合不快取，這樣能減少資料延遲。

* **回寫**：回寫允許商務使用者變更資料格的值來探索假設狀況。 自訂應用程式可以將變更套用到資料來源。 未快取的資料表可以立即顯示變更，達到即時分析的效果。

Power BI Desktop 中的儲存模式設定是三個相關功能之一：

* **複合模型**：允許報表可有兩 (含) 個以上任意組合的資料連線，包括 DirectQuery 連線或匯入。 如需詳細資訊，請參閱 [Power BI Desktop 的複合模型](desktop-composite-models.md)。

* **多對多關聯性**：您可以使用「複合模型」  在資料表之間建立「多對多關聯性」  。 多對多關聯性  會移除資料表中值必須唯一的要求。 此外也會移除先前的因應措施，像是只為了建立關聯性而導入新的資料表。 如需詳細資訊，請參閱 [Power BI Desktop 中的多對多關聯性](desktop-many-to-many-relationships.md)。

* **儲存模式**：您現在可以指定哪些視覺效果必須查詢後端資料來源。 不需要查詢的視覺效果，即便是使用 DirectQuery，也同樣會匯入。 此功能可提升效能，並減輕後端的負載。 先前即使是像交叉分析篩選器這類簡單的視覺效果，都會起始查詢，並將其傳送到後端來源。 儲存模式將在本文後段進一步說明。

> [!NOTE]
> 若要查看目前的儲存模式，請選取 [模型]  檢視，選取感興趣的資料表，然後在 [屬性]  窗格的 [進階]  區段中，檢視 [儲存模式]  值。

## <a name="use-the-storage-mode-property"></a>使用儲存模式屬性

您可以對模型中的每一個資料表，設定儲存模式屬性。 若要設定儲存模式或查看其目前的設定，請在 [模型]  檢視中，選取您要檢視或設定其屬性的資料表，然後選取 [屬性]  窗格，接著展開 [進階]  區段，再展開 [儲存模式]  下拉式清單。

![特色選單中的 [屬性] 命令](media/desktop-storage-mode/storage-mode-02.png)


儲存模式共有三個值：

* **匯入**：當值設定為 [匯入]  時，將會快取匯入的資料表。 將查詢提交給會從匯入資料表傳回資料的 Power BI 資料集，只會傳回快取的資料。

* **DirectQuery**：若是設定此設定，將不會快取 DirectQuery 資料表。 將查詢提交給會從 DirectQuery資料表傳回資料的 Power BI 資料集 (例如資料分析運算式 (DAX))，只能藉由對資料來源執行即時查詢來達成此目的。 提交給資料來源的查詢，會使用適用於該資料來源的查詢語言，例如 SQL。

* **雙重**：雙重資料表可以快取或不快取兩種形式運作，視提交給 Power BI 資料集的查詢內容而定。 在某些情況下，您可以從快取的資料完成查詢。 在其他的情況下，則可以對資料來源執行即時查詢來完成查詢。

將資料表變更為**匯入**的作業無法復原  。 此屬性無法再變更回 DirectQuery 或「雙重」。

> [!NOTE]
> 您可以在 Power BI Desktop 和 Power BI 服務中使用「雙重」  儲存模式。


## <a name="constraints-on-directquery-and-dual-tables"></a>[DirectQuery] 和 [雙重] 資料表的限制

「雙重」資料表具有與 DirectQuery 資料表相同的功能性限制。 包括有限的 M 轉換，以及限制計算結果欄中的 DAX 函式。 如需詳細資訊，請參閱[使用 DirectQuery 的影響](desktop-directquery-about.md#implications-of-using-directquery)。

## <a name="propagation-of-dual"></a>雙重的傳播方式
請考慮下列簡單模型，其中所有資料表都來自支援 [匯入] 和 [DirectQuery] 的單一來源。

![儲存模式的範例關聯性檢視](media/desktop-storage-mode/storage-mode-04.png)

一開始，假設此模型中的所有資料表都是 DirectQuery。 若我們將 *SurveyResponse* 資料表的**儲存模式**變更為「匯入」，將會顯示下列警告視窗：

![儲存模式的警告視窗](media/desktop-storage-mode/storage-mode-05.png)

維度資料表 (*Customer*、*Geography* 和 *Date*) 可以設定為 [雙重]  ，以減少資料集中弱關聯性的數目並改善效能。 弱關聯性通常會涉及至少一個 [DirectQuery] 資料表，其中無法將聯結邏輯推送至來源系統。 [雙重]  資料表可作為 [DirectQuery] 或 [匯入] 運作，因此可協助避免此情況。

傳播邏輯是設計來協助包含許多資料表的模型。 假設您的模型具有 50 個資料表，而且只需要快取特定事實 (交易式) 的資料表。 Power BI Desktop 的邏輯會計算出必須設定為 [雙重]  之維度資料表的最小組合，因此您無須執行此作業。

傳播邏輯只會周遊至 **1 對多**關聯性的 1 邊。

## <a name="storage-mode-usage-example"></a>儲存體模式使用範例
接著讓我們繼續上一節的範例，並假設套用了下列儲存模式的屬性設定：

| 資料表                   | 儲存模式         |
| ----------------------- |----------------------| 
| *Sales*                 | DirectQuery          | 
| *SurveyResponse*        | 匯入               | 
| *Date*                  | 雙重                 | 
| *Customer*              | 雙重                 | 
| *Geography*             | 雙重                 | 


假設 *Sales* 資料表包含大量資料，且設定這些儲存模式屬性引發了下列行為。
* Power BI Desktop 會快取 *Date*、*Customer* 及 *Geography* 維度資料表，因此，當報表在擷取交叉分析篩選器值進行顯示時，很快就能載入初始報表。
* 不快取 *Sales* 資料表可以讓 Power BI Desktop 產生下列結果：
    * 資料重新整理時間可獲得改善，同時降低記憶體耗用量。
    * 對 *Sales* 資料表進行的報表查詢會在 DirectQuery 模式中執行。 這些查詢可能需要較長的時間，但因為沒有快取延遲，所以更接近即時。

* 對 *SurveyResponse* 資料表執行報表查詢，會從記憶體內的快取傳回，因此速度相對較快。

## <a name="queries-that-hit-or-miss-the-cache"></a>命中或遺漏快取的查詢

藉由將 **SQL Profiler** 連線至 Power BI Desktop 的診斷連接埠，您可以利用下列事件執行追蹤，查看哪些查詢會命中或遺漏記憶體中的快取：

* 查詢事件\查詢開始
* 查詢處理\Vertipaq SE 查詢開始
* 查詢處理\DirectQuery 開始

針對每個「查詢開始」  事件，請檢查其他具有相同 *ActivityID* 的事件。 例如，若無任何 *DirectQuery 開始*事件，但有 Vertipaq SE 查詢開始  事件，代表已從快取回應查詢。

參考**雙重**模式資料表的查詢，會盡可能地從快取傳回資料，否則會還原為 DirectQuery。

延續上一個範例，下列查詢只會參考來自**雙重**模式之 *Date* 資料表的資料行。 因此，查詢應會命中快取。

![適用於儲存體模式診斷的指令碼](media/desktop-storage-mode/storage-mode-06.png)

下列查詢只會參考 *Sales* 資料表的資料行，此資料表處於 **DirectQuery** 模式。 因此，它應該「不會」  命中快取。

![適用於儲存體模式診斷的指令碼](media/desktop-storage-mode/storage-mode-07.png)

下列查詢的特別之處在於它結合了兩個資料行。 此查詢不會命中快取。 您可能一開始就預期此查詢會從快取中擷取 *CalendarYear* 值，並從來源中擷取 *SalesAmount* 值，然後合併結果，但相較於將 SUM/GROUP BY 作業提交至來源系統，此方法比較沒有效率。 如果將此作業向下推送至來源，傳回的資料列數目可能大幅減少。 

![適用於儲存體模式診斷的指令碼](media/desktop-storage-mode/storage-mode-08.png)

> [!NOTE]
> 在合併快取及非快取的資料表時，此行為與 [Power BI Desktop 中的多對多關聯性](desktop-many-to-many-relationships.md)不同。

## <a name="caches-should-be-kept-in-sync"></a>快取應該保持同步

上節所示的查詢顯示，**雙重**資料表不一定每一次都會命中快取。 如此一來，當快取過期時，就可傳回不同的值。 例如，查詢執行將不會藉由篩選 DirectQuery 結果以符合快取的值，嘗試掩飾資料問題。 您應該最了解自己的資料流程，並應據此進行設計。 如有必要，可使用一些現有技術，在來源處理這類案例。

*雙重*儲存模式是一種效能最佳化。 只有在不影響達成商務需求的前提之下，才使用此模式。 如需替代行為，請考慮使用 [Power BI Desktop 中的多對多關聯性](desktop-many-to-many-relationships.md)文章中說明的技術。

## <a name="data-view"></a>資料檢視
若資料集中至少有一個資料表已將其儲存模式設定為**匯入**或**雙重**，就會顯示 [資料檢視]  索引標籤。

![Power BI Desktop 中的資料檢視](media/desktop-storage-mode/storage-mode-03.png)

在 [資料檢視]  中選取時，**雙重**及**匯入**資料表會顯示快取的資料。 DirectQuery 資料表不會顯示資料，並會顯示一則訊息，表示無法顯示 DirectQuery 資料表。


## <a name="limitations-and-considerations"></a>限制與考量

此版的儲存模式及其與複合模型之間的相互關聯有一些限制。

下列 Live Connect (多維度) 來源不得與複合模型並用：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 資料集
* Azure Analysis Services

當您使用 DirectQuery 連線到這些多維度來源時，無法連線到其他 DirectQuery 來源，也無法與匯入的資料合併。

使用複合模型時，仍然受限於 DirectQuery 的現有使用限制。 其中有許多限制每個資料表不同，視資料表的儲存模式而定。 例如，已匯入資料表上的計算結果欄可以參考其他資料表，但 DirectQuery 資料表上的計算結果欄仍僅限於參考相同資料表上的資料行。 如果模型內有任何資料表為 DirectQuery，則其他限制會套用至整個模型。 例如，當 QuickInsights 及問與答功能中有任何資料表為 DirectQuery 的儲存模式時，該模型便無法使用這兩項功能。 

## <a name="next-steps"></a>後續步驟

如需複合模型及 DirectQuery 的詳細資訊，請參閱下列文章：
* [Power BI Desktop 中的複合模型](desktop-composite-models.md)
* [Power BI Desktop 中的多對多關聯性](desktop-many-to-many-relationships.md)
* [使用 Power BI 的 DirectQuery](desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
