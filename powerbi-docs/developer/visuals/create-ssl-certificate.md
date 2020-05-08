---
title: 建立 SSL 憑證
description: 為開發人員伺服器手動建立憑證的因應措施指示
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: fab40863d7beae4892a56975aa5e92c4fe5486ac
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380264"
---
# <a name="create-an-ssl-certificate"></a>建立 SSL 憑證

此文章說明如何建立 SSL 憑證。

若要在 Windows 8 或更新版本上使用 Powershell `New-SelfSignedCertificate` Cmdlet 來產生憑證，請執行下列命令：

```cmd
pbiviz --install-cert
```

該工具需要適用於 Windows 7 的 OpenSSL 安裝。 OpenSSL 公用程式必須能從命令列使用。

若要安裝 OpenSSL，請移至 [OpenSSL](https://www.openssl.org) \(英文\) 或 [OpenSSL 二進位檔](https://wiki.openssl.org/index.php/Binaries) \(英文\) 網站。

## <a name="create-a-certificate-mac-os-x"></a>建立憑證 (Mac OS X)

Linux 或 Mac OS X 作業系統通常會提供 OpenSSL 公用程式。

您也可以執行下列其中一個命令來安裝該公用程式：

* 從 *Brew* 套件管理員：

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* 使用 *MacPorts*：

    ```cmd
    sudo port install openssl
    ```

在您安裝 OpenSSL 公用程式以產生新憑證之後，請執行下列命令：

```cmd
pbiviz --install-cert
```

## <a name="create-a-certificate-linux"></a>建立憑證 (Linux)

如果您的 Linux 作業系統未提供 OpenSSL 公用程式，您可以使用下列其中一個命令來安裝它：

* 針對 *APT* 套件管理員：

    ```cmd
    sudo apt-get install openssl
    ```

* 針對 *Yellowdog Updater*：

    ```cmd
    yum install openssl
    ```

* 針對 *Redhat Package Manager*：

    ```cmd
    rpm install openssl
    ```

如果您的作業系統上已有 OpenSSL 公用程式，請執行下列命令來產生新憑證：

```cmd
pbiviz --install-cert
```

或者，您可以移至 [OpenSSL](https://www.openssl.org) \(英文\) 或 [OpenSSL 二進位檔](https://wiki.openssl.org/index.php/Binaries) \(英文\) 網站來取得 OpenSSL 公用程式。

## <a name="generate-the-certificate-manually"></a>手動產生憑證

您可以指定使用任何工具來產生憑證。

如果 OpenSSL 公用程式已經安裝在您的系統上，請執行下列命令來產生新憑證：

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

您通常可以執行下列其中一個命令來找到 PowerBI-visuals-ols Web 伺服器憑證：

* 針對工具的全域執行個體：

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* 針對工具的本機執行個體：

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

如果您使用 PEM 格式，請將憑證檔案儲存為 *PowerBICustomVisualTest_public.crt*，然後將 privateKey 儲存為 *PowerBICustomVisualTest_public.key*。

如果您使用 PFX 格式，請將憑證檔案儲存為 *PowerBICustomVisualTest_public.pfx*。

如果您的 PFX 憑證檔案需要複雜密碼，請執行下列動作：
1. 在設定檔中，請指定：

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. 在 `server` 區段中，請透過取代 "*YOUR PASSPHRASE*" 預留位置來指定複雜密碼：

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBICustomVisualTest_private.key",
        "certificate":"certs/PowerBICustomVisualTest_public.crt",
        "pfx":"certs/PowerBICustomVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"YOUR PASSPHRASE"
    }
    ```