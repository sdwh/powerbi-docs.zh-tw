---
title: 刪除儀表板、報表、活頁簿、資料集或工作區
description: 了解如何刪除 Power BI 中的絶大部分所有項目
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 09/11/2018
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: 770b2796eb8f29cadfe8371cb2baef12cec7c0e8
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2018
ms.locfileid: "48909518"
---
# <a name="delete-almost-anything-in-power-bi-service"></a>刪除 Power BI 服務中的絶大部分所有項目
本文會教導您如何刪除 Power BI 服務中的儀表板、報告、活頁簿、資料集、應用程式、視覺效果和工作區。

## <a name="delete-a-dashboard"></a>刪除儀表板
儀表板可以移除。 移除儀表板並不會刪除基礎資料集，或任何與該儀表板相關聯的報表。

* 如果您是儀表板的擁有者，就可刪除它。 如果您正與同事共用儀表板，則從您的 Power BI 工作區移除儀表板將會從他們的 Power BI 工作區移除該儀表板。
* 如果是別人提供您共用的儀表板，而您不想再看見它，您可以移除它。  移除儀表板並不是把它從其他人的 Power BI 工作區中移除。
* 如果儀表板屬於[組織內容套件](service-organizational-content-pack-disconnect.md)，則移除相關聯的資料集將是移除它的唯一方法。

### <a name="to-delete-a-dashboard"></a>刪除儀表板
1. 在工作區中，選取 [儀表板] 索引標籤。
2. 找到要刪除的儀表板，然後選取刪除圖示 ![刪除圖示](media/service-delete/power-bi-delete-icon.png).

    ![影片](media/service-delete/power-bi-delete-dash.gif)

## <a name="delete-a-report"></a>刪除報表
別擔心，刪除報表不會刪除報表所依據的資料集。  您從報表釘選的所有視覺效果也安全無虞：它們會保留在儀表板上，直到您個別加以刪除。

### <a name="to-delete-a-report"></a>刪除報表
1. 在工作區中，選取 [報表] 索引標籤。
2. 找到要刪除的報表，然後選取刪除圖示   ![刪除圖示](media/service-delete/power-bi-delete-icon.png).   

    ![工作區的報表索引標籤](media/service-delete/power-bi-delete-reportnew.png)
3. 確認刪除。

   ![[刪除報表] 對話方塊](media/service-delete/power-bi-delete-report.png)

   > [!NOTE]
   > 如果報表是[內容套件](service-organizational-content-pack-introduction.md)的一部分，您就無法使用這個方法刪除它。  請參閱[移除與組織內容套件的連接](service-organizational-content-pack-disconnect.md)。
   >
   >

## <a name="delete-a-workbook"></a>刪除活頁簿
活頁簿可以予以移除。 不過，移除活頁簿也會移除包含這個活頁簿資料的所有報表和儀表板磚。

如果活頁簿儲存在商務用 OneDrive 上，則從 Power BI 中刪除它並不會從 OneDrive 予以刪除。

### <a name="to-delete-a-workbook"></a>刪除活頁簿
1. 在工作區中，選取 [活頁簿] 索引標籤。
2. 找到要刪除的活頁簿，然後選取刪除 ![刪除圖示](media/service-delete/power-bi-delete-report2.png) 圖示。

    ![[活頁簿] 索引標籤](media/service-delete/power-bi-delete-workbooknew.png)
3. 確認刪除。

   ![[移除活頁簿] 對話方塊](media/service-delete/power-bi-delete-confirm.png)

## <a name="delete-a-dataset"></a>刪除資料集
資料集可以刪除。 不過，刪除資料集也會刪除包含該資料集資料的所有報告和儀表板圖格。

如果資料集是一或多個[組織內容套件](service-organizational-content-pack-disconnect.md)的一部分，則刪除它的唯一方式是從正在使用它的內容套件中予以移除，並等待處理，然後再嘗試進行刪除。

### <a name="to-delete-a-dataset"></a>刪除資料集
1. 在工作區中，選取 [資料集] 索引標籤。
2. 找到要刪除的資料集，然後選取省略符號 (...)。  

    ![[資料集] 索引標籤](media/service-delete/power-bi-delete-datasetnew.png)
3. 從下拉式清單中，選取 [刪除]。

   ![省略符號功能表](media/service-delete/power-bi-delete-datasetnew2.png)
4. 確認刪除。

   ![[刪除儀表板] 對話方塊](media/service-delete/power-bi-delete-dataset-confirm.png)

## <a name="delete-an-app-workspace"></a>刪除應用程式工作區
> [!WARNING]
> 當您建立應用程式工作區時，您會建立 Office 365 群組。 而當您刪除應用程式工作區時，您刪除的是該 Office 365 群組。 這表示該群組也會從其他 O365 產品 (例如 SharePoint 和 Microsoft Teams) 中予以刪除。
>
>

身為應用程式工作區作者，您可以將它刪除。 如果您已將應用程式發佈到整個組織，則刪除它時，也會刪除所有群組成員的相關聯應用程式，並從 AppSource 中予以移除。 刪除應用程式工作區與離開應用程式工作區不同。

### <a name="to-delete-an-app-workspace---if-you-are-an-admin"></a>刪除應用程式工作區 - 如果您是系統管理員
1. 從左側導覽中，選取 [工作區]

    ![應用程式工作區](media/service-delete/power-bi-delete-workspace.png)
2. 選取要刪除之工作區右邊的省略符號 (...)，然後選擇 [編輯工作區]。

   ![省略符號功能表 > [編輯工作區]](media/service-delete/power-bi-edit-workspace.png)
3. 在 [編輯工作區] 視窗中，選取 [刪除工作區] > [刪除]。

    ![刪除工作區](media/service-delete/power-bi-delete-workspace2.png)

### <a name="to-remove-an-app-workspace-from-your-list"></a>從清單中移除應用程式工作區
如果您不再想要成為應用程式工作區成員，則可以「離開」它，並將它從清單中移除。 保留工作區，會針對所有其他工作區成員將它保留在原地。  

> [!IMPORTANT]
> 如果您是應用程式工作區的唯一系統管理員，則 Power BI 不會允許您離開。
>
>

1. 請從您想要移除的應用程式工作區中啟動。
2. 在右上角選取省略符號 (...)，然後選擇 [Leave workspace]\(保留工作區) > 保留。

      ![離開工作區](media/service-delete/power-bi-leave-workspace.png)

   > [!NOTE]
   > 您在下拉式清單中看到的選項取決於您是該應用程式工作區的系統管理員還是成員。
   >
   >

## <a name="delete-or-remove-an-app"></a>刪除或移除應用程式
應用程式可以從應用程式清單頁面中輕鬆予以移除。 但只有應用程式系統管理員才能永久刪除應用程式。

### <a name="remove-an-app-from-your-app-list-page"></a>從應用程式清單頁面中移除應用程式
從應用程式清單頁面中刪除應用程式，並不會刪除其他成員的應用程式。

1. 在左側導覽中，選取 [應用程式] 以開啟應用程式清單頁面。
2. 將滑鼠游標移至要刪除的應用程式上方，然後選取刪除 ![](media/service-delete/power-bi-delete-report2.png) 圖示。

   ![選取 [應用程式]](media/service-delete/power-bi-delete-app.png)

   如果您不小心移除應用程式，則有數個選項可以進行復原。  您可以要求應用程式建立者重新傳送它、找到包含應用程式連結的原始電子郵件、檢查[通知中心](service-notification-center.md)以查看是否仍列出該應用程式的通知，或者檢查組織的 [AppSource](service-install-use-apps.md)。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
本文涵蓋如何刪除 Power BI 服務的主要建置組塊。 但您在 Power BI 中還有其他可刪除的項目。  

* [移除精選儀表板](service-dashboard-featured.md)
* [移除儀表板 (將儀表板移除最愛)](service-dashboard-favorite.md)
* [刪除報表頁面](service-delete.md)
* [刪除儀表板磚](service-dashboard-edit-tile.md)
* [刪除報表視覺效果](service-delete.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
