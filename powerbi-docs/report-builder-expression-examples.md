---
title: Power BI 報表產生器中的運算式範例
description: 在 Power BI 分頁報表產生器的分頁報表中，經常使用運算式來控制內容和報表外觀。
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: db0ea02237a2279c26f2c47cecd3bae794a5cba4
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840295"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Power BI 報表產生器中的運算式範例
在 Power BI 分頁報表產生器的分頁報表中，經常使用運算式來控制內容和報表外觀。 運算式都是以 Microsoft Visual Basic 撰寫，並可使用內建函式、自訂程式碼、報表和群組變數，以及使用者定義的變數。 運算式會以等號 (=) 開頭。   

本主題提供可用來在報表中執行一般工作的運算式範例。  
  
-   日期、字串、轉換和條件式 Visual Basic 函式的 [Visual Basic 函式](#VisualBasicFunctions)範例。  
  
-   彙總及其他內建報表函式的[報表函式](#ReportFunctions)範例。  
  
-   [報表資料的外觀](#AppearanceofReportData)範例，用於變更報表的外觀。  
  
-   [屬性](#Properties)範例，用於設定報表項目屬性來控制格式或可見度。  
  
-   [參數](#Parameters)範例，用於在運算式中使用參數。  
  
-   內嵌自訂程式碼的[自訂程式碼](#CustomCode)範例。  
  
如需簡單和複雜運算式、運算式可用位置以及運算式中可包含參考型別的詳細資訊，請參閱 [Power BI 報表產生器中的運算式](report-builder-expressions.md)底下的主題。 
  
## <a name="functions"></a>函數  
 報表中的許多運算式都包含函式。 您可以使用這些函式來設定資料格式、套用邏輯和存取報表中繼資料。 您可以撰寫運算式，使用來自 Microsoft Visual Basic 執行階段程式庫，以及來自 `xref:System.Convert` 和 `xref:System.Math` 命名空間的運算式。 您可以將其他組件或自訂程式碼的參考新增至函式。 您也可以使用 Microsoft .NET Framework 中的類別，包括 `xref:System.Text.RegularExpressions`。  
  
##  <a name="VisualBasicFunctions"></a> Visual Basic 函式  
 您可以使用 Visual Basic 函式來操作顯示在文字方塊中的資料，或是用於參數、屬性或其他報表區域的資料。 本節提供示範其中一些函式的範例。 如需詳細資訊，請參閱 MSDN 上的 [Visual Basic Runtime Library Members](https://go.microsoft.com/fwlink/?LinkId=198941) (Visual Basic 執行階段程式庫成員)。  
  
 .NET Framework 提供許多自訂格式選項，例如特定日期格式。 如需詳細資訊，請參閱 MSDN 上的[格式化類型](https://go.microsoft.com/fwlink/?LinkId=112024)。  
  
### <a name="math-functions"></a>數學函式  
  
-   **Round** 函式可用來將數字四捨五入為最接近的整數。 下列運算式會將 1.3 四捨五入為 1：  
  
    ```  
    = Round(1.3)  
    ```  
  
     您也可以撰寫運算式，將值四捨五入為您所指定的倍數，類似於 Excel 中的 **MRound** 函式。 將值乘以因數來建立一個整數，將數字四捨五入，再除以同一個因數。 例如，若要將 1.3 四捨五入為 .2 的最接近倍數 (1.4)，請使用下列運算式：  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="DateFunctions"></a> 日期函式  
  
-   **Today** 函式會提供目前日期。 此運算式可用於文字方塊以顯示報表上的日期，或用於參數以根據目前日期篩選資料。  
  
    ```  
    =Today()  
    ```  
  
-   使用 **DateInterval** 函式來提取日期的特定部分。 以下是一些有效的 **DateInterval** 參數：

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    例如，此運算式會顯示今天日期在目前年份的週數：
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   **DateAdd** 函式可用來根據單一參數提供日期範圍。 下列運算式會提供名為 *StartDate* 的參數日期後六個月的日期。  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   **Year** 函式會顯示特定日期的年份。 您可以使用此函式將日期分組在一起，或將年份顯示為一組日期的標籤。 此運算式會提供一組指定銷售訂單日期的年份。 **Month** 函式及其他函式也可用來操作日期。 如需詳細資訊，請參閱 Visual Basic 文件。  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   您可以在運算式中合併函式來自訂格式。 下列運算式會將日期格式從「月-日-年」格式變更為「月-週-週數」。 例如，將 12/23/2009 變更為 12 月第 3 週：  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     當作為資料集中的導出欄位使用時，您可以在圖表中使用此運算式按每個月內的週次來彙總值。  
  
-   下列運算式會將 SellStartDate 值格式化為 MMM-YY。 SellStartDate 欄位是日期時間資料類型。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   下列運算式會將 SellStartDate 值格式化為 dd/MM/yyyy。 SellStartDate 欄位是日期時間資料類型。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   **CDate** 函式會將值轉換成日期。 **Now** 函式會根據系統傳回包含目前日期和時間的日期值。 **DateDiff** 會傳回長數值，指定兩個日期值之間的時間間隔數目。  
  
     下列範例會顯示目前年份的開始日期  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   下列範例會根據目前月份顯示上個月的開始日期。  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   下列運算式會產生 SellStartDate 到 LastReceiptDate 之間的間隔年數。 這些欄位是在兩個不同的資料集中：DataSet1 和 DataSet2。  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   **DatePart** 函式會傳回整數值，其中包含指定日期值的指定元件。下列運算式會傳回表示 DataSet1 中 SellStartDate 第一個值的年份。 因為報表中有多個資料集，所以會指定資料集範圍。  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   **DateSerial** 函式會傳回日期值，表示指定的年、月和日，並將時間資訊設定為午夜。 下列範例會根據目前月份顯示上個月的結束日期。  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   下列運算式會根據使用者選取的日期參數值顯示各種不同日期。  
  
|範例描述|範例|  
|-------------------------|-------------|  
|Yesterday|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|兩天前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|一個月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|兩個月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|一年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|兩年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="StringFunctions"></a> 字串函式  
  
-   使用串連運算子和 Visual Basic 常數來合併多個欄位。 下列運算式在同一個文字方塊中分行傳回兩個欄位：  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   使用 **Format** 函式來設定字串中的日期和數字格式。 下列運算式會顯示完整日期格式的 *StartDate* 和 *EndDate* 參數值：  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     如果文字方塊只包含日期或數字，則您應該使用文字方塊的 Format 屬性來套用格式，而不是使用文字方塊內的 **Format** 函式。  
  
-   **Right**、**Len** 和 **InStr** 函式可用於傳回子字串，例如將 *DOMAIN*\\*username* 修剪為只有使用者名稱。 下列運算式會從名為 *User* 的參數傳回反斜線 (\\) 字元右側的字串部分：  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     下列運算式會產生與上一個運算式相同的值，但使用 .NET Framework `xref:System.String` 類別的成員，而不是 Visual Basic 函式：  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   從多重值參數顯示選取的值。 下列範例會使用 **Join** 函式，將參數 *MySelection* 所選取值串連成可設定為運算式的單一字串，來表示報表項目中的文字方塊值：  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     下列範例會執行與上述範例相同的作業，並在選取的值清單之前顯示文字字串。  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   來自 .NET Framework `xref:System.Text.RegularExpressions` 的 **Regex** 函式可用於變更現有字串的格式，例如設定電話號碼格式。 下列運算式會使用 **Replace** 函式，將欄位中的十位數電話號碼格式從 "*nnn*-*nnn*-*nnnn*" 變更為 "(*nnn*) *nnn*-*nnnn*"：  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  確認 Fields!Phone.Value 的值沒有額外空格且類型為 `xref:System.String`。  
  
### <a name="lookup"></a>Lookup  
  
-   藉由指定索引鍵欄位，您可以使用 **Lookup** 函式從資料集擷取值來表示一對一關聯性，例如索引鍵/值組。 下列運算式會顯示資料集 ("Product") 中的產品名稱，並提供要比對的產品識別碼：  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   藉由指定索引鍵欄位，您可以使用 **LookupSet** 函式從資料集擷取一組值來表示一對多關聯性。 例如，一個人可以有多個電話號碼。 在下列範例中，假設資料集 PhoneList 在每個資料列中包含人員識別碼和電話號碼。 **LookupSet** 會傳回這些值的陣列。 下列運算式會將傳回值合併成單一字串，並顯示 ContactID 所指定人員的電話號碼清單：  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="ConversionFunctions"></a> 轉換函式  
 您可以使用 Visual Basic 函式，將欄位從一種資料類型轉換成另一種資料類型。 轉換函式可用來將欄位的預設資料類型轉換成計算或合併文字所需資料類型。  
  
-   下列運算式會將常數 500 轉換成十進位類型，以便與 Value 欄位中的 Transact-SQL 貨幣資料類型進行比較來篩選運算式。  
  
    ```  
    =CDec(500)  
    ```  
  
-   下列運算式會顯示為多重值參數 *MySelection* 選取的值數目。  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="DecisionFunctions"></a> 決策函式  
  
-   **Iif** 函式會根據運算式是否為 true 傳回兩個值的其中一個。 下列運算式會使用 **Iif** 函式，在 `LineTotal` 的值超過 100 時傳回布林值 **True**。 否則會傳回 **False**：  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   使用多個 **IIF** 函式 (也稱為「巢狀 IIF」) 根據 `PctComplete` 的值傳回三個值其中一個。 下列運算式可放在文字方塊的填滿色彩中，以根據文字方塊中的值變更背景色彩。  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     值大於或等於 10 會顯示綠色背景，介於 1 到 9 之間會顯示藍色背景，而小於 1 會顯示紅色背景。  
  
-   另一個取得相同功能的方式是使用 **Switch** 函式。 當您有三個 (含) 以上的測試條件時，**Switch** 函式會很有用。 **Switch** 函式會傳回與數列中第一個評估為 true 之運算式建立關聯的值：  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     值大於或等於 10 會顯示綠色背景，介於 1 到 9 之間會顯示藍色背景，等於 1 會顯示黃色背景，而小於或等於 0 會顯示紅色背景。  
  
-   測試 `ImportantDate` 欄位的值，如果超過一週，則傳回 "Red"，否則傳回 "Blue"。 此運算式可用來控制報表項目中文字方塊的 Color 屬性：  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   測試 `PhoneNumber` 欄位的值，如果為 **Null** (在 Visual Basic 中為 **Nothing**)，則傳回 "No Value"，否則傳回電話號碼值。 此運算式可用來控制報表項目中文字方塊的值。  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   測試 `Department` 欄位的值，並傳回子報表名稱或 **Null** (在 Visual Basic 中為 **Nothing**)。 此運算式可用於條件式鑽研子報表。  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   測試欄位值是否為 Null。 此運算式可用來控制影像報表項目的 **Hidden** 屬性。 在下列範例中，只有在欄位的值不是 Null 時，才會顯示欄位 [LargePhoto] 所指定的影像。  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   **MonthName** 函式會傳回包含指定月份名稱的字串值。 當欄位包含值 0 時，下列範例會在 Month 欄位中顯示 NA。  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="ReportFunctions"></a> 報表函式  
 在運算式中，您可以新增其他報表函式的參考來操作報表中資料。 本節提供這些函式其中兩個的範例。 
  
###  <a name="Sum"></a> Sum  
  
-   **Sum** 函式可以加總群組或資料區域中的值。 此函式可用於群組標頭或群組尾。 下列運算式會顯示 Order 群組或資料區域中的資料總和：  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   您也可以使用 **Sum** 函式進行條件式彙總計算。 例如，如果資料集具有一個名為 State 的欄位，其可能值包括 Not Started、Started、Finished，則下列運算式放在群組標頭時，只會計算值 Finished 的彙總：  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="RowNumber"></a> RowNumber  
  
-   **RowNumber** 函式用於資料區域內的文字方塊時，會顯示每個文字方塊執行個體 (其中會出現運算式) 的資料列數目。 此函式可用於表示資料表中的資料列數目。 它也可用於更複雜的工作，例如根據資料列數目提供分頁符號。 如需詳細資訊，請參閱本主題中的[分頁符號](#PageBreaks)。  
  
     您為 **RowNumber** 指定的範圍會控制何時開始重新編號。 **Nothing** 關鍵字指出函式會從最外側資料區域的第一個資料列開始計數。 若要從巢狀資料區域內開始計數，請使用資料區域的名稱。 若要從群組內開始計數，請使用群組的名稱。  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="AppearanceofReportData"></a> 報表資料的外觀  
 您可以使用運算式來操作資料在報表上的呈現方式。 例如，您可以在單一文字方塊中顯示兩個欄位的值、顯示報表的相關資訊，或影響分頁符號在報表中的插入方式。  
  
###  <a name="PageHeadersandFooters"></a> 頁首和頁尾  
 當您設計報表時，可能想要在報表尾顯示報表的名稱和頁碼。 若要執行這項操作，您可以使用下列運算式：  
  
-   下列運算式提供報表的名稱及其執行時間。 它可以放在報表尾或報表主體的文字方塊中。 時間格式採用 .NET Framework 的簡短日期格式字串：  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   下列運算式放在報表尾的文字方塊時，提供頁碼和報表中的總頁數：  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 下列範例描述如何在頁面的頁首顯示第一個值和最後一個值，您可能會在目錄清單中找到類似的做法。 此範例假設有一個包含文字方塊 `LastName` 的資料區域。  
  
-   下列運算式放在頁首左邊的文字方塊時，提供頁面上 `LastName` 文字方塊的第一個值：  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   下列運算式放在頁首右邊的文字方塊時，提供頁面上 `LastName` 文字方塊的最後一個值：  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 下列範例描述如何顯示總頁數。 此範例假設有一個包含文字方塊 `Cost` 的資料區域。  
  
-   下列運算式放在頁首或頁尾時，提供頁面上 `Cost` 文字方塊中的值總和：  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  您只能在頁首或頁尾的每個運算式中參考一個報表項目。 此外，您可以在頁首或頁尾運算式中參考文字方塊名稱，但不能參考文字方塊內的實際資料運算式。  
  
###  <a name="PageBreaks"></a> 分頁符號  
 在某些報表中，您可能想要將分頁符號放在指定的資料列數目結尾及/或群組或報表項目上。 若要執行這項操作，請建立包含您所需群組或詳細記錄的群組、將分頁符號新增至群組，然後新增群組運算式依指定的資料列數目分組。  
  
-   下列運算式放在群組運算式時，會對 25 個資料列的每個集合指派一個數字。 如果為群組定義一個分頁符號，則此運算式會每 25 個資料列產生一個分頁符號。  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     若要允許使用者設定每頁的資料列數值，請建立名為 `RowsPerPage` 的參數，並以該參數作為群組運算式的基礎，如下列運算式所示：  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="Properties"></a> 屬性  
 運算式不只會用來顯示文字方塊中的資料。 也可用來變更屬性套用至報表項目的方式。 您可以變更報表項目的樣式資訊，或變更其可見度。  
  
###  <a name="Formatting"></a> 格式化  
  
-   下列運算式用於文字方塊的 Color 屬性時，會根據 `Profit` 欄位的值變更文字的色彩：  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     您也可以使用 Visual Basic 物件變數 `Me`。 此變數是另一種參考文字方塊值的方式。  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   下列運算式用於資料區域中報表項目的 BackgroundColor 屬性時，會在淡綠色到白色之間交替每個資料列的背景色彩：  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     如果您將運算式用於指定的範圍，您可能必須指出彙總函式的資料集：  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  可用的色彩是來自 .NET Framework KnownColor 列舉。  
  
### <a name="chart-colors"></a>圖表色彩  
 若要指定形狀圖的色彩，您可以使用自訂程式碼來控制對應至資料點值的色彩順序。 這可協助您針對多個具有相同類別群組的圖表使用一致的色彩。 
  
###  <a name="Visibility"></a> 可見度  
 您可以使用報表項目的可見度屬性來顯示和隱藏報表中項目。 在資料表等資料區域中，您可以根據運算式中的值，一開始就隱藏詳細資料列。  
  
-   下列運算式用於群組中詳細資料列的初始可見度時，會顯示 `PctQuota` 欄位中所有銷售超過 90% 的詳細資料列：  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   下列運算式在資料表的 Hidden 屬性中設定時，只有在資料表具有超過 12 個資料列時，才會顯示資料表：  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   下列運算式在資料行的 **Hidden** 屬性中設定時，只有在從資料來源擷取資料之後，報表資料集存在欄位時，才會顯示資料行：  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="Hyperlinks"></a> URL  
 您可以使用報表資料來自訂 URL，也可以有條件地控制是否要新增 URL 作為文字方塊的動作。  
  
-   下列運算式作為文字方塊的動作時，會產生自訂 URL 將資料集欄位 `EmployeeID` 指定為 URL 參數。  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   下列運算式會有條件地控制是否要在文字方塊中新增 URL。 此運算式會根據名為 `IncludeURLs` 的參數，讓使用者決定是否要在報表中包含作用中 URL。 此運算式會設定為文字方塊的動作。 藉由將參數設定為 False，然後檢視報表，您就可以在不需要超連結的情況下匯出 Microsoft Excel 報表。  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="ReportData"></a> 報表資料  
 運算式可用來操作報表中所使用的資料。 您可以參閱參數及其他報表資訊。 您甚至可以變更用來擷取報表資料的查詢。  
  
###  <a name="Parameters"></a> 參數  
 您可以在參數中使用運算式來改變參數的預設值。 例如，您可以使用參數，根據用來執行報表的使用者識別碼將資料篩選至特定使用者。  
  
-   下列運算式作為參數的預設值時，會收集報表執行人員的使用者識別碼：  
  
    ```  
    =User!UserID  
    ```  
  
-   若要參考查詢參數、篩選運算式、文字方塊或其他報表區域中的參數，請使用 **Parameters** 全域集合。 此範例假設參數名稱為 *Department*：  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   您可以在報表中建立參數但設定為隱藏。 當報表在報表伺服器上執行時，參數不會出現在工具列中，且報表讀者無法變更預設值。 您可以使用設定為預設值的隱藏參數作為自訂常數。 您可以在任何運算式中使用這個值，包括欄位運算式。 下列運算式會針對名為 *ParameterField* 的參數，識別其預設參數值所指定的欄位：  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="CustomCode"></a> 自訂程式碼  
 您可以在報表中使用自訂程式碼。 自訂程式碼可以內嵌在報表中，或儲存在報表所使用的自訂組件中。  
  
### <a name="using-group-variables-for-custom-aggregation"></a>使用群組變數進行自訂彙總  
 您可以將特定群組範圍的群組區域變數值初始化，然後在運算式中包含該變數的參考。 您可以搭配自訂程式碼使用群組變數的方式之一是實作自訂彙總。 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>在執行階段隱藏 Null 或零值  
 運算式中的某些值可能會在報表處理時評估為 Null 或未定義。 這可能會產生執行階段錯誤，導致文字方塊中顯示 **#Error**，而不是評估的運算式。 **IIF** 函式對於這種行為特別敏感，因為不同於 If-Then-Else 陳述式，**IIF** 陳述式的每個部分會先評估 (包括函式呼叫)，再傳遞到測試 **true** 或 **false** 的常式。 如果 `Fields!Sales.Value` 為 NOTHING，陳述式 `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` 會在轉譯報表中產生 **#Error**。  
  
 若要避免這種情況，請使用下列策略之一：  
  
-   如果欄位 B 的值為 0 或未定義，請將分子設定為 0，並將分母設定為 1；否則，請將分子設定為欄位 A 的值，並將分母設定為欄位 B 的值。  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   使用自訂程式碼函式來傳回運算式的值。 下列範例會傳回目前值與上一個值之間的百分比差異。 這可用來計算任兩個連續值之間的差異，並處理第一個比較的邊緣案例 (沒有上一個值時)，以及上一個值或目前值是否為 **Null** (在 Visual Basic 中為 **Nothing**) 的案例。  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     下列運算式顯示如何針對 "ColumnGroupByYear" 容器 (群組或資料區域)，從文字方塊呼叫此自訂程式碼。  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     這有助於避免執行階段例外狀況。 您現在可以在文字方塊的 **Color** 屬性中使用 `=IIF(Me.Value < 0, "red", "black")` 等運算式，根據值大於或小於 0 有條件地顯示文字。  
  
## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
  
