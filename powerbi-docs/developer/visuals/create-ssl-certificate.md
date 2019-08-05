---
title: 正在建立 SSL 憑證
description: 為開發人員伺服器手動建立憑證的因應措施指示
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425428"
---
# <a name="creating-ssl-certificate"></a>正在建立 SSL 憑證

執行下列命令，以使用 Windows 8 或更新版本上的 Powershell New-SelfSignedCertificate Cmdlet 來產生憑證。

工具需要適用於 **Windows** **7** 的 OpenSSL 安裝。 從命令列可以使用 Util `openssll`。

如需安裝 OpenSSL，請前往 [https://www.openssl.org](https://www.openssl.org) 或 [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>建立憑證 (Mac OS X)

通常在 Linux 或 Mac OS X 作業系統中可以使用 OpenSSL utils。

否則，您可以從下列項目安裝

*Brew* 套件管理員

```cmd
brew install openssl
brew link openssl --force
```

或使用 *MacPorts*

```cmd
sudo port install openssl
```

在安裝 OpenSSL 以產生新的憑證呼叫之後：

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>建立憑證 (Linux)

在 Linux 作業系統中無法使用 OpenSSL utils，您可以使用下列命令進行安裝。

針對 *APT* 套件管理員：

```cmd
sudo apt-get install openssl
```

針對 *Yellowdog Updater*：

```cmd
yum install openssl
```

針對 *Redhat Package Manager*：

```cmd
rpm install openssl
```

如果在您的作業系統呼叫中已可使用 OpenSSl

```cmd
pbiviz --create-cert
```

來產生新憑證。

或者，可從 [https://www.openssl.org](https://www.openssl.org) 或 [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries) 取得

## <a name="generate-certificate-manually"></a>手動產生憑證

您可以指定任何工具所產生的憑證。

如果您的系統已安裝 OpenSSL，您可以執行下列命令來產生新的憑證

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

PowerBI-visuals-tools 網頁伺服器憑證通常位於

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

適用於工具的全域執行個體

或

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

適用於工具的本機執行個體。

如果您使用 PEM 格式，則應該將憑證檔案儲存為 `PowerBICustomVisualTest_public.cer`，並將 privatekey 儲存為 `PowerBICustomVisualTest_public.key`。
如果您使用 PFX 格式，請將憑證檔案儲存為 `PowerBICustomVisualTest_public.pfx`。

如果您的 PFX 憑證檔案需要複雜密碼，則應該於下列項目中指定

```cmd
\PowerBI-visuals-tools\config.json
```

在伺服器區段：

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
