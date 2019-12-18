---
title: 經認證的 Power BI 視覺效果
description: 提交自訂視覺效果進行認證的需求和程序。 以及經認證的 Power BI 視覺效果清單。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999736"
---
# <a name="get-a-power-bi-visual-certified"></a>取得 Power BI 視覺效果認證

經認證的 Power BI 視覺效果是 *Marketplace* 中視覺效果，符合某些經 *Microsoft Power BI 小組*測試並核准的*指定程式碼*需求。 測試的目的是要檢查視覺效果是否不會存取外部服務或資源。

經認證的 Power BI 視覺效果與[標準 Power BI 視覺效果](power-bi-custom-visuals.md)的使用方式相同。 可以將它們新增至 [Power BI Desktop](../desktop-what-is-desktop.md) 與 [Power BI 服務](../power-bi-service-overview.md)中，並使用 [Power BI 行動版](../consumer/mobile/mobile-apps-for-mobile-devices.md)和 [Power BI Embedded](embedding.md) 查看。

認證程序是選擇性的程序。 開發人員必須自行決定是否要認證其位於 Marketplace 中的 Power BI 視覺效果。 Power BI 視覺效果一旦經過認證，便能提供更多的功能。 例如，您可以[匯出至 PowerPoint](../consumer/end-user-powerpoint.md)，也可以在使用者[訂閱報表頁面](../consumer/end-user-subscribe.md)時所收到的電子郵件中顯示視覺效果。

未經認證的 Power BI 視覺效果不一定不安全。 有些視覺效果未經過認證，因為它們不符合一或多個[認證需求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)。 例如，連接到地圖視覺效果或使用商業程式庫的視覺效果等外部服務。

如果您是想要建立自己的 Power BI 視覺效果並將它們新增至  [Microsoft AppSource](https://appsource.microsoft.com) \(英文\) 的 Web 開發人員，請從 [開發 Power BI 視覺效果](visuals/custom-visual-develop-tutorial.md)教學課程開始。

> [!NOTE]
> **Microsoft**「並非」  協力廠商 Power BI 視覺效果的作者。 若要確認協力廠商視覺效果的功能，我們建議客戶直接連絡視覺效果的作者。

> [!IMPORTANT]
> Microsoft 得片面將 Power BI 視覺效果從[認證清單](#list-of-power-bi-visuals-that-have-been-certified)移除。

## <a name="certification-requirements"></a>認證需求

若要讓您的 Power BI 視覺效果[通過認證](#get-a-power-bi-visual-certified)，請確定您的 Power BI 視覺效果符合此節所列的需求。 

> [!TIP]
> 建議您搭配預設安全性規則集使用 EsLint，以便在提交程式碼前預先加以驗證。

* 已由 Microsoft 賣方儀表板或合作夥伴中心核准。 您的 Power BI 視覺效果應該要位於我們的 [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) \(英文\) 中。
* Power BI 視覺效果是以 *API v2.5* 或更高版本撰寫。
* 程式碼存放庫可供 Power BI 小組檢閱。 例如，在 GitHub 中為我們提供可讀取格式的原始程式碼 (JavaScript 或 TypeScript)。

    >[!NOTE]
    > 您不需要在 Github 中公開共用您的程式碼。

* 程式碼存放庫需求：
  * 必須包含下列檔案：
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * 不得包含 [node_modules]  資料夾 (將 [node_modules]  新增至 .gitingore* 檔案)。
  * *npm install* 命令不得傳回任何錯誤。
  * *npm audit* 命令不得傳回任何層級為高或中的警告。
  * *pbiviz package* 命令不得傳回任何錯誤。
  * 必須包含[來自 Microsoft 的 TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib) \(英文\)，且不具任何已覆寫的設定。 此命令不得傳回任何 lint 錯誤。
   * Power BI 視覺效果的編譯套件必須與所提交的套件相符 (兩個檔案的 md5 雜湊必須相等)。
* 原始程式碼需求：
   * Power BI 視覺效果必須支援[轉譯事件 API](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/) \(英文\)。
   * 請確定沒有執行任何任意/動態程式碼 (不佳：eval()，使用 settimeout()、requestAnimationFrame()、setinterval(一些包含使用者輸入的函式)、執行使用者輸入/資料皆不安全)。
   * 請確定 DOM 是透過安全的方式操縱 (不佳：innerHTML、D3.html(<一些使用者/資料輸入>))，請在新增至 DOM 前清理使用者輸入/資料。
   * 確定瀏覽器主控台中沒有任何輸入資料的 javascript 錯誤或例外狀況。 使用者可能會搭配不同範圍的未預期資料使用您的 Power BI 視覺效果，因此視覺效果不能失敗。 您可以使用此[範例報表](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) \(英文\) 作為測試資料集。

* 若 *capabilities.json* 檔案中的任何屬性發生變更，請確定它們不會中斷現有使用者的報表。

* 確定 Power BI 視覺效果符合 [Power BI 視覺效果指導方針](./guidelines-powerbi-visuals.md)。
    
* 您的程式碼只能使用公用的可檢閱 OSS 元件，例如公用 Javascript 或 TypeScript 程式庫。 原始程式碼必須可供檢閱，而且沒有已知弱點。 我們無法使用商業元件來驗證自訂視覺效果。

* Power BI 視覺效果不得存取外部服務或資源。 例如，不能從 Power BI 將任何 HTTP/S 或 WebSocket 要求發送到任何服務。 

## <a name="submitting-a-power-bi-visual-for-certification"></a>提交 Power BI 視覺效果進行認證

您可以透過合作夥伴中心，要求 Power BI 小組認證您的 Power BI 視覺效果。

>[!TIP]
>Power BI 認證程序可能需要一些時間。 如果您是在建立新的 Power BI 視覺效果，建議您在要求 Power BI 認證之前，先透過合作夥伴中心發佈您的 Power BI 視覺效果。 這可確保視覺效果的發佈不會延遲。

要求 Power BI 認證：

1. 登入合作夥伴中心。
2. 在 [概觀]  頁面上選擇您的 Power BI 視覺效果，然後移至 [產品設定]  頁面。
3. 選取 [要求 Power BI 認證]  核取方塊。
4. 在 [檢閱並發佈]  頁面上的 [認證注意事項]  文字方塊中，提供原始程式碼的連結和存取該程式碼所需的認證。

>[!NOTE]
> 如果您處於 Power BI 視覺效果提交過程期間，而且需要使用[賣方儀表板](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) \(英文\) (舊的管理工具)，請檢閱[賣方儀表板認證提交程序](seller-dashboard.md#seller-dashboard-certification-submission-process)指示。

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>經認證的 Power BI 視覺效果清單

| 連結 | 影片 |
| --- | --- |
| [3AG Systems - Bar Chart With Relative Variance](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) (3AG Systems - 顯示相對變異數的橫條圖) | |
| [3AG Systems - Column Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) (3AG Systems - 顯示相對變異數的直條圖) | |
| [Advanced Donut Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) (進階環圈圖視覺效果) | |
| [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) (進階網路圖視覺效果) | |
| [Advanced TimeSeries Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) (進階時間序列圖視覺效果) | |
| [Advanced Combo Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) (進階組合圖視覺效果) | |
| [Aster Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) (Aster 繪圖) | |
| [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) (Beyondsoft 行事曆) | |
| [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) (MAQ Software 的蝴蝶結圖表) | [影片](https://youtu.be/So5xKMSpVJI) |
| [Box and Whisker chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) (盒鬚圖) | |
| [Box and Whisker chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) (MAQ Software 的盒鬚圖) | [影片](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) (MAQ Software 的磚塊圖) | [影片](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) (Akvelon 的泡泡圖) | |
| [重點式圖表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [影片](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) (依 OKViz 排列的重點式圖表) | [影片](https://youtu.be/mtvUNl9bMjA) |
| [Calendar by Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) (Tallan 行事曆) | |
| [Candlestick by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) (OKViz K 線圖) | [影片](https://youtu.be/nT_18gyRxPo) |
| [依 OKViz 排列並隨附狀態的卡片](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) (Chiclet 交叉分析篩選器) | |
| [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) (和弦圖) | [影片](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) (MAQ Software 的圓形量測計) | [影片](https://youtu.be/9NHXALkBXuY) |
| [Cluster Map](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) (叢集對應) | |
| [Linear gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) (MAQ Software 的圓柱量測計) | [影片](https://youtu.be/DgdoWi7Gcxo) |
| [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) (標度盤量測計) | |
| [Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) (點圖) | |
| [Dot Plot by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) (OKViz 點圖) | [影片](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) (向下切入面積變量圖) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) (向下切入面量圖) | |
| [Drill-down column chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) (向下鑽研直條圖) | [影片](https://youtu.be/lBy2gQQ5YsQ) |
| [時間型資料向下切入直條圖](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [影片](https://youtu.be/T_mRou18vx0) |
| [Drill-down donut chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) (向下切入環圈圖) | [影片](https://youtu.be/AUVFrSHmPeo) |
| [雙重 KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [MAQ 軟體的動態工具提示](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [影片](https://youtu.be/Z-tl97BpEr0) |
| [Enhanced Scatter](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) (增強的散佈圖) | [影片](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) (Enlighten 水族箱) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) (Enlighten 交叉分析篩選器) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) (Enlighten 隨機顯示堆疊圖) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) (Enlighten 方格比例圖) | |
| [Filter by List (開發者：Devscope)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [影片](https://youtu.be/RetEWGwBu0I) |
| [力導向圖](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) \(英文\) | [影片](https://youtu.be/YsTa7uyJ4sg) |
| [Funnel with Source by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) (MAQ Software 的來源漏斗圖) | [影片](https://youtu.be/R_EcimsLI8U) |
| [甘特圖](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [影片](https://youtu.be/qJ7s_KrGiUU) |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) (MAQ Software 상기하여 Gantt 차트) | [影片](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) (全球資料橫條) | |
| [Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) (MAQ Software 格線) | [影片](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) (Akvelon 的階層圖) | [影片](https://youtu.be/0ZGzJaq_KT4) |
| [Histogram Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) (長條圖) | |
| [Histogram with points by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) (MAQ Software 的長條點狀圖) | [影片](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) (MAQ Software 的水平漏斗圖) | [影片](https://youtu.be/SudZei68PPo) |
| [Image by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) (CloudScope 的影像) | |
| [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) (影像方格) | |
| [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) (資訊圖設計工具) | |
| [KPI Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) (Akvelon 的 KPI 圖) | |
| [KPI Column by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) (MAQ Software 的 KPI 資料行) | [影片](https://youtu.be/rU0xoOlIq1U) |
| [KPI Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) (MAQ Software 的 KPI 格線) | [影片](https://youtu.be/dM4PvZh71V0) |
| [KPI 指標](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) (MAQ Software KPI 指示器) | [影片](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) (MAQ Software 的線性量測計) | [影片](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) (顯示資料點的折線圖) | |
| [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) (巧拼圖) | [影片](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) (多個 KPI) | |
| [Overview by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) (CloudScope 的概觀) | |
| [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) (播放軸 (動態交叉分析篩選器)) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [影片](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) (Power KPI 矩陣) | [影片](https://youtu.be/1enze8pcGzY) |
| [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) (Pulse 圖表) | [影片](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) (MAQ Software 的象限圖) | [影片](https://youtu.be/ppBnyhqWNC0) |
| [Radar Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) (雷達圖) | |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) (MAQ Software 的環狀圖) | [影片](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) (MAQ Software 的旋轉圖) | [影片](https://youtu.be/d5xBCMmb3hU) |
| [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) (Sankey 圖表) | [影片](https://youtu.be/WWP9wVUHGaA) |
| [Akvelon 的散佈圖](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [捲軸](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) (依 OKViz 排列的智慧篩選) | [影片](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) (OKViz 走勢圖) | [影片](https://youtu.be/0m3Vnvso9tY) |
| [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) (流線圖) | |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) (放射環狀圖) | |
| [Synoptic Panel by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) \(英文\) | |
| [Table Heatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) (資料表熱度圖) | |
| [轉速計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [影片](https://youtu.be/C3OXdETbS9o) |
| [Text Filter](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) (文字篩選) | |
| [Text Wrapper by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) (MAQ Software 的文字包裝函式) | |
| [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) (MAQ Software 的溫度計) | [影片](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) (時間筆刷交叉分析篩選器) | |
| [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) (時間軸交叉分析篩選器) | [影片](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) (CloudScope 的時間軸) | [影片](https://youtu.be/szNi9YgXFJc) |
| [龍捲風圖](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [影片](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) (MAQ Software 的交易圖) | [影片](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) (終極變異數) | [影片](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) (終極瀑布圖) | [影片](https://youtu.be/0BZsVCQdEkc) |
| [User List by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) (CloudScope 的使用者清單) | |
| [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) (方格圖表) | [影片](https://youtu.be/1vRqYUsm3Vk) |
| [Word 雲端](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [影片](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>常見問題集

如需視覺效果的詳細資訊，請參閱[認證視覺效果的常見問題集](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)。

## <a name="next-steps"></a>後續步驟

* [Developing a Power BI custom visual](../developer/custom-visual-develop-tutorial.md) (開發 Power BI 自訂視覺效果)
* [YouTube 上的 Microsoft 自訂視覺效果播放清單](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI 中的視覺效果](../visuals/power-bi-report-visualizations.md)  
* [Power BI 中的自訂視覺效果](power-bi-custom-visuals.md)  
* [在 Microsoft AppSource 上發佈 Power BI 視覺效果](../developer/office-store.md)  

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
