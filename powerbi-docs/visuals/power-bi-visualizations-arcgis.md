---
title: 與已和您共用的 ArcGIS 地圖互動
description: 在閱讀檢視中使用 ArcGIS Map for Power BI 視覺效果作為報表取用者
author: mihart
ms.reviewer: willt, lukasz
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 05/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: a95e9cd889bdf42ba703649cbc475f587fb1482b
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237808"
---
# <a name="interact-with-arcgis-maps-in-power-bi"></a>在 Power BI 中與 ArcGIS 地圖互動

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

本主題是從在 Power BI 服務、Power BI Desktop 或 Power BI Mobile 中「使用」ArcGIS 地圖的人員觀點來撰寫。 一旦設計師與您共用 ArcGIS Map for Power BI 視覺效果，即可利用許多方法與該視覺效果互動。  若要深入了解如何建立 ArcGIS 地圖，請參閱[由 Esri 提供的 ArcGIS 地圖教學課程](../visuals/power-bi-visualization-arcgis.md)。

> [!NOTE]
> 若要與 Power BI 同事共用報表，必須兩人都擁有個人的 Power BI Pro 授權，或將報表儲存在 Premium 容量中。 請參閱[共用報告](../collaborate-share/service-share-reports.md)。

ArcGIS 地圖與 Power BI 的結合，把在點之外加上地圖的做法帶到了全新境界。 報表設計師會從地圖開始，並將人口統計資料的圖層附加至該地圖。 地圖上的位置型資料圖層 (例如人口普查資料) 與空間分析結合之後，能讓人更深入了解視覺效果中的資料。

> [!TIP]
> GIS 是 Geographic Information System (地理資訊系統) 的縮寫。
> 

此 ArcGIS Map for Power BI 視覺效果會依城市顯示去年的銷售額，並使用街道型地圖和平均家庭收入參考圖層。 此地圖包含兩個圖釘 (紅色和黃色) 及一個行車時間半徑 (以紫色顯示)。

![顯示美國及泡泡、圖釘、行車時間的 ArcGIS 地圖](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri.png)

> [!TIP]
> 若要查看多個範例及閱讀見證，請前往 [Power BI 上的 Esri 頁面](https://www.esri.com/powerbi)。 接著請參閱 Esri 的 [ArcGIS Maps for Power BI 使用者入門頁面](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm)。
> 
> 

## <a name="user-consent"></a>使用者同意

當同事第一次與您共用 ArcGIS 地圖時，Power BI 會顯示同意提示。 ArcGIS Maps for Power BI 是由 Esri (https://www.esri.com) 提供；因此，您的 ArcGIS Maps for Power BI 使用方式受到 Esri 條款及隱私權原則的規範。 如果 Power BI 使用者想要使用 ArcGIS Maps for Power BI 的視覺效果，就必須接受同意對話方塊。


## <a name="understand-the-layers"></a>了解圖層

ArcGIS Maps for Power BI 視覺效果可能有數種不同類型的人口統計位置資訊。

### <a name="base-maps"></a>基本地圖

每個 ArcGIS Maps for Power BI 視覺效果都是從基本地圖開始。 請將基本地圖視為資料的畫布。 基本地圖可能是基本的深色或淺色畫布，

![深灰色基本地圖](media/power-bi-visualizations-arcgis/power-bi-basemap-dark.png) 

或是具有街道和運輸詳細資料的畫布。 

![深灰色基本地圖](media/power-bi-visualizations-arcgis/power-bi-streets-basemap.png)  

基本地圖會完全套用到畫布上，當您移動瀏覽及縮放時，地圖即會更新。 放大可查看更加詳細的街道和運輸資訊。 請從某一洲移動瀏覽至另一洲，詳細資料層級會保持不變。 在這裡，我們已從波爾圖移動瀏覽至北京。

![街道型地圖](media/power-bi-visualizations-arcgis/power-bi-basemap-pan.png)  

### <a name="reference-layers"></a>參考圖層

報表「設計師」可以新增一個參考圖層。 參考圖層是由 Esri 所裝載，並提供與位置有關的額外人口統計資訊圖層。 下列範例具有人口密度的參考圖層。 較暗色彩表示較高的密度。

![顯示人口密度的奧蘭多區域地圖](media/power-bi-visualizations-arcgis/power-bi-reference.png)  

### <a name="infographics"></a>資訊圖

報表「設計師」可以新增許多資訊圖圖層。 資訊圖是顯示在視覺化畫布右側的快速視覺效果指示器。 資訊圖是由 Esri 所裝載，並提供與位置有關的額外人口統計資訊圖層。 以下範例已套用三個資訊圖。 資訊圖不會顯示在地圖本身，而是顯示在卡片上。 當縮放、移動瀏覽及選取地圖上的區域時，資訊圖卡片即會更新。

![放大的奧蘭多區域地圖和畫布右側資訊圖卡片](media/power-bi-visualizations-arcgis/power-bi-infographics.png)  

### <a name="pins"></a>圖釘

圖釘代表精確的位置，例如城市或地址。 有時報表「設計師」會使用具有行車時間半徑的圖釘。 這個範例會顯示北卡羅來納州夏洛特在 50 英哩半徑範圍內的商店。


![圍繞北卡羅來納州夏洛特的行車時間](media/power-bi-visualizations-arcgis/power-bi-drive-times.png) 


## <a name="interact-with-an-arcgis-maps-for-power-bi-visual"></a>與 ArcGIS Maps for Power BI 視覺效果互動
您可以使用的功能取決於報表共用方式，以及您的 Power BI 帳戶類型。 如有任何疑問，請洽詢系統管理員。 ArcGIS Maps for Power BI 視覺效果的表現與報表中其他視覺效果很類似。 您能夠[顯示用來建立視覺效果的資料](../consumer/end-user-show-data.md)、查看[焦點模式和全螢幕模式](../consumer/end-user-focus.md)中的地圖、[新增註解](../consumer/end-user-comment.md)、[與篩選互動](../consumer/end-user-report-filter.md) (篩選是由報表「設計師」所設定) 等。 ArcGIS 視覺效果可以交叉篩選報表頁面上的其他視覺效果，反之亦然。

將游標停留在基本地圖位置 (例如，泡泡) 上方可顯示工具提示。 此外，請使用 ArcGIS 視覺效果選取工具來顯示其他工具提示，並在基本地圖或參考圖層上進行特定選取。  

### <a name="selection-tools"></a>選取工具

ArcGIS Maps for Power BI 具有五個選取模式。 一次最多可以選取 250 個資料點。

![這三個選取工具的螢幕擷取畫面](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools.png)

#### <a name="the-single-select-tool"></a>單選工具

![單一選取工具的螢幕擷取畫面](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) 

從參考圖層選取資料點、泡泡、圖釘或個別資料點。 Power BI 會顯示工具提示，其中包含所選取項目的詳細資料。 單選會根據您的選取項目來交叉篩選報表頁面上其他視覺效果，並更新所選區域的資訊圖卡片。 

在這裡，我們從基本地圖選取了棕色的泡泡資料點。 Power BI：
- 醒目提示我們的選取項目、
- 顯示該資料點的工具提示、 
- 更新資訊圖卡片以便只顯示我們選取項目的資料，以及
- 交叉醒目提示直條圖。

![棕色泡泡工具提示的螢幕擷取畫面](media/power-bi-visualizations-arcgis/power-bi-single-selects.png)

如果地圖有參考圖層，則選取位置即會在工具提示中顯示詳細資料。 在這裡，我們選取了 Seneca County，並查看報表「設計師」新增至地圖的參考圖層 (人口密度) 中資料。 在此範例中，資料點包含兩個不同郡，所以工具提示有兩個頁面。 每個頁面都有一個圖表。 選取圖表上的橫條可顯示其他詳細資料。 

![Seneca County 工具提示的螢幕擷取畫面](media/power-bi-visualizations-arcgis/power-bi-single-select-ref.png)

> [!TIP]
  > 有時候，您可以放大來選取特定位置，藉以減少工具提示頁面的數目。  否則，如果有位置重疊，Power BI 可能會一次提供多個工具提示。 選取箭號即可在工具提示之間移動
  > 
  > ![顯示三頁的工具提示](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)

#### <a name="the-multi-select-tool"></a>複選工具

![複選工具](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) 

在地圖上繪製一個矩形，並選取包含的資料點。 使用 CTRL 鍵可選取多個矩形區域。 複選會更新所選區域的資訊圖卡片，並根據您的選取項目交叉篩選報表頁面上其他視覺效果。

![複選工具](media/power-bi-visualizations-arcgis/power-bi-multi-select.png) 

#### <a name="the-reference-layer-tool"></a>參考圖層工具

![界限的第三個選取工具](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) 

可讓您使用參考圖層內的界限或多邊形，來選取包含的資料點。 雖然很難看到，但參考圖層上有一個黃色的外框。 不同於單選工具，我們不會取得工具提示。 相反地，我們會取得該外框框線內所含任何資料點的相關資料。 在此範例中，我們的選取項目確實包含一個資料點，該資料點是用於 Winston Salem 中的 Lindseys 商店。

![參考選取工具](media/power-bi-visualizations-arcgis/power-bi-ref-tool.png) 

#### <a name="the-buffer-tool"></a>緩衝區工具

![用於緩衝區的第四個選取工具](media/power-bi-visualizations-arcgis/power-bi-esri-selection-4.png) 

允許使用緩衝區圖層選取資料點。 例如，可以使用此工具來選取行車時間半徑，並繼續與報表的其餘部分互動。 行車時間半徑會保持使用中的狀態，而資訊圖卡片會繼續反映行車時間半徑，但選取地圖上其他資料點會交叉篩選報表頁面上的其他視覺效果。

![緩衝區選取工具](media/power-bi-visualizations-arcgis/power-bi-buffer.png) 

#### <a name="the-find-similar-tool"></a>尋找相似項目工具

![用於相似性的第五個選取工具](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference5.png) 

可讓您尋找具有相似屬性的位置。 您一開始會選取一或多個感興趣的點或參考位置，以定義最多五個您想要在分析中使用的維度。 接著，[尋找相似項目] 會計算地圖上最類似您所定義參考位置的 10 個位置。 然後，您可以使用資訊圖卡片來深入了解每個結果的人口統計資料、建立行車時間範圍來了解每個位置之間的行車距離，或甚至使用 [尋找相似項目] 工具本身來篩選報表，並取得更多見解。 最重要的是，所有計算都是在電腦本機上進行，因此您可以確定機密資料仍受到保護。


## <a name="considerations-and-limitations"></a>考量與限制
ArcGIS Maps for Power BI 可在下列服務和應用程式中使用：

|服務/應用程式  |可用性  |
|---------|---------|
|Power BI Desktop     |     是    |
|Power BI 服務 (app.powerbi.com)     |    是     |
|Power BI 行動應用程式     |  是      |
|Power BI 的發佈至網路功能     |  否       |
|Power BI Embedded     |     否    |
|Power BI 服務內嵌 (PowerBI.com)  | 否 |


## <a name="how-do-arcgis-maps-for-power-bi-work-together"></a>如何搭配 ArcGIS Maps for Power BI 運作？
ArcGIS Maps for Power BI 由 Esri (https://www.esri.com) 提供。 因此，您的 ArcGIS Maps for Power BI 使用方式受到 Esri 的[條款](https://go.microsoft.com/fwlink/?LinkID=8263222)及[隱私權原則](https://go.microsoft.com/fwlink/?LinkID=826323)的規範。 如果 Power BI 使用者想要使用 ArcGIS Maps for Power BI 的視覺效果，就必須接受同意對話方塊 (如需詳細資訊，請參閱＜使用者同意＞)。  Esri 的 ArcGIS Maps for Power BI 使用方式受到 Esri 條款及隱私權原則的規範，同意對話方塊也提供相關連結。 每位使用者第一次使用 ArcGIS Maps for Power BI 之前都必須先同意。 一旦使用者接受同意對話方塊，繫結至視覺效果的資料就會傳送至 Esri 服務至少進行地理編碼，這表示會將位置資訊轉換成可在地圖上表示的緯度和經度資訊。 您應該假設任何繫結至資料視覺效果的資料都可能會傳送至 Esri 服務。 Esri 提供基本地圖、空間分析、地理編碼等服務。ArcGIS Maps for Power BI 視覺效果透過受到 Esri 所提供及維護的憑證保護的 SSL 連線與這些服務互動。 您可以從 Esri 的 [ArcGIS Maps for Power BI 產品頁面](https://www.esri.com/powerbi)取得 ArcGIS Maps for Power BI 的其他資訊。

### <a name="power-bi-plus"></a>Power BI Plus

![選取 Plus 圖示以註冊或登入](media/power-bi-visualizations-arcgis/power-bi-plus.png)

當使用者透過 ArcGIS Maps for Power BI 註冊由 Esri 提供的 Plus 訂閱時，即開始與 Esri 的直接關係。 Power BI 不會將使用者的個人資訊傳送至 Esri。 使用者使用自己的 AAD 身分識別登入並信任 Esri 提供的 AAD 應用程式。 如此一來，使用者便可以直接與 Esri 共用其個人資訊。 一旦使用者將 Plus 內容新增至 ArcGIS Maps for Power BI 視覺效果，則想要檢視或編輯該視覺效果的同事也需要 Esri 的 Plus 訂閱。 

如有 Esri 之 ArcGIS Maps for Power BI 運作方式的詳細技術性問題，請透過其支援網站與 Esri 聯繫。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

**ArcGIS 地圖未顯示**    
在無法使用 ArcGIS Maps for Power BI 的服務或應用程式中，視覺效果將顯示為帶有 Power BI 標誌的空白視覺效果。

**我在地圖上看不到我所有的資訊**    
在地圖上對緯度/經度進行地理編碼時，最多可顯示 30,000 個資料點。 對郵遞區號或街道地址等資料點進行地理編碼時，只會對前 15,000 個資料點進行地理編碼。 為位置的名稱或國家/地區進行地理編碼時，不受 1500 個地址的限制。

**使用 ArcGIS Maps for Power BI 會產生任何費用嗎？**

所有 Power BI 使用者皆可免費使用 ArcGIS Map for Power BI。 它是一個由 **Esri** 所提供的元件，因此，您的使用方式受到 **Esri** 的條款及隱私權原則的規範 (如本文稍早所述)。 如果您有訂閱 ArcGIS **Plus**，則需要付費。

**我收到有關快取將滿的錯誤訊息**

此行為是目前正在解決的 Bug。  在此同時，請選取出現在錯誤訊息中的連結，以取得清除 Power BI 快取的相關指示。

**我可以離線檢視我的 ArcGIS 地圖嗎？**

不能，Power BI 需要網路連線才能顯示地圖。

## <a name="next-steps"></a>後續步驟
取得說明：**Esri** 有提供 **ArcGIS Maps for Power BI** 功能集的[完整文件](https://go.microsoft.com/fwlink/?LinkID=828772)。

您可以參與 [**ArcGIS Maps for Power BI** 相關的 Power BI 社群對話](https://go.microsoft.com/fwlink/?LinkID=828771)，提出問題、了解最新資訊、回報問題及尋找解答。


[ArcGIS Maps for Power BI 產品頁面](https://www.esri.com/powerbi)
