---
title: Include 檔案
description: Include 檔案
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: davidi
ms.openlocfilehash: eec30d11c1bd99271416ab1a3a2dbb581687e315
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698296"
---
## <a name="single-sign-on"></a>單一登入

在您將 Azure SQL DirectQuery 資料集發行至服務之後，您可以透過 Azure Active Directory (Azure AD) OAuth2 為終端使用者啟用單一登入 (SSO)。

若要啟用 SSO，請移至資料集、開啟 [資料來源]  索引標籤，然後檢查 [SSO] 方塊。

![設定 Azure SQL DQ 對話方塊](media/direct-query-sso/sso-dialog.png)

若已啟用 SSO 選項，且使用者存取在資料來源上建立的報表，Power BI 會在對 Azure SQL 資料庫或資料倉儲的查詢中，傳送其已驗證的 Azure AD 認證。 這可讓 Power BI 遵從在資料來源層級所設定的安全性設定。

SSO 選項會在使用此資料來源的所有資料集中生效。 它不會影響用於匯入案例的驗證方法。

> [!Note]
> 不支援 Azure Multi-Factor Authentication (MFA)。 想搭配 Azure SQL DirectQuery 使用 SSO 的使用者，必須自 MFA 中免除。