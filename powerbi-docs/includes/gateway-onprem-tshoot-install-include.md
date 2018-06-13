## <a name="update-to-the-latest-version"></a>更新為最新版本
當閘道器版本過期時就會出現很多問題。  這是確定維持最新版本的良好一般做法。  如果超過一個月或更久沒有更新閘道器，您可能要考慮安裝最新版的閘道器，然後查看可否重現這項問題。

## <a name="common-issues"></a>常見問題
以下是幾個常見問題，以及已協助許多網際網路存取受限環境中客戶的解決方案。

### <a name="authentication-to-proxy-server"></a>Proxy 伺服器的驗證
您的 Proxy 可能會要求驗證網域使用者帳戶。 根據預設，閘道會使用 Windows 服務登入使用者的服務 SID。 將登入使用者變更為網域使用者可以解決這個問題。 如需詳細資訊，請參閱[將閘道服務帳戶變更為網域使用者](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user)。

### <a name="your-proxy-only-allows-ports-80-and-443-traffic"></a>您的 Proxy 只允許連接埠 80 和 443 的流量
某些 Proxy 會將流量限制在連接埠 80 和 443。 根據預設，Azure 服務匯流排的通訊會發生在連接埠 443 以外。

您可以強制閘道使用 HTTPS 與 Azure 服務匯流排進行通訊，而不使用 TCP。 您會需要修改 *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* 檔案。 將值從 `AutoDetect` 變更為 `Https`。 根據預設，這個檔案位於 *C:\Program Files\On-premises data gateway* 。

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="installation"></a>安裝
### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>錯誤：無法將使用者加入群組。  (-2147463168   PBIEgwService   效能記錄使用者   )
如果您嘗試在網域控制站上安裝閘道，就有可能會收到這個錯誤。 不支援在網域控制站上部署。 您必須在非網域控制站的電腦上部署閘道。

### <a name="installation-fails"></a>安裝失敗
若安裝電腦上的防毒軟體過期，您可能會遇到安裝失敗。 您可以更新防毒安裝，也可以只在閘道安裝期間停用防毒以待完成，然後重新啟用防毒。

