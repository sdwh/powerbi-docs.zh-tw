---
title: "Power BI 報表伺服器版本資訊"
description: "本主題描述的 Power BI 報表伺服器的限制與問題。"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: asaxton
ms.openlocfilehash: ffd0d1ce38a989121225a666ca4aa924df130216
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="power-bi-report-server-release-notes"></a>Power BI 報表伺服器版本資訊
本主題描述的 Power BI 報表伺服器的限制與問題。

若要下載 Power BI 報表伺服器，以及針對 Power BI 報表伺服器最佳化的 Power BI Desktop，請移至[使用 Power BI 報表伺服器的內部部署報表](https://powerbi.microsoft.com/report-server/)。

## <a name="october-2017"></a>2017年 10 月
* Power BI 報表中已匯入資料的支援
* 在入口網站內檢視 Excel 活頁簿的能力。 這是透過設定 Office Online Server 所完成。
* 新 Power BI 資料表和矩陣視覺效果的支援。
* REST API 支援

## <a name="june-2017"></a>2017 年 6 月
* 2017 年 6 月沒有新項目。

## <a name="may-2017"></a>2017 年 5 月
* Power BI 報表必須使用針對 Power BI 報表伺服器最佳化的 Power BI Desktop 建立，才能與 Power BI 報表伺服器搭配使用。 您可以從此頁面頂端的 [下載] 連結來下載 Power BI Desktop。
* Power BI 報表僅支援即時連接至 Analysis Services (表格式或多維度)。
* 不支援 R 視覺效果。

**問題和客戶影響︰**如果您在相同電腦上同時有 SQL Server Reporting Services 和 Power BI 報表伺服器，並解除安裝其中一個，您將無法再使用報表伺服器組態管理員連接至其餘的報表伺服器。

**因應措施**：若要解決此問題，您必須在解除安裝其中一個伺服器之後執行下列作業。

1. 以系統管理員模式啟動命令提示字元。
2. 移至剩餘的報表伺服器安裝所在的目錄。
   
    *Power BI 報表伺服器的預設位置︰C:\Program Files\Microsoft Power BI Report Server*
   
    *SQL Server Reporting Services 的預設位置︰C:\Program Files\Microsoft SQL Server Reporting Services*
3. 然後移至下一個資料夾。 這會是 *SSRS* 或 *PBIRS*，取決於剩餘的項目。
4. 移至 [WMI] 資料夾。
5. 執行下列命令：
   
    ```
    regsvr32 /i ReportingServicesWMIProvider.dll
    ```
   
    如果看到下列錯誤，可予以忽略。
   
    ```
    The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
    ```

## <a name="next-steps"></a>後續步驟
[Power BI 報表伺服器的新功能](whats-new.md)  
[使用者手冊](user-handbook-overview.md)  
[系統管理員手冊](admin-handbook-overview.md)  
[快速入門︰安裝 Power BI 報表伺服器](quickstart-install-report-server.md)  
[安裝報表產生器](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[下載 SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

