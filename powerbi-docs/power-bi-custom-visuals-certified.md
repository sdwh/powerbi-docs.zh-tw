---
title: 經認證的 Power BI 自訂視覺效果
description: 提交自訂視覺效果進行認證的需求和程序。 以及已通過認證的自訂視覺效果清單。
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 05/9/2019
ms.openlocfilehash: 8c806f0de021c3857039649876864f47e1fffdb2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454551"
---
# <a name="certified-custom-visuals"></a>認證的自訂視覺效果

## <a name="what-are-certified-custom-visuals"></a>什麼是**經認證的**自訂視覺效果？

經認證的自訂視覺效果是 **Marketplace** 中的視覺效果，符合某些經 **Microsoft Power BI 小組**測試並核准的**指定程式碼**需求。 自訂視覺效果一旦經過認證，它會提供更多的功能。 例如，您可以[匯出至 PowerPoint](consumer/end-user-powerpoint.md)，也可以在使用者[訂閱報表頁面](consumer/end-user-subscribe.md)時收到的電子郵件中顯示視覺效果。

系統會使用**經認證的自訂視覺效果**，例如[標準自訂視覺效果](power-bi-custom-visuals.md)。 經認證的自訂視覺效果可以新增至 **Power BI 服務** (**Power BI Desktop 報表**)，並使用 **Power BI 行動版**和 **Power BI Embedded** 進行檢視。

所執行的測試設計為檢查不會存取外部服務或資源的視覺效果。 **Microsoft** 「不是」協力廠商自訂視覺效果的作者，我們建議客戶直接連絡作者以驗證這類視覺效果的功能。

認證程序是一種選擇性程序，開發人員負責決定是否要讓其在 Marketplace 中的視覺效果經過認證。  

**未經認證的自訂視覺效果**不一定表示不安全的視覺效果。 有些視覺效果未經過認證，因為它們不符合一或多個[認證需求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)。 例如，連接到地圖視覺效果或使用商業程式庫的視覺效果等外部服務。

您是否為 Web 開發人員，而且有興趣建立自己的視覺效果並將其新增至  **[Microsoft AppSource](https://appsource.microsoft.com)** ？ 若要了解做法，請參閱 **[開發 Power BI 自訂視覺效果](developer/custom-visual-develop-tutorial.md)** 。

## <a name="removal-of-power-bi-certified-custom-visuals"></a>移除 Power BI 經認證的自訂視覺效果

Microsoft 可自行斟酌將視覺效果自[認證清單](#list-of-custom-visuals-that-have-been-certified)中移除。

## <a name="getting-a-custom-visualcertified"></a>讓自訂視覺效果經過認證

### <a name="certification-requirements"></a>認證需求

若要讓您的自訂視覺效果[經過認證](#certified-custom-visuals)，請確定您的自訂視覺效果符合下列內容：  

* 經過 Microsoft AppSource 核准。 您的自訂視覺效果應該位於我們的 [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) 中。
* 建立版本撰寫的自訂視覺效果**API v2.5**或更高版本。
* （適用於執行個體，人類可讀取的格式 （JavaScript 或 TypeScript） 的原始碼是可傳送給 microsoft，透過 GitHub 取得），程式碼存放庫都可供 Power BI 小組的檢閱。

    >[!Note]
    > 您不需要在 Github 中公開共用您的程式碼。
* 程式碼存放庫的需求：
   * 必須包含最少需要一組檔案：
      * .gitignore
      * capabilities.json
      * pbiviz.json
      * package.json
      * package-lock.json
      * tsconfig.json
   * 不能包含 node_modules 資料夾 （檔案中加入 node_modules.gitingore）
   * **npm 安裝**命令必須未傳回任何錯誤。
   * **npm 稽核**命令必須傳回具有高，或中等層級的任何警告。
   * **pbiviz 套件**命令必須未傳回任何錯誤。
   * 必須包含[TSlint microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib)而不覆寫的設定，而且此命令必須傳回 lint 的任何錯誤。
   * 編譯的封裝的自訂視覺效果必須符合已提交的封裝 （這兩個檔案的 md5 雜湊應該相等）。
* 來源的程式碼的需求：
   * 必須支援的視覺效果[轉譯事件 API](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/)。
   * 請確定沒有任意/動態程式碼執行 (不正確： eval （)，若要使用的 settimeout()、 requestAnimationFrame()、 setinterval （使用者輸入的某些函式）、 執行使用者輸入/資料不安全)。
   * 請確定已安全地操作 DOM (不正確： innerHTML，D3.html （< 某個使用者/資料輸入 >），用於清理使用者輸入/資料之前將它加入至 dom。
   * 請確定沒有任何 javascript 錯誤/例外狀況，在瀏覽器主控台中的任何輸入資料。 使用者可能會與不同範圍的非預期的資料，使用您的視覺效果，讓視覺效果必須不會失敗。 您可以使用[這個範例報表](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)做為測試資料集。

* 如果變更 capabilities.json 中的任何屬性，請確定，它們不會中斷現有的使用者報告。

* 請確定視覺效果遵守[Power BI 視覺效果的指導方針](https://docs.microsoft.com/en-us/power-bi/developer/guidelines-powerbi-visuals#guidelines-for-power-bi-visuals-with-additional-purchases)。 **不允許任何浮水印**。

* 僅使用可公開檢閱的 OSS 元件 (公用的 JS 程式庫或 TypeScript。 原始程式碼可供檢閱，而且沒有已知弱點)。 我們無法使用商業元件來驗證自訂視覺效果。

* 請勿存取外部服務或資源，包括但不限於沒有任何 HTTP/S 或 WebSocket 要求從 Power BI 傳出至任何服務。 

> [!TIP]
> 建議您搭配預設安全性規則集使用 EsLint，以便在提交程式碼前預先加以驗證。

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>提交自訂視覺效果進行認證的程序

提交自訂視覺效果進行認證：

1. 將電子郵件傳送至 Power BI 自訂視覺效果支援小組 (pbicvsupport@microsoft.com)。 於電子郵件中包括下列資訊︰
    * 標題：視覺效果認證要求
    * 連結人類可讀取原始程式碼裝載所在的 GitHub 存放庫
    * [遵守需求](#certification-requirements)
    * 通過程式碼檢閱

2. Microsoft 的自訂視覺效果小組會在您的自訂視覺效果經認證並新增至[經認證清單](#list-of-custom-visuals-that-have-been-certified)，或是遭拒並檢附須修正問題的報表時通知您。 開發人員必須負責維護與 Microsoft 之間暢通的通訊，並在必要時更新其經認證的視覺效果。

## <a name="list-of-custom-visuals-that-have-been-certified"></a>經認證的自訂視覺效果清單

| AppSource 的連結 | 影片的連結 |
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

如需視覺效果的詳細資訊，請參閱[認證視覺效果的常見問題集](power-bi-custom-visuals-faq.md#certified-custom-visuals)。

## <a name="next-steps"></a>後續步驟

* [Developing a Power BI custom visual](developer/custom-visual-develop-tutorial.md) (開發 Power BI 自訂視覺效果)
* [YouTube 上的 Microsoft 自訂視覺效果播放清單](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI 中的視覺效果](visuals/power-bi-report-visualizations.md)  
* [Power BI 中的自訂視覺效果](power-bi-custom-visuals.md)  
* [在 Microsoft AppSource 上發佈自訂視覺效果](developer/office-store.md)  

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
