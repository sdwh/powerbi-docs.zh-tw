---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621584"
---
服務主體是一種驗證方法，可用來讓 Azure AD 應用程式存取 Power BI 服務內容和 API。

當您建立 Azure Active Directory (Azure AD) 應用程式時，會建立[服務主體物件](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)。 服務主體物件 (也稱為「服務主體」  ) 可讓 Azure AD 驗證您的應用程式。 經過驗證之後，應用程式就可以存取 Azure AD 租用戶資源。

若要進行驗證，服務主體會使用 Azure AD 應用程式的「應用程式識別碼」  ，以及下列其中一項：
* 應用程式祕密
* 憑證