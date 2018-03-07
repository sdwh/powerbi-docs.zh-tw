---
title: "內部部署資料閘道"
description: "這是 Power BI 的內部部署資料閘道概觀。 您可以使用此閘道處理 DirectQuery 資料來源。 您也可以使用此閘道以內部部署資料重新整理雲端資料集。"
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
ms.date: 02/22/2018
ms.author: davidi
LocalizationGroup: Gateways
ms.openlocfilehash: c9025194ebe8ce6b1829aacd9d74bff5d9c55e3c
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2018
---
# <a name="on-premises-data-gateway"></a>內部部署資料閘道
內部部署資料閘道作為橋接器，替內部部署資料 (非位於雲端的資料) 與 Power BI、Microsoft Flow、Logic Apps 以及 PowerApps 服務之間，提供快速且安全的資料傳輸。

您可以同時以不同服務使用單一閘道。 如果您同時使用 Power BI 與 PowerApps，單一閘道亦可同時用於兩者。 其取決於您登入時使用的帳戶。

> [!NOTE]
> 內部部署資料閘道會在所有模式中實作資料壓縮和傳輸加密。
> 
> 

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-requirements-include.md)]

### <a name="limitations-of-analysis-services-live-connections"></a>Analysis Services 即時連線的限制
您可以使用即時連線針對表格式或多維度執行個體。

| **伺服器版本** | **必要的 SKU** |
| --- | --- |
| 2012 SP1 CU4 或更新版本 |商業智慧和企業版 SKU |
| 2014 |商業智慧和企業版 SKU |
| 2016 |標準 SKU 或更高版本 |

* 不支援資料格層級格式化與轉譯功能。
* 動作和命名集不會公開至 Power BI，但您仍然可以連接至同樣包含動作或命名集的多維度 Cube，然後建立視覺效果和報表。

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="download-and-install-the-on-premises-data-gateway"></a>下載並安裝內部部署資料閘道
請於下載功能表下選取 [資料閘道]，以下載閘道。 下載[內部部署資料閘道](http://go.microsoft.com/fwlink/?LinkID=820925)。

![](media/service-gateway-onprem/powerbi-download-data-gateway.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-install-include](./includes/gateway-onprem-install-include.md)]

## <a name="install-the-gateway-in-personal-mode"></a>以個人模式安裝閘道
> [!NOTE]
> 個人只適用於 Power BI。
> 
> 

安裝個人閘道之後，您必須啟動 **Power BI Gateway─Personal 設定精靈**。

![](media/service-gateway-onprem/personal-gateway-launch-configuration.png)

然後您必須登入 Power BI 以將閘道註冊至雲端服務。

![](media/service-gateway-onprem/personal-gateway-signin.png)

您也必須提供 Windows 服務執行時會使用的 Windows 使用者名稱和密碼。 您可以指定與您自己的帳戶不同的 Windows 帳戶。 閘道器服務會使用此帳戶來執行。

![](media/service-gateway-onprem/personal-gateway-windows-service.png)

安裝完成後，您必須移至您在 Power BI 中的資料集，並確定已輸入您的內部部署資料來源的認證。

<a name="credentials"></a>

## <a name="storing-encrypted-credentials-in-the-cloud"></a>在雲端中儲存加密的認證
當您在閘道中加入資料來源時，您必須提供該資料來源的認證。 資料來源的所有查詢都會使用這些認證來執行。 認證使用非對稱式加密安全地加密，因此在儲存到雲端之前，都無法在雲端中解密。 認證會傳送至執行閘道的內部部署電腦，並在存取資料來源時解密。

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

<!-- How the gateway works -->
[!INCLUDE [gateway-onprem-how-it-works-include](./includes/gateway-onprem-how-it-works-include.md)]

## <a name="troubleshooting"></a>疑難排解
若您在安裝和設定閘道時遇到問題，請務必參閱[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)。 若您認為您的防火牆發生問題，請參閱疑難排解文章中的[防火牆或 Proxy](service-gateway-onprem-tshoot.md#firewall-or-proxy) 一節。

若您認為自己遇到閘道 Proxy 問題，請參閱[進行 Power BI Gateway 的 Proxy 設定](service-gateway-proxy.md)。

## <a name="next-steps"></a>後續步驟
[管理您的資料來源─Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[管理您的資料來源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[管理您的資料來源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
[管理您的資料來源 - Oracle](service-gateway-onprem-manage-oracle.md)  
[管理您的資料來源 - 匯入/已排程的重新整理](service-gateway-enterprise-manage-scheduled-refresh.md)  
[內部部署資料閘道 - 深入資訊](service-gateway-onprem-indepth.md)  
[內部部署資料閘道 (個人模式) - 新版本的個人閘道](service-gateway-personal-mode.md)
[進行內部部署資料閘道的 Proxy 設定](service-gateway-proxy.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

