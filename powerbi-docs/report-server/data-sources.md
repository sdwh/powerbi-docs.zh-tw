---
title: "Power BI 報表伺服器中的 Power BI 報表資料來源"
description: "Power BI 報表可以連線到不同的資料來源。 根據使用資料的方式而定，可以使用不同的資料來源。"
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: caa45aab2c31974abb041a82eb2216ebee2eb148
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2018
---
# <a name="power-bi-report-data-sources-in-power-bi-report-server"></a>Power BI 報表伺服器中的 Power BI 報表資料來源
Power BI 報表可以連線到不同的資料來源。 根據使用資料的方式而定，可以使用不同的資料來源。 可以匯入資料，或者使用 DirectQuery 或與 SQL Server Analysis Services 的即時連線，直接查詢資料。

這些資料來源專屬於 Power BI 報表伺服器中使用的 Power BI 報表。 如需支援分頁報表之資料來源的詳細資訊，請參閱 [Reporting Services 支援的資料來源](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs)。

> [!IMPORTANT]
> Power BI Desktop 報表中的所有資料來源都必須支援設定排程的重新整理。
> 
> 

## <a name="list-of-supported-data-sources"></a>支援的資料來源清單
其他資料來源可以運作，即使它們不在支援的清單中。

| **資料來源** | **快取資料** | **排程的重新整理** | **即時/DirectQuery** |
| --- | --- | --- | --- |
| SQL Server 資料庫 |是 |是 |是 |
| SQL Server Analysis Services |是 |是 |是 |
| Azure SQL Database |是 |是 |是 |
| Azure SQL 資料倉儲 |是 |是 |是 |
| Excel |是 |是 |否 |
| Access 資料庫 |是 |是 |否 |
| Active Directory |是 |是 |否 |
| Amazon Redshift |是 |否 |否 |
| Azure Blob 儲存體 |是 |是 |否 |
| Azure Data Lake Store |是 |否 |否 |
| Azure HDInsight (HDFS) |是 |是 |否 |
| Azure HDInsight (Spark) |是 |是 |否 |
| Azure 表格儲存體 |是 |是 |否 |
| Dynamics 365 (線上) |是 |否 |否 |
| Facebook |是 |否 |否 |
| 資料夾 |是 |是 |否 |
| Google Analytics (分析) |是 |否 |否 |
| Hadoop 檔案 (HDFS) |是 |否 |否 |
| IBM DB2 資料庫 |是 |是 |否 |
| Impala |是 |否 |否 |
| JSON |是 |是 |否 |
| Microsoft Exchange |是 |否 |否 |
| Microsoft Exchange Online |是 |否 |否 |
| MySQL 資料庫 |是 |是 |否 |
| OData 摘要 |是 |是 |否 |
| ODBC |是 |是 |否 |
| OLE DB |是 |是 |否 |
| Oracle 資料庫 |是 |是 |是 |
| PostgreSQL 資料庫 |是 |是 |否 |
| Power BI 服務 |否 |否 |否 |
| R Script |是 |否 |否 |
| Salesforce 物件 |是 |否 |否 |
| Salesforce 報表 |是 |否 |否 |
| SAP Business Warehouse 伺服器 |是 |是 |是 |
| SAP HANA 資料庫 |是 |是 |是 |
| SharePoint 資料夾 (內部部署) |是 |是 |否 |
| SharePoint 清單 (內部部署) |是 |是 |否 |
| SharePoint Online 清單 |是 |否 |否 |
| 雪花式 |是 |否 |否 |
| Sybase 資料庫 |是 |是 |否 |
| Teradata 資料庫 |是 |是 |是 |
| Text/CSV |是 |是 |否 |
| Web |是 |是 |否 |
| XML |是 |是 |否 |
| appFigures (Beta) |是 |否 |否 |
| Azure Analysis Services 資料庫 (搶鮮版 (Beta)) |是 |否 |否 |
| Azure Cosmos DB (搶鮮版 (Beta)) |是 |否 |否 |
| Azure HDInsight Spark (Beta) |是 |否 |否 |
| Common Data Service (搶鮮版 (Beta)) |是 |否 |否 |
| comScore Digital Analytix (Beta) |是 |否 |否 |
| Dynamics 365 for Customer Insights (Beta) |是 |否 |否 |
| Dynamics 365 for Financials (搶鮮版 (Beta)) |是 |否 |否 |
| GitHub (Beta) |是 |否 |否 |
| Google BigQuery (搶鮮版 (Beta)) |是 |否 |否 |
| IBM Informix 資料庫 (搶鮮版 (Beta)) |是 |否 |否 |
| IBM Netezza (Beta) |是 |否 |否 |
| Kusto (搶鮮版 (Beta)) |是 |否 |否 |
| MailChimp (Beta) |是 |否 |否 |
| Microsoft Azure Consumption Insights (搶鮮版 (Beta)) |是 |否 |否 |
| Mixpanel (搶鮮版 (Beta)) |是 |否 |否 |
| Planview Enterprise (Beta) |是 |否 |否 |
| Projectplace (搶鮮版 (Beta)) |是 |否 |否 |
| QuickBooks Online (Beta) |是 |否 |否 |
| Smartsheet |是 |否 |否 |
| Spark (Beta) |是 |否 |否 |
| SparkPost (Beta) |是 |否 |否 |
| SQL Sentry (Beta) |是 |否 |否 |
| Stripe (搶鮮版 (Beta)) |是 |否 |否 |
| SweetIQ (Beta) |是 |否 |否 |
| Troux (Beta) |是 |否 |否 |
| Twilio (Beta) |是 |否 |否 |
| tyGraph (Beta) |是 |否 |否 |
| Vertica (搶鮮版 (Beta)) |是 |否 |否 |
| Visual Studio Team Services (Beta) |是 |否 |否 |
| Webtrends (Beta) |是 |否 |否 |
| Zendesk (Beta) |是 |否 |否 |

> [!IMPORTANT]
> 在資料來源設定的資料列層級安全性，應該適用於特定 DirectQuery (SQL Server、Azure SQL Database、Oracle 和 Teradata)，且即時連線假設 Kerberos 已在您的環境中適當設定。
> 
> 

## <a name="next-steps"></a>後續步驟
既然已挑選您的資料來源，請使用該資料來源中的資料以[建立報表](quickstart-create-powerbi-report.md)。

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

