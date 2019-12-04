---
title: 實作 ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: 適用於 Office 365 提供替代的路由路徑許多網際網路對向 Office 365 服務。 ExpressRoute for Office 365 的架構根據公告已可存取網際網路上插入到這些 IP 前置詞的後續重新發佈您佈建 ExpressRoute 電路的 Office 365 服務的公用 IP 電話首碼您的網路。 使用 ExpressRoute 有效率地啟用數個不同路由路徑，透過網際網路，以及透過 ExpressRoute，許多 Office 365 服務。 在您的網路路由此狀態可能代表了重大改變您的內部網路拓撲設計的方式。
ms.openlocfilehash: 0b200c3a7a54d28aee20b03c850c908bfd1c868d
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813481"
---
# <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="2503e-106">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="2503e-106">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="2503e-107">*本文適用於 Office 365 企業版和 Microsoft 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="2503e-107">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="2503e-108">適用於 Office 365 提供替代的路由路徑許多網際網路對向 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-108">ExpressRoute for Office 365 provides an alternate routing path to many internet facing Office 365 services.</span></span> <span data-ttu-id="2503e-109">ExpressRoute for Office 365 的架構根據公告已可存取網際網路上插入到這些 IP 前置詞的後續重新發佈您佈建 ExpressRoute 電路的 Office 365 服務的公用 IP 電話首碼您的網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-109">The architecture of ExpressRoute for Office 365 is based on advertising public IP prefixes of Office 365 services that are already accessible over the Internet into your provisioned ExpressRoute circuits for subsequent redistribution of those IP prefixes into your network.</span></span> <span data-ttu-id="2503e-110">使用 ExpressRoute 有效率地啟用數個不同路由路徑，透過網際網路，以及透過 ExpressRoute，許多 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-110">With ExpressRoute you effectively enable several different routing paths, through the internet and through ExpressRoute, for many Office 365 services.</span></span> <span data-ttu-id="2503e-111">在您的網路路由此狀態可能代表了重大改變您的內部網路拓撲設計的方式。</span><span class="sxs-lookup"><span data-stu-id="2503e-111">This state of routing on your network may represent a significant change to how your internal network topology is designed.</span></span>
  
 <span data-ttu-id="2503e-112">**狀態：** 完整指南 v2</span><span class="sxs-lookup"><span data-stu-id="2503e-112">**Status:** Complete Guide v2</span></span>
  
<span data-ttu-id="2503e-113">您必須謹慎規劃您 ExpressRoute for Office 365 實作以容納的需要使用路由插入核心網路和網際網路路由可透過這兩個專用的電路網路複雜性的。</span><span class="sxs-lookup"><span data-stu-id="2503e-113">You must carefully plan your ExpressRoute for Office 365 implementation to accommodate for the network complexities of having routing available via both a dedicated circuit with routes injected into your core network and the internet.</span></span> <span data-ttu-id="2503e-114">如果您和您的小組成員不執行詳細的規劃並測試本指南中，有高風險，您將遇到間歇性或總遺失連線至 Office 365 服務時啟用 ExpressRoute 線路。</span><span class="sxs-lookup"><span data-stu-id="2503e-114">If you and your team don't perform the detailed planning and testing in this guide, there is a high risk you'll experience intermittent or a total loss of connectivity to Office 365 services when the ExpressRoute circuit is enabled.</span></span>
  
<span data-ttu-id="2503e-115">若要讓成功實作，您必須分析您的基礎結構需求、 通過詳細的網路評估和設計、 仔細規劃導入分段且受控制的方式，及建立詳細的驗證和測試計劃。</span><span class="sxs-lookup"><span data-stu-id="2503e-115">To have a successful implementation, you will need to analyze your infrastructure requirements, go through detailed network assessment and design, carefully plan the rollout in a staged and controlled manner, and build a detailed validation and testing plan.</span></span> <span data-ttu-id="2503e-116">在大型、 分散的環境不常見看見 span 幾個月的實作。</span><span class="sxs-lookup"><span data-stu-id="2503e-116">For a large, distributed environment it's not uncommon to see implementations span several months.</span></span> <span data-ttu-id="2503e-117">本指南旨在協助您規劃。</span><span class="sxs-lookup"><span data-stu-id="2503e-117">This guide is designed to help you plan ahead.</span></span>
  
<span data-ttu-id="2503e-118">大型成功部署可能需要規劃的六個月及通常包括網路、 防火牆和 Proxy 伺服器系統管理員、 Office 365 系統管理員、 安全性、 使用者支援、 專案在組織中包含的許多層面的小組成員管理和主管贊助。</span><span class="sxs-lookup"><span data-stu-id="2503e-118">Large successful deployments may take six months in planning and often include team members from many areas in the organization including networking, Firewall and Proxy server administrators, Office 365 administrators, security, end-user support, project management, and executive sponsorship.</span></span> <span data-ttu-id="2503e-119">您在規劃程序的投資會降低您將遇到停機時間或複雜且最耗費成本疑難排解中所產生的部署失敗的可能性。</span><span class="sxs-lookup"><span data-stu-id="2503e-119">Your investment in the planning process will reduce the likelihood that you'll experience deployment failures resulting in downtime or complex and expensive troubleshooting.</span></span>
  
<span data-ttu-id="2503e-120">我們預期會啟動此實作指南之前完成下列先決條件。</span><span class="sxs-lookup"><span data-stu-id="2503e-120">We expect the following pre-requisites to be completed before this implementation guide is started.</span></span>
  
1. <span data-ttu-id="2503e-121">您已完成網路評估，以判斷 ExpressRoute 是否是建議，並核准。</span><span class="sxs-lookup"><span data-stu-id="2503e-121">You've completed a network assessment to determine if ExpressRoute is recommended and approved.</span></span>

2. <span data-ttu-id="2503e-122">您已選取的 ExpressRoute 網路服務提供者。</span><span class="sxs-lookup"><span data-stu-id="2503e-122">You've selected an ExpressRoute network service provider.</span></span> <span data-ttu-id="2503e-123">尋找關於[ExpressRoute 合作夥伴和對等位置](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2503e-123">Find details about the [ExpressRoute partners and peering locations](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span>

3. <span data-ttu-id="2503e-124">您已閱讀並瞭解[ExpressRoute 文件](https://azure.microsoft.com/documentation/services/expressroute/)和您的內部網路是能夠符合 ExpressRoute 先決條件端對端。</span><span class="sxs-lookup"><span data-stu-id="2503e-124">You've already read and understand the [ExpressRoute documentation](https://azure.microsoft.com/documentation/services/expressroute/) and your internal network is able to meet ExpressRoute pre-requisites end to end.</span></span>

4. <span data-ttu-id="2503e-125">您的小組具備讀取的所有公用的指導方針和文件[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)、 [https://aka.ms/ert](https://aka.ms/ert)，和保存的[Azure ExpressRoute for Office 365 訓練](https://channel9.msdn.com/series/aer)數列上 Channel 9，要如何因應了解的重要技術的詳細資訊，包括：</span><span class="sxs-lookup"><span data-stu-id="2503e-125">Your team has read all of the public guidance and documentation at [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert), and watched the [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to gain an understanding of critical technical details including:</span></span>

      - <span data-ttu-id="2503e-126">SaaS 服務網際網路相依性。</span><span class="sxs-lookup"><span data-stu-id="2503e-126">The internet dependencies of SaaS services.</span></span>

      - <span data-ttu-id="2503e-127">如何避免非對稱式路由及處理複雜路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-127">How to avoid asymmetric routes and handle complex routing.</span></span>

      - <span data-ttu-id="2503e-128">如何納入周邊安全性、 可用性及應用程式層級的控制項。</span><span class="sxs-lookup"><span data-stu-id="2503e-128">How to incorporate perimeter security, availability, and application level controls.</span></span>

## <a name="begin-by-gathering-requirements"></a><span data-ttu-id="2503e-129">首先請收集需求</span><span class="sxs-lookup"><span data-stu-id="2503e-129">Begin by gathering requirements</span></span>
<span data-ttu-id="2503e-130"><a name="requirements"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-130"></span></span>

<span data-ttu-id="2503e-131">首先，決定哪些功能和您打算採用您組織內的服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-131">Start by determining which features and services you plan to adopt within your organization.</span></span> <span data-ttu-id="2503e-132">您必須決定將使用不同的 Office 365 服務的功能和您網路上的位置將裝載人員使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="2503e-132">You need to determine which features of the different Office 365 services will be used and which locations on your network will host people using those features.</span></span> <span data-ttu-id="2503e-133">您需要將網路屬性 (attribute) 與目錄的案例中，每個這些案例需要;等輸入和輸出的網路流量流向 Office 365 端點是否可透過 ExpressRoute 與否。</span><span class="sxs-lookup"><span data-stu-id="2503e-133">With the catalog of scenarios, you need to add the network attributes that each of those scenarios require; such as inbound and outbound network traffic flows and if the Office 365 endpoints are available over ExpressRoute or not.</span></span>
  
<span data-ttu-id="2503e-134">收集貴組織的需求：</span><span class="sxs-lookup"><span data-stu-id="2503e-134">To gather your organization's requirements:</span></span>
  
- <span data-ttu-id="2503e-135">型錄，您的組織使用 Office 365 服務的輸入和輸出網路流量。</span><span class="sxs-lookup"><span data-stu-id="2503e-135">Catalog the inbound and outbound network traffic for the Office 365 services your organization is using.</span></span> <span data-ttu-id="2503e-136">如需不同 Office 365 案例需要的流量的說明，請參閱 Office 365 Url 和 IP 位址範圍] 頁面。</span><span class="sxs-lookup"><span data-stu-id="2503e-136">Consult Office 365 URLs and IP address ranges page for the description of flows that different Office 365 scenarios require.</span></span>

- <span data-ttu-id="2503e-137">收集現有顯示您的內部 WAN 骨幹和拓撲的詳細資料、 衛星站台，最後一個哩的使用者連線能力，路由傳送至網路周邊出口點和 proxy 服務連線的網路拓撲的文件。</span><span class="sxs-lookup"><span data-stu-id="2503e-137">Gather documentation of existing network topology showing details of your internal WAN backbone and topology, connectivity of satellite sites, last mile user connectivity, routing to network perimeter egress points, and proxy services.</span></span>

  - <span data-ttu-id="2503e-138">找出在 Office 365 和其他 Microsoft 服務會連線到，顯示網際網路和建議的 ExpressRoute 連線路徑的網路圖表上的輸入的服務端點。</span><span class="sxs-lookup"><span data-stu-id="2503e-138">Identify inbound service endpoints on the network diagrams that Office 365 and other Microsoft services will connect to, showing both internet and proposed ExpressRoute connection paths.</span></span>

  - <span data-ttu-id="2503e-139">找出所有地理使用者位置，以及哪些位置目前沒有通往網際網路和建議讓輸出至 ExpressRoute 對等位置的哪個位置的位置之間的 WAN 連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-139">Identify all geographic user locations and WAN connectivity between locations along with which locations currently have an egress to the internet and which locations are proposed to have an egress to an ExpressRoute peering location.</span></span>

  - <span data-ttu-id="2503e-140">找出所有的邊緣裝置，例如 proxy、 防火牆、 等等並型錄，其關係給分批 ExpressRoute 與網際網路的流量。</span><span class="sxs-lookup"><span data-stu-id="2503e-140">Identify all edge devices, such as proxies, firewalls, and so on and catalog their relationship to flows going over the Internet and ExpressRoute.</span></span>

  - <span data-ttu-id="2503e-141">文件是否使用者會存取 Office 365 服務透過直接路由或間接的應用程式 proxy 的網際網路和 ExpressRoute 流程。</span><span class="sxs-lookup"><span data-stu-id="2503e-141">Document whether end users will access Office 365 services via direct routing or indirect application proxy for both Internet and ExpressRoute flows.</span></span>

- <span data-ttu-id="2503e-142">新增您的租用戶的位置，且符合-我網狀圖的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-142">Add the location of your tenant and meet-me locations to your network diagram.</span></span>

- <span data-ttu-id="2503e-143">估計預期及觀察到的網路效能和延遲特性從主要使用者位置，複製到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2503e-143">Estimate the expected and observed network performance and latency characteristics from major user locations to Office 365.</span></span> <span data-ttu-id="2503e-144">請記住，Office 365 是一組通用且分散式的服務，使用者將連線到可能和其租用戶的位置不同的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-144">Keep in mind that Office 365 is a global and distributed set of services and users will be connecting to locations that may be different from the location of their tenant.</span></span> <span data-ttu-id="2503e-145">基於這個理由，建議測量和透過 ExpressRoute 和網際網路連線最佳化使用者與最接近的 Microsoft 全球網路邊緣之間的延遲。</span><span class="sxs-lookup"><span data-stu-id="2503e-145">For this reason, it is recommended to measure and optimize for latency between the user and the closest edge of Microsoft global network over ExpressRoute and Internet connections.</span></span> <span data-ttu-id="2503e-146">您可以使用從網路評估所發現的錯誤來完成這項作業幫助。</span><span class="sxs-lookup"><span data-stu-id="2503e-146">You can use your findings from the network assessment to aid with this task.</span></span>

- <span data-ttu-id="2503e-147">列出公司網路安全性及必須符合新的 ExpressRoute 連線的高可用性需求。</span><span class="sxs-lookup"><span data-stu-id="2503e-147">List company network security and high availability requirements that need to be met with the new ExpressRoute connection.</span></span> <span data-ttu-id="2503e-148">例如，如何使用者繼續以取得網際網路輸出或 ExpressRoute 線路失敗發生存取 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2503e-148">For example, how do users continue to get access to Office 365 in the event of the Internet egress or ExpressRoute circuit failure.</span></span>

- <span data-ttu-id="2503e-149">文件的輸入和輸出的 Office 365 網路流向會使用網際網路路徑，然後使用 ExpressRoute 的哪。</span><span class="sxs-lookup"><span data-stu-id="2503e-149">Document which inbound and outbound Office 365 network flows will use the Internet path and which will use ExpressRoute.</span></span> <span data-ttu-id="2503e-150">地理位置的使用者與您的內部網路拓撲的詳細資料的詳細規可能需要從一位使用者的位置到另一個不同的計劃。</span><span class="sxs-lookup"><span data-stu-id="2503e-150">The specifics of geographical locations of your users and details of your on-premises network topology may require the plan to be different from one user location to another.</span></span>

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a><span data-ttu-id="2503e-151">型錄，輸出和輸入網路流量</span><span class="sxs-lookup"><span data-stu-id="2503e-151">Catalog your outbound and inbound network traffic</span></span>
<span data-ttu-id="2503e-152"><a name="trafficCatalog"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-152"></span></span>

<span data-ttu-id="2503e-153">路由和其他網路複雜度降至最低，我們建議您只使用 ExpressRoute for Office 365 的網路流量流程前往透過專用連線由於法規需求或網路評估的結果所需。</span><span class="sxs-lookup"><span data-stu-id="2503e-153">To minimize routing and other network complexities, we recommend that you only use ExpressRoute for Office 365 for the network traffic flows that are required to go over a dedicated connection due to regulatory requirements or as the result of the network assessment.</span></span> <span data-ttu-id="2503e-154">此外，我們建議您為不同且不同階段實作專案的階段 ExpressRoute 路由和方法輸出和輸入網路流量的範圍。</span><span class="sxs-lookup"><span data-stu-id="2503e-154">Additionally, we recommend that you stage the scope of ExpressRoute routing and approach outbound and inbound network traffic flows as different and distinct stages of the implementation project.</span></span> <span data-ttu-id="2503e-155">部署 ExpressRoute for Office 365，只是使用者起始輸出的網路流量流向與跨網際網路的輸入的網路流量可協助控制增加拓撲複雜性和其他的 [的簡介風險中保留的非對稱路由的可能性。</span><span class="sxs-lookup"><span data-stu-id="2503e-155">Deploy ExpressRoute for Office 365 for just user initiated outbound network traffic flows and leave inbound network traffic flows across the Internet can help to control the increase in topological complexity and risks of introducing additional asymmetric routing possibilities.</span></span>
  
<span data-ttu-id="2503e-156">您的網路流量目錄應該包含您必須在內部網路與 Microsoft 之間的所有輸入和輸出網路連線的清單。</span><span class="sxs-lookup"><span data-stu-id="2503e-156">Your network traffic catalog should contain listings of all the inbound and outbound network connections that you'll have between your on-premises network and Microsoft.</span></span>
  
- <span data-ttu-id="2503e-157">輸出的網路流量是任何位置連線從您的內部部署環境，例如從起始內部用戶端或伺服器，與 Microsoft 服務的目的地的案例。</span><span class="sxs-lookup"><span data-stu-id="2503e-157">Outbound network traffic flows are any scenarios where a connection is initiated from your on-premises environment, such as from internal clients or servers, with a destination of the Microsoft services.</span></span> <span data-ttu-id="2503e-158">這些連線可能是 Office 365 直接或間接，例如當連線會通過 proxy 伺服器、 防火牆或其他網路裝置的路徑上至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2503e-158">These connections may be direct to Office 365 or indirect, such as when the connection goes through proxy servers, firewalls, or other networking devices on the path to Office 365.</span></span>

- <span data-ttu-id="2503e-159">輸入的網路流量流向是從 Microsoft cloud 初始連線是其中，內部部署主機任何案例。</span><span class="sxs-lookup"><span data-stu-id="2503e-159">Inbound network traffic flows are any scenarios where a connection is initiated from the Microsoft cloud to an on-premises host.</span></span> <span data-ttu-id="2503e-160">這些連線通常需要通過防火牆和客戶安全性原則需要外部起始之流向的其他安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2503e-160">These connections typically need to go through firewall and other security infrastructure that customer security policy requires for externally originated flows.</span></span>

<span data-ttu-id="2503e-161">請閱讀**確保路由對稱性來看**一節的文章[使用 ExpressRoute for Office 365 路由](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)至判斷哪些服務將會傳送的輸入的流量，並尋找在[Office 365 端點](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)參考文章，以判斷其餘的連線資訊中標示**ExpressRoute for Office 365**的資料行。</span><span class="sxs-lookup"><span data-stu-id="2503e-161">Read the **Ensuring route symmetry** section of the article [Routing with ExpressRoute for Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) to determine which services will send inbound traffic and look for the column marked **ExpressRoute for Office 365** in the [Office 365 endpoints](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) reference article to determine the rest of the connectivity information.</span></span>
  
<span data-ttu-id="2503e-162">每個服務所需的輸出連線，您會想要說明計劃的連線能力，包括網路路由、 proxy 組態、 封包檢查服務與頻寬需求。</span><span class="sxs-lookup"><span data-stu-id="2503e-162">For each service that requires an outbound connection, you'll want to describe the planned connectivity for the service including network routing, proxy configuration, packet inspection, and bandwidth needs.</span></span>
  
<span data-ttu-id="2503e-163">每個服務所需的輸入的連線，您需要一些額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="2503e-163">For each service that requires an inbound connection, you'll need some additional information.</span></span> <span data-ttu-id="2503e-164">Microsoft cloud 中的伺服器將會建立連線至您的內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-164">Servers in the Microsoft cloud will establish connections to your on-premises network.</span></span> <span data-ttu-id="2503e-165">若要確保正確地進行連線，您會想要說明此連線，包括; 的所有層面會接受這些輸入的連線服務的公用 DNS 項目，CIDR 格式化 IPv4 IP 位址，涉及哪些 ISP 設備，以及如何輸入的 NAT 或來源 NAT 處理這些連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-165">to ensure the connections are made correctly, you'll want to describe all aspects of this connectivity, including; the public DNS entries for the services that will accept these inbound connections, the CIDR formatted IPv4 IP addresses, which ISP equipment is involved, and how inbound NAT or source NAT is handled for these connections.</span></span>
  
<span data-ttu-id="2503e-166">輸入的連線應該檢閱不論是否他們透過網際網路連線，或以確保非對稱式路由的 ExpressRoute 尚未已引進。</span><span class="sxs-lookup"><span data-stu-id="2503e-166">Inbound connections should be reviewed regardless of whether they're connecting over the internet or ExpressRoute to ensure asymmetric routing hasn't been introduced.</span></span> <span data-ttu-id="2503e-167">在某些情況下，內部部署端點 Office 365 服務啟動的傳入的連線可以可能也需要由其他 Microsoft 與非 Microsoft 服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-167">In some cases, on-premises endpoints that Office 365 services initiate inbound connections to may also need to be accessed by other Microsoft and non-Microsoft services.</span></span> <span data-ttu-id="2503e-168">很重要，啟用 ExpressRoute 路由傳送至 Office 365 進行這些服務不會中斷其他案例。</span><span class="sxs-lookup"><span data-stu-id="2503e-168">It is paramount that enabling ExpressRoute routing to these services for Office 365 purposes doesn't break other scenarios.</span></span> <span data-ttu-id="2503e-169">在許多情況下，客戶可能需要實作特定變更他們的內部網路，例如來源基礎 NAT，以確保來自 Microsoft 的輸入的流量保持對稱，啟用 ExpressRoute 之後。</span><span class="sxs-lookup"><span data-stu-id="2503e-169">In many cases, customers may need to implement specific changes to their internal network, such as source based NAT, to ensure that inbound flows from Microsoft remain symmetric after ExpressRoute is enabled.</span></span>
  
<span data-ttu-id="2503e-170">以下是詳細資料所需的層級的範例。</span><span class="sxs-lookup"><span data-stu-id="2503e-170">Here's a sample of the level of detail required.</span></span> <span data-ttu-id="2503e-171">在此情況下 Exchange 混合式會透過 ExpressRoute 路由至內部部署系統。</span><span class="sxs-lookup"><span data-stu-id="2503e-171">In this case Exchange Hybrid would route to the on-premises system over ExpressRoute.</span></span>

|<span data-ttu-id="2503e-172">**Connection 屬性**</span><span class="sxs-lookup"><span data-stu-id="2503e-172">**Connection property**</span></span>|<span data-ttu-id="2503e-173">**值**</span><span class="sxs-lookup"><span data-stu-id="2503e-173">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2503e-174">**網路流量方向**</span><span class="sxs-lookup"><span data-stu-id="2503e-174">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="2503e-175">輸入</span><span class="sxs-lookup"><span data-stu-id="2503e-175">Inbound</span></span>  <br/> |
|<span data-ttu-id="2503e-176">**服務**</span><span class="sxs-lookup"><span data-stu-id="2503e-176">**Service**</span></span> <br/> |<span data-ttu-id="2503e-177">Exchange 混合式</span><span class="sxs-lookup"><span data-stu-id="2503e-177">Exchange Hybrid</span></span>  <br/> |
|<span data-ttu-id="2503e-178">**公用 Office 365 端點 （來源）**</span><span class="sxs-lookup"><span data-stu-id="2503e-178">**Public Office 365 endpoint (source)**</span></span> <br/> |<span data-ttu-id="2503e-179">Exchange Online （IP 位址）</span><span class="sxs-lookup"><span data-stu-id="2503e-179">Exchange Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="2503e-180">**公用內部端點 （目的地）**</span><span class="sxs-lookup"><span data-stu-id="2503e-180">**Public On-Premises Endpoint (destination)**</span></span> <br/> |<span data-ttu-id="2503e-181">5.5.5.5</span><span class="sxs-lookup"><span data-stu-id="2503e-181">5.5.5.5</span></span>  <br/> |
|<span data-ttu-id="2503e-182">**公用 （網際網路） DNS 項目**</span><span class="sxs-lookup"><span data-stu-id="2503e-182">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="2503e-183">Autodiscover.contoso.com</span><span class="sxs-lookup"><span data-stu-id="2503e-183">Autodiscover.contoso.com</span></span>  <br/> |
|<span data-ttu-id="2503e-184">**將此內部部署端點用於其他 (非 Office 365) 的 Microsoft 服務**</span><span class="sxs-lookup"><span data-stu-id="2503e-184">**Will this on-premises endpoint be used for by other (non-Office 365) Microsoft services**</span></span> <br/> |<span data-ttu-id="2503e-185">否</span><span class="sxs-lookup"><span data-stu-id="2503e-185">No</span></span>  <br/> |
|<span data-ttu-id="2503e-186">**將此內部部署端點可供網際網路上的使用者/系統**</span><span class="sxs-lookup"><span data-stu-id="2503e-186">**Will this on-premises endpoint be used by users/systems on the Internet**</span></span> <br/> |<span data-ttu-id="2503e-187">是</span><span class="sxs-lookup"><span data-stu-id="2503e-187">Yes</span></span>  <br/> |
|<span data-ttu-id="2503e-188">**透過公用的端點發佈的內部系統**</span><span class="sxs-lookup"><span data-stu-id="2503e-188">**Internal systems published through public endpoints**</span></span> <br/> |<span data-ttu-id="2503e-189">Exchange Server 用戶端存取角色 （內部） 192.168.101、 192.168.102、 192.168.103</span><span class="sxs-lookup"><span data-stu-id="2503e-189">Exchange Server client access role (on-premises) 192.168.101, 192.168.102, 192.168.103</span></span>  <br/> |
|<span data-ttu-id="2503e-190">**IP 通告的公開端點**</span><span class="sxs-lookup"><span data-stu-id="2503e-190">**IP advertisement of the public endpoint**</span></span> <br/> |<span data-ttu-id="2503e-191">**網際網路**： 5.5.0.0/16</span><span class="sxs-lookup"><span data-stu-id="2503e-191">**To Internet**: 5.5.0.0/16</span></span>  <br/> <span data-ttu-id="2503e-192">**以 ExpressRoute**: 5.5.5.0/24</span><span class="sxs-lookup"><span data-stu-id="2503e-192">**To ExpressRoute**: 5.5.5.0/24</span></span>  <br/> |
|<span data-ttu-id="2503e-193">**安全性/周邊控制項**</span><span class="sxs-lookup"><span data-stu-id="2503e-193">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="2503e-194">**網際網路路徑**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="2503e-194">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="2503e-195">**ExpressRoute 路徑**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="2503e-195">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="2503e-196">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="2503e-196">**High Availability**</span></span> <br/> |<span data-ttu-id="2503e-197">主動/主動跨 2 異地備援</span><span class="sxs-lookup"><span data-stu-id="2503e-197">Active/Active across 2 geo-redundant</span></span>  <br/> <span data-ttu-id="2503e-198">ExpressRoute 電路-芝加哥與 Dallas</span><span class="sxs-lookup"><span data-stu-id="2503e-198">ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="2503e-199">**路徑對稱性來看控制項**</span><span class="sxs-lookup"><span data-stu-id="2503e-199">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="2503e-200">**方法**： 來源 NAT</span><span class="sxs-lookup"><span data-stu-id="2503e-200">**Method**: Source NAT</span></span>  <br/> <span data-ttu-id="2503e-201">**網際網路路徑**： 來源 NAT 輸入 192.168.5.5 的連線</span><span class="sxs-lookup"><span data-stu-id="2503e-201">**Internet path**: Source NAT inbound connections to 192.168.5.5</span></span>  <br/> |<span data-ttu-id="2503e-202">**ExpressRoute 路徑**： 192.168.1.0 （芝加哥） 與 192.168.2.0 (Dallas) 的來源 NAT 連線</span><span class="sxs-lookup"><span data-stu-id="2503e-202">**ExpressRoute path**: Source NAT connections to 192.168.1.0 (Chicago) and 192.168.2.0 (Dallas)</span></span>  <br/> |

<span data-ttu-id="2503e-203">以下是一種服務，只有輸出範例：</span><span class="sxs-lookup"><span data-stu-id="2503e-203">Here's a sample of a service that is outbound only:</span></span>

|<span data-ttu-id="2503e-204">**Connection 屬性**</span><span class="sxs-lookup"><span data-stu-id="2503e-204">**Connection property**</span></span>|<span data-ttu-id="2503e-205">**值**</span><span class="sxs-lookup"><span data-stu-id="2503e-205">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2503e-206">**網路流量方向**</span><span class="sxs-lookup"><span data-stu-id="2503e-206">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="2503e-207">輸出</span><span class="sxs-lookup"><span data-stu-id="2503e-207">Outbound</span></span>  <br/> |
|<span data-ttu-id="2503e-208">**服務**</span><span class="sxs-lookup"><span data-stu-id="2503e-208">**Service**</span></span> <br/> |<span data-ttu-id="2503e-209">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2503e-209">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="2503e-210">**內部部署端點 （來源）**</span><span class="sxs-lookup"><span data-stu-id="2503e-210">**On-premises endpoint (source)**</span></span> <br/> |<span data-ttu-id="2503e-211">使用者工作站</span><span class="sxs-lookup"><span data-stu-id="2503e-211">User workstation</span></span>  <br/> |
|<span data-ttu-id="2503e-212">**公用 Office 365 端點 （目的地）**</span><span class="sxs-lookup"><span data-stu-id="2503e-212">**Public Office 365 endpoint (destination)**</span></span> <br/> |<span data-ttu-id="2503e-213">SharePoint Online （IP 位址）</span><span class="sxs-lookup"><span data-stu-id="2503e-213">SharePoint Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="2503e-214">**公用 （網際網路） DNS 項目**</span><span class="sxs-lookup"><span data-stu-id="2503e-214">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="2503e-215">\*。 sharepoint.com （和其他 Fqdn）</span><span class="sxs-lookup"><span data-stu-id="2503e-215">\*.sharepoint.com (and additional FQDNs)</span></span>  <br/> |
|<span data-ttu-id="2503e-216">**CDN 轉介**</span><span class="sxs-lookup"><span data-stu-id="2503e-216">**CDN Referrals**</span></span> <br/> |<span data-ttu-id="2503e-217">cdn.sharepointonline.com （和其他 Fqdn）-CDN 提供者所維護的 IP 位址)</span><span class="sxs-lookup"><span data-stu-id="2503e-217">cdn.sharepointonline.com (and additional FQDNs) - IP addresses maintained by CDN providers)</span></span>  <br/> |
|<span data-ttu-id="2503e-218">**IP 廣告和使用中的 NAT**</span><span class="sxs-lookup"><span data-stu-id="2503e-218">**IP advertisement and NAT in use**</span></span> <br/> |<span data-ttu-id="2503e-219">**網際網路路徑/來源 NAT**: 1.1.1.0/24</span><span class="sxs-lookup"><span data-stu-id="2503e-219">**Internet path/Source NAT**: 1.1.1.0/24</span></span>  <br/> <span data-ttu-id="2503e-220">**ExpressRoute 路徑/來源 NAT**: 1.1.2.0/24 （芝加哥） 和 1.1.3.0/24 (Dallas)</span><span class="sxs-lookup"><span data-stu-id="2503e-220">**ExpressRoute path/Source NAT**: 1.1.2.0/24 (Chicago) and 1.1.3.0/24 (Dallas)</span></span>  <br/> |
|<span data-ttu-id="2503e-221">**連線方法**</span><span class="sxs-lookup"><span data-stu-id="2503e-221">**Connectivity method**</span></span> <br/> |<span data-ttu-id="2503e-222">**網際網路**： 透過第 7 層 proxy （.pac 檔案）</span><span class="sxs-lookup"><span data-stu-id="2503e-222">**Internet**: via layer 7 proxy (.pac file)</span></span>  <br/> <span data-ttu-id="2503e-223">**ExpressRoute**： 直接路由 (沒有 proxy)</span><span class="sxs-lookup"><span data-stu-id="2503e-223">**ExpressRoute**: direct routing (no proxy)</span></span>  <br/> |
|<span data-ttu-id="2503e-224">**安全性/周邊控制項**</span><span class="sxs-lookup"><span data-stu-id="2503e-224">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="2503e-225">**網際網路路徑**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="2503e-225">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="2503e-226">**ExpressRoute 路徑**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="2503e-226">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="2503e-227">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="2503e-227">**High Availability**</span></span> <br/> |<span data-ttu-id="2503e-228">**網際網路路徑**： 備援網際網路輸出</span><span class="sxs-lookup"><span data-stu-id="2503e-228">**Internet path**: Redundant internet egress</span></span>  <br/> <span data-ttu-id="2503e-229">**ExpressRoute 路徑**： 主動/主動 '作用馬鈴薯' 路由跨 2 異地備援的 ExpressRoute 電路-芝加哥與 Dallas</span><span class="sxs-lookup"><span data-stu-id="2503e-229">**ExpressRoute path**: Active/Active 'hot potato' routing across 2 geo-redundant ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="2503e-230">**路徑對稱性來看控制項**</span><span class="sxs-lookup"><span data-stu-id="2503e-230">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="2503e-231">**方法**： 來源的所有連線的 NAT</span><span class="sxs-lookup"><span data-stu-id="2503e-231">**Method**: Source NAT for all connections</span></span>  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a><span data-ttu-id="2503e-232">您的網路拓撲設計，區域的連線</span><span class="sxs-lookup"><span data-stu-id="2503e-232">Your network topology design with regional connectivity</span></span>
<span data-ttu-id="2503e-233"><a name="topology"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-233"></span></span>

<span data-ttu-id="2503e-234">一旦您了解 services 和其相關聯的網路流量流程，您可以建立網狀圖，各有這些新的連線能力需求，並且說明您要使用 ExpressRoute for Office 365 進行的變更。</span><span class="sxs-lookup"><span data-stu-id="2503e-234">Once you understand the services and their associated network traffic flows, you can create a network diagram that incorporates these new connectivity requirements and illustrates the changes you'll make to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="2503e-235">您的圖表應包含：</span><span class="sxs-lookup"><span data-stu-id="2503e-235">Your diagram should include:</span></span>
  
1. <span data-ttu-id="2503e-236">其中從存取 Office 365 和其他服務的所有使用者位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-236">All user locations where Office 365 and other services will be accessed from.</span></span>

2. <span data-ttu-id="2503e-237">所有的網際網路和 ExpressRoute 出口點。</span><span class="sxs-lookup"><span data-stu-id="2503e-237">All internet and ExpressRoute egress points.</span></span>

3. <span data-ttu-id="2503e-238">所有輸出和輸入裝置管理內部和外部網路，包括路由器、 防火牆、 應用程式 proxy 伺服器，以及入侵偵測/防護的連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-238">All outbound and inbound devices that manage connectivity in and out of the network, including routers, firewalls, application proxy servers, and intrusion detection/prevention.</span></span>

4. <span data-ttu-id="2503e-239">所有的輸入流量，例如接受來自 ADFS 連線的內部 ADFS 伺服器的內部目的地 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2503e-239">Internal destinations for all inbound traffic, such as internal ADFS servers that accept connections from the ADFS web application proxy servers.</span></span>

5. <span data-ttu-id="2503e-240">會通告的所有 IP 子網路的型錄</span><span class="sxs-lookup"><span data-stu-id="2503e-240">Catalog of all IP subnets that will be advertised</span></span>

6. <span data-ttu-id="2503e-241">識別人員會存取來自 Office 365 和列出符合每個位置-我將使用 ExpressRoute 的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-241">Identify each location where people will access Office 365 from and list the meet-me locations that will be used for ExpressRoute.</span></span>

7. <span data-ttu-id="2503e-242">位置和您的內部網路拓撲，其中會接受來自 ExpressRoute 學到 Microsoft IP 前置詞，部分的過濾並傳播至。</span><span class="sxs-lookup"><span data-stu-id="2503e-242">Locations and portions of your internal network topology, where Microsoft IP prefixes learned from ExpressRoute will be accepted, filtered and propagated to.</span></span>

8. <span data-ttu-id="2503e-243">網路拓撲應說明每個網路區段的地理位置，以及如何連線至 Microsoft network 透過 ExpressRoute 及/或網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-243">The network topology should illustrate the geographic location of each network segment and how it connects to the Microsoft network over ExpressRoute and/or the Internet.</span></span>

<span data-ttu-id="2503e-244">下方圖表顯示每個位置其中人員將會使用從 Office 365 與 Office 365 的輸入和輸出路由廣告。</span><span class="sxs-lookup"><span data-stu-id="2503e-244">The diagram below shows each location where people will be using Office 365 from along with the inbound and outbound routing advertisements to Office 365.</span></span>
  
![ExpressRoute 區域地理符合-我](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
<span data-ttu-id="2503e-246">輸出的流量，人員存取 Office 365 中有三種：</span><span class="sxs-lookup"><span data-stu-id="2503e-246">For outbound traffic, the people access Office 365 in one of three ways:</span></span>
  
1. <span data-ttu-id="2503e-247">透過 meet-我中 「 北美地區 」 中的人員加州的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-247">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="2503e-248">透過 meet-我香港] 中的位置中的人員香港。</span><span class="sxs-lookup"><span data-stu-id="2503e-248">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="2503e-249">透過孟加拉其中有較少的人員，且沒有 ExpressRoute 線路佈建在網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-249">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
<span data-ttu-id="2503e-251">同樣地，從 Office 365 的輸入的網路流量會傳回下列三種方式之一：</span><span class="sxs-lookup"><span data-stu-id="2503e-251">Similarly, the inbound network traffic from Office 365 returns in one of three ways:</span></span>
  
1. <span data-ttu-id="2503e-252">透過 meet-我中 「 北美地區 」 中的人員加州的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-252">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="2503e-253">透過 meet-我香港] 中的位置中的人員香港。</span><span class="sxs-lookup"><span data-stu-id="2503e-253">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="2503e-254">透過孟加拉其中有較少的人員，且沒有 ExpressRoute 線路佈建在網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-254">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![輸入的連線的區域圖](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a><span data-ttu-id="2503e-256">決定適當的符合-我的位置</span><span class="sxs-lookup"><span data-stu-id="2503e-256">Determine the appropriate meet-me location</span></span>

<span data-ttu-id="2503e-257">符合選取範圍-我的位置，也就是其中 ExpressRoute 線路連接至 Microsoft 網路的網路的實體位置，會受到其中人員會存取來自 Office 365 的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-257">The selection of meet-me locations, which are the physical location where your ExpressRoute circuit connects your network to the Microsoft network, is influenced by the locations where people will access Office 365 from.</span></span> <span data-ttu-id="2503e-258">為提供 SaaS，Office 365 不會運作 IaaS 或 PaaS 地區模型下 Azure 沒有相同的方式。</span><span class="sxs-lookup"><span data-stu-id="2503e-258">As a SaaS offering, Office 365 does not operate under the IaaS or PaaS regional model in the same way Azure does.</span></span> <span data-ttu-id="2503e-259">相反地，Office 365 是分散式的一組共同作業服務，使用者可能需要跨多個資料中心和區域，這可能不一定是相同的位置或主控使用者的租用戶的區域中連接至端點。</span><span class="sxs-lookup"><span data-stu-id="2503e-259">Instead, Office 365 is a distributed set of collaboration services, where users may need to connect to endpoints across multiple datacenters and regions, which may not necessarily be in the same location or region where the user's tenant is hosted.</span></span>
  
<span data-ttu-id="2503e-260">這表示您必須先選取符合時的最重要考量-我的 ExpressRoute for Office 365 的位置是在您的組織中的人員從的連接位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-260">This means the most important consideration you need to make when selecting meet-me locations for ExpressRoute for Office 365 is where the people in your organization will be connecting from.</span></span> <span data-ttu-id="2503e-261">一般建議的最佳的 Office 365 連線是實作路由，使 Office 365 服務的使用者要求會交由關閉成 Microsoft 網路的最短的網路路徑，這通常也會被稱為 '作用馬鈴薯' 路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-261">The general recommendation for optimal Office 365 connectivity is implement routing, so that user requests to Office 365 services are handed off into the Microsoft network over the shortest network path, this is also often being referred to as 'hot potato' routing.</span></span> <span data-ttu-id="2503e-262">例如，如果大部分的 Office 365 使用者在一或兩個位置中，選取 [符合-我最接近的鄰近，以這些使用者的位置中的位置會建立最佳的設計。</span><span class="sxs-lookup"><span data-stu-id="2503e-262">For example, if most of the Office 365 users are in one or two locations, selecting meet-me locations that are in the closest proximity to the location of those users will create the optimal design.</span></span> <span data-ttu-id="2503e-263">如果貴公司有大量的使用者人數許多不同的區域中，您可能要考慮建立多個 ExpressRoute 電路符合-我的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-263">If your company has large user populations in many different regions, you may want to consider having multiple ExpressRoute circuits and meet-me locations.</span></span> <span data-ttu-id="2503e-264">針對某些您使用者的位置，到 Microsoft 網路和 Office 365 的最短/最最佳路徑可能無法透過您內部的 WAN 和 ExpressRoute 符合-我點，但是透過網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-264">For some of your user locations, the shortest/most optimal path into Microsoft network and Office 365, may not be through your internal WAN and ExpressRoute meet-me points, but via the Internet.</span></span>
  
<span data-ttu-id="2503e-265">通常時間有多個符合-我無法選取與您的使用者的相對近似值區域內的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-265">Often times, there are multiple meet-me locations that could be selected within a region with relative proximity to your users.</span></span> <span data-ttu-id="2503e-266">填寫下列表格來引導您決策。</span><span class="sxs-lookup"><span data-stu-id="2503e-266">Fill out the following table to guide your decisions.</span></span>

|<span data-ttu-id="2503e-267">**計劃的 ExpressRoute 符合-我加州和 New York 中的位置**</span><span class="sxs-lookup"><span data-stu-id="2503e-267">**Planned ExpressRoute meet-me locations in California and New York**</span></span>||
|:-----|:-----|
|<span data-ttu-id="2503e-268">位置</span><span class="sxs-lookup"><span data-stu-id="2503e-268">Location</span></span>  <br/> |<span data-ttu-id="2503e-269">人數</span><span class="sxs-lookup"><span data-stu-id="2503e-269">Number of people</span></span>  <br/> |<span data-ttu-id="2503e-270">透過網際網路輸出預期 Microsoft 網路延遲</span><span class="sxs-lookup"><span data-stu-id="2503e-270">Expected latency to Microsoft network over Internet egress</span></span>  <br/> |<span data-ttu-id="2503e-271">預期的延遲，Microsoft 網路，透過 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2503e-271">Expected latency to Microsoft network over ExpressRoute</span></span>  <br/> |
|<span data-ttu-id="2503e-272">Los Angeles</span><span class="sxs-lookup"><span data-stu-id="2503e-272">Los Angeles</span></span>  <br/> |<span data-ttu-id="2503e-273">10,000</span><span class="sxs-lookup"><span data-stu-id="2503e-273">10,000</span></span>  <br/> |<span data-ttu-id="2503e-274">~ 15ms</span><span class="sxs-lookup"><span data-stu-id="2503e-274">~15ms</span></span>  <br/> |<span data-ttu-id="2503e-275">~ 10 毫秒 （透過矽谷）</span><span class="sxs-lookup"><span data-stu-id="2503e-275">~10ms (via Silicon Valley)</span></span>  <br/> |
|<span data-ttu-id="2503e-276">華盛頓 DC</span><span class="sxs-lookup"><span data-stu-id="2503e-276">Washington DC</span></span>  <br/> |<span data-ttu-id="2503e-277">15,000</span><span class="sxs-lookup"><span data-stu-id="2503e-277">15,000</span></span>  <br/> |<span data-ttu-id="2503e-278">~ 20 毫秒</span><span class="sxs-lookup"><span data-stu-id="2503e-278">~20ms</span></span>  <br/> |<span data-ttu-id="2503e-279">~ 10 毫秒 （透過 New York)</span><span class="sxs-lookup"><span data-stu-id="2503e-279">~10ms (via New York)</span></span>  <br/> |
|<span data-ttu-id="2503e-280">Dallas</span><span class="sxs-lookup"><span data-stu-id="2503e-280">Dallas</span></span>  <br/> |<span data-ttu-id="2503e-281">5,000</span><span class="sxs-lookup"><span data-stu-id="2503e-281">5,000</span></span>  <br/> |<span data-ttu-id="2503e-282">~ 15ms</span><span class="sxs-lookup"><span data-stu-id="2503e-282">~15ms</span></span>  <br/> |<span data-ttu-id="2503e-283">~ 40ms （透過 New York)</span><span class="sxs-lookup"><span data-stu-id="2503e-283">~40ms (via New York)</span></span>  <br/> |

<span data-ttu-id="2503e-284">一旦顯示 Office 365 地區的全球網路架構，ExpressRoute 的網路服務提供者符合-我已開發位置，以及由位置的人員數量，它可以用來識別是否可以進行任何最佳化。</span><span class="sxs-lookup"><span data-stu-id="2503e-284">Once the global network architecture showing the Office 365 region, ExpressRoute network service provider meet-me locations, and the quantity of people by location has been developed, it can be used to identify if any optimizations can be made.</span></span> <span data-ttu-id="2503e-285">它也可以顯示全域髮夾網路連線其中流量路由傳送到遠端位置以取得符合-我的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-285">It may also show global hairpin network connections where traffic routes to a distant location in order to get the meet-me location.</span></span> <span data-ttu-id="2503e-286">如果在全球網路髮夾找到它應該進行修復才能繼續執行。</span><span class="sxs-lookup"><span data-stu-id="2503e-286">If a hairpin on the global network is discovered it should be remediated before continuing.</span></span> <span data-ttu-id="2503e-287">尋找另一個符合-我的位置或使用選擇性網際網路上下文出口點，以避免發生髮夾。</span><span class="sxs-lookup"><span data-stu-id="2503e-287">Either find another meet-me location, or use selective Internet breakout egress points to avoid the hairpin.</span></span>
  
<span data-ttu-id="2503e-288">第一個圖表中，「 北美地區 」 中顯示兩個實體位置與客戶的範例。</span><span class="sxs-lookup"><span data-stu-id="2503e-288">The first diagram, shows an example of a customer with two physical locations in North America.</span></span> <span data-ttu-id="2503e-289">您可以看到的資訊辦公室的位置，Office 365 租用戶的位置，以及 ExpressRoute 的幾種選擇符合-我的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-289">You can see the information about office locations, Office 365 tenant locations, and several choices for ExpressRoute meet-me locations.</span></span> <span data-ttu-id="2503e-290">在這個範例中，客戶已選取符合-我位置根據兩個原則，順序：</span><span class="sxs-lookup"><span data-stu-id="2503e-290">In this example, the customer has selected the meet-me location based on two principles, in order:</span></span>
  
1. <span data-ttu-id="2503e-291">最接近接近其組織中的人員。</span><span class="sxs-lookup"><span data-stu-id="2503e-291">Closest proximity to the people in their organization.</span></span>

2. <span data-ttu-id="2503e-292">最接近中 Microsoft 資料中心主控 Office 365 的近似值。</span><span class="sxs-lookup"><span data-stu-id="2503e-292">Closest in proximity to a Microsoft datacenter where Office 365 is hosted.</span></span>

![ExpressRoute 美國地理符合-我](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
<span data-ttu-id="2503e-294">稍微擴充此概念進一步範例跨國客戶面臨類似的資訊和決策第二個圖顯示。</span><span class="sxs-lookup"><span data-stu-id="2503e-294">Expanding this concept slightly further, the second diagram shows an example multi-national customer faced with similar information and decision making.</span></span> <span data-ttu-id="2503e-295">此客戶有中孟加拉十個人員著重於得其使用量的區域中的小型小組使用小型的 office。</span><span class="sxs-lookup"><span data-stu-id="2503e-295">This customer has a small office in Bangladesh with only a small team of ten people focused on growing their footprint in the region.</span></span> <span data-ttu-id="2503e-296">沒有符合-我辰內和 Microsoft 資料中心與 Office 365 中的位置中裝載辰內因此符合-我的位置就能明白;不過，十個人員，是各家其他電路費用。</span><span class="sxs-lookup"><span data-stu-id="2503e-296">There is a meet-me location in Chennai and a Microsoft datacenter with Office 365 hosted in Chennai so a meet-me location would make sense; however, for ten people, the expense of the additional circuit is burdensome.</span></span> <span data-ttu-id="2503e-297">為您查看您的網路時，您需要決定是否比消費以取得其他 ExpressRoute 線路首都更有效參與您網路上傳送您的網路流量的延遲。</span><span class="sxs-lookup"><span data-stu-id="2503e-297">As you look at your network, you'll need to determine if the latency involved in sending your network traffic across your network is more effective than spending the capital to acquire another ExpressRoute circuit.</span></span>
  
<span data-ttu-id="2503e-298">或者，在孟加拉十個人員可能會遇到更好的效能其比會在他們的內部網路上中路由，我們示範簡介圖表及重現時，透過網際網路傳送至 Microsoft 網路的網路流量下面。</span><span class="sxs-lookup"><span data-stu-id="2503e-298">Alternatively, the ten people in Bangladesh may experience better performance with their network traffic sent over the internet to the Microsoft network than they would routing on their internal network as we showed in the introductory diagrams and reproduced below.</span></span>
  
![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a><span data-ttu-id="2503e-300">建立您 ExpressRoute for Office 365 實作計劃</span><span class="sxs-lookup"><span data-stu-id="2503e-300">Create your ExpressRoute for Office 365 implementation plan</span></span>
<span data-ttu-id="2503e-301"><a name="implementation"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-301"></span></span>

<span data-ttu-id="2503e-302">您實作計劃應該包含這兩種技術的詳細資訊設定 ExpressRoute，以及設定所有其他基礎結構上您的網路，如下所示的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2503e-302">Your implementation plan should encompass both the technical details of configuring ExpressRoute as well as the details of configuring all the other infrastructure on your network, such as the following.</span></span>
  
- <span data-ttu-id="2503e-303">規劃 ExpressRoute 與網際網路之間分割的服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-303">Plan which services split between ExpressRoute and Internet.</span></span>

- <span data-ttu-id="2503e-304">規劃頻寬、 安全性、 高可用性和容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="2503e-304">Plan for bandwidth, security, high availability and failover.</span></span>

- <span data-ttu-id="2503e-305">設計輸入和輸出路由，包括適當的不同位置的路由路徑最佳化</span><span class="sxs-lookup"><span data-stu-id="2503e-305">Design inbound and outbound routing, including proper routing path optimizations for different locations</span></span>

- <span data-ttu-id="2503e-306">決定 ExpressRoute 路由傳送到您網路的通告花費多少時間以及 「 什麼是以選取 [網際網路] 或 [ExpressRoute 路徑; 用戶端的機制例如，直接路由或應用程式 proxy。</span><span class="sxs-lookup"><span data-stu-id="2503e-306">Decide how far ExpressRoute routes will be advertised into your network and what is the mechanism for clients to select Internet or ExpressRoute path; for example, direct routing or application proxy.</span></span>

- <span data-ttu-id="2503e-307">規劃 DNS 記錄的變更，包括[寄件者原則架構](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx)項目。</span><span class="sxs-lookup"><span data-stu-id="2503e-307">Plan DNS record changes, including [Sender Policy Framework](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) entries.</span></span>

- <span data-ttu-id="2503e-308">規劃 NAT 策略包括輸出和輸入來源 nat。</span><span class="sxs-lookup"><span data-stu-id="2503e-308">Plan NAT strategy including outbound and inbound source NAT.</span></span>

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a><span data-ttu-id="2503e-309">規劃您的路由與網際網路和 ExpressRoute 的網路路徑</span><span class="sxs-lookup"><span data-stu-id="2503e-309">Plan your routing with both internet and ExpressRoute network paths</span></span>
<span data-ttu-id="2503e-310"><a name="paths"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-310"></span></span>

- <span data-ttu-id="2503e-311">初始部署，所有輸入的服務，例如內送電子郵件或混合式連線，建議使用網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-311">For your initial deployment, all inbound services, such as inbound email or hybrid connectivity, are recommended to use the internet.</span></span>

- <span data-ttu-id="2503e-312">規劃使用者用戶端 LAN 路由，例如[設定 PAC/WPAD 檔案](https://aka.ms/manageo365endpoints)、 預設路由，proxy 伺服器及 BGP 路由廣告。</span><span class="sxs-lookup"><span data-stu-id="2503e-312">Plan end user client LAN routing, such as [configuring a PAC/WPAD file](https://aka.ms/manageo365endpoints), default route, proxy servers, and BGP route advertisements.</span></span>

- <span data-ttu-id="2503e-313">規劃外圍路由，包括 proxy 伺服器、 防火牆和雲端 proxy。</span><span class="sxs-lookup"><span data-stu-id="2503e-313">Plan perimeter routing, including proxy servers, firewalls, and cloud proxies.</span></span>

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a><span data-ttu-id="2503e-314">規劃您的頻寬、 安全性、 高可用性和容錯移轉</span><span class="sxs-lookup"><span data-stu-id="2503e-314">Plan your bandwidth, security, high availability and failover</span></span>
<span data-ttu-id="2503e-315"><a name="availability"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-315"></span></span>

<span data-ttu-id="2503e-316">建立計劃每個主要的 Office 365 工作負載所需的頻寬。</span><span class="sxs-lookup"><span data-stu-id="2503e-316">Create a plan for bandwidth required for each major Office 365 workload.</span></span> <span data-ttu-id="2503e-317">分開估計 Exchange Online、 SharePoint Online，與 Skype for Business Online 頻寬需求。</span><span class="sxs-lookup"><span data-stu-id="2503e-317">Separately estimate Exchange Online, SharePoint Online, and Skype for Business Online bandwidth requirements.</span></span> <span data-ttu-id="2503e-318">您可以使用我們提供 Exchange Online 和作為起點; 商務用 Skype 估計計算器不過，試驗測試與使用者設定檔及位置的代表性樣本才充分了解您組織的頻寬需求。</span><span class="sxs-lookup"><span data-stu-id="2503e-318">You can use the estimation calculators we've provided for Exchange Online and Skype for Business as a starting place; however, a pilot test with a representative sample of the user profiles and locations is required to fully understand the bandwidth needs of your organization.</span></span>
  
<span data-ttu-id="2503e-319">新增安全性，在每個網際網路和您的計劃的 ExpressRoute 輸出位置的處理方式，請記住所有 ExpressRoute 連線到 Office 365 使用公用對等，而且必須仍受到保護，根據連接至外部的您公司的安全性原則網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-319">Add how security is handled at each internet and ExpressRoute egress location to your plan, remember all ExpressRoute connections to Office 365 use public peering and must still be secured in accordance with your company security policies of connecting to external networks.</span></span>
  
<span data-ttu-id="2503e-320">新增至相關的人員將會受到何種類型的中斷，這些人員如何將能夠最簡單的方式執行容量滿載其工作您計劃的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2503e-320">Add details to your plan about which people will be affected by what type of outage and how those people will be able to perform their work at full capacity in the simplest manner.</span></span>
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a><span data-ttu-id="2503e-321">規劃包括 Skype 抖動、 延遲、 擁塞、 和發揮空間的商務需求的頻寬需求</span><span class="sxs-lookup"><span data-stu-id="2503e-321">Plan bandwidth requirements including Skype for Business requirements on Jitter, Latency, Congestion, and Headroom</span></span>
  
<span data-ttu-id="2503e-322">Skype 商務 Online 也有特定的其他網路需求[媒體品質和網路連線效能 Skype for Business Online 中](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的文章會詳細說明。</span><span class="sxs-lookup"><span data-stu-id="2503e-322">Skype for Business Online also has specific additional network requirements which are detailed in the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>
  
<span data-ttu-id="2503e-323">請閱讀**頻寬規劃 Azure ExpressRoute 的**[網路規劃使用 ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)一節。</span><span class="sxs-lookup"><span data-stu-id="2503e-323">Read the section **Bandwidth planning for Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
<span data-ttu-id="2503e-324">執行時的頻寬評定，與您的試驗使用者，您可以使用我們的指南。[Office 365 效能調整使用基準與效能歷程記錄](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。</span><span class="sxs-lookup"><span data-stu-id="2503e-324">When performing a bandwidth assessment with your pilot users, you can use our guide; [Office 365 performance tuning using baselines and performance history](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>
  
#### <a name="plan-for-high-availability-requirements"></a><span data-ttu-id="2503e-325">規劃高可用性需求</span><span class="sxs-lookup"><span data-stu-id="2503e-325">Plan for high availability requirements</span></span>
  
<span data-ttu-id="2503e-326">建立計畫，以符合您的需求與這併入更新的網路拓撲圖表的高可用性。</span><span class="sxs-lookup"><span data-stu-id="2503e-326">Create a plan for high availability to meet your needs and incorporate this into your updated network topology diagram.</span></span> <span data-ttu-id="2503e-327">閱讀 [] 區段中**的高可用性和容錯移轉進行 Azure ExpressRoute**的[網路規劃使用 ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)。</span><span class="sxs-lookup"><span data-stu-id="2503e-327">Read the section **High availability and failover with Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
#### <a name="plan-for-network-security-requirements"></a><span data-ttu-id="2503e-328">如需網路安全性需求的計劃</span><span class="sxs-lookup"><span data-stu-id="2503e-328">Plan for network security requirements</span></span>
  
<span data-ttu-id="2503e-329">建立計畫，以符合您的網路安全性需求與這併入更新的網路拓撲圖表。</span><span class="sxs-lookup"><span data-stu-id="2503e-329">Create a plan to meet your network security requirements and incorporate this into your updated network topology diagram.</span></span> <span data-ttu-id="2503e-330">閱讀 [] 區段中**套用安全性控制，以便 Azure ExpressRoute for Office 365 案例**中[使用 ExpressRoute for Office 365 的網路規劃](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)。</span><span class="sxs-lookup"><span data-stu-id="2503e-330">Read the section **Applying security controls to Azure ExpressRoute for Office 365 scenarios** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
### <a name="design-outbound-service-connectivity"></a><span data-ttu-id="2503e-331">設計輸出服務連線</span><span class="sxs-lookup"><span data-stu-id="2503e-331">Design outbound service connectivity</span></span>
<span data-ttu-id="2503e-332"><a name="outbound"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-332"></span></span>

<span data-ttu-id="2503e-333">ExpressRoute for Office 365 有可能不太熟悉的*輸出*網路需求。</span><span class="sxs-lookup"><span data-stu-id="2503e-333">ExpressRoute for Office 365 has  *outbound*  network requirements that may be unfamiliar.</span></span> <span data-ttu-id="2503e-334">具體而言，IP 位址，代表您的使用者與網路到 Office 365，且作為給 Microsoft 的輸出網路連線的來源端點必須遵循以下所述的特定需求。</span><span class="sxs-lookup"><span data-stu-id="2503e-334">Specifically, the IP addresses that represent your users and networks to Office 365 and act as the source endpoints for outbound network connections to Microsoft must follow specific requirements outlined below.</span></span>
  
1. <span data-ttu-id="2503e-335">端點必須是公用 IP 位址，已註冊您的公司或電訊廠商提供給您的 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-335">The endpoints must be public IP addresses, that are registered to your company or to carrier providing ExpressRoute connectivity to you.</span></span>

2. <span data-ttu-id="2503e-336">由 ExpressRoute 必須通告給 Microsoft 及驗證/接受端點。</span><span class="sxs-lookup"><span data-stu-id="2503e-336">The endpoints must be advertised to Microsoft and validated/accepted by ExpressRoute.</span></span>

3. <span data-ttu-id="2503e-337">端點必須不會通告到具有相同或更多的慣用路由公制網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-337">The endpoints must not be advertised to the Internet with the same or more preferred routing metric.</span></span>

4. <span data-ttu-id="2503e-338">端點必須不用於未設定透過 ExpressRoute 的 Microsoft 服務的連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-338">The endpoints must not be used for connectivity to Microsoft services that are not configured over ExpressRoute.</span></span>

<span data-ttu-id="2503e-339">如果您的網路設計不符合這些需求，則您的使用者會體驗到 Office 365 和其他 Microsoft 服務，因為路由黑色 holing 或非對稱式路由的連線失敗高風險。</span><span class="sxs-lookup"><span data-stu-id="2503e-339">If your network design doesn't meet these requirements, there is a high risk your users will experience connectivity failures to Office 365 and other Microsoft services due to route black holing or asymmetric routing.</span></span> <span data-ttu-id="2503e-340">會發生這種情況時要求送至 Microsoft 服務透過 ExpressRoute，路由傳送，但回應會路由傳送回跨網際網路，或反之，以及回應會捨棄封狀態的網路裝置，例如防火牆。</span><span class="sxs-lookup"><span data-stu-id="2503e-340">This occurs when requests to Microsoft services are routed over ExpressRoute, but responses are routed back across the internet, or vice versa, and the responses are dropped by stateful network devices such as firewalls.</span></span>
  
<span data-ttu-id="2503e-341">您可以使用符合上述需求的常見方法是網路的使用來源實作為您的一部分，或您 ExpressRoute 電訊廠商所提供的 NAT。</span><span class="sxs-lookup"><span data-stu-id="2503e-341">The most common method you can use to meet the above requirements is to use source NAT, either implemented as a part of your network or provided by your ExpressRoute carrier.</span></span> <span data-ttu-id="2503e-342">來源 NAT 可讓您擷取的詳細資訊與私人 IP 位址設定網際網路網路的 ExpressRoute 從和;搭配適當 IP 路由廣告，提供簡單的機制，以確保路徑對稱性。</span><span class="sxs-lookup"><span data-stu-id="2503e-342">Source NAT allows you to abstract the details and private IP addressing of your internet network from ExpressRoute and; coupled with proper IP route advertisements, provide an easy mechanism to ensure path symmetry.</span></span> <span data-ttu-id="2503e-343">如果您正在使用 ExpressRoute 對等位置特有的設定狀態的網路裝置，您必須實作不同的 NAT 集區的每個對等以確定路徑對稱性來看的 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="2503e-343">If you're using stateful network devices that are specific to ExpressRoute peering locations, you must implement separate NAT pools for each ExpressRoute peering to ensure path symmetry.</span></span>
  
<span data-ttu-id="2503e-344">閱讀的有關[ExpressRoute NAT 需求](https://azure.microsoft.com/documentation/articles/expressroute-nat/)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2503e-344">Read more about the [ExpressRoute NAT requirements](https://azure.microsoft.com/documentation/articles/expressroute-nat/).</span></span>
  
<span data-ttu-id="2503e-345">網路拓撲圖表中新增的輸出連線的變更。</span><span class="sxs-lookup"><span data-stu-id="2503e-345">Add the changes for the outbound connectivity to the network topology diagram.</span></span>
  
### <a name="design-inbound-service-connectivity"></a><span data-ttu-id="2503e-346">設計輸入的服務連線</span><span class="sxs-lookup"><span data-stu-id="2503e-346">Design inbound service connectivity</span></span>
<span data-ttu-id="2503e-347"><a name="inbound"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-347"></span></span>

<span data-ttu-id="2503e-348">大部分的 Office 365 企業版部署假設在某種形式的輸入連線從 Office 365 的內部服務，例如 Exchange、 SharePoint 和 Skype for Business 的混合式案例、 信箱移轉和使用 ADFS 的驗證基礎結構。</span><span class="sxs-lookup"><span data-stu-id="2503e-348">The majority of enterprise Office 365 deployments assume some form of inbound connectivity from Office 365 to on-premises services, such as for Exchange, SharePoint, and Skype for Business hybrid scenarios, mailbox migrations, and authentication using ADFS infrastructure.</span></span> <span data-ttu-id="2503e-349">當啟用您的內部網路與 Microsoft 之間的輸出連線其他路由路徑的 ExpressRoute，這些輸入的連線可能會不小心受到非對稱式路由，即使您想要有這些流程繼續使用網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-349">When ExpressRoute you enable an additional routing path between your on-premises network and Microsoft for outbound connectivity, these inbound connections may inadvertently be impacted by asymmetric routing, even if you intend to have those flows continue to use the Internet.</span></span> <span data-ttu-id="2503e-350">若要確保有不會影響到網際網路型從 Office 365 與內部部署系統的輸入的流量建議如下所述的一些預防措施。</span><span class="sxs-lookup"><span data-stu-id="2503e-350">A few precautions described below are recommended to ensure there is no impact to Internet based inbound flows from Office 365 to on-premises systems.</span></span>
  
<span data-ttu-id="2503e-351">最小化的非對稱式路由內送的網路流量的風險，所有的輸入連線應該使用來源 NAT 之前他們正在路由傳送到您的網路區段有 ExpressRoute 路由的可視性。</span><span class="sxs-lookup"><span data-stu-id="2503e-351">To minimize the risks of asymmetric routing for inbound network traffic flows, all of the inbound connections should use source NAT before they're routed into segments of your network which have routing visibility into ExpressRoute.</span></span> <span data-ttu-id="2503e-352">如果傳入的連線至網路區段中所允許的沒有來源 NAT ExpressRoute 路由查看，來自 Office 365 的要求會進入從網際網路，但回到 Office 365 的回應會偏好 ExpressRoute回到 Microsoft 網路，而造成非對稱式路由的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-352">If the incoming connections are allowed onto a network segment with routing visibility into ExpressRoute without source NAT, requests originating from Office 365 will enter from the internet, but the response going back to Office 365 will prefer the ExpressRoute network path back to the Microsoft network, causing asymmetric routing.</span></span>
  
<span data-ttu-id="2503e-353">您可能會考慮下列其中一個下列實作模式以滿足此需求：</span><span class="sxs-lookup"><span data-stu-id="2503e-353">You may consider one of the following implementation patterns to satisfy this requirement:</span></span>
  
1. <span data-ttu-id="2503e-354">要求路由傳送到您的內部網路使用網路設備，例如防火牆之前執行來源 NAT 或負載平衡器的路徑上從網際網路至您的內部部署系統。</span><span class="sxs-lookup"><span data-stu-id="2503e-354">Perform source NAT before requests are routed into your internal network using networking equipment such as firewalls or load balancers on the path from the Internet to your on-premises systems.</span></span>

2. <span data-ttu-id="2503e-355">請確定 ExpressRoute 路由不會傳播到其中輸入的服務，例如前方端伺服器或反向 proxy 系統，處理的網際網路連線位於網路區段。</span><span class="sxs-lookup"><span data-stu-id="2503e-355">Ensure that ExpressRoute routes are not propagated to the network segments where inbound services, such as front end servers or reverse proxy systems, handling Internet connections reside.</span></span>

<span data-ttu-id="2503e-356">明確 accounting 對這些案例中您的網路，並保留所有內送的網路流量會透過網際網路協助部署和操作的非對稱式路由的風險降至最低。</span><span class="sxs-lookup"><span data-stu-id="2503e-356">Explicitly accounting for these scenarios in your network and keeping all inbound network traffic flows over the Internet helps to minimize deployment and operational risk of asymmetric routing.</span></span>
  
<span data-ttu-id="2503e-357">可能會有您可以選擇將某些輸入的流量導向透過 ExpressRoute 連線的情況。</span><span class="sxs-lookup"><span data-stu-id="2503e-357">There may be cases where you may choose to direct some inbound flows over ExpressRoute connections.</span></span> <span data-ttu-id="2503e-358">這些情況下，需要考慮下列額外考量。</span><span class="sxs-lookup"><span data-stu-id="2503e-358">For these scenarios, take the following additional considerations into account.</span></span>
  
1. <span data-ttu-id="2503e-359">Office 365 可以只目標內部部署端點，使用公用 Ip。</span><span class="sxs-lookup"><span data-stu-id="2503e-359">Office 365 can only target on-premises endpoints that use public IPs.</span></span> <span data-ttu-id="2503e-360">這表示即使內部輸入的端點只會公開給 Office 365 透過 ExpressRoute，仍然需要有與它相關聯的公用 IP。</span><span class="sxs-lookup"><span data-stu-id="2503e-360">This means that even if the on-premises inbound endpoint is only exposed to Office 365 over ExpressRoute, it still needs to have public IP associated with it.</span></span>

2. <span data-ttu-id="2503e-361">若要解決內部部署端點，執行 Office 365 服務的所有 DNS 名稱解析都發生使用公用 DNS。</span><span class="sxs-lookup"><span data-stu-id="2503e-361">All DNS name resolution that Office 365 services perform to resolve on-premises endpoints happen using public DNS.</span></span> <span data-ttu-id="2503e-362">這表示您必須註冊輸入的服務端點的 FQDN，以在網際網路上的 IP 對應。</span><span class="sxs-lookup"><span data-stu-id="2503e-362">This means that you must register inbound service endpoints' FQDN to IP mappings on the Internet.</span></span>

3. <span data-ttu-id="2503e-363">若要透過 ExpressRoute 接收內送的網路連線，這些端點的公用 IP 子網路必須透過 ExpressRoute 通告給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="2503e-363">In order to receive inbound network connections over ExpressRoute, the public IP subnets for these endpoints must to be advertised to Microsoft over ExpressRoute.</span></span>

4. <span data-ttu-id="2503e-364">仔細評估，以確保該適當的安全性這些輸入的網路流量流量和網路控制項時，會套用至其上，根據您的公司安全性和網路原則。</span><span class="sxs-lookup"><span data-stu-id="2503e-364">Carefully evaluate these inbound network traffic flows to ensure that proper security and network controls are applied to them in accordance with your company security and network policies.</span></span>

5. <span data-ttu-id="2503e-365">一次您在內部部署輸入的端點會通告給 Microsoft，透過 ExpressRoute、 ExpressRoute 將有效成為那些端點的所有 Microsoft 服務，包括 Office 365 的慣用路由路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-365">Once your on-premises inbound endpoints are advertised to Microsoft over ExpressRoute, ExpressRoute will effectively become the preferred routing path to those endpoints for all Microsoft services, including Office 365.</span></span> <span data-ttu-id="2503e-366">這表示，這些端點子網路必須僅可用於與 Office 365 服務和 Microsoft 網路上的任何其他服務的通訊。</span><span class="sxs-lookup"><span data-stu-id="2503e-366">This means that those endpoint subnets must only be used for communications with Office 365 services and no other services on the Microsoft network.</span></span> <span data-ttu-id="2503e-367">否則，您的設計會導致其中來自其他 Microsoft 服務偏好路由傳送的輸入的連線輸入透過 ExpressRoute，雖然傳回路徑將會使用網際網路的非對稱式路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-367">Otherwise, your design will cause asymmetric routing where inbound connections from other Microsoft services prefer to route inbound over ExpressRoute, while the return path will use the Internet.</span></span>

6. <span data-ttu-id="2503e-368">在事件 ExpressRoute 電路或符合-我位置已關閉，您需要確定內部輸入的端點是仍可接受要求透過不同的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-368">In the event an ExpressRoute circuit or meet-me location is down, you'll need to ensure the on-premises inbound endpoints are still available to accept requests over a separate network path.</span></span> <span data-ttu-id="2503e-369">這可能表示廣告子網路，透過多重 ExpressRoute 電路這些端點。</span><span class="sxs-lookup"><span data-stu-id="2503e-369">This may mean advertising subnets for those endpoints through multiple ExpressRoute circuits.</span></span>

7. <span data-ttu-id="2503e-370">我們建議您套用來源 NAT 輸入您的網路，透過 ExpressRoute，尤其是當這些流量跨設定狀態的網路裝置，例如防火牆的所有內送的網路流量流程。</span><span class="sxs-lookup"><span data-stu-id="2503e-370">We recommend applying source NAT for all inbound network traffic flows entering your network through ExpressRoute, especially when these flows cross stateful network devices such as firewalls.</span></span>

8. <span data-ttu-id="2503e-371">某些內部服務，例如 ADFS proxy 或 Exchange 自動探索，可能會收到輸入的要求從 Office 365 服務，以及來自網際網路的使用者。</span><span class="sxs-lookup"><span data-stu-id="2503e-371">Some on-premises services, such as ADFS proxy or Exchange autodiscover, may receive inbound requests from both Office 365 services and users from the Internet.</span></span> <span data-ttu-id="2503e-372">這些要求的 Office 365 會透過網際網路目標相同的 FQDN，因為使用者要求。</span><span class="sxs-lookup"><span data-stu-id="2503e-372">For these requests Office 365 will target the same FQDN as user requests over the Internet.</span></span> <span data-ttu-id="2503e-373">時強制使用 ExpressRoute，Office 365 連線到這些內部部署端點，允許輸入的使用者的連線從網際網路代表重大路由的複雜性。</span><span class="sxs-lookup"><span data-stu-id="2503e-373">Allowing inbound user connections from the internet to those on-premises endpoints, while forcing Office 365 connections to use ExpressRoute, represents significant routing complexity.</span></span> <span data-ttu-id="2503e-374">對於大多數的客戶透過 ExpressRoute 實作這類複雜的案例建議您不要由於操作考量。</span><span class="sxs-lookup"><span data-stu-id="2503e-374">For the vast majority of customers implementing such complex scenarios over ExpressRoute is not recommended due to operational considerations.</span></span> <span data-ttu-id="2503e-375">此額外的負荷量包含，管理風險的非對稱式路由，並且需要您仔細跨多個維度中管理路由廣告和原則。</span><span class="sxs-lookup"><span data-stu-id="2503e-375">This additional overhead includes, managing risks of asymmetric routing and will require you to carefully manage routing advertisements and policies across multiple dimensions.</span></span>

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a><span data-ttu-id="2503e-376">更新您的網路拓撲計劃，以顯示您想要如何避免非對稱式路由</span><span class="sxs-lookup"><span data-stu-id="2503e-376">Update your network topology plan to show how you would avoid asymmetric routes</span></span>
<span data-ttu-id="2503e-377"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-377"></span></span>

<span data-ttu-id="2503e-378">您想要避免以確保您組織中的人員可以順暢地使用 Office 365，以及其他重要服務在網際網路上的非對稱式路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-378">You want to avoid asymmetric routing to ensure people in your organization can seamlessly use Office 365 as well as other important services on the internet.</span></span> <span data-ttu-id="2503e-379">有兩種常見設定客戶可有非對稱式路由會造成。</span><span class="sxs-lookup"><span data-stu-id="2503e-379">There are two common configurations customers have that cause asymmetric routing.</span></span> <span data-ttu-id="2503e-380">現在是很好的時間才能檢閱您計劃要使用並檢查其中一個這些非對稱的路由案例可能存在於網路組態。</span><span class="sxs-lookup"><span data-stu-id="2503e-380">Now's a good time to review the network configuration you're planning to use and check if one of these asymmetric routing scenarios could exist.</span></span>
  
<span data-ttu-id="2503e-381">若要開始，我們將檢查幾個不同的情況下的網狀圖相關聯。</span><span class="sxs-lookup"><span data-stu-id="2503e-381">To begin, we'll examine a few different situations associated with the following network diagram.</span></span> <span data-ttu-id="2503e-382">在此圖表中，所有伺服器接收傳入的要求，例如 ADFS 或內部部署混合伺服器皆紐澤西資料中心，並通知給網際網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-382">In this diagram, all servers that receive inbound requests, such as ADFS or on-premises hybrid servers are in the New Jersey data center and are advertised to the internet.</span></span>
  
1. <span data-ttu-id="2503e-383">周邊網路安全時，沒有任何來源 NAT 可用的傳入要求。</span><span class="sxs-lookup"><span data-stu-id="2503e-383">While the perimeter network is secure, there is no Source NAT available for incoming requests.</span></span>

2. <span data-ttu-id="2503e-384">紐澤西資料中心中的伺服器都能看到網際網路和 ExpressRoute 路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-384">The servers in the New Jersey data center are able to see both internet and ExpressRoute routes.</span></span>

![ExpressRoute 連線概觀](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
<span data-ttu-id="2503e-386">我們也會有如何修正它們的建議。</span><span class="sxs-lookup"><span data-stu-id="2503e-386">We also have suggestions on how to fix them.</span></span>
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a><span data-ttu-id="2503e-387">問題 1： 雲端與在網際網路上的內部部署連線</span><span class="sxs-lookup"><span data-stu-id="2503e-387">Problem 1: Cloud to on-premises connection over the Internet</span></span>
  
<span data-ttu-id="2503e-388">下圖說明當您的網路組態不會透過網際網路的輸入要求從 Microsoft cloud 中提供 NAT 時採取的非對稱的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-388">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over the internet.</span></span>
  
1. <span data-ttu-id="2503e-389">從 Office 365 的輸入的要求從公用 DNS 擷取內部部署端點的 IP 位址，並將要求傳送至您的周邊網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-389">The inbound request from Office 365 retrieves the IP address of the on-premises endpoint from public DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="2503e-390">在此無效的組態中，沒有設定任何來源 NAT 或可在周邊網路流量所在傳送產生的實際的來源 IP 位址被用來作為傳回目的地。</span><span class="sxs-lookup"><span data-stu-id="2503e-390">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="2503e-391">您網路上的伺服器會透過任何可用的 ExpressRoute 網路連線，將傳回流量路由到 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2503e-391">The server on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="2503e-392">結果是該流向 Office 365，導致中斷連線的非對稱路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-392">The result is an Asymmetric path for that flow to Office 365, resulting in a broken connection.</span></span>

![ExpressRoute Asymetric 路由問題 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a><span data-ttu-id="2503e-394">解決方案 1a： 來源 NAT</span><span class="sxs-lookup"><span data-stu-id="2503e-394">Solution 1a: Source NAT</span></span>
  
<span data-ttu-id="2503e-395">只要將 NAT 的來源加入到的傳入要求解析此設定錯誤的網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-395">Simply adding a source NAT to the inbound request resolves this misconfigured network.</span></span> <span data-ttu-id="2503e-396">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="2503e-396">In this diagram:</span></span>
  
1. <span data-ttu-id="2503e-397">傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-397">The incoming request continues to enter through the New Jersey data center's perimeter network.</span></span> <span data-ttu-id="2503e-398">這段時間來源 NAT 使用。</span><span class="sxs-lookup"><span data-stu-id="2503e-398">This time Source NAT is available.</span></span>

2. <span data-ttu-id="2503e-399">從回聚集 nat 來源而不是原始的 IP 位址，傳回相同的網路路徑在回應中產生關聯的 IP 伺服器路由傳送回應。</span><span class="sxs-lookup"><span data-stu-id="2503e-399">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由方案 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a><span data-ttu-id="2503e-401">解決方案 1b： 路由範圍設定</span><span class="sxs-lookup"><span data-stu-id="2503e-401">Solution 1b: Route Scoping</span></span>
  
<span data-ttu-id="2503e-402">或者，您可以選擇不允許前置詞才能被公告 ExpressRoute BGP 移除這些電腦的替代的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-402">Alternatively, you can choose to not allow the ExpressRoute BGP prefixes to be advertised, removing the alternate network path for those computers.</span></span> <span data-ttu-id="2503e-403">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="2503e-403">In this diagram:</span></span>
  
1. <span data-ttu-id="2503e-404">傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-404">The incoming request continues to enter through the New Jersey data center's perimeter network.</span></span> <span data-ttu-id="2503e-405">這一次透過 ExpressRoute 線路通告來自 Microsoft 的前置詞不到紐澤西資料中心。</span><span class="sxs-lookup"><span data-stu-id="2503e-405">This time the prefixes advertised from Microsoft over the ExpressRoute circuit are not available to the New Jersey data center.</span></span>

2. <span data-ttu-id="2503e-406">從伺服器路由傳送的回應備份聚集傳回相同的網路路徑在回應中所產生的 IP 上可用的唯一路由相關聯的原始 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2503e-406">The response from the server routes back toward the IP associated with the original IP address over the only route available, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由方案 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a><span data-ttu-id="2503e-408">問題 2： 雲端與內部連線透過 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2503e-408">Problem 2: Cloud to on-premises connection over ExpressRoute</span></span>
  
<span data-ttu-id="2503e-409">下圖說明當您的網路組態不會提供從 Microsoft cloud 的輸入要求的 NAT 透過 ExpressRoute 時採取的非對稱的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-409">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over ExpressRoute.</span></span>
  
1. <span data-ttu-id="2503e-410">從 Office 365 的輸入的要求從 DNS 擷取的 IP 位址，並將要求傳送至您的周邊網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-410">The inbound request from Office 365 retrieves the IP address from DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="2503e-411">在此無效的組態中，沒有設定任何來源 NAT 或可在周邊網路流量所在傳送產生的實際的來源 IP 位址被用來作為傳回目的地。</span><span class="sxs-lookup"><span data-stu-id="2503e-411">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="2503e-412">在您的網路上的電腦將傳回流量路由到 Office 365 透過任何可用的 ExpressRoute 網路連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-412">The computer on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="2503e-413">結果是 Office 365 的非對稱式連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-413">The result is an Asymmetric connection to Office 365.</span></span>

![ExpressRoute Asymetric 路由問題 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a><span data-ttu-id="2503e-415">解決方案 2： 來源 NAT</span><span class="sxs-lookup"><span data-stu-id="2503e-415">Solution 2: Source NAT</span></span>
  
<span data-ttu-id="2503e-416">只要將 NAT 的來源加入到的傳入要求解析此設定錯誤的網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-416">Simply adding a source NAT to the inbound request resolves this misconfigured network.</span></span> <span data-ttu-id="2503e-417">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="2503e-417">In this diagram:</span></span>
  
1. <span data-ttu-id="2503e-418">傳入的要求會繼續輸入透過紐約資料中心的周邊網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-418">The incoming request continues to enter through the New York data center's perimeter network.</span></span> <span data-ttu-id="2503e-419">這段時間來源 NAT 使用。</span><span class="sxs-lookup"><span data-stu-id="2503e-419">This time Source NAT is available.</span></span>

2. <span data-ttu-id="2503e-420">從回聚集 nat 來源而不是原始的 IP 位址，傳回相同的網路路徑在回應中產生關聯的 IP 伺服器路由傳送回應。</span><span class="sxs-lookup"><span data-stu-id="2503e-420">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由方案 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a><span data-ttu-id="2503e-422">紙張確認網路設計具有路徑對稱性來看</span><span class="sxs-lookup"><span data-stu-id="2503e-422">Paper verify that the network design has path symmetry</span></span>

<span data-ttu-id="2503e-423">此時，您必須確認在紙張上實作計劃提供路由對稱性來看，不同案例中您要使用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="2503e-423">At this point, you need to verify on paper that your implementation plan offers route symmetry for the different scenarios in which you'll be using Office 365.</span></span> <span data-ttu-id="2503e-424">您將識別預期會在使用服務的不同功能時所要採取的特定網路路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-424">You'll identify the specific network route that is expected to be taken when a person uses different features of the service.</span></span> <span data-ttu-id="2503e-425">從內部網路和 WAN 路由至周邊裝置，來連線的路徑。ExpressRoute 或網際網路，並登入 online 端點的連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-425">From the on-premises network and WAN routing, to the perimeter devices, to the connectivity path; ExpressRoute or the internet, and on to the connection to the online endpoint.</span></span>
  
<span data-ttu-id="2503e-426">您需要這麼做的所有 Office 365 網路服務先前已識別為您的組織將採用的服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-426">You'll need to do this for all of the Office 365 network services that were previously identified as services that your organization will adopt.</span></span>
  
<span data-ttu-id="2503e-427">很有幫助不要使用另一位使用者路由此白皮書逐一檢查。</span><span class="sxs-lookup"><span data-stu-id="2503e-427">It helps to do this paper walk through of routes with a second person.</span></span> <span data-ttu-id="2503e-428">說明這些其中每個網路躍點預計需要取得從其下一個路由，並確定您熟悉的路由路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-428">Explain to them where each network hop is expected to get its next route from and ensure that you're familiar with the routing paths.</span></span> <span data-ttu-id="2503e-429">請記住 ExpressRoute 一律會提供更多範圍的路由，以提供比網際網路預設路由的路由成本較低的 Microsoft 伺服器 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2503e-429">Remember that ExpressRoute will always provide a more scoped route to Microsoft server IP addresses giving it lower route cost than an Internet default route.</span></span>
  
### <a name="design-client-connectivity-configuration"></a><span data-ttu-id="2503e-430">設計用戶端連線設定</span><span class="sxs-lookup"><span data-stu-id="2503e-430">Design Client Connectivity Configuration</span></span>
<span data-ttu-id="2503e-431"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-431"></span></span>

![使用 ExpressRoute 的 PAC 檔案](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
<span data-ttu-id="2503e-433">如果您正在使用網際網路 proxy 伺服器繫結的流量，然後您要調整任何 PAC 或用戶端設定檔，以確保您網路上的用戶端電腦已正確設定為您想要的 ExpressRoute 流量傳送至 Office 365，而不 transiting您的 proxy 伺服器，以及剩餘的流量，包括一些 Office 365 流量，會傳送至相關的 proxy。</span><span class="sxs-lookup"><span data-stu-id="2503e-433">If you're using a proxy server for internet bound traffic then you need to adjust any PAC or client configuration files to ensure client computers on your network are correctly configured to send the ExpressRoute traffic you desire to Office 365 without transiting your proxy server, and the remaining traffic, including some Office 365 traffic, is sent to the relevant proxy.</span></span> <span data-ttu-id="2503e-434">閱讀我們的指南，在[管理 Office 365 端點](https://aka.ms/manageo365endpoints)，例如 PAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="2503e-434">Read our guide on [managing Office 365 endpoints](https://aka.ms/manageo365endpoints) for example PAC files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2503e-435">端點變更經常、 每週的頻率。</span><span class="sxs-lookup"><span data-stu-id="2503e-435">The endpoints change frequently, as often as weekly.</span></span> <span data-ttu-id="2503e-436">您只應該進行變更為基礎的服務和功能貴組織已採用以減少您需要對保持最新變更的數目。</span><span class="sxs-lookup"><span data-stu-id="2503e-436">You should only make changes based on the services and features your organization has adopted to reduce the number of changes you'll need to make to stay current.</span></span> <span data-ttu-id="2503e-437">關閉必須注意宣佈所做的變更，並記錄會保留的所有變更，IP 過去宣佈的地址的 RSS 摘要中的**有效日期**可能未通告，或移除通告，直到達到有效的日期。</span><span class="sxs-lookup"><span data-stu-id="2503e-437">Pay close attention to the **Effective Date** in the RSS feed where the changes are announced and a record is kept of all past changes, IP addresses that are announced may not be advertised, or removed from advertisement, until the effective date is reached.</span></span>
  
## <a name="build-your-deployment-and-testing-procedures"></a><span data-ttu-id="2503e-438">建立您的部署和測試程序</span><span class="sxs-lookup"><span data-stu-id="2503e-438">Build your deployment and testing procedures</span></span>
<span data-ttu-id="2503e-439"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-439"></span></span>

<span data-ttu-id="2503e-440">您實作計劃應該包含測試及復原計劃。</span><span class="sxs-lookup"><span data-stu-id="2503e-440">Your implementation plan should include both testing and rollback planning.</span></span> <span data-ttu-id="2503e-441">如果您實作未如預期般運作中，為了影響最少計劃的人員之前探索到的問題。</span><span class="sxs-lookup"><span data-stu-id="2503e-441">If your implementation isn't functioning as expected, the plan should be designed to affect the least number of people before problems are discovered.</span></span> <span data-ttu-id="2503e-442">以下是您的計劃應該考慮一些高階原則。</span><span class="sxs-lookup"><span data-stu-id="2503e-442">The following are some high level principles your plan should consider.</span></span>
  
1. <span data-ttu-id="2503e-443">階段網路區段和使用者服務上架干擾降至最低。</span><span class="sxs-lookup"><span data-stu-id="2503e-443">Stage the network segment and user service onboarding to minimize disruption.</span></span>

2. <span data-ttu-id="2503e-444">規劃測試使用 traceroute 路由和 TCP 連線從不同的網際網路連線的主機。</span><span class="sxs-lookup"><span data-stu-id="2503e-444">Plan for testing routes with traceroute and TCP connect from a separate internet connected host.</span></span>

3. <span data-ttu-id="2503e-445">最好的輸入和輸出服務測試應與測試 Office 365 租用戶隔離的測試網路上。</span><span class="sxs-lookup"><span data-stu-id="2503e-445">Preferably, testing of inbound and outbound services should be done on an isolated test network with a test Office 365 tenant.</span></span>

      - <span data-ttu-id="2503e-446">或者，測試可執行生產網路若還不使用 Office 365 客戶，或位於試驗。</span><span class="sxs-lookup"><span data-stu-id="2503e-446">Alternatively, testing can be performed on a production network if the customer is not yet using Office 365 or is in pilot.</span></span>

      - <span data-ttu-id="2503e-447">或者，測試可以執行測試放在一旁設定實際執行中斷期間和監控僅。</span><span class="sxs-lookup"><span data-stu-id="2503e-447">Alternatively, testing can be performed during a production outage that is set aside for test and monitoring only.</span></span>

      - <span data-ttu-id="2503e-448">或者，測試可透過檢查每個第 3 層路由器節點上每個服務的路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-448">Alternatively, testing can be done by checking routes for each service on each layer 3 router node.</span></span> <span data-ttu-id="2503e-449">此改回應該只用於如果沒有其他測試可能是因為缺少的實體測試介紹風險。</span><span class="sxs-lookup"><span data-stu-id="2503e-449">This fall back should only be used if no other testing is possible since a lack of physical testing introduces risk.</span></span>

### <a name="build-your-deployment-procedures"></a><span data-ttu-id="2503e-450">建立您的部署程序</span><span class="sxs-lookup"><span data-stu-id="2503e-450">Build your deployment procedures</span></span>

<span data-ttu-id="2503e-451">您的部署程序應該推行至小群人分階段以供測試，再部署至較大群人。</span><span class="sxs-lookup"><span data-stu-id="2503e-451">Your deployment procedures should roll out to small groups of people in stages to allow for testing before deploying to larger groups of people.</span></span> <span data-ttu-id="2503e-452">以下是幾種方式可以階段 ExpressRoute 的部署。</span><span class="sxs-lookup"><span data-stu-id="2503e-452">The following are several ways to stage the deployment of ExpressRoute.</span></span>
  
1. <span data-ttu-id="2503e-453">設定與 Microsoft 對等的 ExpressRoute 和已轉寄給僅適用於單一主機的路由通告分段測試之用。</span><span class="sxs-lookup"><span data-stu-id="2503e-453">Set up ExpressRoute with Microsoft peering and have the route advertisements forwarded to a single host only for staged testing purposes.</span></span>

2. <span data-ttu-id="2503e-454">通告路由到單一網路區段第一次 ExpressRoute 網路，並展開路由廣告網路區段或區域。</span><span class="sxs-lookup"><span data-stu-id="2503e-454">Advertise routes to the ExpressRoute network to a single network segment at first and expand route advertisements by network segment or region.</span></span>

3. <span data-ttu-id="2503e-455">如果第一次部署 Office 365，請使用 ExpressRoute 網路部署試驗為數目更少的人員。</span><span class="sxs-lookup"><span data-stu-id="2503e-455">If deploying Office 365 for the first time, use the ExpressRoute network deployment as a pilot for a small number of people.</span></span>

4. <span data-ttu-id="2503e-456">如果使用 proxy 伺服器，您可以另外設定測試 PAC 檔案之前新增更多導向少數幾個受損人士 ExpressRoute 來測試和意見反應。</span><span class="sxs-lookup"><span data-stu-id="2503e-456">If using proxy servers, you can alternatively configure a test PAC file to direct a small number of people to ExpressRoute with testing and feedback before adding more.</span></span>

<span data-ttu-id="2503e-457">您實作計劃應列出每個必須採取的部署程序或要用來部署的網路組態的命令。</span><span class="sxs-lookup"><span data-stu-id="2503e-457">Your implementation plan should list each of the deployment procedures that must be taken or commands that need to be used to deploy the networking configuration.</span></span> <span data-ttu-id="2503e-458">當網路中斷時間會進入的所有變更，這是 arbutus solutions 事先撰寫的部署計劃和對等應該進行都檢閱。</span><span class="sxs-lookup"><span data-stu-id="2503e-458">When the network outage time arrives all of the changes being made should be from the written deployment plan which was written in advance and peer reviewed.</span></span> <span data-ttu-id="2503e-459">ExpressRoute 技術組態，請參閱指導方針。</span><span class="sxs-lookup"><span data-stu-id="2503e-459">See our guidance on the technical configuration of ExpressRoute.</span></span>
  
- <span data-ttu-id="2503e-460">如果您已經變更的任何仍會繼續傳送電子郵件的內部部署伺服器的 IP 位址，請更新您的 SPF TXT 記錄。</span><span class="sxs-lookup"><span data-stu-id="2503e-460">Updating your SPF TXT records if you've changed IP addresses for any on-premises servers that will continue to send email.</span></span>

- <span data-ttu-id="2503e-461">如果您已經變更以容納新的 NAT 設定的 IP 位址，請更新內部部署伺服器的任何 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="2503e-461">Updating any DNS entries for on-premises servers if you've changed IP addresses to accommodate a new NAT configuration.</span></span>

- <span data-ttu-id="2503e-462">請確定您已訂閱 rss 摘要，以維持任何路由或 proxy 設定的 Office 365 端點通知。</span><span class="sxs-lookup"><span data-stu-id="2503e-462">Ensure you've subscribed to the RSS feed for Office 365 endpoint notifications to maintain any routing or proxy configurations.</span></span>

<span data-ttu-id="2503e-463">ExpressRoute 部署完成之後，應該要執行的測試計劃中的程序。</span><span class="sxs-lookup"><span data-stu-id="2503e-463">After your ExpressRoute deployment is complete the procedures in the test plan should be executed.</span></span> <span data-ttu-id="2503e-464">每個程序的結果應該會記錄。</span><span class="sxs-lookup"><span data-stu-id="2503e-464">Results for each procedure should be logged.</span></span> <span data-ttu-id="2503e-465">您必須包含復原到原始的實際執行環境事件中的測試計劃結果指出實作未成功的程序。</span><span class="sxs-lookup"><span data-stu-id="2503e-465">You must include procedures for rolling back to the original production environment in the event the test plan results indicate the implementation was not successful.</span></span>
  
### <a name="build-your-test-procedures"></a><span data-ttu-id="2503e-466">建立測試程序</span><span class="sxs-lookup"><span data-stu-id="2503e-466">Build your test procedures</span></span>

<span data-ttu-id="2503e-467">您測試的程序應該包含對於 Office 365 每個輸出和輸入網路服務將會使用 ExpressRoute 和則不會測試。</span><span class="sxs-lookup"><span data-stu-id="2503e-467">Your testing procedures should include tests for each outbound and inbound network service for Office 365 both that will be using ExpressRoute and ones that will not.</span></span> <span data-ttu-id="2503e-468">這些程序應該包括測試從每個唯一的網路位置，包括不是在內部公司的 LAN 中的使用者。</span><span class="sxs-lookup"><span data-stu-id="2503e-468">The procedures should include testing from each unique network location including users who are not on-premises in the corporate LAN.</span></span>
  
<span data-ttu-id="2503e-469">測試活動的一些範例包括：</span><span class="sxs-lookup"><span data-stu-id="2503e-469">Some examples of test activities include the following.</span></span>
  
1. <span data-ttu-id="2503e-470">從您的內部路由器 ping 到您網路的運算子路由器。</span><span class="sxs-lookup"><span data-stu-id="2503e-470">Ping from your on-premises router to your network operator router.</span></span>

2. <span data-ttu-id="2503e-471">驗證 500 + Office 365 和 CRM Online IP 位址廣告會接收到您的內部路由器。</span><span class="sxs-lookup"><span data-stu-id="2503e-471">Validate the 500+ Office 365 and CRM Online IP address advertisements are received by your on-premises router.</span></span>

3. <span data-ttu-id="2503e-472">驗證您輸入和輸出的 NAT ExpressRoute 和內部部署網路間運作。</span><span class="sxs-lookup"><span data-stu-id="2503e-472">Validate your inbound and outbound NAT is operating between ExpressRoute and the internal network.</span></span>

4. <span data-ttu-id="2503e-473">驗證您的 nat 路由會被通告從您的路由器。</span><span class="sxs-lookup"><span data-stu-id="2503e-473">Validate that routes to your NAT are being advertised from your router.</span></span>

5. <span data-ttu-id="2503e-474">驗證 ExpressRoute 已接受您公告的前置詞。</span><span class="sxs-lookup"><span data-stu-id="2503e-474">Validate that ExpressRoute has accepted your advertised prefixes.</span></span>

      - <span data-ttu-id="2503e-475">若要確認對等的廣告使用下列 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="2503e-475">Use the following cmdlet to verify peering advertisements:</span></span>

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. <span data-ttu-id="2503e-476">驗證公用 NAT IP 範圍未通知伺服器向 Microsoft 透過 ExpressRoute 或公用的網際網路網路電路除非它是較大的範圍，如上述範例所示的特定子集合。</span><span class="sxs-lookup"><span data-stu-id="2503e-476">Validate your public NAT IP range is not advertised to Microsoft through any other ExpressRoute or public Internet network circuit unless it is a specific subset of a larger range as in the previous example.</span></span>

7. <span data-ttu-id="2503e-477">ExpressRoute 電路成對出現，驗證執行這兩個 BGP 工作階段。</span><span class="sxs-lookup"><span data-stu-id="2503e-477">ExpressRoute circuits are paired, validate that both BGP sessions are running.</span></span>

8. <span data-ttu-id="2503e-478">設定您的 NAT 的內部單一主機，使用 ping、 tracert 及 tcpping 跨至主機 outlook.office365.com 的新電路測試連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-478">Set up a single host on the inside of your NAT and use ping, tracert, and tcpping to test connectivity across the new circuit to the host outlook.office365.com.</span></span> <span data-ttu-id="2503e-479">或者，您可以使用 Wireshark 之類的工具，或若要驗證您 MSEE 鏡像連接埠上的 Microsoft Network Monitor 3.4 是能夠連線至 outlook.office365.com 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="2503e-479">Alternatively, you could use a tool such as Wireshark or Microsoft Network Monitor 3.4 on a mirrored port to the MSEE to validate you're able to connect to the IP address associated with outlook.office365.com.</span></span>

9. <span data-ttu-id="2503e-480">Exchange Online 的測試應用程式層級的功能。</span><span class="sxs-lookup"><span data-stu-id="2503e-480">Test application level functionality for Exchange Online.</span></span>

  - <span data-ttu-id="2503e-481">測試 Outlook 是能夠連線到 Exchange Online，並傳送/接收電子郵件。</span><span class="sxs-lookup"><span data-stu-id="2503e-481">Test Outlook is able to connect to Exchange Online and send/receive email.</span></span>

  - <span data-ttu-id="2503e-482">測試 Outlook 是能夠使用線上模式。</span><span class="sxs-lookup"><span data-stu-id="2503e-482">Test Outlook is able to use online-mode.</span></span>

  - <span data-ttu-id="2503e-483">測試智慧型手機連線和收發能力。</span><span class="sxs-lookup"><span data-stu-id="2503e-483">Test smartphone connectivity and send/receive capability.</span></span>

10. <span data-ttu-id="2503e-484">SharePoint Online 的測試應用程式層級功能</span><span class="sxs-lookup"><span data-stu-id="2503e-484">Test application level functionality for SharePoint Online</span></span>

  - <span data-ttu-id="2503e-485">測試 OneDrive for Business 同步處理用戶端。</span><span class="sxs-lookup"><span data-stu-id="2503e-485">Test OneDrive for Business sync client.</span></span>

  - <span data-ttu-id="2503e-486">測試 SharePoint Online web access。</span><span class="sxs-lookup"><span data-stu-id="2503e-486">Test SharePoint Online web access.</span></span>

11. <span data-ttu-id="2503e-487">測試應用程式層級的功能，skype 商務呼叫案例：</span><span class="sxs-lookup"><span data-stu-id="2503e-487">Test application level functionality for Skype for Business calling scenarios:</span></span>

  - <span data-ttu-id="2503e-488">加入電話會議，以驗證的使用者 [由使用者起始的邀請]。</span><span class="sxs-lookup"><span data-stu-id="2503e-488">Join to conference call as authenticated user [invite initiated by end user].</span></span>

  - <span data-ttu-id="2503e-489">邀請使用者電話會議 [寄件者 MCU 邀請]。</span><span class="sxs-lookup"><span data-stu-id="2503e-489">Invite user to conference call [invite sent from MCU].</span></span>

  - <span data-ttu-id="2503e-490">使用 Skype for Business web 應用程式的匿名使用者加入會議。</span><span class="sxs-lookup"><span data-stu-id="2503e-490">Join conference as anonymous user using the Skype for Business web application.</span></span>

  - <span data-ttu-id="2503e-491">加入從有線的電腦連線、 IP 電話和行動裝置的通話。</span><span class="sxs-lookup"><span data-stu-id="2503e-491">Join call from your wired PC connection, IP phone, and mobile device.</span></span>

  - <span data-ttu-id="2503e-492">呼叫以同盟的使用者 o PSTN 驗證的呼叫： 呼叫完成，是可接受的通話品質，是可接受的連線時間。</span><span class="sxs-lookup"><span data-stu-id="2503e-492">Call to federated user o Call to PSTN Validation: call is completed, call quality is acceptable, connection time is acceptable.</span></span>

  - <span data-ttu-id="2503e-493">確認連絡人的目前狀態更新這兩個成員的租用戶和同盟使用者。</span><span class="sxs-lookup"><span data-stu-id="2503e-493">Verify presence status for contacts is updated for both members of the tenant and federated users.</span></span>

### <a name="common-problems"></a><span data-ttu-id="2503e-494">常見的問題</span><span class="sxs-lookup"><span data-stu-id="2503e-494">Common problems</span></span>

<span data-ttu-id="2503e-495">非對稱式路由是最常見的實作問題。</span><span class="sxs-lookup"><span data-stu-id="2503e-495">Asymmetric routing is the most common implementation problem.</span></span> <span data-ttu-id="2503e-496">以下是一些常見的來源，以尋找：</span><span class="sxs-lookup"><span data-stu-id="2503e-496">Here are some common sources to look for:</span></span>
  
- <span data-ttu-id="2503e-497">使用 open 或平面網路路由拓撲不來源就地 NAT。</span><span class="sxs-lookup"><span data-stu-id="2503e-497">Using an open or flat network routing topology without source NAT in place.</span></span>

- <span data-ttu-id="2503e-498">不使用 SNAT 來路由傳送至輸入服務透過網際網路與 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-498">Not using SNAT to route to inbound services through both the internet and ExpressRoute connections.</span></span>

- <span data-ttu-id="2503e-499">不測試上 ExpressRoute 廣泛部署之前先測試網路上的內送的服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-499">Not testing inbound services on ExpressRoute on a test network prior to deploying broadly.</span></span>

## <a name="deploying-expressroute-connectivity-through-your-network"></a><span data-ttu-id="2503e-500">部署 ExpressRoute 連線到您的網路</span><span class="sxs-lookup"><span data-stu-id="2503e-500">Deploying ExpressRoute connectivity through your network</span></span>
<span data-ttu-id="2503e-501"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-501"></span></span>

<span data-ttu-id="2503e-502">階段您一次，逐漸推出至不同的組件的計劃將回復為每個新的網路區段的網路連線網路的一條線段的部署。</span><span class="sxs-lookup"><span data-stu-id="2503e-502">Stage your deployment to one segment of the network at a time, progressively rolling out the connectivity to different parts of the network with a plan to roll back for each new network segment.</span></span> <span data-ttu-id="2503e-503">如果您的部署與 Office 365 部署對齊，第一次部署至您的 Office 365 試驗使用者，並從該處擴充。</span><span class="sxs-lookup"><span data-stu-id="2503e-503">If your deployment is aligned with an Office 365 deployment, deploy to your Office 365 pilot users first and extend from there.</span></span>
  
<span data-ttu-id="2503e-504">第一個測試然後為了建立生產環境：</span><span class="sxs-lookup"><span data-stu-id="2503e-504">First for your test and then for production:</span></span>
  
- <span data-ttu-id="2503e-505">執行啟用 ExpressRoute 的部署步驟。</span><span class="sxs-lookup"><span data-stu-id="2503e-505">Run the deployment steps to enable ExpressRoute.</span></span>

- <span data-ttu-id="2503e-506">測試您的網路路由已如預期般地看到。</span><span class="sxs-lookup"><span data-stu-id="2503e-506">Test your seeing the network routes are as expected.</span></span>

- <span data-ttu-id="2503e-507">執行測試每個輸入和輸出的服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-507">Perform testing on each inbound and outbound service.</span></span>

- <span data-ttu-id="2503e-508">如果您發現任何問題，復原。</span><span class="sxs-lookup"><span data-stu-id="2503e-508">Rollback if you discover any issues.</span></span>

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a><span data-ttu-id="2503e-509">測試網路區段，使用 ExpressRoute 的測試連線設定</span><span class="sxs-lookup"><span data-stu-id="2503e-509">Set up a test connection to ExpressRoute with a test network segment</span></span>

<span data-ttu-id="2503e-510">現在，您必須在紙張上的已完成計劃該是時候來在小規模地測試。</span><span class="sxs-lookup"><span data-stu-id="2503e-510">Now that you have the completed plan on paper it is time to test at a small scale.</span></span> <span data-ttu-id="2503e-511">此測試中您將內部部署網路上建立測試子網路與 Microsoft Peering 單一 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="2503e-511">In this test you will establish a single ExpressRoute connection with Microsoft Peering to a test subnet on your on-premises network.</span></span> <span data-ttu-id="2503e-512">您可以連線到及傳送自測試子網路設定[試用版的 Office 365 租用戶](https://go.microsoft.com/fwlink/p/?LinkID=403802)，並在生產環境中測試子網路中包含您要使用的所有輸出和輸入服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-512">You can configure a [trial Office 365 tenant](https://go.microsoft.com/fwlink/p/?LinkID=403802) with connectivity to and from the test subnet and include all outbound and inbound services that you will be using in production in the test subnet.</span></span> <span data-ttu-id="2503e-513">設定 DNS 進行測試網路區段，並建立輸入和輸出的所有服務。</span><span class="sxs-lookup"><span data-stu-id="2503e-513">Set up DNS for the test network segment and establish all inbound and outbound services.</span></span> <span data-ttu-id="2503e-514">執行測試計劃，請確定您已熟悉針對每個服務和路由傳播路由傳送。</span><span class="sxs-lookup"><span data-stu-id="2503e-514">Execute your test plan and ensure that you are familiar with the routing for each service and the route propagation.</span></span>
  
### <a name="execute-the-deployment-and-test-plans"></a><span data-ttu-id="2503e-515">執行部署和測試計劃</span><span class="sxs-lookup"><span data-stu-id="2503e-515">Execute the deployment and test plans</span></span>

<span data-ttu-id="2503e-516">完成上述的項目之後，請關閉區域您已完成，並確定您和您的小組檢閱它們之前執行您的部署和測試計劃。</span><span class="sxs-lookup"><span data-stu-id="2503e-516">As you complete the items described above, check off the areas you've completed and ensure you and your team have reviewed them before executing your deployment and testing plans.</span></span>
  
- <span data-ttu-id="2503e-517">輸出和輸入網路變更相關的服務清單。</span><span class="sxs-lookup"><span data-stu-id="2503e-517">List of outbound and inbound services that are involved in the network change.</span></span>

- <span data-ttu-id="2503e-518">全球網路架構圖中顯示網際網路輸出及 ExpressRoute 符合-我的位置。</span><span class="sxs-lookup"><span data-stu-id="2503e-518">Global network architecture diagram showing both internet egress and ExpressRoute meet-me locations.</span></span>

- <span data-ttu-id="2503e-519">路由網狀示範部署每個服務使用不同的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="2503e-519">Network routing diagram demonstrating the different network paths used for each service deployed.</span></span>

- <span data-ttu-id="2503e-520">部署計劃與實作的變更和復原，如有需要的步驟。</span><span class="sxs-lookup"><span data-stu-id="2503e-520">A deployment plan with steps to implement the changes and rollback if needed.</span></span>

- <span data-ttu-id="2503e-521">測試每個 Office 365 和網路服務測試計劃。</span><span class="sxs-lookup"><span data-stu-id="2503e-521">A test plan for testing each Office 365 and network service.</span></span>

- <span data-ttu-id="2503e-522">完成輸入和輸出服務的實際執行路由紙張驗證。</span><span class="sxs-lookup"><span data-stu-id="2503e-522">Completed paper validation of production routes for inbound and outbound services.</span></span>

- <span data-ttu-id="2503e-523">跨測試網路區段，包括可用性測試完成的測試。</span><span class="sxs-lookup"><span data-stu-id="2503e-523">A completed test across a test network segment including availability testing.</span></span>

<span data-ttu-id="2503e-524">選擇 [中斷時間長度可透過在整個部署規劃和測試計劃執行，有一些疑難排解可用的時間和復原回如有需要的時間。</span><span class="sxs-lookup"><span data-stu-id="2503e-524">Choose an outage window that is long enough to run through the entire deployment plan and the test plan, has some time available for troubleshooting and time for rolling back if required.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="2503e-525">由於透過網際網路與 ExpressRoute 路由複雜的性質，最好是其他緩衝區時間會新增此視窗以處理疑難排解複雜路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-525">Due to the complex nature of routing over both the internet and ExpressRoute, it is recommended that additional buffer time is added to this window to handle troubleshooting complex routing.</span></span>
  
### <a name="configure-qos-for-skype-for-business-online"></a><span data-ttu-id="2503e-526">QoS skype for Business Online 設定</span><span class="sxs-lookup"><span data-stu-id="2503e-526">Configure QoS for Skype for Business Online</span></span>

<span data-ttu-id="2503e-527">QoS 是必要商務用 Skype 取得語音和會議的優點。</span><span class="sxs-lookup"><span data-stu-id="2503e-527">QoS is necessary to obtain voice and meeting benefits for Skype for Business Online.</span></span> <span data-ttu-id="2503e-528">您必須確定滿足 ExpressRoute 的網路連線不會封鎖任何您其他 Office 365 服務存取權之後，您可以設定 QoS。</span><span class="sxs-lookup"><span data-stu-id="2503e-528">You can configure QoS after you have ensured that the ExpressRoute network connection does not block any of your other Office 365 service access.</span></span> <span data-ttu-id="2503e-529">設定 QoS 所述[的 ExpressRoute 與 QoS Skype for Business Online 中](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)的文章。</span><span class="sxs-lookup"><span data-stu-id="2503e-529">Configuration for QoS is described in the article [ExpressRoute and QoS in Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .</span></span>
  
## <a name="troubleshooting-your-implementation"></a><span data-ttu-id="2503e-530">疑難排解您實作</span><span class="sxs-lookup"><span data-stu-id="2503e-530">Troubleshooting your implementation</span></span>
<span data-ttu-id="2503e-531"><a name="troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="2503e-531"></span></span>

<span data-ttu-id="2503e-532">若要尋找的第一個位置位於此實作指南 》 中的步驟是任何未接在您實作計劃嗎？</span><span class="sxs-lookup"><span data-stu-id="2503e-532">The first place to look is at the steps in this implementation guide, were any missed in your implementation plan?</span></span> <span data-ttu-id="2503e-533">請返回並執行進一步小型網路複寫錯誤和偵錯它那里盡可能測試。</span><span class="sxs-lookup"><span data-stu-id="2503e-533">Go back and run further small network testing if possible to replicate the error and debug it there.</span></span>
  
<span data-ttu-id="2503e-534">識別可輸入或輸出 services 無法在測試期間。</span><span class="sxs-lookup"><span data-stu-id="2503e-534">Identify which inbound or outbound services failed during testing.</span></span> <span data-ttu-id="2503e-535">每個失敗之服務取得特別的 IP 位址和子網路。</span><span class="sxs-lookup"><span data-stu-id="2503e-535">Get specifically the IP addresses and subnets for each of the services which failed.</span></span> <span data-ttu-id="2503e-536">得出引導紙張上的網路拓撲圖表並驗證的路由。</span><span class="sxs-lookup"><span data-stu-id="2503e-536">Go ahead and walk the network topology diagram on paper and validate the routing.</span></span> <span data-ttu-id="2503e-537">驗證特別其中 ExpressRoute 路由會通知給、 測試該路由中斷期間盡可能與追蹤項目。</span><span class="sxs-lookup"><span data-stu-id="2503e-537">Validate specifically where the ExpressRoute routing is advertised to, Test that routing during the outage if possible with traces.</span></span>
  
<span data-ttu-id="2503e-538">使用網路追蹤執行 PSPing，為每個客戶端點，並評估來源及目的地 IP 位址，以驗證其如預期般。</span><span class="sxs-lookup"><span data-stu-id="2503e-538">Run PSPing with a network trace to each customer endpoint and evaluate source and destination IP addresses to validate that they are as expected.</span></span> <span data-ttu-id="2503e-539">執行您在通訊埠 25 上公開，並確認 SNAT 隱藏的原始來源 IP 位址，是否這可預期的任何郵件主機 telnet。</span><span class="sxs-lookup"><span data-stu-id="2503e-539">Run telnet to any mail host that you expose on port 25 and verify that SNAT is hiding the original source IP address if this is expected.</span></span>
  
<span data-ttu-id="2503e-540">請記住，同時部署 Office 365 具有您需要確保這兩個網路組態的 ExpressRoute ExpressRoute 連線的最佳方式設計，而且您也已最佳化其他元件您的網路，例如用戶端電腦上。</span><span class="sxs-lookup"><span data-stu-id="2503e-540">Keep in mind that while deploying Office 365 with an ExpressRoute connection you'll need to ensure both the network configuration for ExpressRoute is optimally designed and you've also optimized the other components on your network such as client computers.</span></span> <span data-ttu-id="2503e-541">除了使用這個規劃指南來疑難排解您可能會有未接的步驟，我們也已寫入[效能疑難排解規劃 Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) 。</span><span class="sxs-lookup"><span data-stu-id="2503e-541">In addition to using this planning guide to troubleshoot the steps you may have missed, we also have written a [Performance troubleshooting plan for Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .</span></span>
  
<span data-ttu-id="2503e-542">您可以使用下列短連結返回這裡：[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span><span class="sxs-lookup"><span data-stu-id="2503e-542">Here's a short link you can use to come back: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="2503e-543">相關主題</span><span class="sxs-lookup"><span data-stu-id="2503e-543">Related Topics</span></span>

[<span data-ttu-id="2503e-544">評估 Office 365 的網路連線能力</span><span class="sxs-lookup"><span data-stu-id="2503e-544">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
[<span data-ttu-id="2503e-545">Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="2503e-545">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="2503e-546">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="2503e-546">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="2503e-547">使用 ExpressRoute for Office 365 進行路由傳送</span><span class="sxs-lookup"><span data-stu-id="2503e-547">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="2503e-548">使用 ExpressRoute for Office 365 進行網路規劃</span><span class="sxs-lookup"><span data-stu-id="2503e-548">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="2503e-549">使用 BGP 社群中 ExpressRoute for Office 365 案例 （預覽）</span><span class="sxs-lookup"><span data-stu-id="2503e-549">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="2503e-550">商務用 Skype Online 中的媒體品質和網路連線效能</span><span class="sxs-lookup"><span data-stu-id="2503e-550">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="2503e-551">針對商務用 Skype Online 最佳化您的網路</span><span class="sxs-lookup"><span data-stu-id="2503e-551">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[<span data-ttu-id="2503e-552">ExpressRoute 與 QoS skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="2503e-552">ExpressRoute and QoS in Skype for Business Online</span></span>](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[<span data-ttu-id="2503e-553">使用 ExpressRoute 的通話流程</span><span class="sxs-lookup"><span data-stu-id="2503e-553">Call flow using ExpressRoute</span></span>](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[<span data-ttu-id="2503e-554">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="2503e-554">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="2503e-555">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="2503e-555">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
  
[<span data-ttu-id="2503e-556">Office 365 URL 與 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="2503e-556">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="2503e-557">Office 365 網路與效能調整</span><span class="sxs-lookup"><span data-stu-id="2503e-557">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
