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
description: 摘要： 了解混合式架構與案例的 Microsoft 的基礎結構以服務 (IaaS)-以 Azure 中的雲端方案。
ms.openlocfilehash: bb6611f51cc346273438e879d957597fe3299c58
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123240"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="fb73e-103">Azure IaaS 的混合式雲端案例</span><span class="sxs-lookup"><span data-stu-id="fb73e-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="fb73e-104">**摘要：** 了解混合式架構與案例 Microsoft 的基礎結構以服務 (IaaS)-以 Azure 中的雲端方案。</span><span class="sxs-lookup"><span data-stu-id="fb73e-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="fb73e-105">擴充您的內部運算並將架設 IT 工作量中執行雲端身分識別基礎結構跨部署 Azure 虛擬網路 (VNets)。</span><span class="sxs-lookup"><span data-stu-id="fb73e-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="fb73e-106">Azure IaaS 混合式案例的架構</span><span class="sxs-lookup"><span data-stu-id="fb73e-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="fb73e-107">圖 1 顯示在 Azure 中的 Microsoft IaaS 為基礎的混合式案例的架構。</span><span class="sxs-lookup"><span data-stu-id="fb73e-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="fb73e-108">**Azure 中的圖 1： Microsoft IaaS 為基礎的混合式案例**</span><span class="sxs-lookup"><span data-stu-id="fb73e-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Azure 中的 Microsoft IaaS 型混合式案例](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="fb73e-110">之架構的每個圖層：</span><span class="sxs-lookup"><span data-stu-id="fb73e-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="fb73e-111">應用程式與案例</span><span class="sxs-lookup"><span data-stu-id="fb73e-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="fb73e-112">IT 工作負載通常是多層、 高度可用的應用程式所組成 Azure 虛擬機器 (Vm)。</span><span class="sxs-lookup"><span data-stu-id="fb73e-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="fb73e-113">身分識別</span><span class="sxs-lookup"><span data-stu-id="fb73e-113">Identity</span></span>
    
    <span data-ttu-id="fb73e-114">將身分識別伺服器，例如 Windows Server AD 網域控制站，新增至 Azure VNets 中執行本機驗證伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="fb73e-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="fb73e-115">工作列最右邊的網路</span><span class="sxs-lookup"><span data-stu-id="fb73e-115">Network</span></span>
    
    <span data-ttu-id="fb73e-116">使用網站 VPN 連線透過網際網路或 ExpressRoute 連線至 Azure IaaS 私人對等。</span><span class="sxs-lookup"><span data-stu-id="fb73e-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="fb73e-117">內部部署</span><span class="sxs-lookup"><span data-stu-id="fb73e-117">On-premises</span></span>
    
    <span data-ttu-id="fb73e-p101">包含已同步處理身分識別執行的伺服器在 Azure 中的身分識別伺服器。也可以包含在 Azure 中執行的 Vm 可以存取，例如儲存區與系統管理基礎結構的資源。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="fb73e-120">Office 365 DirSync 伺服器</span><span class="sxs-lookup"><span data-stu-id="fb73e-120">DirSync server for Office 365</span></span>

<span data-ttu-id="fb73e-121">圖 2 所示在 Azure VNet，從執行您的目錄同步處理 (DirSync) 伺服器是擴充到雲端您運算與身分識別基礎結構的範例。</span><span class="sxs-lookup"><span data-stu-id="fb73e-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="fb73e-122">**圖 2： Azure IaaS 中的 Office 365 DirSync 伺服器**</span><span class="sxs-lookup"><span data-stu-id="fb73e-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![Azure IaaS 中 Office 365 DirSync 伺服器](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="fb73e-p102">圖 2] 中的內部網路主控 Windows Server AD 基礎結構、 proxy 伺服器和其邊緣路由器。路由器請連接至緣的網站 VPN 或 ExpressRoute 連線 Azure VNet Azure 閘道。內部 VNet DirSync 伺服器執行 Azure AD 連線。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="fb73e-127">Office 365 DirSync server 與 Office 365 訂閱 Azure AD 租用同步在 Windows Server AD 帳戶的清單。</span><span class="sxs-lookup"><span data-stu-id="fb73e-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="fb73e-p103">DirSync Windows 型伺服器是執行 Azure AD 連線。更快的佈建或減少您組織中的內部部署伺服器的數目，部署您 DirSync server Azure IaaS 虛擬網路 (VNet) 中。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="fb73e-130">DirSync server 輪詢 Windows Server AD 的變更，然後將其同步與 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="fb73e-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="fb73e-131">如需詳細資訊，請參閱[Microsoft Azure 中部署 Office 365 目錄同步](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="fb73e-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="fb73e-132">列的業務 (LOB) 應用程式</span><span class="sxs-lookup"><span data-stu-id="fb73e-132">Line of business (LOB) application</span></span>

<span data-ttu-id="fb73e-133">圖 3 是在 Azure IaaS 中執行的伺服器端 LOB 應用程式的設定。</span><span class="sxs-lookup"><span data-stu-id="fb73e-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="fb73e-134">**圖 3： 在 Azure IaaS 的 LOB 應用程式**</span><span class="sxs-lookup"><span data-stu-id="fb73e-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Azure IaaS 中的伺服器型 LOB 應用程式](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="fb73e-p104">圖 3-內部網路主控身分識別基礎結構與使用者。所連接的網站 VPN 或 ExpressRoute 連線的 Azure IaaS 閘道。Azure IaaS 主控的 LOB 應用程式伺服器所在的虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="fb73e-139">您可以建立 Azure Vm，位於子網路的 Azure VNet 在 Azure 資料中心內 （又稱為位置） 上執行的 LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb73e-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="fb73e-140">因為您基本上以 Azure 擴充您的內部部署基礎結構，您必須將唯一的私人位址空間指派給您 VNets 及更新您的內部路由表以確保能夠連接至每個 VNet。</span><span class="sxs-lookup"><span data-stu-id="fb73e-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="fb73e-141">一旦連線，可以管理這些 Vm 與遠端桌面連線和您的系統管理軟體，就像是您的內部伺服器。</span><span class="sxs-lookup"><span data-stu-id="fb73e-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="fb73e-142">透過設定公開公開的連接埠，這些 Vm 也可從網際網路行動裝置或遠端使用者。</span><span class="sxs-lookup"><span data-stu-id="fb73e-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="fb73e-143">驗證概念來設定，請參閱[Simulated 跨部署在 Azure 虛擬網路](simulated-cross-premises-virtual-network-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="fb73e-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="fb73e-144">Azure Vm 上裝載的 LOB 應用程式的屬性如下所示：</span><span class="sxs-lookup"><span data-stu-id="fb73e-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="fb73e-145">多層</span><span class="sxs-lookup"><span data-stu-id="fb73e-145">Multiple tiers</span></span>
    
    <span data-ttu-id="fb73e-p105">典型的 LOB 應用程式使用分層的方法。設定伺服器的員工或客戶存取提供身分識別、 資料庫處理、 應用程式及邏輯處理與前端網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="fb73e-148">高可用性</span><span class="sxs-lookup"><span data-stu-id="fb73e-148">High availability</span></span>
    
    <span data-ttu-id="fb73e-p106">典型的 LOB 應用程式提供高可用性使用多部伺服器的每一層。Azure IaaS 提供 99.9%執行時間 SLA Azure 可用性設定中的伺服器。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="fb73e-151">負載分散</span><span class="sxs-lookup"><span data-stu-id="fb73e-151">Load distribution</span></span>
    
    <span data-ttu-id="fb73e-p107">若要散佈層內的多部伺服器之間的網路流量的負載，您可以使用網際網路或內部 Azure 負載平衡器。或者，您可以使用可用的專用的負載平衡器 appliance 從 Azure marketplace。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="fb73e-154">安全性</span><span class="sxs-lookup"><span data-stu-id="fb73e-154">Security</span></span>
    
    <span data-ttu-id="fb73e-p108">若要從網際網路的來路不明傳入流量保護伺服器，您可以使用 Azure 網路安全性群組。您可以定義允許或拒絕的子網路或個別的虛擬機器的網路介面的流量。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="fb73e-157">SharePoint Server 2016 Azure 中的伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="fb73e-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="fb73e-158">多層的範例，Azure 中高度可用的 LOB 應用程式是 SharePoint Server 2016 伺服器陣列，如圖 4 所示。</span><span class="sxs-lookup"><span data-stu-id="fb73e-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="fb73e-159">**圖 4： 在高可用性 SharePoint 伺服器 2016年伺服器陣列中 Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="fb73e-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中高可用性的 SharePoint Server 2016 伺服器陣列](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="fb73e-p109">圖 4] 中的內部網路主控身分識別基礎結構與使用者。所連接的網站 VPN 或 ExpressRoute 連線的 Azure IaaS 閘道。Azure VNet 包含 SharePoint Server 2016 伺服器陣列，其中包含前端伺服器、 應用程式伺服器、 SQL Server 叢集，並在網域控制站的不同層的伺服器。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="fb73e-164">此設定包含在 Azure 中 LOB 應用程式的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fb73e-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="fb73e-165">各層</span><span class="sxs-lookup"><span data-stu-id="fb73e-165">Tiers</span></span>
    
    <span data-ttu-id="fb73e-166">伺服器陣列內執行不同的角色的伺服器建立在各層和每一層有自己的子網路。</span><span class="sxs-lookup"><span data-stu-id="fb73e-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="fb73e-167">高可用性</span><span class="sxs-lookup"><span data-stu-id="fb73e-167">High-availability</span></span>
    
    <span data-ttu-id="fb73e-168">可達到每一層中使用多部伺服器，並在相同的可用性一組中放入層的所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="fb73e-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="fb73e-169">負載分散</span><span class="sxs-lookup"><span data-stu-id="fb73e-169">Load distribution</span></span>
    
    <span data-ttu-id="fb73e-170">內部 Azure 負載平衡器散佈傳入的用戶端 web 流量 （WEB1 和 WEB2） 與前端伺服器和 SQL Server 叢集 （SQL1、 SQL2、 和 MN1） 的接聽程式 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="fb73e-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="fb73e-171">安全性</span><span class="sxs-lookup"><span data-stu-id="fb73e-171">Security</span></span>
    
    <span data-ttu-id="fb73e-172">每個子網路的網路安全性群組可讓您設定允許輸入和輸出的流量。</span><span class="sxs-lookup"><span data-stu-id="fb73e-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="fb73e-173">請遵循成功採用此路徑：</span><span class="sxs-lookup"><span data-stu-id="fb73e-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="fb73e-174">評估及試驗</span><span class="sxs-lookup"><span data-stu-id="fb73e-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="fb73e-175">請參閱[Microsoft Azure 中的 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)了解 SharePoint Server 2016 執行 Azure 中的優點。</span><span class="sxs-lookup"><span data-stu-id="fb73e-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="fb73e-176">請參閱[在 Azure 的開發人員測試環境中的內部網路 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)建置模擬的開發人員測試環境</span><span class="sxs-lookup"><span data-stu-id="fb73e-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="fb73e-177">設計</span><span class="sxs-lookup"><span data-stu-id="fb73e-177">Design</span></span>
    
    <span data-ttu-id="fb73e-178">請參閱逐一檢視程序，以決定 Azure IaaS 網路、 compute、 及儲存項目來架設在伺服器陣列和其設定一組[設計 Azure 中的 SharePoint Server 2016 伺服器陣列](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure)。</span><span class="sxs-lookup"><span data-stu-id="fb73e-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="fb73e-179">部署</span><span class="sxs-lookup"><span data-stu-id="fb73e-179">Deploy</span></span>
    
    <span data-ttu-id="fb73e-180">請參閱[使用 SQL Server AlwaysOn 可用性群組 Azure 中部署 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)逐一檢視端對端陣列的設定高可用性的五個階段。</span><span class="sxs-lookup"><span data-stu-id="fb73e-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="fb73e-181">在 Azure 中的 Office 365 同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="fb73e-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="fb73e-182">在 Azure 中的多層、 高度可用 LOB 應用程式的另一個例子是 Office 365 同盟身分識別。</span><span class="sxs-lookup"><span data-stu-id="fb73e-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="fb73e-183">**圖 5： 在高可用性同盟身分識別基礎結構的 Azure IaaS 中的 Office 365**</span><span class="sxs-lookup"><span data-stu-id="fb73e-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![高可用性 Office 365 同盟 Azure 中的驗證基礎結構](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="fb73e-p110">圖 5-內部網路主控身分識別基礎結構與使用者。所連接的網站 VPN 或 ExpressRoute 連線的 Azure IaaS 閘道。Azure VNet 包含 web proxy 伺服器、 Active Directory Federation Services (AD FS) 伺服器及 Windows Server Active Directory (AD) 的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="fb73e-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="fb73e-188">此設定包含在 Azure 中 LOB 應用程式的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fb73e-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="fb73e-189">**層：** 有各層的 web proxy 伺服器、 AD FS 伺服器及 Windows Server AD 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="fb73e-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="fb73e-190">**載入通訊：** 外部 Azure 負載平衡器將傳入用戶端驗證要求的 web proxy 至和內部 Azure 負載平衡器散佈 AD FS 伺服器的驗證要求。</span><span class="sxs-lookup"><span data-stu-id="fb73e-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="fb73e-191">請遵循成功採用此路徑：</span><span class="sxs-lookup"><span data-stu-id="fb73e-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="fb73e-192">評估及試驗</span><span class="sxs-lookup"><span data-stu-id="fb73e-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="fb73e-193">請參閱建立 Office 365 同盟驗證的模擬的開發人員測試環境[的 Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="fb73e-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="fb73e-194">部署</span><span class="sxs-lookup"><span data-stu-id="fb73e-194">Deploy</span></span>
    
    <span data-ttu-id="fb73e-195">請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)逐一檢視五個階段中的 [AD FS 基礎結構的高可用性的端對端設定。</span><span class="sxs-lookup"><span data-stu-id="fb73e-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="fb73e-196">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb73e-196">See Also</span></span>

[<span data-ttu-id="fb73e-197">Microsoft Hybrid Cloud for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="fb73e-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="fb73e-198">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="fb73e-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


