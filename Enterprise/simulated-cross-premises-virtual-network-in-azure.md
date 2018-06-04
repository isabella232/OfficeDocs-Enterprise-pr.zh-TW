---
title: Azure 中模擬的跨單位部署虛擬網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 摘要：在 Microsoft Azure 中建立模擬的跨單位部署虛擬網路，以作為開發/測試環境。
ms.openlocfilehash: 42ef04a92794c8df53d3de32970db78d4dcf3119
ms.sourcegitcommit: 8fcf6fd9f0c45a5445654ef811410fca3f4f5512
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "19193663"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a><span data-ttu-id="c1199-103">Azure 中模擬的跨單位部署虛擬網路</span><span class="sxs-lookup"><span data-stu-id="c1199-103">Simulated cross-premises virtual network in Azure</span></span>

 <span data-ttu-id="c1199-104">**摘要：** 在 Microsoft Azure 中建立模擬的跨單位部署虛擬網路，以作為開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="c1199-104">**Summary:** Create a simulated cross-premises virtual network in Microsoft Azure as a dev/test environment.</span></span>
  
<span data-ttu-id="c1199-p101">本文逐步引導您建立模擬的混合式雲端環境，具有使用兩個 Azure 虛擬網路的 Microsoft Azure。以下是產生的組態配置。</span><span class="sxs-lookup"><span data-stu-id="c1199-p101">This article steps you through creating a simulated hybrid cloud environment with Microsoft Azure using two Azure virtual networks. Here is the resulting configuration.</span></span> 
  
![模擬的跨部署虛擬網路開發/測試環境，搭配 XPrem VNet 中 DC2 虛擬機器的階段 3](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="c1199-108">它模擬 Azure IaaS 混合式雲端生產環境，包括：</span><span class="sxs-lookup"><span data-stu-id="c1199-108">This simulates an Azure IaaS hybrid cloud production environment and consists of:</span></span>
  
- <span data-ttu-id="c1199-109">裝載在 Azure 虛擬網路 (TestLab 虛擬網路) 中模擬簡化的內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="c1199-109">A simulated and simplified on-premises network hosted in an Azure virtual network (the TestLab virtual network).</span></span>
    
- <span data-ttu-id="c1199-110">裝載在 Azure 中模擬的跨單位部署虛擬網路 (XPrem)。</span><span class="sxs-lookup"><span data-stu-id="c1199-110">A simulated cross-premises virtual network hosted in Azure (XPrem).</span></span>
    
- <span data-ttu-id="c1199-111">兩個虛擬網路之間的 VNet 對等關係。</span><span class="sxs-lookup"><span data-stu-id="c1199-111">A VNet peering relationship between the two virtual networks.</span></span>
    
- <span data-ttu-id="c1199-112">在 XPrem 虛擬網路中的第二個網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c1199-112">A single-server SharePoint farm (SP1 and SQL1) and secondary domain controller (DC2) in the XPrem virtual network.</span></span>
    
<span data-ttu-id="c1199-113">這可作為基礎通用的起點，讓您可以：</span><span class="sxs-lookup"><span data-stu-id="c1199-113">This configuration provides a basis and common starting point from which you can:</span></span> 
  
- <span data-ttu-id="c1199-114">在模擬的 Azure IaaS 混合式雲端環境中開發和測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="c1199-114">Develop and test applications in a simulated Azure IaaS hybrid cloud environment.</span></span>
    
- <span data-ttu-id="c1199-115">建立電腦的測試組態，一些在 TestLab 中虛擬網路、一些在 XPrem 虛擬網路中，以模擬混合式雲端的 IT 工作負載。</span><span class="sxs-lookup"><span data-stu-id="c1199-115">Create test configurations of computers, some within the TestLab virtual network and some within the XPrem virtual network, to simulate hybrid cloud-based IT workloads.</span></span>
    
<span data-ttu-id="c1199-116">設定此開發/測試環境有三個主要階段︰</span><span class="sxs-lookup"><span data-stu-id="c1199-116">There are three major phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="c1199-117">設定 TestLab 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="c1199-117">Configure the TestLab virtual network.</span></span>
    
2. <span data-ttu-id="c1199-118">建立跨單位的虛擬網路</span><span class="sxs-lookup"><span data-stu-id="c1199-118">Phase 2: Create the cross-premises virtual network in Azure</span></span>
    
3. <span data-ttu-id="c1199-119">設定 DC2。</span><span class="sxs-lookup"><span data-stu-id="c1199-119">Configure DC2.</span></span>
    
> [!NOTE]
> <span data-ttu-id="c1199-120">此組態需要付費的 Azure 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="c1199-120">This configuration requires a paid Azure subscription.</span></span> 
  
![Microsoft Cloud 中的測試實驗室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="c1199-122">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="c1199-122">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a><span data-ttu-id="c1199-123">階段 1：設定 TestLab 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="c1199-123">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="c1199-124">使用[基底組態開發/測試環境](base-configuration-dev-test-environment.md)中的說明，在名為 TestLab 的 Azure 虛擬網路中設定 DC1、APP1、CLIENT1 電腦。</span><span class="sxs-lookup"><span data-stu-id="c1199-124">Use the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md) to configure the DC1, APP1, and CLIENT1 computers in the Azure virtual network named TestLab.</span></span>
  
<span data-ttu-id="c1199-125">這是您目前的設定。</span><span class="sxs-lookup"><span data-stu-id="c1199-125">This is your current configuration.</span></span> 
  
![Azure 中具有 CLIENT1 虛擬機器的基底組態的階段 4](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a><span data-ttu-id="c1199-127">階段 2：建立 XPrem 虛擬網路</span><span class="sxs-lookup"><span data-stu-id="c1199-127">Phase 2: Create the cross-premises virtual network in Azure</span></span>

<span data-ttu-id="c1199-128">在這個階段，要建立並設定新的 XPrem 虛擬網路，然後使用 VNet 對等將其連線至 TestLab 虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="c1199-128">In this phase, you create and configure the new XPrem virtual network and then connect it to the TestLab virtual network with VNet peering.</span></span>
  
<span data-ttu-id="c1199-129">首先，在本機電腦上啟動 Azure PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="c1199-129">First, start an Azure PowerShell prompt on your local computer.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c1199-p102">下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="c1199-p102">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="c1199-132">使用下列命令登入您的 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="c1199-132">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="c1199-133">按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0)可取得包含本文中所有 PowerShell 命令的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="c1199-133">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0) to get a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="c1199-134">使用下列命令取得訂用帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="c1199-134">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="c1199-p103">設定 Azure 訂用帳戶。以正確的名稱取代括號中的所有項目 (包括 \< 和 > 字元)。</span><span class="sxs-lookup"><span data-stu-id="c1199-p103">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

<span data-ttu-id="c1199-137">接下來，建立 XPrem 虛擬網路，並使用這些命令以網路安全性群組保護它。</span><span class="sxs-lookup"><span data-stu-id="c1199-137">Next, create the XPrem virtual network and protect it with a network security group with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$Testnet=New-AzureRMVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzureRMVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzureRMNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
```

<span data-ttu-id="c1199-138">接下來，使用這些命令在 TestLab 和 XPrem VNets 之間建立 VNet 對等關係。</span><span class="sxs-lookup"><span data-stu-id="c1199-138">Next, you create the VNet peering relationship between the TestLab and XPrem VNets with these commands.</span></span>
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

<span data-ttu-id="c1199-139">這是您目前的設定。</span><span class="sxs-lookup"><span data-stu-id="c1199-139">This is your current configuration.</span></span> 
  
![模擬的跨部署虛擬網路開發/測試環境，搭配 XPrem VNet 與 VNet 的對等關係的階段 2](images/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a><span data-ttu-id="c1199-141">階段 3：設定 DC2</span><span class="sxs-lookup"><span data-stu-id="c1199-141">Phase 3: Configure APP1</span></span>

<span data-ttu-id="c1199-142">在這個階段，要在 XPrem 虛擬網路中建立 DC2 虛擬機器，然後將它設定為複本網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c1199-142">In this phase, you create the DC2 virtual machine in the XPrem virtual network and then configure it as a replica domain controller.</span></span>
  
<span data-ttu-id="c1199-p104">首先，為 DC2 建立虛擬機器。在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c1199-p104">First, create a virtual machine for DC2. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<your resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzureRMVMConfig -VMName DC2 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="c1199-145">然後，使用本機系統管理員帳戶的名稱和密碼從 [Azure 入口網站](https://portal.azure.com)連線到 DC2 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="c1199-145">Next, connect to the new DC2 virtual machine from the [Azure portal](https://portal.azure.com) using its local administrator account name and password.</span></span>
  
<span data-ttu-id="c1199-p105">接下來，設定 Windows 防火牆規則以允許流量進行基本連線能力測試。在 DC2 上的系統管理員層級的 Windows PowerShell 命令提示字元中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c1199-p105">Next, configure a Windows Firewall rule to allow traffic for basic connectivity testing. From an administrator-level Windows PowerShell command prompt on DC2, run these commands.</span></span> 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

<span data-ttu-id="c1199-p106">ping 命令應會得到來自 IP 位址 10.0.0.4 四次成功的回覆。這是對 VNet 對等關係流量的測試。</span><span class="sxs-lookup"><span data-stu-id="c1199-p106">The ping command should result in four successful replies from IP address 10.0.0.4. This is a test of traffic across the VNet peering relationship.</span></span> 
  
<span data-ttu-id="c1199-150">接著，從 DC2 上的 PowerShell 命令提示字元，使用此命令將額外的資料磁碟新增為新的磁碟區 (磁碟機代號 F:)。</span><span class="sxs-lookup"><span data-stu-id="c1199-150">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="c1199-p107">接著，將 DC2 設定為 corp.contoso.com 網域的複本網域控制站。從 DC2 上的 PowerShell 命令提示字元執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c1199-p107">Next, configure adVM as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt on adVM.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

<span data-ttu-id="c1199-153">請注意，系統會提示您提供 CORP\\User1 的密碼和目錄服務復原模式 (DSRM) 的密碼，並重新啟動 DC2。</span><span class="sxs-lookup"><span data-stu-id="c1199-153">Note that you are prompted to supply both the CORP\\User1 password and a Directory Services Restore Mode (DSRM) password, and to restart DC2.</span></span> 
  
<span data-ttu-id="c1199-p108">既然 XPrem 虛擬網路有自己的 DNS 伺服器 (DC2)，您必須將 XPrem 虛擬網絡設定為使用此 DNS 伺服器。在本機電腦上使用 Azure PowerShell 命令提示字元執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c1199-p108">Now that the XPrem virtual network has its own DNS server (DC2), you must configure the XPrem virtual network to use this DNS server. Run these commands from the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

<span data-ttu-id="c1199-p109">在本機電腦從 Azure 入口網站，使用 CORP\\User1 的憑證連線到 DC1。若要設定 CORP 網域以便讓電腦和使用者可使用其本機網域控制站進行驗證，在 DC1 上以系統管理員層級的 Windows PowerShell 命令提示字元執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c1199-p109">From the Azure portal on your local computer, connect to DC1 with the CORP\\User1 credentials. To configure the CORP domain so that computers and users use their local domain controller for authentication, run these commands from an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

<span data-ttu-id="c1199-158">這是您目前的設定。</span><span class="sxs-lookup"><span data-stu-id="c1199-158">This is your current configuration.</span></span> 
  
![模擬的跨部署虛擬網路開發/測試環境，搭配 XPrem VNet 中 DC2 虛擬機器的階段 3](images/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
<span data-ttu-id="c1199-160">模擬的 Azure 混合式雲端環境已準備好進行測試。</span><span class="sxs-lookup"><span data-stu-id="c1199-160">Your simulated Azure hybrid cloud environment is now ready for testing.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="c1199-161">下一步</span><span class="sxs-lookup"><span data-stu-id="c1199-161">Next step</span></span>

<span data-ttu-id="c1199-162">使用此開發/測試環境模擬[裝載在 Azure 中的 SharePoint Server 2016 內部網路伺服器陣列](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c1199-162">Use this dev/test environment to simulate a [SharePoint Server 2016 intranet farm hosted in Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c1199-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1199-163">See Also</span></span>

[<span data-ttu-id="c1199-164">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="c1199-164">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="c1199-165">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="c1199-165">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="c1199-166">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="c1199-166">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c1199-167">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="c1199-167">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c1199-168">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="c1199-168">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c1199-169">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="c1199-169">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


