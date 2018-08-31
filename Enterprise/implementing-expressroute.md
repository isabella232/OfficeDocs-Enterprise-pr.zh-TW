---
title: 實作 ExpressRoute for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
ms.audience: ITPro
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
description: Office 365 ExpressRoute 替代路由路徑為提供許多網際網路對向 Office 365 服務。Office 365 ExpressRoute 的架構根據公告公用 IP 前置詞之已可存取網際網路的後續可轉散發至那些 IP 前置字元的您已佈建 ExpressRoute 電路到的 Office 365 服務您的網路。使用 ExpressRoute 有效地啟用數個不同路由路徑，透過網際網路與透過 ExpressRoute，許多 Office 365 服務。此狀態的路由網路上可能代表重大變更您的內部網路拓撲設計的方式。
ms.openlocfilehash: c4479a236d1419293dbd433e8d3c10a11ea5fb45
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540284"
---
# <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="8adf0-106">實作 ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="8adf0-106">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="8adf0-p102">Office 365 ExpressRoute 替代路由路徑為提供許多網際網路對向 Office 365 服務。Office 365 ExpressRoute 的架構根據公告公用 IP 前置詞之已可存取網際網路的後續可轉散發至那些 IP 前置字元的您已佈建 ExpressRoute 電路到的 Office 365 服務您的網路。使用 ExpressRoute 有效地啟用數個不同路由路徑，透過網際網路與透過 ExpressRoute，許多 Office 365 服務。此狀態的路由網路上可能代表重大變更您的內部網路拓撲設計的方式。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p102">ExpressRoute for Office 365 provides an alternate routing path to many internet facing Office 365 services. The architecture of ExpressRoute for Office 365 is based on advertising public IP prefixes of Office 365 services that are already accessible over the Internet into your provisioned ExpressRoute circuits for subsequent redistribution of those IP prefixes into your network. With ExpressRoute you effectively enable several different routing paths, through the internet and through ExpressRoute, for many Office 365 services. This state of routing on your network may represent a significant change to how your internal network topology is designed.</span></span>
  
 <span data-ttu-id="8adf0-111">**狀態：** 完整的指南 v2</span><span class="sxs-lookup"><span data-stu-id="8adf0-111">**Status:** Complete Guide v2</span></span>
  
<span data-ttu-id="8adf0-p103">您必須小心規劃 Office 365 實作您 ExpressRoute 配合如有使用路由插入至核心網路與網際網路路由透過這兩個專用的電路網路複雜性。如果您及您的小組不執行詳細的規劃和測試此指南 》 中，將體驗高風險較間歇性或連線至 Office 365 的總遺失服務啟用 ExpressRoute 電路時指派。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p103">You must carefully plan your ExpressRoute for Office 365 implementation to accommodate for the network complexities of having routing available via both a dedicated circuit with routes injected into your core network and the internet. If you and your team don't perform the detailed planning and testing in this guide, there is a high risk you'll experience intermittent or a total loss of connectivity to Office 365 services when the ExpressRoute circuit is enabled.</span></span>
  
<span data-ttu-id="8adf0-p104">若要讓成功實作，您必須分析您的基礎結構需求、 透過詳細的網路評估及設計、 謹慎規劃導入階段性與控制的方式，及建立詳細的驗證和測試計劃。大型、 分散式環境不尋常查看跨越數個月的實作。本指南的設計可協助您規劃繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p104">To have a successful implementation, you will need to analyze your infrastructure requirements, go through detailed network assessment and design, carefully plan the rollout in a staged and controlled manner, and build a detailed validation and testing plan. For a large, distributed environment it's not uncommon to see implementations span several months. This guide is designed to help you plan ahead.</span></span>
  
<span data-ttu-id="8adf0-p105">大型成功部署可能規劃採取六個月及通常包含組織包括網路、 防火牆及 Proxy 伺服器管理員、 Office 365 系統管理員、 安全性、 使用者支援、 專案中的 [從多個區域的小組成員管理及執行贊助權。您在規劃程序的投資會降低將遭遇停機時間或複雜且最耗費成本疑難排解所產生之部署失敗的可能性。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p105">Large successful deployments may take six months in planning and often include team members from many areas in the organization including networking, Firewall and Proxy server administrators, Office 365 administrators, security, end-user support, project management, and executive sponsorship. Your investment in the planning process will reduce the likelihood that you'll experience deployment failures resulting in downtime or complex and expensive troubleshooting.</span></span>
  
<span data-ttu-id="8adf0-119">我們預期啟動此實作指南之前必須完成下列先決條件。</span><span class="sxs-lookup"><span data-stu-id="8adf0-119">We expect the following pre-requisites to be completed before this implementation guide is started.</span></span>
  
1. <span data-ttu-id="8adf0-120">您已完成決定 ExpressRoute 如果是建議與核准的網路評估。</span><span class="sxs-lookup"><span data-stu-id="8adf0-120">You've completed a network assessment to determine if ExpressRoute is recommended and approved.</span></span>

2. <span data-ttu-id="8adf0-p106">您已選取 ExpressRoute 網路服務提供者。尋找關於[ExpressRoute 合作夥伴和對等位置](https://azure.microsoft.com/documentation/articles/expressroute-locations/)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p106">You've selected an ExpressRoute network service provider. Find details about the [ExpressRoute partners and peering locations](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span>

3. <span data-ttu-id="8adf0-123">您已閱讀並瞭解[ExpressRoute 文件](https://azure.microsoft.com/documentation/services/expressroute/)與內部網路能夠符合 ExpressRoute 必要條件端對端。</span><span class="sxs-lookup"><span data-stu-id="8adf0-123">You've already read and understand the [ExpressRoute documentation](https://azure.microsoft.com/documentation/services/expressroute/) and your internal network is able to meet ExpressRoute pre-requisites end to end.</span></span>

4. <span data-ttu-id="8adf0-124">小組擁有 「 讀取的所有公用指引和文件[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)、 [https://aka.ms/ert](https://aka.ms/ert)，並保存的[Office 365 訓練的 Azure ExpressRoute](https://channel9.msdn.com/series/aer)數列 Channel 9 來了解重要技術詳細資料包括：</span><span class="sxs-lookup"><span data-stu-id="8adf0-124">Your team has read all of the public guidance and documentation at [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert), and watched the [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to gain an understanding of critical technical details including:</span></span>

      - <span data-ttu-id="8adf0-125">Saas 和服務的網際網路相依性。</span><span class="sxs-lookup"><span data-stu-id="8adf0-125">The internet dependencies of SaaS services.</span></span>

      - <span data-ttu-id="8adf0-126">如何避免非對稱的路由和處理複雜的路由。</span><span class="sxs-lookup"><span data-stu-id="8adf0-126">How to avoid asymmetric routes and handle complex routing.</span></span>

      - <span data-ttu-id="8adf0-127">若要併入周邊安全性、 可用性及應用程式層級控制項的方式。</span><span class="sxs-lookup"><span data-stu-id="8adf0-127">How to incorporate perimeter security, availability, and application level controls.</span></span>

## <a name="begin-by-gathering-requirements"></a><span data-ttu-id="8adf0-128">首先請收集需求</span><span class="sxs-lookup"><span data-stu-id="8adf0-128">Begin by gathering requirements</span></span>
<span data-ttu-id="8adf0-129"><a name="requirements"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-129"></span></span>

<span data-ttu-id="8adf0-p107">啟動決定哪些功能與您要採用在組織內的服務。您需要決定將使用的不同 Office 365 服務的功能和您網路上的位置會裝載使用這些功能的人員。您要新增網路屬性的使用情況的型錄，每個這些案例需要;例如輸入及輸出的網路流量流向與 Office 365 端點是否可透過 ExpressRoute 或不。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p107">Start by determining which features and services you plan to adopt within your organization. You need to determine which features of the different Office 365 services will be used and which locations on your network will host people using those features. With the catalog of scenarios, you need to add the network attributes that each of those scenarios require; such as inbound and outbound network traffic flows and if the Office 365 endpoints are available over ExpressRoute or not.</span></span>
  
<span data-ttu-id="8adf0-133">若要收集組織的需求：</span><span class="sxs-lookup"><span data-stu-id="8adf0-133">To gather your organization's requirements:</span></span>
  
- <span data-ttu-id="8adf0-p108">目錄貴組織要使用的 Office 365 服務的輸入和輸出網路流量。請洽詢 Office 365 Url 和 IP 位址範圍] 頁面上的不同 Office 365 案例需要的流程描述。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p108">Catalog the inbound and outbound network traffic for the Office 365 services your organization is using. Consult Office 365 URLs and IP address ranges page for the description of flows that different Office 365 scenarios require.</span></span>

- <span data-ttu-id="8adf0-136">收集現有的網路拓撲顯示內部 WAN 骨幹和拓撲的詳細資料、 衛星網站，最後一個哩使用者連線，路由傳送至網路外圍輸出點與 proxy 服務連線的文件。</span><span class="sxs-lookup"><span data-stu-id="8adf0-136">Gather documentation of existing network topology showing details of your internal WAN backbone and topology, connectivity of satellite sites, last mile user connectivity, routing to network perimeter egress points, and proxy services.</span></span>

  - <span data-ttu-id="8adf0-137">找出在 Office 365 與其他 Microsoft 服務會連線至，顯示網際網路和建議的 ExpressRoute 連線路徑的網路圖表上的輸入的服務端點。</span><span class="sxs-lookup"><span data-stu-id="8adf0-137">Identify inbound service endpoints on the network diagrams that Office 365 and other Microsoft services will connect to, showing both internet and proposed ExpressRoute connection paths.</span></span>

  - <span data-ttu-id="8adf0-138">找出所有地理使用者位置和位置的位置目前具有網際網路的輸出和建議讓輸出至 ExpressRoute 對等位置的哪個位置之間的 WAN 連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-138">Identify all geographic user locations and WAN connectivity between locations along with which locations currently have an egress to the internet and which locations are proposed to have an egress to an ExpressRoute peering location.</span></span>

  - <span data-ttu-id="8adf0-139">找出所有 edge 裝置，例如 proxy、 防火牆，以此類推以及目錄流程不必透過網際網路和 ExpressRoute 及其關聯性。</span><span class="sxs-lookup"><span data-stu-id="8adf0-139">Identify all edge devices, such as proxies, firewalls, and so on and catalog their relationship to flows going over the Internet and ExpressRoute.</span></span>

  - <span data-ttu-id="8adf0-140">文件是否一般使用者可存取之網際網路和 ExpressRoute 流程透過直接路由或間接的應用程式 proxy 的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="8adf0-140">Document whether end users will access Office 365 services via direct routing or indirect application proxy for both Internet and ExpressRoute flows.</span></span>

- <span data-ttu-id="8adf0-141">新增您的租用戶的位置，且符合-我網狀圖的位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-141">Add the location of your tenant and meet-me locations to your network diagram.</span></span>

- <span data-ttu-id="8adf0-p109">評估預期及觀察到的網路效能與延遲特性從主要使用者位置到 Office 365。請記住 Office 365 是一組通用且分散式的服務和使用者會連線至可能其租用戶的位置不同的位置。此原因，建議測量及透過 ExpressRoute 和網際網路連線最佳化的使用者與最接近的 Microsoft 通用網路邊緣之間的延遲。從網路評估您發現項目可用於幫助完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p109">Estimate the expected and observed network performance and latency characteristics from major user locations to Office 365. Keep in mind that Office 365 is a global and distributed set of services and users will be connecting to locations that may be different from the location of their tenant. For this reason, it is recommended to measure and optimize for latency between the user and the closest edge of Microsoft global network over ExpressRoute and Internet connections. You can use your findings from the network assessment to aid with this task.</span></span>

- <span data-ttu-id="8adf0-p110">列出公司網路安全性及必須符合新 ExpressRoute 連線的高可用性需求。例如，如何使用者繼續取得 Office 365 存取網際網路的輸出或 ExpressRoute 電路失敗的情況下。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p110">List company network security and high availability requirements that need to be met with the new ExpressRoute connection. For example, how do users continue to get access to Office 365 in the event of the Internet egress or ExpressRoute circuit failure.</span></span>

- <span data-ttu-id="8adf0-p111">文件的輸入和輸出的 Office 365 網路流程會使用網際網路的路徑和這將會使用 ExpressRoute。說明如何在使用者的地理位置和您的內部網路拓撲的詳細資料可能需要為一位使用者位置以另一個不同的計劃。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p111">Document which inbound and outbound Office 365 network flows will use the Internet path and which will use ExpressRoute. The specifics of geographical locations of your users and details of your on-premises network topology may require the plan to be different from one user location to another.</span></span>

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a><span data-ttu-id="8adf0-150">型錄輸出及輸入網路流量</span><span class="sxs-lookup"><span data-stu-id="8adf0-150">Catalog your outbound and inbound network traffic</span></span>
<span data-ttu-id="8adf0-151"><a name="trafficCatalog"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-151"></span></span>

<span data-ttu-id="8adf0-p112">降至最低的路由和其他網路複雜性，我們建議您使用僅 ExpressRoute for Office 365 之所需透過專用連線因法規需求或因網路評估移網路流量流程。此外，我們建議您以不同和不同的階段實作專案的階段 ExpressRoute 路由及方法輸出及輸入網路流量流程的範圍。部署 Office 365 ExpressRoute 剛剛使用者起始輸出網路流量流向和離開撥入的網路流量順利通過網際網路可協助控制增加的拓樸的複雜度及其他的 [的簡介 （英文） 風險的非對稱路由的可能性。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p112">To minimize routing and other network complexities, we recommend that you only use ExpressRoute for Office 365 for the network traffic flows that are required to go over a dedicated connection due to regulatory requirements or as the result of the network assessment. Additionally, we recommend that you stage the scope of ExpressRoute routing and approach outbound and inbound network traffic flows as different and distinct stages of the implementation project. Deploy ExpressRoute for Office 365 for just user initiated outbound network traffic flows and leave inbound network traffic flows across the Internet can help to control the increase in topological complexity and risks of introducing additional asymmetric routing possibilities.</span></span>
  
<span data-ttu-id="8adf0-155">您的網路流量目錄應該包含您必須在內部網路與 Microsoft 之間的所有輸入及輸出的網路連線的清單。</span><span class="sxs-lookup"><span data-stu-id="8adf0-155">Your network traffic catalog should contain listings of all the inbound and outbound network connections that you'll have between your on-premises network and Microsoft.</span></span>
  
- <span data-ttu-id="8adf0-p113">輸出網路流量流向是其中連線從內部部署環境，例如從起始內部用戶端或伺服器與 Microsoft 服務的目的地任何案例。這些連線可能至 Office 365 直接或間接，例如時連線會通過 proxy 伺服器、 防火牆或其他網路裝置路徑至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p113">Outbound network traffic flows are any scenarios where a connection is initiated from your on-premises environment, such as from internal clients or servers, with a destination of the Microsoft services. These connections may be direct to Office 365 or indirect, such as when the connection goes through proxy servers, firewalls, or other networking devices on the path to Office 365.</span></span>

- <span data-ttu-id="8adf0-p114">輸入的網路流量流向是連接位置從 Microsoft cloud 起始至內部部署主機任何案例。這些連線通常需要透過防火牆和客戶安全性原則需要的外部起始之流程其他安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p114">Inbound network traffic flows are any scenarios where a connection is initiated from the Microsoft cloud to an on-premises host. These connections typically need to go through firewall and other security infrastructure that customer security policy requires for externally originated flows.</span></span>

<span data-ttu-id="8adf0-160">閱讀本文以決定哪些服務會傳送的輸入的流量，並尋找[Office 365 中標示為**Office 365 ExpressRoute**欄[與 Office 365 ExpressRoute 路由](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)**確保路由對稱性來看**節端點](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)參考文章來決定其餘的連線資訊。</span><span class="sxs-lookup"><span data-stu-id="8adf0-160">Read the **Ensuring route symmetry** section of the article [Routing with ExpressRoute for Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) to determine which services will send inbound traffic and look for the column marked **ExpressRoute for Office 365** in the [Office 365 endpoints](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) reference article to determine the rest of the connectivity information.</span></span>
  
<span data-ttu-id="8adf0-161">每個服務所需的輸出連線，建議您說明包括網路路由、 proxy 設定、 封包檢查服務的計劃的連線和頻寬需求。</span><span class="sxs-lookup"><span data-stu-id="8adf0-161">For each service that requires an outbound connection, you'll want to describe the planned connectivity for the service including network routing, proxy configuration, packet inspection, and bandwidth needs.</span></span>
  
<span data-ttu-id="8adf0-p115">每個服務所需的輸入的連線，您將需要一些額外的資訊。Microsoft 雲端中的伺服器將會建立您的內部網路的連線。若要確保正確地進行連線，您將想要說明此連線，包括; 的所有層面公用 DNS 項目會接受這些輸入的連線的服務、 CIDR 格式化 IPv4 IP 位址的 ISP 設備的相關資訊及如何輸入的 NAT 或來源 NAT 處理這些連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p115">For each service that requires an inbound connection, you'll need some additional information. Servers in the Microsoft cloud will establish connections to your on-premises network. to ensure the connections are made correctly, you'll want to describe all aspects of this connectivity, including; the public DNS entries for the services that will accept these inbound connections, the CIDR formatted IPv4 IP addresses, which ISP equipment is involved, and how inbound NAT or source NAT is handled for these connections.</span></span>
  
<span data-ttu-id="8adf0-p116">輸入的連線應該檢閱不論它們是否連線透過網際網路或以確保非對稱式路由 ExpressRoute 尚未引進。在某些情況下，在內部部署需要的其他 Microsoft 和非 Microsoft 服務可存取 Office 365 服務也啟動 5 到的傳入的連線的端點。很重要的啟用 ExpressRoute 路由傳送至 Office 365 進行這些服務不會自動換行其他案例。在許多情況下，客戶可能需要實作特定變更其內部網路，例如來源架構以確定從 Microsoft 輸入的排列在啟用 ExpressRoute 之後仍然會對稱的 NAT。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p116">Inbound connections should be reviewed regardless of whether they're connecting over the internet or ExpressRoute to ensure asymmetric routing hasn't been introduced. In some cases, on-premises endpoints that Office 365 services initiate inbound connections to may also need to be accessed by other Microsoft and non-Microsoft services. It is paramount that enabling ExpressRoute routing to these services for Office 365 purposes doesn't break other scenarios. In many cases, customers may need to implement specific changes to their internal network, such as source based NAT, to ensure that inbound flows from Microsoft remain symmetric after ExpressRoute is enabled.</span></span>
  
<span data-ttu-id="8adf0-p117">以下是範例詳細資料所需的層級。在此例中 Exchange 混合式會路由傳送至內部部署系統透過 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p117">Here's a sample of the level of detail required. In this case Exchange Hybrid would route to the on-premises system over ExpressRoute.</span></span>

|<span data-ttu-id="8adf0-171">**連線屬性**</span><span class="sxs-lookup"><span data-stu-id="8adf0-171">**Connection property**</span></span>|<span data-ttu-id="8adf0-172">**值**</span><span class="sxs-lookup"><span data-stu-id="8adf0-172">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8adf0-173">**網路流量方向**</span><span class="sxs-lookup"><span data-stu-id="8adf0-173">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="8adf0-174">輸入</span><span class="sxs-lookup"><span data-stu-id="8adf0-174">Inbound</span></span>  <br/> |
|<span data-ttu-id="8adf0-175">**服務**</span><span class="sxs-lookup"><span data-stu-id="8adf0-175">**Service**</span></span> <br/> |<span data-ttu-id="8adf0-176">Exchange 混合式</span><span class="sxs-lookup"><span data-stu-id="8adf0-176">Exchange Hybrid</span></span>  <br/> |
|<span data-ttu-id="8adf0-177">**公用 Office 365 端點 （來源）**</span><span class="sxs-lookup"><span data-stu-id="8adf0-177">**Public Office 365 endpoint (source)**</span></span> <br/> |<span data-ttu-id="8adf0-178">Exchange Online （IP 位址）</span><span class="sxs-lookup"><span data-stu-id="8adf0-178">Exchange Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="8adf0-179">**公用內部部署端點 （目的地）**</span><span class="sxs-lookup"><span data-stu-id="8adf0-179">**Public On-Premises Endpoint (destination)**</span></span> <br/> |<span data-ttu-id="8adf0-180">5.5.5.5</span><span class="sxs-lookup"><span data-stu-id="8adf0-180">5.5.5.5</span></span>  <br/> |
|<span data-ttu-id="8adf0-181">**公用 （網際網路） DNS 項目**</span><span class="sxs-lookup"><span data-stu-id="8adf0-181">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="8adf0-182">Autodiscover.contoso.com</span><span class="sxs-lookup"><span data-stu-id="8adf0-182">Autodiscover.contoso.com</span></span>  <br/> |
|<span data-ttu-id="8adf0-183">**這個內部部署端點要使用的其他 (非 Office 365) Microsoft 服務**</span><span class="sxs-lookup"><span data-stu-id="8adf0-183">**Will this on-premises endpoint be used for by other (non-Office 365) Microsoft services**</span></span> <br/> |<span data-ttu-id="8adf0-184">否</span><span class="sxs-lookup"><span data-stu-id="8adf0-184">No</span></span>  <br/> |
|<span data-ttu-id="8adf0-185">**這個內部部署端點會使用在網際網路上的使用者/系統**</span><span class="sxs-lookup"><span data-stu-id="8adf0-185">**Will this on-premises endpoint be used by users/systems on the Internet**</span></span> <br/> |<span data-ttu-id="8adf0-186">是</span><span class="sxs-lookup"><span data-stu-id="8adf0-186">Yes</span></span>  <br/> |
|<span data-ttu-id="8adf0-187">**透過公開端點發佈的內部系統**</span><span class="sxs-lookup"><span data-stu-id="8adf0-187">**Internal systems published through public endpoints**</span></span> <br/> |<span data-ttu-id="8adf0-188">Exchange Server 用戶端存取角色 （內部） 192.168.101、 192.168.102、 192.168.103</span><span class="sxs-lookup"><span data-stu-id="8adf0-188">Exchange Server client access role (on-premises) 192.168.101, 192.168.102, 192.168.103</span></span>  <br/> |
|<span data-ttu-id="8adf0-189">**IP 通告的公用端點**</span><span class="sxs-lookup"><span data-stu-id="8adf0-189">**IP advertisement of the public endpoint**</span></span> <br/> |<span data-ttu-id="8adf0-190">**網際網路**： 5.5.0.0/16</span><span class="sxs-lookup"><span data-stu-id="8adf0-190">**To Internet**: 5.5.0.0/16</span></span>  <br/> <span data-ttu-id="8adf0-191">**以 ExpressRoute**: 5.5.5.0/24</span><span class="sxs-lookup"><span data-stu-id="8adf0-191">**To ExpressRoute**: 5.5.5.0/24</span></span>  <br/> |
|<span data-ttu-id="8adf0-192">**安全性/周邊控制項**</span><span class="sxs-lookup"><span data-stu-id="8adf0-192">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="8adf0-193">**網際網路路徑**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="8adf0-193">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="8adf0-194">**ExpressRoute 路徑**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="8adf0-194">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="8adf0-195">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="8adf0-195">**High Availability**</span></span> <br/> |<span data-ttu-id="8adf0-196">主動/主動跨地理冗餘 2</span><span class="sxs-lookup"><span data-stu-id="8adf0-196">Active/Active across 2 geo-redundant</span></span>  <br/> <span data-ttu-id="8adf0-197">ExpressRoute 電路-芝加哥與 Dallas</span><span class="sxs-lookup"><span data-stu-id="8adf0-197">ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="8adf0-198">**路徑對稱性來看控制項**</span><span class="sxs-lookup"><span data-stu-id="8adf0-198">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="8adf0-199">**方法**： 來源 NAT</span><span class="sxs-lookup"><span data-stu-id="8adf0-199">**Method**: Source NAT</span></span>  <br/> <span data-ttu-id="8adf0-200">**網際網路路徑**： 來源 NAT 輸入 192.168.5.5 的連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-200">**Internet path**: Source NAT inbound connections to 192.168.5.5</span></span>  <br/> |<span data-ttu-id="8adf0-201">**ExpressRoute 路徑**： 來源 NAT 連線 192.168.1.0 (Chicago) 和 192.168.2.0 (Dallas)</span><span class="sxs-lookup"><span data-stu-id="8adf0-201">**ExpressRoute path**: Source NAT connections to 192.168.1.0 (Chicago) and 192.168.2.0 (Dallas)</span></span>  <br/> |

<span data-ttu-id="8adf0-202">以下是範例只有在輸出的服務：</span><span class="sxs-lookup"><span data-stu-id="8adf0-202">Here's a sample of a service that is outbound only:</span></span>
|<span data-ttu-id="8adf0-203">**連線屬性**</span><span class="sxs-lookup"><span data-stu-id="8adf0-203">**Connection property**</span></span>|<span data-ttu-id="8adf0-204">**值**</span><span class="sxs-lookup"><span data-stu-id="8adf0-204">**Value**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8adf0-205">**網路流量方向**</span><span class="sxs-lookup"><span data-stu-id="8adf0-205">**Network traffic direction**</span></span> <br/> |<span data-ttu-id="8adf0-206">輸出</span><span class="sxs-lookup"><span data-stu-id="8adf0-206">Outbound</span></span>  <br/> |
|<span data-ttu-id="8adf0-207">**服務**</span><span class="sxs-lookup"><span data-stu-id="8adf0-207">**Service**</span></span> <br/> |<span data-ttu-id="8adf0-208">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="8adf0-208">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="8adf0-209">**內部部署端點 （來源）**</span><span class="sxs-lookup"><span data-stu-id="8adf0-209">**On-premises endpoint (source)**</span></span> <br/> |<span data-ttu-id="8adf0-210">使用者工作站</span><span class="sxs-lookup"><span data-stu-id="8adf0-210">User workstation</span></span>  <br/> |
|<span data-ttu-id="8adf0-211">**公用 Office 365 端點 （目的地）**</span><span class="sxs-lookup"><span data-stu-id="8adf0-211">**Public Office 365 endpoint (destination)**</span></span> <br/> |<span data-ttu-id="8adf0-212">SharePoint Online （IP 位址）</span><span class="sxs-lookup"><span data-stu-id="8adf0-212">SharePoint Online (IP addresses)</span></span>  <br/> |
|<span data-ttu-id="8adf0-213">**公用 （網際網路） DNS 項目**</span><span class="sxs-lookup"><span data-stu-id="8adf0-213">**Public (Internet) DNS entry**</span></span> <br/> |<span data-ttu-id="8adf0-214">\*。 sharepoint.com （和其他的 Fqdn）</span><span class="sxs-lookup"><span data-stu-id="8adf0-214">\*.sharepoint.com (and additional FQDNs)</span></span>  <br/> |
|<span data-ttu-id="8adf0-215">**CDN 轉介**</span><span class="sxs-lookup"><span data-stu-id="8adf0-215">**CDN Referrals**</span></span> <br/> |<span data-ttu-id="8adf0-216">cdn.sharepointonline.com （和其他的 Fqdn）-CDN 提供者所維護的 IP 位址)</span><span class="sxs-lookup"><span data-stu-id="8adf0-216">cdn.sharepointonline.com (and additional FQDNs) - IP addresses maintained by CDN providers)</span></span>  <br/> |
|<span data-ttu-id="8adf0-217">**IP 通告和使用中的 NAT**</span><span class="sxs-lookup"><span data-stu-id="8adf0-217">**IP advertisement and NAT in use**</span></span> <br/> |<span data-ttu-id="8adf0-218">**網際網路路徑/來源 NAT**: 1.1.1.0/24</span><span class="sxs-lookup"><span data-stu-id="8adf0-218">**Internet path/Source NAT**: 1.1.1.0/24</span></span>  <br/> <span data-ttu-id="8adf0-219">**ExpressRoute 路徑/來源 NAT**: 1.1.2.0/24 (Chicago) 和 1.1.3.0/24 (Dallas)</span><span class="sxs-lookup"><span data-stu-id="8adf0-219">**ExpressRoute path/Source NAT**: 1.1.2.0/24 (Chicago) and 1.1.3.0/24 (Dallas)</span></span>  <br/> |
|<span data-ttu-id="8adf0-220">**連線方法**</span><span class="sxs-lookup"><span data-stu-id="8adf0-220">**Connectivity method**</span></span> <br/> |<span data-ttu-id="8adf0-221">**網際網路**： 透過第 7 層 proxy （.pac 檔案）</span><span class="sxs-lookup"><span data-stu-id="8adf0-221">**Internet**: via layer 7 proxy (.pac file)</span></span>  <br/> <span data-ttu-id="8adf0-222">**ExpressRoute**： 直接路由 (沒有 proxy)</span><span class="sxs-lookup"><span data-stu-id="8adf0-222">**ExpressRoute**: direct routing (no proxy)</span></span>  <br/> |
|<span data-ttu-id="8adf0-223">**安全性/周邊控制項**</span><span class="sxs-lookup"><span data-stu-id="8adf0-223">**Security/Perimeter Controls**</span></span> <br/> |<span data-ttu-id="8adf0-224">**網際網路路徑**： DeviceID_002</span><span class="sxs-lookup"><span data-stu-id="8adf0-224">**Internet path**: DeviceID_002</span></span>  <br/> <span data-ttu-id="8adf0-225">**ExpressRoute 路徑**： DeviceID_003</span><span class="sxs-lookup"><span data-stu-id="8adf0-225">**ExpressRoute path**: DeviceID_003</span></span>  <br/> |
|<span data-ttu-id="8adf0-226">**高可用性**</span><span class="sxs-lookup"><span data-stu-id="8adf0-226">**High Availability**</span></span> <br/> |<span data-ttu-id="8adf0-227">**網際網路路徑**： 備援網際網路的輸出</span><span class="sxs-lookup"><span data-stu-id="8adf0-227">**Internet path**: Redundant internet egress</span></span>  <br/> <span data-ttu-id="8adf0-228">**ExpressRoute 路徑**： 主動/主動 '作用馬鈴薯' 路由跨 2 地理位置設為備援的 ExpressRoute 電路-芝加哥與 Dallas</span><span class="sxs-lookup"><span data-stu-id="8adf0-228">**ExpressRoute path**: Active/Active 'hot potato' routing across 2 geo-redundant ExpressRoute circuits - Chicago and Dallas</span></span>  <br/> |
|<span data-ttu-id="8adf0-229">**路徑對稱性來看控制項**</span><span class="sxs-lookup"><span data-stu-id="8adf0-229">**Path symmetry control**</span></span> <br/> |<span data-ttu-id="8adf0-230">**方法**： 來源的所有連線的 NAT</span><span class="sxs-lookup"><span data-stu-id="8adf0-230">**Method**: Source NAT for all connections</span></span>  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a><span data-ttu-id="8adf0-231">網路拓撲設計區域的連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-231">Your network topology design with regional connectivity</span></span>
<span data-ttu-id="8adf0-232"><a name="topology"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-232"></span></span>

<span data-ttu-id="8adf0-p118">一旦您了解其相關聯的網路流量流向且服務，您可以建立同時這些新的連線需求並說明您在變更將會使用 ExpressRoute for Office 365 的網狀圖。將圖表應該包括：</span><span class="sxs-lookup"><span data-stu-id="8adf0-p118">Once you understand the services and their associated network traffic flows, you can create a network diagram that incorporates these new connectivity requirements and illustrates the changes you'll make to use ExpressRoute for Office 365. Your diagram should include:</span></span>
  
1. <span data-ttu-id="8adf0-235">其中 Office 365 及其他服務會從存取的所有使用者位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-235">All user locations where Office 365 and other services will be accessed from.</span></span>

2. <span data-ttu-id="8adf0-236">所有網際網路和 ExpressRoute 輸出點。</span><span class="sxs-lookup"><span data-stu-id="8adf0-236">All internet and ExpressRoute egress points.</span></span>

3. <span data-ttu-id="8adf0-237">所有輸出及輸入裝置的管理連線和網路，包括路由器和防火牆、 應用程式 proxy 伺服器入侵偵測/防護登出。</span><span class="sxs-lookup"><span data-stu-id="8adf0-237">All outbound and inbound devices that manage connectivity in and out of the network, including routers, firewalls, application proxy servers, and intrusion detection/prevention.</span></span>

4. <span data-ttu-id="8adf0-238">所有的輸入流量，例如接受來自 ADFS 連線的內部 ADFS 伺服器內部目的地 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8adf0-238">Internal destinations for all inbound traffic, such as internal ADFS servers that accept connections from the ADFS web application proxy servers.</span></span>

5. <span data-ttu-id="8adf0-239">將通告的所有 IP 子網路的型錄</span><span class="sxs-lookup"><span data-stu-id="8adf0-239">Catalog of all IP subnets that will be advertised</span></span>

6. <span data-ttu-id="8adf0-240">識別人員會存取來自 Office 365 及列出開會每個位置-我將用於 ExpressRoute 的位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-240">Identify each location where people will access Office 365 from and list the meet-me locations that will be used for ExpressRoute.</span></span>

7. <span data-ttu-id="8adf0-241">位置中某些部分的內部網路拓撲，其中會接受來自 ExpressRoute 學到的 Microsoft IP 前置詞、 篩選和傳播到。</span><span class="sxs-lookup"><span data-stu-id="8adf0-241">Locations and portions of your internal network topology, where Microsoft IP prefixes learned from ExpressRoute will be accepted, filtered and propagated to.</span></span>

8. <span data-ttu-id="8adf0-242">網路拓撲應說明每個網路區段的地理位置及如何連線到 Microsoft network 透過 ExpressRoute 和/或網際網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-242">The network topology should illustrate the geographic location of each network segment and how it connects to the Microsoft network over ExpressRoute and/or the Internet.</span></span>

<span data-ttu-id="8adf0-243">下圖顯示每個位置其中人員將會使用從 Office 365 與 Office 365 的輸入和輸出路由通告。</span><span class="sxs-lookup"><span data-stu-id="8adf0-243">The diagram below shows each location where people will be using Office 365 from along with the inbound and outbound routing advertisements to Office 365.</span></span>
  
![ExpressRoute 區域地理開會-我](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
<span data-ttu-id="8adf0-245">輸出流量的人員來存取 Office 365 中三種方法之一：</span><span class="sxs-lookup"><span data-stu-id="8adf0-245">For outbound traffic, the people access Office 365 in one of three ways:</span></span>
  
1. <span data-ttu-id="8adf0-246">透過 meet-我北美加利福尼亞中人員的位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-246">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="8adf0-247">透過 meet-我在香港特別行政區人員香港特別行政區] 中的位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-247">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="8adf0-248">透過孟加拉其中有較少的人員，而沒有 ExpressRoute 電路佈建在網際網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-248">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
<span data-ttu-id="8adf0-250">同樣地，來自 Office 365 的輸入的網路流量會傳回三種方式之一：</span><span class="sxs-lookup"><span data-stu-id="8adf0-250">Similarly, the inbound network traffic from Office 365 returns in one of three ways:</span></span>
  
1. <span data-ttu-id="8adf0-251">透過 meet-我北美加利福尼亞中人員的位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-251">Through a meet-me location in North America for the people in California.</span></span>

2. <span data-ttu-id="8adf0-252">透過 meet-我在香港特別行政區人員香港特別行政區] 中的位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-252">Through a meet-me location in Hong Kong for the people in Hong Kong.</span></span>

3. <span data-ttu-id="8adf0-253">透過孟加拉其中有較少的人員，而沒有 ExpressRoute 電路佈建在網際網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-253">Through the internet in Bangladesh where there are fewer people and no ExpressRoute circuit provisioned.</span></span>

![輸入的連線的區域圖](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a><span data-ttu-id="8adf0-255">決定適當的開會-我位置</span><span class="sxs-lookup"><span data-stu-id="8adf0-255">Determine the appropriate meet-me location</span></span>

<span data-ttu-id="8adf0-p119">將選取範圍開會-我位置，亦即其中 ExpressRoute 電路連線到 Microsoft 網路的網路的實體位置、 會影響人員存取 Office 365 中的位置的位置。提供 saas 和，為 Office 365 不會運作下 IaaS 或 PaaS 區域模型 Azure 沒有相同的方式。而是 Office 365 是一分散式共同作業服務的使用者可能需要跨多個資料中心和區域，可能不一定會在相同的位置或主控使用者的租用戶的地區連線到端點。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p119">The selection of meet-me locations, which are the physical location where your ExpressRoute circuit connects your network to the Microsoft network, is influenced by the locations where people will access Office 365 from. As a SaaS offering, Office 365 does not operate under the IaaS or PaaS regional model in the same way Azure does. Instead, Office 365 is a distributed set of collaboration services, where users may need to connect to endpoints across multiple datacenters and regions, which may not necessarily be in the same location or region where the user's tenant is hosted.</span></span>
  
<span data-ttu-id="8adf0-p120">這表示您必須制定選取 meet 時最重要的考量-我的 Office 365 ExpressRoute 位置是要從連線在組織中的人員。一般建議的最佳的 Office 365 連線會實作路由，以便至 Office 365 服務的使用者要求所交由關閉 Microsoft network 到最短的網路路徑，這通常也會被稱為 '作用馬鈴薯' 路由。例如，如果大部分的 Office 365 使用者是在一或兩個位置中，選取 meet-我最接近接近這些使用者的位置中的位置會建立最佳的設計。如果您的公司具有許多不同地區龐大的使用者人數，可能會想要考慮擁有多個 ExpressRoute 電路且符合-我位置。某些使用者位置到 Microsoft network 和 Office 365 的最短/最最佳路徑可能不是透過內部 WAN 和 ExpressRoute 開會-我點，但透過網際網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p120">This means the most important consideration you need to make when selecting meet-me locations for ExpressRoute for Office 365 is where the people in your organization will be connecting from. The general recommendation for optimal Office 365 connectivity is implement routing, so that user requests to Office 365 services are handed off into the Microsoft network over the shortest network path, this is also often being referred to as 'hot potato' routing. For example, if most of the Office 365 users are in one or two locations, selecting meet-me locations that are in the closest proximity to the location of those users will create the optimal design. If your company has large user populations in many different regions, you may want to consider having multiple ExpressRoute circuits and meet-me locations. For some of your user locations, the shortest/most optimal path into Microsoft network and Office 365, may not be through your internal WAN and ExpressRoute meet-me points, but via the Internet.</span></span>
  
<span data-ttu-id="8adf0-p121">通常時間有多個 meet-我無法選取相對接近您的使用者與區域內的位置。填寫以引導您決定下表。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p121">Often times, there are multiple meet-me locations that could be selected within a region with relative proximity to your users. Fill out the following table to guide your decisions.</span></span>

|<span data-ttu-id="8adf0-266">**計劃的 ExpressRoute 開會-我的 California 和紐約位置**</span><span class="sxs-lookup"><span data-stu-id="8adf0-266">**Planned ExpressRoute meet-me locations in California and New York**</span></span>||
|:-----|:-----|
|<span data-ttu-id="8adf0-267">位置</span><span class="sxs-lookup"><span data-stu-id="8adf0-267">Location</span></span>  <br/> |<span data-ttu-id="8adf0-268">數字的人員</span><span class="sxs-lookup"><span data-stu-id="8adf0-268">Number of people</span></span>  <br/> |<span data-ttu-id="8adf0-269">透過網際網路輸出預期 Microsoft 網路延遲</span><span class="sxs-lookup"><span data-stu-id="8adf0-269">Expected latency to Microsoft network over Internet egress</span></span>  <br/> |<span data-ttu-id="8adf0-270">預期的 ExpressRoute 透過 Microsoft 網路延遲</span><span class="sxs-lookup"><span data-stu-id="8adf0-270">Expected latency to Microsoft network over ExpressRoute</span></span>  <br/> |
|<span data-ttu-id="8adf0-271">洛杉磯</span><span class="sxs-lookup"><span data-stu-id="8adf0-271">Los Angeles</span></span>  <br/> |<span data-ttu-id="8adf0-272">10,000</span><span class="sxs-lookup"><span data-stu-id="8adf0-272">10,000</span></span>  <br/> |<span data-ttu-id="8adf0-273">~ 15ms</span><span class="sxs-lookup"><span data-stu-id="8adf0-273">~15ms</span></span>  <br/> |<span data-ttu-id="8adf0-274">~ 10 毫秒 （透過矽谷）</span><span class="sxs-lookup"><span data-stu-id="8adf0-274">~10ms (via Silicon Valley)</span></span>  <br/> |
|<span data-ttu-id="8adf0-275">華盛頓 DC</span><span class="sxs-lookup"><span data-stu-id="8adf0-275">Washington DC</span></span>  <br/> |<span data-ttu-id="8adf0-276">15000</span><span class="sxs-lookup"><span data-stu-id="8adf0-276">15,000</span></span>  <br/> |<span data-ttu-id="8adf0-277">~ 20ms</span><span class="sxs-lookup"><span data-stu-id="8adf0-277">~20ms</span></span>  <br/> |<span data-ttu-id="8adf0-278">~ 10 毫秒 （透過紐約）</span><span class="sxs-lookup"><span data-stu-id="8adf0-278">~10ms (via New York)</span></span>  <br/> |
|<span data-ttu-id="8adf0-279">Dallas</span><span class="sxs-lookup"><span data-stu-id="8adf0-279">Dallas</span></span>  <br/> |<span data-ttu-id="8adf0-280">5,000</span><span class="sxs-lookup"><span data-stu-id="8adf0-280">5,000</span></span>  <br/> |<span data-ttu-id="8adf0-281">~ 15ms</span><span class="sxs-lookup"><span data-stu-id="8adf0-281">~15ms</span></span>  <br/> |<span data-ttu-id="8adf0-282">~ 40ms （透過紐約）</span><span class="sxs-lookup"><span data-stu-id="8adf0-282">~40ms (via New York)</span></span>  <br/> |

<span data-ttu-id="8adf0-p122">之後顯示 Office 365 區域通用網路架構、 ExpressRoute 網路服務提供者是否符合-我開發位置及位置個人數量、 可用來識別是否可以進行任何最佳化。它可能也會顯示通用髮夾網路連線其中流量路由傳送至距位置以取得開會-我的位置。如果通用網路上的髮夾會發現它應該在於才能繼續執行。尋找其他開會-我的位置或使用選擇性網際網路上下文輸出點，以免發生髮夾。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p122">Once the global network architecture showing the Office 365 region, ExpressRoute network service provider meet-me locations, and the quantity of people by location has been developed, it can be used to identify if any optimizations can be made. It may also show global hairpin network connections where traffic routes to a distant location in order to get the meet-me location. If a hairpin on the global network is discovered it should be remediated before continuing. Either find another meet-me location, or use selective Internet breakout egress points to avoid the hairpin.</span></span>
  
<span data-ttu-id="8adf0-p123">第一張圖表中，會顯示 「 北美地區 」 中的兩個實體位置與客戶的範例。您可以看到辦公室位置、 Office 365 租用戶位置、 資訊及數個 ExpressRoute 選擇符合-我位置。客戶已在此範例中，選取 [開會-我順序中的兩個原則為基礎的位置：</span><span class="sxs-lookup"><span data-stu-id="8adf0-p123">The first diagram, shows an example of a customer with two physical locations in North America. You can see the information about office locations, Office 365 tenant locations, and several choices for ExpressRoute meet-me locations. In this example, the customer has selected the meet-me location based on two principles, in order:</span></span>
  
1. <span data-ttu-id="8adf0-290">最接近接近其組織中的人員。</span><span class="sxs-lookup"><span data-stu-id="8adf0-290">Closest proximity to the people in their organization.</span></span>

2. <span data-ttu-id="8adf0-291">最接近接近 Microsoft 資料中心主控 Office 365 的。</span><span class="sxs-lookup"><span data-stu-id="8adf0-291">Closest in proximity to a Microsoft datacenter where Office 365 is hosted.</span></span>

![ExpressRoute 美國地理開會-我](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
<span data-ttu-id="8adf0-p124">稍微展開此概念進一步範例多重國民客戶面臨類似的資訊和決策制定的第二個圖顯示。此客戶可以中孟加拉小型小組的十著重於得其之上的區域中的人員與小型的辦公室。沒有開會-我清奈及 Microsoft 資料中心與 Office 365 中的位置裝載於辰內所以開會-我位置就意義;不過，十人員其他電路費用遠遠繁瑣。當您在查看您的網路，您需要決定是否比花以取得其他 ExpressRoute 電路資本高效率參與您的網路之間傳送網路流量的延遲。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p124">Expanding this concept slightly further, the second diagram shows an example multi-national customer faced with similar information and decision making. This customer has a small office in Bangladesh with only a small team of ten people focused on growing their footprint in the region. There is a meet-me location in Chennai and a Microsoft datacenter with Office 365 hosted in Chennai so a meet-me location would make sense; however, for ten people, the expense of the additional circuit is burdensome. As you look at your network, you'll need to determine if the latency involved in sending your network traffic across your network is more effective than spending the capital to acquire another ExpressRoute circuit.</span></span>
  
<span data-ttu-id="8adf0-297">或者，在孟加拉十人員可能會遇到較佳的效能與比他們會路由傳送內部網路上為我們在簡介圖表中顯示及重現，透過網際網路傳送至 Microsoft network 其網路流量下面。</span><span class="sxs-lookup"><span data-stu-id="8adf0-297">Alternatively, the ten people in Bangladesh may experience better performance with their network traffic sent over the internet to the Microsoft network than they would routing on their internal network as we showed in the introductory diagrams and reproduced below.</span></span>
  
![輸出連線的區域圖](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a><span data-ttu-id="8adf0-299">建立您的 Office 365 實作計畫 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="8adf0-299">Create your ExpressRoute for Office 365 implementation plan</span></span>
<span data-ttu-id="8adf0-300"><a name="implementation"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-300"></span></span>

<span data-ttu-id="8adf0-301">實作計劃應該包含這兩種技術詳細資料的設定 ExpressRoute 當您在網路上，如下所示設定所有其他基礎結構的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8adf0-301">Your implementation plan should encompass both the technical details of configuring ExpressRoute as well as the details of configuring all the other infrastructure on your network, such as the following.</span></span>
  
- <span data-ttu-id="8adf0-302">規劃 ExpressRoute 與網際網路之間分割的服務。</span><span class="sxs-lookup"><span data-stu-id="8adf0-302">Plan which services split between ExpressRoute and Internet.</span></span>

- <span data-ttu-id="8adf0-303">規劃頻寬、 安全性、 高可用性和容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="8adf0-303">Plan for bandwidth, security, high availability and failover.</span></span>

- <span data-ttu-id="8adf0-304">設計輸入和輸出路由，包括適當的不同位置的路由路徑最佳化</span><span class="sxs-lookup"><span data-stu-id="8adf0-304">Design inbound and outbound routing, including proper routing path optimizations for different locations</span></span>

- <span data-ttu-id="8adf0-305">決定 ExpressRoute 路由至您的網路的通告最及新功能的用戶端選取網際網路或 ExpressRoute 路徑 ； 機制例如，直接路由或應用程式 proxy。</span><span class="sxs-lookup"><span data-stu-id="8adf0-305">Decide how far ExpressRoute routes will be advertised into your network and what is the mechanism for clients to select Internet or ExpressRoute path; for example, direct routing or application proxy.</span></span>

- <span data-ttu-id="8adf0-306">規劃 DNS 記錄變更，包括[寄件者原則架構](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx)項目。</span><span class="sxs-lookup"><span data-stu-id="8adf0-306">Plan DNS record changes, including [Sender Policy Framework](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) entries.</span></span>

- <span data-ttu-id="8adf0-307">規劃 NAT 策略包括輸出及輸入來源 nat。</span><span class="sxs-lookup"><span data-stu-id="8adf0-307">Plan NAT strategy including outbound and inbound source NAT.</span></span>

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a><span data-ttu-id="8adf0-308">規劃您的路由與網際網路和 ExpressRoute 網路路徑</span><span class="sxs-lookup"><span data-stu-id="8adf0-308">Plan your routing with both internet and ExpressRoute network paths</span></span>
<span data-ttu-id="8adf0-309"><a name="paths"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-309"></span></span>

- <span data-ttu-id="8adf0-310">在初始部署的所有內送的服務，例如內送電子郵件或混合式連線、 建議使用網際網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-310">For your initial deployment, all inbound services, such as inbound email or hybrid connectivity, are recommended to use the internet.</span></span>

- <span data-ttu-id="8adf0-311">規劃使用者用戶端 LAN 路由，例如[設定 PAC/WPAD 檔案](https://aka.ms/manageo365endpoints)、 預設路由、 proxy 伺服器與 BGP 路由廣告。</span><span class="sxs-lookup"><span data-stu-id="8adf0-311">Plan end user client LAN routing, such as [configuring a PAC/WPAD file](https://aka.ms/manageo365endpoints), default route, proxy servers, and BGP route advertisements.</span></span>

- <span data-ttu-id="8adf0-312">規劃外圍路由傳送，包括 proxy 伺服器、 防火牆和雲端 proxy。</span><span class="sxs-lookup"><span data-stu-id="8adf0-312">Plan perimeter routing, including proxy servers, firewalls, and cloud proxies.</span></span>

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a><span data-ttu-id="8adf0-313">規劃頻寬、 安全性、 高可用性和容錯移轉</span><span class="sxs-lookup"><span data-stu-id="8adf0-313">Plan your bandwidth, security, high availability and failover</span></span>
<span data-ttu-id="8adf0-314"><a name="availability"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-314"></span></span>

<span data-ttu-id="8adf0-p125">建立所需的每一個主要的 Office 365 工作負載的頻寬的計畫。分開評估 Exchange Online、 SharePoint Online 和 Skype 商務線上的頻寬需求。您可以使用我們提供的 Exchange Online 和 Skype 的業務上進行起始; 估計計算器不過，使用者設定檔及位置的代表性 sample 試驗測試，則需要完全了解您組織的頻寬需求。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p125">Create a plan for bandwidth required for each major Office 365 workload. Separately estimate Exchange Online, SharePoint Online, and Skype for Business Online bandwidth requirements. You can use the estimation calculators we've provided for Exchange Online and Skype for Business as a starting place; however, a pilot test with a representative sample of the user profiles and locations is required to fully understand the bandwidth needs of your organization.</span></span>
  
<span data-ttu-id="8adf0-318">新增安全性在每個網際網路和您的計劃 ExpressRoute 輸出位置的處理方式，請記住所有 ExpressRoute 連線至 Office 365 使用公用對等和仍必須符合您公司的安全性原則連接至外部的安全網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-318">Add how security is handled at each internet and ExpressRoute egress location to your plan, remember all ExpressRoute connections to Office 365 use public peering and must still be secured in accordance with your company security policies of connecting to external networks.</span></span>
  
<span data-ttu-id="8adf0-319">加入您解有哪些人員將會受到何種類型的中斷及如何這些人員將能夠以最簡單的方式執行容量滿載其工作的計劃的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8adf0-319">Add details to your plan about which people will be affected by what type of outage and how those people will be able to perform their work at full capacity in the simplest manner.</span></span>
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a><span data-ttu-id="8adf0-320">規劃頻寬需求包括 Skype 抖動、 延遲、 擁塞、 及發揮空間上的商務需求</span><span class="sxs-lookup"><span data-stu-id="8adf0-320">Plan bandwidth requirements including Skype for Business requirements on Jitter, Latency, Congestion, and Headroom</span></span>
  
<span data-ttu-id="8adf0-321">商務 online Skype 也有特定額外的網路需求[的媒體品質和 Skype 的商務 Online 中的網路連線效能](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)的文章中詳述。</span><span class="sxs-lookup"><span data-stu-id="8adf0-321">Skype for Business Online also has specific additional network requirements which are detailed in the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>
  
<span data-ttu-id="8adf0-322">請閱讀**頻寬規劃 Azure ExpressRoute** [網路規劃與 Office 365 ExpressRoute](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)一節。</span><span class="sxs-lookup"><span data-stu-id="8adf0-322">Read the section **Bandwidth planning for Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
<span data-ttu-id="8adf0-323">當執行與您的試驗使用者的頻寬評估，您可以使用我們指南;[Office 365 效能調整使用基準和效能歷程記錄](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae)。</span><span class="sxs-lookup"><span data-stu-id="8adf0-323">When performing a bandwidth assessment with your pilot users, you can use our guide; [Office 365 performance tuning using baselines and performance history](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).</span></span>
  
#### <a name="plan-for-high-availability-requirements"></a><span data-ttu-id="8adf0-324">規劃高可用性需求</span><span class="sxs-lookup"><span data-stu-id="8adf0-324">Plan for high availability requirements</span></span>
  
<span data-ttu-id="8adf0-p126">建立計畫，以符合您的需求及併入此更新的網路拓撲圖表的高可用性。請閱讀**高可用性和容錯移轉與 Azure ExpressRoute** [網路](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)規劃與 Office 365 ExpressRoute 一節。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p126">Create a plan for high availability to meet your needs and incorporate this into your updated network topology diagram. Read the section **High availability and failover with Azure ExpressRoute** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
#### <a name="plan-for-network-security-requirements"></a><span data-ttu-id="8adf0-327">如需網路安全性需求的計劃</span><span class="sxs-lookup"><span data-stu-id="8adf0-327">Plan for network security requirements</span></span>
  
<span data-ttu-id="8adf0-p127">建立計畫，以符合您的網路安全性需求及併入此更新的網路拓撲圖表。請閱讀] 區段中的[網路規劃與 Office 365 ExpressRoute](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd)**正在套用至 Office 365 案例的 Azure ExpressRoute 的安全性控制**。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p127">Create a plan to meet your network security requirements and incorporate this into your updated network topology diagram. Read the section **Applying security controls to Azure ExpressRoute for Office 365 scenarios** in [Network planning with ExpressRoute for Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).</span></span>
  
### <a name="design-outbound-service-connectivity"></a><span data-ttu-id="8adf0-330">設計外寄的服務連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-330">Design outbound service connectivity</span></span>
<span data-ttu-id="8adf0-331"><a name="outbound"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-331"></span></span>

<span data-ttu-id="8adf0-p128">Office 365 ExpressRoute 有可能不熟悉的*輸出*網路需求。主要是針對 IP 位址，代表至 Office 365 的使用者和網路遊歷輸出的網路連線至 Microsoft 來源端點必須依照下列所述的特定需求。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p128">ExpressRoute for Office 365 has  *outbound*  network requirements that may be unfamiliar. Specifically, the IP addresses that represent your users and networks to Office 365 and act as the source endpoints for outbound network connections to Microsoft must follow specific requirements outlined below.</span></span>
  
1. <span data-ttu-id="8adf0-334">端點必須是公用 IP 位址，為您的公司或電訊廠商提供 ExpressRoute 連線至您要登錄。</span><span class="sxs-lookup"><span data-stu-id="8adf0-334">The endpoints must be public IP addresses, that are registered to your company or to carrier providing ExpressRoute connectivity to you.</span></span>

2. <span data-ttu-id="8adf0-335">端點必須向 Microsoft 公告所並驗證/接受供 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="8adf0-335">The endpoints must be advertised to Microsoft and validated/accepted by ExpressRoute.</span></span>

3. <span data-ttu-id="8adf0-336">端點必須不是到同一個或多慣用路由評量與網際網路進行通告。</span><span class="sxs-lookup"><span data-stu-id="8adf0-336">The endpoints must not be advertised to the Internet with the same or more preferred routing metric.</span></span>

4. <span data-ttu-id="8adf0-337">端點必須不用於未設定透過 ExpressRoute 的 Microsoft 服務的連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-337">The endpoints must not be used for connectivity to Microsoft services that are not configured over ExpressRoute.</span></span>

<span data-ttu-id="8adf0-p129">如果您的網路設計不符合這些需求，有高風險您的使用者會體驗到 Office 365 及其他 Microsoft 服務因為路由黑色 holing 或非對稱式路由的連線失敗。這發生於 ExpressRoute，透過路由傳送至 Microsoft 服務要求但回應會路由傳送回經由網際網路，反之亦然，例如防火牆設定狀態的網路裝置會捨棄回應。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p129">If your network design doesn't meet these requirements, there is a high risk your users will experience connectivity failures to Office 365 and other Microsoft services due to route black holing or asymmetric routing. This occurs when requests to Microsoft services are routed over ExpressRoute, but responses are routed back across the internet, or vice versa, and the responses are dropped by stateful network devices such as firewalls.</span></span>
  
<span data-ttu-id="8adf0-p130">您可以使用符合上述需求的常見方法是網路的使用來源 NAT 實作為您的部分或 ExpressRoute 電信業者所提供。來源 NAT 可讓您抽象的詳細資訊與私人 IP 位址處理的網際網路網路 ExpressRoute 從和;搭配適當的 IP 路由廣告，提供簡單的機制來確保路徑對稱性來看。如果您使用專屬 ExpressRoute 對等位置的可設定狀態的網路裝置，您必須實作分開 NAT 集區中的每個 ExpressRoute 以確保路徑對稱性來看對等。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p130">The most common method you can use to meet the above requirements is to use source NAT, either implemented as a part of your network or provided by your ExpressRoute carrier. Source NAT allows you to abstract the details and private IP addressing of your internet network from ExpressRoute and; coupled with proper IP route advertisements, provide an easy mechanism to ensure path symmetry. If you're using stateful network devices that are specific to ExpressRoute peering locations, you must implement separate NAT pools for each ExpressRoute peering to ensure path symmetry.</span></span>
  
<span data-ttu-id="8adf0-343">閱讀的有關[ExpressRoute NAT 需求](https://azure.microsoft.com/documentation/articles/expressroute-nat/)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8adf0-343">Read more about the [ExpressRoute NAT requirements](https://azure.microsoft.com/documentation/articles/expressroute-nat/).</span></span>
  
<span data-ttu-id="8adf0-344">網路拓撲圖表來新增輸出連線的變更。</span><span class="sxs-lookup"><span data-stu-id="8adf0-344">Add the changes for the outbound connectivity to the network topology diagram.</span></span>
  
### <a name="design-inbound-service-connectivity"></a><span data-ttu-id="8adf0-345">設計輸入的服務連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-345">Design inbound service connectivity</span></span>
<span data-ttu-id="8adf0-346"><a name="inbound"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-346"></span></span>

<span data-ttu-id="8adf0-p131">企業版 Office 365 部署的多數 」 假設來自 Office 365 的輸入連線至內部部署服務的一些表單例如 Exchange、 SharePoint、 和 Skype 商務混合式案例、 信箱移轉和使用 ADFS 的驗證基礎結構。當 ExpressRoute 讓您在內部網路與 Microsoft 之間進行輸出連線其他路由路徑，這些輸入的連線可能不經意受到非對稱式路由]，即使您想要有這些流程繼續使用網際網路。若要確保有到網際網路的任何影響基礎輸入的流程來自 Office 365 與內部部署系統建議如下所述的一些預防措施。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p131">The majority of enterprise Office 365 deployments assume some form of inbound connectivity from Office 365 to on-premises services, such as for Exchange, SharePoint, and Skype for Business hybrid scenarios, mailbox migrations, and authentication using ADFS infrastructure. When ExpressRoute you enable an additional routing path between your on-premises network and Microsoft for outbound connectivity, these inbound connections may inadvertently be impacted by asymmetric routing, even if you intend to have those flows continue to use the Internet. A few precautions described below are recommended to ensure there is no impact to Internet based inbound flows from Office 365 to on-premises systems.</span></span>
  
<span data-ttu-id="8adf0-p132">降至最低的非對稱式路由撥入的網路流量流向風險，輸入連線的所有應使用來源 NAT 他們正在路由傳送到有路由可見性 ExpressRoute 您的網路區段之前。如果路由可見性 ExpressRoute 沒有來源 NAT 與到網路區段允許傳入的連線，要求來自 Office 365 將輸入從網際網路、 但回到 Office 365 的回應會偏好 ExpressRoute回到 Microsoft 網路，而造成非對稱式路由的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p132">To minimize the risks of asymmetric routing for inbound network traffic flows, all of the inbound connections should use source NAT before they're routed into segments of your network which have routing visibility into ExpressRoute. If the incoming connections are allowed onto a network segment with routing visibility into ExpressRoute without source NAT, requests originating from Office 365 will enter from the internet, but the response going back to Office 365 will prefer the ExpressRoute network path back to the Microsoft network, causing asymmetric routing.</span></span>
  
<span data-ttu-id="8adf0-352">您可能會考慮下列實作模式來滿足此需求其中一項：</span><span class="sxs-lookup"><span data-stu-id="8adf0-352">You may consider one of the following implementation patterns to satisfy this requirement:</span></span>
  
1. <span data-ttu-id="8adf0-353">要求路由傳送至內部網路使用網路設備如防火牆之前執行來源 NAT 或從網際網路負載平衡器上路徑至內部部署系統。</span><span class="sxs-lookup"><span data-stu-id="8adf0-353">Perform source NAT before requests are routed into your internal network using networking equipment such as firewalls or load balancers on the path from the Internet to your on-premises systems.</span></span>

2. <span data-ttu-id="8adf0-354">請確定 ExpressRoute 路由不會傳播到輸入的服務，例如前方結束伺服器的位置或反向 proxy 系統處理的網際網路連線都位於網路區段數。</span><span class="sxs-lookup"><span data-stu-id="8adf0-354">Ensure that ExpressRoute routes are not propagated to the network segments where inbound services, such as front end servers or reverse proxy systems, handling Internet connections reside.</span></span>

<span data-ttu-id="8adf0-355">明確會計這些案例您網路中並保留所有內送的網路流量流向透過網際網路它可協助部署及操作的非對稱式路由的風險降到最低。</span><span class="sxs-lookup"><span data-stu-id="8adf0-355">Explicitly accounting for these scenarios in your network and keeping all inbound network traffic flows over the Internet helps to minimize deployment and operational risk of asymmetric routing.</span></span>
  
<span data-ttu-id="8adf0-p133">可能會有您可以選擇直接一些輸入的流程透過 ExpressRoute 連線的情況。這些案例中，採取下列其他考量事項。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p133">There may be cases where you may choose to direct some inbound flows over ExpressRoute connections. For these scenarios, take the following additional considerations into account.</span></span>
  
1. <span data-ttu-id="8adf0-p134">Office 365 可以只目標內部部署端點使用公用 Ip 的。這表示，即使在內部輸入的端點只能透過 ExpressRoute 公開給 Office 365，它仍然需要具有與它相關聯的公用 IP。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p134">Office 365 can only target on-premises endpoints that use public IPs. This means that even if the on-premises inbound endpoint is only exposed to Office 365 over ExpressRoute, it still needs to have public IP associated with it.</span></span>

2. <span data-ttu-id="8adf0-p135">Office 365 服務執行以解析內部部署端點的所有 DNS 名稱解析都發生使用公用 DNS。這表示您必須註冊在網際網路上的 IP 對應至輸入的服務端點的 FQDN。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p135">All DNS name resolution that Office 365 services perform to resolve on-premises endpoints happen using public DNS. This means that you must register inbound service endpoints' FQDN to IP mappings on the Internet.</span></span>

3. <span data-ttu-id="8adf0-362">若要透過 ExpressRoute 接收傳入的網路連線，這些端點的公用 IP 子網路必須透過 ExpressRoute 通告給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="8adf0-362">In order to receive inbound network connections over ExpressRoute, the public IP subnets for these endpoints must to be advertised to Microsoft over ExpressRoute.</span></span>

4. <span data-ttu-id="8adf0-363">謹慎評估以確保該適當的安全性這些輸入的網路流量流程和網路控制項符合您的公司安全性和網路原則套用至他們。</span><span class="sxs-lookup"><span data-stu-id="8adf0-363">Carefully evaluate these inbound network traffic flows to ensure that proper security and network controls are applied to them in accordance with your company security and network policies.</span></span>

5. <span data-ttu-id="8adf0-p136">一次內部輸入的端點向 Microsoft 通告透過 ExpressRoute、 ExpressRoute 將有效成為那些端點的所有 Microsoft 服務，包括 Office 365 的慣用路由路徑。這表示端點子網路必須只用於與 Office 365 服務和 Microsoft 網站上的任何其他服務通訊。否則，您的設計將會造成其中其他 microsoft 服務偏好來路由傳送的輸入的連線的輸入 ExpressRoute，透過時傳回路徑會使用網際網路的非對稱式路由。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p136">Once your on-premises inbound endpoints are advertised to Microsoft over ExpressRoute, ExpressRoute will effectively become the preferred routing path to those endpoints for all Microsoft services, including Office 365. This means that those endpoint subnets must only be used for communications with Office 365 services and no other services on the Microsoft network. Otherwise, your design will cause asymmetric routing where inbound connections from other Microsoft services prefer to route inbound over ExpressRoute, while the return path will use the Internet.</span></span>

6. <span data-ttu-id="8adf0-p137">在事件 ExpressRoute 電路或符合-我位置已關閉，則需要確定內部輸入的端點可用仍可接受要求透過不同的網路路徑。這可能會透過多個 ExpressRoute 電路那些端點意見廣告子網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p137">In the event an ExpressRoute circuit or meet-me location is down, you'll need to ensure the on-premises inbound endpoints are still available to accept requests over a separate network path. This may mean advertising subnets for those endpoints through multiple ExpressRoute circuits.</span></span>

7. <span data-ttu-id="8adf0-369">建議您將套用之所有內送的網路流量流程輸入您的網路透過 ExpressRoute，尤其是當這些流程跨防火牆等設定狀態的網路裝置時的來源 NAT。</span><span class="sxs-lookup"><span data-stu-id="8adf0-369">We recommend applying source NAT for all inbound network traffic flows entering your network through ExpressRoute, especially when these flows cross stateful network devices such as firewalls.</span></span>

8. <span data-ttu-id="8adf0-p138">某些內部部署服務，例如 ADFS proxy 或 Exchange 自動探索可能會收到輸入的要求來自 Office 365 服務和來自網際網路的使用者。這些要求的 Office 365 會透過網際網路目標使用者要求相同的 FQDN。從網際網路允許撥入的使用者連線至那些內部部署端點時強制進行 Office 365 的連線使用 ExpressRoute，代表大幅路由的複雜性。對於大多數的客戶透過 ExpressRoute 實作這類複雜的案例不建議因為操作考量。此額外負荷包含管理風險的非對稱式路由，而且需要您謹慎管理跨多個維度的 [路由廣告和原則。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p138">Some on-premises services, such as ADFS proxy or Exchange autodiscover, may receive inbound requests from both Office 365 services and users from the Internet. For these requests Office 365 will target the same FQDN as user requests over the Internet. Allowing inbound user connections from the internet to those on-premises endpoints, while forcing Office 365 connections to use ExpressRoute, represents significant routing complexity. For the vast majority of customers implementing such complex scenarios over ExpressRoute is not recommended due to operational considerations. This additional overhead includes, managing risks of asymmetric routing and will require you to carefully manage routing advertisements and policies across multiple dimensions.</span></span>

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a><span data-ttu-id="8adf0-375">更新您的網路拓撲計劃来顯示如何將避免發生非對稱式路由</span><span class="sxs-lookup"><span data-stu-id="8adf0-375">Update your network topology plan to show how you would avoid asymmetric routes</span></span>
<span data-ttu-id="8adf0-376"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-376"></span></span>

<span data-ttu-id="8adf0-p139">您想要避免以確保您的組織中的人員可以順暢地使用 Office 365，以及其他重要服務在網際網路上的非對稱式路由。有兩種常見設定客戶可以引發非對稱式路由。現在是很好的時間檢閱您打算使用並檢查是否其中一個這些非對稱的路由案例依然存在的網路組態。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p139">You want to avoid asymmetric routing to ensure people in your organization can seamlessly use Office 365 as well as other important services on the internet. There are two common configurations customers have that cause asymmetric routing. Now's a good time to review the network configuration you're planning to use and check if one of these asymmetric routing scenarios could exist.</span></span>
  
<span data-ttu-id="8adf0-p140">若要開始，我們將檢查幾個不同的情況下的網狀圖相關聯。在此圖表中，會收到傳入的要求的所有伺服器例如 ADFS 或內部部署混合伺服器紐澤西資料中心中與通知給網際網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p140">To begin, we'll examine a few different situations associated with the following network diagram. In this diagram, all servers that receive inbound requests, such as ADFS or on-premises hybrid servers are in the New Jersey data center and are advertised to the internet.</span></span>
  
1. <span data-ttu-id="8adf0-382">安全周邊網路時，沒有任何來源 NAT 可供傳入要求。</span><span class="sxs-lookup"><span data-stu-id="8adf0-382">While the perimeter network is secure, there is no Source NAT available for incoming requests.</span></span>

2. <span data-ttu-id="8adf0-383">紐澤西資料中心中的伺服器都能看到網際網路和 ExpressRoute 路由。</span><span class="sxs-lookup"><span data-stu-id="8adf0-383">The servers in the New Jersey data center are able to see both internet and ExpressRoute routes.</span></span>

![ExpressRoute 連線概觀 （英文)](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
<span data-ttu-id="8adf0-385">我們也具備如何修正這些建議。</span><span class="sxs-lookup"><span data-stu-id="8adf0-385">We also have suggestions on how to fix them.</span></span>
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a><span data-ttu-id="8adf0-386">透過網際網路與內部連線的問題 1： 雲端</span><span class="sxs-lookup"><span data-stu-id="8adf0-386">Problem 1: Cloud to on-premises connection over the Internet</span></span>
  
<span data-ttu-id="8adf0-387">下圖說明當您的網路設定不會透過網際網路的傳入要求的 Microsoft cloud 中提供 NAT 時採取的非對稱的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="8adf0-387">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over the internet.</span></span>
  
1. <span data-ttu-id="8adf0-388">從 Office 365 的輸入的要求從公用 DNS 擷取內部部署端點的 IP 位址，並將要求傳送至周邊網路中。</span><span class="sxs-lookup"><span data-stu-id="8adf0-388">The inbound request from Office 365 retrieves the IP address of the on-premises endpoint from public DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="8adf0-389">這個無效的組態設定中沒有設定任何來源 NAT 或位於周邊網路流量所在傳送產生實際來源 ip 位址作為傳回目的地。</span><span class="sxs-lookup"><span data-stu-id="8adf0-389">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="8adf0-390">您的網路上的伺服器傳回將流量路由傳送至 Office 365 透過任何可用的 ExpressRoute 網路連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-390">The server on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="8adf0-391">結果是 Office 365，則產生的中斷連線的流程非對稱路徑。</span><span class="sxs-lookup"><span data-stu-id="8adf0-391">The result is an Asymmetric path for that flow to Office 365, resulting in a broken connection.</span></span>

![ExpressRoute Asymetric 路由問題 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a><span data-ttu-id="8adf0-393">解決方案 1a： 來源 NAT</span><span class="sxs-lookup"><span data-stu-id="8adf0-393">Solution 1a: Source NAT</span></span>
  
<span data-ttu-id="8adf0-p141">只新增來源 NAT 以將輸入要求解析為此設定錯誤的網路。在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="8adf0-p141">Simply adding a source NAT to the inbound request resolves this misconfigured network. In this diagram:</span></span>
  
1. <span data-ttu-id="8adf0-p142">傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。這次是來源 NAT 使用。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p142">The incoming request continues to enter through the New Jersey data center's perimeter network. This time Source NAT is available.</span></span>

2. <span data-ttu-id="8adf0-398">從伺服器路由回正面 nat 來源，而不是原始的 IP 位址，則傳回的相同的網路路徑的回應產生關聯的 IP 回應。</span><span class="sxs-lookup"><span data-stu-id="8adf0-398">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解決方案 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a><span data-ttu-id="8adf0-400">解決方案 1b： 路由設定範圍</span><span class="sxs-lookup"><span data-stu-id="8adf0-400">Solution 1b: Route Scoping</span></span>
  
<span data-ttu-id="8adf0-p143">或者，您可以選擇不允許將通告的前置詞 ExpressRoute BGP 移除這些電腦的替代的網路路徑。在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="8adf0-p143">Alternatively, you can choose to not allow the ExpressRoute BGP prefixes to be advertised, removing the alternate network path for those computers. In this diagram:</span></span>
  
1. <span data-ttu-id="8adf0-p144">傳入的要求會繼續輸入透過紐澤西資料中心的周邊網路。這次是透過 ExpressRoute 電路通告使用 microsoft 的前置詞不紐澤西資料中心。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p144">The incoming request continues to enter through the New Jersey data center's perimeter network. This time the prefixes advertised from Microsoft over the ExpressRoute circuit are not available to the New Jersey data center.</span></span>

2. <span data-ttu-id="8adf0-405">從伺服器路由回應回他們所產生的相同的網路路徑傳回回應 IP 透過唯一可用的路由相關聯的原始 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="8adf0-405">The response from the server routes back toward the IP associated with the original IP address over the only route available, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解決方案 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a><span data-ttu-id="8adf0-407">問題 2： 雲端 ExpressRoute 透過內部部署連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-407">Problem 2: Cloud to on-premises connection over ExpressRoute</span></span>
  
<span data-ttu-id="8adf0-408">下圖說明當您的網路設定不會透過 ExpressRoute 的傳入要求的 Microsoft cloud 中提供 NAT 時採取的非對稱的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="8adf0-408">The following diagram illustrates the asymmetric network path taken when your network configuration doesn't provide NAT for inbound requests from the Microsoft cloud over ExpressRoute.</span></span>
  
1. <span data-ttu-id="8adf0-409">從 Office 365 的輸入的要求擷取的 IP 位址從 DNS，並將要求傳送至周邊網路中。</span><span class="sxs-lookup"><span data-stu-id="8adf0-409">The inbound request from Office 365 retrieves the IP address from DNS and sends the request to your perimeter network.</span></span>

2. <span data-ttu-id="8adf0-410">這個無效的組態設定中沒有設定任何來源 NAT 或位於周邊網路流量所在傳送產生實際來源 ip 位址作為傳回目的地。</span><span class="sxs-lookup"><span data-stu-id="8adf0-410">In this faulty configuration, there is no Source NAT configured or available at the perimeter network where the traffic is sent resulting in the actual source IP address being used as the return destination.</span></span>

  - <span data-ttu-id="8adf0-411">在您的網路上的電腦傳回將流量路由傳送至 Office 365 透過任何可用的 ExpressRoute 網路連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-411">The computer on your network routes the return traffic to Office 365 through any available ExpressRoute network connection.</span></span>

  - <span data-ttu-id="8adf0-412">結果是 Office 365 的非對稱式連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-412">The result is an Asymmetric connection to Office 365.</span></span>

![ExpressRoute Asymetric 路由問題 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a><span data-ttu-id="8adf0-414">解決方案 2： 來源 NAT</span><span class="sxs-lookup"><span data-stu-id="8adf0-414">Solution 2: Source NAT</span></span>
  
<span data-ttu-id="8adf0-p145">只新增來源 NAT 以將輸入要求解析為此設定錯誤的網路。在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="8adf0-p145">Simply adding a source NAT to the inbound request resolves this misconfigured network. In this diagram:</span></span>
  
1. <span data-ttu-id="8adf0-p146">傳入的要求會繼續輸入透過紐約資料中心的周邊網路。這次是來源 NAT 使用。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p146">The incoming request continues to enter through the New York data center's perimeter network. This time Source NAT is available.</span></span>

2. <span data-ttu-id="8adf0-419">從伺服器路由回正面 nat 來源，而不是原始的 IP 位址，則傳回的相同的網路路徑的回應產生關聯的 IP 回應。</span><span class="sxs-lookup"><span data-stu-id="8adf0-419">The response from the server routes back toward the IP associated with the Source NAT instead of the original IP address, resulting in the response returning along the same network path.</span></span>

![ExpressRoute Asymetric 路由解決方案 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a><span data-ttu-id="8adf0-421">紙張確認網路設計具有路徑對稱性來看</span><span class="sxs-lookup"><span data-stu-id="8adf0-421">Paper verify that the network design has path symmetry</span></span>

<span data-ttu-id="8adf0-p147">此時，您必須確認紙張上實作計劃提供路由對稱性來看不同案例中您將會使用 Office 365。您將識別預期使用者使用服務的不同功能時要採取的特定網路路由。從內部網路和 WAN 路由至周邊裝置的 [連線路徑 ；ExpressRoute 或網際網路和登入到 online 端點的連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p147">At this point, you need to verify on paper that your implementation plan offers route symmetry for the different scenarios in which you'll be using Office 365. You'll identify the specific network route that is expected to be taken when a person uses different features of the service. From the on-premises network and WAN routing, to the perimeter devices, to the connectivity path; ExpressRoute or the internet, and on to the connection to the online endpoint.</span></span>
  
<span data-ttu-id="8adf0-425">您需要這麼做的所有先前已被識別為貴組織要採取的服務 Office 365 網路服務。</span><span class="sxs-lookup"><span data-stu-id="8adf0-425">You'll need to do this for all of the Office 365 network services that were previously identified as services that your organization will adopt.</span></span>
  
<span data-ttu-id="8adf0-p148">很有幫助執行本白皮書逐一檢查的路由與第二個連絡人。說明這些其中每個網路躍點預期會取得其下一條路由從並確定您已熟悉的路由路徑。請記得 ExpressRoute 永遠會提供更多範圍的路由到 Microsoft 伺服器的 IP 位址給予較低的路由成本比網際網路預設路由。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p148">It helps to do this paper walk through of routes with a second person. Explain to them where each network hop is expected to get its next route from and ensure that you're familiar with the routing paths. Remember that ExpressRoute will always provide a more scoped route to Microsoft server IP addresses giving it lower route cost than an Internet default route.</span></span>
  
### <a name="design-client-connectivity-configuration"></a><span data-ttu-id="8adf0-429">設計用戶端連線設定</span><span class="sxs-lookup"><span data-stu-id="8adf0-429">Design Client Connectivity Configuration</span></span>
<span data-ttu-id="8adf0-430"><a name="asymmetric"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-430"></span></span>

![使用 ExpressRoute PAC 檔案](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
<span data-ttu-id="8adf0-p149">如果您使用 proxy 伺服器的網際網路繫結流量則需要調整任何 PAC 或用戶端設定檔以確保您的網路上的用戶端電腦已正確設定以不 transiting 立即所需的 ExpressRoute 流量傳送至 Office 365proxy 伺服器，與其餘的流量，包括一些的 Office 365 流量傳送至相關的 proxy。閱讀有關[管理 Office 365 端點](https://aka.ms/manageo365endpoints)我們指南例如 PAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p149">If you're using a proxy server for internet bound traffic then you need to adjust any PAC or client configuration files to ensure client computers on your network are correctly configured to send the ExpressRoute traffic you desire to Office 365 without transiting your proxy server, and the remaining traffic, including some Office 365 traffic, is sent to the relevant proxy. Read our guide on [managing Office 365 endpoints](https://aka.ms/manageo365endpoints) for example PAC files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="8adf0-p150">端點變更經常、 通常為 [每週。您只應該進行變更為基礎的服務和功能組織已採用以減少需要對最新資訊已變更的數目。關閉必須注意的 RSS 摘要其中所做的變更會即已宣佈及記錄保留的所有舊 IP 的變更會即已宣佈的地址中的**有效的日期**可能未通告、 或移除通告，直到達到有效的日期。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p150">The endpoints change frequently, as often as weekly. You should only make changes based on the services and features your organization has adopted to reduce the number of changes you'll need to make to stay current. Pay close attention to the **Effective Date** in the RSS feed where the changes are announced and a record is kept of all past changes, IP addresses that are announced may not be advertised, or removed from advertisement, until the effective date is reached.</span></span>
  
## <a name="build-your-deployment-and-testing-procedures"></a><span data-ttu-id="8adf0-437">建置您的部署和測試程序</span><span class="sxs-lookup"><span data-stu-id="8adf0-437">Build your deployment and testing procedures</span></span>
<span data-ttu-id="8adf0-438"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-438"></span></span>

<span data-ttu-id="8adf0-p151">同時測試及復原規劃應該包括實作計劃。如果您實作未運作如預期般運作，規劃應設計成影響最數目人員之前發現的問題。以下是您計劃應該考慮一些 high 層級原則。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p151">Your implementation plan should include both testing and rollback planning. If your implementation isn't functioning as expected, the plan should be designed to affect the least number of people before problems are discovered. The following are some high level principles your plan should consider.</span></span>
  
1. <span data-ttu-id="8adf0-442">階段減少中斷網路區段和使用者服務 onboarding。</span><span class="sxs-lookup"><span data-stu-id="8adf0-442">Stage the network segment and user service onboarding to minimize disruption.</span></span>

2. <span data-ttu-id="8adf0-443">規劃測試使用 traceroute 路由和 TCP 連線從不同的網際網路連線的主機。</span><span class="sxs-lookup"><span data-stu-id="8adf0-443">Plan for testing routes with traceroute and TCP connect from a separate internet connected host.</span></span>

3. <span data-ttu-id="8adf0-444">最好測試的輸入和輸出服務應使用的測試 Office 365 租用戶隔離的測試網路上。</span><span class="sxs-lookup"><span data-stu-id="8adf0-444">Preferably, testing of inbound and outbound services should be done on an isolated test network with a test Office 365 tenant.</span></span>

      - <span data-ttu-id="8adf0-445">或者，可以被執行測試生產網路上如果客戶尚無法使用 Office 365 或位於試驗。</span><span class="sxs-lookup"><span data-stu-id="8adf0-445">Alternatively, testing can be performed on a production network if the customer is not yet using Office 365 or is in pilot.</span></span>

      - <span data-ttu-id="8adf0-446">或者，測試預留測試在實際執行中斷期間執行及可監視僅。</span><span class="sxs-lookup"><span data-stu-id="8adf0-446">Alternatively, testing can be performed during a production outage that is set aside for test and monitoring only.</span></span>

      - <span data-ttu-id="8adf0-p152">或者，測試可透過檢查每個第 3 層 router 節點上每個服務的路由。此改應該只用於如果沒有其他測試可能因為缺少實體測試介紹風險。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p152">Alternatively, testing can be done by checking routes for each service on each layer 3 router node. This fall back should only be used if no other testing is possible since a lack of physical testing introduces risk.</span></span>

### <a name="build-your-deployment-procedures"></a><span data-ttu-id="8adf0-449">建置您的部署程序</span><span class="sxs-lookup"><span data-stu-id="8adf0-449">Build your deployment procedures</span></span>

<span data-ttu-id="8adf0-p153">部署程序應該導入的人員的小群組分階段可用於測試再部署至較大組群的人。以下是幾種方式階段 ExpressRoute 的部署。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p153">Your deployment procedures should roll out to small groups of people in stages to allow for testing before deploying to larger groups of people. The following are several ways to stage the deployment of ExpressRoute.</span></span>
  
1. <span data-ttu-id="8adf0-452">與 Microsoft 對等設定 ExpressRoute 並已轉寄給僅針對單一主機路由廣告分段測試目的。</span><span class="sxs-lookup"><span data-stu-id="8adf0-452">Set up ExpressRoute with Microsoft peering and have the route advertisements forwarded to a single host only for staged testing purposes.</span></span>

2. <span data-ttu-id="8adf0-453">Advertise 為單一網路區段第一次 ExpressRoute 網路路由並展開路由廣告網路區段或區域。</span><span class="sxs-lookup"><span data-stu-id="8adf0-453">Advertise routes to the ExpressRoute network to a single network segment at first and expand route advertisements by network segment or region.</span></span>

3. <span data-ttu-id="8adf0-454">如果第一次部署 Office 365，作為 ExpressRoute 網路部署試驗的小型人數。</span><span class="sxs-lookup"><span data-stu-id="8adf0-454">If deploying Office 365 for the first time, use the ExpressRoute network deployment as a pilot for a small number of people.</span></span>

4. <span data-ttu-id="8adf0-455">如果使用 proxy 伺服器，或者可設定將之前加入更多導向少量的測試及意見反應至 ExpressRoute 人員測試 PAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="8adf0-455">If using proxy servers, you can alternatively configure a test PAC file to direct a small number of people to ExpressRoute with testing and feedback before adding more.</span></span>

<span data-ttu-id="8adf0-p154">實作計劃應列出每個必須採取的部署程序或需要用來部署的網路組態的命令。當網路中斷時間會進入做應從書寫的部署計劃已事先撰寫和對等的變更的所有檢閱。請參閱 ExpressRoute 技術組態適用的指引。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p154">Your implementation plan should list each of the deployment procedures that must be taken or commands that need to be used to deploy the networking configuration. When the network outage time arrives all of the changes being made should be from the written deployment plan which was written in advance and peer reviewed. See our guidance on the technical configuration of ExpressRoute.</span></span>
  
- <span data-ttu-id="8adf0-459">如果您已變更的任何仍會繼續傳送電子郵件的內部部署伺服器的 IP 位址，更新 SPF TXT 記錄。</span><span class="sxs-lookup"><span data-stu-id="8adf0-459">Updating your SPF TXT records if you've changed IP addresses for any on-premises servers that will continue to send email.</span></span>

- <span data-ttu-id="8adf0-460">如果您已變更以容納新的 NAT 設定的 IP 位址，更新內部部署伺服器的任何 DNS 項目。</span><span class="sxs-lookup"><span data-stu-id="8adf0-460">Updating any DNS entries for on-premises servers if you've changed IP addresses to accommodate a new NAT configuration.</span></span>

- <span data-ttu-id="8adf0-461">請確定您已訂閱 rss 摘要的 Office 365 端點通知來維護任何路由或 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="8adf0-461">Ensure you've subscribed to the RSS feed for Office 365 endpoint notifications to maintain any routing or proxy configurations.</span></span>

<span data-ttu-id="8adf0-p155">ExpressRoute 部署完成後測試計劃中的程序應該執行。應記錄每個程序的結果。您必須包含復原到原始的實際執行環境的測試計劃結果指出實作未成功可行的程的序。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p155">After your ExpressRoute deployment is complete the procedures in the test plan should be executed. Results for each procedure should be logged. You must include procedures for rolling back to the original production environment in the event the test plan results indicate the implementation was not successful.</span></span>
  
### <a name="build-your-test-procedures"></a><span data-ttu-id="8adf0-465">建立測試程序</span><span class="sxs-lookup"><span data-stu-id="8adf0-465">Build your test procedures</span></span>

<span data-ttu-id="8adf0-p156">在測試程序應該包含 Office 365 將會使用 ExpressRoute 每個輸出及輸入網路服務和類不會測試。本節的程序應該包含測試從包含使用者不是在內部公司的 LAN 中每個唯一的網路位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p156">Your testing procedures should include tests for each outbound and inbound network service for Office 365 both that will be using ExpressRoute and ones that will not. The procedures should include testing from each unique network location including users who are not on-premises in the corporate LAN.</span></span>
  
<span data-ttu-id="8adf0-468">測試活動的一些範例包括下列項目。</span><span class="sxs-lookup"><span data-stu-id="8adf0-468">Some examples of test activities include the following.</span></span>
  
1. <span data-ttu-id="8adf0-469">從您的內部路由器 ping 到您的網路運算子路由器。</span><span class="sxs-lookup"><span data-stu-id="8adf0-469">Ping from your on-premises router to your network operator router.</span></span>

2. <span data-ttu-id="8adf0-470">驗證 500 + Office 365 和 CRM Online IP 位址廣告會接收到您的內部路由器。</span><span class="sxs-lookup"><span data-stu-id="8adf0-470">Validate the 500+ Office 365 and CRM Online IP address advertisements are received by your on-premises router.</span></span>

3. <span data-ttu-id="8adf0-471">驗證您輸入及輸出的 NAT 操作 ExpressRoute 與內部網路之間。</span><span class="sxs-lookup"><span data-stu-id="8adf0-471">Validate your inbound and outbound NAT is operating between ExpressRoute and the internal network.</span></span>

4. <span data-ttu-id="8adf0-472">驗證您的 NAT 路由會被通告從您的路由器。</span><span class="sxs-lookup"><span data-stu-id="8adf0-472">Validate that routes to your NAT are being advertised from your router.</span></span>

5. <span data-ttu-id="8adf0-473">驗證 ExpressRoute 已接受通告的前置詞。</span><span class="sxs-lookup"><span data-stu-id="8adf0-473">Validate that ExpressRoute has accepted your advertised prefixes.</span></span>

      - <span data-ttu-id="8adf0-474">若要確認對等的廣告使用下列 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="8adf0-474">Use the following cmdlet to verify peering advertisements:</span></span>

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. <span data-ttu-id="8adf0-475">驗證其設定為特定先前範例所示的較大範圍的子集範圍不向 Microsoft 透過 ExpressRoute 或公用網際網路網路電路通告您公用 NAT IP。</span><span class="sxs-lookup"><span data-stu-id="8adf0-475">Validate your public NAT IP range is not advertised to Microsoft through any other ExpressRoute or public Internet network circuit unless it is a specific subset of a larger range as in the previous example.</span></span>

7. <span data-ttu-id="8adf0-476">ExpressRoute 電路成對、 驗證執行這兩個 BGP 工作階段。</span><span class="sxs-lookup"><span data-stu-id="8adf0-476">ExpressRoute circuits are paired, validate that both BGP sessions are running.</span></span>

8. <span data-ttu-id="8adf0-p157">在您的 NAT 的內部單一主機及使用 ping、 tracert 及 tcpping 不同主機 outlook.office365.com 至新的電路測試連線。或者，您可以使用 Wireshark 之類的工具或 Microsoft Network Monitor 3.4 來驗證您 MSEE 鏡像連接埠上正在能夠連線到 outlook.office365.com 相關聯的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p157">Set up a single host on the inside of your NAT and use ping, tracert, and tcpping to test connectivity across the new circuit to the host outlook.office365.com. Alternatively, you could use a tool such as Wireshark or Microsoft Network Monitor 3.4 on a mirrored port to the MSEE to validate you're able to connect to the IP address associated with outlook.office365.com.</span></span>

9. <span data-ttu-id="8adf0-479">Exchange Online 的測試應用程式層級的功能。</span><span class="sxs-lookup"><span data-stu-id="8adf0-479">Test application level functionality for Exchange Online.</span></span>

  - <span data-ttu-id="8adf0-480">測試 Outlook 能夠連線至 Exchange Online 並傳送/接收電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8adf0-480">Test Outlook is able to connect to Exchange Online and send/receive email.</span></span>

  - <span data-ttu-id="8adf0-481">測試 Outlook 在能夠使用 「 線上模式。</span><span class="sxs-lookup"><span data-stu-id="8adf0-481">Test Outlook is able to use online-mode.</span></span>

  - <span data-ttu-id="8adf0-482">測試智慧型手機連線並傳送/接收] 功能。</span><span class="sxs-lookup"><span data-stu-id="8adf0-482">Test smartphone connectivity and send/receive capability.</span></span>

10. <span data-ttu-id="8adf0-483">SharePoint Online 的測試應用程式層級功能</span><span class="sxs-lookup"><span data-stu-id="8adf0-483">Test application level functionality for SharePoint Online</span></span>

  - <span data-ttu-id="8adf0-484">測試 OneDrive for Business sync 用戶端。</span><span class="sxs-lookup"><span data-stu-id="8adf0-484">Test OneDrive for Business sync client.</span></span>

  - <span data-ttu-id="8adf0-485">測試 SharePoint Online web access。</span><span class="sxs-lookup"><span data-stu-id="8adf0-485">Test SharePoint Online web access.</span></span>

11. <span data-ttu-id="8adf0-486">商務電話案例 Skype 測試應用程式層級的功能：</span><span class="sxs-lookup"><span data-stu-id="8adf0-486">Test application level functionality for Skype for Business calling scenarios:</span></span>

  - <span data-ttu-id="8adf0-487">已驗證的使用者 [由使用者起始的邀請] 以加入電話會議。</span><span class="sxs-lookup"><span data-stu-id="8adf0-487">Join to conference call as authenticated user [invite initiated by end user].</span></span>

  - <span data-ttu-id="8adf0-488">邀請電話會議 [邀請寄件者 MCU] 的使用者。</span><span class="sxs-lookup"><span data-stu-id="8adf0-488">Invite user to conference call [invite sent from MCU].</span></span>

  - <span data-ttu-id="8adf0-489">使用 Skype 商務 web 應用程式的匿名使用者加入會議。</span><span class="sxs-lookup"><span data-stu-id="8adf0-489">Join conference as anonymous user using the Skype for Business web application.</span></span>

  - <span data-ttu-id="8adf0-490">加入將有線的 PC 連線、 IP 電話與行動裝置的通話。</span><span class="sxs-lookup"><span data-stu-id="8adf0-490">Join call from your wired PC connection, IP phone, and mobile device.</span></span>

  - <span data-ttu-id="8adf0-491">呼叫以同盟的使用者 o PSTN 驗證呼叫： 完成通話、 通話品質來說相當可接受、 連線時間是在可接受。</span><span class="sxs-lookup"><span data-stu-id="8adf0-491">Call to federated user o Call to PSTN Validation: call is completed, call quality is acceptable, connection time is acceptable.</span></span>

  - <span data-ttu-id="8adf0-492">確認連絡人的目前狀態更新兩個成員的租用戶和同盟使用者。</span><span class="sxs-lookup"><span data-stu-id="8adf0-492">Verify presence status for contacts is updated for both members of the tenant and federated users.</span></span>

### <a name="common-problems"></a><span data-ttu-id="8adf0-493">常見問題</span><span class="sxs-lookup"><span data-stu-id="8adf0-493">Common problems</span></span>

<span data-ttu-id="8adf0-p158">非對稱式路由是最常見的實作問題。以下是一些常見的來源來尋找：</span><span class="sxs-lookup"><span data-stu-id="8adf0-p158">Asymmetric routing is the most common implementation problem. Here are some common sources to look for:</span></span>
  
- <span data-ttu-id="8adf0-496">使用 open 或一般網路路由拓撲但未來源位置的 NAT。</span><span class="sxs-lookup"><span data-stu-id="8adf0-496">Using an open or flat network routing topology without source NAT in place.</span></span>

- <span data-ttu-id="8adf0-497">不使用 SNAT 路由傳送至輸入 services 透過網際網路和 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="8adf0-497">Not using SNAT to route to inbound services through both the internet and ExpressRoute connections.</span></span>

- <span data-ttu-id="8adf0-498">不測試輸入的 ExpressRoute 在伺服器上的服務之前先部署廣泛的測試網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-498">Not testing inbound services on ExpressRoute on a test network prior to deploying broadly.</span></span>

## <a name="deploying-expressroute-connectivity-through-your-network"></a><span data-ttu-id="8adf0-499">部署 ExpressRoute 連線到您的網路</span><span class="sxs-lookup"><span data-stu-id="8adf0-499">Deploying ExpressRoute connectivity through your network</span></span>
<span data-ttu-id="8adf0-500"><a name="testing"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-500"></span></span>

<span data-ttu-id="8adf0-p159">階段，一次漸漸地愈來愈啟用連線至網路回復為每個新的網路區段計劃的不同組件部署至多條線段的網路。如果您部署 Office 365 部署的對齊、 先部署至 Office 365 試驗使用者，並從該處擴充。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p159">Stage your deployment to one segment of the network at a time, progressively rolling out the connectivity to different parts of the network with a plan to roll back for each new network segment. If your deployment is aligned with an Office 365 deployment, deploy to your Office 365 pilot users first and extend from there.</span></span>
  
<span data-ttu-id="8adf0-503">先測試然後實際執行：</span><span class="sxs-lookup"><span data-stu-id="8adf0-503">First for your test and then for production:</span></span>
  
- <span data-ttu-id="8adf0-504">執行啟用 ExpressRoute 的部署步驟。</span><span class="sxs-lookup"><span data-stu-id="8adf0-504">Run the deployment steps to enable ExpressRoute.</span></span>

- <span data-ttu-id="8adf0-505">測試您看不到網路路由已如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="8adf0-505">Test your seeing the network routes are as expected.</span></span>

- <span data-ttu-id="8adf0-506">執行測試每個輸入及輸出的服務。</span><span class="sxs-lookup"><span data-stu-id="8adf0-506">Perform testing on each inbound and outbound service.</span></span>

- <span data-ttu-id="8adf0-507">如果您發現任何問題，回復。</span><span class="sxs-lookup"><span data-stu-id="8adf0-507">Rollback if you discover any issues.</span></span>

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a><span data-ttu-id="8adf0-508">設定與測試網路區段 ExpressRoute 測試連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-508">Set up a test connection to ExpressRoute with a test network segment</span></span>

<span data-ttu-id="8adf0-p160">現在，您必須完成的計劃的紙張上該是時候來測試小型向外延展。此測試中您會在內部網路上建立的單一 ExpressRoute 連線與 Microsoft Peering 測試子網路。您可以連線到與測試子網路設定[試用 Office 365 租用戶](https://go.microsoft.com/fwlink/p/?LinkID=403802)和在生產環境中測試子網路中包含您要使用的所有輸出及輸入服務。設定 DNS 的測試網路區段並建立所有輸入及輸出的服務。執行測試計劃並確定您熟悉針對每個服務和路由傳播路由傳送。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p160">Now that you have the completed plan on paper it is time to test at a small scale. In this test you will establish a single ExpressRoute connection with Microsoft Peering to a test subnet on your on-premises network. You can configure a [trial Office 365 tenant](https://go.microsoft.com/fwlink/p/?LinkID=403802) with connectivity to and from the test subnet and include all outbound and inbound services that you will be using in production in the test subnet. Set up DNS for the test network segment and establish all inbound and outbound services. Execute your test plan and ensure that you are familiar with the routing for each service and the route propagation.</span></span>
  
### <a name="execute-the-deployment-and-test-plans"></a><span data-ttu-id="8adf0-514">執行部署和測試計劃</span><span class="sxs-lookup"><span data-stu-id="8adf0-514">Execute the deployment and test plans</span></span>

<span data-ttu-id="8adf0-515">當您完成以上所述的項目，檢查關閉區域在完成並確定您和小組檢閱這些之前執行您的部署和測試計劃。</span><span class="sxs-lookup"><span data-stu-id="8adf0-515">As you complete the items described above, check off the areas you've completed and ensure you and your team have reviewed them before executing your deployment and testing plans.</span></span>
  
- <span data-ttu-id="8adf0-516">輸出及輸入變更網路相關的服務清單。</span><span class="sxs-lookup"><span data-stu-id="8adf0-516">List of outbound and inbound services that are involved in the network change.</span></span>

- <span data-ttu-id="8adf0-517">顯示 internet 輸出及 ExpressRoute 開會通用網路架構圖表-我位置。</span><span class="sxs-lookup"><span data-stu-id="8adf0-517">Global network architecture diagram showing both internet egress and ExpressRoute meet-me locations.</span></span>

- <span data-ttu-id="8adf0-518">網路路由圖示範部署每個服務使用不同的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="8adf0-518">Network routing diagram demonstrating the different network paths used for each service deployed.</span></span>

- <span data-ttu-id="8adf0-519">若要實作的變更和 rollback 視部署計畫的步驟。</span><span class="sxs-lookup"><span data-stu-id="8adf0-519">A deployment plan with steps to implement the changes and rollback if needed.</span></span>

- <span data-ttu-id="8adf0-520">測試每個 Office 365 及網路服務測試計劃。</span><span class="sxs-lookup"><span data-stu-id="8adf0-520">A test plan for testing each Office 365 and network service.</span></span>

- <span data-ttu-id="8adf0-521">完成輸入和輸出服務的實際執行路由紙張驗證。</span><span class="sxs-lookup"><span data-stu-id="8adf0-521">Completed paper validation of production routes for inbound and outbound services.</span></span>

- <span data-ttu-id="8adf0-522">跨包括可用性測試測試網路區段完整的測試。</span><span class="sxs-lookup"><span data-stu-id="8adf0-522">A completed test across a test network segment including availability testing.</span></span>

<span data-ttu-id="8adf0-523">選擇 [中斷] 視窗的時間足以執行透過整個部署規劃和測試計劃、 有一些疑難排解可用的時間和啟用回如果所需的時間。</span><span class="sxs-lookup"><span data-stu-id="8adf0-523">Choose an outage window that is long enough to run through the entire deployment plan and the test plan, has some time available for troubleshooting and time for rolling back if required.</span></span>
  
> [!CAUTION]
> <span data-ttu-id="8adf0-524">因為路由透過網際網路和 ExpressRoute 複雜本質，建議其他緩衝區時間會新增此視窗以處理複雜路由的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="8adf0-524">Due to the complex nature of routing over both the internet and ExpressRoute, it is recommended that additional buffer time is added to this window to handle troubleshooting complex routing.</span></span>
  
### <a name="configure-qos-for-skype-for-business-online"></a><span data-ttu-id="8adf0-525">設定 QoS Skype for Business 線上</span><span class="sxs-lookup"><span data-stu-id="8adf0-525">Configure QoS for Skype for Business Online</span></span>

<span data-ttu-id="8adf0-p161">QoS 是必要的商務 Online Skype 取得語音與會議的優點。您可以設定 QoS 之後您擁有可確保 ExpressRoute 網路連線不會封鎖任何您其他 Office 365 服務存取權。[ExpressRoute 和 Skype 的商務 Online 中的 QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)文章中說明的 QoS 設定。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p161">QoS is necessary to obtain voice and meeting benefits for Skype for Business Online. You can configure QoS after you have ensured that the ExpressRoute network connection does not block any of your other Office 365 service access. Configuration for QoS is described in the article [ExpressRoute and QoS in Skype for Business Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .</span></span>
  
## <a name="troubleshooting-your-implementation"></a><span data-ttu-id="8adf0-529">疑難排解您實作</span><span class="sxs-lookup"><span data-stu-id="8adf0-529">Troubleshooting your implementation</span></span>
<span data-ttu-id="8adf0-530"><a name="troubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="8adf0-530"></span></span>

<span data-ttu-id="8adf0-p162">第一個位置尋找位於此實作指南 》 中的步驟已任何未接的實作計劃中吗？返回並執行進一步測試盡可能複寫錯誤和偵錯該那里的小型網路。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p162">The first place to look is at the steps in this implementation guide, were any missed in your implementation plan? Go back and run further small network testing if possible to replicate the error and debug it there.</span></span>
  
<span data-ttu-id="8adf0-p163">識別此輸入或輸出 services 無法在測試期間。取得特別的 IP 位址和子網路的每個服務的失敗。繼續進行的紙張上引導網路拓撲圖表與驗證路由。驗證特別其中 ExpressRoute 路由會對通告、 測試該路由系統中斷期間盡可能與追蹤項目。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p163">Identify which inbound or outbound services failed during testing. Get specifically the IP addresses and subnets for each of the services which failed. Go ahead and walk the network topology diagram on paper and validate the routing. Validate specifically where the ExpressRoute routing is advertised to, Test that routing during the outage if possible with traces.</span></span>
  
<span data-ttu-id="8adf0-p164">使用網路追蹤執行 PSPing 至每個客戶端點並評估來源和目的地 IP 位址來驗證其如預期般運作。執行連接埠 25 上公開並確認是否這預期 SNAT 隱藏的原始來源 IP 位址的任何郵件主機 telnet。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p164">Run PSPing with a network trace to each customer endpoint and evaluate source and destination IP addresses to validate that they are as expected. Run telnet to any mail host that you expose on port 25 and verify that SNAT is hiding the original source IP address if this is expected.</span></span>
  
<span data-ttu-id="8adf0-p165">請記住，則需要確定這兩個網路組態的 ExpressRoute ExpressRoute 連線以部署 Office 365 時的最佳方式設計及也已進行其他元件最佳化網路等用戶端電腦上。除了使用本規劃指南來疑難排解您可能會有未接的步驟，我們也有寫入[效能疑難排解 Office 365 計劃](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c)。</span><span class="sxs-lookup"><span data-stu-id="8adf0-p165">Keep in mind that while deploying Office 365 with an ExpressRoute connection you'll need to ensure both the network configuration for ExpressRoute is optimally designed and you've also optimized the other components on your network such as client computers. In addition to using this planning guide to troubleshoot the steps you may have missed, we also have written a [Performance troubleshooting plan for Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .</span></span>
  
<span data-ttu-id="8adf0-541">以下是您可以使用回來的簡短連結：[https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span><span class="sxs-lookup"><span data-stu-id="8adf0-541">Here's a short link you can use to come back: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="8adf0-542">相關主題</span><span class="sxs-lookup"><span data-stu-id="8adf0-542">Related Topics</span></span>

[<span data-ttu-id="8adf0-543">對 Office 365 的網路連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-543">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="8adf0-544">Azure ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="8adf0-544">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="8adf0-545">管理 ExpressRoute for Office 365 連線</span><span class="sxs-lookup"><span data-stu-id="8adf0-545">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)
  
[<span data-ttu-id="8adf0-546">使用 ExpressRoute for Office 365 進行路由傳送</span><span class="sxs-lookup"><span data-stu-id="8adf0-546">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="8adf0-547">使用 ExpressRoute for Office 365 進行網路規劃</span><span class="sxs-lookup"><span data-stu-id="8adf0-547">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="8adf0-548">使用 Office 365 案例 （預覽） ExpressRoute BGP 社群 （英文）</span><span class="sxs-lookup"><span data-stu-id="8adf0-548">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="8adf0-549">媒體品質和 Skype 的線上商務的網路連線效能</span><span class="sxs-lookup"><span data-stu-id="8adf0-549">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="8adf0-550">Skype 的最佳化您的網路的線上商務</span><span class="sxs-lookup"><span data-stu-id="8adf0-550">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[<span data-ttu-id="8adf0-551">ExpressRoute 和 Skype Online 企業版的 QoS</span><span class="sxs-lookup"><span data-stu-id="8adf0-551">ExpressRoute and QoS in Skype for Business Online</span></span>](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[<span data-ttu-id="8adf0-552">使用 ExpressRoute 通話流程</span><span class="sxs-lookup"><span data-stu-id="8adf0-552">Call flow using ExpressRoute</span></span>](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[<span data-ttu-id="8adf0-553">使用基準與效能歷程記錄進行 Office 365 效能調整</span><span class="sxs-lookup"><span data-stu-id="8adf0-553">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="8adf0-554">Office 365 的效能疑難排解規劃</span><span class="sxs-lookup"><span data-stu-id="8adf0-554">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
  
[<span data-ttu-id="8adf0-555">Office 365 URL 與 IP 位址範圍</span><span class="sxs-lookup"><span data-stu-id="8adf0-555">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="8adf0-556">Office 365 網路和效能調整</span><span class="sxs-lookup"><span data-stu-id="8adf0-556">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
