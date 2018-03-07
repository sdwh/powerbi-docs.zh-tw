---
title: "停用隱私權設定"
description: "如何在個人閘道器中啟用「快速合併」，以停用重新整理的隱私權設定。"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 54d5f5ec2db890de0fbcef5ef0633548b90a6079
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2018
---
# <a name="disable-privacy-setting-in-power-bi-gateway---personal"></a>停用在 Power BI 閘道器的隱私權設定─個人
> [!NOTE]
> Power BI 有一個新版本的 Personal Gateway，稱為**內部部署資料閘道 (個人模式)**。 下列文章描述舊版的個人閘道，稱為 **Power BI Gateway - Personal**，將於 2017 年 7 月 31 日之後淘汰並停止運作。 如需新版個人閘道的相關資訊，包括如何安裝新版本，請參閱[**內部部署資料閘道 (個人模式)** 文章](service-gateway-personal-mode.md)。 新版本的個人閘道中也有快速合併功能，該文章中也會描述此功能。
> 
> 

取決於搭配個人閘道使用之資料來源的隱私權設定，您可能會收到下列錯誤。

> *處理資料集中的資料時發生錯誤。*
> 
> *[無法合併資料] &lt;查詢部分&gt;/&lt;…&gt;/&lt;…&gt;存取的資料來源擁有無法一併使用的隱私權等級。請重建這個資料組合。*
> 
> 

若要解決此錯誤，您可以開啟 **快速合併**。 **快速合併** 將會忽略允許合併不同資料來源的隱私權設定。

> [!NOTE]
> 合併資料時，不會考慮隱私權等級。 合併資料時，無法公開敏感或機密資料到其他資料來源。
> 
> 

## <a name="what-is-fast-combine"></a>什麼是快速合併？
如需深入了解隱私權等級和「快速合併」，您可以查看[隱私權等級](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)。 根據預設，隱私權層級會設定為私用，因而造成上述錯誤。 這是因為私用的設定會隔離其他來源的資料來源。 一種會導致問題的範例是，會另一個資料來源取得輸入的參數型查詢。

開啟「快速合併」會忽略私用設定，並允許執行。

## <a name="turn-on-fast-combine"></a>開啟「快速合併」
您可以使用下列步驟啟用「快速合併」您的個人閘道。 內部部署資料閘道沒有這項設定。

1. 開啟 **ConnectorConfig.xml**。  這可能位於您電腦上的兩個位置。  如果您是電腦的系統管理員，它會位於如下位置。
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    如果您不是系統管理員，其位置如下。
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
    
2. 將值為 True 的 **&lt;EnableFastCombine&gt;**項目加入組態檔中。 加入這個項目將會開啟 [快速合併]  。
   
   <pre><code>&lt;EnableFastCombine&gt;true&lt;/EnableFastCombine&gt;</code></pre>
   
   ![](media/refresh-enable-fast-combine/configfile.png)
3. 結束並重新啟動閘道器組態畫面。
4. 您會看到狀態，告訴您已啟用「快速合併」。
   
   ![](media/refresh-enable-fast-combine/fastcombineenabled.png)

## <a name="turn-off-fast-combine"></a>關閉「快速合併」
1. 開啟 **ConnectorConfig.xml**。  這可能位於您電腦上的兩個位置。  如果您是電腦的系統管理員，它會位於如下位置。
   
    <pre><code>C:\Program Files\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>
   
    如果您不是系統管理員，其位置如下。
   
    <pre><code>C:\Users\[username]\AppData\Local\Power BI Personal Gateway\1.0\Configurator\Connector</code></pre>

2. 從組態檔中移除 **&lt;EnableFastCombine&gt;** 項目。 移除這個項目將會關閉 **快速合併** 。
3. 結束並重新啟動閘道器組態畫面。
4. 您不會再看到狀態，通知您 **快速合併** 已啟用。

## <a name="next-steps"></a>後續步驟
[內部部署資料閘道 (個人模式) - 新版本的個人閘道](service-gateway-personal-mode.md)
[隱私權等級](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)  
[Power BI Desktop 中的常見查詢工作](desktop-common-query-tasks.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)

