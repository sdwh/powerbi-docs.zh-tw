---
title: Power BI 服務中的設計工具基本概念
description: Power BI 服務工作區、儀表板、報告、資料集和活頁簿。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/18/2018
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 487a67f48913ee774904377956eee85ccbae49fc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296677"
---
# <a name="basic-concepts-for-designers-in-the-power-bi-service"></a>Power BI 服務中的設計工具基本概念

本文假設您已經[註冊 Power BI 服務](service-self-service-signup-for-power-bi.md)並已[新增一些資料](service-get-data.md)。 如果您還沒有任何資料，請嘗試安裝 [Power BI 範例內容套件](sample-datasets.md#the-power-bi-samples-as-content-packs)。

![瀏覽器中的 Power BI 服務首頁畫面](media/service-basic-concepts/power-bi-home-screen.png)

以下是當您在瀏覽器中開啟 Power BI 服務時，您會看到的項目：

1. 瀏覽窗格 (左導覽列)
2. Office 365 應用程式啟動器
3. Power BI 首頁按鈕
4. 圖示按鈕，包括設定、說明與意見反應
5. 搜尋方塊
6. 我的最愛儀表板磚
7. 我的最愛與常用儀表板和報表

我們稍後會深入探討這些功能，不過首先來看 Power BI 的一些概念。

或者，您也可以先觀賞這段影片，再閱讀這篇文章的其餘部分。  在影片中，Will 會檢閱基本概念，並介紹 Power BI 服務。

<iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>


## <a name="power-bi-concepts"></a>Power BI 概念
Power BI 有 4 個主要的建置組塊： **_儀表板_** 、 **_報表_** 、 **_活頁簿_** 及 **_資料集_** 。 而且其會全部整理到 **_工作區_** 中。 在我們深入探討四個建置組塊之前，請務必先了解工作區，因此讓我們先從這裡開始。

## <a name="workspaces"></a>工作區
工作區是 Power BI 中儀表板、報告、活頁簿和資料集的容器。 有兩種類型的工作區：「我的工作區」和「應用程式工作區」。 所以，何謂「應用程式」？ Power BI 應用程式是為了提供重要計量給組織而建立的一組儀表板和報告。 應用程式皆為互動式，但無法編輯。

- [我的工作區] 是可供任何 Power BI 客戶處理自己的內容的個人工作區。 只有您可以存取您的 [我的工作區]。 您可以從 [我的工作區] 共用儀表板和報表。 如果您想要在儀表板和報表上共同作業，或是建立應用程式，則應在應用程式工作區中工作。      
-  [應用程式工作區] 用於共同作業並與同事共用內容。 它們也是您為組織建立、發佈及管理應用程式的地方。 將它們視為將構成 Power BI 應用程式之內容的暫存區域與容器。 您可以將同事新增至您的應用程式工作區，以及在儀表板、報告、活頁簿和資料集上共同作業。 所有應用程式工作區成員都需要 Power BI Pro 授權，但應用程式取用者 (可以存取應用程式的同事) 不一定需要 Pro 授權。  

若要深入了解，請參閱目錄的 [分享您的成果] 區段 (從[如何共同作業及共用儀表板和報告](service-how-to-collaborate-distribute-dashboards-reports.md)開始)


現在，進入 Power BI 建置組塊。 儀表板或報表不能沒有資料 (確實可以有空白儀表板與空白報表，但如果當中沒有資料並沒有幫助)，因此讓我們先從 **資料集**開始。

## <a name="datasets"></a>資料集
「資料集」是您要在其中「匯入」或「連線」的資料集合。 Power BI 可讓您連接和匯入各式各樣的資料集，並將所有資料整合到一個位置。  

資料集與「工作區」相關聯，而單一資料集可以是許多工作區的一部分。 當您開啟工作區時，相關聯的資料集會列在 [資料集] 索引標籤之下。每個列出的資料集代表單一來源的資料，例如 OneDrive 上的 Excel 活頁簿、內部部署的 SSAS 表格式資料集，或 Salesforce 資料集。 其支援許多不同的資料來源，同時我們會不停加入新的資料來源。 [查看可搭配 Power BI 使用的資料集類型清單](service-get-data.md).

在下列範例中，我已選取「銷售與行銷」應用程式工作區，並按下了 [資料集] 的索引標籤。

![選取資料集](media/service-basic-concepts/power-bi-datasets.png)

**一個** 資料集...

* 可以在一或多個工作區中反覆使用。
* 可以用在許多不同的報表中。
* 可在許多不同的儀表板中顯示該單一資料集的視覺效果。

  ![資料集圖表](media/service-basic-concepts/drawing2.png)

若要[連線到或匯入資料集](service-get-data.md)，請選取左導覽列底部的 [取得資料]，或選取右上角的 [建立 > 資料集]。 請遵循指示來連線到或匯入特定來源，並將資料集新增至作用中的工作區。 新的資料集會以黃色星號標示。 您在 Power BI 中執行的工作不會變更基礎資料集。

如果您[屬於一個 **_應用程式工作區_** ](service-collaborate-power-bi-workspace.md)，則其他工作區成員可以使用由其中一位工作區成員所新增的資料集。

您可以重新整理、重新命名、瀏覽及移除資料集。 使用資料集從頭開始建立報告，或執行[快速深入解析](service-insights.md)。  若要查看哪些報告和儀表板已經使用資料集，請選取 [檢視相關的]。 若要瀏覽資料集，請選取該資料集。 您實際上會在報表編輯器中開啟資料集，您可以在編輯器中開始挖掘資料並建立視覺效果。 因此，讓我們前進到下一個主題 - 報表。

### <a name="dig-deeper"></a>深入瞭解
* [什麼是 Power BI Premium？](service-premium.md)
* [取得 Power BI 的資料](service-get-data.md)
* [Power BI 的範例資料集](sample-datasets.md)

## <a name="reports"></a>報表
Power BI 報表是一或多個頁面的視覺效果，例如折線圖、地圖及矩形式樹狀結構圖。 Virtualization 和 **_Visual_** 都是指視覺效果。 報表中的所有視覺效果都是來自單一資料集。 報表可以在 Power BI 從頭開始建立、可以透過同事與您共用的儀表板匯入，也可以在您從 Excel、Power BI Desktop、資料庫、SaaS 應用程式和[應用程式](service-get-data.md)連線到資料集時建立。  例如，當您連接到包含 Power View 工作表的 Excel 活頁簿時，Power BI 會根據這些工作表建立報表。 而當您連接至 SaaS 應用程式時，Power BI 則會匯入預先建立的報表。

有兩種模式可以檢視報表並與其互動：[[閱讀] 檢視和 [編輯] 檢視](service-reading-view-and-editing-view.md)。  只有建立報表的人、共同擁有者及經授與權限之人，可以使用該報表中 [編輯] 檢視的探索、設計、建置及共用功能。 與他們一起共用報表的人，可以在 [閱讀] 檢視中探索報表以及與報表互動。   

當您開啟工作區時，相關聯的報告會列在 [報告] 索引標籤之下。每個列出的報告只會根據一個基礎資料集，呈現一或多個頁面的視覺效果。 若要開啟報表，請選取該報表。

當您開啟應用程式時，您會看到儀表板。  若要存取基礎報表，請選取從報表釘選的儀表板磚 (稍後將詳細說明磚)。 請注意，並非所有圖格都是從報告釘選，所以您可能必須按一下幾個圖格來尋找報告。

根據預設，報告會在 [閱讀檢視] 中開啟。  請直接選取 [編輯報告]，在 [編輯檢視] 中開啟報告 (如果您有必要權限)。

在下列範例中，我已選取「銷售與行銷」應用程式工作區，並按下了 [報告] 的索引標籤。

![選取報表](media/service-basic-concepts/power-bi-reports.png)

**一個** 報表...

* 包含在單一工作區中。
* 可以與該工作區內的多個儀表板相關聯 (從該單一報告釘選的圖格可出現在多個儀表板上)。
* 可使用一個資料集的資料建立而成。 (有一點稍微例外，就是 Power BI Desktop 可以將多個資料集合併成單一報表，且該報表可匯入至 Power BI。)

  ![報表圖表](media/service-basic-concepts/drawing3new.png)

### <a name="dig-deeper"></a>深入瞭解
* [Power BI 服務和 Power BI Desktop 中的報告](service-reports.md)
* [Power BI 行動裝置應用程式中的報告](mobile-reports-in-the-mobile-apps.md)

## <a name="dashboards"></a>儀表板
「儀表板」是您在 **Power BI 服務**中所建立，或由同事在 **Power BI 服務**中建立並與您共用的東西。 其為含有零或多個磚與 Widget 的單一畫布。 從報告或從[問與答](power-bi-q-and-a.md)釘選的每個圖格會顯示從資料集建立並釘選到儀表板的單一[視覺效果](power-bi-report-visualizations.md)。 整個報告頁面也可以當作單一圖格釘選到儀表板。 有許多方法可將磚加入儀表板中；本概觀主題無法全部涵蓋。 若要深入了解，請參閱 [Power BI 的儀表板磚](service-dashboard-tiles.md).

為何要建立儀表板？  以下只是部分原因：

* 所有必要的資訊一目了然，以利做出決策。
* 監視最重要的業務相關資訊。
* 確保所有同事都在相同的頁面上，並檢視與使用相同資訊。
* 監視企業、產品、業務單位或行銷活動等的狀況
* 建立較大型儀表板的個人化檢視 -- 放入所有重要的計量。

當您開啟工作區時，相關聯的儀表板會列在 [儀表板] 索引標籤之下。若要開啟儀表板，請選取該儀表板。 當您開啟應用程式時，您會看到儀表板。  每個儀表板表示基礎資料集其中一部分子集的自訂檢視。  如果您擁有儀表板，您也會有基礎資料集和報告的編輯存取權。  如果與您共用儀表板，您將能夠與儀表板和任何基礎報告互動，但是無法儲存任何變更。

您或同事有許多不同的方式可以[共用儀表板](service-share-dashboards.md)。 需要 Power BI Pro 才能共用儀表板以及檢視共用的儀表板。

**一個** 儀表板...

* 與單一工作區相關聯
* 可顯示許多不同資料集的視覺效果
* 可顯示許多不同報表的視覺效果
* 可以顯示從其他工具 (例如 Excel) 釘選的視覺效果

  ![選取儀表板](media/service-basic-concepts/drawing1.png)

### <a name="dig-deeper"></a>深入瞭解
* [建立新的空白儀表板，然後取得一些資料](service-dashboard-create.md)。
* [複製儀表板](service-dashboard-copy.md)
* [建立儀表板的手機檢視](service-create-dashboard-mobile-phone-view.md)


## <a name="workbooks"></a>活頁簿
活頁簿是一種特殊的資料集。 如果您已閱讀 [資料集] 一節，您幾乎知道您需要了解活頁簿的一切。 但您可能想知道為什麼有時 Power BI 會將 Excel 活頁簿歸類為 [資料集]，而有時又會歸類為 [活頁簿]。

當您將 [取得資料] 用於 Excel 檔案時，您可以選擇 [匯入] 或 [連線] 到檔案。 當您選擇 [連線] 時，您的活頁簿會顯示在 Power BI 中，就像是在 Excel Online 中一樣。 但不同於 Excel Online，您有一些很棒的功能，可協助您將工作表中的項目釘選到儀表板。

您無法在 Power BI 中編輯活頁簿。 但如果您需要進行一些變更，您可以按一下 [編輯]，然後選擇在 Excel Online 中編輯活頁簿，或在電腦上以 Excel 開啟活頁簿。 您所做的任何變更都會儲存到 OneDrive 上的活頁簿。

### <a name="dig-deeper"></a>深入瞭解
* [從 Excel 活頁簿檔案取得資料](service-excel-workbook-files.md)
* [從 Excel 發佈至 Power BI](service-publish-from-excel.md)


## <a name="a-dashboard-in-my-workspace"></a>[我的工作區] 中的儀表板
我們已涵蓋工作區和建置組塊。 讓我們將它合在一起，並檢閱構成 Power BI 服務儀表板體驗的各部分。

![瀏覽器中的 Power BI 服務](media/service-basic-concepts/completenewest.png)

### <a name="1-navigation-pane-left-nav"></a>1.**瀏覽窗格** (左導覽列)
使用瀏覽窗格在您的工作區與 Power BI 建置組塊 (儀表板、報告、活頁簿和資料集) 之間尋找及移動。  

  ![[瀏覽] 窗格](media/service-basic-concepts/power-bi-navigation.png)

* 選取 [取得資料]，[將資料集、報表和儀表板新增至 Power BI](service-get-data.md)。
* 使用此圖示展開及摺疊瀏覽窗格 ![瀏覽窗格圖示](media/service-basic-concepts/expand-icon.png).
* 選取 [我的最愛] 以開啟或管理您最愛的內容。
* 選取 [最近] 以檢視和開啟您最近瀏覽過的內容
* 選取 [應用程式] 以檢視、開啟或刪除應用程式。
* 有同事與您共用內容嗎？ 選取 [與我共用] 來搜尋和排序該內容，以尋找您所需的內容。
* 選取 [工作區] 以顯示並開啟您的工作區。

按一下這些項目：

* 圖示或標題，以在內容檢視中開啟
* 向右箭號 (>)，以開啟 [我的最愛]、[最近] 和 [工作區] 的功能表飛出視窗。
* ＞形箭號圖示，以顯示 [我的工作區] 儀表板、報告、活頁簿和資料集的可捲動清單。

### <a name="2-canvas"></a>2.**畫布**
由於我們已開啟儀表板，所以畫布區域會顯示視覺效果圖格。 例如，如果我們已開啟報表編輯器，則畫布區域會顯示報表頁面。

儀表板是由[磚](service-dashboard-tiles.md)所組成。  圖格可在報告的 [編輯檢視]、[問與答]、其他儀表板中建立，而且可以從 Excel、SSRS 等項目釘選。 一種稱為 [Widget](service-dashboard-add-widget.md) 的特殊磚類型會直接加入儀表板中。 出現在儀表板上的圖格，為報表建立者/擁有者特別放置於此的。  將圖格加入儀表板中的動作稱為「釘選」 。

![Power BI 儀表板畫布](media/service-basic-concepts/canvas.png)

如需詳細資訊，請參閱 [[儀表板]](#dashboards)\(請見上方)。

### <a name="3-qa-question-box"></a>3.**問與答的問題方塊**
瀏覽資料的方式之一為提問，讓 Power BI 問與答以視覺效果的形式為您解答。 [問與答] 可以用來將內容新增至儀表板或報告。

問與答會在連接到儀表板的資料集中尋找答案。  連接的資料集是指具有至少一個圖格釘選至該儀表板的資料集。

![問與答的問題方塊](media/service-basic-concepts/power-bi-qna.png)

一旦您開始輸入問題，問與答就會帶您前往問與答的頁面。 您在輸入時，問與答會以修改措辭、自動填入、建議及更多方式，協助您詢問適當的問題並找尋最佳解答。 如果有您喜歡的視覺效果 (解答)，請予以釘選到您的儀表板中。 如需詳細資訊，請參閱 [Power BI 中的問與答](power-bi-q-and-a.md)。

### <a name="4-icon-buttons"></a>4.**圖示按鈕**
右上角的圖示為您的資源，可供您設定、通知、下載、取得說明，並將意見反應提供給 Power BI 小組。 選取雙箭頭以 [全螢幕] 模式開啟儀表板。  

![圖示按鈕](media/service-basic-concepts/power-bi-icons.png)

### <a name="5-dashboard-title-navigation-path-aka-breadcrumbs"></a>5.**儀表板標題** (導覽路徑，也稱為階層連結)
您不一定能輕鬆地指出哪個工作區和儀表板為作用中，因此 Power BI 會為您建立導覽路徑。  在此範例中，我們看到工作區 (我的工作區) 和儀表板標題 (零售分析範例)。  如果我們開啟了報告，則報告的名稱會附加至導覽路徑的結尾。  路徑的每個部分都是作用中的超連結。  

請注意儀表板標題之後的 "C" 圖示。 此儀表板具有「機密」[資料分類標籤](service-data-classification.md)。 此標籤可識別資料的敏感性和安全性層級。 如果您的系統管理員已開啟資料分類，則每個儀表板將會設定一個預設標籤。 儀表板擁有者應變更此標籤，以符合其儀表板的適當安全性層級。

![資料分類圖示](media/service-basic-concepts/power-bi-title.png)

### <a name="6-office-365-app-launcher"></a>6.**Office 365 應用程式啟動器**
透過應用程式啟動器，按一下即可輕鬆取得所有的 Office 365 應用程式。 您可以從這裡快速地啟動您的電子郵件、文件、行事曆等等。

![Office 應用程式啟動器](media/service-basic-concepts/power-bi-waffle.png)

### <a name="7-power-bi-home"></a>7.**Power BI 首頁**
選取 [Power BI] 將帶您回到 Power BI 首頁。

   ![服務中的「Power BI」](media/service-basic-concepts/version-new.png)

### <a name="8-labeled-icon-buttons"></a>8.**加上標籤的圖示按鈕**
螢幕的這個區域包含與內容互動 (在此例中，與儀表板互動) 的其他選項。  除了您可以看到之加上標籤的圖示，選取省略符號可顯示用於複製、列印、重新整理儀表板等選項。

   ![加上標籤的圖示按鈕](media/service-basic-concepts/power-bi-labeled-icons.png)

## <a name="next-steps"></a>後續步驟
- [Power BI 是什麼？](power-bi-overview.md)  
- [導覽：瀏覽 Power BI 服務](service-the-new-power-bi-experience.md)
- [Power BI 影片](videos.md)  
- [報告編輯器.-.進行導覽](service-the-report-editor-take-a-tour.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
