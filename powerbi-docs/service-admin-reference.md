---
title: 用於管理 Power BI 的 PowerShell Cmdlet、REST API 和 .NET SDK
description: 了解透過指令碼和程式設計 API 管理 Power BI 的方式。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: ffb2ae077add5756af63f07d8f3da830e075e0b4
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36945234"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>用於管理 Power BI 的 PowerShell Cmdlet、REST API 和 .NET SDK
Power BI 可讓系統管理員使用 PowerShell Cmdlet 撰寫一般工作的指令碼。 它也會公開 REST API 並提供 .NET SDK 來開發管理解決方案。 本主題顯示 Cmdlet 清單以及對應 SDK 方法和 REST API 端點。 如需詳細資訊，請參閱：

  - PowerShell [下載](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/)和[文件](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
  - REST API [文件](https://docs.microsoft.com/rest/api/power-bi/admin)
  - .NET SDK [下載](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) 


| **Cmdlet 名稱** | **SDK 方法** | **REST API 端點** | **描述** |
| --- | --- | --- | --- |
| **Get-PowerBIDatasource** | Datasets\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | 取得指定資料集的資料來源。 |
| **Get-PowerBIDataset** | Datasets\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | 取得 Power BI 租用戶中的完整資料集清單。 |
| **Get-PowerBIWorkspace** | Groups\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | 取得 Power BI 租用戶中的完整工作區清單。 |
| **Add-PowerBIWorkspaceUser** | Groups\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | 將使用者新增為指定工作區的成員。 |
| **Remove-PowerBIWorkspaceUser** | Groups\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | 從指定工作區的成員資格清單中移除使用者。 |
| **Restore-PowerBIWorkspace** | Groups\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | 還原已刪除的工作區。 |
| **Set-PowerBIWorkspace** | Groups\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | 更新指定工作區的屬性。 |
| **Get-PowerBIDataset -WorkspaceId** | Groups\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | 取得指定工作區內的資料集。 |
| **Export-PowerBIReport** | Reports\_ExportReportAsAdmin | N/A | 將指定的報表匯出至本機檔案。 |
| **Get-PowerBIReport** | Reports\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | 取得 Power BI 租用戶中的完整報表清單。 |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | 取得 Power BI 租用戶中的完整儀表板清單。 |
| **Get-PowerBIDashboard -WorkspaceId** | Groups\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | 取得指定工作區內的儀表板。 |
| **Get-PowerBITile -DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | 取得指定儀表板的圖格。 |
| **Get-PowerBIReport -WorkspaceId** | Groups\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | 取得指定工作區內的報表。 |
| **Get-PowerBIImport** | Imports\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | 取得 Power BI 租用戶中的完整匯入清單。 |
| **Connect-PowerBIServiceAccount** | N/A | N/A | 登入 Power BI 並啟動工作階段。 |
| **Disconnect-PowerBIServiceAccount** | N/A | N/A | 登出 Power BI 並關閉現有工作階段。 |
| **Invoke-PowerBIRestMethod** | N/A | N/A | 將任意 REST API 呼叫傳送給 Power BI。 |
| **Get-PowerBIAccessToken** | N/A | N/A | 取得工作階段中的 Power BI 存取權杖。 |
| **Resolve-PowerBIError** | N/A | N/A | 取得 Cmdlet 呼叫失敗的詳細錯誤資訊。 |