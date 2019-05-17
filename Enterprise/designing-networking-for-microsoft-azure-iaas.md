---
title: 設計 Microsoft Azure IaaS 的網路
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
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: 摘要： 了解如何設計 Microsoft Azure IaaS 中工作負載的最佳化網路功能。
ms.openlocfilehash: b06564c8a86c59dac4ac9a5380cd88cf9d045974
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068129"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="5598a-103">設計 Microsoft Azure IaaS 的網路</span><span class="sxs-lookup"><span data-stu-id="5598a-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="5598a-104">**摘要：** 了解如何設計 Microsoft Azure IaaS 中工作負載的最佳化網路功能。</span><span class="sxs-lookup"><span data-stu-id="5598a-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="5598a-105">最佳化的裝載在 Azure IaaS 中的 IT 工作負載的網路功能需要瞭解的 Azure 虛擬網路 (Vnet)、 位址空間，路由、 DNS 及負載平衡。</span><span class="sxs-lookup"><span data-stu-id="5598a-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="5598a-106">規劃任何 VNet 中的步驟</span><span class="sxs-lookup"><span data-stu-id="5598a-106">Planning steps for any VNet</span></span>

<span data-ttu-id="5598a-107">任何類型的 VNet，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="5598a-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="5598a-108">步驟 1： 準備您的內部網路的 Microsoft 雲端服務。</span><span class="sxs-lookup"><span data-stu-id="5598a-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="5598a-109">經過[Microsoft 雲端連線能力的共同元素](common-elements-of-microsoft-cloud-connectivity.md)中的**步驟來準備您的 Microsoft 雲端服務的網路**區段。</span><span class="sxs-lookup"><span data-stu-id="5598a-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="5598a-110">步驟 2： 最佳化您的網際網路頻寬。</span><span class="sxs-lookup"><span data-stu-id="5598a-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="5598a-111">最佳化網際網路頻寬使用步驟 2 到 4 的**步驟來準備您的網路以 Microsoft SaaS 服務**] 區段中，在[設計 Microsoft SaaS 的網路](designing-networking-for-microsoft-saas.md)。</span><span class="sxs-lookup"><span data-stu-id="5598a-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="5598a-112">步驟 3： 決定 VNet 的類型 (僅限雲端或跨部門)。</span><span class="sxs-lookup"><span data-stu-id="5598a-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="5598a-113">僅雲端 VNet 有沒有連線至內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="5598a-113">A cloud-only VNet has no connection to an on-premises network.</span></span> <span data-ttu-id="5598a-114">以下是範例。</span><span class="sxs-lookup"><span data-stu-id="5598a-114">Here is an example.</span></span>
  
<span data-ttu-id="5598a-115">**圖 1: 僅雲端 VNet**</span><span class="sxs-lookup"><span data-stu-id="5598a-115">**Figure 1: A cloud-only VNet**</span></span>

![圖 1：Azure 中只存在於雲端的虛擬網路](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="5598a-117">圖 1 顯示僅雲端 VNet 中的一組的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="5598a-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="5598a-118">跨單位 VNet 具有站台對站 (S2S) VPN 或 ExpressRoute 連線到 Azure 閘道在內部網路。</span><span class="sxs-lookup"><span data-stu-id="5598a-118">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway.</span></span> <span data-ttu-id="5598a-119">以下是範例。</span><span class="sxs-lookup"><span data-stu-id="5598a-119">Here is an example.</span></span>
  
<span data-ttu-id="5598a-120">**圖 2: 跨單位 VNet**</span><span class="sxs-lookup"><span data-stu-id="5598a-120">**Figure 2: A cross-premises VNet**</span></span>

![圖 2：Azure 中跨部署的虛擬網路](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="5598a-122">圖 2 顯示一組的虛擬機器中的跨單位 VNet，連線到內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="5598a-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="5598a-123">請參閱其他本文中[的跨單位 VNet 的規劃步驟](designing-networking-for-microsoft-azure-iaas.md#cross_prem)一節。</span><span class="sxs-lookup"><span data-stu-id="5598a-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="5598a-124">步驟 4： 決定 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="5598a-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="5598a-125">表 1 顯示不同類型的 Vnet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="5598a-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="5598a-126">**VNet 的類型**</span><span class="sxs-lookup"><span data-stu-id="5598a-126">**Type of VNet**</span></span>|<span data-ttu-id="5598a-127">**虛擬網路位址空間**</span><span class="sxs-lookup"><span data-stu-id="5598a-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5598a-128">僅雲端</span><span class="sxs-lookup"><span data-stu-id="5598a-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="5598a-129">任意私人位址空間</span><span class="sxs-lookup"><span data-stu-id="5598a-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="5598a-130">互連僅雲端</span><span class="sxs-lookup"><span data-stu-id="5598a-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="5598a-131">任意的私用]，但不是重疊與其他連線 Vnet</span><span class="sxs-lookup"><span data-stu-id="5598a-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="5598a-132">跨單位</span><span class="sxs-lookup"><span data-stu-id="5598a-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="5598a-133">私用]，但不是重疊與內部部署</span><span class="sxs-lookup"><span data-stu-id="5598a-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="5598a-134">互連的跨單位部署</span><span class="sxs-lookup"><span data-stu-id="5598a-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="5598a-135">私用]，但不是重疊的內部部署及其他連線 Vnet</span><span class="sxs-lookup"><span data-stu-id="5598a-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="5598a-136">**表 1： 類型的 Vnet 和其對應的位址空間**</span><span class="sxs-lookup"><span data-stu-id="5598a-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="5598a-137">虛擬機器由 DHCP 指派位址空間的子網路的位址組態：</span><span class="sxs-lookup"><span data-stu-id="5598a-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="5598a-138">位址/子網路遮罩</span><span class="sxs-lookup"><span data-stu-id="5598a-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="5598a-139">預設閘道</span><span class="sxs-lookup"><span data-stu-id="5598a-139">Default gateway</span></span>
    
- <span data-ttu-id="5598a-140">DNS 伺服器 IP 位址</span><span class="sxs-lookup"><span data-stu-id="5598a-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="5598a-141">您也可以保留的靜態 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="5598a-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="5598a-142">虛擬機器也可以指派公用 IP 位址，個別或從包含雲端服務 （適用於僅傳統的部署機器）。</span><span class="sxs-lookup"><span data-stu-id="5598a-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="5598a-143">步驟 5： 決定 VNet 和指派給每個位址空間內的子網路。</span><span class="sxs-lookup"><span data-stu-id="5598a-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="5598a-144">有兩種類型的 VNet 中的子網路、 閘道子網路和虛擬機器裝載的子網路。</span><span class="sxs-lookup"><span data-stu-id="5598a-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="5598a-145">**圖 3：Azure 中的兩種子網路類型**</span><span class="sxs-lookup"><span data-stu-id="5598a-145">**Figure 3: The two types of subnets in Azure**</span></span>

![圖 3：Azure 中的兩種子網路類型](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="5598a-147">圖 3 顯示包含有 Azure 閘道和一組包含虛擬機器的虛擬機器裝載子網路的閘道子網路的 VNet。</span><span class="sxs-lookup"><span data-stu-id="5598a-147">Figure 3 shows a VNet containing a gateway subnet that has an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="5598a-148">Azure 時需要 Azure 閘道子網路，裝載兩部虛擬機器的 Azure 閘道。</span><span class="sxs-lookup"><span data-stu-id="5598a-148">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway.</span></span> <span data-ttu-id="5598a-149">至少要有 29 位元前置詞長度與指定的位址空間 (範例： 192.168.15.248/29)。</span><span class="sxs-lookup"><span data-stu-id="5598a-149">Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29).</span></span> <span data-ttu-id="5598a-150">建議的 27 位元或較小的前置詞長度，尤其是如果您打算使用 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="5598a-150">A 27-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="5598a-151">決定 Azure 閘道子網路的位址空間的最佳作法是：</span><span class="sxs-lookup"><span data-stu-id="5598a-151">A best practice for determining the address space of the Azure gateway subnet is:</span></span>
  
1. <span data-ttu-id="5598a-152">決定的閘道子網路大小。</span><span class="sxs-lookup"><span data-stu-id="5598a-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="5598a-153">在位址空間的 VNet 中變數的位元，設定用於設為 0，閘道子網路的位元，其餘位元數設為 1。</span><span class="sxs-lookup"><span data-stu-id="5598a-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="5598a-154">轉換成十進位及 express 的位址空間為具有前置詞長度設為閘道子網路大小。</span><span class="sxs-lookup"><span data-stu-id="5598a-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="5598a-155">使用此方法之後，閘道子網路的位址空間一定是 VNet 位址空間的邊界最遠的結尾。</span><span class="sxs-lookup"><span data-stu-id="5598a-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="5598a-156">以下是定義閘道子網路的位址前置詞的範例： VNet 位址空間是 10.119.0.0/16。</span><span class="sxs-lookup"><span data-stu-id="5598a-156">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16.</span></span> <span data-ttu-id="5598a-157">組織一開始會使用站台對站 VPN 連線，但最終會收到 ExpressRoute。</span><span class="sxs-lookup"><span data-stu-id="5598a-157">The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute.</span></span> <span data-ttu-id="5598a-158">表 2 示範的步驟和結果判斷網路前置詞表示法 (也稱為 CIDR) 中的閘道子網路位址前置字元。</span><span class="sxs-lookup"><span data-stu-id="5598a-158">Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="5598a-159">以下是步驟和範例判斷閘道子網路位址前置詞：</span><span class="sxs-lookup"><span data-stu-id="5598a-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="5598a-160">決定的閘道子網路大小。</span><span class="sxs-lookup"><span data-stu-id="5598a-160">Decide on the size of the gateway subnet.</span></span> <span data-ttu-id="5598a-161">我們的範例，我們會選擇 /28。</span><span class="sxs-lookup"><span data-stu-id="5598a-161">For our example, we chose /28.</span></span>
2. <span data-ttu-id="5598a-162">設定位元 VNet 位址空間 (b) 部分變數設為 0 閘道子網路位元 (G)，否則 1 (V)。</span><span class="sxs-lookup"><span data-stu-id="5598a-162">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V).</span></span> <span data-ttu-id="5598a-163">我們的範例，我們使用 10.119.0.0/16 位址空間的 VNet。</span><span class="sxs-lookup"><span data-stu-id="5598a-163">For our example, we are using the 10.119.0.0/16 address space for the VNet.</span></span>
<br/>
<br/><span data-ttu-id="5598a-164">10.119。</span><span class="sxs-lookup"><span data-stu-id="5598a-164">10.119.</span></span> <span data-ttu-id="5598a-165">bbbbbbbb。</span><span class="sxs-lookup"><span data-stu-id="5598a-165">bbbbbbbb .</span></span> <span data-ttu-id="5598a-166">bbbbbbbb</span><span class="sxs-lookup"><span data-stu-id="5598a-166">bbbbbbbb</span></span>
<br/><span data-ttu-id="5598a-167">10.119。</span><span class="sxs-lookup"><span data-stu-id="5598a-167">10.119.</span></span> <span data-ttu-id="5598a-168">VVVVVVVV。</span><span class="sxs-lookup"><span data-stu-id="5598a-168">VVVVVVVV .</span></span> <span data-ttu-id="5598a-169">VVVVGGGG</span><span class="sxs-lookup"><span data-stu-id="5598a-169">VVVVGGGG</span></span>
<br/><span data-ttu-id="5598a-170">10.119。</span><span class="sxs-lookup"><span data-stu-id="5598a-170">10.119.</span></span> <span data-ttu-id="5598a-171">11111111。</span><span class="sxs-lookup"><span data-stu-id="5598a-171">11111111 .</span></span> <span data-ttu-id="5598a-172">11110000</span><span class="sxs-lookup"><span data-stu-id="5598a-172">11110000</span></span>
<br/><br/>
3. <span data-ttu-id="5598a-173">步驟 2 中將結果轉換成十進位及快速為位址空間。</span><span class="sxs-lookup"><span data-stu-id="5598a-173">Convert the result from step 2 to decimal and express as an address space.</span></span> <span data-ttu-id="5598a-174">我們的範例，10.119。</span><span class="sxs-lookup"><span data-stu-id="5598a-174">For our example, 10.119.</span></span> <span data-ttu-id="5598a-175">11111111。</span><span class="sxs-lookup"><span data-stu-id="5598a-175">11111111 .</span></span> <span data-ttu-id="5598a-176">11110000 10.119.255.240，且從步驟 1，(在我們的範例 28) 前置詞長度，產生的閘道子網路位址前置詞是 10.119.255.240/28。</span><span class="sxs-lookup"><span data-stu-id="5598a-176">11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="5598a-177">如需詳細資訊，請參閱[Azure 閘道子網路的位址空間計算機](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)。</span><span class="sxs-lookup"><span data-stu-id="5598a-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="5598a-178">虛擬機器裝載的子網路會放置 Azure 的虛擬機器，您可以根據內部一般指導方針，例如一般角色或應用程式或子網路隔離層的位置。</span><span class="sxs-lookup"><span data-stu-id="5598a-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="5598a-179">Azure 每個子網路上使用的第一次 3 的地址。</span><span class="sxs-lookup"><span data-stu-id="5598a-179">Azure uses the first 3 addresses on each subnet.</span></span> <span data-ttu-id="5598a-180">因此，在 Azure 的子網路上可能地址的數目是 2<sup>n</sup> -5，其中 n 是主機位元數。</span><span class="sxs-lookup"><span data-stu-id="5598a-180">Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits.</span></span> <span data-ttu-id="5598a-181">表 3 顯示的虛擬機器有需要的號碼範圍主控個位元所需，與對應的子網路大小。</span><span class="sxs-lookup"><span data-stu-id="5598a-181">Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="5598a-182">**所需的虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="5598a-182">**Virtual machines required**</span></span>|<span data-ttu-id="5598a-183">**主機位元**</span><span class="sxs-lookup"><span data-stu-id="5598a-183">**Host bits**</span></span>|<span data-ttu-id="5598a-184">**子網路大小**</span><span class="sxs-lookup"><span data-stu-id="5598a-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="5598a-185">1-3</span><span class="sxs-lookup"><span data-stu-id="5598a-185">1-3</span></span>  <br/> |<span data-ttu-id="5598a-186">3</span><span class="sxs-lookup"><span data-stu-id="5598a-186">3</span></span>  <br/> |<span data-ttu-id="5598a-187">/29</span><span class="sxs-lookup"><span data-stu-id="5598a-187">/29</span></span>  <br/> |
|<span data-ttu-id="5598a-188">4-11</span><span class="sxs-lookup"><span data-stu-id="5598a-188">4-11</span></span>  <br/> |<span data-ttu-id="5598a-189">4</span><span class="sxs-lookup"><span data-stu-id="5598a-189">4</span></span>  <br/> |<span data-ttu-id="5598a-190">/28</span><span class="sxs-lookup"><span data-stu-id="5598a-190">/28</span></span>  <br/> |
|<span data-ttu-id="5598a-191">12-27</span><span class="sxs-lookup"><span data-stu-id="5598a-191">12-27</span></span>  <br/> |<span data-ttu-id="5598a-192">5</span><span class="sxs-lookup"><span data-stu-id="5598a-192">5</span></span>  <br/> |<span data-ttu-id="5598a-193">/27</span><span class="sxs-lookup"><span data-stu-id="5598a-193">/27</span></span>  <br/> |
|<span data-ttu-id="5598a-194">28-59</span><span class="sxs-lookup"><span data-stu-id="5598a-194">28-59</span></span>  <br/> |<span data-ttu-id="5598a-195">6</span><span class="sxs-lookup"><span data-stu-id="5598a-195">6</span></span>  <br/> |<span data-ttu-id="5598a-196">/26</span><span class="sxs-lookup"><span data-stu-id="5598a-196">/26</span></span>  <br/> |
|<span data-ttu-id="5598a-197">60-123</span><span class="sxs-lookup"><span data-stu-id="5598a-197">60-123</span></span>  <br/> |<span data-ttu-id="5598a-198">7</span><span class="sxs-lookup"><span data-stu-id="5598a-198">7</span></span>  <br/> |<span data-ttu-id="5598a-199">/25</span><span class="sxs-lookup"><span data-stu-id="5598a-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="5598a-200">**表 3： 虛擬機器需求和其子網路大小**</span><span class="sxs-lookup"><span data-stu-id="5598a-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="5598a-201">如需虛擬機器上的子網路或 VNet 的最大數量的詳細資訊，請參閱[網路功能的限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="5598a-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="5598a-202">如需詳細資訊，請參閱[ Plan and design Azure 虛擬網路](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)。</span><span class="sxs-lookup"><span data-stu-id="5598a-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="5598a-203">步驟 6： 決定 DNS 伺服器設定，以及指派給 VNet 中 Vm 的 DNS 伺服器位址。</span><span class="sxs-lookup"><span data-stu-id="5598a-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="5598a-204">Azure 會指派虛擬機器由 DHCP 的 DNS 伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="5598a-204">Azure assigns virtual machines the addresses of DNS servers by DHCP.</span></span> <span data-ttu-id="5598a-205">可以是 DNS 伺服器：</span><span class="sxs-lookup"><span data-stu-id="5598a-205">DNS servers can be:</span></span>
  
- <span data-ttu-id="5598a-206">提供 Azure： 提供本機名稱登錄和本機網際網路名稱解析</span><span class="sxs-lookup"><span data-stu-id="5598a-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="5598a-207">您所提供： 提供本機或網路名稱登錄與內部網路或網際網路名稱解析</span><span class="sxs-lookup"><span data-stu-id="5598a-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="5598a-208">表 4 顯示每種類型的 VNet 的 DNS 伺服器的不同設定。</span><span class="sxs-lookup"><span data-stu-id="5598a-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="5598a-209">**VNet 的類型**</span><span class="sxs-lookup"><span data-stu-id="5598a-209">**Type of VNet**</span></span>|<span data-ttu-id="5598a-210">**DNS 伺服器**</span><span class="sxs-lookup"><span data-stu-id="5598a-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5598a-211">僅雲端</span><span class="sxs-lookup"><span data-stu-id="5598a-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="5598a-212">Azure 提供的本機與網際網路名稱解析</span><span class="sxs-lookup"><span data-stu-id="5598a-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="5598a-213">Azure 虛擬機器的本機與網際網路名稱解析 （DNS 轉寄）</span><span class="sxs-lookup"><span data-stu-id="5598a-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="5598a-214">跨單位</span><span class="sxs-lookup"><span data-stu-id="5598a-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="5598a-215">在內部的本機複本與內部網路的名稱解析</span><span class="sxs-lookup"><span data-stu-id="5598a-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="5598a-216">Azure 虛擬機器的本機複本與內部網路名稱解析 （DNS 複寫和轉送）</span><span class="sxs-lookup"><span data-stu-id="5598a-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="5598a-217">**表 4： 兩個不同類型的 Vnet 的 DNS 伺服器選項**</span><span class="sxs-lookup"><span data-stu-id="5598a-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="5598a-218">如需詳細資訊，請參閱 <<c0>的 Vm 及角色執行個體的名稱解析。</span><span class="sxs-lookup"><span data-stu-id="5598a-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="5598a-219">步驟 7： 決定負載平衡組態 （網際網路對向或內部）。</span><span class="sxs-lookup"><span data-stu-id="5598a-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="5598a-220">在某些情況下，您要將一組具有相同角色之伺服器的傳入流量分散。</span><span class="sxs-lookup"><span data-stu-id="5598a-220">In some cases, you want to distribute incoming traffic to a set of servers that have the same role.</span></span> <span data-ttu-id="5598a-221">Azure IaaS 具有內建的設備，若要這麼做為網際網路對向和內部流量負載。</span><span class="sxs-lookup"><span data-stu-id="5598a-221">Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="5598a-222">Azure 網際網路對向負載平衡會隨機分散來路不明連入網際網路的流量負載平衡集的成員。</span><span class="sxs-lookup"><span data-stu-id="5598a-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="5598a-223">**圖 4：Azure 中的外部負載平衡器**</span><span class="sxs-lookup"><span data-stu-id="5598a-223">**Figure 4: An external load balancer in Azure**</span></span>

![圖 4：Azure 中的外部負載平衡器](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="5598a-225">圖 4 顯示將輸入的 NAT 規則或一組負載平衡集內的虛擬機器的端點上的內送流量的 Azure 中的外部負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="5598a-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="5598a-226">Azure 內部負載平衡會隨機分散來路不明的連入流量從其他 Azure Vm 或內部網路負載平衡集的成員電腦。</span><span class="sxs-lookup"><span data-stu-id="5598a-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="5598a-227">**圖 5：Azure 中的內部負載平衡器**</span><span class="sxs-lookup"><span data-stu-id="5598a-227">**Figure 5: An internal load balancer in Azure**</span></span>

![圖 5：Azure 中的內部負載平衡器](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="5598a-229">圖 5 顯示將輸入的 NAT 規則或一組負載平衡集內的虛擬機器的端點上的內送流量的 Azure 內部負載平衡器。</span><span class="sxs-lookup"><span data-stu-id="5598a-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="5598a-230">如需詳細資訊，請參閱 < <b0>Azure 負載平衡器</b0>。</span><span class="sxs-lookup"><span data-stu-id="5598a-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="5598a-231">步驟 8： 決定使用虛擬設備和使用者定義路由。</span><span class="sxs-lookup"><span data-stu-id="5598a-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="5598a-232">如果您需要轉送到您的 VNet 中的虛擬設備的流量，您可能需要新增一或多個使用者定義路由至子網路。</span><span class="sxs-lookup"><span data-stu-id="5598a-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="5598a-233">**圖 6：Azure 中的虛擬設備和使用者定義路由**</span><span class="sxs-lookup"><span data-stu-id="5598a-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![圖 6：Azure 中的虛擬設備和使用者定義路由](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="5598a-235">圖 6 顯示跨單位 VNet 和指派給指向虛擬 appliance 虛擬機器裝載子網路的使用者定義路由。</span><span class="sxs-lookup"><span data-stu-id="5598a-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="5598a-236">如需詳細資訊，請參閱[使用者定義路由和 IP 轉寄功能](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)。</span><span class="sxs-lookup"><span data-stu-id="5598a-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="5598a-237">步驟 9： 決定如何從網際網路的電腦會連線至虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="5598a-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="5598a-238">有多種方式來提供網際網路存取虛擬機器上的 VNet，包括透過 proxy 伺服器或其他邊緣裝置對組織網路的存取。</span><span class="sxs-lookup"><span data-stu-id="5598a-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="5598a-239">表 5 會列出篩選或檢查來路不明的連入流量的方法。</span><span class="sxs-lookup"><span data-stu-id="5598a-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="5598a-240">**方法**</span><span class="sxs-lookup"><span data-stu-id="5598a-240">**Method**</span></span>|<span data-ttu-id="5598a-241">**部署模型**</span><span class="sxs-lookup"><span data-stu-id="5598a-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5598a-242">1.端點和設定雲端服務上的 Acl</span><span class="sxs-lookup"><span data-stu-id="5598a-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="5598a-243">傳統</span><span class="sxs-lookup"><span data-stu-id="5598a-243">Classic</span></span>  <br/> |
|<span data-ttu-id="5598a-244">2.網路安全性群組</span><span class="sxs-lookup"><span data-stu-id="5598a-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="5598a-245">資源管理員與傳統</span><span class="sxs-lookup"><span data-stu-id="5598a-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="5598a-246">3.網際網路對向負載平衡器使用 NAT 的輸入規則</span><span class="sxs-lookup"><span data-stu-id="5598a-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="5598a-247">資源管理員</span><span class="sxs-lookup"><span data-stu-id="5598a-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="5598a-248">4.網路安全性設備 Azure marketplace （不會顯示）</span><span class="sxs-lookup"><span data-stu-id="5598a-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="5598a-249">資源管理員與傳統</span><span class="sxs-lookup"><span data-stu-id="5598a-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="5598a-250">**表 5： 方法的連接至虛擬機器和其對應的 Azure 的部署模型**</span><span class="sxs-lookup"><span data-stu-id="5598a-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="5598a-251">**圖 7：透過網際網路連線到 Azure 虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="5598a-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![圖 7：透過網際網路連線到 Azure 虛擬機器](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="5598a-253">圖 7 顯示連接中使用端點的雲端服務的虛擬機器上使用網路安全性] 群組中，子網路的虛擬機器，使用外部負載平衡器和 NAT 的輸入的規則的子網路上的虛擬機器連線到網際網路的電腦。</span><span class="sxs-lookup"><span data-stu-id="5598a-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="5598a-254">額外的安全性提供者：</span><span class="sxs-lookup"><span data-stu-id="5598a-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="5598a-255">遠端桌面] 和 [SSH 連線，這是經過驗證及加密。</span><span class="sxs-lookup"><span data-stu-id="5598a-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="5598a-256">遠端 PowerShell 工作階段，這是經過驗證及加密。</span><span class="sxs-lookup"><span data-stu-id="5598a-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="5598a-257">IPsec 傳輸模式，您可以使用的端對端加密。</span><span class="sxs-lookup"><span data-stu-id="5598a-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="5598a-258">Azure DDOS 防護，這有助於防止外部及內部攻擊</span><span class="sxs-lookup"><span data-stu-id="5598a-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="5598a-259">如需詳細資訊，請參閱[Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="5598a-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="5598a-260">步驟 10： 針對多個 Vnet，決定 VNet 對 VNet 連線拓樸。</span><span class="sxs-lookup"><span data-stu-id="5598a-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="5598a-261">Vnet 可以使用類似用於連接組織的站台拓撲彼此連線。</span><span class="sxs-lookup"><span data-stu-id="5598a-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="5598a-262">菊輪鍊設定連接中一系列 Vnet。</span><span class="sxs-lookup"><span data-stu-id="5598a-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="5598a-263">**圖 8: 菊組態 Vnet**</span><span class="sxs-lookup"><span data-stu-id="5598a-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![圖 8：Azure 虛擬網路的菊輪鍊設定](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="5598a-265">圖 8 顯示連線使用菊設定數列中的五個 Vnet。</span><span class="sxs-lookup"><span data-stu-id="5598a-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="5598a-266">輪輻和中樞設定連接至中央 Vnet、 連線至彼此本身是一組多個 Vnet。</span><span class="sxs-lookup"><span data-stu-id="5598a-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="5598a-267">**圖 9: 輪輻和中樞設定 Vnet**</span><span class="sxs-lookup"><span data-stu-id="5598a-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![圖 9：Azure 虛擬網路的輪輻和中樞設定](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="5598a-269">圖 9 顯示六個 Vnet、 兩個 Vnet 會連線至彼此與也兩個其他支點 Vnet 的中樞。</span><span class="sxs-lookup"><span data-stu-id="5598a-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="5598a-270">完整網狀設定連接至彼此的每個 VNet。</span><span class="sxs-lookup"><span data-stu-id="5598a-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="5598a-271">**圖 10： 完整網狀結構 Vnet 的設定**</span><span class="sxs-lookup"><span data-stu-id="5598a-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![圖 10：Azure 虛擬網路的網狀設定](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="5598a-273">圖 10 顯示四個 Vnet 所有連接至彼此，使用六個 VNet 對 VNet 連線總數。</span><span class="sxs-lookup"><span data-stu-id="5598a-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="5598a-274">規劃跨單位 VNet 中的步驟</span><span class="sxs-lookup"><span data-stu-id="5598a-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="5598a-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="5598a-275"></span></span>

<span data-ttu-id="5598a-276">針對跨單位 VNet，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="5598a-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="5598a-277">若要建立模擬的跨單位部署開發/測試環境，請參閱 < <b0>Simulated 跨單位 azure 虛擬網路</b0>。</span><span class="sxs-lookup"><span data-stu-id="5598a-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="5598a-278">步驟 1： 判定 VNet （S2S VPN 或 ExpressRoute） 的跨單位連線。</span><span class="sxs-lookup"><span data-stu-id="5598a-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="5598a-279">表 6 列出不同類型的連線。</span><span class="sxs-lookup"><span data-stu-id="5598a-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="5598a-280">**連線類型**</span><span class="sxs-lookup"><span data-stu-id="5598a-280">**Type of connection**</span></span>|<span data-ttu-id="5598a-281">**用途**</span><span class="sxs-lookup"><span data-stu-id="5598a-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5598a-282">站台對站 (S2S) VPN</span><span class="sxs-lookup"><span data-stu-id="5598a-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="5598a-283">若要在單一 VNet 連線 1-10 個網站 （包括其他 Vnet）。</span><span class="sxs-lookup"><span data-stu-id="5598a-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="5598a-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="5598a-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="5598a-285">透過網際網路 Exchange 提供者 (IXP) 或網路服務提供者 (NSP) Azure 私用、 安全連結。</span><span class="sxs-lookup"><span data-stu-id="5598a-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="5598a-286">點網站 (P2S) VPN</span><span class="sxs-lookup"><span data-stu-id="5598a-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="5598a-287">將單一電腦連接到 VNet。</span><span class="sxs-lookup"><span data-stu-id="5598a-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="5598a-288">VNet 對等或 VNet 對 VNet (V2V) VPN</span><span class="sxs-lookup"><span data-stu-id="5598a-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="5598a-289">連接至另一個 VNet 的 VNet。</span><span class="sxs-lookup"><span data-stu-id="5598a-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="5598a-290">**表 6: 類型之連線的跨單位 Vnet**</span><span class="sxs-lookup"><span data-stu-id="5598a-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="5598a-291">如需有關連線數目上限的詳細資訊，請參閱[網路功能的限制](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)。</span><span class="sxs-lookup"><span data-stu-id="5598a-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="5598a-292">如需 VPN 裝置的詳細資訊，請參閱 <<c0>的站台對站虛擬網路連線的 VPN 裝置。</span><span class="sxs-lookup"><span data-stu-id="5598a-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="5598a-293">如需 VNet 對等的詳細資訊，請參閱[VNet 對等](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)。</span><span class="sxs-lookup"><span data-stu-id="5598a-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="5598a-294">**圖 11: 四種方法來連線至跨單位 VNet**</span><span class="sxs-lookup"><span data-stu-id="5598a-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![圖 11：連線到跨部署 Azure 虛擬網路的三種方式](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="5598a-296">圖 11 顯示具有連線四種類型的 VNet: P2S 連線從電腦、 從內部網路的 S2S VPN 連線、 從內部部署網路，ExpressRoute 連線並從另一個 VNet 的 VNet 對 VNet 連線。</span><span class="sxs-lookup"><span data-stu-id="5598a-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="5598a-297">您可以連線至 Vm VNet 中以下列方式：</span><span class="sxs-lookup"><span data-stu-id="5598a-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="5598a-298">從您的內部網路或網際網路的 VNet Vm 的系統管理</span><span class="sxs-lookup"><span data-stu-id="5598a-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="5598a-299">從您的內部網路的 IT 工作負載存取</span><span class="sxs-lookup"><span data-stu-id="5598a-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="5598a-300">透過其他 Vnet 網路的分機號碼</span><span class="sxs-lookup"><span data-stu-id="5598a-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="5598a-301">連線的安全性是由下列提供：</span><span class="sxs-lookup"><span data-stu-id="5598a-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="5598a-302">P2S 使用安全通訊端通道通訊協定 (SSTP)</span><span class="sxs-lookup"><span data-stu-id="5598a-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="5598a-303">S2S 和 VNet 對 VNet 的 VPN 連線使用 AES256 IPsec 通道模式</span><span class="sxs-lookup"><span data-stu-id="5598a-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="5598a-304">ExpressRoute 是私人 WAN 連線</span><span class="sxs-lookup"><span data-stu-id="5598a-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="5598a-305">如需詳細資訊，請參閱[Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity)和[Azure 網路安全性](https://azure.microsoft.com/blog/azure-network-security/)。</span><span class="sxs-lookup"><span data-stu-id="5598a-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="5598a-306">步驟 2： 決定在內部部署 VPN 裝置或路由器。</span><span class="sxs-lookup"><span data-stu-id="5598a-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="5598a-307">您在內部部署 VPN 裝置或路由器，做為：</span><span class="sxs-lookup"><span data-stu-id="5598a-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="5598a-308">IPsec 對等網路，終止 Azure 閘道的 S2S VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="5598a-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="5598a-309">私用的對等 ExpressRoute 連線 BPG 對等和終止點。</span><span class="sxs-lookup"><span data-stu-id="5598a-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="5598a-310">**圖 12：內部部署 VPN 路由器或裝置**</span><span class="sxs-lookup"><span data-stu-id="5598a-310">**Figure 12: The on-premises VPN router or device**</span></span>

![圖 12：內部部署 VPN 路由器或裝置](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="5598a-312">圖 12 顯示跨單位 VNet 連接到內部部署 VPN 路由器或裝置。</span><span class="sxs-lookup"><span data-stu-id="5598a-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="5598a-313">如需詳細資訊，請參閱 <<c0>關於 VPN 閘道。</span><span class="sxs-lookup"><span data-stu-id="5598a-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="5598a-314">步驟 3： 新增至您的內部網路進行 VNet 位址空間可以到達路由。</span><span class="sxs-lookup"><span data-stu-id="5598a-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="5598a-315">從內部部署路由傳送至 Vnet 包含下列任一動作：</span><span class="sxs-lookup"><span data-stu-id="5598a-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="5598a-316">指向您的 VPN 裝置的 VNet 位址空間的路由。</span><span class="sxs-lookup"><span data-stu-id="5598a-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="5598a-317">在您點之間的 S2S VPN 或 ExpressRoute 連線的 VPN 裝置的 VNet 位址空間路由</span><span class="sxs-lookup"><span data-stu-id="5598a-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="5598a-318">**圖 13: 內部部署路由需要讓 VNet 可以到達**</span><span class="sxs-lookup"><span data-stu-id="5598a-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![圖 13：內部部署路由需要讓 Azure VNet 可以連線](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="5598a-320">圖 13 顯示內部路由器和 VPN 路由器或代表 VNet 位址空間裝置所需的路由資訊。</span><span class="sxs-lookup"><span data-stu-id="5598a-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="5598a-321">步驟 4: ExpressRoute，如規劃與您的提供者的新連線。</span><span class="sxs-lookup"><span data-stu-id="5598a-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="5598a-322">您可以使用私人對等之間您的內部網路與 Microsoft 雲端中三個不同的方式建立 ExpressRoute 連線：</span><span class="sxs-lookup"><span data-stu-id="5598a-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="5598a-323">共置在雲端 exchange</span><span class="sxs-lookup"><span data-stu-id="5598a-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="5598a-324">點對點乙太網路連線</span><span class="sxs-lookup"><span data-stu-id="5598a-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="5598a-325">任何對多 (IP VPN) 網路</span><span class="sxs-lookup"><span data-stu-id="5598a-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="5598a-326">**圖 14： 使用 ExpressRoute 連線至跨單位 VNet**</span><span class="sxs-lookup"><span data-stu-id="5598a-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![圖 14：使用 ExpressRoute 連線到跨部署 Azure 虛擬網路](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="5598a-328">圖 14 顯示跨單位 VNet，以及從內部路由器到 Microsoft Azure ExpressRoute 連線。</span><span class="sxs-lookup"><span data-stu-id="5598a-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="5598a-329">如需詳細資訊，請參閱 <<c0>適用於 Microsoft 雲端連線能力。</span><span class="sxs-lookup"><span data-stu-id="5598a-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="5598a-330">步驟 5： 決定 Azure 閘道的區域網路位址空間。</span><span class="sxs-lookup"><span data-stu-id="5598a-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="5598a-331">進行路由傳送至內部部署或其他 Vnet 從 VNet，Azure 會比對區域網路位址空間指派給閘道 Azure 閘道之間轉送流量。</span><span class="sxs-lookup"><span data-stu-id="5598a-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="5598a-332">**圖 15: 區域網路位址空間的跨單位 VNet**</span><span class="sxs-lookup"><span data-stu-id="5598a-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![圖 15：跨部署 Azure 虛擬網路的區域網路位址空間](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="5598a-334">圖 15 顯示跨單位 VNet 和區域網路位址空間，在 Azure 閘道，表示在內部部署網路上的可連線的位址空間。</span><span class="sxs-lookup"><span data-stu-id="5598a-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="5598a-335">您可以下列方式定義的區域網路位址空間：</span><span class="sxs-lookup"><span data-stu-id="5598a-335">You can define the Local Network address space in these ways:</span></span>
  
- <span data-ttu-id="5598a-336">選項 1： 目前所需的位址空間或 （當您新增新的子網路時，可能需要更新） 的使用中的前置詞的清單。</span><span class="sxs-lookup"><span data-stu-id="5598a-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="5598a-337">選項 2： 整個內部地址空間 （只有當您新增新的位址空間的更新）。</span><span class="sxs-lookup"><span data-stu-id="5598a-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="5598a-338">因為 Azure 閘道不允許摘錄的路由，您必須先定義選項 2 的區域網路位址空間，以便它不會納入 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="5598a-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="5598a-339">**圖 16: 地址空間漏洞建立 VNet 位址空間**</span><span class="sxs-lookup"><span data-stu-id="5598a-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![圖 16：虛擬網路的位址空間所建立的地址空間漏洞](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="5598a-341">圖 16 顯示的位址空間] 根空間和 VNet 位址空間的表示法。</span><span class="sxs-lookup"><span data-stu-id="5598a-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="5598a-342">以下是定義為 「 漏洞 」 建立 VNet 的位址空間周圍的區域網路位址空間的前置詞的範例：</span><span class="sxs-lookup"><span data-stu-id="5598a-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="5598a-343">組織使用私人位址空間 （10.0.0.0/8、 172.16.0.0/12，/8 以及 192.168.0.0/16） 部分，其內部部署網路上。</span><span class="sxs-lookup"><span data-stu-id="5598a-343">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network.</span></span> <span data-ttu-id="5598a-344">他們選擇選項 2 和 10.100.100.0/24 作為其 VNet 位址空間。</span><span class="sxs-lookup"><span data-stu-id="5598a-344">They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="5598a-345">表 7 會顯示的步驟和結果定義此範例的區域網路位址空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="5598a-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="5598a-346">**步驟**</span><span class="sxs-lookup"><span data-stu-id="5598a-346">**Step**</span></span>|<span data-ttu-id="5598a-347">**Results**</span><span class="sxs-lookup"><span data-stu-id="5598a-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="5598a-348">1.清單不是 VNet 位址空間的根空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="5598a-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="5598a-349">172.16.0.0/12 和 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="5598a-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="5598a-350">2.列出變數的八位元，但不包括最後的使用八位元的 VNet 位址空間中的不重疊前置詞。</span><span class="sxs-lookup"><span data-stu-id="5598a-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="5598a-351">10.0.0.0/16、 10.1.0.0/16...]10.99.0.0/16、 10.101.0.0/16...]10.254.0.0/16，10.255.0.0/16 （255 的首碼，已略過 10.100.0.0/16）</span><span class="sxs-lookup"><span data-stu-id="5598a-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="5598a-352">3.清單內的最後一個使用八位元 VNet 位址空間的不重疊前置詞。</span><span class="sxs-lookup"><span data-stu-id="5598a-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="5598a-353">10.100.0.0/24、 10.100.1.0/24...]10.100.99.0/24、 10.100.101.0/24...]10.100.254.0/24，10.100.0.255.0/24 （255 的首碼，已略過 10.100.100.0/24）</span><span class="sxs-lookup"><span data-stu-id="5598a-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="5598a-354">**表 7： 範例本機位址網路空間**</span><span class="sxs-lookup"><span data-stu-id="5598a-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="5598a-355">步驟 6： 設定內部 DNS 伺服器的 DNS 複寫裝載於 Azure 中的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5598a-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="5598a-356">若要確保內部電腦可以解析的以 Azure 為基礎的伺服器名稱，以及以 Azure 為基礎的伺服器可以解析的內部電腦名稱，設定：</span><span class="sxs-lookup"><span data-stu-id="5598a-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="5598a-357">轉寄至內部 DNS 伺服器 VNet 中的 DNS 伺服器</span><span class="sxs-lookup"><span data-stu-id="5598a-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="5598a-358">適當的區域之間 DNS 伺服器的內部和 VNet 中的 DNS 複寫</span><span class="sxs-lookup"><span data-stu-id="5598a-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="5598a-359">**圖 17: DNS 複寫和轉送的跨單位 VNet 的 DNS 伺服器**</span><span class="sxs-lookup"><span data-stu-id="5598a-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![圖 17：跨部署 Azure 虛擬網路中 DNS 伺服器的 DNS 複寫和轉送](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="5598a-361">圖 17 顯示跨單位 VNet 的 DNS 伺服器，在內部部署網路和 VNet 中子網路上。</span><span class="sxs-lookup"><span data-stu-id="5598a-361">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet.</span></span> <span data-ttu-id="5598a-362">DNS 複寫和轉送已設定兩部 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5598a-362">DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="5598a-363">步驟 7： 決定使用強制通道。</span><span class="sxs-lookup"><span data-stu-id="5598a-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="5598a-364">Azure 的子網路的預設系統路由指向網際網路。</span><span class="sxs-lookup"><span data-stu-id="5598a-364">The default system route for Azure subnets points to the Internet.</span></span> <span data-ttu-id="5598a-365">若要確保從虛擬機器中的所有流量都會透過跨單位連線，請使用預設路由，使用 Azure 閘道作為其下一個躍點的位址建立路由表。</span><span class="sxs-lookup"><span data-stu-id="5598a-365">To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address.</span></span> <span data-ttu-id="5598a-366">您然後關聯子網路的路由表。</span><span class="sxs-lookup"><span data-stu-id="5598a-366">You then associate the route table with the subnet.</span></span> <span data-ttu-id="5598a-367">這稱為 「 強制通道。</span><span class="sxs-lookup"><span data-stu-id="5598a-367">This is known as forced tunneling.</span></span> <span data-ttu-id="5598a-368">如需詳細資訊，請參閱 < <b0>Configure 強制通道</b0>。</span><span class="sxs-lookup"><span data-stu-id="5598a-368">For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="5598a-369">**圖 18： 使用者定義路由和強制通道跨單位 VNet**</span><span class="sxs-lookup"><span data-stu-id="5598a-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![圖 18：跨部署 Azure 虛擬網路的使用者定義路由和強制通道](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="5598a-371">圖 18 顯示跨單位 VNet，以指向 Azure 閘道子網路的使用者定義路由。</span><span class="sxs-lookup"><span data-stu-id="5598a-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="5598a-372">Azure 中的 SharePoint Server 2016 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="5598a-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="5598a-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="5598a-373"></span></span>

<span data-ttu-id="5598a-374">內部網路裝載在 Azure IaaS 中的 IT 工作負載的範例為高可用性、 多層式 SharePoint Server 2016 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="5598a-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="5598a-375">**圖 19: 高可用性內部網路 SharePoint Server 2016 伺服器陣列 Azure IaaS 中**</span><span class="sxs-lookup"><span data-stu-id="5598a-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS 中的高可用性 SharePoint Server 2016 伺服器陣列](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="5598a-377">圖 19 顯示部署前端和資料層級會使用內部負載平衡器跨單位 VNet 中的 SharePoint Server 2016 伺服器陣列的九個伺服器。</span><span class="sxs-lookup"><span data-stu-id="5598a-377">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers.</span></span> <span data-ttu-id="5598a-378">如需詳細資訊，包括逐步設計和部署的指示，請參閱 < <b0>Microsoft Azure 中的 SharePoint Server 2016</b0>。</span><span class="sxs-lookup"><span data-stu-id="5598a-378">For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure).</span></span>
  
> [!TIP]
> <span data-ttu-id="5598a-379">若要在模擬的跨單位 VNet 中建立單一伺服器 SharePoint Server 2016 伺服器陣列，請參閱[Azure 開發/測試環境中的內部網路 SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)。</span><span class="sxs-lookup"><span data-stu-id="5598a-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment).</span></span> 
  
<span data-ttu-id="5598a-380">如需其他範例虛擬跨單位 azure 虛擬機器上部署的 IT 工作負載的網路，請參閱[Azure IaaS 的混合式雲端案例](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas)。</span><span class="sxs-lookup"><span data-stu-id="5598a-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://docs.microsoft.com/office365/enterprise/hybrid-cloud-scenarios-for-azure-iaas).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5598a-381">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5598a-381">See also</span></span>

[<span data-ttu-id="5598a-382">Microsoft Cloud Networking for Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="5598a-382">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="5598a-383">Microsoft Cloud IT 架構資源</span><span class="sxs-lookup"><span data-stu-id="5598a-383">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


