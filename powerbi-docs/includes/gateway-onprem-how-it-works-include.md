## <a name="how-the-gateway-works"></a>閘道運作方式
![on-prem-data-gateway-how-it-works](./media/gateway-onprem-how-it-works-include/on-prem-data-gateway-how-it-works.png)

我們先來看看使用者與連接至內部部署資料來源的項目互動時的情形。 

> [!NOTE]
> Power BI 必須設定閘道的資料來源。
> 
> 

1. 雲端服務會建立查詢，和內部部署資料來源的加密認證一起傳送到佇列，以供閘道處理。
2. 閘道雲端服務會分析此查詢，並將要求推送到 [Azure 服務匯流排](https://azure.microsoft.com/documentation/services/service-bus/)。
3. 內部部署資料閘道會輪詢 [Azure 服務匯流排](https://azure.microsoft.com/documentation/services/service-bus/)，得知是否有擱置的要求。
4. 閘道收到查詢、將認證解密，然後使用該認證連接至資料來源。
5. 閘道將查詢傳送到資料來源以用於執行。
6. 結果會從資料來源傳回閘道，然後傳送到雲端服務。 服務接著使用該結果。

