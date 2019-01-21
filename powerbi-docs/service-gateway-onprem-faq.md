---
title: 內部部署資料閘道常見問題集
description: 此為內部部署資料閘道常見問題集。 這會將閘道的常見問題集整合至同一個地方。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: b1c74968365db59d51f7c0a7bdb356552cc75596
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54283774"
---
# <a name="on-premises-data-gateway-faq"></a>內部部署資料閘道常見問題集
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**問：** 是否可以使用 msdmpump.dll 為 Analysis Services 建立自訂的有效使用者名稱對應？  
**答：** 否。 目前不支援此項操作。

**問：** 是否可以使用閘道來連線至多維度 (OLAP) 執行個體？  
**答：** 是！ 內部部署資料閘道同時支援對 Analysis Services 表格式和多維度模型的即時連線。

**問：** 如果我安裝閘道器的電腦與使用 Windows 驗證的內部部署伺服器位在不同網域，會發生什麼事？  
**答：** 這種情況並不會有固定的答案。 這完全取決於兩個網域之間的信任關係。 如果兩個不同網域都位於受信任的網域模型，則此閘道或許可以連接至 Analysis Services 伺服器，且可以解析有效使用者名稱。 若否，您可能會登入失敗。

**問：** 如何知道哪些有效使用者名稱已傳遞至我的內部部署 Analysis Services 伺服器？  
**答：** 我們已在[疑難排解文章](service-gateway-onprem-tshoot.md)中回答這個問題。

**問：** 我在 Analysis Services 中有 25 個資料庫，是否有方法可以一次全部加以啟用供閘道使用？  
**答：** 否。 這在規劃之中，但我們沒有訂下時間範圍。

## <a name="administration"></a>系統管理
**問：** 閘道是否可以有多個系統管理員？  
**答：** 是！ 當您在管理閘道時，您可以移至系統管理員的索引標籤以新增其他系統管理員。

**問：** 閘道管理員是否必須是安裝閘道所在電腦上的系統管理員？  
**答：** 否。 閘道管理員可用來管理服務中的閘道。

**問：** 是否可以防止組織中的使用者建立閘道？  
**答：** 否。 這在規劃之中，但我們沒有訂下時間範圍。

**問：** 是否可以取得組織中閘道使用量和統計資料的資訊？  
**答：** 否。 這在規劃之中，但我們沒有訂下時間範圍。

## <a name="power-bi"></a>Power BI
**問：** 我是否需要升級個人閘道？
**答：** 否，您可以繼續針對 Power BI 使用個人閘道。

**問：** 透過內部部署資料閘道連線時，多久會重新整理一次 Power BI 儀表板中的磚？  
**答：** 約十分鐘。 DirectQuery 連線就是如此。 這並不表示磚會每十分鐘就對內部部署伺服器發出查詢及顯示新資料。

**問：** 是否可以上傳具有連線到內部部署資料來源之 Power Pivot 資料模型的 Excel 活頁簿？ 針對此案例，我會需要閘道嗎？  
**答：** 是，您可以上傳該活頁簿。 而且您不需要使用閘道。 但因為資料將會位在 Excel 資料模型中，所以 Power BI 中以 Excel 活頁簿為基礎的報表就不會是即時報表。 若要重新整理 Power BI 中的報表，您必須每次重新上傳更新的活頁簿。 或者，使用已排定重新整理的閘道。

**問：** 如果使用者共用具有 DirectQuery 連線的儀表板，其他使用者是否能在不具備相同權限的情況下查看資料？  
**答：** 針對已連線至 Analysis Services 的儀表板，使用者只能看到他們所能存取的資料。 如果使用者沒有相同的權限，他們將無法看到任何資料。 若是其他資料來源，所有使用者都將共用管理員針對該資料來源所輸入的認證。

**問：** 為何我無法連線至我的 Oracle 伺服器？  
**答：** 您可能需要先安裝 Oracle 用戶端並使用適當的伺服器資訊設定 tnsnames.ora 檔案，才能連線至 Oracle 伺服器。 這是閘道外的個別安裝。 如需詳細資訊，請參閱[安裝 Oracle 用戶端](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client)。

**問：** 閘道是否可與 ExpressRoute 搭配使用？  
**答：** 是。 如需 ExpressRoute 和 Power BI 的詳細資訊，請參閱 [Power BI 和 ExpressRoute](service-admin-power-bi-expressroute.md)。

**問：** 我正在使用 R 指令碼。 這受到支援嗎？
**解答**：只有個人模式才支援 R 指令碼。

## <a name="next-steps"></a>後續步驟
[內部部署資料閘道](service-gateway-onprem.md)  
[內部部署資料閘道 - 深入資訊](service-gateway-onprem-indepth.md)  
[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

