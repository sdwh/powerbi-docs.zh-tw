---
title: Power BI 的 [發行至 Web]
description: 透過 Power BI 的 [發行至 Web]，您可以輕鬆地使用任何裝置，線上內嵌互動式 Power BI 視覺效果，例如內嵌至部落格文章、網站，或透過電子郵件、社交媒體傳送。
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051569"
---
# <a name="publish-to-web-from-power-bi"></a>Power BI 的 [發行至 Web]

使用 Power BI**發佈至網路**選項時，您可以輕鬆地內嵌互動式 Power BI 視覺效果線上，例如，在部落格文章、 網站，透過電子郵件或社交媒體從任何裝置。 您也可以輕鬆編輯、更新、重新整理或取消共用已發佈的視覺效果。

> [!WARNING]
> 當您使用**發佈至網路**，網際網路上的任何人都可以檢視您的已發行的報表或視覺效果。 這不需要驗證，並包括檢視詳細資料層級的資料彙總報表。 發行報表之前，請確定它是為您公開分享資料及視覺效果的 [確定]。 請勿發行機密或專屬資訊。 如有疑問，請先核查貴組織的原則再發行。

>[!Note]
>若要安全地將您的內容內嵌在內部入口網站或網站，請使用[內嵌](service-embed-secure.md)或[內嵌於 SharePoint Online 中](service-embed-report-spo.md)選項。 這可確保當您的使用者檢視您的內部資料時，所有權限與資料安全性都強制受保護。

## <a name="how-to-use-publish-to-web"></a>如何使用 [發佈至網路]

**發佈至網路**適用於您可以編輯您個人或群組工作區中的報表。  無法使用，或依賴資料列層級安全性來保護資料與共用的報表。 請參閱[**限制**](#limitations)如需完整清單的情況下下, 面章節其中**發佈至網路**不受支援。 檢閱**警告**稍早使用之前的這篇文章**發佈至網路**。

下列*短片*顯示這項功能的運作方式。 然後，自行嘗試下列步驟中。

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

下列步驟說明如何使用 [ **發佈至網路**]。

1. 您可以編輯，並選取您工作區中開啟報表**檔案 > 發佈至網路**。

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. 檢閱內容，然後選取 [] 對話方塊**建立內嵌程式碼**。

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. 如此處所示，檢閱警告，並確認資料可以內嵌在公用網站。 如果是，選取**發佈**。

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. 對話方塊隨即出現的連結。 您可以在 電子郵件傳送此連結、 將它內嵌在 iFrame 中，例如程式碼或將它貼到網頁或部落格，直接。

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. 如果您先前建立的報表內嵌程式碼，並選取**發佈至網路**，將不會看到的對話方塊，在步驟 2-4。 相反地，**內嵌程式碼**對話方塊隨即出現：

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   每個報表只能建立一個內嵌程式碼。


## <a name="tips-and-tricks-for-view-modes"></a>檢視模式的秘訣和訣竅

當您內嵌的部落格文章中的內容時，您通常需要符合特定螢幕大小。  您可以調整高度和寬度，以視需要在 iFrame 標籤。 不過，您需要確保報表符合給定的 iFrame 區內，因此您也必須編輯報表時，設定適當的檢視模式。

下表提供檢視模式的相關指南，以及內嵌後的顯示方式。

| 檢視模式 | 內嵌時的外觀 |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**調整成一頁**會尊重您的報表頁面高度與寬度。 如果您將您的頁面設定為 'Dynamic' 的比例，像是 16:9 或 4:3 您的內容會縮放以符合 iFrame 內。 當內嵌在 iFrame 中時，使用**調整成一頁**可能會導致**上下黑邊**其中灰色背景顯示 iFrame 區域內容之後，調整以符合 iFrame 內。 若要上下黑邊降到最低，iFrame 的高度和寬度適當設定。 |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**實際大小**可確保報表維持您在報表頁面上設定其大小。 這會導致 iFrame 中顯示的捲軸。 設定 iFrame 的高度和寬度以避免捲軸。 |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**調整成視窗寬度**可確保內容符合 iFrame 的水平寬度。 框線仍會顯示，但內容調整為使用所有的水平空間可用。 |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>iFrame 高度和寬度的秘訣和訣竅

A**發佈至網路**內嵌程式碼看起來如下所示：

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
您可以編輯以手動方式以確保它正是您要如何放入您要內嵌在其中的頁面高度與寬度。

若要達到更理想，您可以嘗試加入 iFrame 的高度，以配合下方列的目前大小的 56 像素為單位。 如果報表頁面使用動態大小，下表提供一些您可以使用而不會出現上下黑邊的大小。

| 外觀比例 | 大小 | 尺寸 (寬度 x 高度) |
| --- | --- | --- |
| 16:9 |小 |640 x 416 像素 |
| 16:9 |中 |800 x 506 像素 |
| 16:9 |大 |960 x 596 像素 |
| 4:3 |小 |640 x 536 像素 |
| 4:3 |中 |800 x 656 像素 |
| 4:3 |大 |960 x 776 像素 |

## <a name="manage-embed-codes"></a>管理內嵌程式碼

一旦您建立**發佈至網路**內嵌程式碼，您可以管理您的程式碼，從**設定**Power BI 中的功能表。 管理內嵌程式碼的工作包括能夠移除目標視覺效果、 回報程式碼 （轉譯內嵌程式碼無法使用），或取得內嵌程式碼。

1. 若要管理您的 [發行到 Web]  內嵌程式碼，請開啟 [設定]  齒輪，然後選取 [管理內嵌程式碼]  。

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. 您的內嵌程式碼會出現。

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. 您可以擷取，或刪除內嵌程式碼。 刪除它，就會停用該報表或視覺效果的任何連結。

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. 如果您選取**刪除**，系統會要求您進行確認。

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>報表更新和資料重新整理

建立之後您**發佈至網路**內嵌程式碼和共用報表，它會更新的任何變更要內嵌程式碼連結會立即啟用並開啟連結的任何人可以檢視它。 不過，此初始動作之後，報表或視覺效果的更新可能需要大約一小時才能成為您的使用者可以看見。 如果需要立即可用的更新，您可以刪除內嵌程式碼，並建立新的內嵌程式碼。 若要進一步了解，請參閱[**運作方式**](#howitworks)本文稍後的章節。 

## <a name="data-refresh"></a>資料重新整理

資料重新整理會自動反映在您的內嵌報表或視覺效果中。 大約需要 1 小時，重新整理的資料才會顯示在內嵌程式碼中。 若要停用自動重新整理，您可以選取**不要重新整理**報表使用的資料集排程上。  

## <a name="custom-visuals"></a>自訂視覺效果

[ **發佈至網路**] 支援自訂視覺效果。 當您使用**發佈至網路**，與您共用已發佈視覺效果的使用者不需要啟用自訂視覺效果來檢視報表。

## <a name="limitations"></a>限制

**發佈至網路**支援絕大部分的資料來源與報表在 Power BI 服務中，不過，下列**目前不支援或可用**具有**發佈至網路**:

- 使用資料列層級安全性的報表。
- 使用任何即時連線資料來源的報表，包括裝載於內部部署 的 Analysis Services 表格式、Analysis Service 多維度和 Azure Analysis Services。
- 直接或透過組織內容套件與您共用的報表。
- 位在您非屬編輯成員之群組中的報表。
- 在目前不支援"R"視覺效果**發佈至網路**報表。
- 從報表中的視覺效果匯出資料，其已發行至 web。
- ArcGIS Maps for Power BI 視覺效果。
- 包含報表層級的 DAX 量值的報表。
- 單一登入資料的查詢模型。
- [保護機密或專屬資訊](#publish-to-web-from-power-bi)。
- 隨著 [內嵌]  選項提供的自動驗證功能無法搭配 Power BI JavaScript API 使用。 針對 Power BI JavaScript API，請使用[使用者擁有資料](developer/embed-sample-for-your-organization.md)方式來內嵌。 深入了解[使用者擁有資料](developer/embed-sample-for-your-organization.md)。

## <a name="tenant-setting"></a>租用戶設定

Power BI 系統管理員可以啟用或停用**發佈至網路**功能。 它們也可以限制存取特定的群組，可能會影響您建立內嵌程式碼的能力。

|特徵 |允許整個組織使用 |不允許整個組織使用 |特定安全性群組   |
|---------|---------|---------|---------|
|**發佈至網路**報告的 下方**檔案**功能表|針對全部啟用|並非所有人都可看到|只有經授權的使用者或群組才可看到。|
|[設定]  下的 [管理內嵌程式碼] |針對全部啟用|針對全部啟用|針對全部啟用。<br><br>[刪除]*   選項僅適用於經授權的使用者或群組。<br>針對全部啟用 [取得驗證碼]*   。|
|系統管理員入口網站內的 [內嵌程式碼] |狀態會反映下列其中一項：<br>* 使用中<br>* 不支援<br>* 已封鎖|狀態會顯示 [已停用] |狀態會反映下列其中一項：<br>* 使用中<br>* 不支援<br>* 已封鎖<br><br>如果使用者未以租用戶設定作為基礎加以授權，狀態會顯示成 [侵害]  。|
|現有的已發佈報告|全部已啟用|全部已停用|報告會繼續針對全部項目呈現。|

## <a name="understanding-the-embed-code-status-column"></a>了解內嵌程式碼狀態欄

**管理內嵌程式碼**頁面包含狀態資料行。 根據預設，內嵌程式碼都**Active**，但也可以是下列狀態之一。

| 狀態 | 描述 |
| --- | --- |
| **使用中** |網際網路使用者可以檢視報表並與其互動。 |
| **封鎖** |報表內容違反[Power BI 服務條款](https://powerbi.microsoft.com/terms-of-service)。 Microsoft 已封鎖它。 如果您認為內容遭到不當封鎖，請連絡支援人員。 |
| **不支援** |報表的資料集使用資料列層級安全性或其他不受支援的設定。 請參閱[**限制**](#limitations)區段，如需完整清單。 |
| [侵害]  |內嵌程式碼超出定義的租用戶的原則。 這通常發生於內嵌程式碼所建立，然後**發佈至網路**租用戶設定變更為排除擁有內嵌程式碼的使用者。 如果已停用租用戶設定，或不再允許使用者建立內嵌程式碼，現有的內嵌程式碼顯示**侵害**狀態。 |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>如何回報 [發佈至網路] 內容的相關問題

相關問題的報表**發佈至網路**內容內嵌在網站或部落格，請使用**旗標**圖示下方列中，如下圖所示。 將系統要求您傳送一封電子郵件給 Microsoft 來解釋您的考量。 Microsoft 會評估根據 Power BI 服務條款的內容，並採取適當的動作。

若要回報問題，請選取**旗標**下方列中的圖示**發佈至網路**回報您會看到。

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>授權和定價

您必須是 Microsoft Power BI 使用者才能使用 [ **發佈至網路**]。 您的報表檢視器不需要是 Power BI 使用者。

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>運作方式 (技術性詳細資料)

當您建立內嵌程式碼使用**發佈至網路**，報表就會顯示為網際網路使用者。 它是公開可用的因此您可以預期檢閱者輕鬆地共用日後透過社交媒體的報表。 使用者直接開啟公用 URL 或在內嵌的網頁或部落格中檢視報表時，Power BI 會快取報表定義和檢視報表所需的查詢結果。 這可確保數千名並行使用者可以檢視報表，而不會影響效能。

快取是長時間執行的因此如果您更新報表定義 （例如，如果您變更它的檢視模式），或重新整理報表資料，則可能需要大約一小時的時間，變更會反映在您的使用者檢視報表的版本。 因此建議您預先準備要進行的工作，並且只在對設定滿意後再建立 [ **發佈至網路** ] 內嵌程式碼。

## <a name="next-steps"></a>後續步驟

- [SharePoint Online 報告 Web 組件](service-embed-report-spo.md) 

- [在安全入口網站或網站中內嵌報告](service-embed-secure.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
