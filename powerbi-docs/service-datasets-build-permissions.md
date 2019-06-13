---
title: 建立和共用資料集 (預覽) - Power BI
description: 身為資料集擁有者，您可以建立和共用您的資料集，讓其他人也可以使用。 了解如何使用建置權限控制誰可以存取資料。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 22339b3d5062c01b3795086eede24ed6a8e7d7e7
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461756"
---
# <a name="create-and-share-datasets-preview"></a>建立和共用資料集 (預覽)

身為 Power BI Desktop 中的「資料模型」  建立者，您可以共用這些模型，作為 Power BI 服務中的「資料集」  。 接著，報表建立者可以輕鬆探索並重複使用您共用的資料集。 了解如何共用資料集，以及如何使用建置權限控制誰可以存取資料。

## <a name="steps-to-sharing-your-dataset"></a>共用資料集的步驟

1. 開始方式為使用 Power BI Desktop 中的資料模型建立 .pbix 檔案。 如果您打算將此資料集提供給其他人建立報表，您可能甚至無法在 .pbix 檔案中設計報表。

    最佳做法是將 .pbix 檔案儲存至 Office 365 群組。

1. 將 .pbix 檔案發佈到 Power BI 服務中的[新體驗工作區](service-create-the-new-workspaces.md)。
    
    此工作區的其他成員，已經可以根據此資料集在其他工作區中建立報表。

1. 現在您可以從這個工作區[建立應用程式](service-create-distribute-apps.md)。 當您這麼做時，您可以在 [權限]  頁面上指定誰具有權限來進行哪些項目。

    > [!NOTE]
    > 如果您選取 [整個組織]  ，組織中將沒有任何人具有建置權限。 此為已知的問題。 因此，請在 [特定的個人或群組]  中指定電子郵件地址。  如果您希望整個組織都具有建置權限，請指定整個組織的電子郵件別名。

    ![設定應用程式權限](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. 選取 [發佈應用程式]  ，或 [更新應用程式]  (如果已發佈)。

## <a name="build-permissions-for-shared-datasets"></a>共用資料集的建置權限

建置權限類型只會與資料集相關。 使用者可以利用此權限在資料集建置新內容，例如問與答中的報表、儀表板、釘選圖格，以及見解探索。 也可以在 Power BI 外部的資料集建置新內容，例如透過使用 Excel 分析的 Excel 工作表、XMLA 和匯出。

使用者可以藉由不同方式取得建置權限：

- 資料集所在的工作區成員，可以將權限指派給權限中心內的特定使用者或安全性群組。 選取資料集 > [管理權限]  旁的省略符號 (...)。

    ![選取省略符號](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    這會開啟該資料集的權限中心，您可以在此設定並變更權限。

    ![權限中心](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- 資料集所在工作區的系統管理員或成員，可以在發佈應用程式期間決定具有應用程式權限之使用者也可以獲得基礎資料集的建置權限。 請參閱[共用資料集的步驟](#steps-to-sharing-your-dataset)以取得詳細資料。

- 假設您擁有在資料集上再次共用與建置的權限。 當您共用根據該資料集所建置的報表或儀表板時，您可以指定收件者也可獲得基礎資料集的建置權限。

    ![建置權限](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

您可以移除人員對資料集的建置權限。 如果您這麼做，他們仍可以查看建置於共用資料集的報表，但無法再加以編輯。

## <a name="more-granular-permissions"></a>更細微的權限

Power BI 於 2019 年 6 月推出建置權限，作為現有權限、讀取和再次共用的補充。 所有已在該時間透過應用程式權限、共用或工作區存取權取得資料集讀取權限的使用者，也可獲得這些相同資料集的建置權限。 他們會自動獲得建置權限，因為讀取權限已授與他們在資料集上建置新內容的權限 (藉由使用 Excel 分析或匯出)。

藉由這種更細微的建置權限，您可以選擇誰只能檢視現有報表或儀表板中的內容、誰可以建立連線至基礎資料集的內容。

如果資料集工作區外的報表正在使用資料集，您無法刪除該資料集。 反之，您會看到一則錯誤訊息。

您可以移除建置權限。 如果您這麼做，您已撤銷其權限的使用者仍然可以查看報表，但無法再編輯報表。

## <a name="track-your-dataset-usage"></a>追蹤您的資料集使用方式

當您在工作區中擁有共用資料集時，您可能需要知道其他工作區中的哪些報表以該資料集為基礎。

1. 在資料集清單檢視中，選取 [檢視相關項目]  。

    ![檢視相關項目圖示](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. [相關內容]  對話方塊會顯示所有相關項目。 在此清單中，您會看到此工作區與 [其他工作區]  中的相關項目。
 
    ![[相關內容] 對話方塊](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>後續步驟

- [跨工作區使用資料集 (預覽)](service-datasets-across-workspaces.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
