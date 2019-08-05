---
title: 轉譯事件
description: Power BI 視覺效果可以通知 Power BI 它們已準備好匯出至 Power Point/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425083"
---
# <a name="event-service"></a>事件服務

新的 API 是由三種方法 (started、finished 或 failed) 所組成，這些方法應在轉譯期間呼叫。

當轉譯開始時，自訂視覺效果程式碼會呼叫 renderingStarted 方法來表示已啟動轉譯程序。

如果轉譯成功完成，自訂視覺效果程式碼會立即呼叫 `renderingFinished` 方法，以通知接聽程式 (**主要是「匯出成 PDF」和「匯出成 PowerPoint」** ) 視覺效果的影像已就緒。

如果轉譯程序中發生問題，進而導致自訂視覺效果無法成功完成。 自訂視覺效果程式碼應呼叫 `renderingFailed` 方法，以通知接聽程式轉譯程序尚未完成。 這個方法也會提供失敗原因的選擇性字串。

## <a name="usage"></a>使用量

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>簡單範例。 視覺效果在轉譯時沒有任何動畫

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-with-animation"></a>範例。 具有動畫的視覺效果

如果視覺效果具有用於轉譯的動畫或非同步函式，則應在動畫之後或非同步函式內呼叫 `renderingFinished` 方法。

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>視覺效果認證的轉譯事件

視覺效果的轉譯事件支援是視覺效果認證其中一個需求。 請深入了解[認證需求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
