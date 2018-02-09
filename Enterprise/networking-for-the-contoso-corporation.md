---
title: "Contoso Corporation 的網路"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "摘要： 了解的定義和 Microsoft 混合雲端的元素。"
ms.openlocfilehash: 1f023364c4b2e9c64af954ec9ba63a6197ebc01a
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="9919e-103">Contoso Corporation 的網路</span><span class="sxs-lookup"><span data-stu-id="9919e-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="9919e-104">**摘要：**了解的定義和 Microsoft 混合雲端的元素。</span><span class="sxs-lookup"><span data-stu-id="9919e-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="9919e-p101">若要採用雲端 （含） 的基礎結構，Contoso 的網路工程師實現網路流量傳送到雲端架構服務針對這趟旅行方式基本 shift 鍵。而不是只最佳化的內部伺服器和資料中心流量，等於廣告必須付費來最佳化網際網路邊緣和網際網路之間的流量。</span><span class="sxs-lookup"><span data-stu-id="9919e-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="9919e-107">Contoso 的網路基礎結構</span><span class="sxs-lookup"><span data-stu-id="9919e-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="9919e-108">Contoso 具有圖 1 所示的網路基礎結構。</span><span class="sxs-lookup"><span data-stu-id="9919e-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="9919e-109">**圖 1： Contoso 的 WAN 基礎結構**</span><span class="sxs-lookup"><span data-stu-id="9919e-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![Contoso 的 WAN 基礎結構，連結了總部、區域中樞和分公司辦公室](images/Contoso_Poster/Contoso_WW_Net.png)
  
<span data-ttu-id="9919e-111">圖 1 顯示 Contoso 的辦公室跨全球的環境的地區設定與兩者之間衛星 office WAN 連結。</span><span class="sxs-lookup"><span data-stu-id="9919e-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="9919e-112">其他網路元素如下所示：</span><span class="sxs-lookup"><span data-stu-id="9919e-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="9919e-113">在內部網路</span><span class="sxs-lookup"><span data-stu-id="9919e-113">On-premises network</span></span>
    
    <span data-ttu-id="9919e-p102">WAN 連結連線 Paris headquarters 地區辦公室和區域來衛星辦公室支點和中樞組態中的辦公室。內每個 office、 路由器會傳遞至主機或子網路，使用私人 IP 位址空間的無線存取點的流量。</span><span class="sxs-lookup"><span data-stu-id="9919e-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="9919e-116">網際網路連線能力</span><span class="sxs-lookup"><span data-stu-id="9919e-116">Internet connectivity</span></span>
    
    <span data-ttu-id="9919e-p103">每個 office 有其專屬的網際網路連線能力透過 proxy 伺服器。這通常會實作為 WAN 連結到本機的 ISP 的 proxy 伺服器] 也提供公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="9919e-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="9919e-119">網際網路平台服務</span><span class="sxs-lookup"><span data-stu-id="9919e-119">Internet presence</span></span>
    
    <span data-ttu-id="9919e-p104">Contoso 擁有 contoso.com 公用網域名稱。Contoso 公用網站以進行排序產品是一組 Paris 校園的網際網路連線的資料中心中的伺服器。Contoso 使用 / 24 在網際網路上的公用 IP 位址範圍。</span><span class="sxs-lookup"><span data-stu-id="9919e-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="9919e-123">Contoso 的應用程式基礎結構</span><span class="sxs-lookup"><span data-stu-id="9919e-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="9919e-124">Contoso 具有架構台下列其應用程式及伺服器基礎結構：</span><span class="sxs-lookup"><span data-stu-id="9919e-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="9919e-125">**圖 2： Contoso 的基礎結構的內部應用程式**</span><span class="sxs-lookup"><span data-stu-id="9919e-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Contoso 的內部應用程式基礎結構](images/Contoso_Poster/App_Infra.png)
  
- <span data-ttu-id="9919e-127">衛星辦公室使用快取的本機伺服器以儲存常存取文件與內部網路網站。</span><span class="sxs-lookup"><span data-stu-id="9919e-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="9919e-p105">區域性集線器使用衛星台和區域的應用程式伺服器的區域。這些伺服器與伺服器中的 Paris headquarters 同步處理。</span><span class="sxs-lookup"><span data-stu-id="9919e-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="9919e-130">Paris 校園有包含整個組織提供服務的集中式應用程式伺服器的資料中心。</span><span class="sxs-lookup"><span data-stu-id="9919e-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="9919e-p106">衛星或地區的集線器辦公室的使用者，可以所衛星和地區 hub office server 服務 60%的員工所需的資源。額外 40%的資源要求必須傳送透過 WAN 連結至 Paris 校園。</span><span class="sxs-lookup"><span data-stu-id="9919e-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="9919e-133">Contoso 的網路分析</span><span class="sxs-lookup"><span data-stu-id="9919e-133">Contoso's network analysis</span></span>

<span data-ttu-id="9919e-134">以下是分析的需要網路上以容納 Microsoft cloud 方案的不同類別的變更 Contoso 的結果：</span><span class="sxs-lookup"><span data-stu-id="9919e-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="9919e-135">**Saas 和雲端方案： Office 365、 EMS 及 Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="9919e-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="9919e-136">**Azure PaaS： 行動應用程式**</span><span class="sxs-lookup"><span data-stu-id="9919e-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="9919e-137">**Azure IaaS： 伺服器為基礎的工作負載**</span><span class="sxs-lookup"><span data-stu-id="9919e-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9919e-138">Saas 和服務使用者所擁有的成功採用取決於高可用性和效能低落連線至網際網路，或直接 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="9919e-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="9919e-139">行動使用者及其目前的網際網路存取假設其值為足夠。</span><span class="sxs-lookup"><span data-stu-id="9919e-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="9919e-140">Contoso 公司內部網路上的使用者，每個 office 必須分析和最佳化到網際網路的輸送量和到 Microsoft 的歐洲資料中心主控 Office 365、 EMS 及 Dynamics 365 租用戶的來回時間。</span><span class="sxs-lookup"><span data-stu-id="9919e-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="9919e-p107">若要更佳的支援行動工作者、 舊版的應用程式以及某些檔案共用網站已成為已修訂及部署為 「 Azure PaaS 應用程式。以獲得最佳效能，Contoso 計劃部署在全世界來自多個 Azure 資料中心的新應用程式。Azure 流量管理員傳送給用戶端應用程式要求是否它們是來自行動裝置的使用者或 office 中的電腦到最接近的 Azure 資料中心主控應用程式。</span><span class="sxs-lookup"><span data-stu-id="9919e-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="9919e-144">IT 部門將需要將 PaaS 應用程式的效能和流量通訊群組加入至其網路狀況監視解決方案。</span><span class="sxs-lookup"><span data-stu-id="9919e-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="9919e-145">若要移動 Paris 校園資料中心一些舊版和封存伺服器並根據需要為季端處理新增伺服器，Contoso 計劃使用 Azure 基礎結構服務中執行的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="9919e-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="9919e-146">Azure 虛擬網路，到內含這些伺服器必須設計的不重疊地址空格、 路由、 和整合式 DNS。</span><span class="sxs-lookup"><span data-stu-id="9919e-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="9919e-147">IT 部門必須包含這些新的伺服器網路管理和監控系統。</span><span class="sxs-lookup"><span data-stu-id="9919e-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="9919e-148">ExpressRoute Contoso 的使用</span><span class="sxs-lookup"><span data-stu-id="9919e-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="9919e-p108">ExpressRoute 是從所在位置到您的網路連線至 Microsoft cloud 網路 Microsoft 對等位置專用 WAN 連線。ExpressRoute 連線提供可預測的效能與達 99.9%執行時間 SLA。.</span><span class="sxs-lookup"><span data-stu-id="9919e-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="9919e-p109">使用 ExpressRoute 連線，您會連線到 Microsoft cloud 網路和同一個大陸中的所有 Microsoft 資料中心位置。雲端對等位置與目的地 Microsoft 資料中心之間的流量遷 Microsoft cloud 網路</span><span class="sxs-lookup"><span data-stu-id="9919e-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="9919e-154">**圖 3： Microsoft cloud 網路組成的全球**</span><span class="sxs-lookup"><span data-stu-id="9919e-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![全球 Microsoft 雲端網路](images/Contoso_Poster/MS_WW_Cloud.png)
  
<span data-ttu-id="9919e-156">圖 3 是生活的各區域互連的 Microsoft cloud 網路。</span><span class="sxs-lookup"><span data-stu-id="9919e-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="9919e-p110">使用 ExpressRoute Premium 您可以達到任何大陸從任何大陸上任何 Microsoft 對等位置上的任何 Microsoft 資料中心。透過 Microsoft 雲端網路執行是 continents 之間的流量。</span><span class="sxs-lookup"><span data-stu-id="9919e-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="9919e-159">請依據目前和未來 Microsoft cloud 方案流量分析，Contoso 已執行網路評估及實作具有私人和公用對等的 Azure 資源存取任何-任何 （MPLS 型） ExpressRoute 連線從 Microsoft 對等位置歐洲 Paris headquarters 的關係。</span><span class="sxs-lookup"><span data-stu-id="9919e-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="9919e-160">此連線將提供 Contoso 的 IT 部門：</span><span class="sxs-lookup"><span data-stu-id="9919e-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="9919e-161">一致的效能分散式 Azure PaaS 應用程式的權限管理</span><span class="sxs-lookup"><span data-stu-id="9919e-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="9919e-p111">所有 Contoso 的應用程式開發人員和核心基礎結構 IT 管理員位於 Paris 校園。散佈至不同的 Azure 資料中心全球各地 Azure PaaS 應用程式] 與 Contoso 需要從來管理應用程式和其儲存資源，其中包含的文件 TB Paris 校園一致的效能。</span><span class="sxs-lookup"><span data-stu-id="9919e-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="9919e-164">Azure IaaS 中伺服器的權限管理一致的效能</span><span class="sxs-lookup"><span data-stu-id="9919e-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="9919e-p112">Contoso 的資料中心系統管理員在 Paris 校園且其伺服器設為部署在 Azure 中副檔名為 Paris 資料中心。Contoso 必須一致的效能與這些新的伺服器存取舊版的應用程式及封存儲存區和結束一季處理。</span><span class="sxs-lookup"><span data-stu-id="9919e-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="9919e-167">雲端網路整備的 Contoso 的路徑</span><span class="sxs-lookup"><span data-stu-id="9919e-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="9919e-168">Contoso 以備妥 Microsoft cloud 其網路使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9919e-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="9919e-169">最佳化員工電腦的網際網路存取</span><span class="sxs-lookup"><span data-stu-id="9919e-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="9919e-170">個別電腦則檢查以確認已安裝最新的 TCP/IP 堆疊、 瀏覽器、 NIC 驅動程式及安全性和作業系統的更新。</span><span class="sxs-lookup"><span data-stu-id="9919e-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="9919e-171">分析每個 office 中的網際網路連線使用率，並增加視</span><span class="sxs-lookup"><span data-stu-id="9919e-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="9919e-172">將目前的網際網路使用量分析每個 office 和 WAN 連結頻寬會增加如果操作 70%或以上使用率。</span><span class="sxs-lookup"><span data-stu-id="9919e-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="9919e-173">分析 DMZ 系統每個 office 以達最佳效能</span><span class="sxs-lookup"><span data-stu-id="9919e-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="9919e-p113">防火牆、 Ids、 及其他系統中的網際網路路徑會分析獲得最佳效能。Proxy 伺服器會更新或升級所需。</span><span class="sxs-lookup"><span data-stu-id="9919e-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="9919e-176">新增 Paris 校園 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9919e-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="9919e-177">提供一致資源的存取權 Azure Azure PaaS 和 IaaS 工作負載的權限管理。</span><span class="sxs-lookup"><span data-stu-id="9919e-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="9919e-178">建立及測試 Azure PaaS 應用程式為 Azure 流量管理員設定檔</span><span class="sxs-lookup"><span data-stu-id="9919e-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="9919e-179">測試散佈網際網路流量區域位置中獲取經驗會使用效能的路由方法為 Azure 流量管理員設定檔。</span><span class="sxs-lookup"><span data-stu-id="9919e-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="9919e-180">為 Azure VNets 保留私人位址空間</span><span class="sxs-lookup"><span data-stu-id="9919e-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="9919e-181">根據預計的簡短和長期伺服器在 Azure IaaS 的數字，保留私人位址空間 Azure VNets 和其子網路。</span><span class="sxs-lookup"><span data-stu-id="9919e-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="9919e-182">請參閱</span><span class="sxs-lookup"><span data-stu-id="9919e-182">See Also</span></span>

[<span data-ttu-id="9919e-183">Microsoft Cloud 中的 Contoso</span><span class="sxs-lookup"><span data-stu-id="9919e-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="9919e-184">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="9919e-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="9919e-185">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="9919e-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



