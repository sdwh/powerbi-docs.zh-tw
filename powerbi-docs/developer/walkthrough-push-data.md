---
title: "將資料推送至資料集"
description: "將資料推送至 Power BI 資料集"
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 01/05/2017
ms.author: asaxton
ms.openlocfilehash: aba135a0a790025f732379ecb07157f1150d999c
ms.sourcegitcommit: 7517c068db806f12bb0b953e9a1bd4249ca12da5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="push-data-into-a-power-bi-dataset"></a>將資料推送至 Power BI 資料集
您可以使用 Power BI API 將資料推送至 Power BI 資料集。 例如，您會想要擴充現有商務工作流程，將關鍵資料推送至資料集。 在此情況下，您會想要將 Sales Marketing 資料集 (其中含 Product 資料表) 推送至資料集。

開始將資料推送至資料集之前，您需要 Azure Active Directory (Azure AD) 和 [Power BI 帳戶](create-an-azure-active-directory-tenant.md)。

## <a name="steps-to-push-data-into-a-dataset"></a>將資料推送至資料集的步驟
* 步驟 1：[使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)
* 步驟 2：[取得驗證存取權杖](walkthrough-push-data-get-token.md)
* 步驟 3：[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)
* 步驟 4：[取得資料集，以便將資料列加入 Power BI 資料表](walkthrough-push-data-get-datasets.md)
* 步驟 5： [將資料列加入 Power BI 資料表](walkthrough-push-data-add-rows.md)

下一節是有關資料推送的 Power BI API 作業的一般討論。

## <a name="power-bi-api-operations-to-push-data"></a>推送資料的 Power BI API 作業
透過 Power BI REST API，您可以將資料來源推送至 Power BI。 當應用程式將資料列加入資料集時，儀表板上的磚會自動更新為更新的資料。 若要推送資料，您可使用[建立資料集](https://msdn.microsoft.com/library/mt203562.aspx)作業和[加入資料列](https://msdn.microsoft.com/library/mt203561.aspx)作業。 若要找出資料集，您可以使用[取得資料集](https://msdn.microsoft.com/library/mt203567.aspx)作業。 針對任何一項作業，您可以傳遞群組識別碼來和群組合作。 使用[取得群組](https://msdn.microsoft.com/library/mt243842.aspx)作業，以取得群組識別碼清單。

以下是將資料推送至資料集的作業：

* [建立資料集](https://msdn.microsoft.com/library/mt203562.aspx)
* [取得資料集](https://msdn.microsoft.com/library/mt203567.aspx)
* [新增資料列](https://msdn.microsoft.com/library/mt203561.aspx)
* [取得群組](https://msdn.microsoft.com/library/mt243842.aspx)

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

因此，對於我們的 Sales Marketing 資料集範例，您會傳遞 JSON 字串，如以下範例。 在此範例中， **SalesMarketing** 是資料集的名稱，而 **Product** 是資料表的名稱。 定義資料表之後，您會定義資料表的結構描述。 對於 **SalesMarketing** 資料集，資料表結構描述具有下列資料行：ProductID、Manufacturer、Category、Segment、Product 和 IsCompete。

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
| Double |不允許 Double.MaxValue 和 Double.MinValue 值。 不支援 NaN。部分函式 (例如 Min、Max) 不支援 +Infinity 和 -Infinity。 |
| Boolean |無 |
| Datetime |在資料載入期間，會以一天時間分數將值量化為 1/300 秒 (3.33 毫秒) 的整數倍數。 |
| 字串 |目前允許最多 12 萬 8 千個字元。 |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>深入了解如何將資料推送至 Power BI
若要開始將資料推送至資料集，請參閱左側瀏覽窗格中的[步驟 1：使用 Azure AD 註冊應用程式](walkthrough-push-data-register-app-with-azure-ad.md)。

[下一步 >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>後續步驟
[註冊 Power BI](create-an-azure-active-directory-tenant.md)  
[建立資料集](https://msdn.microsoft.com/library/mt203562.aspx)  
[取得資料集](https://msdn.microsoft.com/library/mt203567.aspx)  
[新增資料列](https://msdn.microsoft.com/library/mt203561.aspx)  
[取得群組](https://msdn.microsoft.com/library/mt243842.aspx)  
[JSON 簡介](http://json.org/)  
[Power BI REST API 概觀](overview-of-power-bi-rest-api.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

