---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464332"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>在 Power BI Desktop 中驗證角色
在建立角色之後，於 Power BI Desktop 中測試角色的結果。

1. 在 [模型]  索引標籤中選取 [以角色身分檢視]  。 

    ![選取 [以角色身分檢視]](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    隨即顯示 [以角色身分檢視]  視窗，您會在此看到您已建立的角色。

    ![[以角色身分檢視] 視窗](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. 選取您建立的角色，然後選取 [確定]  來套用該角色。 

   報表會呈現該角色的相關資料。

4. 您也可以選取 [其他使用者]  並提供指定的使用者。 

    ![選取 [其他使用者]](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   建議提供使用者主體名稱 (UPN)，原因是 Power BI 服務和 Power BI 報表伺服器都會用到。

   在 Power BI Desktop 中，只有當您使用以 DAX 運算式為基礎的動態安全性時，[其他使用者]  才會顯示不同的結果。 

5. 選取 [確定]  。 

   報表就會呈現該使用者可以看到的內容。



