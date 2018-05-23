---
title: 具有 Power BI 內嵌內容的自訂配置
description: 了解在您的應用程式中內嵌 Power BI 內容時的自訂配置。
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 12/19/2017
ms.author: maghan
ms.openlocfilehash: fc684ebdf6b1ccb53bdd7794b19c1120ece635a3
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="custom-layouts"></a>自訂配置


使用自訂配置來內嵌具有與原始報告不同配置的報告。 定義新的配置，與只定義一個頁面大小、控制視覺大小或位置和可見性不同。

若要定義自訂配置，請定義自訂配置物件並將它傳遞至內嵌組態的設定物件。 此外，將 LayoutType 設定為 Custom。 若要深入了解，請參閱[內嵌組態詳細資料](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details)。

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom
    customLayout: {...}
    }
};
```

## <a name="object-definition"></a>物件定義

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Cortana,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`：使用頁面大小來控制畫布區域大小 (也就是報告白色區域)。
- `displayOptions`：可能的值為：FitToWidth、FitToPage 或 ActualSize。 這可控制如何縮放畫布以符合 iframe。
- `pagesLayout`：控制每個視覺效果的配置。 如需詳細資料，請參閱 PagesLayout。

## <a name="pages-layout"></a>頁面配置

定義頁面配置物件時，基本上會定義每個頁面的配置，且針對每個頁面，您可以定義每種視覺效果的配置。
PageLayout 是選擇性的。 如果您未定義頁面的配置，將會套用預設配置 (這會儲存在報告中)。

pagesLayout 是從頁面名稱至 PageLayout 物件的對應。 定義：

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

PageLayout 包含視覺配置對應，可將每個視覺效果名稱對應至視覺配置物件：

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>視覺配置

若要定義視覺配置，請傳遞新的位置和大小以及新的可見性狀態。

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`：定義視覺效果的新位置。
- `width`、高度：定義視覺效果的新大小。
- `displayState`：定義視覺效果的可見性。


## <a name="update-layout"></a>更新配置

您可以使用 updateSettings 方法，在載入報告時隨時更新報告配置。 請參閱[更新設定](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings)。

## <a name="code-example"></a>程式碼範例

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;
    
var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom
        customLayout: {
            pageSize: {
                type: models.PageSizeType.Custom,
                width: 1600,
                height: 1200
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};
     
// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');
 
// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);

```


## <a name="see-also"></a>另請參閱

[內嵌 Power BI 儀表板、報告和圖格](embedding-content.md)   
[詢問 Power BI 社群](https://community.powerbi.com/)

