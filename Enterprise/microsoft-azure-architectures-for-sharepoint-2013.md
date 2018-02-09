---
title: Microsoft Azure Architectures for SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: "摘要： SharePoint 2013 解決方案可以裝載於 Microsoft Azure 虛擬機器。了解解決方案的類型有良好的調整及如何設定 Microsoft Azure 至其中的主機。"
ms.openlocfilehash: 5156f3e8cabb3acabc7ad23a680a016c200c676e
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="57395-104">Microsoft Azure Architectures for SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="57395-104">Microsoft Azure Architectures for SharePoint 2013</span></span>

 <span data-ttu-id="57395-p102">**摘要：**SharePoint 2013 解決方案可以裝載於 Microsoft Azure 虛擬機器。了解解決方案的類型有良好的調整及如何設定 Microsoft Azure 至其中的主機。</span><span class="sxs-lookup"><span data-stu-id="57395-p102">**Summary:** SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.</span></span>
  
<span data-ttu-id="57395-p103">Azure 是架設 SharePoint Server 2013 解決方案良好環境。在大多數情況下，我們建議 Office 365 但架設在 Azure 中的 SharePoint 伺服器陣列可特定解決方案的良好的選擇。本文說明如何包括工程師的 SharePoint 解決方案所以是優符合 Azure 平台。下列兩個特定解決方案作為範例：</span><span class="sxs-lookup"><span data-stu-id="57395-p103">Azure is a good environment for hosting a SharePoint Server 2013 solution. In most cases, we recommend Office 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions. This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform. The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="57395-111">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="57395-111">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="57395-112">Microsoft Azure using SharePoint Server 2013 中的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="57395-112">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="57395-113">建議的 SharePoint 解決方案的 Azure 基礎結構服務</span><span class="sxs-lookup"><span data-stu-id="57395-113">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="57395-p104">Azure 基礎結構服務是架設 SharePoint 解決方案迫切] 選項。某些解決方案會比其他更合適的此平台。下表顯示建議的解決方案。</span><span class="sxs-lookup"><span data-stu-id="57395-p104">Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="57395-117">**解決方案**</span><span class="sxs-lookup"><span data-stu-id="57395-117">**Solution**</span></span>|<span data-ttu-id="57395-118">**此解決方案 azure 為什麼建議使用**</span><span class="sxs-lookup"><span data-stu-id="57395-118">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="57395-119">開發及測試環境</span><span class="sxs-lookup"><span data-stu-id="57395-119">Development and test environments</span></span>  <br/> |<span data-ttu-id="57395-120">很容易建立及管理這些環境。</span><span class="sxs-lookup"><span data-stu-id="57395-120">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="57395-121">Azure 至內部部署 SharePoint 伺服器陣列的災害復原</span><span class="sxs-lookup"><span data-stu-id="57395-121">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="57395-122">**裝載次要資料中心**使用 Azure 演變次要資料中心內的不同區域中。</span><span class="sxs-lookup"><span data-stu-id="57395-122">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="57395-p105">**較低成本嚴重損壞修復環境**維護及工資資源少於內部嚴重損壞修復環境。資源數目取決於您選擇嚴重損壞修復環境： 冷待命、 暖待命或熱待命。</span><span class="sxs-lookup"><span data-stu-id="57395-p105">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. </span></span><br/> <span data-ttu-id="57395-p106">**更多彈入平台**在發生災害時輕鬆地向外延展負載要求修復 SharePoint 伺服器陣列。當您不再需要資源的向外。</span><span class="sxs-lookup"><span data-stu-id="57395-p106">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. </span></span><br/> <span data-ttu-id="57395-127">請參閱[SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="57395-127">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="57395-128">使用功能與刻度不適用於 Office 365 的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="57395-128">Internet-facing sites that use features and scale not available in Office 365</span></span>  <br/> |<span data-ttu-id="57395-129">**整個計畫重心在工作**專注於建置更好的網站而不是建置基礎結構。</span><span class="sxs-lookup"><span data-stu-id="57395-129">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="57395-p107">**利用 Azure 中的 elasticity**大小需求的伺服器陣列來新增伺服器，然後只工資您需要的資源。動態機器配置不支援 （自動調整大小）。</span><span class="sxs-lookup"><span data-stu-id="57395-p107">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). </span></span><br/> <span data-ttu-id="57395-132">**使用 Azure Active Directory (AD)**善用客戶帳戶的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="57395-132">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="57395-133">**無法使用 Office 365 中新增的 SharePoint 功能**新增深報告與 web 分析。</span><span class="sxs-lookup"><span data-stu-id="57395-133">**Add SharePoint functionality not available in Office 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="57395-134">請參閱[Microsoft Azure using SharePoint Server 2013 中的網際網路網站](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)。</span><span class="sxs-lookup"><span data-stu-id="57395-134">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="57395-135">若要支援 Office 365 或內部部署環境的應用程式伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="57395-135">App farms to support Office 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="57395-136">**建立、 測試與代管應用程式**以支援兩個內部部署和雲端環境 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="57395-136">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="57395-137">Azure 而不是購買新硬體的內部部署環境中的**主機此角色**。</span><span class="sxs-lookup"><span data-stu-id="57395-137">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="57395-138">內部網路與共同作業解決方案及工作負載，請考慮下列選項：</span><span class="sxs-lookup"><span data-stu-id="57395-138">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="57395-p108">判斷 Office 365 是否符合您的業務需求或可以是解決方案的一部分。Office 365 提供永遠是最新的豐富的功能集。</span><span class="sxs-lookup"><span data-stu-id="57395-p108">Determine if Office 365 meets your business requirements or can be part of the solution. Office 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="57395-p109">如果 Office 365 不符合所有您的業務需求，請考慮在內部部署 Microsoft 諮詢服務 (ATL-MCS-001) 從 SharePoint 2013 的標準實作。標準架構可以是您一份自訂比支援更、 低廉、 且更容易解決方案。</span><span class="sxs-lookup"><span data-stu-id="57395-p109">If Office 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS). A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="57395-143">如果標準實作不符合您的業務需求，請考慮為自訂的內部部署解決方案。</span><span class="sxs-lookup"><span data-stu-id="57395-143">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="57395-p110">如果您的業務需求的重要使用雲端平台，請考慮在 Azure 基礎結構服務主控的 SharePoint 2013 的標準或自訂實作。容易比其他非原生 Microsoft 公用 cloud 平台支援 Azure 中的 SharePoint 解決方案為何。</span><span class="sxs-lookup"><span data-stu-id="57395-p110">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="57395-146">您在設計 Azure 環境之前</span><span class="sxs-lookup"><span data-stu-id="57395-146">Before you design the Azure environment</span></span>

<span data-ttu-id="57395-p111">儘管本文使用範例 SharePoint 拓撲，您可以使用這些設計概念與任何 SharePoint 伺服器陣列拓撲。設計 Azure 環境之前，請使用下列拓撲、 架構、 容量及效能指導來設計的 SharePoint 伺服器陣列：</span><span class="sxs-lookup"><span data-stu-id="57395-p111">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="57395-149">SharePoint 2013 IT 專業人員的架構設計</span><span class="sxs-lookup"><span data-stu-id="57395-149">Architecture design for SharePoint 2013 IT pros</span></span>](http://technet.microsoft.com/en-us/sharepoint/fp123594.aspx)
    
- [<span data-ttu-id="57395-150">規劃效能和容量管理 SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="57395-150">Plan for performance and capacity management in SharePoint Server 2013</span></span>](http://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="57395-151">決定 Active Directory 網域類型</span><span class="sxs-lookup"><span data-stu-id="57395-151">Determine the Active Directory domain type</span></span>

<span data-ttu-id="57395-p112">每個 SharePoint 伺服器陣列依賴 Active Directory 提供給伺服器陣列安裝程式的管理帳戶。在此階段中，有兩個 Azure 中的 SharePoint 解決方案的選項。下表說明這些。</span><span class="sxs-lookup"><span data-stu-id="57395-p112">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.</span></span>
  
|<span data-ttu-id="57395-155">**選項**</span><span class="sxs-lookup"><span data-stu-id="57395-155">**Option**</span></span>|<span data-ttu-id="57395-156">**說明**</span><span class="sxs-lookup"><span data-stu-id="57395-156">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="57395-157">專用的網域</span><span class="sxs-lookup"><span data-stu-id="57395-157">Dedicated domain</span></span>  <br/> |<span data-ttu-id="57395-p113">您可對 Azure 以支援您的 SharePoint 伺服器陣列部署專用和隔離的 Active Directory 網域。這是不錯的選擇的公用對向網際網路網站。</span><span class="sxs-lookup"><span data-stu-id="57395-p113">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="57395-160">擴充跨部署連線到內部部署網域</span><span class="sxs-lookup"><span data-stu-id="57395-160">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="57395-p114">當您擴充跨部署連線到內部網域時、 使用者會存取透過您的內部網路 SharePoint 伺服器陣列主控內部部署一樣。您可以運用您的內部部署 Active Directory 和 DNS 實作。</span><span class="sxs-lookup"><span data-stu-id="57395-p114">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="57395-163">跨部署的連線，則需要建置 Azure 容錯移轉至從內部部署伺服器陣列中的嚴重損壞修復環境。</span><span class="sxs-lookup"><span data-stu-id="57395-163">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="57395-p115">本文包含擴充跨部署連線到內部網域的設計的概念。如果您的解決方案使用專用的網域，您不需要跨部署的連線。</span><span class="sxs-lookup"><span data-stu-id="57395-p115">This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="57395-166">設計虛擬網路</span><span class="sxs-lookup"><span data-stu-id="57395-166">Design the virtual network</span></span>

<span data-ttu-id="57395-p116">首先需要 Azure，其中包含子網路會放置在虛擬機器中的虛擬網路。虛擬網路需要私人 IP 位址空間，您指派給子網路的部分。</span><span class="sxs-lookup"><span data-stu-id="57395-p116">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="57395-169">如果您要擴充至 Azure 的內部網路透過跨部署連線 （嚴重損壞修復環境需要），您必須選擇尚未在其中包含您組織的網路中其他地方使用私人位址空間內部部署環境及其他 Azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="57395-169">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="57395-170">**圖 1： 內部部署環境與 Azure 虛擬網路**</span><span class="sxs-lookup"><span data-stu-id="57395-170">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![為 SharePoint 解決方案設計的 Microsoft Azure 虛擬網路。Azure 閘道的一個子網路。虛擬機器的一個子網路。](images/OPrrasconWA_AZarch.png)
  
<span data-ttu-id="57395-174">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="57395-174">In this diagram:</span></span>
  
- <span data-ttu-id="57395-p118">在 Azure 虛擬網路是圖解-並排至內部部署環境。兩個環境不尚未連接所連接的跨部署的連線，可以為網站 VPN 連線或 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="57395-p118">A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="57395-p119">此時，虛擬網路只包含子網路與任何其他架構元素。一個子網路將裝載 Azure 閘道和其他子網路主控的 SharePoint 伺服器陣列、 Active Directory 和 DNS 額外一層。</span><span class="sxs-lookup"><span data-stu-id="57395-p119">At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="57395-179">新增跨部署連線</span><span class="sxs-lookup"><span data-stu-id="57395-179">Add cross-premises connectivity</span></span>

<span data-ttu-id="57395-p120">部署下一步是建立跨部署連線 （如果這適用於您的解決方案）。跨部署連線 Azure 閘道位於不同的閘道的子網路，您必須建立並指派位址空間。</span><span class="sxs-lookup"><span data-stu-id="57395-p120">The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="57395-182">當您規劃跨部署的連線時，您會定義及建立 Azure 閘道和內部閘道裝置的連線。</span><span class="sxs-lookup"><span data-stu-id="57395-182">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="57395-183">**圖 2： 使用 Azure 閘道和內部閘道裝置來提供內部部署環境及 Azure 之間的網站連線**</span><span class="sxs-lookup"><span data-stu-id="57395-183">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![內部部署環境已透過跨單位連線連接至 Azure 虛擬網路，其可以是網站對網站 VPN 連線或是 ExpressRoute](images/AZarch_VPNgtwyconnct.png)
  
<span data-ttu-id="57395-185">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="57395-185">In this diagram:</span></span>
  
- <span data-ttu-id="57395-186">上圖中加入，內部部署環境是透過連接至 Azure 虛擬網路的跨內部連線，可以為網站 VPN 連線或 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="57395-186">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="57395-187">Azure 閘道為閘道的子網路上。</span><span class="sxs-lookup"><span data-stu-id="57395-187">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="57395-188">內部部署環境包含閘道裝置，例如路由器或 VPN 伺服器。</span><span class="sxs-lookup"><span data-stu-id="57395-188">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="57395-189">如需規劃及建立跨內部虛擬網路的詳細資訊，請參閱 ＜[連接到 Microsoft Azure 虛擬網路的內部網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="57395-189">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-windows-server-active-directory-ad-and-dns"></a><span data-ttu-id="57395-190">新增 Windows Server Active Directory (AD) 和 DNS</span><span class="sxs-lookup"><span data-stu-id="57395-190">Add Windows Server Active Directory (AD) and DNS</span></span>

<span data-ttu-id="57395-191">您可以在 Azure 中的嚴重損壞修復、 部署 Windows Server AD 和 Windows Server AD 所在的混合式案例的 DNS 同時在內部部署與 Azure 虛擬機器上。</span><span class="sxs-lookup"><span data-stu-id="57395-191">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="57395-192">**圖 3： 混合式 Active Directory 網域組態**</span><span class="sxs-lookup"><span data-stu-id="57395-192">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![STwo 虛擬機器部署到 Azure 虛擬網路和 SharePoint 伺服器陣列子網路是複本網域控制站和 DNS 伺服器](images/AZarch_HyADdomainConfig.png)
  
<span data-ttu-id="57395-p121">此圖建置在先前圖表加入至 Windows Server AD 的兩個虛擬機器與 DNS 的子網路。這些虛擬機器複本的網域控制站和 DNS 伺服器。他們是副檔名為內部部署 Windows Server AD 環境。</span><span class="sxs-lookup"><span data-stu-id="57395-p121">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="57395-p122">下表提供這些 Azure 中的虛擬機器設定建議。使用這些當做起點來設計您自己環境 — 即使為專用網域 Azure 環境不會與內部部署環境通訊的地方。</span><span class="sxs-lookup"><span data-stu-id="57395-p122">The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="57395-199">**項目**</span><span class="sxs-lookup"><span data-stu-id="57395-199">**Item**</span></span>|<span data-ttu-id="57395-200">**設定**</span><span class="sxs-lookup"><span data-stu-id="57395-200">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="57395-201">在 Azure 虛擬機器大小</span><span class="sxs-lookup"><span data-stu-id="57395-201">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="57395-202">標準層中的 A1 或 A2 大小</span><span class="sxs-lookup"><span data-stu-id="57395-202">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="57395-203">作業系統</span><span class="sxs-lookup"><span data-stu-id="57395-203">Operating system</span></span>  <br/> |<span data-ttu-id="57395-204">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="57395-204">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="57395-205">Active Directory 角色</span><span class="sxs-lookup"><span data-stu-id="57395-205">Active Directory role</span></span>  <br/> |<span data-ttu-id="57395-p123">AD DS 網域控制站指定為通用類別目錄伺服器。此設定會減少輸出流量之間的跨部署的連線。</span><span class="sxs-lookup"><span data-stu-id="57395-p123">AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="57395-208">（這是不常見） 變更速率高多網域環境中，設定內部部署不適用於同步處理的通用類別目錄伺服器在 Azure，以減少複寫流量的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="57395-208">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="57395-209">DNS 角色</span><span class="sxs-lookup"><span data-stu-id="57395-209">DNS role</span></span>  <br/> |<span data-ttu-id="57395-210">安裝並設定網域控制站上的 DNS 伺服器服務。</span><span class="sxs-lookup"><span data-stu-id="57395-210">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="57395-211">資料磁碟</span><span class="sxs-lookup"><span data-stu-id="57395-211">Data disks</span></span>  <br/> |<span data-ttu-id="57395-p124">Active Directory 資料庫、 記錄以及 SYSVOL 置於其他 Azure 資料的磁碟。不放置這些作業系統磁碟或 Azure 所提供的暫存磁碟上。</span><span class="sxs-lookup"><span data-stu-id="57395-p124">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="57395-214">IP 位址</span><span class="sxs-lookup"><span data-stu-id="57395-214">IP addresses</span></span>  <br/> |<span data-ttu-id="57395-215">使用靜態 IP 位址並設定虛擬網路之後的網域控制站台，這些位址指派給虛擬網路中的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="57395-215">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="57395-p125">部署在 Azure 中的 Active Directory 之前，請先閱讀[部署 Windows Server Active directory Azure 虛擬機器上的指導方針](https://go.microsoft.com/fwlink/p/?linkid=392681)。這些協助您判斷不同架構或不同的組態設定所需的解決方案。</span><span class="sxs-lookup"><span data-stu-id="57395-p125">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="57395-218">新增 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="57395-218">Add the SharePoint farm</span></span>

<span data-ttu-id="57395-219">置於適當的子網路層 SharePoint 伺服器陣列的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="57395-219">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="57395-220">**圖 4： 位置的 SharePoint 虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="57395-220">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![資料庫伺服器和 SharePoint 伺服器角色加入 SharePoint 伺服器陣列子網路內的 Azure 虛擬網路](images/AZarch_SPVMsinCloudSer.png)
  
<span data-ttu-id="57395-222">此圖建置在先前圖表其各自的各層中加入 SharePoint 伺服器陣列伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="57395-222">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="57395-223">執行 SQL Server 的兩個資料庫虛擬機器時建立的資料庫層。</span><span class="sxs-lookup"><span data-stu-id="57395-223">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="57395-224">在下列各層的每個執行 SharePoint Server 2013 的兩個虛擬機器： 前端伺服器、 分散式快取伺服器及後端伺服器。</span><span class="sxs-lookup"><span data-stu-id="57395-224">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="57395-225">設計與微調可用性設定 」 和 「 容錯網域的伺服器角色</span><span class="sxs-lookup"><span data-stu-id="57395-225">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="57395-p126">容錯網域是硬體的一群中執行哪些角色執行個體。在相同的容錯網域內的虛擬機器可由 Azure 基礎結構更新同時。或者，他們可以因為它們都共用同一個機架失敗，同時。若要避免在相同的容錯網域擁有兩個虛擬機器時的風險，您可以設定虛擬機器可用性設定，以確保每部虛擬機器是不同的容錯網域中。如果三個虛擬機器設定可用性設定、 Azure 保證不超過兩個虛擬機器都位於相同的容錯網域。</span><span class="sxs-lookup"><span data-stu-id="57395-p126">A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="57395-p127">當您設計的 SharePoint 伺服器陣列的 Azure 架構時，設定可用性組屬於相同的伺服器角色。這可確保虛擬機器時所遍佈多個容錯網域。</span><span class="sxs-lookup"><span data-stu-id="57395-p127">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="57395-233">**圖 5： 使用 Azure 可用性設定以提供在 SharePoint 伺服器陣列各層的高可用性**</span><span class="sxs-lookup"><span data-stu-id="57395-233">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![Azure 基礎結構中針對 SharePoint 2013 解決方案的可用性設定組設定](images/AZenv_WinAzureAvailSetsHA.png)
  
<span data-ttu-id="57395-p128">此圖呼叫出 Azure 基礎結構內的可用性設定的設定。每個下列角色共用個別可用性設定：</span><span class="sxs-lookup"><span data-stu-id="57395-p128">This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="57395-237">Active Directory 和 DNS</span><span class="sxs-lookup"><span data-stu-id="57395-237">Active Directory and DNS</span></span>
    
- <span data-ttu-id="57395-238">資料庫</span><span class="sxs-lookup"><span data-stu-id="57395-238">Database</span></span>
    
- <span data-ttu-id="57395-239">後端</span><span class="sxs-lookup"><span data-stu-id="57395-239">Back end</span></span>
    
- <span data-ttu-id="57395-240">發佈快取</span><span class="sxs-lookup"><span data-stu-id="57395-240">Distribute cache</span></span>
    
- <span data-ttu-id="57395-241">前端</span><span class="sxs-lookup"><span data-stu-id="57395-241">Front end</span></span>
    
<span data-ttu-id="57395-p129">SharePoint 伺服器陣列可能會需要可調整的 Azure 平台。若要確保高可用性的所有元件，確定伺服器角色的所有設定的同名。</span><span class="sxs-lookup"><span data-stu-id="57395-p129">The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="57395-p130">以下是顯示標準的網際網路網站架構符合特定的容量和效能目標的範例。本範例會精選下列架構模型： [SharePoint Server 2013 的網際網路網站搜尋架構](https://go.microsoft.com/fwlink/p/?LinkId=261519)。</span><span class="sxs-lookup"><span data-stu-id="57395-p130">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="57395-246">**圖 6： 規劃在三層式伺服器陣列中的容量和效能目標的範例**</span><span class="sxs-lookup"><span data-stu-id="57395-246">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![標準 SharePoint 2013 Internet Sites 架構具有符合特定容量和效能目標的元件配置](images/AZarch_CapPerfexmpArch.png)
  
<span data-ttu-id="57395-248">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="57395-248">In this diagram:</span></span>
  
- <span data-ttu-id="57395-249">表示在三層式伺服器陣列： 網頁伺服器、 應用程式伺服器及資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="57395-249">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="57395-250">具有多個元件同名設定三個網頁伺服器。</span><span class="sxs-lookup"><span data-stu-id="57395-250">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="57395-251">兩部資料庫伺服器的設定都相同。</span><span class="sxs-lookup"><span data-stu-id="57395-251">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="57395-p131">三個應用程式伺服器未設定進行完全相同。這些伺服器角色都需要在 Azure 中的可用性的可調整設定。</span><span class="sxs-lookup"><span data-stu-id="57395-p131">The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="57395-254">讓我們看接近在應用程式伺服器層。</span><span class="sxs-lookup"><span data-stu-id="57395-254">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="57395-255">**圖 7： 應用程式伺服器層之前可調整**</span><span class="sxs-lookup"><span data-stu-id="57395-255">**Figure 7: Application server tier before fine tuning**</span></span>

![調整為 Microsoft Azure 可用性設定組之前的 SharePoint Server 2013 應用程式伺服器層範例](images/AZarch_AppServtierBefore.png)
  
<span data-ttu-id="57395-257">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="57395-257">In this diagram:</span></span>
  
- <span data-ttu-id="57395-258">在 [應用程式層包含三部伺服器。</span><span class="sxs-lookup"><span data-stu-id="57395-258">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="57395-259">第一部伺服器包含四個元件。</span><span class="sxs-lookup"><span data-stu-id="57395-259">The first server includes four components.</span></span>
    
- <span data-ttu-id="57395-260">第二個 server 包含三個元件。</span><span class="sxs-lookup"><span data-stu-id="57395-260">The second server includes three components.</span></span>
    
- <span data-ttu-id="57395-261">第三個伺服器包含兩個元件。</span><span class="sxs-lookup"><span data-stu-id="57395-261">The third server includes two components.</span></span>
    
<span data-ttu-id="57395-p132">您的伺服器陣列的效能與容量目標是判斷元件數目。Azure 能否此架構，我們將所有三部伺服器上複寫的四個元件。這會增加超過功能時所需的效能與容量的元件數目。取捨是此設計可確保當下列三個虛擬機器時指派給可用性設定 Azure 平台中所有的四個元件的高可用性。</span><span class="sxs-lookup"><span data-stu-id="57395-p132">You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="57395-266">**圖 8： 應用程式伺服器層後可調整**</span><span class="sxs-lookup"><span data-stu-id="57395-266">**Figure 8: Application server tier after fine tuning**</span></span>

![調整為 Microsoft Azure 可用性設定組之後的 SharePoint Server 2013 應用程式伺服器層範例](images/AZarch_AppServtierAfter.png)
  
<span data-ttu-id="57395-268">此圖顯示相同的四個元件進行完全相同設定的所有三個應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="57395-268">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="57395-269">當我們將可用性設定新增至 SharePoint 伺服器陣列層時，實作已完成。</span><span class="sxs-lookup"><span data-stu-id="57395-269">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="57395-270">**圖 9： 完成的 SharePoint 伺服器陣列中 Azure 基礎結構服務**</span><span class="sxs-lookup"><span data-stu-id="57395-270">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![Azure Infrastructure Services 中的 SharePoint 2013 伺服器陣列以及虛擬網路、跨單位連線能力、子網路、VM 以及可用性設定組的範例 ](images/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="57395-272">此圖顯示實作於 Azure 基礎結構服務，以提供容錯網域的每一層中的伺服器的可用性設定 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="57395-272">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
<span data-ttu-id="57395-273">**加入討論區**</span><span class="sxs-lookup"><span data-stu-id="57395-273">**Join the discussion**</span></span>

|<span data-ttu-id="57395-274">**與我們連絡**</span><span class="sxs-lookup"><span data-stu-id="57395-274">**Contact us**</span></span>|<span data-ttu-id="57395-275">**描述**</span><span class="sxs-lookup"><span data-stu-id="57395-275">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="57395-276">**雲端採用內容您是否需要吗？**</span><span class="sxs-lookup"><span data-stu-id="57395-276">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="57395-p133">我們會建立橫跨多個 Microsoft cloud 平台及服務的雲端採用的內容。我們知道什麼構思我們雲端採用內容，或藉由傳送電子郵件給[cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)要求特定的內容。</span><span class="sxs-lookup"><span data-stu-id="57395-p133">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="57395-279">**加入雲端採用討論**</span><span class="sxs-lookup"><span data-stu-id="57395-279">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="57395-p134">如果您是找到他們需雲端式解決方案，請考慮加入雲端採用 Advisory 董 (CAAB) 與 Microsoft 內容的開發人員、 產業專業人員和客戶的從遍更大型、 加上鮮豔社群連線。若要加入，新增您自己的 Microsoft 技術社群[CAAB （雲端採用諮詢委員會） 空間](https://aka.ms/caab)的成員身分並在[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)快速的電子郵件傳送意見。任何人都可以讀取上[CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)社群相關內容。不過，CAAB 成員取得說明新雲端採用資源和解決方案的私人研討會的邀請。</span><span class="sxs-lookup"><span data-stu-id="57395-p134">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe. To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!). Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/). However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.  </span></span><br/> |
|<span data-ttu-id="57395-283">**取得您在此處看到美工圖案**</span><span class="sxs-lookup"><span data-stu-id="57395-283">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="57395-p135">如果您想編輯您在本文中看到藝術複本，我們樂於傳送給您。您的要求，包含 URL 及標題的圖案、 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)的電子郵件。</span><span class="sxs-lookup"><span data-stu-id="57395-p135">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="57395-286">請參閱</span><span class="sxs-lookup"><span data-stu-id="57395-286">See Also</span></span>

[<span data-ttu-id="57395-287">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="57395-287">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="57395-288">Microsoft Azure using SharePoint Server 2013 中的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="57395-288">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="57395-289">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="57395-289">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


