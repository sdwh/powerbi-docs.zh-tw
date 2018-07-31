---
title: 連接到 Oracle 資料庫
description: 將 Oracle 連接至 Power BI Desktop 所需的步驟和下載
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6e79de6cb2d6b84d47bc878b8d7acae062e9d8e9
ms.sourcegitcommit: f01a88e583889bd77b712f11da4a379c88a22b76
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39326801"
---
# <a name="connect-to-an-oracle-database"></a>連接到 Oracle 資料庫
若要使用 **Power BI Desktop** 連接到 Oracle 資料庫，執行 Power BI Desktop 的電腦上必須安裝正確的 Oracle 用戶端軟體。 您使用的 Oracle 用戶端軟體取決於您安裝的 Power BI Desktop 版本，也就是 **32 位元**版本或 **64 位元**版本。

**支援的版本**：Oracle 9 和更新版本，Oracle 用戶端軟體 8.1.7 版和更新版本。

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>判斷您已安裝的 Power BI Desktop 版本
若要判斷您已安裝的 Power BI Desktop 版本，請選取 [檔案] > [說明] > [關於]，然後檢查 [版本:] 行。 在下圖中，已安裝 64 位元版本的 Power BI Desktop：

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>安裝 Oracle 用戶端
針對 **32 位元**版本的 Power BI Desktop，使用下列連結，下載並安裝 **32 位元**的 Oracle 用戶端︰

* [32 位元的 Oracle Access Components (ODAC) 與 Oracle Developer Tools for Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

針對 **64 位元**版本的 Power BI Desktop，使用下列連結，下載並安裝 **64 位元** 的 Oracle 用戶端︰

* [適用於 Windows x64 的 64 位元 ODAC 12c Release 4 (12.1.0.2.4)](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>連接到 Oracle 資料庫
安裝相符的 Oracle 用戶端驅動程式之後，您可以連接到 Oracle 資料庫。 請採取下列步驟建立連線：

1. 從 [取得資料] 視窗中，選取 [資料庫] > [Oracle 資料庫]
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. 在出現的 [Oracle 資料庫] 對話方塊中，提供伺服器名稱，然後選取 [連接]。 如果需要 SID，您可以使用以下格式來指定：*ServerName/SID*，其中 SID 是資料庫的唯一名稱。 如果 *ServerName/SID* 格式沒有用，請嘗試使用 *ServerName/ServiceName*，其中 ServiceName 是連接時使用的別名。
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)
3. 如果要使用原生資料庫查詢匯入資料，您可以展開 [Oracle 資料庫] 對話方塊的 [進階選項] 區段，然後將查詢置於 [SQL 陳述式] 方塊中。
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. 在 [Oracle 資料庫] 對話方塊中輸入 Oracle 資料庫的資訊之後 (包括選擇性的資訊，例如 SID 或原生資料庫查詢)，請選取 [確定] 進行連線。
5. 如果 Oracle 資料庫需要資料庫使用者認證，出現提示時，請在對話方塊中輸入這些認證。

