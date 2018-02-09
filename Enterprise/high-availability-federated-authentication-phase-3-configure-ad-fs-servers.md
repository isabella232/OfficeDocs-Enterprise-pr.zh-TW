---
title: "高可用性同盟驗證階段 3 設定 AD FS 伺服器"
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
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: "摘要： 建立並設定您的高可用性同盟驗證 Office 365 的 Active Directory Federation Services (AD FS) 伺服器 in Microsoft Azure。"
ms.openlocfilehash: a9daecddb572bf2432d68ae76ed8d81571ef4b79
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="fb070-103">高可用性同盟驗證階段 3：設定 AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="fb070-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="fb070-104">**摘要：**建立及設定您的高可用性同盟驗證 Office 365 的 Active Directory Federation Services (AD FS) 伺服器 in Microsoft Azure。</span><span class="sxs-lookup"><span data-stu-id="fb070-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="fb070-105">在 Azure 基礎結構服務中部署 Office 365 同盟驗證高可用性的此階段，您會建立內部負載平衡器和兩部 AD FS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fb070-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="fb070-p101">您必須完成此階段中的將移入之前[高可用性同盟驗證階段 4： 設定 web 應用程式 proxy](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。</span><span class="sxs-lookup"><span data-stu-id="fb070-p101">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="fb070-108">在 Azure 中建立 AD FS 伺服器虛擬機器</span><span class="sxs-lookup"><span data-stu-id="fb070-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="fb070-p102">您可以使用下列 PowerShell 命令的區塊，建立兩個 AD FS 伺服器的虛擬機器。此 PowerShell 命令集會使用下表中的值︰</span><span class="sxs-lookup"><span data-stu-id="fb070-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="fb070-111">表格 M，適用於虛擬機器</span><span class="sxs-lookup"><span data-stu-id="fb070-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="fb070-112">表格 R，適用於資源群組</span><span class="sxs-lookup"><span data-stu-id="fb070-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="fb070-113">表格 V，適用於虛擬網路設定</span><span class="sxs-lookup"><span data-stu-id="fb070-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="fb070-114">表格 S，適用於子網路</span><span class="sxs-lookup"><span data-stu-id="fb070-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="fb070-115">表格 I，適用於靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="fb070-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="fb070-116">表格 A，適用於可用性設定組</span><span class="sxs-lookup"><span data-stu-id="fb070-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="fb070-117">重新叫用您定義中的表格 M[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表格 R、 V、 S、 I、 及中的 A[高可用性同盟驗證階段 1： 設定 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="fb070-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="fb070-p103">下列的命令會使用 Azure PowerShell 的最新版本。請參閱[開始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="fb070-p103">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="fb070-p104">首先，您建立 Azure 內部負載平衡器的兩個 AD FS 伺服器。指定的變數，移除值\<和 > 字元。當您有提供所有適當的值時，在 Azure PowerShell 命令提示字元處或 PowerShell ISE 中執行的結果區塊。</span><span class="sxs-lookup"><span data-stu-id="fb070-p104">First, you create an Azure internal load balancer for the two AD FS servers. Specify the values for the variables, removing the \< and > characters. When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="fb070-123">對於包含本文及產生就緒-隨選即用 PowerShell 命令封鎖根據自訂設定 Microsoft Excel 設定活頁簿中的 PowerShell 命令的所有文字檔案，請參閱 ＜[同盟驗證 Office 365 中Azure 部署套件](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。</span><span class="sxs-lookup"><span data-stu-id="fb070-123">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzureRMLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzureRMLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzureRMLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzureRMLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="fb070-124">下一步，建立 AD FS 伺服器虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="fb070-124">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="fb070-125">當您已提供所有適當的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。</span><span class="sxs-lookup"><span data-stu-id="fb070-125">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzureRMVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzureRMLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="fb070-p105">因為這些虛擬機器時 intranet 應用程式，他們不會指派公用 IP 位址] 或 [DNS 網域名稱] 標籤並公開到網際網路。但是，這也表示您無法連線至其從 Azure 入口網站。檢視時的虛擬機器屬性無法使用 [**連線**] 選項。使用遠端桌面連線裝飾或另一個遠端桌面工具來連線至虛擬機器使用私人 IP 位址] 或 [內部網路 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="fb070-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="fb070-p106">針對每一部虛擬機器，使用您所選的遠端桌面用戶端建立遠端桌面連線。請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。</span><span class="sxs-lookup"><span data-stu-id="fb070-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="fb070-132">針對每一部虛擬機器，在 Windows PowerShell 提示上使用以下命令將其加入適當的 Windows Server AD 網域。</span><span class="sxs-lookup"><span data-stu-id="fb070-132">For each virtual machine, join them to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="fb070-133">以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。</span><span class="sxs-lookup"><span data-stu-id="fb070-133">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="fb070-134">**階段 3： AD FS 伺服器與高可用性同盟的驗證基礎結構 Azure 中的內部負載平衡器**</span><span class="sxs-lookup"><span data-stu-id="fb070-134">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![具有 AD FS 伺服器的 Azure 中之高可用性 Office 365 同盟驗證基礎結構的階段 3](images/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="fb070-136">下一步</span><span class="sxs-lookup"><span data-stu-id="fb070-136">Next step</span></span>

<span data-ttu-id="fb070-137">使用[高可用性同盟驗證階段 4： 設定 web 應用程式 proxy](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)繼續設定此工作量。</span><span class="sxs-lookup"><span data-stu-id="fb070-137">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fb070-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb070-138">See Also</span></span>

[<span data-ttu-id="fb070-139">部署在 Azure 中的 Office 365 的高可用性同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="fb070-139">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="fb070-140">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="fb070-140">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


