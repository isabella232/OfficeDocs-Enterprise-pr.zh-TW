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
ms.collection:
- Ent_O365_Hybrid_Top
- Ent_O365
- Ent_O365_Hybrid
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: "摘要： 建立並設定您的高可用性同盟驗證 Office 365 的 Active Directory Federation Services (AD FS) 伺服器 in Microsoft Azure。"
ms.openlocfilehash: b3faf7e7ebf25dbcbfd5a0a8d3431d145b540da8
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>高可用性同盟驗證階段 3：設定 AD FS 伺服器

 **摘要：**建立及設定您的高可用性同盟驗證 Office 365 的 Active Directory Federation Services (AD FS) 伺服器 in Microsoft Azure。
  
在 Azure 基礎結構服務中部署 Office 365 同盟驗證高可用性的此階段，您會建立內部負載平衡器和兩部 AD FS 伺服器。
  
您必須完成此階段中的將移入之前[高可用性同盟驗證階段 4： 設定 web 應用程式 proxy](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>在 Azure 中建立 AD FS 伺服器虛擬機器

您可以使用下列 PowerShell 命令的區塊，建立兩個 AD FS 伺服器的虛擬機器。此 PowerShell 命令集會使用下表中的值︰
  
- 表格 M，適用於虛擬機器
    
- 表格 R，適用於資源群組
    
- 表格 V，適用於虛擬網路設定
    
- 表格 S，適用於子網路
    
- 表格 I，適用於靜態 IP 位址
    
- 表格 A，適用於可用性設定組
    
重新叫用您定義中的表格 M[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表格 R、 V、 S、 I、 及中的 A[高可用性同盟驗證階段 1： 設定 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。
  
> [!NOTE]
> 下列的命令會使用 Azure PowerShell 的最新版本。請參閱[開始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。 
  
首先，您建立 Azure 內部負載平衡器的兩個 AD FS 伺服器。指定的變數，移除值\<和 > 字元。當您有提供所有適當的值時，在 Azure PowerShell 命令提示字元處或 PowerShell ISE 中執行的結果區塊。
  
> [!TIP]
> 對於包含本文及產生就緒-隨選即用 PowerShell 命令封鎖根據自訂設定 Microsoft Excel 設定活頁簿中的 PowerShell 命令的所有文字檔案，請參閱 ＜[同盟驗證 Office 365 中Azure 部署套件](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。 
  
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

下一步，建立 AD FS 伺服器虛擬機器。
  
當您已提供所有適當的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。
  
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
> 因為這些虛擬機器時 intranet 應用程式，他們不會指派公用 IP 位址] 或 [DNS 網域名稱] 標籤並公開到網際網路。但是，這也表示您無法連線至其從 Azure 入口網站。檢視時的虛擬機器屬性無法使用 [**連線**] 選項。使用遠端桌面連線裝飾或另一個遠端桌面工具來連線至虛擬機器使用私人 IP 位址] 或 [內部網路 DNS 名稱。
  
針對每一部虛擬機器，使用您所選的遠端桌面用戶端建立遠端桌面連線。請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。
  
針對每一部虛擬機器，在 Windows PowerShell 提示上使用以下命令將其加入適當的 Windows Server AD 網域。
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。
  
**階段 3： AD FS 伺服器與高可用性同盟的驗證基礎結構 Azure 中的內部負載平衡器**

![具有 AD FS 伺服器的 Azure 中之高可用性 Office 365 同盟驗證基礎結構的階段 3](images/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>下一步

使用[高可用性同盟驗證階段 4： 設定 web 應用程式 proxy](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)繼續設定此工作量。
  
## <a name="see-also"></a>See Also

[部署在 Azure 中的 Office 365 的高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)


