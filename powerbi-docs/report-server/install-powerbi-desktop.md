---
title: 安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop
description: 了解如何安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop
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
ms.date: 03/19/2018
ms.author: maggies
ms.openlocfilehash: 9951137ac10752a39f0e4ad555a36e2935faf327
ms.sourcegitcommit: 93e7362fc47319959b6992dfd037effdf831d010
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2018
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop
了解如何安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop。

若要建立 Power BI 報表伺服器的 Power BI 報告，您必須下載並安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop。 此版本與搭配 Power BI 服務使用的 Power BI Desktop 不同。 例如，Power BI 服務的 Power BI Desktop 版本包含已發行的 Power BI 報表伺服器版本中所提供的預覽功能。 使用此版本可確保報表伺服器可與已知版本的報告和模型互動。 

好消息是，您可以將 Power BI Desktop 和針對 Power BI 報表伺服器最佳化的 Power BI Desktop 並排安裝在相同電腦上。

## <a name="download-and-install-power-bi-desktop"></a>下載及安裝 Power BI Desktop

要確定您所擁有的針對 Power BI 報表伺服器最佳化之最新版 Power BI Desktop 最簡單的方式，是從報表伺服器的 web 入口網站開始。

1. 在報表伺服器 web 入口網站中，選取 [下載] 箭號 > [Power BI Desktop]。

    ![從 Web 入口網站下載 Power BI Desktop](media/install-powerbi-desktop/report-server-download-web-portal.png)

    或者您可以直接移至 Microsoft 下載中心的 [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=56723) (已針對 Power BI 報表伺服器最佳化 - 2018 年 3 月)。

2. 在 [下載中心] 頁面上，選取 [下載]。

3. 根據您的電腦，選取： 

    - **PBIDesktopRS.msi** (32 位元版本) 或

    - **PBIDesktopRS_x64.msi** (64 位元版本)。

1. 下載安裝程式之後，執行 Power BI Desktop (2017 年 10 月) 安裝精靈。
2. 在安裝結束時，請核取 [立即啟動 Power BI Desktop]。
   
    其會自動啟動，一切即就緒。

## <a name="verify-you-are-using-the-correct-version"></a>驗證您使用正確的版本
您可透過，驗證使用正確的 Power BI Desktop。查看 Power BI Desktop 內的啟動螢幕或標題列。 標題列會指出版本的發行年份和月份。

![針對 Power BI 報表伺服器最佳化的 Power BI Desktop 標題列](media/quickstart-create-powerbi-report/report-server-desktop-october-2017-version.png)

Power BI 服務的 Power BI Desktop 版本不會在標題列中顯示年份和月份。

## <a name="file-extension-association"></a>副檔名關聯
如果在同一部電腦上，同時安裝 Power BI Desktop 和針對 Power BI 報表伺服器最佳化的 Power BI Desktop，最後一個安裝之 Power BI Desktop 的檔案關聯為 .pbix。 這表示當您按兩下 pbix 檔案時，便會啟動上次安裝的 Power BI Desktop。

如果您已有 Power BI Desktop，並接著安裝針對 Power BI 報表伺服器最佳化的 Power BI Desktop，則所有 pbix 檔案都預設在後者中開啟。 如果您偏好在開啟 pbix 檔案時預設啟動 Power BI Desktop，請從 Power BI 服務重新安裝 Power BI Desktop。

您隨時可以開啟您想要先用的 Power BI Desktop 版本， 然後再從 Power BI Desktop 中開啟檔案。

無論是從 Power BI 報表伺服器內編輯 Power BI 報表，還是從入口網站建立新的 Power BI 報表，都一律會開啟正確的 Power BI Destop 版本。

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

## <a name="power-bi-desktop-for-earlier-versions-of-power-bi-report-server"></a>適用於舊版 Power BI 報表伺服器的 Power BI Desktop

如果您的報表伺服器是舊版，則需要 Power BI Desktop 的對應版本。 以下是兩個舊版。

- Microsoft Power BI Desktop ([已針對 Power BI 報表伺服器最佳化 - 2017 年 10 月](https://www.microsoft.com/download/details.aspx?id=56136))
- Microsoft Power BI Desktop ([已針對 Power BI 報表伺服器最佳化 - 2017 年 6 月](https://www.microsoft.com/download/details.aspx?id=55330))

## <a name="next-steps"></a>後續步驟
現在您已安裝 Power BI Desktop，即可開始建立 Power BI 報表。

[快速入門︰建立 Power BI 報表伺服器的 Power BI 報表](quickstart-create-powerbi-report.md)  
[開始使用 Power BI Desktop](../desktop-getting-started.md)  
引導式學習︰[開始使用 Power BI Desktop](../guided-learning/gettingdata.yml#step-2)  
[使用者手冊概觀, Power BI 報表伺服器](user-handbook-overview.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

