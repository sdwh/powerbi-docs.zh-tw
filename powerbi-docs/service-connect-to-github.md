---
title: 使用 Power BI 連接到 GitHub
description: 適用於 GitHub 的 Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: b0f2bd53f1d8b82b70072446723c2ca3723eeacd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65608418"
---
# <a name="connect-to-github-with-power-bi"></a>使用 Power BI 連接到 GitHub
這篇文章會引導您提取您的資料，從您的 GitHub 帳戶與 Power BI 範本應用程式。 範本應用程式會產生儀表板、 一組報表，與資料集，以便讓您瀏覽您的 GitHub 資料工作區。 Power BI 的 GitHub 應用程式會顯示深入了解您的 GitHub 存放庫，也稱為 repo、 參與、 問題、 提取要求和作用中使用者相關資料。

您已安裝的範本應用程式之後，您可以變更儀表板和報表。 然後您可以將它散發為應用程式給同事您組織中。

連接到[GitHub 範本應用程式](https://app.powerbi.com/getdata/services/github)或深入了解[GitHub 整合](https://powerbi.microsoft.com/integrations/github)使用 Power BI。

您也可以嘗試[GitHub 教學課程](service-tutorial-connect-to-github.md)。 它會安裝相關的 Power BI 文件的公用存放庫的實際 GitHub 資料。

>[!NOTE]
>範本應用程式需要能夠存取此儲存機制的 GitHub 帳戶。 下方有需求的詳細資料。

## <a name="how-to-connect"></a>如何連接
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]
   
3. 選取  **GitHub** \> **立即取得**。
4. 在 **安裝此 Power BI 應用程式嗎？** 選取**安裝**。
4. 在 **應用程式**窗格中，選取**GitHub**圖格。

    ![Power BI GitHub 磚](media/service-connect-to-github/power-bi-github-tile.png)

6. 在 **開始使用新的應用程式**，選取**將資料連接**。

    ![開始使用您的新應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

5. 輸入該儲存機制的儲存機制名稱和儲存機制擁有者。 請參閱以下關於[尋找這些參數](#FindingParams)的詳細資料。
   
    ![Power BI GitHub 存放庫名稱](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. 輸入您的 GitHub 認證 （此步驟可能會略過如果您已登入您的瀏覽器）。 
6. 針對 [驗證方法]  選取 [oAuth2]  \> [登入]  。 
7. 請遵循 GitHub 驗證畫面。 授與 GitHub 的 GitHub 資料的 Power BI 範本應用程式權限。
   
   ![Power BI 的 GitHub 授權](media/service-connect-to-github/github_authorize.png)
   
    Power BI 連線到 GitHub 與您的資料。  資料會每天重新整理一次。 Power BI 匯入資料之後，您會看到新的 GitHub 工作區的內容。

## <a name="modify-and-distribute-your-app"></a>修改並散發應用程式

您已安裝 GitHub 範本應用程式。 也就是說，您也建立了 GitHub 應用程式工作區。 在工作區中，您可以變更報表和儀表板，並再將它做為散發*應用程式*給組織中的同事。 

1. 在左側的導覽列中選取工作區名稱旁邊的箭號。 您會看到工作區包含儀表板和報表。

    ![在左側的導覽窗格中的應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

8. 選取新[GitHub 儀表板](https://powerbi.microsoft.com/integrations/github)。    
    ![在 Power BI 中 GitHub 儀表板](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

3. 若要檢視新的 GitHub 工作區中的所有內容，在左側的導覽列中，選取**工作區** > **GitHub**。
 
   ![在左側的導覽窗格中的 GitHub 工作區](media/service-connect-to-github/power-bi-github-left-nav.png)

    此檢視位於工作區的內容清單。 在右上角中，您會看到**更新應用程式**。 當您準備好應用程式散發給您的同事時，這是您將開始的地方。 

    ![GitHub 內容清單](media/service-connect-to-github/power-bi-github-content-list.png)

2. 選取 **報表**並**資料集**若要查看工作區中的其他項目。

    了解[將應用程式散發](service-create-distribute-apps.md)向您的同事。

## <a name="whats-included-in-the-app"></a>應用程式中包含的內容
在 Power BI 中 GitHub 提供下列資料：     

| 資料表名稱 | 描述 |
| --- | --- |
| 參與 |參與資料表提供總計新增、 刪除及每週彙總參與者所撰寫的認可。 包含前 100 名參與者。 |
| 問題 |列出所有選取儲存機制的問題，其中包含計算，像是已解決問題的總計和平均時間、未解決問題總數、已解決問題總數。 當儲存機制中沒有任何問題時，此資料表為空白。 |
| 提取要求 |此表格包含此儲存機制和提取要求者之所有提取要求。 它也包含周圍多少開啟、 關閉、 和總計的提取要求的計算、 提取要求所花費的時間和平均的提取要求花費多少時間。 當儲存機制中沒有任何問題時，此資料表為空白。 |
| 使用者 |下表提供 GitHub 使用者或參與者有參與、 提出問題，或解決提取要求選取的儲存機制的清單。 |
| 里程碑 |它具有所選儲存機制的所有里程碑。 |
| DateTable |此資料表包含從今天開始推算多年來在過去，可讓您依日期分析 GitHub 資料的日期。 |
| ContributionPunchCard |這個資料表可以當做所選取儲存機制的參與穿孔卡片。 它會依一週中各天和一天中各小時顯示認可。 此資料表未連接到模型中的其他資料表。 |
| RepoDetails |此資料表會提供選取的儲存機制詳細資料。 |

## <a name="system-requirements"></a>系統需求
* 可存取儲存機制的 GitHub 帳戶。  
* 第一次登入期間授與適用於 GitHub 應用程式之 Power BI 的權限。 請參閱以下撤銷存取權的詳細資訊。  
* 有足夠可用的 API 呼叫，以便提取和重新整理資料。  

### <a name="de-authorize-power-bi"></a>取消授權 Power BI
若要取消授權 Power BI 連線至您的 GitHub 存放庫，您可以撤銷 GitHub 中的存取。 請參閱此[GitHub 說明](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth)如需詳細資訊。

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>尋找參數
您可以查看在 GitHub 本身的儲存機制來判斷擁有者和儲存機制：

![存放庫名稱和擁有者](media/service-connect-to-github/github_ownerrepo.png)

第一個部分的 "Azure" 是擁有者，而第二個部分 "azure-sdk-for-php" 是儲存機制本身。  您會在儲存機制的 URL 中看到這兩個相同項目：

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>疑難排解
如有必要，您可以確認您的 GitHub 認證。  

1. 在另一個瀏覽器視窗中，移至 GitHub 網站並登入 GitHub。 在 GitHub 網站右上角，可以看到您已登入。    
2. 在 GitHub 中瀏覽至您計劃要在 Power BI 中存取之儲存機制的 URL。 例如： https://github.com/dotnet/corefx。  
3. 回到 Power BI，嘗試連接至 GitHub。 在 [設定 GitHub] 對話方塊中，請使用相同儲存機制的儲存機制名稱和儲存機制擁有者名稱。  

## <a name="next-steps"></a>後續步驟

* [教學課程：連接到 Power BI 與 GitHub 存放庫](service-tutorial-connect-to-github.md)
* [在 Power BI 中建立新的工作區](service-create-the-new-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](consumer/end-user-apps.md)
* [連接到外部服務的 Power BI 應用程式](service-connect-to-services.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

