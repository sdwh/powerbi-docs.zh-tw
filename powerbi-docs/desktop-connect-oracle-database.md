---
title: 連接到 Oracle 資料庫
description: 將 Oracle 連接至 Power BI Desktop 所需的步驟和下載
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a118cd0874410e538ca8329e0b8c0ed1bdb430b7
ms.sourcegitcommit: 834cad24901f7fd966c4010e36a7904bc120e57f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82149606"
---
# <a name="connect-to-an-oracle-database"></a>連接到 Oracle 資料庫
若要使用 Power BI Desktop 連接到 Oracle 資料庫，則執行 Power BI Desktop 的電腦上必須安裝正確的 Oracle 用戶端軟體。 您使用的 Oracle 用戶端軟體取決於已安裝的 Power BI Desktop 版本：32 位元或 64 位元。

支援的 Oracle 版本： 
- Oracle 9 和更新版本
- Oracle 用戶端軟體 8.1.7 和更新版本

> [!NOTE]
> 如要設定適用於 Power BI 報表伺服器的 Oracle 資料庫，，請參閱 [Oracle 連線類型](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15)一文中的資訊。 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>判斷您已安裝的 Power BI Desktop 版本
若要判斷您已安裝的 Power BI Desktop 版本，請選取 [檔案]   > [說明]   > [關於]  ，然後檢查 [版本]  行。 在下圖中，已安裝 64 位元版本的 Power BI Desktop：

![Power BI Desktop 版本](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>安裝 Oracle 用戶端
- 如需 32 位元版本的 Power BI Desktop，請[下載並安裝 32 位元的 Oracle 用戶端](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)。

- 如需 64 位元版本的 Power BI Desktop，請[下載並安裝 64 位元的 Oracle 用戶端](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)。

## <a name="connect-to-an-oracle-database"></a>連接到 Oracle 資料庫
安裝相符的 Oracle 用戶端驅動程式之後，您可以連接到 Oracle 資料庫。 請採取下列步驟建立連線：

1. 從 [首頁]  索引標籤，選取 [取得資料]  。 

2. 從顯示的 [取得資料]  視窗，依序選取 [更多]  (如有必要) 和 [資料庫]   > [Oracle 資料庫]  ，然後選取 [連接]  。
   
   ![Oracle 資料庫連接](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. 在顯示的 [Oracle 資料庫]  對話方塊中，提供 [伺服器]  的名稱，然後選取 [確定]  。 如果需要 SID，請使用以下格式加以指定：*ServerName/SID*，其中 *SID* 是資料庫的唯一名稱。 如果 *ServerName/SID* 格式沒有用，請使用 *ServerName/ServiceName*，其中 *ServiceName* 是用來連接的別名。


   ![輸入 Oracle 伺服器名稱](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > 如果您無法在此步驟中進行連接，請嘗試在 [伺服器]  欄位中使用下列格式： *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))*
   
3. 如果您想要使用原生資料庫查詢來匯入資料，請將您的查詢放在展開 [Oracle 資料庫]  對話方塊的 [進階選項]  區段時所顯示 [SQL 陳述式]  方塊中。
   
   ![展開 [進階選項]](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. 在 [Oracle 資料庫]  對話方塊中輸入 Oracle 資料庫資訊之後 (包括任何選擇性資訊，例如 SID 或原生資料庫查詢)，請選取 [確定]  進行連接。
5. 如果 Oracle 資料庫需要資料庫使用者認證，出現提示時，請在對話方塊中輸入這些認證。


## <a name="troubleshooting"></a>疑難排解

若您從 Microsoft Store 下載了 Power BI Desktop，則可能因 Oracle 驅動程式問題，而無法連線到 Oracle 資料庫。 若您發生此問題，會傳回錯誤訊息：「未設定物件參考」  。 若要解決此問題，請執行下列其中一個步驟：

* 從[下載中心](https://www.microsoft.com/download/details.aspx?id=58494) (而不是 Microsoft Store) 下載 Power BI Desktop。

* 如果您想要使用來自 Microsoft Store 的版本：請在您的本機電腦上，將 oraons.dll 從 _12.X.X\client_X_ 複製到 _12.X.X\client_X\bin_，其中 _X_ 代表版本和目錄號碼。

如果您在連接到 Oracle 資料庫時，於 Power BI Gateway 中看到錯誤訊息「未設定物件參考」  ，請遵循[管理您的資料來源 - Oracle](service-gateway-onprem-manage-oracle.md) 中的指示進行。

如要使用 Power BI 報表伺服器，請參閱 [Oracle 連線類型](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15)一文中的指引。