---
title: Power BI 視覺效果方針
description: 了解如何將自訂視覺效果發佈至 AppSource 供其他人探索及透過購買來使用。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 07/16/2019
ms.openlocfilehash: 71752a635c69e6712befbb00e942189fa4dacc36
ms.sourcegitcommit: e2c5d4561455c3a4806ace85defbc72e4d7573b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327723"
---
# <a name="guidelines-for-power-bi-visuals"></a>Power BI 視覺效果指南
在您將視覺效果[發佈](https://docs.microsoft.com/power-bi/developer/office-store)至 AppSource 供其他人探索及使用之前，請務必遵循指導方針，以便為您的使用者打造絕佳體驗。 

## <a name="context-menu"></a>操作功能表
操作功能表是當使用者將滑鼠停留在視覺效果上時所顯示的右鍵功能表。
所有 Power BI 視覺效果都應該啟用操作功能表，以提供一致的體驗。 請參閱[本文](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md)了解如何新增內容功能表。


## <a name="logo-guidelines"></a>標誌指導方針
> [!NOTE]
> 此文章中的單字標誌指的是下面圖形所示的任何商業公司圖示。 

此節說明在 Power BI 視覺效果中心增標誌的規格。 標誌不是必要的。 如已新增，則必須遵循這些指導方針。 

> [!IMPORTANT]
> 標誌*僅可在編輯模式*中使用。 標誌*無法*在檢視模式中顯示。


![定義](media/guidelines-powerbi-visuals/definitions.png)

![注意事項](media/guidelines-powerbi-visuals/things-to-keep-in-mind.png)

![應避免事項](media/guidelines-powerbi-visuals/things-to-avoid.png)

![大小及格式](media/guidelines-powerbi-visuals/size-and-format.png)

![邊界及大小](media/guidelines-powerbi-visuals/margins-and-sizes.png)

![編輯模式](media/guidelines-powerbi-visuals/logos-in-edit-mode.png)


閱讀模式中的資訊圖示 (如果有的話) 應該符合上面標誌的色彩、大小與位置。

## <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>需要另外購買的 Power BI 視覺效果指導方針

到目前為止，Marketplace (AppSource) 只接受免費的 Power BI 視覺效果。 此原則已變更 (2018 年 12 月)，因此您也可以提交具有「可能需要另外購買」價格標籤的視覺效果到 AppSource。 

「可能需要個別購買」視覺效果類似於 Office 市集中的在應用程式內購買 (IAP) 增益集。 開發人員也可以在經過 AppSource 小組核准，確定符合認證需求之後，再提交這些經認證的視覺效果。 如需有關需求的詳細資訊，請參閱[經認證的 Power BI 視覺效果](../power-bi-custom-visuals-certified.md)。

> [!NOTE]
> 視覺效果不得存取外部服務或資源，才能通過驗證。

>[!IMPORTANT]  
> 若您將視覺效果從免費更新為「可能需要另外購買」，使用者仍一定會收到如更新前的同等級免費功能。 您可以在現有的免費功能之上新增選用進階付費功能。 我們建議將具有進階功能的 IAP 視覺效果作為新視覺效果提交，而不更新現有的免費項目。

## <a name="what-changed-in-the-submission-process"></a>提交程序有何變更？

開發人員會透過賣方儀表板將其 IAP 視覺效果上傳至 AppSource，如同上傳免費的視覺效果。 為了指出提交的視覺效果具有 IAP 功能，開發人員應該在賣方儀表板備註中註明：「需要在應用程式內購買的視覺效果」。 此外，開發人員需要提供授權金鑰或權杖，讓驗證小組可驗證 IAP 功能。 在視覺效果經過驗證及核准之後，IAP 視覺效果的 AppSource 清單會在定價選項下方指出「可能需要個別購買」。

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>什麼是具有 IAP 功能的 Power BI 視覺效果？

IAP 視覺效果是提供*免費功能*的*免費*視覺效果。 它也有一些進階功能，但這些功能可能必須另外付費才能使用。 在視覺效果的描述中，開發人員必須通知使用者需要另行購買才能使用的功能。 目前，Microsoft 不提供原生 API 以支援購買應用程式與增益集。

對於這些購買項目，開發人員可以使用任何第三方付款系統。 如需詳細資訊，請參閱[我們的市集原則](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads) \(英文\)。

> [!NOTE]
> 無法在免費功能或免費視覺效果上使用浮水印。 僅可在不具有效授權情況下使用的付費功能上使用浮水印。 若在不具有效授權的情況下使用付費功能，建議您顯示具有全部授權相關資訊的快顯視窗。  


## <a name="best-practices"></a>最佳作法

### <a name="visual-landing-page"></a>視覺效果登陸頁面

利用登陸頁面向使用者釐清可如何使用您的視覺效果，以及何處可購買授權。 不要包含會自動觸發的影片。 請只新增可協助改善使用者體驗的資料，例如授權購買詳細資料的相關資訊或連結，以及如何使用 IAP 功能。

### <a name="license-key-and-token"></a>授權金鑰和權杖

為了使用者方便起見，請在格式窗格頂端新增授權金鑰或權杖相關欄位。

## <a name="faq"></a>常見問題集

如需有關視覺效果的詳細資訊，請參閱[需要另外購買之視覺效果的常見問題集](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases)。

## <a name="next-steps"></a>後續步驟

了解如何將自訂視覺效果發佈至 [AppSource](office-store.md) 供其他人探索及使用。
