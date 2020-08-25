---
title: 在 Power BI 中使用客戶管理的金鑰
description: 了解如何在 Power BI 中使用客戶管理的金鑰。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160918"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>在 Power BI 中使用客戶管理的金鑰

Power BI 會加密「待用」與「處理中」的資料。 根據預設，Power BI 會使用 Microsoft 管理的金鑰來為您加密資料。 組織可以選擇使用自己的金鑰，加密使用者在 Power BI 間待用的內容，從報表影像到 Premium 容量中的匯入資料集。 

## <a name="why-use-customer-managed-keys"></a>為什麼要使用客戶管理的金鑰
使用 Power BI 客戶管理的金鑰 (CMK)，組織可以達到雲端服務提供者 (在此案例中為 Microsoft) 加密待用資料的合規性需求。 CMK 可讓組織使用其提供及管理的金鑰，加密其 Power BI 使用者的內容。 撤銷客戶管理的金鑰，會讓所有人在一小時內無法讀取 Power BI 中的使用者內容，包括 Microsoft。 相較於 BYOK 供應項目，CMK 也涵蓋 Power BI Premium 容量以外的使用者內容，施行更嚴格的快取原則，而且預設啟用所有容量的 BYOK。 
 
## <a name="how-to-use-customer-managed-keys"></a>如何使用客戶管理的金鑰
若選擇使用 Power BI 客戶管理的金鑰，您的組織必須符合大小要求。 組織的全域管理員必須向 Microsoft 提交支援要求，或者可以連絡組織的 Microsoft 帳戶管理員，以深入了解相關流程。  


## <a name="next-steps"></a>後續步驟

下列連結提供有關客戶管理金鑰的實用資訊：

* [攜帶您自己的加密金鑰以用於 Power BI](service-encryption-byok.md)
* [設定 Power BI Premium 的多地理位置支援](service-admin-premium-multi-geo.md)
* [容量的運作方式](service-premium-what-is.md#how-capacities-function)
* [累加式重新整理](service-premium-incremental-refresh.md)。
