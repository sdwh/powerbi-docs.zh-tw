---
title: Power BI 行動版 Windows 應用程式的單一登入
description: 閱讀 Power BI 行動版 Windows 應用程式的單一登入 (SSO) 相關資訊。 SSO 表示您只要以單一使用者帳戶登入一次，就可以存取執行業務所需的所有應用程式和資源。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: mshenhav
ms.openlocfilehash: fdbdebacc2ae41cdfa8296eb6b0c06e52f149cac
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2019
ms.locfileid: "61336836"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Power BI 行動版 Windows 應用程式的單一登入

閱讀 Power BI 行動版 Windows 應用程式的單一登入 (SSO) 相關資訊。 SSO 表示您只要以單一使用者帳戶登入一次，即可存取執行業務所需的所有應用程式和資源。 登入之後，您就能存取所有應用程式，而不需要再次進行驗證。 

由於 Power BI 的 Windows 應用程式已整合到 Azure Active Directory 中，因此您不僅可以使用主要組織帳戶登入已加入網域的裝置，還可以登入 Power BI 服務。 如果您正在 Windows 手機上檢視 Power BI，請確定您用於 Power BI 之帳戶已設定為裝置設定中的工作或學校帳戶。  

只有 Windows Azure Active Directory 所管理的 Windows 裝置才會啟用 SSO。 

## <a name="sign-in-with-sso"></a>使用 SSO 登入

若要簡化登入程序，當您第一次安裝應用程式時，應用程式會自動嘗試使用 SSO，向 Power BI 服務對您進行驗證。 只有此程序不成功時，應用程式才會要求您提供 Power BI 的認證。  

如果您已經使用 Power BI for Windows 行動裝置應用程式，在升級至新版的應用程式時，您也可以使用 SSO。 登出應用程式並關閉它，然後重新開啟該應用程式。 當應用程式重新開啟時，它會自動嘗試使用您目前的 Windows 認證，針對 Power BI 服務進行驗證。 

如果您不想要使用目前的 Windows 使用中工作階段認證來登入 Power BI，只需移至 [設定]  並登出，然後使用不同的認證登入。 
 
## <a name="next-steps"></a>後續步驟

- [開始使用 Power BI for Windows 10 行動裝置 App](mobile-windows-10-phone-app-get-started.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

