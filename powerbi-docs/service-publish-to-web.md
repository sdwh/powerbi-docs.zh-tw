---
title: Power BI 的 [發行至 Web]
description: 透過 Power BI 的 [發行至 Web]，您可以輕鬆地使用任何裝置，線上內嵌互動式 Power BI 視覺效果，例如內嵌至部落格文章、網站，或透過電子郵件、社交媒體傳送。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/30/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 53cc311f2fb0bfa4ab876c80b81ee2a092c4fd8c
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76913633"
---
# <a name="publish-to-web-from-power-bi"></a>Power BI 的 [發行至 Web]

透過 Power BI 的 [發佈至 Web]  選項，您可以輕鬆地從任何裝置透過電子郵件或社交媒體，線上內嵌互動式 Power BI 視覺效果，例如內嵌至部落格文章、網站。 您也可以輕鬆編輯、更新、重新整理或取消共用已發佈的視覺效果。

> [!WARNING]
> 使用 [發佈至 Web]  時，網際網路上的任何人都可以檢視您發佈的報表或視覺效果。 這不需要驗證，且包括檢視報表彙總的詳細資料等級資料。 發佈此報表之前，請確定您可以公開分享資料及視覺效果。 請勿發行機密或專屬資訊。 如有疑問，請先核查貴組織的原則再發行。

>[!Note]
>若要安全地將您的內容內嵌在內部入口網站或網站，請使用[內嵌](service-embed-secure.md)或[內嵌於 SharePoint Online 中](service-embed-report-spo.md)選項。 這可確保當您的使用者檢視您的內部資料時，所有權限與資料安全性都強制受保護。

## <a name="how-to-use-publish-to-web"></a>如何使用 [發佈至網路]

您可以在個人和群組工作區中可編輯的報表使用 [發佈至 Web]  功能。  它不適用於與您共用的報表，也不適用於依賴資料列層級安全性來保護資料的報表。 請參閱下面的[**限制**](#limitations)一節以取得不支援 [發佈至 Web]  的完整案例清單。 使用 [發佈至 Wb]  之前，請先檢閱本文中稍早的＜警告＞  。

下列短片會顯示這項功能的運作方式。 然後，請在下列步驟中親自試試看。

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

下列步驟說明如何使用 [ **發佈至網路**]。

1. 在工作區中開啟您可以編輯的報表，然後選取 [檔案]  > [發佈至 Web]  。

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)
   
2. 如果您的 Power BI 系統管理員尚未允許您建立內嵌程式碼，請連絡他們

   ![PtW1](media/service-publish-to-web/publish_to_web_admin_prompt.png)

3. 檢閱對話方塊內容，並選取 [建立內嵌程式碼]  。

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

4. 檢閱以下所顯示的警告，並確認資料是否可以內嵌在公開網站上。 如果可以，請選取 [發佈]  。

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

5. 隨即顯示內含連結的對話方塊。 您可以使用電子郵件來傳送此連結、將它內嵌在 iFrame 之類的程式碼中，或將它直接貼到網頁或部落格。

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

6. 如果您之前建立了報表的內嵌程式碼，並選取 [發佈至 Web]  ，則不會看到步驟 2-4 中的對話方塊。 而是隨即顯示 [內嵌程式碼]  對話方塊：

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   每個報表只能建立一個內嵌程式碼。


## <a name="tips-and-tricks-for-view-modes"></a>檢視模式的祕訣和訣竅

在部落格文章中內嵌內容時，通常需要符合特定畫面大小。  您可以視需要調整 iFrame 標籤中的高度和寬度。 不過，您必須確保報表符合指定的 iFrame 區域大小，因此您也需要在編輯報表時設定適當的檢視模式。

下表提供檢視模式的相關指南，以及內嵌後的顯示方式。

| 檢視模式 | 內嵌時的外觀 |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |[符合一頁大小]  會遵循報表頁面的高度與寬度。 如果頁面設定為 16:9 或 4:3 之類的「動態」  外觀比例，您的內容就會調整成適合 iFrame 大小。 當內嵌在 iFrame 中時，使用 [符合一頁大小]  會造成「上下黑邊」  ，當內容調整成符合 iFrame 大小後，iFrame 區域會出現灰色背景。 若要將上下黑邊縮到最小，請正確設定 iFrame 的高度及寬度。 |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |[實際大小]  可確保報表維持您在報表頁面上設定的大小。 這會導致 iFrame 中出現捲軸。 設定 iFrame 的高度和寬度以避免出現捲軸。 |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |[符合寬度]  可確保內容符合 iFrame 的水平寬度。 框線仍會顯示，但是內容會調整為使用所有的可用水平空間。 |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>iFrame 高度和寬度的秘訣和訣竅

[發佈至 Web]  內嵌程式碼看起來如下列範例所示：

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
您可以手動編輯寬度與高度，以確保其大小適合您在其中內嵌它的頁面。

若要達到更理想的符合狀態，您可以嘗試在 iFrame 的高度中新增 56 個像素，以配合下方列的目前大小。 如果報表頁面使用動態大小，下表提供一些您可以使用而不會出現上下黑邊的大小。

| 外觀比例 | 大小 | 尺寸 (寬度 x 高度) |
| --- | --- | --- |
| 16:9 |小 |640 x 416 像素 |
| 16:9 |中 |800 x 506 像素 |
| 16:9 |大 |960 x 596 像素 |
| 4:3 |小 |640 x 536 像素 |
| 4:3 |中 |800 x 656 像素 |
| 4:3 |大 |960 x 776 像素 |

## <a name="manage-embed-codes"></a>管理內嵌程式碼

建立 [發佈至 Web]  內嵌程式碼後，您可以從 Power BI 的 [設定]  功能表管理您的程式碼。 管理內嵌程式碼時，可以移除目標視覺效果、回報程式碼 (會導致內嵌程式碼無法使用) 或取得內嵌程式碼。

1. 若要管理您的 [發行到 Web]  內嵌程式碼，請開啟 [設定]  齒輪，然後選取 [管理內嵌程式碼]  。

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. 您的內嵌程式碼隨即出現。

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. 您可以擷取或刪除內嵌程式碼。 刪除它會停用該報表或視覺效果的任何連結。

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. 如果您選取 [刪除]  ，系統會要求您進行確認。

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>報表更新和資料重新整理

建立 [發佈至 Web]  內嵌程式碼並加以共用後，報表將依據您進行的任何變更更新，而內嵌程式碼連結則會立即啟用。 開啟連結的任何人都可以進行檢視。 不過，在這個初始動作之後，報表或視覺效果的更新可能需要大約一小時，才能讓您的使用者看見。 若要深入了解，請參閱本文稍後的[**運作方式**](#howitworks)一節。 

## <a name="data-refresh"></a>資料重新整理

資料重新整理會自動反映在您的內嵌報表或視覺效果中。 大約需要 1 小時，重新整理的資料才會顯示在內嵌程式碼中。 若要停用自動重新整理，請在報表使用的資料集排程上選取 [不重新整理]  。  

## <a name="custom-visuals"></a>自訂視覺效果

[ **發佈至網路**] 支援自訂視覺效果。 使用 [發佈至 Web]  時，與您共用已發佈視覺效果的使用者不需要啟用自訂視覺效果，即可檢視報表。

## <a name="limitations"></a>限制

[發佈至 Web]  支援絕大部分資料來源和 Power BI 服務中的報表，但 [發佈至 Web]  目前不支援或無法使用下列報表：

- 使用資料列層級安全性的報表。
- 使用任何即時連線資料來源的報表，包括裝載於內部部署 的 Analysis Services 表格式、Analysis Service 多維度和 Azure Analysis Services。
- 直接或透過組織內容套件與您共用的報表。
- 位在您非屬編輯成員之群組中的報表。
- [發佈至 Web]  報表目前不支援 "R" 視覺效果。
- 從報表 (已發佈至 Web ) 中的視覺效果匯出資料。
- ArcGIS Maps for Power BI 視覺效果。
- 包含報表層級 DAX 量值的報表。
- 單一登入資料查詢模型。
- 安全的機密或專屬資訊。
- [共用和認證的資料集](service-datasets-share.md)。
- 隨著 [內嵌]  選項提供的自動驗證功能無法搭配 Power BI JavaScript API 使用。 針對 Power BI JavaScript API，請使用[使用者擁有資料](developer/embed-sample-for-your-organization.md)方式來內嵌。

## <a name="tenant-setting"></a>租用戶設定

[發行至 Web]  設定能提供的選項，可讓您設定哪些使用者可以建立內嵌程式碼。

![發行到 Web 設定](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

系統會要求您連絡 Power BI 管理員，以在 [選擇內嵌程式碼的運作方式]  選項設定為 [僅允許現有內嵌程式碼]  ，且 [發行至 Web]  設定為 [啟用]  的情況下建立內嵌程式碼。

![[發行至 Web] 提示](media/service-publish-to-web/publish_to_web_admin_prompt.png)

Power BI 系統管理員可以啟用或停用 [發佈至 Web ]  功能。 他們也可以限制對特定群組的存取，這可能會影響您建立內嵌程式碼的能力。 視 [發行至 Web]  設定而定，您會在 UI 中看到不同的選項。

|特徵 |允許整個組織使用 |不允許整個組織使用 |特定安全性群組   |
|---------|---------|---------|---------|
|報告 [檔案]  功能表下的 [發佈至 Web] |針對全部啟用|並非所有人都可看到|只有經授權的使用者或群組才可看到。|
|[設定]  下的 [管理內嵌程式碼] |針對全部啟用|針對全部啟用|針對全部啟用。<br><br>[刪除]*   選項僅適用於經授權的使用者或群組。<br>針對全部啟用 [取得驗證碼]*   。|
|系統管理員入口網站內的 [內嵌程式碼] |狀態會反映下列其中一個狀態：<br>* 使用中<br>* 不支援<br>* 已封鎖|狀態會顯示 [已停用] |狀態會反映下列其中一個狀態：<br>* 使用中<br>* 不支援<br>* 已封鎖<br><br>如果使用者未以租用戶設定作為基礎加以授權，狀態會顯示成 [侵害]  。|
|現有的已發佈報告|全部已啟用|全部已停用|報告會繼續針對全部項目呈現。|

## <a name="understanding-the-embed-code-status-column"></a>了解內嵌程式碼狀態欄

>[!Note]
>您應該定期檢閱您已發行的內嵌程式碼，並移除不再需要公開提供的任何內嵌程式碼。 

[管理內嵌程式碼]  頁面包含狀態資料行。 根據預設，內嵌程式碼都是 [使用中]  ，但也可以是下列其中一種狀態。

| 狀態 | 描述 |
| --- | --- |
| **使用中** |網際網路使用者可以檢視報表並與其互動。 |
| **封鎖** |報表內容違反 [Power BI 服務條款](https://powerbi.microsoft.com/terms-of-service)。 Microsoft 已予以封鎖。 如果您認為內容遭到不當封鎖，請連絡支援人員。 |
| **不支援** |報表的資料集使用資料列層級安全性或其他不受支援的設定。 如需完整清單，請參閱[**限制**](#limitations)一節。 |
| [侵害]  |內嵌程式碼不屬於定義的租用戶原則。 當內嵌程式碼建立，且 [發佈至 Web]  租用戶設定變更為排除擁有內嵌程式碼的使用者時，通常就會發生這個情況。 如果已停用租用戶設定，或不再允許使用者建立內嵌程式碼，現有的內嵌程式碼就會顯示 [侵害]  狀態。 |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>如何回報 [發佈至網路] 內容的相關問題

若要回報與內嵌在網站或部落格的 [發佈至 Web]  內容相關的問題，請使用下方列的**旗標**圖示，如下圖所示。 系統會要求您傳送電子郵件給 Microsoft 來說明您的問題。 Microsoft 會根據「Power BI 服務條款」來評估內容，並採取適當行動。

若要回報問題，請選取您在 [發佈至 Web]  報表下方列上看到的**旗標**圖示。

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>授權和定價

您必須是 Microsoft Power BI 使用者才能使用 [ **發佈至網路**]。 您的報表檢視人員不需要是 Power BI 使用者。

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>運作方式 (技術性詳細資料)

使用 [發佈至 Web]  建立內嵌程式碼後，任何網際網路使用者都可以檢視報表。 報表可以公開取得，因此，您可以預期檢視人員日後透過社交媒體輕鬆共用報表。 使用者直接開啟公用 URL 或在內嵌的網頁或部落格中檢視報表時，Power BI 會快取報表定義和檢視報表所需的查詢結果。 這可確保數千名並行使用者能夠檢視報表，而不會影響效能。

系統會長時間保留快取，所以如果您更新報表定義 (例如變更檢視模式)，或重新整理報表資料，系統需要大約一小時，才會在使用者檢視的報表版本上反映變更。 因此建議您預先準備要進行的工作，並且只在對設定滿意後再建立 [ **發佈至網路** ] 內嵌程式碼。

## <a name="next-steps"></a>後續步驟

- [SharePoint Online 報告 Web 組件](service-embed-report-spo.md) 

- [在安全入口網站或網站中內嵌報告](service-embed-secure.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
