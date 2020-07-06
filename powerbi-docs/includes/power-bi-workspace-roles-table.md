---
title: Power BI 工作區角色
description: Power BI 工作區角色資料表
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 06/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 9ddf9df0feaed2a2a0177d11e9b36f34135801c6
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365327"
---
|功能   | 系統管理員  | 成員  | 參與者  | 檢視者 |
|---|---|---|---|---|
| 更新和刪除工作區。  |  |   |   |   | 
| 新增/移除人員，包括其他系統管理員。  |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| 允許參與者更新工作區的應用程式  |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| 新增具有較低權限的成員或其他人。  |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 發佈和變更應用程式的權限 |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 更新應用程式。 |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |  如果允許 <sup>1</sup>  |   |
| 共用項目或共用應用程式。<sup>2</sup> |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 允許其他人再次共用項目。<sup>2</sup> |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 在同事的首頁上精選應用程式 |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| 在同事的首頁上精選儀表板和報表 |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| 建立、編輯和刪除工作區中的內容。  |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| 將報表發佈至工作區、刪除內容。  |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| 根據此工作區中的資料集，在另一個工作區中建立報表。<sup>2</sup> |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| 複製報表。<sup>3</sup> | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| 透過內部部署閘道排程資料重新整理。<sup>4</sup> | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| 修改閘道連線設定。<sup>4</sup> | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| 檢視項目並與其互動。<sup>5</sup> |  ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| 讀取儲存在工作區資料流程中的資料 | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) | ![「是」勾選記號](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> 參與者可以更新應用程式中繼資料，但不能發佈新的應用程式或變更具有應用程式權限的人員 (如果[工作區管理員將此權限委派給參與者](../collaborate-share/service-create-the-new-workspaces.md#security-settings))。

<sup>2</sup> 如果參與者和檢視者都有再次共用權限，即可在工作區中共用項目。

<sup>3</sup> 若要複製報表，並根據此工作區的資料集在另一個工作區中建立報表，則需要有[此資料集的建置權限](../connect-data/service-datasets-build-permissions.md)。 具有系統管理員、成員和參與者角色的使用者要透過其工作區角色自動取得建置權限，才能取得此工作區中的資料集。

<sup>4</sup> 請記住，您也需要有閘道的權限。 這些權限是在其他位置管理，不受工作區角色和權限影響。 如需詳細資料，請參閱[管理內部部署閘道](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) (機器翻譯)。

<sup>5</sup> 如果項目位於 Premium 容量的工作區中，則即使沒有 Power BI Pro 授權，您也可以在 Power BI 服務中檢視項目並與其互動。
