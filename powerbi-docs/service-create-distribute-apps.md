---
title: 在 Power BI 中發行的應用程式
description: 了解如何發佈新的應用程式，也就是集合的儀表板與報表內建導覽功能。
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941545"
---
# <a name="publish-an-app-in-power-bi"></a>在 Power BI 中發行的應用程式

在 Power BI 中，您可以建立封裝的官方的內容，然後將它散發給廣大的群眾做*應用程式*。 請在「應用程式工作區」  中建立應用程式，您可以在其中與同事對 Power BI 內容進行共同作業。 然後，您可以將已完成的應用程式發佈到組織中的大型人員群組。 

![Power BI 應用程式](media/service-create-distribute-apps/power-bi-new-apps.png)

商務使用者通常需要多個 Power BI 儀表板和報表來執行業務。 透過 Power BI 應用程式，您可以建立多組儀表板和報表，然後將這些應用程式發佈至整個組織、特定人員或群組。 如果您是報表建立者或系統管理員，應用程式可讓您更輕鬆地管理這些集合的權限。

商務使用者會取得您的應用程式以幾個不同的方式：

- 它們可以尋找並從 Microsoft AppSource 安裝您的應用程式
- 您可以傳送它們的直接連結。
- 如果 Power BI 系統管理員賦予您權限，您可以在您同事的 Power BI 帳戶中自動安裝應用程式。

讓您的使用者可以輕鬆找到您的內容周圍的途中，您可以使用自己的內建導覽功能，建立應用程式。 無法修改應用程式的內容。 它們可以與它在 Power BI 服務中，或其中一個行動應用程式-互動-篩選、 反白顯示和排序資料本身。 他們會自動取得更新，而且您可以控制資料重新整理的頻率。 深入了解[商務使用者的應用程式體驗](consumer/end-user-apps.md)。

## <a name="licenses-for-apps"></a>應用程式的授權
若要建立或更新的應用程式，您需要有 Power BI Pro 授權。 應用程式*取用者*，有兩個選項。

* 選項 1：所有商務使用者都需要 **Power BI Pro** 授權，才能檢視您的應用程式。 
* 選項 2：如果您的應用程式工作區位於 Power BI Premium 容量時，您組織中的免費使用者可以檢視應用程式內容。 如需詳細資訊，請參閱[什麼是 Power BI Premium？](service-premium.md)。

## <a name="publish-your-app"></a>發佈您的應用程式
當工作區中的儀表板和報表就緒時，您可以選擇想要發佈的儀表板和報表，然後將它們發佈為應用程式。 

1. 在工作區清單檢視中，決定哪些儀表板和報表，您想要**包含在應用程式**。

     ![選取要發佈的儀表板](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     如果您選擇不包含具有相關的儀表板的報表，您會看到報表旁的警告。 您仍然可以發行應用程式，但相關的儀表板不會有從該報表的磚。

     ![相關儀表板的警告](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. 選取 **發佈應用程式**啟動程序建立和發佈的應用程式，從工作區的右上角的按鈕。
   
     ![發佈應用程式](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. 在 **安裝程式**，填入名稱和描述，以協助人員尋找應用程式。 您可以設定個人化佈景主題色彩。 您也可以新增至支援網站的連結。
   
     ![建置您的應用程式](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. 在 **瀏覽**，選取要發佈為應用程式一部分的內容。 然後，您將應用程式瀏覽至組織中各節的內容。 請參閱[設計您的應用程式的瀏覽體驗](#design-the-navigation-experience-for-your-app)中進一步了解這篇文章。
   
     ![應用程式瀏覽](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. 在 **存取**，決定誰可以存取應用程式。 
    - 在 [傳統的工作區](service-create-workspaces.md)： 您的組織、 特定的人員或 Azure Active Directory (AAD) 安全性群組中的每個人。
    - 在 [新體驗的工作區](service-create-the-new-workspaces.md)： 特定人員、 AAD 安全性群組和通訊群組清單中，Office 365 群組。

6. 如果您有權限，您可以收件者自動安裝應用程式。 Power BI 系統管理員可以在 Power BI 管理入口網站中啟用此設定。 深入了解[自動安裝應用程式](#automatically-install-apps-for-end-users)這篇文章中。

     ![應用程式權限](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. 當您選取**發佈應用程式**，您會看到確認它已準備好要發佈的訊息。 在 [**共用此應用程式**] 對話方塊中，您可以複製此應用程式的直接連結的 URL。
   
     ![應用程式完成](media/service-create-distribute-apps/power-bi-apps-success.png)

您可以傳送的直接連結的人已共用，或他們可以在 [應用程式] 索引標籤上找到您的應用程式移至**下載並探索更多應用程式從 AppSource**。 深入了解[商務使用者的應用程式體驗](consumer/end-user-apps.md)。

## <a name="change-your-published-app"></a>變更已發佈的應用程式
在您發佈應用程式之後，可能想要進行變更或更新。 它很容易更新它，如果您是系統管理員或在新的應用程式工作區中的成員。 

1. 開啟對應至應用程式的應用程式工作區。 
   
     ![開啟工作區](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. 對儀表板或報表中您想要的任何變更。
 
     應用程式工作區是暫存區域；因此，您的變更在重新發佈之前不會在應用程式中生效。 這可讓您進行變更，而不影響已發佈的應用程式。  
 
    > [!IMPORTANT]
    > 如果您移除報表，並更新應用程式，即使您將報表加入至應用程式，您的應用程式取用者會遺失所有的自訂項目，例如書籤、 註解等。  
 
3. 返回應用程式工作區清單中的內容，然後選取**更新應用程式**右上角。
   
1. 更新**安裝程式**，**瀏覽**，並**權限**時，如果您有需要然後選取**更新應用程式**。
   
您已對其發佈應用程式的人員會自動看到應用程式的已更新版本。 

## <a name="design-the-navigation-experience-for-your-app"></a>設計您的應用程式的瀏覽體驗
**新的瀏覽產生器**選項可讓您建置自訂的瀏覽您的應用程式。 自訂的瀏覽可讓您更方便使用者尋找和使用應用程式中的內容。 現有的應用程式會有這個已關閉的選項和新的應用程式預設為 [開] 選項。

當此選項為 off 時，您可以選取**應用程式登陸頁面**兩種**特定內容**，範例儀表板或報表或選取**None**顯示基本的清單使用者的內容。

當您開啟**新的瀏覽產生器**，您可以設計自訂的瀏覽。 預設會列出所有報表、 儀表板和您在您的應用程式中包含的 Excel 活頁簿為一般清單。 

![應用程式瀏覽](media/service-create-distribute-apps/power-bi-apps-navigation.png)

您可以進一步自訂應用程式瀏的覽：
* 重新排列項目，使用向上 / 向下箭號。 
* 重新命名項目中的**回報詳細資料**，**儀表板的詳細資料**，並**活頁簿詳細資料**。
* 隱藏特定的項目，從瀏覽。
* 使用**新增**選項來加入**各節**群組相關的內容。
* 使用**的新**選項來加入**連結**左側瀏覽至外部資源。 

當您將加入**連結**，請在**連結詳細資料**您可以選擇開啟該連結。 根據預設連結則是在中開啟**目前的索引標籤**，但您可以選取**新的索引標籤**，或**內容區域**。 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>使用新的瀏覽產生器選項的考量
以下是要牢記在心，使用新的瀏覽產生器時的一般事項：
* 報表頁面時，會顯示在應用程式瀏覽區上，為可展開的區段
* 如果您關閉新的瀏覽產生器，然後發佈或更新您的應用程式，您會遺失您所做的自訂。 例如，區段、 排序、 連結和導覽項目的自訂名稱會全部遺失。

當將連結加入至您的應用程式瀏覽並選取 [內容] 區域選項：
* 請確定可內嵌的連結。 某些服務會封鎖第三方網站，例如 Power BI 在其內容範圍的內嵌。
* 不支援在其他工作區中內嵌 Power BI 服務內容，例如報表或儀表板。 
* 內嵌 Power BI 報表伺服器透過其原始的內容內嵌 URL 從內部部署部署的內容。 使用中的步驟[建立 Power BI 報表伺服器 URL](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url)取得 URL。 請注意，適用於一般的驗證規則，讓檢視內容需要 VPN 連線到內部部署伺服器。 
* 在內嵌內容的頂端會顯示安全性警告，表示無法在 Power BI 中的內容。



## <a name="automatically-install-apps-for-end-users"></a>自動為終端使用者安裝應用程式
系統管理員可讓您的權限，您可以自動安裝應用程式*推送*到使用者。 這項推播功能，可讓您更輕鬆地散發給適當的人員或群組正確的應用程式。 您的應用程式會自動出現在使用者的應用程式內容清單。 它們不需要從 Microsoft AppSource 中找到它，或追蹤安裝連結。 請參閱系統管理員的啟用方式[推送應用程式給終端使用者](service-admin-portal.md#push-apps-to-end-users)Power BI 系統管理員入口網站文件中。

### <a name="how-to-push-an-app-automatically-to-end-users"></a>如何將應用程式會自動推送給使用者
系統管理員為您指派權限之後，您有新的選項用來**自動安裝應用程式**。 當您核取方塊，然後選取**發佈應用程式**(或**更新應用程式**)、 應用程式推送到所有使用者或群組中定義**權限**上的應用程式一節**存取** 索引標籤。

![允許推送應用程式](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>使用者如何取得推送至它們的應用程式
推送應用程式之後，它在其應用程式清單中會自動出現。 如此一來，您可以規劃應用程式該特定使用者或工作角色在組織的需求將在他們手中。

![允許推送應用程式](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>自動安裝應用程式的考量
推送應用程式給終端使用者時，請記住下列事項：

* 自動為使用者安裝應用程式可能需要時間。 大部分的應用程式立即對使用者，但推送應用程式的安裝可能會很耗時。  這取決於應用程式中的項目數及有權存取的人數。 建議在使用者需要之前，於時間充足的下班時間推送應用程式。 與幾位使用者確認，再廣泛宣傳應用程式可供使用。

* 重新整理瀏覽器。 使用者可能需要重新整理，或關閉並重新開啟其瀏覽器，才能在 [應用程式] 清單中看到推送的應用程式。

* 如果使用者沒有立即看到的應用程式清單中的應用程式，它們應該重新整理或關閉並重新開啟其瀏覽器。

* 盡量不要造成使用者太多負擔。 請小心不要推送太多應用程式，這樣使用者才能認定預先安裝的應用程式對他們有用。 為調配時間，最好控制誰可以將應用程式推送給終端使用者。 建立可用來取得應用程式推送至使用者的組織中的連絡點。

* 還未接受邀請的來賓使用者不會取得自動安裝的應用程式。  

## <a name="unpublish-an-app"></a>解除發佈應用程式
應用程式工作區的任何成員都可以解除發佈應用程式。

>[!IMPORTANT]
>當您解除發佈應用程式時，應用程式使用者會失去其自訂項目。 他們會失去任何個人書籤、 註解或與應用程式中的內容相關聯的訂用帳戶。 只有在您需要移除應用程式時，才解除發佈該應用程式。
> 
> 

* 在應用程式工作區中，選取右上角的省略符號 ( **...** ) > [Unpublish app]\(解除發佈應用程式)  。
  
     ![解除發佈應用程式](media/service-create-distribute-apps/power-bi-app-unpublish.png)

這個動作會解除安裝您發佈給每個人的應用程式，而且他們將無法再存取該應用程式。 它不會刪除應用程式工作區或其內容。

## <a name="view-your-published-app"></a>檢視已發行的應用程式

當您的應用程式取用者會開啟您的應用程式時，他們會看到您建立，而不是標準的 Power BI 左側瀏覽窗格的導覽。 應用程式瀏覽列出的報表和儀表板中已定義的區段。 它也會列出的個別頁面在每個報表中，而是只是報表名稱。

![瀏覽應用程式](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>後續步驟
* [建立應用程式工作區](service-create-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](consumer/end-user-apps.md)
* [外部服務的 Power BI 應用程式](service-connect-to-services.md)
* [Power BI 管理入口網站](https://docs.microsoft.com/power-bi/service-admin-portal)
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
