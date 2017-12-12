---
title: "內部部署資料閘道的高可用性叢集"
description: "您可以建立內部部署資料閘道的叢集，您的企業提供高可用性。"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 12/05/2017
ms.author: davidi
ms.openlocfilehash: 0288e9613a187b64e5bc71c952e01d70f1f56012
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="high-availability-clusters-for-on-premises-data-gateway"></a>內部部署資料閘道的高可用性叢集
您可以建立**內部部署資料閘道**安裝的**高可用性叢集**，以確保貴組織可以存取 Power BI 報告和儀表板中使用的內部部署資料資源。 這類叢集允許閘道系統管理員將閘道群組，以避免存取內部部署資料資源時發生單一失敗點。 本文說明建立內部部署資料閘道的高可用性叢集時可以採取的步驟，並分享進行這些設定時的最佳做法。 高可用性閘道叢集需要 2017 年 11 月更新的內部部署資料閘道或更新版本。


## <a name="setting-up-high-availability-clusters-of-gateways"></a>設定閘道的高可用性叢集

在**內部部署資料閘道**安裝程序期間，您可以指定是否應將閘道新增至現有的閘道叢集。 

![](media/service-gateway-high-availability-clusters/gateway_clusters_01.png)

若要將閘道新增至現有的叢集，您必須提供主要閘道執行個體的復原金鑰，以供您需要新閘道加入的叢集使用。 叢集的主要閘道必須執行來自 2017 年 11 月版或更新版本的閘道更新。 


## <a name="managing-a-gateway-cluster"></a>管理閘道叢集

一旦閘道叢集包含兩個或多個閘道，所有的閘道管理作業 (例如新增資料來源或授與系統管理員閘道權限) 都適用於屬於叢集的所有閘道。 

當系統管理員使用 [Power BI 服務] 齒輪圖示下找到的 [管理閘道] 功能表項目時，會看到已註冊叢集或個別閘道的清單，但看不到叢集成員的個別閘道執行個體。

所有新的 [已排程重新整理] 要求和 DirectQuery 作業會自動路由到指定閘道叢集的主要執行個體。 如果主要閘道執行個體不在線上，就會將要求路由至叢集中的另一個閘道執行個體。

## <a name="powershell-support-for-gateway-clusters"></a>閘道叢集的 PowerShell 支援

PowerShell 指令碼可用於內部部署資料閘道安裝資料夾。 依預設，該資料夾是 C:\Program Files\On-premises data gateway。 您必須使用 PowerShell 第 5 版或更新版本，這些指令碼才能正常運作。 PowerShell 指令碼可讓使用者執行下列作業：

-   擷取可供使用者使用的閘道叢集清單
-   擷取叢集中註冊的閘道執行個體清單，以及其線上或離線狀態
-   修改叢集內閘道執行個體的啟用/停用狀態，以及其他閘道屬性
-   刪除閘道

若要在資料表中執行 PowerShell 命令，您必須先採取下列步驟：

1. 以系統管理員身分開啟 PowerShell 命令視窗
2. 然後執行下列一次性 PowerShell 命令 (這樣會假設您永遠不會在目前電腦上執行 PowerShell 命令)：

    ```
    Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force
    ```

3. 接下來，在 PowerShell 視窗中瀏覽至內部部署資料閘道安裝資料夾，並使用下列命令匯入必要模組：

    ```
    Import-Module .\OnPremisesDataGatewayHAMgmt.psm1
    ```

完成這些步驟之後，您可以使用下表中的命令來管理閘道叢集

| **命令** | **描述** | **參數** |
| --- | --- | --- |
| Login-OnPremisesDataGateway |此命令可讓使用者登入並管理其內部部署資料閘道叢集。  您必須先執行此命令並登入後，其他高可用性命令才能正常運作。 請注意：登入呼叫過程中所需的 AAD 驗證權杖有效期限只有 1 小時，之後便會過期。 您可以重新執行登入命令來取得新的權杖。| AAD 使用者名稱和密碼 (在命令執行過程而非初始引動過程提供)|
| Get-OnPremisesDataGatewayClusters | 擷取已登入使用者的閘道叢集清單。 | (選擇性) 您可以將格式參數傳遞到此命令來增加可讀性，例如：Format-Table -AutoSize -Wrap |
| Get-OnPremisesDataClusterGateways | 在指定的叢集內擷取閘道清單，以及每個閘道的其他資訊 (上線/離線狀態、電腦名稱等) | -ClusterObjectID xyz (其中 xyz 會以實際的叢集物件 ID 值取代，可使用 Get-OnPremisesDataGatewayClusters 命令加以擷取)|
| Set-OnPremisesDataGateway | 可讓您設定叢集內指定閘道的屬性值，包括啟用/停用特定閘道執行個體的能力  | -ClusterObjectID xyz (xyz 應以實際的叢集物件 ID 值取代，可使用 Get-OnPremisesDataGatewayClusters 命令加以擷取) -GatewayObjectID abc (abc 應以實際的閘道物件 ID 值取代，可使用 Get-OnPremisesDataClusterGateways 命令加以擷取，指定叢集物件 ID) |
| Get-OnPremisesDataGatewayStatus | 可讓您擷取叢集內指定閘道執行個體的狀態  | -ClusterObjectID xyz (xyz 應以實際的叢集物件 ID 值取代，可使用 Get-OnPremisesDataGatewayClusters 命令加以擷取) -GatewayObjectID abc (abc 應以實際的閘道物件 ID 值取代，可使用 Get-OnPremisesDataClusterGateways 命令加以擷取，指定叢集物件 ID) |
| Remove-OnPremisesDataGateway  | 可讓您從叢集移除閘道執行個體 - 請注意，無法移除叢集中的主要閘道，除非已將叢集中的所有其他閘道移除。| -ClusterObjectID xyz (xyz 應以實際的叢集物件 ID 值取代，可使用 Get-OnPremisesDataGatewayClusters 命令加以擷取) -GatewayObjectID abc (abc 應以實際的閘道物件 ID 值取代，可使用 Get-OnPremisesDataClusterGateways 命令加以擷取，指定叢集物件 ID) |


## <a name="next-steps"></a>後續步驟

-   [管理您的資料來源─Analysis Services](service-gateway-enterprise-manage-ssas.md)  
-   [管理您的資料來源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
-   [管理您的資料來源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
-   [管理您的資料來源 - Oracle](service-gateway-onprem-manage-oracle.md)  
-   [管理您的資料來源 - 匯入/已排程的重新整理](service-gateway-enterprise-manage-scheduled-refresh.md)  
-   [內部部署資料閘道 - 深入資訊](service-gateway-onprem-indepth.md)  
-   [內部部署資料閘道 (個人模式)](service-gateway-personal-mode.md)
-   [進行內部部署資料閘道的 Proxy 設定](service-gateway-proxy.md)  
-   [使用 Kerberos 以從 Power BI 單一登入 (SSO) 到內部部署資料來源](service-gateway-kerberos-for-sso-pbi-to-on-premises-data.md)  

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
