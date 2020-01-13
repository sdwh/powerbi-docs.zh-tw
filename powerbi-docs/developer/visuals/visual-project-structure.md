---
title: Power BI 視覺效果專案結構
description: 本文描述視覺化專案的結構
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542085"
---
# <a name="power-bi-visual-project-structure"></a>Power BI 視覺效果專案結構

執行 pbiviz new `<visual project name>` 之後，此工具會在 `<visual project name>` 資料夾中建立檔案和資料夾的基本結構。

## <a name="visual-project-structure"></a>視覺效果專案結構

![視覺效果專案結構](./media/visual-project-structure.png)

* `.vscode` - 包含 VS Code 的專案設定。 若要設定您的工作區，請編輯 `.vscode/settings.json` 檔案。 深入了解[文件中的 VS Code 設定](https://code.visualstudio.com/docs/getstarted/settings)

* `assets` 資料夾僅包含 `icon.png` 檔案。 此工具會在 Power BI 的 [視覺效果] 窗格中，使用此檔案作為視覺效果的圖示。

    ![[視覺效果] 窗格](./media/visualization-pane-analytics-tab.png)

* `node_modules` 資料夾包含[節點套件管理員安裝的](https://docs.npmjs.com/files/folders.html)所有套件。

* `src` 資料夾包含視覺效果的原始程式碼。 此工具預設會建立兩個檔案：

  * `visual.ts` - 視覺效果的主要原始程式碼。

  * `settings.ts` - 視覺效果的設定程式碼。 檔案中的類別可簡化[使用視覺效果屬性的工作](./objects-properties.md#properties)。

* `style` 資料夾包含具有視覺效果樣式的 `visual.less` 檔案。

* `capabilities.json` 檔案包含視覺效果的主要屬性和設定。 此檔案允許視覺效果宣告支援的功能、物件、屬性和資料檢視對應。

    深入了解[文件中的功能](./capabilities.md)。

* `package-lock.json` 會針對 npm 修改 `node_modules` 樹狀結構或 `package.json` 的任何作業自動產生。

    深入了解 [NPM 官方文件中的 `package-lock.json`](https://docs.npmjs.com/files/package-lock.json)。

* `package.json` 描述專案套件。 其中通常包含專案的相關資訊、其作者、描述和專案的相依性。

    深入了解 [NPM 官方文件中的 `package.json`](https://docs.npmjs.com/files/package.json.html)。

* `pbiviz.json` 包含視覺效果中繼資料。 請在這個檔案中指定視覺效果的中繼資料。

    檔案的一般內容：

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    其中

  * `name` - 視覺效果的內部名稱。

  * `displayName` - Power BI UI 介面中的視覺效果名稱。

  * `guid` - 視覺效果的唯一識別碼。

  * `visualClassName` - 視覺效果的主要類別名稱。 Power BI 會建立這個類別的執行個體，以開始使用 Power BI 報表中的視覺效果。

  * `version` - 視覺效果的版本號碼。

  * `author` - 包含作者的名稱和連絡人電子郵件。

  * `assets` 中 `icon` - 視覺效果的圖示檔案路徑。

  * `externalJS` 包含視覺效果所使用 JS 程式庫的路徑。

    > [!IMPORTANT]
    > 最新版的工具 3.x.x 或更高版本不再使用 `externalJS`。

  * `style` 是樣式檔案的路徑。

  * `capabilities` 是 `capabilities.json` 檔案的路徑。

  * `dependencies` 是 `dependencies.json` 檔案的路徑。 `dependencies.json` 包含的資訊與 R 型視覺效果中所使用 R 套件有關。

  * `stringResources` 是當地語系化檔案的路徑陣列。

  深入了解[文件中的視覺效果當地語系化](./localization.md)

* `tsconfig.json` 是 TypeScript 的設定檔。

    深入了解[官方文件中的 TypeScript 設定](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    `files` 區段中的 `tsconfig.json` 必須包含 *.ts 檔案的路徑，其中視覺效果主要類別指定於 `pbiviz.json` 檔案的 `visualClassName` 屬性中。

* `tslint.json` 檔案包含 TSLint 設定。

    深入了解[官方文件中的 TSLint 設定](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>後續步驟

* 深入了解[視覺效果概念](./power-bi-visuals-concept.md)，以進一步了解視覺效果、使用者和 Power BI 彼此互動的方式。

* [透過逐步指南](./custom-visual-develop-tutorial.md)，從頭開始開發您自己的 Power BI 視覺效果。
