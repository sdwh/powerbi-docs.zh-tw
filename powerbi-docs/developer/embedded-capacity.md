---
title: Power BI embedded 分析中的容量和 SKU
description: 了解 Power BI 內嵌式分析中的容量和 SKU。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 1c6c4faa9f5cff46695ddd9d30869103d7bf482b
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427197"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Power BI embedded 分析中的容量和 SKU

移至生產環境時，Power BI 內嵌式分析需要專用容量 (*A*、*EM* 或 *P* SKU) 來發佈內嵌 Power BI 內容。

容量是保留給特別用途的專用資源集。 可讓您將儀表板、報表和資料集發佈給使用者，而不必購買個別使用者授權。 也會為內容提供可靠且一致的效能。

>[!NOTE]
>您需要一個 Power BI Pro 帳戶來發佈。

## <a name="what-is-embedded-analytics"></a>什麼是內嵌式分析？

Power BI 內嵌式分析包含兩種解決方案：
* *Power BI Embedded* - Azure 供應項目
* 作為 *Power BI Premium* 的一部分來內嵌 Power BI - Office 供應項目

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded 適用於想要將視覺效果內嵌到應用程式的 ISV 和開發人員。

使用 Power BI Embedded 的應用程式，可讓使用者取用儲存於 Power BI Embedded 容量的內容。

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../service-premium-what-is.md) 專為企業打造，其單一檢視集結了組織、夥伴、客戶及供應商，適合想要完整 BI 解決方案的企業使用。

Power BI Premium 是 SaaS 產品，可讓使用者透過 Power BI 行動裝置應用程式、內部開發的應用程式或在 Power BI 入口網站 (Power BI 服務) 取用內容。 這可讓 Power BI Premium 同時為內部與外部客戶面向的應用程式提供解決方案。

## <a name="capacity-and-skus"></a>容量與 SKU

每個容量都提供一系列 SKU，而每個 SKU 都提供不同的記憶體和運算能力資源階層。 您需要的 SKU 類型，取決於所要部署的解決方案類型。

在決定要購買哪一種 SKU 前，請檢閱本節中的資訊。
* 若要了解每個階層支援哪些工作負載，請參閱[設定 Premium 容量中的工作負載](../service-admin-premium-workloads.md)一文
* 使用此連結來[規劃及測試容量](../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Power BI Embedded SKU

Power BI Embedded 隨附 *A* SKU。
* [了解 Power BI Embedded 容量可處理的項目](https://powerbi.microsoft.com/blog/power-bi-developer-community-june-july-update/#Capacity-Plan) (英文)
* [購買 *A* SKU](../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)

### <a name="power-bi-premium-skus"></a>Power BI Premium SKU

Power BI Premium 提供兩種 SKU：*P* 和 *EM*。
* [了解 *P* 和 *EM* SKU 之間的差異](../service-premium-what-is.md#subscriptions-and-licensing)
* [購買 Premium SKU](../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>我該使用哪種 SKU？

下表提供功能摘要、所需容量，以及每項功能所需的特定 SKU。 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>功能</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>取用了什麼？</em><p></td>
<td><p><em>正在取用什麼？</em><p></td>
<td style="text-align: center"><p><em>A SKU</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>EM SKU</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>P SKU</br>(Office)</em></p></td>
</tr>
<tr>
<td>從 Power BI 工作區內嵌成品</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Power BI 報表</td>
<td>您組織的內嵌應用程式</br>(使用者擁有資料)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>您客戶的內嵌應用程式</br>(應用程式擁有資料)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Power BI 內容<br>(免費 Power BI 授權)</td>
<td>Power BI 服務</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI 行動版</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>MS Office 應用程式</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>容量考量

下表列出每個容量的收費和使用方式考量。

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>供應項目</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center;">每小時</td>
<td style="text-align: center;">每月</td>
<td style="text-align: center;">每月</td>
</tr>
<tr>
<td><p><strong>履約承諾</strong></td>
<td style="text-align: center;">無</td>
<td style="text-align: center;">每年</td>
<td style="text-align: center;">每月或每年</td>
</tr>
<tr>
<td valign="top"><p><strong>使用量</strong></td>
<td style="text-align: center;">Azure 資源可以：</br>- <a href="azure-pbie-scale-capacity.md">相應增加或減少</a></br>- <a href="azure-pbie-pause-start.md">暫停和繼續</a>
</td>
<td style="text-align: center;">內嵌於應用程式和</br> Microsoft 應用程式</td>
<td style="text-align: center;">內嵌於應用程式和</br> Power BI 服務</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU 記憶體和運算能力

下表描述每個 SKU 的資源和限制。

| 容量節點 | V 核心總數 | 後端 V 核心 | RAM (GB) | 前端 V 核心 | DirectQuery/即時連線 (每秒) | 模型重新整理平行處理原則 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
>[對客戶進行內嵌](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[為組織內嵌](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [從應用程式內嵌](embed-from-apps.md)