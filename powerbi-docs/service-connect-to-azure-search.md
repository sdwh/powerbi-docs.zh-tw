---
title: 使用 Power BI 連接到 Azure 搜尋服務
description: Power BI 的 Azure 搜尋服務
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 1d67b100620d4517e657f92acb37e370f2bb540e
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34480949"
---
# <a name="connect-to-azure-search-with-power-bi"></a>使用 Power BI 連接到 Azure 搜尋服務
Azure 搜尋服務流量分析可讓您監視及了解 Azure 搜尋服務的流量。 Power BI 的 Azure 搜尋服務內容套件提供了搜尋資料的詳細深入解析，包括過去 30 天內的搜尋、索引、服務統計資料和延遲。 更多詳細資料請參閱 [Azure 部落格文章](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/)。

連接到 Power BI 的 [Azure 搜尋服務內容套件](https://app.powerbi.com/getdata/services/azure-search)。

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. 選取 [Azure 搜尋服務] \> [取得]。
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. 提供已儲存 Azure 搜尋服務分析的資料表儲存體帳戶名稱。
   
   ![](media/service-connect-to-azure-search/params.png)
5. 選取 [金鑰]  作為驗證機制，並提供儲存體帳戶金鑰。 按一下 [登入]  開始載入程序。
   
   ![](media/service-connect-to-azure-search/creds.png)
6. 載入一完成，新的儀表板、報表和模型就會出現在瀏覽窗格中。 選取儀表板以檢視匯入的資料。
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](power-bi-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="system-requirements"></a>系統需求
Azure 搜尋服務內容套件需要帳戶啟用 Azure 搜尋服務流量分析。

## <a name="troubleshooting"></a>疑難排解
請確定已提供正確的儲存體帳戶名稱以及完整的存取金鑰。 儲存體帳戶名稱應該對應至使用 Azure 搜尋服務流量分析進行設定的帳戶。

## <a name="next-steps"></a>後續步驟
[開始使用 Power BI](service-get-started.md)

[Power BI - 基本概念](service-basic-concepts.md)

