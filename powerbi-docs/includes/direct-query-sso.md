---
title: Include 檔案
description: Include 檔案
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82255833"
---
## <a name="single-sign-on"></a>單一登入

在將 Azure SQL DirectQuery 資料集發佈至服務之後，即可使用 Azure Active Directory (Azure AD) OAuth2 來為終端使用者啟用單一登入 (SSO)。

若要啟用 SSO，請移至資料集、開啟 [資料來源]  索引標籤，然後檢查 [SSO] 方塊。

![設定 Azure SQL DQ 對話方塊](media/direct-query-sso/sso-dialog.png)

若已啟用 SSO 選項，且使用者存取在資料來源上建立的報表，Power BI 會在對 Azure SQL 資料庫或資料倉儲的查詢中，傳送其已驗證的 Azure AD 認證。 此選項可讓 Power BI 遵從在資料來源層級所設定的安全性設定。

SSO 選項會在使用此資料來源的所有資料集中生效。 它不會影響用於匯入案例的驗證方法。

