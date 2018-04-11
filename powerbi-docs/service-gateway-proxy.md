---
title: 設定內部部署資料閘道的 Proxy 設定
description: 設定內部部署資料閘道的 Proxy 設定的相關資訊。
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 130f4dcea4bc168bd71cd6d8c7c623bfca95d259
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2018
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

預設設定適用於 Windows 驗證。 若您的 Proxy 使用另一種格式的驗證，您將必須變更設定。 若您不確定，應該連絡網路系統管理員。

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

## <a name="next-steps"></a>後續步驟
[內部部署資料閘道 (個人模式)](service-gateway-personal-mode.md)
[防火牆資訊](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

