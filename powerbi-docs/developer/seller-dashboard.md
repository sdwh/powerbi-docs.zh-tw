---
title: 使用賣方儀表板將 Power BI 視覺效果提交至 AppSource
description: 使用賣方儀表板將 Power BI 視覺效果提交至 AppSource
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "75223676"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>使用賣方儀表板將 Power BI 視覺效果提交至 AppSource

您必須先將附有 **pbiviz** 檔案與 **pbix** 檔案的電子郵件傳送至 Power BI 小組，然後再提交至 AppSource。 這樣可讓 Power BI 小組將這些檔案上傳到公用的共用伺服器。 否則，市集就無法擷取檔案。 您必須傳送包含新的 Power BI 視覺效果提交、對現有 Power BI 視覺效果的更新，以及對已拒絕提交所做之修正的檔案。

>[!NOTE]
>[賣方儀表板](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) \(英文\) 即將淘汰。它會由[合作夥伴中心](https://docs.microsoft.com/partner-center/)取代。 只有在先前的 Power BI 視覺效果提交進行到一半的情況下，才應該使用賣方儀表板。 如果您要將新的 Power BI 視覺效果提交至 AppSource，請使用[合作夥伴中心方法](office-store.md#submitting-to-appsource)。

### <a name="seller-dashboard-submission-process"></a>賣方儀表板提交程序

您必須擁有有效的 Office 開發人員帳戶，才能登入 [Office 開發人員中心](https://dev.office.com/)。 Office 開發人員帳戶必須是 Microsoft 帳戶 Live ID，例如 hotmail.com 或 outlook.com。

1. 瀏覽至[開發人員中心](https://sellerdashboard.microsoft.com/Application/Summary)。

2. 選取 [新增應用程式]  。

    ![新增應用程式](media/office-store/powerbi-custom-visual-add-an-app.png)

3. 選取 [Power BI 自訂視覺效果]  然後選取 [下一步]  。

4. 選取 [應用程式套件]  下的 **+** ，然後在開啟的檔案對話方塊中選取從 Power BI 小組收到的應用程式套件 XML 檔案。

    ![應用程式套件](media/office-store/powerbi-custom-visual-apppackage.png)

5. 您應該會收到這是有效 Power BI 應用程式套件的核准。

    ![資訊清單已核准](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. 填寫 [一般資訊]  詳細資料。

   * *提交標題：* 您的提交在開發人員中心的命名方式。
   * *版本：* 版本號碼是從您的增益集應用程式套件自動填入。
   * *發行日期 (UTC)：* 選取應用程式在市集發行的日期。 如果選擇未來的日期，則市集要到該日期才會提供應用程式。
   * *類別：* 第一個類別會自動填入 "Data Visualization + BI"。 這就是所有 Power BI 視覺效果的標記方式。 為了幫助使用者方便搜尋您的視覺效果，您最多可以提供兩個額外的類別。
   * 「測試備註」：  選擇性，如果您想要為 Microsoft 軟體測試人員提供一些指示。
   * 「我的應用程式需要、支援、包含或使用密碼或加密」：  保持取消核取
   * 「將此增益集放在 iPad 上的 Office 增益集目錄中」：  保持取消核取
7. 選取**應用程式標誌** 下的 **+** ，上傳您的視覺效果標誌。 然後在開啟的檔案對話方塊中選取圖示檔。 檔案必須是 .png、.jpg、.jpeg 或 .gif。 它必須剛好是 300px (寬度) x 300px (高度)，大小不能大於 512 KB。

    ![應用程式標誌](media/office-store/powerbi-custom-visual-app-logo.png)

8. 填寫 [支援文件]  詳細資料。

   * 支援文件連結
   * 隱私權文件連結
   * 影片連結
   * 使用者授權合約 (EULA)

       您必須上傳 EULA 檔案。 您可以使用自己的 EULA，或使用 Office 市集內適用於 Power BI 視覺效果的預設 EULA。 若要使用預設的 EULA，請將下列 URL 貼至賣方儀表板的 [使用者授權合約] 檔案上傳對話方塊中︰[https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf) \(英文\)。

9. 選取 [下一步]  前往 [詳細資料]  頁面。

10. 選取 [語言]  並從清單中挑選語言。

    ![語言](media/office-store/powerbi-custom-visual-language.png)

11. 填寫 [描述] 詳細資料。

    * *應用程式名稱 (用於此語言)：* 輸入店面中應該出現的應用程式標題。
    * *簡短描述：* 輸入店面中應該出現的應用程式簡短描述，最多 100 個字元。 此描述會和標誌一起出現在最上層頁面。 您可以使用 pbiviz 套件的描述。
    * *完整描述：* 提供更詳細的應用程式描述，客戶將會在應用程式詳細資料頁面看到此完整描述。 如果您想讓視覺效果成為開放原始碼，讓社群加以改進，請在這裡提供公用存放庫 (如 GitHub) 的連結。

12. 至少上傳一張螢幕擷取畫面。 格式可以是 .png、.jpg、.jpeg 或 .gif。 它必須剛好是 1366 px (寬度) x 768 px (高度)。 檔案大小不能大於 1024 KB。 「為提高使用率，請新增文字泡泡以表達每張螢幕擷取畫面所顯示重要功能的價值定位。」 

12. 如果您想要新增更多語言，請選取 [新增語言]  並重複步驟 10 和 11。 新增更多語言有利於使用者使用自己的語言檢視自訂的視覺效果詳細資料。 未列出的語言會預設為第一個選取的語言。

13. 當您完成新增語言時，請選取 [下一步]  前往 [封鎖存取]  頁面。

14. 如果您想要防止特定國家或地區的客戶使用或購買您的應用程式，請核取此方塊並從清單中選取。

15. 選取 [下一步]  前往 [定價]  頁面。

16. 目前只有「免費」  的視覺效果支援，而且不允許在視覺效果中購買其他項目 (應用程式內購買)。 選取 [此應用程式免費]  。

    > [!NOTE]
    > 如果您選取除了「免費」以外的選項或在應用程式內購買已提交的視覺效果內容，此提交將會遭到拒絕。

17. 您現在可以選取 [儲存為草稿]  於稍後提交，或選取 [提交送審]  向 Office 市集提交自訂的視覺效果。

## <a name="seller-dashboard-certification-submission-process"></a>賣方儀表板認證提交程序

依照此節中的指示來在賣方儀表板中提交 Power BI 視覺效果以進行認證。 如果您先前已使用賣方儀表板將 Power BI 視覺效果提交至 AppSource，請使用此方法。

1. 將電子郵件傳送至 Power BI 視覺效果支援小組 (pbicvsupport@microsoft.com)。 於電子郵件中包括下列資訊︰
    * 標題：視覺效果認證要求
    * 連結人類可讀取原始程式碼裝載所在的 GitHub 存放庫
    * [遵守需求](power-bi-custom-visuals-certified.md#certification-requirements)
    * 通過程式碼檢閱

2. Microsoft 的 Power BI 視覺效果小組會在下列時機通知您：Power BI 視覺效果已通過認證並新增至[經認證的 Power BI 視覺效果](power-bi-custom-visuals-certified.md#certified-power-bi-visuals)清單，或是被拒絕 (並檢附須修正問題的報表)。 開發人員必須負責維護與 Microsoft 之間暢通的通訊，並在必要時更新其經認證的視覺效果。

## <a name="tracking-submission-status-and-usage"></a>追蹤提交狀態和使用方式

您可以檢閱[驗證原則](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals)。

提交之後，您就能夠在[應用程式儀表板](https://sellerdashboard.microsoft.com/Application/Summary/)中檢視提交狀態。

## <a name="certify-your-visual"></a>認證您的視覺效果

建立視覺效果之後，如果需要，可以為您的視覺效果[取得認證](../developer/power-bi-custom-visuals-certified.md)。

## <a name="next-steps"></a>後續步驟

[Developing a Power BI custom visual](visuals/custom-visual-develop-tutorial.md) (開發 Power BI 自訂視覺效果)  
[Power BI 中的視覺效果](../visuals/power-bi-report-visualizations.md)  
[Power BI 中的自訂視覺效果](../developer/power-bi-custom-visuals.md)  
[取得 Power BI 視覺效果認證](../developer/power-bi-custom-visuals-certified.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
