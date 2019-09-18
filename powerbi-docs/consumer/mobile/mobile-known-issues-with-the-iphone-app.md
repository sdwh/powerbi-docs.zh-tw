---
title: 修正 iOS 行動裝置應用程式中的「通訊失敗」- Power BI
description: 如果您看到下列訊息，本文可能有所幫助：「發生通訊失敗。 這些失敗可能與您 Wi-Fi 連線的 Proxy 設定相關。」
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: mshenhav
ms.openlocfilehash: 9e487f4305b663028714cbe45ab76abaaa4a6db9
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2019
ms.locfileid: "61135664"
---
# <a name="fixing-communication-failures-in-ios-mobile-apps---power-bi"></a>修正 iOS 行動裝置應用程式中的「通訊失敗」- Power BI

| ![iPhone](./media/mobile-known-issues-with-the-iphone-app/iphone-logo-50-px.png) | ![iPad](./media/mobile-known-issues-with-the-iphone-app/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone |iPad |

## <a name="we-encountered-communication-failures"></a>「我們遭遇通訊失敗」
「我們遭遇通訊失敗。 這種失敗可能與 Wi-Fi 連線的 Proxy 設定有關。 切換到不同的 Wi-Fi 連線或可解決此問題。」

如果 iPhone 或 iPad 網際網路連線需要手動或自動強制明確設定 HTTP Proxy，您就有可能看到此訊息。 在此情況下，Power BI 應用程式將不會在您的 iOS 裝置上運作。

### <a name="workaround"></a>因應措施
將 iPhone 或 iPad 切換至另一個不需要明確 HTTP Proxy 設定的連線 (亦即 HTTP Proxy 已設定為關閉的連線)。

## <a name="other-issues"></a>其他問題？
請嘗試詢問 [Power BI 社群](http://community.powerbi.com/)。

