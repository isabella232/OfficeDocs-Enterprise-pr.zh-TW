---
title: Azure IaaS 的混合式雲端案例
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 摘要： 了解混合式架構與案例適用於 Microsoft 的基礎結構即服務 (IaaS)-以 Azure 中的雲端供應項目。
ms.openlocfilehash: 5d125780e8baf3dbbe71b0878f6bf57cbeb5740f
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037927"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="5b892-103">Azure IaaS 的混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="5b892-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="5b892-104">**摘要：** 了解混合式架構與案例適用於 Microsoft 的基礎結構即服務 (IaaS)-以 Azure 中的雲端供應項目。</span><span class="sxs-lookup"><span data-stu-id="5b892-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="5b892-105">擴充您的內部運算，到依主控 IT 工作負載中執行雲端的身分識別基礎結構跨單位 Azure 虛擬網路 (Vnet)。</span><span class="sxs-lookup"><span data-stu-id="5b892-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="5b892-106">Azure IaaS 混合案例結構</span><span class="sxs-lookup"><span data-stu-id="5b892-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="5b892-107">圖 1 顯示在 Azure 中的 Microsoft IaaS 型混合式案例的架構。</span><span class="sxs-lookup"><span data-stu-id="5b892-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="5b892-108">**圖 1: Microsoft IaaS 型混合式案例，在 Azure 中**</span><span class="sxs-lookup"><span data-stu-id="5b892-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Azure 中的 Microsoft IaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="5b892-110">每個圖層的架構：</span><span class="sxs-lookup"><span data-stu-id="5b892-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="5b892-111">應用程式和案例</span><span class="sxs-lookup"><span data-stu-id="5b892-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="5b892-112">IT 工作負載通常是多層式、 高度可用的應用程式是由 Azure 虛擬機器 (Vm) 所組成。</span><span class="sxs-lookup"><span data-stu-id="5b892-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="5b892-113">身分識別</span><span class="sxs-lookup"><span data-stu-id="5b892-113">Identity</span></span>
    
    <span data-ttu-id="5b892-114">將身分識別伺服器，例如 Windows Server AD 網域控制站，新增至 Azure Vnet 中執行本機驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="5b892-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="5b892-115">工作列最右邊的網路</span><span class="sxs-lookup"><span data-stu-id="5b892-115">Network</span></span>
    
    <span data-ttu-id="5b892-116">使用在網際網路上的站台對站 VPN 連線或是 ExpressRoute 連線到 Azure IaaS 的私用對等。</span><span class="sxs-lookup"><span data-stu-id="5b892-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="5b892-117">內部部署</span><span class="sxs-lookup"><span data-stu-id="5b892-117">On-premises</span></span>
    
    <span data-ttu-id="5b892-118">包含身分識別伺服器與在 Azure 中執行的身分識別伺服器同步。</span><span class="sxs-lookup"><span data-stu-id="5b892-118">Contains identity servers that are synchronized with the identity servers running in Azure.</span></span> <span data-ttu-id="5b892-119">也可以包含在 Azure 中執行的 Vm 可以存取，例如儲存和系統管理基礎結構的資源。</span><span class="sxs-lookup"><span data-stu-id="5b892-119">Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="5b892-120">Office 365 的目錄同步處理伺服器</span><span class="sxs-lookup"><span data-stu-id="5b892-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="5b892-121">圖 2 所示，從 Azure VNet，執行您的目錄同步處理伺服器會延伸至雲端運算及身分識別基礎結構的範例。</span><span class="sxs-lookup"><span data-stu-id="5b892-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="5b892-122">**Azure IaaS 中的 Office 365 的圖 2： 目錄同步處理伺服器**</span><span class="sxs-lookup"><span data-stu-id="5b892-122">**Figure 2: Directory synchronization server for Office 365 in Azure IaaS**</span></span>

![Azure IaaS 中 Office 365 的目錄同步處理伺服器](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="5b892-124">圖 2 內部部署網路主控 Windows Server AD 基礎結構，配合 proxy 伺服器及在其邊緣路由器。</span><span class="sxs-lookup"><span data-stu-id="5b892-124">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge.</span></span> <span data-ttu-id="5b892-125">路由器請連接至位於與站台對站台 VPN 或 ExpressRoute 連線，Azure VNet 的緣 Azure 閘道。</span><span class="sxs-lookup"><span data-stu-id="5b892-125">The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="5b892-126">VNet 內的目錄同步處理伺服器會執行 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="5b892-126">Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="5b892-127">Office 365 目錄同步處理伺服器與 Office 365 訂閱下 Azure AD 租用戶同步處理的 Windows Server AD 帳戶的清單。</span><span class="sxs-lookup"><span data-stu-id="5b892-127">A directory synchronization server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="5b892-128">目錄同步處理伺服器是 Windows 為主的伺服器，執行 Azure AD Connect。</span><span class="sxs-lookup"><span data-stu-id="5b892-128">A directory synchronization server is a Windows-based server that runs Azure AD Connect.</span></span> <span data-ttu-id="5b892-129">更快的佈建或要減少您組織中的內部部署伺服器的數目，部署在 Azure IaaS 中的虛擬網路 (VNet) 中您的目錄同步處理伺服器。</span><span class="sxs-lookup"><span data-stu-id="5b892-129">For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="5b892-130">目錄同步處理伺服器輪詢 Windows Server AD 的變更，並再將其同步處理與 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="5b892-130">The directory synchronization server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="5b892-131">如需詳細資訊，請參閱 <<c0>在 Microsoft Azure 中部署 Office 365 目錄同步。</span><span class="sxs-lookup"><span data-stu-id="5b892-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="5b892-132">營運 (LOB) 應用程式</span><span class="sxs-lookup"><span data-stu-id="5b892-132">Line of business (LOB) application</span></span>

<span data-ttu-id="5b892-133">圖 3 顯示在 Azure IaaS 中執行的伺服器型 LOB 應用程式的組態。</span><span class="sxs-lookup"><span data-stu-id="5b892-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="5b892-134">**圖 3： 在 Azure IaaS 中的 LOB 應用程式**</span><span class="sxs-lookup"><span data-stu-id="5b892-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Azure IaaS 中的伺服器型 LOB 應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="5b892-136">圖 3 中，在內部部署網路主控身分識別基礎結構和使用者。</span><span class="sxs-lookup"><span data-stu-id="5b892-136">In Figure 3, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="5b892-137">它會連線至 Azure IaaS 閘道與站台對站台 VPN 或 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="5b892-137">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="5b892-138">Azure IaaS 主控一個包含的 LOB 應用程式伺服器的虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="5b892-138">Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="5b892-139">您可以建立 Azure Vm，在 Azure 的資料中心 （也稱為位置） 位於 Azure VNet 的子網路上執行的 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5b892-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="5b892-140">因為您基本上將您的內部部署基礎結構延伸到 Azure，您必須將唯一的私人位址空間指派給您的 Vnet，並更新內部路由的資料表，以確保能夠連接至每個 VNet。</span><span class="sxs-lookup"><span data-stu-id="5b892-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="5b892-141">連線之後，就可以管理這些 Vm 使用的遠端桌面連線或您的系統管理軟體，就像您的內部部署伺服器。</span><span class="sxs-lookup"><span data-stu-id="5b892-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="5b892-142">藉由設定之可公開公開的連接埠，這些 Vm 可也是從網際網路存取行動裝置或遠端使用者。</span><span class="sxs-lookup"><span data-stu-id="5b892-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="5b892-143">概念證明的設定，請參閱 < <b0>Simulated 跨單位 azure 虛擬網路</b0>。</span><span class="sxs-lookup"><span data-stu-id="5b892-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="5b892-144">裝載於 Azure Vm 的 LOB 應用程式的屬性如下所示：</span><span class="sxs-lookup"><span data-stu-id="5b892-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="5b892-145">多個層級</span><span class="sxs-lookup"><span data-stu-id="5b892-145">Multiple tiers</span></span>
    
    <span data-ttu-id="5b892-146">一般的 LOB 應用程式使用的分層的方法。</span><span class="sxs-lookup"><span data-stu-id="5b892-146">Typical LOB applications use a tiered approach.</span></span> <span data-ttu-id="5b892-147">一組伺服器員工或客戶存取提供身分識別、 資料庫處理、 應用程式與邏輯處理和前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="5b892-147">Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="5b892-148">高可用性</span><span class="sxs-lookup"><span data-stu-id="5b892-148">High availability</span></span>
    
    <span data-ttu-id="5b892-149">一般的 LOB 應用程式提供高可用性使用每一層中的多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="5b892-149">Typical LOB applications provide high availability by using multiple servers in each tier.</span></span> <span data-ttu-id="5b892-150">Azure IaaS 提供高達 99.9%執行時間 SLA 的 Azure 可用性設定組中的伺服器。</span><span class="sxs-lookup"><span data-stu-id="5b892-150">Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="5b892-151">負載分散</span><span class="sxs-lookup"><span data-stu-id="5b892-151">Load distribution</span></span>
    
    <span data-ttu-id="5b892-152">若要將負載分散給層中的多個伺服器之間的網路流量，您可以使用的網際網路對向或內部 Azure 負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="5b892-152">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer.</span></span> <span data-ttu-id="5b892-153">或者，您可以使用可用的專用的負載平衡器 appliance 從 Azure marketplace。</span><span class="sxs-lookup"><span data-stu-id="5b892-153">Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="5b892-154">安全性</span><span class="sxs-lookup"><span data-stu-id="5b892-154">Security</span></span>
    
    <span data-ttu-id="5b892-155">若要保護伺服器免於來路不明從網際網路傳入的流量，您可以使用 Azure 網路安全性群組。</span><span class="sxs-lookup"><span data-stu-id="5b892-155">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups.</span></span> <span data-ttu-id="5b892-156">您可以定義允許或拒絕子網路或個別的虛擬機器的網路介面的流量。</span><span class="sxs-lookup"><span data-stu-id="5b892-156">You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="5b892-157">Azure 中的 SharePoint Server 2016 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="5b892-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="5b892-158">多層的範例，請在 Azure 中的高可用性 LOB 應用程式是 SharePoint Server 2016 伺服器陣列圖 4 所示。</span><span class="sxs-lookup"><span data-stu-id="5b892-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="5b892-159">**圖 4: 高可用性 SharePoint Server 2016 伺服器陣列 Azure IaaS 中**</span><span class="sxs-lookup"><span data-stu-id="5b892-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中的高可用性 SharePoint Server 2016 伺服器陣列](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="5b892-161">圖 4 」 中的內部網路可主控身分識別基礎結構與使用者。</span><span class="sxs-lookup"><span data-stu-id="5b892-161">In Figure 4, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="5b892-162">它會連線至 Azure IaaS 閘道與站台對站台 VPN 或 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="5b892-162">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="5b892-163">Azure VNet 包含 SharePoint Server 2016 伺服器陣列，包括前端伺服器、 應用程式伺服器、 SQL Server 叢集，並在網域控制站的不同層的伺服器。</span><span class="sxs-lookup"><span data-stu-id="5b892-163">The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="5b892-164">此設定在 Azure 中具有 LOB 應用程式的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5b892-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="5b892-165">層級</span><span class="sxs-lookup"><span data-stu-id="5b892-165">Tiers</span></span>
    
    <span data-ttu-id="5b892-166">在伺服器陣列內執行不同的角色的伺服器建立層級和每一層有自己的子網路。</span><span class="sxs-lookup"><span data-stu-id="5b892-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="5b892-167">高可用性</span><span class="sxs-lookup"><span data-stu-id="5b892-167">High-availability</span></span>
    
    <span data-ttu-id="5b892-168">在每一層中使用多部伺服器，並將層的所有伺服器都放在相同的可用性設定組來達成。</span><span class="sxs-lookup"><span data-stu-id="5b892-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="5b892-169">負載分散</span><span class="sxs-lookup"><span data-stu-id="5b892-169">Load distribution</span></span>
    
    <span data-ttu-id="5b892-170">內部 Azure 負載平衡器分散傳入的用戶端 web 流量的前端伺服器 （WEB1 與 WEB2），並 （SQL1、 SQL2 和 MN1） 的 SQL Server 叢集接聽程式 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5b892-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="5b892-171">安全性</span><span class="sxs-lookup"><span data-stu-id="5b892-171">Security</span></span>
    
    <span data-ttu-id="5b892-172">網路安全性群組的每個子網路可讓您設定允許的輸入和輸出流量。</span><span class="sxs-lookup"><span data-stu-id="5b892-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="5b892-173">請依照下列成功採用此路徑：</span><span class="sxs-lookup"><span data-stu-id="5b892-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="5b892-174">評估並試驗</span><span class="sxs-lookup"><span data-stu-id="5b892-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="5b892-175">請參閱[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)以了解在 Azure 中執行 SharePoint Server 2016 的優點。</span><span class="sxs-lookup"><span data-stu-id="5b892-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="5b892-176">請參閱[Azure 開發/測試環境中的內部網路 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)以建立模擬的開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="5b892-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="5b892-177">設計</span><span class="sxs-lookup"><span data-stu-id="5b892-177">Design</span></span>
    
    <span data-ttu-id="5b892-178">請參閱 <<c0>設計 SharePoint Server 2016 伺服器陣列在 Azure 中的逐步執行程序來判斷 Azure IaaS 的網路、 計算，並儲存項目，以裝載您的伺服器陣列，其設定的集合。</span><span class="sxs-lookup"><span data-stu-id="5b892-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="5b892-179">部署</span><span class="sxs-lookup"><span data-stu-id="5b892-179">Deploy</span></span>
    
    <span data-ttu-id="5b892-180">請參閱[Deploying SharePoint Server 2016 with SQL Server AlwaysOn 可用性群組在 Azure 中](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)逐步執行五個階段中的高可用性伺服器陣列的端對端組態。</span><span class="sxs-lookup"><span data-stu-id="5b892-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="5b892-181">Azure 中 Office 365 的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="5b892-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="5b892-182">在 Azure 中的多層式、 高可用性 LOB 應用程式的另一個例子是 Office 365 的同盟身分識別。</span><span class="sxs-lookup"><span data-stu-id="5b892-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="5b892-183">**圖 5: 高可用性同盟身分識別基礎結構的 Azure IaaS 中 Office 365**</span><span class="sxs-lookup"><span data-stu-id="5b892-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Office 365 的高可用性同盟驗證基礎結構，在 Azure 中](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="5b892-185">圖 5-內部部署網路主控身分識別基礎結構和使用者。</span><span class="sxs-lookup"><span data-stu-id="5b892-185">In Figure 5, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="5b892-186">它會連線至 Azure IaaS 閘道與站台對站台 VPN 或 ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="5b892-186">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="5b892-187">Azure VNet 包含 web proxy 伺服器、 Active Directory Federation Services (AD FS) 伺服器及 Active Directory 網域服務 (AD DS) 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="5b892-187">The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Active Directory Domain Services (AD DS) domain controllers.</span></span>
  
<span data-ttu-id="5b892-188">此設定在 Azure 中具有 LOB 應用程式的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5b892-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="5b892-189">**層：** 有 web proxy 伺服器、 AD FS 伺服器和 Windows Server AD 網域控制站的層級。</span><span class="sxs-lookup"><span data-stu-id="5b892-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="5b892-190">**載入通訊：** 外部 Azure 負載平衡器分散的傳入用戶端驗證要求的 web proxy，並內部 Azure 負載平衡器散發 AD FS 伺服器的驗證要求。</span><span class="sxs-lookup"><span data-stu-id="5b892-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="5b892-191">請依照下列成功採用此路徑：</span><span class="sxs-lookup"><span data-stu-id="5b892-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="5b892-192">評估並試驗</span><span class="sxs-lookup"><span data-stu-id="5b892-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="5b892-193">請參閱[Office 365 開發/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)來建立模擬的開發/測試環境與 Office 365 同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="5b892-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="5b892-194">部署</span><span class="sxs-lookup"><span data-stu-id="5b892-194">Deploy</span></span>
    
    <span data-ttu-id="5b892-195">請參閱 < <b0>Azure 中 Office 365 的部署高可用性同盟的驗證</b0>逐步執行五個階段中之高可用性 AD FS 基礎結構的端對端組態。</span><span class="sxs-lookup"><span data-stu-id="5b892-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="5b892-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b892-196">See Also</span></span>

[<span data-ttu-id="5b892-197">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="5b892-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="5b892-198">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="5b892-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


