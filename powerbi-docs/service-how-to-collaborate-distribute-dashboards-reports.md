---
title: "該如何在 Power BI 中共同作業和共用儀表板及報表？"
description: "在 Power BI 中，您可以多種方式來共同作業和共用儀表板、報表和磚。 各有其優點。"
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 02/28/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: maggies
ms.openlocfilehash: 1ee8cc60d5c18cb09915029088824ade89d2b39f
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="how-should-i-collaborate-and-share-dashboards-and-reports-in-power-bi"></a>該如何在 Power BI 中共同作業和共用儀表板及報表？
您建立儀表板和報告。 或許您也透過它們與同事共同作業。 然後，您希望其他人可以存取它們。 散發它們的最佳方式為何？

在本文中，我們將比較 Power BI 內共同作業與共用的選項： 

* 與同事共同作業，以在「應用程式工作區」中建立有意義的報表和儀表板。
* 將這些儀表板和報告結合為「應用程式」，並將它們發佈給較大的群組或您的整個組織。
* 從服務或 Power BI 行動裝置應用程式，與一些人員共用儀表板或報表。
* 發行至網站，任何人都可以查看並與它們互動。
* 列印。 

無論您選擇哪個選項，都必須具有 [Power BI Pro 授權](service-free-vs-pro.md)，或內容必須位於[進階容量](service-premium.md)中，才能共用儀表板。 根據您選擇的選項，檢視您儀表板的同事會有不同的授權需求。 下列各節組說明詳細資料。 有任何建議嗎？ Power BI 小組向來重視您的意見反應，請前往 [Power BI 社群網站](https://community.powerbi.com/)。

![Power BI 服務中的應用程式](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-apps-home-blog.png)

*Power BI 服務中的應用程式*

## <a name="collaborate-with-coworkers-to-create-an-app"></a>與同事共同作業來建立應用程式
假設您和小組成員要將 Power BI 深入資訊發佈到您的組織。 這麼做的最好方式是建立「應用程式」。 應用程式是為了提供重要計量給組織而建立的一組儀表板和報告。 

若要建立應用程式，您需要「應用程式工作區」，並以小組成員作為成員。 請將應用程式工作區視為臨時區域，您能在其中與他們共同作業以處理 Power BI 儀表板和報表。 所有人都可以在 Power BI Desktop 中建立報告，並將這些報告發佈到應用程式工作區，且你們全都需要 Power BI Pro 授權。

![應用程式工作區](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-apps-workspaces.png)

**如果您只想要與同事共用已完成的儀表板，請不要將他們新增至應用程式工作區。** 相反地，請[在應用程式工作區中建立儀表板](service-create-distribute-apps.md)，再將應用程式發佈給他們。 

## <a name="publish-your-app-to-a-broad-audience"></a>將您的應用程式發佈給廣大的群眾
假設您想要將自己的儀表板散發給廣大的群眾。 您和同事已建立「應用程式工作區」，且接著在應用程式工作區中建立並調整儀表板、報表和資料集。 現在您可以選取您想要的儀表板和報表，並將其以應用程式的形式發佈給安全性群組的成員或通訊群組清單，或發佈給整個組織。 

![發佈應用程式圖示](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-app-publish-600.png)

在 Power BI 服務中可以輕鬆地找到並安裝應用程式 ([https://powerbi.com](https://powerbi.com))。 您可以將應用程式的直接連結傳送給商務使用者，或者他們可以在 AppSource 中進行搜尋。 如果您的 Power BI 系統管理員賦予您權限，您可以在您同事的 Power BI 帳戶中自動安裝應用程式。 深入了解如何[發佈您的應用程式](service-create-distribute-apps.md#publish-your-app)。 

當他們安裝應用程式之後，就可以在瀏覽器或行動裝置中檢視此應用程式。

若要讓使用者檢視您的應用程式，他們也必須有 Power BI Pro 授權，否則，應用程式必須儲存在 Power BI Premium 容量中。 如需詳細資訊，請參閱[什麼是 Power BI Premium？](service-premium.md)。

## <a name="share-dashboards-and-reports"></a>共用儀表板和報表
假設您已在自己的 [我的工作區] 或在應用程式工作區中完成儀表板和報表，而且希望其他人可以存取此儀表板或報表。 其中一項存取方法是「共用」它。 

![共用圖示](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-share-in-situ.png)

您和內容的共用對象都必須具有 Power BI Pro 授權，或內容必須位於[進階容量](service-premium.md)中，才能共用內容。 當您共用儀表板或報表時，他們可以檢視此儀表板或報表並與之互動，但是無法編輯此儀表板或報表。 除非資料列層級安全性 (RLS) 套用至基礎資料集，否則他們會看到您在儀表板和報表中看到的相同資料。 如果您允許的話，您與其共用的同事可以與他們的同事共用。 

您也可以與組織外部人員共用。 他們也可以檢視和與儀表板互動，但不能共用儀表板。 

深入了解[從 Power BI 服務共用儀表板](service-share-dashboards.md)。

您也可以[共用報表的直接連結](service-share-reports.md)，並略過儀表板。 您可以對連結新增篩選，讓收件者看到篩選後的報表檢視。

## <a name="annotate-and-share-from-the-power-bi-mobile-apps"></a>從 Power BI 行動裝置應用程式標註並共用
在 iOS 和 Android 裝置的 Power BI 行動裝置應用程式中，您可以標註磚、報表或視覺效果，然後透過電子郵件與任何人共用它。 

![在行動裝置應用程式中標註及共用](media/service-how-to-collaborate-distribute-dashboards-reports/power-bi-iphone-annotate.png)

您會共用磚、報表或視覺效果的快照集，而收件者會看到它與您送出郵件時完全相同的內容。 該郵件還包含儀表板或報告的連結。 如果收件者具有 Power BI Pro 授權，或內容位於[進階容量](service-premium.md)中，而且您已經與收件者共用物件，他們便可加以開啟。 您可以將磚的快照集傳送給任何人，而不只是同一電子郵件網域中的同事而已。

深入了解從 iOS 和 Android 的行動應用程式[標註並共用磚、報表和視覺效果](mobile-annotate-and-share-a-tile-from-the-mobile-apps.md)。

您也可以從 Windows 10 裝置的 Power BI 應用程式[共用磚的快照集](mobile-share-tile-windows-10-phone-app.md)。

## <a name="publish-to-the-web"></a>發行至網站
您可以將 Power BI 報表發行至整個網際網路，方法是在任何裝置上將互動式視覺效果內嵌到部落格文章、網站、社交媒體和其他線上通訊。 網際網路上的任何人都可以檢視您的報表，而且您無法控制誰可以查看您的發行內容。 他們不需要 Power BI 授權。 您只能在可編輯的報表中使用發行至網站。 如果報表是與您共用，或報表是在應用程式中，則您無法將報表發行至網站。 深入了解[發行至網站](service-publish-to-web.md).

## <a name="print-or-save-as-pdf-or-other-static-file"></a>列印或儲存為 PDF 或其他靜態檔案
您可以從 Power BI 服務列印整份儀表板、儀表板磚、報表頁面或視覺效果，或將其儲存為 PDF (或其他靜態檔案格式)。 一次只能列印一頁報表 - 您無法一次列印整份報表。 深入了解[列印或儲存為靜態檔案](service-print.md)。

## <a name="next-steps"></a>後續步驟
* 有任何意見嗎？ 請移駕 [Power BI 社群網站](https://community.powerbi.com/)提供您的建議。
* [與同事和其他人共用儀表板](service-share-dashboards.md)
* [在 Power BI 中建立和發佈應用程式](service-create-distribute-apps.md)
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)。

