---
title: "從 Power BI Desktop 發行"
description: "從 Power BI Desktop 發行"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: ccf3f2a544276f3a641be3734fb2c48387706e69
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="publish-from-power-bi-desktop"></a>從 Power BI Desktop 發行
當您將 **Power BI Desktop** 檔案發行至 **Power BI 服務**時，模型中的資料和您在 [報表] 檢視中建立的任何報表，都會發行至 Power BI 工作區。 您會看到新的資料集具有相同名稱，以及在工作區導覽器中的所有報表。

從 **Power BI Desktop** 發行，以及在 Power BI 中使用 [取得資料] 來連接及上傳 **Power BI Desktop** 檔案，兩者效果相同。

> [!NOTE]
> 對報表 Power BI 所做的任何變更，例如加入、刪除或變更報表中的視覺效果，都不會儲存在原始的 **Power BI Desktop** 檔案中。
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>發佈 Power BI Desktop 資料集和報表
1. 在 Power BI Desktop12 \> [檔案]\> [發佈] \> [發佈至 Power BI]，或在功能區上按一下 [發佈]。  
   ![](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)
2. 登入 Power BI。

完成時，就會得到連結，用於在 Power BI 網站中開啟報表。  
    ![](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>重新發佈或取代從 Power BI Desktop 發佈的資料集
當您發行了 **Power BI Desktop** 檔案時，您在 **Power BI Desktop** 中建立的資料集和任何報表都會上傳至 Power BI 網站。 當您重新發行 **Power BI Desktop** 檔案時，會將 Power BI 網站中的資料集取代為 **Power BI Desktop** 檔案中更新過的資料集。

這很直接明瞭，但有幾件事您應該要知道：

* 如果在 Power BI 已經有兩個或多個資料集名稱與 **Power BI Desktop** 檔案名稱相同，則發行可能會失敗。 請確定在 Power BI 只有一個資料集具有相同名稱。 您也可以重新命名此檔案並發佈，建立與檔案同名的新資料集。
* 如果您重新命名或刪除資料行或量值，任何已存在於 Power BI 且具有該欄位的視覺效果都可能會無法使用。 
* Power BI 會忽略現有資料行的某些格式變更。 例如，如果您將資料行格式從 0.25 變更為 25%。
* 如果您已針對在 Power BI 中現有資料集設定重新整理排程，而您將新資料來源新增到檔案後重新發行，就必須在下次排定的重新整理之前，在 [管理資料來源] 中登入這些資源。

