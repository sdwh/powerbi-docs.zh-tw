---
title: 將編頁報表發佈至 Power BI 服務 | Microsoft Docs
description: 在此教學課程中，您將了解如何從本機電腦上傳編頁報表，以將該報表發佈至 Power BI 服務。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: 6f2d1a4e4de87ea6eb63826b59286a9abd54b94f
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "51266827"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>將編頁報表發佈至 Power BI 服務

在此文章中，您將了解如何從本機電腦上傳編頁報表，以將該報表發佈至 Power BI 服務。 只要工作區位於 Premium 容量，您就可以將編頁報表上傳到 [我的工作區] 或任何其他工作區。 尋找工作區名稱旁邊的鑽石圖示 ![Power BI Premium 容量鑽石圖示](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) (在工作區名稱旁邊)。 

如果您的報表資料來源位於內部部署，則需在上傳報表之後[建立閘道](#create-a-gateway-to-an-on-premises-data-source)。

## <a name="add-a-workspace-to-a-premium-capacity"></a>將工作區新增至 Premium 容量

如果工作區的名稱旁邊沒有鑽石圖示 ![Power BI Premium 容量鑽石圖示](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ，則您需要將該工作區新增至 Premium 容量。 

1. 選取 [工作區]、選取工作區名稱旁邊的省略符號 **...**，然後選取 [編輯工作區]。

    ![選取 [編輯工作區]](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. 在 [編輯工作區] 對話方塊中，展開 [進階]，然後將 [專用容量] 滑動至 [開啟]。

    ![選取 [專用容量]](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   您可能無法變更它。 如果沒有，則連絡您的 Power BI Premium 容量管理員，以為您提供指派權限來將您的工作區新增至 Premium 容量。


## <a name="upload-a-paginated-report"></a>上傳編頁報表

1. 在報表產生器中建立編頁報表，然後將它儲存到本機電腦。

1. 在瀏覽器中開啟 Power BI 服務，然後瀏覽至您想要在其中發佈報表的 Premium 工作區。 請注意工作區名稱旁邊的鑽石圖示 ![Power BI Premium 容量鑽石圖示](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) 。 

1. 選取 [取得資料]。

    ![Power BI 中的 [取得資料]](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. 在 [檔案]  方塊中選取 [取得] 。

    ![Power BI 中的 [取得檔案]](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. 選取 [本機檔案] > 瀏覽至編頁報表 > [開啟]。

    ![選取 [本機檔案]](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. 選取 [繼續] > [編輯認證]。

    ![選取 [編輯認證]](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. 設定您的認證 > [登入]。

    ![編輯認證](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   您會在報表清單中看到您的報表。

    ![報表清單中的編頁報表](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. 選取該報表以在 Power BI 服務中開啟它。 如果報表具有參數，則您需要選取它們，才能檢視該報表。
 
    ![選取參數](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>建立閘道

就像任何其他 Power BI 報表，如果報表資料來源位於內部部署，則您需要建立或連線至閘道，才能存取資料。

1. 在報表名稱旁邊，選取 [管理]。

   ![管理編頁報表](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. 如需詳細資料和後續步驟，請參閱 Power BI 服務文章：[安裝閘道](service-gateway-install.md)。

### <a name="gateway-limitations"></a>閘道限制

閘道目前不支援多重值參數。


## <a name="next-steps"></a>後續步驟

- [檢視 Power BI 服務中的編頁報表](paginated-reports-view-power-bi-service.md)
- [什麼是 Power BI Premium 中的編頁報表？(預覽)](paginated-reports-report-builder-power-bi.md)

