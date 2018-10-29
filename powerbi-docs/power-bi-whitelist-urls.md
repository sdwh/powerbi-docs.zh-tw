---
title: Power BI URL
description: 本文描述使用 Power BI 的客戶應該可連線的端點。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/22/2018
ms.openlocfilehash: cc7b24d273f8e83854f7e316f0c761e710e48160
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641957"
---
# <a name="power-bi-urls"></a>Power BI URL

**Power BI 線上服務**也稱為 Power BI SaaS (軟體即服務) 應用程式，需要連線到網際網路。 使用 Power BI 線上服務的客戶，應可使用下列端點。

若要使用 Power BI 線上服務，您必須具備連線到下表中標記為**必要**端點的存取權，以及具備在連結網站上標記為**必要**之任一端點的存取權。 若外部網站的連結是某個特定區域，您就只需要檢閱該區段中的端點。

標記為**選擇性**的端點，也可**列入允許清單**，讓特定功能得以運作。

Power BI 線上服務只需要為所列出的端點，開啟 TCP 連接埠 443。

萬用字元 (*) 代表根網域下的所有層級，而當資訊無法使用時，會以 N/A 表示。 **目的地**資料行是提供 FQDN/網域與外部網站連結的清單，包含更詳細的端點資訊。

>[!Important]
>下表中的資訊並不代表**美國政府雲端**、**德國雲端**或**中國雲端**。

## <a name="authentication"></a>驗證

Power BI 需要仰賴 Office 365 驗證與身分識別區段中的必要端點。 若要使用 Power BI，必須要可以連線到以下所連結的網站中之端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 驗證及身分識別 | 請參閱 Office 365 文件以了解 [Office Online 和一般 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)  | N/A |

## <a name="general-site-usage"></a>一般網站使用方式

如需使用 Power BI 的一般用途，必須要可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 後端 API | *.analysis.windows.net | TCP 443 |
| 2 | **必要：** Office 365 整合 | 請參閱 Office 365 文件以了解 [Office Online 和一般 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/A |
| 3 | **必要：** 入口網站 | app.powerbi.com | TCP 443 |
| 4 | **必要：** 服務遙測 | dc.services.visualstudio.com | TCP 443 |
| 5 | **選擇性：** 資訊訊息 | dynmsg.modpim.com | TCP 443 |
| 6 | **選擇性：** NPS 問卷 | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>系統管理

若要在 Power BI 內執行系統管理功能，必須要可連線到以下連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 供管理使用者及檢視稽核記錄檔 | 請參閱 Office 365 文件以了解 [Office Online 和一般 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/A |
| | | |

## <a name="getting-data"></a>取得資料

若要從例如 OneDrive 等特定資料來源取得資料，必須要能連線到下表中的端點。 組織內使用的特定資料來源可能需要存取其他網際網路網域和 URL。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** AppSource (Power BI 中的內部或外部應用程式) | appsource.microsoft.com </br> *.s-microsoft.com  | TCP 443 |
| 2 | **必要：** 登入並取得內容套件的資料 | *.github.com  | TCP 443 |
| 3 | **選擇性：** 從「OneDrive 個人」匯入檔案 | 請參閱 [OneDrive 網站的必要 URL 與連接埠](https://docs.microsoft.com/en-us/onedrive/required-urls-and-ports) | N/A |
| 4 | **選擇性：** 60 秒 Power BI 教學課程影片 | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 5 | **選擇性：** PubNub 串流資料來源 | 請參閱 [PubNub 文件](https://support.pubnub.com/support/solutions/articles/14000043522) | N/A |
| | | |

## <a name="dashboard-and-report-integration"></a>儀表板與報表整合

Power BI 需要特定端點能夠支援您的儀表板與報表。 您必須可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** Excel 整合 | 請參閱 Office 365 文件以了解 [Office Online 和一般 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) | N/A |
| | | |

## <a name="custom-visuals"></a>自訂視覺效果

Power BI 需要特定端點能夠檢視及存取自訂的視覺效果。 您必須可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 從 Marketplace 介面或檔案匯入自訂視覺效果 | *.azureedge.net </br> *.blob.core.windows.net </br> store.office.com | TCP 443 |
| 2 | **選擇性︰** Bing 地圖服務 | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **選擇性︰** PowerApps | 請參閱 PowerApps 系統需求網站的[必要服務區段](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) | N/A |
| 4 | **選擇性：** Visio | 請參閱 Office 365 文件以了解 [Office Online 和一般 URL](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online)，以及 [SharePoint Online 和商務用 OneDrive](https://docs.microsoft.com/en-us/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) | N/A |
| | | |

## <a name="related-external-sites"></a>相關的外部網站

Power BI 連結至其他相關網站。 這些網站包括文件、支援、新的功能要求等網站。 這些網站不會影響 Power BI 的功能，因此如有需要，可以選擇性地列入允許清單中。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **選擇性：** 社群網站 | community.powerbi.com </br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **選擇性：** 文件網站 | docs.microsoft.com </br> img-prod-cms-rt-microsoft-com.akamaized.net </br> statics-uhf-eas.akamaized.net </br> cdnssl.clicktale.neting-district.clicktale.net | TCP 443 |
| 3 | **選擇性：** 下載網站 (適用於 Power BI Desktop 等) | download.microsoft.com | TCP 443 |
| 4 | **選擇性：** 外部重新導向 | aka.ms </br> go.microsoft.com | TCP 443 |
| 5 | **選擇性：** 想法的意見反應網站| ideas.powerbi.com </br> powerbi.uservoice.com | TCP 443 |
| 6 | **選擇性：** Power BI 網站，包含登陸頁面、深入了解連結、支援網站、下載連結、合作夥伴展示工具等。 | powerbi.microsoft.com | TCP 443 |
| 7 | **選擇性：** Power BI 開發人員中心 | dev.powerbi.com | TCP 443 |
| 8 | **選擇性：** 支援網站 | support.powerbi.com </br> s3.amazonaws.com </br> *.olark.com </br> logx.optimizely.com </br> mscom.demdex.net </br> tags.tiqcdn.com | TCP 443 |
| | | |