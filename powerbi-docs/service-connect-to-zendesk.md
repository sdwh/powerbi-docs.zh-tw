---
title: 使用 Power BI 連接到 Zendesk
description: Zendesk for Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 1edc4179b000191dfeff87387417009bc28e0ee5
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578776"
---
# <a name="connect-to-zendesk-with-power-bi"></a>使用 Power BI 連接到 Zendesk

這篇文章會引導您提取您的資料，從您的 Zendesk 帳戶具有 Power BI 範本應用程式。 Zendesk 應用程式提供 Power BI 儀表板和一組 Power BI 報表，讓您深入了解您的票證數量及代理程式的效能。 資料會自動每天重新整理一次。 

您已安裝的範本應用程式之後，您可以自訂儀表板和報表以突顯您最重視的資訊。 然後您可以將它散發為應用程式給同事您組織中。

連接到 [Zendesk 內容套件](https://app.powerbi.com/getdata/services/zendesk)或深入了解 Power BI 與 [Zendesk 的整合](https://powerbi.microsoft.com/integrations/zendesk)。

您已安裝的範本應用程式之後，您可以變更儀表板和報表。 然後您可以將它散發為應用程式給同事您組織中。

>[!NOTE]
>您需要有 Zendesk 管理帳戶，來連接。 下方有[需求](#system-requirements)的詳細資訊。

## <a name="how-to-connect"></a>如何連接

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. 選取  **Zendesk** \> **立即取得**。
4. 在 **安裝此 Power BI 應用程式嗎？** 選取**安裝**。
4. 在 **應用程式**窗格中，選取**Zendesk**圖格。

    ![Power BI 的 Zendesk 應用程式圖格](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. 在 **開始使用新的應用程式**，選取**將資料連接**。

    ![開始使用您的新應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

4. 提供與您帳戶相關聯的 URL。 URL 的形式 **https://company.zendesk.com** 。 請參閱以下關於[尋找這些參數](#finding-parameters)的詳細資料。
   
   ![連線至 Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. 出現提示時，請輸入您的 Zendesk 認證。  選取 [oAuth 2]  做為驗證機制，然後按一下 [登入]  。 請遵循 Zendesk 驗證流程。 （如果您已登入 Zendesk 瀏覽器中，您可能不會提示輸入認證。）
   
   > [!NOTE]
   > 此內容套件需要您連接到 Zendesk 系統管理員帳戶。 
   > 
   
   ![使用 oAuth2 登入](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. 按一下 [允許]  以允許 Power BI 存取您的 Zendesk 資料。
   
   ![按一下 允許](media/service-connect-to-zendesk/zendesk2.jpg)
7. 按一下 [連接]  開始匯入程序。 
8. Power BI 匯入資料之後，您會看到內容清單中您的 Zendesk 應用程式： 新的儀表板、 報表和資料集。
9. 選取儀表板，開始探索程序。

    ![Zendesk 儀表板](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>修改並散發應用程式

您已安裝 Zendesk 範本應用程式。 也就是說，您也建立了 Zendesk 應用程式工作區。 在工作區中，您可以變更報表和儀表板，並再將它做為散發*應用程式*給組織中的同事。 

1. 若要檢視新的 Zendesk 工作區中的所有內容，在左側的導覽列中，選取**工作區** > **Zendesk**。 

    ![在左側的導覽窗格中的 Zendesk 工作區](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    此檢視位於工作區的內容清單。 在右上角中，您會看到**更新應用程式**。 當您準備好應用程式散發給您的同事時，這是您將開始的地方。 

    ![Zendesk 內容清單](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. 選取 **報表**並**資料集**若要查看工作區中的其他項目。

    了解[將應用程式散發](service-create-distribute-apps.md)向您的同事。

## <a name="system-requirements"></a>系統需求
需要有 Zendesk 系統管理員帳戶才能存取 Zendesk 內容套件。 如果您是代理程式或終端使用者和有興趣檢視 Zendesk 資料，新增建議並檢閱 Zendesk 連接器中的[Power BI Desktop](desktop-connect-to-data.md)。

## <a name="finding-parameters"></a>尋找參數
Zendesk URL 與您用來登入 Zendesk 帳戶的 URL 相同。 如果不確定 Zendesk URL，可以使用 Zendesk [登入說明](https://www.zendesk.com/login/)。

## <a name="troubleshooting"></a>疑難排解
如果您遇到連線問題，請檢查 Zendesk URL，並確認您使用的是 Zendesk 系統管理員帳戶。

## <a name="next-steps"></a>後續步驟

* [在 Power BI 中建立新的工作區](service-create-the-new-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](consumer/end-user-apps.md)
* [連接到外部服務的 Power BI 應用程式](service-connect-to-services.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

