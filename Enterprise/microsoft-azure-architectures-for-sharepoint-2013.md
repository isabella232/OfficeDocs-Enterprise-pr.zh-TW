---
title: Microsoft Azure SharePoint 2013 架構
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 摘要： SharePoint 2013 解決方案可以裝載於 Microsoft Azure 虛擬機器。 了解何種類型的解決方案是很好的調整，以及如何設定 Microsoft Azure，以其中一個主機。
ms.openlocfilehash: 7bc274098f961ccf9aa6aef05f595dfc6e116bec
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032288"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="ddc90-104">Microsoft Azure SharePoint 2013 架構</span><span class="sxs-lookup"><span data-stu-id="ddc90-104">Microsoft Azure Architectures for SharePoint 2013</span></span>

 <span data-ttu-id="ddc90-105">**摘要：** SharePoint 2013 解決方案可裝載在 Microsoft Azure 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="ddc90-105">**Summary:** SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines.</span></span> <span data-ttu-id="ddc90-106">了解何種類型的解決方案是很好的調整，以及如何設定 Microsoft Azure，以其中一個主機。</span><span class="sxs-lookup"><span data-stu-id="ddc90-106">Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.</span></span>
  
<span data-ttu-id="ddc90-107">Azure 是主控 SharePoint Server 2013 解決方案的良好環境。</span><span class="sxs-lookup"><span data-stu-id="ddc90-107">Azure is a good environment for hosting a SharePoint Server 2013 solution.</span></span> <span data-ttu-id="ddc90-108">在大多數情況下，我們建議您 Office 365，但裝載於 Azure 中 SharePoint Server 伺服器陣列可以是很好的選擇，針對特定解決方案。</span><span class="sxs-lookup"><span data-stu-id="ddc90-108">In most cases, we recommend Office 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions.</span></span> <span data-ttu-id="ddc90-109">本文說明如何設計的 SharePoint 解決方案，因此它們是不錯符合在 Azure 的平台。</span><span class="sxs-lookup"><span data-stu-id="ddc90-109">This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform.</span></span> <span data-ttu-id="ddc90-110">下列兩個特定解決方案做為範例：</span><span class="sxs-lookup"><span data-stu-id="ddc90-110">The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="ddc90-111">Microsoft Azure 中的 SharePoint Server 2013 災害復原</span><span class="sxs-lookup"><span data-stu-id="ddc90-111">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="ddc90-112">Microsoft Azure 中使用 SharePoint Server 2013 的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="ddc90-112">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="ddc90-113">Azure 基礎結構服務的建議的 SharePoint 解決方案</span><span class="sxs-lookup"><span data-stu-id="ddc90-113">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="ddc90-114">Azure 基礎結構服務是令人讚嘆裝載 SharePoint 解決方案的選項。</span><span class="sxs-lookup"><span data-stu-id="ddc90-114">Azure infrastructure services is a compelling option for hosting SharePoint solutions.</span></span> <span data-ttu-id="ddc90-115">某些解決方案會比其他較適合此平台。</span><span class="sxs-lookup"><span data-stu-id="ddc90-115">Some solutions are a better fit for this platform than others.</span></span> <span data-ttu-id="ddc90-116">下表顯示建議的解決方案。</span><span class="sxs-lookup"><span data-stu-id="ddc90-116">The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="ddc90-117">**解決方案**</span><span class="sxs-lookup"><span data-stu-id="ddc90-117">**Solution**</span></span>|<span data-ttu-id="ddc90-118">**Azure 為何建議此解決方案**</span><span class="sxs-lookup"><span data-stu-id="ddc90-118">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ddc90-119">開發和測試環境</span><span class="sxs-lookup"><span data-stu-id="ddc90-119">Development and test environments</span></span>  <br/> |<span data-ttu-id="ddc90-120">很容易建立及管理這些環境。</span><span class="sxs-lookup"><span data-stu-id="ddc90-120">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="ddc90-121">內部部署 SharePoint 伺服器陣列至 Azure 的災害復原</span><span class="sxs-lookup"><span data-stu-id="ddc90-121">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="ddc90-122">**託管次要資料中心**使用 Azure，而非投資位於不同地區的次要資料中心內。</span><span class="sxs-lookup"><span data-stu-id="ddc90-122">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="ddc90-123">**成本較低的災害復原環境**維護及支付比內部損毀修復環境較少的資源。</span><span class="sxs-lookup"><span data-stu-id="ddc90-123">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment.</span></span> <span data-ttu-id="ddc90-124">資源數目取決於您選擇在災害復原環境： 冷待命、 暖待命或熱待命。</span><span class="sxs-lookup"><span data-stu-id="ddc90-124">The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby.</span></span> <br/> <span data-ttu-id="ddc90-125">**更多彈性的平台**發生災害時，輕鬆地延展復原 SharePoint 伺服器陣列以符合負載需求。</span><span class="sxs-lookup"><span data-stu-id="ddc90-125">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements.</span></span> <span data-ttu-id="ddc90-126">當您不再需要資源中比例調整。</span><span class="sxs-lookup"><span data-stu-id="ddc90-126">Scale in when you no longer need the resources.</span></span> <br/> <span data-ttu-id="ddc90-127">請參閱[Microsoft Azure 中 SharePoint Server 2013 災害復原](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc90-127">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="ddc90-128">使用功能並不適用於 Office 365 的縮放比例的網際網路對向網站</span><span class="sxs-lookup"><span data-stu-id="ddc90-128">Internet-facing sites that use features and scale not available in Office 365</span></span>  <br/> |<span data-ttu-id="ddc90-129">**業務**專注於建立絕佳的網站，而不是建置基礎結構。</span><span class="sxs-lookup"><span data-stu-id="ddc90-129">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="ddc90-130">**利用 Azure 中的彈性**來新增新的伺服器、 調整大小需求的伺服器陣列，並僅支付您需要的資源。</span><span class="sxs-lookup"><span data-stu-id="ddc90-130">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need.</span></span> <span data-ttu-id="ddc90-131">動態機器配置不受支援 （自動調整大小）。</span><span class="sxs-lookup"><span data-stu-id="ddc90-131">Dynamic machine allocation is not supported (auto scale).</span></span> <br/> <span data-ttu-id="ddc90-132">**使用 Azure Active Directory (AD)** 善用客戶帳戶的 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="ddc90-132">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="ddc90-133">**新增 SharePoint 功能不適用於 Office 365**新增深報告及 web analytics。</span><span class="sxs-lookup"><span data-stu-id="ddc90-133">**Add SharePoint functionality not available in Office 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="ddc90-134">請參閱[Microsoft Azure 中使用 SharePoint Server 2013 的網際網路網站](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc90-134">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="ddc90-135">若要支援 Office 365 或內部部署環境的應用程式伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="ddc90-135">App farms to support Office 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="ddc90-136">**建立、 測試和主機應用程式**以支援這兩個內部部署和雲端環境的 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="ddc90-136">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="ddc90-137">而不是購買新的硬體，內部部署環境的 Azure 中的**主機此角色**。</span><span class="sxs-lookup"><span data-stu-id="ddc90-137">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="ddc90-138">內部網路共同作業解決方案和工作負載，請考慮下列選項：</span><span class="sxs-lookup"><span data-stu-id="ddc90-138">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="ddc90-139">決定 Office 365 是否符合您的業務需求，或是可以是方案的一部分。</span><span class="sxs-lookup"><span data-stu-id="ddc90-139">Determine if Office 365 meets your business requirements or can be part of the solution.</span></span> <span data-ttu-id="ddc90-140">Office 365 提供永遠是最新的豐富的功能集。</span><span class="sxs-lookup"><span data-stu-id="ddc90-140">Office 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="ddc90-141">如果 Office 365 不符合所有您的業務需求，請考慮 SharePoint 2013 內部部署從 Microsoft 諮詢服務 (MCS) 的標準實作。</span><span class="sxs-lookup"><span data-stu-id="ddc90-141">If Office 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS).</span></span> <span data-ttu-id="ddc90-142">標準架構可供您支援超過一份自訂的速度較快，成本較低，且更容易解決方案。</span><span class="sxs-lookup"><span data-stu-id="ddc90-142">A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="ddc90-143">如果標準的實作不符合您的業務需求，請考慮為自訂的內部部署解決方案。</span><span class="sxs-lookup"><span data-stu-id="ddc90-143">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="ddc90-144">如果使用雲端平台是很重要的商務需求，請考慮裝載在 Azure 基礎結構服務中的 SharePoint 2013 的標準或自訂實作。</span><span class="sxs-lookup"><span data-stu-id="ddc90-144">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services.</span></span> <span data-ttu-id="ddc90-145">SharePoint 解決方案會比其他非原生 Microsoft 公用雲端平台支援在 Azure 中更加容易。</span><span class="sxs-lookup"><span data-stu-id="ddc90-145">SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="ddc90-146">您在設計 Azure 環境之前</span><span class="sxs-lookup"><span data-stu-id="ddc90-146">Before you design the Azure environment</span></span>

<span data-ttu-id="ddc90-147">儘管本文使用範例 SharePoint 拓撲，您可以使用這些設計概念與任何 SharePoint 伺服器陣列拓撲。</span><span class="sxs-lookup"><span data-stu-id="ddc90-147">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology.</span></span> <span data-ttu-id="ddc90-148">設計 Azure 環境之前，請使用下列的拓撲、 架構、 容量及效能指引來設計 SharePoint 伺服器陣列：</span><span class="sxs-lookup"><span data-stu-id="ddc90-148">Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="ddc90-149">適用於 SharePoint 2013 IT 專業人員的架構設計</span><span class="sxs-lookup"><span data-stu-id="ddc90-149">Architecture design for SharePoint 2013 IT pros</span></span>](http://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [<span data-ttu-id="ddc90-150">規劃效能和 SharePoint Server 2013 中的容量管理</span><span class="sxs-lookup"><span data-stu-id="ddc90-150">Plan for performance and capacity management in SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="ddc90-151">判定 Active Directory 網域類型</span><span class="sxs-lookup"><span data-stu-id="ddc90-151">Determine the Active Directory domain type</span></span>

<span data-ttu-id="ddc90-152">每個 SharePoint 伺服器陣列依賴 Active Directory 以伺服器陣列安裝程式提供的管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="ddc90-152">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup.</span></span> <span data-ttu-id="ddc90-153">在這個階段中，有兩個選項可在 Azure 中的 SharePoint 解決方案。</span><span class="sxs-lookup"><span data-stu-id="ddc90-153">At this time, there are two options for SharePoint solutions in Azure.</span></span> <span data-ttu-id="ddc90-154">下表說明這些。</span><span class="sxs-lookup"><span data-stu-id="ddc90-154">These are described in the following table.</span></span>
  
|<span data-ttu-id="ddc90-155">**選項**</span><span class="sxs-lookup"><span data-stu-id="ddc90-155">**Option**</span></span>|<span data-ttu-id="ddc90-156">**描述**</span><span class="sxs-lookup"><span data-stu-id="ddc90-156">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ddc90-157">專用的網域</span><span class="sxs-lookup"><span data-stu-id="ddc90-157">Dedicated domain</span></span>  <br/> |<span data-ttu-id="ddc90-158">您可以將以支援您的 SharePoint 伺服器陣列的 Azure 部署專用和隔離的 Active Directory 網域。</span><span class="sxs-lookup"><span data-stu-id="ddc90-158">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm.</span></span> <span data-ttu-id="ddc90-159">這是很好的選擇的公用對向網際網路網站。</span><span class="sxs-lookup"><span data-stu-id="ddc90-159">This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="ddc90-160">擴充跨單位連線到內部部署網域</span><span class="sxs-lookup"><span data-stu-id="ddc90-160">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="ddc90-161">當您擴充跨單位連線到內部部署網域時，使用者會存取透過您的內部網路 SharePoint 伺服器陣列，好像它是裝載於內部。</span><span class="sxs-lookup"><span data-stu-id="ddc90-161">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises.</span></span> <span data-ttu-id="ddc90-162">您可以利用您的內部部署 Active Directory 和 DNS 實作。</span><span class="sxs-lookup"><span data-stu-id="ddc90-162">You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="ddc90-163">需要建立容錯移轉至從內部部署伺服器陣列的 Azure 中的災害復原環境的跨單位連線。</span><span class="sxs-lookup"><span data-stu-id="ddc90-163">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="ddc90-164">本文包含延伸透過跨單位連線內部部署網域設計的概念。</span><span class="sxs-lookup"><span data-stu-id="ddc90-164">This article includes design concepts for extending the on-premises domain through a cross-premises connection.</span></span> <span data-ttu-id="ddc90-165">如果您的解決方案使用專用的網域，您不需要跨單位連線。</span><span class="sxs-lookup"><span data-stu-id="ddc90-165">If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="ddc90-166">設計虛擬網路</span><span class="sxs-lookup"><span data-stu-id="ddc90-166">Design the virtual network</span></span>

<span data-ttu-id="ddc90-167">首先，您必須包含您要放置虛擬機器的子網路的 azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ddc90-167">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines.</span></span> <span data-ttu-id="ddc90-168">虛擬網路需要私人 IP 位址空間，您指派至子網路的部分。</span><span class="sxs-lookup"><span data-stu-id="ddc90-168">The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="ddc90-169">如果您透過跨單位連線 （所需的災害復原環境），將您的內部部署網路延伸到 Azure，您必須選擇尚未在您組織的網路，其中可以包含其他地方使用私人位址空間您的內部部署環境和其他 Azure 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ddc90-169">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="ddc90-170">**圖 1： 內部部署環境與 Azure 虛擬網路**</span><span class="sxs-lookup"><span data-stu-id="ddc90-170">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![為 SharePoint 解決方案設計的 Microsoft Azure 虛擬網路。](media/OPrrasconWA-AZarch.png)
  
<span data-ttu-id="ddc90-174">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="ddc90-174">In this diagram:</span></span>
  
- <span data-ttu-id="ddc90-175">在 Azure 虛擬網路是圖解-並存至內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="ddc90-175">A virtual network in Azure is illustrated side-by-side to the on-premises environment.</span></span> <span data-ttu-id="ddc90-176">在兩個環境已透過跨單位連線，這可以是站台對站 VPN 連線或是 ExpressRoute 尚未連接。</span><span class="sxs-lookup"><span data-stu-id="ddc90-176">The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="ddc90-177">此時，虛擬網路只包含子網路與任何其他架構的項目。</span><span class="sxs-lookup"><span data-stu-id="ddc90-177">At this point, the virtual network just includes the subnets and no other architectural elements.</span></span> <span data-ttu-id="ddc90-178">一個子網路會裝載 Azure 閘道和其他子網路裝載 SharePoint 伺服器陣列，額外一個用於 Active Directory 和 DNS 的層級。</span><span class="sxs-lookup"><span data-stu-id="ddc90-178">One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="ddc90-179">新增交叉部署連線能力</span><span class="sxs-lookup"><span data-stu-id="ddc90-179">Add cross-premises connectivity</span></span>

<span data-ttu-id="ddc90-180">部署下一步是建立跨單位連線 （如果這適用於您的解決方案）。</span><span class="sxs-lookup"><span data-stu-id="ddc90-180">The next deployment step is to create the cross-premises connection (if this applies to your solution).</span></span> <span data-ttu-id="ddc90-181">對於跨單位連線，Azure 閘道位於不同的閘道子網路，您必須建立並指派位址空間。</span><span class="sxs-lookup"><span data-stu-id="ddc90-181">For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="ddc90-182">當您規劃的跨單位連線時，您定義，並建立 Azure 閘道和內部部署閘道器裝置的連線。</span><span class="sxs-lookup"><span data-stu-id="ddc90-182">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="ddc90-183">**圖 2： 使用 Azure 閘道和內部部署閘道器裝置來提供內部部署環境與 Azure 之間的站台對站台連線**</span><span class="sxs-lookup"><span data-stu-id="ddc90-183">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![內部部署環境已透過跨單位連線連接至 Azure 虛擬網路，其可以是網站對網站 VPN 連線或是 ExpressRoute](media/AZarch-VPNgtwyconnct.png)
  
<span data-ttu-id="ddc90-185">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="ddc90-185">In this diagram:</span></span>
  
- <span data-ttu-id="ddc90-186">將新增至上圖，內部部署環境是透過連接至 Azure 虛擬網路的跨單位連線，可以是站台對站 VPN 連線或是 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="ddc90-186">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="ddc90-187">Azure 閘道為閘道子網路上。</span><span class="sxs-lookup"><span data-stu-id="ddc90-187">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="ddc90-188">內部部署環境中包含閘道裝置，例如路由器或 VPN 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ddc90-188">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="ddc90-189">如需規劃和建立跨單位部署虛擬網路的詳細資訊，請參閱[連線到 Microsoft Azure 虛擬網路的內部網路](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc90-189">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a><span data-ttu-id="ddc90-190">新增 Active Directory 網域服務 (AD DS) 和 DNS</span><span class="sxs-lookup"><span data-stu-id="ddc90-190">Add Active Directory Domain Services (AD DS) and DNS</span></span>

<span data-ttu-id="ddc90-191">對於在 Azure 中的災害復原，您部署 Windows Server AD 和混合式案例，其中是 Windows Server AD 中的 DNS 這兩個內部部署與 Azure 虛擬機器上。</span><span class="sxs-lookup"><span data-stu-id="ddc90-191">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="ddc90-192">**圖 3： 混合式 Active Directory 網域組態**</span><span class="sxs-lookup"><span data-stu-id="ddc90-192">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![STwo 虛擬機器部署到 Azure 虛擬網路和 SharePoint 伺服器陣列子網路是複本網域控制站和 DNS 伺服器](media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="ddc90-194">此圖為基礎的前一個圖表新增至 Windows Server AD 的兩部虛擬機器和 DNS 子網路。</span><span class="sxs-lookup"><span data-stu-id="ddc90-194">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet.</span></span> <span data-ttu-id="ddc90-195">這些虛擬機器是複本網域控制站和 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ddc90-195">These virtual machines are replica domain controllers and DNS servers.</span></span> <span data-ttu-id="ddc90-196">它們是副檔名為內部部署 Windows Server AD 環境。</span><span class="sxs-lookup"><span data-stu-id="ddc90-196">They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="ddc90-197">下表提供這些虛擬機器，在 Azure 中的設定建議。</span><span class="sxs-lookup"><span data-stu-id="ddc90-197">The following table provides configuration recommendations for these virtual machines in Azure.</span></span> <span data-ttu-id="ddc90-198">供您自己的環境中使用這些做為起點 — 提供充足的儲存您的 Azure 環境不會與您的內部部署環境通訊的地方專用網域。</span><span class="sxs-lookup"><span data-stu-id="ddc90-198">Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="ddc90-199">**項目**</span><span class="sxs-lookup"><span data-stu-id="ddc90-199">**Item**</span></span>|<span data-ttu-id="ddc90-200">**設定**</span><span class="sxs-lookup"><span data-stu-id="ddc90-200">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ddc90-201">在 Azure 中的虛擬機器大小</span><span class="sxs-lookup"><span data-stu-id="ddc90-201">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="ddc90-202">在標準層中的 A1 或 A2 大小</span><span class="sxs-lookup"><span data-stu-id="ddc90-202">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="ddc90-203">作業系統</span><span class="sxs-lookup"><span data-stu-id="ddc90-203">Operating system</span></span>  <br/> |<span data-ttu-id="ddc90-204">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ddc90-204">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="ddc90-205">Active Directory 角色</span><span class="sxs-lookup"><span data-stu-id="ddc90-205">Active Directory role</span></span>  <br/> |<span data-ttu-id="ddc90-206">AD DS 網域控制站指定為通用類別目錄伺服器。</span><span class="sxs-lookup"><span data-stu-id="ddc90-206">AD DS domain controller designated as a global catalog server.</span></span> <span data-ttu-id="ddc90-207">此設定可透過跨單位連線減少輸出流量。</span><span class="sxs-lookup"><span data-stu-id="ddc90-207">This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="ddc90-208">在多網域率較高的變更 （這並不常見） 環境中，設定網域控制站上未提供給同步處理與 Azure，以減少複寫流量中的通用類別目錄伺服器的內部部署。</span><span class="sxs-lookup"><span data-stu-id="ddc90-208">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="ddc90-209">DNS 角色</span><span class="sxs-lookup"><span data-stu-id="ddc90-209">DNS role</span></span>  <br/> |<span data-ttu-id="ddc90-210">安裝及設定的網域控制站上的 DNS 伺服器服務。</span><span class="sxs-lookup"><span data-stu-id="ddc90-210">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="ddc90-211">資料磁碟</span><span class="sxs-lookup"><span data-stu-id="ddc90-211">Data disks</span></span>  <br/> |<span data-ttu-id="ddc90-212">將 Active Directory 資料庫、 記錄檔及 SYSVOL 放在其他的 Azure 資料磁碟上。</span><span class="sxs-lookup"><span data-stu-id="ddc90-212">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks.</span></span> <span data-ttu-id="ddc90-213">不放置這些作業系統的磁碟或 Azure 所提供的暫存磁碟上。</span><span class="sxs-lookup"><span data-stu-id="ddc90-213">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="ddc90-214">IP 位址</span><span class="sxs-lookup"><span data-stu-id="ddc90-214">IP addresses</span></span>  <br/> |<span data-ttu-id="ddc90-215">使用靜態 IP 位址，並設定已設定網域控制站之後，將這些位址指派給虛擬網路中的虛擬機器的虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ddc90-215">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="ddc90-216">部署在 Azure 中的 Active Directory 之前，請閱讀[部署 Windows Server Active Directory Azure 虛擬機器上的指導方針](https://go.microsoft.com/fwlink/p/?linkid=392681)。</span><span class="sxs-lookup"><span data-stu-id="ddc90-216">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681).</span></span> <span data-ttu-id="ddc90-217">這些協助您判斷解決方案需要不同的架構或不同的組態設定。</span><span class="sxs-lookup"><span data-stu-id="ddc90-217">These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="ddc90-218">新增 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="ddc90-218">Add the SharePoint farm</span></span>

<span data-ttu-id="ddc90-219">在適當的子網路上的層級中放置在 SharePoint 伺服器陣列的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="ddc90-219">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="ddc90-220">**圖 4： 位置的 SharePoint 虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="ddc90-220">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![資料庫伺服器和 SharePoint 伺服器角色加入 SharePoint 伺服器陣列子網路內的 Azure 虛擬網路](media/AZarch-SPVMsinCloudSer.png)
  
<span data-ttu-id="ddc90-222">此圖為基礎的前一個圖表在其各自的層級中加入 SharePoint 伺服器陣列伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="ddc90-222">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="ddc90-223">兩部執行 SQL Server 資料庫虛擬機器建立的資料庫層。</span><span class="sxs-lookup"><span data-stu-id="ddc90-223">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="ddc90-224">下列各層的每個執行 SharePoint Server 2013 的兩部虛擬機器： 前端伺服器、 分散式快取伺服器及後端伺服器。</span><span class="sxs-lookup"><span data-stu-id="ddc90-224">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="ddc90-225">設計並微調可用性設定組 」 和 「 容錯網域的伺服器角色</span><span class="sxs-lookup"><span data-stu-id="ddc90-225">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="ddc90-226">容錯網域是硬體的一種執行哪些角色執行個體中。</span><span class="sxs-lookup"><span data-stu-id="ddc90-226">A fault domain is a grouping of hardware in which role instances run.</span></span> <span data-ttu-id="ddc90-227">在相同的容錯網域內的虛擬機器可以由 Azure 基礎結構更新在同一時間。</span><span class="sxs-lookup"><span data-stu-id="ddc90-227">Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time.</span></span> <span data-ttu-id="ddc90-228">或者，可以在同一時間中失敗，因為它們會共用相同的機架。</span><span class="sxs-lookup"><span data-stu-id="ddc90-228">Or, they can fail at the same time because they share the same rack.</span></span> <span data-ttu-id="ddc90-229">若要避免相同的容錯網域上具有兩部虛擬機器的風險，您可以設定您的虛擬機器的可用性設定組，這可確保每部虛擬機器位於不同的容錯網域為。</span><span class="sxs-lookup"><span data-stu-id="ddc90-229">To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain.</span></span> <span data-ttu-id="ddc90-230">如果三部虛擬機器設定為一個可用性設定組，可確保 Azure 不超過兩個虛擬機器都位於相同的容錯網域。</span><span class="sxs-lookup"><span data-stu-id="ddc90-230">If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="ddc90-231">當您設計的 SharePoint 伺服器陣列的 Azure 架構時，設定相同的伺服器角色是一個可用性設定組的一部分。</span><span class="sxs-lookup"><span data-stu-id="ddc90-231">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set.</span></span> <span data-ttu-id="ddc90-232">這可確保您的虛擬機器會散佈於多個容錯網域。</span><span class="sxs-lookup"><span data-stu-id="ddc90-232">This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="ddc90-233">**圖 5： 使用 Azure 可用性設定組以提供高可用性 SharePoint 伺服器陣列層級**</span><span class="sxs-lookup"><span data-stu-id="ddc90-233">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![Azure 基礎結構中針對 SharePoint 2013 解決方案的可用性設定組設定](media/AZenv-WinAzureAvailSetsHA.png)
  
<span data-ttu-id="ddc90-235">此圖呼叫出 Azure 基礎結構內的可用性設定組的設定。</span><span class="sxs-lookup"><span data-stu-id="ddc90-235">This diagram calls out the configuration of availability sets within the Azure infrastructure.</span></span> <span data-ttu-id="ddc90-236">下列角色的每個共用個別的可用性設定組：</span><span class="sxs-lookup"><span data-stu-id="ddc90-236">Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="ddc90-237">Active Directory 和 DNS</span><span class="sxs-lookup"><span data-stu-id="ddc90-237">Active Directory and DNS</span></span>
    
- <span data-ttu-id="ddc90-238">Database</span><span class="sxs-lookup"><span data-stu-id="ddc90-238">Database</span></span>
    
- <span data-ttu-id="ddc90-239">後端</span><span class="sxs-lookup"><span data-stu-id="ddc90-239">Back end</span></span>
    
- <span data-ttu-id="ddc90-240">發佈快取</span><span class="sxs-lookup"><span data-stu-id="ddc90-240">Distribute cache</span></span>
    
- <span data-ttu-id="ddc90-241">前端</span><span class="sxs-lookup"><span data-stu-id="ddc90-241">Front end</span></span>
    
<span data-ttu-id="ddc90-242">在 SharePoint 伺服器陣列可能需要為正常調整 Azure 的平台] 中。</span><span class="sxs-lookup"><span data-stu-id="ddc90-242">The SharePoint farm might need to be fine tuned in the Azure platform.</span></span> <span data-ttu-id="ddc90-243">若要確保所有元件的高可用性，請確定該伺服器角色的所有設定都相同。</span><span class="sxs-lookup"><span data-stu-id="ddc90-243">To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="ddc90-244">以下是範例會顯示標準的網際網路網站架構符合特定容量和效能目標。</span><span class="sxs-lookup"><span data-stu-id="ddc90-244">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals.</span></span> <span data-ttu-id="ddc90-245">本範例精選，下列的架構模型： [SharePoint Server 2013 的網際網路網站搜尋架構](https://go.microsoft.com/fwlink/p/?LinkId=261519)。</span><span class="sxs-lookup"><span data-stu-id="ddc90-245">This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="ddc90-246">**圖 6： 規劃在三層式伺服器陣列中的容量和效能目標的範例**</span><span class="sxs-lookup"><span data-stu-id="ddc90-246">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![標準 SharePoint 2013 Internet Sites 架構具有符合特定容量和效能目標的元件配置](media/AZarch-CapPerfexmpArch.png)
  
<span data-ttu-id="ddc90-248">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="ddc90-248">In this diagram:</span></span>
  
- <span data-ttu-id="ddc90-249">在三層式伺服器陣列都以表示： 網頁伺服器、 應用程式伺服器與資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="ddc90-249">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="ddc90-250">三個網頁伺服器進行完全相同設定了多個元件。</span><span class="sxs-lookup"><span data-stu-id="ddc90-250">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="ddc90-251">兩部資料庫伺服器的設定都相同。</span><span class="sxs-lookup"><span data-stu-id="ddc90-251">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="ddc90-252">三個應用程式伺服器，未設定相同。</span><span class="sxs-lookup"><span data-stu-id="ddc90-252">The three application servers are not configured identically.</span></span> <span data-ttu-id="ddc90-253">這些伺服器角色需要在 Azure 中的可用性微調設定。</span><span class="sxs-lookup"><span data-stu-id="ddc90-253">These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="ddc90-254">讓我們看接近應用程式伺服器層級。</span><span class="sxs-lookup"><span data-stu-id="ddc90-254">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="ddc90-255">**圖 7： 應用程式伺服器層之前微調**</span><span class="sxs-lookup"><span data-stu-id="ddc90-255">**Figure 7: Application server tier before fine tuning**</span></span>

![調整為 Microsoft Azure 可用性設定組之前的 SharePoint Server 2013 應用程式伺服器層範例](media/AZarch-AppServtierBefore.png)
  
<span data-ttu-id="ddc90-257">在此圖表中：</span><span class="sxs-lookup"><span data-stu-id="ddc90-257">In this diagram:</span></span>
  
- <span data-ttu-id="ddc90-258">三部伺服器都包含在應用程式層。</span><span class="sxs-lookup"><span data-stu-id="ddc90-258">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="ddc90-259">第一部伺服器包含四個元件。</span><span class="sxs-lookup"><span data-stu-id="ddc90-259">The first server includes four components.</span></span>
    
- <span data-ttu-id="ddc90-260">第二個伺服器包含三個元件。</span><span class="sxs-lookup"><span data-stu-id="ddc90-260">The second server includes three components.</span></span>
    
- <span data-ttu-id="ddc90-261">第三個伺服器包含兩個元件。</span><span class="sxs-lookup"><span data-stu-id="ddc90-261">The third server includes two components.</span></span>
    
<span data-ttu-id="ddc90-262">您決定伺服器陣列的效能與容量目標的元件數目。</span><span class="sxs-lookup"><span data-stu-id="ddc90-262">You determine the number of components by the performance and capacity targets for the farm.</span></span> <span data-ttu-id="ddc90-263">Azure 能否這種架構，我們將所有的三部伺服器上複寫的四個元件。</span><span class="sxs-lookup"><span data-stu-id="ddc90-263">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="ddc90-264">這會增加以外的功能所需的效能與容量的元件數目。</span><span class="sxs-lookup"><span data-stu-id="ddc90-264">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="ddc90-265">缺點是這種設計可確保當這些三部虛擬機器會指派給一個可用性設定組 Azure 的平台] 中的所有四個元件的高可用性。</span><span class="sxs-lookup"><span data-stu-id="ddc90-265">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="ddc90-266">**圖 8： 應用程式伺服器層後微調**</span><span class="sxs-lookup"><span data-stu-id="ddc90-266">**Figure 8: Application server tier after fine tuning**</span></span>

![調整為 Microsoft Azure 可用性設定組之後的 SharePoint Server 2013 應用程式伺服器層範例](media/AZarch-AppServtierAfter.png)
  
<span data-ttu-id="ddc90-268">這個圖表顯示所有三個應用程式伺服器都設定具有相同的四個元件。</span><span class="sxs-lookup"><span data-stu-id="ddc90-268">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="ddc90-269">當我們將可用性設定組新增至 SharePoint 伺服器陣列層級時，實作已完成。</span><span class="sxs-lookup"><span data-stu-id="ddc90-269">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="ddc90-270">**圖 9： 完成的 SharePoint 伺服器陣列在 Azure 基礎結構服務中**</span><span class="sxs-lookup"><span data-stu-id="ddc90-270">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![Azure Infrastructure Services 中的 SharePoint 2013 伺服器陣列以及虛擬網路、跨單位連線能力、子網路、VM 以及可用性設定組的範例 ](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="ddc90-272">此圖顯示實作在 Azure 基礎結構服務中，以提供容錯網域中每一層的伺服器的可用性設定組與 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="ddc90-272">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
<span data-ttu-id="ddc90-273">**參與討論**</span><span class="sxs-lookup"><span data-stu-id="ddc90-273">**Join the discussion**</span></span>

|<span data-ttu-id="ddc90-274">**連絡我們**</span><span class="sxs-lookup"><span data-stu-id="ddc90-274">**Contact us**</span></span>|<span data-ttu-id="ddc90-275">**描述**</span><span class="sxs-lookup"><span data-stu-id="ddc90-275">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="ddc90-276">**您需要什麼樣的雲端採用內容？**</span><span class="sxs-lookup"><span data-stu-id="ddc90-276">**What cloud adoption content do you need?**</span></span> <br/> |<span data-ttu-id="ddc90-p133">我們正在建立涵蓋多個 Microsoft 雲端平台及服務的雲端採用內容。請傳送電子郵件至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20)，讓我們知道您對雲端採用內容的看法或對特定內容的要求。</span><span class="sxs-lookup"><span data-stu-id="ddc90-p133">We are creating content for cloud adoption that spans multiple Microsoft cloud platforms and services. Let us know what you think about our cloud adoption content, or ask for specific content by sending email to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?Subject=[Cloud%20Adoption%20Content%20Feedback]:%20).  </span></span><br/> |
|<span data-ttu-id="ddc90-279">**加入雲端採用討論**</span><span class="sxs-lookup"><span data-stu-id="ddc90-279">**Join the cloud adoption discussion**</span></span> <br/> |<span data-ttu-id="ddc90-280">如果您熱愛雲端解決方案，請考慮加入雲端採用諮詢委員會 (Cloud Adoption Advisory Board，CAAB) 與更大且活躍的 Microsoft 內容開發人員、產業專業人員及客戶社群接觸。</span><span class="sxs-lookup"><span data-stu-id="ddc90-280">If you are passionate about cloud-based solutions, consider joining the Cloud Adoption Advisory Board (CAAB) to connect with a larger, vibrant community of Microsoft content developers, industry professionals, and customers from around the globe.</span></span> <span data-ttu-id="ddc90-281">若要加入，將自己新增為 Microsoft 技術社群的[CAAB （雲端採用諮詢委員會） 空間](https://aka.ms/caab)的成員，並在[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!)快速的電子郵件傳送給我們。</span><span class="sxs-lookup"><span data-stu-id="ddc90-281">To join, add yourself as a member of the [CAAB (Cloud Adoption Advisory Board) space](https://aka.ms/caab) of the Microsoft Tech Community and send us a quick email at[CAAB@microsoft.com](mailto:caab@microsoft.com?Subject=I%20just%20joined%20the%20Cloud%20Adoption%20Advisory%20Board!).</span></span> <span data-ttu-id="ddc90-282">任何人都可以讀取[CAAB 部落格](https://blogs.technet.com/b/solutions_advisory_board/)上的社群相關內容。</span><span class="sxs-lookup"><span data-stu-id="ddc90-282">Anyone can read community-related content on the [CAAB blog](https://blogs.technet.com/b/solutions_advisory_board/).</span></span> <span data-ttu-id="ddc90-283">不過，CAAB 成員可獲得雲端採用資源和解決方案說明的私人網路研討會邀請。</span><span class="sxs-lookup"><span data-stu-id="ddc90-283">However, CAAB members get invitations to private webinars that describe new cloud adoption resources and solutions.</span></span>  <br/> |
|<span data-ttu-id="ddc90-284">**取得您在這裡看到的美工圖案**</span><span class="sxs-lookup"><span data-stu-id="ddc90-284">**Get the art you see here**</span></span> <br/> |<span data-ttu-id="ddc90-p135">如果您想要此文章中所看到之美工圖案的可編輯複本，我們很樂於將它傳送給您。請以電子郵件將您的要求 (包括美工圖案的 URL 和標題) 傳送至 [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20)。</span><span class="sxs-lookup"><span data-stu-id="ddc90-p135">If you want an editable copy of the art you see in this article, we'll be glad to send it to you. Email your request, including the URL and title of the art, to [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com?subject=[Art%20Request]:%20).  </span></span><br/> |
   
## <a name="see-also"></a><span data-ttu-id="ddc90-287">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddc90-287">See Also</span></span>

[<span data-ttu-id="ddc90-288">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="ddc90-288">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="ddc90-289">Microsoft Azure 中使用 SharePoint Server 2013 的網際網路網站</span><span class="sxs-lookup"><span data-stu-id="ddc90-289">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="ddc90-290">Microsoft Azure 中的 SharePoint Server 2013 災害復原</span><span class="sxs-lookup"><span data-stu-id="ddc90-290">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


