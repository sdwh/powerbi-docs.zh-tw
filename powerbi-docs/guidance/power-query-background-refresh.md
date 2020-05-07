---
title: 停用 Power Query 背景重新整理
description: 何時停用 Power Query 背景重新整理的指導方針。
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "75623053"
---
# <a name="disable-power-query-background-refresh"></a>停用 Power Query 背景重新整理

本文的目標為使用 Power BI Desktop 匯入資料的模型製作人員。

根據預設，當 Power Query 匯入資料時，也會針對每個查詢快取最多 1000 個資料列的預覽資料。 預覽資料有助於快速預覽來源資料，以及每個查詢步驟的轉換結果。 這些資料分別儲存在磁碟上，而不是在 Power BI Desktop 檔案內。

不過，當您的 Power BI Desktop 檔案包含許多查詢時，擷取和儲存預覽資料可能會延長完成重新整理所需的時間。

## <a name="recommendation"></a>建議

透過設定 Power BI Desktop 檔案以「在背景中」  更新預覽快取，來達成更快速的重新整理。 在 Power BI Desktop 中，您可以選取 [檔案] > [選項及設定] > [選項]  ，然後選取 [資料載入]  頁面加以啟用。 接著，您可以開啟 [允許在背景下載資料預覽]  選項。 請注意，這個選項只能針對目前的檔案進行設定。

![Power BI Desktop 背景資料選項](media/power-query-background-refresh/power-query-options-background-data.png)

啟用背景重新整理可能會導致預覽資料變成過期。 如果發生這種情況，Power Query 編輯器將會透過下列警告通知您：

![Power Query 編輯器有關舊預覽資料的警告](media/power-query-background-refresh/power-query-preview-data-old.png)

一律可以更新預覽快取。 您可以使用 [重新整理預覽]  命令，針對單一查詢或所有查詢進行更新。 在 [Power Query 編輯器] 視窗的 [常用]  功能區中即可找到該命令。

![用來重新整理預覽資料的 Power Query 編輯器命令](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power Query 文件](/power-query/)
- 有任何問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
