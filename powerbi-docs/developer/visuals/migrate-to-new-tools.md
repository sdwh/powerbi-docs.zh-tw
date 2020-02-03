---
title: 移轉到 powerbi-visuals-tools 3.x 版
description: 開始使用新版的 powerbi-visuals-tools
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818816"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>遷移到新的 powerbi-visuals-tools 3.*x* 版

從第 3 版開始，Power BI Visuals Tools (powerbi-visuals-tools，或 `pbiviz`) 會使用 Webpack 來建置自訂視覺效果。
新版本為開發人員提供許多建立視覺效果的改良功能：

- 預設會使用 TypeScript 3.*x*。 從 TypeScript 1.5 開始，命名法已變更。 [深入了解 TypeScript 模組](https://www.typescriptlang.org/docs/handbook/modules.html) \(英文\)。

- 支援 ECMAScript 6 (ES6) 模組。 立即使用 ES6 匯入，而不是 [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries)。

- 支援新版的資料驅動文件 ([D3v5](https://d3js.org/)) 和其他以 ES6 模組為依據的程式庫。

- 已縮減套件大小。 Webpack 會使用 [Tree shaking](https://webpack.js.org/guides/tree-shaking/)來移除未使用的程式碼。 其會減少 JavaScript 程式碼，並讓您在載入視覺效果時獲得更好的效能。

- 已改善 API 效能。

- Globalize.js 程式庫[已整合](migrate-to-new-tools.md#remove-the- globalizejs-library)到 FormattingUtils 中。

- Power BI Visuals Tools 會使用 [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer)來顯示視覺效果的程式碼基底。

本文說明所有適用於新版 Power BI Visuals Tools 的移轉步驟。

## <a name="backward-compatibility"></a>回溯相容性

新工具為舊的視覺效果程式碼基底保留回溯相容性資訊，但可能需要進行一些額外變更，才能載入外部程式庫。

支援模組系統的程式庫會以 Webpack 模組的形式匯入。 視覺效果的所有其他程式庫和原始程式碼都會包裝成一個模組。

先前 Power BI Visuals Tools 中所使用的全域變數 (例如 JQuery 和 Lodash ) 現已過時。 如果您視覺效果的舊程式碼依賴全域變數，則視覺效果可能無法搭配新工具運作。

舊版 Power BI Visuals Tools 必須在 `powerbi.extensibility.visual` 模組底下定義視覺效果類別。 使用新版工具時，您必須改為在主要 TypeScript (.ts) 檔案中定義視覺效果類別。 該檔案通常是 `src/visual.ts`。

## <a name="install-powerbi-visuals-tools"></a>安裝 powerbi-visuals-tools

執行下列命令來安裝新的工具︰

```cmd
npm install -g powerbi-visuals-tools
```

在視覺效果專案已更新為可搭配新工具運作之後，下列程式碼來自 [sampleBarChart 視覺效果存放庫](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15)中的 `package.json` 檔案：

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>安裝 Power BI 自訂視覺效果 API

新版的 powerbi-visual-tools 並未包含所有的 API 版本。 相反地，您必須安裝特定版本的 [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api) 套件。 選擇與您的 Power BI 自訂視覺效果的 API 版本相符的套件版本。 此套件會提供 Power BI 自訂視覺效果 API 的所有類型定義。

執行下列命令，將 `powerbi-visuals-api` 新增至專案的專案相依性：

```cmd
npm install --save-dev powerbi-visuals-api
```

此外，移除任何舊 API 類型定義的連結，因為 Webpack 會自動包含 `powerbi-visuals-api` 中的類型。 對應的變更位於 [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) 和 [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14)中。

## <a name="update-tsconfigjson"></a>更新 tsconfig.json

若要使用外部模組，請將 `out` 選項變更為 `outDir`。 例如，請使用 `"outDir": "./.tmp/build/",`，而不要使用 `"out": "./.tmp/build/visual.js",`。

這是必要的變更，因為 TypeScript 檔案將獨立編譯為 JavaScript 檔案。 這就是您不再需要將 visual.js 檔案指定為輸出的原因。

如果您想要使用新式 JavaScript 作為輸出，也可以將 `target` 選項變更為 `ES6`。 這是[選擇性](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7)變更。

## <a name="update-custom-visuals-utilities"></a>更新自訂視覺效果公用程式

如果您使用任何一個 [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils)套件，也應該將其更新為最新版本。 若要這麼做，請執行此命令：

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

例如，若要使用 TypeScript 的外部模組來取得新版本，請執行： 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

如需使用所有 `powerbi-visuals-utils` 套件的視覺效果範例，請參閱 [MekkoChart 存放庫](https://github.com/Microsoft/powerbi-visuals-mekkochart)。

## <a name="remove-the-globalizejs-library"></a>移除 Globalize.js 程式庫

新版的 [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) 包含 Globalize.js。 因此，您不需要手動將此程式庫包含於您的專案中。 所有必要的當地語系化都將自動新增至最終套件。

## <a name="configure-loading-of-external-libraries"></a>設定外部程式庫的載入

在 `pbiviz.json` 的 `externalJS` 陣列中，將新的 JavaScript 檔案包含在程式庫後面。 例如：

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

在您的原始程式碼中匯入程式庫。 例如，針對 `lodash-es`，使用下列陳述式：

```JS
import * as _ from "lodash-es";
```

在上述範例中，`_` 是 `lodash` 程式庫的全域變數。

## <a name="make-changes-in-the-sources-of-your-visuals"></a>在視覺效果的來源中進行變更

您必須進行的主要變更，就是將內部模組轉換成外部模組。 您不能在內部模組內使用外部模組。

以下是要進行的變更詳細描述。 這些修改會在長條圖自訂視覺效果程式碼範例的內容中加以說明：

1. 從每個[原始程式碼](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3)檔案中移除所有模組定義：

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [匯入 Power BI 自訂視覺效果 API 定義](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4)：

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. 從 `powerbi` 內部模組[匯入必要的介面或類別](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35)。

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

4. [匯入 D3.js 程式庫](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2)：

    ```typescript
    import * as d3 from "d3";
    ```

    或者，只匯入必要的 D3 程式庫模組：

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [將視覺效果專案中定義的公用程式、類別和介面匯入](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41)到主要來源檔案中：

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

新版工具可讓您將 `CSS` 和 `Less` 樣式直接匯入 TypeScript 程式碼中。 編譯器現在會忽略先前使用的[樣式區段](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21)。

若要使用您的樣式表，請開啟主要 TypeScript (.ts) 檔案並新增以下一行：  

```typescript
import "./../style/visual.less";
```  

您的 `CSS` 和 `Less` 樣式將會自動編譯。

### <a name="externaljs-section-in-pbivizjson"></a>pbiviz.json 中的 externalJS 區段

工具[不需要 `externalJS` 程式庫的清單](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20)載入到視覺效果套件組合中，因為 Webpack 包含所有匯入的程式庫。

> [!NOTE]
> 在 `pbiviz.json`中，將 `externalJS` 區段保留空白。

使用一般命令 `npm run package`建立視覺效果套件，或使用 `npm run start` 啟動開發伺服器。

## <a name="update-the-d3js-library-to-version-5"></a>將 D3.js 程式庫更新到第 5 版

利用新的視覺效果工具，您就可以開始使用新版的 D3.js 程式庫。 執行下列命令以更新您視覺效果專案中的 D3：

- `npm install --save d3@5` 可安裝新的 D3.js。

- `npm install --save-dev @types/d3@5` 可安裝適用於 D3.js 的新類型定義。

> [!IMPORTANT]
> D3 第 5 版引進了幾項重大變更。

修改您的程式碼以使用新的 D3.js：

- `d3.Selection<T>` 介面[已變更](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157)為 `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`。

- 您無法使用 `attr` 方法的單一呼叫來套用數個屬性。 相反地，您必須[將個別呼叫中的每個屬性傳遞](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278)至 `attr`。 此外，對 `style` 方法進行[個別呼叫](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247)。

- D3.js 第 4 版引進了新的 `merge` 方法。 此方法通常用來在資料聯結作業之後合併 `enter` 和 `update` 選取項目。 若要正確使用 D3，[請呼叫 `merge` 方法](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272)。

[深入了解](https://github.com/d3/d3/blob/master/CHANGES.md) D3.js 程式庫中的相關變更。

## <a name="install-babel-and-core-js"></a>安裝 Babel 和 core-js

從 3.1 版開始，視覺效果工具會使用 Babel 將新式 JavaScript 程式碼編譯為舊的 ECMAScript 5 (ES5)，以支援各種瀏覽器。

預設會啟用 Babel 選項，但您必須手動匯入 [`core-js`](https://www.npmjs.com/package/core-js) 套件。 執行下列命令來安裝此套件︰

```cmd
npm install --save core-js
```

然後，在視覺效果程式碼的起點匯入套件。 這通常是 'src/visual.ts' 檔案。

```JS
import "core-js/stable";
```

[在文件中](https://babeljs.io/docs/en/) \(英文\) 深入了解 Babel。
