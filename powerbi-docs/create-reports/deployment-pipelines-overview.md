---
title: 部署管線概觀
description: 了解什麼是 Power BI 中的部署管線
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: 5522d84cab235270a2eb368be02cfa0fb4e5eaa9
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557133"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>部署管線簡介 (預覽)

在現今的世界中，分析是在幾乎每個組織中進行決策的重要部分。 Power BI 作為分析工具的用途日益增加，要求其使用更多的資料、吸引人且方便使用。 不過，在所有的情況下，Power BI 必須一律是可用且可靠的。 為了符合這些需求，BI 建立者必須有效率地共同作業。

部署管線是一種有效率且可重複使用的工具，可讓企業中具有 Premium 容量的 BI 建立者管理組織內容的生命週期。 這可讓終端使用者在使用報表、儀表板與資料集之前，先進行 Power BI 內容的開發及測試。

此工具的設計是具有三個階段的管線：

* **<a name="development"></a>開發**
    
    這個階段是用來與其他建立者一起設計、建置及上傳新內容。 這是部署管線中的第一個階段。

* **<a name="test"></a>測試**

    上傳內容並在開發階段進行所有變更之後，即可將內容移到這個階段進行測試。 以下是可在測試環境中完成的三個範例：

    * 與測試人員和檢閱者共用內容

    * 載入並執行包含大量資料的測試

    * 測試您的應用程式，以查看終端使用者將看到的外觀

* **<a name="production"></a>生產**

    測試內容之後，請使用生產階段來與組織中的商務使用者共用內容的最終版本。

![運作中部署管線的螢幕擷取畫面，其全部三個階段 ([開發]、[測試] 與 [生產環境]) 皆已經填入。](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[開始使用部署管線](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[了解部署管線程序](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[部署管線疑難排解](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[部署管線最佳做法](deployment-pipelines-best-practices.md)