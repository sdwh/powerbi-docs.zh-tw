---
title: 教學課程：連接到 Power BI 與 GitHub 存放庫
description: 在本教學課程中，您使用 Power BI 連線至 GitHub 服務中的實際資料，而且 Power BI 會自動建立儀表板和報表。
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578605"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>教學課程：連接到 Power BI 與 GitHub 存放庫
在本教學課程中，您使用 Power BI 連線接至 GitHub 服務中的實際資料，而且 Power BI 會自動建立儀表板和報表。 您連接到 Power BI 內容公用儲存機制 (也稱為*存放庫*)，並查看這類問題的答案：有多少人參與 Power BI 的公用內容？ 誰參與最多？ 哪個星期幾的參與最多？ 和其他問題。 

![Power BI 中的 GitHub 報表](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

在本教學課程中，您完成下列步驟：

> [!div class="checklist"]
> * 在尚未有 GitHub 帳戶時，註冊一個帳戶 
> * 登入 Power BI 帳戶，或在尚未有 Power BI 帳戶時，註冊一個帳戶
> * 開啟 Power BI 服務
> * 尋找 GitHub 應用程式
> * 輸入 Power BI 公用 GitHub 存放庫的資訊
> * 使用 GitHub 資料檢視儀表板和報表
> * 刪除應用程式以清除資源

如果您尚未註冊 Power BI，請先進行[免費註冊](https://app.powerbi.com/signupredirect?pbi_source=web)再開始。

## <a name="prerequisites"></a>先決條件

若要完成本教學課程，您需要 GitHub 帳戶 (如果還沒有的話)。 

- 報名[的 GitHub 帳戶](https://docs.microsoft.com/contribute/get-started-setup-github)。


## <a name="how-to-connect"></a>如何連接
1. 登入 Power BI 服務 (https://app.powerbi.com) 。 
2. 在左側瀏覽窗格中，選取 [應用程式]  ，然後選取 [取得應用程式]  。
   
   ![Power BI Get 應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. 選取 **應用程式**，型別**GitHub**在搜尋方塊中 >**立即取得**。
   
   ![Power BI Get GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. 在 **安裝此 Power BI 應用程式嗎？** 選取**安裝**。
5. 在 **新的應用程式已準備好**，選取**移至應用程式**。
6. 在 **開始使用新的應用程式**，選取**將資料連接**。

    ![開始使用您的新應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. 輸入該儲存機制的儲存機制名稱和儲存機制擁有者。 此存放庫的 URL 是 https://github.com/MicrosoftDocs/powerbi-docs，因此 [存放庫擁有者]  是 **MicrosoftDocs**，而 [存放庫]  是 **powerbi-docs**。 
   
    ![Power BI GitHub 存放庫名稱](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. 輸入您所建立的 GitHub 認證。 如果您已在瀏覽器中登入 GitHub，則 Power BI 可能會略過此步驟。 

6. 針對**驗證方法**，保留**oAuth2**選定\>**登入**。

7. 請遵循 GitHub 驗證畫面。 將 Power BI 權限授與 GitHub 資料。
   
   Power BI 現在可以與 GitHub 連線，並連線至資料。  資料會每天重新整理一次。

8. Power BI 匯入資料之後，您會看到新的 GitHub 工作區的內容。 
9. 在左側的導覽列中選取工作區名稱旁邊的箭號。 您會看到工作區包含儀表板和報表。 

    ![在左側的導覽窗格中的應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. 選取儀表板名稱旁的省略符號 （...） >**重新命名**> 型別**GitHub 儀表板**。
 
    ![Power BI GitHub 磚](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. 選取全域導覽圖示來最小化左側導覽，讓您有更多空間。

    ![全域導覽圖示](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. 選取 [GitHub 儀表板]。
    
    GitHub 儀表板中將包含即時資料，因此您看到的值可能會不同。

    ![Power BI 中的 GitHub 儀表板](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>詢問問題

1. 將游標置於**詢問資料相關問題**。 Power BI 提供**問題來協助您開始**。 

1. 選取 **多少使用者是否有**。
 
    ![有多少使用者](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. 在中間**多少**並**使用者是否有**，型別**提取要求每個**。 

     Power BI 會建立橫條圖，顯示每一個人的提取要求的數目。

    ![有多少提取要求每位使用者](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. 選取要釘選到儀表板，然後釘選**結束問與答**。

## <a name="view-the-github-report"></a>檢視 GitHub 報表 

1. 在 GitHub 儀表板中，選取 直條圖**依月份的提取要求**開啟相關的報表。

    ![依月份直條圖的提取要求](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. 選取 使用者名稱**總計的提取要求，由使用者**圖表。 在此範例中，我們會看到其工作時數的大部分已在 2 月。

    ![Power BI GitHub 報表反白顯示](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. 選取 [穿孔卡片]  索引標籤來檢視報表中的下一個頁面。 
 
    ![Power BI GitHub 報表穿孔卡片](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    顯然星期二下午 3 是最常見時間，而一週的星期幾*認可*，當使用者簽入其工作。

## <a name="clean-up-resources"></a>清除資源

既然您已經完成本教學課程，就可以刪除 GitHub 應用程式。 

1. 在左側導覽列中，選取 [應用程式]  。
2. 將滑鼠游標停留在 GitHub 磚，然後選取 [刪除]  垃圾桶。

    ![刪除 GitHub 應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已連線至 GitHub 公用存放庫並取得 Power BI 已在儀表板和報表中格式化的資料。 您已經探索儀表板和報表來回答有關資料的一些問題。 您現在可以深入了解連線至其他服務，例如 Salesforce、Microsoft Dynamics 和 Google Analytics。 
 
> [!div class="nextstepaction"]
> [連線至使用的線上服務](service-connect-to-services.md)


