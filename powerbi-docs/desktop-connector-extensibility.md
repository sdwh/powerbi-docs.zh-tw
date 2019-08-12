---
title: Power BI 中的連接器擴充性
description: 連接器擴充性功能、安全性設定和認證的連接器
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 7d5d743dda31d05df0beb528648c5a43ffc6b335
ms.sourcegitcommit: 32a44dd17a44ccfd4a2d86a0d235251c2fda1c5c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702117"
---
# <a name="connector-extensibility-in-power-bi"></a>Power BI 中的連接器擴充性

在 Power BI 中，客戶和開發人員可透過許多方式延伸他們所連線的資料來源。 他們可以使用現有連接器和一般資料來源 (例如 ODBC、OData、Oledb、Web、CSV、XML 和 JSON)。 或者，開發人員可以建立資料延伸模組 (稱為**自訂連接器**)，然後將它們設為**經過認證的連接器**。

目前，您可以透過功能表啟用**自訂連接器**，該功能表可讓您安全地控制您希望允許在系統上執行的自訂程式碼層級。 您可以在 [取得資料]  對話方塊中選擇所有自訂連接器，或是僅限由 Microsoft 散發且認證的連接器。

## <a name="custom-connectors"></a>自訂連接器

**自訂連接器**可包含各種可能性，從對您商務不可或缺的小型 API，到 Microsoft 尚未發行連接器的大型產業特定服務。 廠商也會散發許多連接器。 若您需要特定的資料連接器，建議您連絡廠商。

若要使用**自訂連接器**，請將它們放在 *\[Documents]\\Power BI Desktop\\Custom Connectors* 資料夾中，然後遵循下一節中的描述來調整安全性設定。

您不需要調整安全性設定來使用**認證的連接器**。

## <a name="data-extension-security"></a>資料延伸模組安全性

若要變更資料延伸模組安全性設定，請在 **Power BI Desktop** 中，選取 [檔案] > [選項和設定] > [選項] > [安全性]  。

![使用資料延伸模組安全性選項控制是否想要載入自訂連接器](media/desktop-connector-extensibility/data-extension-security-1.png)

在 [資料延伸模組]  下，您可以從兩種安全性層級中選取：

* (建議) 僅允許認證的延伸模組載入
* (不建議) 允許任何延伸模組載入而不警告

如果您計劃使用**自訂連接器**，或是您或協力廠商開發的連接器，您必須選取 [(不建議) 允許任何延伸模組載入而不警告]  。 除非您絕對信任您的自訂連接器，否則我們不建議使用此安全性設定。 因為，其中的程式碼可能會處理認證，包括透過 HTTP 傳送它們及忽略隱私權層級等。

在 [(建議)]  安全性設定中，若您的系統上有自訂連接器，您會收到錯誤「下列連接器尚未經過認證，因此我們無法驗證您可以安全地使用該連接器」，其後附帶無法安全載入的連接器清單。

![描述因為安全性設定而無法載入自訂連接器的對話方塊，在此案例中為 TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

若要在不變更安全性的情況下解決錯誤，請從您的 'Custom Connectors' 資料夾中移除未經簽署的連接器。

若要解決錯誤並使用那些連接器，請將您的安全性設定變更為 [(不建議) 允許任何延伸模組載入而不警告]  設定，如先前所述。 然後，請重新啟動 **Power BI Desktop**。

## <a name="certified-connectors"></a>認證的連接器

有限且視為**通過認證**的部分資料延伸模組。 請在 [取得資料]  對話方塊中存取經過認證的連接器。 但是，建立連接器的協力廠商開發人員需負責其維護和支援。 雖然 Microsoft 會散發這些連接器，但 Microsoft 不會負責其效能或功能的持續性。

如果您想要認證自訂連接器，請要求您的廠商連絡 dataconnectors@microsoft.com。
