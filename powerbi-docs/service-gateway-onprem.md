---
title: 內部部署資料閘道
description: 這是 Power BI 的內部部署資料閘道概觀。 您可以使用此閘道處理 DirectQuery 資料來源。 您也可以使用此閘道以內部部署資料重新整理雲端資料集。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 57c4292913a2056ab285716de1e1b83e2313f723
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307107"
---
# <a name="what-is-an-on-premises-data-gateway"></a>什麼是內部部署的資料閘道？

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

內部部署資料閘道會用來作為橋樑，在內部部署資料 (非位於雲端的資料) 與數個 Microsoft 雲端服務 (包括 Power BI、PowerApps、Microsoft Flow、Azure Analysis Services 以及 Logic Apps) 之間，提供快速且安全的資料轉送。 使用閘道，組織便能將資料庫和其他資料來源保留在它們的內部部署網路上，同時安全地在雲端服務中使用內部部署資料。

## <a name="how-the-gateway-works"></a>閘道運作方式

![閘道概觀](media/service-gateway-onprem/on-premises-data-gateway.png)

如需閘道運作方式的詳細資訊，請參閱[內部部署資料閘道架構](/data-integration/gateway/service-gateway-onprem-indepth)。

## <a name="types-of-gateways"></a>閘道類型

閘道有兩種不同的類型，分別適用於不同案例：

* **內部部署資料閘道** – 允許多個使用者連線到多個內部部署資料來源。 您可以透過單一閘道安裝來使用具備所有支援服務的內部部署資料閘道。 此閘道非常適合有許多人存取多個資料來源的複雜案例。

* **內部部署資料閘道 (個人模式)** - 可讓一位使用者連線至來源，但不能與其他人共用。 內部部署資料閘道 (個人模式) 僅能搭配 Power BI 使用。 此閘道非常適合您是建立報表的唯一人員，且不需要與其他人共用任何資料來源的案例。

## <a name="using-a-gateway"></a>使用閘道

使用閘道有四個主要步驟：

1. 在本機電腦上[下載並安裝閘道](/data-integration/gateway/service-gateway-install)。
2. 根據您的防火牆和其他網路要求，[設定](/data-integration/gateway/service-gateway-app)閘道。
3. [新增閘道系統管理員](/data-integration/gateway/service-gateway-manage)，讓他們管理其他網路要求。
4. 發生錯誤時，針對閘道[進行疑難排解](service-gateway-onprem-tshoot.md)。

## <a name="next-steps"></a>後續步驟

* [安裝內部部署資料閘道](/data-integration/gateway/service-gateway-install)


有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
