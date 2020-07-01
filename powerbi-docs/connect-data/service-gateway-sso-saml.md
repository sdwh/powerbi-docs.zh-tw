---
title: 針對從 Power BI 到內部部署資料來源的 SSO，使用安全性聲明標記語言 (SAML)
description: 使用安全性聲明標記語言 (SAML) 設定閘道，以啟用從 Power BI 到內部部署資料來源的 SSO。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 772a9c0d171c2391a137f2e8a97f262f59df5cfe
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231380"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>針對從 Power BI 到內部部署資料來源的 SSO，使用安全性聲明標記語言 (SAML)

啟用 SSO 可讓 Power BI 報表和儀表板輕鬆重新整理來自內部部署來源的資料，同時遵守在這些來源上設定的使用者層級權限。 使用[安全性聲明標記語言 (SAML)](https://www.onelogin.com/pages/saml) 啟用無縫單一登入連線。 

## <a name="supported-data-sources"></a>支援的資料來源

我們目前支援使用 SAML 的 SAP HANA。 如需使用 SAML 來安裝和設定 SAP HANA 單一登入的詳細資訊，請參閱[從 BI 平台到 HANA 的 SAML SSO](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA)。

我們使用 [Kerberos](service-gateway-sso-kerberos.md) 支援其他資料來源 (包含 SAP HANA)。

針對 SAP HANA，建議您先啟用加密再建立 SAML SSO 連線。 若要啟用加密，請將 HANA 伺服器設定為接受加密連線，並將閘道設定為使用加密來與您的 HANA 伺服器進行通訊。 因為 HANA ODBC 驅動程式預設不會加密 SAML 判斷提示，所以已簽署之 SAML 判斷提示會從閘道傳送到「沒有問題」  的 HANA 伺服器，且很容易被第三方攔截並重複使用。 如需如何使用 OpenSSL 程式庫啟用 HANA 加密的指示，請參閱[啟用 SAP HANA 的加密](/power-bi/desktop-sap-hana-encryption)。

## <a name="configuring-the-gateway-and-data-source"></a>設定閘道和資料來源

若要使用 SAML，您必須在要啟用 SSO 的 HANA 伺服器與閘道之間建立信任關係。 在本案例中，閘道可作為 SAML 識別提供者 (IdP)。 建立此關係的方式很多，例如將閘道 IdP 的 x509 憑證匯入 HANA 伺服器信任存放區，或讓 HANA 伺服器所信任根憑證授權單位 (CA) 簽署閘道的 X509 憑證。 即使本指南會在後文中描述第二種方法，但如有更方便的方法，您也可以使用其他方法。

雖然本指南使用 OpenSSL 作為 HANA 伺服器的密碼編譯提供者，但 SAP 建議您使用 SAP 密碼編譯程式庫 (也稱為 CommonCryptoLib 或 sapcrypto) 而不是 OpenSSL 來完成建立信任關係的設定步驟。 如需詳細資訊，請參閱官方的 SAP 文件。

下列步驟描述如何使用 HANA 伺服器所信任根 CA 來簽署閘道 IdP 的 X509 憑證，以建立 HANA 伺服器與閘道 IdP 之間的信任關係。 您將建立這個根 CA：

1. 建立根 CA 的 X509 憑證和私密金鑰。 例如，若要以 .pem 格式建立根 CA 的 X509 憑證和私密金鑰，請輸入下列命令：

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
   ```

    請確定根 CA 的私密金鑰受到適當保護。 如果其由協力廠商取得，則可能用來獲取對 HANA 伺服器的未經授權存取。 

 1. 將憑證 (例如，CA_Cert.pem) 新增至 HANA 伺服器的信任存放區，HANA 伺服器才會信任由您建立之根 CA 所簽署的任何憑證。 

    您可以檢查 **ssltruststore** 組態設定來找出 HANA 伺服器的信任存放區位置。 如已遵循 SAP 文件中有關如何設定 OpenSSL 的指示，則 HANA 伺服器可能已信任您可重複使用的根 CA。 如需詳細資訊，請參閱 [How to Configure Open SSL for SAP HANA Studio to SAP HANA Server](https://archive.sap.com/documents/docs/DOC-39571) (如何設定 SAP HANA 伺服器的 Open SSL for SAP HANA Studio)。 如有多部您要啟用 SAML SSO 的 HANA 伺服器，請確定每部伺服器都信任此根 CA。

1. 建立閘道 IdP 的 X509 憑證。 

   例如，若要建立憑證簽署要求 (IdP_Req.pem) 和有效期為一年的私用金鑰 (IdP_Key.pem)，請執行下列命令：

   ```
   openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
   ```

 1. 使用已設定 HANA 伺服器要信任的根 CA 來簽署憑證簽署要求。 

    例如，若要使用 CA_Cert.pem 和 CA_Key.pem (根 CA 的憑證和金鑰) 簽署 IdP_Req.pem，請執行下列命令：

    ```
    openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
    ```

     產生的 IdP 憑證有效期為一年 (請參閱 -days 選項)。 

匯入 HANA Studio 中的 IdP 憑證，以建立新的 SAML 識別提供者：

1. 在 SAP HANA Studio 中，以滑鼠右鍵按一下您的 SAP HANA 伺服器名稱，然後巡覽至 [安全性]  &gt; [開啟安全性主控台]  &gt; [SAML 識別提供者]  &gt; [OpenSSL 密碼編譯程式庫]  。

    ![識別提供者](media/service-gateway-sso-saml/identity-providers.png)

1. 選取 [匯入]  ，巡覽至 IdP_Cert.pem 並匯入它。

1. 在 SAP HANA Studio 中，選取 [安全性]  資料夾。

    ![安全性資料夾](media/service-gateway-sso-saml/security-folder.png)

1. 展開 [使用者]  ，然後選取要對應 Power BI 使用者的目標使用者。

1. 選取 [SAML]  ，然後選取 [設定]  。

    ![設定 SAML](media/service-gateway-sso-saml/configure-saml.png)

1. 選取您在步驟 2 中建立的識別提供者。 針對 [外部身分識別]  ，輸入 Power BI 使用者的 UPN (通常是使用者用來登入 Power BI 的電子郵件地址)，然後選取 [新增]  。 若您設定閘道使用 *ADUserNameReplacementProperty* 設定選項，則請輸入將取代 Power BI 使用者原始 UPN 的值。 

   例如，若您將 *ADUserNameReplacementProperty* 設為 **SAMAccountName**，則您應輸入使用者的 **SAMAccountName**。

    ![選取識別提供者](media/service-gateway-sso-saml/select-identity-provider.png)

現在您已設定閘道的憑證和身分識別，接下來便可以將憑證轉換為 pfx 格式，並將閘道設定為使用憑證：

1. 請執行下列命令來將憑證轉換成 pfx 格式。 此命令會將產生的 .pfx 檔案命名為 samlcert.pfx，並設定 *root* 為其密碼：

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. 將 pfx 檔案複製到閘道電腦：

    1. 按兩下 samltest.pfx，然後選取 [本機電腦]  &gt; [下一步]  。

    1. 輸入密碼，然後選取 [下一步]  。

    1. 選取 [將所有憑證放在下列存放區]  ，然後選取 [瀏覽]  &gt; [個人]  &gt; [確定]  。

    1. 選取 [下一步]  ，然後選取 [完成]  。

       ![匯入憑證](media/service-gateway-sso-saml/import-certificate.png)

1. 將閘道服務帳戶存取權授與該憑證的私密金鑰：

    1. 在閘道電腦上執行 Microsoft Management Console (MMC)。

        ![執行 MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. 在 [檔案]  下方選取 [新增/移除嵌入式管理單元]  。

        ![新增嵌入式管理單元](media/service-gateway-sso-saml/add-snap-in.png)

    1. 選取 [憑證]  &gt; [新增]  ，然後選取 [電腦帳戶]  &gt; [下一步]  。

    1. 選取 [本機電腦]  &gt; [完成]  &gt; [確定]  。

    1. 依序展開 [憑證]  &gt; [個人]  &gt; [憑證]  ，並尋找憑證。

    1. 以滑鼠右鍵按一下憑證，並巡覽至 [所有工作]  &gt; [管理私密金鑰]  。

        ![管理私用金鑰](media/service-gateway-sso-saml/manage-private-keys.png)

    1. 將閘道服務帳戶新增至清單。 根據預設，此帳戶是 **NT SERVICE\PBIEgwService**。 您可以藉由執行  並尋找**內部部署資料閘道服務**，來了解哪個帳戶正在執行閘道服務。

        ![閘道服務](media/service-gateway-sso-saml/gateway-service.png)

最後，請遵循下列步驟將憑證指紋新增至閘道設定：

1. 執行下列 PowerShell 命令來列出您電腦上的憑證：

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

1. 複製您所建立憑證的指紋。

1. 巡覽至閘道目錄，其預設為 C:\Program Files\On-premises data gateway。

1. 開啟 PowerBI.DataMovement.Pipeline.GatewayCore.dll.config，並尋找  *SapHanaSAMLCertThumbprint* 區段。 貼上您複製的指紋。

1. 重新啟動閘道服務。

## <a name="running-a-power-bi-report"></a>執行 Power BI 報表

現在您可以使用 Power BI 中的 [管理閘道]  頁面來設定 SAP HANA 資料來源。 在 [進階設定]  下方，透過 SAML 啟用 SSO。 這麼做可讓您發佈繫結至該資料來源的報表和資料集。

   ![進階設定](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>疑難排解

在您設定 SAML 式 SSO 之後，您可能會在 Power BI 入口網站中看到下列錯誤：提供的認證無法用於 SapHana 來源。  此錯誤表示 SAP Hana 拒絕了該 SAML 認證。

伺服器端驗證會追蹤提供的詳細資訊，以針對 SAP HANA 上的認證問題進行疑難排解。 請遵循以下步驟來為 SAP HANA 伺服器設定追蹤：

1. 在 SAP HANA 伺服器上，透過執行下列查詢來開啟驗證追蹤：

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. 重現問題。

1. 在 HANA Studio 中，開啟管理主控台並選取 [診斷檔案]  索引標籤。

1. 開啟最近的索引伺服器追蹤，然後搜尋 *SAMLAuthenticator.cpp*。

    您應該會看到指出根本原因的詳細錯誤訊息，例如：

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. 完成疑難排解之後，透過執行下列查詢來關閉驗證追蹤：

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>後續步驟

如需內部部署資料閘道和 DirectQuery 的詳細資訊，請參閱下列資源：

* [什麼是內部部署的資料閘道？](/data-integration/gateway/service-gateway-onprem)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](power-bi-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
