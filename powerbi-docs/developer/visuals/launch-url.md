---
title: 啟動 URL
description: Power BI 視覺效果可以在新的索引標籤上開啟 URL
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1a7002c3b45f341c0cbc0db683bc4f8a113e21f9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424853"
---
# <a name="launch-url"></a>啟動 URL

啟動 URL 可藉由將實際工作委派給 Power BI 來開啟新的瀏覽器索引標籤 (或視窗)。

## <a name="sample"></a>範例

```typescript
   this.host.launchUrl('https://powerbi.microsoft.com');
```

## <a name="usage"></a>使用量

您可以使用 `host.launchUrl()` API 呼叫，並傳遞您的目的地 URL 作為字串引數：

```typescript
this.host.launchUrl('http://some.link.net');
```

## <a name="restrictions"></a>限制

* 只能使用絕對路徑，不能使用相對路徑。 `http://some.link.net/subfolder/page.html` 沒問題，`/page.html` 將不會開啟。
* 目前僅支援 `http` 和 `https` 通訊協定。 請避免 `ftp`、`mailto` 等。

## <a name="best-practices"></a>最佳作法

1. 在大部分情況下，最好只在回應使用者的明確動作時才開啟連結。 讓使用者輕鬆了解按一下連結或按鈕會導致開啟新的索引標籤。觸發 `launchUrl()` 呼叫而不需要使用者採取動作，或作為其他動作的副作用，可能會讓使用者感到困惑或挫折。
2. 如果連結對於視覺效果的正常運作並不重要，則建議為報表作者提供停用和隱藏連結的方式。 這與特殊 Power BI 使用案例特別相關，例如將報表內嵌於協力廠商應用程式或發佈至 Web。
3. 避免從迴圈內部、視覺效果的 `update` 函式或任何其他經常重複出現的程式碼觸發 `launchUrl()` 呼叫。

## <a name="step-by-step-example"></a>逐步範例

### <a name="adding-a-link-launching-element"></a>新增連結啟動元素

下列程式碼行已新增至視覺效果的 `constructor` 函式：

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

此外，已新增用於建立和附加錨點元素的私用函式：

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

最後，visual.less 檔案中下列項目會定義連結元素的樣式：

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="adding-a-toggling-mechanism"></a>新增切換機制

這需要新增靜態物件 (請參閱[靜態物件教學課程](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties))，讓報表的作者可以切換連結元素的可見度 (預設會設定為 hidden)。
`showHelpLink` 布林值靜態物件已新增至 `capabilities.json` 物件項目：

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![啟動 URL 切換](./media/launchurl-toggle.png)

此外，在視覺效果的 `update` 函式中，已新增下列程式碼行：

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

`hidden` 類別定義於 visual.less 中，可控制元素的顯示。
