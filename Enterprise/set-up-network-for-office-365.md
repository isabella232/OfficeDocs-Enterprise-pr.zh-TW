---
title: 為 Office 365 設定您的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 摘要：請參閱這些文章以了解 Office 365 的網路功能。
ms.openlocfilehash: 958841733259bd01cd16a908cfac65998a3f3127
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722682"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="e7197-103">為 Office 365 設定您的網路</span><span class="sxs-lookup"><span data-stu-id="e7197-103">Set up your network for Office 365</span></span>

<span data-ttu-id="e7197-104">**摘要：** 請參閱這些文章以了解 Office 365 的網路功能。</span><span class="sxs-lookup"><span data-stu-id="e7197-104">**Summary:** See these articles to understand networking for Office 365.</span></span>
  
<span data-ttu-id="e7197-p101">對 Office 365 上線很重要的一點是，要先確定您的網路和網際網路連線已針對最佳化存取進行設定。設定您的內部部署網路以存取全域分散式的軟體即服務 (SaaS) 雲端，與針對內部部署資料中心的流量進行最佳化的傳統網路不同。</span><span class="sxs-lookup"><span data-stu-id="e7197-p101">An important part of your Office 365 onboarding is to first ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters.</span></span> 

<span data-ttu-id="e7197-107">參閱這些文章以了解主要差異，並修改您的邊緣裝置、用戶端電腦與內部部署網路，以取得最佳的使用者效能。</span><span class="sxs-lookup"><span data-stu-id="e7197-107">Use these articles to understand the key differences and to modify your  edge devices, client computers, and on-premises network to get the best user performance.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="e7197-108">Office 365 網路功能的運作方式</span><span class="sxs-lookup"><span data-stu-id="e7197-108">How Office 365 networking works</span></span>

<span data-ttu-id="e7197-109">請參閱下列文章，以取得 Office 365 連線能力概觀：</span><span class="sxs-lookup"><span data-stu-id="e7197-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="e7197-110">Office 365 網路連線能力概觀</span><span class="sxs-lookup"><span data-stu-id="e7197-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="e7197-111">Office 365 網路連線能力原則</span><span class="sxs-lookup"><span data-stu-id="e7197-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="e7197-112">評估 Office 365 的網路連線能力</span><span class="sxs-lookup"><span data-stu-id="e7197-112">Office 365 network connectivity principles</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="e7197-113">如需提升效能的建議，請參閱 [Office 365 的網路規劃和效能調整](network-planning-and-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="e7197-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="e7197-114">支援 Office 365 網路為網路設備廠商</span><span class="sxs-lookup"><span data-stu-id="e7197-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="e7197-p102">如果您是網路設備廠商，請加入 [Office 365 網路合作夥伴計畫](office-365-networking-partner-program.md)。註冊此計畫，將 Office 365 網路連線原則建置到您的產品與解決方案中。</span><span class="sxs-lookup"><span data-stu-id="e7197-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="e7197-117">Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="e7197-117">Office 365 endpoints</span></span>

<span data-ttu-id="e7197-118">端點為一組目的地 IP 位址、DNS 網域名稱，以及網際網路上 Office 365 流量的 URL。</span><span class="sxs-lookup"><span data-stu-id="e7197-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="e7197-p103">若要最佳化 Office 365 雲端式服務的效能，這些端點需要由用戶端瀏覽器和邊緣網路中的裝置進行特別處理。這些裝置包括防火牆、SSL 中斷和檢查及封包檢查裝置，以及資料外洩防護系統。</span><span class="sxs-lookup"><span data-stu-id="e7197-p103">To optimize performance to Office 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="e7197-121">請參閱[管理 Office 365 端點](managing-office-365-endpoints.md)以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e7197-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="e7197-p104">目前有五種不同的 Office 365 雲端。下表顯示每種雲端的端點清單。</span><span class="sxs-lookup"><span data-stu-id="e7197-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="e7197-124">全球端點</span><span class="sxs-lookup"><span data-stu-id="e7197-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="e7197-125">全球 Office 365 訂閱的端點，包括美國政府社群雲端 (GCC)。</span><span class="sxs-lookup"><span data-stu-id="e7197-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="e7197-126">美國政府 DoD 端點</span><span class="sxs-lookup"><span data-stu-id="e7197-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="e7197-127">適用於美國國防部 (DoD) 訂閱的端點。</span><span class="sxs-lookup"><span data-stu-id="e7197-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="e7197-128">美國政府 GCC High 端點</span><span class="sxs-lookup"><span data-stu-id="e7197-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="e7197-129">適用於美國政府社群雲端高 (GCC High) 訂閱的端點。</span><span class="sxs-lookup"><span data-stu-id="e7197-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="e7197-130">由 21Vianet 營運的 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="e7197-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="e7197-131">由 21Vianet 營運的 Office 365 端點，其目的是為了符合中國的 Office 365 需求。</span><span class="sxs-lookup"><span data-stu-id="e7197-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="e7197-132">Office 365 Germany 端點</span><span class="sxs-lookup"><span data-stu-id="e7197-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="e7197-133">針對德國、歐盟 (EU) 以及歐洲自由貿易聯盟 (EFTA) 中受管制客戶的歐洲個別雲端端點。</span><span class="sxs-lookup"><span data-stu-id="e7197-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="e7197-134">若要自動取得您 Office 365 雲端的最新端點清單，請參閱 [Office 365 IP 位址和 URL Web 服務](office-365-ip-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="e7197-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="e7197-135">如需其他端點，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="e7197-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="e7197-136">未包含在 Web 服務中的其他端點</span><span class="sxs-lookup"><span data-stu-id="e7197-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="e7197-137">Mac 版 Office 2016 中的網路要求</span><span class="sxs-lookup"><span data-stu-id="e7197-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="e7197-138">Office 365 網路功能的其他主題</span><span class="sxs-lookup"><span data-stu-id="e7197-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="e7197-139">請參閱下列文章，了解 Office 365 網路功能中的特定主題：</span><span class="sxs-lookup"><span data-stu-id="e7197-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="e7197-140">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="e7197-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="e7197-141">Office 365 服務中的 IPv6 支援</span><span class="sxs-lookup"><span data-stu-id="e7197-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="e7197-142">Office 365 的 NAT 支援</span><span class="sxs-lookup"><span data-stu-id="e7197-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="e7197-143">ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="e7197-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="e7197-144">請參閱下列文章，了解針對 Office 365 流量使用 ExpressRoute 的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="e7197-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="e7197-145">Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="e7197-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="e7197-146">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="e7197-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="e7197-147">使用 ExpressRoute for Office 365 進行網路規劃</span><span class="sxs-lookup"><span data-stu-id="e7197-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="e7197-148">使用 ExpressRoute for Office 365 進行路由傳送</span><span class="sxs-lookup"><span data-stu-id="e7197-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
