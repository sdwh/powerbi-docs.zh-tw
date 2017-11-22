---
title: "教學課程：Microsoft Flow 的 Power BI 整合"
description: "了解如何建立由 Power BI 資料警示觸發的流程。"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: YhmNstC39Mw
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/30/2017
ms.author: mihart
ms.openlocfilehash: efab2e6be1d376a0da70c13bb66144ba34afa58c
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="microsoft-flow-and-power-bi"></a>Microsoft Flow 和 Power BI

[Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started) 是一款 SaaS 供應項目，在企業用戶所仰賴的越來越多種應用程式和 SaaS 服務之間，將工作流程自動化。 您可以使用 Flow 整合最愛的應用程式和服務 (包括 Power BI) 來將工作自動化，以取得通知、同步檔案、收集資料等。 工作流程自動化讓重複性的工作變得輕鬆。

[立即開始使用 Flow。](https://flow.microsoft.com/documentation/getting-started)

觀看 Sirui 建立流程，在 Power BI 警示觸發時，將詳細的電子郵件傳送給同事。 然後遵循影片下方的逐步指示親自試試看。

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>建立由 Power BI 資料警示觸發的流程
本教學課程將示範如何建立兩個不同流程；一個從範本建立，一個從頭建立。 如果要跟著做，請[在 Power BI 中建立資料警示](service-set-data-alerts.md)，並[註冊 Microsoft Flow](https://flow.microsoft.com/en-us/#home-signup) (免費！)。

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>建立使用 Power BI 的流程 - 從範本
在這項工作中，我們將使用範本來建立由 Power BI 資料警示 (通知) 觸發的簡單流程。

1. 登入 Microsoft Flow (flow.microsoft.com)。
2. 選取 [我的流程]。
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. 選取 [從範本建立]。
   
    ![](media/service-flow-integration/power-bi-template.png)
4. 使用 [搜尋] 方塊尋找 Power BI 範本，然後選取 [Post a message to a Slack channel when a Power BI data alert is triggered] \(在觸發 Power BI 資料警示時將訊息張貼到 Slack 通道)。
   
    ![](media/service-flow-integration/power-bi-template2.png)
5. 選取 [使用此範本]。
   
   ![](media/service-flow-integration/power-bi-use-template.png)
6. 若出現提示，請選取 [登入] 連線到 Slack 和 Power BI ，然後遵循提示。 您可以從綠色核取記號知道自己已登入。  確認連線後，選取 [繼續]。
   
   ![](media/service-flow-integration/power-bi-flow-signin.png)

### <a name="build-the-flow"></a>建置流程
此範本有一個觸發程序 (愛爾蘭新奧運獎牌的 Power BI 資料警示) 和一個動作 (將訊息張貼到 Slack)。 在您選取欄位時，Flow 會顯示可以包含的動態內容。  在此範例中，訊息本文包含了磚的值和磚 URL。

![](media/service-flow-integration/power-bi-flow-template.png)

1. 從觸發程序下拉式清單中，選取一項 Power BI 資料警示。 選取 [New medal for Ireland] \(愛爾蘭的新獎牌)。 若要了解如何建立警示，請參閱 [Power BI 中的資料警示](service-set-data-alerts.md)。
   
   ![](media/service-flow-integration/power-bi-trigger-flow.png)
2. 若要張貼到 Slack，請輸入通道名稱和訊息文字 (您也可以選取 Flow 建立的預設訊息)。 請注意訊息文字欄位中包含的動態內容。
   
   > [!NOTE]
   > 在通道名稱的開頭加上 "@"。  例如，如果 Slack 通道名稱為 "channelA"，則在流程中輸入 "@channelA"。
   > 
   > 
   
   ![](media/service-flow-integration/power-bi-flow-slacker.png)
3. 當您完成時，請選取 [建立流程] 或 [儲存流程]。  流程隨即建立並進行評估。  Flow 可讓您知道當中是否有錯誤。
4. 如果發現錯誤，請選取 [編輯流程] 加以修正，否則選取 [完成] 即可執行新流程。
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
5. 開啟您的 Slack 帳戶以查看訊息。  
   
   ![](media/service-flow-integration/power-bi-slack-message.png)

## <a name="create-a-flow-that-uses-power-bi---from-scratch-blank"></a>建立使用 Power BI 的流程 - 從頭 (空白)
在這項工作中，我們將從頭建立由 Power BI 資料警示 (通知) 觸發的簡單流程。

1. 登入 Microsoft Flow。
2. 選取 [我的流程] > [從空白建立]。
   
   ![](media/service-flow-integration/power-bi-my-flows.png)
3. 使用 [搜尋] 方塊尋找 Power BI 觸發程序，然後選取[當觸發 Power BI 資料驅動警示時觸發流程]。

### <a name="build-your-flow"></a>建立流程
1. 從下拉式清單中，選取您的警示名稱。  若要了解如何建立警示，請參閱 [Power BI 中的資料警示](service-set-data-alerts.md)。
   
    ![](media/service-flow-integration/power-bi-totalstores.png)
2. 選取 [新步驟] > [新增動作]。
   
   ![](media/service-flow-integration/power-bi-new-step.png)
3. 搜尋 **Outlook**，然後選取 [建立事件]。
   
   ![](media/service-flow-integration/power-bi-create-event.png)
4. 填入事件欄位。 在您選取欄位時，Flow 會顯示可以包含的動態內容。
   
   ![](media/service-flow-integration/power-bi-flow-event.png)
5. 完成時請選取 [建立流程]。  Flow 會儲存並評估流程。 如果沒有錯誤，請選取 [完成] 執行此流程。  新流程會新增到 [我的流程] 頁面中。
   
   ![](media/service-flow-integration/power-bi-flow-running.png)
6. 當 Power BI 資料警示觸發流程時，您會收到類似這樣的 Outlook 事件通知。
   
    ![](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>後續步驟
* [開始使用 Microsoft Flow](https://flow.microsoft.com/en-us/documentation/getting-started/)
* [在Power BI 服務中設定資料警示](service-set-data-alerts.md)
* [在 iPhone 上設定資料警示](mobile-set-data-alerts-in-the-mobile-apps.md)
* [在 Power BI for Windows 10 行動裝置 App 中設定資料警示](mobile-set-data-alerts-in-the-mobile-apps.md)
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

