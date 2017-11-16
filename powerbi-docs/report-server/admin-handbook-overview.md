---
title: "系統管理員手冊概觀, Power BI 報表伺服器"
description: "歡迎使用 Power BI 報表伺服器的系統管理員手冊，您可於此內部部署位置中儲存和管理您的 Power BI 報表、行動報表及編頁報表。"
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.author: asaxton
ms.openlocfilehash: 6307e6cc3beb119ffaba40344736ff29e293fc95
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="administrator-handbook-overview-power-bi-report-server"></a>系統管理員手冊概觀, Power BI 報表伺服器
歡迎使用 Power BI 報表伺服器的系統管理員手冊，您可於此內部部署位置中儲存和管理您的 Power BI 報表、行動報表及編頁報表。

![](media/admin-handbook-overview/admin-handbook.png)

此手冊將協助您了解規劃、部署及管理 Power BI 報表伺服器的概念。

## <a name="installing-and-migration"></a>安裝和移轉
您必須安裝 Power BI 報表伺服器，方可加以使用。 我們有可讓您處理這項工作的資訊。

請先參閱報表伺服器的[系統需求](system-requirements.md)，再開始安裝、升級或移轉至 Power BI 報表伺服器。

### <a name="installing"></a>安裝
若您要部署新的 Power BI 報表伺服器，可使用下列協助文件。 可使用快速入門直接開始。 或者您也可以查看安裝文件，了解完整詳細資料。

* [快速入門︰安裝 Power BI 報表伺服器](quickstart-install-report-server.md)
* [安裝 Power BI 報表伺服器](install-report-server.md)

### <a name="migration"></a>移轉
SQL Server Reporting Services 沒有任何就地升級。 若您有現有的 SQL Server Reporting Services 執行個體，且想要設為 Power BI 報表伺服器，則必須移轉它。 您也可能因為其他原因而想進行移轉。 檢閱移轉文件以了解詳細資料。

[移轉報表伺服器安裝](migrate-report-server.md)

## <a name="configuring-your-report-server"></a>設定報表伺服器
設定報表伺服器時，您有許多選項可選。 您要使用 SSL 嗎？ 您要設定電子郵件伺服器嗎？ 您要與 Power BI 服務整合，以釘選視覺效果嗎？

您的多數設定都將在報表伺服器組態管理員中進行。 查看[組態管理員](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode)文件以取得詳細資料。

## <a name="security"></a>安全性
安全性與保護對所有組織而言都至關重要。 您可以在[安全性](https://docs.microsoft.com/sql/reporting-services/security/reporting-services-security-and-protection)文件中，了解驗證、授權、角色和權限。

## <a name="next-steps"></a>後續步驟
[快速入門︰安裝 Power BI 報表伺服器](quickstart-install-report-server.md)  
[如何找到您的報表伺服器產品金鑰](find-product-key.md)  
[安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop](install-powerbi-desktop.md)  
[安裝報表產生器](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[下載 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

