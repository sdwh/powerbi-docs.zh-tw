---
title: 協力廠商服務：適用於 Power BI Desktop 的 Facebook 連接器
description: 協力廠商服務：適用於 Power BI Desktop 的 Facebook 連接器
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 66f6fa32ecabecfbaa178b5744e71c80a6020ebd
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2018
ms.locfileid: "52669650"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>適用於 Power BI Desktop 的 Facebook 連接器
**Power BI Desktop** 中的 Facebook 連接器依賴 Facebook 圖形 API。 因此，功能與可用性可能會隨著時間遷移而變化。

您可以看到[適用於 Power BI Desktop 的 Facebook 連接器相關教學課程](desktop-tutorial-facebook-analytics.md).

Facebook 的圖形 API v1.0 已於 2015 年 4 月 30 日<sup></sup>到期。 Power BI 針對 Facebook 連接器在幕後使用圖形 API，可讓您連接到資料並進行分析。

2015 年 4 月 30 日以前建置的查詢<sup></sup>可能不再作用或傳回較少的資料。 2015 年 4 月 30 日之後<sup></sup>，Power BI 對 Facebook API 的所有呼叫都使用 v2.8。 如果您的查詢建置在 2015 年 4 月 30 日之前，而且您之後都未使用，您可能需要重新驗證，以核准我們要求的新權限集。

雖然我們嘗試一有變更即發行更新，但是應用程式開發介面變更的方式可能會影響我們產生查詢的結果。 在某些情況下，可能不再支援某些查詢。 由於這種相依性，我們無法保證您使用這個連接器的查詢結果。

如需 Facebook API 變更的詳細資訊，請參閱[這裡](https://developers.facebook.com/docs/apps/changelog#v2_0).

