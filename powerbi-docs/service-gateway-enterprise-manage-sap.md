---
title: 管理您的資料來源 - SAP HANA
description: 如何管理內部部署資料閘道及屬於該閘道的資料來源。 本文為 SAP HANA 專用。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: a09388e8b22131c9b82771385b69142b18e3cc84
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730016"
---
# <a name="manage-your-data-source---sap-hana"></a>管理您的資料來源 - SAP HANA

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

在您[安裝內部部署資料閘道](/data-integration/gateway/service-gateway-install)後，您將需要[新增資料來源](service-gateway-data-sources.md#add-a-data-source)，其可與閘道搭配使用。 本文會探討如何搭配閘道和 SAP HANA 資料來源來用於排程重新整理或 DirectQuery。

## <a name="add-a-data-source"></a>加入資料來源

如需如何新增資料來源的資訊，請參閱[新增資料來源](service-gateway-data-sources.md#add-a-data-source)。 針對 [資料來源類型]  選取 SAP HANA。

![新增 SAP HANA 資料來源](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

在您選取 SAP HANA 資料來源類型後，您接下來可以填入資料來源的 [伺服器]  、[使用者名稱]  和 [密碼]  資訊。

> [!NOTE]
> 資料來源的所有查詢都會使用這些認證來執行。 若要深入了解認證的儲存方式，請參閱[在雲端中儲存加密認證](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud)。

![填入資料來源設定](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

在您填入所有項目後，選取 [新增]  。 您現在可以使用此資料來源，針對內部部署的 SAP HANA 伺服器，用於已排程的重新整理或 DirectQuery。 如果成功，您會看到 [連接成功]  。

![顯示連線狀態](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>進階設定

您可以選擇性地設定您資料來源的隱私權等級。 這可以控制合併資料的方式。 這只能用於已排程的重新整理。 不適用於 DirectQuery。 若要深入了解您資料來源的隱私權等級，請參閱[隱私權等級 (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)。

![設定隱私權等級](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="using-the-data-source"></a>使用資料來源

在您建立資料來源後，便可以搭配 DirectQuery 連線或已排程重新整理來使用它。

> [!NOTE]
> Power BI Desktop 和內部部署資料閘道內資料來源的伺服器和資料庫名稱必須相符。

您的資料集和閘道內的資料來源是根據您的伺服器名稱和資料庫名稱以建立連結。 這些項目必須相符。 例如，若您在 Power BI Desktop 中為伺服器名稱提供 IP 位址，您將需要在閘道設定中針對資料來源使用 IP 位址。 若您使用 *SERVER\INSTANCE*，則在 Power BI Desktop 中，您將必須在針對閘道設定的資料來源內使用相同值。

這適用於 DirectQuery 和已排程的重新整理。

### <a name="using-the-data-source-with-directquery-connections"></a>使用 DirectQuery 連接來使用資料來源

您需要確保在 Power BI Desktop 和針對閘道所設定的資料來源之間具有相符的伺服器和資料庫名稱。 您也需要確保使用者會列出在資料來源的 [使用者]  索引標籤中，才能發佈 DirectQuery 資料集。 當您第一次匯入資料時，Power BI Desktop 內會出現 DirectQuery 的選取項目。 如需使用 DirectQuery 的詳細資訊，請參閱[在 PowerBI Desktop 中使用 DirectQuery](desktop-use-directquery.md)。

發行之後，您的報表會從 Power BI Desktop 或**取得資料**開始工作。 建立閘道內的資料來源之後，可能需要幾分鐘的時間才能使用連線。

### <a name="using-the-data-source-with-scheduled-refresh"></a>使用已排程的重新整理使用資料來源

若您已列在閘道內所設定資料來源的 [使用者]  索引標籤中，且伺服器和資料庫名稱相符，您將會看到可以與已排程重新整理搭配使用的閘道選項。

![顯示使用者](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>後續步驟

* [為內部部署資料閘道進行疑難排解](/data-integration/gateway/service-gateway-tshoot)
* [針對閘道進行疑難排解 - Power BI](service-gateway-onprem-tshoot.md)  

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

