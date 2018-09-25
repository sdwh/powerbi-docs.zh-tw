---
title: 經認證的 Power BI 自訂視覺效果
description: 提交自訂視覺效果進行認證的需求和程序。 以及已通過認證的自訂視覺效果清單。
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 02/13/2018
ms.author: mihart
ms.openlocfilehash: 45bd00877aadba2a84ac533add18b82337fa8403
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46546249"
---
# <a name="getting-a-custom-visual-certified"></a>讓自訂視覺效果*經認證*
## <a name="what-is-meant-by-certified"></a>*經認證*是什麼意思？
*經認證的自訂視覺效果*代表其符合一組程式碼需求，並已通過嚴格的安全性測試。  自訂視覺效果通過認證後，就可以[匯出至 PowerPoint](consumer/end-user-powerpoint.md)，而且會顯示在使用者[訂閱報告頁面](consumer/end-user-subscribe.md)時所收到的電子郵件中。 當然，它也可以像[標準自訂視覺效果](power-bi-custom-visuals.md)一樣使用、新增至 Power BI 服務和 Power BI Desktop 報表，及在 Power BI 行動版和 Power BI Embedded 中檢視。

您是否為 Web 開發人員，而且有興趣將自己建立的視覺效果發佈到 [Microsoft AppSource](https://appsource.microsoft.com) 呢？ 請參閱[開始使用開發人員工具](service-custom-visuals-getting-started-with-developer-tools.md)了解如何進行。


## <a name="certification-requirements"></a>認證需求
* 經過 Microsoft AppSource 核准    
* 自訂視覺效果使用 Versioned API 1.2 或以上版本撰寫    
* 程式碼存放庫可供檢閱 (例如，視覺效果程式碼可透過 GitHub 取得)    
* 僅使用可公開檢閱的 OSS 元件    
* 不會存取外部服務或資源    

> **提示**︰建議您搭配預設安全性規則集使用 EsLint，以便在提交程式碼前預先加以驗證。
> 
> 

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>提交自訂視覺效果進行認證的程序
提交自訂視覺效果進行認證：

1. 將電子郵件傳送至 Power BI 自訂視覺效果支援 (pbicvsupport@microsoft.com)。 於電子郵件中包括下列資訊︰    

   * 標題︰視覺效果認證要求    
   * 連結至視覺效果原始程式碼裝載所在的 GitHub 存放庫    
   * 遵守需求 (如上所述)    
   * 通過程式碼與安全性檢閱    

2. Microsoft 的自訂視覺效果小組會在您的自訂視覺效果經認證並新增至經認證清單 (下方)，或是遭拒並檢附須修正問題的報告時通知您。 開發人員必須負責維護與 Microsoft 之間暢通的通訊，並在必要時更新其經認證的視覺效果。

## <a name="removal-of-power-bi-certified-custom-visuals"></a>移除 Power BI 經認證的自訂視覺效果
Microsoft 可自行斟酌將視覺效果自認證清單中移除。  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>經認證的自訂視覺效果清單

| AppSource 的連結 | 影片的連結 |
| --- | --- |
| [Aster Plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) (Aster 繪圖) | |
| [Beyondsoft Calendar](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) (Beyondsoft 行事曆) | |
| [Bowtie Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) (MAQ Software 的蝴蝶結圖表) | [影片](https://youtu.be/So5xKMSpVJI) |
| [Box and Whisker chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) (盒鬚圖) | |
| [Box and Whisker chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) (MAQ Software 的盒鬚圖) | [影片](https://youtu.be/JoHaFLfhXdo) |
| [Brick Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) (MAQ Software 的磚塊圖) | [影片](https://youtu.be/hA3DOsvn2xY) |
| [Bubble Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) (Akvelon 的泡泡圖) | |
| [重點式圖表](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [影片](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) (依 OKViz 排列的重點式圖表) | [影片](https://youtu.be/mtvUNl9bMjA) |
| [Calendar by Tallan](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) (Tallan 行事曆) | |
| [Candlestick by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) (OKViz K 線圖) | [影片](https://youtu.be/nT_18gyRxPo) |
| [依 OKViz 排列並隨附狀態的卡片](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) (Chiclet 交叉分析篩選器) | |
| [Chord](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) (和弦圖) | [影片](https://youtu.be/AQvd2FhRyCI) |
| [Circular Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) (MAQ Software 的圓形量測計) | [影片](https://youtu.be/9NHXALkBXuY) |
| [Cluster Map](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) (叢集對應) | |
| [Linear gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) (MAQ Software 的圓柱量測計) | [影片](https://youtu.be/DgdoWi7Gcxo) |
| [Dial Gauge](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) (標度盤量測計) | |
| [Dot Plot](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) (點圖) | |
| [Dot Plot by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) (OKViz 點圖) | [影片](https://youtu.be/By16pX9KT40) |
| [Drilldown Cartogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) (向下切入面積變量圖) | |
| [Drilldown Choropleth](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) (向下切入面量圖) | |
| [Drill-down column chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) (向下鑽研直條圖) | [影片](https://youtu.be/lBy2gQQ5YsQ) |
| [Drill-down column chart for time based data](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) (時間型資料向下切入直條圖) | [影片](https://youtu.be/T_mRou18vx0) |
| [Drill-down donut chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) (向下切入環圈圖) | [影片](https://youtu.be/AUVFrSHmPeo) |
| [雙重 KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [MAQ 軟體的動態工具提示](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380983) | [影片](https://youtu.be/Z-tl97BpEr0) |
| [Enhanced Scatter](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) (增強的散佈圖) | [影片](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) (Enlighten 水族箱) | |
| [Enlighten Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) (Enlighten 交叉分析篩選器) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) (Enlighten 隨機顯示堆疊圖) | |
| [Enlighten Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) (Enlighten 方格比例圖) | |
| [力導向圖](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) \(英文\) | [影片](https://youtu.be/YsTa7uyJ4sg) |
| [Funnel with Source by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) (MAQ Software 的來源漏斗圖) | [影片](https://youtu.be/R_EcimsLI8U) |
| [甘特圖](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [影片](https://youtu.be/qJ7s_KrGiUU) |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) (MAQ Software 상기하여 Gantt 차트) | [影片](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) (全球資料橫條) | |
| [Grid by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380825) (MAQ Software 格線) | [影片](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchy Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) (Akvelon 的階層圖) | [影片](https://youtu.be/0ZGzJaq_KT4) |
| [Histogram Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) (長條圖) | |
| [Histogram with points by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) (MAQ Software 的長條點狀圖) | [影片](https://youtu.be/-ILF--wExrw) |
| [Horizontal Funnel by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) (MAQ Software 的水平漏斗圖) | [影片](https://youtu.be/SudZei68PPo) |
| [Image by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) (CloudScope 的影像) | |
| [Image Grid](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) (影像方格) | |
| [Infographic Designer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) (資訊圖設計工具) | |
| [KPI Chart by Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) (Akvelon 的 KPI 圖) | |
| [KPI Column by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380996) (MAQ Software 的 KPI 資料行) | [影片](https://youtu.be/rU0xoOlIq1U) |
| [KPI Grid by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380947) (MAQ Software 的 KPI 格線) | [影片](https://youtu.be/dM4PvZh71V0) |
| [KPI 指標](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) (MAQ Software KPI 指示器) | [影片](https://youtu.be/cudG4gsZ2V8) |
| [Linear Gauge by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) (MAQ Software 的線性量測計) | [影片](https://youtu.be/7_jFaM30dkc) |
| [LineDot Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) (顯示資料點的折線圖) | |
| [Mekko Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) (巧拼圖) | [影片](https://youtu.be/90FLCKpgicA) |
| [Overview by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381477) (CloudScope 的概觀) | |
| [Play Axis (Dynamic Slicer)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) (播放軸 (動態交叉分析篩選器)) | |
| [Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [影片](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI Matrix](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) (Power KPI 矩陣) | [影片](https://youtu.be/1enze8pcGzY) |
| [Pulse Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381006) (Pulse 圖表) | [影片](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) (MAQ Software 的象限圖) | [影片](https://youtu.be/ppBnyhqWNC0) |
| [Radar Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) (雷達圖) | |
| [Ring Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) (MAQ Software 的環狀圖) | [影片](https://youtu.be/pDToHDFHnq8) |
| [Rotating Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) (MAQ Software 的旋轉圖) | [影片](https://youtu.be/d5xBCMmb3hU) |
| [Sankey Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) (Sankey 圖表) | [影片](https://youtu.be/WWP9wVUHGaA) |
| [捲軸](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) (依 OKViz 排列的智慧篩選) | [影片](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) (OKViz 走勢圖) | [影片](https://youtu.be/0m3Vnvso9tY) |
| [Stream Graph](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) (流線圖) | |
| [Sunburst](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) (放射環狀圖) | |
| [Synoptic Panel by OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380873) \(英文\) | |
| [Table Heatmap](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) (資料表熱度圖) | |
| [轉速計](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [影片](https://youtu.be/C3OXdETbS9o) |
| [Text Filter](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) (文字篩選) | |
| [Text Wrapper by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) (MAQ Software 的文字包裝函式) | |
| [Thermometer by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380847) (MAQ Software 的溫度計) | [影片](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380798) (時間筆刷交叉分析篩選器) | |
| [Timeline Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) (時間軸交叉分析篩選器) | [影片](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381427) (CloudScope 的時間軸) | [影片](https://youtu.be/szNi9YgXFJc) |
| [龍捲風圖](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [影片](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Trading Chart by MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) (MAQ Software 的交易圖) | [影片](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate Variance](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) (終極變異數) | [影片](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) (終極瀑布圖) | [影片](https://youtu.be/0BZsVCQdEkc) |
| [User List by CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) (CloudScope 的使用者清單) | |
| [Waffle Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) (方格圖表) | [影片](https://youtu.be/1vRqYUsm3Vk) |
| [Word 雲端](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [影片](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>後續步驟
[開始使用自訂視覺效果開發人員工具 (預覽)](service-custom-visuals-getting-started-with-developer-tools.md)      
[YouTube 上的 Microsoft 自訂視覺效果播放清單](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Power BI 中的視覺效果](visuals/power-bi-report-visualizations.md)  
[Power BI 中的自訂視覺效果](power-bi-custom-visuals.md)  
[在 Microsoft AppSource 上發佈自訂視覺效果](developer/office-store.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

