---
title: Power BI 的自訂視覺效果
description: Power BI 中的自訂視覺效果
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 3fd2f3e47c9b6dd2144ed5a66d45e65a00c5b92e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051245"
---
# <a name="custom-visuals-in-power-bi"></a>Power BI 的自訂視覺效果

當建立或編輯在 Power BI 報表時，您可以使用許多不同類型的視覺效果。 這些視覺效果的圖示會出現在**視覺效果**窗格。 當您下載預先包裝這些視覺效果，隨附[Power BI Desktop](https://powerbi.microsoft.com/desktop/)或開啟[Power BI 服務](https://app.powerbi.com)。

![視覺效果](media/power-bi-custom-visuals/power-bi-visualizations.png)

不過，不限於這組視覺效果。 如果您選取底部的省略符號 （...），另一個來源的報表視覺效果會變成使用-*自訂視覺效果*。

開發人員建立使用自訂的視覺效果 SDK 的自訂視覺效果。 這些視覺效果可讓商務使用者，以查看其資料，以最符合其業務的方式。 報表作者接著可以自訂的視覺效果檔案匯入其報表，並使用它們，如同任何其他 Power BI 視覺效果。 自訂視覺效果是 Power BI 中的第一級公民，並可篩選、 反白顯示、 編輯、 共用、 和等。

自訂視覺效果會部署下列三種方法：

* 自訂視覺效果檔案
* 組織視覺效果
* Marketplace 視覺效果

## <a name="custom-visual-files"></a>自訂視覺效果檔案

自訂視覺效果是封裝，包括程式碼轉譯提供給他們的資料。 任何人都可以建立自訂視覺效果並將其封裝成單一`.pbiviz`檔案，可以再匯入至 Power BI 報表。

> [!WARNING]
> 自訂視覺效果可能包含具有安全性或隱私權風險的程式碼。 請確定您信任作者及自訂 visual 來源之前將它匯入您的報表。

## <a name="organizational-visuals"></a>組織視覺效果

Power BI 系統管理員核准，並將自訂視覺效果部署到組織，而報表作者可以輕鬆地探索、 更新，請使用。 系統管理員可以輕鬆地管理 （例如，更新版本、 停用/啟用） 這些視覺效果。

 [深入了解組織視覺效果](power-bi-custom-visuals-organization.md)。

## <a name="marketplace-visuals"></a>Marketplace 視覺效果

社群成員和 Microsoft 已提供其公用權益的自訂視覺效果並發佈他們[AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) marketplace。 您可以下載這些視覺效果將它們新增至您的 Power BI 報表。 Microsoft 已測試並核准這些自訂的視覺效果的功能與品質。

什麼是 [AppSource](developer/office-store.md)？ 這是您可以找到您的 Microsoft 軟體應用程式、 增益集和延伸模組的位置。 [AppSource](https://appsource.microsoft.com/)連接數百萬位使用者的產品，如同 Office 365、 Azure、 Dynamics 365、 Cortana 和 Power BI，到解決方案，協助他們開始更有效地、 通透，完成工作又美觀的方式比以前。

### <a name="certified-visuals"></a>認證的視覺效果

Power BI 認證的視覺效果都是已通過額外嚴格品質測試，並在其他情況下，例如支援的 marketplace 視覺效果[電子郵件訂閱](https://docs.microsoft.com/power-bi/service-report-subscribe)，和[匯出至 PowerPoint](https://docs.microsoft.com/power-bi/service-publish-to-powerpoint).
若要查看已認證的自訂視覺效果清單，或提交您自己的視覺效果，請參閱[已認證的自訂視覺效果](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified)。

您是否為 Web 開發人員，而且有興趣將自己建立的視覺效果發佈到 AppSource 呢？ 請參閱[開發 Power BI 自訂視覺效果](developer/custom-visual-develop-tutorial.md)，並了解如何[AppSource 上發佈自訂視覺效果](https://docs.microsoft.com/power-bi/developer/office-store)。

### <a name="import-a-custom-visual-from-a-file"></a>從檔案匯入自訂視覺效果

1. 從底部選取省略符號**視覺效果**窗格。

    ![visualizations2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. 在下拉式清單中，選取 [從檔案匯入]  。

    ![從檔案匯入](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. 從 [開啟檔案] 功能表中，選取`.pbiviz`檔案，您想要匯入，然後選取**開啟**。 自訂視覺效果的圖示新增至底部您**視覺效果**窗格中，且現在可在報表中使用。

    ![已匯入 cv](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>匯入組織視覺效果

1. 從底部選取省略符號**視覺效果**窗格。

    ![視覺效果組織 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. 在下拉式清單中，選取 [從 Marketplace 匯入]  。

    ![視覺效果組織 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. 選取頂端索引標籤功能表中的 [我的組織]  。

    ![視覺效果組織 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. 捲動清單，尋找要匯入的視覺效果。

    ![視覺效果組織 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. 選取 **新增**匯入自訂視覺效果。 它的圖示新增至底部您**視覺效果**窗格中，且現在可在報表中使用。

    ![視覺效果組織 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>從 Microsoft AppSource 下載或匯入自訂視覺效果

您已下載和匯入自訂視覺效果的兩個選項： 從 Power BI 中進出[AppSource 網站](https://appsource.microsoft.com/)。

### <a name="import-custom-visuals-from-within-power-bi"></a>從 Power BI 匯入自訂視覺效果

1. 從底部選取省略符號**視覺效果**窗格。

    ![視覺效果 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. 在下拉式清單中，選取 [從 Marketplace 匯入]  。

    ![視覺效果組織 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. 捲動清單，尋找要匯入的視覺效果。

    ![匯入視覺效果](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. 若要深入了解其中一個視覺效果，請加以反白並選取。

    ![選取](media/power-bi-custom-visuals/power-bi-select.png)

5. 您可以在詳細資料頁面上檢視螢幕擷取畫面、影片、詳細的描述等等。

    ![Synoptic](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. 捲動至底部即可看到評論。

    ![評論](media/power-bi-custom-visuals/power-bi-reviews.png)

7. 選取 **新增**匯入自訂視覺效果。 它的圖示新增至底部您**視覺效果**窗格中，且現在可在報表中使用。

    ![已匯入視覺效果](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>從 Microsoft AppSource 下載並匯入自訂視覺效果

1. 請先前往 [Microsoft AppSource](https://appsource.microsoft.com) 並選取 [應用程式]  索引標籤。

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. 前往[應用程式結果頁面](https://appsource.microsoft.com/marketplace/apps)，您可在其中檢視各種類別的熱門應用程式，包括 *Power BI 應用程式*。 自訂視覺效果，讓我們選取想要尋求**Power BI 視覺效果**從左側瀏覽清單來縮小結果。

    ![AppSource 視覺效果](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. AppSource 會顯示每個自訂視覺效果的磚。  每個磚都有自訂的視覺化快照集的簡短描述與下載連結。 若要查看更多詳細資訊，請選取磚。

    ![自訂選取視覺效果](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. 您可以在詳細資料頁面上檢視螢幕擷取畫面、影片、詳細的描述等等。 選取 **立即取得**下載自訂視覺效果並然後同意使用條款。

    ![AppSource 取得](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. 選取連結以下載自訂視覺效果。

    ![下載](media/power-bi-custom-visuals/powerbi-custom-download.png)

    下載頁面也包含如何將 Power BI Desktop 和 Power BI 服務中匯入自訂視覺效果上的指示。

    您也可以下載範例報表，包括自訂視覺效果及其功能的展示。

    ![試用範例](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. 儲存`.pbiviz`檔案，然後開啟 Power BI。

7. 匯入`.pbiviz`檔案到您的報表。 (請參閱上面的[從檔案匯入自訂視覺效果](#import-a-custom-visual-from-a-file)一節。)

## <a name="considerations-and-limitations"></a>考量與限制

* 自訂視覺效果在匯入後會加入特定的報表。 如果想在另一份報表中使用這個視覺效果，也必須將它匯入該報表。 使用 [另存新檔]  選項儲存具有自訂視覺效果的報表時，自訂視覺效果的複本就會與新報表一起儲存。

* 如果您沒有看到**視覺效果** 窗格中，這表示您沒有編輯權限的報表。  您只能在您可編輯的報表中新增自訂視覺效果，而在與您共用的報表中則不能。

## <a name="troubleshoot"></a>疑難排解

若要疑難排解，請參閱[疑難排解您的 Power BI 自訂視覺效果](power-bi-custom-visuals-troubleshoot.md)。

## <a name="faq"></a>常見問題集

如需詳細資訊和問題的解答，請前往 [Power BI 自訂視覺效果的常見問題集](power-bi-custom-visuals-faq.md#organizational-custom-visuals)。

## <a name="next-steps"></a>後續步驟

* [在 Power BI 報表中的視覺效果](visuals/power-bi-report-visualizations.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)。
