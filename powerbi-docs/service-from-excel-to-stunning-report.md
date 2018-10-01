---
title: 即刻從 Excel 活頁簿到令人驚豔的報表
description: 即刻從 Excel 活頁簿到令人驚豔的報表
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/28/2018
ms.author: mihart
LocalizationGroup: Data from files
ms.openlocfilehash: ebbca73f781946f989b2f3afa65aa0a940f7a680
ms.sourcegitcommit: 0ff358f1ff87e88daf837443ecd1398ca949d2b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46545122"
---
# <a name="from-excel-workbook-to-stunning-report-in-no-time"></a>即刻從 Excel 活頁簿到令人驚豔的報表
您的經理在下班時想要看到您最近的銷售數字以及之前行銷活動效果的報表。 但最新的資料在各種協力廠商系統中，以及您膝上型電腦的檔案內。 在過去，需要好幾個小時的時間才能製作具有各種視覺效果與格式的報表， 所以您覺得有點焦慮。

但別擔心。 有了 Power BI 之後，您可以很快地製作令人讚嘆的報表。

在此範例中，我們將從本機系統上傳 Excel 檔、建立新的報表，並與同事分享 - 全部都從 Power BI 中進行即可。

## <a name="prepare-your-data"></a>準備資料
以一個簡單的 Excel 檔做為範例。 將 Excel 檔載入 Power BI 之前，必須先將資料整理放在二維資料表中。 這表示每個資料行包含相同的資料類型 - 例如，文字、日期、數字或貨幣。 應該要有標題列，但不應該是任何顯示總計的資料行或資料列。

![在 Excel 中組織資料](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

接下來，將資料格式化為資料表。 在 Excel 中，於 [首頁] 索引標籤的 [樣式] 群組中，選取 [格式化為表格] 。 選取要套用至您工作表的表格樣式。 現在 Excel 即已備妥可載入 Power BI 中。

![格式化為資料表的資料](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-into-power-bi"></a>將 Excel 檔上傳到 Power BI
Power BI 可連接至許多資料來源，包括您電腦上的 Excel 檔。 若要開始使用，請登入 Power BI 服務。 若尚未註冊，[可以免費註冊](https://powerbi.com)。

您想要建立新的儀表板。 開啟 [我的工作區]，然後選取 **+ 建立**圖示。

![建立圖示](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

選取 [儀表板]，並輸入名稱，然後選取 [建立]。 即會顯示新的儀表板 -- 不含資料。

![[建立] 下拉式清單](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

在左側功能窗格底部，選取 [取得資料]。 在 [取得資料] 頁面的 [匯入或連接至資料] 下方，於 [檔案] 方塊中選取 [取得] 。

![從檔案取得資料](media/service-from-excel-to-stunning-report/pbi_get_files.png)

在 [檔案] 頁面上，選取 [本機檔案] 。 瀏覽至您電腦上的 Excel 活頁簿檔案，並加以選取，以將其載入 Power BI 中。 選取 [匯入]。

> **注意**︰若要遵循本教學課程的其餘部分，請使用[財務範例活頁簿](sample-financial-download.md)。
> 
> 

![[取得資料] > [檔案] 視窗](media/service-from-excel-to-stunning-report/pbi_local_file.png)

## <a name="build-your-report"></a>建立報表
Power BI 匯入您的 Excel 檔案之後，開始製作報表。 出現 [您的資料集已經就緒] 訊息時，請選取 [檢視資料集]。  Power BI 會以編輯檢視開啟，並顯示報表畫布。 右側為 [視覺效果]、[篩選] 和 [欄位] 窗格。

請注意，您的 Excel 活頁簿資料表資料會出現在 [欄位] 窗格中。 Power BI 會在資料表名稱下，列出資料行標題做為個別的欄位。

![Excel 資料在 [欄位] 窗格中的樣子](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

現在即可開始建立視覺效果。 您的經理想要看一段時間的收益。 在 [欄位] 窗格中，將 [收益]  拖曳至報表畫布。 Power BI 預設會顯示橫條圖。 接著，請將 [日期]  拖曳至報表畫布。 Power BI 會更新橫條圖以依據日期來顯示收益。

![報表編輯器中的直條圖](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

> **提示**︰如果您的圖表看起來與預期不同，請檢查彙總。 例如，在 [值] 區以右鍵按一下您剛新增的欄位，並確認資料以您想要的方式彙總。  在本例中，我們使用 [加總]。
> 
> 

您的經理想要知道利潤最高的國家/地區。 用地圖視覺效果來讓她覺得印象深刻吧。 選取畫布上的空白區域，然後從 [欄位] 窗格中，直接將 [國家/地區] 與 [收益] 欄位拖曳至上方。 Power BI 會建立地圖視覺與泡泡，代表每個地點相對的收益。

![報表編輯器中的地圖視覺效果](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

想要以圖形依產品及市場區段顯示銷售額嗎? 簡單。 在 [欄位] 窗格中，選取 [銷售]、[產品] 及 [市場區隔] 欄位旁的核取方塊。 Power BI 會立即建立橫條圖。 選擇 [視覺效果] 功能表中的任一圖示來，可變更圖表的類型。 例如，將其變更為堆疊橫條圖。  若要排序圖表，請選取省略符號 (...) > [排序依據]。

![報表編輯器中的堆疊直條圖](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

將所有視覺效果都釘選到儀表板。 如此即已就緒可與同事分享。

![已釘選 3 個視覺效果的儀表板](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>共用儀表板
您想要與經理 Paula 共用您的儀表板。 您可以與具有 Power BI 帳戶的任何同事，共用您的儀表板與基礎報表。 他們可以與您的報表互動，但無法儲存變更。

若要共用您的報表，請在儀表板頂端選取 [共用] 。

![共用圖示](media/service-from-excel-to-stunning-report/power-bi-share.png)

Power BI 會隨即顯示 [共用儀表板] 頁面。 請在最上層的區域中，輸入收件者的電子郵件地址。 在以下欄位中加入一則訊息。 若要允許收件者能與其他人共用您的儀表板，請選取 [允許收件者共用您的儀表板] 。 選取 [共用] 。

![[共用儀表板] 視窗](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

後續步驟

* [開始使用 Power BI 服務](service-get-started.md)
* [開始使用 Power BI Desktop](desktop-getting-started.md)
* [Power BI - 基本概念](consumer/end-user-basic-concepts.md)
* 有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

