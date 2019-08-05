---
title: 視覺效果互動
description: 如何檢查 Power BI 視覺效果是否應該允許視覺效果互動
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424485"
---
# <a name="visuals-interactions"></a>視覺效果互動

視覺效果可以查詢 'allowInteractions' 旗標的值，這個值指出視覺效果是否應該允許視覺效果互動。
例如，視覺效果在報表檢視或編輯期間會互動，但在儀表板中檢視時則不會互動。
這些互動包括按一下、平移、縮放、選取等。
請注意，不論此旗標為何，所有案例中應該會啟用工具提示。

'allowInteractions' 旗標會在視覺效果初始化期間以布林值形式傳遞，作為 IVisualHost 介面的成員。

在需要視覺效果不會互動的任何 Power BI 案例中 (例如儀表板磚)，'allowInteractions' 旗標會設定為 false。
在其他案例中 (例如報表)，'allowInteractions' 會設定為 true。

如需詳細資訊，請參閱 [SampleBarChart 視覺效果存放庫](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

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
