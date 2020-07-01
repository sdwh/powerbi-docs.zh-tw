---
title: 管理您的資料來源 - Oracle
description: 如何管理內部部署資料閘道及屬於該閘道的資料來源。
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 5ebc9a36b4a4e54d6388625921c98c571859568f
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237584"
---
# <a name="manage-your-data-source---oracle"></a>管理您的資料來源 - Oracle

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

在您[安裝內部部署資料閘道](/data-integration/gateway/service-gateway-install)後，您需要[新增資料來源](service-gateway-data-sources.md#add-a-data-source)，其可與閘道搭配使用。 本文會探討如何針對已排程重新整理或 DirectQuery 使用閘道和 Oracle 資料來源。

## <a name="install-the-oracle-client"></a>安裝 Oracle 用戶端

若要將閘道連接至您的 Oracle 伺服器，必須先安裝及設定 .Net 的 Oracle 資料提供者 (ODP.NET)。 ODP.NET 是 Oracle 資料存取元件 (ODAC) 的一部分。

針對 32 位元版本的 Power BI Desktop，請使用下列連結來下載並安裝 32 位元的 Oracle 用戶端：

* [32 位元的 Oracle Access Components (ODAC) 與 Oracle Developer Tools for Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

針對 64 位元版本的 Power BI Desktop 或內部部署資料閘道，請使用下列連結來下載並安裝 64 位元的 Oracle 用戶端：

* [適用於 Windows x64 的 64 位元 ODAC 12.2c Release 1 (12.2.0.1.0)](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

安裝用戶端之後，請使用您資料庫的適當資訊來設定 tnsnames.ora 檔案。 Power BI Desktop 和閘道將會離開 tnsnames.ora 檔案中定義的 net_service_name。 如果未設定 net_service_name，您就無法連接。 tnsnames.ora 的預設路徑為 `[Oracle Home Directory]\Network\Admin\tnsnames.ora`。 如需如何設定 tnsnames.ora 檔案的詳細資訊，請參閱 [Oracle:本機命名引數 (tnsnames.ora)](https://docs.oracle.com/cd/B28359_01/network.111/b28317/tnsnames.htm)。

### <a name="example-tnsnamesora-file-entry"></a>範例 tnsnames.ora 檔案項目

以下是 tnsname.ora 中的項目基本格式：

```
net_service_name=
 (DESCRIPTION=
   (ADDRESS=(protocol_address_information))
   (CONNECT_DATA=
     (SERVICE_NAME=service_name)))
```

以下是填入的伺服器及連接埠資訊範例：

```
CONTOSO =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = oracleserver.contoso.com)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = CONTOSO)
    )
  )
```

## <a name="add-a-data-source"></a>加入資料來源

如需如何新增資料來源的詳細資訊，請參閱[新增資料來源](service-gateway-data-sources.md#add-a-data-source)。 在 [資料來源類型]  下選取 [Oracle]  。

![新增 Oracle 資料來源](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

在您選取 Oracle 資料來源類型後，請填入資料來源的資訊，其中包括 [伺服器]  和 [資料庫]  。 

在 [驗證方法]  下，您可以選擇 [Windows]  或 [基本]  。 若您計劃使用在 Oracle 而非 Windows 驗證中所建立的帳戶，請選擇 [基本]  。 然後輸入要用於這個資料來源的認證。

> [!NOTE]
> 資料來源的所有查詢都會使用這些認證來執行。 若要深入了解認證的儲存方式，請參閱[在雲端中儲存加密認證](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud)。

![填入資料來源設定](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

填入所有資訊之後，選取 [新增]  。 您現在可以使用此資料來源，針對內部部署的 Oracle 伺服器，用於已排程的重新整理或 DirectQuery。 如果成功，您會看到「連線成功」  。

![顯示連線狀態](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>進階設定

您可以選擇性地設定您資料來源的隱私權等級。 此設定可以控制合併資料的方式。 只能用於已排程的重新整理。 隱私權層級設定不適用於 DirectQuery。 若要深入了解您資料來源的隱私權等級，請參閱[隱私權等級 (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)。

![設定隱私權等級](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="use-the-data-source"></a>使用資料來源

建立資料來源之後，您便可以搭配 DirectQuery 連線，或是透過已排程的重新整理來使用它。

> [!WARNING]
> Power BI Desktop 和內部部署資料閘道內資料來源的伺服器和資料庫名稱必須相符。

您的資料集和閘道內的資料來源是根據您的伺服器名稱和資料庫名稱以建立連結。 這些名稱必須相符。 例如，若您在 Power BI Desktop 中為伺服器名稱提供 IP 位址，則必須在閘道設定中針對資料來源使用 IP 位址。 此名稱也必須符合 tnsnames.ora 檔案中定義的別名。 如需 tnsnames.ora 檔案的詳細資訊，請參閱[安裝 Oracle 用戶端](#install-the-oracle-client)。

這項需求適用於 DirectQuery 和已排程的重新整理。

### <a name="use-the-data-source-with-directquery-connections"></a>使用 DirectQuery 連線來使用資料來源

請確定在 Power BI Desktop 和針對閘道所設定資料來源之間具有相符的伺服器和資料庫名稱。 您也必須確定資料來源的 [使用者]  索引標籤已列出使用者，才能發佈 DirectQuery 資料集。 當您第一次匯入資料時，Power BI Desktop 內會出現 DirectQuery 的選取項目。 如需如何使用 DirectQuery 的詳細資訊，請參閱[在 Power BI Desktop 中使用 DirectQuery](desktop-use-directquery.md)。

發佈之後，您的報表會從 Power BI Desktop 或**取得資料**開始工作。 建立閘道內的資料來源之後，可能需要幾分鐘的時間才能使用連線。

### <a name="use-the-data-source-with-scheduled-refresh"></a>使用已排程的重新整理使用資料來源

若您已列在閘道內所設定資料來源的 [使用者]  索引標籤中，且伺服器名稱和資料庫名稱相符，您將會看到可以與已排程重新整理搭配使用的閘道選項。

![顯示使用者](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>疑難排解

當命名語法不正確或未正確設定時，可能會遇到來自 Oracle 的多種錯誤：

* ORA-12154:TNS：無法解析指定的連接識別碼。
* ORA-12514:TNS：接聽程式目前不了解連接描述元中要求的服務。
* ORA-12541:TNS：沒有任何接聽程式。
* ORA-12170:TNS：發生連接逾時。
* ORA-12504:TNS 接聽程式在 CONNECT_DATA 中未得到 SERVICE_NAME。

若未安裝或未正確設定 Oracle 用戶端，便可能會發生這些錯誤。 若已安裝，請驗證 tnsnames.ora 檔案已正確設定，且您使用的是適當的 net_service_name。 您也必須確定使用 Power BI Desktop 的電腦與執行閘道的電腦所使用的 net_service_name 相同。 如需詳細資訊，請參閱[安裝 Oracle 用戶端](#install-the-oracle-client)。

> [!NOTE]
> 您也可能遭遇 Oracle 伺服器版本與 Oracle 用戶端版本之間的相容性問題。 一般而言，這些版本應當相符。

如何與閘道相關的其他疑難排解資訊，請參閱[為內部部署資料閘道進行疑難排解](/data-integration/gateway/service-gateway-tshoot)。

## <a name="next-steps"></a>後續步驟

* [針對閘道進行疑難排解 - Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](../admin/service-premium-what-is.md)

有其他問題嗎？ 請嘗試詢問 [Power BI 社群](https://community.powerbi.com/)。
