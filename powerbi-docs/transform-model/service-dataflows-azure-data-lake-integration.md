---
title: 資料流程與 Azure Data Lake 整合
description: Power BI 資料流程如何與 Azure Data Lake Storage Gen2 整合的概觀
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5b13fdc1f65fe2650ea0fb4fee1be20611ac3e8b
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83307489"
---
# <a name="dataflows-and-azure-data-lake-integration-preview"></a>Dataflows and Azure Data Lake 整合 (預覽)

根據預設，搭配 Power BI 使用的資料儲存在 Power BI 提供的內部儲存體中。 透過整合資料流程與 Azure Data Lake Storage Gen2 (ADLS Gen2)，您可以在組織的 Azure Data Lake Storage Gen2 帳戶中儲存資料流程。 

![Azure 儲存體中的資料流程](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_01.jpg)

## <a name="how-cdm-folders-relate-to-dataflows"></a>CDM 資料夾與資料流程的關係

有了**資料流程**之後，使用者和組織就能整合來自不同來源的資料，並為模型化做好準備。 使用通用資料模型 (CDM) 時，組織就能使用跨應用程式和部署提供語意一致性的資料格式。 與 Azure Data Lake Storage gen2 (ADLS Gen2) 搭配之後，就能將更細部的存取和授權控制項套用至 Azure 中的 Data Lake。 結合時，這些元素就能為應用程式提供吸引人的集中式資料、結構化資料、更細部的存取控制，以及語意一致性，並在整個企業中起始。

以 CDM 格式儲存的資料能夠為組織中所有的應用程式和部署提供語意一致性。 CDM 與 ADLS Gen2 整合之後，就可以使用包含標準 CDM 格式結構描述化資料的 CDM 資料夾，將相同的結構化一致性和語意意義套用至 (ADLS Gen2) 中儲存的資料。 Azure Data Lake 中的標準化中繼資料和自我描述資料有助於簡化中繼資料探索，以及資料產生者和取用者 (例如 Power BI、Azure Data Factory、Azure Data Lake、Databricks 和 Azure Machine Learning (ML)) 之間的互通性。 

資料流程會以下列格式將其定義和資料儲存在 CDM 資料夾中：

**Model.json**
* **Model.json** 中繼資料描述檔案包含和實體記錄與屬性有關的語意資訊，以及基礎資料檔案的連結。 Model.json 檔案的存在會指示 CDM 中繼資料格式的合規性，而且可能包含標準實體，而該實體中則具有應用程式可使用的其他豐富且立即可用的語意中繼資料。
* Power BI 也會儲存每個資料來源資訊，以及.Power BI 服務中資料流程編輯器體驗所產生的「查詢和轉換」  。 資料來源的密碼不會儲存在模型檔案中。

**資料檔案**
* 資料檔案包含在CDM 資料夾中，其結構和格式已妥善定義 (子資料夾是選擇性的，如本文稍後所述)，並且會在 model.json 檔案中參考這些資料檔案。 目前，資料檔案必須是 .csv 格式，但後續更新可能支援其他格式。 

下圖顯示由 Power BI 資料流程建立並包含三個實體的 CDM 資料夾範例：

![Azure 儲存體中的資料流程](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_01.jpg)

上圖中的 model.json 或中繼資料檔案上會提供對整個 CDM 資料夾實體資料檔的指標。

## <a name="power-bi-organizes-cdm-folders-in-the-data-lake"></a>Power BI 會組織 Data Lake 中的 CDM 資料夾

有了 Power BI 資料流程並和 ADLS Gen2 整合之後，Power BI 就可以在 Data Lake 中產生資料。 身為資料產生者，Power BI 必須為包含 model.json 檔案和其相關聯資料檔案的每個資料流程建立 CDM 資料夾。 Power BI 會在 Data Lake 中使用「檔案系統」  將其資料與其他資料產生者產生的資料分開儲存。 若要深入了解 Azure Data Lake Storage Gen2 檔案系統和階層命名空間，請參閱[描述它們的文章](https://docs.microsoft.com/azure/storage/data-lake-storage/namespace) \(英文\)。

Power BI 會使用子資料夾避免混淆，並提供已改進的資料組織方式以在「Power BI 服務」  中呈現。 資料夾命名和結構代表工作區 (資料夾) 與資料流程 (CDM 資料夾)。 下圖顯示 Power BI 和其他資料產生者共用之 Data Lake 的可能結構。 每個服務 (在此案例中為 Dynamics 365、Dynamics for Finance and Operation，以及 Power BI) 會建立並維護它們自己的檔案系統。 系統會根據每個服務中的體驗，建立子資料夾以在檔案系統中更妥善地組織 CDM 資料夾。 

![來自 Azure 儲存體中各種服務的資料流程](media/service-dataflows-azure-data-lake-integration/dataflows-azure-integration_02.jpg)

## <a name="power-bi-protects-data-in-the-data-lake"></a>Power BI 會保護 Data Lake 中的資料

Power BI 會使用 Azure Data Lake Storage Gen2 所提供的 *Active Directory OAuth 持有人*權杖與 *POSIX ACl* 功能。 這些功能能夠限制 Power BI 對它在 Data Lake 中所管理檔案系統的存取範圍，也可以限制使用者只能存取他們建立的資料流程或 CDM 資料夾。 

若要建立及管理 Power BI 檔案系統內的 CDM 資料夾，需具備檔案系統的讀取、寫入及執行權限。 在 Power BI 中建立的每個資料流程都會儲存在它自己的 CDM 資料夾中，且系統會將 CDM 資料夾和其內容的唯讀存取權授與資料流程的擁有者。 這種方法可保護 Power BI 所產生資料的完整性，並讓系統管理員能夠使用稽核記錄來監視哪些使用者存取過 CDM 資料夾。 

### <a name="authorizing-users-or-services-for-cdm-folders"></a>授權使用者或服務存取 CDM 資料夾

與資料取用者 (例如需要讀取資料的使用者或服務) 共用 CDM 資料夾的程序，已透過使用 Active Directory OAuth 持有人權杖和 POSIX ACL 簡化。 這樣做讓系統管理員能夠監視哪些人存取過 CDM 資料夾。 唯一需要進行的動作是，將對 CDM 資料夾的存取權授與您所選擇的 Active Directory 物件 (例如使用者群組或服務)。 對於資料產生者以外的任何身分識別，我們建議全部都只授與 CDM 資料夾的唯讀權限。 這樣做可以保護產生者所產生資料的完整性。

若要將 CDM 資料夾新增至 Power BI，新增 CDM 資料夾的使用者應該具備 CDM 資料夾本身和其中任何檔案或資料夾的*讀取* 存取 ACL。 此外，還要有 CDM 資料夾本身和其中任何資料夾的*執行* 存取 ACL。 如需詳細資訊，建議您檢閱[檔案和目錄的存取控制清單](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control#access-control-lists-on-files-and-directories)與[使用 Azure Data Lake Storage Gen2 的最佳做法](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-best-practices) () 文章。


### <a name="alternative-forms-of-authorization"></a>授權替代形式

Power BI 外部的人員或服務也可以利用授權替代形式，這些替代方式允許金鑰持有者存取帳戶中的「所有」  資源、有 Lake 中所有資源的完整存取權，且無法將其存取範圍限制為檔案系統或 CDM 資料夾。 那些替代方式或許是授與存取權的簡易方式，但它們會限制共用 Data Lake 中特定資源的功能，而且不會向使用者提供可稽核哪些人存取儲存體的功能。 [Azure Data Lake Storage Gen2 中的存取控制](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-access-control
) \(英文\) 文章中提供了可用授權配置的完整詳細資料。


## <a name="next-steps"></a>後續步驟

本文提供了 Power BI 資料流程、CDM 資料夾，以及 Azure Data Lake Storage Gen2 整合的概觀。 如需其他資訊，請參閱下列文章：

如需有關資料流程、CDM 和 Azure Data Lake Storage Gen2 的詳細資訊，請參閱下列文章：

* [設定工作區資料流程設定 (預覽)](service-dataflows-configure-workspace-storage-settings.md)
* [新增 CDM 資料夾成為 Power BI 資料流程 (預覽)](service-dataflows-add-cdm-folder.md)
* [連接 Azure Data Lake Storage Gen2 來儲存資料流程 (預覽)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

如需有關資料流程的整體資訊，請參閱這些文章：

* [建立 Power BI 中的資料流程](service-dataflows-create-use.md)
* [在 Power BI Premium 上使用計算實體](service-dataflows-computed-entities-premium.md)
* [搭配內部部署資料來源使用資料流程](service-dataflows-on-premises-gateways.md)
* [Power BI 資料流程的開發人員資源](service-dataflows-developer-resources.md)

如需 Azure 儲存體的詳細資訊，您可以閱讀這些文章：
* [Azure 儲存體安全性指南](https://docs.microsoft.com/azure/storage/common/storage-security-guide)
* [開始使用 Azure 資料服務的 GitHub 範例](https://aka.ms/cdmadstutorial) \(英文\)

如需 Common Data Service 的詳細資訊，您可以閱讀它的概觀文章：
* [Common Data Service - 概觀](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM 資料夾](https://go.microsoft.com/fwlink/?linkid=2045304) \(英文\)
* [CDM 模型檔案定義](https://go.microsoft.com/fwlink/?linkid=2045521) \(英文\)

此外，您隨時都可以試著[向 Power BI 社群發問](https://community.powerbi.com/) \(英文\)。
