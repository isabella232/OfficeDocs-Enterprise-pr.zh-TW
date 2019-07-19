---
title: Azure ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
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
description: 了解 Azure ExpressRoute 搭配 Office 365 的方式，以及如何規劃將會需要，如果您要為搭配 Office 365 部署 Azure ExpressRoute 的網路實作專案。
ms.openlocfilehash: d881dc4e65ca2533f511c7f613c38569811b95a7
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782353"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute for Office 365

了解 Azure ExpressRoute 搭配 Office 365 的方式，以及如何規劃將會需要，如果您要為搭配 Office 365 部署 Azure ExpressRoute 的網路實作專案。 在 Azure 中執行的基礎結構和平台服務通常會受益所定址網路架構與效能考量。 建議 Azure 的 ExpressRoute 在這些情況下。 軟體即 like 已透過網際網路存取安全且可靠地建置 Office 365 和 Dynamics 365 服務方案。 您可以閱讀有關網際網路效能與安全性，以及時，您可能會列入考量 Azure ExpressRoute for Office 365 文章[評估 Office 365 網路連線](assessing-network-connectivity.md)。

> [!NOTE]
> Microsoft 授權，才能使用 ExpressRoute for Office 365。 Microsoft 檢閱每個客戶要求，以及客戶的法規需求所要求的直接連線時，授權 ExpressRoute for Office 365 流量。 如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。 未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。

您現在可以新增至 Office 365 的直接的網路連線的所選的 Office 365 網路流量。 Azure ExpressRoute 可提供直接連線，可預測的效能，和隨附的 Microsoft 網路元件的執行時間 SLA 99.95%。 您仍將需要網際網路連線不支援透過 Azure ExpressRoute 的服務。

## <a name="planning-azure-expressroute-for-office-365"></a>規劃 Azure ExpressRoute for Office 365

除了網際網路連線能力，您可以選擇透過提供可預測性和 Microsoft 網路元件 99.95%執行時間 SLA 直接連線路由其 Office 365 的網路流量的子集。 Azure ExpressRoute 為您提供此專用的網路連線至 Office 365 和其他 Microsoft 雲端服務。

無論您是否已現有 MPLS WAN，ExpressRoute 可新增至您的網路架構中有三種;透過支援的雲端 exchange 代管提供者，乙太網路點對點連線提供者，或是 MPLS 連線提供者。 請參閱[提供者會在您的地區中使用](https://azure.microsoft.com/documentation/articles/expressroute-locations/)何種。 直接 ExpressRoute 連線會啟用連線中所述的應用程式[哪些 Office 365 服務都包含在內？](azure-expressroute.md#BKMK_WhatDoIGet)下方。 所有其他應用程式和服務的網路流量會繼續周遊網際網路。

請考慮下列高等級的網路圖表顯示典型的 Office 365 客戶，透過網際網路存取 Office 365、 Windows Update] 等 TechNet 的所有 Microsoft 應用程式的連線至 Microsoft 資料中心。 客戶使用類似的網路路徑，不論他們正在連線從內部網路或從獨立的網際網路連線。

![Office 365 網路連線能力](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

現在請查看更新的圖表以說明 Office 365 客戶使用的網際網路和 ExpressRoute 連線到 Office 365 的人員。 請注意一些連線，例如公用 DNS 和內容傳遞網路節點仍需要公用的網際網路連線。 也請注意並非位於其 ExpressRoute 連線的建置透過網際網路連線的客戶的使用者。

![使用 ExpressRoute 的 office 365 連線能力](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

仍需要更多資訊？ 了解如何[管理您的網路流量使用 Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)並了解如何[設定 Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。 我們也已記錄以協助說明的概念更徹底 Channel 9 10 部分的[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)系列。

## <a name="what-office-365-services-are-included"></a>包含哪些 Office 365 服務？
<a name="BKMK_WhatDoIGet"> </a>

下表列出透過 ExpressRoute 支援的 Office 365 服務。 請檢閱[Office 365 端點文章](https://aka.ms/o365endpoints)以了解這些應用程式的網路要求需要網際網路連線能力。

|**包含的應用程式**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|Skype 商務 Online<sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive for Business<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|入口網站及共用的<sup>1</sup> <br/> Azure Active Directory<sup>1</sup> <br/> AAD 連線<sup>1</sup> <br/> Office<sup>1</sup> <br/> |

<sup>1</sup>每個這些應用程式不支援透過 ExpressRoute 的網際網路連線能力需求，請參閱[Office 365 端點文章](https://aka.ms/o365endpoints)如需詳細資訊。

不包含使用 ExpressRoute for Office 365 服務，而 Office 365 專業增強版的用戶端下載項目、 內部部署身分識別提供者登入]，在中國的 Office 365 (21vianet 21 Vianet) 服務。

## <a name="implementing-expressroute-for-office-365"></a>實作 ExpressRoute for Office 365

實作 ExpressRoute 需要網路和應用程式的擁有人的參與程度，而且需要仔細規劃至判斷新的[網路路由架構](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、 頻寬需求，將安全性的實作，高可用性等等。 若要實作 ExpressRoute，您將需要：

1. 完全了解 ExpressRoute 滿足您 Office 365 連線能力規劃中的需求。 了解哪些應用程式會使用 ExpressRoute 的網際網路和完全規劃您的網路容量、 安全性和高可用性需求在內容中使用的網際網路和 ExpressRoute for Office 365 的流量。

2. 判定輸出及網際網路和 ExpressRoute 流量<sup>1</sup>的對等位置。

3. 判斷在網際網路上及 ExpressRoute 連線所需的容量。

4. 有計劃中實作的安全性和其他標準周邊控制項<sup>1</sup>的地方。

5. 必須是有效的 Microsoft Azure 帳戶 ExpressRoute 訂閱。

6. 選取連線模型和[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。 請記住，客戶可以選取多個連線模型或協力廠商和協力廠商不一定要與您現有的網路提供者相同。

7. 驗證前將 ExpressRoute 流量導向的部署。

8. （選用） [ [qos](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)並評估地區擴充。

<sup>1</sup>重要的效能考量。 此處的決策可能大幅會影響這是重要的商務用 Skype 等應用程式的延遲。

針對其他參考資料，使用我們[路由指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)除了[ExpressRoute 文件](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)。

若要購買 ExpressRoute for Office 365，您需要使用一個或多個[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)佈建所需的數目與大小電路 ExpressRoute 進階版訂閱。 有從 Office 365 購買額外的授權。

您可以使用下列短連結返回這裡：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

備妥可註冊的[ExpressRoute for Office 365](https://aka.ms/ert)？

## <a name="related-topics"></a>相關主題

[評估 Office 365 網路連線](assessing-network-connectivity.md)

[管理 ExpressRoute for Office 365 連線](managing-expressroute-for-connectivity.md)

[使用 ExpressRoute for Office 365 進行路由傳送](routing-with-expressroute.md)

[使用 ExpressRoute for Office 365 進行網路規劃](network-planning-with-expressroute.md)

[實作 ExpressRoute for Office 365](implementing-expressroute.md)

[使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）](bgp-communities-in-expressroute.md)

[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)

[使用基準與效能歷程記錄進行 Office 365 效能調整](performance-tuning-using-baselines-and-history.md)

[Office 365 的效能疑難排解規劃](performance-troubleshooting-plan.md)

[Office 365 URL 與 IP 位址範圍](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) (英文)

[Office 365 網路與效能調整](network-planning-and-performance.md)
