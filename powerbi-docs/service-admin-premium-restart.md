---
title: 重新啟動 Power BI Premium 容量
description: 了解如何重新啟動 Power BI Premium 容量以解決效能問題。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/17/2019
LocalizationGroup: Premium
ms.openlocfilehash: 1622e06cd7aa394d384954b393d1e547e87df10a
ms.sourcegitcommit: 57e45f291714ac99390996a163436fa1f76db427
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2019
ms.locfileid: "71305661"
---
# <a name="restart-a-power-bi-premium-capacity"></a>重新啟動 Power BI Premium 容量

身為 Power BI 管理員，您可能需要重新啟動 Premium 容量。 本文說明如何重新啟動容量，並解決有關重新啟動和效能的數個問題。

## <a name="why-does-power-bi-provide-this-option"></a>Power BI 為何提供此選項？

Power BI 可讓使用者在大量資料上執行複雜的分析。 不幸的是，使用者可能由於其作業使 Power BI 服務超載、撰寫過於複雜的查詢、建立循環參考等，而造成效能問題。

Power BI 共用容量透過加諸檔案大小限制、重新整理排程及服務的其他層面，為這類情況提供一些防護。 相較之下，在 Power BI Premium 容量中，上述大部分限制會提高。 因此，具有不正確 DAX 運算式或非常複雜模型的單一報表可能會造成顯著的效能問題。 處理時，此報表可能會耗用容量的所有可用資源。 

Power BI 持續改善其保護 Premium 容量使用者免於這類問題的方式。 我們也提供管理員強大的工具，以便分析容量何時及為何負載過重。 如需詳細資訊，請參閱我們的[簡短訓練課程](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be)和[更完整的訓練課程](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2174)。 在此同時，您必須能夠在發生重大問題時予以解決。 解決這些問題的最快方式就是重新啟動容量。

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>重新啟動程序安全嗎？ 我是否會遺失任何資料？

所有儲存在容量的資料、定義、報表和儀表板在重新啟動後都會保持完整。 當您重新啟動容量時，所有進行中的排程和特定重新整理都會停止。 當容量可用時，服務會嘗試重試重新整理。 與容量互動的使用者將會遺失未儲存的工作。 他們應該在重新啟動完成時，重新整理其瀏覽器。

## <a name="how-do-i-restart-a-capacity"></a>如何重新啟動容量？

請遵循下列步驟來重新啟動容量。

1. 在 Power BI 管理入口網站的 [容量設定]  索引標籤上，巡覽至您的容量。 

1. 將 **CapacityRestart**「功能旗標」  新增至您的容量 URL： https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true。

1. 在 [進階設定]   > [容量重新啟動]  下，選取 [重新啟動容量]  。

    ![重新啟動容量](media/service-admin-premium-restart/restart-capacity.png)

1. 在 [容量重新啟動]  對話方塊中，選取 [是，重新啟動容量]  。

    ![確認重新啟動](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>如何避免在未來發生問題？

避免問題的最佳方式就是教育使用者如何有效率地建立資料模型。 如需詳細資訊，請參閱我們的[訓練課程](https://www.microsoft.com/businessapplicationssummit/video/BAS2018-2170)。

我們也建議您定期[監視您的容量](service-admin-premium-monitor-capacity.md)來尋找指出基本問題的趨勢。 我們計劃定期發行監視應用程式和其他工具，讓您可以更有效率地監視及管理您的容量。

## <a name="next-steps"></a>後續步驟

[什麼是 Power BI Premium？](service-premium-what-is.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
