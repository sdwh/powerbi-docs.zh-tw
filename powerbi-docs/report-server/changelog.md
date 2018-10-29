---
title: Power BI 報表伺服器的變更記錄
description: 此變更記錄適用於 Power BI 報表伺服器，並列出新的項目，以及每個發行組建的 Bug 修正。
author: jtarquino
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 03/31/2018
ms.author: jtarquino
ms.openlocfilehash: 41f48e886c376f6cc00a76313538e5a6b9ac1c3b
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641934"
---
# <a name="changelog-for-power-bi-report-server"></a>Power BI 報表伺服器的變更記錄

此變更記錄適用於 Power BI 報表伺服器，並列出新的項目，以及每個發行組建的 Bug 修正。

如需新功能的詳細資訊，請參閱 [Power BI 報表伺服器的新增功能](whats-new.md)。 

## <a name="august-2018"></a>2018 年 8 月
- **Power BI 報表伺服器**
    - *版本 1.3.6816.37243 (組建 15.0.2.557)，發行日期：2018 年 8 月 30 日*
        - Bug 修正
            - 已修正當在繫結重新導向未更新的情況下將伺服器從舊版 PBI Report Server 升級時，客戶會看到此訊息的問題：      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - 資料標籤透明度 (Data Label Transparency) 的錯誤 (Bug) 現在已修正。
            
    - 版本 1.3.6801.38816 (組建 15.0.2.540)，發行日期：2018 年 8 月 15 日
        - 功能
            - SAP HANA SSO Direct Query 對 Kerberos 的支援現在於 Power BI 報表中正式運作
            - 此版本隨附自訂視覺效果 API - 1.13.0 版
            - 自訂視覺效果將會回復為與目前伺服器 API 版本相容的舊版 (如果有的話)

- **Power BI Desktop (針對 Power BI 報表伺服器最佳化)**
    - 版本：2.61.5192.641 (2018 年 8 月)，發行日期：2018 年 8 月 15 日
        - 包含與 Power BI 報表伺服器連接所需的變更 (2018 年 8 月)         
        
## <a name="march-2018"></a>2018 年 3 月
- **Power BI 報表伺服器**
    - *版本 1.2.6690.34729 (組建：15.0.2.402)，發行日期：2018 年 4 月 27 日*
        - Bug 修正
            - 啟用 SQL Server Reporting Services 2017 目錄移轉功能
            - 針對 Power BI 報表 (PBIX)
                - 當伺服器設定為使用自訂驗證時，可以重新整理報表
                - 修改報表屬性不會重設資料來源認證
            - 針對編頁報表 (RDL)
                - 在 RDL 運算式中使用 `Lookup()` 或導數函式 (例如 `LookupSet()` 和 `MultiLookup()`) 已不再會產生 `#Error`
                - 連結報表在列印時會依照目標報表的頁面大小
                - 可以針對使用串聯參數的連結報表建立訂閱
                - 使用 IE11 時，可以修改多值參數預設值
                - 可以編輯資料導向訂閱傳遞選項
                - 可以在訂閱處於執行中狀態時，檢視和編輯訂閱
                - 設定資料來源認證不會移除以運算式為基礎的連接字串
            - 針對 KPI
                - 更新資料時會重新整理趨勢線
            - 一般穩定性改進

    - 版本 1.2.6660.39920 (組建 15.0.2.389)，發行日期：2018 年 3 月 28 日
        - Bug 修正
            - 針對 Power BI 報表 (PBIX)，修正匯出資料無法從 Power BI 視覺效果運作的情況
            - 針對 Power BI 報表 (PBIX)，修正 URL 篩選無法運作的情況
            - 針對編頁報表 (RDL)，修正在升級到 Power BI 報表伺服器 3 月版本之後映像無法在 IE11 中正確顯示的情況

    - 版本 1.2.6648.38132 (組建 15.0.2.378)，發行日期：2018 年 3 月 19 日
        - 安全性更新
        - 協助工具改善
        - Bug 修正
            - 針對編頁報表 (RDL)，修正編輯其屬性後還原之連結報表中的參數可見度
            - 修正其自訂表單驗證會忽略滑動期限 Cookie 的入口網站
            - 修正 Word 的匯出，如果列內容空白，會建立不相等的列高
            - 針對編頁報表 (RDL)，修正以連接字串為基礎的運算式，當我們變更資料來源的認證時，會刪除該連接字串
            - 修正搭配使用 KPI 和文字值的功能
            - 針對編頁報表 (RDL)，修正將新資料集指派給現有編頁報表 (RDL) 的功能
            - 其他穩定性和可用性修正

- **Power BI Desktop (針對 Power BI 報表伺服器最佳化)**
    - 版本：2.56.5023.1043 (2018 年 3 月)，發行日期：2018 年 3 月 19 日
        - 包含與 Power BI 報表伺服器連接所需的變更 (2018 年 3 月)

## <a name="october-2017"></a>2017年 10 月

- **Power BI 報表伺服器**
    - 版本 1.1.6582.41691 (組建 14.0.600.442)，發行日期：2018 年 1 月 10 日
        - 安全性更新
        - Bug 修正
            - Model.GetParameters 傳回 400 的修正
            - 設定共用資料設為現有分頁報表 (RDL) 的修正
            - 將具有不同參數值的報表匯出成 PDF 時，ExecutionNotFoundException 的修正

    - *1.1.6551.5155 版 (組建 14.0.600.438)，發行日期：2017 年 12 月 11 日*
        - Bug 修正
            - 在重新整理特定 Power BI Desktop 報表之後無法儲存資料。

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
    - *版本：2.51.4885.3981 (2017 年 10 月)，發行日期：2018 年 4 月 10 日*
        - 安全性更新

    - 版本：2.51.4885.2501 (2017 年 10 月)，發行日期：2018 年 1 月 10 日
        - 安全性更新

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
    - 組建 14.0.600.309，發行日期：2018 年 1 月 10 日
        - 安全性更新

    - 組建 14.0.600.305，發行日期：2017 年 9 月 19 日  
        - Bug 修正
            - 更新至最新的 [Bing 地圖服務 Web 控制項](https://msdn.microsoft.com/library/mt712542.aspx)

    - 組建 14.0.600.301，發行日期：2017 年 7 月 11 日
        - Bug 修正
            - `{{UserId}}` 標記會解析成預存認證，而不是正在「Power BI 報表」中執行報表的使用者
            - 無法轉譯 Power BI 報表伺服器報表中的某些影像
            - 無法變更 Power BI 報表伺服器中 Power BI 報表的名稱
            - 無法載入 Power BI 行動應用程式中的自訂視覺效果 (您可能需要重新安裝行動裝置應用程式，以清除本機快取)

    - 組建 14.0.600.271，發行日期：2017 年 6 月 12 日
        - Power BI 報表伺服器初始版本

- **Power BI Desktop (針對 Power BI 報表伺服器最佳化)**
    - 版本：2.47.4766.4901 (2017 年 6 月)，發行日期：2018 年 1 月 10 日
        - 安全性更新

## <a name="next-steps"></a>後續步驟

[什麼是 Power BI 報表伺服器？](get-started.md)
[管理員概觀](admin-handbook-overview.md)  
[安裝 Power BI 報表伺服器](install-report-server.md)  
[安裝報表產生器](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[下載 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
