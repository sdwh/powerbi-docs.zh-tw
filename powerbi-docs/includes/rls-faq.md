---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: bbd9b38f30a4ca5cb8072496c9cacb635b03aa88
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71409351"
---
## <a name="faq"></a>常見問題集
**問：** 如果先前曾在 Power BI 服務中建立了資料集的角色與規則會如何？ 如果什麼都不做，它們還可以運作嗎？  
**答：** 視覺效果不會正確轉譯。 您必須在 Power BI Desktop 內重新建立角色與規則，然後將其發行至 Power BI 服務。

**問：** 我可以為 Analysis Services 資料來源建立這些角色嗎？  
**答：** 如果已將資料匯入 Power BI Desktop，就可建立。 如果您使用的是即時連線，就無法在 Power BI 服務中設定 RLS。 這定義在內部部署 Analysis Services 模型中。

**問：** 我可以使用 RLS 來限制使用者能夠存取的資料行或量值嗎？  
**答：** 否，如果使用者具有特定資料列的存取權，就可以查看該資料列的所有資料行。

**問：** RLS 是否可讓我隱藏詳細資料，但允許存取以視覺效果摘要的資料？  
**答：** 否，您可以保護個別資料列，但使用者一律可以查看詳細資料或摘要的資料。

**問：** 我的資料來源已定義了安全性角色 (例如 SQL Server 角色或 SAP BW 角色)。 這些與 RLS 之間有何關聯性？  
**答：** 答案取決於您是匯入資料，或是使用 DirectQuery。 若您是將資料匯入 Power BI 資料集，便不會使用資料來源中的安全性角色。 此時您應定義 RLS，對 Power BI 中的連線使用者施行安全性規則。 若您是使用 DirectQuery，將會使用資料來源中的安全性角色。 當使用者開啟報表時，Power BI 會傳送查詢給基礎資料來源，而基礎資料來源將會依據使用者的認證對資料套用安全性規則。
