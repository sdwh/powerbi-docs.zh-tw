---
title: DAX：DIVIDE 函式與除法運算子 (/) 的比較
description: 何時使用 DAX DIVIDE 函式的指引。
author: guyinacube
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/05/2019
ms.author: v-pemyer
ms.openlocfilehash: d22491ee314ebcebd4479c4e57dbfdf7a6a1ffdb
ms.sourcegitcommit: c2197c3ad1d747b4ad490ab75771a0d32d0ae208
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "70010429"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX：DIVIDE 函式與除法運算子 (/) 的比較

本文適用於定義 DAX 運算式的資料模型製作人員。

## <a name="background"></a>背景

撰寫 DAX 運算式將分子除以分母時，您可以選擇使用 [DIVIDE](/dax/divide-function-dax) 函式或除法運算子 (/ - 正斜線)。

使用 DIVIDE 函式時，您必須傳入分子和分母運算式。 (選擇性) 您可以傳入表示替代結果的值。

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

DIVIDE 函式已設計為自動處理除以零的案例。 如果未傳入替代結果，且分母為零或空白，則函式會傳回空白。 如果傳入替代結果，則會傳回該結果，而不是空白。

DIVIDE 函式很方便，因為它會避免您的運算式必須先測試分母值。 此函式針對測試分母值的最佳化也比 [IF](/dax/if-function-dax) 函式更佳。 使用 DIVIDE 也會產生更精簡的運算式。

## <a name="example"></a>範例

下列量值運算式會產生安全的除法，但它牽涉到使用三個 DAX 函式。

```dax

=IF(ISBLANK([Sales]) || [Sales] = 0, BLANK(), [Profit] / [Sales])

```

此量值運算式可達到相同的結果，但效率更高且更簡潔。

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>建議

建議您在分母為「可能」  傳回零或空白的運算式時，使用 DIVIDE 函式。

在分母為常數值的情況下，建議您使用除法運算子。 在此情況下，除法保證會成功，且您的運算式執行效果更佳，因為它會避免不必要的測試。

您應該仔細考慮 DIVIDE 函式是否應該傳回替代值。 針對量值，傳回空白通常是較佳的設計。 這是因為當摘要為空白時，報表視覺效果預設會排除群組。 這可讓視覺效果專注於資料存在的群組。 如有必要，您可以藉由啟用 [顯示沒有資料的項目] 選項，將視覺效果設定為顯示篩選內容中的所有群組 (傳回值或空白)。
