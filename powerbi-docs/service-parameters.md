---
title: 檢視和編輯 Power BI 服務中的資料集參數設定
description: 查詢參數會在 Power BI Desktop 中建立，但可以在 Power BI 服務中檢閱及更新
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: ac271e8013bce5824931153351a651644a716a2f
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965151"
---
# <a name="what-is-a-query-parameter"></a>什麼是查詢參數？
報表建立者會在 Power BI Desktop 中新增查詢參數。 參數允許他們讓報表的各部分根據一或多個參數「值」。 例如，報表建立者可能會建立將資料限制為單一國家/區域的參數或定義可接受欄位格式的參數 (例如日期、時間和文字)。

![[常用] 索引標籤顯示 Desktop 中的 [管理參數] 選項](media/service-parameters/power-bi-manage-parameters.png)


## <a name="review-and-edit-parameters-in-power-bi-service"></a>檢閱和編輯 Power BI 服務中的參數

在 Desktop 中定義參數之後，將該[報表發佈至 Power BI 服務](desktop-upload-desktop-files.md)時，參數設定和選取項目會與該報表一起移動。 有些參數設定可以在 Power BI 服務中檢閱和編輯，但不是限制可用資料的參數，而是定義和描述可接受值的參數。

1. 在 Power BI 服務中，選取齒輪圖示 ![齒輪圖示](media/service-parameters/power-bi-cog.png) 以開啟 [設定]。

2. 選取 [資料集] 的索引標籤，並醒目提示清單中的資料集。 
    
    ![設定已選取 [資料集] 索引標籤的視窗](media/service-parameters/power-bi-select-dataset2.png)

3. 展開 [參數]。  如果選取的資料集沒有參數，則您會看到訊息，內含深入了解查詢參數的連結。 但是，如果資料集具有參數，則展開 [參數] 標題會顯示這些參數。 

    ![已展開 [參數] 的 [設定] 視窗](media/service-parameters/power-bi-settings.png)

    檢閱參數設定，並在必要時變更。 灰色欄位不可編輯。 


## <a name="next-steps"></a>後續步驟
新增簡單參數的臨機操作方式為[修改 URL](service-url-filters.md)。