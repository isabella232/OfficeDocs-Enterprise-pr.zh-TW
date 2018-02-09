---
title: "高可用性同盟的驗證階段 1 設定 Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "摘要： 設定主機高可用性的 Microsoft Azure 基礎結構的 Office 365 同盟的驗證。"
ms.openlocfilehash: 829bad1dadc3c3987e42d32f8afe8c1f76459ff0
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="dd20b-103">高可用性同盟驗證階段 1：設定 Azure</span><span class="sxs-lookup"><span data-stu-id="dd20b-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="dd20b-104">**摘要：**設定 Office 365 的主機同盟的高可用性驗證 Microsoft Azure 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="dd20b-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="dd20b-p101">在此階段中，您會建立資源群組、 儲存帳戶、 階段 2、 3 及 4 主控虛擬機器的 Azure 中的虛擬網路 (VNet) 和可用性設定。您必須完成此階段中的將移入之前[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p101">In this phase, you create the resource groups, storage accounts, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="dd20b-108">Azure 必須佈建使用這些基本元件：</span><span class="sxs-lookup"><span data-stu-id="dd20b-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="dd20b-109">資源群組</span><span class="sxs-lookup"><span data-stu-id="dd20b-109">Resource groups</span></span>
    
- <span data-ttu-id="dd20b-110">跨單位 Azure 虛擬網路 (VNet)，包含裝載 Azure 虛擬機器的子網路</span><span class="sxs-lookup"><span data-stu-id="dd20b-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="dd20b-111">用於執行子網路隔離的網路安全性群組</span><span class="sxs-lookup"><span data-stu-id="dd20b-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="dd20b-112">可用性設定組</span><span class="sxs-lookup"><span data-stu-id="dd20b-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="dd20b-113">設定 Azure 元件</span><span class="sxs-lookup"><span data-stu-id="dd20b-113">Configure Azure components</span></span>

<span data-ttu-id="dd20b-p102">開始設定 Azure 元件之前，請填入如下表所示。若要協助您在設定 Azure 的程序，此區段列印和寫下所需的資訊或將本節複製到文件並填入其。針對 VNet 的設定，填入表格 V。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="dd20b-117">**項目**</span><span class="sxs-lookup"><span data-stu-id="dd20b-117">**Item**</span></span>|<span data-ttu-id="dd20b-118">**組態設定**</span><span class="sxs-lookup"><span data-stu-id="dd20b-118">**Configuration setting**</span></span>|<span data-ttu-id="dd20b-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="dd20b-119">**Description**</span></span>|<span data-ttu-id="dd20b-120">**值**</span><span class="sxs-lookup"><span data-stu-id="dd20b-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="dd20b-121">1.</span><span class="sxs-lookup"><span data-stu-id="dd20b-121">1.</span></span>  <br/> |<span data-ttu-id="dd20b-122">VNet 名稱</span><span class="sxs-lookup"><span data-stu-id="dd20b-122">VNet name</span></span>  <br/> |<span data-ttu-id="dd20b-123">要指派給 VNet 的名稱 (例如 FedAuthNet)。</span><span class="sxs-lookup"><span data-stu-id="dd20b-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |<span data-ttu-id="dd20b-124">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-124"></span></span>  <br/> |
|<span data-ttu-id="dd20b-125">2.</span><span class="sxs-lookup"><span data-stu-id="dd20b-125">2.</span></span>  <br/> |<span data-ttu-id="dd20b-126">VNet 位置</span><span class="sxs-lookup"><span data-stu-id="dd20b-126">VNet location</span></span>  <br/> |<span data-ttu-id="dd20b-127">將包含虛擬網路的區域性 Azure 資料中心</span><span class="sxs-lookup"><span data-stu-id="dd20b-127">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |<span data-ttu-id="dd20b-128">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-128"></span></span>  <br/> |
|<span data-ttu-id="dd20b-129">3.</span><span class="sxs-lookup"><span data-stu-id="dd20b-129">3.</span></span>  <br/> |<span data-ttu-id="dd20b-130">VPN 裝置 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-130">VPN device IP address</span></span>  <br/> |<span data-ttu-id="dd20b-131">網際網路上 VPN 裝置介面的公用 IPv4 位址。 </span><span class="sxs-lookup"><span data-stu-id="dd20b-131">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |<span data-ttu-id="dd20b-132">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-132"></span></span>  <br/> |
|<span data-ttu-id="dd20b-133">4.</span><span class="sxs-lookup"><span data-stu-id="dd20b-133">4.</span></span>  <br/> |<span data-ttu-id="dd20b-134">VNet 位址空間</span><span class="sxs-lookup"><span data-stu-id="dd20b-134">VNet address space</span></span>  <br/> |<span data-ttu-id="dd20b-p103">虛擬網路的位址空間。請與您的 IT 部門合作以決定此位址空間。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |<span data-ttu-id="dd20b-137">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-137"></span></span>  <br/> |
|<span data-ttu-id="dd20b-138">5.</span><span class="sxs-lookup"><span data-stu-id="dd20b-138">5.</span></span>  <br/> |<span data-ttu-id="dd20b-139">IPsec 共用金鑰</span><span class="sxs-lookup"><span data-stu-id="dd20b-139">IPsec shared key</span></span>  <br/> |<span data-ttu-id="dd20b-p104">32 個字元隨機、 英數字元字串將用來驗證網站 VPN 連線的兩側。使用您的 IT 或安全性部門決定此機碼的值。或者，請參閱[建立 IPsec 預先共用金鑰的隨機字串](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="dd20b-143">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-143"></span></span>  <br/> |
   
 <span data-ttu-id="dd20b-144">**表格 V：跨單位虛擬網路設定**</span><span class="sxs-lookup"><span data-stu-id="dd20b-144">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="dd20b-p105">下一步，針對此解決方案的子網路填寫表格 S。所有位址空間應是無類別網域間路由選擇 (CIDR) 格式 (也稱為網路前置詞格式)。例如 10.24.64.0/20。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="dd20b-p106">針對前三個子網路，請根據虛擬網路位址空間指定名稱和單一 IP 位址空間。針對閘道子網路，請根據以下項目決定 Azure 閘道子網路的 27 位元位址空間 (使用 /27 前置長度)。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="dd20b-150">將 VNet 位址空間中的變數位元數設為 1 (閘道子網路正在使用的位元數)，其餘位元數設為 0。</span><span class="sxs-lookup"><span data-stu-id="dd20b-150">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="dd20b-151">將結果位元數轉換為小數，使用設定為閘道子網路大小的前置長度將其表示為位址空間。</span><span class="sxs-lookup"><span data-stu-id="dd20b-151">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="dd20b-152">請參閱[Azure 閘道的子網路的位址空間計算器](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)PowerShell 命令封鎖與您執行此計算的 C# 或 Python 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dd20b-152">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="dd20b-153">請與您的 IT 部門合作，以從虛擬網路位址空間判斷這些位址空間。</span><span class="sxs-lookup"><span data-stu-id="dd20b-153">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="dd20b-154">**項目**</span><span class="sxs-lookup"><span data-stu-id="dd20b-154">**Item**</span></span>|<span data-ttu-id="dd20b-155">**子網路名稱**</span><span class="sxs-lookup"><span data-stu-id="dd20b-155">**Subnet name**</span></span>|<span data-ttu-id="dd20b-156">**子網路位址空間**</span><span class="sxs-lookup"><span data-stu-id="dd20b-156">**Subnet address space**</span></span>|<span data-ttu-id="dd20b-157">**用途**</span><span class="sxs-lookup"><span data-stu-id="dd20b-157">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="dd20b-158">1.</span><span class="sxs-lookup"><span data-stu-id="dd20b-158">1.</span></span>  <br/> |<span data-ttu-id="dd20b-159">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-159"></span></span>  <br/> |<span data-ttu-id="dd20b-160">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-160"></span></span>  <br/> |<span data-ttu-id="dd20b-161">Windows Server Active Directory (AD) 網域控制站和 DirSync 伺服器虛擬機器 (VM) 使用的子網路。</span><span class="sxs-lookup"><span data-stu-id="dd20b-161">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="dd20b-162">2.</span><span class="sxs-lookup"><span data-stu-id="dd20b-162">2.</span></span>  <br/> |<span data-ttu-id="dd20b-163">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-163"></span></span>  <br/> |<span data-ttu-id="dd20b-164">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-164"></span></span>  <br/> |<span data-ttu-id="dd20b-165">AD FS VM 使用的子網路。</span><span class="sxs-lookup"><span data-stu-id="dd20b-165">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="dd20b-166">3.</span><span class="sxs-lookup"><span data-stu-id="dd20b-166">3.</span></span>  <br/> |<span data-ttu-id="dd20b-167">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-167"></span></span>  <br/> |<span data-ttu-id="dd20b-168">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-168"></span></span>  <br/> |<span data-ttu-id="dd20b-169">Web 應用程式 Proxy VM 使用的子網路。</span><span class="sxs-lookup"><span data-stu-id="dd20b-169">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="dd20b-170">4.</span><span class="sxs-lookup"><span data-stu-id="dd20b-170">4.</span></span>  <br/> |<span data-ttu-id="dd20b-171">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="dd20b-171">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="dd20b-172">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-172"></span></span>  <br/> |<span data-ttu-id="dd20b-173">Azure 閘道 VM 使用的子網路。</span><span class="sxs-lookup"><span data-stu-id="dd20b-173">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="dd20b-174">**表格 S：虛擬網路中的子網路**</span><span class="sxs-lookup"><span data-stu-id="dd20b-174">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="dd20b-175">下一步，針對指派至虛擬機器和負載平衡器執行個體的靜態 IP 位址填寫表格 I。</span><span class="sxs-lookup"><span data-stu-id="dd20b-175">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="dd20b-176">**項目**</span><span class="sxs-lookup"><span data-stu-id="dd20b-176">**Item**</span></span>|<span data-ttu-id="dd20b-177">**用途**</span><span class="sxs-lookup"><span data-stu-id="dd20b-177">**Purpose**</span></span>|<span data-ttu-id="dd20b-178">**子網路上的 IP 位址**</span><span class="sxs-lookup"><span data-stu-id="dd20b-178">**IP address on the subnet**</span></span>|<span data-ttu-id="dd20b-179">**值**</span><span class="sxs-lookup"><span data-stu-id="dd20b-179">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="dd20b-180">1.</span><span class="sxs-lookup"><span data-stu-id="dd20b-180">1.</span></span>  <br/> |<span data-ttu-id="dd20b-181">第一個網域控制站的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-181">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="dd20b-182">定義於表格 S 的項目 1 中，子網路位址空間的第四個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-182">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-183">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-183"></span></span>  <br/> |
|<span data-ttu-id="dd20b-184">2.</span><span class="sxs-lookup"><span data-stu-id="dd20b-184">2.</span></span>  <br/> |<span data-ttu-id="dd20b-185">第二個網域控制站的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-185">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="dd20b-186">定義於表格 S 的項目 1 中，子網路位址空間的第五個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-186">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-187">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-187"></span></span>  <br/> |
|<span data-ttu-id="dd20b-188">3.</span><span class="sxs-lookup"><span data-stu-id="dd20b-188">3.</span></span>  <br/> |<span data-ttu-id="dd20b-189">DirSync 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-189">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="dd20b-190">定義於表格 S 的項目 1 中，子網路位址空間的第六個可能 IP 位址。 </span><span class="sxs-lookup"><span data-stu-id="dd20b-190">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-191">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-191"></span></span>  <br/> |
|<span data-ttu-id="dd20b-192">4.</span><span class="sxs-lookup"><span data-stu-id="dd20b-192">4.</span></span>  <br/> |<span data-ttu-id="dd20b-193">AD FS 伺服器內部負載平衡器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-193">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="dd20b-194">定義於表格 S 的項目 2 中，子網路位址空間的第四個可能 IP 位址。 </span><span class="sxs-lookup"><span data-stu-id="dd20b-194">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-195">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-195"></span></span>  <br/> |
|<span data-ttu-id="dd20b-196">5.</span><span class="sxs-lookup"><span data-stu-id="dd20b-196">5.</span></span>  <br/> |<span data-ttu-id="dd20b-197">第一個 AD FS 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-197">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="dd20b-198">定義於表格 S 的項目 2 中，子網路位址空間的第五個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-198">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-199">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-199"></span></span>  <br/> |
|<span data-ttu-id="dd20b-200">6.</span><span class="sxs-lookup"><span data-stu-id="dd20b-200">6.</span></span>  <br/> |<span data-ttu-id="dd20b-201">第二個 AD FS 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-201">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="dd20b-202">定義於表格 S 的項目 2 中，子網路位址空間的第六個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-202">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-203">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-203"></span></span>  <br/> |
|<span data-ttu-id="dd20b-204">7.</span><span class="sxs-lookup"><span data-stu-id="dd20b-204">7.</span></span>  <br/> |<span data-ttu-id="dd20b-205">第一個 Web 應用程式 Proxy 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-205">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="dd20b-206">定義於表格 S 的項目 3 中，子網路位址空間的第四個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-206">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-207">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-207"></span></span>  <br/> |
|<span data-ttu-id="dd20b-208">8。</span><span class="sxs-lookup"><span data-stu-id="dd20b-208">8.</span></span>  <br/> |<span data-ttu-id="dd20b-209">第二個 Web 應用程式 Proxy 伺服器的靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="dd20b-209">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="dd20b-210">定義於表格 S 的項目 3 中，子網路位址空間的第五個可能 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-210">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="dd20b-211">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-211"></span></span>  <br/> |
   
 <span data-ttu-id="dd20b-212">**虛擬網路中的表格 i： 靜態 IP 位址**</span><span class="sxs-lookup"><span data-stu-id="dd20b-212">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="dd20b-213">針對初次在虛擬網路中設定網域控制站時，您要在內部部署網路中使用的網域名稱系統 (DNS) 伺服器，填寫表格 D。請與您的 IT 部門合作以決定此清單。</span><span class="sxs-lookup"><span data-stu-id="dd20b-213">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="dd20b-214">**項目**</span><span class="sxs-lookup"><span data-stu-id="dd20b-214">**Item**</span></span>|<span data-ttu-id="dd20b-215">**DNS 伺服器的易記名稱**</span><span class="sxs-lookup"><span data-stu-id="dd20b-215">**DNS server friendly name**</span></span>|<span data-ttu-id="dd20b-216">**DNS 伺服器 IP 位址**</span><span class="sxs-lookup"><span data-stu-id="dd20b-216">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="dd20b-217">1.</span><span class="sxs-lookup"><span data-stu-id="dd20b-217">1.</span></span>  <br/> |<span data-ttu-id="dd20b-218">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-218"></span></span>  <br/> |<span data-ttu-id="dd20b-219">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-219"></span></span>  <br/> |
|<span data-ttu-id="dd20b-220">2.</span><span class="sxs-lookup"><span data-stu-id="dd20b-220">2.</span></span>  <br/> |<span data-ttu-id="dd20b-221">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-221"></span></span>  <br/> |<span data-ttu-id="dd20b-222">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-222"></span></span>  <br/> |
   
 <span data-ttu-id="dd20b-223">**表格 D：內部部署 DNS 伺服器**</span><span class="sxs-lookup"><span data-stu-id="dd20b-223">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="dd20b-p107">若要透過站台對站台的 VPN 連線，將封包從跨單位網路路由傳送至組織網路，您必須透過區域網路來設定虛擬網路，該區域網路會包含組織內部部署網路上所有可觸及位置的位址空間 (以 CIDR 標記法) 清單。定義區域網路的位址空間清單必須是唯一的，且不可與其他虛擬網路或其他區域網路使用的位址空間重疊。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="dd20b-p108">針對區域網路位址空間集，請填寫表格 L。請注意，雖已列出三個空白項，但一般來說您會需要更多。請與您的 IT 部門合作以決定此位址空間清單。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="dd20b-228">**項目**</span><span class="sxs-lookup"><span data-stu-id="dd20b-228">**Item**</span></span>|<span data-ttu-id="dd20b-229">**區域網路位址空間**</span><span class="sxs-lookup"><span data-stu-id="dd20b-229">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="dd20b-230">1.</span><span class="sxs-lookup"><span data-stu-id="dd20b-230">1.</span></span>  <br/> |<span data-ttu-id="dd20b-231">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-231"></span></span>  <br/> |
|<span data-ttu-id="dd20b-232">2.</span><span class="sxs-lookup"><span data-stu-id="dd20b-232">2.</span></span>  <br/> |<span data-ttu-id="dd20b-233">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-233"></span></span>  <br/> |
|<span data-ttu-id="dd20b-234">3.</span><span class="sxs-lookup"><span data-stu-id="dd20b-234">3.</span></span>  <br/> |<span data-ttu-id="dd20b-235">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-235"></span></span>  <br/> |
   
 <span data-ttu-id="dd20b-236">**表格 L：區域網路的網址前置詞**</span><span class="sxs-lookup"><span data-stu-id="dd20b-236">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="dd20b-237">現在讓我們開始建置 Azure 基礎結構以裝載您的 Office 365 同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="dd20b-237">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="dd20b-p109">下列的命令會使用 Azure PowerShell 的最新版本。請參閱[開始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="dd20b-240">首先，啟動 Azure PowerShell 提示並登入您的帳戶。</span><span class="sxs-lookup"><span data-stu-id="dd20b-240">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="dd20b-241">對於包含本文及產生就緒-隨選即用 PowerShell 命令封鎖根據自訂設定 Microsoft Excel 設定活頁簿中的 PowerShell 命令的所有文字檔案，請參閱 ＜[同盟驗證 Office 365 中Azure 部署套件](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。</span><span class="sxs-lookup"><span data-stu-id="dd20b-241">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="dd20b-242">使用下列命令取得訂用帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="dd20b-242">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="dd20b-243">Azure PowerShell 較舊版本，請改用以下命令。</span><span class="sxs-lookup"><span data-stu-id="dd20b-243">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="dd20b-p110">設定您的 Azure 訂閱。括住，包括所有內容取代為\<和 > 具有正確的名稱的字元。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="dd20b-p111">下一步，建立新的資源群組。若要判斷資源群組名稱是否是唯一一組，可使用此命令來列出現有的資源群組。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="dd20b-248">針對這唯一的一組資源群組名稱，填寫下列表格。</span><span class="sxs-lookup"><span data-stu-id="dd20b-248">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="dd20b-249">**項目**</span><span class="sxs-lookup"><span data-stu-id="dd20b-249">**Item**</span></span>|<span data-ttu-id="dd20b-250">**資源群組名稱**</span><span class="sxs-lookup"><span data-stu-id="dd20b-250">**Resource group name**</span></span>|<span data-ttu-id="dd20b-251">**用途**</span><span class="sxs-lookup"><span data-stu-id="dd20b-251">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="dd20b-252">1.</span><span class="sxs-lookup"><span data-stu-id="dd20b-252">1.</span></span>  <br/> |<span data-ttu-id="dd20b-253">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-253"></span></span>  <br/> |<span data-ttu-id="dd20b-254">網域控制站</span><span class="sxs-lookup"><span data-stu-id="dd20b-254">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="dd20b-255">2.</span><span class="sxs-lookup"><span data-stu-id="dd20b-255">2.</span></span>  <br/> |<span data-ttu-id="dd20b-256">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-256"></span></span>  <br/> |<span data-ttu-id="dd20b-257">AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="dd20b-257">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="dd20b-258">3.</span><span class="sxs-lookup"><span data-stu-id="dd20b-258">3.</span></span>  <br/> |<span data-ttu-id="dd20b-259">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-259"></span></span>  <br/> |<span data-ttu-id="dd20b-260">Web 應用程式 Proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="dd20b-260">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="dd20b-261">4.</span><span class="sxs-lookup"><span data-stu-id="dd20b-261">4.</span></span>  <br/> |<span data-ttu-id="dd20b-262">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-262"></span></span>  <br/> |<span data-ttu-id="dd20b-263">基礎結構元素</span><span class="sxs-lookup"><span data-stu-id="dd20b-263">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="dd20b-264">**表： 資源群組**</span><span class="sxs-lookup"><span data-stu-id="dd20b-264">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="dd20b-265">使用這些命令建立新的資源群組。</span><span class="sxs-lookup"><span data-stu-id="dd20b-265">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="dd20b-266">下一步，建立 Azure 虛擬網路和其子網路。</span><span class="sxs-lookup"><span data-stu-id="dd20b-266">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="dd20b-p112">接下來，您建立網路的每個包含虛擬機器時的子網路的安全性群組。若要執行的子網路隔離，您可以新增特定類型的流量允許或拒絕的子網路的網路安全性] 群組的規則。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="dd20b-269">接著，使用以下命令來建立站台對站台 VPN 連線的閘道。</span><span class="sxs-lookup"><span data-stu-id="dd20b-269">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="dd20b-p113">個別使用者的同盟的驗證不依賴任何內部部署的資源。不過，如果無法使用此網站 VPN 連線，VNet 在網域控制站也不會收到的使用者帳戶和群組中的內部 Windows Server AD 所做的更新。若要確保這不會發生，您可以設定高可用性的網站 VPN 連線。如需詳細資訊，請參閱[高度可用的跨單位] 和 [VNet-VNet 連線](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span><span class="sxs-lookup"><span data-stu-id="dd20b-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="dd20b-274">接著，從顯示的以下命令中，記錄虛擬網路 Azure VPN 閘道的公用 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-274">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="dd20b-p114">接下來，設定您的內部部署 VPN 裝置連線至 Azure VPN 閘道。如需詳細資訊，請參閱 ＜ [Configure VPN 裝置](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="dd20b-277">若要設定您的內部部署 VPN 裝置，您需要下列項目︰</span><span class="sxs-lookup"><span data-stu-id="dd20b-277">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="dd20b-278">Azure VPN 閘道的公用 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="dd20b-278">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="dd20b-279">網站 VPN 連線 （表格 V-項目 5-值欄） 的 IPsec 預先共用的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dd20b-279">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="dd20b-p115">下一步，確認從內部部署網路可觸及虛擬網路的位址空間。一般來說，完成方式是新增路由以將虛擬網路位址空間對應至 VPN 裝置，然後將此路由傳達給其餘組織網路的路由基礎結構。請與您的 IT 部門合作以決定如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="dd20b-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="dd20b-p116">下一步，定義三個可用性設定組的名稱。填寫表格 A。 </span><span class="sxs-lookup"><span data-stu-id="dd20b-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="dd20b-285">**項目**</span><span class="sxs-lookup"><span data-stu-id="dd20b-285">**Item**</span></span>|<span data-ttu-id="dd20b-286">**用途**</span><span class="sxs-lookup"><span data-stu-id="dd20b-286">**Purpose**</span></span>|<span data-ttu-id="dd20b-287">**可用性設定名稱**</span><span class="sxs-lookup"><span data-stu-id="dd20b-287">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="dd20b-288">1.</span><span class="sxs-lookup"><span data-stu-id="dd20b-288">1.</span></span>  <br/> |<span data-ttu-id="dd20b-289">網域控制站</span><span class="sxs-lookup"><span data-stu-id="dd20b-289">Domain controllers</span></span>  <br/> |<span data-ttu-id="dd20b-290">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-290"></span></span>  <br/> |
|<span data-ttu-id="dd20b-291">2.</span><span class="sxs-lookup"><span data-stu-id="dd20b-291">2.</span></span>  <br/> |<span data-ttu-id="dd20b-292">AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="dd20b-292">AD FS servers</span></span>  <br/> |<span data-ttu-id="dd20b-293">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-293"></span></span>  <br/> |
|<span data-ttu-id="dd20b-294">3.</span><span class="sxs-lookup"><span data-stu-id="dd20b-294">3.</span></span>  <br/> |<span data-ttu-id="dd20b-295">Web 應用程式 Proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="dd20b-295">Web application proxy servers</span></span>  <br/> |<span data-ttu-id="dd20b-296">_______________________________</span><span class="sxs-lookup"><span data-stu-id="dd20b-296"></span></span>  <br/> |
   
 <span data-ttu-id="dd20b-297">**表格： 可用性設定**</span><span class="sxs-lookup"><span data-stu-id="dd20b-297">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="dd20b-298">當您在階段 2、3 和 4 中建立虛擬機器時，將會需要這些名稱。</span><span class="sxs-lookup"><span data-stu-id="dd20b-298">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="dd20b-299">請使用這些 Azure PowerShell 命令來建立新的可用性設定組。</span><span class="sxs-lookup"><span data-stu-id="dd20b-299">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

<span data-ttu-id="dd20b-300">以下是成功完成此階段的設定結果。</span><span class="sxs-lookup"><span data-stu-id="dd20b-300">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="dd20b-301">**階段 1： Azure 基礎結構的高可用性同盟驗證 Office 365**</span><span class="sxs-lookup"><span data-stu-id="dd20b-301">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![具有 Azure 基礎結構的 Azure 中之高可用性 Office 365 同盟驗證的階段 1](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="dd20b-303">下一步</span><span class="sxs-lookup"><span data-stu-id="dd20b-303">Next step</span></span>

<span data-ttu-id="dd20b-304">使用[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)繼續執行此工作負載的組態。</span><span class="sxs-lookup"><span data-stu-id="dd20b-304">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dd20b-305">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd20b-305">See Also</span></span>

[<span data-ttu-id="dd20b-306">部署在 Azure 中的 Office 365 的高可用性同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="dd20b-306">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="dd20b-307">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="dd20b-307">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="dd20b-308">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="dd20b-308">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="dd20b-309">Office 365 的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="dd20b-309">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


