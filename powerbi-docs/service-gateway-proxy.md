---
title: 設定內部部署資料閘道的 Proxy 設定
description: 設定內部部署資料閘道的 Proxy 設定的相關資訊。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 7264ef7b1057f64d6eb51ccc77cbec2a74be6d0e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54283981"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>設定內部部署資料閘道的 Proxy 設定
您的工作環境可能需要執行 Proxy 以存取網際網路。 這可以防止內部部署資料閘道連線到服務。

## <a name="does-your-network-use-a-proxy"></a>您的網路是否使用 Proxy？
如欲判斷您的網路是否使用 Proxy，可以參考 Superuser.com 刊登的下列文章。

[如何得知我目前使用的是哪些 Proxy 伺服器？(SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>設定檔位置和預設設定
Proxy 資訊是在 .NET 設定檔中所設定。 位置和檔案名稱將會隨您正在使用的閘道而有所不同。

### <a name="on-premises-data-gateway"></a>內部部署資料閘道
有兩個與內部部署資料閘道有關的主要設定檔。

**設定**

第一個是實際設定閘道的設定畫面。 若您有設定閘道的問題，可以查看這個檔案。

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Windows 服務**

第二個是與 Power BI 服務互動和處理要求的實際 Windows 服務。

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>設定 Proxy 設定
預設的 Proxy 設定如下所示。

    <system.net>
        <defaultProxy useDefaultCredentials="true" />
    </system.net>

預設設定適用於 Windows 驗證。 若您的 Proxy 使用另一種格式的驗證，您將必須變更設定。 若您不確定，應該連絡網路系統管理員。 不建議使用基本 Proxy 驗證，且嘗試使用基本 Proxy 驗證可能會造成 Proxy 驗證錯誤，而導致未能正確設定閘道。 請使用較強的 Proxy 驗證機制來解決。

除了使用預設認證之外，您也可以新增 <proxy> 元素，詳加定義 Proxy 伺服器設定。 舉例來說，您可以透過將 bypassonlocal 參數設為 false，指定內部部署的資料閘道應一律使用 Proxy，即使對本機資源亦然。 如果您想要在 Proxy 記錄檔中追蹤從內部部署的資料閘道產生的所有 https 要求，這會有助於疑難排解。 下列範例組態指定所有要求都必須通過 IP 位址為 192.168.1.10 的特定 Proxy。

    <system.net>
        <defaultProxy useDefaultCredentials="true">
            <proxy  
                autoDetect="false"  
                proxyaddress="http://192.168.1.10:3128"  
                bypassonlocal="false"  
                usesystemdefault="true"
            />  
        </defaultProxy>
    </system.net>

若要深入了解.NET 設定檔的 Proxy 項目設定，請參閱 [defaultProxy 項目 (網路設定)](https://msdn.microsoft.com/library/kd3cf2ex.aspx)。

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>將閘道服務帳戶變更為網域使用者
如前文所述，將 Proxy 設定為使用預設認證時，您與 Proxy 之間可能會出現驗證問題。 這是因為預設服務帳戶是服務 SID，而不是通過驗證的網域使用者。 您可以變更閘道的服務帳戶，讓 Proxy 驗證順利進行。

> [!NOTE]
> 建議使用受管理的服務帳戶，以免需要重設密碼。 了解如何在 Active Directory 中建立[受管理的服務帳戶](https://technet.microsoft.com/library/dd548356.aspx)。
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>變更內部部署資料閘道服務帳戶
1. 變更**內部部署資料閘道服務**的 Windows 服務帳戶。

    此服務的預設帳戶是 *NT SERVICE\PBIEgwService*。 您可以將其變更為 Active Directory 網域中的網域使用者帳戶。 也可以使用受管理的服務帳戶，以免需要變更密碼。

    您可以在 Windows 服務屬性的 [登入] 索引標籤中變更此帳戶。
2. 重新啟動**內部部署資料閘道服務**。

    在系統管理員命令提示字元中發出下列命令。

        net stop PBIEgwService

        net start PBIEgwService
3. 啟動**內部部署資料閘道設定程式**。 您可以選取 Windows 的 [開始] 按鈕，然後搜尋「內部部署資料閘道」。
4. 登入 Power BI。
5. 使用您的修復金鑰還原閘道。

    如此一來，新的服務帳戶就能將資料來源的預存認證解密。

> [!NOTE]
> 當您直接使用服務控制台來變更服務帳戶時，不會自動更新 ACL。 您必須確認新的服務帳戶可以存取安裝檔案和資料夾。 閘道安裝資料夾位於 C:\Program Files\On-premises data gateway 之下。 
> 

## <a name="next-steps"></a>後續步驟
[內部部署資料閘道 (個人模式)](service-gateway-personal-mode.md)
[防火牆資訊](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

