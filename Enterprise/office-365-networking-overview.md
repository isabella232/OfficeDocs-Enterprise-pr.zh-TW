---
title: Office 365 網路連線概觀 （英文)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: 討論為何網路最佳化，務必 saas 和服務的目標的 Office 365 網路和 saas 和需要不同的網路中其他工作負載的方式。
ms.openlocfilehash: 4acaee86136c88e5ac5b3c795f594fb056d15204
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897206"
---
# <a name="office-365-network-connectivity-overview"></a><span data-ttu-id="77175-103">Office 365 網路連線概觀 （英文)</span><span class="sxs-lookup"><span data-stu-id="77175-103">Office 365 network connectivity overview</span></span>

<span data-ttu-id="77175-p101">Office 365 是提供透過各式各樣的微服務及應用程式的生產力和共同作業案例分散式的軟體為-a-服務 (SaaS) 雲端。例如 Outlook、 Word 及 PowerPoint 的 Office 365 的用戶端元件在使用者電腦上執行並連線至 Office 365 中 Microsoft 資料中心來執行其他元件。會決定的 Office 365 一般使用者經驗品質的最重要因素是網路可靠性與 Office 365 用戶端與 Office 365 服務前方門之間的低延遲。</span><span class="sxs-lookup"><span data-stu-id="77175-p101">Office 365 is a distributed Software-as-a-Service (SaaS) cloud that provides productivity and collaboration scenarios through a diverse set of micro-services and applications. Client components of Office 365 such as Outlook, Word and PowerPoint run on user computers and connect to other components of Office 365 that run in Microsoft datacenters. The most significant factor that determines the quality of the Office 365 end user experience is network reliability and low latency between Office 365 clients and Office 365 service front doors.</span></span>

<span data-ttu-id="77175-107">在本文中，您將了解 Office 365 網路、 目標與為什麼要選擇 Office 365 網路需要比一般網際網路流量最佳化的不同方法。</span><span class="sxs-lookup"><span data-stu-id="77175-107">In this article, you will learn about the goals of Office 365 networking, and why Office 365 networking requires a different approach to optimization than generic Internet traffic.</span></span>

## <a name="office-365-networking-goals"></a><span data-ttu-id="77175-108">Office 365 網路目標</span><span class="sxs-lookup"><span data-stu-id="77175-108">Office 365 networking goals</span></span>

<span data-ttu-id="77175-p102">Office 365 網路的最終目標是以啟用用戶端和最接近的 Office 365 端點之間的最低嚴格存取最佳化使用者經驗。一般使用者經驗品質直接相關的效能和回應使用者使用的應用程式。例如，Microsoft 小組依賴低延遲，讓使用者電話、 會議及共用] 畫面上共同作業雜音干擾的且 Outlook 依賴運用伺服器端索引與電腦控制的立即搜尋功能的更好的網路連線功能。</span><span class="sxs-lookup"><span data-stu-id="77175-p102">The ultimate goal of Office 365 networking is to optimize the end user experience by enabling the least restrictive access between clients and the closest Office 365 endpoints. The quality of end user experience is directly related to the performance and responsiveness of the application that the user is using. For example, Microsoft Teams relies on low latency so that user phone calls, conferences and shared screen collaborations are glitch-free, and Outlook relies on great networking connectivity for instant search features that leverage server-side indexing and AI capabilities.</span></span>

<span data-ttu-id="77175-p103">網路設計中的主要目標應該是以延遲降至最低降低的來回時間 (RTT) 從用戶端機器 Microsoft 通用網路、 連接 Microsoft 資料中心的所有具備低延遲的 Microsoft 的公用網路骨幹全球各地擴張高可用性雲端應用程式的進入點。您可以深入了解在[如何 Microsoft 是以其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)Microsoft 通用網路。</span><span class="sxs-lookup"><span data-stu-id="77175-p103">The primary goal in the network design should be to minimize latency by reducing the round-trip time (RTT) from client machines to the Microsoft Global Network, Microsoft's public network backbone that interconnects all of Microsoft's datacenters with low latency, high availability cloud application entry points spread around the world. You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="77175-p104">Office 365 網路效能最佳化不需要複雜。您可以遵循下列幾個主要原則來取得獲得最佳效能：</span><span class="sxs-lookup"><span data-stu-id="77175-p104">Optimizing Office 365 network performance doesn't need to be complicated. You can get the best possible performance by following a few key principles:</span></span>

- <span data-ttu-id="77175-116">確認 Office 365 網路流量</span><span class="sxs-lookup"><span data-stu-id="77175-116">Identify Office 365 network traffic</span></span>
- <span data-ttu-id="77175-117">允許網際網路的 Office 365 網路流量的本機分支輸出從每個使用者連線至 Office 365 的位置</span><span class="sxs-lookup"><span data-stu-id="77175-117">Allow local branch egress of Office 365 network traffic to the internet from each location where users connect to Office 365</span></span>
- <span data-ttu-id="77175-118">允許略過 proxy 和封包檢查裝置的 Office 365 流量</span><span class="sxs-lookup"><span data-stu-id="77175-118">Allow Office 365 traffic to bypass proxies and packet inspection devices</span></span>

<span data-ttu-id="77175-119">如需有關 Office 365 網路連線原則的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="77175-119">For more information on Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="traditional-network-architectures-and-saas"></a><span data-ttu-id="77175-120">傳統網路架構和 saas 和</span><span class="sxs-lookup"><span data-stu-id="77175-120">Traditional network architectures and SaaS</span></span>

<span data-ttu-id="77175-p105">用戶端和端點之間的流量不會將公司網路周邊網路外的假設周圍的設計被用用戶端/伺服器工作量的傳統網路架構原則。另外，許多的企業網路中所有輸出的網際網路連線周遊公司網路，並從集中位置的輸出。</span><span class="sxs-lookup"><span data-stu-id="77175-p105">Traditional network architecture principles for client/server workloads are designed around the assumption that traffic between clients and endpoints does not extend outside the corporate network perimeter. Also, in many enterprise networks, all outbound Internet connections traverse the corporate network, and egress from a central location.</span></span>

<span data-ttu-id="77175-p106">傳統網路架構中較高延遲的一般網際網路流量所需的取捨以維護網路周邊安全性，且網際網路流量的效能最佳化通常需要升級或向外延展在網路輸出點的設備。不過，這個方法並未涵蓋的 saas 和服務，例如 Office 365 的最佳網路效能的需求。</span><span class="sxs-lookup"><span data-stu-id="77175-p106">In traditional network architectures, higher latency for generic Internet traffic is a necessary tradeoff in order to maintain network perimeter security, and performance optimization for Internet traffic typically involves upgrading or scaling out the equipment at network egress points. However, this approach does not address the requirements for optimum network performance of SaaS services such as Office 365.</span></span>

## <a name="identifying-office-365-network-traffic"></a><span data-ttu-id="77175-125">用來識別 Office 365 網路流量</span><span class="sxs-lookup"><span data-stu-id="77175-125">Identifying Office 365 network traffic</span></span>

<span data-ttu-id="77175-126">我們正在進行容易識別 Office 365 網路流量，並使其成為簡化管理網路識別。</span><span class="sxs-lookup"><span data-stu-id="77175-126">We're making it easier to identify Office 365 network traffic and making it simpler to manage the network identification.</span></span>

- <span data-ttu-id="77175-p107">若要從網際網路延遲不會影響的網路流量區分極重要的網路流量的網路端點的新類別。有剛少數 Url 和最重要的"最佳化"類別中支援的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="77175-p107">New categories of network endpoints to differentiate highly critical network traffic from network traffic which is not impacted by Internet latencies. There are just a handful of URLs and supporting IP Addresses in the most critical “Optimize” category.</span></span>
- <span data-ttu-id="77175-p108">Web 服務的指令碼分派狀況] 或 [Office 365 的直接裝置組態和變更管理網路識別碼。變更可從 web 服務或 RSS 格式或使用 Microsoft 流程範本的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="77175-p108">Web services for script usage or direct device configuration and change management of Office 365 network identification. Changes are available from the web service, or in RSS format, or on email using a Microsoft Flow template.</span></span>
- <span data-ttu-id="77175-131">[Office 365 網路協力廠商程式](http://aka.ms/Office365NPP)與 Microsoft 協力廠商提供裝置或服務，請遵循 Office 365 網路連線準則而有簡單的設定。</span><span class="sxs-lookup"><span data-stu-id="77175-131">[Office 365 Network partner program](http://aka.ms/Office365NPP) with Microsoft partners who provide devices or services that follow Office 365 network connectivity principles and have simple configuration.</span></span>

## <a name="securing-office-365-connections"></a><span data-ttu-id="77175-132">保護 Office 365 的連線</span><span class="sxs-lookup"><span data-stu-id="77175-132">Securing Office 365 connections</span></span>

<span data-ttu-id="77175-p109">傳統網路安全性的目標是強化公司網路周邊對入侵和惡意入侵的狀況。大部分的企業網路強制執行網路使用 proxy 伺服器、 防火牆、 SSL 符號技術的網際網路流量的安全性和檢查、 深入的封包檢查及資料遺失防護系統。這些技術提供一般的網際網路要求降低重要的風險，但可大幅減少效能、 延展性及套用至 Office 365 端點時的使用者體驗的品質。</span><span class="sxs-lookup"><span data-stu-id="77175-p109">The goal of traditional network security is to harden the corporate network perimeter against intrusion and malicious exploits. Most enterprise networks enforce network security for Internet traffic using technologies like proxy servers, firewalls, SSL break and inspect, deep packet inspection, and data loss prevention systems. These technologies provide important risk mitigation for generic Internet requests but can dramatically reduce performance, scalability, and the quality of end user experience when applied to Office 365 endpoints.</span></span>

<span data-ttu-id="77175-p110">Office 365 有助於符合貴組織的需求內容安全性及資料流量規範與設計特別針對 Office 365 功能及工作負載的內建安全性和管理功能。如需 Office 365 安全性及規範的詳細資訊，請參閱[Office 365 安全性藍圖](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap)。多個執行進階層級處理程序在 Office 365 流量的進階的網路解決方案上關於 Microsoft 的建議及支援位置資訊，請參閱[使用協力廠商網路裝置或 Office 365 流量的解決方案](https://support.microsoft.com/en-us/help/2690045)。</span><span class="sxs-lookup"><span data-stu-id="77175-p110">Office 365 helps meet your organization's needs for content security and data usage compliance with built-in security and governance features designed specifically for Office 365 features and workloads. For more information about Office 365 security and compliance, see the [Office 365 security roadmap](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). For more information about Microsoft’s recommendations and support position on advanced network solutions that perform advanced-level processing on Office 365 traffic, see [Using third-party network devices or solutions on Office 365 traffic](https://support.microsoft.com/en-us/help/2690045).</span></span>

## <a name="why-is-office-365-networking-different"></a><span data-ttu-id="77175-139">為什麼要選擇 Office 365 網路不同？</span><span class="sxs-lookup"><span data-stu-id="77175-139">Why is Office 365 networking different?</span></span>

<span data-ttu-id="77175-p111">Office 365 的以達最佳效能使用端點安全性和加密的網路連線，以減少需要藉助周邊安全性強制作業的設計。Office 365 資料中心位於不同全球和服務的設計目的在於使用各種方法的用戶端連線到最佳可用的服務端點。由於使用者資料及處理會分散對齊許多 Microsoft 資料中心之間，有哪些用戶端可以連線機器沒有單一網路端點。事實上，資料與您的 Office 365 租用戶中的服務以動態方式最佳化 Microsoft 通用網路能否從中他們不時常存取的使用者的地理位置。</span><span class="sxs-lookup"><span data-stu-id="77175-p111">Office 365 is designed for optimal performance using endpoint security and encrypted network connections, reducing the need for perimeter security enforcement. Office 365 datacenters are located across the world and the service is designed to use various methods for connecting clients to best available service endpoints. Since user data and processing is distributed between many Microsoft datacenters, there is no single network endpoint to which client machines can connect. In fact, data and services in your Office 365 tenant are dynamically optimized by the Microsoft Global Network to adapt to the geographic locations from which they are accessed by end users.</span></span>

<span data-ttu-id="77175-144">在 Office 365 流量受限於封包檢查和集中式的輸出建立某些常見的效能問題：</span><span class="sxs-lookup"><span data-stu-id="77175-144">Certain common performance issues are created when Office 365 traffic is subject to packet inspection and centralized egress:</span></span>

- <span data-ttu-id="77175-145">高延遲可能會造成視訊和音訊資料流的效能非常不佳及資料擷取、 搜尋、 即時共同作業、 行事曆空閒/忙碌資訊、 產品中的內容及其他服務的速度過慢回應</span><span class="sxs-lookup"><span data-stu-id="77175-145">High latency can cause extremely poor performance of video and audio streams, and slow response of data retrieval, searches, real-time collaboration, calendar free/busy information, in-product content and other services</span></span>
- <span data-ttu-id="77175-146">Egressing 從集中管理位置擊敗動態路由功能之 Office 365 通用網路的連線、 新增延遲和來回時間</span><span class="sxs-lookup"><span data-stu-id="77175-146">Egressing connections from a central location defeats the dynamic routing capabilities of the Office 365 global network, adding latency and round-trip time</span></span>
- <span data-ttu-id="77175-147">解密 SSL 安全 Office 365 網路流量並重新加密它可能會造成通訊協定的錯誤與有安全性風險</span><span class="sxs-lookup"><span data-stu-id="77175-147">Decrypting SSL secured Office 365 network traffic and re-encrypting it can cause protocol errors and has security risk</span></span>

<span data-ttu-id="77175-p112">允許用戶端流量輸出至其地理位置盡關閉縮短 Office 365 的進入點的網路路徑可改善連線效能與使用者體驗 Office 365 中。它也可以協助減少對 Office 365 效能與可靠性的網路架構未來變更的影響。指定連線模型是永遠提供使用者的位置，不論是否將在公司網路或遠端位置，例如 home、 旅館、 咖啡廳及機場網路輸出。一般網際網路流量及 WAN 為主的公司網路流量會分別路由傳送與未使用本機直接輸出模式。在下圖表示此本機直接輸出模型。</span><span class="sxs-lookup"><span data-stu-id="77175-p112">Shortening the network path to Office 365 entry points by allowing client traffic to egress as close as possible to their geographic location can improve connectivity performance and the end user experience in Office 365. It can also help to reduce the impact of future changes to the network architecture on Office 365 performance and reliability. The optimum connectivity model is to always provide network egress at the user's location, regardless of whether this is on the corporate network or remote locations such as home, hotels, coffee shops and airports. Generic Internet traffic and WAN based corporate network traffic would be separately routed and not use the local direct egress model. This local direct egress model is represented in the diagram below.</span></span>

![本機輸出網路架構](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

<span data-ttu-id="77175-154">本機輸出架構會有下列優點針對 Office 365 的網路流量透過傳統模型：</span><span class="sxs-lookup"><span data-stu-id="77175-154">The local egress architecture has the following benefits for Office 365 network traffic over the traditional model:</span></span>
  
- <span data-ttu-id="77175-p113">提供 Office 365 的最佳效能最佳化路由長度。使用者連線動態路由傳送至最接近的 Office 365 進入點的 Microsoft 通用網路_分散式服務前方門_基礎結構、 和流量會路由傳送內部至資料和服務端點透過 Microsoft高可用性深色光纖極端低延遲。</span><span class="sxs-lookup"><span data-stu-id="77175-p113">Provides optimal Office 365 performance by optimizing route length. End user connections are dynamically routed to the nearest Office 365 entry point by the Microsoft Global Network's _Distributed Service Front Door_ infrastructure, and traffic is then routed internally to data and service endpoints over Microsoft's ultra-low latency high availability dark fiber.</span></span>
- <span data-ttu-id="77175-157">允許的 Office 365 流量，略過 proxy 和流量檢查裝置的本機輸出減少公司網路基礎結構的負載。</span><span class="sxs-lookup"><span data-stu-id="77175-157">Reduces the load on corporate network infrastructure by allowing local egress for Office 365 traffic, bypassing proxies and traffic inspection devices.</span></span>
- <span data-ttu-id="77175-158">利用用戶端端點的安全性與雲端安全性功能，避免應用程式的備援網路安全性技術保護兩端上的連線。</span><span class="sxs-lookup"><span data-stu-id="77175-158">Secures connections on both ends by leveraging client endpoint security and cloud security features, avoiding application of redundant network security technologies.</span></span>

> [!NOTE]
> <span data-ttu-id="77175-p114">_分散式服務前方門_基礎結構的 Microsoft 通用網路高度可用且擴充度佳的網路邊緣的地理位置分散的位置。它會終止使用者連線並有效率地將這些路由傳送 Microsoft 通用網路內。您可以深入了解在[如何 Microsoft 是以其快速且可靠的通用網路](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)Microsoft 通用網路。</span><span class="sxs-lookup"><span data-stu-id="77175-p114">The _Distributed Service Front Door_ infrastructure is the Microsoft Global Network's highly available and scalable network edge with geographically distributed locations. It terminates end user connections and efficiently routes them within the Microsoft Global Network. You can learn more about the Microsoft Global Network at [How Microsoft builds its fast and reliable global network](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).</span></span>

<span data-ttu-id="77175-162">如需詳細了解及套用 Office 365 網路連線原則的詳細資訊，請參閱[Office 365 網路連線原則](office-365-network-connectivity-principles.md)。</span><span class="sxs-lookup"><span data-stu-id="77175-162">For more information on understanding and applying Office 365 network connectivity principles, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="conclusion"></a><span data-ttu-id="77175-163">總結</span><span class="sxs-lookup"><span data-stu-id="77175-163">Conclusion</span></span>

<span data-ttu-id="77175-p115">Office 365 網路效能最佳化真正而言向下移除不必要的障礙。藉由將 Office 365 的連線視為信任的流量，您可以防止延遲所引進的封包檢查及 proxy 頻寬的競爭。允許用戶端機器與 Office 365 端點之間的本機連線可讓動態路由傳送到 Microsoft 通用網路流量。</span><span class="sxs-lookup"><span data-stu-id="77175-p115">Optimizing Office 365 network performance really comes down to removing unnecessary impediments. By treating Office 365 connections as trusted traffic, you can prevent latency from being introduced by packet inspection and competition for proxy bandwidth. Allowing local connections between client machines and Office 365 endpoints enables traffic to be dynamically routed through the Microsoft Global Network.</span></span>

## <a name="related-topics"></a><span data-ttu-id="77175-167">相關主題</span><span class="sxs-lookup"><span data-stu-id="77175-167">Related Topics</span></span>

[<span data-ttu-id="77175-168">Office 365 網路連線原則</span><span class="sxs-lookup"><span data-stu-id="77175-168">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="77175-169">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="77175-169">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="77175-170">管理 Office 365 端點</span><span class="sxs-lookup"><span data-stu-id="77175-170">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="77175-171">Office 365 IP 位址和 URL Web 服務</span><span class="sxs-lookup"><span data-stu-id="77175-171">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="77175-172">對 Office 365 的網路連線能力</span><span class="sxs-lookup"><span data-stu-id="77175-172">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="77175-173">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="77175-173">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="77175-174">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="77175-174">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="77175-175">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="77175-175">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="77175-176">Microsoft 如何建立其快速且可靠的通用網路</span><span class="sxs-lookup"><span data-stu-id="77175-176">How Microsoft builds its fast and reliable global network</span></span>](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
