---
title: "Power BI 的內嵌功能"
description: "Power BI 提供 API 來將您的儀表板和報表內嵌至應用程式。"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: 36eb4231b6b3d3278d571722bde731051ffdf05e
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="embedding-with-power-bi"></a>Power BI 的內嵌功能
Power BI 提供 API 來將您的儀表板和報表內嵌至應用程式。 Power BI API 在內嵌內容時，提供一組一致的功能以及最新 Power BI 功能的存取權 (例如儀表板、閘道和應用程式工作區)。

## <a name="a-single-api"></a>單一 API
內嵌 Power BI 內容時有兩個主要案例。 對組織進行內嵌，以及對客戶進行內嵌。 這兩個案例都允許使用 Power BI REST API。 這可讓您將儀表板和報告內嵌至您的自訂應用程式，並使用相同的 API 來服務組織或客戶。 您可以針對內嵌需求而完整利用 JavaScript 和 REST API。

若要檢視內嵌運作方式的範例，請參閱 [JavaScript 內嵌範例](https://microsoft.github.io/PowerBI-JavaScript/demo/)。

## <a name="embedding-for-your-organization"></a>對組織進行內嵌
對組織進行內嵌可讓您擴充 Power BI 服務。 當您想要檢視內容時，應用程式的終端使用者就需要登入 Power BI 服務。 您的組織中有人登入之後，他們只能存取 Power BI 服務中已經與他們共用的儀表板和報告。 

對組織進行內嵌的範例包括內部 Web 應用程式、SharePoint Online 網頁組件和 Microsoft Teams 整合。

若要對組織進行內嵌，請參閱下列文章：

* [將儀表板整合到應用程式](integrate-dashboard.md)
* [將磚整合到應用程式](integrate-tile.md)
* [將報表整合到應用程式](integrate-report.md)

針對 Power BI 使用者內嵌時，可透過 [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) 來使用自助功能，例如編輯、儲存等。

## <a name="embedding-for-your-customers"></a>對客戶進行內嵌
對客戶進行內嵌可讓您將儀表板和報表內嵌至沒有 Power BI 帳戶的使用者。 您的客戶完全不需要了解 Power BI。 需要至少一個 Power BI Pro 帳戶。 Power BI Pro 帳戶將成為應用程式的主帳戶。 將這個當作 Proxy 帳戶。 Power BI Pro 帳戶也可讓您產生內嵌權杖，以允許存取 Power BI 服務內的儀表板和報表。 

對客戶進行內嵌的範例包括銷售給其他公司的 ISV 應用程式。

![對客戶進行內嵌的內嵌流程](media/embedding/powerbi-embed-flow.png)

若要內嵌儀表板、報表和磚，您使用的 API 應該與對組織進行內嵌時所用的 API 相同。

> [!IMPORTANT]
> 雖然內嵌相依於 Power BI 服務，但客戶不相依於 Power BI。 他們不需要註冊 Power BI，即可檢視應用程式中的內嵌內容。
> 
> 

當您準備好進入生產環境時，必須將應用程式工作區指派給容量。 Microsoft Azure 中的 Power BI Embedded 提供用於應用程式的容量。

如需有關如何內嵌的詳細資訊，請參閱[如何內嵌 Power BI 儀表板、報告和圖格](embedding-content.md)。

如果您在 Azure 內使用 Power BI 工作區集合服務，請參閱[從 Power BI 工作區集合 Azure 服務移轉內容](migrate-from-powerbi-embedded.md)以取得如何移轉內容的資訊。

## <a name="next-steps"></a>後續步驟
[如何內嵌 Power BI 儀表板、報告和圖格](embedding-content.md)  
[如何將 Power BI Embedded 工作區集合內容移轉至 Power BI](migrate-from-powerbi-embedded.md)  
[何謂 Power BI Premium](../service-premium.md)  
[JavaScript API Git 存放庫](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git 存放庫](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript 內嵌示範](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[內嵌的分析容量規劃白皮書](https://aka.ms/pbiewhitepaper)  
[Power BI Premium 技術白皮書](https://aka.ms/pbipremiumwhitepaper)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

