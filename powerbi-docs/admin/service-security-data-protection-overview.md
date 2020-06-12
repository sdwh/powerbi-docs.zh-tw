---
title: Power BI 的資料保護
description: 了解 Power BI 資料保護的運作方式
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315664"
---
# <a name="data-protection-in-power-bi"></a>Power BI 的資料保護

現代化企業對如何處理及保護敏感性資料具有嚴格的商務規範和需求。 為了提供對這類資料的控制力和可見度，Power BI 會與 Microsoft 資訊保護和 Microsoft Cloud App Security 整合。 這可讓您：
* 使用 Microsoft 資訊保護的[敏感度標籤](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide)，以利用與分類及保護 Office 365 檔案相同的分類法，來分類及標記 Power BI 服務中的內容 (儀表板、報表、資料集和資料流程)。
* 將資料匯出至 Excel、PowerPoint 或 PDF 檔案時，將 Microsoft 資訊保護的敏感度標籤和保護套用至該資料。
* 使用 Microsoft Cloud App Security 監視 Power BI 中的活動、調查安全性問題，以及使用 Microsoft Cloud App Security 條件式存取應用程式控制保護 Power BI 中的內容。

**重要事項**
* 敏感度標籤**不會**影響對 Power BI 內容的存取，存取 Power BI 中的內容僅透過 Power BI 權限進行管理。 顯示標籤時，不會套用任何相關聯的加密設定 (在 [Microsoft 365 安全性中心](https://security.microsoft.com/)或 [Microsoft 365 合規性中心](https://compliance.microsoft.com/)內設定)。 這些設定僅適用於匯出至 Excel、PowerPoint 和 PDF 檔案的資料。
* 在匯出至 Excel、PowerPoint 和 PDF 以外的任何匯出路徑中，**不會**套用敏感度標籤和檔案加密。 Power BI 租用戶系統管理員可停用任何或所有不支援套用和其相關聯檔案加密設定的匯出路徑。

## <a name="sensitivity-labels-in-power-bi"></a>Power BI 中的敏感度標籤

敏感度標籤是在 [Microsoft 365 安全性中心](https://security.microsoft.com/)或 [Microsoft 365 合規性中心](https://compliance.microsoft.com/)建立及管理。

若要存取任一中心的敏感度標籤，請巡覽至 [分類] > [敏感度標籤]。 這些敏感度標籤可供多項 Microsoft 服務使用，例如 Azure 資訊保護、Office 應用程式和 Office 365 服務。

> [!Important]
> 如果您的組織使用 Azure 資訊保護的敏感度標籤，您必須將其[移轉](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)至前列服務之一，才能在 Power BI 中使用這些標籤。

> [!NOTE]
> 僅公用雲端的租用戶支援敏感度標籤；主權雲端等雲端租用戶則不支援這些標籤。

## <a name="how-sensitivity-labels-work-in-power-bi"></a>敏感度標籤在 Power BI 中的運作方式

將敏感度標籤套用至 Power BI 的儀表板、報表、資料集或資料流程時，即類似於將標記套用至該資源，這具有下列優點：
* **可自訂** - 您可以在組織中建立不同等級機密內容的類別，例如個人、公用、一般、機密和高度機密。
* **純文字** - 因為標籤是純文字，所以使用者很容易就能根據敏感度標籤的指導方針，了解如何處理內容。
* **持續性** - 將敏感度標籤套用至內容之後，敏感度標籤會在內容匯出至 Excel、PowerPoint 和 PDF 檔案時伴隨該內容，並成為套用和施行原則的基礎。

這表示敏感度標籤會在內容匯出至 Excel、PowerPoint 和 PDF 檔案時跟隨該內容，並成為套用和施行原則的基礎。

Power BI 租用戶系統管理員可以控制 [Power BI 管理入口網站](service-admin-portal.md)中的[匯出至 Excel](service-admin-portal.md#export-to-excel) 及[匯出至 PowerPoint 和 PDF](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents)。

## <a name="sensitivity-label-example"></a>敏感度標籤範例

以下是 Power BI 中敏感度標籤如何運作的快速範例。
1. 在 Power BI 服務中，**高度機密**的敏感度標籤會套用至報表。

   ![以清單檢視的敏感度標籤](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. 當資料從這份報表匯出到 Excel 檔案時，敏感度標籤和保護也隨之套用至匯出的 Excel 檔案。

   ![敏感度標籤會跟隨內容](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

在 Microsoft Office 應用程式中，敏感度標籤在電子郵件或文件上會顯示為標籤，與上圖中顯示的內容類似。 您也可以指派內容分類 (例如貼紙)，使其得以隨使用及共用的內容在整個 Power BI 中保存及漫遊。 您可以使用此分類產生使用量報告，並查看敏感性內容的活動資料。 根據此資訊，您隨時可以選擇稍後套用保護設定。

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>在 Power BI 中使用敏感度標籤的需求

您必須先完成下列必要條件，才能在 Power BI 中啟用敏感度標籤：
* 請確定已在 [Microsoft 365 安全性中心](https://security.microsoft.com/)或 [Microsoft 365 合規性中心](https://compliance.microsoft.com/)定義敏感度標籤。
* 在 Power BI 中[啟用敏感度標籤](service-security-enable-data-sensitivity-labels.md)。
* 確定使用者擁有[適當的授權](#licensing)。
* 如果搭配 Power BI 使用 Microsoft Cloud App Security，請務必擁有[適當的授權](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing)。

## <a name="protect-content-using-microsoft-cloud-app-security"></a>使用 Microsoft Cloud App Security 保護內容

您可以使用 Microsoft Cloud App Security 來保護 Power BI 的內容免於遭到非預期外洩或入侵。 設定好 Microsoft Cloud App Security 之後，安全性系統管理員即可監視使用者的存取和活動、執行即時的風險分析，以及設定標籤特定的控制項。

例如，組織可以使用 Microsoft Cloud App Security 設定原則，防止使用者將 Power BI 的敏感性資料從下載到非受控裝置。 此種設定可讓使用者保持生產力、從任何地方連線到 Power BI，同時還能使用 Microsoft Cloud App Security 防止有害的使用者動作，全都能即時執行。

**需求**

您必須先滿足下列必要條件，敏感度標籤才可以使用 Microsoft Cloud App Security：
* [必須為租用戶啟用](https://docs.microsoft.com/cloud-app-security/azip-integration) Cloud App Security 和 Azure 資訊保護。
* 應用程式[必須連線到 Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps)。

## <a name="licensing"></a>授權

* 若要在 Power BI 中檢視或套用 Microsoft 資訊保護敏感度標籤，必須具備 Azure 資訊保護進階 P1 或進階 P2 授權。 您可單獨購買 Microsoft Azure 資訊保護，或透過其中一個 Microsoft 授權套件來購買。 如需詳細資訊，請參閱 [Azure 資訊保護定價](https://azure.microsoft.com/pricing/details/information-protection/)。
* 必須滿足[授權需求](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels)，以在 Office 應用程式中檢視與套用標籤。
* 使用者除上述其中一個 Azure 資訊保護授權外，還必須擁有 Power BI Pro 授權，才能將標籤套用至 Power BI 內容。
* 如果您要使用該功能來保護 Power BI 內容免於發生未預期的外洩和違規，您必須擁有 [Microsoft Cloud App Security 的必要授權](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing)。

## <a name="considerations-and-limitations"></a>考量與限制

下列清單提供 Power BI 敏感度標籤的一些限制：

**一般**
* 敏感度標籤只能套用到儀表板、報表、資料集與資料流程。 目前不適用於[編頁報表](../paginated-reports/report-builder-power-bi.md)與活頁簿。
* Power BI 資產的敏感度標籤會顯示在工作區清單、譜系、我的最愛、最近項目或應用程式檢視中；目前不會顯示在 [與我共用] 檢視中。 但請注意，即使看不見套用至 Power BI 資產的標籤，其也一律保存在匯出至 Excel、PowerPoint 與 PDF 檔案的資料上。
* 只有全域 (公用) 雲端中的租用戶，才能使用敏感度標籤。 其他雲端中的租用戶無法使用敏感度標籤。
* 範本應用程式不支援資料敏感度標籤。 擷取與安裝應用程式時，會移除範本應用程式建立者設定的敏感度標籤，而當應用程式更新時，由應用程式取用者新增到已經安裝之範本應用程式的成品中的敏感度標籤會遺失 (重設為不加任何標籤)。
* Power BI 不支援[不可轉寄](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)、[使用者定義](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) 及 [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions) 保護類型的敏感度標籤。 「不可轉寄」和「使用者定義」保護類型指的是 [Microsoft 365 安全性中心](https://security.microsoft.com/)或 [Microsoft 365 合規性中心](https://compliance.microsoft.com/)內定義的標籤。
* 不建議讓使用者在 Power BI 內套用父標籤。 如果將父標籤套用到內容，將資料從該內容匯出至檔案 (Excel、PowerPoint 和 PDF) 的作業就會失敗。 請參閱[子標籤 (分組標籤)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels)。

**匯出**
* 只有在資料匯出至 Excel、PowerPoint 和 PDF 檔案時，才會施行標籤和保護控制項。 將資料匯出至 .csv 或 .pbix 檔案、[使用 Excel 分析] 或任何其他匯出路徑時，不會施行標籤和保護。
* 將敏感度標籤和保護套用至匯出的檔案，並不會將內容標記新增至該檔案。 不過，如果標籤已設定成要套用內容標記，那麼當檔案在 Office 傳統型應用程式中開啟時，Azure 資訊保護的統一標籤用戶端就會自動套用標記。 當您針對傳統型、行動裝置或 Web 應用程式使用內建標籤時，不會自動套用內容標記。 如需詳細資料，請參閱 [Office 應用程式何時套用內容標記和加密](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption)。
* 從 Power BI 匯出檔案的使用者，有權根據敏感度標籤設定來存取與編輯該檔案。 但匯出資料的使用者不會取得檔案擁有者權限。
* 如果將資料匯出至檔案時無法套用標籤，則匯出將會失敗。 若要檢查匯出是否因無法套用標籤而失敗，請按一下標題列中央的報表或儀表板名稱，並在開啟的資訊下拉式清單中查看其是否顯示「無法載入敏感度標籤」。 如果套用的標籤已由安全性管理員解除發佈或刪除，或是因暫時性系統問題而解除發佈或刪除，就可能會發生這種情況。


## <a name="next-steps"></a>後續步驟

本文提供 Power BI 資料保護概觀。 下列文章提供 Power BI 資料保護的詳細資料。 

* [在 Power BI 中啟用資料敏感度標籤](service-security-enable-data-sensitivity-labels.md)
* [在 Power BI 中套用資料敏感度標籤](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [在 Power BI 中使用 Microsoft Cloud App Security 控制項](service-security-using-microsoft-cloud-app-security-controls.md)
* [資料保護計量報表](service-security-data-protection-metrics-report.md)