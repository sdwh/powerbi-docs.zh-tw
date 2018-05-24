---
title: 建立 Power BI 行動裝置應用程式中的特定位置連結
description: 了解如何使用統一資源識別項 (URI)，建立 Power BI 行動裝置應用程式中特定儀表板、磚或報表的深層連結。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 3be6882219e23a2d22ee03e6805ce3a1e8e08b8f
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>建立 Power BI 行動裝置應用程式中的特定位置連結
您可以建立和使用統一資源識別項 (URI)，以連結至所有行動平台 (iOS、Android 裝置和 Windows 10) 上之 Power BI 行動裝置應用程式內的特定位置 (「深層連結」)。

URI 連結可以直接指向儀表板、磚和報表。

深層連結的目的地決定 URI 的格式。 請遵循下列步驟來建立不同位置的深層連結。 

## <a name="open-the-power-bi-mobile-app"></a>開啟 Power BI 行動裝置應用程式
在任何裝置上，使用此 URI 開啟 Power BI 行動裝置應用程式：

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>開啟至特定儀表板
此 URI 會將 Power BI 行動裝置應用程式開啟至特定儀表板：

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

若要尋找 36 個字元的儀表板物件識別碼，請巡覽至 Power BI 服務 (https://powerbi.com) 中的特定儀表板。 例如，查看此 URL 的強調顯示區段：

https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**

如果儀表板位於 [我的工作區] 以外的群組中，請在儀表板識別碼前面或後面加上 `&GroupObjectId=<36-character-group-id>`。 例如： 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

請注意兩者之間的 & 符號。

## <a name="open-to-a-specific-tile-in-focus"></a>以焦點模式開啟至特定磚
此 URI 會在 Power BI 行動裝置應用程式中，以焦點模式開啟特定磚：

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

若要尋找 36 個字元的儀表板和磚物件識別碼，請巡覽至 Power BI 服務 (https://powerbi.com) 中的特定儀表板，然後以焦點模式開啟此磚。 例如，查看此 URL 的強調顯示區段：

https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

此磚的 URI 會是：

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

請注意兩者之間的 & 符號。

如果儀表板位於 [我的工作區] 以外的群組中，請加入 `&GroupObjectId=<36-character-group-id>`

## <a name="open-to-a-specific-report"></a>開啟至特定報表
此 URI 會在 Power BI 行動裝置應用程式中，開啟特定報表：

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

若要尋找 36 個字元的報表物件識別碼，請巡覽至 Power BI 服務 (https://powerbi.com) 中的特定報表。 例如，查看此 URL 的強調顯示區段：

https://powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

## <a name="open-to-a-specific-report-page"></a>開啟至特定報表頁面
此 URI 會在 Power BI 行動裝置應用程式中，開啟特定報表頁面：

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

此報表頁面稱為 "ReportSection"，後面接著一個數字。 同樣地，在 Power BI 服務 (https://powerbi.com) 中開啟報表，然後巡覽至特定報表頁面。 

例如，查看此 URL 的強調顯示區段：

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**ReportSection11**

## <a name="open-in-full-screen-mode"></a>以全螢幕模式開啟
以粗體新增參數以在全螢幕模式中開啟特定的報表︰

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

例如： 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>新增內容 (選擇性)
您也可以在字串中新增內容。 然後，如果您需要與我們連絡，我們可以使用該內容在您的應用程式中篩選出我們的資料。 將 `&context=<app-name>` 新增至連結

例如，查看此 URL 的強調顯示區段： 

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**&context=SlackDeepLink**

## <a name="next-steps"></a>後續步驟
您的意見反應可協助我們決定要在未來實作的項目，因此別忘了對您想在 Power BI 行動應用程式中看到的其他功能進行投票。 

* [行動裝置的 Power BI 應用程式](mobile-apps-for-mobile-devices.md)
* 請在 Twitter 上關注 @MSPowerBI
* 加入 [Power BI 社群](http://community.powerbi.com/)的交談
* [開始使用 Power BI](service-get-started.md)

