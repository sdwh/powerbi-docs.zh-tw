---
title: 在新的工作區中組織工作 - Power BI
description: 了解新的工作區，這些工作區是為了提供重要計量給組織而建立的儀表板和報告集合。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 419cd2137b8924f153009843d6f60db594219059
ms.sourcegitcommit: a42c6758aa255c21ece6366a3257b0dd82f3606b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2019
ms.locfileid: "67345531"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>在 Power BI 中組織新工作區中的工作

 「工作區」  是要與同事共同合作來建立儀表板、報表和編頁報表集合的地方。 新的工作區體驗可協助您更妥善管理內容的存取。 本文描述新的工作區，以及它們與傳統工作區有何不同。  如同傳統工作區一樣，您仍然使用它們來建立和散發應用程式。 閱讀如何[建立新的工作區體驗](service-create-the-new-workspaces.md)。

新的工作區體驗已正式運作 (GA)，而且現在是預設工作區。 您仍然可以繼續根據 Office 365 群組建立並使用[傳統工作區](service-create-workspaces.md)。 

> [!NOTE]
> 若要強制執行資料列層級安全性 (RLS)，讓使用者瀏覽工作區中的內容，請使用檢視者角色。 如果尚無法在您的租用戶中使用檢視者角色，請繼續使用[傳統工作區](service-create-workspaces.md)，然後選取 [成員只能檢視 Power BI 內容]  選項。 或者，將 Power BI 應用程式發佈給這些使用者，或使用「共用」來散發內容。

使用新的工作區，您可以：

- 將工作區角色指派給使用者群組：安全性群組、通訊群組清單、Office 365 群組，以及個人。
- 在 Power BI 中建立工作區，而不建立 Office 365 群組。
- 使用更精細的工作區角色，在工作區中進行更有彈性的權限管理。
- Power BI 系統管理員可以控制誰可以在 Power BI 中建立工作區。

當您建立其中一個新工作區時，不會建立基礎的相關聯 Office 365 群組。 所有工作區管理都是在 Power BI 中進行，而不是 Office 365。 在新的工作區體驗中，您現在可以在工作區存取清單中新增 Office 365 群組，以繼續透過 Office 365 群組管理使用者對內容的存取。

## <a name="administering-new-workspace-experience-workspaces"></a>管理新的工作區體驗工作區
現在可在 Power BI 中管理新的工作區體驗工作區，因為 Power BI 系統管理員可決定組織中的誰可以建立工作區。 他們也可以管理和復原工作區。 若要這樣做，他們需要使用 Power BI 管理入口網站或 PowerShell Cmdlet。 對於以 Office 365 群組為基礎的傳統工作區，可在 Office 365 管理入口網站和 Azure Active Directory 中繼續進行管理。

在管理入口網站的 [工作區設定]  中，系統管理員可以使用 [建立工作區] (新的工作區體驗) 設定，來允許組織中的每個人或不允許任何人建立新的工作區體驗工作區。 他們也可以限制只有特定安全性群組的成員才能建立。

> [!NOTE]
> [建立工作區] (新的工作區體驗) 設定預設為只允許可以建立 Office 365 群組的使用者，才能在 Power BI 中建立新的工作區。 請務必在 Power BI 管理入口網站設定一值，以確保適當的使用者可以建立新的工作區體驗工作區。

![管理入口網站中的 [工作區設定]](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

Power BI 管理入口網站中[提供工作區清單](service-admin-portal.md#workspaces)。 

![工作區清單](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>新的工作區與傳統工作區並排

新的升級工作區與現有的傳統工作區並排共存，您可以建立任一個工作區。 新的工作區體驗是預設工作區類型。 Power BI 會繼續列出使用者是 Power BI 中成員的所有 Office 365 群組，以避免變更現有的工作流程。 若要了解如何建立新的工作區，請閱讀[建立新的工作區](service-create-the-new-workspaces.md)。 若要了解如何建立傳統工作區，請閱讀[建立傳統工作區](service-create-workspaces.md)。

## <a name="roles-in-the-new-workspaces"></a>新工作區中的角色

若要授與新工作區的存取權，請將使用者群組或個人新增至其中一個工作區角色：檢視者、成員、參與者或系統管理員。 使用者群組中的每個人都會取得您已定義的角色。 如果個人在數個使用者群組中，他們會取得所指派角色提供的最高層級權限。

角色可讓您管理誰可以在工作區中做什麼，因此小組可以共同作業。 新的工作區可讓您將角色指派給個人和使用者群組：安全性群組、Office 365 群組，以及通訊群組清單。 

當您將角色指派給使用者群組時，群組中的個人可以存取內容。 如果巢狀處理使用者群組，則所有包含的使用者都具有權限。 在數個使用者群組中具有不同角色的使用者，會獲得授與他們的最高層級權限。 

新的工作區提供四種角色：系統管理員、成員、參與者和檢視者。

|功能   | 系統管理員  | 成員  | 參與者  | 檢視者 |
|---|---|---|---|---|
| 更新和刪除工作區。  | X  |   |   |   | 
| 新增/移除人員，包括其他系統管理員。  | X  |   |   |   |
| 新增具有較低權限的成員或其他人。  |  X | X  |   |   |
| 發佈和更新應用程式。 |  X | X  |   |   |
| 共用項目或共用應用程式。 |  X | X  |   |   |
| 允許其他人再次共用項目。 |  X | X  |   |   |
| 建立、編輯和刪除工作區中的內容。  |  X | X  | X  |   |
| 將報表發佈至工作區、刪除內容。  |  X | X  | X  |   |
| 檢視項目。 |  X | X  | X  | X  |
 
 
## <a name="licensing"></a>授權
新增至共用容量中工作區的每個人都必須有 Power BI Pro 授權。 在工作區中，這些使用者皆可在儀表板和報表上共同作業，以準備發佈給更多對象，甚至整個組織。 

如果您想要將內容散發給組織內的其他人，則可以將 Power BI Pro 授權指派給這些使用者，或將工作區置於 Power BI Premium 容量中。

當工作區在 Power BI Premium 容量中時，具有檢視者角色的使用者可以存取工作區，即使他們沒有 Power BI Pro 授權也一樣。 不過，如果您將較高的角色 (例如系統管理員、成員或參與者) 指派給這些使用者，他們將無法存取工作區。 系統會在他們嘗試存取工作區時提示他們啟動 Pro 試用版。 若要在沒有 Pro 授權的情況下，利用使用者的檢視者功能，請確定檢視者角色中的使用者未以下列方式位於其他工作區角色中：個別或透過使用者群組。 

> [!NOTE]
> 將報表發佈至新的工作區體驗會更嚴格地強制執行現有的授權規則。 嘗試在沒有 Pro 授權的情況下，從 Power BI Desktop 或其他用戶端工具發佈的使用者會看到「只有具備 Power BI Pro 授權的使用者才能發佈至這個工作區」錯誤。

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>新工作區與目前工作區有何不同？

我們使用新的工作區重新設計了一些功能。 以下是您可預期為永久性的變更。 

* 建立這些工作區不會如傳統工作區一般建立 Office 365 群組。 不過，您現在可以使用 Office 365 群組，藉由指派角色給它，讓使用者可以存取您的工作區。 
* 在傳統工作區中，您只能將個人新增至成員和系統管理員清單。 在新的工作區中，您可以將多個 AD 安全性群組、通訊群組清單或 Office 365 群組新增至這些清單，以便能夠更輕鬆地進行使用者管理。 
- 您可以從傳統工作區建立組織內容套件。 但無法從新的工作區建立組織內容套件。
- 您可以從傳統工作區取用組織內容套件。 但無法從新的工作區取用組織內容套件。

## <a name="workspace-contact-list"></a>工作區連絡人清單
新的「連絡人清單」  功能可讓您指定哪些使用者會收到工作區中發生問題的通知。 根據預設，指定為工作區系統管理員的任何使用者或群組都會收到通知，但您可以自訂清單。 連絡人清單中所列的使用者或群組將會顯示在使用者介面 (UI) 中，以協助使用者取得與工作區相關的說明。 

深入閱讀[設定工作區連絡人清單](service-create-the-new-workspaces.md#workspace-contact-list)。

## <a name="workspace-onedrive"></a>工作區 OneDrive
工作區 OneDrive 功能可讓您設定 Office 365 群組，其 SharePoint 文件庫的檔案儲存體可供工作區使用者使用。 需要在 Power BI 外建立群組。 

Power BI 不會同步處理使用者或群組的權限，而這些使用者或群組會設定為可利用 Office 365 群組成員資格存取工作區。 最佳作法是透過相同的 Office 365 群組管理工作區存取，而您會在此設定中設定該群組的檔案儲存體。 

閱讀如何[設定和存取工作區 OneDrive](service-create-the-new-workspaces.md#workspace-onedrive)。  
   
## <a name="auditing"></a>稽核
Power BI 會稽核新工作區體驗工作區的下列活動。

| 易記名稱 |   作業名稱 |
|---|---|
| 已建立 Power BI 資料夾 | CreateFolder |
| 已刪除 Power BI 資料夾 | DeleteFolder |
| 已更新 Power BI 資料夾 | UpdateFolder |
| 已更新 Power BI 資料夾存取權| UpdateFolderAccess |

深入閱讀 [Power BI 稽核](service-admin-auditing.md#activities-audited-by-power-bi)。

## <a name="limitations-and-considerations"></a>限制與考量

要注意的限制：

- 工作區可包含最多 1,000 個資料集，或每個資料集 1,000 個報表。 
- 擁有 Power BI Pro 授權的人員可以是工作區數目上限為 1,000 的成員。
- 不支援 Power BI Publisher for Excel。

## <a name="workspace-features-that-work-differently"></a>運作方式不同的工作區功能

某些功能在新工作區的運作方式不同於目前工作區。 根據我們從客戶收到的意見反應，這些差異是刻意設計的，並會啟用更彈性方法，以便與工作區共同作業：

- 授權強制執行：將報表發佈至新的工作區體驗會強制執行現有的授權規則，此規則需要在工作區中共同作業的使用者，或在 Power BI 服務中與其他人共用內容的使用者具有 Power BI Pro 授權。 沒有 Pro 授權的使用者會看到「僅具有 Powre BI Pro 授權的使用者才能發佈至這個工作區」錯誤。
- 成員可以或無法再次共用：取代為「參與者」角色
- 唯讀工作區：無需將工作區的唯讀存取權授與使用者，請將使用者指派給檢視者角色，這會允許工作區中內容的類似唯讀存取權。
- 如果工作區在 Power BI Premium 容量中，則沒有 Pro 授權的使用者可以存取工作區，即使使用者只有檢視者角色也一樣。
- 若要允許具有檢視者角色的使用者匯出資料，請確定他們對工作區中的資料集具有建置權限。
- 沒有 [離開工作區]  按鈕。

## <a name="frequently-asked-questions"></a>常見問題集

**現有內容受到新工作區體驗影響的連結是否正式運作**

否。 新的工作區體驗不會影響傳統工作區中現有項目的連結。 正式運作 (GA) 的新工作區體驗會變更您建立的預設工作區，但不會變更現有工作區。 

**現有的工作區是否升級至正式運作的新工作區體驗**

否。 新的工作區體驗 GA 只會將預設工作區類型變更為新的工作區體驗。 基於 Office 365 群組的現有傳統工作區維持不變。

**是否仍會針對 Office 365 群組自動建立工作區**

是。 因為我們支援這兩種類型的工作區並排，所以我們會繼續列出工作區清單中使用者可以存取的所有 Office 365 群組。

## <a name="next-steps"></a>後續步驟
* [在 Power BI 中建立新的工作區](service-create-the-new-workspaces.md)
* [建立傳統工作區](service-create-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](service-create-distribute-apps.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
