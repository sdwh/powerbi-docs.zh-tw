---
title: 使用 Power BI 連接到 IntelliBoard
description: IntelliBoard for Power BI
services: powerbi
documentationcenter: ''
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d73a02e754615263a155d3a7e31e47af4b740fd8
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2018
---
# <a name="connect-to-intelliboard-with-power-bi"></a>使用 Power BI 連接到 IntelliBoard
IntelliBoard 透過 Reporting Services 簡化對 Moodle 學習管理系統的存取。 Power BI 的 IntelliBoard 內容套件提供額外的分析，包括您的課程、註冊的使用者、整體績效和 LMS 活動的度量。

連接到 Power BI 的 [IntelliBoard 內容套件](https://app.powerbi.com/getdata/services/intelliboard)。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. 在 [服務]  方塊中，選取 [取得] 。  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. 選取 [IntelliBoard]，然後選取 [取得]。  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. 選取 [OAuth 2]，然後 [登入]。 出現提示時，提供您的 IntelliBoard 認證。
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. 連接後，會自動載入儀表板、報表和資料集。 完成時，圖格會更新為您 IntelliBoard 帳戶中的資料。
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](power-bi-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

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
[開始使用 Power BI](service-get-started.md)

[Power BI - 基本概念](service-basic-concepts.md)

