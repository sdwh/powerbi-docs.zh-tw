---
title: 使用 Microsoft Teams 的 Power BI 索引標籤內嵌報表
description: 使用 Microsoft Teams 的 Power BI 索引標籤，您可以輕鬆地在頻道和聊天中內嵌互動報表。
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 01/31/2020
ms.openlocfilehash: fb4846a777dda4787e1ed0be7de869367a616ea5
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530479"
---
# <a name="embed-report-with-the-power-bi-tab-for-microsoft-teams"></a>使用 Microsoft Teams 的 Power BI 索引標籤內嵌報表

使用 Microsoft Teams 更新後的 Power BI 索引標籤，您可以輕鬆地在 Microsoft Teams 頻道和聊天中內嵌互動報表。

使用 Microsoft Teams 的 Power BI 標籤，可以協助同事尋找您小組使用的資料，並在小組頻道中討論資料。

## <a name="requirements"></a>需求

若要讓 **Microsoft Teams 的 Power BI 索引標籤**運作，下列為必要項目：

- Power BI Pro 授權，或報表包含在具備 Power BI 授權的 [Power BI Premium Capacity (EM 或 P SKU)](service-premium-what-is.md) 中。
- Microsoft Teams 的 Power BI 索引標籤。
- 使用者必須登入 Power BI 服務，才能啟用 Power BI 授權來取用報表。
- 使用者必須具備檢視報表的權限。

## <a name="embed-your-report"></a>內嵌報表
若要將報表內嵌到 Microsoft Teams 頻道或聊天中，請按照以下方式新增。

1. 在 Microsoft Teams 中開啟所需的頻道或聊天，然後選取 **+** 圖示。

    ![將索引標籤新增到頻道或聊天](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. 選取 Power BI 索引標籤。

    ![顯示 Power BI 的 Microsoft Teams 索引標籤清單](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. 使用提供的選項來從 [工作區]、[與我共用] 或 Power BI 應用程式中挑選報表

    ![Microsoft Teams Power BI 索引標籤設定](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. 索引標籤名稱會自動更新以符合報表名稱的名稱，但您可以變更該名稱。 

5. 按下 [儲存]  。

## <a name="supported-reports"></a>支援的報告

索引標籤會啟用下列報表的內嵌：

- 互動與編頁報表
- [我的工作區] (全新的工作區體驗) 和傳統工作區中的報表
- Power BI 應用程式中的報表


## <a name="grant-access-to-reports"></a>授與報告存取權

在 Microsoft Teams 中內嵌報表不會自動提供使用者檢視報表的權限。您需要[允許使用者檢視 Power BI 中的報表](service-share-dashboards.md)。 您可以針對小組使用 Office 365 群組來讓這項工作變得更加容易。 

> [!IMPORTANT]
> 請務必檢閱可以看到 Power BI 服務內報表的成員，並將存取權授與未列出的成員。

確保小組中所有人皆具備您所內嵌報表存取權限的一種方式是將所有人放置在 Power BI 中單一工作區內，並針對小組提供 Office 365 群組的工作區存取權。

## <a name="known-issues-and-limitations"></a>已知的問題及限制

- Power BI 不支援 Microsoft Teams 支援的相同當地語系化語言。 因此，您可能會在內嵌報表中看到未適當當地語系化的內容。
- Power BI 儀表板無法內嵌在 Microsoft Teams 的 Power BI 索引標籤中。
- 沒有 Power BI 授權或報表權限的使用者會看到「無法使用內容」訊息。
- 您若使用 Internet Explorer 10，可能會遇到問題。 <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Microsoft Teams 的 Power BI 索引標籤不支援 [URL 篩選條件](service-url-filters.md)。
- 在全國性雲端中無法使用新的 Power BI 索引標籤，但可能可以使用不支援全新工作區體驗工作區或 Power BI 應用程式中報表的較舊版本。 
- 儲存索引標籤後，即無法透過索引標籤設定來變更索引標籤名稱。 請使用重新命名選項來進行變更。

## <a name="next-steps"></a>後續步驟
- [Share a dashboard with colleagues and others](service-share-dashboards.md) (與同事和其他人共用儀表板)  
- [在 Power BI 中建立和散發應用程式](service-create-distribute-apps.md)  
- [什麼是 Power BI Premium？](service-premium-what-is.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
