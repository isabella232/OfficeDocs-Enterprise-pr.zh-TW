---
title: "高可用性同盟驗證階段 4 設定 web 應用程式 proxy"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Hybrid_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: "摘要： 設定 Microsoft Azure 中的 Office 365 在高可用性同盟驗證的 web 應用程式 proxy 伺服器。"
ms.openlocfilehash: 02aeac727815a82c15cd602094e945a14ed551af
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="bc7e6-103">高可用性同盟驗證階段 4：設定 Web 應用程式 Proxy</span><span class="sxs-lookup"><span data-stu-id="bc7e6-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

 <span data-ttu-id="bc7e6-104">**摘要：**Microsoft Azure 中設定您的 Office 365 的高可用性同盟驗證的 web 應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-104">**Summary:** Configure the web application proxy servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="bc7e6-105">在 Azure 基礎結構服務中部署 Office 365 同盟驗證高可用性的此階段，您會建立內部負載平衡器和兩部 AD FS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="bc7e6-p101">您必須完成此階段中的將移入之前[高可用性同盟驗證階段 5： 設定 Office 365 同盟的驗證](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-p101">You must complete this phase before moving on to [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="bc7e6-108">在 Azure 中建立網際網路對應負載平衡器</span><span class="sxs-lookup"><span data-stu-id="bc7e6-108">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="bc7e6-109">您必須先建立網際網路對應負載平衡器，讓 Azure 將從網際網路傳入的用戶端驗證流量分散到兩個 Web 應用程式 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-109">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="bc7e6-p102">下列的命令會使用 Azure PowerShell 的最新版本。請參閱[開始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="bc7e6-112">當您已提供位置和資源群組的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-112">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="bc7e6-113">對於包含本文及產生就緒-隨選即用 PowerShell 命令封鎖根據自訂設定 Microsoft Excel 設定活頁簿中的 PowerShell 命令的所有文字檔案，請參閱 ＜[同盟驗證 Office 365 中Azure 部署套件](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-113">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzureRmPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzureRmLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="bc7e6-114">若要顯示指派到您網際網路對應負載平衡器的公用 IP 位址，請在本機電腦上的 Azure PowerShell 命令提示字元上執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="bc7e6-114">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="bc7e6-115">決定您的同盟服務 FQDN 並建立 DNS 記錄</span><span class="sxs-lookup"><span data-stu-id="bc7e6-115">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="bc7e6-p103">您需要決定 DNS 名稱以在網際網路上識別您的同盟伺服器名稱。Azure AD Connect 會以階段 5 中的此名稱設定 Office 365，這將會包含在 Office 365 用來與用戶端連線以取得安全性權杖所傳送的 URL 內。例如 fs.contoso.com (fs 表示同盟服務)。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-p103">You need to determine the DNS name to identify your federation service name on the Internet. Azure AD Connect will configure Office 365 with this name in Phase 5, which will become part of the URL that Office 365 sends to connecting clients to get a security token. An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="bc7e6-119">一旦您有了同盟服務 FQDN，請針對同盟服務 FDQN 建立公用 DNS 網域 A 記錄，這會解析為 Azure 網際網路對應負載平衡器的公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-119">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="bc7e6-120">**名稱**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-120">**Name**</span></span>|<span data-ttu-id="bc7e6-121">**類型**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-121">**Type**</span></span>|<span data-ttu-id="bc7e6-122">**TTL**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-122">**TTL**</span></span>|<span data-ttu-id="bc7e6-123">**值**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-123">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="bc7e6-124">同盟服務 FDQN</span><span class="sxs-lookup"><span data-stu-id="bc7e6-124">federation service FDQN</span></span>  <br/> |<span data-ttu-id="bc7e6-125">A</span><span class="sxs-lookup"><span data-stu-id="bc7e6-125">A</span></span>  <br/> |<span data-ttu-id="bc7e6-126">3600</span><span class="sxs-lookup"><span data-stu-id="bc7e6-126">3600</span></span>  <br/> |<span data-ttu-id="bc7e6-127">Azure 網際網路對向負載平衡器 （由上一節中的命令會**寫入主機**顯示） 的公用 IP 位址</span><span class="sxs-lookup"><span data-stu-id="bc7e6-127">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="bc7e6-128">範例如下：</span><span class="sxs-lookup"><span data-stu-id="bc7e6-128">Here is an example:</span></span>
  
|<span data-ttu-id="bc7e6-129">**名稱**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-129">**Name**</span></span>|<span data-ttu-id="bc7e6-130">**類型**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-130">**Type**</span></span>|<span data-ttu-id="bc7e6-131">**TTL**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-131">**TTL**</span></span>|<span data-ttu-id="bc7e6-132">**值**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-132">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="bc7e6-133">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="bc7e6-133">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="bc7e6-134">A</span><span class="sxs-lookup"><span data-stu-id="bc7e6-134">A</span></span>  <br/> |<span data-ttu-id="bc7e6-135">3600</span><span class="sxs-lookup"><span data-stu-id="bc7e6-135">3600</span></span>  <br/> |<span data-ttu-id="bc7e6-136">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="bc7e6-136">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="bc7e6-137">下一步，將 DNS 位址記錄新增至您的組織私人 DNS 命名空間，此命名空間會將您的同盟服務 FQDN 解析為 AD FS 伺服器內部負載平衡器的私人 IP 位址 (表格 I、項目 4、值欄)。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-137">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="bc7e6-138">在 Azure 中建立 Web 應用程式 Proxy 伺服器虛擬機器</span><span class="sxs-lookup"><span data-stu-id="bc7e6-138">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="bc7e6-139">您可以使用下列 Azure PowerShell 命令的區塊，建立兩部 Web 應用程式 Proxy 伺服器的虛擬機器。 </span><span class="sxs-lookup"><span data-stu-id="bc7e6-139">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="bc7e6-140">請注意，下列 Azure PowerShell 命令集會使用下表中的值︰</span><span class="sxs-lookup"><span data-stu-id="bc7e6-140">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="bc7e6-141">表格 M，適用於虛擬機器</span><span class="sxs-lookup"><span data-stu-id="bc7e6-141">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="bc7e6-142">表格 R，適用於資源群組</span><span class="sxs-lookup"><span data-stu-id="bc7e6-142">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="bc7e6-143">表格 V，適用於虛擬網路設定</span><span class="sxs-lookup"><span data-stu-id="bc7e6-143">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="bc7e6-144">表格 S，適用於子網路</span><span class="sxs-lookup"><span data-stu-id="bc7e6-144">Table S, for your subnets</span></span>
    
- <span data-ttu-id="bc7e6-145">表格 I，適用於靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="bc7e6-145">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="bc7e6-146">表格 A，適用於可用性設定組</span><span class="sxs-lookup"><span data-stu-id="bc7e6-146">Table A, for your availability sets</span></span>
    
<span data-ttu-id="bc7e6-147">重新叫用您定義中的表格 M[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表格 R、 V、 S、 I、 及中的 A[高可用性同盟驗證階段 1： 設定 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-147">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="bc7e6-148">當您已提供所有適當的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-148">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="bc7e6-p104">因為這些虛擬機器時 intranet 應用程式，他們不會指派公用 IP 位址] 或 [DNS 網域名稱] 標籤並公開到網際網路。但是，這也表示您無法連線至其從 Azure 入口網站。檢視時的虛擬機器屬性無法使用 [**連線**] 選項。使用遠端桌面連線裝飾或另一個遠端桌面工具來連線至虛擬機器使用其私人 IP 位址] 或 [內部網路的 DNS 名稱與本機系統管理員帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-p104">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="bc7e6-153">以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-153">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="bc7e6-154">**階段 4： 網際網路對向的負載平衡器與高可用性同盟的驗證基礎結構 Azure 中的 web 應用程式 proxy 伺服器**</span><span class="sxs-lookup"><span data-stu-id="bc7e6-154">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![具有 Web 應用程式 Proxy 伺服器的 Azure 中之高可用性 Office 365 同盟驗證基礎結構的階段 4](images/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="bc7e6-156">下一步</span><span class="sxs-lookup"><span data-stu-id="bc7e6-156">Next step</span></span>

<span data-ttu-id="bc7e6-157">使用[高可用性同盟驗證階段 5： 設定 Office 365 同盟的驗證](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)繼續設定此工作量。</span><span class="sxs-lookup"><span data-stu-id="bc7e6-157">Use [High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc7e6-158">See Also</span><span class="sxs-lookup"><span data-stu-id="bc7e6-158">See Also</span></span>

[<span data-ttu-id="bc7e6-159">部署在 Azure 中的 Office 365 的高可用性同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="bc7e6-159">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="bc7e6-160">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="bc7e6-160">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="bc7e6-161">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="bc7e6-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="bc7e6-162">Office 365 的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="bc7e6-162">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


