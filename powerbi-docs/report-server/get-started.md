---
title: 什麼是 Power BI 報表伺服器？
description: 取得「Power BI 報表伺服器」的概觀，以了解它如何與 SQL Server Reporting Services (SSRS) 及其餘 Power BI 搭配運作。
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: 1be2270074011f73c3d942677211dd99d18c6b2b
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34294563"
---
# <a name="what-is-power-bi-report-server"></a>什麼是 Power BI 報表伺服器？

「Power BI 報表伺服器」是一個內部部署報表伺服器，其中含有入口網站，可供您顯示及管理報表和 KPI，還含有工具，可用來建立 Power BI 報表、編頁報表、行動報表及 KPI。 您的使用者可以透過各種不同方式存取這些報表：在網頁瀏覽器或行動裝置中檢視，或是在其收件匣中以電子郵件的形式檢視。

![Power BI 報表伺服器入口網站](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>比較 Power BI 報表伺服器 
「Power BI 報表伺服器」與 SQL Server Reporting Services 和 Power BI 線上服務都類似，但方式不同。 「Power BI 報表伺服器」與 Power BI 服務相似之處在於，兩者都裝載 Power BI 報表 (.PBIX) 和 Excel 檔案。 「Power BI 報表伺服器」與 Reporting Services 相似之處在於，兩者都位於內部部署環境且裝載編頁報表 (.RDL)。 「Power BI 報表伺服器」是 Reporting Services 的超集：所有可以在 Reporting Services 中執行的作業，您都能以「Power BI 報表伺服器」來執行且不僅限於這些作業，此外還支援 Power BI 報表。 如需詳細資料，請參閱[比較 Power BI 報表伺服器與 Power BI 服務](compare-report-server-service.md)。

## <a name="licensing-power-bi-report-server"></a>授權 Power BI 報表伺服器
您可以透過兩種不同的授權取得「Power BI 報表伺服器」：[Power BI Premium](../service-premium.md) 及含有「軟體保證」的 [SQL Server Enterprise Edition](https://www.microsoft.com/sql-server/sql-server-2017-editions)。 使用 Power BI Premium 授權時，您可以建立混合了雲端和內部部署環境的混合式部署。  

## <a name="web-portal"></a>入口網站
「Power BI 報表伺服器」的入口是一個可在任何新式瀏覽器中檢視的安全入口網站。 您可以在該處存取所有報表和 KPI。 入口網站上的內容會採用傳統資料夾階層的組織方式。 在您的資料夾中，內容會依類型分組：Power BI 報表、行動報表、編頁報表、KPI 及 Excel 活頁簿，再加上要用來作為報表構成要素的共用資料集和共用資料來源。 您可以標記我的最愛，以在單一資料夾中檢視它們。 並可直接在入口網站中建立 KPI。 

![Power BI 報表伺服器入口網站](media/get-started/web-portal.png)

您可以依據您的權限來管理入口網站中的內容。 您可以排定報表處理、視需要存取報表，以及訂閱已發佈的報表。 您也可以將自己的自訂[商標](https://docs.microsoft.com/sql/reporting-services/branding-the-web-portal)套用到入口網站。 

深入了解 [Power BI 報表伺服器入口網站](https://docs.microsoft.com/sql/reporting-services/web-portal-ssrs-native-mode)。

## <a name="power-bi-reports"></a>Power BI 報表
您使用已針對報表伺服器最佳化的 Power BI Desktop 版本來建立 Power BI 報表 (.PBIX)。 然後將這些報表發佈至您自己環境中的入口網站，並在該入口網站中檢視它們。

![「Power BI 報表伺服器」中的 Power BI 報表](media/get-started/powerbi-reports.png)

Power BI 報表是資料模型的多面向檢視，具有代表來自該資料模型各種不同發現和見解的視覺效果。  報表只能有一種視覺效果或有各種視覺效果的頁面。 視您的角色而定，您可能可以讀取和探索報表，或是為其他項目建立報表。

請安裝[已針對 Power BI 報表伺服器最佳化的 Power BI Desktop](quickstart-create-powerbi-report.md)。

## <a name="paginated-reports"></a>編頁報表
編頁報表 (.RDL) 是含有視覺效果的文件型報表，其中資料表會以水平和垂直方式展開來顯示其所有資料，並視需要一頁接著一頁延伸下去。 它們非常適用於已針對列印進行最佳化的固定配置、完美像素文件，例如 PDF 和 Word 檔案。

![「Power BI 報表伺服器」中的編頁報表](media/get-started/paginated-reports.png)

您可使用[報表產生器](https://docs.microsoft.com/sql/reporting-services/report-builder/report-builder-in-sql-server-2016)或 [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt) 的報表設計師建立外觀現代化的報表。

## <a name="reporting-services-mobile-reports"></a>Reporting Services 行動報表
行動報表會連線至內部部署資料，並具有可因應不同裝置和不同持有方式的回應式配置。 您可以使用「SQL Server 行動報表發行工具」來建立它們。

深入了解 [Reporting Services 行動報表](https://docs.microsoft.com/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher)。 

## <a name="report-server-programming-features"></a>報表伺服器的程式設計功能
您可以利用「Power BI 報表伺服器」的程式設計功能來延伸及自訂報表功能，並使用 API 來整合或延伸自訂應用程式中的資料和報表處理。

其他[報表伺服器開發人員文件](https://docs.microsoft.com/sql/reporting-services/reporting-services-developer-documentation)。

## <a name="next-steps"></a>後續步驟
[安裝 Power BI 報表伺服器](install-report-server.md)  
[安裝報表產生器](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)


