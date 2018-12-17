---
title: 解決 Power BI Desktop 中的 Access 和 .XLS 匯入問題
description: 解決 Power BI Desktop 和 Power Query 中匯入 Access 資料庫和 .XLS 試算表的問題
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: a1a350a8348dce5ba2553873077a0dfb102a187c
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024721"
---
# <a name="resolve-issues-importing-access-and-xls-files-in-power-bi-desktop"></a>解決 Power BI Desktop 中匯入 Access 和 .XLS 檔案的問題
在 **Power BI Desktop** 中，**Access 資料庫**和舊版的 **Excel 活頁簿** (Excel 97-2003 的 .XLS 檔案類型) 都使用「Access 資料庫引擎」。 有三種常見的情況會妨礙 Access 資料庫引擎正常運作：

## <a name="situation-1-no-access-database-engine-installed"></a>狀況 1：未安裝 Access 資料庫引擎
當 Power BI Desktop 錯誤訊息指出未安裝 Access 資料庫引擎時，您必須安裝符合 Power BI Desktop 版本的 Access 資料庫引擎版本 (32 位元或 64 位元)。 您可以從[下載頁面](http://www.microsoft.com/download/details.aspx?id=13255)安裝 Access 資料庫引擎。

>[!NOTE]
>如果安裝的 Access 資料庫引擎位元版本與 Microsoft Office 安裝的位元版本不同，Office 應用程式就不能使用 Access 資料庫引擎。

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>狀況 2：Access 資料庫引擎位元版本 (32 位元或 64 位元) 和 Power BI Desktop 的位元版本不同
這種情況通常發生在安裝的 Microsoft Office 版本是 32 位元，而安裝的 Power BI Desktop 版本是 64 位元。 相反的情況也可能發生，並且在兩個案例中都有位元版本不符的情況發生 (如果您使用 Office 365 訂閱，請參閱**情況 3** 以了解不同問題和解決方式)。 下列解決方案的任何一項，都可以解決位元版本不符的錯誤︰

1. 將 Power BI Desktop 版本變更為符合 Microsoft Office 安裝的位元版本。 若要變更 Power BI Desktop 的位元版本，請解除安裝 Power BI Desktop，然後再安裝符合 Office 安裝的 Power BI Desktop 版本。 若要選取 Power BI Desktop 版本，請在 Desktop 的下載頁面上選取 [進階下載選項] 。
   
   ![](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
   在出現的下載頁面上選擇您的語言，然後選取 [下載]  按鈕。 在出現的畫面上，如需 32 位元版本請選取 PBIDesktop.msi 旁邊的核取方塊，如需 64 位元版本請選取 PBIDesktop_x64.msi 旁邊的核取方塊。 下面的畫面中選取了 64 位元版本。
   
   ![](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >使用 32 位元版的 Power BI Desktop 時，可能會在建立超大型資料模型時發生記憶體不足的問題。
2. 將 Microsoft Office 版本變更為符合 Power BI Desktop 安裝的位元版本。 若要變更 Microsoft Office 的位元版本，請先解除安裝Office，然後再安裝符合 Power BI Desktop 安裝的 Office 版本。
3. 如果在嘗試開啟 .XLS 檔案 (Excel 97-2003 活頁簿) 時發生錯誤，您可以在 Excel 中開啟 .XLS 檔案，並將它另存為 .XLSX 檔案，以避免使用 Access 資料庫引擎。
4. 如果前面三個解決方案皆不可行，您可以安裝兩個版本的 Access 資料庫引擎，但這 *不* 是建議的解決方法。 安裝兩個版本會解決 Power Query for Excel 和 Power BI Desktop 的這個問題，但會造成任何預設自動使用先安裝之 Access 資料庫引擎位元版本的應用程式錯誤和問題。 若要安裝 Access 資料庫引擎的兩種位元版本，請[下載](http://www.microsoft.com/download/details.aspx?id=13255)兩個版本，然後使用 */passive* 參數分別執行。 例如：
   
       c:\users\joe\downloads\AccessDatabaseEngine.exe /passive
   
       c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive

## <a name="situation-3-trouble-using-access-or-xls-files-with-an-office-365-subscription"></a>狀況 3︰無法搭配 Office 365 訂閱使用 Access 或 .XLS 檔案
如果您使用 Office 365 訂閱，不論是 **Office 2013** 或 **Office 2016**，Access 資料庫引擎提供者都註冊於虛擬登錄位置中，「僅」能由 Office 處理序存取。 因此，Mashup Engine (負責執行非 Office 365 的 Excel 和 Power BI Desktop) 不是 Office 處理序，因此無法使用 Access 資料庫引擎提供者。

若要解決這種情況，您可以[下載並安裝 Access 資料庫引擎可轉散發套件](http://www.microsoft.com/download/details.aspx?id=13255)，但與 Power BI Desktop 安裝的位元版本需相符 (如需有關位元版本的詳細資訊，請參閱稍早的章節)。

## <a name="other-situations-that-cause-import-issues"></a>造成匯入問題的其他情況
我們致力於將 Access 或 .XLS 檔案所發生的問題涵蓋在本文中。 如果您遇到沒有涵蓋在本文中的問題，請將問題的相關提問提交至 [Power BI 支援](https://powerbi.microsoft.com/support/)。 我們經常檢視可能會影響眾多客戶的問題，並將它們包含在我們的文章內。

