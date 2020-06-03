---
title: 服務主體概觀
description: 服務主體概觀
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 8482278d9054228dedafb6bd1b37368f5a4b5dce
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315745"
---
服務主體是一種驗證方法，可用來讓 Azure AD 應用程式存取 Power BI 服務內容和 API。

當您建立 Azure Active Directory (Azure AD) 應用程式時，會建立[服務主體物件](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)。 服務主體物件 (也稱為「服務主體」  ) 可讓 Azure AD 驗證您的應用程式。 經過驗證之後，應用程式就可以存取 Azure AD 租用戶資源。

若要進行驗證，服務主體會使用 Azure AD 應用程式的「應用程式識別碼」  ，以及下列其中一項：

* 應用程式祕密
* 憑證