---
title: 經認證的 Power BI 視覺效果
description: 提交自訂視覺效果進行認證的需求和程序，以及經認證的 Power BI 視覺效果清單。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/01/2020
ms.openlocfilehash: 8aea9041665de69b2c5be954dc8f13a6402a06e0
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260753"
---
# <a name="get-a-power-bi-visual-certified"></a>取得 Power BI 視覺效果認證

經認證的 Power BI 視覺效果是 [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) 中的 Power BI 視覺效果，符合 Microsoft Power BI 小組[程式碼需求](#certification-requirements)。 這些視覺效果會經過測試，以驗證它們不會存取外部服務或資源，而且它們會遵循安全的程式碼模式和指導方針。

Power BI 視覺效果一旦經過認證，便能提供更多的功能。 例如，您可以[匯出至 PowerPoint](../consumer/end-user-powerpoint.md)，也可以在使用者[訂閱報表頁面](../consumer/end-user-subscribe.md)時所收到的電子郵件中顯示視覺效果。

認證程序是選擇性的。 未經認證的 Power BI 視覺效果，不一定是不安全的 Power BI 視覺效果。 有些 Power BI 視覺效果未經過認證，因為它們不符合一或多個[認證需求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)。 例如，連接至外部服務的對應 Power BI 視覺效果，或使用商業程式庫的 Power BI 視覺效果。

> [!NOTE]
> Microsoft 並非協力廠商 Power BI 視覺效果的作者。 若要確認第三方視覺效果的功能，請直接連絡視覺效果的作者。

## <a name="certification-requirements"></a>認證需求

若要讓您的 Power BI 視覺效果[通過認證](#get-a-power-bi-visual-certified)，您的 Power BI 視覺效果必須符合此節所列的需求。 

### <a name="general-requirements"></a>一般需求

您的 Power BI 視覺效果必須由賣方儀表板或合作夥伴中心核准。 我們建議您的 Power BI 視覺效果已在 [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) 中。 若要了解如何將 Power BI 視覺效果發佈至 AppSource，請參閱[將 Power BI 視覺效果發佈至合作夥伴中心](office-store.md)。

在提交您的 Power BI 視覺效果以獲得認證之前，請確認它符合 [Power BI 視覺效果的指導方針](./guidelines-powerbi-visuals.md)。

提交 Power BI 視覺效果時，請確定編譯的套件完全符合已提交的套件。

### <a name="code-repository-requirements"></a>程式碼存放庫需求

雖然您不需要在 GitHub 中公開共用程式碼，但是程式碼存放庫必須可供 Power BI 小組檢閱。 執行此動作的最佳方式是在 GitHub 中提供原始程式碼 (JavaScript 或 TypeScript)。

存放庫必須包含下列項目：
* 僅限一個 Power BI 視覺效果的程式碼。 不能包含多個 Power BI 視覺效果或不相關的程式碼。
* 名為 **certification** 的分支 (必須是小寫)。 此分支中的原始程式碼必須符合已提交的套件。 如果您要重新提交 Power BI 視覺效果，則只能在下一次提交程序期間更新此程式碼。

如果您的 Power BI 視覺效果使用私人 npm 套件或 git 子模組，您必須提供其他存放庫 (包含此程式碼) 的存取權。

若要了解 Power BI 視覺效果存放庫的外觀，請檢閱 GitHub 存放庫中的 [Power BI 視覺效果範例橫條圖](https://github.com/microsoft/PowerBI-visuals-sampleBarChartgi) \(英文\)。

### <a name="file-requirements"></a>檔案需求

使用最新版本的 API 來撰寫 Power BI 視覺效果。

存放庫必須包含下列檔案：
* **.gitignore** - 將 `node_modules`、`.tmp`、`dist` 新增至此檔案。 程式碼不能包含 *node_modules*、 *.tmp* 或 *dist* 資料夾。
* **capabilities.json** - 如果您要提交較新版本的 Power BI 視覺效果，並變更此檔案中的屬性，請確認它們不會中斷現有使用者的報告。
* **pbiviz.json** 
* **package.json**. 視覺效果必須已安裝下列套件：
   * ["tslint"](https://www.npmjs.com/package/tslint)："5.18.0" 或更高版本
   * ["typescript"](https://www.npmjs.com/package/typescript)："3.0.0" 或更高版本
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib)："6.2.0" 或更高版本
   * 檔案必須包含用於執行 linter 的命令："lint"："tslint -c tslint.json -p tsconfig.json"
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>命令需求

請確定下列命令不會傳回任何錯誤。

* `npm install`
* `pbiviz package`
* `npm audit` - 不得傳回任何層級為高或中的警告。
* [Microsoft 提供的 TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib)，且必須具有[必要設定](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json)。 此命令不得傳回任何 lint 錯誤。

### <a name="compiling-requirements"></a>編譯需求

使用最新版本的 [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) 來撰寫 Power BI 視覺效果。

您必須使用 `pbiviz package` 來編譯您的 Power BI 視覺效果。 如果您要使用自己的組建指令碼，請提供 `npm run package` 自訂組建命令。



### <a name="source-code-requirements"></a>原始程式碼需求

確認您遵循 [Power BI 視覺效果其他認證](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification)原則清單。 如果您的提交未遵循這些指導方針，合作夥伴中心的拒絕電子郵件將會包含此連結中所列的原則號碼。

依照下列程式碼需求，確定您的程式碼符合 Power BI 認證原則。  

**必要**
* 只能使用公用的可檢閱 OSS 元件，例如公用 JavaScript 或 TypeScript 程式庫。
* 程式碼必須支援[轉譯事件 API](./visuals/event-service.md)。
* 請確定已安全地操作 DOM。 請先對使用者輸入或使用者資料使用清理，再將其新增至 DOM。
* 使用[範例報告](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)作為測試資料集。

**不允許**
* 存取外部服務或資源。 例如，不能從 Power BI 將任何 HTTP/S 或 WebSocket 要求發送到任何服務。
* 使用 `innerHTML` 或 `D3.html(user data or user input)`。
* 瀏覽器主控台中任何輸入資料的 JavaScript 錯誤或例外狀況。
* 任意或動態程式碼，例如 `eval()`、不安全地使用 `settimeout()`、`requestAnimationFrame()`、`setinterval(user input function)`，以及使用者輸入或使用者資料。
* 縮短 JavaScript 檔案或專案。

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

### <a name="private-repository-submission-process"></a>私人存放庫提交程序

如果您使用 GitHub 之類的私人存放庫來提交您的 Power BI 視覺效果進行認證，請遵循此節中的指示。
1. 針對驗證小組建立新的帳戶。
2. 針對您的帳戶設定[雙因素驗證](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) \(英文\)。
3. [產生一組新的復原碼](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes) \(英文\)。
4. 提交您的 Power BI 視覺效果時，請提供下列項目：
    * 存放庫的連結
    * 登入認證 (包括密碼)
    * 復原碼
    * 我們帳戶 ([pbicvsupport](https://github.com/pbicvsupport) 的唯讀權限

## <a name="certified-power-bi-visuals"></a>經認證的 Power BI 視覺效果

認證的 Power BI 視覺效果如下所示。 按一下連結以在 AppSource 中開啟 Power BI 視覺效果。 如有可用的影片，您可以按一下影片連結來觀看影片。

* [3AG Systems - Bar Chart With Absolute Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802) (3AG Systems - 顯示絕對變異數的橫條圖)
*  [3AG Systems - Bar Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912) (3AG Systems - 顯示相對變異數的橫條圖)
*  [3AG Systems - Column Chart With Relative Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) (3AG Systems - 顯示相對變異數的直條圖)
*  [3AG Systems - Column Chart with Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724) (3AG Systems - 顯示變異數的直條圖)
* [Advanced Donut Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) (進階環圈圖視覺效果 (完整版本))
*  [Advanced Donut Visual (Light Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) (進階環圈圖視覺效果 (精簡版))
*  [Advanced Graph Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086) (進階圖表視覺效果)
*  [Advanced Network Visualization](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) (進階網路圖視覺效果)
*  [Advanced TimeSeries Visual (Full Edition)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) (進階時間序列圖視覺效果 (完整版本))
*  [Aster Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) (Aster 繪圖)
*  [Beyondsoft Calendar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) (Beyondsoft 行事曆)
*  [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) (MAQ Software 的蝴蝶結圖表)
*  [Box and Whisker chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) (盒鬚圖)
* [Box and Whisker chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) (MAQ Software 的盒鬚圖)
*  [Brick Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) (MAQ Software 的磚塊圖)
*  [Bubble Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) (Akvelon 的泡泡圖)
*  [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) (子彈圖)， **[影片連結](https://youtu.be/AOlsFYkfkcw)**
* [重點式圖表](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) (OKViz 子彈圖)， **[影片連結](https://youtu.be/mtvUNl9bMjA)**
* [Calendar by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844) (MAQ Software 行事曆)
*  [Calendar by Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) (Tallan 行事曆)
*  [Candlestick by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) (OKViz K 線圖)， **[影片連結](https://youtu.be/nT_18gyRxPo)**
*  [依 OKViz 排列並隨附狀態的卡片](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) (Chiclet 交叉分析篩選器)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) (和弦圖)， **[影片連結](https://youtu.be/AQvd2FhRyCI)**
*  [Circular Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) (MAQ Software 的圓形量測計)
*  [Cluster Map](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) (叢集對應)
* [Custom Calendar by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179) (Akvelon 自訂行事曆)
* [Linear gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) (MAQ Software 的圓柱量測計)
*  [Dial Gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
 (標度盤量測計) [Dot Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) (點圖)
*  [Dot Plot by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949)(OKViz 點圖)， **[影片連結](https://youtu.be/By16pX9KT40)**
*  [Drilldown Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) (向下切入面積變量圖)
*  [Drilldown Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) (向下切入面量圖)
*  [Drill-down column chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) (向下切入直條圖) **[影片連結](https://youtu.be/lBy2gQQ5YsQ)**
*  [Drill-down column chart for time based data](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) (時間資料向下切入直條圖)， **[影片連結](https://youtu.be/T_mRou18vx0)**
*  [Drill-down donut chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) (向下切入環圈圖) **[影片連結](https://youtu.be/AUVFrSHmPeo)**
*  [雙重 KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [MAQ 軟體的動態工具提示](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Enhanced Scatter](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) (增強的散佈圖) **[影片連結](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) (Enlighten 水族箱)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) (Enlighten 交叉分析篩選器)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) (Enlighten 隨機顯示堆疊圖)
*  [Enlighten Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) (Enlighten 方格比例圖)
*  [Filter by List by Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) (Devscope 清單篩選)， **[影片連結](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) (力導向配置圖)， **[影片連結](https://youtu.be/YsTa7uyJ4sg)**
*  [Funnel with Source by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) (MAQ Software 的來源漏斗圖)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) (甘特圖)， **[影片連結](https://youtu.be/qJ7s_KrGiUU)**
* [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) (MAQ Software 상기하여 Gantt 차트)
*  [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) (全球資料橫條)
*  [Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) (MAQ Software 格線)
*  [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) (Akvelon 階層圖)， **[影片連結](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogram Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) (長條圖)
*  [Histogram with points by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) (MAQ Software 的長條點狀圖)
* [Horizontal bar chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230) (水平橫條圖)
*  [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) (MAQ Software 的水平漏斗圖)
*  [Image by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) (CloudScope 的影像)
*  [Image Grid](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) (影像方格)
*  [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) (資訊圖設計工具)
*  [KPI Chart by Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) (Akvelon 的 KPI 圖)
*  [KPI Column by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) (MAQ Software 的 KPI 資料行)
*  [KPI Grid by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) (MAQ Software 的 KPI 格線)
*  [KPI 指標](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI Ticker by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) (MAQ Software KPI 指示器)
* [Linear Gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) (MAQ Software 的線性量測計)
*  [LineDot Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) (顯示資料點的折線圖)
*  [Mekko Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) (馬賽克圖)， **[影片連結](https://youtu.be/90FLCKpgicA)**
*  [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) (多個 KPI)
*  [Overview by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) (CloudScope 的概觀)
*  [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) (播放軸 (動態交叉分析篩選器))
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083)，[影片連結](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) (Power KPI 矩陣)， **[影片連結](https://youtu.be/1enze8pcGzY)**
*  [Pulse Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) (脈波圖)， **[影片連結](https://youtu.be/DQWdcQtjDVw)**
*  [Quadrant Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) (MAQ Software 的象限圖)
*  [Radar Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) (雷達圖)
*  [Ring Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) (MAQ Software 的環狀圖)
*  [Rotating Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) (MAQ Software 的旋轉圖)
*  [Sankey Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) (桑基圖)， **[影片連結](https://youtu.be/WWP9wVUHGaA)**
*  [Akvelon 的散佈圖](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [捲軸](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) (OKViz 智慧篩選)， **[影片連結](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) (OKViz 走勢圖)， **[影片連結](https://youtu.be/0m3Vnvso9tY)**
*  [Stream Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) (流線圖)
*  [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) (放射環狀圖)
*  [Synoptic Panel by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) \(英文\)
*  [Table Heatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) (資料表熱度圖)
*  [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) (轉速計)， **[影片連結](https://youtu.be/C3OXdETbS9o)**
*  [Text Filter](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) (文字篩選)
*  [Text Wrapper by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) (MAQ Software 的文字包裝函式)
*  [Thermometer by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) (MAQ Software 的溫度計)
*  [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) (時間筆刷交叉分析篩選器)
*  [Timeline Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) (時間軸交叉分析篩選器)， **[影片連結](https://youtu.be/ozMtZ4_NZ10)**
*  [Timeline by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) (CloudScope 時間軸)，[影片連結](https://youtu.be/szNi9YgXFJc)
*  [Tornado Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) (龍捲風圖)， **[影片連結](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Trading Chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) (MAQ Software 的交易圖)
* [Ultimate KPI Card](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977) (終極 KPI 卡片)
*  [Ultimate Variance](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) (終極變異數)， **[影片連結](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) (終極瀑布圖)， **[影片連結](https://youtu.be/0BZsVCQdEkc)**
*  [User List by CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) (CloudScope 的使用者清單)
*  [Venn Diagram by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231) (MAQ Software 文氏圖)
*  [Violin Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947) (小提琴圖)
*  [Visio Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132) (Visio 視覺效果)
*  [Waffle Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) (鬆餅圖)， **[影片連結](https://youtu.be/1vRqYUsm3Vk)**
*  [Word Cloud](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) (文字雲)， **[影片連結](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>常見問題集

如需視覺效果的詳細資訊，請參閱[認證視覺效果的常見問題集](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)。

## <a name="next-steps"></a>後續步驟

* [Developing a Power BI custom visual](../developer/custom-visual-develop-tutorial.md) (開發 Power BI 自訂視覺效果)
* [YouTube 上的 Microsoft 自訂視覺效果播放清單](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI 中的視覺效果](../visuals/power-bi-report-visualizations.md)  
* [Power BI 中的自訂視覺效果](power-bi-custom-visuals.md)  
* [在 Microsoft AppSource 上發佈 Power BI 視覺效果](../developer/office-store.md) 
* 如果您是想要建立自己的 Power BI 視覺效果並將它們新增至  [Microsoft AppSource](https://appsource.microsoft.com) \(英文\) 的 Web 開發人員，請從 [開發 Power BI 視覺效果](visuals/custom-visual-develop-tutorial.md)教學課程開始。 

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
