---
title: "讓資料適用於 Power BI 的問與答"
description: "讓資料適用於 Power BI 的問與答"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 09/26/2017
ms.author: mihart
ms.openlocfilehash: 499c3beca9046af9336de6dfec96994004050986
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="make-your-data-work-well-with-qa-in-power-bi"></a>讓資料適用於 Power BI 的問與答
如果您是建立資料模型的人員，或要建立搭配 Power BI 使用的 Excel 活頁簿，請繼續閱讀...

在 Power BI 中，問與答可搜尋結構化的資料，並為您的問題選擇適當的視覺效果，就是這一點讓它成為大家愛用的工具。   

問與答可以處理任何已上傳的 Excel 檔案 (有資料表、範圍或包含 PowerPivot 模型)，但是最佳化和資料清除執行愈多次，問與答的效能就愈穩固。 

## <a name="how-qa-works"></a>問與答的運作方式
問與答有一組可在您的資料中運作的功能，可了解核心自然語言。 它會搜尋 Excel 資料表、資料行和導出欄位名稱之內容相關的關鍵字。 其次，它有內建如何篩選、排序、彙總、群組和顯示資料的相關知識。 

例如，在一個名為「銷售」的 Excel 資料表，其資料行為「產品」、「月」、「單位銷售」、「銷售毛額」和「利潤」，您可以詢問有關任何這些實體的問題。  您可以要求顯示銷售額、各月份的總計收益、依單位銷售排序產品等等。 深入了解[可提問的問題種類](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-1.aspx)、[使用問題範本詢問](service-q-and-a.md)與[問與答查詢中可以指定的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-a-workbook-for-qa"></a>準備適用於問與答的活頁簿
問與答依賴資料表、資料行和導出欄位的名稱，藉此回應特定資料的問題，這表示您如何在活頁簿中命名實體會相當重要！

以下是在您的活頁簿中善加利用問與答的一些秘訣。

* 請確定您的資料位於 Excel 資料表中。 以下是[如何建立 Excel 資料表](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664?ui=en-US&rs=en-US&ad=US)的說明.
* 請確定您的資料表、資料行和導出欄位的英文名稱合理。
  
  例如，如果您有包含銷售資料的資料表時，請將資料表命名為「銷售額」。 「年」、「產品」、「銷售代表」和「金額」等資料行名稱可適用於問與答。

> [!NOTE]
> 如果您的活頁簿有 PowerPivot 資料模型，您就可以更進一步地最佳化。 深入了解我們內部團隊之自然語言專家的 [Demystifying Power BI Q&A part 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) (揭密 Power BI 問與答第 2 部分)。
> 
> 

## <a name="next-steps"></a>後續步驟
[Power BI 中的問與答](service-q-and-a.md)  
[教學課程：Power BI 問與答簡介](power-bi-visualization-introduction-to-q-and-a.md)  
[取得 Power BI 的資料](service-get-data.md)  
[Power BI - 基本概念](service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

