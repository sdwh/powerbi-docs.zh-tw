---
title: "Power BI Desktop 中的資料來源"
description: "Power BI Desktop 中的資料來源"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: complete
qualitydate: 04/29/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: davidi
ms.openlocfilehash: 6014b38e0e9cabe0dc909268f87cdb284de47106
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="data-sources-in-power-bi-desktop"></a>Power BI Desktop 中的資料來源
有了 Power BI Desktop，您可以從許多不同來源連接至資料。 在此頁面底部有可用資料來源的完整清單。

若要連接到資料，請從 [主資料夾]  功能區選取 [取得資料]  。 選取向下箭號，或按鈕上的 [取得資料]  文字，會顯示 [最常見]  資料類型功能表，如下圖所示。

![](media/desktop-data-sources/data-sources_1.png)

選取 [其他...]， 該選項來自 [最常見] 功能表，如此即會顯示 [取得資料] 視窗。 您也可以藉由直接選取 [取得資料] **圖示按鈕**，叫出 [取得資料] 視窗 (並略過 [最常見] 功能表)。

![](media/desktop-data-sources/data-sources_2.png)

> [!NOTE]
> Power BI 小組會持續將可用的資料來源擴充到 **Power BI Desktop** 和 **Power BI 服務**。 因此，您經常會看到舊版工作進行中的資料來源標示為 *Beta* 或「預覽」。 任何標示為 *Beta* 或「預覽」的資料來源，受到的支援和功能都有限制，不應該用在生產環境。
> 
> 

## <a name="data-sources"></a>資料來源
資料類型會組織成下列類別：

* 全部
* 檔案
* 資料庫
* Azure
* 線上服務
* 其他

[全部]  類別包含所有類別的所有資料連線類型。

[檔案]  類別提供下列資料連線：

* Excel
* Text/CSV
* XML
* JSON
* 資料夾
* SharePoint 資料夾

下圖顯示 [檔案]  的 [取得資料] 視窗。

![](media/desktop-data-sources/data-sources_3.png)

> [!NOTE]
> 在舊版的 Power BI Desktop 中，**CSV** 與**文字**為不同的資料連線類型。 這兩個資料連接器已合併為 **CSV/文字**。
> 
> 

[資料庫]  類別提供下列資料連線：

* SQL Server 資料庫
* Access 資料庫
* SQL Server Analysis Services 資料庫
* Oracle 資料庫
* IBM DB2 資料庫
* IBM Informix 資料庫 (搶鮮版 (Beta))
* IBM Netezza (Beta)
* MySQL 資料庫
* PostgreSQL 資料庫
* Sybase 資料庫
* Teradata 資料庫
* SAP HANA 資料庫
* SAP Business Warehouse 伺服器
* Amazon Redshift
* Impala
* Google BigQuery (搶鮮版 (Beta))
* 雪花式

> [!NOTE]
> 某些資料庫連接器的啟用方式為選取 **[檔案] > [選項和設定] > [選項]**，然後選取 [預覽功能] 並啟用該連接器。 如果您沒有看到上述連接器，但想要加以使用，請檢查您的 [預覽功能] 設定。 亦請注意，任何標示為 *Beta* 或「預覽」的資料來源，受到的支援和功能都有限制，不應該用在生產環境。
> 
> 

下圖顯示 [資料庫]  的 [取得資料] 視窗。

![](media/desktop-data-sources/data-sources_4.png)

[Azure]  類別提供下列資料連線：

* Azure SQL Database
* Azure SQL 資料倉儲
* Azure Analysis Services 資料庫 (搶鮮版 (Beta))
* Azure Blob 儲存體
* Azure 表格儲存體
* Azure Cosmos DB (搶鮮版 (Beta))
* Azure Data Lake Store
* Azure HDInsight (HDFS)
* Azure HDInsight Spark (Beta)

下圖顯示 [Azure]  的 [取得資料] 視窗。

![](media/desktop-data-sources/data-sources_5.png)

[線上服務] 類別提供下列資料連線：

* Power BI 服務
* SharePoint Online 清單
* Microsoft Exchange Online
* Dynamics 365 (線上)
* Dynamics 365 for Financials (搶鮮版 (Beta))
* Common Data Service (搶鮮版 (Beta))
* Microsoft Azure Consumption Insights (搶鮮版 (Beta))
* Visual Studio Team Services (Beta)
* Salesforce 物件
* Salesforce 報表
* Google Analytics (分析)
* appFigures (Beta)
* comScore Digital Analytix (Beta)
* Dynamics 365 for Customer Insights (Beta)
* Facebook
* GitHub (Beta)
* Kusto (搶鮮版 (Beta))
* MailChimp (Beta)
* Mixpanel (搶鮮版 (Beta))
* Planview Enterprise (Beta)
* Projectplace (搶鮮版 (Beta))
* QuickBooks Online (Beta)
* Smartsheet
* SparkPost (Beta)
* SQL Sentry (Beta)
* Stripe (搶鮮版 (Beta))
* SweetIQ (Beta)
* Troux (Beta)
* Twilio (Beta)
* tyGraph (Beta)
* Webtrends (Beta)
* Zendesk (Beta)

下圖顯示 [線上服務] 的 [取得資料] 視窗。

![](media/desktop-data-sources/data-sources_6b.png)

[其他]  類別提供下列資料連線：

* Vertica (搶鮮版 (Beta))
* Web
* SharePoint 清單
* OData 摘要
* Active Directory
* Microsoft Exchange
* Hadoop 檔案 (HDFS)
* Spark (Beta)
* R Script
* ODBC
* OLE DB
* 空白查詢

下圖顯示 [其他]  的 [取得資料] 視窗。

![](media/desktop-data-sources/data-sources_7a.png)

> [!NOTE]
> 目前無法連線至使用 Azure Active Directory 保護的自訂資料來源。
> 
> 

## <a name="connecting-to-a-data-source"></a>連接到資料來源
若要連接至資料來源，請從 [取得資料]  視窗選取資料來源，然後選取 [連接] 。 在下圖中，從 [其他]  資料連線類別選取了 [Web]  。

![](media/desktop-data-sources/data-sources_7b.png)

隨即會顯示資料連線類型特有的連線視窗。 如果需要認證，將提示您提供它們。 下圖顯示輸入 URL 以連接到 Web 資料來源。

![](media/desktop-data-sources/datasources_fromwebbox.png)

輸入 URL 或資源連線資訊之後，請選取 [確定] 。 Power BI Desktop 會建立資料來源的連線，並在 [導覽器] 中呈現可用的資料來源。

![](media/desktop-data-sources/datasources_fromnavigatordialog.png)

您可以選取 [導覽器]  窗格底部的 [載入]  按鈕來載入資料，或是選取 [編輯]  按鈕，在載入資料之前先編輯查詢。

這就是連接到 Power BI Desktop 中資料來源的全部資訊！ 嘗試連接到我們持續增加的資料來源，並經常回來查看，我們隨時會增加新的來源。

## <a name="next-steps"></a>後續步驟
您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [開始使用 Power BI Desktop](desktop-getting-started.md)
* [Power BI Desktop 的查詢概觀](desktop-query-overview.md)
* [Power BI Desktop 中的資料類型](desktop-data-types.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常見查詢工作](desktop-common-query-tasks.md)    

