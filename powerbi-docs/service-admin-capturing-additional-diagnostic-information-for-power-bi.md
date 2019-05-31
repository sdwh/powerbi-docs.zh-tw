---
title: 擷取其他診斷資訊
description: 這些指示提供兩個可能的選項，以從 Power BI Web 用戶端手動收集其他診斷資訊。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100151"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>擷取 Power BI 的其他診斷資訊

本文章提供有關手動從 Power BI web 用戶端收集其他診斷資訊的指示。

1. 瀏覽至[Power BI](https://app.powerbi.com)與 Microsoft Edge 或 Internet Explorer。

1. 按下**F12**開啟 Microsoft Edge 開發人員工具。

   ![螢幕擷取畫面的 Microsoft Edge 開發人員工具項目 索引標籤。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. 切換至 [網路]  索引標籤。其中列出已經擷取的流量。

   ![螢幕擷取畫面的 Microsoft Edge 開發人員工具網路 索引標籤。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    您可以：

    * 瀏覽 視窗中，並重現可能遇到任何問題。

    * 隱藏和顯示開發人員工具 視窗中工作階段期間，隨時按 F12。

1. 若要停止分析工作階段，您可以在選取紅色方形**網路**] 索引標籤的 [開發人員工具區域。

   ![螢幕擷取畫面的 Microsoft Edge 開發人員工具網路 索引標籤的呼叫，從 停止 按鈕。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. 選取磁碟片圖示，將資料匯出為 HTTP 封存 (HAR) 檔案。

   ![螢幕擷取畫面的 Microsoft Edge 開發人員工具網路 索引標籤包含的磁碟片圖示的圖說文字。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. 提供檔案名稱並儲存 HAR 檔案。

    HAR 檔案會包含瀏覽器視窗與包括 Power BI 之間網路要求的所有資訊：

    * 每個要求活動識別碼。

    * 針對每個要求的精確時間戳記。

    * 任何錯誤訊息傳回至用戶端。

    這項追蹤也會包含用來填入畫面上所示視覺效果的資料。

1. 您可以提供 HAR 檔案以支援檢閱。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
