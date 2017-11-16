---
title: "在 Power BI Desktop 中為行動裝置應用程式標記條碼欄位"
description: "當您在 Power BI Desktop 中為模型的條碼欄位做標記時，您可以在 iPhone 上的 Power BI 應用程式中自動篩選條碼資料。"
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 07/18/2017
ms.author: maggies
ms.openlocfilehash: 029d93df808163ab5ff3015161121dafbbfa175d
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2017
---
# <a name="tag-barcodes-in-power-bi-desktop-for-the-mobile-apps"></a>在 Power BI Desktop 中為行動裝置應用程式標記條碼
在 Power BI Desktop 中，您可以在資料行內[分類資料](desktop-data-categorization.md)，使 Power BI Desktop 知道在報表中以何種視覺效果處理值。 您也可以將資料行分類為**條碼**。 當您或您的同事在 iPhone 上 [ 使用 Power BI 應用程式掃描產品上條碼](mobile-apps-scan-barcode-iphone.md)時，您會看到任何包含該條碼的報表。 當您在行動裝置應用程式中開啟報表時，Power BI 會自動篩選出報表中與條碼相關的資料。

1. 在 Power BI Desktop 內切換到資料檢視。
2. 選取具有條碼資料的資料行。 請參閱下方[支援的條碼格式](#supported-barcode-formats)清單。
3. 在 [模型] 索引標籤上，選取 [資料類別] > [條碼]。
   
    ![資料類別清單](media/desktop-mobile-barcodes/power-bi-desktop-barcode.png)
4. 在 [報表] 檢視中，將此欄位加入要由條碼篩選的視覺效果中。
5. 儲存報表，並將其發行至 Power BI 服務。

現在當您開啟 [Power BI for iPhone 應用程式](mobile-ios-ipad-iphone-apps.md)上的掃描器並掃描條碼時，您會在報表清單中看到這份報表。 當您開啟該報表時，將會按照您掃描的產品條碼篩選其視覺效果。

## <a name="supported-barcode-formats"></a>支援的條碼格式
如果您能在 Power BI 報表中為條碼加上標籤，則 Power BI 就能夠辨識下列的條碼︰ 

* UPCECode 
* Code39Code  
* A39Mod43Code 
* EAN13Code 
* EAN8Code  
* 93Code  
* 128Code 
* PDF417Code 
* Interleaved2of5Code 
* ITF14Code 

## <a name="next-steps"></a>後續步驟
* [在您的 iPhone 上從 Power BI 應用程式掃描條碼](mobile-apps-scan-barcode-iphone.md)
* [在 iPhone 上掃描條碼遇到的問題](mobile-apps-scan-barcode-iphone.md#issues-with-scanning-a-barcode)
* [Power BI Desktop 中的資料分類](desktop-data-categorization.md)  
* 有問題嗎？ [嘗試在 Power BI 社群提問](http://community.powerbi.com/)

