---
title: 高可用性同盟驗證階段 4 設定 web 應用程式 proxy
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 摘要： 設定 Microsoft Azure 中的 Office 365 在高可用性同盟驗證的 web 應用程式 proxy 伺服器。
ms.openlocfilehash: 0f0299fe8fecdea608330eebc12aea01098f8cec
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915808"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>高可用性同盟驗證階段 4：設定 Web 應用程式 Proxy

 **摘要：** Microsoft Azure 中設定您的 Office 365 的高可用性同盟驗證的 web 應用程式 proxy 伺服器。
  
在 Azure 基礎結構服務中部署 Office 365 同盟驗證高可用性的此階段，您會建立內部負載平衡器和兩部 AD FS 伺服器。
  
您必須完成此階段中的將移入之前[高可用性同盟驗證階段 5： 設定 Office 365 同盟的驗證](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)的所有階段。
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>在 Azure 中建立網際網路對應負載平衡器

您必須先建立網際網路對應負載平衡器，讓 Azure 將從網際網路傳入的用戶端驗證流量分散到兩個 Web 應用程式 Proxy 伺服器。
  
> [!NOTE]
> 下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。 
  
當您已提供位置和資源群組的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。
  
> [!TIP]
> 對於包含本文及產生就緒-隨選即用 PowerShell 命令封鎖根據自訂設定 Microsoft Excel 設定活頁簿中的 PowerShell 命令的所有文字檔案，請參閱 ＜[同盟驗證 Office 365 中Azure 部署套件](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)。 
  
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

若要顯示指派到您網際網路對應負載平衡器的公用 IP 位址，請在本機電腦上的 Azure PowerShell 命令提示字元上執行以下命令：
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>決定您的同盟服務 FQDN 並建立 DNS 記錄

您需要決定 DNS 名稱以在網際網路上識別您的同盟伺服器名稱。Azure AD Connect 會以階段 5 中的此名稱設定 Office 365，這將會包含在 Office 365 用來與用戶端連線以取得安全性權杖所傳送的 URL 內。例如 fs.contoso.com (fs 表示同盟服務)。
  
一旦您有了同盟服務 FQDN，請針對同盟服務 FDQN 建立公用 DNS 網域 A 記錄，這會解析為 Azure 網際網路對應負載平衡器的公用 IP 位址。
  
|**名稱**|**類型**|**TTL**|**值**|
|:-----|:-----|:-----|:-----|
|同盟服務 FDQN  <br/> |A  <br/> |3600  <br/> |Azure 網際網路對應負載平衡器的公用 IP 位址 (透過上一節中的 **Write-Host** 命令顯示) <br/> |
   
範例如下：
  
|**名稱**|**類型**|**TTL**|**值**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
下一步，將 DNS 位址記錄新增至您的組織私人 DNS 命名空間，此命名空間會將您的同盟服務 FQDN 解析為 AD FS 伺服器內部負載平衡器的私人 IP 位址 (表格 I、項目 4、值欄)。
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>在 Azure 中建立 Web 應用程式 Proxy 伺服器虛擬機器

您可以使用下列 Azure PowerShell 命令的區塊，建立兩部 Web 應用程式 Proxy 伺服器的虛擬機器。  
  
請注意，下列 Azure PowerShell 命令集會使用下表中的值︰
  
- 表格 M，適用於虛擬機器
    
- 表格 R，適用於資源群組
    
- 表格 V，適用於虛擬網路設定
    
- 表格 S，適用於子網路
    
- 表格 I，適用於靜態 IP 位址
    
- 表格 A，適用於可用性設定組
    
重新叫用您定義中的表格 M[高可用性同盟驗證階段 2： 設定網域控制站](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)和表格 R、 V、 S、 I、 及中的 A[高可用性同盟驗證階段 1： 設定 Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。
  
當您已提供所有適當的值時，在 Azure PowerShell 命令提示字元上或 PowerShell ISE 中執行結果區塊。
  
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
> 由於這些虛擬機器是用於內部網路應用程式，系統並不會指派公用 IP 位址或 DNS 網域名稱標籤給它們，它們也不會公開在網際網路上。不過，這也表示您無法從 Azure 入口網站連線到這些虛擬機器。當您檢視虛擬機器的屬性時，無法使用**連線**選項。請使用遠端桌面連線附屬應用程式或另一個遠端桌面工具，透過使用虛擬機器的私人 IP 位址或內部網路 DNS 名稱，以及本機管理員帳戶的認證來與其連線。
  
以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。
  
**階段 4：Azure 中高可用性同盟驗證基礎結構的網際網路對應負載平衡器和 Web 應用程式 Proxy 伺服器**

![具有 Web 應用程式 Proxy 伺服器的 Azure 中之高可用性 Office 365 同盟驗證基礎結構的階段 4](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>下一步

使用[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)以繼續設定此工作負載。
  
## <a name="see-also"></a>另請參閱

[Azure 中的 Office 365 高可用性同盟驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Office 365 開發人員/測試環境的同盟身分識別](federated-identity-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)

[同盟的驗證選項](about-office-365-identity.md#federated-authentication-options)


