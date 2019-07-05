---
title: 更新、刪除及擷取 Power BI 範本應用程式
description: 如何更新、刪除及擷取範本應用程式。
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 273734493c761739f9780e6a7fe6e781900723f9
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "67125870"
---
# <a name="update-delete-and-extract-template-app"></a>更新、刪除及擷取範本應用程式

既然您的應用程式已經進入生產階段，您可以在測試階段內重新開始，而不中斷生產階段內的應用程式。
## <a name="update-your-app"></a>更新應用程式


1. 在 [發行管理]  窗格中，選取 [建立應用程式]  。
2. 返回再執行應用程式建立程序。
3. 在您設定好 **Branding**、**Content**、**Control** 及 **Access** 後，再次選取 [建立應用程式]  。
4. 選取 [關閉]  並回到 [發行管理]  。

   您會看到您現在有兩個版本：生產階段中的版本，加上測試階段中的新版本。

    ![範本應用程式的兩個版本](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. 當您準備好要將應用程式升階至生產階段前，以進一步於租用戶外部測試時，請返回 [發行管理] 窗格，並選取 [測試]  旁邊的 [升階應用程式]  。
6. 您的連結現已正式運作。 請遵循 [Power BI 應用程式供應項目更新](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer)的步驟，將其再次提交至 Cloud Partner 入口網站 (CPP)。
7. 您必須在 CPP 中再次 [發佈]  供應項目，以及再次驗證它。

>[!NOTE]
>請僅在 Cloud Partner 入口網站核准您的應用程式，且您已將其發佈之後，再將應用程式升階至生產階段。

## <a name="extract-workspace"></a>擷取工作區
有了擷取功能，現在要回復到舊版範本應用程式比以往更為容易。 下列步驟將會從各種不同的發行階段，擷取特定應用程式版本到新的工作區：

1. 在 [發行管理] 窗格中，按 [(...)]  (更多)，然後按 [擷取]  。

    ![擷取範本應用程式版本](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![擷取範本應用程式版本](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. 在對話方塊中，輸入所擷取工作區的名稱。 將會新增新的工作區。

新的工作區版本設定會重設，您可以繼續從新擷取的工作區開發和散發範本應用程式。

## <a name="delete-template-app-version"></a>刪除範本應用程式版本
範本應用程式工作區是使用中分散式範本應用程式的來源。 為了保護範本應用程式使用者，若未先移除工作區中建立的所有應用程式版本，便無法刪除工作區。
刪除應用程式版本時，也會刪除無法再運作的應用程式 URL。

1. 在 [發行管理] 窗格中，按下選取省略符號 [(...)]  ，然後按 [刪除]  。
 ![刪除範本應用程式版本](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
 ![刪除範本應用程式版本](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>請勿刪除客戶或 **AppSource** 正在使用的應用程式版本，否則它們將無法再運作。

## <a name="next-steps"></a>後續步驟

請參閱[在您的組織中安裝、自訂及散發範本應用程式](service-template-apps-install-distribute.md)，了解客戶如何與範本應用程式互動。

如需散發應用程式的詳細資料，請參閱 [Power BI 應用程式供應項目](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer)。
