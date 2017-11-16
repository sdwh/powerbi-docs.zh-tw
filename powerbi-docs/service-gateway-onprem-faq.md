---
title: "內部部署資料閘道常見問題集"
description: "此為內部部署資料閘道常見問題集。 這會將閘道的常見問題集整合至同一個地方。"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: davidi
ms.openlocfilehash: 063fd92829c6b642fc33e578026d109d891b8fd5
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="on-premises-data-gateway-faq"></a>內部部署資料閘道常見問題集
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**問題：** 可以使用 msdmpump.dll 為 Analysis Services 建立自訂的有效使用者名稱對應嗎？  
**答：** 否。 目前不支援此項操作。

**問題：** 可以使用閘道連接至多維度 (OLAP) 執行個體嗎？  
**回答：** 可以！ 內部部署資料閘道同時支援對 Analysis Services 表格式和多維度模型的即時連線。

**問題：** 如果我安裝閘道器的電腦與使用 Windows 驗證的內部部署伺服器位在不同網域，會怎麼樣？  
**回答：** 這種情況下沒有標準做法。 這完全取決於兩個網域之間的信任關係。 如果兩個不同網域都位於受信任的網域模型，則此閘道或許可以連接至 Analysis Services 伺服器，且可以解析有效使用者名稱。 若否，您可能會登入失敗。

**問題：** 如何知道哪些有效使用者名稱已傳遞至我的內部部署 Analysis Services 伺服器？  
**回答︰**我們會在[疑難排解文章](service-gateway-onprem-tshoot.md)內回答這問題。

**問題︰** 我在 Analysis Services 中有 25 個資料庫，有方法可以一次全部加以啟用供閘道使用嗎？  
**答：** 否。 這在規劃之中，但我們沒有訂下時間範圍。

## <a name="administration"></a>系統管理
**問題︰**閘道可以有多個系統管理員嗎？  
**回答：** 可以！ 當您在管理閘道時，您可以移至系統管理員的索引標籤以新增其他系統管理員。

**問題︰**閘道管理員必須是安裝閘道所在電腦上的系統管理員嗎？  
**答：** 否。 閘道管理員可用來管理服務中的閘道。

**問題︰**是否可以防止組織中的使用者建立閘道？  
**答：** 否。 這在規劃之中，但我們沒有訂下時間範圍。

**問題︰**是否可以取得組織中閘道使用量和統計資料的資訊？  
**答：** 否。 這在規劃之中，但我們沒有訂下時間範圍。

## <a name="power-bi"></a>Power BI
**問題︰**我需要升級個人閘道嗎？
**回答︰**否，您可以繼續針對 Power BI 使用個人閘道。

**問題：**透過內部部署資料閘道進行連接時，多久會重新整理一次 Power BI 儀表板中的磚？  
**回答：** 約十分鐘。 DirectQuery 連線就是如此。 這並不表示磚會每十分鐘就對內部部署伺服器發出查詢及顯示新資料。

**問題：** 如果 Excel 活頁簿具有連接到內部部署資料來源的 Power Pivot 資料模型，我可以上傳 Excel 活頁簿嗎？ 針對此案例，我會需要閘道嗎？  
**回答：** 沒錯，您可以上傳這種活頁簿。 而且您不需要使用閘道。 但因為資料將會位在 Excel 資料模型中，所以 Power BI 中以 Excel 活頁簿為基礎的報表就不會是即時報表。 若要重新整理 Power BI 中的報表，您必須每次重新上傳更新的活頁簿。 或者，使用已排定重新整理的閘道。

**問題：**如果使用者共用具有 DirectQuery 連線的儀表板，其他使用者能在不具備相同權限的情況下查看資料嗎？  
**回應：** 針對連接至 Analysis Services 的儀表板，使用者只會看到他們可以存取的資料。 如果使用者沒有相同的權限，他們將無法看到任何資料。 若是其他資料來源，所有使用者都將共用管理員針對該資料來源所輸入的認證。

**問題︰**為何我無法連接至我的 Oracle 伺服器？  
**答案︰**您可能需要先安裝 Oracle 用戶端並使用適當的伺服器資訊設定 tnsnames.ora 檔案，才能連接至 Oracle 伺服器。 這是閘道外的個別安裝。 如需詳細資訊，請參閱[安裝 Oracle 用戶端](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client)。

**問題︰**閘道可與 ExpressRoute 搭配使用嗎？  
**回答：** 可以。 如需 ExpressRoute 和 Power BI 的詳細資訊，請參閱 [Power BI 和 ExpressRoute](service-admin-power-bi-expressroute.md)。

## <a name="next-steps"></a>後續步驟
[內部部署資料閘道](service-gateway-onprem.md)  
[內部部署資料閘道 - 深入資訊](service-gateway-onprem-indepth.md)  
[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

