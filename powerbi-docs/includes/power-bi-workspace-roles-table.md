---
title: Power BI 工作區角色
description: Power BI 工作區角色資料表
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781334"
---
以下是四種角色的功能：系統管理員、成員、參與者和檢視者。 除了檢視和互動功能以外，所有這些功能都需要 Power BI Pro 授權。

|功能   | 系統管理員  | 成員  | 參與者  | 檢視者 |
|---|---|---|---|---|
| 更新和刪除工作區。  | X  |   |   |   | 
| 新增/移除人員，包括其他系統管理員。  | X  |   |   |   |
| 新增具有較低權限的成員或其他人。  |  X | X  |   |   |
| 發佈和更新應用程式。 |  X | X  |   |   |
| 共用項目或共用應用程式。<sup>1</sup> |  X | X  |   |   |
| 允許其他人再次共用項目。<sup>1</sup> |  X | X  |   |   |
| 在同事的首頁上精選應用程式 |  X | X  |   |   |
| 在同事的首頁上精選儀表板和報表 |  X | X  | X |   |
| 建立、編輯和刪除工作區中的內容。  |  X | X  | X  |   |
| 將報表發佈至工作區、刪除內容。  |  X | X  | X  |   |
| 根據此工作區中的資料集，在另一個工作區中建立報表。<sup>1</sup> |  X | X  | X  |   |
| 複製報表。<sup>2</sup> | X | X | X |  |
| 透過內部部署閘道排程資料重新整理。<sup>3</sup> | X | X | X |  |
| 修改閘道連線設定。<sup>3</sup> | X | X | X |  |
| 檢視項目並與其互動。<sup>4</sup> |  X | X  | X  | X  |
| 讀取儲存在工作區資料流程中的資料 | X | X | X | X |

1. 如果參與者和檢視者都有再次共用權限，即可在工作區中共用項目。
2. 若要複製報表，並根據此工作區的資料集在另一個工作區中建立報表，則需要有此資料集的 [建置] 權限。 具有系統管理員、成員和參與者角色的使用者要透過其工作區角色取得 [建置] 權限，才能取得此工作區中的資料集。
3. 請記住，您也需要有閘道的權限。 這些權限是在其他位置管理，不受工作區角色和權限影響。 如需詳細資料，請參閱[管理內部部署閘道](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) (機器翻譯)。
4. 如果項目位於 Premium 容量的工作區中，則即使沒有 Power BI Pro 授權，您也可以在 Power BI 服務中檢視項目並與其互動。

