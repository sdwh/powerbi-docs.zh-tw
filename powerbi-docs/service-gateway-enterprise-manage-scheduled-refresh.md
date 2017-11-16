---
title: "管理您的資料來源 - 匯入/已排程的重新整理"
description: "如何管理內部部署資料閘道及屬於該閘道的資料來源。 本文旨在說明可用於匯入/已排程重新整理的資料來源。"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 07/20/2017
ms.author: davidi
ms.openlocfilehash: c41035db173c937caedab92b65eeb66dbcfafdb9
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>管理您的資料來源 - 匯入/已排程的重新整理
安裝內部部署資料閘道之後，您必須新增可搭配閘道使用的資料來源。 本文將探討相對於 DirectQuery 或即時連線，如何使用可用於已排程之重新整理的閘道和資料來源。

## <a name="download-and-install-the-gateway"></a>下載並安裝閘道
您可以從 Power BI 服務下載閘道。 選取 [下載] > [資料閘道]，或移至 [gateway download page (閘道下載頁面)](https://go.microsoft.com/fwlink/?LinkId=698861)。

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-download-data-gateway.png)

## <a name="add-a-gateway"></a>加入閘道
若要新增閘道，請直接將企業閘道[下載](https://go.microsoft.com/fwlink/?LinkId=698863)並安裝到您環境中的伺服器上。 安裝閘道之後，它會顯示在 [管理閘道] 底下的閘道清單中。

> [!NOTE]
> 您必須是至少一個閘道的管理員，才會顯示 [管理閘道]。 當以管理員身分加入閘道時，或者當您安裝並設定閘道時，就會發生這種情況。
> 
> 

## <a name="remove-a-gateway"></a>移除閘道器
移除閘道器的同時也會刪除該閘道器下的所有資料來源。  這也會中斷依賴這些資料來源的任何儀表板和報表。

1. 選取右上角的齒輪圖示![](media/service-gateway-enterprise-manage-scheduled-refresh/pbi_gearicon.png) > [管理閘道] 。
2. [閘道] > [移除]
   
   ![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings7.png)

## <a name="add-a-data-source"></a>加入資料來源
您可以選取閘道並按一下 [加入資料來源]，或移至 [閘道] > [加入資料來源] ，以加入資料來源。

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings1.png)

您可以接著從清單中選取 [資料來源類型]  。 所有列出的資料來源可搭配企業閘道用於已排程的重新整理。 Analysis Services、SQL Server 和 SAP HANA 可以用於已排程的重新整理或 DirectQuery/即時連線。

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

您接著需要填入資料來源的資訊，包括用來存取資料來源的來源資訊和認證。

> [!NOTE]
> 資料來源的所有查詢都會使用這些認證來執行。 如需詳細資訊，請參閱主要內部部署資料閘道文章，以深入了解[認證](service-gateway-onprem.md#credentials)的儲存方式。
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

您可以在填入所有內容之後，按一下 [加入]  。  您現在可以使用此資料來源，用於內部部署資料已排程的重新整理。 如果成功，您會看到「連接成功」  。

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

<!-- Shared Install steps Include -->
[!INCLUDE [gateway-onprem-datasources-include](./includes/gateway-onprem-datasources-include.md)]

### <a name="advanced-settings"></a>進階設定
您可以設定資料來源的隱私權等級， 如此可控制如何混搭資料。 這只能用於已排程的重新整理。 [深入了解](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="remove-a-data-source"></a>移除資料來源
移除資料來源的同時也會中斷依賴指定資料來源的所有儀表板或報表。  

若要移除資料來源，請前往 [資料來源] > [移除]。

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings6.png)

## <a name="manage-administrators"></a>管理管理員
在 [管理員] 索引標籤上，您可以針對閘道加入並移除可管理閘道的使用者。 您在這個階段只會加入使用者， 而不會加入安全性群組。

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings8.png)

## <a name="manage-users"></a>管理使用者
您可以在 [使用者] 索引標籤上，針對資料來源加入並移除可以使用這個資料來源的使用者或安全性群組。

> [!NOTE]
> 使用者清單僅控制獲准發行報表的人員。 報表擁有者可以建立儀表板或內容套件，並與其他使用者共用。
> 
> 

![](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings5.png)

## <a name="using-the-data-source-for-scheduled-refresh"></a>使用資料來源進行已排程的重新整理
建立資料來源之後，您將可使用其中一個 DirectQuery 連接或透過已排程的重新整理，以取得資料來源。

> [!NOTE]
> 伺服器和資料庫名稱必須符合內部部署資料閘道內的 Power BI Desktop 和資料來源！
> 
> 

您的資料集和閘道內的資料來源是根據您的伺服器名稱和資料庫名稱以建立連結。 這些項目必須相符。 例如，若您的伺服器名稱是 IP 位址，在 Power BI Desktop 內，您將必須使用該 IP 位址以取得閘道設定內的資料來源。 若您使用 *SERVER\INSTANCE*，在 Power BI Desktop 中，您將必須使用相同的伺服器名稱以取得閘道內設定的資料來源。

若閘道內設定資料來源的 [使用者] 索引標籤中列出您的使用者，而伺服器和資料庫名稱也相符，您就可以將閘道作為進行已排程重新整理的一個選項。

![](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> 如果您的資料集包含多個資料來源，每個資料來源都必須新增至閘道中。 如果有一或多個資料來源未新增至閘道，就看不到閘道可供排程的重新整理使用。
> 
> 

## <a name="limitations"></a>限制
* OAuth 不是內部部署資料閘道支援的驗證結構描述。 您無法新增需要 OAuth 的資料來源。 如果您的資料集有需要 OAuth 的資料來源，就無法使用閘道進行排程的重新整理。

## <a name="next-steps"></a>後續步驟
[內部部署資料閘道](service-gateway-onprem.md)  
[內部部署資料閘道 - 深入資訊](service-gateway-onprem-indepth.md)  
[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

