---
title: "透過 Power BI 中的問與答提出問題的秘訣和訣竅"
description: "透過 Power BI 中的問與答提出問題的秘訣和訣竅"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/24/2017
ms.author: jastru
ms.openlocfilehash: 4b861927bad961837f40f34636f0570106aaabc6
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>在 Power BI 問與答中詢問問題的秘訣
## <a name="words-and-terminology-that-qa-recognizes"></a>問與答可辨識的字組與專有名詞
此關鍵字清單並非完整清單。  想知道 Power BI 能否辨識關鍵字的最佳辦法，就是在問題方塊中輸入關鍵字。  如果字詞顯示為灰色，表示 Power BI 無法辨識，或無法在目前內容中辨識。

下列清單使用現在式，但所有時態在大部分情況下皆可辨識。 例如，“is” 包括 are、was、were、will be、have、has、had、will have、has got、do、does、did。  而 “sort” 包括 sorted 和 sorting。  此外，PowerBI 可辨識並包含單字的單複數形態。 例如，Power BI 可辨識 “year” 和 “years”。

> [!NOTE]
> 現在 [iPad、iPhone 及 iPod Touch 裝置上的 iOS 版 Microsoft Power BI 應用程式](mobile-apps-ios-qna.md)也提供問與答。
> 
> 

您若為資料集的擁有者，可新增語法與同義字，提升您客戶問與答結果的品質。

**彙總**：total、sum、amount、number、quantity、count、average、most、least、fewest、largest、smallest、highest、biggest、maximum、max、greatest、lowest、littlest、minimum、min

**冠詞**：a、an、the

**空白和布林值**：blank、empty、null、前綴 “non” 或 “non-“、empty string、empty text、true、t、false、f

**比較**：vs、versus、compared to、compared with

**連接詞**：and、or、each of、with、versus、&、and、but、nor、along with、in addition to

**縮寫**︰問與答可辨識幾乎所有的縮寫，請試試看。例如：didn’t、haven’t、he’d、he’s、isn’t、it’s、she’ll、they’d、weren’t、where’ll、who’s、won’t、wouldn’t。

**日期**：Power BI 可辨識大部分的日期字詞 (day、week、month、year、quarter、decade 等等) 和許多不同的日期格式 (請見下文)。 Power BI 也能辨識下列關鍵字：MonthName、Days 1-31、decade。

範例：January 3rd of 1995、January 3rd 1995、jan 03 1995、3 Jan 1995、the 3rd of January、January 1995、1995 January、1995-01、01/1995、月份名稱。

**相對日期**：today、right now、current time、yesterday、tomorrow、the current、next、the coming、last、previous、ago、before now、sooner than、after、later than、from、at、on、from now、after now、in the future、past、last、previous、within、in、over、N days ago、N days from now、next、once、twice。

範例︰count of orders in the past 6 days。

**相等 (範圍)**：in、equal to、=、after、is more than、in、between、before

範例︰Order year is before 2012? (2012 以前的訂單年份？) Price equals between 10 and 20? (大於等於 10、小於等於 20 的價格？) Is the age of John greater than 40? (John 超過 40 歲了嗎？) Total sales in 200-300? (介於 200-300 之間的銷售總額？)

**相等 (值)**：is、equal、equal to、in、of、for、within、is in、is on

範例：Which products are green? (哪些產品是綠色的？) Order date equals 2012. (訂單日期為 2012 年。) Is the age of John 40? (John 40 歲嗎？) Total sales that is not equal to 200? (不等於 200 的銷售總額？) Order date of 1/1/2016. (訂單日期是 2016 年 1 月 1 日。) 10 in price? (價格為 10？) Green for color? (顏色是綠色嗎？) 10 in price? (價格為 10？)

**名稱**：如果資料集中的資料行包含片語「名稱」(例如 EmployeeName)，則問與答能了解該資料行中的值為名稱，而且您可以詢問像是「哪些員工名字是 Robert」。

**代名詞**：he、him、himself、his、she、herself、her、hers、it、itself、its、they、their、them、themselves、theirs、this、these、that、those

**查詢命令**：sorted、sort by、direction、group、group by、by、show、list、display、give me、name、just、only、arrange、rank、compare、to、with、against、alphabetically、ascending、descending、order

**範圍**：greater、more、larger、above、over、>、less、smaller、fewer、below、under、<、at least、no less than、>=、at most、no more than、<=、in、between、in the range of、from、later、earlier、sooner、after、on、at、later than、after、since、starting with、starting from、ending with

**時間**：am、pm、o'clock、noon、midnight、hour、minute、second、hh:mm:ss

範例：10 pm、10:35 pm、10:35:15 pm、10 oclock、noon、midnight、hour、minute、second。

**前 N 個** (順序、排名)：top、bottom、highest、lowest、first、last、next、earliest、newest、oldest、latest、most recent、next

**視覺效果類型**：Power BI 所有的原生視覺效果類型。  如果是 [視覺效果] 窗格中的選項，就可以包含在問題中。  但手動加入 [視覺效果] 窗格中的[自訂視覺效果](power-bi-custom-visuals.md)例外。

範例︰以橫條圖依月份和銷售總額顯示區域資料

**Wh (關係詞、限定詞)**：when、where、which、who、whom、how many、how much、how many times、how often、how frequently、amount、number、quantity、how long、what

## <a name="qa-helps-you-phrase-the-question"></a>問與答可協助您將問題分段
問與答會盡可能地確保答案能精準反映所提出的問題。 它以數種方式達成此目標。 但所有方法，您都可以完整、部份或完全不接受該動作。 當您輸入問題時，問與答會：

* 自動完成文組與問題。 它使用各種不同的策略，包括自動完成可辨識的字組、基礎活頁簿的熱門問題，以及先前已使用且傳回有效回應的問題。 如果可使用一個以上自動完成選項，則選項會出現在下拉式清單中。
* 更正拼字。
* 以視覺效果形式提供回答的預覽結果。 視覺效果會在您輸入及編輯問題時更新 (不用等您按下 Enter 鍵)。
* 將游標移回 [問題] 方塊時，從基礎資料集自動建議取代的字詞。
* 依據基礎資料集中的資料，再次陳述問題。 這有助於確保問與答能了解您的問題，因為問與答會將您使用的字組，以基礎資料集的同義字取代。
* 不了解的字組會變暗。

## <a name="combine-results-from-more-than-one-dataset"></a>合併來自多個資料集的結果
Power BI 最強大的功能之一是能夠合併來自不同資料集的資料。  因此不要將您的問題侷限在單一資料集，您可以詢問從多個資料集擷取資料的問題。 例如，如果我的儀表板包含來自零售分析範例的磚及州人口資料集，我可以要求*依州人口以橫條圖遞減顯示商店計數*.

## <a name="dont-stop-now"></a>不立即停止
問與答顯示您的結果之後，持續保存交談內容！ 使用視覺效果的互動功能與問答集，發掘更多深入資訊。

## <a name="next-steps"></a>後續步驟
回到 [Power BI 中的問與答](service-q-and-a.md)  

[Power BI - 基本概念](service-basic-concepts.md)  

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

