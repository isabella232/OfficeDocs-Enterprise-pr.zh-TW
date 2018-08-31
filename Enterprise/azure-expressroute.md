---
title: Azure ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: 了解如何搭配 Office 365 使用 Azure ExpressRoute 以及如何規劃各自需要如果您要部署 Azure ExpressRoute 與 Office 365 搭配使用的網路實作專案。
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22539966"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute for Office 365

了解如何搭配 Office 365 使用 Azure ExpressRoute 以及如何規劃各自需要如果您要部署 Azure ExpressRoute 與 Office 365 搭配使用的網路實作專案。執行 Azure 中的基礎結構和平台服務通常會受益所定址網路架構與效能考量。建議 Azure 的 ExpressRoute 在下列情況下。為 Office 365 和 Dynamics 365 建置透過網際網路存取安全地且可靠像是服務方案的軟體。據以，僅建議 ExpressRoute 這些特定案例中的應用程式。您可以閱讀關於網際網路效能及安全性及可以考慮 Azure ExpressRoute for Office 365 中的文章[與 Office 365 的網路連線](network-connectivity.md)。

> [!NOTE]
> 啟動 2017 年 7 月 31，您可以直接從 Azure 系統管理主控台，或使用 PowerShell 啟用 Microsoft Peering。啟用 Microsoft Peering、 之後您可以建立接收特定 BGP 路由廣告路由篩選器。您需要建立篩選器的 Office 365 的授權及可以隨時建立 Dynamics 365 客戶參與應用程式 （前身為 CRM Online） 篩選。會談到您的 Microsoft 帳戶小組取得授權來建立 Office 365 路由篩選程序。未經授權嘗試建立 Office 365 路由篩選的訂閱將收到[錯誤訊息](https://support.microsoft.com/kb/3181709)

您現在可以新增至 Office 365 的直接的網路連線所選的 Office 365 網路流量。Azure ExpressRoute 提供直接連線，可預測的效能，以及隨附的 Microsoft 網路元件的執行時間 SLA 99.95%以下。您仍會透過 Azure ExpressRoute 不受支援的服務需要網際網路連線。

## <a name="planning-azure-expressroute-for-office-365"></a>規劃 Office 365 Azure ExpressRoute

除了網際網路連線，您可以選擇透過直接連線提供可預測性和 Microsoft 網路元件 99.95%執行時間 SLA 路由其 Office 365 網路流量的子集。Azure ExpressRoute 提供此專用的網路連線至 Office 365 與其他 Microsoft 雲端服務。

不論是否有現有 MPLS WAN，ExpressRoute 可以新增至其中一個三種方式，將網路架構透過支援的雲端 exchange 代管提供者、 乙太網路點對點連線的提供者，或透過 MPLS 連線提供者。請參閱何種[提供者可用在您的區域](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。直接 ExpressRoute 連線會啟用中所述的應用程式的連線[什麼 Office 365 服務都包含在內？](azure-expressroute.md#BKMK_WhatDoIGet)下方。所有其他應用程式及服務的網路流量會繼續周遊網際網路。

請考慮下列高的層級網狀圖顯示典型的 Office 365 客戶透過網際網路存取 Office 365、 Windows Update 及 TechNet 等的所有 Microsoft 應用程式的連線到 Microsoft 資料中心。客戶使用類似的網路路徑不論他們正在連線從內部網路或從獨立的網際網路連線。

![Office 365 網路連線](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

現在查看更新圖表說明 Office 365 客戶使用的網際網路和 ExpressRoute 連線到 Office 365 的。注意到一些連線等公用 DNS 和內容傳遞網路節點仍需要公用網際網路連線。也請注意並非位於透過網際網路連線連接的建置其 ExpressRoute 客戶的使用者。

![Office 365 ExpressRoute 連線](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

仍然需要更多資訊吗？了解如何[管理您的網路流量與 Office 365 的 Azure ExpressRoute](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)並了解如何[設定 Office 365 的 Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。我們也已記錄 10 的組件[的 Office 365 訓練 Azure ExpressRoute](https://channel9.msdn.com/series/aer)數列 Channel 9 以協助先徹底更多說明的概念。

([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>哪些 Office 365 服務都包含在內？
<a name="BKMK_WhatDoIGet"> </a>

下表列出了 over ExpressRoute 所支援的 Office 365 服務。請檢閱[Office 365 端點文章](https://aka.ms/o365endpoints)了解這些應用程式的網路要求需要網際網路連線能力。

|**包含的應用程式**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> 探索<sup>1</sup> <br/> |
|Skype 商務線上<sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive for Business<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|入口網站和共用的<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD 連線<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup>每個這些應用程式不支援 ExpressRoute 透過網際網路連線需求，請參閱[Office 365 端點文章](https://aka.ms/o365endpoints)如需詳細資訊。

不含 ExpressRoute for Office 365 服務是 Office 365 ProPlus 的用戶端下載、 內部身分識別提供者登入、 和以中國 (由 21 Vianet 21vianet) 的 Office 365 服務。

([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>實作 ExpressRoute for Office 365

實作 ExpressRoute 需要涉及之網路和應用程式擁有者及需要小心規劃來決定新的[網路路由架構](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、 將安全性的頻寬需求的實作、 高可用性等等。若要實作 ExpressRoute，您需要：

1. 完全了解 ExpressRoute 找出符合 Office 365 連線規劃中的需求。了解哪些應用程式將使用的網際網路或 ExpressRoute 及完全規劃您的網路容量、 安全性及高可用性需求的 Office 365 使用的網際網路和 ExpressRoute 內容中的流量。

2. 決定輸出和網際網路和 ExpressRoute 流量<sup>1</sup>對等的位置。

3. 決定所需之網際網路與 ExpressRoute 連線的容量。

4. 有的計劃中的位置實作安全性及其他標準周邊控制項<sup>1</sup>。

5. 具有有效的 Microsoft Azure 帳戶 ExpressRoute 訂閱。

6. 選取 [連線模型及[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。請記住、 客戶可以選取多個連線模型或協力廠商和協力廠商不需要與您現有的網路提供者一樣。

7. 驗證前將 ExpressRoute 流量導向的部署。

8. （選用） [[實作 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)並評估區域的擴充。

<sup>1</sup>重要的效能考量。以下決策可能大幅提高會影響這十分重要的商務 Skype 等應用程式的延遲。

其他參考使用我們[路由指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)除了[ExpressRoute 文件](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)。

若要購買 Office 365 ExpressRoute，您需要使用一或多個[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)佈建的所需的數目與大小電路搭配 ExpressRoute 進階版訂閱。沒有任何額外的授權購買來自 Office 365。

以下是您可以使用回來的簡短連結：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

備妥可註冊的[Office 365 ExpressRoute](https://aka.ms/ert)吗？

([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>相關主題
<a name="BKMK_End"> </a>

[對 Office 365 的網路連線](network-connectivity.md)

[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)

[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)

[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)

[實作 ExpressRoute for Office 365](implementing-expressroute.md)

[使用 Office 365 案例 （預覽） ExpressRoute BGP 社群 （英文）](bgp-communities-in-expressroute.md)

[媒體品質和 Skype 的線上商務的網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)

[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)

[Office 365 URL 與 IP 位址範圍](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Office 365 網路和效能調整](network-planning-and-performance.md)
