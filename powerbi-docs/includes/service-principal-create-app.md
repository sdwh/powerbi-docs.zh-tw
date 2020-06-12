---
title: 服務主體建立應用程式
description: 服務主體建立應用程式
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315746"
---
1. 登入 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜尋 [應用程式註冊]，然後按一下 [應用程式註冊] 連結。

    ![azure 應用程式註冊](media/embedded-service-principal/azure-app-registration.png)

3. 按一下 [新增註冊]。

    ![新增註冊](media/embedded-service-principal/new-registration.png)

4. 填寫必要資訊：
    * **名稱** - 輸入應用程式的名稱
    * **支援的帳戶類型** - 選取支援的帳戶類型
    * (選擇性) **重新導向 URI** - 必要時輸入 URI

5. 按一下 [註冊] 。

6. 註冊之後，您可以從 [概觀] 索引標籤取得「應用程式識別碼」。複製並儲存「應用程式識別碼」以供稍後使用。

    ![應用程式識別碼](media/embedded-service-principal/application-id.png)