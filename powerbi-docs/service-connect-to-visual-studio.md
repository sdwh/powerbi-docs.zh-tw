---
title: "使用 Power BI 連接到 Visual Studio Team Services"
description: Visual Studio Team Services for Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 20ea9117cf1eee3d7b05be21e5964226349a58c1
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-visual-studio-team-services-with-power-bi"></a>使用 Power BI 連接到 Visual Studio Team Services
若要深入了解您的 Git 和 TFVC Team 專案，請使用 Power BI 的 Visual Studio Team Services 內容套件。 建立連接之後，您的資料會自動出現在儀表板和報表中。 

連接到 [Visual Studio Team Services 內容套件](https://app.powerbi.com/getdata/services/visual-studio-online)或深入了解 Power BI 與 [Visual Studio Team Services 的整合](https://powerbi.microsoft.com/integrations/visual_studio_online)。

>[!NOTE]
>此內容套件需要存取啟用 OAuth 的帳戶。 下方有需求的詳細資料。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。  
   ![](media/service-connect-to-visual-studio/pbi_getdata.png) 
2. 在 [服務]  方塊中，選取 [取得] 。  
   ![](media/service-connect-to-visual-studio/pbi_getservices.png) 
3. 選取 [Visual Studio Team Services 內容套件]，然後按一下 [取得]。     
   ![](media/service-connect-to-visual-studio/vsts.png)
4. 輸入您的 Visual Studio Team Services 帳戶的相關資訊。 請參閱以下關於[尋找這些參數](#FindingParams)的詳細資料。
   
   ![](media/service-connect-to-visual-studio/pbi_vsosignin.png)
   
   您的帳戶名稱是 URL 中 visualstudio.com 前面的部分：    
   ![](media/service-connect-to-visual-studio/urlimage.png)
   
   您的專案名稱是您在 Visual Studio Team Services 中的每一頁頂端看到的名稱：  
   ![](media/service-connect-to-visual-studio/projectimage.png)
5. 使用 oAuth2 進行 Visual Studio Team Services 驗證。 您可能會因此看到 VSTS 登入對話方塊。 
   
   > [!IMPORTANT]
   > 某些 Visual Studio Team Services 部署不支援 oAuth2。  登入失敗時，請遵循＜疑難排解＞一節中的指導方針。
   > 
   > 
   
   ![](media/service-connect-to-visual-studio/pbi_vsosignin2.png)
6. 請遵循 Visual Studio Team Services 驗證畫面，授與 Power BI 的 Visual Studio 內容套件對您 Team 專案資料的權限。   
   ![](media/service-connect-to-visual-studio/vsoauthorizeapp450.png)
7. 連接到 Visual Studio Team Services 專案之後，您會在左側瀏覽窗格中看到新的儀表板、報表和資料集。 新的項目會以黃色星號標示\*。  
   ![](media/service-connect-to-visual-studio/visualstudioonline800px.png) 

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](service-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="whats-included"></a>包含的內容
Power BI 中的 Visual Studio Team Services 提供多樣的資料表和欄位供您的報表使用。 內容套件中所包含項目的完整清單可以在這裡找到：<https://www.visualstudio.com/get-started/report/vso-pbi-whats-available-vs>

## <a name="system-requirements"></a>系統需求
* Visual Studio Team Services 帳戶的存取權，且具有權限可使用 REST API 收集資料。  
* 在初始連線期間，授與權限給 “Power BI” 應用程式。 若要中斷 Power BI 的連接並移除其存取您 Visual Studio Team Services 帳戶的授權，您可以在 Visual Studio Team Services 中撤銷存取權。 請參閱 <https://www.visualstudio.com/get-started/setup/change-application-access-policies-vs>。  

如需詳細資訊，請參閱 <https://www.visualstudio.com/en-us/get-started/report/connect-vso-pbi-vs>。

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>尋找參數
您的帳戶名稱是 URL 中 visualstudio.com 前面的部分：    
    ![](media/service-connect-to-visual-studio/urlimage.png)

您的專案名稱是您在 VSTS 中的每一頁頂端看到的名稱：  
    ![](media/service-connect-to-visual-studio/projectimage.png)

您也可以使用萬用字元來選取多個專案。 例如，您可以只輸入“\*” 來選取所有專案，或輸入 “Azure\*” 來選取以 “Azure” 開頭的所有專案。

## <a name="troubleshooting"></a>疑難排解
當您嘗試登入 Visual Studio Team Services 時，可能會收到登入失敗的訊息。

您無法成功通過驗證有兩個常見的原因：

1) 使用個人的帳戶登入，而不是工作或學校帳戶  

2) 您的 Visual Studio Team Services 部署不支援 oAuth 

**使用工作或學校帳戶登入**  
如果您看到這個問題，可能表示您已使用與載入資料的帳戶不同的帳戶來進行 Visual Studio Team Services 驗證 - 例如，如果您使用個人 Microsoft 帳戶連接至 Visual Studio Team Services，而用工作或學校帳戶連接至 PowerBI。

解決這個問題：  

* 取消組態對話方塊  
* 登出 Visual Studio Team Services 的個人帳戶  
* 使用工作或學校帳戶登入 Visual Studio Online  
* 重新啟動上述的「取得資料」程序 

使用您的工作或學校帳戶 (Azure Active Directory / AAD) 連接：  
    ![](media/service-connect-to-visual-studio/vsologinscreen.png)

如果您看到這個對話方塊中，而您想要使用工作或學校帳戶 (Azure Active Directory) 連接，請務必按一下連結以使用該帳戶登入 – 請勿在右手邊提供您的 AAD 認證，那預期為 Microsoft 帳戶 (您個人的帳戶)。

**不支援 oAuth2 的 Visual Studio Team Services 部署**  
VSTS 系統管理員可能已為您的 Visual Studio Team Services 部署停用 oAuth。  當發生這種情況時，您便無法在目前使用 Power BI 的 Visual Studio 內容套件。 

![](media/service-connect-to-visual-studio/oauth.png)

## <a name="next-steps"></a>後續步驟
* [開始使用 Power BI](service-get-started.md)
* [取得資料](service-get-data.md)

