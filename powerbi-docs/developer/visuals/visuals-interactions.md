---
title: Power BI 視覺效果中的視覺效果互動
description: 此文章討論如何檢查 Power BI 視覺效果是否應允許視覺效果互動。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1fb4f7d5950ab18a74dcacfdfef9c3ada90512c4
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378930"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Power BI 視覺效果中的視覺效果互動

視覺效果可以查詢 `allowInteractions` 旗標的值，這個值指出視覺效果是否應該允許視覺效果互動。 例如，視覺效果在報表檢視或編輯期間是可以互動的，但在儀表板中檢閱時則不是。 這些互動包括「按一下」  、「移動瀏覽」  、「縮放」  、「選取」  等。 

> [!NOTE]
> 無論指示哪一個旗標，在所有情況下，您都應該啟用工具提示。

`allowInteractions` 旗標會在視覺效果初始化期間以布林值形式傳遞，作為 IVisualHost 介面的成員。

在需要視覺效果不會互動的任何 Power BI 案例中 (例如，儀表板圖格)，`allowInteractions` 旗標會設定為 `false`。 否則 (例如，報表)，`allowInteractions` 會設定為 `true`。

如需詳細資訊，請參閱 [SampleBarChart 視覺效果存放庫](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)。

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
