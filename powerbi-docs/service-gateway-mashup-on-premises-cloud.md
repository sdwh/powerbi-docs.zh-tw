---
title: 合併或附加內部部署與雲端資料來源
description: 使用內部部署資料閘道，在相同查詢中合併或附加內部部署和雲端資料來源。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 06/06/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2547be7f7bdadb7f991db54230d4fd791941838d
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37600056"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>合併或附加內部部署與雲端資料來源

內部部署資料閘道，讓您能在相同查詢中合併或附加內部部署和雲端資料來源。 當您想要混用來自多個來源的資料而不需要使用個別的查詢時，這會有所助益。

## <a name="prerequisites"></a>先決條件

- [安裝在本機電腦上的閘道](service-gateway-install.md)。
- 具有結合內部部署和雲端資料來源之查詢的 Power BI Desktop 檔案。

1. 在 Power BI 服務的右上角，選取齒輪圖示 ![設定齒輪圖示](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) > [管理閘道]。

    ![管理閘道](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. 選取您想要設定的閘道。

3. 在 [閘道叢集設定] 下，選取 [允許使用者的雲端資料來源，以透過此閘道叢集重新整理] > [套用]。

    ![透過此閘道叢集重新整理](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. 在此閘道叢集下，新增在查詢中使用的任何[內部部署資料來源](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source)。 您不需要在這裡新增雲端資料來源。

5. 將具有結合內部部署和雲端資料來源之查詢的 Power BI Desktop 檔案上傳至 Power BI 服務。

6. 在新資料集的 [資料集設定] 頁面：

   - 對於內部部署來源，選取與此資料來源建立關聯的閘道。

   - 在 [資料來源認證] 下，視需要編輯雲端資料來源認證。

     ![資料集設定](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

7. 設定雲端認證之後，您現在可以使用 [立即重新整理] 選項重新整理資料集，或將它排程為定期重新整理。


## <a name="next-steps"></a>後續步驟

若要深入了解閘道的資料重新整理，請參閱[使用資料來源進行已排程的重新整理](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh)。