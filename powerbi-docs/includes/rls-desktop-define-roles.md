---
ms.openlocfilehash: 27d6db6cf8ad8ebd7b2c957954ceec34b83681d0
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464335"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>在 Power BI Desktop 中定義角色和規則
您可以在 Power BI Desktop 中定義角色和規則。 當發佈到 Power BI 時，也會發佈角色定義。

若要定義安全性角色，請遵循這些步驟。

1. 將資料匯入 Power BI Desktop 報表，或設定 DirectQuery 連線。
   
   > [!NOTE]
   > 您不能在 Power BI Desktop 中定義 Analysis Services 即時連線的角色。 您必須在 Analysis Services 模型中進行此動作。
   > 
   > 
2. 在 [模型]  索引標籤中，選取 [管理角色]  。
   
   ![選取 [管理角色]](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
3. 從 [管理角色]  視窗中，選取 [建立]  。
   
   ![選取 [建立]](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
4. 在 [角色]  下提供角色名稱。 
5. 在 [資料表]  下選取要套用 DAX 規則的資料表。
6. 在 [資料表篩選 DAX 運算式]  方塊中，輸入 DAX 運算式。 這個運算式會傳回 true 或 false 的值。 例如：```[Entity ID] = “Value”```。
      
   ![[管理角色] 視窗](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)

   > [!NOTE]
   > 這個運算式中可以使用 *username()* 。 請注意，*username()* 在 Power BI Desktop 中的格式為「網域\使用者名稱」  。 在 Power BI 服務和 Power BI 報表伺服器中，格式則為使用者的使用者主體名稱 (UPN)。 或者，您可以使用 *userprincipalname()* ，這一律會以使用者主體名稱的格式 (*username\@contoso.com*) 傳回使用者。
   > 
   > 

7. 建立 DAX 運算式之後，請選取運算式方塊上方的核取記號，以驗證運算式。
      
   ![有效的 DAX 運算式](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > 在此運算式方塊中，即使您使用的地區設定慣用分號分隔字元 (例如法文或德文)，您仍須使用逗號分隔 DAX 函式的引數。 
   >
   >
   
8. 選取 [儲存]  。

您無法在 Power BI Desktop 中指派使用者給角色。 請在 Power BI 服務中指派他們。 在 Power BI Desktop 內，您可以使用 *username()* 或 *userprincipalname()* DAX 函式，並設定合適的關聯性，以啟用動態安全性。 

