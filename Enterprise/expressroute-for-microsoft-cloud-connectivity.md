---
title: Microsoft 雲端連線的 ExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 摘要： 了解如何 ExpressRoute 可協助您使用速度更快且更可靠連線至 Microsoft 雲端服務與平台。
ms.openlocfilehash: a3b36e98c946bc3ae7281bd38cd4b98820ee8afb
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574007"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="3e360-103">Microsoft 雲端連線的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3e360-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="3e360-104">**摘要：** 了解如何 ExpressRoute 可協助您使用速度更快且更可靠連線至 Microsoft 雲端服務與平台。</span><span class="sxs-lookup"><span data-stu-id="3e360-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="3e360-105">ExpressRoute 可提供連線至 Microsoft 雲端服務的隱私、專屬、高輸送量網路連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="3e360-106">Microsoft cloud 的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3e360-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="3e360-107">以下是 Microsoft cloud 不含 ExpressRoute 連線的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="3e360-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="3e360-108">**圖 1：不使用 ExpressRoute 的網路路徑**</span><span class="sxs-lookup"><span data-stu-id="3e360-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![圖 1：不使用 ExpressRoute 的網路路徑](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="3e360-110">圖 1 顯示在內部網路與 Microsoft 雲端之間的一般路徑。</span><span class="sxs-lookup"><span data-stu-id="3e360-110">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud.</span></span> <span data-ttu-id="3e360-111">在內部網路邊緣連線到網際網路透過 WAN 連結的 ISP。</span><span class="sxs-lookup"><span data-stu-id="3e360-111">The on-premises network edge connects to the Internet through a WAN link to an ISP.</span></span> <span data-ttu-id="3e360-112">流量然後一起出差在網際網路上的 Microsoft cloud 邊緣。</span><span class="sxs-lookup"><span data-stu-id="3e360-112">The traffic then travels across the Internet to the edge of the Microsoft cloud.</span></span> <span data-ttu-id="3e360-113">在 Microsoft cloud 中的雲端供應項目包括 Office 365、 Microsoft Azure、 Microsoft Intune 和 Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="3e360-113">Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365.</span></span> <span data-ttu-id="3e360-114">組織的使用者可以位於內部網路或網際網路上。</span><span class="sxs-lookup"><span data-stu-id="3e360-114">Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="3e360-115">如果沒有 ExpressRoute 連線，只有部分的 Microsoft 雲端的流量路徑可讓您控制 （與具有與服務提供者的關係） 是您在內部網路邊緣和您的 ISP 之間的連結。</span><span class="sxs-lookup"><span data-stu-id="3e360-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="3e360-116">您的 ISP 和 Microsoft 雲端邊緣之間的路徑是受限於中斷、 流量壅塞及監視惡意使用者在網際網路上的最佳傳遞系統。</span><span class="sxs-lookup"><span data-stu-id="3e360-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="3e360-117">漫遊或遠端使用者，例如，在網際網路上的使用者透過網際網路傳送至 Microsoft cloud 與其流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="3e360-118">以下是以 Microsoft cloud 具有 ExpressRoute 連線的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="3e360-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="3e360-119">**圖 2：使用 ExpressRoute 的網路路徑**</span><span class="sxs-lookup"><span data-stu-id="3e360-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![圖 2：使用 ExpressRoute 的網路路徑](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="3e360-121">圖 2 顯示兩個網路路徑。</span><span class="sxs-lookup"><span data-stu-id="3e360-121">Figure 2 shows two networking paths.</span></span> <span data-ttu-id="3e360-122">Microsoft Intune 的流量傳輸路徑相同一般網際網路流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-122">Traffic to Microsoft Intune travels the same path as normal Internet traffic.</span></span> <span data-ttu-id="3e360-123">Office 365、 Microsoft Azure 和 Dynamics 365 達成跨 ExpressRoute 連線、 內部網路邊緣與 Microsoft 雲端的邊緣之間的專用的路徑流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-123">Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="3e360-124">使用 ExpressRoute 連線] 中，您現在沒有控制權，透過服務供應商關係，透過 Microsoft 自您的整個流量路徑雲端 edge。</span><span class="sxs-lookup"><span data-stu-id="3e360-124">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge.</span></span> <span data-ttu-id="3e360-125">此連線所能提供可預測的效能與[99.95%執行時間 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)。</span><span class="sxs-lookup"><span data-stu-id="3e360-125">This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="3e360-126">您現在可以倚賴可預測的輸送量和延遲，根據您的服務提供者連線，Office 365、 Azure 和 Dynamics 365 服務。</span><span class="sxs-lookup"><span data-stu-id="3e360-126">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services.</span></span> <span data-ttu-id="3e360-127">ExpressRoute 連線至 Microsoft Intune 不支援這一次。</span><span class="sxs-lookup"><span data-stu-id="3e360-127">ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="3e360-128">ExpressRoute 連線傳送的流量會不再受到網際網路中斷、 流量壅塞和監視。</span><span class="sxs-lookup"><span data-stu-id="3e360-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="3e360-129">在網際網路上，例如漫遊或遠端使用者，使用者仍會傳送至 Microsoft cloud 與其流量透過網際網路。</span><span class="sxs-lookup"><span data-stu-id="3e360-129">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet.</span></span> <span data-ttu-id="3e360-130">其中一個例外是裝載在 Azure IaaS，透過內部部署網路的遠端存取連線 ExpressRoute 連線傳送中的企業營運應用程式內部網路線的流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-130">One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="3e360-131">即使具有 ExpressRoute 連線，某些流量仍會傳送網際網路 DNS 查詢，例如憑證撤銷清單檢查，以及內容傳遞網路 (CDN) 要求。</span><span class="sxs-lookup"><span data-stu-id="3e360-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="3e360-132">請參閱這些額外的資源，如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="3e360-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="3e360-133">ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="3e360-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="3e360-134">Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3e360-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="3e360-135">Azure ExpressRoute 的優點</span><span class="sxs-lookup"><span data-stu-id="3e360-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="3e360-136">以下是使用 ExpressRoute 的以 Azure 為基礎的雲端服務的一些優點：</span><span class="sxs-lookup"><span data-stu-id="3e360-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="3e360-137">**可預測的效能：** Microsoft cloud 的邊緣專用路徑，您的效能不會受限於網際網路提供者中斷與尖峰中的網際網路流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-137">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic.</span></span> <span data-ttu-id="3e360-138">您可以判斷並保留您的提供者至 Microsoft 雲端中負責對輸送量和延遲 SLA。</span><span class="sxs-lookup"><span data-stu-id="3e360-138">You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="3e360-139">**為您的流量資料隱私權：** 您專用的 ExpressRoute 連線傳送的流量不會受限於網際網路監控或封包擷取及分析惡意使用者。</span><span class="sxs-lookup"><span data-stu-id="3e360-139">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users.</span></span> <span data-ttu-id="3e360-140">它是一樣安全使用多重通訊協定標籤切換 MPLS 架構的 WAN 連結。</span><span class="sxs-lookup"><span data-stu-id="3e360-140">It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="3e360-141">**高輸送量連線：** Exchange 提供者和網路服務提供者的 ExpressRoute 連線的整體支援，您可以取得最多 10 個 Gbps 連結至 Microsoft 雲端。</span><span class="sxs-lookup"><span data-stu-id="3e360-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="3e360-142">**降低成本的一些設定：** 雖然 ExpressRoute 連線支付額外的費用，在某些情況下單一 ExpressRoute 連線可以成本小於增加網際網路容量在貴組織的多個位置提供給 Microsoft 雲端服務的適當輸送量。</span><span class="sxs-lookup"><span data-stu-id="3e360-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="3e360-143">ExpressRoute 連線並不保證郵件的較高的效能，每個組態中。</span><span class="sxs-lookup"><span data-stu-id="3e360-143">An ExpressRoute connection is not a guarantee of higher performance in every configuration.</span></span> <span data-ttu-id="3e360-144">它可能會有較低的效能透過低頻寬 ExpressRoute 連線較高頻寬網際網路連線，則只有幾個躍點開地區的 Microsoft 資料中心。</span><span class="sxs-lookup"><span data-stu-id="3e360-144">It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="3e360-145">使用 ExpressRoute 與 Office 365 的最新的建議，請參閱[ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。</span><span class="sxs-lookup"><span data-stu-id="3e360-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="3e360-146">ExpressRoute 連接模型</span><span class="sxs-lookup"><span data-stu-id="3e360-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="3e360-147">表 1 顯示 ExpressRoute 連線的三個主要 connectivity 模型。</span><span class="sxs-lookup"><span data-stu-id="3e360-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="3e360-148">**共置在雲端 exchange**</span><span class="sxs-lookup"><span data-stu-id="3e360-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="3e360-149">**點對點乙太網路**</span><span class="sxs-lookup"><span data-stu-id="3e360-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="3e360-150">**任何對多 (IP VPN) 連線**</span><span class="sxs-lookup"><span data-stu-id="3e360-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![ExpressRoute 連接模型：共置在雲端 Exchange 中](media/Network-Poster/ER-Conn1.png)|![ExpressRoute 連接模型：點對點乙太網路](media/Network-Poster/ER-Conn2.png)|![ExpressRoute 連接模型：多點對多點 (IP VPN) 連線](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="3e360-154">如果您的資料中心共同位於設備與雲端 exchange 中，您可以依虛擬跨-連線到代管提供者的乙太網路 exchange 透過 Microsoft 雲端。</span><span class="sxs-lookup"><span data-stu-id="3e360-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="3e360-155">如果您的資料中心位於您內部部署，您可以使用點對點乙太網路連結來連線至 Microsoft 雲端。</span><span class="sxs-lookup"><span data-stu-id="3e360-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="3e360-156">如果您已連線您組織的站台使用 IP VPN (MPLS) 提供者，Microsoft cloud ExpressRoute 連線的行為類似您私人 WAN 上的另一個位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="3e360-157">**表 1: ExpressRoute 連線模型**</span><span class="sxs-lookup"><span data-stu-id="3e360-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="3e360-158">Microsoft 雲端服務的 ExpressRoute 對等關係</span><span class="sxs-lookup"><span data-stu-id="3e360-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="3e360-159">單一 ExpressRoute 連線支援最多兩個不同框線閘道通訊協定 (BGP) 對等關係的 Microsoft cloud 的不同組件。</span><span class="sxs-lookup"><span data-stu-id="3e360-159">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud.</span></span> <span data-ttu-id="3e360-160">BPG 使用對等關係來建立信任關係，且 exchange 路由的資訊。</span><span class="sxs-lookup"><span data-stu-id="3e360-160">BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="3e360-161">**圖 3: 兩個不同的 BGP 關係中的單一的 ExpressRoute 連線**</span><span class="sxs-lookup"><span data-stu-id="3e360-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![圖 3: 兩個不同的 BGP 關係中的單一的 ExpressRoute 連線](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="3e360-163">圖 3 顯示從內部網路的 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-163">Figure 3 shows an ExpressRoute connection from an on-premises network.</span></span> <span data-ttu-id="3e360-164">ExpressRoute 連接有兩個邏輯的對等關係。</span><span class="sxs-lookup"><span data-stu-id="3e360-164">The ExpressRoute connection has two logical peering relationships.</span></span> <span data-ttu-id="3e360-165">Microsoft 對等關係移至 Microsoft SaaS 服務，包括 Office 365、 Dynamcs 365 和 Azure PaaS 服務。</span><span class="sxs-lookup"><span data-stu-id="3e360-165">A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services.</span></span> <span data-ttu-id="3e360-166">Azure IaaS，並裝載虛擬機器的虛擬網路閘道，則會移私用的對等關係。</span><span class="sxs-lookup"><span data-stu-id="3e360-166">A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="3e360-167">Microsoft 對等 BGP 關係：</span><span class="sxs-lookup"><span data-stu-id="3e360-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="3e360-168">從您 DMZ 中的路由器為 Office 365、 Dynamics 365 和 Azure 服務的公用地址。</span><span class="sxs-lookup"><span data-stu-id="3e360-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="3e360-169">支援雙向起始通訊。</span><span class="sxs-lookup"><span data-stu-id="3e360-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="3e360-170">私用的對等 BGP 關係：</span><span class="sxs-lookup"><span data-stu-id="3e360-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="3e360-171">從組織網路邊界的路由器為指派給 Azure Vnet 的私人 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="3e360-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="3e360-172">支援雙向起始通訊。</span><span class="sxs-lookup"><span data-stu-id="3e360-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="3e360-173">是您組織網路的 Microsoft cloud，完整的內部一致的處理和路由的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="3e360-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="3e360-174">在舊版的這篇文章所述的公用對等 BGP 關係已被取代。</span><span class="sxs-lookup"><span data-stu-id="3e360-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="3e360-175">使用 ExpressRoute 的應用程式部署和流量流程的範例</span><span class="sxs-lookup"><span data-stu-id="3e360-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="3e360-176">流量流經 ExpressRoute 連線，並在 Microsoft cloud 中的方式是在路徑的來源與目的地和應用程式行為之間躍點路由的函式。</span><span class="sxs-lookup"><span data-stu-id="3e360-176">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior.</span></span> <span data-ttu-id="3e360-177">以下是透過站台對站 VPN 連線會存取內部部署 SharePoint 伺服器陣列的 Azure 虛擬機器上執行應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="3e360-177">Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="3e360-178">**圖 4：Azure 虛擬機器上的應用程式，會存取內部部署 SharePoint 伺服器陣列**</span><span class="sxs-lookup"><span data-stu-id="3e360-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![圖 4：Azure 虛擬機器上的應用程式，會存取內部部署 SharePoint 伺服器陣列](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="3e360-180">圖 4 顯示應用程式伺服器之間流動的內部部署 SharePoint 伺服器陣列、 內部網路與在 Azure IaaS 中，為 Azure IaaS 虛擬機器和流量執行應用程式伺服器的虛擬網路之間的站台對站 VPN 連線和在 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="3e360-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="3e360-181">應用程式找出 SharePoint 伺服器陣列使用內部部署 DNS 的 IP 位址和所有流量透過站台對站 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="3e360-182">此組織移轉至 Office 365 中 SharePoint Online 的其內部部署 SharePoint 伺服器陣列，並部署 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="3e360-183">**圖 5：將內部部署 SharePoint 伺服器陣列移動到 SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="3e360-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![圖 5：將內部部署 SharePoint 伺服器陣列移動到 SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="3e360-185">圖 5 顯示與對等關係的 ExpressRoute 連線新增至 Microsoft SaaS 和 Office 365 和 Azure IaaS 包含虛擬網路上的應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="3e360-185">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network.</span></span> <span data-ttu-id="3e360-186">SharePoint 內部部署伺服器陣列已移轉至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3e360-186">The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="3e360-187">與 Microsoft 私用的對等關係：</span><span class="sxs-lookup"><span data-stu-id="3e360-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="3e360-188">從 Azure 虛擬網路閘道，內部部署位置都是可用的 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="3e360-189">從 Office 365 訂閱，公用 IP 位址的邊緣裝置，例如 proxy 伺服器，可透過 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="3e360-190">從內部網路邊緣，Azure VNet 的私人 IP 位址和 Office 365 的公用 IP 位址都是可用的 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="3e360-191">當應用程式存取 Url 的 SharePoint Online 時，它會透過 ExpressRoute 連線至 edge 中的 proxy 伺服器轉送其流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="3e360-192">時使用 proxy 伺服器會找出 SharePoint Online 的 IP 位址，它會將流量轉送回透過 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-192">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection.</span></span> <span data-ttu-id="3e360-193">回應流量流經反向路徑。</span><span class="sxs-lookup"><span data-stu-id="3e360-193">Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="3e360-194">**圖 6：當 SharePoint 伺服器陣列已移轉至 Office 365 的 SharePoint Online 時的流量**</span><span class="sxs-lookup"><span data-stu-id="3e360-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![圖 6：當 SharePoint 伺服器陣列已移轉至 Office 365 的 SharePoint Online 時的流量](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="3e360-196">圖 6 顯示如何應用程式伺服器與 Office 365 中 SharePoint Online 之間的流量透過私人的對等關係，從內部部署網路邊界，應用程式伺服器，然後從 edge 上流通 Microsoft 對等關係Office 365。</span><span class="sxs-lookup"><span data-stu-id="3e360-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="3e360-197">結果是髮型釘選的路由和應用程式行為的後果。</span><span class="sxs-lookup"><span data-stu-id="3e360-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="3e360-198">ExpressRoute 和 Microsoft 的雲端網路</span><span class="sxs-lookup"><span data-stu-id="3e360-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="3e360-199">兩個不同的版本中的 ExpressRoute 連線可用： ExpressRoute 和 ExpressRoute 進階版。</span><span class="sxs-lookup"><span data-stu-id="3e360-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="3e360-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3e360-200">ExpressRoute</span></span>

<span data-ttu-id="3e360-201">如何流量流經之間您組織的網路與 Microsoft 資料中心是組合：</span><span class="sxs-lookup"><span data-stu-id="3e360-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="3e360-202">您的位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-202">Your locations.</span></span>
    
- <span data-ttu-id="3e360-203">Microsoft 雲端對等的位置 （連線至 Microsoft edge 的實體位置）。</span><span class="sxs-lookup"><span data-stu-id="3e360-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="3e360-204">Microsoft 資料中心位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="3e360-205">Microsoft 資料中心和對等位置的雲端所有連線至 Microsoft 雲端網路。</span><span class="sxs-lookup"><span data-stu-id="3e360-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="3e360-206">當您建立 ExpressRoute 連線至 Microsoft 雲端的對等位置時，您會連線至 Microsoft 雲端網路與中相同洲的所有 Microsoft 資料中心位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-206">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent.</span></span> <span data-ttu-id="3e360-207">雲端對等位置與目的地 Microsoft 資料中心之間的流量會存在於 Microsoft 雲端網路。</span><span class="sxs-lookup"><span data-stu-id="3e360-207">The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="3e360-208">這可能導致非最佳傳遞至本機 Microsoft 資料中心，任何對多 connectivity 模型。</span><span class="sxs-lookup"><span data-stu-id="3e360-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="3e360-209">**使用單一 ExpressRoute 連線的地理位置分散的組織圖 7： 範例**</span><span class="sxs-lookup"><span data-stu-id="3e360-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![使用單一 ExpressRoute 連線的地理位置分散的組織圖 7： 範例](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="3e360-211">圖 7 顯示兩個位置，組織中的美國西北位置 1 和東北中的位置 2。</span><span class="sxs-lookup"><span data-stu-id="3e360-211">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast.</span></span> <span data-ttu-id="3e360-212">他們是透過任何對多 WAN 提供者連接。</span><span class="sxs-lookup"><span data-stu-id="3e360-212">They are connected by an any-to-any WAN provider.</span></span> <span data-ttu-id="3e360-213">此組織也有 ExpressRoute 連線到西岸上的 Microsoft 對等位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-213">This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast.</span></span> <span data-ttu-id="3e360-214">東北目的地東西岸資料中心中的來自位置 2 流量必須旅行一路跨組織的 WAN 西岸，Microsoft 對等的位置，然後再回到國內各地透過 Microsoft 雲端網路東西岸資料中心。</span><span class="sxs-lookup"><span data-stu-id="3e360-214">Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="3e360-215">最佳傳遞，使用多重 ExpressRoute 連線至地區的 Microsoft 雲端對等位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="3e360-216">**圖 8：使用多重 ExpressRoute 連線，以求對區域資料中心傳遞的最佳化**</span><span class="sxs-lookup"><span data-stu-id="3e360-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![圖 8：使用多重 ExpressRoute 連線，以求對區域資料中心傳遞的最佳化](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="3e360-218">圖 8 顯示相同的組織有兩個 ExpressRoute 連線，其中每個位置，請到當地 Microsoft 對等位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-218">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations.</span></span> <span data-ttu-id="3e360-219">在此組態中，從位置 2 在目的地東西岸資料中心東北流量直接至東西岸對等位置、 Microsoft 雲端網路時，然後再到東亞西岸資料中心。</span><span class="sxs-lookup"><span data-stu-id="3e360-219">In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="3e360-220">多重 ExpressRoute 連線可以提供：</span><span class="sxs-lookup"><span data-stu-id="3e360-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="3e360-221">當地 Microsoft 資料中心位置的較佳效能。</span><span class="sxs-lookup"><span data-stu-id="3e360-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="3e360-222">至 Microsoft 雲端的本機的 ExpressRoute 連線變成無法使用時的高可用性。</span><span class="sxs-lookup"><span data-stu-id="3e360-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="3e360-223">這非常適合在同一個洲的組織。</span><span class="sxs-lookup"><span data-stu-id="3e360-223">This works well for organizations in the same continent.</span></span> <span data-ttu-id="3e360-224">不過，在網際網路上移動到 Microsoft 資料中心外部組織的洲的流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-224">However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="3e360-225">洲際透過 Microsoft 雲端網路流量，您必須使用 ExpressRoute 高階連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="3e360-226">ExpressRoute 進階版</span><span class="sxs-lookup"><span data-stu-id="3e360-226">ExpressRoute Premium</span></span>

<span data-ttu-id="3e360-227">全域分佈洲的組織，您可以使用 ExpressRoute 進階版。</span><span class="sxs-lookup"><span data-stu-id="3e360-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="3e360-228">使用 ExpressRoute 進階版，您可以連線到任何大陸上任何大陸任何 Microsoft 對等位置上的任何 Microsoft 資料中心。</span><span class="sxs-lookup"><span data-stu-id="3e360-228">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent.</span></span> <span data-ttu-id="3e360-229">Continents 之間的流量會存在於 Microsoft 雲端網路。</span><span class="sxs-lookup"><span data-stu-id="3e360-229">The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="3e360-230">使用多重 ExpressRoute 高階連線，您可以：</span><span class="sxs-lookup"><span data-stu-id="3e360-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="3e360-231">Continentally 本機 Microsoft 資料中心的較佳效能。</span><span class="sxs-lookup"><span data-stu-id="3e360-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="3e360-232">至全域的 Microsoft cloud 本機的 ExpressRoute 連線變成無法使用時的高可用性。</span><span class="sxs-lookup"><span data-stu-id="3e360-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="3e360-233">需要 Office 365 型 ExpressRoute 連線 ExpressRoute 進階版。</span><span class="sxs-lookup"><span data-stu-id="3e360-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="3e360-234">**圖 9： 全球 Microsoft 雲端網路**</span><span class="sxs-lookup"><span data-stu-id="3e360-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![圖 9： 全球 Microsoft 雲端網路](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="3e360-236">圖 9 顯示全球 Microsoft 雲端網路，跨洲和全球和其相對的區域網路使用的邏輯圖表。</span><span class="sxs-lookup"><span data-stu-id="3e360-236">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections.</span></span> <span data-ttu-id="3e360-237">與 Microsoft 雲端網路中每個洲的一部分，全域企業會建立 ExpressRoute 高階連線從其地區中心辦公室到本機 Microsoft 對等位置。</span><span class="sxs-lookup"><span data-stu-id="3e360-237">With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="3e360-238">地區的 office、 適當的 Office 365 流量：</span><span class="sxs-lookup"><span data-stu-id="3e360-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="3e360-239">大陸 Office 365 資料中心，透過 Microsoft 雲端網路內大陸。</span><span class="sxs-lookup"><span data-stu-id="3e360-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="3e360-240">在另一個洲的 office 365 資料中心，透過洲際的 Microsoft 雲端網路。</span><span class="sxs-lookup"><span data-stu-id="3e360-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="3e360-241">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="3e360-241">For more information, see:</span></span>
  
- [<span data-ttu-id="3e360-242">Azure ExpressRoute for Office 365 訓練</span><span class="sxs-lookup"><span data-stu-id="3e360-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="3e360-243">Office 365 的網路規劃與效能調整</span><span class="sxs-lookup"><span data-stu-id="3e360-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="expressroute-options"></a><span data-ttu-id="3e360-244">ExpressRoute 選項</span><span class="sxs-lookup"><span data-stu-id="3e360-244">ExpressRoute options</span></span>

<span data-ttu-id="3e360-245">您也可以將下列選項併入 ExpressRoute 部署：</span><span class="sxs-lookup"><span data-stu-id="3e360-245">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="3e360-246">**安全性，請參閱您 edge:** 若要流量傳送和接收透過 ExpressRoute 連線，例如流量檢查或入侵/惡意程式碼偵測，提供進階的安全性放置安全性設備中的流量路徑，您 DMZ 中或在您的內部網路的框線。</span><span class="sxs-lookup"><span data-stu-id="3e360-246">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="3e360-247">**Vm 的網際網路流量：** 若要防止 Azure Vm 初始化直接與網際網路位置的流量，通告預設路由傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="3e360-247">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft.</span></span> <span data-ttu-id="3e360-248">透過 ExpressRoute 連線並透過您內部部署 proxy 伺服器，會路由傳送至網際網路的流量。</span><span class="sxs-lookup"><span data-stu-id="3e360-248">Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers.</span></span> <span data-ttu-id="3e360-249">從 Azure Vm Azure PaaS 服務或 Office 365 的流量路由傳送回透過 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3e360-249">Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="3e360-250">**WAN 最佳化程式：** 您可以部署在私人的對等連線的兩邊的 WAN 最佳化程式的跨單位 Azure 虛擬網路 (VNet)。</span><span class="sxs-lookup"><span data-stu-id="3e360-250">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet).</span></span> <span data-ttu-id="3e360-251">內部 Azure VNet 中，使用來自 Azure marketplace 和使用者定義路由 WAN 的最佳化網路應用裝置透過裝置所傳入的流量路由傳送。</span><span class="sxs-lookup"><span data-stu-id="3e360-251">Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="3e360-252">**的服務品質：** 使用您的流量 IPv4 標頭中的區別服務代碼點 (DSCP) 值，來標示語音、 互動式視訊/，或最佳傳遞。</span><span class="sxs-lookup"><span data-stu-id="3e360-252">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery.</span></span> <span data-ttu-id="3e360-253">這是 Microsoft 對等關係與 Skype for Business Online 流量特別重要。</span><span class="sxs-lookup"><span data-stu-id="3e360-253">This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="3e360-254">請參閱這些額外的資源，如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="3e360-254">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="3e360-255">ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="3e360-255">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="3e360-256">Azure ExpressRoute for Office 365 訓練</span><span class="sxs-lookup"><span data-stu-id="3e360-256">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="3e360-257">Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3e360-257">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="3e360-258">下一步</span><span class="sxs-lookup"><span data-stu-id="3e360-258">Next step</span></span>

[<span data-ttu-id="3e360-259">設計 Microsoft SaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="3e360-259">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="3e360-260">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e360-260">See also</span></span>

[<span data-ttu-id="3e360-261">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="3e360-261">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="3e360-262">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="3e360-262">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

