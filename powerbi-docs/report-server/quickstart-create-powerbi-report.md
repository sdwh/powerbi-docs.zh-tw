---
title: 建立 Power BI 報表伺服器的 Power BI 報表
description: 了解如何透過一些簡單步驟，建立 Power BI 報表伺服器的 Power BI 報表。
services: powerbi
documentationcenter: ''
author: maggiesMSFT
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 3/22/2018
ms.author: maggies
ms.openlocfilehash: 4d860c9d18d1053b6c6cff55be2735eea6e86703
ms.sourcegitcommit: 493f160d04ed411ff4741c599adc63ba1f65230f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33814281"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>建立 Power BI 報表伺服器的 Power BI 報表
您可在 Power BI 報表伺服器入口網站儲存和管理內部部署 Power BI 報表，如同您可在 Power BI 服務 (https://powerbi.com)) 中將 Power BI 報表儲存於雲端一樣。 在 Power BI Desktop 中建立和編輯報表，並將其發行至入口網站。 接著您組織的報表讀者就可在瀏覽器，或在行動裝置上的 Power BI 行動裝置應用程式中加以檢視。

![入口網站中的 Power BI 報表](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

以下是快速入門的四個步驟。

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>步驟 1：安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop

如果您已在 Power BI Desktop 中建立 Power BI 報告，就幾乎準備好建立 Power BI 報表伺服器的 Power BI 報告。 建議您安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop 版本，以便確保伺服器和應用程式一律會保持同步。您在同一部電腦上，可以同時有這兩個版本的 Power BI Desktop 。

1. 在報表伺服器 web 入口網站中，選取 [下載] 箭號 > [Power BI Desktop]。

    ![從 Web 入口網站下載 Power BI Desktop](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    或者直接前往 Microsoft 下載中心的 [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=56723) (已針對 Power BI 報表伺服器最佳化 - 2018 年 3 月)。

2. 在 [下載中心] 頁面上，選取 [下載]。

3. 根據您的電腦，選取：

    - **PBIDesktopRS.msi** (32 位元版本) 或

    - **PBIDesktopRS_x64.msi** (64 位元版本)。

4. 下載安裝程式之後，執行 Power BI Desktop (2018 年 3 月) 安裝精靈。

2. 在安裝結束時，請核取 [立即啟動 Power BI Desktop]。
   
    其會自動啟動，一切即就緒。 「Power BI Desktop (2018 年 3 月)」出現在標題列中即表示版本正確。

    ![Power BI Desktop 2018 年 3 月版本](media/quickstart-create-powerbi-report/report-server-desktop-march-2018.png)

3. 如果您不熟悉 Power BI Desktop，請考慮觀看歡迎畫面上的影片。
   
    ![Power BI Desktop 開始畫面](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>步驟 2︰選取資料來源
您可以連線到各式各樣的資料來源。 閱讀更多[連接至資料來源](connect-data-sources.md)。

1. 在歡迎畫面上，選取 [取得資料]。
   
    或是在 [首頁] 索引標籤上，選取 [取得資料]。
2. 選取您的資料來源 -- 在此範例中為 **Analysis Services**。
   
    ![選取資料來源](media/quickstart-create-powerbi-report/report-server-get-data-ssas.png)
3. 填寫 [伺服器]，並選擇性地填寫 [資料庫]。 確定已選取 [即時連接] > [確定]。
   
    ![伺服器名稱](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. 選擇您將在其中儲存報表的報表伺服器。
   
    ![報表伺服器選取項目](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>步驟 3︰設計報表
以下是有趣的部分︰您可以建立視覺效果來說明您的資料。

比方說，您可以依據年收入建立客戶和群組值的漏斗圖。

![設計報表](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. 在 [視覺效果] 中，選取 [漏斗圖]。
2. 將要計算的欄位拖曳至 [值]。 如果不是數值欄位，Power BI Desktop 會自動將其轉為「計數」值。
3. 將要分組的欄位拖曳至 [群組]。

閱讀更多有關[設計 Power BI 報表](../desktop-report-view.md)的內容。

## <a name="step-4-save-your-report-to-the-report-server"></a>步驟 4︰將報表儲存至報表伺服器
當您的報表就緒時，就將其儲存到您在步驟 2 中選擇的 Power BI 報表伺服器。

1. 在 [檔案] 功能表上，選取 [另存新檔] > [Power BI 報表伺服器]。
   
    ![儲存到報表伺服器](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. 現在您可以在入口網站中加以檢視。
   
    ![在入口網站中檢視報表](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

## <a name="considerations-and-limitations"></a>考量與限制
Power BI 報表伺服器和 Power BI 服務 (http://powerbi.com)) 中的報表行為幾乎完全相同，但部分功能不同。

### <a name="in-a-browser"></a>在瀏覽器中
Power BI 報表伺服器報表支援所有視覺效果，包括：

* 自訂視覺效果

Power BI 報表伺服器報表不支援：

* R 視覺效果
* ArcGIS 地圖
* 階層連結
* Power BI Desktop 預覽功能

### <a name="in-the-power-bi-mobile-apps"></a>在 Power BI 行動裝置應用程式中
Power BI 報表伺服器報表支援 [Power BI 行動裝置應用程式](../mobile-apps-for-mobile-devices.md)中的所有基本功能，包括：

* [手機報表配置](../desktop-create-phone-report.md)：您可以將 Power BI 行動裝置應用程式的報表最佳化。 在您的行動電話上，最佳化的報表會有特殊圖示 ![手機報表配置圖示](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-icon.png) 和配置。
  
    ![專為手機設計的報表](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-report.png)

Power BI 報表伺服器報表不支援 Power BI 行動裝置應用程式中的下列功能：

* R 視覺效果
* ArcGIS 地圖
* 自訂視覺效果
* 階層連結
* 地區篩選或條碼

## <a name="next-steps"></a>後續步驟
### <a name="power-bi-desktop"></a>Power BI Desktop
有許多絕佳的資源可用來在 Power BI Desktop 中建立報表。 此連結是不錯的起點。

* [開始使用 Power BI Desktop](../desktop-getting-started.md)

### <a name="power-bi-report-server"></a>Power BI 報表伺服器
* [安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop](install-powerbi-desktop.md)  
* [Power BI 報表伺服器使用者手冊](user-handbook-overview.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
