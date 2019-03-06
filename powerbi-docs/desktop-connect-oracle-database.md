---
title: 連接到 Oracle 資料庫
description: 將 Oracle 連接至 Power BI Desktop 所需的步驟和下載
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/22/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b28c4ea9b4cacc77a7f98af5bfc006670f40af94
ms.sourcegitcommit: 76772a361e6cd4dd88824b2e4b32af30656e69db
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2019
ms.locfileid: "56892267"
---
# <a name="connect-to-an-oracle-database"></a>連接到 Oracle 資料庫
若要使用 **Power BI Desktop** 連接到 Oracle 資料庫，執行 Power BI Desktop 的電腦上必須安裝正確的 Oracle 用戶端軟體。 您使用的 Oracle 用戶端軟體取決於您安裝的 Power BI Desktop 版本，也就是 **32 位元**版本或 **64 位元**版本。

**支援的版本**：Oracle 9 和更新版本、Oracle 用戶端軟體 8.1.7 和更新版本。

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
2. 在出現的 [Oracle 資料庫] 對話方塊中，提供伺服器名稱，然後選取 [連接]。 如果需要 SID，您可以使用以下格式加以指定︰「伺服器名稱/SID」，其中 SID 是資料庫的唯一名稱。 如果 *ServerName/SID* 格式沒有用，請嘗試使用 *ServerName/ServiceName*，其中 ServiceName 是連接時使用的別名。


   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > 如果您在這個步驟遇到連線問題，請嘗試在 [Server Name] \(伺服器名稱\) 欄位使用此格式：(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))
   
3. 如果要使用原生資料庫查詢匯入資料，您可以展開 [Oracle 資料庫] 對話方塊的 [進階選項] 區段，然後將查詢置於 [SQL 陳述式] 方塊中。
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. 在 [Oracle 資料庫] 對話方塊中輸入 Oracle 資料庫的資訊之後 (包括選擇性的資訊，例如 SID 或原生資料庫查詢)，請選取 [確定] 進行連線。
5. 如果 Oracle 資料庫需要資料庫使用者認證，出現提示時，請在對話方塊中輸入這些認證。


## <a name="troubleshooting"></a>疑難排解

若您從 Microsoft Store 下載了 Power BI Desktop，則可能因 Oracle 驅動程式問題，而無法連線到 Oracle 資料庫。 若您發生此問題，會傳回錯誤訊息「未設定物件參考」。 若要處理此問題，請執行下列其中一項動作：

* 改為從 https://powerbi.microsoft.com/desktop 下載 Power BI Desktop。

* 若要使用來自 Microsoft Store 的版本：請在您的本機電腦上，將 oraons.dll 從 _12.X.X\client_X_ 複製到 _12.X.X\client_X\bin_。 X 代表版本及目錄號碼。
