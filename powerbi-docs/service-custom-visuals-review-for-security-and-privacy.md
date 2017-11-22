---
title: "檢閱自訂視覺效果的安全性與隱私權"
description: "啟用自訂視覺效果之前，您應該先檢閱該視覺效果的安全性和隱私權，確定它是否符合貴組織的標準。"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/05/2017
ms.author: asaxton
ms.openlocfilehash: 20a697cbc4698e237f3ac09b031ea0c4cb734a52
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="review-custom-visuals-for-security-and-privacy"></a>檢閱自訂視覺效果的安全性與隱私權
啟用自訂視覺效果之前，您應該先檢閱該視覺效果的安全性和隱私權，確定它是否符合貴組織的標準。

## <a name="enable-a-custom-visual"></a>啟用自訂視覺效果
<a name="enable"></a>報表的自訂視覺效果會一直停用到您選擇 [啟用自訂視覺效果] 為止，如下所示。  

![](media/service-custom-visuals-review-for-security-and-privacy/emptyvisual.png)

## <a name="considerations-before-you-enable-a-custom-visual"></a>啟用自訂視覺效果之前的考量
<a name="considerations"></a>

> [!WARNING]
> 自訂視覺效果可能包含有安全性或隱私權風險的程式碼，因此在您選擇 [啟用自訂視覺效果] 之前都會停用報表的自訂視覺效果。 以下的考量可協助您決定是否啟用自訂視覺效果：
> 
> 

1. 確定信任報表所用自訂視覺效果的作者及來源
2. 如果不確定該怎麼做，您應該連絡您的 IT 團隊權衡是否應該啟用所檢視報表的自訂視覺效果。
3. 如果有人與您共用包含自訂視覺效果的報表，即使他們是很親近的同事，也請不要覺得有義務啟用自訂視覺效果。 您可以回頭考慮這項操作對手邊工作的必要性。 如果您覺得自訂視覺效果不保險，您可以要求別人提供無自訂視覺效果的報表，這沒什麼不好。

## <a name="security-best-practices-for-it-professionals-to-enable-a-custom-visual"></a>IT 專業人員啟用自訂視覺效果的安全性最佳作法
<a name="security"></a>

> [!WARNING]
> 自訂視覺效果可能包含有安全性或隱私權風險的程式碼，因此在您選擇 [啟用自訂視覺效果] 之前都會停用報表的自訂視覺效果。 您可以遵循數個最佳作法，用以評估自訂視覺效果的安全性與隱私權。
> 
> 

1. 在組織內實作自訂視覺效果的檢查程序。 自訂視覺效果的檢查結果會透過內部網站與內部使用者共用，例如 SharePoint 文件庫或 OneNote 文件。
2. 為商務使用者提供合適的自訂視覺效果使用手冊，以及可傳送安全性和隱私權問題的電子郵件群組。
3. 評估自訂視覺效果 pbiviz 檔案中的 JavaScript 程式碼。

**評估自訂視覺效果的 JavaScript 程式碼**

自訂視覺效果使用 JavaScript，因此可能有安全性或隱私權風險。 當您收到不明來源的自訂視覺效果或有自訂視覺效果的 pbix 檔案時，您可能會想要檢查 JavaScript 看它安不安全。

若要評估自訂視覺效果的 JavaScript 程式碼，請解壓縮自訂視覺效果的程式碼。 以下是解壓縮程式碼的方法：  

1. 將 .pbiviz 檔案儲存到資料夾。
2. 將檔案重新命名為 .zip 檔案。
3. 將 zip 檔案解壓縮至本機資料夾。

## <a name="custom-visual-file-contents"></a>自訂視覺效果檔案內容
pbiviz 檔案的內容如下：

| **檔案** | **描述** |
|:--- |:--- |
| ./package.json |資訊清單檔，指出使用自訂視覺效果要載入的檔案。 |
| ./resources |包含自訂視覺效果使用的 CSS、TypeScript 和 JavaScript。 |
| ./resources/&lt;name&gt; |&lt;name&gt; 是自訂視覺效果的名稱。 |
| ./resources/&lt;name&gt;.css |自訂視覺效果的 css 資源檔。 |
| ./resources/&lt;name&gt;.js |當使用者按一下 [啟用自訂視覺效果]，或在使用者匯入自訂視覺效果之後執行的程式碼。 警告：JavaScript 程式碼可能有安全性或隱私權風險。 |
| ./resources/&lt;name&gt;.ts |TypeScript 格式視覺效果的 JavaScript 原始程式碼。 警告：JavaScript 或 TypeScript 程式碼可能有安全性或隱私權風險。 |
| ./resources/&lt;name&gt;.png |使用者看到的視覺效果圖示。 |

解壓縮 pbiviz 檔案之後，您就可以評估程式碼。 以下是一些最佳作法和要尋找的威脅。

## <a name="best-practices-to-evaluate-the-javascript-or-typescript-code"></a>評估 JavaScript 或 TypeScript 程式碼的最佳做法
**JavaScript** 或 **TypeScript** 程式碼可能有安全性或隱私權風險。 以下是一些最佳作法和要尋找的威脅。

### <a name="best-practices-to-evaluate-javascript-code"></a>評估 JavaScript 程式碼的最佳作法
* 一定要評估 .js 檔案內容。 這是實際執行的程式碼。 這可能是 .ts 檔案內容沒有編譯成包含在自訂視覺效果中的 .js 檔案。
* 一定要評估 .ts 檔案內容。 您可以將 .ts 檔案載入到**開發人員工具**，然後匯出視覺效果，再比較新建立的 .pbiviz 檔案中產生的 .js 檔案和視覺效果中所包含的原始 .js 檔案
* 檢查自訂視覺效果的圖示是否不像使用者熟悉的其他視覺效果。
* 一定要在擁有最低權限但沒有機密資料存取權的測試帳戶中評估視覺效果。 在理想情況下，測試帳戶應是只有 Power BI 服務登入資訊的本機帳戶。

### <a name="threats-to-look-for-in-javascript-code"></a>要尋找的 JavaScript 程式碼威脅
* 在編輯和檢視模式中同時使用視覺效果時，請檢查網路活動。 確定滿意所提出的要求。 您不該看到對 Power BI 網域外的資源要求，除非視覺效果的作者事先已告知此情況。
* 任何您看到離開 Power BI 網域的資料都應該符合您對所謂「一般」使用的期望。 例如，如果視覺效果實作視訊播放器，使用 IFrame 檢視其他站台的影片，iFrame 要求應該會傳出某些資訊正確播放影片。 但是，如果您看到整個資料集正透過網路傳出，您應該要進一步調查這是否為必要且需要。
* 檢查自訂視覺效果是否傳送或儲存個人的識別資料。
* 檢查自訂視覺效果是否正在嘗試存取本機資源，例如將檔案寫入磁碟，或存取 Cookie。
* 檢查自訂視覺效果是否有看似混亂的程式碼或目的不明的程式碼。
* 儲存過去檢閱過的每種視覺效果的副本。
* 如果您現在檢閱的是先前檢閱過的視覺效果更新，請務必檢查是否有變更。 對待更新，要如同第一次收到檢閱 8 視覺效果一樣的嚴謹
* 如果發現有可疑或不清楚的地方，請連絡我們提供協助。

## <a name="next-steps"></a>後續步驟
[Power BI 中的視覺效果](power-bi-report-visualizations.md)  
[Power BI 中的自訂視覺效果](power-bi-custom-visuals.md)  
[將自訂視覺效果發佈至 Office 市集](developer/office-store.md)  
[開始使用自訂視覺效果開發人員工具](service-custom-visuals-getting-started-with-developer-tools.md)  
[如何認證自訂視覺效果](power-bi-custom-visuals-certified.md)    
[影片：和 Sachin Patney 及 Nico Cristache 一起建立 Power BI 的自訂視覺效果](https://www.youtube.com/watch?v=kULc2VbwjCc)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

