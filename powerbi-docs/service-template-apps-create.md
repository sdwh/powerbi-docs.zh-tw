---
title: 在 Power BI 中建立範本應用程式 (預覽)
description: 如何在 Power BI 中建立可以散發給所有 Power BI 客戶的範本應用程式。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: maggies
ms.openlocfilehash: c08b7e60777b720aa4fc2489b02c212bdd3e7169
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249536"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>在 Power BI 中建立範本應用程式 (預覽)

新的 Power BI「範本應用程式」讓 Power BI 合作夥伴撰寫少量程式碼或不用撰寫程式碼，即可建置 Power BI 應用程式，再將應用程式部署至所有 Power BI 客戶。  本文包含建立 Power BI 範本應用程式的逐步指示。 

如果您可以建立 Power BI 報表及儀表板，您便可以成為「範本應用程式建置者」，將分析內容建置並封裝在「應用程式」中。 接著，您可以透過任何可用的平台 (例如 AppSource)，或在您自己的 Web 服務中使用應用程式，來將應用程式部署至其他 Power BI 租用戶。 身為建置者，您可以建立受保護的分析套件以供散發。 

Power BI 租用戶系統管理員可管理並控制其組織中可以建立及安裝範本應用程式的人員。 獲授權的人員可以安裝您的範本應用程式，然後予以修改並散發給其組織中的 Power BI 使用者。

## <a name="prerequisites"></a>先決條件 

以下為建立範本應用程式的需求：  

- [Power BI Pro 授權](service-self-service-signup-for-power-bi.md)
- [安裝 Power BI Desktop](desktop-get-the-desktop.md) (選用)
- 熟悉 [Power BI 的基本概念](service-basic-concepts.md)
- 建立範本應用程式的權限。 如需詳細資料，請參閱 Power BI [管理入口網站、範本應用程式設定](service-admin-portal.md#template-apps-settings-preview)。

## <a name="enable-app-developer-mode"></a>啟用應用程式開發人員模式

若要建立可以散發給其他 Power BI 租用戶的範本應用程式，您需要處於應用程式開發人員模式。 否則，您建立的應用程式只能供您自己組織的 Power BI 使用者使用。
 
1. 在瀏覽器中開啟 Power BI 服務。
2. 前往 [設定] > [一般] > [開發人員] > [啟用範本應用程式開發模式]。

    ![啟用範本應用程式](media/service-template-apps-create/power-bi-dev-template-app.png)

    如果您未看到該選項，請連絡 Power BI 系統管理員，要求其授與您管理入口網站中的[範本應用程式開發權限](service-admin-portal.md#template-apps-settings-preview)。

3. 選取 [ **套用**]。

## <a name="create-the-template-app-workspace"></a>建立範本應用程式工作區

若要建立可以散發給其他 Power BI 租用戶的範本應用程式，您需要在其中一個新的應用程式工作區中予以建立。 
 
1. 在 Power BI 服務中，選取 [工作區] > [建立應用程式工作區]。 
 
    ![建立應用程式工作區](media/service-template-apps-create/power-bi-new-workspace.png)

3. 在 [建立應用程式工作區] 的 [預覽改進的工作區] 中，選取 [立即試用]。

    ![試用新的工作區](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

5. 輸入您應用程式工作區的名稱、描述 (選用) 及標誌影像 (選用)。

4. 選取 [開發範本應用程式]。

    ![開發範本應用程式](media/service-template-apps-create/power-bi-template-app-develop.png)

5. 選取 [儲存]。

## <a name="create-the-content-in-your-template-app"></a>在範本應用程式中建立內容

如同使用一般的 Power BI 應用程式工作區，下一步要在工作區中建立內容。  在這個範本應用程式預覽版本中，每個項目最多只支援一個：一個資料集、一份報表和一個儀表板。

- 在應用程式工作區中[建立 Power BI 內容](power-bi-creator-landing.md)。

如果您使用 Power Query 中的參數，請確認它們具有正確定義的類型 (例如 Text)。 不支援 Any 及 Binary 類型。 

[在 Power BI 中撰寫範本應用程式的提示 (預覽)](service-template-apps-tips.md)有建議，您可在建立範本應用程式的報表及儀表板時加以考慮。

## <a name="create-the-test-template-app"></a>建立測試範本應用程式

既然您的工作區中已有內容，就可開始將它封裝進範本應用程式了。 第一步為建立測試範本應用程式，您只能從您租用戶上的組織內存取。

1. 在範本應用程式工作區中，選取 [建立應用程式]。 

    ![建立應用程式](media/service-template-apps-create/power-bi-create-app.png)
 
    您需要在這裡填入範本應用程式的其他參數，分為四種。 

    **Branding**

    - 應用程式名稱 
    - 描述
    - 應用程式標誌 (選用)
    - 應用程式色彩 

    **Content** 

    - 應用程式登陸頁面 (選用)：定義要作為應用程式登陸頁面的報表或儀表板。  
    
    **Control** 

    控制應用程式使用者在應用程式內容使用上的一些限制。 您可以使用這個控制項來保護應用程式可能包含的特定智慧財產權。

    **Access**

    - 在測試階段中，決定您組織內哪些其他人員可以安裝並測試應用程式。

    放心，您之後隨時可以回來變更這些設定。  

2. 選取 [建立應用程式]。 

    您會看到測試應用程式已就緒的訊息，還有供您複製並分享給應用程式測試者的連結。

    ![測試應用程式已就緒](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    您也已經完成發行管理程序的第一步，將於以下說明該程序。

    

## <a name="manage-the-template-app-release"></a>管理範本應用程式發行

在公開發行這個範本應用程式前，建議您確認其已準備就緒。 Power BI 已建立 [發行管理] 窗格，供您遵循並檢查完整的應用程式發行路徑。 您也可以觸發階段之間的轉換。 常見的階段有： 

- 產生測試應用程式：僅供在您組織內測試。 
- 將測試套件升至生產階段前：在您的組織外測試。
- 將生產階段前套件升至生產階段：生產階段版本。 
- 刪除所有套件，或從先前的階段重新開始。 

讓我們逐步了解各階段。

1. 在範本應用程式工作區中，選取 [發行管理]。

    ![發行管理圖示](media/service-template-apps-create/power-bi-release-management-icon.png)

2. 選取 [建立應用程式]。 

    如果您已在上述**建立測試範本應用程式**中建立測試應用程式，則 [測試] 旁邊會填好黃點，您不需要再選取這裡的 [建立應用程式]。 如果您「真的」選取了，就會回到範本應用程式建立程序。
 
3. 選取 [取得連結]。

    ![建立應用程式、取得連結](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)
 
9. 若要測試應用程式安裝體驗，請複製通知視窗中的連結，並貼到新的瀏覽器視窗。 

    從這裡開始，您遵循的程序與客戶要遵循的程序相同。 如需查看他們的版本，請參閱[在您的組織中安裝及散發範本應用程式](service-template-apps-install-distribute.md)。
 
10. 在對話方塊中，選取 [安裝]。

    安裝成功後，您會看到新應用程式已就緒的通知。 
 
11. 選取 [前往應用程式]。
 
12. 在 [開始使用新的應用程式] 中，您會看到與客戶所見相同的應用程式。 

    ![開始使用新的應用程式](media/service-template-apps-create/power-bi-template-app-get-started.png)

13. 選取 [探索應用程式] 來以範例資料驗證測試應用程式。

1. 若要進行任何變更，請返回原始工作區中的應用程式。 並將測試應用程式更新到您滿意為止。

9. 當您準備好要將應用程式升至生產階段前，以進一步在租用戶外測試時，請返回 [發行管理] 窗格，並選取 [測試] 旁邊的 [升階應用程式]。
 
    ![將應用程式升至生產階段前](media/service-template-apps-create/power-bi-template-app-promote.png)

11. 選取 [升階] 來確認您的選擇。 

12. 複製這個新的 URL 來分享至租用戶外部，以進行測試。 要在 AppSource 上開始應用程式的散發程序時，也是提交這個連結。

12. 當您的應用程式已準備好進入生產階段或透過 AppSource 分享時，請返回 [發行管理] 窗格，並選取 [生產階段前] 旁邊的 [升階應用程式]。
 
11. 選取 [升階] 來確認您的選擇。 

    現在您的應用程式已經進入生產階段，並準備好散發。

    ![應用程式進入生產階段](media/service-template-apps-create/power-bi-template-app-production.png)

若要讓全球上千位 Power BI 使用者都能使用您的應用程式，建議您將應用程式提交至 AppSource。 如需詳細資料，請參閱 [Power BI 應用程式供應項目](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer)。 

## <a name="update-your-app"></a>更新應用程式

既然您的應用程式已經進入生產階段，您可以在測試階段內重新開始，而不中斷生產階段內的應用程式。 

1. 在 [發行管理] 窗格中，選取 [建立應用程式]。

1. 返回再執行應用程式建立程序。 
2. 在您設定好 **Branding**、**Content**、**Control** 及 **Access** 後，再次選取 [建立應用程式]。
3. 選取 [關閉] 並回到 [發行管理]。 

    您會看到您現在有兩個版本：生產階段中的版本，加上測試階段中的新版本。 

    ![範本應用程式的兩個版本](media/service-template-apps-create/power-bi-template-app-2-versions.png)

## <a name="next-steps"></a>後續步驟

請參閱[在您的組織中安裝、自訂及散發範本應用程式](service-template-apps-install-distribute.md)，了解客戶如何與範本應用程式互動。

如需散發應用程式的詳細資料，請參閱 [Power BI 應用程式供應項目](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer)。





