---
title: 開發 Power BI 自訂視覺效果
description: 說明如何開發 Power BI 自訂視覺效果的教學課程
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 11/06/2018
ms.openlocfilehash: 6590e442fc5f183213681dc7d10a7d91e87ac35b
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282371"
---
# <a name="tutorial-developing-a-power-bi-custom-visual"></a>教學課程：開發 Power BI 自訂視覺效果

開發人員可以輕鬆地將自訂視覺效果加入 Power BI，以用於儀表板和報表。 為了協助您開始使用，我們已將所有視覺效果的程式碼發行到 GitHub。

除了視覺效果架構之外，我們還提供測試套件與工具，以協助社群建置適用於 Power BI 的高品質自訂視覺效果。

此教學課程說明如何開發名為 Circle Card 的 Power BI 自訂視覺效果，以在圓形中顯示已設定格式的量值。 Circle Card 視覺效果支援自訂填滿色彩與外框粗細。

在 Power BI Desktop 報表中，卡片被修改成 Circle Cards。

  ![Power BI 自訂視覺效果範例輸出](media/custom-visual-develop-tutorial/circle-cards.png)

在本教學課程中，您會了解如何：
> [!div class="checklist"]
> * 建立 Power BI 自訂視覺效果。
> * 使用 D3 視覺效果元素開發自訂視覺效果。
> * 設定與視覺效果元素的資料繫結。
> * 設定資料值的格式。

## <a name="prerequisites"></a>先決條件

* 如果您尚未註冊 **Power BI Pro**，請先[註冊免費試用](https://powerbi.microsoft.com/en-us/pricing/)，再開始進行。
* 您需要安裝 [Visual Studio Code](https://www.visualstudio.com/)。
* 您需要適用於 Windows 使用者的 [Windows PowerShell](https://docs.microsoft.com/powershell/scripting/setup/installing-windows-powershell?view=powershell-6) 4 或更新版本，亦或是適用於 OSX 使用者的 [Terminal](https://macpaw.com/how-to/use-terminal-on-mac)。

## <a name="setting-up-the-developer-environment"></a>設定開發人員環境

除了先決條件之外，您還需要安裝幾個工具。

### <a name="installing-nodejs"></a>安裝 Node.js

1. 若要安裝 Node.js，請在網頁瀏覽器中瀏覽至 [Node.js](https://nodejs.org) \(英文\)。

2. 下載最新的功能 MSI 安裝程式。

3. 執行安裝程式，然後按照安裝步驟執行。 接受授權合約的條款與所有預設值。

   ![ Node.js 安裝程式](media/custom-visual-develop-tutorial/node-js-setup.png)

4. 將電腦重新開機。

### <a name="installing-packages"></a>安裝套件

現在，您必須安裝 **pbiviz** 套件。

1. 在電腦重新開機之後，開啟 Windows PowerShell。

2. 若要安裝 pbiviz，請輸入下列命令。

    ```powershell
    npm i -g powerbi-visuals-tools
    ```

### <a name="creating-and-installing-a-certificate"></a>建立及安裝憑證

#### <a name="windows"></a>Windows

1. 若要建立憑證，請輸入下列命令。

    ```powershell
    pbiviz --create-cert
    ```

  它會傳回產生「複雜密碼」的結果。 在此案例中，「複雜密碼」是 **_15105661266553327_**。

  ![透過 PowerShell 建立的憑證](media/custom-visual-develop-tutorial/cert-create.png)

2. 現在我們要安裝憑證。 若要安裝憑證，請輸入下列命令。

    ```powershell
    pbiviz --install-cert
    ```

3. 在 [憑證匯入精靈] 中，確認存放區位置已 設定為 [目前使用者]。 接著，選取 [下一步]。

      ![憑證安裝](media/custom-visual-develop-tutorial/install-cert-PowerShell.png)

4. 在 [要匯入的檔案] 步驟中，選取 [下一步]。

5. 在 [私密金鑰保護] 步驟中，在 [密碼] 方塊中，貼上您從建立憑證步驟收到的複雜密碼。同樣地，在此案例中，它是 **_15105661266553327_**。

      ![複製複雜密碼](media/custom-visual-develop-tutorial/cert-install-wizard-show-passphrase.png)

6. 在 [憑證存放區] 步驟中，選取 [將所有憑證放入以下的存放區] 選項。 接著，選取 [瀏覽]。

      ![所有憑證都在下列存放區中](media/custom-visual-develop-tutorial/all-certs-in-the-following-store.png)

7. 在 [選取憑證存放區] 視窗中，選取 [受信任的根憑證授權單位]，然後選取 [確定]。 接著，在 [憑證存放區] 畫面上，選取 [下一步]。

      ![受信任的根憑證](media/custom-visual-develop-tutorial/trusted-root-cert.png)

8. 若要完成匯入，請選取 [完成]。

9. 如果您收到安全性警告，請選取 [是]。

    ![安全性警告](media/custom-visual-develop-tutorial/cert-security-warning.png)

10. 當系統通知匯入成功時，請選取 [確定]。

    ![憑證匯入成功](media/custom-visual-develop-tutorial/cert-import-successful.png)

> [!Important]
> 請勿關閉 Windows PowerShell 工作階段。

#### <a name="osx"></a>OSX

1. 如果左上方的鎖為鎖定狀態，請選取該鎖以解除鎖定。 搜尋 *localhost* 並按兩下憑證。

    ![在 OSX 上安裝 SSL 憑證 1](media/custom-visual-develop-tutorial/install-ssl-certificate-osx.png)

2. 選取 [永遠信任]，然後關閉視窗。

    ![在 OSX 上安裝 SSL 憑證 2](media/custom-visual-develop-tutorial/install-ssl-certificate-osx2.png)

3. 輸入您的使用者名稱和密碼。 選取 [更新設定]。

    ![在 OSX 上安裝 SSL 憑證 3](media/custom-visual-develop-tutorial/install-ssl-certificate-osx3.png)

4. 關閉任何已開啟的瀏覽器。

> [!NOTE]
> 如果系統無法辨識憑證，您可能需要重新啟動電腦。

## <a name="creating-a-custom-visual"></a>建立自訂視覺效果

您現在已經設定好環境，可以開始建立視覺效果了。

您可以[下載](https://github.com/Microsoft/PowerBI-visuals-circlecard)此教學課程的完整原始程式碼。

1. 請確認已安裝 Power BI 視覺效果工具套件。

    ```powershell
    pbiviz
    ```
    您應該會看到下列說明的輸出。

    <pre><code>
        +syyso+/
    oms/+osyhdhyso/
    ym/       /+oshddhys+/
    ym/              /+oyhddhyo+/
    ym/                     /osyhdho
    ym/                           sm+
    ym/               yddy        om+
    ym/         shho /mmmm/       om+
        /    oys/ +mmmm /mmmm/       om+
    oso  ommmh +mmmm /mmmm/       om+
    ymmmy smmmh +mmmm /mmmm/       om+
    ymmmy smmmh +mmmm /mmmm/       om+
    ymmmy smmmh +mmmm /mmmm/       om+
    +dmd+ smmmh +mmmm /mmmm/       om+
            /hmdo +mmmm /mmmm/ /so+//ym/
                /dmmh /mmmm/ /osyhhy/
                    //   dmmd
                        ++

        PowerBI Custom Visual Tool

    Usage: pbiviz [options] [command]

    Commands:

    new [name]        Create a new visual
    info              Display info about the current visual
    start             Start the current visual
    package           Package the current visual into a pbiviz file
    update [version]  Updates the api definitions and schemas in the current visual. Changes the version if specified
    help [cmd]        display help for [cmd]

    Options:

    -h, --help      output usage information
    -V, --version   output the version number
    --install-cert  Install localhost certificate
    </code></pre>

    <a name="ssl-setup"></a>

2. 檢閱輸出，包括支援的命令清單。

    ![支援的命令](media/custom-visual-develop-tutorial/PowerShell-supported-commands.png) 

3. 若要建立自訂視覺效果專案，請輸入下列命令。 **CircleCard** 是專案名稱。

    ```PowerShell
    pbiviz new CircleCard
    ```
    ![新的 CircleCard 結果](media/custom-visual-develop-tutorial/new-circle-card-result.png)

4. 瀏覽至專案資料夾。

    ```powershell
    cd CircleCard
    ```
5. 啟動自訂視覺效果。 您的 CircleCard 視覺效果正在執行，且同時裝載在您的電腦上。

    ```powershell
    pbiviz start
    ```

    ![開始執行自訂視覺效果](media/custom-visual-develop-tutorial/start-running-custom-visual-PowerShell.png)

> [!Important]
> 請勿關閉 Windows PowerShell 工作階段。

### <a name="testing-the-custom-visual"></a>測試自訂視覺效果

在此節中，我們將會上傳 Power BI Desktop 報表，然後編輯要顯示自訂視覺效果的報表，以測試 CircleCard 自訂視覺效果。

1. 登入 [PowerBI.com](https://powerbi.microsoft.com/) > 移至**齒輪圖示** > 然後選取 [設定]。

      ![Power BI 設定](media/custom-visual-develop-tutorial/power-bi-settings.png)

2. 選取 [開發人員]，然後選取 [啟用開發人員視覺效果以供測試] 核取方塊。

    ![[開發人員] 頁面設定](media/custom-visual-develop-tutorial/developer-page-settings.png)

3. 上傳 Power BI Desktop 報表。  

    [取得資料] > [檔案] > [本機檔案]。

    如果沒有已建立的報表，您可以[下載](https://microsoft.github.io/PowerBI-visuals/docs/step-by-step-lab/images/US_Sales_Analysis.pbix)範例 Power BI Desktop 報表。

    ![取得資料](media/custom-visual-develop-tutorial/get-data.png) ![本機檔案](media/custom-visual-develop-tutorial/local-file.png)

    現在要檢視報表，從左側導覽窗格中的 [報表] 區段中選取 [US_Sales_Analysis]。

    ![自訂視覺效果 Desktop 範例](media/custom-visual-develop-tutorial/custom-visual-sample.png)

4. 現在，您需要在 Power BI 服務中編輯報表。

    移至 [編輯報表]。

    ![編輯報表](media/custom-visual-develop-tutorial/edit-report.png)

5. 從 [視覺效果] 窗格選取 [開發人員視覺效果]。

    ![開發人員視覺效果](media/custom-visual-develop-tutorial/developer-visual.png)

    > [!Note]
    > 此視覺效果會呈現您在電腦上啟動的自訂視覺效果。 只有在啟用開發人員設定時才能取得它。

6. 請注意視覺效果已新增至報表畫布。

    ![新增視覺效果](media/custom-visual-develop-tutorial/new-visual-in-report.png)

    > [!Note]
    > 這是非常簡單的視覺效果，它會顯示呼叫 Update 方法的次數。 在這個階段中，視覺效果尚未擷取任何資料。

7. 選取報表中新視覺效果的同時，移至 [欄位] 窗格 > 展開 [Sales] \(銷售\) > 選取 [Quantity] \(數量\)。

    ![銷售數量](media/custom-visual-develop-tutorial/quantity-sales.png)

8. 然後測試新的視覺效果，調整視覺效果的大小，並注意 Update 值會遞增。

    ![調整視覺效果的大小](media/custom-visual-develop-tutorial/resize-visual.png)

若要停止在 PowerShell 中執行的自訂視覺效果，請輸入 Ctrl + C。 當系統提示您終止批次作業時，請輸入 Y，然後按 Enter。

## <a name="adding-visual-elements"></a>新增視覺效果元素

現在，您必須安裝 **D3 JavaScript 程式庫**。 D3 是用來在網頁瀏覽器中產生動態、互動式資料視覺效果的 JavaScript 程式庫。 它使用廣為實作的 SVG HTML5 與 CSS 標準。

現在，您可以開發自訂視覺效果，以顯示包含文字的圓形。

> [!Note]
> 此教學課程中的許多文字項目都可以從[這裡](https://github.com/uve/circlecard)複製。

1. 若要在 PowerShell 中安裝 **D3 程式庫**，請輸入以下命令。

    ```powershell
    npm i d3@3.5.5 --save
    ```

    ![安裝 D3 程式庫](media/custom-visual-develop-tutorial/install-d3-library.png)

2. 若要安裝 **D3 程式庫**的型別定義，請輸入以下命令。

    ```powershell
    npm i @types/d3@3.5
    ```

    ![安裝 D3 程式庫](media/custom-visual-develop-tutorial/install-d3-library-type-def.png)

    此命令會安裝以 JavaScript 檔案為基礎的 TypeScript 定義，讓您可以在 TypeScript (JavaScript 的超集合) 中開發自訂視覺效果。 Visual Studio Code 是開發 TypeScript 應用程式的理想 IDE。

3. 啟動 [Visual Studio Code](https://code.visualstudio.com/)。

    您可以使用下列命令從 PowerShell 啟動 **Visual Studio Code**。

    ```powershell
    code .
    ```

4. 在 [檔案總管] 窗格中，展開 [node_modules] 資料夾，以確認已經安裝 **D3 程式庫**。

    ![Visual Studio Code 中的 D3 程式庫](media/custom-visual-develop-tutorial/d3-library.png)

5. 在 [檔案總管] 窗格中展開 [node_modules] > [@types] > d3，並注意 TypeScript 檔案 (**index.d.ts**)。

    ![Index.d.ts 檔案](media/custom-visual-develop-tutorial/index-d-ts.png)

6. 選取 [pbiviz.json] 檔案。

7. 若要註冊 **D3 程式庫**，請將下列檔案參考輸入到 externalJS 陣列中。 請務必在現有檔案參考與新檔案參考之間加入「逗號」。

    ```javascript
    "node_modules/d3/d3.min.js"
    ```
    ![新增 node_modules/d3/d3.min.js](media/custom-visual-develop-tutorial/adding-node-module.png)

8. 儲存 **pbiviz.json** 檔案的變更。

### <a name="developing-the-visual-elements"></a>開發視覺效果元素

現在我們可以探索如何開發自訂視覺效果，以顯示圓形與範例文字。

1. 在 [檔案總管] 窗格中，展開 [src] 資料夾，然後選取 [visual.ts]。

    > [!Note]
    > 請注意在 **visual.ts** 檔案頂端的註解。 使用 Power BI 自訂視覺效果的權限是根據 MIT 授權的規定免費授與的。 根據該合約所規定，您必須將註解保留在檔案頂端。

2. 將下列預設的自訂視覺效果邏輯從 Visual 類別中移除。
    * 四個類別層級的私用變數宣告。
    * 來自建構函式的所有程式碼行。
    * 來自 update 方法的所有程式碼行。
    * 模組中其餘各行，包括 parseSettings 與 enumerateObjectInstances 方法。

    確認模組程式碼看起來像下面這樣。

    ```typescript
    module powerbi.extensibility.visual {
    "use strict";
    export class Visual implements IVisual {

        constructor(options: VisualConstructorOptions) {

        }

        public update(options: VisualUpdateOptions) {

            }
        }
    }
    ```

3. 在 *Visual* 類別宣告下方，插入下列類別層級屬性。

    ```typescript
     private host: IVisualHost;
     private svg: d3.Selection<SVGElement>;
     private container: d3.Selection<SVGElement>;
     private circle: d3.Selection<SVGElement>;
     private textValue: d3.Selection<SVGElement>;
     private textLabel: d3.Selection<SVGElement>; 
    ```

    ![Visual.ts 檔案類別層級屬性](media/custom-visual-develop-tutorial/visual-ts-file-class-level-properties.png)

4. 將下列程式碼新增到 *constructor*。

    ```typescript
    this.svg = d3.select(options.element)
                 .append('svg')
                 .classed('circleCard', true);
    this.container = this.svg.append("g")
                         .classed('container', true);
    this.circle = this.container.append("circle")
                             .classed('circle', true);
    this.textValue = this.container.append("text")
                                 .classed("textValue", true);
    this.textLabel = this.container.append("text")
                                 .classed("textLabel", true);
    ```

    此程式碼會在視覺效果中新增 SVG 群組，然後新增三個圖形：一個圓形與兩個文字元素。

    若要設定文件中程式碼的格式，請在 **Visual Studio Code 文件**中以滑鼠右鍵選取任一處，然後選取 [格式化文件]。

      ![格式化文件](media/custom-visual-develop-tutorial/format-document.png)

    若要改善可讀性，建議您每次貼上程式碼片段之後，都對文件進行格式設定。

5. 將下列程式碼新增到 *update* 方法。

    ```typescript
    let width: number = options.viewport.width;
    let height: number = options.viewport.height;
    this.svg.attr({
     width: width,
     height: height
    });
    let radius: number = Math.min(width, height) / 2.2;
    this.circle
     .style("fill", "white")
     .style("fill-opacity", 0.5)
     .style("stroke", "black")
     .style("stroke-width", 2)
    .attr({
     r: radius,
     cx: width / 2,
     cy: height / 2
    });
    let fontSizeValue: number = Math.min(width, height) / 5;
    this.textValue
     .text("Value")
     .attr({
         x: "50%",
         y: "50%",
         dy: "0.35em",
         "text-anchor": "middle"
     }).style("font-size", fontSizeValue + "px");
    let fontSizeLabel: number = fontSizeValue / 4;
    this.textLabel
     .text("Label")
     .attr({
         x: "50%",
         y: height / 2,
         dy: fontSizeValue / 1.2,
         "text-anchor": "middle"
     })
     .style("font-size", fontSizeLabel + "px");
    ```

    此程式碼會設定視覺效果的寬與高，然後將視覺效果元素的的屬性與樣式初始化。

6. 儲存 **visual.ts** 檔案。

7. 選取 [capabilities.json] 檔案。

    在第 14 行，移除整個物件元素 (第 14-60 行)。

8. 儲存 **capabilities.json** 檔案。

9. 在 PowerShell 中，啟動自訂視覺效果。

    ```powershell
    pbiviz
    ```

### <a name="toggle-auto-reload"></a>切換自動重新載入

1. 瀏覽回到 Power BI 報表。
2. 在開發人員視覺效果上方浮動的工具列中，選取 [切換自動重新載入]。

    ![切換自動重新載入](media/custom-visual-develop-tutorial/toggle-auto-reload.png)

    此選項可確保您每次儲存專案變更時，視覺效果都會自動重新載入。

3. 從 [欄位] 窗格中，將 [Quantity] \(數量\) 欄位拖曳到開發人員視覺效果中。

4. 確認視覺效果看起來像下面這樣。

    ![圓形開發人員視覺效果](media/custom-visual-develop-tutorial/circle-developer-visual.png)

5. 調整視覺效果的大小。

    請注意圓形與文字會縮放，以符合視覺效果的可用範圍。

    隨著調整視覺效果的大小，update 方法會持續被呼叫，因此產生視覺效果元素的流暢縮放。

    您現在已經開發視覺效果元素。

6. 繼續執行視覺效果。

## <a name="configuring-data-binding"></a>設定資料繫結

定義資料角色與資料檢視對應，然後修改自訂視覺效果邏輯以顯示量值的值與顯示名稱。

### <a name="configuring-the-capabilities"></a>設定功能

修改 **capabilities.json** 檔案，以定義資料角色與資料檢視對應。

1. 在 Visual Studio Code 中，於 **capabilities.json** 檔案內，將 **dataRoles** 陣列中的所有內容 (第 3-12 行) 都移除。

2. 在 **dataRoles** 陣列中，插入下列程式碼。

    ```json
    {
     "displayName": "Measure",
     "name": "measure",
     "kind": "Measure"
    }
    ```
    **dataRoles** 陣列現在定義類型為 **measure** 的單一資料角色，其名稱為 **measure**，且顯示為 **Measure**。 此資料角色可讓您傳遞量值欄位或加總之後的欄位。

3. 在 **dataViewMappings** 陣列中，將所有內容 (第 10-31 行) 都移除。

4. 在 **dataViewMappings** 陣列中，插入下列內容。

    ```json
            {
            "conditions": [
                { "measure": { "max": 1 } }
            ],
            "single": {
                "role": "measure"
            }
           }
    ```
    **dataViewMappings** 陣列現在定義一個可以傳遞到名為 **measure** 之資料角色的欄位。

5. 儲存 **capabilities.json** 檔案。

6. 在 Power BI 中，請注意視覺效果現在可以使用 [Measure] \(量值\) 來設定。

    ![數量量值](media/custom-visual-develop-tutorial/quantity_measure.png)

    > [!Note]
    > 視覺效果尚未包含資料繫結邏輯。

### <a name="exploring-the-dataview"></a>探索資料檢視

1. 在視覺效果上方浮動的工具列中，選取 [顯示資料檢視]。

    ![顯示資料檢視](media/custom-visual-develop-tutorial/show-dataview-toolbar.png)

2. 向下展開到 [single]，然後注意該值。

    ![向下展開到值](media/custom-visual-develop-tutorial/value-display-in-visual.png)

3. 向下展開到 [metadata] 中，然後到 [columns] 陣列中，並請特別注意 [format] 與 [displayName] 值。

    ![Displayname 值](media/custom-visual-develop-tutorial/displayname-and-format-metadata.png)

4. 若要切換回到視覺效果，在視覺效果上方浮動的工具列中，選取 [顯示資料檢視]。

    ![切換回](media/custom-visual-develop-tutorial/show-dataview-toolbar-revert.png)

### <a name="configuring-data-binding"></a>設定資料繫結

1. 在 [Visual Studio Code] 中，於 **visual.ts** 檔案內，將下列陳述式新增為 update 方法的第一個陳述式。

    ```typescript
    let dataView: DataView = options.dataViews[0];
    ```
    ![Update 陣列中的資料檢視](media/custom-visual-develop-tutorial/dataview-in-update-array.png)

    為了方便存取，陳述式將 *dataView* 指派給變數，然後宣告該變數參考 *dataView* 物件。

2. 在 **update** 方法中，將 .text("Value") 取代成下列項目。

    ```typescript
    .text(dataView.single.value as string)
    ```
    ![取代 textValue](media/custom-visual-develop-tutorial/text-value-replace.png)

3. 在 **update** 方法中，將 **.text("Label")** 取代成下列項目。

    ```typescript
    .text(dataView.metadata.columns[0].displayName)
    ```
    ![取代 textLabel](media/custom-visual-develop-tutorial/text-label-replace.png)

4. 儲存 **visual.ts** 檔案。

5. 在 [Power BI] 中，檢閱視覺效果，它現在會顯示值與顯示名稱。

您現在已經設定資料角色，並將視覺效果繫結到資料檢視。

在下一個教學課程中，您將了解如何將格式設定選項新增到自訂視覺效果。

## <a name="debugging"></a>偵錯

如需偵錯自訂視覺效果的祕訣，請參閱[偵錯指南](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/how-to-debug/)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [新增格式設定選項](custom-visual-develop-tutorial-format-options.md)