---
title: 如何購買 Power BI Premium
description: 了解如何購買 Power BI Premium，以及讓整個組織存取內容。
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/26/2019
LocalizationGroup: Premium
ms.openlocfilehash: 8922bb329e4b598745fd259c67e74b063368b7be
ms.sourcegitcommit: 76772a361e6cd4dd88824b2e4b32af30656e69db
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "56892382"
---
# <a name="how-to-purchase-power-bi-premium"></a>如何購買 Power BI Premium

本文描述如何為您的組織購買 Power BI Premium 容量 (P1-P3)。 您可以在 Office 365 系統管理中心購買 Power BI Premium 容量，並可在 Power BI 管理入口網站中[管理您的容量](service-admin-premium-manage.md)。 如需目前的定價和規劃資訊，請參閱 [Power BI 定價頁面](https://powerbi.microsoft.com/pricing/)和 [Power BI Premium 計算機](https://powerbi.microsoft.com/calculator/)。

即使您的組織使用 Power BI Premium，內容的作者仍然需要 Power BI Pro 授權。 請確定您為貴組織購買至少一個 Power BI Pro 授權。

如果 Premium 訂用帳戶過期，您仍有 30 天可完整存取您的容量。 在該期限之後，您的內容會還原至共用的容量。 共用容量不支援 1 GB 以上的模型。

## <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>建立具有 Power BI Premium P1 的新租用戶

如果您目前沒有租用戶並想建立一個，您可以同時購買 Power BI Premium。 下列連結會引導您完成建立新租用戶的程序，並可讓您購買 Power BI Premium：[Power BI Premium P1 供應項目](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1)。 當您建立租用戶時，系統會自動將您指派為該租用戶的 Office 365 全域管理員角色。

## <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>為現有的組織購買 Power BI Premium 容量

如果您有現有的組織 (租用戶)，則您必須是 Office 365 全域管理員角色或計費管理員角色，才能購買訂閱和授權。 如需詳細資訊，請參閱[關於 Office 365 系統管理員角色](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)。

若要購買 Premium 容量，請遵循下列步驟。

1. 從 Power BI 服務內選取 Office 365 應用程式選擇器，然後選取 [系統管理員]。

    ![Office 365 應用程式選擇器](media/service-admin-premium-purchase/o365-app-picker.png)

    或者，您可以瀏覽至 Office 365 系統管理中心。 您可以前往 [https://portal.office.com](https://portal.office.com)，再選取 [系統管理]，如此就能進入系統管理中心。

1. 選取 [計費] > [購買服務]。

1. 在 [其他方案] 下，尋找 Power BI Premium 供應項目。 如此會列出 P1 到 P3、EM3 以及 P1 (逐月)。

1. 將滑鼠停留在省略符號 (**. . .**)，然後選取 [立即購買]。

    ![立即購買](media/service-admin-premium-purchase/premium-purchase.png)

1. 請依照下列步驟完成購買程序。

完成購買之後，[購買服務] 頁面會顯示項目已購買且在使用中。

![已購買 Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

## <a name="purchase-additional-capacities"></a>購買額外的容量

現在您有了容量，您可以依照需求的增長來新增更多容量。 在您的組織內，您可以使用 Premium 容量 SKU 的任意組合 (P1 至 P3)。 不同的 SKU 可提供不同資源容量。

1. 在 Office 365 系統管理中心中，選取 [計費] > [購買服務]。

1. 在 [其他方案] 下，尋找您要購買更多的 Power BI Premium 項目。

1. 將滑鼠停留在**省略符號 (...)**，然後選取 [變更授權數量]。

    ![變更授權數量](media/service-admin-premium-purchase/premium-purchase-more.png)

1. 針對此項目，變更為您想要的執行個體數目。 完成時選取 [送出]。

   > [!IMPORTANT]
   > 選取 [送出] 會對信用卡收取費用。

[購買服務] 頁面將會指出您擁有的執行個體數目。 在 Power BI 管理入口網站的 [容量設定] 下，可用的 V 核心反映新購買的容量。

![Power BI Premium 容量可用的 V 核心](media/service-admin-premium-purchase/premium-capacities.png)

## <a name="cancel-your-subscription"></a>取消您的訂用帳戶

您可以從 Office 365 系統管理中心取消訂用帳戶。 若要取消您的 Premium 訂閱，請執行下列動作。

1. 瀏覽至 Office 365 系統管理中心。

1. 選取 [計費] > [訂用帳戶]。

1. 從清單中選取您的 Power BI Premium 訂用帳戶。

1. 選取 [More actions] \(其他動作\) > [Cancel subscription] \(取消訂閱\)。

1. [取消訂用帳戶] 頁面會指出您是否對[提早取消費用](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3)負有責任。 此頁面也會讓您知道何時將會刪除訂用帳戶的資料。

1. 請完成閱讀此資訊，如果您想要繼續，請選取 [取消訂用帳戶]。

## <a name="next-steps"></a>後續步驟

[Power BI 定價頁面](https://powerbi.microsoft.com/pricing/)
[Power BI Premium 計算機](https://powerbi.microsoft.com/calculator/)
[什麼是 Power BI Premium？](service-premium.md)
[Power BI Premium 問與答](service-premium-faq.md)
[Microsoft Power BI Premium 白皮書](https://aka.ms/pbipremiumwhitepaper)
[規劃 Power BI Enterprise 部署白皮書](https://aka.ms/pbienterprisedeploy)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)