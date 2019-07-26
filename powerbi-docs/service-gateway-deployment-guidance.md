---
title: 部署 Power BI 之資料閘道的指引
description: 了解部署 Power BI 之閘道的最佳做法和考量。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271711"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>部署 Power BI 之資料閘道的指引

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

本文提供在網路環境中部署 Power BI 資料閘道的指引和考量。

如需如何下載、安裝、設定和管理內部部署資料閘道的資訊，請參閱[什麼是內部部署資料閘道](/data-integration/gateway/service-gateway-onprem)。 您也可以前往 [Microsoft Power Blog](https://powerbi.microsoft.com/blog/) (Microsoft Power 部落格) 及 [Microsoft Power BI Community](https://community.powerbi.com/) (Microsoft Power BI 社群) 網站來深入了解內部部署資料閘道及 Power BI。

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>內部部署資料閘道的安裝考量

在為您的 Power BI 雲端服務安裝內部部署資料閘道前，建議您謹記一些考量事項。 下列各節會描述這些考量事項。

### <a name="number-of-users"></a>使用者數目

使用利用閘道之報表的使用者數目是決定在何處安裝閘道的重要度量。 以下是要考慮的一些問題：

* 使用者會在每天的不同時間使用這些報表嗎？
* 他們正在使用的連接類型 (DirectQuery 或 Import) 為何？
* 所有使用者都使用相同的報表嗎？

若使用者都會在每天的相同時間存取指定報表，則建議您確定已在可處理所有這些要求的電腦上安裝閘道 (請參閱下列各節，以取得可協助您判斷這個情況的效能計數器和最低需求)。

**Power BI** 中有一個「報表」  只允許「一個」  閘道的條件約束；因此，即使報表是根據多個資料來源，所有這類資料來源還是必須經過單一閘道。 不過，如果儀表板根據「多個」  報表，您可以針對每個參與的報表使用專用閘道，因而將閘道負載分散到多個參與該單一儀表板的報表。

### <a name="connection-type"></a>連線類型

**Power BI** 提供兩種類型的連線：**DirectQuery** 和**匯入**。 並非所有資料來源都支援兩種連接類型，而且有許多原因可能會導致選擇其中一個，例如安全性需求、效能、資料限制和資料模型大小。 您可以在[可用資料來源類型清單](service-gateway-data-sources.md#list-of-available-data-source-types)中深入了解連線類型和支援的資料來源。

根據使用的連接類型而定，閘道使用量可能會不同。 例如，可能的話，您應該嘗試分隔 **DirectQuery** 資料來源與 [排程重新整理]  資料來源 (假設它們位於不同的報表中，而且可以予以分隔)。 在早上排程重新整理用於公司主要儀表板的大規模資料模型的同時，這樣做可避免閘道將數千個 DirectQuery 要求排入佇列中。 以下是每個所需要考量的事項：

* **排程重新整理**：根據查詢大小以及每天發生的重新整理次數，您可以選擇保持建議的最低硬體需求，或升級為更高效能的電腦。 如果未摺疊指定的查詢，就會在閘道電腦上進行轉換；因此，閘道電腦受惠於具有更多可用的 RAM。

* **DirectQuery**：每次任何使用者開啟報表或查看資料時，都會傳送查詢。 因此，如果您預期有 1,000 位以上的使用者同時存取資料，則您會想要確定電腦具有穩固且支援硬體的元件。 更多的 CPU 核心將會導致 **DirectQuery** 連接具有更佳的輸送量。

您可以在內部部署資料閘道的[安裝需求](/data-integration/gateway/service-gateway-install#requirements)中找到要進行安裝的電腦需求。

### <a name="location"></a>位置

閘道安裝位置可能會對查詢效能造成重大影響，因此請嘗試確定您的閘道、資料來源位置和 Power BI 租用戶盡可能彼此接近，將網路延遲降至最低。 若要判斷 Power BI 租用戶位置，請在 Power BI 服務中選取右上角的 **?** 圖示，然後選取 [關於 Power BI]  。

![判斷您的 Power BI 租用戶位置](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

此外，若您想要搭配 Azure Analysis Services 使用 Power BI 閘道，請確認在這兩個項目中的資料區域相符。 如需設定多個服務資料區域的詳細資訊，請觀看[此影片](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/)。

## <a name="next-steps"></a>後續步驟

* [設定 Proxy 設定](/data-integration/gateway/service-gateway-proxy)  
* [針對閘道進行疑難排解 - Power BI](service-gateway-onprem-tshoot.md)  
* [內部部署資料閘道常見問題集 - Power BI](service-gateway-power-bi-faq.md)  

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

