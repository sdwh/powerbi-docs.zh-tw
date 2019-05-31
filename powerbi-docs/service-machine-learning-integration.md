---
title: Power BI 與 Azure Machine Learning 的整合 (預覽)
description: 了解如何搭配 Power BI 使用 Machine Learning
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 6c09392566805f2857c50784f16c0e3f9d4b5697
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61232343"
---
# <a name="azure-machine-learning-integration-in-power-bi-preview"></a>Power BI 與 Azure Machine Learning 的整合 (預覽)

許多組織使用 **Machine Learning** 模型來取得關於其業務的更好的見解與預測。 在您的報告與儀表板和其他分析中，能夠從這些模型視覺化及叫用見解的能力有助於傳播這些見解給最需要它的企業使用者。  Power BI 現在可讓您輕鬆使用直覺的點按手勢整合來自 Azure Machine Learning 服務上裝載之模型的見解。

若要使用此功能，資料科學家可以使用 Azure 入口網站將對 Azure ML 模型的存取權授與 BI 分析師。  接著，在每個工作階段開頭，Power Query 會探索使用者有權存取的所有 Azure ML 模型並將它們公開為動態 Power Query 函式。  使用者接著可以透過從 Power Query 編輯器中的功能區存取函式，或透過直接叫用 M 函式，來叫用那些函式。 Power BI 也會在針對一組資料列叫用 Azure ML 模型時自動分存取要求分批，以獲得更好的效能。

目前只有 Power BI 資料流程與 Power BI 服務中的線上 Power Query 支援此功能。

若要深入了解資料流程，請參閱 [Power BI 中的自助資料準備](service-dataflows-overview.md)。

若要深入了解 Azure Machine Learning，請參閱：

- 概觀：[什麼是 Azure Machine Learning 服務？](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml)
- Azure Machine Learning 的快速入門與教學課程：[Azure Machine Learning 文件](https://docs.microsoft.com/azure/machine-learning/)

## <a name="granting-access-to-the-azure-ml-model-to-a-power-bi-user"></a>將對 Azure ML 模型的存取權授與 Power BI 使用者

若要從 Power BI 存取 Azure ML 模型，使用者必須有對 Azure 訂用帳戶的**讀取**存取權。  此外：

- 針對 Machine Learning Studio 模型，需要對 Machine Learning Studio 服務的**讀取**存取權。
- 針對 Machine Learning Studio 模型，需要對 Machine Learning Studio 工作區的**讀取**存取權。

此文章中的步驟說明如何將對 Azure ML 上裝載之模型的存取權授與 Power BI 使用者，以便他們能以 Power Query 函式形式存取此模型。  如需進一步的詳細資料，請參閱[使用 RBAC 與 Azure 入口網站管理存取權](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal)。

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 移至 [訂用帳戶]  頁面。 您可以透過 Azure 入口網站左側瀏覽功能表中的 [所有服務]  清單找到 [訂用帳戶]  頁面。

    ![Azure 訂用帳戶頁面](media/service-machine-learning-integration/machine-learning-integration_01.png)

3. 選取您的訂用帳戶。

    ![選取您的訂用帳戶](media/service-machine-learning-integration/machine-learning-integration_02.png)

4. 選取 [存取控制 (IAM)]  ，然後選取 [新增]  按鈕。

    ![存取控制 AIM](media/service-machine-learning-integration/machine-learning-integration_03.png)

5. 選取 [讀者]  做為 [角色]。 選取您希望為其授與對 Azure ML 模型之存取權的 Power BI 使用者。

    ![選取 [讀者] 做為 [角色]](media/service-machine-learning-integration/machine-learning-integration_04.png)

6. 選取 [儲存]  。

7. 重複步驟三到六以將**讀者**存取權授與特定 Machine Learning Studio Web 服務或  裝載模型之 Machine Learning 服務工作區的使用者。


## <a name="schema-discovery-for-machine-learning-service-models"></a>針對 Machine Learning Service 模型的結構描述探索

資料科學家主要使用 Python 來開發甚至是部署其 Machine Learning Service 機器學習模型。  不像 Machine Learning Studio 會協助自動化為模型建立結構描述檔案的工作，在 Machine Learning Service 的案例中，資料科學家必須明確地使用 Python 產生結構描述檔案。

此結構描述檔案必須包含在

## <a name="invoking-the-azure-ml-model-in-power-bi"></a>在 Power BI 中叫用 Azure ML 模型

您可以直接從您資料流程中的 Power Query 編輯器叫用任何您已獲授與存取權的 Azure ML 模型。 若要存取 Azure ML 模型，請針對您要從您的 Azure ML 模型豐富見解的實體選取 [編輯]  按鈕，如下列影像所示。

![Power BI 服務 - 編輯實體](media/service-machine-learning-integration/machine-learning-integration_05.png)

選取 [編輯]  按鈕以針對您資料流程中的實體開啟 Power Query 編輯器。

![Power Query 編輯器](media/service-machine-learning-integration/machine-learning-integration_06.png)

選取功能區中的 [AI 見解]  按鈕，然後從左側瀏覽功能表選取 [Azure Machine Learning 模型]  資料夾。 您擁有存取權的所有 Azure ML 模型會在這裡列為 Power Query 函式。 此外，Azure ML 模型的輸入參數會自動對應為對應之 Power Query 函式的參數。

若要叫用 Azure ML 模型，您可以從下拉式清單中指定任何所選實體的資料行作為輸入。 您也可以將資料行圖示切換至 [輸入] 對話方塊的左側，以指定要當作輸入使用的常數值。

![選取資料行](media/service-machine-learning-integration/machine-learning-integration_07.png)

選取 [叫用]  來檢視 Azure ML 模型的輸出作為實體資料表中新資料行的預覽。 您也將看到模型叫用作為查詢套用的步驟。

![選取叫用](media/service-machine-learning-integration/machine-learning-integration_08.png)

如果模型傳回多個輸出參數，它們會群組在一起以記錄形式的輸出資料行。 您可以展開資料行，在不同的資料行中產生個別的輸出參數。

![展開 資料行](media/service-machine-learning-integration/machine-learning-integration_09.png)

一旦您儲存資料流程之後，當您針對實體資料表中任何新的或更新的資料列重新整理資料流程時，將會自動叫用模型。

## <a name="next-steps"></a>後續步驟

此文章提供將 Machine Learning 整合到 Power BI 服務的概觀。 下列文章可能也很有趣且實用。 

* [教學課程：在 Power BI 中叫用 Machine Learning Studio 模型 (預覽)](service-tutorial-invoke-machine-learning-model.md)
* [教學課程：在 Power BI 中使用認知服務](service-tutorial-use-cognitive-services.md)
* [Power BI 中的認知服務 (預覽)](service-cognitive-services.md)

如需資料流程的詳細資訊，您可以閱讀這些文章：
* [在 Power BI 中建立及使用資料流程](service-dataflows-create-use.md)
* [使用 Power BI Premium 上的計算的實體](service-dataflows-computed-entities-premium.md)
* [使用內部部署資料來源的資料流程](service-dataflows-on-premises-gateways.md)
* [Power BI 資料流程的開發人員資源](service-dataflows-developer-resources.md)
* [資料流程與 Azure Data Lake 的整合 (預覽)](service-dataflows-azure-data-lake-integration.md)


