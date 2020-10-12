---
title: 將操作功能表新增至 Power BI 視覺效果
description: 了解如何將操作功能表新增至 Power BI 視覺效果。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 9e63a1196ddc7557fcf8b2fceb424415a63d4df9
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748072"
---
# <a name="add-context-menu-to-power-bi-visual"></a>將操作功能表新增至 Power BI 視覺效果

您可以使用 `selectionManager.showContextMenu()` 搭配參數 `selectionId` 和位置 (作為 `{x:, y:}` 物件)，讓 Power BI 顯示視覺效果的操作功能表。

> [!IMPORTANT]
> `selectionManager.showContextMenu()` 是在視覺效果 API 2.2.0 中引進。

通常會新增為以滑鼠右鍵按一下的事件 (或長按觸控裝置) 操作功能表已新增至範例橫條圖以供參考：

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
