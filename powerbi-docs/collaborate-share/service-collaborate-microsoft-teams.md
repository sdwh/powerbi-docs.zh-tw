---
title: 在 Microsoft Teams 中使用 Power BI 共同作業
description: 您可輕鬆地與 Microsoft Teams 頻道和聊天室中的互動式 Power BI 內容共用和共同作業。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 17a0879dac416a98d214ed11861947cb2c311487
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87253883"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>在 Microsoft Teams 中使用 Power BI 共同作業

您有數個選項可與 Microsoft Teams 頻道和聊天室中的互動式 Power BI 內容共用和共同作業。 

- 使用 Microsoft Teams 的 [Power BI] 索引標籤，即可[在 Microsoft Teams 頻道和聊天中內嵌互動式報表](service-embed-report-microsoft-teams.md)。 [Power BI] 索引標籤可協助同事尋找小組資料，並討論小組頻道內的資料。 
- 當將報表、儀表板和應用程式的連結貼到 Microsoft Teams 訊息方塊時，請建立[連結預覽](service-teams-link-preview.md)。 連結預覽會顯示連結的相關資訊。 
- 在 Power BI 服務中檢視報表和儀表板時，使用 [共用至 Teams](service-share-report-teams.md)，即可在小組中快速開始交談。
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="內嵌在 Teams 頻道中的 Power B I 報表螢幕擷取畫面。":::

## <a name="requirements"></a>需求

一般而言，若要讓 Power BI 在 Microsoft Teams 中工作，請確定下列項目：

- 您擁有 Power BI Pro 授權，或報表包含於具備 Power BI 授權的 [Power BI Premium 容量 (EM 或 P SKU)](../admin/service-premium-what-is.md) 中。
- 使用者必須登入 Power BI 服務，才能啟用 Power BI 授權。
- 使用者符合使用 Microsoft Teams 中 [Power BI] 索引標籤的需求。

若要使用 Microsoft Teams 中的 [Power BI] 索引標籤，請確定下列項目：

- Microsoft Teams 具有 [Power BI] 索引標籤。
- 若要在具備 [Power BI] 索引標籤的 Microsoft Teams 中新增報表，則在裝載報表的工作區中至少必須具備「檢閱者」角色。 如需不同角色的相關資訊，請參閱[新工作區中的角色](service-new-workspaces.md#roles-in-the-new-workspaces)。
- 若要在 Microsoft Teams 的 [Power BI] 索引標籤中查看報表，使用者必須具備檢視報表的權限。
- 使用者必須是有權存取頻道和聊天的 Microsoft Teams 使用者。

若要在 Power BI 中使用 [共用至 Teams] 功能，請確定此設定：

- Power BI 系統管理員尚未停用 Power BI 系統管理員入口網站中的 [共用至 Teams] 租用戶設定。 此設定可供組織隱藏 [共用至 Teams] 按鈕。 如需詳細資料，請參閱 [Power BI 管理入口網站](../admin/service-admin-portal.md#share-to-teams-tenant-setting)一文。

## <a name="grant-access-to-reports"></a>授與報告存取權

在 Microsoft Teams 中內嵌報表，或傳送項目的連結，不會自動為使用者授與檢視報表的權限。 您需要[允許使用者檢視 Power BI 中的報表](service-share-dashboards.md)。 您可以為小組使用 Microsoft 365 群組，讓此過程變得更簡單。

> [!IMPORTANT]
> 請務必檢閱可以看到 Power BI 服務內報表的成員，並將存取權授與未列出的成員。

確保小組中每位成員都有權存取報表的方式之一是將報表放在單一工作區中，並為小組授與 Microsoft 365 群組的存取權。

## <a name="known-issues-and-limitations"></a>已知的問題及限制

- Power BI 不支援 Microsoft Teams 所支援的相同當地語系化語言。 因此，您可能不會在內嵌報表中看到適當的當地語系化。
- Power BI 儀表板無法內嵌於 Microsoft Teams 的 [Power BI] 索引標籤中。
- 沒有 Power BI 授權或存取報表權限的使用者會看到「內容無法使用」訊息。
- 如果您使用 Internet Explorer 10，可能就會遇到問題。 <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Microsoft Teams 的 [Power BI] 索引標籤不支援 [URL 篩選](service-url-filters.md)。
- 在國家雲端中，無法使用新的 [Power BI] 索引標籤。 較舊的版本可能無法在 Power BI 應用程式中支援全新的工作區體驗或報表。
- 儲存索引標籤之後，即無法透過索引標籤設定來變更索引標籤名稱。 請使用 [重新命名] 選項加以變更。
- 連結預覽服務不支援單一登入。
- 連結預覽在會議聊天或私人頻道中無法使用。

## <a name="next-steps"></a>後續步驟

- [在 Microsoft Teams 中內嵌 Power BI 內容](service-embed-report-microsoft-teams.md)
- [在 Microsoft Teams 中取得 Power BI 連結預覽](service-teams-link-preview.md)
- [從 Power BI 服務直接共用到 Teams](service-share-report-teams.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)。
