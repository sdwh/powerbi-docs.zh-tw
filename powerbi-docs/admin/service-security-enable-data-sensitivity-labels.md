---
title: 在 Power BI 中啟用資料敏感度標籤
description: 了解如何在 Power BI 中啟用資料敏感度標籤
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/23/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: ba1cacfa930bcc0ed51234dea13639420ac8fab7
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315641"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>在 Power BI 中啟用資料敏感度標籤

為了讓 [Microsoft 資訊保護的資料敏感度標籤](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)可在 Power BI 中使用，必須在租用戶上啟用這些標籤。 本文說明 Power BI 租用戶系統管理員如何執行這項操作。 如需 Power BI 中資料敏感度標籤的概觀，請參閱 [Power BI 的資料保護 (預覽)](service-security-data-protection-overview.md)。 如需在 Power BI 中套用敏感度標籤的相關資訊，請參閱[在 Power BI 中套用資料敏感度標籤 (預覽)](../collaborate-share/service-security-apply-data-sensitivity-labels.md) 

啟用敏感度標籤時：

* 組織中的指定使用者與安全性群組可為敏感度標籤分類，並對 Power BI 報表、儀表板、資料集與資料流程[套用敏感度標籤](../collaborate-share/service-security-apply-data-sensitivity-labels.md)。
* 組織的所有成員都能看到這些標籤。

啟用資料敏感度標籤需要 Azure 資訊保護授權。 如需詳細資料，請參閱[授權](service-security-data-protection-overview.md#licensing)。

## <a name="enable-data-sensitivity-labels"></a>啟用資料敏感度標籤

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

* 您不具 Azure 資訊保護[授權](service-security-data-protection-overview.md#licensing)。
* 敏感度標籤尚未轉移成 Power BI 支援的 Microsoft 資訊保護版本。 深入了解[轉移敏感度標籤](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)。
* 您的組織尚未定義 Microsoft 資訊保護敏感度標籤。 請注意，若要使用標籤，必須將標籤列入發佈的原則之中。 [深入了解敏感度標籤](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)，或流覽 [Microsoft 安全性與合規性中心](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels)，以了解如何為您的組織定義標籤和發佈原則。

## <a name="considerations-and-limitations"></a>考量與限制

下列清單提供 Power BI 敏感度標籤的一些限制：

**一般**
* 敏感度標籤只能套用到儀表板、報表、資料集與資料流程。 目前不適用於[編頁報表](../paginated-reports/report-builder-power-bi.md)與活頁簿。
* Power BI 資產的敏感度標籤會顯示在工作區清單、譜系、我的最愛、最近項目或應用程式檢視中；目前不會顯示在 [與我共用] 檢視中。 但請注意，即使看不見套用至 Power BI 資產的標籤，其也一律保存在匯出至 Excel、PowerPoint 與 PDF 檔案的資料上。
* 只有全域 (公用) 雲端中的租用戶，才能使用敏感度標籤。 其他雲端中的租用戶無法使用敏感度標籤。
* 範本應用程式不支援資料敏感度標籤。 擷取與安裝應用程式時，會移除範本應用程式建立者設定的敏感度標籤，而當應用程式更新時，由應用程式取用者新增到已經安裝之範本應用程式的成品中的敏感度標籤會遺失 (重設為不加任何標籤)。
* Power BI 不支援[不可轉寄](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)、[使用者定義](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)及 [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions) 保護類型的敏感度標籤。 「不可轉寄」和「使用者定義」保護類型指的是在 [Microsoft 365 安全性中心](https://security.microsoft.com/)或 [Microsoft 365 合規性中心](https://compliance.microsoft.com/)內定義的標籤。
* 不建議讓使用者在 Power BI 內套用父標籤。 如果將父標籤套用到內容，將資料從該內容匯出至檔案 (Excel、PowerPoint 和 PDF) 的作業就會失敗。 請參閱[子標籤 (分組標籤)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels)。

**匯出**
* 只有在資料匯出至 Excel、PowerPoint 和 PDF 檔案時，才會施行標籤和保護控制措施。 將資料匯出至 .csv 或 .pbix 檔案、[使用 Excel 分析] 或任何其他匯出路徑時，不會施行標籤和保護。
* 將敏感度標籤和保護套用至匯出的檔案，並不會將內容標示新增至該檔案。 不過，如果標籤已設定成要套用內容標示，那麼當檔案在 Office 傳統型應用程式中開啟時，Azure 資訊保護的統一標籤用戶端就會自動套用標記。 當您針對傳統型、行動裝置或 Web 應用程式使用內建標籤時，不會自動套用內容標示。 如需詳細資料，請參閱 [Office 應用程式何時套用內容標示和加密](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption)。
* 從 Power BI 匯出檔案的使用者，有權根據敏感度標籤設定來存取與編輯該檔案。 但匯出資料的使用者不會取得檔案擁有者權限。
* 如果將資料匯出至檔案時無法套用標籤，則匯出將會失敗。 若要檢查匯出是否因無法套用標籤而失敗，請按一下標題列中央的報表或儀表板名稱，並在開啟的資訊下拉式清單中查看其是否顯示「無法載入敏感度標籤」。 如果套用的標籤已由安全性系統管理員解除發佈或刪除，就可能發生這種情況，也可能是暫時性系統問題所致。

## <a name="next-steps"></a>後續步驟

本文說明如何在 Power BI 中啟用資料敏感度標籤。 下列文章提供 Power BI 資料保護的詳細資料。 

* [Power BI 中的資料保護概觀](service-security-data-protection-overview.md)
* [在 Power BI 中套用資料敏感度標籤](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [在 Power BI 中使用 Microsoft Cloud App Security 控制項](service-security-using-microsoft-cloud-app-security-controls.md)
* [資料保護計量報表](service-security-data-protection-metrics-report.md)