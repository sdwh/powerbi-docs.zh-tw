---
title: 使用 Power BI 連線到 Snowflake
description: 使用 SSO 的 Snowflake for Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "77576860"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>連線到 Power BI 服務中的 Snowflake

## <a name="introduction"></a>簡介

連線到 Power BI 服務中的 Snowflake 只有一個方面與其他連接器不同，就是為 AAD 提供額外的容量 (有 SSO 選項)。 整合的不同部分需有跨 Snowflake、Power BI 和 Azure 的不同系統管理角色。 您也可以選擇啟用 AAD 驗證，而不使用 SSO。 基本驗證的運作方式和服務中其他連接器相類似。

如果您想要設定 AAD 整合，以及選擇性啟用 SSO：
* 如果您是 Snowflake 系統管理員，請參閱 Snowflake 文件中的 [Power BI SSO to Snowflake - Getting Started](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) (Power BI SSO 至 Snowflake - 使用者入門) 一文。
* (SSO) 如果您是 Power BI 系統管理員，請查看＜Power BI 服務設定 - 系統管理入口網站＞一節
* (SSO) 如果您是 Power BI 資料集建立者，請查看＜Power BI 服務設定 - 啟用資料集＞一節

## <a name="power-bi-service-configuration"></a>Power BI 服務設定

### <a name="admin-portal"></a>管理入口網站

如果您想要啟用 SSO，則租用戶系統管理員必須前往系統管理員入口網站，並核准將 Power BI AAD 認證傳送至 Snowflake。

![Snowflake SSO 的租用戶系統管理設定](media/service-connect-snowflake/snowflakessotenant.png)

巡覽至您的「系統管理員入口網站」，選取 [租用戶設定] 資訊看板項目，向下捲動至 [整合設定]，您即會看到 [Snowflake SSO] 選項。

如警告所述，您必須手動啟用此服務以同意將 AAD 權杖傳送至 Snowflake 伺服器。 若要啟用此選項，請按一下 [停用] 切換，然後按 [套用] 並等待設定變更生效。 服務傳播此設定的最長時間可能為一小時。

完成後，您就可以利用 SSO 來使用報表。

### <a name="configuring-a-dataset-with-aad"></a>以 AAD 設定資料集

將以 Snowflake 連接器為基礎的報表發佈至 Web 之後，在 Power BI Web 服務中，資料集建立者必須巡覽至適當的工作區，依序選取 [資料集] 和 [設定] (在相關資料集旁，提供其他動作的 [...] 功能表下)。

因為 Power BI 的運作方式，SSO 只會在沒有任何資料來源透過內部部署資料閘道執行時運作。

* 如果您只在資料模型中使用 Snowflake 來源，則若選擇不使用內部部署資料閘道，您就可以使用 SSO
* 如果您同時使用 Snowflake 來源和其他來源，則若所有來源都不使用內部部署資料閘道，您就可以使用 SSO
* 如果您透過內部部署資料閘道使用 Snowflake 來源，則目前不支援 AAD 認證。 如果您嘗試從已安裝閘道的單一 IP 存取 VNet，而不是從整個 Power BI IP 範圍存取 VNet，這就可能是相關的。
* 如果您同時使用 Snowflake 來源與需要閘道的其他來源，則將必須透過內部部署資料閘道來使用 Snowflake，且無法使用 SSO。

如需如何使用內部部署資料閘道的詳細資訊，請參閱 [什麼是內部部署資料閘道](https://docs.microsoft.com/power-bi/service-gateway-onprem)一文

如不打算使用閘道，則一切已準備就緒。 如已在內部部署資料閘道上設定 Snowflake 認證，但只在模型中使用該資料來源，您可以按一下 [資料集設定] 頁面上的切換，以關閉該資料模型的閘道。

![關閉閘道的資料集設定](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

資料集建立者必須選取 [資料來源認證] 並登入。 此資料集可以使用基本認證或 OAuth2 (AAD) 認證來登入 Snowflake。 如果您選擇使用 AAD，則可啟用資料集以使用 SSO。 當第一位使用者登入 Snowflake 以取得資料集時，其必須選取讓其他使用者擁有其擷取資料所用 Oauth2 認證的選項。 這將會啟用 AAD SSO。 不論初始使用者使用基本驗證或 OAuth2 (AAD) 登入，為 SSO 傳送的都會是 AAD 認證。 

![Snowflake SSO 的資料集設定](media/service-connect-snowflake/snowflakessocredui.png)

此動作完成後，任何其他使用者都應該自動使用其 AAD 驗證連線到來自該 Snowflake 資料集的資料。

如果您選擇不啟用 SSO，則重新整理報表之使用者將會使用已登入使用者的認證，就像大多數其他 Power BI 報表一樣。

### <a name="troubleshooting"></a>疑難排解

如果整合方面發生任何問題，請參閱 Snowflake [疑難排解指南](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting)。

