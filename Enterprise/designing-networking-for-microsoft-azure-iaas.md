---
title: 設計 Microsoft Azure IaaS 的網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 摘要： 了解如何設計的 Microsoft Azure IaaS 中的工作負載最佳化的網路。
ms.openlocfilehash: 0e7af14768aa1a21548b25a20a465b644b749f3e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915118"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="36bff-103">設計 Microsoft Azure IaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="36bff-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="36bff-104">**摘要：** 了解如何設計的 Microsoft Azure IaaS 中的工作負載最佳化的網路。</span><span class="sxs-lookup"><span data-stu-id="36bff-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="36bff-105">最佳化網路的 IT 工作量架設在 Azure IaaS 需要瞭解 Azure 虛擬網路 (VNets) 地址空格、 路由、 DNS、 和負載平衡。</span><span class="sxs-lookup"><span data-stu-id="36bff-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="36bff-106">規劃步驟任何 VNet</span><span class="sxs-lookup"><span data-stu-id="36bff-106">Planning steps for any VNet</span></span>

<span data-ttu-id="36bff-107">任何類型的 VNet 遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="36bff-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="36bff-108">步驟 1： 準備您的內部網路的 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="36bff-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="36bff-109">經歷中[常見的元素 Microsoft cloud 連線的](common-elements-of-microsoft-cloud-connectivity.md)**步驟來準備您的 Microsoft 雲端服務的網路**區段。</span><span class="sxs-lookup"><span data-stu-id="36bff-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="36bff-110">步驟 2： 最佳化您的網際網路頻寬。</span><span class="sxs-lookup"><span data-stu-id="36bff-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="36bff-111">最佳化您的網際網路頻寬使用中[設計的 Microsoft saas 和網路](designing-networking-for-microsoft-saas.md)的**步驟來準備您的網路 Microsoft saas 和服務的**一節的步驟 2 到 4。</span><span class="sxs-lookup"><span data-stu-id="36bff-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="36bff-112">步驟 3： 判斷 VNet 類型 (僅限雲端或跨部門)。</span><span class="sxs-lookup"><span data-stu-id="36bff-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="36bff-p101">僅限雲端 VNet 有未連線至內部網路。以下是範例。</span><span class="sxs-lookup"><span data-stu-id="36bff-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="36bff-115">**圖 1： 僅限雲端 VNet**</span><span class="sxs-lookup"><span data-stu-id="36bff-115">**Figure 1: A cloud-only VNet**</span></span>

![圖 1：Azure 中只存在於雲端的虛擬網路](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="36bff-117">圖 1 顯示虛擬機器的一的組中僅限雲端 VNet。</span><span class="sxs-lookup"><span data-stu-id="36bff-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="36bff-p102">A 跨部署 VNet 具有至網站 (S2S) 透過 Azure 閘道的內部網路的 VPN 或 ExpressRoute 連線。以下是範例。</span><span class="sxs-lookup"><span data-stu-id="36bff-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="36bff-120">**圖 2： 跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="36bff-120">**Figure 2: A cross-premises VNet**</span></span>

![圖 2：Azure 中跨部署的虛擬網路](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="36bff-122">圖 2 顯示一組的虛擬機器在跨部署 VNet，連線至內部網路中。</span><span class="sxs-lookup"><span data-stu-id="36bff-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="36bff-123">請參閱其他本文中[的跨單位 VNet 的規劃步驟](designing-networking-for-microsoft-azure-iaas.md#cross_prem)一節。</span><span class="sxs-lookup"><span data-stu-id="36bff-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="36bff-124">步驟 4： 決定 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="36bff-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="36bff-125">表 1 顯示的位址空間 VNets 不同類型。</span><span class="sxs-lookup"><span data-stu-id="36bff-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="36bff-126">**VNet 的類型**</span><span class="sxs-lookup"><span data-stu-id="36bff-126">**Type of VNet**</span></span>|<span data-ttu-id="36bff-127">**虛擬網路位址空間**</span><span class="sxs-lookup"><span data-stu-id="36bff-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="36bff-128">僅雲端</span><span class="sxs-lookup"><span data-stu-id="36bff-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="36bff-129">任意私人位址空間</span><span class="sxs-lookup"><span data-stu-id="36bff-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="36bff-130">僅限雲端彼此互相</span><span class="sxs-lookup"><span data-stu-id="36bff-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="36bff-131">任意私人，但不是重疊與其他連線 VNets</span><span class="sxs-lookup"><span data-stu-id="36bff-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="36bff-132">跨單位</span><span class="sxs-lookup"><span data-stu-id="36bff-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="36bff-133">私人，但不是重疊與內部部署</span><span class="sxs-lookup"><span data-stu-id="36bff-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="36bff-134">互連的跨部署</span><span class="sxs-lookup"><span data-stu-id="36bff-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="36bff-135">私人，但不是重疊與內部部署與其他連線 VNets</span><span class="sxs-lookup"><span data-stu-id="36bff-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="36bff-136">**表 1： 類型的 VNets 和其對應的位址空間**</span><span class="sxs-lookup"><span data-stu-id="36bff-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="36bff-137">虛擬機器時的 DHCP 指派之子網路的位址空間的地址組態：</span><span class="sxs-lookup"><span data-stu-id="36bff-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="36bff-138">位址/子網路遮罩</span><span class="sxs-lookup"><span data-stu-id="36bff-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="36bff-139">預設閘道</span><span class="sxs-lookup"><span data-stu-id="36bff-139">Default gateway</span></span>
    
- <span data-ttu-id="36bff-140">DNS 伺服器 IP 位址</span><span class="sxs-lookup"><span data-stu-id="36bff-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="36bff-141">您也可以保留靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="36bff-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="36bff-142">虛擬機器可以也指派公用 IP 位址，個別或從包含雲端服務 （適用於僅限傳統部署機器）。</span><span class="sxs-lookup"><span data-stu-id="36bff-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="36bff-143">步驟 5： 決定 VNet 和指派給每個位址空間內的子網路。</span><span class="sxs-lookup"><span data-stu-id="36bff-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="36bff-144">有兩種類型的子網路中 VNet、 閘道子網路和虛擬機器裝載的子網路。</span><span class="sxs-lookup"><span data-stu-id="36bff-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="36bff-145">**圖 3：Azure 中的兩種子網路類型**</span><span class="sxs-lookup"><span data-stu-id="36bff-145">**Figure 3: The two types of subnets in Azure**</span></span>

![圖 3：Azure 中的兩種子網路類型](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="36bff-147">圖 3 是含有包含 Azure 閘道與一組的虛擬機器裝載含有虛擬機器時的子網路的閘道子網路 VNet。</span><span class="sxs-lookup"><span data-stu-id="36bff-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="36bff-p103">Azure 閘道子網路會需要 Azure 主控兩個虛擬機器的 Azure 的閘道。使用至少 29 位元前置詞長度指定位址空間 (範例： 192.168.15.248/29)。建議的 28 位元或較小的前置詞長度，特別是如果您打算使用 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="36bff-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="36bff-151">決定 Azure 閘道子網路的位址空間的最佳作法是下列：</span><span class="sxs-lookup"><span data-stu-id="36bff-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="36bff-152">決定閘道子網路的大小。</span><span class="sxs-lookup"><span data-stu-id="36bff-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="36bff-153">VNet 的位址空間中變數的位元，設為 0 的閘道子網路所使用的位元，並將剩餘的位元設定為 1。</span><span class="sxs-lookup"><span data-stu-id="36bff-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="36bff-154">轉換成十進位和 express 位址空間為具有前置詞長度設為閘道子網路的大小。</span><span class="sxs-lookup"><span data-stu-id="36bff-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="36bff-155">使用此方法之後，閘道子網路的位址空間一律為結尾處的最遠 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="36bff-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="36bff-p104">以下是定義閘道子網路的地址前置字的範例： VNet 位址空間是 10.119.0.0/16。組織一開始會使用網站 VPN 連線，但將最後取得 ExpressRoute。表 2 顯示的步驟及決定閘道的子網路位址前置詞的網路前置詞表示法 (也稱為 CIDR) 的結果。</span><span class="sxs-lookup"><span data-stu-id="36bff-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="36bff-159">以下是步驟與範例判斷閘道的子網路位址前置詞：</span><span class="sxs-lookup"><span data-stu-id="36bff-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="36bff-p105">決定閘道子網路的大小。用於此範例中，我們在 [選擇 /28。</span><span class="sxs-lookup"><span data-stu-id="36bff-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="36bff-p106">設定位元 VNet 位址空間 (b) 的可變部分為 0 閘道的子網路位元 (G)，否則為 1 (V)。我們的範例中，我們使用 10.119.0.0/16 位址空間的 VNet。</span><span class="sxs-lookup"><span data-stu-id="36bff-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="36bff-p107">10.119。 bbbbbbbb。bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="36bff-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="36bff-p108">10.119。 VVVVVVVV。VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="36bff-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="36bff-p109">10.119。 11111111。11110000</span><span class="sxs-lookup"><span data-stu-id="36bff-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="36bff-p110">步驟 2 的結果轉換成十進位和 express 為位址空間。例如我們 10.119。11111111。11110000 是 10.119.255.240，並從步驟 1，(在我們的範例 28) 前置詞長度] 中，所產生的閘道的子網路位址首碼是 10.119.255.240/28。</span><span class="sxs-lookup"><span data-stu-id="36bff-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="36bff-177">如需詳細資訊，請參閱[Azure 閘道的子網路的位址空間計算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。</span><span class="sxs-lookup"><span data-stu-id="36bff-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="36bff-178">虛擬機器裝載的子網路會放置 Azure 虛擬機器，您可以根據內部一般指導方針，例如一般角色或應用程式或子網路隔離層中執行的位置。</span><span class="sxs-lookup"><span data-stu-id="36bff-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="36bff-p111">Azure 每個子網路上使用的前 3 的地址。因此，可能 Azure 的子網路上的地址的數目是 2<sup>n</sup> -5、 其中 n 是主機位元數。表 3 顯示的虛擬機器時所需、 數目範圍主控需要的位元和相對應的子網路大小。</span><span class="sxs-lookup"><span data-stu-id="36bff-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="36bff-182">**所需的虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="36bff-182">**Virtual machines required**</span></span>|<span data-ttu-id="36bff-183">**主機位元**</span><span class="sxs-lookup"><span data-stu-id="36bff-183">**Host bits**</span></span>|<span data-ttu-id="36bff-184">**子網路大小**</span><span class="sxs-lookup"><span data-stu-id="36bff-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="36bff-185">1-3</span><span class="sxs-lookup"><span data-stu-id="36bff-185">1-3</span></span>  <br/> |<span data-ttu-id="36bff-186">3</span><span class="sxs-lookup"><span data-stu-id="36bff-186">3</span></span>  <br/> |<span data-ttu-id="36bff-187">/29</span><span class="sxs-lookup"><span data-stu-id="36bff-187">/29</span></span>  <br/> |
|<span data-ttu-id="36bff-188">4-11</span><span class="sxs-lookup"><span data-stu-id="36bff-188">4-11</span></span>  <br/> |<span data-ttu-id="36bff-189">4</span><span class="sxs-lookup"><span data-stu-id="36bff-189">4</span></span>  <br/> |<span data-ttu-id="36bff-190">/28</span><span class="sxs-lookup"><span data-stu-id="36bff-190">/28</span></span>  <br/> |
|<span data-ttu-id="36bff-191">12-27</span><span class="sxs-lookup"><span data-stu-id="36bff-191">12-27</span></span>  <br/> |<span data-ttu-id="36bff-192">5</span><span class="sxs-lookup"><span data-stu-id="36bff-192">5</span></span>  <br/> |<span data-ttu-id="36bff-193">/27</span><span class="sxs-lookup"><span data-stu-id="36bff-193">/27</span></span>  <br/> |
|<span data-ttu-id="36bff-194">28-59</span><span class="sxs-lookup"><span data-stu-id="36bff-194">28-59</span></span>  <br/> |<span data-ttu-id="36bff-195">6</span><span class="sxs-lookup"><span data-stu-id="36bff-195">6</span></span>  <br/> |<span data-ttu-id="36bff-196">/26</span><span class="sxs-lookup"><span data-stu-id="36bff-196">/26</span></span>  <br/> |
|<span data-ttu-id="36bff-197">60-123</span><span class="sxs-lookup"><span data-stu-id="36bff-197">60-123</span></span>  <br/> |<span data-ttu-id="36bff-198">7</span><span class="sxs-lookup"><span data-stu-id="36bff-198">7</span></span>  <br/> |<span data-ttu-id="36bff-199">/25</span><span class="sxs-lookup"><span data-stu-id="36bff-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="36bff-200">**表 3： 虛擬機器的需求和其子網路大小**</span><span class="sxs-lookup"><span data-stu-id="36bff-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="36bff-201">如需虛擬機器上的子網路或 VNet 最大數量的詳細資訊，請參閱[網路限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="36bff-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="36bff-202">如需詳細資訊，請參閱[＜ Plan and design Azure 虛擬網路](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。</span><span class="sxs-lookup"><span data-stu-id="36bff-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="36bff-203">步驟 6： 決定 DNS 伺服器設定和指派給 VNet Vm DNS 伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="36bff-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="36bff-p112">Azure 指派虛擬機器時的 DHCP 的 DNS 伺服器的位址。DNS 伺服器可以是：</span><span class="sxs-lookup"><span data-stu-id="36bff-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="36bff-206">提供由 Azure： 提供本機名稱登錄與本機與網際網路名稱解析</span><span class="sxs-lookup"><span data-stu-id="36bff-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="36bff-207">提供您： 提供本機或網路名稱登錄與內部網路或網際網路名稱解析</span><span class="sxs-lookup"><span data-stu-id="36bff-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="36bff-208">表 4 顯示每種類型的 VNet 的 DNS 伺服器的不同設定。</span><span class="sxs-lookup"><span data-stu-id="36bff-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="36bff-209">**VNet 的類型**</span><span class="sxs-lookup"><span data-stu-id="36bff-209">**Type of VNet**</span></span>|<span data-ttu-id="36bff-210">**DNS 伺服器**</span><span class="sxs-lookup"><span data-stu-id="36bff-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="36bff-211">僅雲端</span><span class="sxs-lookup"><span data-stu-id="36bff-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="36bff-212">Azure 提供本機和網際網路名稱解析</span><span class="sxs-lookup"><span data-stu-id="36bff-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="36bff-213">Azure 虛擬機器的本機與網際網路名稱解析 （DNS 轉接）</span><span class="sxs-lookup"><span data-stu-id="36bff-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="36bff-214">跨單位</span><span class="sxs-lookup"><span data-stu-id="36bff-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="36bff-215">在內部的本機與內部網路名稱解析</span><span class="sxs-lookup"><span data-stu-id="36bff-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="36bff-216">Azure 虛擬機器的本機與內部網路名稱解析 （DNS 複寫和轉寄）</span><span class="sxs-lookup"><span data-stu-id="36bff-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="36bff-217">**表 4: VNets 兩種不同類型的 DNS 伺服器選項**</span><span class="sxs-lookup"><span data-stu-id="36bff-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="36bff-218">如需詳細資訊，請參閱[Vm 和角色執行個體的名稱解析](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)。</span><span class="sxs-lookup"><span data-stu-id="36bff-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="36bff-219">步驟 7： 決定負載平衡設定 （網際網路或內部）。</span><span class="sxs-lookup"><span data-stu-id="36bff-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="36bff-p113">在某些情況下，您想要散佈的一組具有相同角色的伺服器到的傳入流量。Azure IaaS 若要這樣做為網際網路對向內建設備且內部流量負載。</span><span class="sxs-lookup"><span data-stu-id="36bff-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="36bff-222">Azure 的網際網路對向負載平衡隨機分散每個來路不明傳入流量從網際網路到負載平衡的一組的成員。</span><span class="sxs-lookup"><span data-stu-id="36bff-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="36bff-223">**圖 4：Azure 中的外部負載平衡器**</span><span class="sxs-lookup"><span data-stu-id="36bff-223">**Figure 4: An external load balancer in Azure**</span></span>

![圖 4：Azure 中的外部負載平衡器](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="36bff-225">圖 4 顯示分散每個撥入的 NAT 規則或一組負載平衡集內的虛擬機器時的端點上的內送流量的 Azure 中的外部負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="36bff-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="36bff-226">Azure 內部的負載平衡隨機分散每個來自其他 Azure Vm 或從內部網路負載平衡的一組的成員電腦的來路不明傳入流量。</span><span class="sxs-lookup"><span data-stu-id="36bff-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="36bff-227">**圖 5：Azure 中的內部負載平衡器**</span><span class="sxs-lookup"><span data-stu-id="36bff-227">**Figure 5: An internal load balancer in Azure**</span></span>

![圖 5：Azure 中的內部負載平衡器](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="36bff-229">圖 5 顯示分散每個撥入的 NAT 規則或一組負載平衡集內的虛擬機器時的端點上的內送流量的 Azure 中的內部負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="36bff-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="36bff-230">如需詳細資訊，請參閱[Azure 負載平衡器](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)。</span><span class="sxs-lookup"><span data-stu-id="36bff-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="36bff-231">步驟 8： 決定使用虛擬設備和使用者定義的路由。</span><span class="sxs-lookup"><span data-stu-id="36bff-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="36bff-232">如果您需要轉寄至虛擬設備中您 VNet 流量，您可能需要將一或多個使用者定義的路由新增至子網路。</span><span class="sxs-lookup"><span data-stu-id="36bff-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="36bff-233">**圖 6：Azure 中的虛擬設備和使用者定義路由**</span><span class="sxs-lookup"><span data-stu-id="36bff-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![圖 6：Azure 中的虛擬設備和使用者定義路由](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="36bff-235">圖 6 顯示跨部署 VNet 和使用者定義的路由指派給指向虛擬 appliance 的虛擬機器裝載子網路。</span><span class="sxs-lookup"><span data-stu-id="36bff-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="36bff-236">如需詳細資訊，請參閱[使用者定義的路由和 IP 轉寄](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。</span><span class="sxs-lookup"><span data-stu-id="36bff-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="36bff-237">步驟 9： 決定如何從網際網路的電腦會連線至虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="36bff-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="36bff-238">有多個提供存取網際網路才能虛擬機器上 VNet，其中包含從您組織的網路透過 proxy 伺服器或其他 edge 裝置存取的方式。</span><span class="sxs-lookup"><span data-stu-id="36bff-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="36bff-239">表 5 列出篩選或檢查來路不明的傳入流量的方法。</span><span class="sxs-lookup"><span data-stu-id="36bff-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="36bff-240">**方法**</span><span class="sxs-lookup"><span data-stu-id="36bff-240">**Method**</span></span>|<span data-ttu-id="36bff-241">**部署模型**</span><span class="sxs-lookup"><span data-stu-id="36bff-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="36bff-242">1.端點和雲端服務上設定的 Acl</span><span class="sxs-lookup"><span data-stu-id="36bff-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="36bff-243">傳統</span><span class="sxs-lookup"><span data-stu-id="36bff-243">Classic</span></span>  <br/> |
|<span data-ttu-id="36bff-244">2.網路安全性群組</span><span class="sxs-lookup"><span data-stu-id="36bff-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="36bff-245">資源管理員與傳統</span><span class="sxs-lookup"><span data-stu-id="36bff-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="36bff-246">3.網際網路對向的負載平衡器以輸入 NAT 規則</span><span class="sxs-lookup"><span data-stu-id="36bff-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="36bff-247">資源管理員</span><span class="sxs-lookup"><span data-stu-id="36bff-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="36bff-248">4.網路安全性設備中 （不會顯示） Azure Marketplace</span><span class="sxs-lookup"><span data-stu-id="36bff-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="36bff-249">資源管理員與傳統</span><span class="sxs-lookup"><span data-stu-id="36bff-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="36bff-250">**連線至虛擬機器和其對應的 Azure 部署模型的表 5： 方法**</span><span class="sxs-lookup"><span data-stu-id="36bff-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="36bff-251">**圖 7：透過網際網路連線到 Azure 虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="36bff-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![圖 7：透過網際網路連線到 Azure 虛擬機器](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="36bff-253">圖 7 顯示網際網路連線的電腦連線至虛擬機器使用端點的雲端服務、 使用網路安全性] 群組中，將子網路上的虛擬機器及虛擬機器上使用外部負載平衡器和撥入的 NAT 規則的子網路。</span><span class="sxs-lookup"><span data-stu-id="36bff-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="36bff-254">提供其他安全性：</span><span class="sxs-lookup"><span data-stu-id="36bff-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="36bff-255">遠端桌面和 SSH 連線，這會驗證與加密。</span><span class="sxs-lookup"><span data-stu-id="36bff-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="36bff-256">遠端 PowerShell 工作階段，這會驗證與加密。</span><span class="sxs-lookup"><span data-stu-id="36bff-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="36bff-257">IPsec 傳輸模式，您可以使用端對端加密。</span><span class="sxs-lookup"><span data-stu-id="36bff-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="36bff-258">Azure DDOS 保護，有助於防止外部和內部攻擊</span><span class="sxs-lookup"><span data-stu-id="36bff-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="36bff-259">如需詳細資訊，請參閱[Microsoft 雲端 Security for Enterprise 架構師](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="36bff-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="36bff-260">步驟 10： 針對多個 VNets 決定 VNet-VNet 連線拓撲。</span><span class="sxs-lookup"><span data-stu-id="36bff-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="36bff-261">VNets 可以使用類似用來連接組織的站台的拓撲彼此進行連線。</span><span class="sxs-lookup"><span data-stu-id="36bff-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="36bff-262">雛菊鏈結設定連接中一系列 VNets。</span><span class="sxs-lookup"><span data-stu-id="36bff-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="36bff-263">**圖 8： Daisy 鏈結設定 VNets**</span><span class="sxs-lookup"><span data-stu-id="36bff-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![圖 8：Azure 虛擬網路的菊輪鍊設定](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="36bff-265">圖 8 顯示五個 VNets 連線使用 daisy 鏈結組態的數列。</span><span class="sxs-lookup"><span data-stu-id="36bff-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="36bff-266">支點和中樞設定連線至中央 VNets，連線至彼此本身是一組多個 VNets。</span><span class="sxs-lookup"><span data-stu-id="36bff-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="36bff-267">**圖 9： 支點和中樞設定 VNets**</span><span class="sxs-lookup"><span data-stu-id="36bff-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![圖 9：Azure 虛擬網路的輪輻和中樞設定](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="36bff-269">圖 9 顯示六個 VNets 兩個 VNets 連接至彼此和也兩個其他支點 VNets 的集線器。</span><span class="sxs-lookup"><span data-stu-id="36bff-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="36bff-270">完整網狀設定連接至彼此的每個 VNet。</span><span class="sxs-lookup"><span data-stu-id="36bff-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="36bff-271">**圖 10： 完整網狀結構 VNets 組態**</span><span class="sxs-lookup"><span data-stu-id="36bff-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![圖 10：Azure 虛擬網路的網狀設定](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="36bff-273">圖 10 說明四種 VNets 連接至彼此、 使用六個 VNet-VNet 連線的總。</span><span class="sxs-lookup"><span data-stu-id="36bff-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="36bff-274">跨部署 VNet 的規劃步驟</span><span class="sxs-lookup"><span data-stu-id="36bff-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="36bff-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="36bff-275"></span></span>

<span data-ttu-id="36bff-276">針對跨部署 VNet 遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="36bff-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="36bff-277">若要建立模擬的跨部署的開發人員/測試環境，請參閱[Simulated 跨部署在 Azure 虛擬網路](simulated-cross-premises-virtual-network-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="36bff-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="36bff-278">步驟 1： 判斷 VNet （S2S VPN 或 ExpressRoute） 跨部署的連線。</span><span class="sxs-lookup"><span data-stu-id="36bff-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="36bff-279">表 6 列出不同類型的連線。</span><span class="sxs-lookup"><span data-stu-id="36bff-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="36bff-280">**連線類型**</span><span class="sxs-lookup"><span data-stu-id="36bff-280">**Type of connection**</span></span>|<span data-ttu-id="36bff-281">**用途**</span><span class="sxs-lookup"><span data-stu-id="36bff-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="36bff-282">若要網站 (S2S) VPN</span><span class="sxs-lookup"><span data-stu-id="36bff-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="36bff-283">以單一 VNet 連線 1-10 網站 （包括其他 VNets）。</span><span class="sxs-lookup"><span data-stu-id="36bff-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="36bff-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="36bff-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="36bff-285">透過網際網路 Exchange 提供者 (IXP) 或網路服務提供者 (NSP) Azure 私人的安全連結。</span><span class="sxs-lookup"><span data-stu-id="36bff-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="36bff-286">若要網站點 (P2S) VPN</span><span class="sxs-lookup"><span data-stu-id="36bff-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="36bff-287">會在單一電腦連線至 VNet。</span><span class="sxs-lookup"><span data-stu-id="36bff-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="36bff-288">VNet 對等或 VNet VNet (V2V) VPN</span><span class="sxs-lookup"><span data-stu-id="36bff-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="36bff-289">連接至另一個 VNet 資訊 VNet。</span><span class="sxs-lookup"><span data-stu-id="36bff-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="36bff-290">**表 6： 連線類型的跨單位 VNets**</span><span class="sxs-lookup"><span data-stu-id="36bff-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="36bff-291">如需詳細的連線數目上限的詳細資訊，請參閱[網路限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="36bff-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="36bff-292">如需 VPN 裝置的詳細資訊，請參閱[網站虛擬網路連線的 VPN 裝置](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="36bff-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="36bff-293">如需 VNet 對等的詳細資訊，請參閱[VNet 對等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。</span><span class="sxs-lookup"><span data-stu-id="36bff-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="36bff-294">**圖 11： 四種方式連線至跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="36bff-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![圖 11：連線到跨部署 Azure 虛擬網路的三種方式](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="36bff-296">圖 11 顯示 VNet 與四種類型的連線： P2S 連線的電腦、 從內部網路 S2S VPN 連線、 從內部網路、 ExpressRoute 連線及來自另一個 VNet VNet-VNet 連線。</span><span class="sxs-lookup"><span data-stu-id="36bff-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="36bff-297">您可以透過下列方式連線至 Vm VNet：</span><span class="sxs-lookup"><span data-stu-id="36bff-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="36bff-298">管理的 VNet Vm 從您的內部網路或網際網路</span><span class="sxs-lookup"><span data-stu-id="36bff-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="36bff-299">從內部網路的 IT 工作量存取</span><span class="sxs-lookup"><span data-stu-id="36bff-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="36bff-300">透過其他 VNets 您網路的延伸模組</span><span class="sxs-lookup"><span data-stu-id="36bff-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="36bff-301">由下列提供連線安全性：</span><span class="sxs-lookup"><span data-stu-id="36bff-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="36bff-302">P2S 使用安全通訊端通訊協定通道通訊協定 (SSTP)</span><span class="sxs-lookup"><span data-stu-id="36bff-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="36bff-303">S2S 和 VNet-VNet VPN 連線會使用 IPsec 通道模式與 AES256</span><span class="sxs-lookup"><span data-stu-id="36bff-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="36bff-304">ExpressRoute 是私人的 WAN 連線</span><span class="sxs-lookup"><span data-stu-id="36bff-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="36bff-305">如需詳細資訊，請參閱[Microsoft 雲端 Security for Enterprise 架構師](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="36bff-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="36bff-306">步驟 2： 決定在內部部署 VPN 裝置或路由器。</span><span class="sxs-lookup"><span data-stu-id="36bff-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="36bff-307">您的內部部署 VPN 裝置或路由器做為：</span><span class="sxs-lookup"><span data-stu-id="36bff-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="36bff-308">終止 Azure 閘道的 S2S VPN 連線 IPsec 等。</span><span class="sxs-lookup"><span data-stu-id="36bff-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="36bff-309">私人的對等 ExpressRoute 連線 BPG 對等和終止點。</span><span class="sxs-lookup"><span data-stu-id="36bff-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="36bff-310">**圖 12：內部部署 VPN 路由器或裝置**</span><span class="sxs-lookup"><span data-stu-id="36bff-310">**Figure 12: The on-premises VPN router or device**</span></span>

![圖 12：內部部署 VPN 路由器或裝置](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="36bff-312">圖 12 顯示跨部署 VNet 連線至內部部署 VPN 路由器或裝置。</span><span class="sxs-lookup"><span data-stu-id="36bff-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="36bff-313">如需詳細資訊，請參閱 ＜[關於 VPN 閘道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)。</span><span class="sxs-lookup"><span data-stu-id="36bff-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="36bff-314">步驟 3： 將路由新增至您的內部網路進行連至 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="36bff-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="36bff-315">從內部部署路由傳送至 VNets 包含下列：</span><span class="sxs-lookup"><span data-stu-id="36bff-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="36bff-316">Points 正面 VPN 裝置 VNet 位址空間的路由。</span><span class="sxs-lookup"><span data-stu-id="36bff-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="36bff-317">在您跨 S2S VPN 或 ExpressRoute 連接點的 VPN 裝置 VNet 位址空間路由</span><span class="sxs-lookup"><span data-stu-id="36bff-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="36bff-318">**圖 13： 內部部署路由所需進行 VNet 連至**</span><span class="sxs-lookup"><span data-stu-id="36bff-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![圖 13：內部部署路由需要讓 Azure VNet 可以連線](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="36bff-320">圖 13 顯示內部路由器和 VPN 路由器或代表 VNet 位址空間的裝置所需的路由資訊。</span><span class="sxs-lookup"><span data-stu-id="36bff-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="36bff-321">步驟 4： ExpressRoute，規劃的提供者的新連線。</span><span class="sxs-lookup"><span data-stu-id="36bff-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="36bff-322">您可以使用私人對等之間的內部網路和 Microsoft cloud 三個不同的方式建立 ExpressRoute 連線：</span><span class="sxs-lookup"><span data-stu-id="36bff-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="36bff-323">共同位於雲端 exchange</span><span class="sxs-lookup"><span data-stu-id="36bff-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="36bff-324">點對點乙太網路連線</span><span class="sxs-lookup"><span data-stu-id="36bff-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="36bff-325">任何-任何 (IP VPN) 網路</span><span class="sxs-lookup"><span data-stu-id="36bff-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="36bff-326">**圖 14： 使用 ExpressRoute 連線至跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="36bff-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![圖 14：使用 ExpressRoute 連線到跨部署 Azure 虛擬網路](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="36bff-328">圖 14 顯示跨部署 VNet 和 ExpressRoute 由內部路由器連線至 Microsoft Azure。</span><span class="sxs-lookup"><span data-stu-id="36bff-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="36bff-329">如需詳細資訊，請參閱[Microsoft 雲端連線 ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)。</span><span class="sxs-lookup"><span data-stu-id="36bff-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="36bff-330">步驟 5： 決定 Azure 閘道的區域網路位址空間。</span><span class="sxs-lookup"><span data-stu-id="36bff-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="36bff-331">路由傳送至內部部署或其他 VNets 從 VNet、 Azure 會將流量轉送跨找出指派給閘道之本機網路位址空間 Azure 閘道。</span><span class="sxs-lookup"><span data-stu-id="36bff-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="36bff-332">**圖 15： 本機網路位址空間以便跨部署 VNet**</span><span class="sxs-lookup"><span data-stu-id="36bff-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![圖 15：跨部署 Azure 虛擬網路的區域網路位址空間](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="36bff-334">圖 15 會顯示在 Azure 的閘道，代表在內部網路上的連至位址空間跨部署 VNet 與區域網路位址空間。</span><span class="sxs-lookup"><span data-stu-id="36bff-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="36bff-335">您可以透過下列方式定義的區域網路位址空間：</span><span class="sxs-lookup"><span data-stu-id="36bff-335">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="36bff-336">做法 1： 目前所需的位址空間或 （更新時可能需要新增新的子網路時） 的使用中的前置詞的清單。</span><span class="sxs-lookup"><span data-stu-id="36bff-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="36bff-337">選項 2： 整個內部位址空間 （只需要新增新的位址空間時的更新）。</span><span class="sxs-lookup"><span data-stu-id="36bff-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="36bff-338">因為 Azure 閘道不允許摘要的路由，您必須定義選項 2 的區域網路位址空間，讓它不會納入 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="36bff-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="36bff-339">**圖 16: 位址空間內徑建立 VNet 位址空間**</span><span class="sxs-lookup"><span data-stu-id="36bff-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![圖 16：虛擬網路的位址空間所建立的地址空間漏洞](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="36bff-341">圖 16 顯示與根空間的位址空間和 VNet 位址空間的表示法。</span><span class="sxs-lookup"><span data-stu-id="36bff-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="36bff-342">以下是定義使用者的周圍的位址空間"內徑"VNet 所建立的區域網路位址空間的前置詞的範例：</span><span class="sxs-lookup"><span data-stu-id="36bff-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="36bff-p114">組織會使用透過其內部網路中某些部分的私人位址空間 （10.0.0.0/8、 172.16.0.0/12、 / 8 以及 192.168.0.0/16）。他們選擇選項 2 和 10.100.100.0/24 作為其 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="36bff-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="36bff-345">表 7 示範中的步驟及產生定義此範例的區域網路位址空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="36bff-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="36bff-346">**步驟**</span><span class="sxs-lookup"><span data-stu-id="36bff-346">**Step**</span></span>|<span data-ttu-id="36bff-347">**結果**</span><span class="sxs-lookup"><span data-stu-id="36bff-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="36bff-348">1.清單不是 VNet 位址空間根空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="36bff-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="36bff-349">172.16.0.0/12 和 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="36bff-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="36bff-350">2.清單變數八位元，但不包括 VNet 位址空間的最後一個使用八位元的不重疊前置詞。</span><span class="sxs-lookup"><span data-stu-id="36bff-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="36bff-351">10.0.0.0/16、 10.1.0.0/16...]10.99.0.0/16、 10.101.0.0/16...]10.254.0.0/16、 10.255.0.0/16 （255 的首碼，已略過 10.100.0.0/16）</span><span class="sxs-lookup"><span data-stu-id="36bff-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="36bff-352">3.清單內的最後一個使用八位元 VNet 位址空間的不重疊前置詞。</span><span class="sxs-lookup"><span data-stu-id="36bff-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="36bff-353">10.100.0.0/24、 10.100.1.0/24...]10.100.99.0/24、 10.100.101.0/24...]10.100.254.0/24、 10.100.0.255.0/24 （255 的首碼，已略過 10.100.100.0/24）</span><span class="sxs-lookup"><span data-stu-id="36bff-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="36bff-354">**表 7： 範例本機位址網路空間**</span><span class="sxs-lookup"><span data-stu-id="36bff-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="36bff-355">步驟 6： 設定具有裝載在 Azure 中的 DNS 伺服器的內部 DNS 伺服器的 DNS 複寫。</span><span class="sxs-lookup"><span data-stu-id="36bff-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="36bff-356">若要確保內部部署電腦可以解析 Azure 型伺服器的名稱和 Azure 型伺服器可以解析內部電腦的名稱，來設定：</span><span class="sxs-lookup"><span data-stu-id="36bff-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="36bff-357">在您 VNet 以轉送至內部 DNS 伺服器之 DNS 伺服器</span><span class="sxs-lookup"><span data-stu-id="36bff-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="36bff-358">DNS 複寫的適當的區域之間 DNS 伺服器的內部及 VNet</span><span class="sxs-lookup"><span data-stu-id="36bff-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="36bff-359">**圖 17： DNS 複寫及轉寄跨部署 VNet 的 DNS 伺服器**</span><span class="sxs-lookup"><span data-stu-id="36bff-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![圖 17：跨部署 Azure 虛擬網路中 DNS 伺服器的 DNS 複寫和轉送](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="36bff-p115">圖 17 顯示具有 DNS 伺服器跨部署 VNet 在內部網路及 VNet 中的子網路。DNS 複寫及轉寄已設定兩部 DNS 伺服器之間。</span><span class="sxs-lookup"><span data-stu-id="36bff-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="36bff-363">步驟 7： 決定使用強制通道。</span><span class="sxs-lookup"><span data-stu-id="36bff-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="36bff-p116">Azure 的子網路的預設系統路由會指向網際網路。若要確保從虛擬機器時的所有流量一起都出差之間的跨部署的連線，建立路由表格與預設路由使用 Azure 閘道作為其下個躍點位址。然後將路由表建立關聯與子網路。這就是所謂強制通道。如需詳細資訊，請參閱 ＜ [Configure 強制通道](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)。</span><span class="sxs-lookup"><span data-stu-id="36bff-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="36bff-369">**圖 18： 使用者定義的路由和強制通道的跨單位 VNet**</span><span class="sxs-lookup"><span data-stu-id="36bff-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![圖 18：跨部署 Azure 虛擬網路的使用者定義路由和強制通道](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="36bff-371">圖 18 顯示以指向 Azure 閘道的子網路的使用者定義路由跨部署 VNet。</span><span class="sxs-lookup"><span data-stu-id="36bff-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="36bff-372">SharePoint Server 2016 Azure 中的伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="36bff-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="36bff-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="36bff-373"></span></span>

<span data-ttu-id="36bff-374">IT 工作負載架設在 Azure IaaS 內部網路的範例是高可用性、 多層的 SharePoint Server 2016 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="36bff-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="36bff-375">**圖 19： 高度可用的內部網路 SharePoint Server 2016 中的伺服器陣列 Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="36bff-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中高可用性的 SharePoint Server 2016 伺服器陣列](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="36bff-p117">圖 19 顯示部署中使用內部負載平衡器的前端和資料層跨部署 VNet 的 SharePoint Server 2016 伺服器陣列的九個伺服器。如需詳細資訊，包括逐步設計及部署指示，請參閱[Microsoft Azure 中的 SharePoint Server 2016](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="36bff-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="36bff-379">若要建立單一伺服器的 SharePoint Server 2016 伺服器陣列中模擬的跨部署 VNet，請參閱[Azure 的開發人員測試環境中的內部網路 SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="36bff-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="36bff-380">如需其他範例虛擬跨部署 Azure 中的虛擬機器上部署的 IT 工作負載的網路，請參閱[Azure IaaS 的混合式雲端案例](https://technet.microsoft.com/library/mt750502.aspx)。</span><span class="sxs-lookup"><span data-stu-id="36bff-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="36bff-381">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36bff-381">See also</span></span>

<span data-ttu-id="36bff-382"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="36bff-382"></span></span>

[<span data-ttu-id="36bff-383">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="36bff-383">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="36bff-384">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="36bff-384">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="36bff-385">Microsoft 的 Enterprise Cloud 藍圖：IT 決策者的資源</span><span class="sxs-lookup"><span data-stu-id="36bff-385">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



