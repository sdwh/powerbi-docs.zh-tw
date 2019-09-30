---
title: 使用內部部署資料來源的單一登入 (SSO)
description: 設定您的閘道以啟用從 Power BI 到內部部署資料來源的單一登入 (SSO)。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4991117cfa8b34d9adbbd2dc29082d1e75b6852d
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71100393"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Power BI 中閘道的單一登入 (SSO) 概觀

您可以藉由使用 Kerberos 限制委派或安全性聲明標記語言 (SAML) 來設定內部部署資料閘道，以取得順暢的單一登入連線，讓 Power BI 報表和儀表板能夠從內部部署資料進行即時更新。 內部部署資料閘道可以使用 DirectQuery 支援 SSO，也就是用來連線到內部部署資料來源的方法。

我們目前支援下列資料來源︰

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) 和 [SAML](service-gateway-sso-saml.md))
* SAP BW ([Kerberos](service-gateway-sso-kerberos.md))
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

當使用者與 Power BI 服務中的 DirectQuery 報表互動時，每個交叉篩選、配量、排序和報表編輯作業可能會導致針對基礎內部部署資料來源即時執行查詢。 當 SSO 針對資料來源設定時，查詢會在使用者用來與 Power BI 互動的身分識別下執行 (也就是，透過 Web 體驗或 Power BI 行動應用程式)。 因此，每個使用者會準確看到他們在基礎資料來源中擁有權限的資料 – 設定單一登入之後，不同使用者之間沒有共用的資料快取。

## <a name="query-steps-when-running-sso"></a>執行 SSO 時的查詢步驟

使用 SSO 執行的查詢包含三個步驟，如下圖所示。

![SSO 查詢步驟](media/service-gateway-sso-overview/sso-query-steps.png)

以下是關於這些步驟的其他詳細資料：

1. 針對每個查詢，將查詢要求傳送至已設定的閘道時，**Power BI 服務**包含*使用者主體名稱*(UPN)。

2. 閘道必須將 Azure Active Directory UPN 對應至本機 Active Directory 身分識別。

   a.  如果已設定 Azure AD DirSync (也稱為「Azure AD Connect」  )，則閘道中的對應功能會自動運作。

   b.  否則，閘道可以對本機 Active Directory 網域執行查閱，以查閱 Azure AD UPN 並將其對應至本機使用者。

3. 閘道服務處理序會模擬對應的本機使用者，開啟與基礎資料庫的連線並傳送查詢。 閘道不需要安裝在與資料庫相同的電腦上。

## <a name="next-steps"></a>後續步驟

現在您已了解透過閘道進行 SSO 的基本概念，請參閱 Kerberos 和 SAML 的詳細資訊：

* [單一登入 (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [單一登入 (SSO) - SAML](service-gateway-sso-saml.md)
