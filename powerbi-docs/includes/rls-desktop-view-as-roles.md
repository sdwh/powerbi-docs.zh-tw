## <a name="validating-the-role-within-power-bi-desktop"></a>在 Power BI Desktop 中驗證角色
建立角色之後，您就可以在 Power BI Desktop 中測試角色的結果。 若要這樣做，請選取 [以角色身分檢視]。

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

[以角色身分檢視] 對話方塊可讓您變更正在查看的特定使用者或角色的檢視。 您會看到您所建立的角色。

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

選取已建立的角色，然後選取 [確定] 將該角色套用到您正在檢視的內容。 報表只會呈現與該角色相關的資料。

您也可以選取 [其他使用者] 並提供指定的使用者。 最好提供使用者主體名稱 (UPN)，因為這正是 Power BI 服務會使用的。 選取 [確定]，報表就會顯示該使用者可以看到的內容。 

![](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

> [!NOTE]
> 如果您使用的是以 DAX 運算式為基礎的動態安全性，在 Power BI Desktop 中，這只會顯示不同的結果。
> 
> 

