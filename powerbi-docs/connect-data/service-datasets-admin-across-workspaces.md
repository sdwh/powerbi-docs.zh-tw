---
title: 控制跨工作區使用資料集 - Power BI
description: 了解如何限制 Power BI 租用戶中的資訊流程。
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 0caaf46956656c141992482ae39773d19e8fc550
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2020
ms.locfileid: "91374142"
---
# <a name="control-the-use-of-datasets-across-workspaces"></a>控制跨工作區使用資料集

跨工作區使用資料集是在組織內推動資料文化特性和資料民主化的強大方式。 儘管如此，如果您是 Power BI 系統管理員，有時候您想要限制 Power BI 租用戶內的資訊流程。 利用 [跨工作區使用資料集] 這個租用戶設定，您可以完全或部分限制每個安全性群組的資料集重複使用。

![Power BI 系統管理員工作區設定](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

如果您關閉這項設定，以下是對報表建立者造成的影響：

- 跨工作區複製報表的按鈕無法使用。 
- 在根據共用資料集的報表中，[編輯報表] 按鈕無法使用。
- 在 Power BI 服務中，探索體驗只會顯示目前工作區中的資料集。
- 在 Power BI Desktop 中，探索體驗只會顯示您所隸屬工作區中的資料集。
- 在 Power BI Desktop 中，如果使用者開啟 .pbix 檔案，並即時連線至任何所屬工作區之外的資料集，他們會看到一則錯誤訊息，要求他們連接到不同的資料集。

## <a name="provide-a-link-for-the-certification-process"></a>提供認證程序的連結

身為 Power BI 系統管理員，您可在 [背書] 設定頁面上提供 [深入了解] 連結的 URL。  此連結可以移至認證程序的相關文件。 若您沒有為 [深入了解] 連結提供目的地，則根據預設該連結會指向[資料庫認證](service-datasets-certify.md)一文。

![資料集認證深入了解](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>後續步驟

- [跨工作區使用資料集](service-datasets-across-workspaces.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
