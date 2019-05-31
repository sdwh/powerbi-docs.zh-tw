---
title: 篩選報表，並與同事-Power BI 共用
description: 了解如何篩選 Power BI 報表並與組織中的同事共用。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770690"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>篩選 Power BI 報表，並與同事共用
「共用」  是讓一些人存取您儀表板和報表的一種好方法。 如果要共用報表的篩選版本呢？ 可能是只顯示特定城市或特定銷售人員或特定年份等資料的報表。 請嘗試篩選報表和共用，或建立自訂的 URL。 當收件者第一次開啟報表時，將會篩選報表。 收件者可以修改 URL，以移除篩選條件。 

Power BI 還提供[數種其他方式可進行共同作業及散發您的報表](service-how-to-collaborate-distribute-dashboards-reports.md)。 若要共用，您和您的收件者必須具有 [Power BI Pro 授權](service-features-license-type.md)，或內容必須位於[進階容量](service-premium-what-is.md)中。 

## <a name="two-ways-to-filter-a-report"></a>兩種方式來篩選報表

### <a name="set-a-filter"></a>設定篩選

在 [[編輯檢視]](consumer/end-user-reading-view.md) 中開啟報告，套用篩選條件，然後儲存報告。
   
在本例中，我們要篩選[零售分析範例](sample-tutorial-connect-to-the-samples.md)，只顯示 **Territory** 等於 **NC** 的值。
   
![報表篩選窗格](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>在 URL 中建立篩選器

在報表頁面 URL 的結尾處新增下列內容︰
   
?filter=<資料表名稱>  /<檔案名稱>  eq <值> 
   
欄位必須是類型的號碼、 datetime 或字串。 *tablename* 或 *fieldname* 值不能包含空格。
   
在本例中，資料表的名稱是 **Store**、欄位名稱是 **Territory**，要篩選的值是 **NC**：
   
?filter=Store/Territory eq 'NC'
   
![已篩選的報表 URL](media/service-share-reports/power-bi-filter-url3.png)
   
瀏覽器會新增特殊字元來代表斜線、空格和單引號，因此最後會是︰
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

請參閱文章[在 URL 中使用查詢字串參數篩選報表](service-url-filters.md)的更多詳細資料。

## <a name="share-the-filtered-report"></a>共用已篩選的報表

1. 當您[共用報表](service-share-dashboards.md)，清除**傳送給收件者的電子郵件通知**核取方塊。

    ![共用報表對話方塊](media/service-share-reports/power-bi-share-report-dialog.png)

4. 傳送含有您先前所建立篩選的連結。

## <a name="next-steps"></a>後續步驟
* 有任何意見嗎？ 請移駕 [Power BI 社群網站](https://community.powerbi.com/)提供您的建議。
* [應該如何共同作業和共用儀表板和報表？](service-how-to-collaborate-distribute-dashboards-reports.md)
* [共用儀表板](service-share-dashboards.md)
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)。

