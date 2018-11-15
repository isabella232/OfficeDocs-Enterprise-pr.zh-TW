---
title: Microsoft 雲端連線的 ExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/03/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 摘要： 了解如何 ExpressRoute 可協助您更快且更可靠連線至 Microsoft 雲端服務和平台。
ms.openlocfilehash: 1cd78372d37e40a53ba7725ff3653ef01daa48b0
ms.sourcegitcommit: 9da69a749ba557a4c4ae80070ce57e606148521f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "26525834"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="3691f-103">Microsoft 雲端連線的 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3691f-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="3691f-104">**摘要：** 了解如何 ExpressRoute 可協助您更快且更可靠連線至 Microsoft 雲端服務和平台。</span><span class="sxs-lookup"><span data-stu-id="3691f-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="3691f-105">ExpressRoute 可提供連線至 Microsoft 雲端服務的隱私、專屬、高輸送量網路連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="3691f-106">以 Microsoft cloud ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3691f-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="3691f-107">以下是 Microsoft cloud ExpressRoute 連線的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="3691f-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="3691f-108">**圖 1：不使用 ExpressRoute 的網路路徑**</span><span class="sxs-lookup"><span data-stu-id="3691f-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![圖 1：不使用 ExpressRoute 的網路路徑](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="3691f-p101">圖 1 顯示的內部網路與 Microsoft cloud 之間的一般路徑。在內部網路邊緣連線至網際網路透過 WAN 連結的 ISP。流量然後一起出差經由網際網路 Microsoft cloud 的邊緣。Microsoft 雲端中的雲端方案包含 Office 365、 Microsoft Azure、 Microsoft Intune 及 Dynamics 365。組織中的使用者可以是位在內部網路或網際網路上。</span><span class="sxs-lookup"><span data-stu-id="3691f-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="3691f-115">沒有 ExpressRoute 連線，僅部分的 Microsoft cloud 流量路徑您可以控制 （且與服務提供者的關係） 是您在內部網路邊緣和您的 ISP 之間的連結。</span><span class="sxs-lookup"><span data-stu-id="3691f-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="3691f-116">您的 ISP 與 Microsoft cloud 邊緣間的路徑是適合投入比傳遞系統中斷、 流量壅塞以及監控惡意使用者在網際網路上。</span><span class="sxs-lookup"><span data-stu-id="3691f-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="3691f-117">漫遊或遠端使用者，例如，在網際網路上的使用者透過網際網路傳送至 Microsoft cloud 其流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="3691f-118">以下是 Microsoft cloud ExpressRoute 連線的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="3691f-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="3691f-119">**圖 2：使用 ExpressRoute 的網路路徑**</span><span class="sxs-lookup"><span data-stu-id="3691f-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![圖 2：使用 ExpressRoute 的網路路徑](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="3691f-p102">圖 2 顯示兩個網路路徑。Microsoft Intune 流量一起出差標準網際網路流量為相同的路徑。Office 365、 Microsoft Azure 和 Dynamics 365 達成跨 ExpressRoute 連線、 專用的路徑與內部網路的 edge 和 Microsoft cloud 緣之間的流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="3691f-p103">包含 ExpressRoute 連線，您現在可控制，透過與服務提供者的關係，透過 Microsoft 自您的整個流量路徑雲端 edge。可預測的效能與[99.95%執行時間 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)可以提供此連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="3691f-p104">您現在可以計算上可預測的輸送量和延遲，根據到 Office 365、 Azure、 和 Dynamics 365 服務的服務提供者的連線。Microsoft Intune ExpressRoute 連線不支援這一次。</span><span class="sxs-lookup"><span data-stu-id="3691f-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="3691f-128">受限於網際網路中斷、 流量壅塞及監視不再有透過 ExpressRoute 連線傳送的流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="3691f-p105">漫遊或遠端使用者，例如，在網際網路上的使用者仍會傳送給 Microsoft cloud 其流量透過網際網路。有一個例外是架設在 Azure IaaS，透過遠端存取連線至內部網路 ExpressRoute 連傳送的商務應用程式的內部網路線條的流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="3691f-131">即使具有 ExpressRoute 連線，某些流量仍傳送網際網路 DNS 查詢，例如憑證撤銷清單檢查，而且內容傳遞網路 (CDN) 要求。</span><span class="sxs-lookup"><span data-stu-id="3691f-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="3691f-132">請參閱如需詳細資訊下列額外資源：</span><span class="sxs-lookup"><span data-stu-id="3691f-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="3691f-133">ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="3691f-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="3691f-134">Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3691f-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="3691f-135">Azure ExpressRoute 的優點</span><span class="sxs-lookup"><span data-stu-id="3691f-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="3691f-136">以下是使用 ExpressRoute Azure 型雲端服務的部分優點：</span><span class="sxs-lookup"><span data-stu-id="3691f-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="3691f-p106">**可預測的效能：** 包含 Microsoft cloud 緣專用路徑，您的效能不會受限於網際網路提供者中斷與暴增在網際網路的流量。您可以決定並保留以 Microsoft cloud 努力輸送量和延遲 SLA 來提供者。</span><span class="sxs-lookup"><span data-stu-id="3691f-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="3691f-p107">**您流量資料隱私權：** 透過專用的 ExpressRoute 連線傳送的流量不會受限於網際網路監控或封包擷取及分析惡意使用者。它會為安全使用多重通訊協定標籤切換 MPLS 為基礎的 WAN 連結。</span><span class="sxs-lookup"><span data-stu-id="3691f-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="3691f-141">**高輸送量連線：** 整體 ExpressRoute 連線 exchange 提供者及網路服務提供者支援，您可以取得最多 10 個 Gbps 連結到 Microsoft 雲端。</span><span class="sxs-lookup"><span data-stu-id="3691f-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="3691f-142">**降低成本的一些設定：** 雖然 ExpressRoute 連線的其他成本，但在某些情況下的單一 ExpressRoute 連線可以成本小於增加提供適當輸送量 Microsoft 雲端服務在多個位置貴組織的網際網路容量。</span><span class="sxs-lookup"><span data-stu-id="3691f-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="3691f-p108">ExpressRoute 連線不保證郵件可以在每個設定較高的效能。有可能已透過低頻寬 ExpressRoute 連線比為只從地區的 Microsoft 資料中心幾個躍點高頻寬網際網路連線的較低的效能。</span><span class="sxs-lookup"><span data-stu-id="3691f-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="3691f-145">搭配 Office 365 使用 ExpressRoute 的最新建議，請參閱[Office 365 ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)。</span><span class="sxs-lookup"><span data-stu-id="3691f-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="3691f-146">ExpressRoute connectivity 模型</span><span class="sxs-lookup"><span data-stu-id="3691f-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="3691f-147">表 1 顯示 ExpressRoute 連線的三個主要 connectivity 的模型。</span><span class="sxs-lookup"><span data-stu-id="3691f-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="3691f-148">**共同位於雲端 exchange**</span><span class="sxs-lookup"><span data-stu-id="3691f-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="3691f-149">**點對點乙太網路**</span><span class="sxs-lookup"><span data-stu-id="3691f-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="3691f-150">**任何-任何 (IP VPN) 連線**</span><span class="sxs-lookup"><span data-stu-id="3691f-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![ExpressRoute 連接模型：共置在雲端 Exchange 中](media/Network-Poster/ER-Conn1.png)|![ExpressRoute 連接模型：點對點乙太網路](media/Network-Poster/ER-Conn2.png)|![ExpressRoute 連接模型：多點對多點 (IP VPN) 連線](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="3691f-154">如果您的資料中心共同位於與雲端 exchange 設備、 可排序虛擬跨連線至 Microsoft 雲端透過代管提供者的乙太網路交換。</span><span class="sxs-lookup"><span data-stu-id="3691f-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="3691f-155">如果您的資料中心位於您內部部署，您可以使用的點對點乙太網路連結來連線至 Microsoft cloud。</span><span class="sxs-lookup"><span data-stu-id="3691f-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="3691f-156">如果您已經在使用的 IP VPN (MPLS) 提供者連接組織的網站、 Microsoft cloud ExpressRoute 連線 bot 通常在私人的 WAN 的另一個位置。</span><span class="sxs-lookup"><span data-stu-id="3691f-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="3691f-157">**表 1: ExpressRoute connectivity 模型**</span><span class="sxs-lookup"><span data-stu-id="3691f-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="3691f-158">Microsoft 雲端服務的 ExpressRoute 對等關係</span><span class="sxs-lookup"><span data-stu-id="3691f-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="3691f-p109">單一 ExpressRoute 連線支援多達三個不同框線閘道通訊協定 (BGP) 對等關聯至 Microsoft cloud 的不同組件。BPG 使用對等的關聯性建立信任及 exchange 路由資訊。</span><span class="sxs-lookup"><span data-stu-id="3691f-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="3691f-161">**圖 3：單一的 ExpressRoute 連線中三種不同的 BGP關係**</span><span class="sxs-lookup"><span data-stu-id="3691f-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![圖 3：單一的 ExpressRoute 連線中三種不同的 BGP關係](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="3691f-p110">圖 3 是從內部網路 ExpressRoute 連線。ExpressRoute 連線有三個邏輯的對等關係。Microsoft 對等關係前往 Microsoft saas 和服務，包括 Office 365 和 Dynamcs CRM Online。公用的對等關係會移至 Azure PaaS 服務。私人的對等關係會移至 Azure IaaS 以及主控虛擬機器時的虛擬網路閘道。</span><span class="sxs-lookup"><span data-stu-id="3691f-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection has three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="3691f-168">Microsoft 對等 BGP 關係：</span><span class="sxs-lookup"><span data-stu-id="3691f-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="3691f-169">在您 DMZ 路由器從 Office 365 和 Dynamics 365 服務公用地址。</span><span class="sxs-lookup"><span data-stu-id="3691f-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="3691f-170">支援雙向起始的通訊。</span><span class="sxs-lookup"><span data-stu-id="3691f-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="3691f-171">公用的對等 BGP 關係：</span><span class="sxs-lookup"><span data-stu-id="3691f-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="3691f-172">在您 DMZ 路由器從 Azure 服務公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="3691f-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="3691f-p111">支援單向起始通訊從僅內部部署系統。對等關係不支援從 Azure PaaS 服務起始的通訊。</span><span class="sxs-lookup"><span data-stu-id="3691f-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="3691f-175">私人的對等 BGP 關係：</span><span class="sxs-lookup"><span data-stu-id="3691f-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="3691f-176">從您組織的網路邊緣上的路由器指派給 Azure VNets 的私人 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="3691f-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="3691f-177">支援雙向起始的通訊。</span><span class="sxs-lookup"><span data-stu-id="3691f-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="3691f-178">為副檔名為 Microsoft cloud 完成與內部一致的處理和路由傳送至您組織的網路。</span><span class="sxs-lookup"><span data-stu-id="3691f-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="3691f-179">使用 ExpressRoute 的應用程式部署和流量流程的範例</span><span class="sxs-lookup"><span data-stu-id="3691f-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="3691f-p112">流量一起出差 ExpressRoute 連線和 Microsoft cloud 內是在路徑的來源與目的地及應用程式的行為之間旋入之路由的函數。以下是透過網站 VPN 連線存取內部部署 SharePoint 伺服器陣列 Azure 虛擬機器上執行的應用程式的範例。</span><span class="sxs-lookup"><span data-stu-id="3691f-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="3691f-182">**圖 4：Azure 虛擬機器上的應用程式，會存取內部部署 Sharepoint 伺服器陣列**</span><span class="sxs-lookup"><span data-stu-id="3691f-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![圖 4：Azure 虛擬機器上的應用程式，會存取內部部署 Sharepoint 伺服器陣列](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="3691f-184">圖 4 顯示內部部署 SharePoint 伺服器陣列、 網站 VPN 連線與內部網路和虛擬網路以 Azure IaaS、 Azure IaaS 虛擬機器與流量所執行的應用程式伺服器之間的應用程式伺服器之間的流程和SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="3691f-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="3691f-185">會找出應用程式使用的內部 DNS 的 SharePoint 伺服器陣列的 IP 位址及所有流量會都移至網站 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="3691f-186">此組織移轉至 SharePoint Online 在 Office 365 中的其內部部署 SharePoint 伺服器陣列並部署 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="3691f-187">**圖 5：將內部部署 SharePoint 伺服器陣列移動到 SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="3691f-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![圖 5：將內部部署 SharePoint 伺服器陣列移動到 SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="3691f-p113">圖 5 顯示的對等相關聯的 ExpressRoute 連線至 Microsoft saas 和與 Office 365 和 Azure IaaS 包含應用程式伺服器上的虛擬網路。SharePoint 內部部署伺服器陣列已移轉至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3691f-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="3691f-191">Microsoft 與私人的對等關係：</span><span class="sxs-lookup"><span data-stu-id="3691f-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="3691f-192">Azure 虛擬網路閘道，從內部部署位置中都是可用的 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="3691f-193">從 Office 365 訂閱的 edge 裝置，例如 proxy 伺服器的公用 IP 位址是透過提供 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="3691f-194">從內部網路邊緣、 Azure VNet 的私人 IP 位址與 Office 365 的公用 IP 位址是透過提供 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="3691f-195">時之應用程式存取 Url 的 SharePoint Online，它會跨 ExpressRoute 連線到 proxy 伺服器中的 edge 轉寄其流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="3691f-p114">時使用 proxy 伺服器尋找 SharePoint Online 的 IP 位址，它會回復 ExpressRoute 連轉送流量。回應流量一起出差反向的路徑。</span><span class="sxs-lookup"><span data-stu-id="3691f-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="3691f-198">**圖 6：當 SharePoint 伺服器陣列已移轉至 Office 365 的 SharePoint Online 時的流量**</span><span class="sxs-lookup"><span data-stu-id="3691f-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![圖 6：當 SharePoint 伺服器陣列已移轉至 Office 365 的 SharePoint Online 時的流量](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="3691f-200">圖 6 顯示應用程式伺服器與 SharePoint Online 在 Office 365 之間的流量透過 Microsoft 對等關係流向透過私人對等關係從應用程式伺服器的內部網路邊緣，然後從邊緣Office 365。</span><span class="sxs-lookup"><span data-stu-id="3691f-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="3691f-201">結果是行為的字形固定的路由和應用程式的後果。</span><span class="sxs-lookup"><span data-stu-id="3691f-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="3691f-202">ExpressRoute 與 Microsoft 的雲端網路</span><span class="sxs-lookup"><span data-stu-id="3691f-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="3691f-203">ExpressRoute 連線會提供兩種不同的版本： ExpressRoute 與 ExpressRoute Premium。</span><span class="sxs-lookup"><span data-stu-id="3691f-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="3691f-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3691f-204">ExpressRoute</span></span>

<span data-ttu-id="3691f-205">如何組織網路與 Microsoft 資料中心是組合之間一起出差的流量：</span><span class="sxs-lookup"><span data-stu-id="3691f-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="3691f-206">您的位置。</span><span class="sxs-lookup"><span data-stu-id="3691f-206">Your locations.</span></span>
    
- <span data-ttu-id="3691f-207">Microsoft 雲端對等的位置 （以連線至 Microsoft edge 的實體位置）。</span><span class="sxs-lookup"><span data-stu-id="3691f-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="3691f-208">Microsoft 資料中心位置。</span><span class="sxs-lookup"><span data-stu-id="3691f-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="3691f-209">Microsoft 資料中心及雲端對等位置所有連線至 Microsoft cloud 網路。</span><span class="sxs-lookup"><span data-stu-id="3691f-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="3691f-p115">當您建立 ExpressRoute 連線至 Microsoft cloud 對等位置時，您會連線到 Microsoft cloud 網路和同一個大陸中的所有 Microsoft 資料中心位置。透過 Microsoft 雲端網路執行是雲端對等位置與目的地 Microsoft 資料中心之間的流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="3691f-212">這可能會導致非最佳傳遞到任何-任何 connectivity 模型的本機 Microsoft 資料中心。</span><span class="sxs-lookup"><span data-stu-id="3691f-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="3691f-213">**圖 7： 範例中的地理位置分散的組織使用的單一 ExpressRoute 連線**</span><span class="sxs-lookup"><span data-stu-id="3691f-213">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![圖 7： 範例中的地理位置分散的組織使用的單一 ExpressRoute 連線](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="3691f-p116">圖 7 顯示兩個位置與組織中的美國西北位置 1 和東北中的位置 2。他們是透過任何-任何 WAN 提供者連接。此組織也有 ExpressRoute 連線到西岸上的 Microsoft 對等位置。東北目的地東岸 datacenter 位置 2 流量必須旅行社一直跨組織的 WAN 西岸到 Microsoft 對等的位置並再回到跨國家透過 Microsoft 雲端網路東岸資料中心。</span><span class="sxs-lookup"><span data-stu-id="3691f-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="3691f-219">最佳傳遞的使用多個 ExpressRoute 連線至區域 Microsoft cloud 對等的位置。</span><span class="sxs-lookup"><span data-stu-id="3691f-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="3691f-220">**圖 8：使用多重 ExpressRoute 連線，以求對區域資料中心傳遞的最佳化**</span><span class="sxs-lookup"><span data-stu-id="3691f-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![圖 8：使用多重 ExpressRoute 連線，以求對區域資料中心傳遞的最佳化](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="3691f-p117">圖 8 顯示含有兩個 ExpressRoute 連線，一個用於每個位置、 地域本機 Microsoft 對等位置相同組織。在此組態中，位置 2 東北目的地東岸資料中心中的流量會移至東岸對等位置直接、 Microsoft cloud 網路]、 [東岸資料中心。</span><span class="sxs-lookup"><span data-stu-id="3691f-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="3691f-224">多個 ExpressRoute 連線可以提供：</span><span class="sxs-lookup"><span data-stu-id="3691f-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="3691f-225">更好的效能與地域本機 Microsoft 資料中心位置。</span><span class="sxs-lookup"><span data-stu-id="3691f-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="3691f-226">以 Microsoft cloud 本機 ExpressRoute 連線變成無法使用時的較高可用性。</span><span class="sxs-lookup"><span data-stu-id="3691f-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="3691f-p118">這項措施適用於在同一個大陸的組織。不過，透過網際網路一起出差到外部組織的大陸 Microsoft 資料中心的流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="3691f-229">對於洲際透過 Microsoft 雲端網路流量，您必須使用 ExpressRoute 高階的連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="3691f-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="3691f-230">ExpressRoute Premium</span></span>

<span data-ttu-id="3691f-231">對於全域分散於 continents 的組織而言，您可以使用 ExpressRoute Premium。</span><span class="sxs-lookup"><span data-stu-id="3691f-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="3691f-p119">使用 ExpressRoute Premium 您可以達到任何大陸從任何大陸上任何 Microsoft 對等位置上的任何 Microsoft 資料中心。透過 Microsoft 雲端網路執行是 continents 之間的流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="3691f-234">含有多個 ExpressRoute Premium 連線，您可以：</span><span class="sxs-lookup"><span data-stu-id="3691f-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="3691f-235">Continentally 本機 Microsoft 資料中心來提升效能。</span><span class="sxs-lookup"><span data-stu-id="3691f-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="3691f-236">以全域 Microsoft cloud 本機 ExpressRoute 連線變成無法使用時的較高可用性。</span><span class="sxs-lookup"><span data-stu-id="3691f-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="3691f-p120">ExpressRoute Premium 是必要的 Office 365 型 ExpressRoute 連線。不過，是企業版與 500 或更多授權使用者的其他成本。</span><span class="sxs-lookup"><span data-stu-id="3691f-p120">ExpressRoute Premium is required for Office 365-based ExpressRoute connections. However, there is no additional cost for enterprises with 500 or more licensed users.</span></span>
  
<span data-ttu-id="3691f-239">**圖 9： World wide Microsoft cloud 網路**</span><span class="sxs-lookup"><span data-stu-id="3691f-239">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![圖 9：全球 Microsoft 雲端網路](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="3691f-p121">圖 9 顯示組成的全球 Microsoft 雲端網路涵蓋 continents 與全球和其相對的區域網路的邏輯圖。與 Microsoft cloud 網路中每一個大陸的部分全域企業 ExpressRoute Premium 連線從建立其區域 hub 辦公室本機 Microsoft 對等的位置。</span><span class="sxs-lookup"><span data-stu-id="3691f-p121">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="3691f-243">區域的 office、 適用 Office 365 流量：</span><span class="sxs-lookup"><span data-stu-id="3691f-243">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="3691f-244">透過 Microsoft 雲端網路內大陸一起出差大陸 Office 365 資料中心。</span><span class="sxs-lookup"><span data-stu-id="3691f-244">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="3691f-245">Office 365 資料中心中另一個大陸一起出差洲際 Microsoft cloud 網路。</span><span class="sxs-lookup"><span data-stu-id="3691f-245">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="3691f-246">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="3691f-246">For more information, see:</span></span>
  
- [<span data-ttu-id="3691f-247">Azure ExpressRoute for Office 365 訓練</span><span class="sxs-lookup"><span data-stu-id="3691f-247">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="3691f-248">Office 365 的網路規劃和效能調整</span><span class="sxs-lookup"><span data-stu-id="3691f-248">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="3691f-249">Office 365 績效管理</span><span class="sxs-lookup"><span data-stu-id="3691f-249">Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="3691f-250">ExpressRoute 選項</span><span class="sxs-lookup"><span data-stu-id="3691f-250">ExpressRoute options</span></span>

<span data-ttu-id="3691f-251">您也可以將下列選項併入 ExpressRoute 部署中：</span><span class="sxs-lookup"><span data-stu-id="3691f-251">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="3691f-252">**您邊緣的安全性：** 若要提供進階的安全性的流量傳送和接收透過 ExpressRoute 連線，例如流量檢查或入侵/惡意程式碼偵測置於您 DMZ 內或在您的內部網路的框線的流量路徑中的安全性設備。</span><span class="sxs-lookup"><span data-stu-id="3691f-252">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="3691f-p122">若要防止 Azure Vm 初始化直接與網際網路位置流量的 Vm 的網際網路流量 advertise 預設路由給 Microsoft。跨 ExpressRoute 連線及透過您的內部部署 proxy 伺服器路由傳送至網際網路的流量。Azure Vm Azure PaaS 服務或 Office 365 的流量路由傳送回跨 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="3691f-p122">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="3691f-p123">**WAN 最佳化程式：** 您可以部署在私人的對等連線的兩側 WAN 最佳化程式跨部署 azure 虛擬網路 (VNet)。Azure VNet、 內使用 Azure marketplace 和使用者定義路由的 WAN 最佳化網路 appliance 透過 appliance 的流量路由傳送。</span><span class="sxs-lookup"><span data-stu-id="3691f-p123">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="3691f-p124">**服務品質：** 使用您的流量 IPv4 標頭中的區別服務代碼點 (DSCP) 值標示語音、 互動式視訊/，或最大的努力傳遞。這是特別重要的 Microsoft 對等關係與 Skype 商務 Online 流量。</span><span class="sxs-lookup"><span data-stu-id="3691f-p124">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="3691f-260">請參閱如需詳細資訊下列額外資源：</span><span class="sxs-lookup"><span data-stu-id="3691f-260">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="3691f-261">ExpressRoute for Office 365</span><span class="sxs-lookup"><span data-stu-id="3691f-261">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="3691f-262">Azure ExpressRoute for Office 365 訓練</span><span class="sxs-lookup"><span data-stu-id="3691f-262">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="3691f-263">Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="3691f-263">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="3691f-264">下一步</span><span class="sxs-lookup"><span data-stu-id="3691f-264">Next step</span></span>

[<span data-ttu-id="3691f-265">設計 Microsoft SaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="3691f-265">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="3691f-266">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3691f-266">See also</span></span>

[<span data-ttu-id="3691f-267">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="3691f-267">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="3691f-268">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="3691f-268">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="3691f-269">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="3691f-269">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



