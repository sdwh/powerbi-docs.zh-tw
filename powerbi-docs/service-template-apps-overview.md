---
title: 什麼是 Power BI 範本應用程式？ (預覽)
description: 本文為 Power BI 範本應用程式的概觀。 了解如何撰寫少量程式碼或不需撰寫程式碼，即可建置 Power BI 應用程式，並將應用程式部署至所有 Power BI 客戶。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
ms.openlocfilehash: 0ea8f19fa36bf1f9ceb5f8f0b92bd53ebdfa2a01
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578519"
---
# <a name="what-are-power-bi-template-apps-preview"></a>什麼是 Power BI 範本應用程式？ (預覽)

新的 Power BI「範本應用程式」  讓 Power BI 合作夥伴撰寫少量程式碼或不用撰寫程式碼，即可建置 Power BI 應用程式，再將應用程式部署至所有 Power BI 客戶。  本文為 Power BI 範本應用程式的概觀。

範本應用程式取代目前的服務內容套件。 身為 Power BI 合作夥伴，您可以為客戶建立一組現成可用的內容並親自發佈。  

您可以建置範本應用程式，讓客戶透過自己的帳戶連線並具現化。 身為網域專家，他們可將資料解除鎖定，讓其商務使用者都能輕鬆使用。  

您送出至 Cloud Partner 入口網站應用程式範本。 然後該應用程式會在 Power BI 應用程式庫 (app.powerbi.com/getdata/services) 中和 Microsoft AppSource (appsource.microsoft.com) 上公開推出。 以下是公用的範本應用程式建立體驗高階介紹。  

## <a name="process"></a>程序
開發並提交範本應用程式的一般程序牽涉到數個階段。 某些階段可以併入多個活動，在相同的時間。


| 階段 | Power BI Desktop |  |Power BI 服務  |  |Cloud Partner 入口網站  |
|---|--------|--|---------|---------|---------|
| **One** | 以 .pbix 檔案建置資料模型及報表 |  | 建立工作區。 匯入 .pbix 檔案。 建立互補儀表板  |  | 註冊為合作夥伴 |
| **Two** |  |  | 建立測試套件並執行內部驗證        |  | |
| **Three** | |  | 將測試套件升至生產階段前，以在您的 Power BI 租用戶外進行驗證，並提交至 AppSource  |  | 使用您的生產階段前套件，建立 Power BI 範本應用程式供應項目並啟動驗證程序 |
| **Four** | |  | 將生產階段前套件升至生產階段 |  | 正式運作 |

## <a name="requirements"></a>需求

若要建立範本應用程式，您需有建立權限。 如需詳細資料，請參閱 Power BI 管理入口網站、範本應用程式設定。 

若要將範本應用程式發佈至 Power BI 服務及 AppSource，您必須符合[成為雲端市集發行者](https://docs.microsoft.com/azure/marketplace/become-publisher)的需求。
 
## <a name="high-level-steps"></a>高階步驟

以下為高階步驟。 

1. [參閱需求](#requirements)確認您符合需求。 

1. 在 Power BI Desktop 中建置報表。 使用參數，以便將其儲存為他人可用的檔案。 

1. 為您 Power BI 服務 (app.powerbi.com) 上租用戶中的範本應用程式建立工作區。 

1. 匯入您的 .pbix 檔案，並將儀表板等內容新增至您的應用程式。 

1. 建立測試套件，以在您的組織內親自測試範本應用程式。 

1. 將測試應用程式升至生產階段前，以提交該應用程式至 AppSource 進行驗證，以及在您自己的租用戶外測試。 

1. 將內容提交至雲端合作夥伴平台以發佈。 

1. 讓您的供應項目在 AppSource 中「正式運作」，並在 Power BI 中將應用程式移至生產階段。
2. 現在您可以在生產階段前，於相同工作區開始開發下一個版本。 

## <a name="requirements"></a>需求

若要建立範本應用程式，您需有建立權限。 如需詳細資料，請參閱 Power BI [管理入口網站、範本應用程式設定](service-admin-portal.md#template-apps-settings-preview)。 

若要將範本應用程式發佈至 Power BI 服務及 AppSource，您必須符合[成為雲端市集發行者](https://docs.microsoft.com/azure/marketplace/become-publisher)的需求。

## <a name="tips"></a>祕訣 

- 確認您的應用程式包含範例資料，讓所有人按一下即可開始使用。 
- 藉由將應用程式安裝在您的租用戶及次要租用戶中，來仔細檢查您的應用程式。 確認客戶只會看到您要他們看到的項目。 
- 將 AppSource 用作代管您應用程式的線上市集。 如此一來，所有使用 Power BI 的人員都可以找到您的應用程式。 
- 考慮針對個別特殊情況提供多個範本應用程式。 
- 啟用資料自訂，例如支援透過安裝程式設定自訂連線及參數。

如需更多建議，請參閱[在 Power BI 中撰寫範本應用程式的提示 (預覽)](service-template-apps-tips.md)。

## <a name="support"></a>支援
如需在開發期間的支援，請使用 [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support)。 我們會主動監視及管理這個網站。 讓適當的小組可快速開始處理客戶事件。

## <a name="next-steps"></a>後續步驟

[建立範本應用程式](service-template-apps-create.md)