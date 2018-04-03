---
title: Power BI 和 ExpressRoute
description: Power BI 和 ExpressRoute
services: powerbi
documentationcenter: ''
author: davidiseminger
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
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Administration
ms.openlocfilehash: faf438e9f76a7a929f7369dc91ef4edb4fbef42d
ms.sourcegitcommit: 1fe3ababba34c4e7aea08adb347ec5430e0b38e4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="power-bi-and-expressroute"></a>Power BI 和 ExpressRoute
透過 **Power BI** 和 **ExpressRoute**，您可以建立從組織到 Power BI (或使用 ISP 設備代管) 的私人網路連線，藉由略過網際網路，更妥善地保護您的 Power BI 機密資料和連線。

**ExpressRoute** 是 Azure 服務，可讓您在 Azure 資料中心 (Power BI 的所在位置) 與內部部署基礎結構之間建立私人連線，或在 Azure 資料中心與代管環境之間建立私人連線。

![](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)

您可以取得 [ExpressRoute 的詳細資訊](https://azure.microsoft.com/services/expressroute/)，或了解[如何註冊](https://azure.microsoft.com/pricing/details/expressroute/)。

> [!NOTE]
> 公用對等互連模式支援 Power BI，如[這份常見問題集](https://docs.microsoft.com/azure/expressroute/expressroute-faqs)所述。
> 
> 

## <a name="power-bi-expressroute-exceptions"></a>Power BI ExpressRoute 例外狀況
Power BI 符合 ExpressRoute 規範，但在某些例外狀況下，Power BI 會透過公用網際網路取得或傳送資料。 這些特定的例外狀況通常包括靜態資料，例如從最近的**內容傳遞網路 (CDN)** 節點下載的瀏覽器組態檔。 除了一些適用於所有 Power BI 的廣泛例外狀況之外，還有幾種服務或功能特定的例外狀況，以下各節將個別加以說明。

### <a name="overall-exceptions-to-power-bi-and-expressroute"></a>Power BI 和 ExpressRoute 的整體例外狀況
**Power BI** 和 **ExpressRoute** 的例外狀況是指透過公用網際網路從 Power BI 傳輸資料或將資料傳輸到 Power BI，而不是透過私人 ExpressRoute 連結傳輸。

Power BI 使用 ExpressRoute 時的兩種整體例外狀況為：

* 從**內容傳遞網路 (CDN)** 和網站下載的靜態檔案
* 透過公用網際網路傳送的**遙測**資料

Power BI 使用多個**內容傳遞網路 (CDN)** 或網站，以透過公用網際網路，根據地區設定有效率地將必要靜態內容和檔案散發給使用者。 這些靜態檔案包括產品下載 (例如 **Power BI Desktop**、**內部部署資料閘道** 或來自不同獨立服務提供者的 **Power BI 內容套件**)、用來起始及建立任何 Power BI 後續連線的瀏覽器設定檔，以及初始的安全 Power BI 登入頁面 (實際認證只會透過 ExpressRoute 傳送)。   

特定**遙測資料**也會透過公用網際網路和 ExpressRoute 傳送。 這些遙測資料包括使用量統計資料和類似的資料，會傳輸到用來監視使用量和活動的服務。

### <a name="power-bi-saas-application-and-expressroute"></a>Power BI SaaS 應用程式和 ExpressRoute
當使用者啟動 Power BI 服務的連線時 (powerbi.com 或透過 Cortana)，會從透過公用網際網路連線的 CDN 或網站擷取 Power BI 登陸頁面、登入頁面和靜態檔案，讓瀏覽器準備好連線到 Power BI 並與其互動。

一旦建立登入，後續的 Power BI 資料互動會透過 ExpressRoute 進行，但不包括相依於公用網際網路資料的特定功能和服務：

* **地圖視覺效果**需要連線並將資料傳輸到 Bing Virtual Earth 服務或 Bing 地理編碼服務，其中各項都是透過公用網際網路建立。
* Power BI 與 **Cortana** 的整合需要透過公用網際網路存取 Bing。
* 當使用者新增**自訂連結**時 (例如影像 Widget 或視訊)，Power BI 會根據使用者提供的連結來要求資料，而此連結不一定會使用 ExpressRoute。
* 使用者可以透過 User Voice 意見反應機制以文字 (或影像) 傳送**意見反應給 Power BI**，該機制使用公用網際網路進行傳輸。
* **Bing 新聞內容提供者**使用公用網際網路從 Bing 下載內容。
* 當連接到 **應用程式** (例如內容套件) 時，使用者通常必須使用 SaaS 提供者提供的頁面輸入認證和設定。 這類頁面不一定會使用 ExpressRoute。

| 使用者活動 | 目的地 |
| --- | --- |
| 登陸頁面 (登入前) |`maxcdn.bootstrapcdn.com ; ajax.aspnetcdn.com ; netdna.bootstrapcdn.com ; cdn.optimizely.com; google-analytics.com ` |
| 登入 |`*.mktoresp.com ; *.aadcdn.microsoftonline-p.com ; *.msecnd.com ; *.localytics.com ; ajax.aspnetcdn.com` |
| 儀表板、報表、資料集管理 (包括地圖和地理編碼) |`*.localytics.com ; *.virtualearth.net ; platform.bing.com; powerbi.microsoft.com; c.microsoft.com; app.powerbi.com; *.powerbi.com; dc.services.visualstudio.com ` |
| 支援 |`support.powerbi.com ; powerbi.uservoice.com ; go.microsoft.com ` |

### <a name="power-bi-desktop-and-expressroute"></a>Power BI Desktop 和 ExpressRoute
Power BI Desktop 也符合 ExpressRoute 規範，但有一些下列清單所述的例外狀況︰

* 用來偵測使用者是否有最新版 Power BI Desktop 的**更新通知**是透過公用網際網路傳送。
* 特定**遙測資料**是透過公用網際網路傳送。
* **地圖視覺效果**需要連線並將資料傳輸到 **Bing Virtual Earth** 服務或 **Bing 地理編碼**服務，其中各項都是透過公用網際網路建立。
* 從**網路**或協力廠商 SaaS 提供者等資料來源**取得資料**是透過公用網際網路進行。

### <a name="power-bi-paas-and-expressroute"></a>Power BI PaaS 和 ExpressRoute
Power BI 提供以 API 和其他平台為基礎的功能，讓開發人員可以建立自訂的 Power BI 解決方案和應用程式。 除了本主題先前所述的遙測和 CDN 資料之外，當透過公用網際網路傳輸 Power BI PaaS 資料時，會使用下列服務︰

| PaaS 活動 | 其他使用的目的地 |
| --- | --- |
| 公用內嵌 (遙測) |`c1.microsoft.com` |
| 自訂視覺效果 (CDN) |`*.azureedge.net` |

有些**自訂視覺效果**是由協力廠商建立，有些則是由 Microsoft 建立。 這些視覺效果不一定會使用 ExpressRoute。

### <a name="power-bi-mobile-and-expressroute"></a>Power BI Mobile 和 ExpressRoute
本文件並未涵蓋 Power BI Mobile 應用程式的使用。  

### <a name="on-premises-data-gateway-and-expressroute"></a>內部部署資料閘道與 ExpressRoute
當**內部部署資料閘道**搭配 Power BI 使用時，傳輸符合 ExpressRoute 規範，但不包括本主題稍早 **Power BI SaaS 應用程式和 ExpressRoute** 一節中所述的使用者活動。  

