---
title: 使用 Power BI 連接到 Microsoft Azure Consumption Insights
description: Microsoft Azure Consumption Insights for Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020428"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>使用 Power BI 連接到 Microsoft Azure Consumption Insights
使用 Power BI 內容套件探索並監視 Power BI 服務中的 Microsoft Azure 耗用量資料。 資料會自動每天重新整理一次。

連線到 Power BI 服務的 [Microsoft Azure 使用量見解內容套件](https://app.powerbi.com/getdata/services/azureconsumption)。

> [!NOTE]
> 如需自訂程度更高的安裝程式，請嘗試在 Power BI Desktop 中使用 [Azure 使用量見解連接器](desktop-connect-azure-consumption-insights.md)。

## <a name="how-to-connect"></a>如何連接
1. 在 Power BI 服務中，選取左側瀏覽窗格底部的 [取得資料]  。
   
    ![取得資料](media/service-connect-to-azure-consumption-insights/getdata.png)
2. 在 [服務]  方塊中，選取 [取得]  。
   
   ![取得服務](media/service-connect-to-azure-consumption-insights/services.png)
3. 選取 [Microsoft Azure 使用量見解]  \> [立即取得]  。 
   
   ![立即取得](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. 提供要匯入的月份數資料和 Azure 企業版的註冊號碼。 請參閱以下關於[尋找這些參數](#FindingParams)的詳細資料。
   
    ![連線至 Microsoft Azure 使用量見解](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. 提供連接用的存取金鑰。 您可以在 Azure EA 入口網站中找到您的註冊金鑰。 
   
    ![Microsoft Azure 使用量見解：金鑰](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. 匯入程序會自動開始。 完成時，新的儀表板、報表與模型會出現在 [瀏覽] 窗格中。 選取儀表板以檢視匯入的資料。
   
   ![Microsoft Azure 使用量見解儀表板](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](consumer/end-user-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](consumer/end-user-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但您可以變更重新整理排程，或使用 [立即重新整理]  視需要嘗試重新整理

## <a name="whats-included"></a>包含的內容
Microsoft Azure 使用量見解內容套件包含每月報告資料，其範圍是連接程序期間所提供的月份。 範圍是移動的時段，以便重新整理資料集時，將會更新包含的日期。

## <a name="system-requirements"></a>系統需求
內容套件需要存取 Azure 入口網站中的企業版功能。 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>尋找參數
能夠檢視帳單資訊的 EA Direct、合作夥伴和間接客戶都可以取得 Power BI 報表。 閱讀下文以取得尋找連接流程所有預期值的詳細資料。

**月份數**

* 您要從今天開始匯入資料的月份數 (1-36)。

**註冊號碼**

* 您的 Azure 企業版註冊號碼，您可以在 [Azure 企業入口網站](https://ea.azure.com/)主畫面的 [註冊詳細資料]  中找到它。
  
    ![註冊號碼](media/service-connect-to-azure-consumption-insights/params2.png)

**存取金鑰**

* 您可以在 Azure 企業版入口網站的 [下載使用量]   > [API 存取金鑰]  下找到您的存取金鑰。
  
    ![存取金鑰](media/service-connect-to-azure-consumption-insights/creds2.png)

**其他說明**

* 如需有關設定 Azure 企業版 Power BI 套件的額外說明，請登入 Azure 企業版入口網站並在 [說明]  下檢視 API 說明檔。 您也可以菜 [報表]   -> [下載使用量]   -> [API 存取金鑰]  下找到其他指示。
* 如需自訂程度更高的安裝程式，請嘗試在 Power BI Desktop 中使用 [Azure 使用量見解連接器](desktop-connect-azure-consumption-insights.md)。

## <a name="next-steps"></a>後續步驟

Power BI Desktop 中的 [Azure 使用量見解連接器](desktop-connect-azure-consumption-insights.md)

[取得 Power BI 中的資料](service-get-data.md)

