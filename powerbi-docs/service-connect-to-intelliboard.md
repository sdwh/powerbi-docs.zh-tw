---
title: 使用 Power BI 連接到 IntelliBoard
description: IntelliBoard for Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 06fc561d3fbe07cbf553be63c7b19de3ab11992e
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060947"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>使用 Power BI 連接到 IntelliBoard
IntelliBoard 透過 Reporting Services 提供對您 Moodle 學習管理系統資料的簡化存取方式。 Power BI 的 IntelliBoard 內容套件提供額外的分析，包括您的課程、註冊的使用者、整體績效和 LMS 活動的度量。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

連接到 Power BI 的 [IntelliBoard 內容套件](https://app.powerbi.com/getdata/services/intelliboard)。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. 在 [服務]  方塊中，選取 [取得]  。  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. 選取 [IntelliBoard]  ，然後選取 [取得]  。  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. 選取 [OAuth 2]  ，然後 [登入]  。 出現提示時，提供您的 IntelliBoard 認證。
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. 連接後，會自動載入儀表板、報表和資料集。 完成時，圖格會更新為您 IntelliBoard 帳戶中的資料。
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](consumer/end-user-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](consumer/end-user-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理]  視需要嘗試重新整理

## <a name="whats-included"></a>包含的內容
此內容套件包含下列資料表中的資料：  

    - 活動  
    - Agents  
    - Auth  
    - 國家/地區  
    - CoursesProgress  
    - Enrollments
    - Lang  
    - Platform  
    - Totals  
    - UsersProgress    

## <a name="system-requirements"></a>系統需求
需要有具備上述資料表權限的 IntelliBoard 帳戶，才能具現化此內容套件。

## <a name="next-steps"></a>後續步驟
[Power BI 是什麼？](fundamentals/power-bi-overview.md)

[Power BI 服務中的設計工具基本概念](service-basic-concepts.md)

