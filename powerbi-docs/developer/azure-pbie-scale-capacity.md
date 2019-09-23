---
title: 調整您的 Power BI Embedded 容量規模 | Microsoft Docs
description: 本文逐步解說如何在 Microsoft Azure 中調整 Power BI Embedded 容量規模。
services: power-bi-embedded
author: rkarlin
ms.author: rkarlin
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 01/31/2019
ms.openlocfilehash: b9a632fa39d320d14d1282cee5e59022a8ab0303
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61388393"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>在 Azure 入口網站中調整您的 Power BI Embedded 容量規模

本文逐步解說如何在 Microsoft Azure 中調整 Power BI Embedded 容量規模。 調整規模可讓您增加或減少您容量的大小。

假設您已建立 Power BI Embedded 容量。 如果您尚未建立，請參閱[在 Azure 入口網站中建立 Power BI Embedded 容量](azure-pbie-create-capacity.md)以開始進行。

> [!NOTE]
> 調整規模作業可能需要約一分鐘的時間。 在這段期間，容量將無法使用。 Embedded 內容可能無法載入。

## <a name="scale-a-capacity"></a>調整容量規模

1. 登入[Azure 入口網站](https://portal.azure.com/)。

2. 選取 [所有服務]   > [Power BI Embedded]  查看您的容量。

    ![Azure 入口網站中的所有服務](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. 選取您要調整規模的容量。

    ![Azure 入口網站中的 Power BI Embedded 容量清單](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. 在您容量中的 [調整規模]  下，選取 [定價層]  。

    ![[調整規模] 下的 [定價層]](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    您目前的定價層會以藍色顯示。

    ![目前的定價層以藍色顯示](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. 若要相應增加或減少，請選取要移至的新定價層。 選取新的定價層會在選取四周加上藍色虛線外框。 選取 [選取]  調整為新的定價層。

    ![選取新的定價層](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    調整您的容量規模可能需要一到兩分鐘的時間才能完成。

6. 檢視 [概觀] 索引標籤來確認您的定價層。目前的定價層隨即列出。

    ![確認目前的定價層](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>後續步驟

若要暫停或啟動您的容量，請參閱[在 Azure 入口網站中暫停和啟動您的 Power BI Embedded 容量](azure-pbie-pause-start.md)。

若要在您的應用程式中開始內嵌 Power BI 內容，請參閱[如何內嵌您的 Power BI 儀表板、報表及磚](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/)。

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
