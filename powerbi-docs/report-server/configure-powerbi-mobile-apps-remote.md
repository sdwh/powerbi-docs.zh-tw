---
title: 從遠端設定 Power BI iOS 行動裝置應用程式對報表伺服器的存取
description: 了解如何為報表伺服器從遠端設定 iOS 行動裝置應用程式。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/22/2018
ms.author: maggies
ms.openlocfilehash: bbade67c9510b8d316364d991c09444712309514
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722170"
---
# <a name="configure-power-bi-ios-mobile-app-access-to-a-report-server-remotely"></a>從遠端設定 Power BI iOS 行動裝置應用程式對報表伺服器的存取

在本文中，您可以了解如何使用組織的 MDM 工具來設定 Power BI iOS 行動裝置應用程式對報表伺服器的存取。 若要進行此設定，IT 系統管理員會使用要推送到應用程式的必要資訊來建立應用程式組態原則。 

 之後，因為報表伺服器連線已經設定好，Power BI iOS 行動裝置應用程式使用者要連線到組織的報表伺服器就更加輕鬆。 


## <a name="create-the-app-configuration-policy-in-mdm-tool"></a>在 MDM 工具中建立應用程式組態原則 

若您是系統管理員，請在 Microsoft Intune 中遵循這些步驟來建立應用程式組態原則。 應用程式組態原則的建立步驟與體驗，在其他 MDM 工具中可能不同。 

1. 與您的 MDM 工具連線。 
2. 建立新的應用程式組態原則並為其命名。 
3. 選擇要將此應用程式組態原則發佈給哪些使用者。 
4. 建立機碼值組。 

下表提供各組的詳細說明。

|金鑰  |類型  |描述  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ServerURL | 字串 | 報表伺服器 URL </br> 開頭應為 http/https |
| com.microsoft.powerbi.mobile.ServerUsername | 字串 | [選擇性] </br> 用於與伺服器連線的使用者名稱。 </br> 若沒有此名稱，應用程式會提示使用者鍵入用於連線的使用者名稱。| 
| com.microsoft.powerbi.mobile.ServerDisplayName | 字串 | [選擇性] </br> 預設值為「報表伺服器」 </br> 應用程式中用來代表伺服器的易記名稱 | 
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolean | 預設值為 True </br> 若設為 “True”，這會覆寫任何已在行動裝置中的報表伺服器定義 (已設定的現有伺服器將會刪除)。 </br> Override 設為 True 也會讓使用者無法移除該組態。 </br> 設為 “False” 則會新增推送的值，保留任何現有設定。 </br> 若行動應用裝置中已設定相同的伺服器 URL，應用程式就會保留該組態的原樣，而且不會要求使用者為相同的伺服器重新驗證。 |

以下是使用 Intune 設定設定原則的範例。

![Intune 組態設定](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configuration-settings.png)

## <a name="end-users-connecting-to-a-report-server"></a>終端使用者連線到報表伺服器

在您發佈應用程式組態原則後，為該原則而定義的發佈清單中使用者和裝置，在啟動 Power BI iOS 行動裝置應用程式時，會有以下體驗。 

1. 他們會看到訊息顯示行動裝置應用程式已設有報表伺服器，然後點選 [登入]。

    ![登入報表伺服器](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-sign-in.png)

2.  在 [連線到伺服器] 頁面上，報表伺服器的詳細資料已填入。 他們會點選 [連線]。

    ![報表伺服器詳細資料已填入](media/configure-powerbi-mobile-apps-remote/power-bi-ios-remote-configure-connect-server.png)

3. 他們會鍵入密碼以進行驗證，然後點選 [登入]。 

    ![報表伺服器詳細資料已填入](media/configure-powerbi-mobile-apps-remote/power-bi-config-server-address.png)

現在，他們可以檢視儲存在報表伺服器上的 KPI 和 Power BI 報表，並與其互動。

## <a name="next-steps"></a>後續步驟
[系統管理員概觀](admin-handbook-overview.md)  
[安裝 Power BI 報表伺服器](install-report-server.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

