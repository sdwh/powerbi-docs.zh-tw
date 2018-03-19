---
title: "Power BI 中 DirectQuery 支援的資料來源"
description: "取得可使用 DirectQuery 的資料來源清單。"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 03/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 2f395a5030cb2e025b8b69fa9b5375f471dea452
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Power BI 中 DirectQuery 支援的資料來源
**Power BI Desktop** 和 **Power BI 服務**有許多資料來源供您連線和存取資料。 本文描述 Power BI 的哪些資料來源可支援稱為 **DirectQuery** 的連線方法。 如需 DirectQuery 的詳細資訊，請參閱 [ **Power BI 中的 DirectQuery**](desktop-directquery-about.md)。

下列資料來源在 Power BI 中支援 DirectQuery：

* Amazon Redshift
* Azure HDInsight Spark (Beta)
* Azure SQL Database
* Azure SQL 資料倉儲
* Google BigQuery (搶鮮版 (Beta))
* IBM Netezza (Beta)
* Impala (2.x 版)
* Oracle 資料庫 (第 12 版及更新版本)
* SAP Business Warehouse 應用程式伺服器
* SAP Business Warehouse 訊息伺服器搶鮮版 (Beta)
* SAP HANA
* 雪花式
* Spark (Beta) (0.9 版及更新版本)
* SQL Server
* Teradata 資料庫
* Vertica (搶鮮版 (Beta))

名稱後面有 **(Beta)** 或 **(預覽)** 的資料來源可能會變更，不支援用於實際執行環境。 將報告發佈至 **Power BI 服務** 之後可能也不支援這些資料來源，這表示開啟已發行的報告或瀏覽資料集可能會導致錯誤。

**(Beta)** 和 **(預覽)** 資料來源唯一的差別是 **(預覽)** 來源必須先啟用成為預覽功能，才可供使用。 若要啟用 **(預覽)** 資料連接器，請在 **Power BI Desktop** 中移至 [檔案] > [選項和設定]，然後移至 [設定] > [選項] > [預覽功能]。

## <a name="on-premises-gateway-requirements"></a>內部部署閘道需求
下表指定將報告發佈至 **Power BI 服務**之後，是否需要**內部部署資料閘道**才能連線至指定的資料來源。

| 來源 | 需要閘道？ |
| --- | --- |
| SQL Server |是 |
| Azure SQL Database |否 |
| Azure SQL 資料倉儲 |否 |
| SAP HANA |是 |
| Oracle 資料庫 |是 |
| Teradata 資料庫 |是 |
| Amazon Redshift |否 |
| Impala (2.x 版) |是 |
| 雪花式 |是 |
| Spark (Beta) 0.9 版及更新版本 |**Power BI 服務**中尚不支援 |
| Azure HDInsight Spark (Beta) |否 |
| IBM Netezza |是 |
| SAP Business Warehouse 應用程式伺服器 |是 |
| SAP Business Warehouse 訊息伺服器 |**Power BI 服務**中尚不支援 |
| Google BigQuery |否 |


## <a name="next-steps"></a>後續步驟
如需 DirectQuery 的詳細資訊，請參閱下列資源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [內部部署資料閘道](service-gateway-onprem.md)

