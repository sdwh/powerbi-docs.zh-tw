---
title: "與同事和其他人共用儀表板 - Power BI"
description: "如何與組織內外的同事共用 Power BI 儀表板，以及需要了解的共用相關資訊。"
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
featuredvideoid: 0tUwn8DHo3s
qualityfocus: monitoring
qualitydate: 08/14/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: maggies
ms.openlocfilehash: 9c88c70de013679ea27faae17a3672c0d172b2a9
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="share-your-power-bi-dashboards-with-coworkers-and-others"></a>與同事和其他人共用 Power BI 儀表板
「共用」是讓一些人存取您儀表板和報表的一種好方法。 Power BI 提供[數種方式可進行共同作業以及散發您的儀表板](service-how-to-collaborate-distribute-dashboards-reports.md)，而共用只是其中的一種功能。

![儀表板清單中的共用圖示](media/service-share-dashboards/power-bi-share-dash.png)

若要共用，無論您是在組織內部或外部共用內容，您和您的收件者都必須具有 [Power BI Pro 授權](service-free-vs-pro.md)，或內容必須位於[進階容量](service-premium.md)中。 有任何建議嗎？ Power BI 小組向來重視您的意見反應，請前往 [Power BI 社群網站](https://community.powerbi.com/)。

您可以從您自己的 [我的工作區] 或應用程式工作區共用儀表板。 當您與他人共用儀表板時，他們可以檢視和互動，但是無法對其編輯。 除非套用[資料列層級安全性 (RLS)](service-admin-rls.md)，否則他們會看到您在儀表板和報表中看到的相同資料。 如果您允許的話，您與其共用的同事可以與他們的同事共用儀表板。 組織外部人員也可以檢視儀表板並與之互動，但不能共用儀表板。 

您也可以[從任何 Power BI 行動裝置應用程式共用儀表板](mobile-share-dashboard-from-the-mobile-apps.md)。 您可以從 Power BI 服務和 Power BI 行動裝置應用程式共用儀表板，但無法從 Power BI Desktop 共用。

## <a name="video-share-a-dashboard"></a>影片：共用儀表板
觀看 Amanda 與她公司內外的同事共用儀表板。 然後遵循影片下方的逐步指示親自試試看。

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard"></a>共用儀表板
1. 在 [我的工作區] 或應用程式工作區中，開啟儀表板，然後選取 [共用] ![共用圖示](media/service-share-dashboards/power-bi-share-icon.png)。
2. 在頂端的方塊中，輸入個人、通訊群組或安全性群組的完整電子郵件地址。 您無法共用動態通訊清單。 
   
   您可以與其位址在您組織外的人員共用，但是您會看到一則警告。
   
   ![外部共用的相關警告](media/service-share-dashboards/power-bi-share-dialog-warning.png)  
3. 您可以視需要新增訊息。 這是選擇性的。
4. 若要讓同事將您的儀表板再次與他人共用，請核取 [允許收件者共用您的儀表板]。
   
   允許其他人共用稱為「再次共用」。 如果您允許的話，他們就可以從 Power BI 服務和行動裝置應用程式再次共用，或將電子郵件邀請轉寄給組織中的其他人。 邀請有效期一個月。 組織外部人員無法再次共用。 身為儀表板的擁有者，您可以關閉再次共用，或個別撤銷再次共用。請參閱以下的[停止共用儀表板或停止其他人共用](service-share-dashboards.md#stop-sharing-a-dashboard-or-stop-others-from-sharing)。
5. 選取 [共用]。
   
   ![選取 [共用] 按鈕](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI 會將電子郵件邀請傳送給個人而非群組，其中會有此共用儀表板的連結，您會看到**成功**通知。 
   
   當組織內的收件者按一下連結時，Power BI 會將儀表板新增至其 [與我共用] 清單頁面。 他們可以選取您的名稱，就能查看您已共用的所有儀表板。 
   
   ![[與我共用] 清單頁面](media/service-share-dashboards/power-bi-shared-with-me-list-page.png)
   
   當組織外的收件者按一下連結時，他們會看到儀表板，但不是在平常的 Power BI 入口網站中。 如需詳細資料，請參閱以下的[與組織外部人員共用儀表板](service-share-dashboards.md#share-a-dashboard-with-people-outside-your-organization)。

## <a name="who-has-access-to-a-dashboard-i-shared"></a>誰可以存取我共用的儀表板？
有時您需要查看您已共用儀表板的人員，以及這些人已共用儀表板的其他人員。

1. 在儀表板清單或儀表板本身中，選取 [共用] ![共用圖示](media/service-share-dashboards/power-bi-share-icon.png)。 
2. 在 [共用儀表板] 對話方塊中，選取 [存取]。
   
    ![[共用儀表板] 對話方塊的 [存取] 索引標籤](media/service-share-dashboards/power-bi-share-dialog-access.png)
   
    組織外部人員列為 [Guest]。

## <a name="stop-sharing-a-dashboard-or-stop-others-from-sharing"></a>停止共用儀表板或停止其他人共用
只有儀表板擁有者可以開啟和關閉再次共用。

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>如果您尚未傳送共用邀請
* 清除邀請底部的 [允許收件者共用您的儀表板] 核取方塊，再傳送邀請。

### <a name="if-youve-already-shared-the-dashboard"></a>如果您已共用儀表板
1. 在儀表板清單或儀表板本身中，選取 [共用] ![共用圖示](media/service-share-dashboards/power-bi-share-icon.png)。 
2. 在 [共用儀表板] 對話方塊中，選取 [存取]。
   
    ![[共用儀表板] 對話方塊的 [存取] 索引標籤](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. 選取 [讀取並再次共用] 旁的省略符號 (**...**)，然後選取：
   
   ![[讀取並再次共用] 的省略符號](media/service-share-dashboards/power-bi-change-access.png)
   
   * [讀取]，阻止該員與其他人共用。
   * [移除存取權]，使該員完全看不到儀表板。

## <a name="share-a-dashboard-with-people-outside-your-organization"></a>與組織外部人員共用儀表板
與組織外部人員共用時，他們會收到具有共用儀表板連結的電子郵件，而且必須登入 Power BI 才能看到儀表板。 如果沒有 Power BI Pro 授權，他們可以按一下連結來註冊授權。

登入後，就不會在平常的 Power BI 入口網站中，而是在其瀏覽器視窗中看到沒有左瀏覽窗格的共用儀表板。 他們也必須將連結設為書籤，日後才能存取這個儀表板。

他們無法編輯這個儀表板或報表中的任何內容。 他們可以與報告中的圖表互動 (交叉醒目提示)，以及變更連線至儀表板的任何報告上可用的篩選條件/交叉分析篩選器，但無法儲存變更。

只有您的直接收件者才看得到共用儀表板。 例如，如果您傳送電子郵件給 Vicki@contoso.com，只有 Vicki 看得到儀表板。 其他人就算有連結也看不到這個儀表板，而 Vicki 必須使用相同的電子郵件地址才能存取該儀表板。 如果她使用任何其他電子郵件地址登入，亦無法存取儀表板。

如果內部部署的 Analysis Services 表格式模型實作角色或資料列層級安全性，則組織外部人員就完全看不到任何資料。

如果您從 Power BI 行動裝置應用程式傳送連結給組織外部的人員，當這些人按一下連結時，會在瀏覽器中開啟儀表板，而不是在 Power BI 行動裝置應用程式中開啟。

## <a name="limitations-and-considerations"></a>限制與考量
共用儀表板時的重要事項︰

* 一般來說，您和您的同事在儀表板中會看到相同的資料。 因此，如果您的權限看到的資料比他們多，他們就能夠看到您儀表板中所有的資料。 不過，如果[資料列層級安全性 (RLS)](service-admin-rls.md) 已套用至儀表板的基礎資料集，則會使用每個人的認證來決定其可以存取的資料。
* 共用您儀表板的每個人都可以看到此儀表板，並在[閱讀檢視](service-report-open-in-reading-view.md)中與您的報表互動。 他們無法建立報表，或在現有的報表中儲存變更。
* 但沒有人可以看到或下載資料集。
* 每個人都可以手動[重新整理儀表板資料](refresh-data.md)
* 如果電子郵件使用 Office 365，您可以輸入與通訊群組相關聯的電子郵件地址來與通訊群組的成員共用。
* 電子郵件網域與您相同的同事，以及網域不同、但登錄在相同租用戶中的同事，可以與其他人共用儀表板。 例如，假設網域 contoso.com 和 contoso2.com 都登錄在相同的租用戶中。 如果您的電子郵件地址是 konrads@contoso.com，則 ravali@contoso.com 和 gustav@contoso2.com 只要經過您授權共用，就可以共用。
* 如果您的同事已能存取特定的儀表板，您只需要在儀表板中時，複製該儀表板的 URL，就能傳送該儀表板的直接連結。 例如：   
  
    https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx
* 同樣地，如果您的同事已能存取特定的儀表板，您可以[傳送基礎報表的直接連結](service-share-reports.md)。 

## <a name="next-steps"></a>後續步驟
* 有任何意見嗎？ 請移駕 [Power BI 社群網站](https://community.powerbi.com/)提供您的建議。
* [應該如何共同作業和共用儀表板和報表？](service-how-to-collaborate-distribute-dashboards-reports.md)
* [只共用 Power BI 報表](service-share-reports.md)
* 有問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)。

