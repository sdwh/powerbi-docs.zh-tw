---
title: "開始使用 Power BI 閘道"
description: "了解 Power BI 資料閘道的基本概念。"
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
ms.date: 09/25/2017
ms.author: davidi
ms.openlocfilehash: 617dcbf1d149966369aa0d1566094f6ce820a40a
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="getting-started-with-power-bi-gateways"></a>開始使用 Power BI 閘道
歡迎使用**開始使用 Power BI 閘道**指南。 這個簡短逐步解說會帶領您了解閘道的作用、其運作方式，以及如何安裝、設定和執行專屬閘道。  

![](media/service-gateway-getting-started/gw_gettingstarted_0a.png)

閘道可以是技術主體，並且，因為每個網路和企業都不同，所以閘道可能十分複雜。 為了不要造成這種複雜性，請從基本概念開始。

## <a name="how-power-bi-gateways-work"></a>Power BI 閘道運作方式
**閘道**是一種軟體，可針對雲端服務中的後續使用 (例如 Power BI)，方便存取私用內部部署網路上的資料。 它就像接聽連線要求的閘道管理員，並且只有在使用者的要求符合特定準則時才會授與它們 (例如是否允許它們使用閘道)。 這可讓組織將資料庫和倉儲保留在其內部部署網路上，但可安全地使用該資料的子集，以在 Power BI 中建立吸引人的報表和儀表板。

閘道也會加密和壓縮所有通過它的資料來保護安全的存取權和資料，以及用來連接至資料來源的任何密碼。 我相信這聽起來十分簡單明瞭，但需要考量許多詳細資料。

您有時只想要有專屬閘道；您可能有大型 Excel 活頁簿以及三個包含數年執行銷售和行銷資料的 SQL 資料庫，而且您想要建立 Power BI 儀表板來顯示每個角度的銷售。 您是唯一會建立報表的人員、它是 Excel 活頁簿，而且只有您才能使用這些資料庫來建立 Power BI 報表。 您只需要一個閘道供您個人使用，而不需要與其他人共用這些資料來源。

其他時候，您的組織可能會有不同廠商的各種資料庫 (包括 Analysis Services、SAP、Oracle、IBM 和其他各種資料來源)，而您需要許多人可以存取它們以建立許多報表。 在此情況下，您需要可讓您設定所有這些來源之存取權的閘道，接著需要與組織中的許多人共用。 這完全是不同類型的閘道。

幸好，Power BI 提供兩個閘道，並且針對所有這些案例進行調整。 Power BI 的這兩個閘道供應項目如下︰

* **內部部署資料閘道 (個人模式)** - 可讓一位使用者連線至來源，但不能與其他人共用。 只能與 Power BI 搭配使用。
* **內部部署資料閘道**：可讓多位使用者連接至多個內部部署資料來源，並且可供 Power BI、**PowerApps**、Flow 和 Azure Logic 應用程式使用，這些都是透過單一閘道安裝來完成。

兩個閘道都執行類似的功能，可方便存取私用內部部署網路上的資料；因此，資料可以用於 Power BI 這類雲端服務中。 個人閘道可供一個人使用，而且只能由 Power BI 使用，而**內部部署資料閘道**可供許多使用者和許多服務使用。

有三個部分 (階段) 可讓閘道運作︰

* 安裝閘道
* 將使用者新增至閘道 (讓它們使用閘道)
* 連接至資料來源

此外，使用閘道可讓您執行其他重要事項︰

* 重新整理內部部署資料，以使用全新資料來更新 Power BI 報表

重新整理資料表示 Power BI 儀表板和報表看起來就像全新的，並反映最新資料。 因此，有人檢視您使用內部部署資料所建立的報表時，該報表會顯示最新資訊，即使您不久前才剛建立報表也是一樣。

第一個部分是安裝閘道，這十分簡單。 允許使用者存取閘道也十分簡單：您只要在 Power BI 的對話方塊中新增他們即可，他們已經準備就緒。 連接至資料來源可能十分複雜，因為有這麼多的資料來源，而且每個都有它自己的連線需求和細微差別。 而且，我們會處理另一個指南中的重新整理，將本文著重在閘道。

因此，讓我們先執行簡單的事項，並逐步解說如何安裝閘道。

## <a name="install-the-gateway"></a>安裝閘道
若要安裝閘道，請開啟 Power BI 服務 (您可以在瀏覽器中使用此連結啟動 Power BI 服務，並登入)，然後使用 Power BI 帳戶登入。 在 Power BI 服務中，選取右上角的**下載圖示** (如下圖所示)，然後選取 [資料閘道]。

![](media/service-gateway-getting-started/gw_gettingstarted_01.png)

這會將您帶往下載頁面，您可以在其中按一下 [下載閘道] 按鈕來起始下載。

![](media/service-gateway-getting-started/gw_gettingstarted_02.png)

這個畫面提供閘道用途的超濃縮說明。 它也提供幾個重要**警告**；閘道在安裝之後，會在執行安裝的電腦上實際執行。 如果關閉該電腦，也會一併關閉閘道 (因此它未執行時將不會運作)。 此外，在使用無線網路的電腦上安裝並不是最佳方式，因此您應該使用連接至有線網路的電腦。

當您準備好時，請選取 [下一步] 繼續進行安裝。

![](media/service-gateway-getting-started/gw_gettingstarted_03.png)

以下是您決定要安裝之閘道的位置：內部部署閘道或個人閘道。 在本指南中，我們將安裝**內部部署資料閘道**。

在此決策點，您需要注意幾件事︰

* 兩個閘道都需要 64 位元 Windows 作業系統。
* 閘道不能安裝在網域控制站上。
* 同一部電腦最多可安裝兩個內部部署資料閘道，每個閘道各執行一種模式 (個人和標準)。 
* 同一部電腦不可有一個以上的閘道執行相同的模式。
* 不同電腦上可安裝多個內部部署資料閘道，並可從相同的 Power BI 閘道管理介面一併管理 (個人模式除外，請參閱下列的項目符號)。
* 每個 Power BI 使用者只能執行一個個人模式閘道。 如果為相同的使用者安裝另一個個人模式閘道 (即使在不同的電腦上)，最新的安裝都會取代先前的既有安裝。

選取 [下一步] 時，即開始安裝閘道。 您需要指定安裝它的位置，而且通常最好是預設位置。

![](media/service-gateway-getting-started/gw_gettingstarted_06.png)

安裝程序十分快速，並且會提供狀態列。

![](media/service-gateway-getting-started/gw_gettingstarted_06a.png)

幾乎完成之後，您需要識別要與閘道搭配使用的帳戶。 這應該是您用來登入 Power BI 的帳戶 (使用者名稱和密碼)、閘道會與您的 Power BI 帳戶建立關聯，而且您可以從 Power BI 服務設定閘道。

![](media/service-gateway-getting-started/gw_gettingstarted_07.png)

您將會登入，如下圖所示。

![](media/service-gateway-getting-started/gw_gettingstarted_08.png)

登入之後，您必須建立**修復金鑰**。 我們將在另一篇文章中更深入討論這些作業，但現在，請注意您在復原或移動閘道時會需要它。

![](media/service-gateway-getting-started/gw_gettingstarted_09.png)

一切順利時，您會看到告訴您閘道已備妥的視窗。

![](media/service-gateway-getting-started/gw_gettingstarted_10.png)

現在即可安裝內部部署閘道。 就如承諾一樣，它是相當簡單的程序。 接著，下個步驟是「新增使用者」或「新增資料來源」：您可以先執行任一項，並在初始設定之後新增任一項。

下節描述如何將使用者新增至閘道，在那之後，我們將討論接下來如何將資料來源新增至閘道。

## <a name="add-users-to-a-gateway"></a>將使用者新增至閘道
既然我們已安裝閘道，我們將會從「Power BI 服務」管理閘道。 若要到達閘道的管理畫面，請在 Power BI 服務中選取右上角的齒輪圖示，然後選取 [管理閘道]。

![](media/service-gateway-getting-started/gw_gettingstarted_15.png)

即會出現 Power BI 服務畫布內的頁面，您可以在其中管理閘道。 [閘道設定] 頁面看起來如下。

![](media/service-gateway-getting-started/gw_gettingstarted_12.png)

如果您點選或按一下 [系統管理員]，則會看到下列系統管理員的管理頁面。 請注意，這就是哪些使用者可以「管理」閘道，以及使用不同的頁面在每個個別資料來源中新增 (或移除) 閘道的使用者，我們會在接下來的幾個段落中進行檢閱。

![](media/service-gateway-getting-started/gw_gettingstarted_13.png)

資料來源在安裝並驗證 (成功連接) 之後，就會顯示在這個 [管理閘道] 畫面左側的相關聯閘道下方，如下圖所示。 請注意，在右窗格中，您可以切換兩個區段︰[資料來源設定] 和 [使用者]。 緊接著的畫面是 [資料來源設定] 區段。

![](media/service-gateway-getting-started/gw_gettingstarted_16.png)

選取 [使用者] 時，請在文字方塊中輸入組織中您要授與所選取資料來源存取權的使用者。 在下列畫面中，您可以看到我已新增 Maggie 和 Adam。

當您開始在文字方塊中輸入電子郵件地址時，Power BI 會顯示一份電子郵件符合所輸入內容的使用者清單，讓您可以按一下名稱，並將其新增至清單。

您也可以新增電子郵件群組 (別名)，以允許多組人員和個人存取。

![](media/service-gateway-getting-started/gw_gettingstarted_17.png)

選取 [新增] 之後，新增的成員就會顯示在方塊中，如果想要的話，還可以新增更多成員。 移除使用者也一樣簡單。 只需要核取其名稱旁邊的核取方塊，然後選取該方塊下方的 [移除] 按鈕。

![](media/service-gateway-getting-started/gw_gettingstarted_18.png)

就是這麼簡單。 請記住，您必須將使用者新增至您要授與存取權的每個資料來源。 每個資料來源都有不同的使用者清單，而且您必須分別將使用者新增至每個資料來源。

## <a name="adding-data-sources"></a>新增資料來源
當然，為了將閘道設為有用，您會想要新增資料來源。 這是造成一些 Power BI 閘道複雜性的位置：有許多不同的資料來源可用，而且每個都有專屬需求 (通常它會擁有必要驅動程式)。

但閱讀另一篇文章之前，請先查看如何新增資料來源。 位於 [Power BI 服務] 的 [管理閘道] 頁面時，請選取您想要新增資料來源的閘道，然後選取頁面左上角的 [新增資料來源]，就在閘道清單上方。

當您這樣做時，[資料來源設定] 面板就會顯示在右窗格中，如下圖所示。 您可以在這裡命名資料來源 (輸入於 [資料來源名稱] 文字方塊中)，然後從 [資料來源類型] 下拉式清單中選取其類型。

![](media/service-gateway-getting-started/gw_gettingstarted_14.png)

好了，您現在已安裝閘道，而且您已經準備好新增資料來源。 太棒了！ 如需資料來源的資訊、使用閘道的更多詳細資料，以及其他有用資訊，請參閱下節中的資源。

## <a name="next-steps"></a>後續步驟
[使用內部部署資料閘道](service-gateway-onprem.md)  
[內部部署資料閘道 - 深入資訊](service-gateway-onprem-indepth.md)  
[內部部署資料閘道 (個人模式)](service-gateway-personal-mode.md)

[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

