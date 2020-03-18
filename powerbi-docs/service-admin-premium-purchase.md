---
title: 如何購買 Power BI Premium
description: 了解如何購買 Power BI Premium，以及讓整個組織存取內容。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/13/2020
LocalizationGroup: Premium
ms.openlocfilehash: aed0d1e4dec6f6efe49dd39cd5b6fc60f8977e44
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488606"
---
# <a name="how-to-purchase-power-bi-premium"></a>如何購買 Power BI Premium

本文描述如何為貴組織購買 Power BI Premium 容量。 本文包含兩個案例：

- 使用 P SKU 處理一般生產案例。 P SKU 需要每月或每年履約承諾，按月計費。

- 測試案例及無必要權限可購買 P SKU 的情況 (Microsoft 365 全域管理員角色或計費管理員角色)，請使用 A SKU。 A SKU 不需要任何時限的履約承諾，按小時計費。 A SKU 在 [Azure 入口網站](https://portal.azure.com)中購買。

如需 Power BI Premium 的詳細資訊，請參閱 [什麼是 Power BI Premium？](service-premium-what-is.md)。 如需目前的定價和規劃資訊，請參閱 [Power BI 定價頁面](https://powerbi.microsoft.com/pricing/)和 [Power BI Premium 計算機](https://powerbi.microsoft.com/calculator/)。 即使您的組織使用 Power BI Premium，內容的作者仍然需要 [Power BI Pro 授權](service-admin-purchasing-power-bi-pro.md)。 請確定您為貴組織購買至少一個 Power BI Pro 授權。 使用 A SKU 時，_取用內容的所有使用者_也都需要 Pro 授權。

> [!NOTE]
> 如果 Premium 訂用帳戶過期，您仍有 30 天可完整存取您的容量。 在該期限之後，您的內容會還原至共用的容量。 共用容量不支援 1 GB 以上的模型。

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>一般生產案例請購買 P SKU

您可以建立已設定 Power BI Premium P1 SKU 建立的新租使用者，也可以為現有的組織購買 Power BI Premium 容量。 如有需要，這兩種情況都可以新增容量。

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>建立具有 Power BI Premium P1 的新租用戶

如果您目前沒有租用戶並想建立一個，您可以同時購買 Power BI Premium。 下列連結會引導您完成建立新租用戶的程序，並可讓您購買 Power BI Premium：[Power BI Premium P1 供應項目](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1)。 當您建立租用戶時，系統會自動將該租用戶的 Microsoft 365 全域管理員角色指派給您。

購買容量之後，請了解如何[管理容量](service-admin-premium-manage.md#manage-capacity)並針對容量來[指派工作區](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity)。

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>為現有的組織購買 Power BI Premium 容量

如果您有現有的組織 (租用戶)，則您必須是 Microsoft 365 全域管理員角色或計費管理員角色才能購買訂閱和授權。 如需詳細資訊，請參閱[關於 Microsoft 365 系統管理員角色](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)。

若要購買 Premium 容量，請遵循下列步驟。

1. 從 Power BI 服務內選取 Microsoft 365 應用程式選擇器，然後選取 [系統管理員]  。

    ![Microsoft 365 應用程式選擇器](media/service-admin-premium-purchase/o365-app-picker.png)

    或者，您可以瀏覽至 Microsoft 365 系統管理中心。

1. 選取 [計費]   > [購買服務]  。

1. 在 [其他方案]  下，尋找 Power BI Premium 供應項目。 如此會列出 P1 到 P3、EM3 以及 P1 (逐月)。

1. 將滑鼠停留在省略符號 ( **. . .** )，然後選取 [立即購買]  。

    ![立即購買](media/service-admin-premium-purchase/premium-purchase.png)

1. 請依照下列步驟完成購買程序。

完成購買之後，[購買服務]  頁面會顯示項目已購買且在使用中。

![已購買 Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

購買容量之後，請了解如何[管理容量](service-admin-premium-manage.md#manage-capacity)並針對容量來[指派工作區](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity)。

### <a name="purchase-additional-capacities"></a>購買額外的容量

現在您有了容量，您可以依照需求的增長來新增更多容量。 在您的組織內，您可以使用 Premium 容量 SKU 的任意組合 (P1 至 P3)。 不同的 SKU 可提供不同資源容量。

1. 在 Microsoft 365 系統管理中心內，選取 [帳單]   > [購買服務]  。

1. 在 [其他方案]  下，尋找您要購買更多的 Power BI Premium 項目。

1. 將滑鼠暫留在 [更多選項]  (...)，然後選取 [變更授權數量]  。

    ![變更授權數量](media/service-admin-premium-purchase/premium-purchase-more.png)

1. 針對此項目，變更為您想要的執行個體數目。 完成時選取 [送出]  。

   > [!IMPORTANT]
   > 選取 [送出]  會對信用卡收取費用。

[購買服務]  頁面將會指出您擁有的執行個體數目。 在 Power BI 管理入口網站的 [容量設定]  下，可用的 V 核心反映新購買的容量。

![Power BI Premium 容量可用的 V 核心](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>取消您的訂用帳戶

您可以從 Microsoft 365 系統管理中心取消訂用帳戶。 若要取消您的 Premium 訂閱，請執行下列動作。

1. 瀏覽至 MIcrosoft 365 系統管理中心。

1. 選取 [計費]   > [訂用帳戶]  。

1. 從清單中選取您的 Power BI Premium 訂用帳戶。

1. 選取 [More actions] \(其他動作\)   > [Cancel subscription] \(取消訂閱\)  。

1. [取消訂用帳戶]  頁面會指出您是否對[提早取消費用](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3)負有責任。 此頁面也會讓您知道何時將會刪除訂用帳戶的資料。

1. 請完成閱讀此資訊，如果您想要繼續，請選取 [取消訂用帳戶]  。

#### <a name="when-canceling-or-your-license-expires"></a>取消或授權到期時

當您取消 Premium 訂閱，或您的容量授權到期時，自取消或授權到期的日期起，可以繼續存取進階容量 30 天。 30 天後，您將不再能夠存取您的進階容量或其中的工作區。

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>購買用於測試和其他案例的 A SKU

A SKU 可透過 Azure Power BI Embedded 服務取得。 您可以透過下列方式使用 A SKU︰

- 將 Power BI 內嵌在協力廠商應用程式中。 如需詳細資訊，請參閱 [Power BI Embedded](developer/embedded/azure-pbie-what-is-power-bi-embedded.md)。

- 購買 P SKU 之前，請先測試 Premium 功能。

- 在使用 P SKU 的生產環境中，建立開發和測試環境。

- 即使您不具有 Microsoft 365 全域管理員角色或計費管理員角色，也請購買 Power BI Premium。

> [!NOTE]
> 如果購買 A4 或更高等級的 SKU，您可以利用除無限制共用內容外的所有高階功能。 使用 A SKU 時，_取用內容的所有使用者_都需要 Pro 授權。

遵循下列步驟在 Azure 入口網站中購買 A SKU：

1. 使用在 Power BI 中至少具有容量系統管理員權限的帳戶，登入 [Azure 入口網站](https://portal.azure.com)。

1. 搜尋 _Power BI Embedded_ 並在搜尋結果中選取服務。

    ![Azure 入口網站搜尋](media/service-admin-premium-purchase/azure-portal-search.png)

1. 選取 [Create Power BI Embedded] \(建立 Power BI Embedded\)  。

    ![建立 Power BI Embedded](media/service-admin-premium-purchase/create-power-bi-embedded.png)

1. 在建立 **Power BI Embedded** 的畫面中，指定下列資訊：

    - 要建立 Power BI Embedded 服務的**訂閱**。

    - 建立包含服務的資源群組所在實體**位置**。 為了達到較佳的效能，此位置應該接近您 Power BI 的 Azure Active Directory 租用戶位置。

    - 要使用的現有**資源群組**，或如範例所示建立一個新的資源群組。

    - **Power BI 容量管理員**。 容量管理員必須是您 Azure AD 租用戶的成員使用者或服務主體。

    ![訂閱和資源群組](media/service-admin-premium-purchase/subscription-resource-group.png)

1. 若要使用 Power BI Premium 的所有功能 (無限制共用除外)，您至少需要一個 A4 SKU。 選取 [變更大小]  。

    ![變更容量大小](media/service-admin-premium-purchase/change-capacity-size.png)

1. 選取對應 P1、P2 和 P3 的 [A4]、[A5] 或 [A6] 容量大小。

    ![選取 [A3] 容量](media/service-admin-premium-purchase/select-a3-capacity.png)

1. 選取 [檢閱 + 建立]  ，檢閱所選選項，然後選取 [建立]  。

    ![建立資源](media/service-admin-premium-purchase/create-resource.png)

1. 完成部署需要幾分鐘。 一切準備就緒後，請選取 [前往資源]  。

    ![部署完成](media/service-admin-premium-purchase/deployment-complete.png)

1. 在管理畫面中，檢閱用於管理服務的選項，包括暫停未使用的服務。

    ![管理容量](media/service-admin-premium-purchase/manage-capacity.png)

購買容量之後，請了解如何[管理容量](service-admin-premium-manage.md#manage-capacity)並針對容量來[指派工作區](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity)。

## <a name="next-steps"></a>後續步驟

[設定及管理 Power BI Premium 中的容量](service-admin-premium-manage.md)\
[Power BI 定價頁面](https://powerbi.microsoft.com/pricing/)\
[Power BI Premium 計算機](https://powerbi.microsoft.com/calculator/)\
[Power BI Premium 常見問題集](service-premium-faq.md)\
[規劃 Power BI 企業部署白皮書](https://aka.ms/pbienterprisedeploy)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
