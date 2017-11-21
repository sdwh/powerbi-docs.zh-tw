---
title: Power BI Gateway - Personal
description: Power BI Gateway - Personal
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
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: b1cb5bda9b80cb08ece111959884b840ff8d42cc
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
> [!NOTE]
> Power BI 有一個新版本的個人閘道，稱為**內部部署資料閘道 (個人模式)**。 下列文章描述舊版的個人閘道，稱為 **Power BI Gateway - Personal**，將於 2017 年 7 月 31 日之後淘汰並停止運作。 如需新版個人閘道的相關資訊，包括如何安裝新版本，請參閱[**內部部署資料閘道 (個人模式)** 文章](service-gateway-personal-mode.md)。
> 
> 

**Power BI Gateway - Personal** 以橋接器的角色連結 Power BI 服務和支援[重新整理](refresh-data.md)的內部部署資料來源，提供兩者之間快速且安全的資料傳輸。 本文旨在帶領您深入了解閘道器的運作方式，以及閘道器對您來說是否必要。 另外我們也針對個人閘道器整理出這個[實用影片](https://www.youtube.com/watch?v=de58vROLqZI)。 

此工具會以服務在您的電腦上安裝並執行。 這項服務會使用組態期間所指定的 Windows 帳戶來執行。 在某些情況下，閘道會以應用程式來執行。 我們稍後會討論更多有關這方面的資訊。

當 Power BI 重新整理內部部署資料來源的資料時，閘道器可確保您的 Power BI 帳戶具有適當權限，以便連接到來源的資料並加以查詢。

Power BI 和閘道器之間的資料傳輸會透過 [Azure 服務匯流排](http://azure.microsoft.com/documentation/services/service-bus/)加以保護。 服務匯流排會在 Power BI 服務與您電腦之間，建立安全的通道。 由於閘道器提供這種安全的連線，所以通常不需要在防火牆中開啟連接埠。

在我們詳細討論閘道器之前，請先看一看 Power BI 中所用到的一些字詞：

「資料集」  是指從線上或內部部署資料來源上傳到 Power BI 服務內的資料。 當您使用 [取得資料] 連接並上傳資料時，就會建立資料集。 資料集會出現在瀏覽器裡的 Power BI 工作區的 [我的工作區] 窗格中。 當您建立報表並將磚釘選到儀表板時，您看到的資料便是來自您的資料集。

*資料來源* 是指您上傳至資料集內之資料的實際來源處， 可以是近乎任何項目，像是資料庫、Excel 工作表、Web 服務等等。如果是在 Excel 活頁簿中，您可以建立含有資料列的簡易工作表，而這即視為資料來源。 您也可以使用 Excel 中的 Power Query 或 Power Pivot 同時連接並查詢來自線上和內部部署資料來源的資料，全都在同一個活頁簿中作業。 若為 Power BI Desktop，您可以使用 [取得資料] 同時連接並查詢線上和內部部署資料來源的資料。

個人閘道可透過內部部署資料閘道安裝。 可以在 [Power BI 閘道頁面](https://powerbi.microsoft.com/gateway/)下載。

## <a name="do-i-need-a-gateway"></a>我需要閘道器嗎？
安裝閘道器之前，請務必了解您是否確實需要閘道器。 實際上，這取決於您的資料來源：

### <a name="on-premises-data-sources"></a>內部部署資料來源
如果要重新整理從您組織內受支援之內部部署資料來源取得資料的資料集，就「需要」個人閘道器。

透過閘道器，從以下來源上傳的資料集可支援 [立即重新整理] 和 [排程重新整理]：

* Microsoft Excel 2013 (或更新版本) 活頁簿；您可在其中使用 Power Query 或 Power Pivot 來連接及查詢受支援之內部部署資料來源的資料。 Power Query 或 Power Pivot 的 [取得外部資料] 中所顯示的所有內部部署資料來源都支援重新整理，Hadoop 檔案 (HDFS) 與 Microsoft Exchange 除外。
* Microsoft Power BI Desktop 的檔案；您可在其中使用 [取得資料] 來連接並查詢受支援之內部部署資料來源的資料。 [取得資料] 中所顯示的所有內部部署資料來源都支援重新整理，Hadoop 檔案 (HDFS) 與 Microsoft Exchange 除外。

### <a name="online-data-sources"></a>線上資料來源
「唯有」在您使用 [ **Web.Page** ](https://msdn.microsoft.com/library/mt260924.aspx)函式的情況下才需要閘道器。 在其他情況下，如果是要重新整理只從線上資料來源取得資料的資料集，則「不需要」閘道器。

> [!NOTE]
> 如果您使用 [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx) 函式，則唯有在您於 2016 年 11 月 18 日之後重新發佈資料集或報表的情況下才需要閘道器。
> 
> 

從以下來源上傳的資料集可支援 [立即重新整理] 和 [排程重新整理]，不需要閘道器：

* 來自線上資料來源的內容套件 (內容套件\\服務)。 根據預設，內容套件的資料集會每天自動更新一次，不過您也可以手動重新整理或設定重新整理排程。
* Microsoft Excel 2013 (或更新版本) 活頁簿；您可在其中使用 Power Query 或 Power Pivot 來連接及查詢線上資料來源的資料。
* Microsoft Power BI Desktop 檔案；您可在其中使用 [取得資料] 來連接並查詢線上資料來源的資料。

**問題：** 如果我的 Excel 活頁簿或 Power BI Desktop 檔案同時從線上和內部部署資料來源取得資料呢？

**回答：** 「需要」  閘道。 您必須安裝和設定閘道器，才能重新整理來自內部部署資料來源的資料。

**問題：** 如果我的 Excel 活頁簿中只有我輸入的資料列呢？**

**回答：** 「不」  需要閘道。 只有在活頁簿使用 Power Query 或 Power Pivot 來查詢資料並將資料載入受支援之內部部署資料來源的資料模型時，您才需要安裝並設定閘道器。

## <a name="setting-up-a-gateway-for-the-first-time"></a>首次設定閘道器
首次設定閘道器的程序有三個步驟：

1. 下載並安裝閘道器
2. 設定閘道
3. 登入 Power BI 中的資料來源

接下來我們進一步討論每個步驟。

### <a name="download-and-install-a-gateway"></a>下載並安裝閘道器
> [!NOTE]
> Power BI 有一個新版本的個人閘道，稱為**內部部署資料閘道 (個人模式)**。 本文描述舊版的個人閘道，稱為 **Power BI Gateway - Personal**，將於 2017 年 7 月 31 日之後淘汰並停止運作。 如需新版個人閘道的相關資訊，包括如何安裝新版本，請參閱[**內部部署資料閘道 (個人模式)** 文章](service-gateway-personal-mode.md)。
> 
> 

當您第一次針對受支援的資料集按一下 [立即重新整理] 或 [排程重新整理] 時，系統會提示您安裝閘道器。 或者，於 [下載] 功能表下選取 [資料閘道] 以下載閘道。 下載[內部部署資料閘道](http://go.microsoft.com/fwlink/?LinkID=820925)。

您會想要選取 [個人閘道] 而不是 [內部部署資料閘道]，以擁有您專屬的閘道。

安裝閘道其實不會很複雜。 您只要選取要安裝的位置，閱讀並接受授權合約，一如安裝任何其他應用程式。 不過有一些重要須知，請務必了解。 尤其是安裝閘道器所在電腦的類型，以及在該電腦上用來登入 Windows 的帳戶類型。

> [!NOTE]
> 閘道必須能夠存取資料來源。 如果您的個人電腦無法連線到資料來源，建議您考慮在能夠存取資料來源的電腦上安裝[內部部署資料閘道](service-gateway-onprem.md)。 將 SQL Server 安裝在裝載於 Azure 的虛擬機器 (VM) 上，即為此做法的範例之一。 您的個人電腦可能無法存取 VM。 您可以改為在 VM 上安裝內部部署資料閘道，並在 Power BI 服務內設定資料來源。
> 
> 

### <a name="computer-type"></a>電腦類型
您安裝閘道器所在電腦的類型非常重要。

> [!NOTE]
> 個人閘道僅適用於 64 位元的 Windows 作業系統。
> 
> 

膝上型電腦 - 若要讓排程的重新整理執行，閘道器必須啟動並執行。 膝上型電腦關閉或處於睡眠狀態的機率，通常高於正在執行。 如果您在膝上型電腦上安裝閘道器，請務必將排定的重新整理時間設為膝上型電腦執行的時段。 若不如此，直到下次排定的重新整理時間之前，都不會再次嘗試重新整理。

桌上型電腦 – 問題不多。 只要確認在您所排定的重新整理時間，電腦和閘道器都在執行中即可。 許多桌上型電腦會進入睡眠模式，如果電腦處於睡眠狀態，則排定的重新整理就無法執行。

您只需要安裝一個閘道器。 一個閘道器即可用於任何數目的受支援資料集。 您也不需要在您上傳活頁簿和 Power BI Desktop 檔案的同一部來源電腦上安裝閘道器。 範例如下：假設您有一個連接到您組織內 SQL Server 資料來源的 Excel 活頁簿。 您使用 Power BI 中的 [取得資料] 從膝上型電腦上傳活頁簿。 您另外還有一部隨時都在執行的桌上型電腦，且已在該電腦上安裝並設定閘道器。 在 Power BI 中，您登入資料來源並針對資料集設定好重新整理排程。  排定的重新整理時間一到，Power BI 就會建立與您安裝在桌上型電腦上閘道器的安全連線。 接著它會安全地連接到資料來源以取得更新。 針對重新整理這個部分，並不會與您從膝上型電腦上傳的原始活頁簿進行通訊。

> [!NOTE]
> 您可以在同一部電腦上安裝個人和企業閘道。
> 
> 

### <a name="windows-account"></a>Windows 帳戶
當您安裝閘道器時，系統會使用您的 Windows 帳戶將您登入電腦。 您的 Windows 帳戶所擁有的權限類型，會影響閘道器在 Windows 中的安裝及執行方式。

當您登入 Windows：

|  | 使用系統管理員權限 | 不使用系統管理員權限 |
| --- | --- | --- |
| **Power BI Gateway - Personal 執行為** |服務 |應用程式 |
| **排定的重新整理** |只要您的電腦與閘道器服務正在執行，您就不須在已排程的重新整理時間登入。 |您必須在已排程的重新整理時間登入您的電腦。 |
| **變更 Windows 帳戶密碼** |您必須變更閘道器服務的密碼。 如果閘道器所使用的帳戶密碼不再有效，重新整理就會失敗。 |閘道器執行時一律使用您目前登入所用的帳戶和密碼。 如果您未登入 Windows，閘道器就不會執行，且重新整理會失敗。 |

### <a name="configure-the-gateway"></a>設定閘道
安裝精靈完成之後，系統會提示您啟動 [組態精靈]。 設定閘道器其實不會很複雜。 您必須從精靈登入 Power BI。 精靈需要此動作，才能使用您的 Power BI 帳戶在 Power BI 服務中建立連線。

如果您是以具有系統管理員權限的帳戶登入 Windows，系統會要求您輸入您的 Windows 帳戶認證。 您可以指定不同的 Windows 帳戶，但請務必記得，權限會決定閘道器的執行方式。 閘道器服務會使用此帳戶來執行。

### <a name="sign-in-to-data-sources"></a>登入的資料來源
一旦 [組態精靈] 完成且您的閘道器已啟動並執行，您就必須指定驗證類型，然後登入您每一個資料集的資料來源。 您會在 Power BI 中完成這個步驟。

![](media/personal-gateway/pg_dataset_settings_signin.png)

您只需要指定驗證類型並登入資料來源一次。 您可以從資料集 [設定] 畫面的 **[管理資料來源]** 區段登入。 如果您有多個資料來源，您就必須一一登入。 閘道器會根據資料來源判定預設的驗證類型。 在大部分情況下，驗證類型為 Windows 驗證。不過在某些情況下，您的資料來源可能需要不同的驗證類型。 如果您不確定，請洽詢您的資料來源管理員。

## <a name="up-and-running"></a>啟動並執行！
閘道器啟動並執行之後，您就可以按一下資料集的 [排程重新整理]，並看到資料集的 [設定] 頁面。

![](media/personal-gateway/pg_awintsales_settings.png)

此頁面會顯示：

1. 重新整理狀態 – 顯示重新整理成功和下次排定的重新整理時間。
2. **閘道器** – 顯示閘道器是否已安裝且已上線。 如果閘道器已安裝但未上線，則會停用 [管理資料來源] 和 [排程重新整理] 設定。
3. **管理資料來源** – 顯示資料集連接的資料來源。 您可以登入或變更驗證類型。 您只需要登入每個資料來源一次。
4. **排程重新整理** – 您可以在此設定重新整理排程設定值。 如果閘道器未上線，則會停用這些設定。
5. 重新整理失敗通知 – 此選項依預設為已選取，會在排定的重新整理失敗時傳送電子郵件給您。

## <a name="updating-your-windows-account-password"></a>更新您的 Windows 帳戶密碼
如果您在安裝閘道器時以具有系統管理員權限的 Windows 帳戶登入電腦，則閘道器會以服務的形式使用您在 [組態精靈] 中所指定的 Windows 帳戶來執行。 通常這會是您用來登入電腦的同一個 Windows 帳戶。 當您變更 Windows 帳戶密碼時，也需要變更閘道器中的帳戶密碼，否則服務可能不會執行且重新整理將會失敗。 若要變更閘道器的 Windows 帳戶密碼，請選取 Windows 桌面工作列上或應用程式中的個人閘道器圖示。

![](media/personal-gateway/pg_programicon.png)

您可以從這裡更新密碼並檢查閘道器的連線狀態。

![](media/personal-gateway/pg_credentials.png)

## <a name="ports"></a>連接埠
閘道會在輸出連接埠上進行通訊：TCP 443 (預設)、5671、5672、9350 到 9354。  閘道不需要輸入連接埠。

| 網域名稱 | 輸出連接埠 | 描述 |
| --- | --- | --- |
| *.powerbi.com |443 |HTTPS |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671-5672 |進階訊息佇列通訊協定 (AMQP) |
| *.servicebus.windows.net |443, 9350-9354 |透過 TCP 之服務匯流排轉送上的接聽程式 (需要 443 以取得存取控制 Token) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| login.windows.net |443 |HTTPS |

如果您需要白名單 IP 位址，而不是網域，您可以下載並使用 Microsoft Azure Datacenter IP 範圍清單。 [下載](https://www.microsoft.com/download/details.aspx?id=41653)

## <a name="next-steps"></a>後續步驟
[內部部署資料閘道 (個人模式) - 新版本的個人閘道](service-gateway-personal-mode.md)

[進行 Power BI Gateway 的 Proxy 設定](service-gateway-proxy.md)  
[Power BI Premium](service-premium.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

