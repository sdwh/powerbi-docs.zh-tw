---
title: Power BI 資料集屬性
description: 了解 Power BI 資料集 API 的屬性
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: e74e390a5d228cb4a158d422cf0adab48b573cce
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079661"
---
# <a name="dataset-properties"></a>資料集屬性

資料集 API 目前的 v1 只允許用名稱和資料表集合建立資料集。 每個資料表各包含一個名稱和一個資料行集合。 每個資料行各有名稱和資料類型。 我們將擴充這些屬性，最值得注意的是支援資料表間的量值和關聯性。 這個版本支援的屬性完整清單如下：

> [!IMPORTANT]
> 它可以在 [Datasets Operation Groups](https://docs.microsoft.com/rest/api/power-bi/datasets) 頁面存取。

## <a name="dataset"></a>資料集

名稱  |類型  |描述  |唯讀  |必要
---------|---------|---------|---------|---------
id     |  Guid       | 系統範圍的資料集唯一識別碼。        | True        | False        
name     | 字串        | 使用者定義的資料集名稱。        | False        | True        
資料表     | Table[]        | 資料表集合。        |  False       | False        
關聯性     | Relationship[]        | 資料表之間的關聯性集合。        | False        |  False  
defaultMode     | 字串        | 用 "Push" 和 "Streaming" 值，決定要對資料集執行推送、串流或兩者。         | False        |  False

## <a name="table"></a>資料表

名稱  |類型  |描述  |唯讀  |必要
---------|---------|---------|---------|---------
name     | 字串        |  使用者定義的資料表名稱。 其也用作資料表的識別碼。       | False        |  True       
資料行     |  column[]       |  資料行集合。       | False        |  True       
量值     | measure[]        |  量值集合。       | False        |  False       
isHidden     | 布林值        | 若為 true，資料表會從用戶端工具隱藏。        | False        | False        

## <a name="column"></a>資料行

名稱  |類型  |描述  |唯讀  |必要
---------|---------|---------|---------|---------
name     |  字串        | 使用者定義的資料行名稱。        |  False       | True       
dataType     |  字串       |  支援的 [EDM 資料類型](https://msdn.microsoft.com/library/ee382832.aspx)與限制。 請參閱[資料類型](#data-type-restrictions)限制。      |  False       | True        
formatString     | 字串        | 描述顯示值時應如何設定其格式的字串。 若要深入了解字串格式設定，請參閱 [FORMAT_STRING 內容](https://msdn.microsoft.com/library/ms146084.aspx)。      | False        | False        
sortByColumn    | 字串        |   要用以排序目前資料行的相同資料表中，資料行的字串名稱。     | False        | False       
dataCategory     | 字串        |  用於描述此資料行內資料之資料類別的字串值。 常見的值包括：Address、City、Continent、Country、Image、ImageUrl、Latitude、Longitude、Organization、Place、PostalCode、StateOrProvince、WebUrl       |  False       | False        
isHidden    |  布林值       |  指出資料行是否從檢視隱藏的屬性。 預設為 false。       | False        | False        
summarizeBy     | 字串        |  資料行的預設彙總方法。 值包括：default、none、sum、min、max、count、average、distinctCount     |  False       | False

## <a name="measure"></a>量值

名稱  |類型  |描述  |唯讀  |必要
---------|---------|---------|---------|---------
name     | 字串        |  使用者定義的量值名稱。       |  False       | True        
運算式     | 字串        | 有效的 DAX 運算式。        | False        |  True       
formatString     | 字串        |  描述顯示值時應如何設定其格式的字串。 若要深入了解字串格式設定，請參閱 [FORMAT_STRING 內容](https://msdn.microsoft.com/library/ms146084.aspx)。       | False        | False        
isHidden     | 字串        |  若為 true，資料表會從用戶端工具隱藏。       |  False       | False       

## <a name="relationship"></a>關聯性

名稱  |類型  |描述  |唯讀  |必要 
---------|---------|---------|---------|---------
name     | 字串        | 使用者定義的關聯性名稱。 其也用作關聯性的識別碼。        | False       | True        
crossFilteringBehavior     | 字串        |    篩選關聯性的方向：OneDirection (預設)、BothDirections、Automatic       | False        | False        
fromTable     | 字串        | 外部索引鍵資料表的名稱。        | False        | True         
fromColumn    | 字串        | 外部索引鍵資料行的名稱。        | False        | True         
toTable    | 字串        | 主索引鍵資料表的名稱。        | False        | True         
toColumn     | 字串        | 主索引鍵資料行的名稱。        | False        | True        

## <a name="data-type-restrictions"></a>資料類型限制

這些限制適用於 dataType 屬性。

資料類型  |限制  
---------|---------
Int64     |   不允許 Int64.MaxValue 和 Int64.MinValue。      
Double     |  不允許 Double.MaxValue 和 Double.MinValue 值。 不支援 NaN。部分函式 (例如 Min、Max) 不支援 +Infinity 和 -Infinity。       
布林值     |   True 或 False。
Datetime    |   在資料載入期間，會以一天時間分數將值量化為 1/300 秒 (3.33 毫秒) 的整數倍數。      
字串     |  每個字串值目前都允許最多 4000 個字元。
小數位數|精確度=28、小數位數=4

## <a name="example"></a>範例
下列程式碼範例包括其中數個屬性：

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```