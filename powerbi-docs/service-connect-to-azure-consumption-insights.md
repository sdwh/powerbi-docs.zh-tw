---
title: 使用 Power BI 連接到 Microsoft Azure Consumption Insights
description: Microsoft Azure Consumption Insights for Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222135"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>使用 Power BI 連接到 Microsoft Azure Consumption Insights
使用 Power BI 內容套件探索並監視 Power BI 中的 Microsoft Azure 耗用量資料。 資料會自動重新整理一天一次。

連接到 Power BI 的 [Microsoft Azure Consumption Insights 內容套件](https://app.powerbi.com/getdata/services/azureconsumption)。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. 在 [服務]  方塊中，選取 [取得]  。
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. 選取  **Microsoft Azure Consumption Insights** \> **立即取得**。 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. 提供要匯入的月份數資料和 Azure 企業版的註冊號碼。 請參閱以下關於[尋找這些參數](#FindingParams)的詳細資料。
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. 提供連接用的存取金鑰。 您可以在 Azure EA 入口網站中找到您的註冊金鑰。 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. 匯入程序會自動開始。 完成時，新的儀表板、 報表和模型就會出現在瀏覽窗格中。 選取儀表板以檢視匯入的資料。
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](consumer/end-user-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](consumer/end-user-tiles.md)，開啟基礎報表。
* 雖然您的資料集排程為每日重新整理，您可以變更重新整理排程，或嘗試重新整理視需要使用**立即重新整理**

## <a name="whats-included"></a>包含的內容
Microsoft Azure Consumption Insights 內容套件包含每月報告連接時所提供的月份範圍的資料。 範圍會是移動的視窗中，因此當重新整理資料集，會更新包含的日期。

## <a name="system-requirements"></a>系統需求
內容套件需要存取 Azure 入口網站內的企業功能。 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>尋找參數
Power BI 報表可供 EA Direct、 合作夥伴和間接客戶可以檢視帳單資訊。 閱讀下面有關尋找每個值必須是連接流程的詳細資料。

**月份數**

* 從今天開始您想要匯入資料的月份 (1 到 36) 數目。

**註冊號碼**

* 您可以在中找到的 Azure 企業版註冊號碼[Azure 企業版入口網站](https://ea.azure.com/)下方的主畫面**註冊詳細資料**。
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**存取金鑰**

* 您可以找到在 Azure 企業版入口網站中，您的存取金鑰底下**下載使用量** > **API 存取金鑰**。
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**其他說明**

* 如需其他說明 Azure 企業版 Power BI 套件設定，登入 Azure 企業版入口網站並檢視下的 API 說明檔案**協助**。 您也可以找到下的取得其他指示**報表** -> **下載使用量** -> **API 存取金鑰**。

## <a name="next-steps"></a>後續步驟
[開始使用 Power BI](service-get-started.md)

[取得 Power BI 中的資料](service-get-data.md)

