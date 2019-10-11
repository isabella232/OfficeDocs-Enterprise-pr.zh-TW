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
ms.openlocfilehash: 360cae39010f35b5a921ec95f6e8ed1d02afb808
ms.sourcegitcommit: ecfa362182f906befa885bf5f0094528ff570779
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "37435407"
---
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="939a8-103">Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="939a8-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="939a8-104">*本文適用於 Office 365 企業版和 Microsoft 365 企業版*</span><span class="sxs-lookup"><span data-stu-id="939a8-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise*</span></span>

<span data-ttu-id="939a8-105">了解 Azure ExpressRoute 搭配 Office 365 的方式，以及如何規劃將會需要，如果您要為搭配 Office 365 部署 Azure ExpressRoute 的網路實作專案。</span><span class="sxs-lookup"><span data-stu-id="939a8-105">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365.</span></span> <span data-ttu-id="939a8-106">在 Azure 中執行的基礎結構和平台服務通常會受益所定址網路架構與效能考量。</span><span class="sxs-lookup"><span data-stu-id="939a8-106">Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations.</span></span> <span data-ttu-id="939a8-107">建議 Azure 的 ExpressRoute 在這些情況下。</span><span class="sxs-lookup"><span data-stu-id="939a8-107">We recommend ExpressRoute for Azure in these cases.</span></span> <span data-ttu-id="939a8-108">軟體即 like 已透過網際網路存取安全且可靠地建置 Office 365 和 Dynamics 365 服務方案。</span><span class="sxs-lookup"><span data-stu-id="939a8-108">Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet.</span></span> <span data-ttu-id="939a8-109">您可以閱讀有關網際網路效能與安全性，以及時，您可能會列入考量 Azure ExpressRoute for Office 365 文章[評估 Office 365 網路連線](assessing-network-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="939a8-109">You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Assessing Office 365 network connectivity](assessing-network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="939a8-110">Microsoft 授權，才能使用 ExpressRoute for Office 365。</span><span class="sxs-lookup"><span data-stu-id="939a8-110">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="939a8-111">Microsoft 檢閱每個客戶要求，以及客戶的法規需求所要求的直接連線時，授權 ExpressRoute for Office 365 流量。</span><span class="sxs-lookup"><span data-stu-id="939a8-111">Microsoft reviews every customer request and authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="939a8-112">如果您有這類需求，請提供規定您解讀表示直接連線需要在[ExpressRoute for Office 365 要求表單](https://aka.ms/O365ERReview)中，若要開始 Microsoft 檢閱其文字摘錄與網頁連結。</span><span class="sxs-lookup"><span data-stu-id="939a8-112">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="939a8-113">未經授權嘗試建立 Office 365 路由篩選器的訂用帳戶會收到[錯誤訊息](https://support.microsoft.com/kb/3181709)。</span><span class="sxs-lookup"><span data-stu-id="939a8-113">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>

<span data-ttu-id="939a8-114">您現在可以新增至 Office 365 的直接的網路連線的所選的 Office 365 網路流量。</span><span class="sxs-lookup"><span data-stu-id="939a8-114">You can now add a direct network connection to Office 365 for selected Office 365 network traffic.</span></span> <span data-ttu-id="939a8-115">Azure ExpressRoute 可提供直接連線，可預測的效能，和隨附的 Microsoft 網路元件的執行時間 SLA 99.95%。</span><span class="sxs-lookup"><span data-stu-id="939a8-115">Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components.</span></span> <span data-ttu-id="939a8-116">您仍將需要網際網路連線不支援透過 Azure ExpressRoute 的服務。</span><span class="sxs-lookup"><span data-stu-id="939a8-116">You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="939a8-117">規劃 Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="939a8-117">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="939a8-118">除了網際網路連線能力，您可以選擇透過提供可預測性和 Microsoft 網路元件 99.95%執行時間 SLA 直接連線路由其 Office 365 的網路流量的子集。</span><span class="sxs-lookup"><span data-stu-id="939a8-118">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components.</span></span> <span data-ttu-id="939a8-119">Azure ExpressRoute 為您提供此專用的網路連線至 Office 365 和其他 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="939a8-119">Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="939a8-120">無論您是否已現有 MPLS WAN，ExpressRoute 可新增至您的網路架構中有三種;透過支援的雲端 exchange 代管提供者，乙太網路點對點連線提供者，或是 MPLS 連線提供者。</span><span class="sxs-lookup"><span data-stu-id="939a8-120">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider.</span></span> <span data-ttu-id="939a8-121">請參閱[提供者會在您的地區中使用](https://azure.microsoft.com/documentation/articles/expressroute-locations/)何種。</span><span class="sxs-lookup"><span data-stu-id="939a8-121">See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="939a8-122">直接 ExpressRoute 連線會啟用連線中所述的應用程式[哪些 Office 365 服務都包含在內？](azure-expressroute.md#BKMK_WhatDoIGet)下方。</span><span class="sxs-lookup"><span data-stu-id="939a8-122">The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below.</span></span> <span data-ttu-id="939a8-123">所有其他應用程式和服務的網路流量會繼續周遊網際網路。</span><span class="sxs-lookup"><span data-stu-id="939a8-123">Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="939a8-124">請考慮下列高等級的網路圖表顯示典型的 Office 365 客戶，透過網際網路存取 Office 365、 Windows Update] 等 TechNet 的所有 Microsoft 應用程式的連線至 Microsoft 資料中心。</span><span class="sxs-lookup"><span data-stu-id="939a8-124">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet.</span></span> <span data-ttu-id="939a8-125">客戶使用類似的網路路徑，不論他們正在連線從內部網路或從獨立的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="939a8-125">Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 網路連線能力](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="939a8-127">現在請查看更新的圖表以說明 Office 365 客戶使用的網際網路和 ExpressRoute 連線到 Office 365 的人員。</span><span class="sxs-lookup"><span data-stu-id="939a8-127">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365.</span></span> <span data-ttu-id="939a8-128">請注意一些連線，例如公用 DNS 和內容傳遞網路節點仍需要公用的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="939a8-128">Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection.</span></span> <span data-ttu-id="939a8-129">也請注意並非位於其 ExpressRoute 連線的建置透過網際網路連線的客戶的使用者。</span><span class="sxs-lookup"><span data-stu-id="939a8-129">Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![使用 ExpressRoute 的 office 365 連線能力](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="939a8-131">仍需要更多資訊？</span><span class="sxs-lookup"><span data-stu-id="939a8-131">Still want more information?</span></span> <span data-ttu-id="939a8-132">了解如何[管理您的網路流量使用 Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)並了解如何[設定 Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)。</span><span class="sxs-lookup"><span data-stu-id="939a8-132">Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).</span></span> <span data-ttu-id="939a8-133">我們也已記錄以協助說明的概念更徹底 Channel 9 10 部分的[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)系列。</span><span class="sxs-lookup"><span data-stu-id="939a8-133">We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="939a8-134">包含哪些 Office 365 服務？</span><span class="sxs-lookup"><span data-stu-id="939a8-134">What Office 365 services are included?</span></span>
<span data-ttu-id="939a8-135"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="939a8-135"></span></span>

<span data-ttu-id="939a8-136">下表列出透過 ExpressRoute 支援的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="939a8-136">The following table lists the Office 365 services that are supported over ExpressRoute.</span></span> <span data-ttu-id="939a8-137">請檢閱[Office 365 端點文章](https://aka.ms/o365endpoints)以了解這些應用程式的網路要求需要網際網路連線能力。</span><span class="sxs-lookup"><span data-stu-id="939a8-137">Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="939a8-138">**包含的應用程式**</span><span class="sxs-lookup"><span data-stu-id="939a8-138">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="939a8-139">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-139">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-140">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-140">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-141">Delve<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-141">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="939a8-142">Skype 商務 Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-142">Skype for Business Online<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-143">Microsoft Teams <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-143">Microsoft Teams <sup>1</sup></span></span> <br/> |
|<span data-ttu-id="939a8-144">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-144">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-145">OneDrive for Business<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-145">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-146">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-146">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="939a8-147">入口網站及共用的<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-147">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-148">Azure Active Directory<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-148">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-149">AAD 連線<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-149">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="939a8-150">Office<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="939a8-150">Office<sup>1</sup></span></span> <br/> |

<span data-ttu-id="939a8-151"><sup>1</sup>每個這些應用程式不支援透過 ExpressRoute 的網際網路連線能力需求，請參閱[Office 365 端點文章](https://aka.ms/o365endpoints)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="939a8-151"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="939a8-152">不包含使用 ExpressRoute for Office 365 服務，而 Office 365 專業增強版的用戶端下載項目、 內部部署身分識別提供者登入]，在中國的 Office 365 (21vianet 21 Vianet) 服務。</span><span class="sxs-lookup"><span data-stu-id="939a8-152">The services that aren't included with ExpressRoute for Office 365 are Office 365 ProPlus client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="939a8-153">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="939a8-153">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="939a8-154">實作 ExpressRoute 需要網路和應用程式的擁有人的參與程度，而且需要仔細規劃至判斷新的[網路路由架構](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、 頻寬需求，將安全性的實作，高可用性等等。</span><span class="sxs-lookup"><span data-stu-id="939a8-154">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on.</span></span> <span data-ttu-id="939a8-155">若要實作 ExpressRoute，您將需要：</span><span class="sxs-lookup"><span data-stu-id="939a8-155">To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="939a8-156">完全了解 ExpressRoute 滿足您 Office 365 連線能力規劃中的需求。</span><span class="sxs-lookup"><span data-stu-id="939a8-156">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning.</span></span> <span data-ttu-id="939a8-157">了解哪些應用程式會使用 ExpressRoute 的網際網路和完全規劃您的網路容量、 安全性和高可用性需求在內容中使用的網際網路和 ExpressRoute for Office 365 的流量。</span><span class="sxs-lookup"><span data-stu-id="939a8-157">Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="939a8-158">判定輸出及網際網路和 ExpressRoute 流量<sup>1</sup>的對等位置。</span><span class="sxs-lookup"><span data-stu-id="939a8-158">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="939a8-159">判斷在網際網路上及 ExpressRoute 連線所需的容量。</span><span class="sxs-lookup"><span data-stu-id="939a8-159">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="939a8-160">有計劃中實作的安全性和其他標準周邊控制項<sup>1</sup>的地方。</span><span class="sxs-lookup"><span data-stu-id="939a8-160">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="939a8-161">必須是有效的 Microsoft Azure 帳戶 ExpressRoute 訂閱。</span><span class="sxs-lookup"><span data-stu-id="939a8-161">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="939a8-162">選取連線模型和[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)。</span><span class="sxs-lookup"><span data-stu-id="939a8-162">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="939a8-163">請記住，客戶可以選取多個連線模型或協力廠商和協力廠商不一定要與您現有的網路提供者相同。</span><span class="sxs-lookup"><span data-stu-id="939a8-163">Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="939a8-164">驗證前將 ExpressRoute 流量導向的部署。</span><span class="sxs-lookup"><span data-stu-id="939a8-164">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="939a8-165">（選用） [ [qos](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)並評估地區擴充。</span><span class="sxs-lookup"><span data-stu-id="939a8-165">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="939a8-166"><sup>1</sup>重要的效能考量。</span><span class="sxs-lookup"><span data-stu-id="939a8-166"><sup>1</sup>Important performance considerations.</span></span> <span data-ttu-id="939a8-167">此處的決策可能大幅會影響這是重要的商務用 Skype 等應用程式的延遲。</span><span class="sxs-lookup"><span data-stu-id="939a8-167">Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="939a8-168">針對其他參考資料，使用我們[路由指南](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)除了[ExpressRoute 文件](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)。</span><span class="sxs-lookup"><span data-stu-id="939a8-168">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="939a8-169">若要購買 ExpressRoute for Office 365，您需要使用一個或多個[核准提供者](https://azure.microsoft.com/documentation/articles/expressroute-locations/)佈建所需的數目與大小電路 ExpressRoute 進階版訂閱。</span><span class="sxs-lookup"><span data-stu-id="939a8-169">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription.</span></span> <span data-ttu-id="939a8-170">有從 Office 365 購買額外的授權。</span><span class="sxs-lookup"><span data-stu-id="939a8-170">There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="939a8-171">您可以使用下列短連結返回這裡：[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="939a8-171">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="939a8-172">備妥可註冊的[ExpressRoute for Office 365](https://aka.ms/ert)？</span><span class="sxs-lookup"><span data-stu-id="939a8-172">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

## <a name="related-topics"></a><span data-ttu-id="939a8-173">相關主題</span><span class="sxs-lookup"><span data-stu-id="939a8-173">Related Topics</span></span>

[<span data-ttu-id="939a8-174">評估 Office 365 網路連線</span><span class="sxs-lookup"><span data-stu-id="939a8-174">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="939a8-175">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="939a8-175">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="939a8-176">使用 ExpressRoute for Office 365 進行路由傳送</span><span class="sxs-lookup"><span data-stu-id="939a8-176">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="939a8-177">使用 ExpressRoute for Office 365 進行網路規劃</span><span class="sxs-lookup"><span data-stu-id="939a8-177">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="939a8-178">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="939a8-178">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="939a8-179">使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）</span><span class="sxs-lookup"><span data-stu-id="939a8-179">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

<span data-ttu-id="939a8-180">[商務用 Skype Online 中的媒體品質和網路連線效能](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917) (英文)</span><span class="sxs-lookup"><span data-stu-id="939a8-180">[Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)</span></span>

[<span data-ttu-id="939a8-181">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="939a8-181">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="939a8-182">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="939a8-182">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

<span data-ttu-id="939a8-183">[Office 365 URL 與 IP 位址範圍](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges) (英文)</span><span class="sxs-lookup"><span data-stu-id="939a8-183">[Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)</span></span>

[<span data-ttu-id="939a8-184">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="939a8-184">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

## <a name="see-also"></a><span data-ttu-id="939a8-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="939a8-185">See also</span></span>

[<span data-ttu-id="939a8-186">Microsoft 365 企業版概觀</span><span class="sxs-lookup"><span data-stu-id="939a8-186">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
