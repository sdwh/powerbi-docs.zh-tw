---
title: Azure SQL Database 排程重新整理疑難排解
description: Power BI 中的 Azure SQL Database 排程重新整理疑難排解
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 292f80b4fec7da9ff6ce42e3611bf4d6353bae2d
ms.sourcegitcommit: 90bd747b7c460d17b74cd386d3f5714234b1f6c9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74791960"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Power BI 中的 Azure SQL Database 排程重新整理疑難排解

如需重新整理的詳細資訊，請參閱[重新整理 Power BI 中的資料](refresh-data.md)及[設定排程的重新整理](refresh-scheduled-refresh.md)。

當您設定 Azure SQL 資料庫的排程重新整理時，如果在編輯認證時收到錯誤碼 400 的錯誤，請嘗試下列步驟以設定適當的防火牆規則：

1. 登入 [Azure 入口網站](https://portal.azure.com)。

1. 移至您要設定重新整理的 Azure SQL 資料庫。

1. 在 [概觀]  刀鋒視窗頂端，選取 [設定伺服器防火牆]  。

1. 在 [防火牆設定]  刀鋒視窗上，確定 [允許存取 Azure 服務]  已設定為 [開啟]  。

    ![Azure 所允許的服務](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
