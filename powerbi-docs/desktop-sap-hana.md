---
title: 在 Power BI Desktop 中使用 SAP HANA
description: 在 Power BI Desktop 中使用 SAP HANA
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1932848cb2f8ad7d75e841870265cc22308467c2
ms.sourcegitcommit: a00fe5fb545c3df13b7cd13a701fd6a2b2521a17
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70200850"
---
# <a name="use-sap-hana-in-power-bi-desktop"></a>在 Power BI Desktop 中使用 SAP HANA
使用 Power BI Desktop，您現在可以存取 **SAP HANA** 資料庫。 若要使用 **SAP HANA**，SAP HANA ODBC 驅動程式必須安裝在本機用戶端電腦，以便 Power BI Desktop **SAP HANA** 資料連接正常運作。 您可以從 [SAP Software Download Center](https://support.sap.com/swdc) (SAP 軟體下載中心) 下載 SAP HANA ODBC 驅動程式. 從該處搜尋適用於 Windows 電腦的 SAP HANA CLIENT。 由於 **SAP Software Download Center** (SAP 軟體下載中心) 經常變更其結構，因此未提供瀏覽該網站的更具體指引。

若要連接到 **SAP HANA** 資料庫，請選取 [取得資料] > [資料庫] > [SAP HANA 資料庫]  ，如下圖所示：

![](media/desktop-sap-hana/sap-hana-1.png)

在連接到 SAP HANA 資料庫時，指定伺服器名稱。 然後從下拉式輸入方塊中，指定連接埠。

在此版本中，Power BI Desktop 和 Power BI 服務支援 [DirectQuery](desktop-directquery-sap-hana.md) 模式中的 **SAP HANA**，而且您可以在 DirectQuery 模式中，將使用 **SAP HANA** 的報表發佈或上傳至 Power BI 服務。 如果不在 DirectQuery 模式中使用 **SAP HANA** ，您可以發佈和上傳報表至 Power BI Service。

## <a name="supported-features-for-sap-hana"></a>SAP HANA 的支援功能
這個版本包含許多 **SAP HANA**功能，如下列清單所示：

* 適用於 **SAP HANA** 的 Power BI 連接器使用 SAP ODBC 驅動程式來提供最佳使用者體驗
* **SAP HANA** 同時支援 [DirectQuery] 和 [匯入] 選項
* Power BI 支援 HANA 資訊模型 (例如分析和計算檢視)，且已最佳化瀏覽
* 透過 **SAP HANA**，您也可以使用直接 SQL 功能連接到資料列和資料行資料表
* 包含 HANA 模型的最佳化瀏覽
* Power BI 支援 **SAP HANA** 變數和輸入參數
* 以 HDI 容器為基礎的計算檢視
  * 以 HDI 容器為基礎的計算檢視支援已於 2019 年 8 月所發行 Power BI Desktop 中公開預覽。 若要存取 Power BI 中以 HDI 容器為基礎的計算檢視，請確定您要與 Power BI 搭配使用的 HANA 資料庫使用者具有權限，可存取儲存您所要存取檢視的 HDI 執行階段容器。 若要授與此存取權，您必須建立允許存取 HDI 容器的角色，並將該角色指派給您要與 Power BI 搭配使用的 HANA 資料庫使用者 (依照慣例，此使用者也必須具有從 \_SYS\_BI 結構描述中系統資料表讀取的權限)。 如需如何建立和指派資料庫角色的詳細指示，請參閱官方 SAP 文件。 [此 SAP 部落格文章](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fblogs.sap.com%2F2018%2F01%2F24%2Fthe-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user%2F&data=02%7C01%7Cv-adbold%40microsoft.com%7Cf7e0a405fe334598ba0608d7096ef5b4%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636988244476739316&sdata=PuRu61GPRYp34mLuGbQk6gdbRikdgbxfqo8q1RBQtm0%3D&reserved=0)可能是不錯的起點。
  * 請注意，將 HANA 變數附加至以 HDI 為基礎的計算檢視時，目前有一些限制。 這些限制是由於 HANA 端的錯誤所造成，並將在 SAP HANA 的未來版本中解決。 首先，您無法將 HANA 變數套用至以 HDI 容器為基礎計算檢視的共用資料行。 升級至 HANA 2 37.02 版和更新版本或 HANA 2 42 版和更新版本，即可修正這項限制。 其次，變數和參數的多重輸入預設值目前不會在 Power BI UI 中顯示。 這也是由於 SAP HANA 中的錯誤所造成；SAP 尚未宣告修正。

## <a name="limitations-of-sap-hana"></a>SAP HANA 的限制
使用 **SAP HANA**也會有一些限制，如下所示：

* NVARCHAR 字串會截斷成 4000 個 Unicode 字元的最大長度
* 不支援 SMALLDECIMAL
* 不支援 VARBINARY
* 有效日期介於 1899/12/30 到 9999/12/31 之間。


## <a name="next-steps"></a>後續步驟
如需 DirectQuery 和 SAP HANA 的詳細資訊，請參閱下列資源：

* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](desktop-directquery-data-sources.md)
* [啟用 SAP HANA 的加密](desktop-sap-hana-encryption.md)


