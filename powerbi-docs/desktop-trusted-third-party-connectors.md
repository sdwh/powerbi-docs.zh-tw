---
title: 受信任的 Power BI 中的第三方連接器
description: 如何信任簽署的協力廠商連接器，在 Power BI 中
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607785"
---
# <a name="trusting-third-party-connectors"></a>信任的協力廠商連接器

## <a name="why-do-you-need-trusted-third-party-connectors"></a>您為何需要受信任的協力廠商連接器？

在 Power BI 中，我們通常建議在較高的層級，這是為了避免不由 Microsoft 認證的程式碼的載入，讓您 「 資料延伸模組安全性 」 層級。 不過，可能有許多情況下，您要載入特定的連接器，您已經撰寫，是 1 或顧問或 Microsoft 憑證路徑的外部廠商提供給您的項目。

給定連接器的開發人員可以使用憑證進行簽署，並提供您與您要安全地載入它，而不會降低您的安全性設定所需的資訊。

如果您想要深入了解的安全性設定，您可以閱讀它們[此處](https://docs.microsoft.com/power-bi/desktop-connector-extensibility)。

## <a name="using-the-registry-to-trust-third-party-connectors"></a>使用登錄來信任協力廠商連接器

信任協力廠商連接器，在 Power BI，即可列出您想要指定的登錄值中的信任憑證的指紋。 如果此指紋符合您想要載入連接器上憑證的指紋，您將能夠將其載入 Power BI 的 [建議] 安全性層級。 

登錄路徑是 HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop。 請確定路徑存在，或建立它。 我們選擇此位置，因為它主要是 IT 原則，以及需要本機電腦系統管理存取權，若要編輯受控制。 

![不具信任的協力廠商索引鍵的 power BI Desktop 登錄設定](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

新增了上面指定的路徑下的新值。 類型應該是 「 多字串值 「 (REG_MULTI_SZ)，和它應該呼叫 「 TrustedCertificateThumbprints" 

![Power BI Desktop 登錄中以受信任的協力廠商連接器，但不含索引鍵的項目](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

新增您想要信任的憑證的指紋。 您可以新增多個憑證，利用 「 \0"作為分隔符號，或在登錄編輯器中，右邊按一下-> 修改，並放在新行上的每個憑證指紋。 範例指紋是取自自我簽署憑證。 

 ![受信任的協力廠商金鑰組的 power BI Desktop 登錄](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

如果您已正確，遵循指示進行，而且會由您的開發人員提供適當的憑證指紋，您現在應該能夠安全地使用相關聯的憑證簽署信任連接器。

## <a name="how-to-sign-connectors"></a>如何登入連接器

如果您或開發人員必須登入，您會有的連接器，您可以閱讀它 Power Query 文件中[此處](https://docs.microsoft.com/power-query/handlingconnectorsigning)。
