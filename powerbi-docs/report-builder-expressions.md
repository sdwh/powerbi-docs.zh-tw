---
title: Power BI 報表產生器中的運算式
description: 在整個 Power BI 分頁報表產生器的分頁報表中會廣泛利用運算式來擷取、計算、顯示、分組、排序、篩選、參數化和格式化資料。
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d3a72fd967eeb24cfa1093d16c4434447d5fc89d
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840617"
---
# <a name="expressions-in-power-bi-report-builder"></a>Power BI 報表產生器中的運算式
  在整個 Power BI 分頁報表產生器的分頁報表中會廣泛利用運算式來擷取、計算、顯示、分組、排序、篩選、參數化和格式化資料。 
  
  許多報表項目屬性都可以設為運算式。 運算式可協助您控制報表的內容、設計和互動。 運算式都是以 Microsoft Visual Basic 撰寫，儲存在報表定義中，並會在您執行報表時由報表處理器評估。  
  
 報表不像 Microsoft Office Excel 等應用程式，可讓您直接在工作表中使用資料，而是要使用作為資料預留位置的運算式。 您必須預覽報表，才能查看來自經評估之運算式的實際資料。 當您執行報表時，報表處理器會在合併報表資料和報表版面配置元素 (例如表格和圖表) 時評估每個運算式。  
  
 在您設計報表時，系統會為您設定許多報表項目的運算式。 例如，當您在報表設計介面上將欄位從資料窗格拖曳到表格儲存格時，便會為欄位將文字方塊值設為簡易運算式。 在下圖中，[報表資料] 窗格會顯示資料集欄位 ID、Name、SalesTerritory、Code 及 Sales。 有三個欄位已新增至表格：[Name]、[Code] 及 [Sales]。 設計介面上的標記法 [Name] 表示基礎運算式 `=Fields!Name.Value`。  
  
![報表產生器設計檢視](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 當您預覽報表時，報表處理器會將表格資料區域與資料連線所提供的實際資料合併，並針對結果集中的每個資料列在表格中顯示一列。  
  
 若要手動輸入運算式，請在設計介面上選取項目，然後使用捷徑功能表和對話方塊來設定項目的屬性。 當您看到 [(fx)] 按鈕或是在下拉式清單中看到 `<Expression>` 值時，表示您可以將屬性設為運算式。 
  
##  <a name="Types"></a> 了解簡單和複雜的運算式  
 運算式會以等號 (=) 開頭，並以 Microsoft Visual Basic 撰寫。 運算式可以包含常數、運算子、內建值 (欄位、集合和函式) 參考以及外部或自訂程式碼參考的組合。  
  
 您可以使用運算式來指定許多報表項目屬性的值。 最常見的屬性是文字方塊和預留位置文字的值。 一般而言，若文字方塊只包含一個運算式，運算式便是文字方塊屬性的值。 若文字方塊包含多個運算式，則每個運算式都是文字方塊中預留位置文字的值。  
  
 根據預設，運算式會以「簡單運算式」  或「複雜運算式」  的形式出現在報表設計介面上。  
  
-   **簡單**：簡單運算式包含內建集合中單一項目的參考，例如資料集欄位、參數或內建欄位。 在設計介面上，簡單運算式會出現在方括號內。 例如，`[FieldName]` 會對應到基礎運算式 `=Fields!FieldName.Value`。 在您建立報表版面配置，並將項目從 [報表資料] 窗格中拖曳到設計介面上時，系統即會自動為您建立簡單運算式。 如需表示不同內建集合之符號的詳細資訊，請參閱[了解簡單運算式的前置符號](#DisplayText)。  
  
-   **複雜**：複雜運算式包含多個內建參考的參考、運算子和函式呼叫。 複雜運算式會在運算式值包含多個簡單參考時，以 <\<Expr>> 的方式顯示。 若要檢視運算式，請在其上暫留並使用工具提示。 若要編輯運算式，請在 [運算式]  對話方塊中開啟它。  
  
 下圖說明文字方塊和預留位置文字的典型簡單和複雜運算式。  
  
![報表產生器運算式預設格式](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 若要顯示範例值而非運算式的文字，請將格式設定套用到文字方塊或預留位置文字。 下圖說明切換至顯示範例值的報表設計介面：  
  
![報表產生器運算式範例格式](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="DisplayText"></a> 了解簡單運算式中的前置符號  

簡單運算式會使用符號指出參考是欄位、參數、內建集合，還是 ReportItems 集合的參考。 下表說明顯示和運算式文字的範例：  
  
|項目|顯示文字範例|運算式文字範例|  
|----------|--------------------------|-----------------------------|  
|資料集欄位|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|報表參數|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|內建欄位|`[&ReportName]`|`=Globals!ReportName.Value`|  
|用於顯示文字的常值字元|`\[Sales\]`|`[Sales]`|  
  
##  <a name="References"></a> 撰寫複雜運算式  
 運算式可以包含函式、運算子、常數、欄位、參數、來自內建集合的項目，以及內嵌自訂程式碼或自訂組件的參考。  
  
 下表列出您可以在運算式中包含的參考類型：  
  
|參考|描述|範例|  
|----------------|-----------------|-------------|  
|常數|描述您可以針對需要常數值的屬性 (例如字型色彩)，透過互動方式存取的常數。|`="Blue"`|  
|運算子|描述您可以用來在運算式中合併參考的運算子。 例如， **&** 運算子可以用來串連字串。|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|內建集合|描述您可以在運算式中包含的內建集合，例如 `Fields`、`Parameters` 和 `Variables`。|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|內建報表和彙總函式|描述您可以從運算式存取的內建函式 (例如 `Sum` 或 `Previous`)。|`=Previous(Sum(Fields!Sales.Value))`|  
|報表產生器中運算式內的自訂程式碼和組件參考 |描述如何存取內建 CLR 類別 `xref:System.Math` 和 `xref:System.Convert`、其它 CLR 類別、Visual Basic 執行階段程式庫函式，或是來自外部組件的方法。<br /><br /> 描述如何存取內嵌在您報表中的自訂程式碼，或是您在報表用戶端及報表伺服器上編譯及安裝為自訂組件的自訂程式碼。|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="Valid"></a> 驗證運算式  
 當您為特定報表項目屬性建立運算式時，您可以在運算式中包含的參考取決於該報表項目屬性可接受的值，以及評估屬性的範圍。 例如：  
  
-   根據預設，運算式 [Sum] 會計算評估運算式時範圍內的資料總和。 針對表格儲存格，範圍則取決於列及行群組成員資格。 
  
-   針對 Font 屬性的值，其值必須評估為字型的名稱。  
  
-   運算式語法會在設計階段進行驗證。 運算式範圍驗證則會在您發佈報表時進行。 針對相依於實際資料的驗證，只能在執行階段時偵測錯誤。 這些運算式中的一部分會在轉譯報表中產生 #Error 作為錯誤訊息。 

## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
