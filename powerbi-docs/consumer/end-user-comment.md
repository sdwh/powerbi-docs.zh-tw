---
title: 將註解新增至儀表板和報表
description: 本文件說明如何將註解新增至儀表板、 報表或視覺效果，以及如何使用註解來與共同作業者進行對話。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 04/30/2019
ms.author: mihart
LocalizationGroup: Consumer
ms.openlocfilehash: a633095ba3139c056bf55989149cd9fd379710b9
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100888"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>將註解新增至儀表板或報表
新增個人註解或啟動與您的同事的儀表板或報表的相關交談。 **註解**功能只是「取用者」  可與其他人共同作業的其中一種方法。 

![註解影片](media/end-user-comment/comment.gif)

## <a name="how-to-use-the-comments-feature"></a>如何使用註解功能
可以加入註解，整個儀表板、 儀表板上的個別視覺效果、 報表頁面，及至報表頁面上的個別視覺效果。 將一般註解或註解目標為特定的同事。  

當您在報表中加入註解時，Power BI 會擷取目前的篩選和交叉分析篩選器值。 這表示當您選取，或回應意見時，報表頁面或報表視覺效果可能會改變，以顯示篩選和交叉分析篩選器選取項目處於作用中的第一個註解時加入。  

![與篩選 video 搭配運作的報表](media/end-user-comment/comment-reports-with-filters/comment-reports-with-filters.gif)

這為何重要？ 假設有位同事套用揭露有趣的深入解析，他想要與小組分享了篩選器。 不含該選取的篩選，註解可能沒有任何意義。 

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>將一般註解新增至儀表板或報表
將註解新增至儀表板或報表的處理程序很類似。 在此範例中，我們使用儀表板。 

1. 開啟 Power BI 儀表板或報表，然後選取**註解**圖示。 這會開啟 [註解] 對話方塊。

    ![註解圖示](media/end-user-comment/power-bi-comment-icon.png)

    在此我們會看到儀表板建立者已新增一般註解。  有權存取此儀表板的任何人都可以看到此註解。

    ![註解圖示](media/end-user-comment/power-bi-dash-comment.png)

2. 若要回應，請選取 [回覆]  ，鍵入您的回應，然後選取 [張貼]  。  

    ![註解回覆圖示](media/end-user-comment/power-bi-comment-reply.png)

    根據預設，Power BI 將引導您回應發起註解討論串的同事，在本例中為 Aaron F。 

    ![具有回應的註解](media/end-user-comment/power-bi-response.png)

 3. 如果您想要加入的註解不屬於現有的執行緒，輸入您的註解的上方的文字欄位中。

    ![註解回覆圖示](media/end-user-comment/power-bi-new-comment.png)

    此儀表板的註解現在看起來如下。

    ![註解的交談](media/end-user-comment/power-bi-comment-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>將註解新增至特定儀表板或報表視覺效果
除了整個儀表板或整份報表頁面，請新增註解，您可以加入註解，個別的儀表板磚和個別的報表視覺效果。 處理程序類似，而且在此範例中，我們會使用報表。

1. 將滑鼠暫留在視覺效果上並選取省略符號 (...)。    
2. 從下拉式清單中，選取 [新增註解]  。

    ![新增註解是第一個選項](media/end-user-comment/power-bi-comment-report.png)  

3.  **註解** 對話方塊隨即開啟，並在頁面上的其他視覺效果會呈現灰色。此視覺效果還沒有任何註解。 

    ![新增註解給自己](media/end-user-comment/power-bi-comment-bar.png)  

4. 鍵入您的註解，然後選取 [張貼]  。

    ![新增註解給自己](media/end-user-comment/power-bi-comment-june.png)  

    - 報表頁面上，選取 視覺效果，所做的註解會醒目提示該視覺效果 （請參閱前述）。

    - 在儀表板、 圖表圖示 ![具有圖表圖示的註解](media/end-user-comment/power-bi-comment-chart-icon.png) 可讓我們知道，繫結至特定的視覺效果的註解。 套用至整個儀表板的註解不需要特殊的圖示。 選取圖表圖示會反白顯示相關的視覺效果的儀表板上。

        ![醒目提示的相關視覺效果](media/end-user-comment/power-bi-comment-highlight2.png)

5. 按一下 [關閉]  返回儀表板或報表。

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>使用 @ 符號吸引同事注意
您建立的儀表板、 報表、 磚或視覺的註解，擷取您的同事注意使用 「\@"符號。  當您輸入"\@」 符號，Power BI 會開啟下拉式清單，您可以在其中搜尋並選取從您的組織的個人。 任何前面加上 "\@" 符號的已驗證名稱都會以藍色字型顯示。 

以下是我和視覺效果「設計師」  進行的交談。 他使用 @ 符號，確保我看到註解。 我知道這個註解是寫給我看的。 當我在 Power BI 中開啟這個應用程式儀表板時，從標頭選取 [註解]  。 [註解]  窗格會顯示我們的交談。

![新增註解提及](media/end-user-comment/power-bi-comment-convo.png)  



## <a name="next-steps"></a>後續步驟
回到[適用於取用者的視覺效果](end-user-visualizations.md)    
<!--[Select a visualization to open a report](end-user-open-report.md)-->
