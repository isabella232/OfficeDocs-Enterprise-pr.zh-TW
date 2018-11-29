---
title: 將您的網路提升為雲端連線網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 摘要： 了解如何雲端採用需要網路基礎結構投資的新方法。
ms.openlocfilehash: c8fba120292b89894850312a84fd6067d925a07f
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872254"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="20ec8-103">將您的網路提升為雲端連線網路</span><span class="sxs-lookup"><span data-stu-id="20ec8-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="20ec8-104">**摘要：** 了解如何雲端採用需要網路基礎結構投資的新方法。</span><span class="sxs-lookup"><span data-stu-id="20ec8-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="20ec8-p101">雲端移轉改變了公司網路內外部的流量大小與本質。它也會影響降低安全性風險的方法。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="20ec8-107">雲端之前</span><span class="sxs-lookup"><span data-stu-id="20ec8-107">Before the cloud</span></span>
    
    <span data-ttu-id="20ec8-p102">大部分的網路基礎結構投資已所花費的確保可用、 可靠和效能低落連線到內部部署資料中心。許多組織的網際網路連線能力未內部商務作業的關鍵。網路界限已主要防禦安全性缺口。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p102">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters. For many organizations, Internet connectivity was not critical for internal business operations. Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="20ec8-111">在雲端之後</span><span class="sxs-lookup"><span data-stu-id="20ec8-111">After the cloud</span></span>
    
    <span data-ttu-id="20ec8-p103">新增及已移轉的產能與雲端中執行的 IT 工作量，基礎結構投資移動從內部部署至網際網路連線能力，現在有重大的內部企業營運資料中心。同盟的連線騰出安全性策略來保護身分識別和資料通過其網路與 Microsoft 雲端服務連線點。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p103">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations. Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="20ec8-p104">網路基礎結構投資的開頭連線。其他投資取決於雲端服務的類別。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p104">Network infrastructure investments begin with connectivity. Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="20ec8-p105">**軟體即服務 (SaaS)** Microsoft saas 和服務包括 Office 365、 Microsoft Intune 和 Microsoft Dynamics 365。Saas 和服務使用者所擁有的成功採用取決於高可用性和效能低落連線至網際網路，或直接 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p105">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="20ec8-p106">網路架構著重於可靠而變得多餘連線和容許足夠的頻寬。進行中的投資包括效能監視與調整。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p106">Network architecture focuses on reliable, redundant connectivity and ample bandwidth. Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="20ec8-p107">**Azure 平台服務 (PaaS)** 除了 Microsoft saas 和服務的投資、 多個網站或地理位置分散 PaaS 應用程式可能會需要架構 Azure 流量管理員來散佈的用戶端流量。進行中的投資包括效能和流量通訊監控與容錯移轉測試。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p107">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic. Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="20ec8-p108">**Azure 基礎架構以服務 (IaaS)** Microsoft SaaS 和 PaaS 服務成本，除了 IaaS 中執行 IT 工作量需要設計及設定的 Azure 虛擬網路該主機虛擬機器、 它們、 路由、 IP 上執行應用程式的安全連線處理、 DNS、 和負載平衡。進行中的投資包括效能及安全性監視與疑難排解。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p108">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing. Ongoing investments include performance and security monitoring and troubleshooting.</span></span>

<span data-ttu-id="20ec8-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365)是 Office 365、 企業管理 + 安全性 (EMS) 和 Windows 10 的組合。Microsoft 365 結合多個 SaaS 及完成的智慧型解決方案可讓所有人設為小小寫 Azure 服務及安全共同作業。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365) is a combination of Office 365, Enterprise Management + Security (EMS), and Windows 10. Microsoft 365 combines multiple SaaS and Azure services for a complete, intelligent solution that empowers everyone to be creative and work together securely.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="20ec8-126">區域的網路投資在雲端中成功</span><span class="sxs-lookup"><span data-stu-id="20ec8-126">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="20ec8-p110">企業組織而受益最佳化網路輸送量跨內部網路及網際網路進行條理方法。您可能也會受益從 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p110">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet. You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="20ec8-129">最佳化您的邊緣網路的內部網路連線</span><span class="sxs-lookup"><span data-stu-id="20ec8-129">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="20ec8-p111">多年來，許多組織已最佳化內部網路的連線能力與內部部署資料中心中執行的應用程式的效能。產能、 方法及執行 Microsoft 雲端中的 IT 工作量其他投資必須確保連線高可用性和邊緣網路與您的內部網路的使用者之間的流量效能是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p111">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters. With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="20ec8-132">最佳化在邊緣網路輸送量</span><span class="sxs-lookup"><span data-stu-id="20ec8-132">Optimize throughput at your edge network</span></span>

<span data-ttu-id="20ec8-133">為多個至雲端您日常產能流量移動，您應該密切在邊緣網路以確保它們是目前、 提供高可用性，並有足夠的容量以符合尖峰負載檢查的系統。</span><span class="sxs-lookup"><span data-stu-id="20ec8-133">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="20ec8-134">使用 Azure、 Office 365 及 Dynamics 365 高 SLA、 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="20ec8-134">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="20ec8-p112">雖然您可以使用目前的網際網路連線的邊緣網路，到與 Microsoft 雲端服務的流量必須共用管道與其他移至網際網路的內部網路流量。此外，您以 Microsoft 雲端服務的流量受限於網際網路流量壅塞。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p112">Although you can use your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet. Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="20ec8-137">高 SLA 與最佳效能，請使用 ExpressRoute、 網路和 Azure、 Office 365、 Dynamics 365 或所有三個之間的專用 WAN 連線。</span><span class="sxs-lookup"><span data-stu-id="20ec8-137">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="20ec8-p113">ExpressRoute 可以運用您現有的網路提供者的專屬的連線。透過 ExpressRoute 連接的資源便會出現好像他們是在您的 WAN，甚至是針對地理位置分散的組織。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p113">ExpressRoute can leverage your existing network provider for a dedicated connection. Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="20ec8-140">如需詳細資訊，請參閱[Microsoft 雲端連線 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="20ec8-140">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="20ec8-141">網路投資的範圍</span><span class="sxs-lookup"><span data-stu-id="20ec8-141">Scope of network investments</span></span>

<span data-ttu-id="20ec8-p114">網路投資的範圍取決於雲端服務的類別。跨 Microsoft cloud 演變最大化網路團隊的投資。例如投資 IaaS services 套用至所有的投資區域。</span><span class="sxs-lookup"><span data-stu-id="20ec8-p114">The scope of network investments depend on the category of cloud service. Investing across Microsoft's cloud maximizes the investments of networking teams. For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="20ec8-145">投資區域</span><span class="sxs-lookup"><span data-stu-id="20ec8-145">Investment area</span></span>  <br/> |<span data-ttu-id="20ec8-146">Saas 和</span><span class="sxs-lookup"><span data-stu-id="20ec8-146">SaaS</span></span>  <br/> |<span data-ttu-id="20ec8-147">PaaS</span><span class="sxs-lookup"><span data-stu-id="20ec8-147">PaaS</span></span>  <br/> |<span data-ttu-id="20ec8-148">IaaS</span><span class="sxs-lookup"><span data-stu-id="20ec8-148">IaaS</span></span>  <br/> |
|<span data-ttu-id="20ec8-149">以容許足夠的頻寬架構師可靠而變得多餘網際網路連線</span><span class="sxs-lookup"><span data-stu-id="20ec8-149">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="20ec8-150">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-150">Applies</span></span>  <br/> |<span data-ttu-id="20ec8-151">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-151">Applies</span></span>  <br/> |<span data-ttu-id="20ec8-152">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-152">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-153">監視與調整效能的網際網路輸送量</span><span class="sxs-lookup"><span data-stu-id="20ec8-153">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="20ec8-154">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-154">Applies</span></span>  <br/> |<span data-ttu-id="20ec8-155">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-155">Applies</span></span>  <br/> |<span data-ttu-id="20ec8-156">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-156">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-157">網際網路連線能力與輸送量問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="20ec8-157">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="20ec8-158">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-158">Applies</span></span>  <br/> |<span data-ttu-id="20ec8-159">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-159">Applies</span></span>  <br/> |<span data-ttu-id="20ec8-160">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-160">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-161">設計以負載平衡流量到不同的端點 Azure 流量管理員</span><span class="sxs-lookup"><span data-stu-id="20ec8-161">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="20ec8-162">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-162">Applies</span></span>  <br/> |<span data-ttu-id="20ec8-163">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-163">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-164">架構師可靠、 備援，與效能低落連線到 Azure 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="20ec8-164">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="20ec8-165">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-165">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-166">設計與 Azure 虛擬機器的安全連線</span><span class="sxs-lookup"><span data-stu-id="20ec8-166">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="20ec8-167">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-167">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-168">設計和實作內部部署位置和虛擬網路間的路由</span><span class="sxs-lookup"><span data-stu-id="20ec8-168">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="20ec8-169">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-169">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-170">包括工程師及實作的內部和網際網路對向 IT 工作量負載平衡</span><span class="sxs-lookup"><span data-stu-id="20ec8-170">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="20ec8-171">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-171">Applies</span></span>  <br/> |
|<span data-ttu-id="20ec8-172">虛擬機器連線及輸送量問題的疑難排解</span><span class="sxs-lookup"><span data-stu-id="20ec8-172">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="20ec8-173">適用於</span><span class="sxs-lookup"><span data-stu-id="20ec8-173">Applies</span></span>  <br/> |
   
## <a name="next-step"></a><span data-ttu-id="20ec8-174">下一步</span><span class="sxs-lookup"><span data-stu-id="20ec8-174">Next step</span></span>

[<span data-ttu-id="20ec8-175">Microsoft 雲端連線的常見的元素</span><span class="sxs-lookup"><span data-stu-id="20ec8-175">Common elements of Microsoft cloud connectivity</span></span>](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="20ec8-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20ec8-176">See also</span></span>

[<span data-ttu-id="20ec8-177">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="20ec8-177">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="20ec8-178">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="20ec8-178">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



