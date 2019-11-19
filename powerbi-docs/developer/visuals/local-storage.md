---
title: Power BI 視覺效果中的本機存放區 API
description: 本文描述如何使用 Power BI 視覺效果 API 取得瀏覽器本機存放區的存取權
author: uve
ms.author: v-grniki
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: 3b6746b611a41ddfb471008f5aefa4f7dc391456
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432818"
---
# <a name="local-storage-api"></a>本機存放區 API

本機存放區 API 是自訂視覺效果可用以要求主機在裝置存放區儲存或載入資料的 API。 為區隔不同視覺效果類型之間的存放區存取權，所以予以隔離。

## <a name="sample"></a>範例

如果自訂視覺效果在每次呼叫 update 方法時都應增加一些計數器，卻又應該保留計數器值，且不在每次視覺效果啓動時重設：

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>已知限制及問題

預設不針對自訂視覺效果啟動本機存放區 API。 如果想要針對自己的自訂視覺效果啟動它，請將要求傳送給 Power BI 自訂視覺效果支援 `pbicvsupport@microsoft.com`
