---
title: 高可用性同盟驗證階段 3 設定 AD FS 伺服器
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
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: 摘要： 建立並在 Microsoft Azure 中設定您的 Office 365 的高可用性同盟驗證的 Active Directory Federation Services (AD FS) 伺服器。
ms.openlocfilehash: a69738e5be639341963ac1e90aff08328a83257b
ms.sourcegitcommit: 9c9982badeb95b8ecc083609a1a922cbfdfc9609
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "38793300"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="10fec-103">高可用性同盟驗證階段 3：設定 AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="10fec-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

 <span data-ttu-id="10fec-104">**摘要：** 建立並在 Microsoft Azure 中設定您的 Office 365 的高可用性同盟驗證的 Active Directory Federation Services (AD FS) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="10fec-104">**Summary:** Create and configure the Active Directory Federation Services (AD FS) servers for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="10fec-105">在 Azure 基礎結構服務中部署 Office 365 同盟驗證高可用性的此階段，您會建立內部負載平衡器和兩部 AD FS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="10fec-105">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="10fec-106">您必須完成此階段，才可繼續在[高可用性同盟驗證階段 4： 設定 web 應用程式 proxy](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。</span><span class="sxs-lookup"><span data-stu-id="10fec-106">You must complete this phase before moving on to [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="10fec-107">所有階段，請參閱[在 Azure 中的 Office 365 部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="10fec-107">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="10fec-108">在 Azure 中建立 AD FS 伺服器虛擬機器</span><span class="sxs-lookup"><span data-stu-id="10fec-108">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="10fec-109">使用下列的 PowerShell 命令區塊建立兩部 AD FS 伺服器虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="10fec-109">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers.</span></span> <span data-ttu-id="10fec-110">此 PowerShell 命令集會使用下表中的值：</span><span class="sxs-lookup"><span data-stu-id="10fec-110">This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="10fec-111">表格 M，適用於虛擬機器</span><span class="sxs-lookup"><span data-stu-id="10fec-111">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="10fec-112">表格 R，適用於資源群組</span><span class="sxs-lookup"><span data-stu-id="10fec-112">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="10fec-113">表格 V，適用於虛擬網路設定</span><span class="sxs-lookup"><span data-stu-id="10fec-113">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="10fec-114">表格 S，適用於子網路</span><span class="sxs-lookup"><span data-stu-id="10fec-114">Table S, for your subnets</span></span>
    
- <span data-ttu-id="10fec-115">表格 I，適用於靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="10fec-115">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="10fec-116">表格 A，適用於可用性設定組</span><span class="sxs-lookup"><span data-stu-id="10fec-116">Table A, for your availability sets</span></span>
    
<span data-ttu-id="10fec-117">還記得您定義中的表格 M[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表格 R、 V、 S、 I 和 A 中的[高可用性同盟驗證階段 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="10fec-117">Recall that you defined Table M in [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="10fec-118">[!附註] 下列命令集會使用最新版的 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="10fec-118">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="10fec-119">請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="10fec-119">See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="10fec-120">首先，您建立 Azure 內部負載平衡器的兩個 AD FS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="10fec-120">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="10fec-121">為指定值的變數，移除\<和 > 字元。</span><span class="sxs-lookup"><span data-stu-id="10fec-121">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="10fec-122">當您已提供所有適當的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。</span><span class="sxs-lookup"><span data-stu-id="10fec-122">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="10fec-123">接下來，建立 AD FS 伺服器虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="10fec-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="10fec-124">當您已提供所有適當的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。</span><span class="sxs-lookup"><span data-stu-id="10fec-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="10fec-p105">由於這些虛擬機器是用於內部網路應用程式，並不會指派公用 IP 位址或 DNS 網域名稱標籤，也不會曝露在網際網路上。不過，這也表示您無法透過 Azure 入口網站與虛擬機器連線。當您檢視虛擬機器的屬性時，無法使用**連線**選項。請使用遠端桌面連線附屬應用程式或另一個遠端桌面工具，透過使用其私人 IP 位址或內部網路 DNS 名稱來與虛擬機器連線。</span><span class="sxs-lookup"><span data-stu-id="10fec-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="10fec-129">對於每部虛擬機器，使用您所選的遠端桌面用戶端，建立的遠端桌面連線。</span><span class="sxs-lookup"><span data-stu-id="10fec-129">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection.</span></span> <span data-ttu-id="10fec-130">請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。</span><span class="sxs-lookup"><span data-stu-id="10fec-130">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="10fec-131">對於每部虛擬機器，請將其加入適當的 Active Directory 網域服務 (AD DS) 網域的 Windows PowerShell 提示字元使用以下命令中。</span><span class="sxs-lookup"><span data-stu-id="10fec-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="10fec-132">以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。</span><span class="sxs-lookup"><span data-stu-id="10fec-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="10fec-133">**階段 3: AD FS 伺服器和高可用性同盟的驗證基礎結構在 Azure 中的內部負載平衡器**</span><span class="sxs-lookup"><span data-stu-id="10fec-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![階段 3 的高可用性 Office 365 同盟驗證基礎結構在 Azure 中的使用 AD FS 伺服器](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="10fec-135">下一步</span><span class="sxs-lookup"><span data-stu-id="10fec-135">Next step</span></span>

<span data-ttu-id="10fec-136">使用[高可用性同盟驗證階段 4： 設定 web 應用程式 proxy](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)以繼續設定此工作負載。</span><span class="sxs-lookup"><span data-stu-id="10fec-136">Use [High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="10fec-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10fec-137">See Also</span></span>

[<span data-ttu-id="10fec-138">Azure 中的 Office 365 高可用性同盟驗證</span><span class="sxs-lookup"><span data-stu-id="10fec-138">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="10fec-139">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="10fec-139">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


