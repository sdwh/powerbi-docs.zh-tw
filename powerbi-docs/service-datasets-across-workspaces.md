---
title: 跨工作區使用資料集 (預覽) - Power BI
description: 了解如何與整個組織的使用者共用資料集。 然後他們可以您的資料集為基礎，在自己的工作區中建置報表。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a5e4b41b36dfbf6cca14a348268b96eaad21b00e
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461848"
---
# <a name="use-datasets-across-workspaces-preview"></a>跨工作區使用資料集 (預覽)

商業智慧是一項共同作業活動。 建立可成為「真實單一來源」的標準化資料集非常重要。 探索及重複使用這些標準化資料集是關鍵因素。 當組織中的專業資料模型製作者建立並共用最佳化資料集時，報表建立者可以從這些資料集開始建置精確的報表。 然後，組織會擁有一致的資料以進行決策，並擁有健全的資料文化特性。

Power BI 可讓資料集建立者輕鬆認證或推廣資料集，以利其他人探索。 然後，報表作者可以在 Power BI 中找到可讓他們使用的高品質官方資料集。 資料集擁有者可以使用[建置權限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)，掌控誰可以存取資料。 租用戶系統管理員具有[跨工作區管理資料集使用方式](service-datasets-admin-across-workspaces.md)的新租用戶設定。

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>資料集共用和新的工作區體驗

根據不同工作區中的資料集建置報表、將報表複製到不同的工作區，與[新的工作區體驗](service-create-the-new-workspaces.md)緊密結合：

- 在服務中，當您從新工作區體驗中開啟資料集目錄時，資料集目錄會顯示位於「我的工作區」和新工作區體驗工作區中的資料集。 
- 當您從傳統工作區開啟資料集目錄時，您只能看到該工作區中的資料集，無法看到其他工作區中的資料集。
- 在 Desktop 中，只要 Live Connect 報表的資料集位於新體驗工作區中，您即可將其發佈至不同的工作區。
- 跨工作區複製報表時，目標工作區必須是新體驗工作區。

## <a name="build-permission-for-datasets"></a>資料集的建置權限

透過建置權限類型，您可以讓組織中的其他人在現有資料集上建置新內容，例如問與答中的報表、儀表板和釘選圖格。 也可以在 Power BI 外部的資料集建置新內容，例如透過使用 Excel 分析的 Excel 工作表、XMLA 和匯出。 深入了解[建置權限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)。

## <a name="discover-datasets-preview"></a>探索資料集 (預覽)

在現有資料集上建置報表時，第一個步驟是連線至 Power 服務中或 Power BI Desktop 中的資料集。 閱讀[探索不同工作區的資料集 (預覽)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>複製報表

當您找到喜歡的報表時，您可在工作區或應用程式中複製該報表，然後按照您的需求修改該報表。 您不需要建立資料模型。 已經為您建立好了。 修改現有的報表，比從頭開始要輕鬆許多。 深入了解[複製報表](service-datasets-copy-reports.md)。

## <a name="promotion-and-certification"></a>推廣與認證

如果您要建立資料集，請建立一個可讓其他人受益的資料集，並[推廣您的資料集](service-datasets-promote.md)以利他們輕鬆找到。 您也可以要求您組織中的專家[認證您的資料集](service-datasets-certify.md)。

## <a name="licensing"></a>授權

基於共用資料集功能所建置的特定功能和體驗，會根據其現有情況來授權。  例如：

- 在一般情況下，任何人都可探索並連線至共用資料集。 不過，不具有 Pro 授權的使用者，只能連線至位於其個人「我的工作區」或 Premium 工作區的資料集。
- 在個人工作區之外推廣與認證資料集需要 Pro 授權，因為您需要 Pro 授權才能成為應用程式工作區中的成員。
- 在工作區之間複製報表需要 Pro 授權，同樣是因為您需要 Pro 授權才能成為應用程式工作區中的成員。
- 從應用程式複製報表需要 Pro 授權，這是組織內容套件所需。

## <a name="considerations-and-limitations"></a>考量與限制

- 在不同工作區的資料集上建置報表，需要兩端的新工作區體驗：報表必須位於新工作區體驗中，資料集也必須位於新工作區體驗中。
- 在傳統工作區中，資料集探索體驗只會顯示該工作區中的資料集。
- 您可以在應用程式工作區中建立以不同工作區中之資料集為基礎的報表。 不過，您無法為包含這些資料集的工作區建立應用程式。
- Desktop 中的免費使用者只會看到「我的工作區」和 Premium 型工作區的資料集。
- 如果您希望根據共用資料集將報表新增至應用程式，您必須是資料集工作區的成員。 這是已知的問題。
- 「發佈至 Web 」不適用於以共用資料集為基礎的報表。 這是預設行為。
- 如果兩名人員是正在存取共用資料集之工作區的成員，則可能只有其中一個人可以在工作區中查看相關資料集。 只有對資料集具有最低讀取權限的人員，才能查看共用資料集。 

## <a name="next-steps"></a>後續步驟

- [宣傳資料集](service-datasets-promote.md)
- [認證資料集](service-datasets-certify.md)
- [跨工作區管理資料集使用方式](service-datasets-admin-across-workspaces.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
