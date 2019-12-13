---
title: DAX：DIVIDE 函式與除法運算子 (/) 的比較
description: 何時使用 DAX DIVIDE 函式的指引。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c20a366ef657e851ef77a9649dbcc8b66b67dac0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74695189"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX：DIVIDE 函式與除法運算子 (/) 的比較

身為資料模型製造者，當您在撰寫 DAX 運算式來將分子除以分母時，可以選擇使用 [DIVIDE](/dax/divide-function-dax) 函式或除法運算子 (/ - 正斜線)。

使用 DIVIDE 函式時，您必須傳入分子和分母運算式。 (選擇性) 您可以傳入表示「替代結果」  的值。

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

DIVIDE 函式設計目的是要自動處理除以零的案例。 如果未傳入替代結果，且分母為零或空白，則函式會傳回空白。 傳入替代結果時，會傳回該結果，而不是 BLANK。

DIVIDE 函式很方便，因為它會避免您的運算式必須先測試分母值。 此函式針對測試分母值的最佳化也比 [IF](/dax/if-function-dax) 函式更佳。 效能增益很明顯，因為檢查除數為零的代價很昂貴。 進一步使用 DIVIDE 會產生更精簡的運算式。

## <a name="example"></a>範例

下列量值運算式會產生安全的除法，但它牽涉到使用四個 DAX 函式。

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

此量值運算式可達到相同的結果，但效率更高且更簡潔。

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>建議

建議您在分母為「可能」  傳回零或空白的運算式時，使用 DIVIDE 函式。

在分母為常數值的情況下，建議您使用除法運算子。 在此情況下，除法保證會成功，且您的運算式執行效果更佳，因為它會避免不必要的測試。

請仔細考慮 DIVIDE 函式是否應該傳回替代值。 對於量值來說，在無法評估有意義的結果時傳回 BLANK 通常是較好的設計。 如需詳細資訊，請參閱[避免將 BLANK 轉換成值](dax-avoid-converting-blank.md)。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
