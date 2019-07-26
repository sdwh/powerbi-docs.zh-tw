---
title: Power BI Gateway - Personal 疑難排解
description: Power BI Gateway - Personal 疑難排解
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 7827ce359022eccfb75798b08da164b7504c84df
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271845"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Power BI Gateway - Personal 疑難排解

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

下列各節會探討使用 Power BI Gateway - Personal 時可能會遇到的一些常見問題。

## <a name="update-to-the-latest-version"></a>更新為最新版本

目前供個人使用的閘道版本是**內部部署資料閘道 (個人)** 。 請更新您的安裝才能使用該版本。

當閘道版本過期時就會出現很多問題。  確認您維持在最新版本是一個良好的一般做法。 若您超過一個月或更久沒有更新閘道，建議您考慮安裝最新版的閘道。 然後，查看您是否可以重現問題。

## <a name="installation"></a>安裝
**個人閘道為 64 位元** - 若您的電腦是 32 位元，您便無法安裝個人閘道。 您的作業系統必須是 64 位元版本。 請安裝 64 位元版本的 Windows 或在 64 位元的電腦上安裝個人閘道。

**雖然您是電腦的本機系統管理員，但無法將個人閘道作為服務進行安裝** - 如果使用者位於電腦的本機系統管理員群組中，但群組原則不允許該使用者名稱以服務身分登入，安裝就有可能失敗。 目前，請確認群組原則允許使用者以服務身分登入。 我們正努力修正這個問題。 [深入了解](https://technet.microsoft.com/library/cc739424.aspx)

**作業逾時** - 如果您正在安裝個人閘道的電腦 (實體機器或 VM) 具有單一核心處理器，就很容易出現此訊息。 請關閉任何應用程式，並關閉任何非必要程序，然後再次嘗試安裝。

**資料管理閘道或 Analysis Services Connector 無法在相同電腦上安裝為個人閘道** - 如果您已經安裝了 Analysis Services Connector 或資料管理閘道，您必須先解除安裝 Connector 或閘道。 再嘗試安裝個人閘道。

> [!NOTE]
> 如果您在安裝期間遇到問題，安裝記錄檔可以提供協助您解決問題的資訊。 如需詳細資訊，請參閱[安裝記錄](#SetupLogs)。
> 
> 

 **Proxy 設定**：如果您的環境需要使用 Proxy，您可能會遇到個人閘道設定問題。 若要深入了解如何設定 Proxy 資訊，請參閱[設定內部部署資料閘道的 Proxy 設定](/data-integration/gateway/service-gateway-proxy)。

## <a name="schedule-refresh"></a>排程重新整理
**錯誤：遺漏儲存在雲端中的認證。**

如果您已排程重新整理，然後解除安裝又重新安裝了個人閘道，則您可能會在 \<dataset\> 的設定中遇到這項錯誤。 當您解除安裝個人閘道時，已設定要重新整理資料集的資料來源認證會從 Power BI 服務中移除。

**解決方案：** 在 Power BI 中，移至資料集的重新整理設定。 請在 [管理資料來源] 中，針對發生錯誤的任何資料來源，按一下 [編輯認證]  ，並再次登入此資料來源。

**錯誤：為此資料集提供的認證不正確。請更新重新整理過程中或在 [資料來源設定] 對話方塊中的認證以繼續。**

**解決方案**：如果您收到認證訊息，可能表示：

* 確定用來登入資料來源的使用者名稱和密碼處於最新狀態。 在 Power BI 中，移至該資料集的 [重新整理] 設定。 在 [管理資料來源] 中，選取 [編輯認證]  來更新該資料來源的認證。
* 如果雲端來源和內部部署來源之一使用 OAuth 進行驗證，則單一查詢中兩個來源之間的混搭將無法在個人閘道中重新整理。 CRM Online 和本機 SQL Server 之間的混搭即為一例。 由於 CRM Online 需要 OAuth，因此混搭會失敗。
  
  這項錯誤是已知問題，且我們正在進行調查。 若要針對此問題採取因應措施，請針對雲端來源和內部部署來源使用不同的查詢。 然後使用合併或附加查詢合併它們。

**錯誤：不支援的資料來源。**

**解決方案：** 如果您在 [排程重新整理] 設定中看見不支援的資料來源訊息，這可能表示： 

* 資料來源目前不支援在 Power BI 中重新整理。 
* Excel 活頁簿不包含資料模型，僅包含工作表資料。 目前僅當上傳的 Excel 活頁簿包含資料模型時，Power BI 才支援重新整理。 當您使用 Power Query 在 Excel 中匯入資料時，請務必選擇此選項來載入資料至資料模型。 此選項可確保資料匯入至資料模型。 

**錯誤：[無法合併資料] &lt;查詢部分&gt;/&lt;…&gt;/&lt;…&gt;正在存取具有隱私權等級的資料來源，而其無法一起使用。請重建這個資料組合。**

**解決方案**：這項錯誤是由於隱私權等級限制及所使用的資料來源類型所致。

**錯誤：資料來源錯誤:無法將值 "\[Table\]" 轉換成類型 Table。**

**解決方案**：這項錯誤是由於隱私權等級限制及所使用的資料來源類型所致。

**錯誤：這個資料列沒有足夠空間。**

若您有大小超過 4 MB 的單一資料列，就會發生這個錯誤。 請從資料來源中尋找該資料列，然後嘗試篩選掉該資料列或減少該資料列的大小。

## <a name="data-sources"></a>資料來源
**遺漏資料提供者** - 個人閘道僅提供 64 位元版本。 必須將資料提供者的 64 位元版本安裝在個人閘道安裝的相同電腦上。 例如，如果該資料集的資料來源是 Microsoft Access，您就必須將 64 位元的 ACE 提供者安裝在安裝了個人閘道的相同電腦上。  

>[!NOTE]
>若您擁有 32 位元版本的 Excel，您便無法在相同電腦上安裝 64 位元版本的 ACE 提供者。

**Access 資料庫不支援 Windows 驗證** - Power BI 目前對於 Access 資料庫僅支援匿名操作。 我們正在研究如何啟用 Access 資料庫的 Windows 驗證。

**輸入資料來源認證時發生登入錯誤** - 如果您在輸入資料來源的 Windows 認證時出現類似錯誤，可能是因為您還在使用舊版的個人閘道。 [安裝最新版本的 Power BI Gateway - Personal](https://powerbi.microsoft.com/gateway/)。

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**錯誤：選取使用 ACE OLEDB 資料來源的 Windows 驗證時發生登入錯誤** - 在輸入使用 ACE OLEDB 提供者的資料來源的資料來源認證時，如果發生下列錯誤：

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Power BI 目前不支援使用 ACE OLEDB 提供者資料來源的 Windows 驗證。

**解決方案：** 若要針對這個錯誤採取因應措施，您可以選取 [匿名驗證]  。 針對舊版 ACE OLE DB 提供者，匿名認證與 Windows 認證相同。

## <a name="tile-refresh"></a>磚重新整理
如果您收到儀表板磚重新整理錯誤，請參閱下列文章。

[為磚錯誤進行疑難排解](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>疑難排解的工具
### <a name="refresh-history"></a>重新整理歷程記錄
**重新整理歷程記錄**可以協助您查看發生了哪些錯誤，以及在需要建立支援要求時提供有用的資料。 您可以同時檢視已排程及隨選的重新整理。 以下是取得**重新整理歷程記錄**的方式。

1. 在 Power BI 瀏覽窗格中，於 [資料集]  中選取資料集 &gt; [開啟功能表]&gt; [排程重新整理]  。
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. 在 [設定...]  中，選取 [重新整理歷程記錄]  。  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>事件記錄檔
有數個事件記錄檔可以提供資訊。 若您是電腦的系統管理員，前兩個是**資料管理閘道**和 **PowerBIGateway**。  若您不是系統管理員，且正在使用個人閘道，就會在**應用程式**記錄檔內看到記錄項目。

**Data Management Gateway** 和 **PowerBIGateway** 記錄檔位於 **Application and Services Logs**下。

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Fiddler 追蹤
[Fiddler](http://www.telerik.com/fiddler) 是 Telerik 提供的免費工具，可用來監視 HTTP 流量。 您可以從用戶端電腦看到與 Power BI 服務的通訊。 此通訊可能會顯示錯誤及其他相關資訊。

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>安裝程式記錄檔
若**個人閘道**無法安裝，您會看到顯示安裝記錄檔的連結。 安裝記錄檔會顯示失敗的相關詳細資料。 這些記錄檔是 Windows 安裝記錄檔，也稱為 MSI 記錄檔。 可能相當複雜且難以閱讀。 產生的錯誤通常會在底部，但判斷錯誤的原因並非易事。 原因有可能是不同記錄的錯誤結果，或是記錄中更上層錯誤的結果。

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

或者，您可以改為前往**暫存資料夾** (%temp%) 尋找開頭為 **Power\_BI\_** 的檔案。

> [!NOTE]
> %temp% 可能位在暫存資料夾的子資料夾內。**Power\_BI\_** 檔案會在暫存目錄的根目錄中。  您可能需要向上一或兩個層級。
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>後續步驟
[進行內部部署資料閘道的 Proxy 設定](/data-integration/gateway/service-gateway-proxy)  
[資料重新整理](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[為磚錯誤進行疑難排解](refresh-troubleshooting-tile-errors.md)  
[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

