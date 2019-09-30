---
title: 使用 CommonCryptoLib (sapcrypto.dll) 將 Kerberos 單一登入用於 SAP BW 的 SSO
description: 使用 CommonCryptoLib (sapcrypto.dll) 設定您的 SAP BW 伺服器，以從 Power BI 服務啟用 SSO
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 6c4f2b0d8856d5e68e02b9b33cf393ca85ecb580
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106277"
---
# <a name="use-kerberos-single-sign-on-for-sso-to-sap-bw-using-commoncryptolib-sapcryptodll"></a>使用 CommonCryptoLib (sapcrypto.dll) 將 Kerberos 單一登入用於 SAP BW 的 SSO

本文描述如何使用 CommonCryptoLib (sapcrypto.dll) 設定您的 SAP BW 伺服器，以從 Power BI 服務啟用 SSO。

> [!NOTE]
> 除了在嘗試重新整理使用 Kerberos SSO 的 SAP BW 架構報告之前[設定 Kerberos SSO](service-gateway-sso-kerberos.md) 中步驟之外，另請完成本文中的步驟。 使用 CommonCryptoLib 作為您的 SNC 程式庫，可讓 SSO 連線到 SAP BW 應用程式伺服器和 SAP BW 訊息伺服器。

## <a name="configure-sap-bw-server-to-enable-sso-using-commoncryptolib"></a>使用 CommonCryptoLib 來設定 SAP BW 以啟用 SSO

> [!NOTE]
> 內部部署資料閘道是 64 位元軟體，因此需要 64 位元版本的 CommonCryptoLib (sapcrypto.dll)。 如果您打算在透過閘道嘗試 SSO 連線之前，在 SAP GUI 中測試 SAP BW 伺服器的 SSO 連線 (建議)，則也需要 32 位元版本的 CommonCryptoLib，因為 SAP GUI 是 32 位元軟體。

1. 請確定您的 BW 伺服器已使用 CommonCryptoLib 針對 Kerberos SSO 正確設定。 如果已正確設定，您應該能夠透過 SAP GUI 之類已設定為使用 CommonCryptoLib 的 SAP 工具，使用 SSO 來存取 BW 伺服器 (直接或透過 SAP BW 訊息伺服器)。 如需設定步驟的詳細資訊，請參閱 [SAP Single Sign-On:Authenticate with Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/) (SAP 單一登入：使用 Kerberos/SPNEGO 進行驗證)。 您的 BW 伺服器應該使用 CommonCryptoLib 作為其 SNC 程式庫，並具有以 "CN=" 開頭的 SNC 名稱，例如 "CN=BW1"。 如需 SNC 名稱需求的詳細資訊，請參閱 [Kerberos 設定的 SNC 參數](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (具體來說，是 snc/identity/as 參數)。

1. 如果您尚未這麼做，請在已安裝閘道的電腦上安裝 [SAP .NET 連接器](https://support.sap.com/en/product/connectors/msnet.html)的 x64 版本。 您可以透過嘗試在 Power BI Desktop 中連線到 BW 伺服器，檢查元件是否已安裝。 如果您無法使用 2.0 執行進行連線，則未安裝 .NET 連接器。

1. 請確定在安裝閘道的電腦上未執行 SAP 安全登入用戶端 (SLC)。 SLC 快取 Kerberos 票證時，可能會干擾閘道能否使用 Kerberos 進行 SSO。 如果已安裝 SLC，請將它解除安裝，或確定您結束 SAP 安全登入用戶端：以滑鼠右鍵按一下系統匣中的圖示，然後依序選取 [登出] 和 [結束]，再嘗試使用閘道進行 SSO 連線。 Windows Server 電腦不支援使用 SLC。 如需詳細資訊，請參閱 [SAP Note 2780475](https://launchpad.support.sap.com/#/notes/2780475) (需要 s 使用者)。

    ![SAP 安全登入用戶端](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    如果您解除安裝 SLC，或依序選取 [登出]  和 [結束]  、開啟 cmd 視窗並輸入 `klist purge` 以清除任何快取的 Kerberos 票證，然後嘗試透過閘道進行 SSO 連線。

1. 從 SAP Launchpad 下載 64 位元的 CommonCryptoLib (sapcrypto.dll) **8.5.25 版或更新版本**，並將它複製到閘道電腦上的資料夾。 在您複製 sapcrypto.dll 的相同目錄中，建立名為 sapcrypto.ini 的檔案，其中包含下列內容：

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    .Ini 檔案包含 CommonCryptoLib 在閘道案例中啟用 SSO 所需的設定資訊。

    > [!NOTE]
    > 這些檔案必須儲存在相同的位置；換句話說， _/path/to/sapcrypto/_ 應該同時包含 sapcrypto.ini 和 sapcrypto.dll。

    閘道服務使用者和服務使用者將模擬的 Active Directory (AD) 使用者，都需要這兩個檔案的讀取和執行權限。 我們建議將 .ini 和 .dll 檔案的權限授與 [已驗證的使用者] 群組。 基於測試目的，您也可以將這些權限明確授與給閘道服務使用者和您用於測試的 Active Directory 使用者。 在以下螢幕擷取畫面中，我們已將 sapcrypto.dll 的**讀取和執行**權限授與 [已驗證的使用者] 群組：

    ![已驗證的使用者](media/service-gateway-sso-kerberos/authenticated-users.png)

1. 如果您沒有 SAP BW 資料來源，請在 Power BI 服務的 [管理閘道]  頁面上，新增資料來源。 如果您已經有 BW 資料來源與您想要 SSO 連線流經的閘道建立關聯，請準備進行編輯。 如果您想要建立 BW 應用程式伺服器的 SSO 連線，請選擇 [SAP Business Warehouse]  作為 [資料來源類型]  。 如果您想要建立 BW 訊息伺服器的 SSO 連線，請選取 [SAP Business Warehouse 訊息伺服器]  。

    針對 [SNC 程式庫]  ，選取 [SNC\_LIB 或 SNC\_LIB\_64 環境變數]  或 [自訂]  。 如果您選取 [SNC\_LIB]  選項，則必須將閘道電腦上 **SNC\_LIB\_64** 環境變數值設定為閘道電腦上 sapcrypto.dll 64 位元複本的絕對路徑，例如 C:\Users\Test\Desktop\sapcrypto.dll。 如果您選擇 [自訂]  ，請將 sapcrypto.dll 絕對路徑貼入 [管理閘道]  頁面上出現的 [自訂 SNC 程式庫路徑] 欄位。 針對 [SNC 合作夥伴名稱]  ，輸入 BW 伺服器的 SNC 名稱。 在 [進階設定]  底下，確定已核取 [透過 Kerberos 使用 SSO 進行 DirectQuery 查詢]  。 如果您是從 PBI Desktop 建立 Windows 驗證連線，則應該填入其他欄位。

1. 建立 CCL\_PROFILE 系統環境變數，並將它指向 sapcrypto.ini：

    ![CCL\_PROFILE 系統環境變數](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    請記住，sapcrypto .dll 和 .ini 檔案必須存在於相同的位置。 在上方所示的範例中，sapcrypto.ini 位於桌面，sapcrypto.dll 也應該位於桌面。

1. 重新啟動閘道服務：

    ![重新啟動閘道服務](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. [執行 Power BI 報表](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>疑難排解

如果您無法在 Power BI 服務中重新整理報表，可以使用閘道追蹤、CPIC 追蹤和 CommonCryptoLib 追蹤來協助診斷問題。 CPIC 追蹤和 CommonCryptoLib 是 SAP 產品，因此 Microsoft 無法為其提供任何直接支援。 對於要授與 BW SSO 存取權的 Active Directory 使用者，某些 Active Directory 設定可能會要求使用者在安裝閘道的電腦上必須是 Administrators 群組成員。

1. **閘道記錄：** 只要重現問題、開啟[閘道應用程式](https://docs.microsoft.com/data-integration/gateway/service-gateway-app)、移至 [診斷]  索引標籤，然後選取 [匯出記錄]  ：

    ![匯出閘道記錄](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **CPIC 追蹤：** 若要啟用 CPIC 追蹤，請設定兩個環境變數：CPIC\_TRACE 和 CPIC\_TRACE\_DIR。 第一個變數會設定追蹤層級，而第二個變數會設定追蹤檔案目錄。 此目錄必須是 [已驗證的使用者] 群組成員可以寫入的位置。 將 CPIC\_TRACE 設為 3，並將 CPIC\_TRACE\_DIR 設為您想要寫入追蹤檔案的任何目錄。

    ![CPIC 追蹤](media/service-gateway-sso-kerberos/cpic-tracing.png)

    重現問題，並檢查 CPIC\_TRACE\_DIR 是否包含追蹤檔案。

1. **CommonCryptoLib 追蹤：** 將兩行新增至您稍早建立的 sapcrypto.ini 檔案，以開啟 CommonCryptoLib 追蹤：

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    請務必將 _ccl/trace/directory_ 選項變更為 [已驗證的使用者] 群組成員可以寫入的位置。 或者，建立新的 .ini 檔案來變更此行為。 在與 sapcrypto.ini 和 sapcrypto.dll 相同的目錄中，建立名為 sectrace.ini 的檔案，其中包含下列內容。 將 DIRECTORY 選項取代為您電腦上已驗證使用者可以寫入的位置：

    ```
    LEVEL = 5

    DIRECTORY = <drive>:\logs\sectrace
    ```

    現在，請重現問題，並檢查 DIRECTORY 所指向的位置是否包含追蹤檔案。 當您完成時，請務必關閉 CPIC 和 CCL 追蹤。

    如需 CommonCryptoLib 追蹤的詳細資訊，請參閱 [SAP Note 2491573](https://launchpad.support.sap.com/#/notes/2491573) (需要 s 使用者)。

## <a name="next-steps"></a>後續步驟

如需**內部部署資料閘道**和 **DirectQuery** 的詳細資訊，請參閱下列資源：

* [什麼是內部部署的資料閘道？](/data-integration/gateway/service-gateway-getting-started)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
