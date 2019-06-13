---
title: 複製其他工作區的報表 (預覽) - Power BI
description: 了解如何與整個組織的使用者共用資料集。 然後他們可以您的資料集為基礎，在自己的工作區中建置報表。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461457"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>複製其他工作區的報表 (預覽)

了解如何複製某個工作區的報表，將它儲存到不同的工作區。 然後您可以修改該報表，新增或刪除視覺效果和其他項目。

當您找到喜歡的報表時，您可在工作區或應用程式中複製它，然後按照您的需求修改它。 您不必擔心建立資料模型。 它已經為您建立。 修改現有的報表，比從頭開始還容易。

## <a name="save-a-copy-of-a-report"></a>儲存報表複本

1. 在應用程式或工作區中，移至 [報表] 清單檢視。

1. 在 [動作]  下選取 [儲存複本]  。

    ![儲存報表複本](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    如果報表位在新體驗工作區中，而您有[建置權限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)，您只會看到**儲存複本**圖示。 即使您可以存取該工作區，您也必須有資料集的建置權限。

3. 在 [儲存此報表的複本]  中，為報表命名，然後選取目的地工作區。

    ![儲存複本對話方塊](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    您可以將報表儲存在目前工作區或 Power BI 服務的其他工作區。 您只會看到您為所屬成員之新體驗工作區的工作區。
  
4. 選取 [儲存]  。

    當您儲存報表的複本時，您即建立資料集的即時連線，並以可用的完整資料集來開啟報表建立體驗。 您尚未製作資料集的複本。 資料集仍位在其原始位置。 您可以使用您報表的資料集中所有資料表和量值。 資料集的資料列層級安全性 (RLS) 限制已生效，因此您只會看到根據您 RLS 角色有權查看的資料。

    如果報表是以工作區外的資料集為基礎，則 Power BI 會自動在資料集清單中建立項目。 此資料集圖示和工作區資料集的圖示不同： ![共用的資料集圖示](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    如此一來，工作區成員就可以分辨哪些報表和儀表板使用工作區外的資料集。 此項目會顯示資料集的相關資訊以及少數選取動作。

    ![資料集動作](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>檢視相關資料集

當您的工作區中有報表時，您可能需要知道它以何資料集為本。

1. 在 [報表] 清單檢視中，選取 [檢視相關項目]  。

    ![檢視相關項目圖示](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. [相關內容]  對話方塊會顯示所有相關項目。 在此清單中，資料集彼此看起來都差不多。 您無法分辨它是否位在不同的工作區中。 此為已知問題。
 
    ![[相關內容] 對話方塊](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>後續步驟

- [跨工作區使用資料集 (預覽)](service-datasets-across-workspaces.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
