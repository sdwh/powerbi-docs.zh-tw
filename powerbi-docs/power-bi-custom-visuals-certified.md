---
title: "經認證的 Power BI 自訂視覺效果"
description: "提交自訂視覺效果進行認證的需求和程序。 以及已通過認證的自訂視覺效果清單。"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/20/2017
ms.author: mihart
ms.openlocfilehash: 3d51475b300fadc55f33960b03c3adc0031a39b8
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="getting-a-custom-visual-certified"></a>讓自訂視覺效果*經認證*
## <a name="what-is-meant-by-certified"></a>*經認證*是什麼意思？
*經認證的自訂視覺效果*代表其符合一組程式碼需求，並已通過嚴格的安全性測試。  自訂視覺效果通過認證後，就可以[匯出至 PowerPoint](service-publish-to-powerpoint.md)，而且會顯示在使用者[訂閱報告頁面](service-report-subscribe.md)時所收到的電子郵件中。

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
| [Aster plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759?src=office&tab=Overview) (Aster 繪圖) | |
| [Bowtie chart by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838?src=office&tab=Overview) (MAQ Software 的蝴蝶結圖表) |[影片](https://youtu.be/So5xKMSpVJI) |
| [BciCalendar (Beyondsoft 行事曆)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096?src=office&tab=Overview)  | |
| [Box and Whisker](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) (盒鬚圖) | |
| [重點式圖表](https://store.office.com/app.aspx?assetid=WA104380755) |[Video1](https://youtu.be/AOlsFYkfkcw)   [Video2](https://youtu.be/AQvd2FhRyCI) |
| [Bullet Chart by OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) (依 OKViz 排列的重點式圖表) |[影片](https://youtu.be/mtvUNl9bMjA) |
| [Calendar by Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146?src=office&tab=Overview) (Tallan 行事曆) | |
| [Chiclet Slicer](https://store.office.com/chiclet-slicer-WA104380756.aspx) (Chiclet 交叉分析篩選器) |[影片](https://youtu.be/iYOkJ1APueY) |
| [Chord Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761?src=office&tab=Overview) (和弦圖) |[影片](https://youtu.be/AQvd2FhRyCI) |
| [Circular gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) (MAQ 軟體的圓形量測計) | |
| [圓柱形量測計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | |
| [Dial gauge](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) (標度盤量測計) |[影片](https://youtu.be/AOlsFYkfkcw) |
| [Donut chart (Ring chart) by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) (MAQ 軟體的環圈圖 (環形圖)) |[影片](https://youtu.be/pDToHDFHnq8) |
| [Dot Plot by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381101?src=office&tab=Overview) (OKViz 點圖) |[影片](https://youtu.be/4lskRgcpFJY) |
| [Drill down donut chart by ZoomCharts](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) (ZoomCharts 向下切入環圈圖) | |
| [雙重 KPI](https://store.office.com/dual-kpi-WA104380774.aspx) |[影片](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112?src=office&tab=Overview) (Enlighten 水族箱) | |
| Enlighten World Flags (Enlighten 世界旗幟) - 即將推出 | |
| Enlighten Stack Shuffle (Enlighten 動態堆疊) - 即將推出 | |
| [甘特圖](https://store.office.com/gantt-WA104380765.aspx) |[影片](https://youtu.be/qJ7s_KrGiUU) |
| [長條圖](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [水平漏斗圖](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) |[影片](https://youtu.be/SudZei68PPo) |
| [KPI 指標](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| [Linear gauge by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821?src=office&tab=Overview) (MAQ 軟體的線性量測計) |[影片](https://youtu.be/AOlsFYkfkcw) |
| [Mekko chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785?src=office&tab=Overview) (巧拼圖)  | [影片](https://youtu.be/90FLCKpgicA)|
| [Play Axis (Dynamic Slicer)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) (播放軸 (動態交叉分析篩選器)) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[影片](https://youtu.be/IvfIP3E6-1Q) |
| [Radar Chart](https://store.office.com/radar-chart-WA104380771.aspx) (雷達圖) | |
| [Ring chart (Donut chart) by MAQSoftware](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824?src=office&tab=Overview) (MAQSoftware 環狀圖 (環圈圖)) | [影片](https://youtu.be/pDToHDFHnq8)|
| [Sankey 圖表](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[影片](https://youtu.be/WWP9wVUHGaA) |
| [捲軸](https://store.office.com/scroller-WA104381018.aspx) |[影片](https://youtu.be/uhRFQF2cGSY) |
| [Smart Filter by SQLBI](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) (SQLBI 智慧篩選) |[影片](https://youtu.be/gcJsDDRQq28) |
| [Sparkline by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910?src=office&tab=Overview) (OKViz 走勢圖) |[影片](https://youtu.be/0m3Vnvso9tY) |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767?src=office&tab=Overview) (放射環狀圖) | |
| [轉速計](https://store.office.com/tachometer-WA104380937.aspx?) |[影片](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Thermometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847?src=office&tab=Overview) (溫度計) | [影片](https://youtu.be/SPX9mgrAdBc)|
| [時間序列分解](https://appsource.microsoft.com/product/power-bi-visuals/WA104380897) | |
| [Table Heatmap](https://store.office.com/table-heatmap-WA104380818.aspx) (資料表熱度圖) | |
| [文字包裝](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [時間軸交叉分析篩選器](https://store.office.com/timeline-slicer-WA104380786.aspx) |[影片](https://youtu.be/ozMtZ4_NZ10) |
| [龍捲風圖](https://store.office.com/tornado-chart-WA104380768.aspx) |[影片](https://youtu.be/AQvd2FhRyCI) |
| [Waffle chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049?src=office&tab=Overview) (Waffle 圖表) |[影片](https://youtu.be/1vRqYUsm3Vk) |
| [Word 雲端](https://store.office.com/word-cloud-WA104380752.aspx?) |[影片](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>後續步驟
[開始使用自訂視覺效果開發人員工具 (預覽)](service-custom-visuals-getting-started-with-developer-tools.md)      
[YouTube 上的 Microsoft 自訂視覺效果播放清單](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Power BI 中的視覺效果](power-bi-report-visualizations.md)  
[Power BI 中的自訂視覺效果](power-bi-custom-visuals.md)  
[在 Microsoft AppSource 上發佈自訂視覺效果](developer/office-store.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

