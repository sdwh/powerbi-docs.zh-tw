## <a name="firewall-or-proxy"></a>防火牆或 Proxy
若要了解如何為您的閘道提供 Proxy 資訊，請參閱[進行 Power BI 閘道的 Proxy 設定](../service-gateway-proxy.md)。

您可以從 PowerShell 提示字元執行 [Test-NetConnection](https://technet.microsoft.com/library/dn372891.aspx) 進行測試，以了解您的防火牆 (或 Proxy) 是否封鎖連線。 這將會測試 Azure 服務匯流排連線。 這只會測試網路連線，不會動用雲端伺服器服務或閘道。 其可協助判斷您的電腦是否可以連出網際網路。

    Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350

> [!NOTE]
> Test-NetConnection 僅可在 Windows Server 2012 R2 及更新版本使用。 也適用於 Windows 8.1 和更新版本。 在較舊的 OS 版本上，您可以使用 Telnet 來測試連接埠連線能力。
> 
> 

結果應該類似以下所示。 差異將會是 TcpTestSucceeded。 若 **TcpTestSucceeded** 不是 *True*，則您可能遭到防火牆封鎖。

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

若您想獲得完全相同的結果，請以[連接埠](../service-gateway-onprem.md#ports)列出的內容替代 **ComputerName** 和**Port** 的值。

防火牆也可能會封鎖 Azure 服務匯流排對 Azure 資料中心的連線。 若是這類情況下，您可以將這些資料中心區域的 IP 位址加入允許名單 (解除封鎖) 中。 您可以在[這裡](https://www.microsoft.com/download/details.aspx?id=41653)取得一份 Azure IP 位址清單。

