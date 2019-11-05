---
title: 使用 Azure Active Directory B2B 將 Power BI 內容散發給外部來賓使用者
description: 此白皮書說明如何使用 Azure Active Directory B2B 將 Power BI 散發給外部來賓使用者
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 0227072818b7c09463b47ba896c782ded1e7f248
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432412"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>使用 Azure Active Directory B2B 將 Power BI 內容散發給外部來賓使用者

**摘要：** 這是一份技術白皮書，概述如何使用 Azure Active Directory 企業對企業（Azure AD B2B）的整合，將內容散發給組織外部的使用者。

**寫入器：** Lukasz Pawlowski，Kasper de Jonge

**技術審核者：** Adam Wilson、Sheng Liu、Qian Liang、Sergei Gundorov、Jacob Grimm、Adam Saxton、Maya Shenhav、Nimrod Shalit、Elisabeth Olson

> [!NOTE]
> 您可選取瀏覽器的 [列印]，然後選取 [儲存為 PDF] 來儲存或列印本白皮書。

## <a name="introduction"></a>簡介

Power BI 為組織提供360角度的業務觀點，並讓這些組織中的每個人都能使用資料做出明智的決策。 其中許多組織都具有與外部合作夥伴、用戶端和承包商的強式和信任關係。 這些組織需要為這些外部合作夥伴的使用者提供 Power BI 儀表板和報表的安全存取。

Power BI 與[Azure Active Directory 的企業對企業（AZURE AD B2B）](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)整合，以安全地將 Power BI 內容散發給組織外部的來賓使用者，同時仍保有控制和管理內部資料的存取權。

本白皮書涵蓋瞭解 Power BI 與 Azure Active Directory B2B 整合所需的所有詳細資料。 我們會討論其最常見的使用案例、設定、授權和資料列層級安全性。

> [!NOTE]
> 在此白皮書中，我們將 Azure Active Directory 稱為 Azure AD，並 Azure Active Directory 企業對企業 Azure AD B2B。

## <a name="scenarios"></a>場景

Contoso 是一家汽車製造商，可與許多不同的供應商合作，以提供執行其製造作業所需的所有元件、材質和服務。 Contoso 想要簡化其供應鏈物流，並計畫使用 Power BI 來監視其供應鏈的關鍵效能計量。 Contoso 想要以安全且可管理的方式與外部供應鏈合作夥伴分析分享。

Contoso 可以使用 Power BI 和 Azure AD B2B，為外部使用者啟用下列體驗。

### <a name="ad-hoc-per-item-sharing"></a>特定的每個專案共用

Contoso 與建立 Contoso 車輛 radiators 的供應商合作。 他們通常需要使用 Contoso 所有車輛的資料來優化 radiators 的可靠性。 Contoso 的分析師會使用 Power BI，與供應商的工程師分享 radiator 的可靠性報告。 工程師會收到一封電子郵件，其中包含可供您查看報表的連結。

如上所述，此臨機操作共用是由商務使用者視需要執行。 Power BI 傳送給外部使用者的連結是 Azure AD B2B 邀請 連結。 當外部使用者開啟連結時，系統會要求他們將 Contoso 的 Azure AD 組織加入為來賓使用者。 接受邀請之後，此連結會開啟特定的報表或儀表板。 Azure Active Directory 管理員會將邀請外部使用者的許可權委派給組織，並選擇當使用者接受此邀請之後可執行檔動作，如本檔的治理一節中所述。 Contoso 分析師只能邀請來賓使用者，因為 Azure AD 系統管理員允許該動作，而 Power BI 系統管理員允許使用者邀請來賓在 Power BI 的租使用者設定中查看內容。

![邀請來賓使用 AAD Power BI](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. 此程式會從 Contoso 內部使用者開始，並與外部使用者共用儀表板或報表。 如果外部使用者還不是 Contoso Azure AD 中的來賓，則會受到邀請。 電子郵件會傳送到其電子郵件地址，其中包含 Contoso 的邀請 Azure AD
2. 收件者會接受 Contoso 的 Azure AD 邀請，並在 Contoso 的 Azure AD 中新增為來賓使用者。
3. 然後，系統會將收件者重新導向至使用者的唯讀 Power BI 儀表板、報表或應用程式。

此程式會被視為臨機操作，因為 Contoso 中的商務使用者會視需要執行邀請動作以因應其商務用途。 共用的每個專案都是外部使用者可以存取以查看內容的單一連結。

一旦外部使用者受邀存取 Contoso 資源，就可以在 Contoso Azure AD 中建立陰影帳戶，而且不需要再次邀請他們。  第一次嘗試存取 Contoso 資源（例如 Power BI 儀表板）時，他們會通過同意程式，贖回邀請。  如果他們未完成同意，他們就無法存取 Contoso 的任何內容。  如果他們無法透過提供的原始連結兌換其邀請，則 Azure AD 系統管理員可以重新傳送特定的邀請連結供他們兌換。

### <a name="planned-per-item-sharing"></a>已規劃每個專案共用

Contoso 會與轉包商合作，以執行 radiators 的可靠性分析。 轉包商有10個人的小組，需要在 Contoso 的 Power BI 環境中存取資料。 Contoso Azure AD 系統管理員會參與邀請所有使用者，並在轉包商變更時處理任何新增/變更。 Azure AD 系統管理員會為轉包商的所有員工建立一個安全性群組。 Contoso 的員工可以使用安全性群組，輕鬆地管理報表的存取權，並確保所有必要的轉包人員都能夠存取所有必要的報表、儀表板和 Power BI 應用程式。 Azure AD 系統管理員也可以藉由選擇將邀請權利委派給 Contoso 或轉包商的受信任員工，以避免與邀請程式完全相關，以確保及時的人員管理。

有些組織需要更充分掌控外部使用者的新增時間、邀請外部組織中的多個使用者，或許多外部組織。 在這些情況下，規劃的共用可以用來管理共用規模、強制執行組織原則，甚至將許可權委派給受信任的人員來邀請和管理外部使用者。 Azure AD B2B 支援[由 IT 系統管理員直接從 Azure 入口網站](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)傳送已規劃的邀請，或透過[PowerShell 使用邀請管理員 API](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) ，其中一組使用者可以在一個動作中受到邀請。 組織可以使用計畫的邀請方法，控制誰可以邀請使用者及實施核准程式。 Advanced Azure AD 功能（例如動態群組）可讓您輕鬆地自動維護安全性群組成員資格。


![控制哪些來賓可以查看內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. IT 系統管理員以手動方式或透過提供的 API 來邀請來賓使用者的程式星星 Azure Active Directory
2. 使用者接受組織的邀請。
3. 使用者接受邀請之後，Power BI 中的使用者就可以與外部使用者或他們所在的安全性群組共用報表或儀表板。 就像在中 Power BI 一般共用一樣，外部使用者會收到包含專案連結的電子郵件。
4. 當外部使用者存取連結時，其目錄中的驗證會傳遞至 Contoso 的 Azure AD，並用來取得 Power BI 內容的存取權。

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Power BI 應用程式的特定或規劃共用

Contoso 有一組需要與一或多個供應商共用的報表和儀表板。 為確保所有必要的外部使用者都能夠存取此內容，請將其封裝為 Power BI 應用程式。 外部使用者可以直接新增至應用程式存取清單，或透過安全性群組加入。 Contoso 的某人接著會將應用程式 URL 傳送給所有外部使用者，例如在電子郵件中。 當外部使用者開啟連結時，他們會在單一輕鬆流覽體驗中看到所有內容。

使用 Power BI 應用程式可讓 Contoso 輕鬆地為其供應商建立 BI 入口網站。 單一存取清單可控制對所有必要內容的存取，減少浪費時間檢查和設定專案層級許可權。 Azure AD B2B 會使用供應商的原生身分識別維護安全性存取權，因此使用者不需要額外的登入認證。 如果將計畫的邀請與安全性群組搭配使用，則會簡化應用程式的存取權管理。 手動或使用[動態群組](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups)的安全性群組成員資格，讓來自供應商的所有外部使用者自動新增至適當的安全性群組。


![使用 AAD 控制內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. 此程式會由使用者透過 Azure 入口網站或 PowerShell 邀請到 Contoso 的 Azure AD 組織開始
2. 使用者可以新增至 Azure AD 中的使用者群組。 您可以使用靜態或動態使用者群組，但動態群組可協助減少手動工作。
3. 外部使用者可以透過使用者群組取得 Power BI 應用程式的存取權。 應用程式 URL 應直接傳送給外部使用者，或放在他們可以存取的網站上。 Power BI 會盡力將含有應用程式連結的電子郵件傳送給外部使用者，但使用成員資格可能變更的使用者群組時，Power BI 無法傳送給透過使用者群組管理的所有外部使用者。
4. 當外部使用者存取 Power BI 應用程式 URL 時，會由 Contoso 的 Azure AD 進行驗證、為使用者安裝應用程式，而且使用者可以在應用程式內看到所有包含的報表和儀表板。

應用程式也具有獨特的功能，可讓應用程式作者自動為使用者安裝應用程式，以便在使用者登入時使用。 這項功能只會針對在應用程式發佈或更新時已屬於 Contoso 組織的外部使用者自動安裝。 因此，最適合用於已規劃的邀請方法，並取決於將使用者新增至 Contoso 的 Azure AD 之後，要發佈或更新的應用程式。 外部使用者一律可以使用應用程式連結來安裝應用程式。

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>為組織中的內容加上批註並訂閱

當 Contoso 繼續與轉包商或供應商合作時，外部工程師必須與 Contoso 的分析師密切合作。 Power BI 提供數個共同作業功能，可協助使用者溝通他們所能使用的內容。 儀表板批註（和報告批註很快）可讓使用者討論他們看到的資料點，並與報表作者溝通以詢問問題。

目前，外部來賓使用者可以離開留言並閱讀回復，以參與留言。 不過，不同于內部使用者，來賓使用者無法 @mentioned，也不會收到他們收到留言的通知。 在撰寫本文時，來賓使用者無法使用 Power BI 內的訂閱功能。 在即將發行的版本中，這些限制將會提升，而來賓使用者會在留言 @mentions 或將訂用帳戶傳遞至包含 Power BI 內容連結的電子郵件時，收到電子郵件。

### <a name="access-content-in-the-power-bi-mobile-apps"></a>存取 Power BI mobile apps 中的內容

在即將推出的版本中，當 Contoso 的使用者與其外部來賓對應專案共用報表或儀表板時，Power BI 會傳送一封電子郵件來通知來賓。 當來賓使用者在行動裝置上開啟報表或儀表板的連結時，內容將會在其裝置上的原生 Power BI 行動應用程式中開啟（如果已安裝）。 然後，來賓使用者將能夠在外部租使用者中與他們共用的內容之間流覽，並從他們的主要租使用者回到自己的內容。

> [!NOTE]
> 來賓使用者無法開啟 Power BI 行動應用程式，並立即流覽至外部租使用者，他們必須以外部租使用者中專案的連結開始。 一般因應措施會在本檔稍後的將[連結發佈到父組織的 Power BI](#distributing-links-to-content-in-the-parent-organizations-power-bi)一節中說明。

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Power BI 內容的跨組織編輯和管理

Contoso 及其供應商和轉包商的合作程度日益緊密。 在轉包商的分析師，通常需要將額外的計量或資料視覺效果加入至 Contoso 已與他們共用的報表。 資料應位於 Contoso 的 Power BI 租使用者中，但外部使用者應能夠編輯、建立新內容，甚至將其散發給適當的個人。

Power BI 提供一個選項，可讓**外部來賓使用者編輯和管理**組織中的內容。 根據預設，外部使用者具有唯讀的耗用量導向體驗。 不過，這種新的設定可讓 Power BI 系統管理員選擇哪些外部使用者可以在自己的組織內編輯和管理內容。 允許之後，外部使用者可以編輯報表、儀表板、發行或更新應用程式、在工作區中工作，以及連接到他們有權使用的資料。

此案例將在本檔稍後的讓外部使用者編輯和管理內容 Power BI 一節中詳細說明。

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>使用 Power BI 和 Azure AD B2B 的組織關聯性

當 Power BI 的所有使用者都在組織內部時，就不需要使用 Azure AD B2B。 不過，一旦兩個或多個組織想要共同處理資料和見解，Power BI 對 Azure AD B2B 的支援可讓您輕鬆且符合成本效益。

以下通常會遇到組織結構，其適用于 Power BI 中的 Azure AD B2B 樣式跨組織共同作業。 Azure AD B2B 在大多數情況下都很有用，但在某些情況下，這份檔結尾所涵蓋的常見替代方法是值得考慮的。

### <a name="case-1-direct-collaboration-between-organizations"></a>案例1：組織間的直接共同作業

Contoso 與 radiator 供應商的關係是組織之間直接共同作業的範例。 因為 Contoso 和其供應商的使用者數目相對較少，而需要存取 radiator 可靠性資訊，所以使用 Azure AD B2B 型外部共用是理想的選擇。 它很容易使用且易於管理。 這也是諮詢服務中的常見模式，顧問可能需要為組織建立內容。

![在組織之間共用](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


一般來說，這項共用會在一開始使用特定的每個專案共用時發生。 不過，當小組成長或關聯性加深時，規劃的每個專案共用方法會成為降低管理額外負荷的慣用方法。 此外，Power BI 應用程式的臨機操作或規劃分享、對組織中的內容加上評論和訂閱、對行動應用程式中內容的存取也可能也會播放，以及跨組織編輯和管理 Power BI 內容。 重要的是，如果這兩個組織的使用者在其各自的組織中都有 Power BI Pro 授權，他們就可以在彼此的 Power BI 環境中使用這些 Pro 授權。 這會提供有利的授權，因為邀請的組織可能不需要支付外部使用者的 Power BI Pro 授權。 本檔稍後的授權一節會詳細討論這一點。

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>案例2：父系及其分支機搆或關係企業

有些組織結構比較複雜，包括部分或全部擁有的分公司、附屬公司，或受控服務提供者關聯性。 這些組織都有一個父組織，例如保存的公司，但基礎組織會以半自主的方式運作，有時是在不同的地區需求之下。 這會導致每個組織都有自己的 Azure AD 環境，以及個別 Power BI 的租使用者。

![使用子公司](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


在此結構中，父組織通常需要將標準化的深入解析散發到其子公司。 一般而言，此共用會使用 Power BI Apps 的臨機操作或規劃共用進行，如下圖所示，因為它允許將標準化的授權內容散發給廣大的觀眾。 實際上，我們會使用本檔稍早提到的所有案例組合。

![結合情節](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


這會遵循下列程式：

1. 來自每個分公司的使用者會被邀請到 Contoso 的 Azure AD
2. 然後會發佈 Power BI 應用程式，讓這些使用者存取所需的資料
3. 最後，使用者會透過所提供的連結來開啟應用程式，以查看報告

此結構中的組織會面臨幾個重要的挑戰：

- 如何將連結發佈到父組織 Power BI 中的內容
- 如何允許子公司使用者存取父組織所主控的資料來源

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>將連結發佈到父組織 Power BI 中的內容

通常會使用三種方法來散發內容的連結。 第一個和最基本的是將應用程式的連結傳送給所需的使用者，或將它放在可以開啟它的 SharePoint Online 網站中。 使用者可以將瀏覽器中的連結加入書簽，以便更快速地存取所需的資料。

第二種方法依賴跨組織的 Power BI 內容功能的編輯和管理。 父組織可讓分公司的使用者存取其 Power BI，並透過許可權控制他們可以存取的內容。 這會提供 Power BI 首頁的存取權，讓子公司的使用者看到在父組織的租使用者中共用的完整內容清單。 然後，會將父組織 Power BI 環境的 URL 提供給子公司的使用者。

最後一種方法會使用在每個子公司的 Power BI 租使用者內建立的 Power BI 應用程式。 Power BI 應用程式包含具有以[[外部連結] 選項設定之磚](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink)的儀表板。 當使用者按下磚時，系統會將他們帶到父組織 Power BI 中適當的報表、儀表板或應用程式。 這種方法的優點是，應用程式可以針對子公司中的所有使用者自動安裝，而且只要登入自己的 Power BI 環境，就能使用。 這種方法的優點是，它可以與可原生開啟連結的 Power BI 行動應用程式搭配運作。 您也可以將此結合成第二種方法，讓您更輕鬆地在 Power BI 環境之間切換。

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>允許子公司使用者存取父組織所主控的資料來源

分公司的分析師通常需要使用父組織所提供的資料來建立自己的分析。 在此情況下，通常會使用雲端資料來源來解決挑戰。

第一種方法會利用[Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview)來建立企業級資料倉儲，以滿足整個父系及其子公司的分析師需求，如下圖所示。 Contoso 可以裝載資料並使用資料列層級安全性之類的功能，以確保每個分公司的使用者只能存取他們的資料。 每個組織的分析師可以透過 Power BI Desktop 來存取資料倉儲，並將產生的分析發佈到其各自的 Power BI 租使用者。

![如何使用 Power BI 租使用者進行共用](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


第二種方法會利用[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)來建立關聯式資料倉儲，以提供資料的存取權。 其運作方式類似于 Azure Analysis Services 的方法，不過某些功能（例如資料列層級安全性）可能會難以跨分公司部署和維護。

此外，也可以使用更複雜的方法，但上述的最常見。

### <a name="case-3-shared-environment-across-partners"></a>案例3：跨合作夥伴的共用環境

Contoso 可能會進入與競爭對手的合作關係，以在共用的組裝線上共同建立車輛，但在不同品牌或不同地區散佈車輛。 這需要廣泛的共同作業，以及跨組織的資料、智慧和分析的共同擁有權。 此結構在諮詢服務產業中也很常見，其中的顧問團隊可能會對用戶端進行以專案為基礎的分析。

![跨合作夥伴的共用環境](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



實際上，這些結構是複雜的，如下圖所示，而且需要人員進行維護。 為有效，此結構會依賴跨組織的 Power BI 內容功能的編輯和管理，因為它可讓組織重複使用針對其各自 Power BI 租使用者購買的 Power BI Pro 授權。

![授權和共用的組織內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



若要建立共用 Power BI 租使用者，您必須建立 Azure Active Directory，而且必須為該 Active Directory 中的使用者購買至少一個 Power BI Pro 的使用者帳戶。 此使用者邀請所需的使用者加入共用組織。 重要的是，在此案例中，Contoso 的使用者在共用組織的 Power BI 內運作時，會被視為外部使用者。

此程式如下所示：

1. 共用組織會建立為新的 Azure Active Directory，而且在新組織中至少會建立一個使用者帳戶。 該使用者應指派 Power BI Pro 授權。
2. 然後，此使用者會建立 Power BI 租使用者，並邀請 Contoso 和合作夥伴組織所需的使用者。 使用者也會建立任何共用資料資產，例如 Azure Analysis Services。 Contoso 和合作夥伴的使用者可以存取共用組織的 Power BI 做為來賓使用者。 如果允許編輯和管理中的內容 Power BI 外部使用者可以使用 Power BI 首頁，請使用工作區、上傳或編輯內容和共用報表。 一般而言，所有共用的資產都會儲存並從共用組織存取。
3. 根據合作物件如何同意共同作業，每個組織都可以使用共用資料倉儲資產來開發自己專屬的資料和分析。 他們可以使用其內部 Power BI 租使用者，將它們散發給其各自的內部使用者。

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>案例4：散發給數百或數千個外部夥伴

Contoso 在建立一個供應商的 radiator 可靠性報告時，現在 Contoso 想要為數百位供應商建立一組標準化的報告。 這可讓 Contoso 確保所有供應商都擁有所需的分析，以進行改進或修正製造瑕疵。

![散發給許多合作夥伴](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


當組織需要將標準化資料和深入解析散發給許多外部使用者/組織時，他們可以使用 Power BI Apps 案例的臨機操作或規劃共用，快速建立 BI 入口網站，而不需要大量的開發成本。 案例研究：使用本檔稍後的 Power BI + Azure AD B2B –逐步指示建立 BI 入口網站中，涵蓋使用 Power BI 應用程式建立這類入口網站的流程。

此案例的常見變化是當組織嘗試與取用者共用見解時，特別是在想要搭配 Power BI 使用 Azure B2C 時。 Power BI 原本就不支援 Azure B2C。 如果您要評估此案例的選項，請考慮在一般替代方法中使用替代選項2，本檔稍後的一節。

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>案例研究：使用 Power BI + Azure AD B2B-逐步指示建立 BI 入口網站

Power BI 與 Azure AD B2B 的整合提供了一種順暢且輕鬆的方式，讓來賓使用者能夠安全地存取其 BI 入口網站。 Contoso 可以透過三個步驟來設定此項：

![建立入口網站](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. 在 Power BI 中建立 BI 入口網站

    Contoso 的第一項工作是在 Power BI 中建立其 BI 入口網站。 Contoso 的 BI 入口網站會包含一個專門建立的儀表板和報表集合，可供許多內部和來賓使用者使用。 在 Power BI 中執行此作業的建議方式是建立 Power BI 應用程式。 深入瞭解[Power BI 中的應用程式](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/)。

- Contoso 的 BI 小組會在 Power BI 中建立工作區

    ![區域](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- 其他作者會新增至工作區

    ![新增作者](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- 內容是在工作區內建立

    ![在工作區中建立內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    現在已在工作區中建立內容，Contoso 已準備好邀請夥伴組織中的來賓使用者取用此內容。

2. 邀請來賓使用者

    Contoso 有兩種方式可以在 Power BI 中邀請來賓使用者到其 BI 入口網站：

    * 規劃的邀請
    * 特定邀請

    **規劃的邀請**

    在這種方法中，Contoso 會先邀請來賓使用者進行 Azure AD，然後將 Power BI 內容散發給他們。 Contoso 可以邀請來自 Azure 入口網站的來賓使用者，或使用 PowerShell。 以下是從 Azure 入口網站邀請來賓使用者的步驟：

    - Contoso 的 Azure AD 系統管理員流覽至**Azure 入口網站 > Azure Active Directory > 使用者和群組 > 新的來賓使用者 > 所有使用者**

    ![來賓使用者](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - 新增來賓使用者的邀請訊息，然後按一下 [邀請]

    ![新增邀請](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > 若要邀請 Azure 入口網站中的來賓使用者，您必須是租使用者 Azure Active Directory 的系統管理員。

    如果 Contoso 想要邀請許多來賓使用者，他們可以使用 PowerShell 來執行此動作。 Contoso 的 Azure AD 系統管理員會將所有來賓使用者的電子郵件地址儲存在 CSV 檔案中。 以下是 Azure Active Directory 的 B2B 共同作業程式[代碼和 PowerShell 範例](https://docs.microsoft.com/azure/active-directory/b2b/code-samples)和指示。

    邀請之後，來賓使用者會收到含有邀請連結的電子郵件。

    ![邀請連結](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    一旦來賓使用者按一下連結，他們就可以存取 Contoso Azure AD 租使用者中的內容。

    > [!NOTE]
    > 如[這裡](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email)所述，您可以使用 Azure AD 商標功能來變更邀請電子郵件的配置。


    **特定邀請**

    如果 Contoso 不知道想要事先邀請的所有來賓使用者，該怎麼辦？ 或者，如果 Contoso 中建立 BI 入口網站的分析師想要自行發佈內容給來賓使用者，該怎麼辦？ 我們也會在 Power BI 中使用臨機操作邀請來支援此案例。

    分析師可以直接將外部使用者新增至應用程式的存取清單（當他們發佈時）。 來賓使用者會取得邀請，一旦接受，系統會自動將他們重新導向至 Power BI 內容。

    ![新增外部使用者](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > 只有第一次邀請外部使用者加入您的組織時，才需要邀請。


3. 散發內容

    既然 Contoso 的 BI 小組已建立 BI 入口網站和受邀的來賓使用者，他們就可以提供來賓使用者對應用程式的存取權並加以發佈，將其入口網站散發給他們的使用者。 Power BI 自動完成先前已新增至 Contoso 租使用者之來賓使用者的名稱。 您也可以在此時新增其他來賓使用者的臨機操作邀請。

    > [!NOTE]
    > 如果使用安全性群組來管理外部使用者對應用程式的存取，請使用計畫的邀請方法，並與每個必須存取它的外部使用者直接共用應用程式連結。 否則，外部使用者可能無法從應用程式內安裝或查看內容。 _

    來賓使用者會收到附有應用程式連結的電子郵件。

    ![電子郵件邀請連結](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    當您按一下此連結時，系統會要求來賓使用者以自己的組織身分識別進行驗證。

    ![登入頁面](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    成功驗證之後，系統會將他們重新導向至 Contoso 的 BI 應用程式。

    ![請參閱共用內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    來賓使用者接著可以按一下電子郵件中的連結或將連結加入書簽，以取得 Contoso 的應用程式。 Contoso 也可以藉由將這個連結新增至來賓使用者已使用的任何現有外部網路入口網站，讓來賓使用者更輕鬆。

4. 後續步驟

    使用 Power BI 應用程式和 Azure AD B2B，Contoso 能夠以無程式碼的方式，為其供應商快速建立 BI 入口網站。 這麼做可大幅簡化將標準化分析散發給所有需要它的供應商。

    雖然此範例示範如何在供應商之間散發單一通用報表，Power BI 可以更進一步。 為了確保每個夥伴只會看到與本身相關的資料，資料列層級安全性可以輕鬆地加入至報表和資料模型。 本檔稍後的「外部合作夥伴的資料安全性」一節將詳細說明此程式。

    通常，個別的報表和儀表板必須內嵌到現有的入口網站中。 這也可以用來重複使用範例中所示的許多技巧。 不過，在這些情況下，直接從工作區內嵌報表或儀表板可能會比較容易。 邀請和指派安全性許可權給要求使用者的程式會維持不變。

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>在幕後：如何從 Supplier1 Lucy，才能從 Contoso 的租使用者存取 Power BI 內容？

既然我們已瞭解 Contoso 如何能夠順暢地將 Power BI 內容散發給夥伴組織中的來賓使用者，讓我們來看看這在幕後的運作方式。

當 Contoso 受邀[lucy@supplier1.com](mailto:lucy@supplier1.com)到其目錄時，Azure AD 會在[Lucy@supplier1.com](mailto:Lucy@supplier1.com)與 Contoso Azure AD 租使用者之間建立連結。 此連結可讓 Azure AD 知道 Lucy@supplier1.com 可以存取 Contoso 租使用者中的內容。

當 Lucy 嘗試存取 Contoso 的 Power BI 應用程式時，Azure AD 會驗證 Lucy 是否可以存取 Contoso 租使用者，然後提供 Power BI 權杖，指出 Lucy 已通過驗證，可存取 Contoso 租使用者中的內容。 Power BI 使用此權杖來授權並確保 Lucy 可存取 Contoso 的 Power BI 應用程式。

![驗證與授權](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Power BI 與 Azure AD B2B 的整合會與所有公司電子郵件地址搭配運作。 如果使用者沒有 Azure AD 身分識別，系統可能會提示他們建立一個。 下圖顯示詳細的流程：

![整合流程圖表](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


請務必瞭解，將會在外部合作物件的 Azure AD 中使用或建立 Azure AD 帳戶，這可讓 Lucy 使用自己的使用者名稱和密碼，而且其認證會在每次執行時自動停止于其他租使用者中工作。Lucy 會在其組織也使用 Azure AD 時離開公司。

## <a name="licensing"></a>授權

Contoso 可以選擇三種方法的其中一種，將來賓使用者從其供應商和合作夥伴組織授權，以取得 Power BI 內容的存取權。

> [!NOTE]
> _Azure AD B2B's 免費層就足以配合 AZURE AD B2B 使用 Power BI。某些先進的 Azure AD B2B 功能（例如動態群組）需要額外的授權。如需其他資訊，請參閱 Azure AD B2B 檔：_ [ _https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_ ](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>方法1： Contoso 使用 Power BI Premium

透過這種方法，Contoso 會購買 Power BI Premium 的容量，並將其 BI 入口網站內容指派給此容量。 這可讓合作夥伴組織的來賓使用者存取 Contoso 的 Power BI 應用程式，而不需要任何 Power BI 授權。

外部使用者也受限於在 Power BI Premium 中取用內容時，Power BI 提供給「免費」使用者的使用體驗。

Contoso 也可以利用其他 Power BI premium 功能來執行其應用程式，例如增加的重新整理頻率、專用容量和大型模型大小。

![其他功能](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>方法2： Contoso 會將 Power BI Pro 授權指派給來賓使用者

透過這種方法，Contoso 會將 pro 授權指派給合作夥伴組織的來賓使用者，這可以從 Contoso 的 Microsoft 365 系統管理中心完成。 這可讓合作夥伴組織的來賓使用者存取 Contoso 的 Power BI 應用程式，而不需要自行購買授權。 這可能適用于與組織尚未採用 Power BI 的外部使用者共用。

> [!NOTE]
> Contoso 的 pro 授權僅適用于當來賓使用者存取 Contoso 租使用者中的內容時。 Pro 授權可讓您存取不在 Power BI Premium 容量中的內容。 不過，具有 Pro 授權的外部使用者預設會受到僅限耗用量體驗的限制。 您可以使用在本檔稍後的在 Power BI 一節中_啟用外部使用者來編輯和管理內容_中所述的方法來變更此項。

![授權資訊](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>方法3：來賓使用者攜帶自己的 Power BI Pro 授權

使用此方法時，供應商1會將 Power BI Pro 授權指派給 Lucy。 然後，他們就可以使用此授權來存取 Contoso 的 Power BI 應用程式。 因為 Lucy 可以在存取外部 Power BI 環境時，從自己的組織使用其 Pro 授權，所以這種方法有時稱為「自備_授權_」（BYOL）。 如果這兩個組織都使用 Power BI，這會為整體分析解決方案提供有利的授權，並將指派授權給外部使用者的額外負荷降到最低。

> [!NOTE]
> 供應商1提供給 Lucy 的 pro 授權適用于 Lucy 為來賓使用者的任何 Power BI 租使用者。 Pro 授權可讓您存取不在 Power BI Premium 容量中的內容。 不過，具有 Pro 授權的外部使用者預設會受到僅限耗用量體驗的限制。 您可以使用在本檔稍後的 Power BI 一節中_啟用外部使用者來編輯和管理內容_中所述的方法來變更。

![Pro 授權需求](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>外部合作夥伴的資料安全性

通常在使用多個外部供應商時，Contoso 必須確保每個供應商只會看到其本身產品的資料。 以使用者為基礎的安全性和動態資料列層級安全性可讓您輕鬆完成 Power BI。

### <a name="user-based-security"></a>以使用者為基礎的安全性

資料列層級安全性 Power BI 最強大的功能之一。 這項功能可讓 Contoso 建立單一報表和資料集，但仍會針對每個使用者套用不同的安全性規則。 如需深入說明，請參閱資料[列層級安全性（RLS）](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/)。

Power BI 與 Azure AD B2B 的整合，可讓 Contoso 在來賓使用者受邀至 Contoso 租使用者時，將資料列層級安全性規則指派給他們。 如先前所見，Contoso 可以透過計畫或臨機操作邀請來新增來賓使用者。 如果 Contoso 想要強制執行資料列層級安全性，強烈建議您事先使用計畫的邀請來新增來賓使用者，並將它們指派給安全性角色，然後再共用內容。 如果 Contoso 改為使用臨機操作邀請，可能會有一小段時間，讓來賓使用者看不到任何資料。

> [!NOTE]
> 使用臨機操作邀請時，存取 RLS 所保護的資料時，這項延遲可能會導致對您的 IT 小組提出支援要求，因為使用者在收到的電子郵件中開啟共用連結時，將會看到空白或已中斷的報表/儀表板。 因此，強烈建議在此案例中使用計畫的邀請。 * *

讓我們使用範例來逐步解說。

如先前所述，Contoso 有全球供應商，他們想要確保供應商組織的使用者只從他們的領域取得資料的深入解析。  但是 Contoso 的使用者可以存取所有資料。 Contoso 不會建立數個不同的報表，而是會建立單一報表，並根據使用者的流覽方式來篩選資料。

![共用內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

為了確保 Contoso 可以根據正在連線的物件來篩選資料，Power BI desktop 中會建立兩個角色。 一個用來篩選 SalesTerritory "歐洲" 的所有資料，另一個則用於 "北美洲"。

![管理角色](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

每當在報表中定義角色時，就必須將使用者指派給特定的角色，才能存取任何資料。 角色指派會在 Power BI 服務內發生（**資料集 > 安全性**）

![設定安全性](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

這會開啟一個頁面，Contoso 的 BI 小組可以看到他們所建立的兩個角色。  Contoso 的 BI 小組現在可以將使用者指派給角色。

![資料列層級安全性](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

在範例中，Contoso 會將電子郵件地址為 "[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)" 的夥伴組織中的使用者新增至歐洲角色：

![資料列層級安全性設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

當 Azure AD 解決此問題時，Contoso 可以看到該名稱顯示在準備要新增的視窗中：

![顯示角色](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

現在，當此使用者開啟與他們共用的應用程式時，他們只會看到包含歐洲資料的報表：

![檢視內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>動態資料列層級安全性

另一個有趣的主題是瞭解動態資料列層級安全性（RLS）如何與 Azure AD B2B 搭配使用。

簡單地說，動態資料列層級安全性的運作方式，是根據連接到 Power BI 之人員的使用者名稱，篩選模型中的資料。 您不需要為使用者群組新增多個角色，而是在模型中定義使用者。 我們不會在此詳細說明此模式。 Kasper de Jong 在[Power BI Desktop 動態安全性](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)功能提要和[本白皮書](https://msdn.microsoft.com/library/jj127437.aspx)中提供所有資料列層級安全性的詳細資訊。

讓我們看一個小範例-Contoso 有一個依群組分組的簡單報告：

![範例內容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

現在這份報告必須與兩位來賓使用者和內部使用者共用-內部使用者可以看到所有內容，但來賓使用者只能看到他們可以存取的群組。 這表示我們必須僅針對來賓使用者篩選資料。 為了適當地篩選資料，Contoso 會使用白皮書和 blog 文章中所述的動態 RLS 模式。 這表示 Contoso 會將使用者名稱新增至資料本身：

![將 RLS 使用者向資料本身查看](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

然後，Contoso 會建立正確的資料模型，以適當的關聯性來篩選資料：

![會顯示適當的資料](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

若要根據登入的人員自動篩選資料，Contoso 必須建立一個在連接的使用者中傳遞的角色。 在此情況下，Contoso 會建立兩個角色–第一個是「securityrole」，它會使用登入 Power BI 的目前使用者名稱來篩選使用者資料表（這適用于 Azure AD B2B 來賓使用者）。

![管理角色](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso 也會為可查看所有專案的內部使用者建立另一個「AllRole」–此角色沒有任何安全性述詞。

將 Power BI desktop 檔案上傳至服務之後，Contoso 可以將來賓使用者指派給 "SecurityRole" 和內部使用者至 "AllRole"

現在，當來賓使用者開啟報表時，他們只會看到來自群組 A 的銷售：

![僅來自群組 A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

在右邊的矩陣中，您可以看到 USERNAME （）和 USERPRINCIPALNAME （）函式的結果，這兩個函式都會傳回來賓使用者的電子郵件地址。

現在，內部使用者會看到所有資料：

![顯示的所有資料](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

如您所見，動態 RLS 可與內部或來賓使用者一起使用。

> [!NOTE]
> 在 Azure Analysis Services 中使用模型時，此案例也適用。 您的 Azure 分析服務通常會與您的 Power BI 連線到相同的 Azure AD-在此情況下，Azure Analysis Services 也會知道透過 Azure AD B2B 邀請的來賓使用者。

## <a name="connecting-to-on-premises-data-sources"></a>連接到內部部署資料來源

Power BI 提供的功能讓 Contoso 能夠直接使用內部部署資料來源，例如[SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)或[SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) ，因為內部[部署資料閘道](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/)。 您甚至可以使用與 Power BI 搭配使用的相同認證來登入這些資料來源。

> [!NOTE]
> 安裝閘道以連線到您的 Power BI 租使用者時，您必須使用在您的租使用者中建立的使用者。 外部使用者無法安裝閘道，並將其連線到您的租使用者。 _

對於外部使用者而言，這可能會比較複雜，因為內部部署 AD 通常不知道外部使用者。 Power BI 為此提供了因應措施，允許 Contoso 系統管理員將外部使用者名稱對應至內部使用者名稱，如[管理您的資料來源-Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)中所述。 例如， [lucy@supplier1.com](mailto:lucy@supplier1.com)可以對應至[lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com)。

![對應使用者名稱](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

如果 Contoso 只有少數使用者，或 Contoso 可以將所有外部使用者對應至單一內部帳戶，這種方法就沒問題。 針對更複雜的案例，其中每個使用者都需要自己的認證，還有更先進的方法，可使用[自訂 AD 屬性](https://technet.microsoft.com/library/cc961737.aspx)來進行對應，如[管理您的資料來源-Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)中所述。 這可讓 Contoso 系統管理員為您 Azure AD 中的每位使用者（也是外部 B2B 使用者）定義對應。  這些屬性可以透過使用腳本或程式碼的 AD 物件模型來設定，讓 Contoso 可以完全自動化邀請上的對應或排定的步調。

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>讓外部使用者在 Power BI 內編輯和管理內容

Contoso 可以讓外部使用者在組織內提供內容，如先前在 Power BI 內容的跨組織編輯和管理一節中所述。

> [!NOTE]
> 若要編輯和管理組織 Power BI 中的內容，使用者必須在 [我的工作區] 以外的工作區中具有 [Power BI Pro 授權]。 使用者可以取得本檔的_授權_一節中所涵蓋的 Pro 授權。

Power BI 系統管理員入口網站會在 [租使用者設定] 中提供 [**允許外部來賓使用者編輯和管理組織中的內容**] 設定。 根據預設，設定會設定為 [停用]，表示外部使用者預設會取得受限的唯讀體驗。 設定會套用至 Azure AD 中設定為 [來賓] 的使用者。 下表描述使用者體驗的行為，視其 UserType 和設定的方式而定。

| **Azure AD 中的使用者類型** | **允許外部來賓使用者編輯和管理內容設定** | **表現** |
| --- | --- | --- |
| 來賓 | 已針對使用者停用（預設值） | 僅限每個專案耗用量。 透過傳送給來賓使用者的 URL 觀看時，允許對報表、儀表板和應用程式進行唯讀存取。 Power BI 行動版應用程式會為來賓使用者提供唯讀的視圖。 |
| 來賓 | 為使用者啟用 | 外部使用者可以存取完整的 Power BI 體驗，不過有些功能無法使用。 外部使用者必須使用 Power BI 服務 URL 與包含的租使用者資訊，登入 Power BI。 使用者可以取得家庭體驗、[我的工作區] 和 [根據許可權]，以流覽、查看和建立內容。 </br></br> Power BI 行動版應用程式會為來賓使用者提供唯讀的視圖。 |

> [!NOTE]
> Azure AD 中的外部使用者也可以設定為 UserType 成員。 Power BI 目前不支援這項功能。

在 Power BI 系統管理員入口網站中，設定如下圖所示。

![系統管理員設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

來賓使用者會取得唯讀的預設體驗，並可編輯和管理內容。 預設為停用，表示所有來賓使用者都有唯讀體驗。 Power BI 系統管理員可以針對組織中的所有來賓使用者，或針對 Azure AD 中定義的特定安全性群組啟用設定。 在下圖中，Contoso Power BI 系統管理員在 Azure AD 中建立安全性群組，以管理哪些外部使用者可以編輯和管理 Contoso 租使用者中的內容。

為協助這些使用者登入 Power BI，請提供租使用者 URL 給他們。 若要尋找租用戶 URL，請遵循下列步驟。

1. 在 Power BI 服務的頂端功能表中，選取 [說明] （ **？** ），然後**關於 Power BI**。
2. 尋找 [**租使用者 URL**] 旁的值。 這是您可以與來賓使用者共用的租使用者 URL。

    ![租用戶 URL](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

使用 [允許外部來賓使用者編輯和管理組織中的內容] 時，指定的來賓使用者可以存取您組織的 Power BI，並查看他們具有許可權的任何內容。 他們可以存取 Home、流覽和參與工作區內容、安裝位於存取清單中的應用程式，以及擁有 [我的工作區]。 針對使用新工作區體驗的工作區，他們可以建立工作區管理員，或是成為工作區管理員。

> [!NOTE]
> 使用此選項時，請務必審查此檔的治理區段，因為預設 Azure AD 設定會防止來賓使用者使用某些功能，例如人員選擇器，這可能會導致經驗降低。 * *

針對透過 [允許外部來賓使用者編輯和管理組織中的內容] 設定啟用的來賓使用者，某些體驗無法供他們使用。 若要更新或發行報表，來賓使用者必須使用 Power BI 服務 web UI，包括取得要上傳 Power BI Desktop 檔案的資料。 不支援下列體驗：

- 從 Power BI Desktop 直接發佈至 Power BI 服務
- 來賓使用者無法使用 Power BI Desktop 連接到 Power BI 服務中的服務資料集
- 與 Office 365 群組系結的傳統工作區：來賓使用者無法建立或管理這些工作區的系統管理員。 他們可以是成員。
- 工作區的存取清單不支援傳送臨時邀請
- Power BI Publisher for Excel 不支援來賓使用者
- 來賓使用者無法安裝 Power BI Gateway，並將它連接到您的組織
- 來賓使用者無法安裝應用程式並發佈到整個組織
- 來賓使用者無法使用、建立、更新或安裝組織內容套件
- 來賓使用者無法使用 [使用 Excel 分析]
- 來賓使用者無法在批註中 @mentioned （即將推出的版本中將會新增此功能）
- 來賓使用者無法使用訂用帳戶（將在即將推出的版本中新增此功能）
- 如果來賓使用者要使用這項功能，則應具備工作或學校帳戶。 因為登入限制，使用個人帳戶的來賓使用者會遇到更多限制。



## <a name="governance"></a>控管

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>其他 Azure AD 設定，會影響與 Azure AD B2B 相關 Power BI 中的體驗

當您使用 Azure AD B2B 共用時，Azure Active Directory 系統管理員會控制外部使用者體驗的各個層面。 這些是在您租使用者的 [Azure Active Directory 設定] 中的 [外部共同作業設定] 頁面上控制。

如需這些設定的詳細資料，請參閱：

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> 根據預設，[來賓使用者權限受限] 選項會設定為 [是]，因此 Power BI 中的來賓使用者在使用者選擇器 Ui 無法用於這些使用者的情況下，會有有限的使用經驗。 請務必與您的 Azure AD 系統管理員合作，將其設定為 [否]，如下所示，以確保良好的體驗。 * *

![外部共同作業設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>控制來賓邀請

Power BI 系統管理員可以造訪 Power BI 系統管理員入口網站，只控制 Power BI 的外部共用。 但是，租使用者系統管理員也可以使用各種 Azure AD 原則來控制外部共用。  這些原則可讓租使用者系統管理員

- 關閉終端使用者的邀請
- 只有系統管理員和來賓邀請者角色中的使用者可以邀請
- 系統管理員、來賓邀請者角色和成員可以邀請
- 所有使用者（包括來賓）都可以邀請

若要深入瞭解這些原則，請參閱[委派邀請中的 AZURE ACTIVE DIRECTORY B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations)共同作業。

外部使用者的所有 Power BI 動作也會[在我們的「審核入口網站」中進行審核](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)。

### <a name="conditional-access-policies-for-guest-users"></a>來賓使用者的條件式存取原則

Contoso 可以針對從 Contoso 租使用者存取內容的來賓使用者，強制執行條件式存取原則。 您可以在 B2B 共同作業[使用者的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions)中找到詳細的指示。

## <a name="common-alternative-approaches"></a>常見的替代方法

雖然 Azure AD B2B 可讓您輕鬆地跨組織共用資料和報告，但有其他幾種常用的方法，在某些情況下可能會更高階。

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>替代選項1：為夥伴使用者建立重複的身分識別

使用此選項時，Contoso 必須針對 Contoso 租使用者中的每個合作夥伴使用者手動建立重複的身分識別，如下圖所示。 然後，在 Power BI 內，Contoso 可以與適當的報表、儀表板或應用程式共用至指派的身分識別。

![設定適當的對應和名稱](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

選擇此替代方法的理由：

- 由於使用者的身分識別是由您的組織所控制，因此任何相關的服務（例如電子郵件、SharePoint 等等）也會在您組織的控制範圍內。 您的 IT 系統管理員可以重設密碼、停用帳戶的存取權，或審核這些服務中的活動。
- 針對其商務使用個人帳戶的使用者，通常會受到限制而無法存取某些服務，因此可能需要組織帳戶。
- 某些服務僅適用于您組織的使用者。 例如，使用 Intune 來管理使用 Azure B2B 之外部使用者的個人/行動裝置上的內容可能是不可行的。

不選擇此替代方法的理由：

- 合作夥伴組織的使用者必須記住兩組認證–一個用來從自己的組織存取內容，另一個用來從 Contoso 存取內容。 這對這些來賓使用者而言很麻煩，而許多來賓使用者會因為此經驗而感到困惑。
- Contoso 必須購買並將每個使用者的授權指派給這些使用者。 如果使用者需要收到電子郵件或使用 office 應用程式，他們需要適當的授權，包括 Power BI Pro 在 Power BI 中編輯和共用內容。
- Contoso 可能會想要針對外部使用者強制執行更嚴格的授權和治理原則，與內部使用者相較之下。 為了達到此目的，Contoso 必須為外部使用者建立內部的命名法，而且所有 Contoso 使用者都必須對此命名法進行教育。
- 當使用者離開組織時，他們會繼續存取 Contoso 的資源，直到 Contoso 系統管理員手動刪除其帳戶
- Contoso 管理員必須管理來賓的身分識別，包括建立、重設密碼等。

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>替代選項2：使用自訂驗證建立自訂 Power BI Embedded 應用程式

Contoso 的另一個選項是使用自訂驗證（「[應用程式擁有資料](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers)」）來建立自己的自訂內嵌 Power BI 應用程式。 雖然許多組織都沒有時間或資源來建立自訂應用程式，以將 Power BI 內容散發給其外部夥伴，但對於某些組織來說，這是最好的方法，而且值得認真考慮。

組織通常會有現有的合作夥伴入口網站，以集中存取合作夥伴的所有組織資源、提供與內部組織資源的隔離，並為合作夥伴提供簡化的體驗，以支援許多合作夥伴和其個別使用者。

![許多合作夥伴入口網站](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

在上述範例中，每個供應商的使用者登入 Contoso 的合作夥伴入口網站，並使用 AAD 做為身分識別提供者。 它可以使用 AAD B2B、Azure B2C、原生身分識別，或與任何數目的其他身分識別提供者同盟。 使用者會使用 Azure Web 應用程式或類似的基礎結構，登入並存取合作夥伴入口網站組建。

在 web 應用程式內，會從 Power BI Embedded 部署內嵌 Power BI 報表。 Web 應用程式會以一致的體驗，簡化對報表和任何相關服務的存取，目的在於讓供應商能夠輕鬆與 Contoso 互動。 此入口網站環境會與 Contoso 內部 AAD 和 Contoso 的內部 Power BI 環境隔離，以確保供應商無法存取這些資源。 一般而言，資料會儲存在個別的合作夥伴資料倉儲中，以確保資料的隔離。 這項隔離有其優點，因為它會限制可直接存取您組織資料的外部使用者數目、限制外部使用者可能可以使用的資料，以及限制不小心與外部使用者共用。

使用 Power BI Embedded，入口網站可以利用有利的授權、使用應用程式權杖或主要使用者加上在 Azure 模型中購買的 premium 容量，這可簡化將授權指派給使用者的疑慮，並可根據預期相應增加/減少實例. 入口網站可以提供整體高品質和一致的體驗，因為合作夥伴會存取單一入口網站，並將其設計為所有合作夥伴的需求。 最後，由於以 Power BI Embedded 為基礎的解決方案通常是設計為多租使用者，因此可讓您更輕鬆地確保夥伴組織之間的隔離。

選擇此替代方法的理由：

- 隨著合作夥伴組織的人數成長，更容易管理。 由於合作夥伴會新增至與 Contoso 的內部 AAD 目錄隔離的個別目錄中，因此它可簡化 IT 治理責任，並協助防止意外將內部資料共用給外部使用者。
- 一般合作夥伴入口網站是具有高度品牌的體驗，具備跨合作夥伴一致的體驗，並可簡化以符合一般合作夥伴的需求。 因此，Contoso 可以藉由將所有必要的服務整合到單一入口網站，為合作夥伴提供更好的整體體驗。
- 在 Power BI Embedded 中編輯內容等高級案例的授權成本涵蓋于購買的 Power BI Premium，而且不需要將 Power BI Pro 授權指派給那些使用者。
- 如果架構為多租使用者解決方案，則可跨合作夥伴提供更好的隔離。
- 合作夥伴入口網站通常包含其他適用于合作夥伴 Power BI 報表、儀表板和應用程式以外的工具。

不選擇此替代方法的理由：

- 若要建立、操作及維護這類入口網站，必須投入大量的時間來投入資源和時間。
- 解決方案的時間比使用 B2B 共用長，因為需要仔細規劃並在多個工作流上執行。
- 如果有較少的合作夥伴，此替代方案所需的投入量可能會太高而無法論證。
- 與臨機操作共用共同作業是您組織面臨的主要案例。
- 每個夥伴的報表和儀表板都不同。 此替代方案會導入管理額外負荷，而不僅直接與合作夥伴共用。



## <a name="faq"></a>常見問題集

**Contoso 是否可以傳送自動兌換的邀請，讓使用者只是「準備好了」？或者，使用者是否一定要按到兌換 URL？**

使用者必須一律先按同意體驗，才能存取內容。

如果您要邀請許多來賓使用者，建議您將[使用者新增至資源組織中的來賓邀請者角色，以](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role)從您的核心 Azure AD 系統管理員委派這項功能。 這位使用者可以使用登入 UI、PowerShell 腳本或 Api，邀請夥伴組織中的其他使用者。 這可降低 Azure AD 系統管理員的管理負擔，以邀請或重新傳送邀請給合作夥伴組織的使用者。

**如果來賓使用者的夥伴沒有多重要素驗證，Contoso 是否可以強制執行多重要素驗證？**

是。 如需詳細資訊，請參閱 B2B 共同作業[使用者的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions)。

**當受邀的合作夥伴使用同盟來新增自己的內部部署驗證時，B2B 共同作業如何運作？**

如果合作夥伴具有與內部部署驗證基礎結構同盟的 Azure AD 租使用者，則會自動達成內部部署單一登入（SSO）。 如果合作夥伴沒有 Azure AD 租使用者，則可能會為新的使用者建立 Azure AD 帳戶。

**我可以使用取用者電子郵件帳戶邀請來賓使用者嗎？**

Power BI 支援使用取用者電子郵件帳戶邀請來賓使用者。 這包括 hotmail.com、outlook.com 和 gmail.com 等網域。 不過，這些使用者可能會遇到超出工作或學校帳戶的使用者所遇到的限制。
