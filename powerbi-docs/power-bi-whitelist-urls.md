---
title: Power BI URL
description: 使用 Power BI 的客戶應可連上端點
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 8e29fa0c9471bb865619102247f38776208c3d87
ms.sourcegitcommit: 8990028a348b642ba5c96f001fe3a4280f0166ee
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "40101117"
---
# <a name="power-bi-urls"></a>Power BI URL

**Power BI 線上服務**也稱為 Power BI SaaS (軟體即服務) 應用程式，需要連線到網際網路。 使用 Power BI 線上服務的客戶，應可使用下列端點。

若要使用 Power BI 線上服務，您必須具備連線到下表中標記為**必要**端點的存取權，以及具備在連結網站上標記為**必要**之任一端點的存取權。 若外部網站的連結是某個特定區域，您就只需要檢閱該區段中的端點。

標記為**選擇性**的端點，也可**列入允許清單**，讓特定功能得以運作。

Power BI 線上服務只需要為所列出的端點，開啟 TCP 連接埠 443。

萬用字元 (*) 代表根網域下的所有層級，而當資訊無法使用時，會以 N/A 表示。 **目的地**資料行是提供 FQDN/網域與外部網站連結的清單，包含更詳細的端點資訊。

>[!Important]
>下表中的資訊並不代表**美國政府雲端**、**德國雲端**，以及**中國雲端**。

## <a name="authentication"></a>驗證

Power BI 需要仰賴 Office 365 驗證與身分識別區段中的必要端點。 若要使用 Power BI，必須要可以連線到以下所連結的網站中之端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **必要：** 驗證及身分識別 | 請參閱 Office 365 允許清單網站的 [Office 365 驗證與身分識別區段](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_identity) | N/A |

## <a name="general-site-usage"></a>一般網站使用方式

如需使用 Power BI 的一般用途，必須要可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **必要：** 後端 API | *.analysis.windows.net | TCP 443 |
| 2 | **必要：** Office 365 整合 | 請參閱 Office 365 允許清單網站的 [Office 365 入口網站與共用區段](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) | N/A |
| 3 | **必要：** 入口網站 | app.powerbi.com | TCP 443 |
| 4 | **必要：** 服務遙測 | dc.services.visualstudio.com | TCP 443 |
| 5 | **選擇性：** 資訊訊息 | dynmsg.modpim.com | TCP 443 |
| 6 | **選擇性：** NPS 問卷 | nps.onyx.azure.net | TCP 443 |

## <a name="administration"></a>系統管理

若要在 Power BI 內執行系統管理功能，必須要可連線到以下連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **必要：** 供管理使用者及檢視稽核記錄檔 | 請參閱 Office 365 允許清單網站的 [Office 365 入口網站與共用區段](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) | N/A |

## <a name="get-data"></a>取得資料

若要能從像是 OneDrive 等特定資料來源取得資料，必須要可連線到下表中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **必要：** AppSource (Power BI 中的內部或外部應用程式) | appsource.microsoft.com | TCP 443 |
| 2 | **選擇性：** 從「OneDrive 個人」匯入檔案 | 請參閱 [OneDrive 網站的必要 URL 與連接埠](https://support.office.com/en-ie/article/required-urls-and-ports-for-onedrive-ce15d2cc-52ef-42cd-b738-d9c6f9b03f3a) | N/A |
| 3 | **選擇性：** 60 秒 Power BI 教學課程影片 | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 4 | **選擇性：** PubNub 串流資料來源 | 請參閱 [PubNub 文件](https://support.pubnub.com/support/solutions/articles/14000043522) | N/A |

## <a name="dashboard-and-report-integration"></a>儀表板與報表整合 

Power BI 需要特定端點能夠支援您的儀表板與報表。 您必須可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **必要：** Excel 整合 | 請參閱 Office 365 允許清單網站的 [Office Online 區段](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) | N/A |

## <a name="custom-visuals"></a>自訂視覺效果

Power BI 需要特定端點能夠檢視及存取自訂的視覺效果。 您必須可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **必要：** 從 Marketplace 介面與檔案，匯入自訂視覺效果 | *.microsoft.com </br> *.bing.com </br> *.msecnd.net </br> *.osi.office.net </br> *.azureedge.net </br> ajax.aspnetcdn.com </br> nexus.ensighten.com </br> store.office.com | TCP 443 |
| 2 | **選擇性︰** Bing 地圖服務 | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **選擇性︰** PowerApps | 請參閱 PowerApps 系統需求網站的[必要服務區段](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) | N/A |
| 4 | **選擇性：** Visio | 請參閱 Office 365 允許清單網站的 [Office Online 區段](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) | N/A |