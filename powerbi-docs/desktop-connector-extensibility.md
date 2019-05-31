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
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412990"
---
# <a name="connector-extensibility-in-power-bi"></a>Power BI 中的連接器擴充性

在 Power BI 中，客戶和開發人員可以擴充它們連線在許多方面的資料來源。 使用現有的連接器和泛用資料來源 （例如 ODBC、 OData、 Oledb、 Web、 CSV、 XML、 JSON）。 或者，開發人員建立資料延伸模組，稱為**自訂連接器**，並將其**認證連接器**。

目前，您啟用**自訂連接器**使用功能表，可讓您安全地控制您想要讓您的系統上執行的自訂程式碼層級。 您可以選擇所有的自訂連接器或只有連接器認證，並由 Microsoft 分散式**取得資料** 對話方塊。

## <a name="custom-connectors"></a>自訂連接器

**自訂連接器**可以包含各種不同的可能性，範圍從小型的 Api 重要到您的企業，大型的產業特定服務由 Microsoft 尚未發行的連接器。 許多連接器會分散廠商。 如果您需要為特定的資料連接器，您應連絡廠商。

若要使用**自訂連接器**，將它放在 *\[文件]\\Power BI Desktop\\自訂連接器*資料夾，然後調整安全性設定中所述下一節。

您不需要調整安全性設定來使用**認證的連接器**。

## <a name="data-extension-security"></a>資料延伸模組安全性

若要變更的資料延伸模組的安全性設定，在**Power BI Desktop**選取**檔案 > 選項及設定 > 選項 > 安全性**。

![控制是否要載入的資料延伸模組的安全性選項的自訂連接器](media/desktop-connector-extensibility/data-extension-security-1.png)

在 [資料延伸模組]  下，您可以從兩種安全性層級中選取：

* (建議) 僅允許認證的延伸模組載入
* (不建議) 允許任何延伸模組載入而不警告

如果您計劃使用**自訂連接器**或您或協力廠商所開發的連接器，您必須選取 **"(Not Recommended) 允許任何擴充功能載入而不發出警告 」** 。 我們不建議此安全性設定，除非您絕對信任您的自訂連接器。 因為裡面的程式碼可以處理認證，包括其傳送 HTTP，並忽略隱私權等級。

在 **」 （建議選項） 」** 安全性設定，如果您的系統上沒有自訂連接器時，會出現錯誤，描述因為安全性無法載入連接器。

![一個對話方塊，描述此案例的 TripPin 中的安全性設定，因為無法載入的自訂連接器](media/desktop-connector-extensibility/data-extension-security-2.png)

若要解決此錯誤，並使用這些連接器，變更 安全性設定，以便 **"(Not Recommended) 允許任何擴充功能載入而不發出警告 」** 設定稍早所述。 然後，重新啟動**Power BI Desktop**。

## <a name="certified-connectors"></a>認證的連接器

資料延伸模組的有限的子集會被視為**Certified**。 存取中的認證的連接器**取得資料** 對話方塊。 但是，第三方開發人員建立的連接器會負責其維護和支援。 雖然 Microsoft 散發連接器，它不負責其效能或持續函式。

如果您想要認證自訂連接器，請要求您的廠商連絡 dataconnectors@microsoft.com。
