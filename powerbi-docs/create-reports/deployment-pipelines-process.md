---
title: 部署管線程序
description: 了解 Power BI 部署管線程序
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: c4a823b0b41def6c10cd8f932bb97e91eb977ecb
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148605"
---
# <a name="understand-the-deployment-process-preview"></a>了解部署程序 (預覽)

部署程序可讓您將管線中某個階段的內容複製到另一個階段，通常是從開發到測試，以及從測試到實際執行環境。

在部署期間，Power BI 會將內容從目前階段複製到目標階段。 複製程序期間會保留所複製項目之間的連線。 Power BI 也會將設定的資料集規則套用到目標階段中更新的內容。 視部署的項目數而定，部署內容可能需要花費一些時間。 在這段期間，您可以瀏覽至 Power BI 入口網站中的其他頁面，但不能使用目標階段中的內容。

## <a name="deploying-content-to-an-empty-stage"></a>將內容部署到空白階段

當您將內容部署到空白階段時，會將您要從中部署之工作區中報表、儀表板與資料集的中繼資料複製到您要部署的目標階段。 您要部署之目標階段的新工作區會建立於 Premium 容量上。

有兩種方式可將內容從一個階段部署到下一個階段。 您可以部署所有內容，也可以[選取要部署的內容項目](deployment-pipelines-get-started.md#selective-deployment)。

您也可以從部署管線中較後面的階段，將內容回溯部署到較前面的階段。

部署完成之後，重新整理資料集，如此便可使用新複製的內容。 您必須重新整理資料集，因為資料不會從某個階段複製到另一個階段。 若要了解部署程序期間複製了哪些項目屬性，以及未複製哪些項目屬性，請檢閱[部署期間複製的項目屬性](#item-properties-copied-during-deployment)一節。

### <a name="creating-a-premium-capacity-workspace"></a>建立 Premium 容量工作區

在首次部署期間，部署管線會檢查您是否擁有 Premium 容量權限。  

如果您擁有容量權限，可將工作區的內容複製到您要部署的目標階段，並在 Premium 容量上建立該階段的新工作區。

如果您沒有容量權限，就會建立工作區，但不會複製內容。 您可以要求容量管理員將您的工作區新增至容量，或要求容量的指派權限。 稍後將工作區指派給容量時，您可以將內容部署到此工作區。

### <a name="workspace-and-content-ownership"></a>工作區與內容所有權

部署使用者會自動成為複製資料集的資料集擁有者，以及新工作區的唯一管理員。

## <a name="deploy-content-to-an-existing-workspace"></a>將內容部署到現有的工作區

在工作的生產管線中將內容部署到具有現有工作區的階段，包括下列作業：

* 將新內容當成新增項目部署到已經包含內容的階段。

* 已在目前的工作階段中部署新內容來取代舊內容。

### <a name="deployment-process"></a>部署程序

內容會從目前階段複製到目標階段。 Power BI 可識別目標階段中的現有內容並加以覆寫。 為了識別需要覆寫的內容項目，部署管線會使用父項目與其複製項之間的連線。 建立新內容時會保留此連線。 覆寫作業只會覆寫項目的內容。 項目的識別碼、URL 與權限會保持不變。

在目標階段中，[未複製的項目屬性](deployment-pipelines-process.md#item-properties-that-are-not-copied)會維持其部署之前的樣子。 新內容與新項目會從目前階段複製到目標階段。

### <a name="refreshing-the-dataset"></a>重新整理資料集

盡可能保留目標資料集中的資料。 如果沒有變更資料集，資料在部署之前會維持原狀。

對於小型變更 (例如，新增資料表或導出量值)，Power BI 會保留原始資料，並將重新整理最佳化，以便只重新整理所需的內容。 對於中斷性結構描述變更，或資料來源連線中的變更，則需要完整的重新整理。

### <a name="requirements-for-deploying-to-a-stage-with-an-existing-workspace"></a>使用現有工作區部署到階段的需求

只要部署的內容位於 [Premium 容量](../admin/service-premium-what-is.md)上，符合下列條件的使用者就可以使用現有工作區來將其部署到階段：

* [Pro 使用者](../admin/service-admin-purchasing-power-bi-pro.md)，這是來源與目標部署階段中這兩個工作區的成員。

* 目標工作區中即將部署之所有資料集的擁有者。

如需詳細資訊，請檢閱[權限](#permissions)一節。

## <a name="deployed-items"></a>部署的項目

當您將內容從一個管線階段部署到另一個管線階段時，複製的內容包含下列 Power BI 項目：

* 資料集

* 報表

* 儀表板

### <a name="unsupported-items"></a>不支援的項目

部署管線不支援下列項目：

* 不是源自 .pbix 的資料集

* 以不支援之資料集為基礎的報表

* 工作區無法使用範本應用程式

* 編頁報表

* 資料流程

* 推送資料集

* 活頁簿

## <a name="item-properties-copied-during-deployment"></a>在部署期間複製的項目屬性

在部署期間，會複製下列項目屬性，並覆寫目標階段上的項目屬性：

* 資料來源 (支援[資料集規則](deployment-pipelines-get-started.md#step-4---create-dataset-rules))

* 參數 (支援[資料集規則](deployment-pipelines-get-started.md#step-4---create-dataset-rules))

* 報表視覺效果

* 報表頁面

* 儀表板圖格

* 模型中繼資料

* 項目關聯性

### <a name="item-properties-that-are-not-copied"></a>未複製的項目屬性

下列項目屬性不會在部署期間複製：

* 資料：不會複製資料，只會複製中繼資料

* URL

* 識別碼

* 權限：適用於工作區或特定項目

* 工作區設定：每個階段都有自己的工作區

* 應用程式內容與設定：若要部署您的應用程式，請參閱[部署 Power BI 應用程式](#deploying-power-bi-apps)

下列資料集屬性也不會在部署期間複製：

* 角色指派
    
* 重新整理排程
    
* 資料來源認證
    
* 查詢快取設定 (可繼承自容量)
    
* 簽署設定

## <a name="deploying-power-bi-apps"></a>部署 Power BI 應用程式

[Power BI 應用程式](../consumer/end-user-apps.md)是將內容發佈給免費 Power BI 取用者的建議方式。 使用部署管線，您可以在部署管線中管理 Power BI 應用程式，讓您在應用程式的生命週期內擁有更多的控制和彈性。

建立適用於每個部署管線階段的應用程式，讓您可以從使用者的觀點測試每個應用程式更新。 部署管線可讓您輕鬆管理此程序。 使用工作區卡片中的發佈或檢視按鈕，在特定管線階段中發佈或檢視應用程式。

[![](media/deployment-pipelines-process/publish.png "Publish app")](media/deployment-pipelines-process/publish.png#lightbox)

在生產階段，左下角的主要動作按鈕會在 Power BI 中開啟更新應用程式頁面，讓應用程式使用者能夠使用任何內容更新。

[![](media/deployment-pipelines-process/update-app.png "Update app")](media/deployment-pipelines-process/update-app.png#lightbox)

>[!IMPORTANT]
>部署程序不包含更新應用程式內容或設定。 若要將變更套用到內容或設定，您必須在必要的管線階段手動更新應用程式。

## <a name="permissions"></a>權限

管線權限與工作區權限是分別授與及管理的。 例如，含有管線存取權但不具工作區權限的使用者，將能檢視管線並與其他人共用。 不過，此使用者將無法在管線中或在工作區頁面中檢視工作區的內容，也不能執行部署。

### <a name="user-with-pipeline-access"></a>具有管線存取權的使用者

具有管線存取權的使用者具有下列權限：

* 檢視管線
    
* 與其他人共用管線
    
* 編輯及刪除管線

>[!NOTE]
>管線存取權不會授與權限來檢視工作區內容或對其採取動作。

### <a name="workspace-viewer"></a>工作區檢視者

具有「管線存取權」的工作區檢視者也可以執行下列動作：

* 取用內容

>[!NOTE]
>工作區檢視者無法存取資料集或編輯工作區內容。

### <a name="workspace-contributor"></a>工作區參與者

具有「管線存取權」的工作區參與者也可以執行下列動作：

* 取用內容

* 比較階段

* 檢視資料集

### <a name="workspace-member"></a>工作區成員

具有「管線存取權」的工作區成員也可以執行下列動作：

* 檢視工作區內容
    
* 比較階段
    
* 部署報表與儀表板

* 移除工作區

### <a name="workspace-admin"></a>工作區管理員

具有「管線存取權」的工作區管理員可以執行「工作區成員」動作，而且也可以執行下列動作：

* 指派工作區

* 移除工作區

### <a name="dataset-owner"></a>資料集擁有者

屬於工作區成員或管理員的資料集擁有者也可以執行下列動作：

* 更新資料集
    
* 設定規則

>[!NOTE]
>此節說明部署管線中的使用者權限。 此節所列的權限在其他 Power BI 功能中可能會有不同的應用。

## <a name="limitations"></a>限制

此節列出部署管線中大部分的限制。

* 工作區必須位於  [Premium 容量](../admin/service-premium-what-is.md)。

* 無法部署 Power BI 項目 (例如，具有 Power BI [敏感度標籤](../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi)的報表與儀表板)。

* 無法部署以[累加式重新整理](../admin/service-premium-incremental-refresh.md)設定的資料集。

* 如需工作區限制的清單，請參閱[工作區指派限制](deployment-pipelines-get-started.md#workspace-assignment-limitations)。

* 如需資料集規則限制的清單，請參閱[資料集規則限制](deployment-pipelines-get-started.md#dataset-rule-limitations)

* 如需不支援的項目清單，請參閱[不支援的項目](#unsupported-items)。

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[部署管線的簡介](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[部署管線最佳做法](deployment-pipelines-best-practices.md)

>[!div class="nextstepaction"]
>[開始使用部署管線](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[部署管線疑難排解](deployment-pipelines-troubleshooting.md)