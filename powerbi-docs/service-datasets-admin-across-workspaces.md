---
title: 控制跨工作區的資料集使用 (預覽) - Power BI
description: 了解如何限制 Power BI 租用戶中的資訊流程。
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d1ad29bebc148d9f30e8d22240dd149787251a0a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872571"
---
# <a name="control-the-use-of-datasets-across-workspaces-preview"></a>控制跨工作區的資料集使用 (預覽)

跨工作區使用資料集是在組織內推動資料文化特性和資料民主化的強大方式。 儘管如此，如果您是 Power BI 系統管理員，有時候您想要限制 Power BI 租用戶內的資訊流程。 利用 [跨工作區使用資料集]  這個租用戶設定，您可以完全或部分限制每個安全性群組的資料集重複使用。

![Power BI 系統管理員工作區設定](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

如果您關閉這項設定，以下是對報表建立者造成的影響：

- 跨工作區複製報表的按鈕無法使用。 
- 在根據共用資料集的報表中，[編輯報表]  按鈕無法使用。
- 在 Power BI 服務中，探索體驗只會顯示目前工作區中的資料集。
- 在 Power BI Desktop 中，探索體驗只會顯示您所隸屬工作區中的資料集。
- 在 Power BI Desktop 中，如果使用者開啟 .pbix 檔案，並即時連線至任何所屬工作區之外的資料集，他們會看到一則錯誤訊息，要求他們連接到不同的資料集。

## <a name="provide-a-link-for-the-certification-process"></a>提供認證程序的連結

您身為租用戶系統管理員，可以在 [簽署]  設定頁面上提供 [深入了解]  連結的 URL。  此連結可以移至認證程序的相關文件。 若您沒有為 [深入了解]  連結提供目的地，則根據預設該連結會指向[資料庫認證](service-datasets-certify.md)一文。

![資料集認證深入了解](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>後續步驟

- [跨工作區使用資料集 (預覽)](service-datasets-across-workspaces.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
