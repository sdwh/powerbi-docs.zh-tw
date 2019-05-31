---
title: 連線到 Power BI Premium 與用戶端應用程式和工具 （預覽） 的資料集
description: 描述如何從用戶端應用程式和工具連線到 Power BI Premium 中的資料集。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 063f43cb2345ccb3d1fec5c414100beb8ccde451
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941518"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>連線到資料集與用戶端應用程式和工具 （預覽）

Power BI Premium 工作區和資料集支援*唯讀*來自 Microsoft 和協力廠商用戶端應用程式和工具連線。 

> [!NOTE]
> 這篇文章只被要介紹 Power BI Premium 工作區和資料集上的唯讀狀態連線。 它*不是*主要用來提供可程式性、 特定的工具和應用程式、 架構和管理工作區和資料集的深入資訊。 此處所述的主旨需要充分了解 Analysis Services 表格式模型資料庫架構和管理。

## <a name="protocol"></a>通訊協定

Power BI Premium 使用[XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) (XMLA) 通訊協定，用戶端應用程式和管理您的工作區和資料集的引擎之間的通訊。 這些通訊都是透過功能通常稱為 XMLA 端點。 XMLA 是相同的 Microsoft Analysis Services 引擎在幕後，執行 Power BI 語意模型化、 管理、 生命週期及資料管理所使用的通訊協定。 

大部分的用戶端應用程式和工具不明確通訊與引擎藉由使用 XMLA 端點。 相反地，它們會使用 MSOLAP、 ADOMD，等 AMO 用戶端程式庫為用戶端應用程式和引擎，它只會使用 XMLA 通訊協定之間的媒介。


## <a name="supported-tools"></a>支援的工具

這些工具可支援 Power BI Premium 工作區和資料集的唯讀存取：

**SQL Server Management Studio (SSMS)** -支援 DAX、 MDX、 XMLA 和 TraceEvent 的查詢。 需要版本 18.0。 下載[此處](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)。 

**SQL Server Profiler** -隨附於 SSMS 18.0 （預覽），這項工具提供追蹤和偵錯的伺服器事件。 您可以擷取，並將每一個事件相關的資料儲存至檔案或資料表，以供稍後分析。 雖然正式被取代的 SQL Server，Profiler 會繼續包含在 SSMS 中，並仍可支援 Analysis Services 和現在，Power BI Premium。 若要進一步了解，請參閱[SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler)。

**DAX Studio** -開放原始碼社群工具，用於執行和分析 DAX 查詢 Analysis Services。 需要 2.8.2 版或更高版本。 若要進一步了解，請參閱[daxstudio.org](https://daxstudio.org/)。

**Excel 樞紐分析表**-按一下隨選版本的 Office 16.0.11326.10000 以上。

**第三方**-包含用戶端的資料視覺效果應用程式和可以連線到的工具、 查詢，並使用 Power BI Premium 中的資料集。 大部分工具皆需要最新版本的 MSOLAP 用戶端程式庫，但某些可能使用 ADOMD。

## <a name="client-libraries"></a>用戶端程式庫

用戶端程式庫所需連接到 Power BI Premium 工作區的 用戶端應用程式和工具。 用來連接到 Analysis Services 相同的用戶端程式庫也支援在 Power BI Premium。 Microsoft 用戶端應用程式，例如 Excel、 SQL Server Management Studio (SSMS) 和 SQL Server Data Tools (SSDT) 安裝所有三個用戶端程式庫，並加以更新，以及一般的應用程式更新。 在某些情況下，特別是使用協力廠商應用程式和工具，您可能需要安裝較新版的用戶端程式庫。 用戶端程式庫會每月更新。 若要進一步了解，請參閱[適用於連接到 Analysis Services 的用戶端程式庫](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers)。

## <a name="connecting-to-a-premium-workspace"></a>連接到 Premium 工作區

您可以連接到工作區指派給 Premium 專用容量。 指派給專用容量的工作區中有一個連接字串 URL 格式。 

若要取得工作區的連接字串，在 Power BI 中，在**工作區設定**上**Premium**索引標籤**工作區連線**，按一下 **複製**.

![工作區連接字串](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

工作區連線會使用下列 URL 格式來解決工作區，如同它已執行的 Analysis Services 伺服器名稱：   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

比方說， `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`
> [!NOTE]
> `[workspace name]` 會區分大小寫，並可包含空格。 

### <a name="to-connect-in-ssms"></a>若要在 SSMS 中連線

在 **連接到伺服器** > **伺服器類型**，選取**Analysis Services**。 在 **伺服器名稱**，輸入 URL。 在 **驗證**，選取**Active Directory-與 MFA 支援通用**，然後在**使用者名稱**，輸入您組織的使用者識別碼。 

當連線時，工作區會顯示為 Analysis Services 伺服器，並在工作區中的資料集都會顯示為 資料庫。  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>初始目錄

有些工具，像是 SQL Server Profiler，您可能需要指定*Initial Catalog*。 指定工作區中的資料集 （資料庫）。 在 **連接到伺服器**，按一下**選項**。 在 **連接到伺服器**對話方塊上**連接屬性**索引標籤**連接到資料庫**，輸入資料集名稱。

### <a name="duplicate-workspace-name"></a>重複的工作區名稱

連接到另一個工作區名稱相同的工作區時，您可能會收到下列錯誤：**無法連線到 powerbi://api.powerbi.com/v1.0/ [租用戶名稱] / [工作區名稱]。**

若要解決這個錯誤，除了工作區名稱，指定 ObjectIDGuid，可以從 URL 中的工作區 objectID 複製。 附加至連接 URL 的 objectID。 例如，' powerbi://api.powerbi.com/v1.0/myorg/Contoso 銷售-9d83d204-82a9-4b36-98f2-a40099093830'

### <a name="duplicate-dataset-name"></a>重複的資料集名稱

連接到具有相同的工作區中的另一個資料集名稱相同的資料集時，請將資料集 guid 附加至資料集名稱。 您可以取得這兩個資料集名稱*和*時連線到工作區，在 SSMS 中的 guid。 

### <a name="delay-in-datasets-shown"></a>顯示的資料集的延遲時間

連線到工作區時，新增、 刪除及重新命名的資料集的變更可能需要 5 分鐘的時間才會出現。 

### <a name="unsupported-datasets"></a>不支援的資料集

藉由使用 XMLA 端點便無法存取下列資料集。 這些資料集*不會*出現在 其他工具或 SSMS 中的工作區： 

- 透過即時連線到 Analysis Services 模型的資料集。 
- 使用 REST API 將資料推送的資料集。
- Excel 活頁簿的資料集。 

在 Power BI 服務中不支援下列資料集：   

- 透過即時連線到 Power BI 資料集的資料集。

## <a name="audit-logs"></a>稽核記錄 

當用戶端應用程式和工具連線到工作區時，透過 XMLA 端點的存取會記錄在 Power BI 稽核記錄檔底下**GetWorkspaces**作業。 若要進一步了解，請參閱[稽核 Power BI](service-admin-auditing.md)。

## <a name="see-also"></a>另請參閱

[Analysis Services 參考](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[SQL Server Analysis Services 表格式通訊協定](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[動態管理檢視 (Dmv)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
