---
title: 將 Kerberos 用於 SAP HANA 的單一登入 (SSO)
description: 設定您的 SAP HANA 伺服器，以從 Power BI 服務啟用 SSO
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4e94781b3a424e894e0f0e2209ec48efb25c5db5
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106300"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>將 Kerberos 用於 SAP HANA 的單一登入 (SSO)

本文描述如何設定您的 SAP HANA 伺服器，以從 Power BI 服務啟用 SSO。

> [!NOTE]
> 除了在嘗試重新整理使用 Kerberos SSO 的 SAP HANA 架構報告之前[設定 Kerberos SSO](service-gateway-sso-kerberos.md) 的步驟之外，另請完成本文中的步驟。

## <a name="enable-sso-for-sap-hana"></a>啟用 SAP HANA 的 SSO

若要啟用 SAP HANA 的 SSO，請遵循下列步驟：

* 請確定 SAP HANA 伺服器執行的是所需最低版本，這取決於 SAP HANA 伺服器的平台層級：
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* 在閘道電腦上安裝最新的 SAP HANA ODBC 驅動程式。  最低版本為 2017 年 8 月的 HANA ODBC 2.00.020.00 版。

請確定已針對 Kerberos 架構 SSO 設定 SAP HANA 伺服器。 如需使用 Kerberos 為 SAP HANA 設定 SSO 的詳細資訊，請參閱 "SAP HANA Security Guide" 中的 "[Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html)"。 另請參閱該頁面中的連結，尤其是 SAP Note 1837331 – 如何使用 HANA DBSSO Kerberos/Active Directory。

我們也建議您遵循這些額外步驟，這可以稍微提升效能。

1. 在閘道安裝目錄中尋找並開啟這個設定檔：*Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*。

2. 尋找 *FullDomainResolutionEnabled* 屬性，將其值變更為 *True*。

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

現在，請[執行 Power BI 報表](service-gateway-sso-kerberos.md#run-a-power-bi-report)。

## <a name="next-steps"></a>後續步驟

如需**內部部署資料閘道**和 **DirectQuery** 的詳細資訊，請參閱下列資源：

* [什麼是內部部署的資料閘道？](/data-integration/gateway/service-gateway-getting-started)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
