---
title: 進化網路以善用雲端連線能力
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: 摘要： 了解如何雲端採用需要網路基礎結構的投資的新方法。
ms.openlocfilehash: 47d24a4f545cfae8a6bd1c507a61f48b6d26cc7d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067629"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="a0201-103">進化網路以善用雲端連線能力</span><span class="sxs-lookup"><span data-stu-id="a0201-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="a0201-104">**摘要：** 了解如何雲端採用需要網路基礎結構的投資的新方法。</span><span class="sxs-lookup"><span data-stu-id="a0201-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="a0201-p101">雲端移轉改變了公司網路內外部的流量大小與本質。它也會影響降低安全性風險的方法。</span><span class="sxs-lookup"><span data-stu-id="a0201-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="a0201-107">在雲端之前</span><span class="sxs-lookup"><span data-stu-id="a0201-107">Before the cloud</span></span>
    
    <span data-ttu-id="a0201-108">大部分的網路基礎結構投資已所花費的確保可供使用、 可靠性和效能低落連線到內部部署資料中心。</span><span class="sxs-lookup"><span data-stu-id="a0201-108">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters.</span></span> <span data-ttu-id="a0201-109">對許多組織而言，網際網路連線能力來說並不重要的內部業務作業。</span><span class="sxs-lookup"><span data-stu-id="a0201-109">For many organizations, Internet connectivity was not critical for internal business operations.</span></span> <span data-ttu-id="a0201-110">網路界限的主要防禦安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="a0201-110">Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="a0201-111">在雲端之後</span><span class="sxs-lookup"><span data-stu-id="a0201-111">After the cloud</span></span>
    
    <span data-ttu-id="a0201-112">新的和已移轉的產能與執行在雲端的 IT 工作負載，基礎結構的投資移動從內部部署資料中心，以網際網路連線能力，也就是現在重要的內部企業營運。</span><span class="sxs-lookup"><span data-stu-id="a0201-112">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations.</span></span> <span data-ttu-id="a0201-113">同盟的連線會進入安全性策略，保護身分識別和資料通過的網路與 Microsoft 雲端服務的連線點。</span><span class="sxs-lookup"><span data-stu-id="a0201-113">Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="a0201-114">網路基礎結構的投資的開頭的連線。</span><span class="sxs-lookup"><span data-stu-id="a0201-114">Network infrastructure investments begin with connectivity.</span></span> <span data-ttu-id="a0201-115">其他投資取決於雲端服務的類別。</span><span class="sxs-lookup"><span data-stu-id="a0201-115">Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="a0201-116">**軟體即服務 (SaaS)** Microsoft SaaS 服務包含 Office 365、 Microsoft Intune 和 Microsoft Dynamics 365。</span><span class="sxs-lookup"><span data-stu-id="a0201-116">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365.</span></span> <span data-ttu-id="a0201-117">成功的 SaaS 服務使用者採用取決於高可用性和效能低落連線至網際網路，或直接在 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="a0201-117">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="a0201-118">網路架構著重於可靠的備援連線與足夠的頻寬。</span><span class="sxs-lookup"><span data-stu-id="a0201-118">Network architecture focuses on reliable, redundant connectivity and ample bandwidth.</span></span> <span data-ttu-id="a0201-119">進行中的投資包含效能監視與調整。</span><span class="sxs-lookup"><span data-stu-id="a0201-119">Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="a0201-120">**Azure 的平台即服務 (PaaS)** 除了針對 Microsoft SaaS 服務投資，多站台或地理位置分散 PaaS 應用程式可能需要架構 Azure 流量管理員可將用戶端流量分散。</span><span class="sxs-lookup"><span data-stu-id="a0201-120">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic.</span></span> <span data-ttu-id="a0201-121">進行中的投資包括效能和流量通訊監視和容錯移轉測試。</span><span class="sxs-lookup"><span data-stu-id="a0201-121">Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="a0201-122">**Azure 基礎結構即服務 (IaaS)** Microsoft SaaS 和 PaaS 服務投資，除了在 IaaS 中執行的 IT 工作負載需要設計及設定 Azure 虛擬網路的裝載虛擬機器，它們，路由，IP 上執行的應用程式的安全連線解決，DNS 及負載平衡。</span><span class="sxs-lookup"><span data-stu-id="a0201-122">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing.</span></span> <span data-ttu-id="a0201-123">進行中的投資包括效能與安全性監視及疑難排解。</span><span class="sxs-lookup"><span data-stu-id="a0201-123">Ongoing investments include performance and security monitoring and troubleshooting.</span></span>

<span data-ttu-id="a0201-124">[Microsoft 365](https://www.microsoft.com/microsoft-365)是 Office 365、 企業管理 + 安全性 (EMS) 和 Windows 10 的組合。</span><span class="sxs-lookup"><span data-stu-id="a0201-124">[Microsoft 365](https://www.microsoft.com/microsoft-365) is a combination of Office 365, Enterprise Management + Security (EMS), and Windows 10.</span></span> <span data-ttu-id="a0201-125">Microsoft 365 結合多個 SaaS 和 Azure 服務的完整的智慧型解決方案，讓所有人發揮創意並安全地合作。</span><span class="sxs-lookup"><span data-stu-id="a0201-125">Microsoft 365 combines multiple SaaS and Azure services for a complete, intelligent solution that empowers everyone to be creative and work together securely.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="a0201-126">區域的網路成功定域機組中的投資</span><span class="sxs-lookup"><span data-stu-id="a0201-126">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="a0201-127">企業組織受益於採取有條理的方法，以最佳化網路輸送量，在您內部網路和網際網路。</span><span class="sxs-lookup"><span data-stu-id="a0201-127">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet.</span></span> <span data-ttu-id="a0201-128">您也可以受益於 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="a0201-128">You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="a0201-129">最佳化您的邊緣網路的內部網路連線</span><span class="sxs-lookup"><span data-stu-id="a0201-129">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="a0201-130">多年來，許多組織有最佳化內部網路連線能力與內部部署資料中心中執行的應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="a0201-130">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters.</span></span> <span data-ttu-id="a0201-131">產能與執行 Microsoft cloud 中的 IT 工作負載，其他投資必須確定連線高可用性和邊緣網路與您的內部網路使用者之間的流量效能是最佳的作法。</span><span class="sxs-lookup"><span data-stu-id="a0201-131">With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="a0201-132">在邊緣網路輸送量最佳化</span><span class="sxs-lookup"><span data-stu-id="a0201-132">Optimize throughput at your edge network</span></span>

<span data-ttu-id="a0201-133">為多個至雲端您日常生產力流量移動，密切應該在您的邊緣網路，以確保其目前，提供高可用性，且沒有足夠的容量，以滿足尖峰負載檢查系統的集合。</span><span class="sxs-lookup"><span data-stu-id="a0201-133">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="a0201-134">若要在 Azure、 Office 365 和 Dynamics 365 高 SLA，使用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="a0201-134">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="a0201-135">雖然您可以使用您目前的網際網路連線從您的邊緣網路，到及傳送自 Microsoft 雲端服務的流量必須與其他內部網路流量，移至 [網際網路共用管道。</span><span class="sxs-lookup"><span data-stu-id="a0201-135">Although you can use your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet.</span></span> <span data-ttu-id="a0201-136">此外，您對 Microsoft 雲端服務的流量受限於網際網路流量壅塞。</span><span class="sxs-lookup"><span data-stu-id="a0201-136">Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="a0201-137">針對高 SLA 及最佳效能，使用 ExpressRoute，您的網路和 Azure、 Office 365、 Dynamics 365 或所有三個間的專用 WAN 連線。</span><span class="sxs-lookup"><span data-stu-id="a0201-137">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="a0201-138">ExpressRoute 可以利用現有的專用連線的網路提供者。</span><span class="sxs-lookup"><span data-stu-id="a0201-138">ExpressRoute can leverage your existing network provider for a dedicated connection.</span></span> <span data-ttu-id="a0201-139">透過 ExpressRoute 連線的資源會顯示好像他們位於您 WAN，即使的地理位置分散的組織。</span><span class="sxs-lookup"><span data-stu-id="a0201-139">Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="a0201-140">如需詳細資訊，請參閱 <<c0>適用於 Microsoft 雲端連線能力。</span><span class="sxs-lookup"><span data-stu-id="a0201-140">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="a0201-141">網路投資的範圍</span><span class="sxs-lookup"><span data-stu-id="a0201-141">Scope of network investments</span></span>

<span data-ttu-id="a0201-142">網路投資的範圍取決於雲端服務的類別。</span><span class="sxs-lookup"><span data-stu-id="a0201-142">The scope of network investments depend on the category of cloud service.</span></span> <span data-ttu-id="a0201-143">跨 Microsoft 雲端投資會最大化網路團隊的投資。</span><span class="sxs-lookup"><span data-stu-id="a0201-143">Investing across Microsoft's cloud maximizes the investments of networking teams.</span></span> <span data-ttu-id="a0201-144">例如，IaaS services 投資套用到所有投資區域。</span><span class="sxs-lookup"><span data-stu-id="a0201-144">For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a0201-145">投資區域</span><span class="sxs-lookup"><span data-stu-id="a0201-145">Investment area</span></span>  <br/> |<span data-ttu-id="a0201-146">SaaS</span><span class="sxs-lookup"><span data-stu-id="a0201-146">SaaS</span></span>  <br/> |<span data-ttu-id="a0201-147">PaaS</span><span class="sxs-lookup"><span data-stu-id="a0201-147">PaaS</span></span>  <br/> |<span data-ttu-id="a0201-148">IaaS</span><span class="sxs-lookup"><span data-stu-id="a0201-148">IaaS</span></span>  <br/> |
|<span data-ttu-id="a0201-149">架構師可靠的備援網際網路連線能力，具有足夠的頻寬</span><span class="sxs-lookup"><span data-stu-id="a0201-149">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="a0201-150">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-150">Applies</span></span>  <br/> |<span data-ttu-id="a0201-151">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-151">Applies</span></span>  <br/> |<span data-ttu-id="a0201-152">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-152">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-153">效能的監視與調整網際網路輸送量</span><span class="sxs-lookup"><span data-stu-id="a0201-153">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="a0201-154">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-154">Applies</span></span>  <br/> |<span data-ttu-id="a0201-155">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-155">Applies</span></span>  <br/> |<span data-ttu-id="a0201-156">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-156">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-157">網際網路連線及輸送量問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a0201-157">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="a0201-158">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-158">Applies</span></span>  <br/> |<span data-ttu-id="a0201-159">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-159">Applies</span></span>  <br/> |<span data-ttu-id="a0201-160">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-160">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-161">設計 Azure 流量管理員將流量負載平衡到不同的端點</span><span class="sxs-lookup"><span data-stu-id="a0201-161">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="a0201-162">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-162">Applies</span></span>  <br/> |<span data-ttu-id="a0201-163">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-163">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-164">Azure 虛擬網路的架構設計人員可靠的備援和效能低落連線</span><span class="sxs-lookup"><span data-stu-id="a0201-164">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="a0201-165">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-165">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-166">設計 Azure 虛擬機器的安全連線</span><span class="sxs-lookup"><span data-stu-id="a0201-166">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="a0201-167">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-167">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-168">設計和實作內部部署位置和虛擬網路之間的路由</span><span class="sxs-lookup"><span data-stu-id="a0201-168">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="a0201-169">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-169">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-170">設計和實作內部和網際網路對向的 IT 工作負載的負載平衡</span><span class="sxs-lookup"><span data-stu-id="a0201-170">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="a0201-171">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-171">Applies</span></span>  <br/> |
|<span data-ttu-id="a0201-172">針對虛擬機器連線及輸送量問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a0201-172">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="a0201-173">適用於</span><span class="sxs-lookup"><span data-stu-id="a0201-173">Applies</span></span>  <br/> |
   
## <a name="next-step"></a><span data-ttu-id="a0201-174">下一步</span><span class="sxs-lookup"><span data-stu-id="a0201-174">Next step</span></span>

[<span data-ttu-id="a0201-175">Microsoft 雲端連線的常見的元素</span><span class="sxs-lookup"><span data-stu-id="a0201-175">Common elements of Microsoft cloud connectivity</span></span>](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="a0201-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0201-176">See also</span></span>

[<span data-ttu-id="a0201-177">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="a0201-177">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="a0201-178">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="a0201-178">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



