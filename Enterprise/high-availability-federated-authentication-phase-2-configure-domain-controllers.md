---
title: "高可用性同盟驗證階段 2 設定網域控制站"
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: "摘要： 設定網域控制站與您的高可用性同盟驗證 Office 365 DirSync server in Microsoft Azure。"
ms.openlocfilehash: 5e2cc8b5c750b5b2cf48ff0c594a5bd716d5bcf2
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>高可用性同盟驗證階段 2：設定網域控制站

 **摘要：**設定網域控制站與您的高可用性同盟驗證 Office 365 DirSync server in Microsoft Azure。
  
在 Azure 基礎結構服務中部署 Office 365 同盟驗證高可用性的此階段，您會在 Azure 虛擬網路中設定兩個網域控制站和 DirSync 伺服器。然後用戶端 Web 驗證要求即可在 Azure 虛擬網路中驗證，而非透過站台對站台的 VPN 連線來傳送驗證流量至內部部署網路。
  
> [!NOTE]
> Active Directory 同盟服務 (AD FS) 無法使用 Azure Active Directory 網域服務替代 Windows Server AD 網域控制站。 
  
您必須完成此階段中的將移入之前[高可用性同盟驗證階段 3： 設定 AD FS 伺服器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>在 Azure 中建立網域控制站虛擬機器

首先，您必須填寫**虛擬機器名稱**] 欄中的表格 M 與 [**最小大小**] 欄中所視需要修改虛擬機器大小。
  
|**項目**|**虛擬機器名稱**|**[圖庫圖像**|**儲存體類型**|**大小下限**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |______________ (第一個網域控制站，範例 DC1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |______________ (第二個網域控制站，範例 DC2)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |______________ (DirSync 伺服器，範例 DS1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |______________ (第一個 AD FS 伺服器，範例 ADFS1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |______________ (第二個 AD FS 伺服器，範例 ADFS2)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |______________ (第一個 Web 應用程式 Proxy 伺服器，範例 WEB1)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |______________ (第二個 Web 應用程式 Proxy 伺服器，範例 WEB2)  <br/> |Windows Server 2016 Datacenter  <br/> |StandardLRS  <br/> |Standard_D2  <br/> |
   
 **表 M-Azure 中的 Office 365 的高可用性同盟驗證的虛擬機器**
  
虛擬機器大小的完整清單，請參閱[虛擬機器時的大小](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)。
  
下列的 Azure PowerShell 命令區塊會建立兩個網域控制站虛擬機器。指定的變數，移除值\<和 > 字元。請注意此 Azure PowerShell 命令區塊會使用下表中的值：
  
- 表格 M，適用於虛擬機器
    
- 表格 R，適用於資源群組
    
- 表格 V，適用於虛擬網路設定
    
- 表格 S，適用於子網路
    
- 表格 I，適用於靜態 IP 位址
    
- 表格 A，適用於可用性設定組
    
重新叫用您定義資料表 R、 V、 S、 I、 及中的 A[高可用性同盟驗證階段 1： 設定 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。
  
> [!NOTE]
> 下列的命令會使用 Azure PowerShell 的最新版本。請參閱[開始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。 
  
當您已經提供所有正確的值時，在 Azure PowerShell 提示中或本機電腦的 PowerShell 整合式指令碼環境 (ISE) 中執行結果區塊。
  
> [!TIP]
> 對於包含本文及產生就緒-隨選即用 PowerShell 命令封鎖根據自訂設定 Microsoft Excel 設定活頁簿中的 PowerShell 命令的所有文字檔案，請參閱 ＜[同盟驗證 Office 365 中Azure 部署套件](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> 因為這些虛擬機器時 intranet 應用程式，他們不會指派公用 IP 位址] 或 [DNS 網域名稱] 標籤並公開到網際網路。但是，這也表示您無法連線至其從 Azure 入口網站。檢視時的虛擬機器屬性無法使用 [**連線**] 選項。使用遠端桌面連線裝飾或另一個遠端桌面工具來連線至虛擬機器使用私人 IP 位址] 或 [內部網路 DNS 名稱。
  
## <a name="configure-the-first-domain-controller"></a>設定第一個網域控制站

使用您所選的遠端桌面用戶端，建立第一個網域控制站虛擬機器的遠端桌面連線。請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。
  
下一步] 新增至與此命令的第一個網域控制站的額外資料磁碟從 Windows PowerShell 命令提示字元中**第一個網域控制站虛擬機器上**：
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

下一步] 以測試在您組織的網路位置的第一個網域控制站連線使用**ping**命令 ping 名稱及 IP 位址您組織的網路上的資源。
  
此程序可確保 DNS 名稱解析運作正常 (虛擬機器已透過內部部署 DNS 伺服器正確設定)，而且封包可在跨單位虛擬網路間傳送。如果此基本測試失敗，請連絡您的 IT 部門，以針對 DNS 名稱解析和封包傳遞問題進行移難排解。
  
下一步，從第一個網域控制站上的 Windows PowerShell 命令提示字元，執行下列命令：
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred
```

系統會提示您提供網域管理員帳戶的認證。電腦將會重新啟動。
  
## <a name="configure-the-second-domain-controller"></a>設定第二個網域控制站

使用您所選的遠端桌面用戶端，建立第二個網域控制站虛擬機器的遠端桌面連線。請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。
  
接下來，您需要從 Windows PowerShell 命令提示字元中**第二個網域控制站虛擬機器上**使用此命令的第二個網域控制站新增額外的資料磁碟：
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

接著，執行下列命令：
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs" -Credential $cred

```

系統會提示您提供網域管理員帳戶的認證。電腦將會重新啟動。
  
接下來，您需要讓該 Azure 指派虛擬機器的兩個新網域控制站作為其 DNS 伺服器的 IP 位址更新為您的虛擬網路的 DNS 伺服器。變數中填滿，然後在本機電腦上的 Windows PowerShell 命令提示字元執行下列命令：
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

請注意，我們會重新啟動兩個網域控制站，所以這兩個控制站不會像 DNS 伺服器一樣，透過內部部署 DNS 伺服器來設定。因為這兩個控制站本身就是 DNS 伺服器，當系統提示其作為網域控制站時，這些控制站會自動透過內部部署 DNS 伺服器設定為 DNS 轉寄站。
  
下一步，我們需要建立一個 Active Directory 複寫站台，以確保 Azure 的虛擬網路中的伺服器會使用本機網域控制站。請使用網域管理員帳戶與其中一個網域控制站連線，並從管理員層級的 Windows PowerShell 提示執行下列命令：
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a>設定 DirSync 伺服器

使用您選擇在遠端桌面用戶端及建立 DirSync server 虛擬機器的遠端桌面連線。使用其內部網路 DNS 或電腦名稱以及本機管理員帳戶的認證。
  
下一步，在 Windows PowerShell 提示上使用以下命令將其加入適當的 Windows Server AD 網域。
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。
  
**階段 2： 的網域控制站和 DirSync server 高可用性同盟的驗證基礎結構 Azure 中**

![具有網域控制站的 Azure 中之高可用性 Office 365 同盟驗證基礎結構的階段 2](images/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>下一步

使用[高可用性同盟驗證階段 3： 設定 AD FS 伺服器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)繼續設定此工作量。
  
## <a name="see-also"></a>請參閱

[部署在 Azure 中的 Office 365 的高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[Office 365 的同盟身分識別](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


