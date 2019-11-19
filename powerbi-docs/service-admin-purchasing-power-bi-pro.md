---
title: 購買及指派 Power BI Pro 授權
description: 了解如何購買及指派 Power BI Pro 使用者授權，讓您的使用者可以存取 Power BI 服務中的內容，並在其中與同事共同作業。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 31739cee4371a8991f8c88e6ba67bfb48878a33c
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73431402"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>購買及指派 Power BI Pro 使用者授權

Power BI Pro 是一種個別使用者授權，可允許使用者讀取及和其他使用者在 Power BI 服務中發佈的報表與儀表板互動，並與其他 Power BI Pro 使用者共用內容和共同作業。 只有具備 Power BI Pro 使用者授權的使用者才能發佈或和其他使用者共用內容，或取用由其他使用者建立的內容，除非該內容是裝載在 Power BI Premium 容量中。 如需詳細資訊，請參閱[依授權類型排列的 Power BI 功能](service-features-license-type.md)。

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>購買及指派 Power BI Pro 使用者授權

本文說明如何在 Microsoft 365 系統管理中心中購買 Power BI Pro 使用者授權，接著會說明系統管理員用來將那些授權指派給個別使用者時的兩個選項：在 Microsoft 365 系統管理中心及 Azure 入口網站 (選擇一個選項)。

### <a name="prerequisites"></a>先決條件

若要在 Microsoft 365 系統管理中心內購買和指派授權，您必須是 Microsoft 365 中 **[全域管理員或計費管理員](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** 角色的成員。

若要在 Azure 入口網站中指派授權，您必須是 Power BI 針對 Azure Active Directory 查閱所使用 Azure 訂用帳戶的擁有者。

### <a name="purchase-licenses-in-microsoft-365"></a>在 Microsoft 365 中購買授權

請遵循下列步驟以在 Microsoft 365 系統管理中心內購買 Power BI Pro 授權：

1. 開啟 [MIcrosoft 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)。

2. 在左邊的瀏覽窗格中，選取 [帳單]   > [訂閱]  。

    ![[瀏覽] 窗格](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. 在 [訂閱]  頁面的右上角，選取 [新增訂閱]  。

    ![訂用帳戶](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. 找出所需的訂閱供應項目：

    在 [企業套件]  下方，選取 [Office 365 Enterprise E5]  。

    ![Office E5 訂閱](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    在 [其他方案]  下，選取 [Power BI Pro]  。

    ![Power BI 訂用帳戶](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. 將滑鼠停留在所需訂閱的省略符號 ( **. . .** ) 上方，然後選取 [立即購買]  。

    ![立即購買](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. 根據您的計費喜好設定，選擇 [按月支付]  或 [支付全年費用]  。

7. 在 [您想要多少使用者?]  下，輸入所需的授權數目，然後選取 [立即結帳]  以完成交易。

8. 確認所取得的訂閱現在會列於 [訂閱]  頁面上。

   ![已取得的訂閱](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. 若要在初次購買之後新增更多授權，請從 [訂閱]  頁面選取 [Power BI Pro]  ，然後取 [新增/移除授權]  。

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 系統管理中心內指派授權

按照以下步驟操作，將 Power BI Pro 授權指派給個別使用者帳戶：

1. 開啟 [MIcrosoft 365 系統管理中心](https://portal.office.com/adminportal/home#/homepage)。

2. 在左側瀏覽窗格中，展開 [使用者]  ，然後選取 [作用中使用者]  。

    ![作用中使用者](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. 選取使用者，然後在 [產品授權]  下方，選取 [編輯]  。

    ![編輯產品授權](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. 在 [Power BI Pro]  下方，將設定切換成 [開啟]  ，然後選取 [儲存]  。

    ![已開啟的產品授權](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. 在所選取帳戶的 [狀態]  下方，確認已成功指派 Power BI Pro 授權。

    ![確認授權狀態](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>在 Azure 入口網站中指派授權

按照以下步驟操作，將 Power BI Pro 授權指派給個別使用者帳戶：

1. 開啟 [Azure 入口網站](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0)。

2. 在左側的導覽列中，選取 [Azure Active Directory]  。

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. 在 [Azure Active Directory]  下方，選取 [授權]  。

    ![授權](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. 在 [授權]  下方，選取 [所有產品]  ，然後選取 [Power BI Pro]  以顯示已授權使用者的清單。

    ![授權 - 所有產品](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. 選取 [指派]  來將 Power BI Pro 授權新增至使用者帳戶。

    ![指派授權](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>後續步驟

您現在已經指派授權，接著可以深入了解 Power BI Pro。

[組織中的 Power BI 授權](service-admin-licensing-organization.md)

[尋找已登入的 Power BI 使用者](service-admin-access-usage.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
