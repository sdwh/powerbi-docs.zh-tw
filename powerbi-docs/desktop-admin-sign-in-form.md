---
title: 管理員如何管理 Power BI Desktop 登入表單
description: 了解開啟 Power BI Desktop 時，如何管理初始登入表單。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/02/2018
ms.author: davidi
ms.openlocfilehash: f35553acd65aeea2c1bf02b04fcbd665af4b99ea
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721079"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>系統管理員如何管理 Power BI Desktop 登入表單
Power BI Desktop 第一次啟動時，會顯示登入表單。 您可以填入資訊，或登入 Power BI 以繼續。 系統管理員使用登錄機碼來管理此表單。 

![Power BI desktop 的初始登入表單](media/desktop-admin-sign-in-form/sign-in-form.png)

系統管理員使用下列登錄機碼停用登入表單。 這也可以使用全域原則推送到全組織。

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

0 值會停用對話方塊。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

