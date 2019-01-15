---
title: 從 Power BI Desktop 檔案取得資料
description: 了解如何從 Power BI Desktop 取得資料和報表並放入 Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 8173e78428af5392c2a359df20a1df65b1b8b988
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275655"
---
# <a name="get-data-from-power-bi-desktop-files"></a>從 Power BI Desktop 檔案取得資料
![](media/service-desktop-files/pbid_file_icon.png)

**Power BI Desktop** 讓商業智慧和報表變得容易。 不論您是要連接到許多不同的資料來源、查詢和轉換資料、建立資料模型，還是建立強大的動態報表，**Power BI Desktop** 都讓商業智慧工作變得直接易懂又快速。 如果您不熟悉 **Power BI Desktop**，請參閱[開始使用 Power BI Desktop](desktop-getting-started.md)。

當您將資料放入 **Power BI Desktop**，並建立一些報表後，您就能夠將儲存的檔案放入 **Power BI 服務**。

## <a name="where-your-file-is-saved-makes-a-difference"></a>檔案的儲存位置會形成差異
**本機** - 如果您將檔案儲存到電腦上的本機磁碟或組織中的其他位置，您可以「匯入」檔案或從 Power BI Desktop「發佈」，以將其資料和報表放入 Power BI。 您的檔案實際上會保留在本機磁碟，因此不是真的將整個檔案移至 Power BI。 真正發生的情況是在 Power BI 中建立新的資料集，並將資料和資料模型從 Power BI Desktop 檔案載入資料集。 如果您的檔案有任何報表，這些報表會顯示在 Power BI 網站的 [報表] 下。

**OneDrive - 商務** - 如果您有商務用 OneDrive，並使用與用來登入 Power BI 相同的帳戶進行登入，這樣做可以有效地讓 Power BI Desktop 中的工作，與 Power BI 中的資料集、報表和儀表板保持同步。由於 Power BI 和 OneDrive 都在雲端，因此 Power BI 每隔約一小時就會「連接」到您在 OneDrive 上的檔案。 如果發現任何變更，便會自動更新 Power BI 中的資料集、報表和儀表板。

**OneDrive - 個人** - 如果您將檔案儲存到自己的 OneDrive 帳戶，則可以利用許多與使用商務用 OneDrive 相同的優點。 最大的差異是當您第一次連接到檔案時 (使用 [取得資料] > [檔案] > [OneDrive - 個人])，需要使用 Microsoft 帳戶登入 OneDrive，這通常與用來登入 Power BI 的帳戶不同。 當您使用 Microsoft 帳戶登入 OneDrive 時，請務必選取 [讓我保持登入] 選項。 如此一來，Power BI 每隔約一小時就會連接到您的檔案，以確保您在 Power BI 中的資料集保持同步。

**SharePoint 小組網站** - 將 Power BI Desktop 檔案儲存到 SharePoint - 小組網站與儲存到商務用 OneDrive 大致相同。 最大的差異是從 Power BI 連接到檔案的方式。 您可以指定 URL 或連接到根資料夾。

## <a name="import-or-connect-to-a-power-bi-desktop-file-from-power-bi"></a>從 Power BI 匯入或連接到 Power BI Desktop 檔案
>[!IMPORTANT]
>您可以匯入 Power BI 的檔案大小上限為 1 GB。

1. 在 Power BI 的導覽器窗格中，按一下 [取得資料]。
   
   ![](media/service-desktop-files/pbid_get_data_button.png)
2. 在 [檔案] 中，按一下 [取得]。
   
   ![](media/service-desktop-files/pbid_files_get.png)
3. 尋找您的檔案。 Power BI Desktop 檔案的副檔名為 .PBIX。
   
   ![](media/service-desktop-files/pbid_find_your_file.png)

## <a name="publish-a-file-from-power-bi-desktop-to-your-power-bi-site"></a>將檔案從 Power BI Desktop 發佈至您的 Power BI 網站
使用 Power BI Desktop 的 [發佈]，實際上就是使用 Power BI 的 [取得資料] 從本機磁碟匯入檔案或連接到 OneDrive 上的檔案。  以下是快速操作說明，但您可以參閱[從 Power BI Desktop 發佈](desktop-upload-desktop-files.md)以深入了解。

1. 在 Power BI Desktop 中，按一下 [檔案] > [發佈] > [發佈至 Power BI]，或在功能區上按一下 [發佈]。
   
   ![](media/service-desktop-files/pbid_publish.png)
2. 登入 Power BI。 只有第一次才需要執行這項作業。
   
   完成時，就會得到連結，用於在 Power BI 網站中開啟報表。
   
   ![](media/service-desktop-files/pbid_publishing.png)

## <a name="next-steps"></a>後續步驟
**瀏覽您的資料** - 將檔案中的資料和報表匯入 Power BI 後，您就可以開始瀏覽。 如果您的檔案已經有報表，即會顯示在導覽器窗格的 [報表] 中。 如果檔案只有資料，您可以建立新報表；請直接以滑鼠右鍵按一下新資料集，然後按一下 [瀏覽]。

**重新整理外部資料來源** - 如果您的 Power BI Desktop 檔案連接到外部資料來源，您可以設定排定的重新整理，確保資料集一律為最新狀態。 在大多數情況下，設定排定的重新整理相當容易，但細節部分則不在本文的討論範圍內。 如需深入了解，請參閱 [Power BI 的資料重新整理](refresh-data.md)。

