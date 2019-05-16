---
title: 高可用性同盟的驗證階段 1 設定 Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 摘要： 設定主機高可用性的 Microsoft Azure 基礎結構的 Office 365 同盟的驗證。
ms.openlocfilehash: 8b6511a3ce23a352b59a0e9a89f8f9901897391f
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067499"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="e8afd-103">高可用性同盟驗證階段 1：設定 Azure</span><span class="sxs-lookup"><span data-stu-id="e8afd-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="e8afd-104">**摘要：** 設定 Microsoft Azure 基礎結構，以主應用程式的 Office 365 的高可用性同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="e8afd-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="e8afd-105">在這個階段，您會建立資源群組，將在階段 2、 3 和 4 中裝載虛擬機器的 Azure 中的虛擬網路 (VNet) 和可用性設定。</span><span class="sxs-lookup"><span data-stu-id="e8afd-105">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4.</span></span> <span data-ttu-id="e8afd-106">您必須完成此階段，才可繼續在[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="e8afd-106">You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="e8afd-107">所有階段，請參閱[在 Azure 中的 Office 365 部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="e8afd-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="e8afd-108">Azure 必須佈建與以下基本元件：</span><span class="sxs-lookup"><span data-stu-id="e8afd-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="e8afd-109">資源群組</span><span class="sxs-lookup"><span data-stu-id="e8afd-109">Resource groups</span></span>
    
- <span data-ttu-id="e8afd-110">跨單位 Azure 虛擬網路 (VNet) 與裝載 Azure 虛擬機器的子網路</span><span class="sxs-lookup"><span data-stu-id="e8afd-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="e8afd-111">用於執行子網路隔離的網路安全性群組</span><span class="sxs-lookup"><span data-stu-id="e8afd-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="e8afd-112">可用性設定組</span><span class="sxs-lookup"><span data-stu-id="e8afd-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="e8afd-113">設定 Azure 元件</span><span class="sxs-lookup"><span data-stu-id="e8afd-113">Configure Azure components</span></span>

<span data-ttu-id="e8afd-114">在開始設定 Azure 元件之前，填寫下列表格。</span><span class="sxs-lookup"><span data-stu-id="e8afd-114">Before you begin configuring Azure components, fill in the following tables.</span></span> <span data-ttu-id="e8afd-115">為了可在設定 Azure 的程序中協助您，請列印此節並記下所需資訊，或將此節複製到一份文件並加以填寫。</span><span class="sxs-lookup"><span data-stu-id="e8afd-115">To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in.</span></span> <span data-ttu-id="e8afd-116">對於 VNet 的設定，填寫表格 V。</span><span class="sxs-lookup"><span data-stu-id="e8afd-116">For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="e8afd-117">**Item**</span><span class="sxs-lookup"><span data-stu-id="e8afd-117">**Item**</span></span>|<span data-ttu-id="e8afd-118">**組態設定**</span><span class="sxs-lookup"><span data-stu-id="e8afd-118">**Configuration setting**</span></span>|<span data-ttu-id="e8afd-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="e8afd-119">**Description**</span></span>|<span data-ttu-id="e8afd-120">**值**</span><span class="sxs-lookup"><span data-stu-id="e8afd-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="e8afd-121">1.</span><span class="sxs-lookup"><span data-stu-id="e8afd-121">1.</span></span>  <br/> |<span data-ttu-id="e8afd-122">VNet 名稱</span><span class="sxs-lookup"><span data-stu-id="e8afd-122">VNet name</span></span>  <br/> |<span data-ttu-id="e8afd-123">要指派給 VNet （例如 FedAuthNet） 的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8afd-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-124">2.</span><span class="sxs-lookup"><span data-stu-id="e8afd-124">2.</span></span>  <br/> |<span data-ttu-id="e8afd-125">VNet 位置</span><span class="sxs-lookup"><span data-stu-id="e8afd-125">VNet location</span></span>  <br/> |<span data-ttu-id="e8afd-126">區域性 Azure 資料中心將包含虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="e8afd-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-127">3.</span><span class="sxs-lookup"><span data-stu-id="e8afd-127">3.</span></span>  <br/> |<span data-ttu-id="e8afd-128">VPN 裝置 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-128">VPN device IP address</span></span>  <br/> |<span data-ttu-id="e8afd-129">網際網路上 VPN 裝置介面的公用 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-129">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-130">4.</span><span class="sxs-lookup"><span data-stu-id="e8afd-130">4.</span></span>  <br/> |<span data-ttu-id="e8afd-131">VNet 位址空間</span><span class="sxs-lookup"><span data-stu-id="e8afd-131">VNet address space</span></span>  <br/> |<span data-ttu-id="e8afd-p103">虛擬網路的位址空間。請與您的 IT 部門合作以決定此位址空間。</span><span class="sxs-lookup"><span data-stu-id="e8afd-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-134">5.</span><span class="sxs-lookup"><span data-stu-id="e8afd-134">5.</span></span>  <br/> |<span data-ttu-id="e8afd-135">IPsec 共用金鑰</span><span class="sxs-lookup"><span data-stu-id="e8afd-135">IPsec shared key</span></span>  <br/> |<span data-ttu-id="e8afd-p104">32 個字元的隨機英數字元字串，用以驗證站台對站台 VPN 連線的兩端站台。請與您的 IT 或安全性部門合作，以決定此金鑰值。或者，請參閱[建立隨機字串以作為 IPsec 的預先共用金鑰](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)。  </span><span class="sxs-lookup"><span data-stu-id="e8afd-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="e8afd-139">**表格 V：跨單位虛擬網路設定**</span><span class="sxs-lookup"><span data-stu-id="e8afd-139">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="e8afd-p105">下一步，針對此解決方案的子網路填寫表格 S。所有位址空間應是無類別網域間路由選擇 (CIDR) 格式 (也稱為網路前置詞格式)。例如 10.24.64.0/20。</span><span class="sxs-lookup"><span data-stu-id="e8afd-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="e8afd-143">針對的前三個的子網路，指定的名稱及虛擬網路位址空間為基礎的單一 IP 位址空間。</span><span class="sxs-lookup"><span data-stu-id="e8afd-143">For the first three subnets, specify a name and a single IP address space based on the virtual network address space.</span></span> <span data-ttu-id="e8afd-144">針對閘道子網路，判斷 27 位元位址空間 (使用/27 前置長度) Azure 閘道子網路下列項目：</span><span class="sxs-lookup"><span data-stu-id="e8afd-144">For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="e8afd-145">將 VNet 位址空間中的變數位元數設為 1 (閘道子網路正在使用的位元數)，其餘位元數設為 0。</span><span class="sxs-lookup"><span data-stu-id="e8afd-145">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="e8afd-146">將結果位元數轉換為小數，使用設定為閘道子網路大小的前置長度將其表示為位址空間。</span><span class="sxs-lookup"><span data-stu-id="e8afd-146">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="e8afd-147">請參閱 < <b0>Azure 閘道子網路的位址空間計算機</b0>PowerShell 命令區塊和 C# 或 Python 主控台應用程式，為您執行此計算。</span><span class="sxs-lookup"><span data-stu-id="e8afd-147">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="e8afd-148">請與您的 IT 部門合作，以從虛擬網路位址空間判斷這些位址空間。</span><span class="sxs-lookup"><span data-stu-id="e8afd-148">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="e8afd-149">**Item**</span><span class="sxs-lookup"><span data-stu-id="e8afd-149">**Item**</span></span>|<span data-ttu-id="e8afd-150">**子網路名稱**</span><span class="sxs-lookup"><span data-stu-id="e8afd-150">**Subnet name**</span></span>|<span data-ttu-id="e8afd-151">**子網路位址空間**</span><span class="sxs-lookup"><span data-stu-id="e8afd-151">**Subnet address space**</span></span>|<span data-ttu-id="e8afd-152">**用途**</span><span class="sxs-lookup"><span data-stu-id="e8afd-152">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="e8afd-153">1.</span><span class="sxs-lookup"><span data-stu-id="e8afd-153">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-154">使用的子網路的 Active Directory 網域服務 (AD DS) 網域控制站和 DirSync 伺服器虛擬機器 (Vm)。</span><span class="sxs-lookup"><span data-stu-id="e8afd-154">The subnet used by the Active Directory Domain Services (AD DS) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="e8afd-155">2.</span><span class="sxs-lookup"><span data-stu-id="e8afd-155">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-156">AD FS Vm 所使用的子網路。</span><span class="sxs-lookup"><span data-stu-id="e8afd-156">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="e8afd-157">3.</span><span class="sxs-lookup"><span data-stu-id="e8afd-157">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-158">Web 應用程式 proxy Vm 使用的子網路。</span><span class="sxs-lookup"><span data-stu-id="e8afd-158">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="e8afd-159">4.</span><span class="sxs-lookup"><span data-stu-id="e8afd-159">4.</span></span>  <br/> |<span data-ttu-id="e8afd-160">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="e8afd-160">GatewaySubnet</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-161">Azure 閘道 Vm 使用的子網路。</span><span class="sxs-lookup"><span data-stu-id="e8afd-161">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="e8afd-162">**表格 S：虛擬網路中的子網路**</span><span class="sxs-lookup"><span data-stu-id="e8afd-162">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="e8afd-163">下一步，針對指派至虛擬機器和負載平衡器執行個體的靜態 IP 位址填寫表格 I。</span><span class="sxs-lookup"><span data-stu-id="e8afd-163">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="e8afd-164">**Item**</span><span class="sxs-lookup"><span data-stu-id="e8afd-164">**Item**</span></span>|<span data-ttu-id="e8afd-165">**用途**</span><span class="sxs-lookup"><span data-stu-id="e8afd-165">**Purpose**</span></span>|<span data-ttu-id="e8afd-166">**子網路上的 IP 位址**</span><span class="sxs-lookup"><span data-stu-id="e8afd-166">**IP address on the subnet**</span></span>|<span data-ttu-id="e8afd-167">**值**</span><span class="sxs-lookup"><span data-stu-id="e8afd-167">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="e8afd-168">1.</span><span class="sxs-lookup"><span data-stu-id="e8afd-168">1.</span></span>  <br/> |<span data-ttu-id="e8afd-169">第一個網域控制站的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-169">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="e8afd-170">定義於表格 S 的項目 1 中，子網路位址空間的第四個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-170">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-171">2.</span><span class="sxs-lookup"><span data-stu-id="e8afd-171">2.</span></span>  <br/> |<span data-ttu-id="e8afd-172">第二個網域控制站的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-172">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="e8afd-173">定義於表格 S 的項目 1 中，子網路位址空間的第五個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-173">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-174">3.</span><span class="sxs-lookup"><span data-stu-id="e8afd-174">3.</span></span>  <br/> |<span data-ttu-id="e8afd-175">DirSync 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-175">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="e8afd-176">表格 s 的項目 1 中所定義的子網路的位址空間第六個可能 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-176">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-177">4.</span><span class="sxs-lookup"><span data-stu-id="e8afd-177">4.</span></span>  <br/> |<span data-ttu-id="e8afd-178">AD FS 伺服器內部負載平衡器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-178">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="e8afd-179">定義於表格 S 的項目 2 中，子網路位址空間的第四個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-179">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-180">5.</span><span class="sxs-lookup"><span data-stu-id="e8afd-180">5.</span></span>  <br/> |<span data-ttu-id="e8afd-181">第一部 AD FS 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-181">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="e8afd-182">定義於表格 S 的項目 2 中，子網路位址空間的第五個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-182">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-183">6.</span><span class="sxs-lookup"><span data-stu-id="e8afd-183">6.</span></span>  <br/> |<span data-ttu-id="e8afd-184">第二個 AD FS 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-184">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="e8afd-185">定義於表格 S 的項目 2 中，子網路位址空間的第六個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-185">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-186">7.</span><span class="sxs-lookup"><span data-stu-id="e8afd-186">7.</span></span>  <br/> |<span data-ttu-id="e8afd-187">第一個 web 應用程式 proxy 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-187">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="e8afd-188">定義於表格 S 的項目 3 中，子網路位址空間的第四個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-188">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-189">8.</span><span class="sxs-lookup"><span data-stu-id="e8afd-189">8.</span></span>  <br/> |<span data-ttu-id="e8afd-190">第二個 web 應用程式 proxy 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="e8afd-190">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="e8afd-191">定義於表格 S 的項目 3 中，子網路位址空間的第五個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-191">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="e8afd-192">**表格 I：虛擬網路中的靜態 IP 位址**</span><span class="sxs-lookup"><span data-stu-id="e8afd-192">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="e8afd-193">針對您想要使用一開始設定您的虛擬網路中的網域控制站時您在內部網路中的兩個網域名稱系統 (DNS) 伺服器，填寫表格 d 工時與您的 IT 部門，以決定此清單。</span><span class="sxs-lookup"><span data-stu-id="e8afd-193">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="e8afd-194">**Item**</span><span class="sxs-lookup"><span data-stu-id="e8afd-194">**Item**</span></span>|<span data-ttu-id="e8afd-195">**DNS 伺服器的易記名稱**</span><span class="sxs-lookup"><span data-stu-id="e8afd-195">**DNS server friendly name**</span></span>|<span data-ttu-id="e8afd-196">**DNS 伺服器 IP 位址**</span><span class="sxs-lookup"><span data-stu-id="e8afd-196">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e8afd-197">1.</span><span class="sxs-lookup"><span data-stu-id="e8afd-197">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-198">2.</span><span class="sxs-lookup"><span data-stu-id="e8afd-198">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="e8afd-199">**表格 D：內部部署 DNS 伺服器**</span><span class="sxs-lookup"><span data-stu-id="e8afd-199">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="e8afd-200">若要跨站台對站 VPN 連線，路由傳送到您組織的網路跨內部部署網路封包，您必須設定虛擬網路的本機網路，具有連至所有位址空間 （以 CIDR 標記法） 清單在您的組織內部網路上的位置。</span><span class="sxs-lookup"><span data-stu-id="e8afd-200">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network.</span></span> <span data-ttu-id="e8afd-201">定義區域網路的位址空間清單必須是唯一的，且不可與其他虛擬網路或其他區域網路使用的位址空間重疊。</span><span class="sxs-lookup"><span data-stu-id="e8afd-201">The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="e8afd-p108">針對區域網路位址空間集，請填寫表格 L。請注意，雖已列出三個空白項，但一般來說您會需要更多。請與您的 IT 部門合作以決定此位址空間清單。</span><span class="sxs-lookup"><span data-stu-id="e8afd-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="e8afd-204">**項目**</span><span class="sxs-lookup"><span data-stu-id="e8afd-204">**Item**</span></span>|<span data-ttu-id="e8afd-205">**區域網路位址空間**</span><span class="sxs-lookup"><span data-stu-id="e8afd-205">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e8afd-206">1.</span><span class="sxs-lookup"><span data-stu-id="e8afd-206">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-207">2.</span><span class="sxs-lookup"><span data-stu-id="e8afd-207">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-208">3.</span><span class="sxs-lookup"><span data-stu-id="e8afd-208">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="e8afd-209">**表格 L：區域網路的網址前置詞**</span><span class="sxs-lookup"><span data-stu-id="e8afd-209">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="e8afd-210">現在讓我們開始建置 Azure 基礎結構以裝載您的 Office 365 同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="e8afd-210">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e8afd-p109">[!附註] 下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="e8afd-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="e8afd-213">首先，啟動 Azure PowerShell 提示並登入您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="e8afd-213">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
<span data-ttu-id="e8afd-214">使用下列命令取得訂用帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="e8afd-214">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="e8afd-215">對於較舊版本的 Azure PowerShell，請改為使用此命令。</span><span class="sxs-lookup"><span data-stu-id="e8afd-215">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="e8afd-216">設定 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="e8afd-216">Set your Azure subscription.</span></span> <span data-ttu-id="e8afd-217">取代引號，包括內的所有項目\<和 > 字元，以正確的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8afd-217">Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="e8afd-218">接下來，建立新的資源群組。</span><span class="sxs-lookup"><span data-stu-id="e8afd-218">Next, create the new resource groups.</span></span> <span data-ttu-id="e8afd-219">若要判斷資源群組名稱是否是唯一一組，可使用此命令來列出現有的資源群組。</span><span class="sxs-lookup"><span data-stu-id="e8afd-219">To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="e8afd-220">針對這唯一的一組資源群組名稱，填寫下列表格。</span><span class="sxs-lookup"><span data-stu-id="e8afd-220">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="e8afd-221">**項目**</span><span class="sxs-lookup"><span data-stu-id="e8afd-221">**Item**</span></span>|<span data-ttu-id="e8afd-222">**資源群組名稱**</span><span class="sxs-lookup"><span data-stu-id="e8afd-222">**Resource group name**</span></span>|<span data-ttu-id="e8afd-223">**用途**</span><span class="sxs-lookup"><span data-stu-id="e8afd-223">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e8afd-224">1.</span><span class="sxs-lookup"><span data-stu-id="e8afd-224">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-225">網域控制站</span><span class="sxs-lookup"><span data-stu-id="e8afd-225">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="e8afd-226">2.</span><span class="sxs-lookup"><span data-stu-id="e8afd-226">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-227">AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="e8afd-227">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="e8afd-228">3.</span><span class="sxs-lookup"><span data-stu-id="e8afd-228">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-229">Web 應用程式 proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="e8afd-229">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="e8afd-230">4.</span><span class="sxs-lookup"><span data-stu-id="e8afd-230">4.</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="e8afd-231">基礎結構元素</span><span class="sxs-lookup"><span data-stu-id="e8afd-231">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="e8afd-232">**表格 R：資源群組**</span><span class="sxs-lookup"><span data-stu-id="e8afd-232">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="e8afd-233">使用這些命令建立新的資源群組。</span><span class="sxs-lookup"><span data-stu-id="e8afd-233">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="e8afd-234">接著，建立 Azure 虛擬網路和其子網路。</span><span class="sxs-lookup"><span data-stu-id="e8afd-234">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="e8afd-235">接下來，您建立網路安全性群組的每個具有虛擬機器的子網路。</span><span class="sxs-lookup"><span data-stu-id="e8afd-235">Next, you create network security groups for each subnet that has virtual machines.</span></span> <span data-ttu-id="e8afd-236">若要執行子網路隔離，您可以針對允許或拒絕子網路安全小組流量的特定類型新增規則。</span><span class="sxs-lookup"><span data-stu-id="e8afd-236">To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="e8afd-237">接著，使用以下命令來建立站台對站台 VPN 連線的閘道。</span><span class="sxs-lookup"><span data-stu-id="e8afd-237">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="e8afd-238">個別使用者的聯盟驗證不會仰賴任何內部部署資源。</span><span class="sxs-lookup"><span data-stu-id="e8afd-238">Federated authentication of individual users does not rely on any on-premises resources.</span></span> <span data-ttu-id="e8afd-239">不過，如果此站台對站 VPN 連線變成無法使用，VNet 中的網域控制站也不會收到使用者帳戶和群組在內部部署 Active Directory 網域服務中所做的更新。</span><span class="sxs-lookup"><span data-stu-id="e8afd-239">However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services.</span></span> <span data-ttu-id="e8afd-240">若要確保不是這樣，您可以設定高可用性的站台對站 VPN 連線。</span><span class="sxs-lookup"><span data-stu-id="e8afd-240">To ensure this does not happen, you can configure high availability for your site-to-site VPN connection.</span></span> <span data-ttu-id="e8afd-241">如需詳細資訊，請參閱[高度可用的跨單位和 VNet-VNet 連線](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="e8afd-241">For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="e8afd-242">接著，從顯示的以下命令中，記錄虛擬網路 Azure VPN 閘道的公用 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-242">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="e8afd-p114">接著，設定內部部署 VPN 裝置與 Azure VPN 閘道連線。如需詳細資訊，請參閱[設定您的 VPN 裝置](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="e8afd-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="e8afd-245">若要設定您的內部部署 VPN 裝置，您需要下列項目︰</span><span class="sxs-lookup"><span data-stu-id="e8afd-245">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="e8afd-246">Azure VPN 閘道的公用 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="e8afd-246">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="e8afd-247">站台對站台 VPN 連線的 IPsec 預先共用金鑰 (表格 V - 項目 5 - 值欄)。</span><span class="sxs-lookup"><span data-stu-id="e8afd-247">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="e8afd-p115">下一步，確認從內部部署網路可觸及虛擬網路的位址空間。一般來說，完成方式是新增路由以將虛擬網路位址空間對應至 VPN 裝置，然後將此路由傳達給其餘組織網路的路由基礎結構。請與您的 IT 部門合作以決定如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="e8afd-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="e8afd-251">接下來，定義三個可用性設定組的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8afd-251">Next, define the names of three availability sets.</span></span> <span data-ttu-id="e8afd-252">填寫表格 A。</span><span class="sxs-lookup"><span data-stu-id="e8afd-252">Fill out Table A.</span></span> 
  
|<span data-ttu-id="e8afd-253">**項目**</span><span class="sxs-lookup"><span data-stu-id="e8afd-253">**Item**</span></span>|<span data-ttu-id="e8afd-254">**用途**</span><span class="sxs-lookup"><span data-stu-id="e8afd-254">**Purpose**</span></span>|<span data-ttu-id="e8afd-255">**可用性設定組名稱**</span><span class="sxs-lookup"><span data-stu-id="e8afd-255">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e8afd-256">1.</span><span class="sxs-lookup"><span data-stu-id="e8afd-256">1.</span></span>  <br/> |<span data-ttu-id="e8afd-257">網域控制站</span><span class="sxs-lookup"><span data-stu-id="e8afd-257">Domain controllers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-258">2.</span><span class="sxs-lookup"><span data-stu-id="e8afd-258">2.</span></span>  <br/> |<span data-ttu-id="e8afd-259">AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="e8afd-259">AD FS servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="e8afd-260">3.</span><span class="sxs-lookup"><span data-stu-id="e8afd-260">3.</span></span>  <br/> |<span data-ttu-id="e8afd-261">Web 應用程式 proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="e8afd-261">Web application proxy servers</span></span>  <br/> |![](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="e8afd-262">**表格 A：可用性設定組**</span><span class="sxs-lookup"><span data-stu-id="e8afd-262">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="e8afd-263">當您在階段 2、3 和 4 中建立虛擬機器時，將會需要這些名稱。</span><span class="sxs-lookup"><span data-stu-id="e8afd-263">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="e8afd-264">使用這些 Azure PowerShell 命令建立新的可用性設定組。</span><span class="sxs-lookup"><span data-stu-id="e8afd-264">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="e8afd-265">以下是成功完成此階段的設定結果。</span><span class="sxs-lookup"><span data-stu-id="e8afd-265">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="e8afd-266">**階段 1: Azure 基礎結構的 Office 365 的高可用性同盟驗證**</span><span class="sxs-lookup"><span data-stu-id="e8afd-266">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![階段 1 的 Office 365 的高可用性同盟驗證在 Azure 中使用 Azure 基礎結構](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="e8afd-268">下一步</span><span class="sxs-lookup"><span data-stu-id="e8afd-268">Next step</span></span>

<span data-ttu-id="e8afd-269">使用[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)以繼續設定此工作負載。</span><span class="sxs-lookup"><span data-stu-id="e8afd-269">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e8afd-270">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8afd-270">See Also</span></span>

[<span data-ttu-id="e8afd-271">Azure 中的 Office 365 高可用性同盟驗證</span><span class="sxs-lookup"><span data-stu-id="e8afd-271">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="e8afd-272">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="e8afd-272">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e8afd-273">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="e8afd-273">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="e8afd-274">了解 Office 365 身分識別和 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e8afd-274">Understanding Office 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


