---
title: 在 Power BI 中發佈具有儀表板和報表的應用程式
description: 了解如何發佈應用程式，這些應用程式是為了提供重要計量給組織而建立的儀表板和報表集合。
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 62950462f60fea6db44a9756eff8f99a6841d1d4
ms.sourcegitcommit: 1a79e48ac820c28c5d0fd05399f49ed22fc74ed7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49435434"
---
# <a name="publish-apps-with-dashboards-and-reports-in-power-bi"></a>在 Power BI 中發佈具有儀表板和報表的應用程式

在 Power BI 中，您可以發佈具有相關儀表板和報表集合的「應用程式」。 請在「應用程式工作區」中建立應用程式，您可以在其中與同事對 Power BI 內容進行共同作業。 然後，您可以將已完成的應用程式發佈到組織中的大型人員群組。 深入了解[建立應用程式工作區](service-create-workspaces.md)。

![Power BI 應用程式](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

商務使用者通常需要多個 Power BI 儀表板和報表來執行業務。 透過 Power BI 應用程式，您可以建立多組儀表板和報表，然後將這些應用程式發佈至整個組織、特定人員或群組。 如果您是報表建立者或系統管理員，應用程式可讓您更輕鬆地管理這些集合的權限。

商務使用者可透過幾個不同的方式取得您的應用程式。 如果 Power BI 系統管理員賦予您權限，您可以在您同事的 Power BI 帳戶中自動安裝應用程式。 否則，他們可以從 Microsoft AppSource 安裝您的應用程式，或者您可以將直接連結傳送給他們。 他們可以輕鬆地找到並傳回至您的內容，因為它就在一個地方。 他們無法修改應用程式的內容，但可以在 Power BI 服務或其中一個行動裝置應用程式中與其互動 - 篩選、醒目提示和排序資料本身。 他們會自動取得更新，而且您可以控制資料重新整理的頻率。 深入了解[商務使用者的應用程式體驗](consumer/end-user-apps.md)。

**您知道嗎？** Power BI 正在預覽新的工作區體驗。 請閱讀[建立新的工作區 (預覽)](service-create-the-new-workspaces.md) 來查看工作區未來如何變更。 

## <a name="apps-and-organizational-content-packs"></a>應用程式和組織內容套件
應用程式是組織內容套件的演進。 內容組件無法在新的工作區體驗預覽中使用。 新的工作區體驗正式推出之後，您將無法在新建立的工作區中使用內容套件。 如果您還未將內容套件移轉到應用程式，請開始這麼做。

## <a name="video-apps-and-app-workspaces"></a>影片：應用程式及應用程式工作區
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>應用程式的授權
應用程式工作區的每個成員都必須有 Power BI Pro 授權。 應用程式使用者有兩個選項。

* 選項 1：所有商務使用者都需要 **Power BI Pro** 授權，才能檢視您的應用程式。 
* 選項 2：如果您的應用程式位於 Power BI Premium 容量中，則組織中的免費使用者可以檢視應用程式內容。 如需詳細資訊，請參閱[什麼是 Power BI Premium？](service-premium.md)。

## <a name="publish-your-app"></a>發佈您的應用程式
當工作區中的儀表板和報表就緒時，您可以選擇想要發佈的儀表板和報表，然後將它們發佈為應用程式。 您可以將直接連結傳送給更多的對象，或者可以移至 [從 AppSource 下載並探索更多應用程式]，從 [應用程式] 索引標籤找到您的應用程式。 

1. 在工作區清單檢視中，決定您想要在應用程式中包含哪些儀表板和報表。

     ![選取要發佈的儀表板](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     如果您選擇不發佈報表，您就會在報表和其相關儀表板旁看到警告。 您仍然可以發佈應用程式，但相關的儀表板將會在該報表中遺失磚。

     ![相關儀表板的警告](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. 選取右上角的 [發佈應用程式] 按鈕，來啟動共用該工作區中所有內容的程序。
   
     ![發佈應用程式](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. 在 [詳細資料] 上，填寫描述以協助人員尋找應用程式。 您可以設定背景色彩來進行個人化。
   
     ![應用程式詳細資料](media/service-create-distribute-apps/power-bi-apps-details.png)

4. 在 [內容] 上，您會看到即將發佈為應用程式一部分的內容，即您在該工作區中選取的所有內容。 您也可以設定應用程式登陸頁面，這是儀表板或報表人員移至您的應用程式時先看到的頁面。 您可以選擇 [無]。 接著，他們會到達應用程式中所有內容的清單。 
   
     ![應用程式內容](media/service-create-distribute-apps/power-bi-apps-content.png)

5. 在 [存取] 上，決定誰可以存取應用程式：組織中的所有人、特定人員、Active Directory 安全性群組。 如果您有權限，您可以決定為收件者自動安裝應用程式。 您可以在 [Power BI 管理入口網站](#how-to-enable-pushing-apps)中啟用這項設定。 您可以了解[推送應用程式](#how-to-enable-pushing-apps)的其他考量。

    ![應用程式存取](media/service-create-distribute-apps/power-bi-apps-access.png)

6. 當您選取 [完成] 時，會看到確認它已準備好要發佈的訊息。 在成功對話方塊中，您可以複製直接連結至此應用程式的 URL，並將它傳送給您已與之共用的人員。
   
     ![應用程式完成](media/service-create-distribute-apps/power-bi-apps-success.png)

深入了解[商務使用者的應用程式體驗](consumer/end-user-apps.md)。

## <a name="change-your-published-app"></a>變更已發佈的應用程式
在您發佈應用程式之後，可能想要進行變更或更新。 如果您是應用程式工作區的系統管理員或成員，或是新應用程式工作區的參與者，則很容易進行更新。 

1. 開啟對應至應用程式的應用程式工作區。 
   
     ![開啟工作區](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. 開啟儀表板或報表。 您可以看到您可以進行任何您想要的變更。
   
     應用程式工作區是暫存區域；因此，您的變更在重新發佈之前不會在應用程式中生效。 這可讓您進行變更，而不影響已發佈的應用程式。  
 
3. 回到內容的應用程式工作區清單，然後選取 [更新應用程式]。
   
     ![更新應用程式按鈕](media/service-create-distribute-apps/power-bi-app-update-button.png)

4. 更新 [詳細資料]、[內容] 和 [存取]\(必要時)，然後選取 [更新應用程式]。
   
     ![更新應用程式按鈕](media/service-create-distribute-apps/power-bi-app-update-complete.png)

您已對其發佈應用程式的人員會自動看到應用程式的已更新版本。 

## <a name="automatically-install-apps-for-end-users"></a>自動為終端使用者安裝應用程式
應用程式會提供您的終端使用者執行其工作所需的資料。 如果系統管理員授與您權限，您可以自動為終端使用者安裝應用程式，因此可更輕鬆地將適當的應用程式散發到適當的人員或群組。 您的應用程式將自動顯示在終端使用者的應用程式內容清單中，而不是必須從 Microsoft AppSource 中尋找或追蹤安裝連結。 這可讓您更輕鬆地向使用者推出標準 Power BI 內容。

### <a name="how-to-install-an-app-automatically-for-end-users"></a>如何自動為終端使用者安裝應用程式
系統管理員為您指派權限之後，您有新的選項用來**自動安裝應用程式**。 當您選取此方塊並選取 [完成] (針對現有的應用程式，則為 [更新應用程式]) 後，應用程式就會推送至 [存取] 索引標籤上應用程式的 [權限] 區段中所定義的所有使用者或群組。

![允許推送應用程式](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-were-pushed-to-them"></a>使用者如何取得推送給他們的應用程式
推送應用程式之後，該應用程式會自動出現在 [應用程式] 清單中。 您可以統籌組織中的特定使用者或工作角色必須立即擁有的應用程式。

![允許推送應用程式](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>自動安裝應用程式的考量
推送應用程式給終端使用者時，請記住下列事項：

* 自動為使用者安裝應用程式可能需要時間。 大部分應用程式會立即為使用者安裝，但推送應用程式可能需要時間。  這取決於應用程式中的項目數及有權存取的人數。 建議在使用者需要之前，於時間充足的下班時間推送應用程式。 與幾位使用者確認，再廣泛宣傳應用程式可供使用。

* 重新整理您的瀏覽器。 使用者可能需要重新整理，或關閉並重新開啟其瀏覽器，才能在 [應用程式] 清單中看到推送的應用程式。

* 如果使用者未立即在 [應用程式] 清單中看到應用程式，則應該重新整理，或關閉並重新開啟其瀏覽器。

* 盡量不要造成使用者太多負擔。 請小心不要推送太多應用程式，這樣使用者才能認定預先安裝的應用程式對他們有用。 為調配時間，最好控制誰可以將應用程式推送給終端使用者。 您可以建立連絡點，來將組織中的應用程式推送給終端使用者。

* 不會自動為未接受邀請的來賓使用者安裝應用程式。  

## <a name="unpublish-an-app"></a>解除發佈應用程式
應用程式工作區的任何成員都可以解除發佈應用程式。

* 在應用程式工作區中，選取右上角的省略符號 (**...**) > [Unpublish app]\(解除發佈應用程式)。
  
     ![解除發佈應用程式](media/service-create-distribute-apps/power-bi-app-unpublish.png)

這個動作會解除安裝您發佈給每個人的應用程式，而且他們將無法再存取該應用程式。 它不會刪除應用程式工作區或其內容。

## <a name="next-steps"></a>後續步驟
* [建立應用程式工作區](service-create-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](consumer/end-user-apps.md)
* [外部服務的 Power BI 應用程式](service-connect-to-services.md)
* [Power BI 管理入口網站](https://docs.microsoft.com/power-bi/service-admin-portal)
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
