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
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="8da74-103">Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="8da74-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="8da74-104">了解 Azure ExpressRoute 搭配 Office 365 的方式，以及如何規劃將會需要，如果您要為搭配 Office 365 部署 Azure ExpressRoute 的網路實作專案。</span><span class="sxs-lookup"><span data-stu-id="8da74-104">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365.</span></span> <span data-ttu-id="8da74-105">在 Azure 中執行的基礎結構和平台服務通常會受益所定址網路架構與效能考量。</span><span class="sxs-lookup"><span data-stu-id="8da74-105">Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations.</span></span> <span data-ttu-id="8da74-106">建議 Azure 的 ExpressRoute 在這些情況下。</span><span class="sxs-lookup"><span data-stu-id="8da74-106">We recommend ExpressRoute for Azure in these cases.</span></span> <span data-ttu-id="8da74-107">軟體即 like 已透過網際網路存取安全且可靠地建置 Office 365 和 Dynamics 365 服務方案。</span><span class="sxs-lookup"><span data-stu-id="8da74-107">Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet.</span></span> <span data-ttu-id="8da74-108">您可以閱讀有關網際網路效能與安全性，以及時，您可能會列入考量 Azure ExpressRoute for Office 365 文章[評估 Office 365 網路連線](assessing-network-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="8da74-108">You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Assessing Office 365 network connectivity](assessing-network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8da74-109">Microsoft 授權，才能使用 ExpressRoute for Office 365。</span><span class="sxs-lookup"><span data-stu-id="8da74-109">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="8da74-110">Microsoft 檢閱每個客戶要求，以及客戶的法規需求所要求的直接連線時，授權 ExpressRoute for Office 365 流量。</span><span class="sxs-lookup"><span data-stu-id="8da74-110">Microsoft reviews every customer request and authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="8da74-111">如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。</span><span class="sxs-lookup"><span data-stu-id="8da74-111">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="8da74-112">未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="8da74-112">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>

<span data-ttu-id="8da74-113">您現在可以新增至 Office 365 的直接的網路連線的所選的 Office 365 網路流量。</span><span class="sxs-lookup"><span data-stu-id="8da74-113">You can now add a direct network connection to Office 365 for selected Office 365 network traffic.</span></span> <span data-ttu-id="8da74-114">Azure ExpressRoute 可提供直接連線，可預測的效能，和隨附的 Microsoft 網路元件的執行時間 SLA 99.95%。</span><span class="sxs-lookup"><span data-stu-id="8da74-114">Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components.</span></span> <span data-ttu-id="8da74-115">您仍將需要網際網路連線不支援透過 Azure ExpressRoute 的服務。</span><span class="sxs-lookup"><span data-stu-id="8da74-115">You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="8da74-116">規劃 Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="8da74-116">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="8da74-117">除了網際網路連線能力，您可以選擇透過提供可預測性和 Microsoft 網路元件 99.95%執行時間 SLA 直接連線路由其 Office 365 的網路流量的子集。</span><span class="sxs-lookup"><span data-stu-id="8da74-117">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components.</span></span> <span data-ttu-id="8da74-118">Azure ExpressRoute 為您提供此專用的網路連線至 Office 365 和其他 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="8da74-118">Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="8da74-119">無論您是否已現有 MPLS WAN，ExpressRoute 可新增至您的網路架構中有三種;透過支援的雲端 exchange 代管提供者，乙太網路點對點連線提供者，或是 MPLS 連線提供者。</span><span class="sxs-lookup"><span data-stu-id="8da74-119">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider.</span></span> <span data-ttu-id="8da74-120">請參閱[提供者會在您的地區中使用](https://azure.microsoft.com/documentation/articles/expressroute-locations/)何種。</span><span class="sxs-lookup"><span data-stu-id="8da74-120">See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="8da74-121">直接 ExpressRoute 連線會啟用連線中所述的應用程式[哪些 Office 365 服務都包含在內？](azure-expressroute.md#BKMK_WhatDoIGet)下方。</span><span class="sxs-lookup"><span data-stu-id="8da74-121">The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below.</span></span> <span data-ttu-id="8da74-122">所有其他應用程式和服務的網路流量會繼續周遊網際網路。</span><span class="sxs-lookup"><span data-stu-id="8da74-122">Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="8da74-123">請考慮下列高等級的網路圖表顯示典型的 Office 365 客戶，透過網際網路存取 Office 365、 Windows Update] 等 TechNet 的所有 Microsoft 應用程式的連線至 Microsoft 資料中心。</span><span class="sxs-lookup"><span data-stu-id="8da74-123">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet.</span></span> <span data-ttu-id="8da74-124">客戶使用類似的網路路徑，不論他們正在連線從內部網路或從獨立的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="8da74-124">Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 網路連線能力](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="8da74-126">現在請查看更新的圖表以說明 Office 365 客戶使用的網際網路和 ExpressRoute 連線到 Office 365 的人員。</span><span class="sxs-lookup"><span data-stu-id="8da74-126">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365.</span></span> <span data-ttu-id="8da74-127">請注意一些連線，例如公用 DNS 和內容傳遞網路節點仍需要公用的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="8da74-127">Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection.</span></span> <span data-ttu-id="8da74-128">也請注意並非位於其 ExpressRoute 連線的建置透過網際網路連線的客戶的使用者。</span><span class="sxs-lookup"><span data-stu-id="8da74-128">Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![使用 ExpressRoute 的 office 365 連線能力](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="8da74-130">仍需要更多資訊？</span><span class="sxs-lookup"><span data-stu-id="8da74-130">Still want more information?</span></span> <span data-ttu-id="8da74-131">了解如何[管理您的網路流量使用 Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)並了解如何[設定 Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。</span><span class="sxs-lookup"><span data-stu-id="8da74-131">Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).</span></span> <span data-ttu-id="8da74-132">我們也已記錄以協助說明的概念更徹底 Channel 9 10 部分的[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)系列。</span><span class="sxs-lookup"><span data-stu-id="8da74-132">We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="8da74-133">包含哪些 Office 365 服務？</span><span class="sxs-lookup"><span data-stu-id="8da74-133">What Office 365 services are included?</span></span>
<span data-ttu-id="8da74-134"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="8da74-134"></span></span>

<span data-ttu-id="8da74-135">下表列出透過 ExpressRoute 支援的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="8da74-135">The following table lists the Office 365 services that are supported over ExpressRoute.</span></span> <span data-ttu-id="8da74-136">請檢閱[Office 365 端點文章](https://aka.ms/o365endpoints)以了解這些應用程式的網路要求需要網際網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="8da74-136">Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="8da74-137">**包含的應用程式**</span><span class="sxs-lookup"><span data-stu-id="8da74-137">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="8da74-138">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-138">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="8da74-139">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-139">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="8da74-140">Delve<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-140">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="8da74-141">Skype 商務 Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-141">Skype for Business Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="8da74-142">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-142">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="8da74-143">OneDrive for Business<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-143">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="8da74-144">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-144">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="8da74-145">入口網站及共用的<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-145">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="8da74-146">Azure Active Directory<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-146">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="8da74-147">AAD 連線<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-147">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="8da74-148">Office<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8da74-148">Office<sup>1</sup></span></span> <br/> |

<span data-ttu-id="8da74-149"><sup>1</sup>每個這些應用程式不支援透過 ExpressRoute 的網際網路連線能力需求，請參閱[Office 365 端點文章](https://aka.ms/o365endpoints)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8da74-149"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="8da74-150">不包含使用 ExpressRoute for Office 365 服務，而 Office 365 專業增強版的用戶端下載項目、 內部部署身分識別提供者登入]，在中國的 Office 365 (21vianet 21 Vianet) 服務。</span><span class="sxs-lookup"><span data-stu-id="8da74-150">The services that aren't included with ExpressRoute for Office 365 are Office 365 ProPlus client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="8da74-151">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="8da74-151">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="8da74-152">實作 ExpressRoute 需要網路和應用程式的擁有人的參與程度，而且需要仔細規劃至判斷新的[網路路由架構](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、 頻寬需求，將安全性的實作，高可用性等等。</span><span class="sxs-lookup"><span data-stu-id="8da74-152">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on.</span></span> <span data-ttu-id="8da74-153">若要實作 ExpressRoute，您將需要：</span><span class="sxs-lookup"><span data-stu-id="8da74-153">To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="8da74-154">完全了解 ExpressRoute 滿足您 Office 365 連線能力規劃中的需求。</span><span class="sxs-lookup"><span data-stu-id="8da74-154">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning.</span></span> <span data-ttu-id="8da74-155">了解哪些應用程式會使用 ExpressRoute 的網際網路和完全規劃您的網路容量、 安全性和高可用性需求在內容中使用的網際網路和 ExpressRoute for Office 365 的流量。</span><span class="sxs-lookup"><span data-stu-id="8da74-155">Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="8da74-156">判定輸出及網際網路和 ExpressRoute 流量<sup>1</sup>的對等位置。</span><span class="sxs-lookup"><span data-stu-id="8da74-156">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="8da74-157">判斷在網際網路上及 ExpressRoute 連線所需的容量。</span><span class="sxs-lookup"><span data-stu-id="8da74-157">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="8da74-158">有計劃中實作的安全性和其他標準周邊控制項<sup>1</sup>的地方。</span><span class="sxs-lookup"><span data-stu-id="8da74-158">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="8da74-159">必須是有效的 Microsoft Azure 帳戶 ExpressRoute 訂閱。</span><span class="sxs-lookup"><span data-stu-id="8da74-159">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="8da74-160">選取連線模型和[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。</span><span class="sxs-lookup"><span data-stu-id="8da74-160">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="8da74-161">請記住，客戶可以選取多個連線模型或協力廠商和協力廠商不一定要與您現有的網路提供者相同。</span><span class="sxs-lookup"><span data-stu-id="8da74-161">Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="8da74-162">驗證前將 ExpressRoute 流量導向的部署。</span><span class="sxs-lookup"><span data-stu-id="8da74-162">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="8da74-163">（選用） [ [qos](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)並評估地區擴充。</span><span class="sxs-lookup"><span data-stu-id="8da74-163">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="8da74-164"><sup>1</sup>重要的效能考量。</span><span class="sxs-lookup"><span data-stu-id="8da74-164"><sup>1</sup>Important performance considerations.</span></span> <span data-ttu-id="8da74-165">此處的決策可能大幅會影響這是重要的商務用 Skype 等應用程式的延遲。</span><span class="sxs-lookup"><span data-stu-id="8da74-165">Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="8da74-166">針對其他參考資料，使用我們[路由指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)除了[ExpressRoute 文件](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)。</span><span class="sxs-lookup"><span data-stu-id="8da74-166">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="8da74-167">若要購買 ExpressRoute for Office 365，您需要使用一個或多個[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)佈建所需的數目與大小電路 ExpressRoute 進階版訂閱。</span><span class="sxs-lookup"><span data-stu-id="8da74-167">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription.</span></span> <span data-ttu-id="8da74-168">有從 Office 365 購買額外的授權。</span><span class="sxs-lookup"><span data-stu-id="8da74-168">There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="8da74-169">您可以使用下列短連結返回這裡：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="8da74-169">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="8da74-170">備妥可註冊的[ExpressRoute for Office 365](https://aka.ms/ert)？</span><span class="sxs-lookup"><span data-stu-id="8da74-170">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

## <a name="related-topics"></a><span data-ttu-id="8da74-171">相關主題</span><span class="sxs-lookup"><span data-stu-id="8da74-171">Related Topics</span></span>

[<span data-ttu-id="8da74-172">評估 Office 365 網路連線</span><span class="sxs-lookup"><span data-stu-id="8da74-172">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="8da74-173">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="8da74-173">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="8da74-174">使用 ExpressRoute for Office 365 進行路由傳送</span><span class="sxs-lookup"><span data-stu-id="8da74-174">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="8da74-175">使用 ExpressRoute for Office 365 進行網路規劃</span><span class="sxs-lookup"><span data-stu-id="8da74-175">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="8da74-176">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="8da74-176">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="8da74-177">使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）</span><span class="sxs-lookup"><span data-stu-id="8da74-177">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

<span data-ttu-id="8da74-178">[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)</span><span class="sxs-lookup"><span data-stu-id="8da74-178">[Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)</span></span>

[<span data-ttu-id="8da74-179">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="8da74-179">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="8da74-180">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="8da74-180">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

<span data-ttu-id="8da74-181">[Office 365 URL 與 IP 位址範圍](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) (英文)</span><span class="sxs-lookup"><span data-stu-id="8da74-181">[Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)</span></span>

[<span data-ttu-id="8da74-182">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="8da74-182">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
