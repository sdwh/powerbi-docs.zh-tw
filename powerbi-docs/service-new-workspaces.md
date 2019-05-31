---
title: 組織在新的工作區-Power BI 中的工作
description: 深入了解新的工作區，也就是儀表板和報表，為了提供重要計量給組織而建立的集合。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9f5dfaa5a23ae46fef131a52355531b5fbde3051
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100700"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>組織中新的工作區，在 Power BI 中的工作

 *工作區*個位置中建立集合的儀表板、 報表和編頁的報表的同事共同作業。 新的工作區體驗可協助您更妥善管理內容的存取權。 本文說明新的工作區，以及它們之間的差異，從傳統的工作區。  因為與傳統的工作區，您仍然使用它們來建立和散發應用程式。 了解如何[建立新的工作區體驗](service-create-the-new-workspaces.md)。

新的工作區體驗已公開上市 (GA)，而且現在預設工作區。 您仍然可以繼續建立並使用[傳統的工作區](service-create-workspaces.md)根據 Office 365 群組。 

> [!NOTE]
> 若要強制執行瀏覽工作區中的內容的 Power BI Pro 使用者的資料列層級安全性 (RLS)，請繼續使用[傳統的工作區](service-create-workspaces.md)。 選取 **成員只能檢視 Power BI 內容**選項。 或者，將 Power BI 應用程式發行給這些使用者，或使用 「 共用 」 來發佈內容。 即將推出的檢視器角色將會啟用此案例在未來，新的工作區體驗工作區中。

使用新的工作區中，您可以：

- 將工作區角色指派給使用者群組：安全性群組、通訊群組清單、Office 365 群組，以及個人。
- 在 Power BI 中建立工作區，而不建立 Office 365 群組。
- 使用更精細的工作區角色，在工作區中進行更有彈性的權限管理。

當您建立其中一個新工作區時，不會建立基礎的相關聯 Office 365 群組。 所有工作區管理都是在 Power BI 中進行，而不是 Office 365。 在新的工作區體驗中，您現在可以新增工作區存取清單中的 Office 365 群組，繼續管理使用者存取透過 Office 365 群組的內容。

## <a name="administering-new-workspace-experience-workspaces"></a>管理新的工作區體驗工作區
新的工作區體驗工作區的系統管理現在是在 Power BI，Power BI 系統管理員決定組織內誰可以建立工作區。 它們也可以管理和復原工作區。 若要這樣做需要使用 Power BI 管理入口網站或 PowerShell Cmdlet。 Office 365 群組為基礎的傳統工作區，系統管理 會繼續出現在 Office 365 系統管理入口網站和 Azure Active Directory。

在 **工作區設定**中系統管理員入口網站中，管理員可以使用設定來允許每個人或沒有人在組織中建立工作區 （新工作區體驗） 來建立新的工作區體驗工作區。 他們也可以限制只有特定安全性群組的成員才能建立。

> [!NOTE]
> 設定為只允許使用者可以建立 Office 365 群組，以在 Power BI 中建立新的工作區的預設值建立工作區 （新工作區體驗）。 請務必設定 Power BI 管理入口網站，以確保適當的使用者可以建立新的工作區體驗工作區中的值。

![管理入口網站中的 [工作區設定]](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

[工作區清單](service-admin-portal.md#workspaces)Power BI 管理入口網站中。 

![工作區清單](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>新的工作區以並排方式與傳統的工作區

新的升級工作區，與傳統的現有工作區並排顯示，有共存，您可以建立。 新的工作區體驗是預設工作區類型。 Power BI 會繼續列出所有的 Office 365 群組，使用者會在 Power BI，以避免變更現有的工作流程中的成員。 若要了解如何建立新的工作區，請閱讀[建立新的工作區](service-create-the-new-workspaces.md)。 若要了解如何建立傳統的工作區，請閱讀[建立傳統的工作區](service-create-workspaces.md)。

## <a name="roles-in-the-new-workspaces"></a>新工作區中的角色

若要授與新的工作區的存取，新增至其中一個工作區角色的使用者群組或個人： 成員、 參與者或系統管理員。 使用者群組中的每個人都會取得您已定義的角色。 如果個人在數個使用者群組，他們會取得最高層級的角色指派所提供的權限。

角色可讓您管理誰可以在工作區中做什麼，因此小組可以共同作業。 新的工作區可讓您將角色指派給個人和使用者群組：安全性群組、Office 365 群組，以及通訊群組清單。 

當您將角色指派給使用者群組時，群組中的個人可以存取內容。 如果巢狀處理使用者群組，則所有包含的使用者都具有權限。 在數個使用者群組中具有不同角色的使用者，會獲得授與他們的最高層級權限。 

新的工作區提供三種角色：系統管理員、成員和參與者。

|功能   | 系統管理員  | 成員  | 參與者  | 
|---|---|---|---|
| 更新和刪除工作區。  | X  |   |   |
| 新增/移除人員，包括其他系統管理員。  | X  |   |   |
| 新增具有較低權限的成員或其他人。  |  X | X  |   |
| 發佈和更新應用程式。 |  X | X  |   |
| 共用項目或共用應用程式。 |  X | X  |   |
| 允許其他人再次共用項目。 |  X | X  |   |
| 建立、編輯和刪除工作區中的內容。  |  X | X  | X  |
| 將報表發佈至工作區、刪除內容。 |  X | X  | X  |
 
 
## <a name="licensing"></a>授權
新增至工作區的每個人都必須有 Power BI Pro 授權。 在工作區中，這些使用者皆可在儀表板和報表上共同作業，以準備發佈給更多對象，甚至整個組織。 如果您想要將內容散發給組織內的其他人，則可以將 Power BI Pro 授權指派給這些使用者，或將工作區置於 Power BI Premium 容量中。

> [!NOTE]
> 將報表發行至新的工作區體驗有更嚴格強制執行現有的授權規則。 嘗試發行從 Power BI Desktop 或其他用戶端工具，而不需要 Pro 授權的使用者會看到錯誤 「 只有具備 Power BI Pro 授權的使用者可以發佈到此工作區 」。

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>新工作區與目前工作區有何不同？

我們使用新的工作區重新設計了一些功能。 以下是您可以預期是永久的變更。 

* 建立這些工作區不會建立 Office 365 群組，例如傳統的工作區不同。 不過，您現在可以使用 Office 365 群組，讓使用者存取您的工作區將它指派角色。 
* 在傳統的工作區，您可以加入只個人的成員和系統管理員清單。 在新的工作區中，您可以將多個 AD 安全性群組、通訊群組清單或 Office 365 群組新增至這些清單，以便能夠更輕鬆地進行使用者管理。 
- 您可以從傳統的工作區中建立組織內容套件。 但無法從新的工作區建立組織內容套件。
- 您可以使用組織內容套件從傳統的工作區。 但無法從新的工作區取用組織內容套件。

## <a name="workspace-contact-list"></a>工作區中的連絡人清單
新**連絡人清單**功能可讓您指定哪些使用者會收到通知的方式在工作區中所發生的問題。 根據預設，任何使用者或群組指定為工作區系統管理員會收到通知，但您可以自訂清單。 使用者或連絡人清單中所列的群組將會顯示在使用者介面 (UI)，以協助使用者取得與工作區相關的協助。 

深入了解[設定工作區中的連絡人清單](service-create-the-new-workspaces.md#workspace-contact-list)。

## <a name="workspace-onedrive"></a>Workspace OneDrive
工作區 OneDrive 功能可讓您設定 Office 365 群組的 SharePoint 文件庫的檔案儲存體可供工作區的使用者。 需要 Power BI 外部建立的群組。 

Power BI 不會同步處理使用者或群組已設定為擁有 Office 365 群組成員資格的工作區存取權的限。 最佳做法是管理工作區存取，透過相同的 Office 365 群組設定此設定中的檔案儲存體。 

了解如何[設定和存取工作區 OneDrive](service-create-the-new-workspaces.md#workspace-onedrive)。  
   
## <a name="auditing"></a>稽核
下列活動會從 Power BI 稽核的新工作區體驗工作區。

| 易記名稱 |   作業名稱 |
|---|---|
| 已建立 Power BI 資料夾 | CreateFolder |
| 已刪除 Power BI 資料夾 | DeleteFolder |
| 已更新 Power BI 資料夾 | UpdateFolder |
| 已更新 Power BI 資料夾存取權| UpdateFolderAccess |

深入了解[Power BI 稽核](service-admin-auditing.md#activities-audited-by-power-bi)。

## <a name="limitations-and-considerations"></a>限制與考量

要注意的限制：

- 工作區可包含最多 1,000 個資料集，或每個資料集 1,000 個報表。 
- 具有 Power BI Pro 授權的人員可以是最大值 1000 工作區的成員。
- 不支援 power BI publisher for Excel。

## <a name="workspace-features-that-work-differently"></a>運作方式不同的工作區功能

某些功能在新工作區的運作方式不同於目前工作區。 這些差異是刻意設計的根據我們收到來自客戶，並啟用共同作業與工作區的更彈性方法的意見反應：

- 授權強制執行：將報表發行至新的工作區體驗會強制執行現有的授權規則需要 Power BI Pro 授權使用者在工作區中共同作業，或共用給其他人的 Power BI 服務中的內容。 不需要 Pro 授權的使用者會看到錯誤 「 只有使用 Powre BI Pro 授權的使用者可以發佈到此工作區 」。
- 成員可以或無法再次共用：取代為「參與者」角色
- 唯讀工作區：無需將工作區的唯讀存取權授與使用者，您可以將使用者指派給即將推出的「檢視者」角色，這會允許工作區中內容的類似唯讀存取權。
- 沒有 [離開工作區]  按鈕。

## <a name="frequently-asked-questions"></a>常見問題集

**會影響新的工作區的現有內容的連結體驗正式運作**

否。 連結至傳統的工作區中的現有項目不會受到新的工作區體驗。 新的工作區體驗的公開上市 (GA) 變更預設工作區，您建立，但不會變更現有工作區。 

**現有的工作區升級至新的工作區體驗，有了 GA**

否。 新的工作區體驗 GA 只會變更為新的工作區體驗的預設工作區類型。 現有的傳統工作區為基礎的 Office 365 群組維持不變。

**工作區仍會自動建立的 Office 365 群組嗎**

是。 因為我們支援兩種類型的工作區並排顯示，我們會繼續列出使用者可存取工作區 清單中的所有 Office 365 群組。

## <a name="next-steps"></a>後續步驟
* [在 Power BI 中建立新的工作區](service-create-the-new-workspaces.md)
* [建立傳統的工作區](service-create-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](service-create-distribute-apps.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
