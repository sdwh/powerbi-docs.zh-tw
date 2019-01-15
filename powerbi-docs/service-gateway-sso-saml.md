---
title: 將 SAML 用於內部部署資料來源的單一登入 (SSO)
description: 使用安全性聲明標記語言 (SAML) 設定閘道，以啟用從 Power BI 到內部部署資料來源的單一登入 (SSO) 。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: cb4d53166c848bcdb111b667ff413d96da9e72d5
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290513"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>針對從 Power BI 到內部部署資料來源的單一登入 (SSO)，使用安全性聲明標記語言 (SAML)

使用[安全性聲明標記語言 (SAML)](https://www.onelogin.com/pages/saml) 啟用無縫單一登入連線。 啟用 SSO 可讓 Power BI 報表和儀表板輕鬆重新整理來自內部部署來源的資料。

## <a name="supported-data-sources"></a>支援的資料來源

我們目前支援使用 SAML 的 SAP HANA。 如需使用 SAML 來安裝和設定單一登入 SAP HANA 的詳細資訊，請參閱 SAP HANA 文件中的[從 BI 平台到 HANA 的 SAML SSO](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) 主題。

我們使用 [Kerberos ](service-gateway-sso-kerberos.md) 支援其他資料來源。

## <a name="configuring-the-gateway-and-data-source"></a>設定閘道和資料來源

若要使用 SAML，請先為 SAML 識別提供者產生憑證，然後將 Power BI 使用者對應至該身分識別。

1. 產生憑證。 請確定您在填寫「一般名稱」時，使用 SAP HANA 伺服器的 FQDN。 憑證會在 365 天後過期。

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. 在 SAP HANA Studio 中，請以滑鼠右鍵按一下您的 SAP HANA 伺服器，然後巡覽至 [安全性] > [開啟安全性主控台] > [SAML 識別提供者] > [OpenSSL 密碼編譯程式庫]。

1. 選取 [匯入]，巡覽至 samltest.crt 並將其匯入。

    ![識別提供者](media/service-gateway-sso-saml/identity-providers.png)

1. 在 SAP HANA Studio 中，選取 [安全性] 資料夾。

    ![安全性資料夾](media/service-gateway-sso-saml/security-folder.png)

1. 展開 [使用者] 然後選取要對應 Power BI 使用者的目標使用者。

1. 選取 [SAML]、[設定]。

    ![設定 SAML](media/service-gateway-sso-saml/configure-saml.png)

1. 選取您在步驟 2 中建立的識別提供者。 針對 [外部身分識別]，輸入 Power BI 使用者的 UPN，然後選取 [新增]。

    ![選取識別提供者](media/service-gateway-sso-saml/select-identity-provider.png)

接下來，使用 [xmlsec1 工具](http://sgros.blogspot.com/2013/01/signing-xml-document-using-xmlsec1.html)，透過「SAML 判斷提示」來驗證設定。

1. 將下面的判斷提示儲存為 template.xml。 使用您在步驟 7 中輸入的 Power BI 使用者 UPN，來取代 \<MyUserId\>。

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <saml2:Assertion ID="Assertion12345789" IssueInstant="2015-07-16T04:47:49.858Z" Version="2.0" xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
      <saml2:Issuer></saml2:Issuer> 
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
          <CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
          <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
          <Reference URI="">
            <Transforms>
              <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
              <Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
            </Transforms>
            <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
            <DigestValue />
          </Reference>
        </SignedInfo>
        <SignatureValue />
        <KeyInfo>
          <X509Data />
        </KeyInfo>
      </Signature>
      <saml2:Subject>
        <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified"><MyUserId></saml2:NameID>
      </saml2:Subject>
      <saml2:Conditions NotBefore="2010-01-01T00:00:00Z" NotOnOrAfter="2050-01-01T00:00:00Z"/>
    </saml2:Assertion>
    ```

1. 執行下列命令： saltest.key 和 samltest.crt 是您在步驟 1 中產生的金鑰與憑證。

    ```
    xmlsec1 --sign --privkey-pem samltest.key, samltest.crt --output signed.xml assertion-template.xml
    ```

1. 在 SAP HANA Studio 中，開啟 SQL 主控台視窗並執行下列命令。 使用上一個步驟的 XML 內容取代 \<SAMLAssertion\>。

    ```SQL
    CONNECT WITH SAML ASSERTION '<SAMLAssertion>'
    ```

如果查詢成功，則表示您的 SAP HANA SAML SSO 設定成功。

現在您已成功設定身分識別與憑證，請將憑證轉換為 pfx 格式並將閘道電腦設定為使用憑證。

1. 執行下列命令，將憑證轉換為 pfx 格式。

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
    ```

1. 將 pfx 檔案複製到閘道電腦：

    1. 按兩下 samltest.pfx，然後選取 [本機電腦] > [下一步]。

    1. 輸入密碼，然後選取 [下一步]。

    1. 依序選取 [將所有憑證放在下列存放區]、[瀏覽] > [個人] > [確定]。

    1. 選取 [下一步]，然後選取 [完成]。

    ![匯入憑證](media/service-gateway-sso-saml/import-certificate.png)

1. 將閘道服務帳戶存取權授與該憑證的私密金鑰：

    1. 在閘道電腦上執行 Microsoft Management Console (MMC)。

        ![執行 MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. 在 [檔案] 下方選取 [新增/移除嵌入式管理單元]。

        ![新增嵌入式管理單元](media/service-gateway-sso-saml/add-snap-in.png)

    1. 選取 [憑證] > [新增]，然後選取 [電腦帳戶] > [下一步]。

    1. 選取 [本機電腦] > [完成] > [確定]。

    1. 依序展開 [憑證] > [個人] > [憑證]，並尋找憑證。

    1. 以滑鼠右鍵按一下憑證，並巡覽至 [所有工作] > [管理私用金鑰]。

        ![管理私用金鑰](media/service-gateway-sso-saml/manage-private-keys.png)

    1. 將閘道服務帳戶新增至清單。 根據預設，此帳戶是 **NT SERVICE\PBIEgwService。** 您可以藉由執行 **services.msc** 並尋找**內部部署資料閘道服務**，找出哪一個帳戶正在執行閘道服務。

        ![閘道服務](media/service-gateway-sso-saml/gateway-service.png)

最後，請遵循下列步驟來將憑證指紋新增至閘道設定。

1. 執行下列 PowerShell 命令來列出您電腦上的憑證。

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. 複製您所建立憑證的指紋。

1. 巡覽至閘道目錄 (預設為 C:\Program Files\On-premises data gateway)。

1. 開啟 PowerBI.DataMovement.Pipeline.GatewayCore.dll.config，並尋找 \* SapHanaSAMLCertThumbprint\* 區段。 貼上您複製的憑證指紋。

1. 重新啟動閘道服務。

## <a name="running-a-power-bi-report"></a>執行 Power BI 報表

現在您可以使用 Power BI 中的 [管理閘道] 頁面來設定資料來源，並在其下方的 [進階設定] 啟用 SSO。 然後您可以發佈繫結至該資料來源的報表和資料集。

![進階設定](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="next-steps"></a>後續步驟

如需**內部部署資料閘道**和 **DirectQuery** 的詳細資訊，請參閱下列資源：

* [內部部署資料閘道](service-gateway-onprem.md)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)