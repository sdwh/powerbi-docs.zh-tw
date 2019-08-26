---
title: 管理 Power BI 和 Office 365 中的應用程式工作區
description: Power BI 中的應用程式工作區是建置在 Office 365 群組上的共同作業體驗。 管理 Power BI 和 Office 365 中的應用程式工作區。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/08/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 278d631e755c4d484db0788b6c58fca9cfce4616
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68961870"
---
# <a name="manage-your-app-workspace-in-power-bi-and-office-365"></a>管理 Power BI 和 Office 365 中的應用程式工作區

[Power BI 或 Office 365 中應用程式工作區](service-create-distribute-apps.md)的建立者或管理員，有幾個管理 Power BI 中工作區的層面要管理。 您在 Office 365 中管理的其他層面。

> [!NOTE]
> 新的工作區體驗預覽會變更 Power BI 工作區與 Office 365 群組之間的關聯性。 每次建立其中一個新的工作區時，您都不會自動建立 Office 365 群組。 了解如何[建立新的工作區](service-create-the-new-workspaces.md)。

在 **Power BI** 中，您可以：

* 新增或移除應用程式工作區成員，包括將工作區成員設為系統管理員。
* 編輯應用程式工作區名稱。
* 刪除應用程式工作區。

在 **Office 365** 中，您可以：

* 新增或移除應用程式工作區的群組成員，包括將成員設為擁有者。
* 編輯群組名稱、影像、描述和其他設定。
* 查看群組電子郵件地址。
* 刪除群組。

您需要 [Power BI Pro 授權](service-features-license-type.md)，才能成為應用程式工作區的系統管理員或成員。 除非您的應用程式工作區在 Power BI Premium 容量中，否則，您的應用程式使用者也需要 Power BI Pro 授權。 如需詳細資訊，請參閱[什麼是 Power BI Premium？](service-premium-what-is.md)。

## <a name="edit-your-app-workspace-in-power-bi"></a>編輯 Power BI 中的應用程式工作區

1. 在 Power BI 服務中，選取 [工作區]  旁邊的箭號 > 選取工作區名稱旁邊的省略符號 (…) > [編輯此工作區]  。

   ![編輯 Power BI 中的工作區](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-ellipsis.png)

   > [!NOTE]
   > 只有在您是應用程式工作區管理員時，才會看到 [編輯此工作區]  。

1. 您可在此重新命名工作區、新增或移除成員，或刪除工作區。

   ![[編輯工作區] 對話方塊](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-edit-workspace.png)

1. 選取 [儲存]  或 [取消]  。

## <a name="edit-power-bi-app-workspace-properties-in-office-365"></a>編輯 Office 365 中的 Power BI 應用程式工作區屬性

您也可以直接在 Outlook for Office 365 中編輯應用程式工作區的外觀。

### <a name="edit-the-members-of-the-app-workspace-group"></a>編輯應用程式工作區群組的成員

1. 在 Power BI 服務中，選取 [工作區]  旁邊的箭號 > 選取工作區名稱旁邊的省略符號 (…) > [成員]  。

   ![編輯 Power BI 中的工作區](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-ellipsis-members.png)

   這會開啟應用程式工作區的 Outlook for Office 365 群組檢視。 您可能需要登入公司帳戶。

1. 選取小組成員名稱旁邊的角色，將該人員設為 [成員]  或 [擁有者]  。 選取 [X]  以從群組中移除該人員。

   ![編輯 Office 365 中的群組](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_managegroupo365.png)

### <a name="add-an-image-and-set-other-workspace-properties"></a>新增影像並設定其他工作區屬性

從應用程式工作區散發應用程式時，您在這裡新增的影像會成為應用程式的影像。 請參閱＜建立新工作區＞  一文的[＜將影像新增至 Office 365 應用程式工作區 (選擇性)＞](service-create-workspaces.md#add-an-image-to-your-office-365-app-workspace-optional)一節。

1. 在應用程式工作區的 Outlook for Office 365 檢視中，移至 [關於]  索引標籤，然後選取 [編輯]  。

    ![編輯群組圖示](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_editgroupo365.png)
1. 您可以編輯群組相關通知的名稱、描述和語言。 您也可以在這裡新增影像並設定其他屬性。

   ![[編輯群組] 對話方塊](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_editgrpo365dialog.png)

1. 選取 [儲存]  或 [捨棄]  。

## <a name="next-steps"></a>後續步驟

* [使用 Power BI 發佈應用程式](service-create-distribute-apps.md)

* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
