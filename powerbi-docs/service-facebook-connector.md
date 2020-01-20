---
title: 第三方服務：適用於 Power BI Desktop 的 Facebook 連接器
description: 第三方服務：適用於 Power BI Desktop 的 Facebook 連接器
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: dcfc695d0371cce21a827ddfe71b3b4b05863935
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762408"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>使用適用於 Power BI Desktop 的 Facebook 連接器
**Power BI Desktop** 中的 Facebook 連接器依賴 Facebook 圖形 API。 因此，功能與可用性可能會隨著時間而變化。

您可以看到[適用於 Power BI Desktop 的 Facebook 連接器相關教學課程](desktop-tutorial-facebook-analytics.md).

Facebook 的 Graph API v1.0 已於 2015 年 4 月 30 日過期。 Power BI 針對 Facebook 連接器在幕後使用圖形 API，可讓您連接到資料並進行分析。

2015 年 4 月 30 日以前建置的查詢可能無法繼續運作或會傳回較少的資料。 2015 年 4 月 30 日之後，Power BI 對 Facebook API 的所有呼叫都使用 v2.8。 如果您的查詢建置在 2015 年 4 月 30 日之前，而且您之後都未使用，您可能需要重新驗證，以核准我們要求的新權限集。

雖然我們嘗試一有變更即發行更新，但是應用程式開發介面變更的方式可能會影響我們產生查詢的結果。 在某些情況下，可能不再支援某些查詢。 由於這種相依性，我們無法保證您使用這個連接器的查詢結果。

如需 Facebook API 變更的詳細資訊，請參閱[這裡](https://developers.facebook.com/docs/apps/changelog#v2_0).

