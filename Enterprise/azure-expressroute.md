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
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="0a297-103">Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="0a297-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="0a297-p101">了解如何搭配 Office 365 使用 Azure ExpressRoute 以及如何規劃各自需要如果您要部署 Azure ExpressRoute 與 Office 365 搭配使用的網路實作專案。執行 Azure 中的基礎結構和平台服務通常會受益所定址網路架構與效能考量。建議 Azure 的 ExpressRoute 在下列情況下。為 Office 365 和 Dynamics 365 建置透過網際網路存取安全地且可靠像是服務方案的軟體。據以，僅建議 ExpressRoute 這些特定案例中的應用程式。您可以閱讀關於網際網路效能及安全性及可以考慮 Azure ExpressRoute for Office 365 中的文章[與 Office 365 的網路連線](network-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="0a297-p101">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365. Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations. We recommend ExpressRoute for Azure in these cases. Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet. Accordingly, we only recommend ExpressRoute for these applications in specific scenarios. You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Network connectivity to Office 365](network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0a297-p102">啟動 2017 年 7 月 31，您可以直接從 Azure 系統管理主控台，或使用 PowerShell 啟用 Microsoft Peering。啟用 Microsoft Peering、 之後您可以建立接收特定 BGP 路由廣告路由篩選器。您需要建立篩選器的 Office 365 的授權及可以隨時建立 Dynamics 365 客戶參與應用程式 （前身為 CRM Online） 篩選。會談到您的 Microsoft 帳戶小組取得授權來建立 Office 365 路由篩選程序。未經授權嘗試建立 Office 365 路由篩選的訂閱將收到[錯誤訊息](https://support.microsoft.com/kb/3181709)</span><span class="sxs-lookup"><span data-stu-id="0a297-p102">Starting July 31st, 2017, you can enable Microsoft Peering directly from the Azure Administrative console or using PowerShell. After enabling Microsoft Peering, you can create route filters to receive specific BGP route advertisements. You'll need authorization to create filters for Office 365 and can create Dynamics 365 Customer Engagement applications (formerly known as CRM Online) filters at any time. Talk to your Microsoft Account team about the process to obtain authorization to create Office 365 route filters. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709)</span></span>

<span data-ttu-id="0a297-p103">您現在可以新增至 Office 365 的直接的網路連線所選的 Office 365 網路流量。Azure ExpressRoute 提供直接連線，可預測的效能，以及隨附的 Microsoft 網路元件的執行時間 SLA 99.95%以下。您仍會透過 Azure ExpressRoute 不受支援的服務需要網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="0a297-p103">You can now add a direct network connection to Office 365 for selected Office 365 network traffic. Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components. You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="0a297-118">規劃 Office 365 Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="0a297-118">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="0a297-p104">除了網際網路連線，您可以選擇透過直接連線提供可預測性和 Microsoft 網路元件 99.95%執行時間 SLA 路由其 Office 365 網路流量的子集。Azure ExpressRoute 提供此專用的網路連線至 Office 365 與其他 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="0a297-p104">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components. Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="0a297-p105">不論是否有現有 MPLS WAN，ExpressRoute 可以新增至其中一個三種方式，將網路架構透過支援的雲端 exchange 代管提供者、 乙太網路點對點連線的提供者，或透過 MPLS 連線提供者。請參閱何種[提供者可用在您的區域](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。直接 ExpressRoute 連線會啟用中所述的應用程式的連線[什麼 Office 365 服務都包含在內？](azure-expressroute.md#BKMK_WhatDoIGet)下方。所有其他應用程式及服務的網路流量會繼續周遊網際網路。</span><span class="sxs-lookup"><span data-stu-id="0a297-p105">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider. See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/). The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below. Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="0a297-p106">請考慮下列高的層級網狀圖顯示典型的 Office 365 客戶透過網際網路存取 Office 365、 Windows Update 及 TechNet 等的所有 Microsoft 應用程式的連線到 Microsoft 資料中心。客戶使用類似的網路路徑不論他們正在連線從內部網路或從獨立的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="0a297-p106">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet. Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 網路連線](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="0a297-p107">現在查看更新圖表說明 Office 365 客戶使用的網際網路和 ExpressRoute 連線到 Office 365 的。注意到一些連線等公用 DNS 和內容傳遞網路節點仍需要公用網際網路連線。也請注意並非位於透過網際網路連線連接的建置其 ExpressRoute 客戶的使用者。</span><span class="sxs-lookup"><span data-stu-id="0a297-p107">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365. Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection. Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![Office 365 ExpressRoute 連線](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="0a297-p108">仍然需要更多資訊吗？了解如何[管理您的網路流量與 Office 365 的 Azure ExpressRoute](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)並了解如何[設定 Office 365 的 Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。我們也已記錄 10 的組件[的 Office 365 訓練 Azure ExpressRoute](https://channel9.msdn.com/series/aer)數列 Channel 9 以協助先徹底更多說明的概念。</span><span class="sxs-lookup"><span data-stu-id="0a297-p108">Still want more information? Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

<span data-ttu-id="0a297-135">([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="0a297-135">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="0a297-136">哪些 Office 365 服務都包含在內？</span><span class="sxs-lookup"><span data-stu-id="0a297-136">What Office 365 services are included?</span></span>
<span data-ttu-id="0a297-137"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="0a297-137"></span></span>

<span data-ttu-id="0a297-p109">下表列出了 over ExpressRoute 所支援的 Office 365 服務。請檢閱[Office 365 端點文章](https://aka.ms/o365endpoints)了解這些應用程式的網路要求需要網際網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="0a297-p109">The following table lists the Office 365 services that are supported over ExpressRoute. Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="0a297-140">**包含的應用程式**</span><span class="sxs-lookup"><span data-stu-id="0a297-140">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="0a297-141">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-141">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="0a297-142">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-142">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="0a297-143">探索<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-143">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="0a297-144">Skype 商務線上<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-144">Skype for Business Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="0a297-145">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-145">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="0a297-146">OneDrive for Business<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-146">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="0a297-147">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-147">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="0a297-148">入口網站和共用的<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-148">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="0a297-149">Azure Active Directory<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-149">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="0a297-150">AAD 連線<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-150">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="0a297-151">Office Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0a297-151">Office Online<sup>1</sup></span></span> <br/> |

<span data-ttu-id="0a297-152"><sup>1</sup>每個這些應用程式不支援 ExpressRoute 透過網際網路連線需求，請參閱[Office 365 端點文章](https://aka.ms/o365endpoints)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0a297-152"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="0a297-153">不含 ExpressRoute for Office 365 服務是 Office 365 ProPlus 的用戶端下載、 內部身分識別提供者登入、 和以中國 (由 21 Vianet 21vianet) 的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="0a297-153">The services that aren't included with ExpressRoute for Office 365 are Office 365 ProPlus client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

<span data-ttu-id="0a297-154">([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="0a297-154">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="0a297-155">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="0a297-155">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="0a297-p110">實作 ExpressRoute 需要涉及之網路和應用程式擁有者及需要小心規劃來決定新的[網路路由架構](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、 將安全性的頻寬需求的實作、 高可用性等等。若要實作 ExpressRoute，您需要：</span><span class="sxs-lookup"><span data-stu-id="0a297-p110">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on. To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="0a297-p111">完全了解 ExpressRoute 找出符合 Office 365 連線規劃中的需求。了解哪些應用程式將使用的網際網路或 ExpressRoute 及完全規劃您的網路容量、 安全性及高可用性需求的 Office 365 使用的網際網路和 ExpressRoute 內容中的流量。</span><span class="sxs-lookup"><span data-stu-id="0a297-p111">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning. Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="0a297-160">決定輸出和網際網路和 ExpressRoute 流量<sup>1</sup>對等的位置。</span><span class="sxs-lookup"><span data-stu-id="0a297-160">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="0a297-161">決定所需之網際網路與 ExpressRoute 連線的容量。</span><span class="sxs-lookup"><span data-stu-id="0a297-161">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="0a297-162">有的計劃中的位置實作安全性及其他標準周邊控制項<sup>1</sup>。</span><span class="sxs-lookup"><span data-stu-id="0a297-162">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="0a297-163">具有有效的 Microsoft Azure 帳戶 ExpressRoute 訂閱。</span><span class="sxs-lookup"><span data-stu-id="0a297-163">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="0a297-p112">選取 [連線模型及[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。請記住、 客戶可以選取多個連線模型或協力廠商和協力廠商不需要與您現有的網路提供者一樣。</span><span class="sxs-lookup"><span data-stu-id="0a297-p112">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="0a297-166">驗證前將 ExpressRoute 流量導向的部署。</span><span class="sxs-lookup"><span data-stu-id="0a297-166">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="0a297-167">（選用） [[實作 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)並評估區域的擴充。</span><span class="sxs-lookup"><span data-stu-id="0a297-167">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="0a297-p113"><sup>1</sup>重要的效能考量。以下決策可能大幅提高會影響這十分重要的商務 Skype 等應用程式的延遲。</span><span class="sxs-lookup"><span data-stu-id="0a297-p113"><sup>1</sup>Important performance considerations. Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="0a297-170">其他參考使用我們[路由指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)除了[ExpressRoute 文件](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)。</span><span class="sxs-lookup"><span data-stu-id="0a297-170">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="0a297-p114">若要購買 Office 365 ExpressRoute，您需要使用一或多個[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)佈建的所需的數目與大小電路搭配 ExpressRoute 進階版訂閱。沒有任何額外的授權購買來自 Office 365。</span><span class="sxs-lookup"><span data-stu-id="0a297-p114">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription. There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="0a297-173">以下是您可以使用回來的簡短連結：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="0a297-173">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="0a297-174">備妥可註冊的[Office 365 ExpressRoute](https://aka.ms/ert)吗？</span><span class="sxs-lookup"><span data-stu-id="0a297-174">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

<span data-ttu-id="0a297-175">([Office 365 的 azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="0a297-175">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="related-topics"></a><span data-ttu-id="0a297-176">相關主題</span><span class="sxs-lookup"><span data-stu-id="0a297-176">Related Topics</span></span>
<span data-ttu-id="0a297-177"><a name="BKMK_End"> </a></span><span class="sxs-lookup"><span data-stu-id="0a297-177"></span></span>

[<span data-ttu-id="0a297-178">對 Office 365 的網路連線</span><span class="sxs-lookup"><span data-stu-id="0a297-178">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="0a297-179">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="0a297-179">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="0a297-180">使用 ExpressRoute for Office 365 進行路由傳送</span><span class="sxs-lookup"><span data-stu-id="0a297-180">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="0a297-181">使用 ExpressRoute for Office 365 進行網路規劃</span><span class="sxs-lookup"><span data-stu-id="0a297-181">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="0a297-182">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="0a297-182">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="0a297-183">使用 Office 365 案例 （預覽） ExpressRoute BGP 社群 （英文）</span><span class="sxs-lookup"><span data-stu-id="0a297-183">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

[<span data-ttu-id="0a297-184">媒體品質和 Skype 的線上商務的網路連線效能</span><span class="sxs-lookup"><span data-stu-id="0a297-184">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[<span data-ttu-id="0a297-185">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="0a297-185">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="0a297-186">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="0a297-186">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="0a297-187">Office 365 URL 與 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="0a297-187">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="0a297-188">Office 365 網路和效能調整</span><span class="sxs-lookup"><span data-stu-id="0a297-188">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
