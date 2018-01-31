---
title: "管理員如何管理 Power BI Desktop 登入表單"
description: "了解開啟 Power BI Desktop 時，如何管理初始登入表單。"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 519f8b56b5086292addf577d969a707a6d6efcc8
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>系統管理員如何管理 Power BI Desktop 登入表單
Power BI Desktop 第一次啟動時，會顯示登入表單。 您可以填入資訊，或登入 Power BI 以繼續。 系統管理員可以使用登錄機碼來管理此表單。 

![Power BI desktop 的初始登入表單](media/desktop-admin-sign-in-form/sign-in-form.png)

系統管理員可以使用下列登錄機碼停用登入表單。 這也可以使用全域原則推送到全組織。

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

0 值會停用對話方塊。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

