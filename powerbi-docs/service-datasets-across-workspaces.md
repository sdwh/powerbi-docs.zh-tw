---
title: 跨工作區的資料集簡介 (預覽)
description: 了解如何與整個組織的使用者共用資料集。 然後他們可以您的資料集為基礎，在自己的工作區中建置報表。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/16/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: ace40fed472dc516cce5a761544cc5365566f3cd
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074117"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>跨工作區的資料集簡介 (預覽)

商業智慧是一項共同作業活動。 建立可成為「真實單一來源」的標準化資料集非常重要。 然後關鍵便是探索並重複使用這些標準化資料集。 當組織中的專業資料模型製作者建立並共用最佳化資料集時，報表建立者可以從這些資料集開始建置精確的報表。 然後，組織會擁有一致的資料以進行決策，並擁有健全的資料文化特性。

![選取共用資料集](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

在 Power BI 中，資料集建立者可以使用[建置權限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)，控制誰可以存取其資料。 資料集建立者也可以「認證」  資料集或將其「升階」  ，以利其他人探索。 那樣一來，報表作者便知道有哪些資料集是高品質且正式的，並可以在 Power BI 中撰寫時使用那些資料集。 租用戶系統管理員具有[跨工作區管理資料集使用方式](service-datasets-admin-across-workspaces.md)的新租用戶設定。

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>資料集共用和新的工作區體驗

根據不同工作區中的資料集建置報表、將報表複製到不同的工作區，與[新的工作區體驗](service-create-the-new-workspaces.md)緊密結合：

- 在服務中，當您從新工作區體驗中開啟資料集目錄時，資料集目錄會顯示位於「我的工作區」和其他新工作區體驗工作區中的資料集。 
- 當您從傳統工作區開啟資料集目錄時，您只能看到該工作區中的資料集，無法看到其他工作區中的資料集。
- 在 Power BI Desktop 中，只要 Live Connect 報表的資料集位於新體驗工作區中，您即可將其發佈至不同的工作區。
- 跨工作區複製報表時，目標工作區必須是新體驗工作區。

## <a name="discover-datasets-preview"></a>探索資料集 (預覽)

在現有資料集上建置報表時，第一個步驟是連線至 Power BI 服務或 Power BI Desktop 中的資料集。 閱讀[探索不同工作區的資料集 (預覽)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>複製報表

當您找到喜歡的報表時，您可在工作區或應用程式中複製該報表，然後按照您的需求修改該報表。 您不需要建立資料模型。 已經為您建立好了。 修改現有的報表，比從頭開始要輕鬆許多。 深入了解[複製報表](service-datasets-copy-reports.md)。

## <a name="build-permission-for-datasets"></a>資料集的建置權限

使用建置權限類型時，如果您是資料集建立者，則可以判斷組織中的哪些人員可在資料集上建置新內容。 具有建置權限的人員也可以在 Power BI 外部的資料集上建置新內容，例如透過使用 Excel 分析、XMLA 和匯出的 Excel 工作表。 深入了解[建置權限](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)。

## <a name="promotion-and-certification"></a>推廣與認證

如果您要建立資料集，則在建立一個可讓其他人受益的資料集時，可以[將您的資料集升階](service-datasets-promote.md)以利他們輕鬆找到。 您也可以要求您組織中的專家[認證您的資料集](service-datasets-certify.md)。

## <a name="licensing"></a>授權

基於共用資料集功能所建置的特定功能和體驗，會根據其現有情況來授權。 例如：

- 在一般情況下，任何人都可探索並連線至共用資料集。 不過，沒有具有 Pro 授權的使用者，只能連線至位於其個人「我的工作區」的資料集。
- 如果這兩個工作區 (一個包含內容，另一個包含資料集) 裝載於 Premium 容量中，則沒有 Pro 授權的使用者只能取用依據共用資料集所建置報表和儀表板。
- 在 Power BI Desktop 中，沒有 Pro 授權的使用者，只能看到其「我的工作區」中的資料集。
- 在工作區之間複製報表需要 Pro 授權。
- 從應用程式複製報表需要 Pro 授權，這是組織內容套件所需。
- 將資料集升階和認證資料集需要 Pro 授權。

## <a name="considerations-and-limitations"></a>考量與限制

- 在不同工作區的資料集上建置報表，需要兩端的新工作區體驗：報表必須位於新工作區體驗中，資料集也必須位於新工作區體驗中。
- 假設您在工作區 A 中建立以工作區 B 資料集為基礎的報表。當您建立工作區 A 的應用程式時，如果您也是工作區 B 的成員，則只能在工作區 A 應用程式中包含該報表。
- 在傳統工作區中，資料集探索體驗只會顯示該工作區中的資料集。
- 如果您希望根據共用資料集將報表新增至應用程式，您必須是資料集工作區的成員。 這是已知的問題。
- 根據設計，「發佈至 Web 」不適用於以共用資料集為基礎的報表。
- 如果兩名人員是正在存取共用資料集之工作區的成員，則可能只有其中一個人可以在工作區中查看相關資料集。 只有對資料集具有最低讀取權限的人員，才能查看共用資料集。 

## <a name="next-steps"></a>後續步驟

- [宣傳資料集](service-datasets-promote.md)
- [認證資料集](service-datasets-certify.md)
- [跨工作區管理資料集使用方式](service-datasets-admin-across-workspaces.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)
