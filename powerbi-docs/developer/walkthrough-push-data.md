---
title: 將資料推送至資料集
description: 將資料推送至 Power BI 資料集
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222146"
---
# <a name="push-data-into-a-power-bi-dataset"></a>將資料推送至 Power BI 資料集

Power BI API 可讓您將資料推送至 Power BI 資料集。 在本文中，我們說明如何將現有的資料集包含 Product 資料表 Sales Marketing 資料集。

開始之前，您需要 Azure Active Directory (Azure AD) 和[Power BI 帳戶](create-an-azure-active-directory-tenant.md)。

## <a name="steps-to-push-data-into-a-dataset"></a>將資料推送至資料集的步驟

* 步驟 1：[使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)
* 步驟 2：[取得驗證存取權杖](walkthrough-push-data-get-token.md)
* 步驟 3：[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)
* 步驟 4：[取得資料集，以便將資料列新增至 Power BI 資料表](walkthrough-push-data-get-datasets.md)
* 步驟 5：[將資料列新增至 Power BI 資料表](walkthrough-push-data-add-rows.md)

下一節是有關資料推送的 Power BI API 作業的一般討論。

## <a name="power-bi-api-operations-to-push-data"></a>推送資料的 Power BI API 作業

透過 Power BI REST API，您可以將資料來源推送至 Power BI。 當應用程式會將資料列加入至資料集時、 儀表板磚更新會自動使用新的資料。 若要將資料推送，使用[PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)並[PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)作業。 若要尋找的資料集，請使用[取得資料集](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)作業。 您可以傳遞群組識別碼來使用任何一項作業的群組。 若要取得群組識別碼清單，請使用[取得群組](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)作業。

以下是將資料推送至資料集的作業：

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [取得資料集](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [取得群組](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

您可以將 JavaScript 物件標記法 (JSON) 字串傳遞至 Power BI 服務，在 Power BI 中建立資料集。 若要深入了解 JSON，請參閱 [JSON 簡介](http://json.org/)。

資料集的 JSON 字串具有下列格式：

**Power BI 資料集 JSON 物件**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

Sales Marketing 資料集範例中，您會傳遞 JSON 字串，如下所示。 在此範例中， **SalesMarketing**是資料集的名稱，以及**產品**的資料表名稱。 定義資料表之後, 您可以定義資料表結構描述。 針對 **SalesMarketing** 資料集，資料表結構描述具有這些資料行：產品識別碼、製造商、類別、區段，產品和 IsCompete。

**範例資料集物件 JSON**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

在 Power BI 資料表結構描述中，您可以使用下列資料類型。

## <a name="power-bi-table-data-types"></a>Power BI 資料表資料類型

| **資料類型** | **限制** |
| --- | --- |
| Int64 |不允許 Int64.MaxValue 和 Int64.MinValue。 |
| Double |不允許 Double.MaxValue 和 Double.MinValue 值。 不支援 NaN。 + Infinity 和-Infinity 不支援某些函式 (例如 Min、 Max)。 |
| Boolean |無 |
| Datetime |資料載入，使用以 1/300 秒 （3.33 毫秒） 的整數倍數的一天時間分數將值量化。 |
| String |目前允許最多可有 128 個字元。 |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>深入了解如何將資料推送至 Power BI

若要開始將資料推送至資料集，請參閱左側導覽窗格中的[步驟 1：使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)。

[下一步 >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>後續步驟

[註冊 Power BI](create-an-azure-active-directory-tenant.md)  
[JSON 簡介](http://json.org/)  
[Power BI REST API 概觀](overview-of-power-bi-rest-api.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)