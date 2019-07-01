---
title: 在您的組織中散發範本應用程式 - Power BI
description: 了解如何在 Power BI 中於您的組織內安裝、自訂和散發範本應用程式。
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 158345c44f8801a98e19dcd9b4c7dde14aa6126b
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264522"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>在您的組織中散發範本應用程式 - Power BI

您是 Power BI 分析員嗎？ 如果是，本文說明如何安裝「範本應用程式」  ，以連線到執行業務所用的多個服務，例如 Salesforce、Microsoft Dynamics 和 Google Analytics。 您可以修改儀表板和報表來滿足組織需求，然後以「應用程式」  的形式散發給同事。 

![已安裝 Power BI 應用程式](media/service-template-apps-install-distribute/power-bi-get-apps.png)

如果您有興趣建立範本應用程式並自行散發，請參閱 [Create a template app in Power BI](service-template-apps-create.md) (在 Power BI 中建立範本應用程式)。 Power BI 合作夥伴只要撰寫少量程式碼或不需撰寫程式碼，即可建置 Power BI 應用程式，並將應用程式部署至 Power BI 客戶。 

## <a name="prerequisites"></a>先決條件  

以下是安裝、自訂和散發範本應用程式的需求： 

- [Power BI 專業授權](service-self-service-signup-for-power-bi.md)
- 熟悉 [Power BI 的基本概念](service-basic-concepts.md)
- 來自範本應用程式提供者或 AppSource 的有效安裝連結。 
- 安裝範本應用程式的權限。 

## <a name="install-a-template-app"></a>安裝範本應用程式

您可能會收到範本應用程式的連結。 若否，您可在 AppSource 搜尋自己想要的範本應用程式。 不論如何，只要安裝了範本應用程式，您就能加以修改並在組織內散發。

### <a name="search-appsource-from-a-browser"></a>從瀏覽器搜尋 AppSource

在瀏覽器中選取此連結，來開啟已篩選至 Power BI 應用程式的 AppSource：

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>從 Power BI 服務搜尋 AppSource

1. 在 Power BI 服務的左側瀏覽窗格中選取 [應用程式]   > [取得應用程式]  。

    ![取得應用程式](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. 在 AppSource 中選取 [應用程式]  。

    ![在 AppSource 中搜尋](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. 瀏覽或搜尋應用程式，然後選取 [立即取得]  。

4. 在對話方塊中，選取 [安裝]  。

    ![安裝應用程式](media/service-template-apps-install-distribute/power-install-dialog.png) 如果您有 Power BI Pro 授權，那麼應用程式會安裝到與其相關的應用程式工作區內。 您在相關工作區內自訂應用程式。

    安裝成功後，您會看到新應用程式已就緒的通知。
4. 選取 [前往應用程式]  。
5. 在 [Get started with your new app]  \(開始使用您的新應用程式\) 中選取三個選項的其中一個：

    ![開始使用您的新應用程式](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **Explore app** (探索應用程式)：基本範例資料探索。 從這裡著手來了解應用程式的外觀和感覺。 
    - **Connect Data** (將資料連線)：將資料來源從範例資料變更為您自己的資料來源。 您可以重新定義資料集參數和資料來源認證。 請參閱範本應用程式提示主題中的 [Known limitations](service-template-apps-tips.md#known-limitations) (已知限制)。 
    - **Go to workspace** (前往工作區) (最進階的選項)：您可以進行應用程式建置者允許的所有變更。

    您也可以跳過此對話方塊，並透過左側瀏覽窗格中的 [工作區]  直接存取相關工作區。
    >[!NOTE]
    >安裝範本應用程式同時會安裝為「組織應用程式」  與「應用程式工作區」  。 深入了解如何[在 Power BI 中散發應用程式](service-create-distribute-apps.md)。
 
6. 建議您先連線至自己的資料，再將其與同事共用。 此外也建議您修改報表或儀表板，以使其適用於您的組織。 您也可以在這個時候新增其他報表或儀表板。

   若您選取未列於 AppSource 上之應用程式的安裝連結，您將會看到驗證對話方塊要求您確認您的選擇。

   ![安裝應用程式](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >若要安裝未列於 AppSource 上的範本應用程式，您必須向您的系統管理員要求權限。 如需詳細資料，請參閱 Power BI [管理入口網站、範本應用程式設定](service-admin-portal.md#template-apps-settings)。

## <a name="update-and-distribute-the-app"></a>更新和散發應用程式

當您為組織更新應用程式後，就能準備加以發佈。 這些步驟就和發佈任何其他應用程式一樣。

1. 當您完成自訂後，請於工作區清單檢視的右上角選取 [更新應用程式]  。  

    ![開始應用程式安裝](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. 您可在 [詳細資料]  中修改描述和背景色彩。

   ![設定應用程式描述和色彩](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. 您可在 [內容]  中選取登陸頁面，有儀表板和報表可供選擇。

   ![設定應用程式登陸頁面](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. 在 [存取權]  中，您可將存取權授與選取的使用者或整個組織。  

   ![設定應用程式存取](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. 選取 [更新應用程式]  。 

6. 成功發佈應用程式後，您可以複製連結並和您授與存取權的對象共用。 如果您與他們共用，他們就能在 AppSource 的 [我的組織]  索引標籤看到該應用程式。

## <a name="next-steps"></a>後續步驟 

[與同事在 Power BI 中建立工作區](service-create-workspaces.md)





￼ 

 
