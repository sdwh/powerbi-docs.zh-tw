---
title: 了解 Power BI Desktop 的資料列層級安全性 (RLS)
description: 如何在 Power BI Desktop 內，為匯入的資料集和 DirectQuery 設定資料列層級安全性。
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/03/2018
ms.author: maghan
LocalizationGroup: Create reports
ms.openlocfilehash: 022668737f6bcce987b2923ba7a4416f4a08460a
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>使用 Power BI Desktop 的資料列層級安全性 (RLS)
使用 Power BI Desktop 的資料列層級安全性 (RLS) 可限制指定使用者的資料存取。 篩選會限制資料列層級的資料。 您可以在角色中定義篩選。

您現在可以使用 Power BI Desktop 為匯入 Power BI 的資料模型設定 RLS。 您也可以針對使用 DirectQuery (如 SQL Server) 的資料集設定 RLS。 先前，您只能夠在 Power BI 外部的內部部署 Analysis Services 模型實作 RLS。 您可以在內部部署模型上，為 Analysis Services 即時連線設定資料列層級安全性。 即時連線資料集不會顯示安全性選項。

> [!IMPORTANT]
> 如果您在 Power BI 服務中定義角色與規則，就必須在 Power BI Desktop 中重新建立這些角色，並將報表發佈至服務。
> 
> 

深入了解 [Power BI 服務內的 RLS](service-admin-rls.md) 的選項。

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>後續步驟
[使用 Power BI 服務的資料列層級安全性 (RLS)](service-admin-rls.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

