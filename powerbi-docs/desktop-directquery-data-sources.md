---
title: Power BI 中 DirectQuery 支援的資料來源
description: 取得可使用 DirectQuery 的資料來源清單。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 098447f4d0c0b1dc9534c91e84827c4cefb8850c
ms.sourcegitcommit: fdb54145f9bc93b312409c15c603749f3a4a876e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52452537"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Power BI 中 DirectQuery 支援的資料來源
**Power BI Desktop** 和 **Power BI 服務**有許多資料來源供您連線和存取資料。 本文描述 Power BI 的哪些資料來源可支援稱為 **DirectQuery** 的連線方法。 如需 DirectQuery 的詳細資訊，請參閱 [ **Power BI 中的 DirectQuery**](desktop-directquery-about.md)。

下列資料來源在 Power BI 中支援 DirectQuery：

* Amazon Redshift
* Azure HDInsight Spark (Beta)
* Azure SQL Database
* Azure SQL 資料倉儲
* Google BigQuery (搶鮮版 (Beta))
* IBM DB2 資料庫
* IBM Netezza (Beta)
* Impala (2.x 版)
* Oracle 資料庫 (第 12 版及更新版本)
* SAP Business Warehouse 應用程式伺服器
* SAP Business Warehouse 訊息伺服器 (搶鮮版 (Beta))
* SAP HANA
* 雪花式
* Spark (Beta) (0.9 版及更新版本)
* SQL Server
* Teradata 資料庫
* Vertica (搶鮮版 (Beta))

名稱後面有**搶鮮版 (Beta)** 或 **(預覽)** 的資料來源可能會變更，不支援用於生產環境。 將報告發佈至 **Power BI 服務** 之後可能也不支援這些資料來源，這表示開啟已發佈的報表或瀏覽資料集可能會導致錯誤。

**(Beta)** 和 **(預覽)** 資料來源唯一的差別是 **(預覽)** 來源必須先啟用成為預覽功能，才可供使用。 若要啟用 **(預覽)** 資料連接器，請在 **Power BI Desktop** 中移至 [檔案] > [選項及設定] > [設定]，然後選取 [預覽功能]。

> [!NOTE]
> 對 SQL Server 的 DirectQuery 查詢需要使用目前 Windows 驗證認證或資料庫驗證以建立存取。 不支援備用認證。
>

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
| Snowflake |是 |
| Spark (Beta) 0.9 版及更新版本 |是 |
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

