---
title: 移轉到 powerbi-visuals-tools 3.x
description: 開始使用新版的 powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 245475feeb43ee544117aaa54969f2de1e207cd5
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74696274"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>移轉到新的 powerbi-visuals-tools 3.x.x

從第 3 版開始，Power BI 視覺效果工具會使用 Webpack 來建置自訂視覺效果。
新版本為開發人員帶來許多建立視覺效果的新機會：

* 預設為 TypeScript v3.x.x。 從 TypeScript 1.5 開始，命名法已變更。 [深入了解 TypeScript 模組](https://www.typescriptlang.org/docs/handbook/modules.html) \(英文\)。

* 支援 ES6 模組。 您不再需要使用 [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries)，請改為使用 ES6 匯入。

* 支援新版的 [D3v5](https://d3js.org/) \(英文\) 和其他以 ES6 模組為基礎的程式庫。

* 已縮減套件大小。 Webpack 使用 [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) \(英文\) 來移除未使用的程式碼。 其會縮減 JS 的程式碼；因此，您可以在載入視覺效果時獲得更好的效能。

* 已改善 API 效能。

* Globalize.js 程式庫[已整合](migrate-to-new-tools.md#remove-globalizejs-library)到 formatting-utils。

* 工具會使用 [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) \(英文\) 來顯示視覺效果的程式碼基底。

以下描述所有適用於新版 Power BI 視覺效果工具的移轉步驟。

## <a name="backward-compatibility"></a>回溯相容性

新工具為舊的視覺效果程式碼基底保留回溯相容性，但可能需要進行一些額外變更，才能載入外部程式庫。

支援模組系統的程式庫將會以 Webpack 模組形式匯入。 所有其他程式庫和視覺效果原始程式碼都將包裝成一個模組。

先前 pbiviz 工具中所使用的全域變數 (例如 JQuery 和 Lodash ) 現已過時。 這表示，如果舊的視覺效果程式碼會在全域變數上轉送，則視覺效果可能會在此情況下中斷。

舊版 Power BI 視覺效果工具必須在 `powerbi.extensibility.visual` 模組底下定義視覺效果類別。

## <a name="how-to-install-powerbi-visuals-tools"></a>如何安裝 powerbi-visuals-tools

您可以執行下列命令來安裝新的工具組

```cmd
npm install -g powerbi-visuals-tools
```

`package.json` 中 SampleBarChart 視覺效果的範例及對應的[變更](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16)：

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>如何安裝 Power BI 自訂視覺效果 API

新版的 powerbi-visual-tools 並未隨附所有 API 版本。 反而是該開發人員應安裝特定版本的 [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api) \(英文\) 套件。 套件的版本會與 Power BI 自訂視覺效果的 API 版本相符，並針對 Power BI 自訂視覺效果 API 提供所有類型定義。

藉由執行 `npm install --save-dev powerbi-visuals-api` 命令，將 `powerbi-visuals-api` 新增至專案的相依性。
因此，您應該移除舊有 API 類型定義的連結。 因為 Webpack 會自動包含來自 `powerbi-visuals-api` 的類型。 對應的變更位於 `package.json` 中的[這](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14)行。

## <a name="update-tsconfigjson"></a>更新 `tsconfig.json`

若要使用外部模組，您應該將 `out` 選項切換為 `outDir`。
`"outDir": "./.tmp/build/",` 而非 `"out": "./.tmp/build/visual.js",`。

這是必要的，因為 TypeScript 檔案將獨立編譯為 JavaScript 檔案。 這就是您不再需要將 visual.js 檔案指定為輸出的原因。

此外，如果您想要使用新式 JavaScript 作為輸出，也可以將 `target` 選項變更為 `ES6`。 [這是選擇性的](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6)。

## <a name="update-custom-visuals-utils"></a>更新自訂視覺效果公用程式

如果您使用其中一個 powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) ，也應該將其更新為最新版本。

執行 `npm install powerbi-visuals-utils-<UTILNAME> --save` 命令。 (例如 `npm install powerbi-visuals-utils-dataviewutils --save`) 以使用 TypeScript 的外部模組來取得新版本。

您可以在 MekkoChart [存放庫](https://github.com/Microsoft/powerbi-visuals-mekkochart)中找到範例。
此視覺效果會使用所有公用程式。

## <a name="remove-globalizejs-library"></a>移除 Globalize.js 程式庫

新版的 [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) 包含現成的 globalize.js。
您不需要手動將此程式庫包含於專案中。
所有必要的當地語系化都將自動新增至最終套件。

## <a name="fix-loading-external-libraries"></a>修正載入外部程式庫

請改為在 `pbiviz.json` 的 `externalJS` 陣列中，將新的 JS 檔案包含於程式庫後面。 範例：

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

匯入來源中的程式庫。 適用於 `lodash-es` 的範例：

```JS
import * as _ from "lodash-es";
```

其中 `_` 是 `lodash` 程式庫的全域變數。

## <a name="changes-in-the-visuals-sources"></a>視覺效果來源中的變更

主要變更是將內部模組轉換為外部模組，因為您無法在內部模組中使用外部模組。

那些變更會描述已套用至範例橫條圖的修改

以下為變更的詳細描述：

1. 從[原始程式碼](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)的每個檔案中移除所有模組定義

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [匯入 Power BI 自訂視覺效果 API 定義](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2)。

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. 從 `powerbi` 內部模組[匯入](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23)必要的介面或類別。

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [匯入](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) D3.js 程式庫

    ```typescript
    import * as d3 from "d3";
    ```

    或者，只匯入必要的 D3 程式庫模組

    ```typescript
    import { max, min } from "d3-array";
    ```

5. 將視覺效果專案中定義的公用程式、類別、介面[匯入](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10)到主要來源檔案

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>匯入 CSS 樣式

新版工具可讓開發人員將 CSS、LESS 樣式直接匯入到 TypeScript 程式碼。

因此，編譯器將忽略先前使用的[樣式區段](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22)。

若要使用您的樣式表，請開啟主要 ts 檔案，並新增下一行：  

```typescript
import "./../style/visual.less";
```  

您的 CSS、LESS 樣式將會自動編譯。  

### <a name="externaljs-section-in-pbivizjson"></a>pbiviz.json 中的 externalJS 區段

工具[不需要](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20)將 `externalJS` 清單載入到視覺效果套件組合。 因為 Webpack 會包含所有匯入的程式庫。

**pbivi.json 中的 externalJS 區段應該是空的。**

呼叫一般命令 `npm run package`，以建立視覺效果套件或 `npm run start` 來啟動開發伺服器。

## <a name="updating-d3js-library-to-version-5"></a>將 D3.js 程式庫更新到第 5 版

利用新工具，您就可以開始使用新版的 D3.js 程式庫。

呼叫命令以更新您視覺效果專案中的 D3

`npm install --save d3@5` 可安裝新的 D3.js。

`npm install --save-dev @types/d3@5` 可安裝適用於 D3.js 的新類型定義。

有數個中斷性變更，而您應該修改程式碼以使用新的 D3.js。

1. `d3.Selection<T>` 介面[已變更](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157)為 `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. 您無法透過 `attr` 方法的單一呼叫來套用數個屬性。 您[應該在不同的 `attr` 方法呼叫中傳遞](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278)每個屬性。 `style` 方法也[類似](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247)。

3. 在 D3.js v4 中，引進了新的合併方法。 此方法通常用來在資料聯結之後合併輸入和更新選取項目。 [呼叫 merge 方法](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272)以正確使用 D3。

[深入了解](https://github.com/d3/d3/blob/master/CHANGES.md) \(英文\) D3.js 程式庫中的相關變更。

## <a name="babel"></a>Babel

從 3.1 版開始，這些工具會使用 Babel 來將新的新式 JS 程式碼編譯為舊的 ES5，以支援各類瀏覽器。

預設會啟用此選項，但您必須手動匯入 [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill) \(英文\) 套件。

執行命令以安裝套件

`npm install --save @babel/polyfill`

然後，將套件匯入到視覺效果程式碼的起點 (通常是 'src/visual.ts' 檔案)：

`import "@babel/polyfill";`

[在文件中](https://babeljs.io/docs/en/) \(英文\) 深入了解 Babel。

最後，執行 [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer)，以顯示視覺效果的程式碼基底。  

![視覺效果程式碼統計資料](./media/webpack-stats.png)
