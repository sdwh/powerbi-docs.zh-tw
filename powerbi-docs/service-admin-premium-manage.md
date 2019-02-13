---
title: 管理 Power BI Premium 和 Power BI Embedded 內的容量
description: 了解如何管理 Power BI Premium，以及讓整個組織存取內容。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/07/2019
LocalizationGroup: Premium
ms.openlocfilehash: 2a38d53a121f0a58c18f627370bf81413cf36982
ms.sourcegitcommit: 3729c88bd991e450fcb2d9b79e6ab478b6e8dc76
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55888202"
---
# <a name="manage-capacities-within-power-bi-premium-and-power-bi-embedded"></a>管理 Power BI Premium 和 Power BI Embedded 內的容量

了解如何管理提供內容專用資源的 Power BI Premium 和 Power BI Embedded 容量。

![Power BI 的容量設定畫面](media/service-admin-premium-manage/premium-capacity-management.png)

## <a name="what-is-capacity"></a>什麼是容量？

「容量」是 Power BI Premium 和 Power BI Embedded 供應項目的中心。 它是一組專門保留供組織使用的資源集。 擁有專用容量可讓您將儀表板、報表和資料集發佈給整個組織的使用者，而不必購買其個別使用者授權。 它也會為容量中所裝載內容提供可靠且一致的效能。 如需詳細資訊，請參閱[什麼是 Power BI Premium？](service-premium.md)。

### <a name="capacity-admins"></a>容量管理員

當您被指派為容量的「容量管理員」時，您就可以全權掌控容量和其系統管理功能。 從 Power BI 管理入口網站，您可以新增更多容量管理員，或將容量指派權限授與使用者。 您可以將工作區大量指派給容量，並檢視容量的使用量計量。

> [!NOTE]
> 針對 Power BI Embedded，容量管理員是在 Microsoft Azure 入口網站中定義。

每個容量都有其自己的管理員。 指派某個容量的容量管理員，並不會提供他們對您組織內所有容量的存取權。 容量管理員預設無法存取所有的 Power BI 管理區域，例如使用計量、稽核記錄檔或租用戶設定。 容量管理員也沒有設定新容量或變更現有容量 SKU 的權限。 只有 Office 365 全域管理員或 Power BI 服務管理員可以存取這些項目。

所有 Office 365 全域管理員和 Power BI 服務管理員都會自動成為 Power BI Premium 容量和 Power BI Embedded 容量的容量管理員。

## <a name="purchase-capacity"></a>購買容量

若要利用專用容量，您必須在 Office 365 系統管理中心內購買 Power BI Premium，或在 Microsoft Azure 入口網站中建立 Power BI Embedded 資源。 如需詳細資訊，請參閱下列文章：

* **Power BI Premium：**[如何購買 Power BI Premium](service-admin-premium-purchase.md)

* **Power BI Embedded：**[在 Azure 入口網站中建立 Power BI Embedded 容量](https://docs.microsoft.com/azure/power-bi-embedded/create-capacity)

當您購買 Power BI Premium 或 Embedded SKU 時，租用戶會收到供執行中容量使用的對應 V 核心數目。 例如，購買 Power BI Premium P3 SKU 可提供租用戶 32 個 V 核心。 如需 SKU 的詳細資訊，請參閱 [Premium 容量節點](service-premium.md#premium-capacity-nodes)。

## <a name="what-premium-looks-like-for-users"></a>Premium 對使用者而言是什麼

在大部分的情況下，使用者不需要知道他們位在 Premium 容量中。 其儀表板和報表也能夠運作。 在 Premium 容量中工作區旁有一個菱形圖示，這是視覺效果提示。

![菱形表示 Premium 容量已備份工作區](media/service-admin-premium-manage/premium-workspace.png)

## <a name="configure-workloads"></a>設定工作負載

根據預設，適用於 Power BI Premium 和 Power BI Embedded 的容量，只支援雲端上與執行中 Power BI 查詢相關聯的工作負載。 我們現在針對兩個額外的工作負載提供預覽支援：**編頁報表**和**資料流程**。 如需詳細資訊，請參閱 [Premium 容量中的	工作負載](service-premium.md#workloads-in-premium-capacity)。

若要在 Power BI 管理入口網站中啟用工作負載，請進行下列步驟。

1. 在 [容量設定] 底下，選取容量。

1. 在 [更多選項] 底下，展開 [工作負載]。

1. 啟用一或多個工作負載，並設定 [最大記憶體] 的值。

    ![在管理入口網站設定工作負載](media/service-admin-premium-manage/admin-portal-workloads.png)

1. 選取 [ **套用**]。

## <a name="monitor-capacity-usage"></a>監視容量使用方式

Power BI 提供用於監視容量使用狀況的應用程式。 如需詳細資訊，請參閱[監視您組織中的 Power BI Premium 容量](service-admin-premium-monitor-capacity.md)。

## <a name="manage-capacity"></a>管理容量

在 Office 365 中購買容量節點之後，請在 Power BI 管理入口網站中設定容量。 您可以在入口網站的 [容量設定] 區段中管理 Power BI Premium 容量。

![管理入口網站內的容量設定](media/service-admin-premium-manage/admin-portal-premium.png)

您可以選取容量的名稱來管理容量。 這會將您帶到容量管理畫面。

![選取容量名稱以移至容量指派畫面](media/service-admin-premium-manage/capacity-assignment.png)

如果未將任何工作區指派給容量，您會看到[將工作區指派給容量](#assign-a-workspace-to-a-capacity)的相關訊息。

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>設定新的容量 (Power BI Premium)

管理入口網站會顯示您已使用和您仍然可用的「虛擬核心」(V 核心) 數目。 V 核心總數是根據您購買的進階 SKU 數。 例如，購買 P3 和 P2 會得到 48 個可用的核心，P3 有 32 個，P2 有 16 個。

![Power BI Premium 已使用和可使用的 V 核心](media/service-admin-premium-manage/admin-portal-v-cores.png)

如有可用的 V 核心，請執行下列步驟來設定新容量。

1. 選取 [設定新的容量]。

1. 提供您容量的名稱。

1. 定義誰是這個容量的管理員。

1. 選取容量大小。 可用的選項取決於您有多少可用的 V 核心。 您無法選取超過可用數量的選項。

    ![可用的 Premium 容量大小](media/service-admin-premium-manage/premium-capacity-size.png)

1. 選取 [設定]。

    ![設定新的容量](media/service-admin-premium-manage/set-up-capacity.png)

容量管理員以及 Power BI 管理員和 Office 365 全域管理員，接著會看到管理入口網站中所列的容量。

### <a name="capacity-settings"></a>容量設定

1. 在 Premium 容量管理畫面的 [動作] 下方，選取**齒輪圖示**以檢閱和更新設定。 

    ![容量管理區中的容量動作](media/service-admin-premium-manage/capacity-actions.png)

1. 您可以看到誰是服務管理員、容量的 SKU/大小，以及容量所在的地區。

    ![容量設定](media/service-admin-premium-manage/capacity-settings.png)

1. 您也可以重新命名或刪除容量。

    ![Power BI Premium 中的容量設定 [刪除] 和 [套用] 按鈕](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> Power BI Embedded 容量設定是在 Microsoft Azure 入口網站中進行管理。

### <a name="change-capacity-size"></a>變更容量大小

Power BI 管理員和 Office 365 全域管理員可以變更 Power BI Premium 容量。 不是 Power BI 管理員或 Office 365 全域管理員的容量管理員沒有此選項。

1. 選取 [變更容量大小]。

    ![變更 Power BI Premium 容量大小](media/service-admin-premium-manage/change-capacity-size.png)

1. 在 [變更容量大小] 畫面上，視情況升級或降級您的容量。

    ![變更 Power BI Premium 容量大小下拉式清單](media/service-admin-premium-manage/change-capacity-size2.png)

    系統管理員可隨意建立、調整大小和刪除節點，只要他們有必要的 V 核心數量。

    P SKU 無法降級為 EM SKU。 您可以將滑鼠暫留在任何已停用的選項上以查看說明。

### <a name="manage-user-permissions"></a>管理使用者權限

您可以指派其他容量管理員，以及指派具有「容量指派」權限的使用者。 如果具有指派權限的使用者是應用程式工作區管理員，則他們可以將該工作區指派給容量。 他們也可以將其個人的「我的工作區」指派給容量。 具有指派權限的使用者無法存取管理入口網站。

> [!NOTE]
> 針對 Power BI Embedded，容量管理員是在 Microsoft Azure 入口網站中定義。

在 [使用者權限] 下方，展開 [具有指派權限的使用者]，然後視情況新增使用者或群組。

![容量使用者權限](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>將工作區指派給容量

有兩種方式可將工作區指派給容量：在管理入口網站和從應用程式工作區。

### <a name="assign-from-the-admin-portal"></a>從管理入口網站指派

容量管理員以及 Power BI 管理員和 Office 365 全域管理員，可以在管理入口網站的 Premium 容量管理區段中大量指派工作區。 當您管理容量時，會看到可讓您指派工作區的 [工作區] 區段。

![容量管理的工作區指派區域](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. 選取 [指派工作區]。 此選項可以在多個位置中使用。

1. 選取 [套用對象] 的選項。

    ![指派工作區](media/service-admin-premium-manage/assign-workspaces.png)

   | 選取項目 | 描述 |
   | --- | --- |
   | **依使用者選取工作區** | 當您指派使用者或群組的工作區時，會將這些使用者所擁有的所有工作區都指派給進階容量，包括使用者的個人工作區。 就是使用者會自動取得工作區指派權限。<br>這包括已指派給不同容量的工作區。 |
   | **特定工作區** | 輸入要指派給所選取容量的特定工作區名稱。 |
   | **The entire organization's workspaces (整個組織的工作區)** | 將整個組織的工作區指派給 Premium 容量，會將組織中的所有應用程式工作區和「我的工作區」指派給這個 Premium 容量。 此外，所有目前和未來使用者都有權將個別工作區重新指派給這個容量。 |
   | | |

1. 選取 [ **套用**]。

### <a name="assign-from-app-workspace-settings"></a>從應用程式工作區設定指派

您也可以從該工作區的設定中，將應用程式工作區指派給進階容量。 若要將工作區移至容量，您必須具有該工作區的管理員權限，同時具有該容量的容量指派權限。 請注意，工作區管理員一律可以從 Premium 容量中移除工作區。

1. 選取省略符號 **(. . .)** 然後選取 [編輯工作區] 來編輯應用程式工作區。

    ![從省略符號操作功能表編輯工作區](media/service-admin-premium-manage/edit-app-workspace.png)

1. 在 [編輯工作區] 下方，展開 [進階]。

1. 選取您想要將這個應用程式工作區指派至其中的容量。

    ![容量選項下拉式清單](media/service-admin-premium-manage/app-workspace-advanced.png)

1. 選取 [儲存]。

儲存之後，工作區和其所有內容都會移至 Premium 容量，而不會干擾終端使用者的任何體驗。

## <a name="power-bi-report-server-product-key"></a>Power BI 報表伺服器產品金鑰

在 Power BI 管理入口網站的 [容量設定] 索引標籤上，您可以存取 Power BI 報表伺服器產品金鑰。 這只適用於全域管理員，或已獲指派 Power BI 服務系統管理員角色的使用者，如已購買 Power BI Premium SKU。

![[容量設定] 內的 Power BI 報表伺服器金鑰](media/service-admin-premium-manage/pbirs-product-key.png)

選取 [Power BI 報表伺服器金鑰] 會顯示一個包含產品金鑰的對話方塊。 您可以複製金鑰，並在安裝時使用。

![Power BI 報表伺服器產品金鑰](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

如需詳細資訊，請參閱[安裝 Power BI 報表伺服器](report-server/install-report-server.md)。

## <a name="next-steps"></a>後續步驟

與使用者共用已發佈的應用程式。 如需詳細資訊，請參閱[在 Power BI 中建立和散發應用程式](service-create-distribute-apps.md)。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
