---
title: 比較 Power BI 報表伺服器和 Power BI 服務
description: 本文會比較 Power BI 報表伺服器和 Power BI 服務的功能。
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.date: 05/07/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-report-server
manager: kfile
ms.custom: mvc
ms.openlocfilehash: c47722fda28fc45289858f082a0838f583b53dbb
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34296771"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>比較 Power BI 報表伺服器和 Power BI 服務

Power BI 報表伺服器和 Power BI 服務有許多相似之處和一些主要差異。 下表將會逐一說明。

| 功能 | Power BI 報表伺服器 | Power BI 服務 | 注意
|---------|---------|---------|---------|
| 部署 | 內部部署或雲端託管 | 雲端 | 如果透過 Power BI Premium 授權，Power BI 報表伺服器可以部署在 Azure VM (雲端託管) 中
| 來源資料 | 雲端及/或內部部署 | 雲端及/或內部部署 |  
| 授權 | Power BI Premium 或使用 SA 的 SQL Server EE | Power BI Pro 及/或 Power BI Premium |  
| 生命週期 | 新式生命週期原則 | 完全受控的服務 |  
| 發行週期 | 每 4 個月一次 | 每月一次 | 最新功能和修正首先會提供給 Power BI 服務。 在接下來的幾個版本中，大部分的核心功能都會提供給 Power BI 報表伺服器，而某些功能僅適用於 Power BI 服務。
| 在 Power BI Desktop 中建立 Power BI 報表 | 是 | 是 |  
| 在瀏覽器中建立 Power BI 報表 | 否 | 是 |  
| 需要閘道器 | 否 | 是 (針對內部部署資料來源) |  
| 即時串流 | 否 | 是 | [Power BI 中的即時串流](../service-real-time-streaming.md)
| Dashboards | 否 | 是 | [Power BI 服務中的儀表板](../service-dashboards.md) 
| 使用應用程式發佈群組的報表 | 否 | 是 | [使用儀表板和報表建立並發佈應用程式](../service-create-distribute-apps.md) 
| 內容套件 | 否 | 是 | [組織內容套件：簡介](../service-organizational-content-pack-introduction.md) 
| 連線到服務 (例如 Salesforce) | 否 | 是 | 使用 Power BI 服務[連線到所用服務](../service-connect-to-services.md)
| 問與答 | 否 | 是 | [Power BI 服務和 Power BI Desktop 中的問與答](../power-bi-q-and-a.md) 
| 快速見解 | 否 | 是 | [使用 Power BI 自動產生資料的見解](../service-insights.md) 
| 在 Excel 中分析 | 否 | 是 | [使用 Excel 分析](../service-analyze-in-excel.md) 
| 編頁報表 | 是 | 否 | 編頁報表無法在 Power BI 服務中使用，但您可以[將編頁報表項目釘選至 Power BI 儀表板](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)
| Power BI 行動應用程式 | 是 | 是 | [Power BI 行動裝置應用程式概觀](../mobile-apps-for-mobile-devices.md) 
| ARC GIS 地圖 | 否 | 是 | [Power BI 服務及 Power BI Desktop 中由 Esri 提供的 ArcGIS 地圖](../power-bi-visualization-arcgis.md)
| Power BI 報表的電子郵件訂用帳戶 | 否 | 是 | [訂閱 Power BI 服務中的報表或儀表板](../service-report-subscribe.md) 
| 編頁報表的電子郵件訂用帳戶 | 是 | 否 | [Reporting Services 中的電子郵件傳遞](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  
| 資料警示 | 否 | 是 | Power BI 服務中的[資料警示](../service-set-data-alerts.md)
| 資料列層級安全性 | 只能透過 DirectQuery 模式中的資料來源 | DirectQuery (資料來源) 與匯入模式中皆可使用 | Power BI 的[資料列層級安全性 (RLS)](../service-admin-rls.md) 
| 全螢幕模式 | 否 | 是 | Power BI 服務的[全螢幕模式](../service-fullscreen-mode.md) 
| 進階的 Office 365 共同作業 | 否 | 是 | 與 Office 365 [在應用程式工作區中共同作業](../service-collaborate-power-bi-workspace.md) 
| R 視覺效果 | 否 | 是 | 在 Power BI 服務中[建立 R 視覺效果](../service-r-visuals.md)  
| 預覽功能 | 否 | 是 | [選擇加入 Power BI 服務預覽](../service-preview-features.md)功能 
| 自訂視覺效果 | 是 | 是 | [Power BI 的自訂視覺效果](../power-bi-custom-visuals.md) 
| Power BI Desktop | 針對報表服務器進行了版本最佳化，可透過報表伺服器下載使用 | 針對 Power BI 服務進行了版本最佳化，可從 Windows 市集取得 | [適用於報表伺服器的 Power BI Desktop](https://powerbi.microsoft.com/report-server/) <br><br> [適用於 Power BI 服務的 Power BI Desktop](http://aka.ms/pbidesktopstore)

## <a name="next-steps"></a>後續步驟
[安裝 Power BI 報表伺服器](install-report-server.md)  



