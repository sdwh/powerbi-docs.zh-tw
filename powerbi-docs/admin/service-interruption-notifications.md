---
title: 服務中斷通知
description: 了解如何在 Power BI 服務中斷或效能降低時，接收電子郵件通知。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/11/2020
ms.author: kfollis
ms.openlocfilehash: 344ce3b83bbb9922e0359e04e65c01a1a088bcb3
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83135399"
---
# <a name="service-interruption-notifications"></a>服務中斷通知

取得任務關鍵性商務應用程式的可用性見解相當重要。 Power BI 提供事件通知，因此您可以選擇是否要在服務中斷或效能降低時收到電子郵件。 雖然在 Power BI 的 99.9% 服務等級協定 (SLA) 保護下，這類情況很罕見，但我們仍想確保您隨時掌握情況。 下列螢幕擷取畫面顯示當您啟用通知時，可收到的電子郵件類型：

![重新整理通知電子郵件](media/service-interruption-notifications/refresh-notification-email.png)

目前，我們會針對下列_可靠性案例_傳送電子郵件：

- 開啟報表可靠性
- 模型重新整理可靠性
- 查詢重新整理可靠性

在開啟報表、資料集重新整理或查詢執行等作業中若遇到「延遲延長」  ，就會傳送通知。 在解決事件之後，您會收到後續的電子郵件。

> [!NOTE]
> 這項功能目前僅適用於 Power BI Premium 中的專用容量， 其不適用於共用或內嵌容量。

## <a name="capacity-and-reliability-notifications"></a>容量和可靠性通知

當 Power BI Premium 容量遇到可能會影響可靠性的高資源使用量時段時，會傳送通知電子郵件。 這類影響的範例，包括開啟報表、重新整理資料集和執行查詢等作業遭遇較長的延遲。 

通知電子郵件會針對高資源使用量的原因提供資訊，包括下列項目：

* 負責資料集的資料集識別碼
* 作業類型
* 與高資源使用量建立關聯的 CPU 時間

在偵測到 Power BI Premium 容量超載時，Power BI 也會傳送電子郵件通知。 該電子郵件會說明超載的可能原因、在過去 10 分鐘內產生負載的作業，以及每個作業產生的負載量。 


如果有多個 Premium 容量，該電子郵件會包含這些容量在超載期間的資訊，以便您可考慮將包含大量資源項目的工作區，移至具有最低負載的容量。

只有在觸發超載閾值時，才會傳送超載電子郵件通知。 當 Premium 容量的負載回到非超載層級時，將不會再次收到電子郵件。

下圖顯示範例通知電子郵件：

![超載容量的通知電子郵件](media/service-interruption-notifications/refresh-notification-email-2.png)


## <a name="enable-notifications"></a>啟用通知

Power BI 租用戶系統管理員可在管理入口網站中啟用通知：

1. 識別或建立應接收通知並已啟用電子郵件功能的安全性群組。

1. 在管理入口網站中，選取 [租用戶設定]  。 在 [說明及支援設定]  下方，展開 [Receive email notifications for service outages or incidents] \(接收服務中斷或事件的電子郵件通知\)  。

1. 啟用通知，輸入安全性群組，然後選取 [套用]  。

    ![啟用服務通知](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI 會透過 no-reply-powerbi@microsoft.com 帳戶傳送通知。 請確認此帳戶已列入允許清單，以免通知被送入垃圾郵件或垃圾資料夾中。

## <a name="next-steps"></a>後續步驟

[Power BI Pro 和 Power BI Premium 支援選項](service-support-options.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)