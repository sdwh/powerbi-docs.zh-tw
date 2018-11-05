---
title: 關於 Power BI 自訂視覺效果的常見問題集
description: 瀏覽 Power BI 自訂視覺效果相關的常見問題與回答清單
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: a2e43d205b9e4f3085652ac3603ee68f67b2b33c
ms.sourcegitcommit: f9dd6098ca57d4d6cad34284126d4e58eab1c92c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50222144"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>關於 Power BI 自訂視覺效果的常見問題集

## <a name="organizational-custom-visuals"></a>組織自訂視覺效果

**系統管理員如何管理組織自訂視覺效果？**

在管理入口網站中的 [組織自訂視覺效果] 索引標籤底下，系統管理員可以查看並[管理企業中的所有組織自訂視覺效果](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals)：新增、停用、啟用及刪除。
無需再透過電子郵件或共用資料夾來共用這些視覺效果！ 一旦部署到組織存放庫，組織中的使用者就可以輕鬆地探索組織自訂視覺效果，並直接從 Power BI Desktop 或服務將它們匯入至其報告中。 可以在 [我的組織] 索引標籤下的內建存放區 (在 Desktop 與服務中) 找到組織自訂視覺效果。一旦系統管理員上傳新的組織自訂視覺效果版本後，組織中的每個人都會獲得相同的更新版本。 報表作者不需要刪除報告中的視覺效果即可獲取這些視覺效果的新版本，因為使用這些視覺效果的所有報告都會自動更新！ 更新機制類似於 Marketplace 視覺效果。

**如果系統管理員將自訂視覺效果從公用 Marketplace 上傳到組織存放區，那麼一旦供應商在公用 Marketplace 中更新視覺效果，它是否會自動更新？**

否，公用 Marketplace 沒有自動更新功能。
如有需要，系統管理員有責任更新組織自訂視覺效果的版本。

**有停用組織存放區的方法嗎？**

否，使用者一定會看到 Power BI Desktop 和服務中的 [我的組織 ] 索引標籤。 系統管理員可以從管理入口網站停用或刪除所有的組織自訂視覺效果，而組織的存放區是空的。
  
**如果系統管理員從管理入口網站 (租用戶設定) 停用自訂視覺效果，使用者是否仍可以存取組織自訂視覺效果？**

是，如果系統管理員從管理入口網站停用自訂視覺效果，不會影響組織的存放區。 某些組織會停用自訂視覺效果，並僅啟用由 Power BI 系統管理員匯入與上傳到組織的存放區的精選視覺效果。 在 Power BI Desktop 中未強制停用管理入口網站中的自訂視覺效果。 Desktop 使用者仍可以在其報表中加入和使用公用 Marketplace 中的自訂視覺效果。 但是，這些公用的自訂視覺效果會在發行至 Power BI 服務後停止轉譯，並發出適當的錯誤訊息。 使用 Power BI 服務時，您無法從公用 Marketplace 匯入自訂視覺效果。 只能匯入組織的存放區中的視覺效果，因為管理入口網站中的自訂視覺效果設定，在 Power BI 服務中是強制執行的。

**為什麼組織的存放區和組織自訂視覺效果能夠成為絕佳的企業解決方案？**

* 每個人都取得相同的視覺效果版本，由 Power BI 系統管理員所控制。 系統管理員在管理入口網站中更新視覺效果版本後，組織中的所有使用者會自動取得更新版本。

* 無需再透過電子郵件或共用資料夾共用視覺效果檔案！ 同一位置，登入的所有成員都可以看到。

* 安全性和可支援性，組織自訂視覺效果的新版本會在類似於 Marketplace 視覺效果的所有報表中自動更新。

* 組織中使用組織自訂視覺效果的使用者必須登入才能查看及使用組織自訂視覺效果，也就是組織的安全性元素。

* 系統管理員可以控制組織中可用的自訂視覺效果。

* 系統管理員可以從管理入口網站啟用/停用視覺效果以進行測試。 更好的安全性強制，因為僅允許組織成員使用這些視覺效果。

## <a name="certified-custom-visuals"></a>認證的自訂視覺效果

**什麼是認證的自訂視覺效果？**

認證的自訂視覺效果是 [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) 中的視覺效果，符合某些[指定](power-bi-custom-visuals-certified.md)程式碼需求並由 Power BI 小組進行測試。  執行的測試是設計用來檢查視覺效果不會存取外部服務或資源；但是，Microsoft 不是協力廠商自訂視覺效果的作者，我們建議客戶直接連絡作者以驗證這類視覺效果的功能。
