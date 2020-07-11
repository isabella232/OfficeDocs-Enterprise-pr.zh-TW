---
title: 高可用性同盟驗證階段2設定網域控制站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 摘要：在 Microsoft Azure 中設定 Microsoft 365 高可用性同盟驗證的網域控制站與目錄同步處理伺服器。
ms.openlocfilehash: 14939691e8dc114a6234bfee1ade7212762eae04
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102521"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="7e030-103">高可用性同盟驗證階段 2：設定網域控制站</span><span class="sxs-lookup"><span data-stu-id="7e030-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

<span data-ttu-id="7e030-104">在此階段，在 Azure 基礎結構服務中為 Microsoft 365 同盟驗證部署高可用性時，您會在 Azure 虛擬網路中設定兩個網域控制站與目錄同步處理伺服器。</span><span class="sxs-lookup"><span data-stu-id="7e030-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the directory synchronization server in the Azure virtual network.</span></span> <span data-ttu-id="7e030-105">然後用戶端 Web 驗證要求即可在 Azure 虛擬網路中驗證，而非透過站台對站台的 VPN 連線來傳送驗證流量至內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="7e030-105">Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7e030-106">Active Directory Federation Services (AD FS) 無法使用 Azure Active Directory (Azure AD) 取代 Active Directory 網域服務 (AD DS) 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="7e030-106">Active Directory Federation Services (AD FS) cannot use Azure Active Directory (Azure AD) as a substitute for Active Directory Domain Services (AD DS) domain controllers.</span></span> 
  
<span data-ttu-id="7e030-107">您必須先完成此階段，再移至[階段3：設定 AD FS 伺服器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="7e030-107">You must complete this phase before moving on to [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="7e030-108">請參閱[在 Azure 中部署 Microsoft 365 的高可用性同盟驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)，以瞭解所有階段。</span><span class="sxs-lookup"><span data-stu-id="7e030-108">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="7e030-109">在 Azure 中建立網域控制站虛擬機器</span><span class="sxs-lookup"><span data-stu-id="7e030-109">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="7e030-110">首先，您必須填寫表格 M 的 **虛擬機器名稱** 欄，然後依需求在 **大小下限** 欄中修改虛擬機器大小。</span><span class="sxs-lookup"><span data-stu-id="7e030-110">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="7e030-111">**項目**</span><span class="sxs-lookup"><span data-stu-id="7e030-111">**Item**</span></span>|<span data-ttu-id="7e030-112">**虛擬機器名稱**</span><span class="sxs-lookup"><span data-stu-id="7e030-112">**Virtual machine name**</span></span>|<span data-ttu-id="7e030-113">**圖庫影像**</span><span class="sxs-lookup"><span data-stu-id="7e030-113">**Gallery image**</span></span>|<span data-ttu-id="7e030-114">**儲存類型**</span><span class="sxs-lookup"><span data-stu-id="7e030-114">**Storage type**</span></span>|<span data-ttu-id="7e030-115">**大小下限**</span><span class="sxs-lookup"><span data-stu-id="7e030-115">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="7e030-116">1.</span><span class="sxs-lookup"><span data-stu-id="7e030-116">1.</span></span>  <br/> |![線條](./media/Common-Images/TableLine.png) <span data-ttu-id="7e030-118"> (第一個網域控制站，範例 DC1)</span><span class="sxs-lookup"><span data-stu-id="7e030-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="7e030-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7e030-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="7e030-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="7e030-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="7e030-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="7e030-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="7e030-122">2.</span><span class="sxs-lookup"><span data-stu-id="7e030-122">2.</span></span>  <br/> |![線條](./media/Common-Images/TableLine.png) <span data-ttu-id="7e030-124"> (第二個網域控制站，範例 DC2)</span><span class="sxs-lookup"><span data-stu-id="7e030-124">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="7e030-125">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7e030-125">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="7e030-126">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="7e030-126">Standard_LRS</span></span>  <br/> |<span data-ttu-id="7e030-127">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="7e030-127">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="7e030-128">3.</span><span class="sxs-lookup"><span data-stu-id="7e030-128">3.</span></span>  <br/> |![線條](./media/Common-Images/TableLine.png) <span data-ttu-id="7e030-130"> (目錄同步處理伺服器，範例 DS1) </span><span class="sxs-lookup"><span data-stu-id="7e030-130">(directory synchronization server, example DS1)</span></span>  <br/> |<span data-ttu-id="7e030-131">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7e030-131">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="7e030-132">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="7e030-132">Standard_LRS</span></span>  <br/> |<span data-ttu-id="7e030-133">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="7e030-133">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="7e030-134">4.</span><span class="sxs-lookup"><span data-stu-id="7e030-134">4.</span></span>  <br/> |![線條](./media/Common-Images/TableLine.png) <span data-ttu-id="7e030-136"> (第一個 AD FS 伺服器，範例 ADFS1) </span><span class="sxs-lookup"><span data-stu-id="7e030-136">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="7e030-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7e030-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="7e030-138">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="7e030-138">Standard_LRS</span></span>  <br/> |<span data-ttu-id="7e030-139">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="7e030-139">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="7e030-140">5.</span><span class="sxs-lookup"><span data-stu-id="7e030-140">5.</span></span>  <br/> |![線條](./media/Common-Images/TableLine.png) <span data-ttu-id="7e030-142"> (第二個 AD FS 伺服器，範例 ADFS2) </span><span class="sxs-lookup"><span data-stu-id="7e030-142">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="7e030-143">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7e030-143">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="7e030-144">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="7e030-144">Standard_LRS</span></span>  <br/> |<span data-ttu-id="7e030-145">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="7e030-145">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="7e030-146">6.</span><span class="sxs-lookup"><span data-stu-id="7e030-146">6.</span></span>  <br/> |![線條](./media/Common-Images/TableLine.png) <span data-ttu-id="7e030-148"> (第一個 web 應用程式 proxy 伺服器，範例 WEB1) </span><span class="sxs-lookup"><span data-stu-id="7e030-148">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="7e030-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7e030-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="7e030-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="7e030-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="7e030-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="7e030-151">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="7e030-152">7.</span><span class="sxs-lookup"><span data-stu-id="7e030-152">7.</span></span>  <br/> |![線條](./media/Common-Images/TableLine.png) <span data-ttu-id="7e030-154"> (第二個 web 應用程式 proxy 伺服器，範例 WEB2) </span><span class="sxs-lookup"><span data-stu-id="7e030-154">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="7e030-155">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="7e030-155">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="7e030-156">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="7e030-156">Standard_LRS</span></span>  <br/> |<span data-ttu-id="7e030-157">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="7e030-157">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="7e030-158">**表格 M-Azure 中 Microsoft 365 高可用性同盟驗證的虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="7e030-158">**Table M - Virtual machines for the high availability federated authentication for Microsoft 365 in Azure**</span></span>
  
<span data-ttu-id="7e030-159">如需虛擬機器大小的完整清單，請參閱[虛擬機器大小](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)。</span><span class="sxs-lookup"><span data-stu-id="7e030-159">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="7e030-160">下列 Azure PowerShell 命令區塊可建立兩個網域控制站的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="7e030-160">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="7e030-161">指定變數的值，並移除 \< and > 字元。</span><span class="sxs-lookup"><span data-stu-id="7e030-161">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="7e030-162">請注意，此 Azure PowerShell 命令區塊會使用下表中的值︰</span><span class="sxs-lookup"><span data-stu-id="7e030-162">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="7e030-163">表格 M，適用於虛擬機器</span><span class="sxs-lookup"><span data-stu-id="7e030-163">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="7e030-164">表格 R，適用於資源群組</span><span class="sxs-lookup"><span data-stu-id="7e030-164">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="7e030-165">表格 V，適用於虛擬網路設定</span><span class="sxs-lookup"><span data-stu-id="7e030-165">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="7e030-166">表格 S，適用於子網路</span><span class="sxs-lookup"><span data-stu-id="7e030-166">Table S, for your subnets</span></span>
    
- <span data-ttu-id="7e030-167">表格 I，適用於靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="7e030-167">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="7e030-168">表格 A，適用於可用性設定組</span><span class="sxs-lookup"><span data-stu-id="7e030-168">Table A, for your availability sets</span></span>
    
<span data-ttu-id="7e030-169">請記得您在[階段1： Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)中定義的表格 R、V、S、I 和 A。</span><span class="sxs-lookup"><span data-stu-id="7e030-169">Recall that you defined Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="7e030-170">[!附註] 下列命令集會使用最新版的 Azure PowerShell。</span><span class="sxs-lookup"><span data-stu-id="7e030-170">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="7e030-171">請參閱[Azure PowerShell 入門](https://docs.microsoft.com/powershell/azure/get-started-azureps)。</span><span class="sxs-lookup"><span data-stu-id="7e030-171">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="7e030-172">當您已經提供所有正確的值時，在 Azure PowerShell 提示中或本機電腦的 PowerShell 整合式指令碼環境 (ISE) 中執行結果區塊。</span><span class="sxs-lookup"><span data-stu-id="7e030-172">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="7e030-173">若要根據您的自訂設定來產生現成 PowerShell 命令區塊，請使用此[Microsoft Excel 配置活頁簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="7e030-173">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="7e030-174">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span><span class="sxs-lookup"><span data-stu-id="7e030-174">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="7e030-175">However, this also means that you cannot connect to them from the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="7e030-175">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="7e030-176">The **Connect** option is unavailable when you view the properties of the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="7e030-176">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="7e030-177">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span><span class="sxs-lookup"><span data-stu-id="7e030-177">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="7e030-178">設定第一個網域控制站</span><span class="sxs-lookup"><span data-stu-id="7e030-178">Configure the first domain controller</span></span>

<span data-ttu-id="7e030-179">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine.</span><span class="sxs-lookup"><span data-stu-id="7e030-179">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine.</span></span> <span data-ttu-id="7e030-180">Use its intranet DNS or computer name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="7e030-180">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="7e030-181">接下來，**在第一個網域控制站虛擬機器**的 Windows PowerShell 命令提示字元中，使用此命令將額外的資料磁片新增至第一個網域控制站：</span><span class="sxs-lookup"><span data-stu-id="7e030-181">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="7e030-182">下一步，使用 **ping** 命令來對組織網路上的資源名稱和 IP 位址執行 Ping，以測試第一個網域控制站對組織網路上位置的連線狀況。</span><span class="sxs-lookup"><span data-stu-id="7e030-182">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="7e030-183">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network.</span><span class="sxs-lookup"><span data-stu-id="7e030-183">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network.</span></span> <span data-ttu-id="7e030-184">If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span><span class="sxs-lookup"><span data-stu-id="7e030-184">If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="7e030-185">下一步，從第一個網域控制站上的 Windows PowerShell 命令提示字元，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7e030-185">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="7e030-186">You will be prompted to supply the credentials of a domain administrator account.</span><span class="sxs-lookup"><span data-stu-id="7e030-186">You will be prompted to supply the credentials of a domain administrator account.</span></span> <span data-ttu-id="7e030-187">The computer will restart.</span><span class="sxs-lookup"><span data-stu-id="7e030-187">The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="7e030-188">設定第二個網域控制站</span><span class="sxs-lookup"><span data-stu-id="7e030-188">Configure the second domain controller</span></span>

<span data-ttu-id="7e030-189">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine.</span><span class="sxs-lookup"><span data-stu-id="7e030-189">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine.</span></span> <span data-ttu-id="7e030-190">Use its intranet DNS or computer name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="7e030-190">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="7e030-191">接下來，您必須使用**第二個網域控制站虛擬機器上**的 Windows PowerShell 命令提示字元，將額外的資料磁片新增至第二個網域控制站。</span><span class="sxs-lookup"><span data-stu-id="7e030-191">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="7e030-192">接著，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7e030-192">Next, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="7e030-193">You will be prompted to supply the credentials of a domain administrator account.</span><span class="sxs-lookup"><span data-stu-id="7e030-193">You will be prompted to supply the credentials of a domain administrator account.</span></span> <span data-ttu-id="7e030-194">The computer will restart.</span><span class="sxs-lookup"><span data-stu-id="7e030-194">The computer will restart.</span></span>
  
<span data-ttu-id="7e030-195">下一步，您需要更新虛擬網路的 DNS 伺服器，如此一來，此 Azure 會指派兩個新的網域控制站 IP 位址給虛擬機器，以便使用虛擬機器的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7e030-195">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="7e030-196">填寫變數，然後在本機電腦上的 Windows PowerShell 命令提示字元中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="7e030-196">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```powershell
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

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="7e030-197">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers.</span><span class="sxs-lookup"><span data-stu-id="7e030-197">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers.</span></span> <span data-ttu-id="7e030-198">Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span><span class="sxs-lookup"><span data-stu-id="7e030-198">Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="7e030-199">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers.</span><span class="sxs-lookup"><span data-stu-id="7e030-199">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers.</span></span> <span data-ttu-id="7e030-200">Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span><span class="sxs-lookup"><span data-stu-id="7e030-200">Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a><span data-ttu-id="7e030-201">設定目錄同步處理伺服器</span><span class="sxs-lookup"><span data-stu-id="7e030-201">Configure the directory synchronization server</span></span>

<span data-ttu-id="7e030-202">使用您選擇的遠端桌面用戶端，建立與目錄同步處理伺服器虛擬機器的遠端桌面連線。</span><span class="sxs-lookup"><span data-stu-id="7e030-202">Use the remote desktop client of your choice and create a remote desktop connection to the directory synchronization server virtual machine.</span></span> <span data-ttu-id="7e030-203">請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。</span><span class="sxs-lookup"><span data-stu-id="7e030-203">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="7e030-204">接下來，在 Windows PowerShell 提示字元，使用下列命令將其加入適當的 AD DS 網域。</span><span class="sxs-lookup"><span data-stu-id="7e030-204">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="7e030-205">以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。</span><span class="sxs-lookup"><span data-stu-id="7e030-205">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="7e030-206">**階段2： Azure 中高可用性同盟驗證基礎結構的網域控制站及目錄同步處理伺服器**</span><span class="sxs-lookup"><span data-stu-id="7e030-206">**Phase 2: The domain controllers and directory synchronization server for your high availability federated authentication infrastructure in Azure**</span></span>

![Azure 中具有網域控制站之高可用性 Microsoft 365 同盟驗證基礎結構的階段2](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="7e030-208">下一步</span><span class="sxs-lookup"><span data-stu-id="7e030-208">Next step</span></span>

<span data-ttu-id="7e030-209">使用[階段3：設定 AD FS 伺服器](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)以繼續設定此工作負載。</span><span class="sxs-lookup"><span data-stu-id="7e030-209">Use [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7e030-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e030-210">See Also</span></span>

[<span data-ttu-id="7e030-211">Azure 中的 Microsoft 365 高可用性同盟驗證</span><span class="sxs-lookup"><span data-stu-id="7e030-211">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="7e030-212">Microsoft 365 開發/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="7e030-212">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="7e030-213">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="7e030-213">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)


