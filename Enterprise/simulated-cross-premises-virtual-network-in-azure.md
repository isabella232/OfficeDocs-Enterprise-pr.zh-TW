---
title: Azure 中模擬的跨單位部署虛擬網路
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 0a3555dc-6f96-49a5-b9e2-7760e16630b3
description: 摘要：在 Microsoft Azure 中建立模擬的跨單位部署虛擬網路，以作為開發/測試環境。
ms.openlocfilehash: 7341c8cc412636e633001882edfdfc661cce9a11
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897136"
---
# <a name="simulated-cross-premises-virtual-network-in-azure"></a>Azure 中模擬的跨單位部署虛擬網路

 **摘要：** 在 Microsoft Azure 中建立模擬的跨單位部署虛擬網路，以作為開發/測試環境。
  
本文逐步引導您建立模擬的混合式雲端環境，具有使用兩個 Azure 虛擬網路的 Microsoft Azure。以下是產生的組態配置。 
  
![模擬的跨部署虛擬網路開發/測試環境，搭配 XPrem VNet 中 DC2 虛擬機器的階段 3](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
它模擬 Azure IaaS 混合式雲端生產環境，包括：
  
- 裝載在 Azure 虛擬網路 (TestLab 虛擬網路) 中模擬簡化的內部部署網路。
    
- 裝載在 Azure 中模擬的跨單位部署虛擬網路 (XPrem)。
    
- 兩個虛擬網路之間的 VNet 對等關係。
    
- 在 XPrem 虛擬網路中的第二個網域控制站。
    
這可作為基礎通用的起點，讓您可以： 
  
- 在模擬的 Azure IaaS 混合式雲端環境中開發和測試應用程式。
    
- 建立電腦的測試組態，一些在 TestLab 中虛擬網路、一些在 XPrem 虛擬網路中，以模擬混合式雲端的 IT 工作負載。
    
設定此開發/測試環境有三個主要階段︰
  
1. 設定 TestLab 虛擬網路。
    
2. 建立跨單位的虛擬網路
    
3. 設定 DC2。
    
> [!NOTE]
> 此組態需要付費的 Azure 訂用帳戶。 
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="phase-1-configure-the-testlab-virtual-network"></a>階段 1：設定 TestLab 虛擬網路

使用[基底組態開發/測試環境](base-configuration-dev-test-environment.md)中的說明，在名為 TestLab 的 Azure 虛擬網路中設定 DC1、APP1、CLIENT1 電腦。
  
這是您目前的設定。 
  
![Azure 中具有 CLIENT1 虛擬機器的基底組態的階段 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>階段 2：建立 XPrem 虛擬網路

在這個階段，要建立並設定新的 XPrem 虛擬網路，然後使用 VNet 對等將其連線至 TestLab 虛擬網路。
  
首先，在本機電腦上啟動 Azure PowerShell 提示字元。
  
> [!NOTE]
> 下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/)。 
  
使用此命令登入您的 Azure 帳戶。
  
```
Login-AzureRMAccount
```

> [!TIP]
> 按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-7844edd0)以取得包含本文中所有 PowerShell 命令的文字檔案。
  
使用此命令取得訂用帳戶名稱。
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

設定 Azure 訂用帳戶。以正確的名稱取代括號中的所有項目 (包括 \< 和 > 字元)。
  
```
$subscrName="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscrName | Select-AzureRmSubscription
```

接下來，建立 XPrem 虛擬網路，並使用這些命令以網路安全性群組保護它。
  
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

接下來，使用這些命令在 TestLab 和 XPrem VNets 之間建立 VNet 對等關係。
  
```
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzureRmVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzureRmVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

這是您目前的設定。 
  
![模擬的跨部署虛擬網路開發/測試環境，搭配 XPrem VNet 與 VNet 的對等關係的階段 2](media/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>階段 3：設定 DC2

在這個階段，要在 XPrem 虛擬網路中建立 DC2 虛擬機器，然後將它設定為複本網域控制站。
  
首先，為 DC2 建立虛擬機器。在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

然後，使用本機系統管理員帳戶的名稱和密碼從 [Azure 入口網站](https://portal.azure.com)連線到 DC2 虛擬機器。
  
接下來，設定 Windows 防火牆規則以允許流量進行基本連線能力測試。在 DC2 上的系統管理員層級的 Windows PowerShell 命令提示字元中，執行下列命令。 
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

ping 命令應會得到來自 IP 位址 10.0.0.4 四次成功的回覆。這是對 VNet 對等關係流量的測試。 
  
接著，從 DC2 上的 PowerShell 命令提示字元，使用此命令將額外的資料磁碟新增為新的磁碟區 (磁碟機代號 F:)。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

接著，將 DC2 設定為 corp.contoso.com 網域的複本網域控制站。從 DC2 上的 PowerShell 命令提示字元執行下列命令。
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

請注意，系統會提示您提供 CORP\\User1 的密碼和目錄服務復原模式 (DSRM) 的密碼，並重新啟動 DC2。 
  
既然 XPrem 虛擬網路有自己的 DNS 伺服器 (DC2)，您必須將 XPrem 虛擬網絡設定為使用此 DNS 伺服器。在本機電腦上使用 Azure PowerShell 命令提示字元執行下列命令。
  
```
$vnet=Get-AzureRmVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzureRmVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRmVM -ResourceGroupName $rgName -Name "DC2"
```

在本機電腦從 Azure 入口網站，使用 CORP\\User1 的憑證連線到 DC1。若要設定 CORP 網域以便讓電腦和使用者可使用其本機網域控制站進行驗證，在 DC1 上以系統管理員層級的 Windows PowerShell 命令提示字元執行下列命令。
  
```
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

這是您目前的設定。 
  
![模擬的跨部署虛擬網路開發/測試環境，搭配 XPrem VNet 中 DC2 虛擬機器的階段 3](media/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
模擬的 Azure 混合式雲端環境已準備好進行測試。
  
## <a name="next-step"></a>下一步

使用此開發/測試環境模擬[裝載在 Azure 中的 SharePoint Server 2016 內部網路伺服器陣列](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)。
  
## <a name="see-also"></a>另請參閱

[基底組態開發/測試環境](base-configuration-dev-test-environment.md)
  
[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[適用於 Office 365 開發/測試環境的進階威脅防護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)


