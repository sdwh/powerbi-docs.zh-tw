---
title: "Power BI 報表伺服器的變更記錄"
description: "此變更記錄適用於 Power BI 報表伺服器，並列出新的項目，以及每個發行組建的 Bug 修正。"
services: powerbi
documentationcenter: 
author: jtarquino
manager: jonhp
backup: maggies
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/17/2017
ms.author: jaimeta
ms.openlocfilehash: e56976943e58aba8c9ef36c576a16ab5eba4c796
ms.sourcegitcommit: 7d4ad2ba92a932d7cc6637348e0774be6623559e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="changelog-for-power-bi-report-server"></a>Power BI 報表伺服器的變更記錄

此變更記錄適用於 Power BI 報表伺服器，並列出新的項目，以及每個發行組建的 Bug 修正。

如需新功能的詳細資訊，請參閱 [Power BI 報表伺服器的新增功能](whats-new.md)。

## <a name="october-2017"></a>2017年 10 月

- **Power BI 報表伺服器**
    - 1.1.6530.30789 版 (組建 14.0.600.437)，發行日期：2017 年 11 月 17 日
        - Bug 修正
            - 修正基本驗證案例 
            - 修正無法在訂閱、快取重新整理計劃以及入口網站的歷程記錄快照集中的排程頁面選取平日
            - 針對編頁報表 (RDL)，修正 CanGrow 屬性文字當塊中的運算式設為 false 時，導致值無法正確顯示色彩與字型
            - 針對 Power BI 報表 (PBIX)，修正將圖例新增至折線圖會呈現空白的視覺效果

    - 版本 1.1.6514.9163 (組建 14.0.600.434)，發行日期：2017 年 11 月 1 日
        - Bug 修正
            - 超過 500 MB 之 PBIX 報表上傳可靠性問題的修正
            - 超過 1 GB 之 PBIX 報表資料載入問題的修正

    - 版本 1.1.6513.3500 (組建 14.0.600.433)，發行日期：2017 年 10 月 31 日
        - 功能
            - 內嵌資料模型支援
            - Excel 活頁簿檢視 (啟用 Office Online Server 整合)
            - 排程的資料重新整理 (PBIX)
            - 直接查詢支援
            - 大型檔案支援 (最多 2 GB)
            - 公開 REST API
            - Power BI Desktop 中的共用資料集支援 (透過 oData)
            - PBIX 檔案的 URL 參數支援
            - 協助工具增強功能

- **Power BI Desktop (針對 Power BI 報表伺服器最佳化)**
    - 版本：2.51.4885.1423 (2017 年 10 月)，發行日期：2017 年 11 月 17 日
        - Bug 修正
            - 修正無法在 x86 OS 上執行 32 位元的 Power BI Desktop
            - 針對 Power BI 報表 (PBIX)，修正以顯示 X 軸格線
            - 其他小 Bug 修正

    - 版本：2.51.4885.1041 (2017 年 10 月)，發行日期：2017 年 10 月 31 日
        - 功能
            - 包含與 Power BI 報表伺服器連線所需的變更 (2017 年 10 月)

## <a name="june-2017"></a>2017 年 6 月

- **Power BI 報表伺服器**
    - 組建 14.0.600.305，發行日期：2017 年 9 月 19 日  
        - Bug 修正
            - 更新至最新的 [Bing 地圖服務 Web 控制項](https://msdn.microsoft.com/library/mt712542.aspx)

    - 組建 14.0.600.301，發行日期：2017 年 7 月 11 日
        - Bug 修正
            - {{UserId}} 標記會解析成預存認證，而不是正在 Power BI 報表中執行報表的使用者
            - 無法轉譯 Power BI 報表伺服器報表中的某些影像
            - 無法變更 Power BI 報表伺服器中 Power BI 報表的名稱
            - 無法載入 Power BI 行動應用程式中的自訂視覺效果 (您可能需要重新安裝行動裝置應用程式，以清除本機快取)

    - 組建 14.0.600.271，發行日期：2017 年 6 月 12 日
        - Power BI 報表伺服器初始版本

## <a name="next-steps"></a>後續步驟

[使用者手冊](user-handbook-overview.md)  
[系統管理員手冊](admin-handbook-overview.md)  
[快速入門︰安裝 Power BI 報表伺服器](quickstart-install-report-server.md)  
[安裝報表產生器](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[下載 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)