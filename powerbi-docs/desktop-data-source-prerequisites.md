---
title: "Power BI 資料來源必要條件"
description: "Power BI 資料來源必要條件"
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 213fb5fb23b2f6f9cd53e8dd7ce614160a334425
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="power-bi-data-source-prerequisites"></a>Power BI 資料來源的必要條件
針對每個資料提供者，Power BI 會在物件上支援特定的提供者版本。 如需 Power BI 可用資料來源的詳細資訊，請參閱[資料來源](desktop-data-sources.md)。 下表說明這些需求。

| 資料來源 | 提供者 | 最低提供者版本 | 最低資料來源版本 | 支援的資料來源物件 | 下載連結 |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (內建於 .Net Framework) |.Net framework 3.5 (僅限) |SQL Server 2005+ |資料表/檢視、純量函數、資料表函數 |包含在 .NET Framework 3.5 或更新版本中 |
| Access |Microsoft Access 資料庫引擎 (ACE) |ACE 2010 SP1 |沒有限制 |資料表/檢視 |[下載連結](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (僅限 .xls 檔案) (請參閱附註 1) |Microsoft Access 資料庫引擎 (ACE) |ACE 2010 SP1 |沒有限制 |資料表、工作表 |[下載連結](http://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (請參閱附註 2) |ODP.NET |ODAC 11.2 版本 5 (11.2.0.3.20) |9.x + |資料表/檢視 |[下載連結](http://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| System.Data.OracleClient (內建於 .Net Framework) |.NET framework 3.5 |9.x + |資料表/檢視 |包含在 .NET Framework 3.5 或更新版本中 | |
| IBM DB2 |來自 IBM (IBM 資料伺服器驅動程式套件的一部分) 的 ADO.Net 用戶端 |10.1 |9.1+ |資料表/檢視 |[下載連結](http://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |連接器/網路 |6.6.5 |5.1 |資料表/檢視、純量函數 |[下載連結](http://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |NPGSQL ADO.NET 提供者 |2.0.12 |7.4 |資料表/檢視 |[下載連結](http://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |Teradata 的 .NET 資料提供者 |14+ |12+ |資料表/檢視 |[下載連結](http://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere for .NET 3.5 |16+ |16+ |資料表/檢視 |[下載連結](http://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>副檔名為 .xlsx 的 Excel 檔案不需要安裝個別提供者。

>[!NOTE]
>Oracle 提供者也需要 Oracle 用戶端軟體 (版本 8.1.7+)。
> 
> 

