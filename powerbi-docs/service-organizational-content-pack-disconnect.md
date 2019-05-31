---
title: 與組織內容套件中斷連接 - Power BI
description: 了解如何藉由刪除 Power BI 中內容套件的資料集來移除組織內容套件的連線。
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d4c9e6a925a783d810bc4d097ec18806c3d33d99
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61226539"
---
# <a name="remove-your-connection-to-a-power-bi-organizational-content-pack"></a>移除與 Power BI 組織內容套件的連接

> [!NOTE]
> 您無法在新的工作區體驗預覽中建立組織內容套件或加以安裝。 如果您尚未開始，現在是將您的內容套件升級為應用程式的好時機。 深入了解[新的工作區體驗](service-create-the-new-workspaces.md)。
> 

假設有位同事建立了內容套件， 您在 AppSource 中找到了該套件，並將其新增到您的 Power BI 工作區中。 現在，您不再需要該套件了。  該如何移除呢？

若要移除內容套件，請移除其資料集。  

* 在左方瀏覽窗格中，選取資料集右方的省略符號，然後選取 [移除] **\> [是]** 。  
  
  ![移除內容套件](media/service-organizational-content-pack-disconnect/power-bi-remove-organizational-content-pack-dataset.png)

移除資料集的同時，也會移除所有相關聯的報表和儀表板。 不過，移除與內容套件的連線並不會從組織的 AppSource 中刪除該內容套件。  您可以隨時回到 AppSource，將內容套件再次新增回工作區。 如果您是內容套件建立者，就只能[從 AppSource 中刪除內容套件](service-organizational-content-pack-manage-update-delete.md)。

## <a name="next-steps"></a>後續步驟
* [組織內容套件簡介](service-organizational-content-pack-introduction.md) 
* [在 Power BI 中建立和散發應用程式](service-create-distribute-apps.md) 
* [Power BI 基本概念](consumer/end-user-basic-concepts.md)  
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

