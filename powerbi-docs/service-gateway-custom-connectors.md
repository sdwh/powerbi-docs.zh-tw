---
title: 透過內部部署資料閘道使用自訂資料連接器
description: 您可以透過內部部署資料閘道使用自訂資料連接器。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 51d03582ec91b926526a075a356323eb4f95a84b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "77609876"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>透過內部部署資料閘道使用自訂資料連接器

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

有了適用於 Power BI 的資料連接器，您可以連接並存取應用程式、服務或資料來源中的資料。 您可以在 Power BI Desktop 中開發並使用自訂資料連接器。

若要深入了解如何為 Power BI 開發自訂資料連接器，請參閱[資料連接器 SDK GitHub 頁面](https://aka.ms/dataconnectors)。 此網站包含 Power BI 和 Power Query 的開始使用方式和範例資訊。

當您在 Power BI Desktop 中建置使用自訂資料連接器的報表時，您可以使用內部部署資料閘道從 Power BI 服務重新整理這些報表。

## <a name="enable-and-use-this-capability"></a>啟用及使用此功能

當您安裝內部部署資料閘道的 2018 年七月版本或更新版本時，您會在內部部署資料閘道應用程式中看到 [連接器]  索引標籤。 在 [從資料夾載入自訂資料連線器]  方塊中，選取執行閘道服務之使用者可存取的資料夾。 預設使用者是 *NT SERVICE\PBIEgwService*。 閘道會自動載入位於該資料夾中的自訂連接器檔案。 它們會出現在資料連線器清單中。

![自訂資料連接器](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

若您使用的是內部部署資料閘道 (個人模式)，您就可以將 Power BI 報表上傳到 Power BI 服務，並使用閘道來加以重新整理。

針對內部部署資料閘道，您必須為您的自訂連接器建立資料來源。 在 Power BI 服務的閘道設定頁面中，當您選取閘道叢集以允許透過此叢集使用自訂連接器時，您應該會看到選項。 確定叢集中的所有閘道都有 2018 年 7 月更新版或更新版本，才能使用此選項。 選取該選項以允許透過此叢集使用自訂連接器。

![[閘道叢集設定] 頁面](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

啟用此選項時，您的自訂連接器會顯示為可在此閘道叢集下建立的可用資料來源。 在您建立使用新自訂連接器的資料來源之後，您可以在 Power BI 服務中使用該自訂連接器來重新整理 Power BI 報表。

![[資料來源設定] 頁面](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>考量與限制

* 請確定您所建立的資料夾可供背景閘道服務存取。 一般而言，無法存取您使用者的 Windows 資料夾或系統資料夾下的資料夾。 如果無法存取資料夾，內部部署資料閘道應用程式會顯示一則訊息。 此指示不適用於內部部署資料閘道 (個人模式)。
* 若要讓自訂連接器使用內部部署資料閘道，它們需要在自訂連接器的程式碼中實作 "TestConnection" 區段。 當您透過 Power BI Desktop 使用自訂連接器時，就不需要此區段。 基於此原因，您有一個可透過 Power BI Desktop 運作但無法透過閘道運作的連接器。 如需如何實作 TestConnection 區段的詳細資訊，請參閱[此文件](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support)。
* 目前僅針對閘道管理員支援透過閘道的 OAuth 自訂連接器，而針對其他資料來源使用者則不支援。

## <a name="next-steps"></a>後續步驟

* [管理您的資料來源─Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [管理您的資料來源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [管理您的資料來源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [管理您的資料來源 - Oracle](service-gateway-onprem-manage-oracle.md)  
* [管理您的資料來源 - 匯入/排程重新整理](service-gateway-enterprise-manage-scheduled-refresh.md)
* [設定內部部署資料閘道的 Proxy 設定](/data-integration/gateway/service-gateway-proxy)
* [針對從 Power BI 到內部部署資料來源的單一登入 (SSO) 使用 Kerberos](service-gateway-sso-kerberos.md)  

有其他問題嗎？ 請嘗試詢問 [Power BI 社群](https://community.powerbi.com/)。
