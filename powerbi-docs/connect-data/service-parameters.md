---
title: 在 Power BI 服務中編輯參數設定
description: 查詢參數會在 Power BI Desktop 中建立，但可以在 Power BI 服務中檢閱及更新
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/04/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 3b64c1dd502fd16199fbff9f64cd2c017006d1f1
ms.sourcegitcommit: a7227f6d3236e6e0a7bc1f83ff6099b5cd58bff3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768466"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>在 Power BI 服務中編輯參數設定
報表建立者會在 Power BI Desktop 中將查詢參數新增至報表。 參數允許他們讓報表的各部分根據一或多個參數「值」  。 例如，報表建立者可能會建立將資料限制為單一國家/地區的參數，或定義可接受欄位格式的參數 (例如日期、時間和文字)。

![[常用] 索引標籤顯示 Desktop 中的 [管理參數] 選項](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>檢閱和編輯 Power BI 服務中的參數

身為報表建立者，您可在 Power BI Desktop 中定義參數。 當您[將該報表發佈至 Power BI 服務](../create-reports/desktop-upload-desktop-files.md)時，參數設定和選取範圍會隨之移動。 您可在 Power BI 服務中檢閱並編輯參數設定，但不能建立這些設定。

1. 在 Power BI 服務中，選取齒輪圖示 ![齒輪圖示](media/service-parameters/power-bi-cog.png) 以開啟 [設定]。

2. 選取 [資料集]  的索引標籤，並醒目提示清單中的資料集。 
    
    ![設定已選取 [資料集] 索引標籤的視窗](media/service-parameters/power-bi-select-dataset2.png)

3. 展開 [參數]  。  如果選取的資料集沒有參數，則會看到訊息，其包含深入了解查詢參數的連結。 如果資料集具有參數，則展開 [參數] 標題會顯示這些參數。 

    ![已展開 [參數] 的 [設定] 視窗](media/service-parameters/power-bi-settings.png)

    檢閱參數設定，並在必要時變更。 灰色欄位不可編輯。 


## <a name="next-steps"></a>後續步驟
新增簡單參數的臨機操作方式為[修改 URL](../collaborate-share/service-url-filters.md)。
