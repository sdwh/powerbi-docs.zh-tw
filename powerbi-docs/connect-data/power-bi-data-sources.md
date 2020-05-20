---
title: Power BI 資料來源
description: 本文列出 Power BI 支援的資料來源，包括 DirectQuery 和內部部署資料閘道的相關資訊。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/10/2020
ms.author: kfollis
ms.openlocfilehash: 2aa12ec3d55e491535d12107fc70709f9d41c3f0
ms.sourcegitcommit: 6ba7cc9afaf91229f717374bc0c12f0b8201d15e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83438077"
---
# <a name="power-bi-data-sources"></a>Power BI 資料來源

下表顯示 Power BI 針對資料集所支援的資料來源，包括 DirectQuery 與內部部署資料閘道的相關資訊。 如需資料流程的詳細資訊，請參閱[連線到 Power BI 資料流程的資料來源](../transform-model/service-dataflows-data-sources.md)。

> [!NOTE]
> 需要 Internet Explorer 10 (或更新版本) 進行驗證的 Power BI Desktop 有許多資料連接器。 


| 資料來源 | 從桌面連線 | 從服務連線並重新整理 | DirectQuery/即時連線限制 | 閘道 (支援) | 閘道 (必要) |
|---|---|---|---|---|---|---|---|
| Access 資料庫 | 有 | 有 | 否 | 是 <sup>1</sup> | 有 |
| ActiveDirectory | 有 | 有 | 否 | 有 | 有 |
| Adobe Analytics | 有 | 有 | 否 | 否 | 否 |
| Amazon Redshift | 有 | 有 | 有 | 有 | 否 |
| appFigures | 有 | 有 | 否 | 否 | 否 |
| AtScale Cube | 有 | 有 | 有 | 有 | 否 |
| Azure Analysis Services | 有 | 有 | 有 | 是 <sup>2</sup> | 否 |
| Azure Blob 儲存體 | 有 | 有 | 否 | 有 | 否 |
| Azure Cosmos DB | 有 | 有 | 否 | 否 | 否 |
| Azure 成本管理 | 有 | 有 | 否 | 否 | 否 |
| Azure 資料總管 (kusto) | 有 | 有 | 有 | 否 | 否 |
| Azure Data Lake Storage Gen1 | 有 | 有 | 否 | 否 | 否 |
| Azure Data Lake Storage Gen2 | 有 | 有 | 否 | 有 | 否 |
| Azure DevOps | 有 | 有 | 否 | 否 | 否 |
| Azure DevOps Server | 有 | 有 | 否 | 有 | 有 |
| Azure HDInsight (HDFS) | 有 | 有 | 否 | 否 | 否 |
| Azure HDInsight Spark | 有 | 有 | 有 | 否 | 否 |
| Azure SQL Database | 有 | 有 | 有 | 是 <sup>2</sup> | 否 |
| Azure SQL 資料倉儲 | 有 | 有 | 有 | 是 <sup>2</sup> | 否 |
| Azure 資料表儲存體 | 有 | 有 | 否 | 有 | 否 |
| BI 連接器 | 有 | 有 | 有 | 有 | 有 |
| BI360 - Budgeting & Financial Reporting | 有 | 有 | 否 | 否 | 否 |
| Common Data Service | 有 | 有 | 否 | 否 | 否 |
| Data.World - 取得資料集 | 有 | 有 | 否 | 否 | 否 |
| Denodo | 有 | 有 | 有 | 有 | 有 |
| Dremio | 有 | 有 | 有 | 有 | 有 |
| Dynamics 365 (線上) | 有 | 有 | 否 | 否 | 否 |
| Dynamics 365 Business Central | 有 | 有 | 否 | 否 | 否 |
| Dynamics 365 Business Central (內部部署) | 有 | 有 | 否 | 否 | 否 |
| Dynamics 365 Customer Insights | 有 | 有 | 否 | 否 | 否 |
| Dynamics NAV | 有 | 有 | 否 | 否 | 否 |
| Emigo 資料來源 | 有 | 有 | 否 | 否 | 否 |
| Entersoft 商務套件 | 有 | 有 | 否 | 否 | 否 |
| Essbase | 有 | 有 | 有 | 有 | 有 |
| Exasol | 有 | 有 | 有 | 有 | 有 |
| Excel | 是 <sup>3</sup> | 是 <sup>3</sup> | 否 | 是 <sup>3</sup> | 否 <sup>4</sup> |
| Facebook | 有 | 有 | 否 | 否 | 否 |
| 檔案 | 有 | 有 | 否 | 有 | 有 |
| 資料夾 | 有 | 有 | 否 | 有 | 有 |
| GitHub | 有 | 有 | 否 | 否 | 否 |
| Google Analytics (分析) | 有 | 有 | 否 | 否 | 否 |
| Google BigQuery | 有 | 有 | 是 | 否 | 否 |
| Hadoop 檔案 (HDFS) | 有 | 否 | 否 | 否 | 否 |
| HDInsight 互動式查詢 | 有 | 有 | 有 | 否 | 否 |
| IBM DB2 | 有 | 有 | 有 | 有 | 否 |
| IBM Informix 資料庫 | 有 | 有 | 否 | 有 | 否 |
| IBM Netezza | 有 | 有 | 有 | 有 | 有 |
| Impala | 有 | 有 | 有 | 有 | 有 |
| Indexima | 有 | 有 | 有 | 有 | 有 |
| 企業 App Store | 有 | 有 | 否 | 否 | 否 |
| Information Grid | 有 | 有 | 否 | 否 | 否 |
| Intersystems IRIS | 有 | 有 | 有 | 有 | 有 |
| Intune 資料倉儲 | 有 | 有 | 否 | 否 | 否 |
| Jethro ODBC | 有 | 有 | 有 | 有 | 有 |
| JSON | 有 | 有 | 否 | 是** | 否 <sup>4</sup> |
| Kyligence Enterprise | 有 | 有 | 有 | 有 | 有 |
| MailChimp | 有 | 有 | 否 | 否 | 否 |
| Marketo | 有 | 有 | 否 | 否 | 否 |
| MarkLogic ODBC | 有 | 有 | 有 | 有 | 有 |
| Microsoft Azure 使用量見解 | 有 | 有 | 否 | 否 | 否 |
| Microsoft Exchange | 有 | 有 | 否 | 有 | 否 |
| Microsoft Exchange Online | 有 | 有 | 否 | 否 | 否 |
| Microsoft Graph 安全性 | 有 | 有 | 否 | 有 | 否 |
| Mixpanel | 有 | 有 | 否 | 否 | 否 |
| MySQL | 有 | 有 | 否 | 有 | 有 |
| OData | 有 | 有 | 否 | 有 | 否 |
| ODBC | 有 | 有 | 否 | 有 | 有 |
| OleDb | 有 | 有 | 否 | 有 | 有 |
| Oracle | 有 | 有 | 有 | 有 | 有 |
| Paxata | 有 | 有 | 否 | 有 | 否 |
| PDF | 有 | 有 | 否 | 有 | 否 <sup>4</sup> |
| Planview Enterprise One - CTM | 有 | 有 | 否 | 否 | 否 |
| Planview Enterprise One - PRM | 有 | 有 | 否 | 否 | 否 |
| Planview Projectplace | 有 | 有 | 否 | 否 | 否 |
| PostgreSQL | 有 | 有 | 有 | 有 | 否 |
| Power BI 資料流程 | 有 | 有 | 否 | 否 | 否 |
| Power BI 資料集 | 有 | 有 | 有 | 否 | 否 |
| Power Platform 資料流程 | 有 | 有 | 否 | 否 | 否 |
| Python 指令碼 | 有 | 是 <sup>5</sup> | 否 | 是 <sup>5</sup> | 有 |
| QubolePresto | 有 | 有 | 有 | 有 | 有 |
| Quick Base | 有 | 有 | 否 | 有 | 有 |
| QuickBooks Online | 有 | 有 | 否 | 否 | 否 |
| R 指令碼 | 有 | 是 <sup>5</sup> | 否 | 是 <sup>5</sup> | 否 |
| Roamler | 有 | 有 | 否 | 有 | 否 |
| Salesforce 物件 | 有 | 有 | 否 | 否 | 否 |
| Salesforce 報表 | 有 | 有 | 否 | 否 | 否 |
| SAP Business Warehouse 訊息伺服器 | 有 | 有 | 有 | 有 | 有 |
| SAP Business Warehouse 伺服器 | 有 | 有 | 有 | 有 | 有 |
| SAP HANA | 有 | 有 | 有 | 有 | 有 |
| SharePoint 資料夾 | 有 | 有 | 否 | 有 | 否 <sup>4</sup> |
| SharePoint 清單 | 有 | 有 | 否 | 有 | 否 <sup>4</sup> |
| SharePoint Online 清單 | 有 | 有 | 否 | 是 <sup>2</sup> | 否 |
| Smartsheet | 有 | 有 | 否 | 否 | 否 |
| 雪花式 | 有 | 有 | 有 | 有 | 否 |
| Spark | 有 | 有 | 有 | 有 | 否 |
| SparkPost | 有 | 有 | 否 | 否 | 否 |
| SQL Server | 有 | 有 | 有 | 有 | 有 |
| SQL Server Analysis Services | 有 | 有 | 有 | 有 | 有 |
| Stripe | 有 | 有 | 否 | 否 | 否 |
| SurveyMonkey | 有 | 有 | 否 | 有 | 否 |
| SweetIQ | 有 | 有 | 否 | 否 | 否 |
| Sybase | 有 | 有 | 否 | 有 | 有 |
| TeamDesk | 有 | 有 | 否 | 有 | 否 |
| Tenforce | 有 | 有 | 否 | 否 | 否 |
| Teradata | 有 | 有 | 有 | 有 | 有 |
| 文字/CSV | 有 | 有 | 否 | 有 | 否 <sup>4</sup> |
| Twilio | 有 | 有 | 否 | 否 | 否 |
| tyGraph | 有 | 有 | 否 | 否 | 否 |
| Vertica | 有 | 有 | 有 | 有 | 有 |
| Web | 有 | 有 | 否 | 有 | 是 <sup>6</sup> |
| Webtrends | 有 | 有 | 否 | 否 | 否 |
| Workforce Dimensions | 有 | 有 | 否 | 有 | 否 |
| XML | 有 | 有 | 否 | 有 | 否 <sup>4</sup> |
| Zendesk | 有 | 有 | 否 | 否 | 否 |
| | | | | | | | |

<sup>1</sup> 支援 [ACE OLEDB 提供者](https://www.microsoft.com/download/details.aspx?id=54920)，其與閘道安裝在同一部電腦上。

<sup>2</sup> 支援與內部部署版本相同的 M 函式，造成受限的驗證選項 (閘道不支援 OAuth)。

<sup>3</sup> Excel 1997-2003 檔案 (.xls) 需要 [ACE OLEDB 提供者](https://www.microsoft.com/download/details.aspx?id=54920)。

<sup>4</sup> 技術的內部部署版本所需。

<sup>5</sup> 僅支援[個人閘道](service-gateway-personal-mode.md)。

<sup>6</sup> .html、.xls 與 Access 資料庫需要

## <a name="single-sign-on-sso-for-directquery-sources"></a>DirectQuery 來源的單一登入 (SSO)

若已啟用 SSO 選項，且您使用者存取建置在資料來源上的報告，則 Power BI 會在對基礎資料來源的查詢中傳送其已驗證 Azure AD 認證。 這可讓 Power BI 遵從在資料來源層級所設定的安全性設定。
SSO 選項會在使用此資料來源的所有資料集中生效。 它不會影響用於匯入案例的驗證方法。 下列資料來源支援透過 DirectQuery 進行連線的 SSO：

- Azure SQL Database
- Azure SQL 資料倉儲
- Impala
- SAP HANA
- SAP BW
- SAP BW 訊息伺服器
- 雪花式
- Spark
- SQL Server
- Teradata

> [!Note]
> 不支援 Azure Multi-Factor Authentication (MFA)。 想要搭配 DirectQuery 使用 SSO 的使用者必須豁免於 MFA 之外。

## <a name="next-steps"></a>後續步驟

[連接至 Power BI Desktop 中的資料](desktop-quickstart-connect-to-data.md)  
[使用 Power BI 中的 DirectQuery](desktop-directquery-about.md)  
[Power BI 中的 SQL Server Analysis Services 即時資料](sql-server-analysis-services-tabular-data.md)  
[什麼是內部部署的資料閘道？](service-gateway-onprem.md)  
