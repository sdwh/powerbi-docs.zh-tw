---
title: 使用 gx64krb5 將 Kerberos 用於 SAP BW 的單一登入 (SSO)
description: 設定您的 SAP BW 伺服器，以使用 gx64krb5 從 Power BI 服務啟用 SSO
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5dd31dc4333dc03100370100e16eadab6012c1f0
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106323"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>使用 gx64krb5 將 Kerberos 用於 SAP BW 的單一登入 (SSO)

本文描述如何設定您的 SAP BW 伺服器，以使用 gx64krb5 從 Power BI 服務啟用 SSO。

> [!NOTE]
> 除了[設定 Kerberos SSO](service-gateway-sso-kerberos.md) 中的步驟之外，您還可以完成本文中的步驟，以在 Power BI 服務中針對使用 Kerberos SSO 的 SAP BW 應用程式伺服器架構報表啟用重新整理。 不過，Microsoft 建議使用 CommonCryptoLib 作為您的 SNC 程式庫。 SAP 不再提供 gx64krb5 的支援，因此相較於 CommonCryptoLib，將其設定為與閘道搭配使用所需的步驟變得更為複雜。 如需如何使用 CommonCryptoLib 設定 SSO 的說明，請參閱[使用 CommonCryptoLib 針對 SSO 設定 SAP BW](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md)。 您應該完成 CommonCryptoLib 或  gx64krb5 的設定。 請勿同時完成這兩個程式庫的設定步驟。

### <a name="set-up-gx64krb5gsskrb5-on-gateway-machine-and-the-sap-bw-server"></a>在閘道電腦和 SAP BW 伺服器上設定 gx64krb5/gsskrb5

> [!NOTE]
> SAP 已不再主動支援 `gx64krb5` 和 `gsskrb5`。 如需詳細資訊，請參閱 [SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295) (SAP 附註 352295)。 另請注意，`gx64krb5` 不允許透過 SSO 從資料閘道連線到 SAP BW 訊息伺服器， 而是只能連線到 SAP BW 應用程式伺服器。 如果您使用 [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) 作為 SNC 程式庫，則不會有這個僅限應用程式伺服器的限制。 其他 SNC 程式庫也適用於 BW SSO，但 Microsoft 並未正式支援這些程式庫。

用戶端和伺服器都必須使用 `gx64krb5` \ `gsskrb5`，才能透過閘道完成 SSO 連線；亦即，用戶端和伺服器必須使用相同的 SNC 程式庫。

1. 從 [SAP Note 2115486](https://launchpad.support.sap.com/) 下載 `gx64krb5` (需要 SAP 使用者)。 請確認您具備 1.0.11.x 以上的版本。 如果您想要先在 SAP GUI 中測試 SSO 連線，再嘗試透過閘道的 SSO 連線，也請下載 `gsskrb5` (32 位元版本的程式庫) (建議)。 需要 32 位元版本才能使用 SAP GUI 進行測試，因為 SAP GUI 僅能在 32 位元中使用。

1. 將 `gx64krb5` 放在閘道電腦上可由閘道服務使用者存取的位置中 (如果您要使用 SAP 登入測試 SSO 連線，也可以透過 SAP GUI)。 閘道服務使用者和服務使用者將模擬的 Active Directory (AD) 使用者都需要此 .dll 的讀取和執行權限。 我們建議將 .dll 的權限授與 [已驗證的使用者] 群組。 基於測試目的，您也可以將這些權限明確授與給閘道服務使用者和您用來測試的 Active Directory 使用者。

1. 如果您的 BW 伺服器尚未使用 gx64krb5/gsskrb5 設定進行 SSO，請將另一個複本放在 SAP BW 伺服器電腦上 SAP BW 伺服器可存取的位置中。 

1. 在用戶端和伺服器電腦上，設定 `SNC_LIB` 或 `SNC_LIB_64` 環境變數。 如果您使用 gsskrb5，請將 `SNC_LIB` 變數設定為 gsskrb5.dll 的絕對路徑。 如果您使用 gx64krb5，請將 `SNC_LIB_64` 變數設定為 gx64krb5.dll 的絕對路徑。

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication"></a>設定 SAP BW 服務使用者並啟用 SNC 通訊

如果您尚未使用 gx64krb5/gsskrb5 設定 SAP BW 伺服器進行 SNC 通訊 (例如 SSO)，請完成本節。

> [!NOTE]
> 本節假設您已經建立 BW 的服務使用者，並將適當的 SPN 繫結到該使用者 (例如，以 `SAP/` 開頭的項目)。

1. 授與服務使用者對 SAP BW 應用程式伺服器的存取權：

    1. 在 SAP BW 伺服器電腦上，將服務使用者新增至本機系統管理員群組。 開啟 [電腦管理] 程式，然後按兩下您伺服器的本機系統管理員群組。

        ![[電腦管理] 程式的螢幕擷取畫面](media/service-gateway-sso-kerberos/computer-management.png)

    1. 按兩下本機系統管理員群組，然後選取 [新增]  將您的服務使用者新增至該群組。 請選取 [檢查名稱]  來確保已正確輸入名稱。 選取 [確定]  。

1. 將 SAP BW 伺服器的服務使用者，設定為在 SAP BW 伺服器電腦上啟動 SAP BW 伺服器服務的使用者。

    1. 開啟 [執行]  ，並輸入 "Services.msc"。 尋找與 SAP BW 應用程式伺服器執行個體對應的服務。 以滑鼠右鍵按一下該服務，然後選取 [屬性]  。

        ![服務的螢幕擷取畫面，其中已醒目提示 [屬性]](media/service-gateway-sso-kerberos/server-properties.png)

    1. 切換至 [登入]  索引標籤，然後將使用者變更為您的 SAP BW 服務使用者。 輸入使用者的密碼，然後選取 [確定]  。

1. 在 SAP 登入中登入您的伺服器，並使用 RZ10 交易來設定下列設定檔參數：

    1. 將 snc/identity/as 設定檔參數設定為 p:\<您剛剛建立的 SAP BW 服務使用者\>，例如 p:BWServiceUser@MYDOMAIN.COM。 請注意位於服務使用者 UPN 之前的 p:。 它不是像使用 Common Crypto Lib 作為 SNC 程式庫時的 p:CN=。

    1. 將 snc/gssapi\_lib 設定檔參數設定為 \<BW 伺服器電腦上 gsskrb5.dll/gx64krb5.dll 的路徑 (您將使用的程式庫取決於作業系統位元)\>。 請務必將程式庫放在 SAP BW 應用程式伺服器可以存取的位置。

    1. 另請設定下列其他設定檔參數，根據您的需要來變更值。 請注意，最後五個選項可讓用戶端無需設定 SNC 即可使用 SAP 登入連線至 SAP BW 伺服器。

        | **設定** | **值** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. 將 snc/enable 設定為 1。

1. 設定這些設定檔參數之後，請在伺服器電腦上開啟 SAP 管理主控台並重新啟動 SAP BW 執行個體。 如果伺服器無法啟動，請確認設定檔參數已正確設定。 如需設定檔參數設定的詳細資訊，請參閱 [SAP documentation](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm) (SAP 文件)。 如果遇到問題，您也可以參考本節稍後的疑難排解資訊。

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>將 SAP BW 使用者對應至 Active Directory 使用者

如果您還沒這麼做，請將 Active Directory 使用者對應至 SAP BW 應用程式伺服器使用者，並在 SAP 登入中測試 SSO 連線。

1. 使用 SAP 登入來登入您的 SAP BW 伺服器。 執行交易 SU01。

1. 針對 [使用者]  ，輸入您想要啟用 SSO 連線的 SAP BW 使用者 (在上一個螢幕擷取畫面中我們設定了 BIUSER 的權限)。 選取 SAP 登入視窗左上角附近的**編輯**圖示 (畫筆的影像)。

    ![SAP BW [使用者維護] 畫面的螢幕擷取畫面](media/service-gateway-sso-kerberos/user-maintenance.png)

1. 選取 [SNC]  索引標籤。在 SNC 名稱輸入方塊中，輸入 p:\<您的 Active Directory 使用者\>@\<您的網域\>。 請注意，Active Directory 使用者 UPN 前面必須加上強制的 p:。 您指定的 Active Directory 使用者，應屬於要為其啟用 SAP BW 應用程式伺服器 SSO 存取權的人員或組織。 例如，如果您希望為使用者 testuser\@TESTDOMAIN.COM 啟用 SSO 存取權，請輸入 p:testuser@TESTDOMAIN.COM。

    ![SAP BW [維護使用者] 畫面的螢幕擷取畫面](media/service-gateway-sso-kerberos/maintain-users.png)

1. 選取畫面左上角附近的**儲存**圖示 (磁碟片的影像)。

### <a name="test-sign-in-by-using-sso"></a>使用 SSO 測試登入

請確認您是否可以使用 SAP 登入透過 SSO 當作剛剛已啟用 SSO 存取權的 Active Directory 使用者來登入伺服器。

1. 以您剛為其啟用 SSO 存取權的 Active Directory 使用者身分，登入已安裝 SAP 登入的電腦。 啟動 SAP 登入，並建立新的連線。

1. 在 [Create New System Entry] \(建立新的系統項目\)  畫面中，選取 [User Specified System] \(使用者指定的系統\)   > [下一步]  。

    ![[Create New System Entry] \(建立新的系統項目\) 畫面的螢幕擷取畫面](media/service-gateway-sso-kerberos/new-system-entry.png)

1. 在下一個畫面填入適當的詳細資料，包括應用程式伺服器、執行個體數目以及系統識別碼。 然後選取 [完成]  。

1. 以滑鼠右鍵按一下新連線，然後選取 [屬性]  。 切換至 [網路]  索引標籤。在 [SNC Name] \(SNC 名稱\)  文字方塊中輸入 p:\<SAP BW 服務使用者的 UPN\>，例如 p:BWServiceUser@MYDOMAIN.COM。 然後選取 [確定]  。

    ![[System Entry Properties] \(系統項目屬性\)畫面的螢幕擷取畫面](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. 按兩下您剛才建立的連線，以嘗試與 SAP BW 伺服器建立 SSO 連線。 如果連線成功，請繼續下一個步驟。 如果未成功，請檢閱此文件中先前的步驟，確定這些步驟已正確完成，或檢閱以下的疑難排解一節。 請注意，如果您在此內容中無法透過 SSO 連線至 SAP BW 伺服器，則無法在閘道內容中使用 SSO 連線至 SAP BW 伺服器。

### <a name="add-registry-entries-to-the-gateway-machine"></a>新增登錄項目至閘道電腦

將所需的登錄項目新增至閘道安裝所在之電腦的登錄，同時安裝至要從 Power BI Desktop 連線至的電腦上。 以下是要執行的命令：

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>將新的 SAP BW 應用程式伺服器資料來源新增至 Power BI 服務，或編輯現有的資料來源

1. 在資料來源設定視窗中，輸入應用程式伺服器的 [主機名稱]  、[系統編號]  和 [用戶端識別碼]  ，如同您用來從 Power BI Desktop 登入 SAP BW 伺服器的資訊。

1. 在 [SNC Partner Name] \(SNC 合作夥伴名稱\)  欄位中，輸入 p: \<您對應至 SAP BW 服務使用者的 SPN\>。 例如，如果 SPN 為 SAP/BWServiceUser@MYDOMAIN.COM，您應該在 [SNC 合作夥伴名稱]  欄位中輸入 p:SAP/BWServiceUser@MYDOMAIN.COM。

1. 針對 SNC 程式庫，請選取 **SNC_LIB** 或 **SNC_LIB_64**。 請確定閘道機器上的 SNC_LIB_64 指向 gx64krb5.dll。 或者，您可以選取 [自訂] 選項，並提供 gx64krb5.dll 的絕對路徑 (在閘道電腦上)。

1. 選取 [Use SSO via Kerberos for DirectQuery queries] \(透過 Kerberos 使用 SSO 進行 DirectQuery 查詢)  方塊，然後選取 [套用]  。 如果測試連線不成功，請確認已正確完成先前的安裝和設定步驟。

1. [執行 Power BI 報表](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>疑難排解

### <a name="troubleshoot-gx64krb5gsskrb5-configuration"></a>針對 gx64krb5/gsskrb5 設定進行疑難排解

如果您遇到任何問題，請遵循下列步驟針對 SAP 登入中的 gx64krb5/gsskrb5 安裝和 SSO 連線進行疑難排解。

* 檢視伺服器記錄檔 (伺服器電腦上的 …work\dev\_w0) 可協助您針對在完成 gx64krb5/gsskrb5 安裝步驟時遇到的任何錯誤進行疑難排解。 特別是在設定檔參數變更後無法啟動 SAP BW 伺服器時。

* 如果由於登入失敗而無法啟動 SAP BW 服務，則在設定 SAP BW「啟動為」使用者時可能提供了錯誤的密碼。 以 SAP BW 服務使用者身分登入 Active Directory 環境中的電腦來驗證密碼。

* 如果您收到導致伺服器無法啟動的 SQL 認證相關錯誤，請確認您已授與服務使用者對 SAP BW 資料庫的存取權。

* 您可能會收到下列訊息：「(GSS-API) 指定的目標未知或無法存取」。 這通常表示您指定了錯誤的 SNC 名稱。 請務必在用戶端應用程式中只使用 "p:"，而非 "p:CN =" 或其他任何項目 (除了服務使用者的 UPN 以外)。

* 您可能會收到下列訊息：「(GSS-API) 提供了無效的名稱」。 請確認 "p:" 位於伺服器 SNC 身分識別設定檔參數的值中。

* 您可能會收到下列訊息：「(SNC 錯誤) 無法找到指定的模組」。 這通常是由於 `gsskrb5.dll/gx64krb5.dll` 需要提高權限 (系統管理員權限) 才能存取。

### <a name="troubleshoot-gateway-connectivity-issues"></a>針對閘道連線問題進行疑難排解

1. 檢查閘道記錄。 開啟閘道設定應用程式，然後選取 [診斷]   > [匯出記錄]  。 最新錯誤會位在您檢查的任何記錄檔底部。

    ![[內部部署的資料閘道] 應用程式的螢幕擷取畫面，其中已醒目提示 [診斷]](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. 開啟 SAP BW 追蹤，並檢閱產生的記錄檔。 有許多不同類型的 SAP BW 追蹤可供使用。 如需詳細資訊，請參閱 SAP 文件。

## <a name="next-steps"></a>後續步驟

如需**內部部署資料閘道**和 **DirectQuery** 的詳細資訊，請參閱下列資源：

* [什麼是內部部署的資料閘道？](/data-integration/gateway/service-gateway-getting-started)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
