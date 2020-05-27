---
title: 連線到 Power BI 工作區 OneDrive 中的檔案
description: 了解如何儲存和連線到 Power BI 工作區 OneDrive 上的 Excel、CSV 和 Power BI Desktop 檔案。
author: maggiesMSFT
ms.reviewer: lukasz
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 180fd8d451be794070d8b0f4d37c40965671d23d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "73854868"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-workspace"></a>連線到儲存在 Power BI 工作區 OneDrive 中的檔案
[在 Power BI 中建立工作區](service-create-distribute-apps.md)後，即可將 Excel、CSV 及 Power BI Desktop 檔案儲存至 Power BI 工作區的商務用 OneDrive。 您可以繼續更新儲存在 OneDrive 中的檔案。 這些更新會自動反映到以這些檔案為基礎的 Power BI 報表和儀表板中。 

> [!NOTE]
> 新工作區體驗會變更 Power BI 工作區與 Office 365 群組之間的關聯性。 每次建立一個新的工作區時，不會自動建立 Office 365 群組。 了解如何[建立新的工作區](service-create-the-new-workspaces.md)

將檔案新增至工作區是兩步驟的程序： 

1. 首先，請[將檔案上傳至工作區的商務用 OneDrive](service-connect-to-files-in-app-workspace-onedrive-for-business.md#1-upload-files-to-the-onedrive-for-business-for-your-workspace)。
2. 然後您[從 Power BI 連接至這些檔案](service-connect-to-files-in-app-workspace-onedrive-for-business.md#2-import-excel-files-as-datasets-or-as-excel-online-workbooks)。

> [!NOTE]
> 僅 [Power BI Pro](service-features-license-type.md) 提供工作區。
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 將檔案上傳至工作區的商務用 OneDrive
1. 在 Power BI 服務中，選取工作區旁的箭號 > 選取工作區名稱旁邊的省略符號 ( **...** )。 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. 選取 [檔案]  開啟 Office 365 工作區的商務用 OneDrive。
   
   > [!NOTE]
   > 如果在工作區功能表上看不到 [檔案]  ，請選取 [成員]  以開啟工作區的商務用 OneDrive。 在該處選取 [檔案]  。 Office 365 會設定應用程式群組工作區檔案的 OneDrive 儲存位置。 此程序可能需要一些時間。 
   > 
   > 
3. 您可以在這裡將檔案上傳至工作區的商務用 OneDrive。 選取 [上傳]  ，並瀏覽至您的檔案。
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 將 Excel 檔案匯入為資料集或 Excel Online 活頁簿
既然檔案已在工作區的商務用 OneDrive 中，即可進行選擇。 您可以： 

* [將 Excel 活頁簿中的資料以資料集匯入](service-get-data-from-files.md)。 然後使用此資料建置可在網頁瀏覽器和行動裝置上檢視的報表和儀表板。
* 或者[連接到 Power BI 的完整 Excel 活頁簿](service-excel-workbook-files.md)，讓其顯示畫面完全與在 Excel Online 一樣。

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>匯入或連線至工作區中的檔案
1. 在 Power BI 中，切換至工作區，讓工作區名稱顯示於左上角。 
2. 選取導覽窗格底部的 [取得資料]  。 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. 在 [檔案]  方塊中選取 [取得]  。
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. 選取 [OneDrive - <工作區名稱>]。
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. 選取您想要的檔案 > [連接]  。
   
    此時您需決定是要[從 Excel 活頁簿匯入資料](service-get-data-from-files.md)，或[連線至整個 Excel 活頁簿](service-excel-workbook-files.md)。
6. 選取 [匯入]  或 [連接]  。
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. 如果您選取 [匯入]  ，則活頁簿會出現在 [資料集]  索引標籤中。 
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    如果您選取 [連線]  ，則活頁簿會出現在 [活頁簿]  索引標籤中。
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>後續步驟
* [在 Power BI 中建立應用程式和工作區](service-create-distribute-apps.md)
* [從 Excel 活頁簿匯入資料](service-get-data-from-files.md)
* [連接至整個 Excel 活頁簿](service-excel-workbook-files.md)
* 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
* 想提出意見反應嗎？ 請前往 [Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi)

