---
title: Office 365 網路連線能力概述
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 討論為何網路優化對於 SaaS 服務非常重要, Office 365 網路的目標, 以及 SaaS 如何與其他工作負載不同的網路。
ms.openlocfilehash: e1ae446d7a69d0fab83e7dd4aa253bd1120e6c08
ms.sourcegitcommit: 99bf8739dfe1842c71154ed9548ebdd013c7e59e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2019
ms.locfileid: "35017283"
---
# <a name="office-365-network-connectivity-overview"></a><span data-ttu-id="8abf5-103">Office 365 網路連線能力概述</span><span class="sxs-lookup"><span data-stu-id="8abf5-103">Office 365 network connectivity overview</span></span>

<span data-ttu-id="8abf5-104">Office 365 是分散式的軟體即服務 (SaaS) 雲端, 可透過一組不同的微服務和應用程式提供生產力和共同作業案例。</span><span class="sxs-lookup"><span data-stu-id="8abf5-104">Office 365 is a distributed Software-as-a-Service (SaaS) cloud that provides productivity and collaboration scenarios through a diverse set of micro-services and applications.</span></span> <span data-ttu-id="8abf5-105">Office 365 的用戶端元件, 例如 Outlook、Word 和 PowerPoint 在使用者電腦上執行, 並連接到在 Microsoft 資料中心執行的 Office 365 的其他元件。</span><span class="sxs-lookup"><span data-stu-id="8abf5-105">Client components of Office 365 such as Outlook, Word and PowerPoint run on user computers and connect to other components of Office 365 that run in Microsoft datacenters.</span></span> <span data-ttu-id="8abf5-106">決定 Office 365 使用者體驗品質的最重要因素, 是 Office 365 用戶端與 Office 365 服務前端之間的網路可靠性和低延遲。</span><span class="sxs-lookup"><span data-stu-id="8abf5-106">The most significant factor that determines the quality of the Office 365 end user experience is network reliability and low latency between Office 365 clients and Office 365 service front doors.</span></span>

<span data-ttu-id="8abf5-107">在本文中, 您將瞭解 Office 365 網路的目標, 以及為什麼 Office 365 網路需要不同的方法來優化一般網際網路流量。</span><span class="sxs-lookup"><span data-stu-id="8abf5-107">In this article, you will learn about the goals of Office 365 networking, and why Office 365 networking requires a different approach to optimization than generic Internet traffic.</span></span>

## <a name="office-365-networking-goals"></a><span data-ttu-id="8abf5-108">Office 365 網路目標</span><span class="sxs-lookup"><span data-stu-id="8abf5-108">Office 365 networking goals</span></span>

<span data-ttu-id="8abf5-109">Office 365 網路的最終目標是在用戶端和最接近的 Office 365 端點之間啟用最小限制存取, 以優化使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="8abf5-109">The ultimate goal of Office 365 networking is to optimize the end user experience by enabling the least restrictive access between clients and the closest Office 365 endpoints.</span></span> <span data-ttu-id="8abf5-110">使用者經驗品質與使用者所使用之應用程式的效能及回應能力直接相關。</span><span class="sxs-lookup"><span data-stu-id="8abf5-110">The quality of end user experience is directly related to the performance and responsiveness of the application that the user is using.</span></span> <span data-ttu-id="8abf5-111">例如, Microsoft 團隊依賴低延遲, 讓使用者電話通話、會議和共用螢幕共同作業不會造成任何問題, 而 Outlook 則依賴出色的網路連線來進行即時搜尋功能, 以利用伺服器端的索引和 AI能力.</span><span class="sxs-lookup"><span data-stu-id="8abf5-111">For example, Microsoft Teams relies on low latency so that user phone calls, conferences and shared screen collaborations are glitch-free, and Outlook relies on great networking connectivity for instant search features that leverage server-side indexing and AI capabilities.</span></span>

<span data-ttu-id="8abf5-112">網路設計的主要目標是將用戶端電腦的往返時間 (RTT) 減少為 Microsoft 全球網路, 並將所有 Microsoft 資料中心與低延遲互連在一起, 以減少延遲時間。, 高可用性雲端應用程式進入點遍佈世界各地。</span><span class="sxs-lookup"><span data-stu-id="8abf5-112">The primary goal in the network design should be to minimize latency by reducing the round-trip time (RTT) from client machines to the Microsoft Global Network, Microsoft's public network backbone that interconnects all of Microsoft's datacenters with low latency, high availability cloud application entry points spread around the world.</span></span> <span data-ttu-id="8abf5-113">您可以在[Microsoft 如何建立其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/), 深入瞭解 Microsoft 全球網路。</span><span class="sxs-lookup"><span data-stu-id="8abf5-113">You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="8abf5-114">優化 Office 365 網路效能不需要很複雜。</span><span class="sxs-lookup"><span data-stu-id="8abf5-114">Optimizing Office 365 network performance doesn't need to be complicated.</span></span> <span data-ttu-id="8abf5-115">您可以遵循下列幾個重要的原則, 取得最佳的效能:</span><span class="sxs-lookup"><span data-stu-id="8abf5-115">You can get the best possible performance by following a few key principles:</span></span>

- <span data-ttu-id="8abf5-116">識別 Office 365 網路流量</span><span class="sxs-lookup"><span data-stu-id="8abf5-116">Identify Office 365 network traffic</span></span>
- <span data-ttu-id="8abf5-117">允許使用者連線至 Office 365 的每個位置, 從每個位置, 允許 Office 365 網路流量的本機分支出口</span><span class="sxs-lookup"><span data-stu-id="8abf5-117">Allow local branch egress of Office 365 network traffic to the internet from each location where users connect to Office 365</span></span>
- <span data-ttu-id="8abf5-118">允許 Office 365 流量略過 proxy 與封包檢查裝置</span><span class="sxs-lookup"><span data-stu-id="8abf5-118">Allow Office 365 traffic to bypass proxies and packet inspection devices</span></span>

<span data-ttu-id="8abf5-119">如需 Office 365 網路連線原則的詳細資訊, 請參閱[office 365 網路連線原則](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="8abf5-119">For more information on Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="traditional-network-architectures-and-saas"></a><span data-ttu-id="8abf5-120">傳統的網路架構和 SaaS</span><span class="sxs-lookup"><span data-stu-id="8abf5-120">Traditional network architectures and SaaS</span></span>

<span data-ttu-id="8abf5-121">用戶端/伺服器工作負載的傳統網路架構原則, 是圍繞用戶端與端點之間的流量所設計, 不會延伸到公司網路周邊之外。</span><span class="sxs-lookup"><span data-stu-id="8abf5-121">Traditional network architecture principles for client/server workloads are designed around the assumption that traffic between clients and endpoints does not extend outside the corporate network perimeter.</span></span> <span data-ttu-id="8abf5-122">此外, 在許多商業網路中, 所有的輸出網際網路連線都會透過公司網路, 以及從中央位置外出。</span><span class="sxs-lookup"><span data-stu-id="8abf5-122">Also, in many enterprise networks, all outbound Internet connections traverse the corporate network, and egress from a central location.</span></span>

<span data-ttu-id="8abf5-123">在傳統的網路架構中, 一般網際網路流量的較高延遲是維護網路周邊安全性所需的折衷措施, 而且網際網路流量的效能優化通常包括升級或擴充網路出局點的裝置。</span><span class="sxs-lookup"><span data-stu-id="8abf5-123">In traditional network architectures, higher latency for generic Internet traffic is a necessary tradeoff in order to maintain network perimeter security, and performance optimization for Internet traffic typically involves upgrading or scaling out the equipment at network egress points.</span></span> <span data-ttu-id="8abf5-124">不過, 此方法並不會解決 SaaS 服務 (例如 Office 365) 的最佳網路效能需求。</span><span class="sxs-lookup"><span data-stu-id="8abf5-124">However, this approach does not address the requirements for optimum network performance of SaaS services such as Office 365.</span></span>

## <a name="identifying-office-365-network-traffic"></a><span data-ttu-id="8abf5-125">識別 Office 365 網路流量</span><span class="sxs-lookup"><span data-stu-id="8abf5-125">Identifying Office 365 network traffic</span></span>

<span data-ttu-id="8abf5-126">我們讓您更容易識別 Office 365 網路流量, 並簡化網路識別的管理。</span><span class="sxs-lookup"><span data-stu-id="8abf5-126">We're making it easier to identify Office 365 network traffic and making it simpler to manage the network identification.</span></span>

- <span data-ttu-id="8abf5-127">新類別的網路端點, 以區分高重要的網路流量與不受網際網路延遲影響的網路流量。</span><span class="sxs-lookup"><span data-stu-id="8abf5-127">New categories of network endpoints to differentiate highly critical network traffic from network traffic which is not impacted by Internet latencies.</span></span> <span data-ttu-id="8abf5-128">在最重要的「優化」類別中, 只會有少數 Url 和支援 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="8abf5-128">There are just a handful of URLs and supporting IP Addresses in the most critical “Optimize” category.</span></span>
- <span data-ttu-id="8abf5-129">Web 服務以取得腳本使用方式, 或直接裝置設定, 以及 Office 365 網路識別的變更管理。</span><span class="sxs-lookup"><span data-stu-id="8abf5-129">Web services for script usage or direct device configuration and change management of Office 365 network identification.</span></span> <span data-ttu-id="8abf5-130">您可以從 web 服務或 RSS 格式, 或使用 Microsoft 流程範本在電子郵件上進行變更。</span><span class="sxs-lookup"><span data-stu-id="8abf5-130">Changes are available from the web service, or in RSS format, or on email using a Microsoft Flow template.</span></span>
- <span data-ttu-id="8abf5-131">[Office 365 網路合作夥伴計畫](http://aka.ms/Office365NPP), 其中的 Microsoft 合作夥伴提供的裝置或服務遵循 Office 365 網路連線原則並具有簡單的設定。</span><span class="sxs-lookup"><span data-stu-id="8abf5-131">[Office 365 Network partner program](http://aka.ms/Office365NPP) with Microsoft partners who provide devices or services that follow Office 365 network connectivity principles and have simple configuration.</span></span>

## <a name="securing-office-365-connections"></a><span data-ttu-id="8abf5-132">保護 Office 365 連線的安全</span><span class="sxs-lookup"><span data-stu-id="8abf5-132">Securing Office 365 connections</span></span>

<span data-ttu-id="8abf5-133">傳統網路安全性的目標是加強公司網路周邊, 防範入侵和惡意攻擊。</span><span class="sxs-lookup"><span data-stu-id="8abf5-133">The goal of traditional network security is to harden the corporate network perimeter against intrusion and malicious exploits.</span></span> <span data-ttu-id="8abf5-134">大部分的商業網路會使用類似 proxy 伺服器、防火牆、SSL 中斷、檢查、深入封包檢查和資料遺失防護系統等技術, 來強制執行網際網路流量的網路安全性。</span><span class="sxs-lookup"><span data-stu-id="8abf5-134">Most enterprise networks enforce network security for Internet traffic using technologies like proxy servers, firewalls, SSL break and inspect, deep packet inspection, and data loss prevention systems.</span></span> <span data-ttu-id="8abf5-135">這些技術可提供一般網際網路要求的重要風險減輕, 但是可以大幅降低效能、擴充性, 以及套用至 Office 365 端點時的使用者體驗品質。</span><span class="sxs-lookup"><span data-stu-id="8abf5-135">These technologies provide important risk mitigation for generic Internet requests but can dramatically reduce performance, scalability, and the quality of end user experience when applied to Office 365 endpoints.</span></span>

<span data-ttu-id="8abf5-136">Office 365 使用專為 Office 365 功能和工作負載而設計的內建安全性和控管功能, 協助滿足您組織的內容安全性和資料使用性的需求。</span><span class="sxs-lookup"><span data-stu-id="8abf5-136">Office 365 helps meet your organization's needs for content security and data usage compliance with built-in security and governance features designed specifically for Office 365 features and workloads.</span></span> <span data-ttu-id="8abf5-137">如需有關 Office 365 安全性和合規性的詳細資訊, 請參閱[Office 365 安全性藍圖](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。</span><span class="sxs-lookup"><span data-stu-id="8abf5-137">For more information about Office 365 security and compliance, see the [Office 365 security roadmap](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap).</span></span> <span data-ttu-id="8abf5-138">如需在執行 Office 365 流量的高級網路解決方案上, Microsoft 建議和支援位置的詳細資訊, 請參閱在[office 365 流量上使用協力廠商網路裝置或解決方案](https://support.microsoft.com/en-us/help/2690045)。</span><span class="sxs-lookup"><span data-stu-id="8abf5-138">For more information about Microsoft’s recommendations and support position on advanced network solutions that perform advanced-level processing on Office 365 traffic, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045).</span></span>

## <a name="why-is-office-365-networking-different"></a><span data-ttu-id="8abf5-139">為什麼 Office 365 網路是不同的？</span><span class="sxs-lookup"><span data-stu-id="8abf5-139">Why is Office 365 networking different?</span></span>

<span data-ttu-id="8abf5-140">Office 365 的設計是使用端點安全性和加密網路連線來優化效能, 以減少周邊安全性強制執行的需求。</span><span class="sxs-lookup"><span data-stu-id="8abf5-140">Office 365 is designed for optimal performance using endpoint security and encrypted network connections, reducing the need for perimeter security enforcement.</span></span> <span data-ttu-id="8abf5-141">Office 365 資料中心位於全球, 且服務的設計目的是使用各種方法將用戶端連線至最佳可用的服務端點。</span><span class="sxs-lookup"><span data-stu-id="8abf5-141">Office 365 datacenters are located across the world and the service is designed to use various methods for connecting clients to best available service endpoints.</span></span> <span data-ttu-id="8abf5-142">因為使用者資料和處理是分散在許多 Microsoft 資料中心, 所以用戶端電腦無法連線的單一網路端點。</span><span class="sxs-lookup"><span data-stu-id="8abf5-142">Since user data and processing is distributed between many Microsoft datacenters, there is no single network endpoint to which client machines can connect.</span></span> <span data-ttu-id="8abf5-143">事實上, Office 365 租使用者中的資料和服務會透過 Microsoft 全球網路進行動態優化, 以適應使用者存取使用者的地理位置。</span><span class="sxs-lookup"><span data-stu-id="8abf5-143">In fact, data and services in your Office 365 tenant are dynamically optimized by the Microsoft Global Network to adapt to the geographic locations from which they are accessed by end users.</span></span>

<span data-ttu-id="8abf5-144">當 Office 365 流量受到封包檢查和集中式外出時, 就會建立一些常見的效能問題:</span><span class="sxs-lookup"><span data-stu-id="8abf5-144">Certain common performance issues are created when Office 365 traffic is subject to packet inspection and centralized egress:</span></span>

- <span data-ttu-id="8abf5-145">高延遲可能會造成影片和音訊資料流程的效能不良, 以及資料檢索、搜尋、即時共同作業、行事曆空閒/忙碌資訊、產品內容及其他服務的回應速度緩慢</span><span class="sxs-lookup"><span data-stu-id="8abf5-145">High latency can cause extremely poor performance of video and audio streams, and slow response of data retrieval, searches, real-time collaboration, calendar free/busy information, in-product content and other services</span></span>
- <span data-ttu-id="8abf5-146">來自中央位置的 Egressing 連線會破壞 Office 365 通用網路的動態路由功能、新增延遲時間和往返時間</span><span class="sxs-lookup"><span data-stu-id="8abf5-146">Egressing connections from a central location defeats the dynamic routing capabilities of the Office 365 global network, adding latency and round-trip time</span></span>
- <span data-ttu-id="8abf5-147">解密 SSL 安全的 Office 365 網路流量並重新加密可能會造成通訊協定錯誤, 並有安全性風險</span><span class="sxs-lookup"><span data-stu-id="8abf5-147">Decrypting SSL secured Office 365 network traffic and re-encrypting it can cause protocol errors and has security risk</span></span>

<span data-ttu-id="8abf5-148">透過讓用戶端流量盡可能接近其地理位置, 以縮短 Office 365 進入點的網路路徑, 可改善連線效能和 Office 365 中的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="8abf5-148">Shortening the network path to Office 365 entry points by allowing client traffic to egress as close as possible to their geographic location can improve connectivity performance and the end user experience in Office 365.</span></span> <span data-ttu-id="8abf5-149">它也可協助您降低未來對 Office 365 效能和可靠性的網路架構所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="8abf5-149">It can also help to reduce the impact of future changes to the network architecture on Office 365 performance and reliability.</span></span> <span data-ttu-id="8abf5-150">最佳連線模型是在使用者的位置始終提供網路出局, 不論這是在公司網路還是在家、酒店、咖啡店和機場等遠端位置。</span><span class="sxs-lookup"><span data-stu-id="8abf5-150">The optimum connectivity model is to always provide network egress at the user's location, regardless of whether this is on the corporate network or remote locations such as home, hotels, coffee shops and airports.</span></span> <span data-ttu-id="8abf5-151">一般網際網路流量和 WAN 的公司網路流量將會分開路由, 且不會使用本機直接輸出模式。</span><span class="sxs-lookup"><span data-stu-id="8abf5-151">Generic Internet traffic and WAN based corporate network traffic would be separately routed and not use the local direct egress model.</span></span> <span data-ttu-id="8abf5-152">此本機直接輸出模型會在下圖中表示。</span><span class="sxs-lookup"><span data-stu-id="8abf5-152">This local direct egress model is represented in the diagram below.</span></span>

![本機出局網路架構](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

<span data-ttu-id="8abf5-154">本機出局架構針對傳統模型的 Office 365 網路流量有下列優點:</span><span class="sxs-lookup"><span data-stu-id="8abf5-154">The local egress architecture has the following benefits for Office 365 network traffic over the traditional model:</span></span>
  
- <span data-ttu-id="8abf5-155">優化路由長度, 以提供最佳的 Office 365 效能。</span><span class="sxs-lookup"><span data-stu-id="8abf5-155">Provides optimal Office 365 performance by optimizing route length.</span></span> <span data-ttu-id="8abf5-156">使用者連線會透過 Microsoft 全球網路的_分散式服務前端_基礎結構, 動態路由傳送至最接近的 Office 365 進入點, 然後流量會在內部路由傳送至 microsoft 的資料和服務端點。超低延遲高可用性深纖程。</span><span class="sxs-lookup"><span data-stu-id="8abf5-156">End user connections are dynamically routed to the nearest Office 365 entry point by the Microsoft Global Network's _Distributed Service Front Door_ infrastructure, and traffic is then routed internally to data and service endpoints over Microsoft's ultra-low latency high availability dark fiber.</span></span>
- <span data-ttu-id="8abf5-157">透過允許 Office 365 流量的本機出口, 以減少公司網路基礎結構的負載, 略過 proxy 和流量檢查裝置。</span><span class="sxs-lookup"><span data-stu-id="8abf5-157">Reduces the load on corporate network infrastructure by allowing local egress for Office 365 traffic, bypassing proxies and traffic inspection devices.</span></span>
- <span data-ttu-id="8abf5-158">利用用戶端端點安全性和雲端安全性功能, 以避免應用冗余網路安全性技術, 來保護兩端的連線。</span><span class="sxs-lookup"><span data-stu-id="8abf5-158">Secures connections on both ends by leveraging client endpoint security and cloud security features, avoiding application of redundant network security technologies.</span></span>

> [!NOTE]
> <span data-ttu-id="8abf5-159">_分散式服務前端_基礎結構是 Microsoft 全球網路的高度可用和可伸縮網路 edge, 以及地理位置分散的位置。</span><span class="sxs-lookup"><span data-stu-id="8abf5-159">The _Distributed Service Front Door_ infrastructure is the Microsoft Global Network's highly available and scalable network edge with geographically distributed locations.</span></span> <span data-ttu-id="8abf5-160">它會終止使用者連線, 並有效地將它們路由傳送至 Microsoft 全球網路中。</span><span class="sxs-lookup"><span data-stu-id="8abf5-160">It terminates end user connections and efficiently routes them within the Microsoft Global Network.</span></span> <span data-ttu-id="8abf5-161">您可以在[Microsoft 如何建立其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/), 深入瞭解 Microsoft 全球網路。</span><span class="sxs-lookup"><span data-stu-id="8abf5-161">You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="8abf5-162">如需瞭解並套用 Office 365 網路連線原則的詳細資訊, 請參閱[office 365 網路連線原則](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="8abf5-162">For more information on understanding and applying Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="conclusion"></a><span data-ttu-id="8abf5-163">總結</span><span class="sxs-lookup"><span data-stu-id="8abf5-163">Conclusion</span></span>

<span data-ttu-id="8abf5-164">優化 Office 365 網路效能實際上會降低移除不必要的障礙。</span><span class="sxs-lookup"><span data-stu-id="8abf5-164">Optimizing Office 365 network performance really comes down to removing unnecessary impediments.</span></span> <span data-ttu-id="8abf5-165">將 Office 365 連線視為信任的流量, 可防止資料包檢查和競爭的 proxy 頻寬帶來延遲。</span><span class="sxs-lookup"><span data-stu-id="8abf5-165">By treating Office 365 connections as trusted traffic, you can prevent latency from being introduced by packet inspection and competition for proxy bandwidth.</span></span> <span data-ttu-id="8abf5-166">允許用戶端機器與 Office 365 端點之間的本機連線可透過 Microsoft 全球網路動態路由傳送流量。</span><span class="sxs-lookup"><span data-stu-id="8abf5-166">Allowing local connections between client machines and Office 365 endpoints enables traffic to be dynamically routed through the Microsoft Global Network.</span></span>

## <a name="related-topics"></a><span data-ttu-id="8abf5-167">相關主題</span><span class="sxs-lookup"><span data-stu-id="8abf5-167">Related Topics</span></span>

[<span data-ttu-id="8abf5-168">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="8abf5-168">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="8abf5-169">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="8abf5-169">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

<span data-ttu-id="8abf5-170">[Office 365 URL 與 IP 位址範圍](urls-and-ip-address-ranges.md) (英文)</span><span class="sxs-lookup"><span data-stu-id="8abf5-170">[Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md)</span></span>

[<span data-ttu-id="8abf5-171">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="8abf5-171">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="8abf5-172">評估 Office 365 網路連線能力</span><span class="sxs-lookup"><span data-stu-id="8abf5-172">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="8abf5-173">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="8abf5-173">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="8abf5-174">評估 Office 365 網路連線能力</span><span class="sxs-lookup"><span data-stu-id="8abf5-174">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="8abf5-175">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="8abf5-175">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="8abf5-176">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="8abf5-176">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="8abf5-177">內容傳遞網路</span><span class="sxs-lookup"><span data-stu-id="8abf5-177">Content Delivery Networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="8abf5-178">Office 365 網路上架工具</span><span class="sxs-lookup"><span data-stu-id="8abf5-178">Office 365 Network Onboarding tool</span></span>](https://aka.ms/netonboard)

[<span data-ttu-id="8abf5-179">Microsoft 如何建立其快速且可靠的通用網路</span><span class="sxs-lookup"><span data-stu-id="8abf5-179">How Microsoft builds its fast and reliable global network</span></span>](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[<span data-ttu-id="8abf5-180">Office 365 網路博客</span><span class="sxs-lookup"><span data-stu-id="8abf5-180">Office 365 Networking blog</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
