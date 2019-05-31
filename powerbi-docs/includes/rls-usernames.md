---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193582"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>使用 username() 或 userprincipalname() DAX 函式
您可以在資料集內使用 DAX 函式 *username()* 或 *userprincipalname()* 。 您可以在 Power BI Desktop 中將它們用在運算式內。 當您發行模型時，它會用在 Power BI 服務中。

在 Power BI Desktop 內，*username()* 會以「網域\使用者」  格式傳回使用者，*userprincipalname()* 會以 <em>user@contoso.com</em> 格式傳回使用者。

在 Power BI 服務內，*username()* 和 *userprincipalname()* 都會傳回使用者的使用者主體名稱 (UPN)。 這看起來類似電子郵件地址。

