---
title: 具有 DirectQuery 的 Azure SQL Database
description: 具有 DirectQuery 的 Azure SQL Database
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/20/2018
LocalizationGroup: Data from databases
ms.openlocfilehash: 5365c076b75d0989df8db15c1dc16f4e11bc3f09
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448365"
---
# <a name="azure-sql-database-with-directquery"></a>具有 DirectQuery 的 Azure SQL Database

了解如何直接連線至 Azure SQL Database 及建立使用即時資料的報表。 您可以將您的資料保留在來源，而不是在 Power BI 中。

藉由 DirectQuery，當您瀏覽報表檢視中的資料時，會將查詢傳送至您的 Azure SQL Database。 對於熟悉所連接資料庫與實體的使用者，會推薦這種做法。

**注意：**

* 連接時請指定完整的伺服器名稱 (請參閱以下以取得詳細資料)
* 請確定已將資料庫的防火牆規則設定為 [[允許存取 Azure 服務](https://msdn.microsoft.com/library/azure/ee621782.aspx)]
* 例如選取資料行或加入篩選器的每一個動作，都會傳送查詢回資料庫
* 圖格會每小時重新整理 (重新整理不需要排程)。 當您連接時，這可以在 [進階] 設定中調整。
* 問與答不能用於 DirectQuery 資料集
* 不會自動挑選結構描述變更

隨著我們持續改善這些體驗，這些限制和備註可能會變更。 連接的步驟如下所述。

> [!Important]
> 我們已改善與 Azure SQL Database 的連線。  若要獲得連線至 Azure SQL Database 資料來源的最佳體驗，請使用 Power BI Desktop。  在您建置模型和報表之後，即可將它發佈至 Power BI 服務。  現在已取代 Power BI 服務中 Azure SQL Database 的直接連接器。

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop 和 DirectQuery

您必須使用 Power BI Desktop，才能連線到使用 DirectQuery 的 Azure SQL Database。 這個方法提供額外的彈性與功能。 使用 Power BI Desktop 建立的報表可以發行至 Power BI 服務。 您可以深入了解如何在 Power BI Desktop 中連線到 [ DirectQuery 的 Azure SQL Database](desktop-use-directquery.md)。

## <a name="finding-parameter-values"></a>尋找參數值

在 Azure 入口網站中可以找到您完整的伺服器名稱與資料庫名稱。

![新的 Azure 連接埠更新](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Azure 入口網站更新](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>後續步驟

* [在 Power BI Desktop 中使用 DirectQuery](desktop-use-directquery.md)  
* [Power BI 是什麼？](power-bi-overview.md)  
* [取得 Power BI 的資料](service-get-data.md)  

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
