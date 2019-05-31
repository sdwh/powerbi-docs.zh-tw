---
title: Power BI 是什麼？
description: Power BI 和說明的不同部分如何彼此搭配運作的概觀 Power BI Desktop、 Power BI 服務、 Power BI 行動裝置、 報表伺服器和 Power BI embedded。
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7236caba1c7a8eb07e93c6f2af7068141b8ac3a7
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413027"
---
# <a name="what-is-power-bi"></a>Power BI 是什麼？
**Power BI** 是軟體服務、應用程式和連接器的集合，它們搭配使用來將不相關的資料來源轉換成相關、視覺上融入的互動式深入剖析。 不論您的資料是簡單的 Excel 試算表，或是一組雲端和內部部署混合式資料倉儲， Power BI 可讓您輕鬆地連接到資料來源、 視覺化和了解重要的是，以及與任何人或您想要分享。

![顯示 Power BI 輸入來源的圖表](media/power-bi-overview/power-bi-input-new.png)

Power BI 可以是簡單和快速、 能夠從 Excel 試算表或本機資料庫建立快速深入剖析。 但 Power BI 也是穩定和企業等級，準備好進行廣泛模型化和即時分析，以及自訂開發。 它可以是您的個人報告和視覺效果工具，同時也是群組專案、 部門或整個公司的分析和決策引擎。

## <a name="the-parts-of-power-bi"></a>Power BI 的各部分
Power BI 所組成： 
- Windows 桌面應用程式呼叫**Power BI Desktop**
- 線上 SaaS (*軟體即服務*) 稱為服務**Power BI 服務** 
- Power BI**行動裝置應用程式**Windows、 iOS 和 Android 裝置

![Power BI Desktop、服務、行動裝置](media/power-bi-overview/power-bi-blocks.png)

這三個元素&mdash;Power BI Desktop、 服務和行動裝置應用程式&mdash;設計成讓人員建立、 共用和使用方式為，或其角色，提供最有效的商務深入解析。

第四個元素，**Power BI 報表伺服器**，可讓您在 Power BI Desktop 中建立 Power BI 報表之後，將它們發行至內部部署報表伺服器。 深入了解 [Power BI 報表伺服器](#on-premises-reporting-with-power-bi-report-server)。

## <a name="how-power-bi-matches-your-role"></a>Power BI 如何符合您的角色
Power BI 的使用方式可能取決於您在專案或小組中的角色。 其他人，在其他角色，可能會使用 Power BI 以不同的方式。

例如，您可能主要使用 **Power BI 服務**。 但是您的數字處理、業務報表建立同事可能會大量使用 **Power BI Desktop** 建立報表，並將 Desktop 報表發行到 Power BI 服務進行檢視。 另一個同事在銷售可能主要使用其**Power BI 手機應用程式**以監視其銷售配額進度，並向下鑽研到新的銷售潛在客戶詳細資料。

如果您是開發人員，便可以使用 Power BI API 將資料推送至資料集，或將儀表板和報表內嵌至您自己的自訂應用程式。 有新視覺效果的構想嗎？ 您可以自行建置並與其他人分享。  

您也可以使用 Power BI 的每個項目，在不同的時間，視您嘗試達成或您指定專案的角色而定。

Power BI 的使用方式取決於 Power BI 的哪些功能或服務是最適合您解決方案的工具。 比方說，您可以使用 Power BI Desktop 來建立您自己的小組有關客戶參與統計資料的報表，而您可以檢視庫存和製造進度，在 Power BI 服務中的即時儀表板。 您可以使用 Power BI 的每個部分，這就是它如此具有彈性且吸引人的原因。

探索與您角色相關的文件：
- 適用於[***設計師***](desktop-what-is-desktop.md)的 Power BI
- 適用於[***取用者***](consumer/end-user-consumer.md)的 Power BI
- 適用於[***開發人員***](developer/what-can-you-do.md)的 Power BI
- 適用於[***系統管理員***](service-admin-administering-power-bi-in-your-organization.md)的 Power BI

## <a name="the-flow-of-work-in-power-bi"></a>Power BI 中的工作流程
常見的 Power BI 中的工作流程一開始會連接到資料來源，及建置報表，Power BI Desktop 中。 然後發佈至 Power BI 服務，該報表從 Power BI Desktop，並共用它，因此在 Power BI 服務和行動裝置的終端使用者可以檢視及與報表互動。
此工作流程是常見的情況，並示範三個主要 Power BI 元素如何彼此互補。

以下是詳細的 [Power BI Desktop 與 Power BI 服務的比較](service-service-vs-desktop.md)。

但如果您尚未做好移至雲端的準備，而想要將報表保留在公司防火牆後方，該怎麼辦？  請繼續閱讀。

## <a name="on-premises-reporting-with-power-bi-report-server"></a>在內部部署報表與 Power BI 報表伺服器
建立、 部署及管理 Power BI 行動和分頁報表，在內部部署環境已準備好要使用的工具和 Power BI 報表伺服器提供服務的範圍。

![內部部署的圖表](media/power-bi-overview/power-bi-report-server2.png)

「Power BI 報表伺服器」是一項解決方案，您會將其部署在防火牆後方，然後以各種不同方式 (不論是在網頁瀏覽器中、行動裝置上還是以電子郵件形式檢視) 將報表傳遞給正確的使用者。 而由於「Power BI 報表伺服器」與雲端 Power BI 相容，因此您可以在準備就緒後就移至雲端。 

深入了解 [Power BI 報表伺服器](report-server/get-started.md)。

## <a name="next-steps"></a>後續步驟
- [快速入門：了解 Power BI 服務的使用方法](service-the-new-power-bi-experience.md)   
- [教學課程：開始使用 Power BI 服務](service-get-started.md)
- [快速入門：在 Power BI Desktop 中連線至資料](desktop-quickstart-connect-to-data.md)
