---
title: 使用 Power BI 連接到 QuickBooks Online
description: QuickBooks Online for Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b4cd8974316119978749db4f3996db76d907ab38
ms.sourcegitcommit: e8d924ca25e060f2e1bc753e8e762b88066a0344
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37136057"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>使用 Power BI 連接到 QuickBooks Online
當您從 Power BI 連接到您的 QuickBooks Online 資料時，您會立即取得 Power BI 儀表板和 Power BI 報表，其針對您企業的現金流量、獲利率、客戶和其他項目提供深入資訊。 您可以使用原有的儀表板和報表，或是加以自訂，反白顯示您特別有興趣的資訊。 資料會自動每天重新整理一次。

連接到 Power BI 的 [QuickBooks Online 內容套件](https://dxt.powerbi.com/getdata/services/quickbooks-online)。

>[!NOTE]
>您必須是 QuickBooks Online 帳戶上的系統管理員，且以您的系統管理員帳戶認證登入，才能夠將 QuickBooks Online 資料匯入 Power BI。 您無法以 QuickBooks Desktop 軟體使用此連接器。 

## <a name="how-to-connect"></a>如何連接
1. 選取左側瀏覽窗格底部的 [取得資料]  。
   
   ![](media/service-connect-to-quickbooks-online/pbi_getdata.png) 
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![](media/service-connect-to-quickbooks-online/pbi_getservices.png) 
3. 選取 [QuickBooks Online]，然後選取 [取得]。
   
   ![](media/service-connect-to-quickbooks-online/qbo.png)
4. 針對 [驗證方法] 選取 [oAuth2]  ，然後選取 [登入] 。 
5. 出現提示時，請輸入您的 QuickBooks Online 認證，並遵循 QuickBooks Online 驗證程序。 如果您已經在瀏覽器中登入 QuickBooks Online，可能就不會出現輸入認證的提示。
   >[!NOTE]
   >您需要 QuickBooks Online 帳戶的系統管理員認證。
6. 請在下一個畫面中，選取您要連接至 Power BI 的公司。
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)
7. 在下一個畫面中選取 [授權]  開始匯入程序。 這可能需要幾分鐘的時間，視您公司資料的大小而定。 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
   Power BI 匯入資料之後，您會在左側瀏覽窗格中看到新的儀表板、報表和資料集。 新的項目會以黃色星號標示\*。
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_leftnavnew.png)
8. 選取 QuickBooks Online 儀表板。 這是 Power BI 自動建立的儀表板，可顯示您匯入的資料。 您可以修改此儀表板，以您想要的任何方式來顯示資料。 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_dash.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](power-bi-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](service-dashboard-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="troubleshooting"></a>疑難排解
「糟糕！發生錯誤了。」

如果您在選取 [授權] 之後收到此訊息：

「糟糕！ 發生錯誤了。 請關閉此視窗並再試一次。

應用程式已由此公司的另一位使用者訂閱。 請連絡 [管理員電子郵件] 來變更此訂閱。」

![](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

...這表示您公司的另一位管理員已經使用 Power BI 連接到您的公司資料。 請向該管理員要求與您共用儀表板。 目前，只有一位管理員使用者可以連接至 Power BI 的特定 QuickBooks Online 公司資料集。 Power BI 建立儀表板之後，管理員可在同一個 Power BI 租用戶上與多位同事共用儀表板。

**「這個應用程式並未設定為允許來自於您的國家/地區的連線」**

目前 Power BI 僅支援美國的 QuickBooks Online 版本。 

![](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>後續步驟
[Power BI 是什麼？](power-bi-overview.md)

[Power BI - 基本概念](service-basic-concepts.md)

