---
title: Power BI 封存工作區
description: 管理 Office 365 租用戶之後的 Power BI 封存工作區
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b9fcf1c6121c4aeecfdf948b77493f1f2a7f825
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34293620"
---
# <a name="power-bi-archived-workspace"></a>Power BI 封存工作區
任何人都可以透過 Power BI 在幾分鐘內完成註冊並開始使用服務。  稍後，您組織的 IT 部門可能會選擇代替組織中的使用者接管 Power BI。  如果發生這種接管情況，您不僅會因為集中管理組織內的使用者和權限而受益，也可以使用針對組織內其他服務所用的相同使用者名稱和密碼進行登入，因而簡化登入。 

您在 IT 部門開始管理 Power BI 之前所建立的任何內容都將置於 Power BI [封存工作區] 中，稍後可從 [Power BI](https://app.powerbi.com) 的左導覽列存取。  您應該在 [我的工作區] 中開始建立新的 Power BI 內容，這個工作區是由組織的 IT 部門保護及管理。  您的 [封存工作區] 會持續存在，但會限制您可以對 [封存工作區] 中的內容執行的動作。  若要移除這些限制，您必須將內容從 [封存工作區] 移轉至由 IT 部門管理的 [我的工作區]。

## <a name="restrictions-in-your-archived-workspace"></a>封存工作區的限制
封存工作區中的內容不會遭到刪除。  您可以繼續取得資料、建立報表和儀表板，以及重新整理資料集。  與您共用內容的現有使用者還是可以在自己的 [封存工作區] 中檢視內容。

不過，封存工作區中的內容有些限制：

* **商務用 OneDrive。**  您無法再從商務用 OneDrive 取得 [封存工作區] 中資料集的資料，或重新整理該資料集。  如果您嘗試連接到這個來源，您會收到警告。
* **共用儀表板。**  您無法與其他使用者共用 [封存工作區] 中的儀表板。  已經具有存取權的任何使用者可透過存取自己的 [封存工作區]，繼續檢視共用的儀表板。
* **建立群組。**  您無法在 [封存工作區] 中建立群組。
* **Power BI 行動應用程式的存取。**  您仍然可以檢視 [封存工作區] 中的網頁內容，但這份內容不會再出現於 Power BI 行動裝置應用程式中。

## <a name="migrating-content-in-your-archived-workspace"></a>移轉封存工作區中的內容
若要繼續使用 Power BI，您應該在由 IT 部門管理的 [我的工作區] 中建立新內容。   您也應該規劃將 [封存工作區] 中的任何內容移轉至 [我的工作區]。  移轉內容的方式取決於內容類型：

* **Excel 或 Power BI Desktop 資料集。**  移轉這些資料集的方式是從 [封存工作區] 切換至 [我的工作區]，然後按一下 [我的資料] 按鈕，以重新上傳 Excel 或 Power BI Desktop 檔案。  如果您已設定排程重新整理，您必須對 [我的工作區] 中的新資料集重新進行這些設定。
* **其他資料集。**  切換至 [我的工作區]，然後按一下 [取得資料] 按鈕，以重新連接到您在 [封存工作區] 中建立的其他任何資料集。  您可能需要重新輸入安全性或連接資訊。
* **報表。**  不論是包含在 Excel 或 Power BI Desktop 檔案中的報表，還是安裝作為內容套件一部分的報表，都會在您重新上傳對應的 Excel 或 Power BI Desktop 檔案，或者重新連接到內容套件時自動重新建立。  如果您透過 Power BI 服務建立自己的報表，則必須在 [我的工作區] 中重新建立這些報表。
* **儀表板。**  安裝作為內容套件一部分的儀表板，會在您重新連接到 [我的工作區] 中的內容套件時自動重新建立。  如果您透過 Power BI 服務建立自己的儀表板，則必須在 [我的工作區] 中重新建立這些儀表板。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

