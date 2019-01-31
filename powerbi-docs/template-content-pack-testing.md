---
title: 測試 Power BI 的範本內容套件
description: 範本內容套件測試
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/09/2017
ms.author: maggies
ms.openlocfilehash: 8a5382a5e435f916599b05310f89d9b1f0327023
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430663"
---
# <a name="testing-template-content-packs-for-power-bi"></a>測試 Power BI 的範本內容套件
在送出內容套件以供發行之前，您可以透過多種方式測試該內容套件。  

> [!NOTE]
> 如果您的內容套件使用您開發的自訂[資料連接器](https://aka.ms/DataConnectors)，您就無法如下所述測試資料重新整理或範本內容套件。 如果是這樣，請前往[提交](#submission)您的內容套件，Power BI 小組會和您一起測試您的內容套件。
> 
> 

## <a name="testing-scheduled-data-refresh"></a>測試排程的資料重新整理
範本內容套件利用 PowerBI.com 中的重新整理，在連線時以客戶資料來實例化內容套件。 在公開推出內容套件之前，您可以透過您已建立的 Desktop 檔案來測試此流程。

上傳檔案後，選取資料集旁的 [...]，並選取 [排程重新整理]。 設定來源的認證。 請確定您的資料集已成功重新整理，請嘗試 [立即重新整理] 和 [排程的重新整理]。 如果重新整理發生任何一次失敗，請查看錯誤訊息，並驗證您的查詢和終端系統。

### <a name="additional-refresh-tips"></a>其他重新整理秘訣
* 嘗試排程重新整理時，應該只會偵測到一個資料來源  
* 測試連接應該會表示您的使用者將可載入內容套件。 若非如此，請確定您的查詢可處理其他錯誤情況。  
* 重新整理應在合理的時間內完成，建議為 5 分鐘內  

![設定](media/template-content-pack-testing/scheduledrefresh.png)

<a name="templates"></a>

## <a name="testing-templates"></a>測試範本
除了範本內容套件不會在資料集中包含實際資料以外，其與現有的解決方案非常類似。 相反地，使用者使用或實例化範本時，系統會提示其輸入參數和認證才能連線。 連線之後，其便會在儀表板、報表和資料集中看到自己的資料。 

使用者將內容套件具現化之後，即可存取資料庫設定 (包括排程的重新整理)，資料集上的任何 RLS 設定都**不會**隨內容套件發行。  

> [!NOTE]
> 範本內容套件只能包含 1 個儀表板、1 份報表和 1 個資料集。 請參閱[撰寫](template-content-pack-authoring.md#restrictions)頁面中的限制清單。 
> 
> 

若要為您的租用戶建立範本，請與您的 Power BI 系統管理員共同啟用下列功能切換。 

![功能切換](media/template-content-pack-testing/featureswitch.png)

啟用後，您會在 [[建立內容套件]](https://app.powerbi.com/groups/me/publish-content/) 底部看到一個核取方塊，該核取方塊可讓您將範本內容套件發行至您的組織。 

![核取方塊](media/template-content-pack-testing/checkbox.png)

### <a name="naming"></a>命名
我們建議您在內容套件中以一致的方式命名儀表板、報表和資料集。 這些名稱是硬式編碼，且對所有使用者都會相同，因此使用您的產品/案例名稱可讓您的客戶更容易找出這些項目。

### <a name="additional-template-tips"></a>其他範本秘訣
* 確定您在查詢中指定的參數對使用者具有意義
* 請考慮使用者等候排程的重新整理完成的時間長度

![建立](media/template-content-pack-testing/createtemplate.png)

<a name="submission"></a>

## <a name="submission"></a>送出
透過 [Microsoft AppSource](https://appsource.microsoft.com/partners/list-an-app) 的提交程序會讓您在 PowerBI.com 的服務內容套件庫發行您的範本內容套件，以及在 [Microsoft AppSource](http://appsource.microsoft.com) 中列示您的內容套件。

### <a name="before-submission"></a>送出前
* 針對內容套件中的每個成品檢閱撰寫秘訣
* 透過各種帳戶和資料條件進行測試和連線。 (如果您已開發自己自訂的[資料連接器](https://aka.ms/DataConnectors)，請略過此步驟。)
* 檢閱所有視覺特效，並仔細查看是否有拼字錯誤的項目
* 確定內容套件可妥善回應問與答，我們建議您在資料模型中至少測試 30 個不同的問題。 (如果您已開發自己自訂的[資料連接器](https://aka.ms/DataConnectors)，請略過此步驟。)

### <a name="submission"></a>送出
作好提交準備後，請前往 AppSource 的[應用程式提交頁面](https://appsource.microsoft.com/partners/list-an-app)並提交您的資訊。 請務必從可用的產品清單中選取 Power BI

Power BI 小組會檢閱您提交的內容，並與您連絡以確定所有成品都符合提交需求。 除了正在完成的項目以外，我們也會驗證提供的儀表板和報表品質，並確保其符合應用程式中所述的商務案例。

### <a name="updates"></a>更新
遵循與原始送出類似的流程來更新您的內容套件。 

