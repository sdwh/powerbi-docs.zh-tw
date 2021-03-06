---
title: 部署管線概觀
description: 了解什麼是 Power BI 中的部署管線
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: contperfq1
ms.date: 09/15/2020
ms.openlocfilehash: 58d1adef9a9b2a8a4f818f94da2cb34e6529db83
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90855487"
---
# <a name="introduction-to-deployment-pipelines"></a>部署管線的簡介

在現今的世界中，分析是在幾乎每個組織中進行決策的重要部分。 Power BI 作為分析工具的用途日益增加，要求其使用更多的資料、吸引人且方便使用。 不過，在所有的情況下，Power BI 必須一律是可用且可靠的。 為了符合這些需求，BI 建立者必須有效率地共同作業。

部署管線工具可供 BI 建立者管理組織內容的生命週期。 這項工具對於企業中具有 Premium 容量的建立者而言相當有效率，且可重複使用。 這項工具可供建立者在使用者使用 Power BI 內容之前，事先開發並測試內容。 內容的類型包括報表、儀表板以及資料集。

此工具的設計是具有三個階段的管線：

* **<a name="development"></a>開發**
    
    這個階段是用來與其他建立者一起設計、建置及上傳新內容。 這是部署管線中的第一個階段。

* **<a name="test"></a>測試**

    您已準備好在對內容進行所有變更之後進入測試階段。 您要上傳已修改的內容，以便進入該內容的測試階段。 以下是在測試環境中可使用的三個範例：

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
