## <a name="using-the-username-or-userprincipalname-dax-function"></a>使用 username() 或 userprincipalname() DAX 函式
您可以在資料集內使用 DAX 函式 *username()* 或 *userprincipalname()*。 您可以在 Power BI Desktop 中將它們用在運算式內。 當您發行模型時，它會用在 Power BI 服務中。

在 Power BI Desktop 內，*username()* 會以「網域\使用者」格式傳回使用者，*userprincipalname()* 會以 *user@contoso.com* 格式傳回使用者。

在 Power BI 服務內，*username()* 和 *userprincipalname()* 都會傳回使用者的使用者主體名稱 (UPN)。 這看起來類似電子郵件地址。

