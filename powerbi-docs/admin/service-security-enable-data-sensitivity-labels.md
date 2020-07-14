---
title: 在 Power BI 中啟用敏感度標籤
description: 了解如何在 Power BI 中啟用敏感度標籤
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/06/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 0fe1b7b1b8175511838005b7b63ca7543bbf939a
ms.sourcegitcommit: 181679a50c9d7f7faebcca3a3fc55461f594d9e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86034328"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>在 Power BI 中啟用敏感度標籤

為了讓 [Microsoft 資訊保護的敏感度標籤](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)可在 Power BI 中使用，必須在租用戶上啟用這些標籤。 本文說明 Power BI 租用戶系統管理員如何執行這項操作。 如需 Power BI 中敏感度標籤的概觀，請參閱 [Power BI 中的敏感度標籤](service-security-sensitivity-label-overview.md)。 如需在 Power BI 中套用敏感度標籤的相關資訊，請參閱[在 Power BI 中套用資料敏感度標籤 (預覽)](./service-security-apply-data-sensitivity-labels.md) 

啟用敏感度標籤時：

* 組織中的指定使用者與安全性群組可為敏感度標籤分類，並對 Power BI 報表、儀表板、資料集與資料流程[套用敏感度標籤](./service-security-apply-data-sensitivity-labels.md)。
* 組織的所有成員都能看到這些標籤。

啟用敏感度標籤需要 Azure 資訊保護授權。 如需詳細資料，請參閱[授權](service-security-sensitivity-label-overview.md#licensing)。

## <a name="enable-sensitivity-labels"></a>啟用敏感度標籤

前往 Power BI **管理入口網站**，開啟 [租用戶設定] 窗格，然後尋找 [資訊保護] 區段。

![尋找 [資訊保護] 區段](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

在 [資訊保護] 區段中，執行下列步驟：
1. 開啟 [允許使用者對 Power BI 內容套用敏感度標籤]。
1. 啟用切換按鈕。
1. 定義可以在 Power BI 資產中套用及變更敏感度標籤的使用者。 根據預設，組織中的每一位使用者都能套用敏感度標籤。 您也可以選擇只允許特定使用者或安全性群組設定敏感度標籤。 選取了整個組織或特定安全性群組之後，就可以排除特定使用者或安全性群組中的某些人員。
   
   * 若啟用敏感度標籤的對象是整個組織，通常會以安全性群組為例外。
   * 若只為特定使用者或安全性群組啟用敏感度標籤，通常以特定的使用者為例外。  
    此法可以避免屬於有權套用敏感度標籤之群組的特定使用者，無法在 Power BI 中套用敏感度標籤。

1. 按 [套用]。

![啟用敏感度標籤](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> 只有有權*建立*及*編輯*資產的 Power BI Pro 使用者，以及隸屬於您先前在此區段中設定之相關安全性群組的使用者，才能設定及編輯敏感度標籤。 不屬於此群組的使用者無法設定或編輯此標籤。  

## <a name="troubleshooting"></a>疑難排解

Power BI 使用 Microsoft 資訊保護敏感度標籤。 因此，當您在嘗試啟用敏感度標籤時若出現錯誤訊息，有可能是下列其中一項原因所致：

* 您不具 Azure 資訊保護[授權](service-security-sensitivity-label-overview.md#licensing)。
* 敏感度標籤尚未轉移成 Power BI 支援的 Microsoft 資訊保護版本。 深入了解[轉移敏感度標籤](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)。
* 您的組織尚未定義 Microsoft 資訊保護敏感度標籤。 請注意，若要使用標籤，必須將標籤列入發佈的原則之中。 [深入了解敏感度標籤](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)，或流覽 [Microsoft 安全性與合規性中心](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels)，以了解如何為您的組織定義標籤和發佈原則。

## <a name="considerations-and-limitations"></a>考量與限制

如需 Power BI 中的敏感度標籤限制清單，請參閱 [Power BI 中的敏感度標籤](service-security-sensitivity-label-overview.md#limitations)。

## <a name="next-steps"></a>後續步驟

本文描述如何在 Power BI 中啟用敏感度標籤。 下列文章提供 Power BI 資料保護的詳細資料。 

* [Power BI 中的敏感度標籤概觀](service-security-sensitivity-label-overview.md)
* [如何在 Power BI 中套用敏感度標籤](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [在 Power BI 中使用 Microsoft Cloud App Security 控制項](service-security-using-microsoft-cloud-app-security-controls.md)
* [保護計量報表](service-security-data-protection-metrics-report.md)