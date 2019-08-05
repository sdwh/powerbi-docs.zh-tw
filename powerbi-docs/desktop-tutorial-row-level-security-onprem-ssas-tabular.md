---
title: Power BI 中的動態資料列層級安全性與 Analysis Services 表格式模型
description: 動態資料列層級安全性與 Analysis Services 表格式模型
author: selvarms
manager: amitaro
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/28/2019
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: 6bfcb218f92c2b6e8a3349261e15e6b71b9512b2
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523224"
---
# <a name="dynamic-row-level-security-with-analysis-services-tabular-model"></a>動態資料列層級安全性與 Analysis Services 表格式模型

本教學課程使用範例資料集進行下列步驟，為您示範如何在 **Analysis Services 表格式模型**中
實作[**資料列層級安全性**](service-admin-rls.md)，並將其用於 Power BI 報表。 

* 在 [**AdventureworksDW2012** 資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)中建立新的安全性資料表
* 使用所需的事實和維度資料表建立表格式模型
* 定義使用者角色和權限
* 將模型部署到 **Analysis Services 表格式**執行個體
* 建置 Power BI Desktop 報表，以顯示為存取報表之使用者量身訂做的資料
* 將報表部署至 **Power BI 服務**
* 根據報表建立新的儀表板
* 與同事共用儀表板 

本教學課程需要 [**AdventureworksDW2012** 資料庫](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>工作 1︰建立使用者安全性資料表，並定義資料關聯性

您可以找到許多文章描述如何定義資料列層級動態的安全性與 **SQL Server Analysis Services (SSAS) 表格式**模型。 我們的範例使用 [Implement Dynamic Security by Using Row Filters](https://msdn.microsoft.com/library/hh479759.aspx) (使用資料列篩選來實作動態安全性)。 

此處的步驟需要使用 **AdventureworksDW2012** 關聯式資料庫。

1. 在 **AdventureworksDW2012** 中建立 **DimUserSecurity** 資料表，如下所示。 您可以使用 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 來建立資料表。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

2. 建立資料表並儲存之後，您必須在 **DimUserSecurity** 資料表 **SalesTerritoryID** 資料行與 **DimSalesTerritory** 資料表 **SalesTerritoryKey** 資料行之間建立關聯性，如下所示。 

   在 **SSMS** 中，以滑鼠右鍵按一下 **DimUserSecurity** 資料表，選取 [設計]  。 然後，選取 [資料表設計工具] -> [關聯性...]  。完成後，儲存資料表。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

3. 將使用者新增至資料表：以滑鼠右鍵按一下 **DimUserSecurity** 資料表，然後選取 [編輯前 200 個資料列]  。 新增使用者後，**DimUserSecurity** 資料表看起來應類似下列程式碼，但會具有您自己的使用者：
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   您會在稍後的工作中看到這些使用者。

4. 接下來，使用 **DimSalesTerritory** 資料表來完成「內部聯結」  ，該資料表顯示與使用者相關聯的區域詳細資料。 此處的 SQL 程式碼會執行「內部聯結」  ，且隨後會出現顯示資料表應如何出現的圖片。
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)

   上圖顯示各個銷售區域分別由誰負責，此資料是根據您在**步驟 2** 中建立的關聯性。 例如，您可以看到 **Jon Doe** 負責**澳洲**。 

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>工作 2︰使用事實和維度資料表建立表格式模型

1. 在您的關聯式資料倉儲就緒之後，您需要定義表格式模型。 您可以使用 [**SQL Server Data Tools (SSDT)** ](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools) 來建立模型。 如需詳細資訊，請參閱[建立新的表格式模型專案](https://msdn.microsoft.com/library/hh231689.aspx)。

2. 將所有必要的資料表匯入模型中，如下所示。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

3. 在您匯入所需的資料表之後，您必須使用**讀取**權限定義名為 **SalesTerritoryUsers** 的角色。 選取 SQL Server Data Tools 中的 [模型]  功能表，然後選取 [角色]  。 在 [角色管理員]  對話方塊中，選取 [新增]  。

4. 在 [角色管理員]  的 [成員]  索引標籤下，新增您在**工作 1 - 步驟 3** 中 **DimUserSecurity** 資料表所定義的使用者。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

5. 接下來，為 **DimSalesTerritory** 和 **DimUserSecurity** 資料表加入適當的函數，如 [資料列篩選]  索引標籤下所示。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

6. 在此步驟中，您將使用 **LOOKUPVALUE** 函式傳回資料行的值，其中 Windows 使用者名稱與 **USERNAME** 函式所傳回的使用者名稱相同。 然後，您可以將查詢限制在 **LOOKUPVALUE** 傳回值符合相同或相關資料表中值的位置。 在 [DAX 篩選]  資料行中，輸入下列公式︰
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])

    在此公式中，**LOOKUPVALUE** 函數會傳回 **DimUserSecurity [SalesTerritoryID]** 資料行的所有值，其中 **DimUserSecurity [UserName]** 等同於目前登入的 Windows 使用者名稱，而 **DimUserSecurity [SalesTerritoryID]** 等同 **DimSalesTerritory [SalesTerritoryKey]** 。
   
    > [!IMPORTANT]
    > 使用資料列層級安全性時不支援 DAX 函式 [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax)。

   SalesTerritoryKey 接著會使用 **LOOKUPVALUE** 所傳回的銷售集，限制在 **DimSalesTerritory** 中顯示的資料列。 只有當資料列的 **SalesTerritoryKey** 值位於由 **LOOKUPVALUE** 函式所傳回的識別碼集內，該資料列才會顯示。

7. 針對 **DimUserSecurity** 表格，請於 **DAX 篩選**資料行中新增下列公式：
   
       =FALSE()

    此公式會指定將所有資料行都解析成 `false`；亦即無法查詢 **DimUserSecurity** 資料表資料行。

8. 現在您需要處理並部署該模型。 如需詳細資訊，請參閱[部署](https://msdn.microsoft.com/library/hh231693.aspx)一文。

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>工作 3︰在您的內部部署資料閘道中新增資料來源

部署表格式模型以供使用之後，您需要將資料來源連線新增到內部部署 Analysis Services 表格式伺服器中。

1. 若要允許 **Power BI 服務**存取您內部部署的分析服務，您必須在環境中安裝及設定 **[內部部署資料閘道](service-gateway-onprem.md)** 。

2. 當正確設定閘道之後，必須為 **Analysis Services** 表格式執行個體建立資料來源連接。 如需詳細資訊，請參閱[管理您的資料來源 - Analysis Services](service-gateway-enterprise-manage-ssas.md)。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

  完成上一個步驟之後，即完成了閘道設定，可與內部部署的 **Analysis Services** 資料來源互動。

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>工作 4︰使用 Power BI Desktop 建立以 Analysis Services 表格式模型為基礎的報表

1. 啟動 [Power BI Desktop]  ，然後選取 [取得資料] > [資料庫]  。

2. 從資料來源清單中，選取 **SQL Server Analysis Services 資料庫**，然後選取 [連線]  。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

3. 填寫您的 **Analysis Services** 表格式執行個體詳細資料，然後選取 [即時連線]  。 然後選取 [確定]  。 使用 **Power BI**，動態安全性僅適用於**即時連線**。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

4. 您可以看到部署的模型位於 **Analysis Services** 執行個體中。 選取個別模型，然後選取 [確定]  。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   **Power BI Desktop** 現在會在 [欄位]  窗格中畫布右方顯示所有可用的欄位。

5. 在右方 [欄位]  窗格上，選取 [FactInternetSales]  資料表的 [SalesAmount]  量值和 [SalesTerritory]  資料表的 [SalesTerritoryRegion]  維度。

6. 為了將這份報表保持簡潔，我們現在不會新增任何其他的欄位。 為了讓資料以更能表達意義的方式呈現，請將視覺效果變更為**環圈圖**。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

7. 在報表準備就緒之後，您可以直接將其發行至 Power BI 入口網站。 在 **Power BI Desktop** 的 [主資料夾]  功能區上，選取 [發行]  。

## <a name="task-5-create-and-share-a-dashboard"></a>工作 5︰建立及共用儀表板

1. 您已建立報表並將其發佈至 **Power BI** 服務。 現在，您可以使用在先前步驟中建立的範例來示範模型安全性案例。
   
   身為**銷售經理**角色，Sumit 可以在所有不同的銷售區域查看資料。 Sumit 建立此報表 (在上一個工作步驟中建立的報表)，並將其發佈至 Power BI 服務。
   
   Sumit 發佈報表之後，下一步就是根據該報表在 Power BI 服務中建立稱為 **TabularDynamicSec** 的儀表板。 在下圖中，請注意 Sumit 可以看到對應至所有銷售區域的資料。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

2. 現在 Sumit 和他的同事 Jon Doe (負責澳洲地區的銷售) 共用儀表板。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

3. 當 Jon Doe 登入 **Power BI** 服務並檢視 Sumit 建立的共用儀表板時，應該**只**會看到其職責區域的銷售狀況。 
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)

    恭喜您！ **Power BI 服務**會顯示內部部署 **Analysis Services** 表格式模型中定義的資料列層級安全性。 Power BI 使用 **EffectiveUserName** 屬性，將目前的 Power BI 使用者認證傳送到內部部署資料來源以執行查詢。

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>工作 6︰了解幕後發生的情況

此工作假設您熟悉 [SQL Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler)，因為您需要擷取內部部署 SSAS 表格式執行個體上的 SQL Server Profiler 追蹤。

1. 使用者 (Jon Doe) 在 Power BI 服務中存取儀表板時，就會立刻將工作階段初始化。 您可以看到 **salesterritoryusers** 角色立即生效，並使用有效的使用者名稱 **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>**
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>

2. 根據有效的使用者名稱要求，Analysis Services 會在查詢本機 Active Directory 後將要求轉換為實際 moonneo/jondoe 認證。 一旦 **Analysis Services** 取得認證，**Analysis Services** 會傳回使用者具有檢視和存取權的資料。

3. 如果儀表板發生更多的活動，例如若是 Jon Doe 從儀表板前往基礎報表，您可以使用 SQL Profiler 看到特定查詢會作為 DAX 查詢回到 Analysis Services 表格式模型。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

4. 您也可以在下方看到正在執行以開始填入報表資料的 DAX 查詢。
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>考量

* 搭配 Power BI 的內部部署資料列層級安全性僅適用於即時連線。

* 使用 [即時連線]  存取報表的使用者，可立即從 Power BI 服務使用處理模型後所的任何資料變更。

