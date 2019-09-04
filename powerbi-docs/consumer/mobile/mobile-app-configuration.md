---
title: Power BI iOS 應用程式組態設定
description: 如何使用 MDM 工具自訂 Power BI 用於 iOS 的行為
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: bc9c6dd8cd892ab0304cc5a99a3bb780486f32f0
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160169"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>使用行動裝置管理 (MDM) 工具從遠端設定 Power BI iOS 應用程式

適用於 iOS 的 Power BI 行動裝置應用程式支援可讓 Office 365 和 Intune 等行動裝置管理 (MDM) 之管理員自訂應用程式行為的應用程式設定。

適用於 iOS 的 Power BI 行動裝置應用程式支援下列設定案例：

- 報表伺服器設定
- 資料保護設定

## <a name="report-server-configuration"></a>報表伺服器設定

Power BI iOS 應用程式可讓管理員使用已註冊的裝置從遠端「推送」報表伺服器設定。

| 索引鍵 | 類型 | 描述 |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | 字串 | 報表伺服器 URL。<br><br>開頭應為 http/https。|
| com.microsoft.powerbi.mobile.ServerUsername | 字串 | [選擇性]<br><br>用於與伺服器連線的使用者名稱。<br><br>若沒有此名稱，應用程式會提示使用者鍵入用於連線的使用者名稱。|
| com.microsoft.powerbi.mobile.ServerDisplayName | 字串 | [選擇性]<br><br>預設值為「報表伺服器」<br><br>應用程式中用來代表伺服器的易記名稱。 |
| com.microsoft.powerbi.mobile.OverrideServerDetails | 布林值 | [選擇性]<br><br>預設值為 True。 當其設定為 True 時，會覆寫已在行動裝置中的所有報表伺服器定義。 將會刪除已設定的現有伺服器。 Override 設為 True 也會讓使用者無法移除該組態。<br><br>設為 False 則會新增推送的值，保留任何現有設定。 如果在行動裝置應用程式中已設定了相同的伺服器 URL，應用程式就會脫離該設定的原狀。 應用程式不會要求使用者重新驗證相同的伺服器。 |

## <a name="data-protection-setting"></a>資料保護設定

Power BI iOS 應用程式可讓管理員自訂安全性和隱私權設定的預設設定。 您可以強制使用者在存取 Power BI 應用程式時提供其 Face ID、Touch ID 或密碼。

| 索引鍵 | 類型 | 描述 |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | 布林值 | 預設值為 False。 <br><br>可能需要生物識別技術 (例如 TouchID 或 FaceID)，才能讓使用者存取其裝置上的應用程式。 如果需要，除了使用驗證，還會使用生物識別技術。<br><br>如果使用應用程式防護原則，Microsoft 建議停用此設定以防止雙重存取提示。 |

## <a name="deploying-app-configuration-settings"></a>部署應用程式組態設定

下列步驟可讓您建立應用程式設定原則。 建立設定原則之後，您可以將其設定指派給使用者群組。

1. 與您的 MDM 工具連線。

2. 建立新的應用程式組態原則並為其命名。

3. 選擇要將此應用程式組態原則發佈給哪些使用者。

4. 為您要推送到使用者的設定建立金鑰/值組。

Intune 入口網站可讓管理員透過應用程式設定原則，輕鬆地將這些設定部署到 Power BI iOS 應用程式。
不過，支援任何 MDM 提供者。 如果您不想使用 Intune，您必須參考 MDM 文件以了解如何部署這些設定。

## <a name="next-steps"></a>後續步驟

* 下載 [Power BI iPhone 行動裝置應用程式](http://go.microsoft.com/fwlink/?LinkId=522062)
* 在 Twitter 上關注 [@MSPowerBI](https://twitter.com/MSPowerBI)
* 加入 [Power BI 社群](http://community.powerbi.com/)的交談
