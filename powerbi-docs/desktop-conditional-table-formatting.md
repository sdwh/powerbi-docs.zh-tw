---
title: 在 Power BI Desktop 中設定資料表格式化的條件
description: 將自訂格式套用至資料表
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 05/08/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1626c2af5906004b6b4f79f4830f003b96e241fc
ms.sourcegitcommit: 509be8852ba7595b9441c9479224f9dca298b26d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2018
---
# <a name="conditional-formatting-in-tables"></a>設定資料表格式化的條件
設定資料表格式化的條件時，您可以根據資料格值或根據其他值或欄位來指定自訂資料格背景色彩，也可以使用漸層色彩。 若要存取條件式格式設定，請在 Power BI Desktop [視覺效果] 窗格的 [欄位] 集區，選取您要格式化的 [值] 集區中，值旁邊的向下箭號 (或以滑鼠右鍵按一下欄位)。 您只能管理 [欄位] 集區之 [值] 區域中的欄位條件式格式設定。

![設定資料表格式化的條件](media/desktop-conditional-table-formatting/table-formatting_1.png)

在出現的對話方塊中，您可以設定色彩以及 [最小值] 和 [最大值]。 如果您選取 [發散] 方塊，您也可以設定選擇性的「中間」值。

![發散色彩](media/desktop-conditional-table-formatting/table-formatting_2.png)

您也可以將色彩漸層作為資料模型中欄位的基礎。 此外，您可以指定所選取欄位的彙總類型 (選取的欄位指定於 [Apply color to] \(將色彩套用至\) 欄位中，因此您可以追蹤)。

![欄位的基準色彩](media/desktop-conditional-table-formatting/table-formatting_2b.png)

套用至資料表時，使用上述步驟套用的自訂格式，會覆寫套用至條件化設定資料格之格式的任何自訂資料表樣式。

![資料表格式化](media/desktop-conditional-table-formatting/table-formatting_3.png)

您也可以將設定格式化的條件套用至文字和日期欄位，只要您選擇數值作為格式化基礎。 

若要從視覺效果移除設定格式化的條件，只要以滑鼠右鍵再按一次欄位，然後選取 [移除設定格式化的條件] 即可。

![移除資料表格式化](media/desktop-conditional-table-formatting/table-formatting_4.png)

