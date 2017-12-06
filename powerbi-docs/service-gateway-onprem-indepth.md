---
title: "深入了解內部部署資料閘道"
description: "本文探討內部部署閘道的深入資訊。 這會探討服務與 Azure Active Directory 之間的運作方式以及本機 Active Directory 使用 Analysis Services 時的運作方式"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: fbb1b22b930a00fa9e090b3ebc5ab9fd1ffc88c0
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="on-premises-data-gateway-in-depth"></a>深入了解內部部署資料閘道
您組織中的使用者可以看到您的內部部署資料 (他們已經具有存取授權)，但在那些使用者能夠連接至內部部署資料來源之前，內部部署資料閘道必須先行安裝和設定。 此閘道有助於讓雲端的使用者快速安全地以幕後通訊方式，在內部部署資料來源和雲端之間往返。

安裝和設定閘道器通常是由系統管理員完成。 此作業也許需要對內部部署伺服器的專業知識，而且在某些情況下可能需要伺服器管理員權限。

本文不會提供如何安裝和設定閘道器的逐步指引。 如需該資訊，請務必查看[內部部署資料閘道](service-gateway-onprem.md)。 本文旨在讓您深入了解閘道器的運作方式。 我們也將深入探討 Azure Active Directory 和 Analysis Services 中使用者名稱和安全性的相關詳細資料，以及雲端服務如何運用使用者用以登入的電子郵件地址、閘道和 Active Directory，進而安全地連接及查詢內部部署資料。

<!-- Shared Requirements Include -->
[!INCLUDE [gateway-onprem-requirements-include](./includes/gateway-onprem-how-it-works-include.md)]

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

## <a name="sign-in-account"></a>登入帳戶
使用者將會使用公司或學校帳戶登入。 這是您的組織帳戶。 如果您註冊 Office 365 供應項目，而且未提供實際的公司電子郵件，其看起來可能會類似 nancy@contoso.onmicrosoft.com。您在雲端服務中的帳戶會儲存在 Azure Active Directory (AAD) 租用戶中。 在大部分情況下，您的 AAD 帳戶 UPN 會比對電子郵件地址。

## <a name="authentication-to-on-premises-data-sources"></a>內部部署資料來源的驗證
預存的認證將用來從 Analysis Services 以外的閘道連接至內部部署資料來源。 不論是哪位個別使用者，閘道都會使用預存的認證進行連接。

## <a name="authentication-to-a-live-analysis-services-data-source"></a>即時 Analysis Services 資料來源的驗證
每次使用者和 Analysis Services 互動時，有效使用者名稱皆會傳遞至閘道，然後傳到內部部署 Analysis Services 伺服器。 使用者主體名稱 (UPN)，通常是您用以登入雲端的電子郵件地址，即為當作有效使用者傳遞給 Analysis Services 的內容。 傳遞此 UPN 時是使用連接屬性 EffectiveUserName。 此電子郵件地址應符合本機 Active Directory 網域內定義的 UPN。 UPN 是 Active Directory 帳戶的屬性。 接著，該 Windows 帳戶就必須出現於 Analysis Services 角色中，以取得伺服器的存取權。 如果沒有在 Active Directory 中找到符合的項目，登入不會成功。

Analysis Services 也可以提供根據此帳戶進行篩選。 可以根據角色型安全性或資料列層級安全性來篩選。

## <a name="role-based-security"></a>角色型安全性
模型會依據使用者角色來提供安全性。 針對特定模型專案來定義角色的方式為使用 SQL Server Management Studio (SSMS)，時間點可能在使用 SQL Server Data Tools – 商業智慧 (SSDT-BI) 撰寫期間，或者在部署模型之後。 角色所包含的成員依 Windows 使用者名稱或 Windows 群組而定。 角色定義了使用者在模型上查詢或執行動作的權限。 大部分的使用者將屬於擁有讀取權限的角色。 其他角色適用於具有處理項目、管理資料庫函數及管理其他角色等權限的系統管理員。

## <a name="row-level-security"></a>資料列層級安全性
資料列層級安全性為 Analysis Services 資料列層級安全性所特有。 模型會提供動態的資料列層級安全性。 不同於具有至少一個使用者隸屬的角色，動態安全性並非任何表格式模型所需。 在較高的層級，動態安全性定義使用者讀取資料的權限，用於讀取特定資料表中特定資料列的資料。 動態資料列層級安全性與角色類似，也仰賴使用者的 Windows 使用者名稱。

查詢和檢視模型資料的使用者功能，首先由 Windows 使用者帳戶所隸屬的角色而定，其次由動態資料列層級安全性而定 (如果已設定的話)。

在模型中實作角色和動態資料列層級安全性已超出本文的範圍。  若要深入了解，您可以前往 MSDN 上的[角色 (SSAS 表格式)](https://msdn.microsoft.com/library/hh213165.aspx) 和[安全性角色 (Analysis Services - 多維度資料)](https://msdn.microsoft.com/library/ms174840.aspx)。 此外，為了徹底了解表格式模型安全性，請下載並閱讀保護[表格式 BI 語意模型技術白皮書](https://msdn.microsoft.com/library/jj127437.aspx)。

## <a name="what-about-azure-active-directory"></a>Azure Active Directory 的情況為何？
Microsoft 雲端服務會使用 [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) 來負責驗證使用者。 Azure Active Directory 是包含使用者名稱和安全性群組的租用戶。 一般而言，使用者登入時使用的電子郵件地址與帳戶的 UPN 相同。

我的本機 Active Directory 角色是什麼？

為了讓 Analysis Services 可判斷予以連接的使用者所屬角色是否具有讀取資料的權限，該伺服器需要轉換從 AAD 傳遞到閘道再傳遞到 Analysis Services 伺服器的有效使用者名稱。 Analysis Services 伺服器會將有效使用者名稱傳遞至 Windows Active Directory 網域控制站 (DC)。 Active Directory DC 接著會驗證此有效使用者名稱是否為有效 UPN (於本機帳戶上)，然後將該使用者的 Windows 使用者名稱傳回給 Analysis Services 伺服器。

EffectiveUserName 不能用在未加入網域的 Analysis Services 伺服器上。 Analysis Services 伺服器必須已加入網域中，以避免任何登入錯誤。

## <a name="how-do-i-tell-what-my-upn-is"></a>如何判斷我的 UPN 為何？
您可能不知道您的 UPN 為何，且您可能不是網域系統管理員。 您可以從工作站使用下列命令來查明您帳戶的 UPN。

    whoami /upn

結果看起來類似電子郵件地址，但這是您本機網域帳戶上的 UPN。 如果您使用 Analysis Services 資料來源進行即時連線，則必須符合從閘道傳遞給 EffectiveUserName 的資料來源。

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>對應 Analysis Services 資料來源的使用者名稱
Power BI 可讓您對應 Analysis Services 資料來源的使用者名稱。 您可以設定規則，將登入 Power BI 的使用者名稱對應至 Analysis Services 連線上傳遞給 EffectiveUserName 的名稱。 當您在 AAD 中的使用者名稱不符合本機 Active Directory 中的 UPN 時，使用者名稱對應功能是解決問題的好方法。 比方說，如果您的電子郵件地址為 nancy@contoso.onmicrsoft.com，您可以將其對應至 nancy@contoso.com，然後該值就會傳遞至閘道。 您可以深入了解如何[對應使用者名稱](service-gateway-enterprise-manage-ssas.md#map-user-names)。

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>同步處理內部部署 Active Directory 和 Azure Active Directory 
如果您打算使用 Analysis Services 即時連線，建議您讓本機 Active Directory 帳戶符合 Azure Active Directory。 因為帳戶之間的 UPN 必須相符合。

雲端服務只了解 Azure Active Directory 內的帳戶。 是否將帳戶加入您的本機 Active Directory 並不重要，如果其在 AAD 中不存在，就無法使用。 有不同的方式可以將本機 Active Directory 帳戶和 Azure Active Directory 比對。

1. 您可以手動將帳戶加入 Azure Active Directory。
   
   您可以在 Azure 網站或 Office 365 管理入口網站上建立帳戶，帳戶名稱必須符合本機 Active Directory 帳戶的 UPN。
2. 您可以使用 [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) 工具，將本機帳戶同步處理至您的 Azure Active Directory 租用戶。
   
   Azure AD Connect 工具提供目錄和密碼同步處理使用的選項。 如果您不是租用戶管理員或本機網域系統管理員，您必須連絡您的 IT 管理員來進行這項設定。
3. 您可以設定 Active Directory 同盟服務 (ADFS)。
   
   您可以使用 [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) 工具將 ADFS 伺服器與 AAD 租用戶建立關聯。 ADFS 使用以上所討論的目錄同步作業，但允許單一登入 (SSO) 體驗。 例如，如果您位於您的公司網路中，當您前往雲端服務並移至登入後，系統可能不會提示您輸入使用者名稱或密碼。 您必須與您的 IT 管理員討論這是否可供您的組織使用。

使用 Azure AD Connect 可確保 UPN 會在 AAD 與本機 Active Directory 之間相符。

> [!NOTE]
> 使用 Azure AD Connect 工具同步處理帳戶會在 AAD 租用戶內建立新的帳戶。
> 
> 

## <a name="now-this-is-where-the-gateway-comes-in"></a>這就是閘道器現在的運作方式
閘道可作為雲端和內部部署伺服器之間的橋接器。 雲端和閘道之間的資料傳輸會透過 [Azure 服務匯流排](https://azure.microsoft.com/documentation/services/service-bus/)加以保護。 此服務匯流排會透過閘道上的輸出連線，建立雲端與內部部署伺服器之間的安全通道。  您不需要在內部部署防火牆上開啟任何輸入的連線。

如果您有 Analysis Services 資料來源，則需要在與 Analysis Services 伺服器加入同一個樹系/網域的電腦上安裝閘道器。

閘道器越接近伺服器，連接速度就越快。 如果您可以取得與資料來源位於相同伺服器上的閘道器，就最能夠避免閘道器和伺服器之間的網路延遲。

## <a name="what-to-do-next"></a>下一個步驟是什麼？
安裝閘道之後，您將需要建立該閘道的資料來源。 您可以在 [管理閘道] 畫面內加入資料來源。 如需詳細資訊，請參閱管理資料來源文章。

[管理您的資料來源─Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[管理您的資料來源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[管理您的資料來源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
[管理您的資料來源 - Oracle](service-gateway-onprem-manage-oracle.md)  
[管理您的資料來源 - 匯入/已排程的重新整理](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>可能發生錯誤之處
有時候，閘道器會安裝失敗； 或者閘道看似安裝成功，但服務仍然無法搭配運作。 在許多情況下，錯誤的起因很簡單，例如閘道器用以登入資料來源的認證密碼。

在其他情況下，問題則可能出在使用者登入的電子郵件地址類型，或 Analysis Services 無法解析有效使用者名稱。 如果您有多個互相信任的網域，且閘道位於其中一個，而 Analysis Services 位於另一個，則這種情況有時會造成一些問題。

我們不會在這裡進行閘道問題的疑難排解，而是在另一篇文章[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)中，提供一系列的疑難排解步驟。 希望您不會遇到任何問題。 但如果您遇到了問題，則了解這裡所有步驟和疑難排解文章將有所幫助。

<!-- Account and Port information -->
[!INCLUDE [gateway-onprem-accounts-ports-more](./includes/gateway-onprem-accounts-ports-more.md)]

## <a name="next-steps"></a>後續步驟
[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
[Azure 服務匯流排](https://azure.microsoft.com/documentation/services/service-bus/)  
[Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

