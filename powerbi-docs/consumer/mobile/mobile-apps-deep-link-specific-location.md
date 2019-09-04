---
title: 建立 Power BI 行動裝置應用程式中的特定位置連結
description: 了解如何使用統一資源識別項 (URI)，建立 Power BI 行動裝置應用程式中特定儀表板、磚或報表的深層連結。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: mshenhav
ms.openlocfilehash: 4e09b10e38b018f8e5572343b343a243ace3bf81
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906516"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>建立 Power BI 行動裝置應用程式中的特定位置連結
您可以使用連結直接存取 Power BI 中的特定項目：報表、 儀表板和磚。

有兩個主要案例使用 Power BI Mobile 中的連結： 

* 若要開啟 從 Power BI**應用程式外**，並在特定內容 （報表/儀表板/應用程式） 上的土地。 這通常是整合案例中，當您想要從其他應用程式中開啟 Power BI 行動裝置。 
* 若要**瀏覽**在 Power BI。 這是通常在您想要在 Power BI 中建立自訂的瀏覽。


## <a name="use-links-from-outside-of-power-bi"></a>使用 Power BI 外部的連結
當您使用來自 Power BI 應用程式外的連結時，您想要確定它會開啟應用程式，而且如果應用程式未安裝在裝置上，則提供使用者安裝它。 為了支援完全的我們已經建立的特殊連結格式。 此連結格式，可確保裝置使用應用程式來開啟該連結，，和應用程式未安裝在裝置上，如果網域控制站會提供使用者移至市集，取得它。

連結應以下列開頭  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> 如果您的內容裝載在特殊的資料中心內，例如政府、 中國等。連結的開頭應正確的 Power BI 位址，例如`app.powerbigov.us`或`app.powerbi.cn`。   
>


**查詢參數**是：
* **action** (必要) = OpenApp / OpenDashboard / OpenTile / OpenReport
* **appId** = 如果您想要開啟報表或儀表板屬於的應用程式 
* **groupObjectId** = 如果您想要開啟報表或儀表板屬於的工作區 （但不是我的工作區）
* **dashboardObjectId** = 儀表板物件識別碼 （如果動作是 OpenDashboard 或 OpenTile）
* **reportObjectId** = 報表物件識別碼 （如果動作是 openreport 巨集）
* **tileObjectId** = 磚物件識別碼 （如果動作是 OpenTile）
* **reportPage** = 如果您想要開啟特定報表區段 （如果動作是 openreport 巨集）
* **ctid** = 項目組織識別碼 （與 B2B 案例相關。 這可省略的項目屬於使用者的組織）。

**範例：**

* 開啟應用程式連結 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* 開啟儀表板屬於應用程式 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* 開啟工作區 部分中的報表
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>如何取得正確的連結格式

#### <a name="links-of-apps-and-items-in-app"></a>連結的應用程式和應用程式中的項目

針對**應用程式和報表和儀表板應用程式的一部分**，最簡單的方式，取得該連結會移至應用程式工作區，然後選擇 [更新應用程式]。 這會開啟 「 發行應用程式 」 的經驗，並在 [存取] 索引標籤中，您會發現**連結**一節。 展開區段，您會看到應用程式的清單，和其所有內容的都連結，可用來直接存取。

![Power BI 的發佈的應用程式連結 ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>項目不在應用程式中的連結 

為報表和儀表板，不是應用程式的一部分，您需要擷取項目 URL 中的識別碼。

例如，若要尋找 36 個字元**儀表板**物件識別碼，請瀏覽至 Power BI 服務中的特定儀表板 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

若要尋找 36 個字元**報表**物件識別碼，請瀏覽至 Power BI 服務中的特定報表。
這是報表的從 「 我的工作區 」 範例

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
上述 URL 也包含特定報表頁面 **"ReportSection3"** 。

這是報表的從工作區 （不我的工作區） 範例

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>使用 Power BI 內的連結

在 Power BI 內的連結運作完全相同 Power BI 服務的行動應用程式中。

如果您想要將連結加入到報表中指向另一個 Power BI 項目，您就可以從瀏覽器網址列，只複製的項目 URL。 深入了解[如何將超連結加入至報表中的文字方塊](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box)。

## <a name="use-report-url-with-filter"></a>含篩選器使用報表 URL
與相同，Power BI 服務，Power BI 行動裝置應用程式也支援包含篩選查詢參數的報表 URL。 您可以在 Power BI 行動應用程式中開啟報表，並篩選特定的狀態。 比方說，此 URL 會開啟 Sales 報表，而篩選依領域

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

閱讀更多資訊[如何建立查詢參數來篩選報表](https://docs.microsoft.com/power-bi/service-url-filters)。

## <a name="next-steps"></a>後續步驟
您的意見反應可協助我們決定要在未來實作的項目，因此別忘了對您想在 Power BI 行動應用程式中看到的其他功能進行投票。 

* [行動裝置的 Power BI 應用程式](mobile-apps-for-mobile-devices.md)
* 請在 Twitter 上關注 @MSPowerBI
* 加入 [Power BI 社群](http://community.powerbi.com/)的交談
* [Power BI 是什麼？](../../power-bi-overview.md)

