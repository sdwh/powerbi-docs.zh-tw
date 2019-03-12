---
ms.openlocfilehash: d2f8d15c53271b4919d04644407577eec2cea238
ms.sourcegitcommit: 80961ace38ff9dac6699f81fcee0f7d88a51edf4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56246747"
---
## <a name="general"></a>一般
**問：** 實際的 Windows 服務稱為什麼？  
**答：** 閘道在服務中稱為內部部署資料閘道服務

**問：** 閘道需求為何？  
**答：** 請參閱主要[閘道文章](../service-gateway-onprem.md)的＜需求＞一節。

**問：** 閘道支援哪些資料來源？  
**答：** 請參閱主要[閘道文章](../service-gateway-onprem.md)的資料來源表。

**問：** 雲端資料來源 (如 Azure SQL Database) 需要閘道嗎？  
**答：** 否！ 此服務不需要閘道就能連接至該資料來源。

**問：** 雲端有任何閘道輸入連線嗎？  
**答：** 否。  閘道使用 Azure 服務匯流排的輸出連線。

**問：** 如果封鎖輸出連線會怎麼樣？ 需要開啟什麼？  
**答：** 請參閱閘道使用的[連接埠清單](../service-gateway-onprem.md#ports)和主機。

**問：** 閘道必須和資料來源安裝在同一部電腦嗎？  
**答：** 否。  閘道會使用之前提供的連接資訊，連接至資料來源。 就這一點而言，請將閘道視為用戶端應用程式。 它只需要能夠連接至之前提供的伺服器名稱即可。

**問：** 從閘道對資料來源執行查詢會有何種延遲？ 最佳架構為何？  
**答：** 建議您讓閘道盡可能接近資料來源，以避免網路延遲。 如果可以將閘道安裝在實際的資料來源上，就能將其造成的延遲降到最低。 亦請考慮資料中心。 例如，如果您的服務利用美國西部的資料中心，而您將 SQL Server 裝載於 Azure VM，您可能會希望 Azure VM 也位在美國西部。 這會將延遲降至最低，並可避免 Azure VM 的輸出流量費用。

**問：** 網路頻寬有任何需求嗎？  
**答：** 網路連線建議要有良好的輸送量。 每個環境都不同，而且這也要看傳送的資料量而定。 使用 ExpressRoute 有利於保證內部部署與 Azure 資料中心之間的輸送量等級。

您可以使用協力廠商的 [Azure Speed Test 應用程式](http://azurespeedtest.azurewebsites.net/)協助測量輸送量。

**問：** 可以使用 Azure Active Directory 帳戶執行閘道 Windows 服務嗎？  
**答：** 否。  Windows 服務必須有有效的 Windows 帳戶。 預設使用服務 SID (*NT SERVICE\PBIEgwService*) 執行。

**問：** 結果會如何傳回雲端？  
**答：** 透過 Azure 服務匯流排傳回。 如需詳細資訊，請參閱[運作方式](../service-gateway-onprem.md#how-the-gateway-works)。

**問：** 我的認證會儲存在哪裡？  
**答：** 您輸入的資料來源認證會以加密狀態儲存在閘道雲端服務中。 認證會在內部部署閘道解密。

**問：** 可以將閘道放在周邊網路 (也稱為周邊網路 (DMZ) 及遮蔽式子網路) 嗎？  
**答：** 此閘道必須能夠連接到資料來源。 若資料來源無法在您的周邊網路中存取，此閘道就無法與其連接。 例如，若您的 SQL Server 不在您的周邊網路中， 您就無法從周邊網路連線到您的 SQL Server。 若您將此閘道部署在您的周邊網路中，其就無法聯繫 SQL Server。

**問：** 可以強制閘道在 Azure 服務匯流排使用 HTTPS 流量，而不使用 TCP 嗎？  
**答：** 是。 不過，這會大幅降低效能。 您會需要修改 *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* 檔案。 您會需要將值從 `AutoDetect` 變更為 `Https`。 根據預設，這個檔案位於 *C:\Program Files\On-premises data gateway* 。

**問：** 我需要將 Azure DataCenter IP 清單加入允許清單嗎？ 何處取得清單？  
**答：** 如果您要封鎖輸出 IP 流量，您可能需要將 Azure DataCenter IP 清單加入允許清單。 目前，閘道會使用 IP 位址及完整網域名稱來與 Azure 服務匯流排通訊。 Azure DataCenter IP 清單會每週更新一次。 您可以下載 [Microsoft Azure 資料中心的 IP 清單](https://www.microsoft.com/download/details.aspx?id=41653)。

```xml
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>高可用性/災害復原
**問：** 有任何為閘道啟用高可用性案例的計劃嗎？  
**答：** 有，這是 Power BI 小組目前投入的領域。 請持續關注 [Power BI 部落格](https://powerbi.microsoft.com/blog/)以取得這項功能的進一步更新。

**問：** 災害復原有哪些選項？  
**答：** 您可以使用修復金鑰還原或移動閘道。 請在安裝閘道時提供修復金鑰。

**問：** 修復金鑰的優勢是什麼？  
**答：** 它提供移轉或修復閘道設定的方法。 這也適用於災害復原。

## <a name="troubleshooting"></a>疑難排解
**問：** 閘道記錄位於何處？  
**答：** 請參閱[疑難排解文章](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting)的＜工具＞一節。

**問：** 我如何知道哪些查詢傳送到了內部部署資料來源？  
**答：** 您可以啟用查詢追蹤。  這包括正在傳送的查詢。 完成疑難排解後，請記得變更回原始值。 啟用追蹤查詢會使得記錄變大。

您也可以查看資料來源的追蹤查詢工具。 例如，SQL Server 和 Analysis Services 可以使用擴充事件或 SQL Profiler。

