---
title: 高可用性同盟驗證階段 2 設定網域控制站
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 摘要：在 Microsoft Azure 中設定 Office 365 高可用性同盟驗證的網域控制站和 DirSync 伺服器。
ms.openlocfilehash: bda22a1df0165724f660019e28a9f088280fea4f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491332"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="c334c-103">高可用性同盟驗證階段 2：設定網域控制站</span><span class="sxs-lookup"><span data-stu-id="c334c-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="c334c-104">**摘要：** 在 Microsoft Azure 中設定 Office 365 高可用性同盟驗證的網域控制站和 DirSync 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c334c-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="c334c-p101">在 Azure 基礎結構服務中部署 Office 365 同盟驗證高可用性的此階段，您會在 Azure 虛擬網路中設定兩個網域控制站和 DirSync 伺服器。然後用戶端 Web 驗證要求即可在 Azure 虛擬網路中驗證，而非透過站台對站台的 VPN 連線來傳送驗證流量至內部部署網路。</span><span class="sxs-lookup"><span data-stu-id="c334c-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="c334c-107">Active Directory Federation Services (AD FS) 無法使用 Azure Active Directory Domain Services 代替 Active Directory 網域服務的網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c334c-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Active Directory Domain Services domain controllers.</span></span> 
  
<span data-ttu-id="c334c-108">您必須先完成此階段，才可繼續 [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="c334c-108">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="c334c-109">所有階段，請參閱[在 Azure 中的 Office 365 部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="c334c-109">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="c334c-110">在 Azure 中建立網域控制站虛擬機器</span><span class="sxs-lookup"><span data-stu-id="c334c-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="c334c-111">首先，您必須填寫表格 M 的 **虛擬機器名稱** 欄，然後依需求在 **大小下限** 欄中修改虛擬機器大小。</span><span class="sxs-lookup"><span data-stu-id="c334c-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="c334c-112">**項目**</span><span class="sxs-lookup"><span data-stu-id="c334c-112">**Item**</span></span>|<span data-ttu-id="c334c-113">**虛擬機器名稱**</span><span class="sxs-lookup"><span data-stu-id="c334c-113">**Virtual machine name**</span></span>|<span data-ttu-id="c334c-114">**圖庫影像**</span><span class="sxs-lookup"><span data-stu-id="c334c-114">**Gallery image**</span></span>|<span data-ttu-id="c334c-115">**儲存類型**</span><span class="sxs-lookup"><span data-stu-id="c334c-115">**Storage type**</span></span>|<span data-ttu-id="c334c-116">**大小下限**</span><span class="sxs-lookup"><span data-stu-id="c334c-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="c334c-117">1.</span><span class="sxs-lookup"><span data-stu-id="c334c-117">1.</span></span>  <br/> |<span data-ttu-id="c334c-118">![](./media/Common-Images/TableLine.png) (第一個網域控制站，範例 DC1)</span><span class="sxs-lookup"><span data-stu-id="c334c-118">![](./media/Common-Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="c334c-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="c334c-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="c334c-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="c334c-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="c334c-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="c334c-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="c334c-122">2.</span><span class="sxs-lookup"><span data-stu-id="c334c-122">2.</span></span>  <br/> |<span data-ttu-id="c334c-123">![](./media/Common-Images/TableLine.png) (第二個網域控制站，範例 DC2)</span><span class="sxs-lookup"><span data-stu-id="c334c-123">![](./media/Common-Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="c334c-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="c334c-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="c334c-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="c334c-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="c334c-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="c334c-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="c334c-127">3.</span><span class="sxs-lookup"><span data-stu-id="c334c-127">3.</span></span>  <br/> |<span data-ttu-id="c334c-128">![](./media/Common-Images/TableLine.png)（DirSync 伺服器，範例 DS1）</span><span class="sxs-lookup"><span data-stu-id="c334c-128">![](./media/Common-Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="c334c-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="c334c-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="c334c-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="c334c-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="c334c-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="c334c-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="c334c-132">4.</span><span class="sxs-lookup"><span data-stu-id="c334c-132">4.</span></span>  <br/> |<span data-ttu-id="c334c-133">![](./media/Common-Images/TableLine.png)（第一部 AD FS 伺服器，範例 ADFS1）</span><span class="sxs-lookup"><span data-stu-id="c334c-133">![](./media/Common-Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="c334c-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="c334c-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="c334c-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="c334c-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="c334c-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="c334c-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="c334c-137">5.</span><span class="sxs-lookup"><span data-stu-id="c334c-137">5.</span></span>  <br/> |<span data-ttu-id="c334c-138">![](./media/Common-Images/TableLine.png)（第二個 AD FS 伺服器，範例 ADFS2）</span><span class="sxs-lookup"><span data-stu-id="c334c-138">![](./media/Common-Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="c334c-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="c334c-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="c334c-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="c334c-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="c334c-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="c334c-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="c334c-142">6.</span><span class="sxs-lookup"><span data-stu-id="c334c-142">6.</span></span>  <br/> |<span data-ttu-id="c334c-143">![](./media/Common-Images/TableLine.png)（第一個 web 應用程式 proxy 伺服器，範例 WEB1）</span><span class="sxs-lookup"><span data-stu-id="c334c-143">![](./media/Common-Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="c334c-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="c334c-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="c334c-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="c334c-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="c334c-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="c334c-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="c334c-147">7.</span><span class="sxs-lookup"><span data-stu-id="c334c-147">7.</span></span>  <br/> |<span data-ttu-id="c334c-148">![](./media/Common-Images/TableLine.png)（第二個 web 應用程式 proxy 伺服器，範例 WEB2）</span><span class="sxs-lookup"><span data-stu-id="c334c-148">![](./media/Common-Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="c334c-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="c334c-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="c334c-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="c334c-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="c334c-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="c334c-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="c334c-152">**表格 M-Azure 中 Office 365 的高可用性同盟驗證的虛擬機器**</span><span class="sxs-lookup"><span data-stu-id="c334c-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="c334c-153">如需虛擬機器大小的完整清單，請參閱[虛擬機器大小](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes)。</span><span class="sxs-lookup"><span data-stu-id="c334c-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="c334c-154">下列 Azure PowerShell 命令區塊可建立兩個網域控制站的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="c334c-154">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="c334c-155">為指定值的變數，移除\<和 > 字元。</span><span class="sxs-lookup"><span data-stu-id="c334c-155">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="c334c-156">請注意，此 Azure PowerShell 命令區塊會使用下表中的值︰</span><span class="sxs-lookup"><span data-stu-id="c334c-156">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="c334c-157">表格 M，適用於虛擬機器</span><span class="sxs-lookup"><span data-stu-id="c334c-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="c334c-158">表格 R，適用於資源群組</span><span class="sxs-lookup"><span data-stu-id="c334c-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="c334c-159">表格 V，適用於虛擬網路設定</span><span class="sxs-lookup"><span data-stu-id="c334c-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="c334c-160">表格 S，適用於子網路</span><span class="sxs-lookup"><span data-stu-id="c334c-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="c334c-161">表格 I，適用於靜態 IP 位址</span><span class="sxs-lookup"><span data-stu-id="c334c-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="c334c-162">表格 A，適用於可用性設定組</span><span class="sxs-lookup"><span data-stu-id="c334c-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="c334c-163">還記得您定義表格 R、 V、 S、 I 和 A 在[高可用性同盟驗證階段 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="c334c-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="c334c-p104">下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="c334c-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="c334c-166">當您已經提供所有正確的值時，在 Azure PowerShell 提示中或本機電腦的 PowerShell 整合式指令碼環境 (ISE) 中執行結果區塊。</span><span class="sxs-lookup"><span data-stu-id="c334c-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
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

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="c334c-p105">由於這些虛擬機器是用於內部網路應用程式，並不會指派公用 IP 位址或 DNS 網域名稱標籤，也不會曝露在網際網路上。不過，這也表示您無法透過 Azure 入口網站與虛擬機器連線。當您檢視虛擬機器的屬性時，無法使用**連線**選項。請使用遠端桌面連線附屬應用程式或另一個遠端桌面工具，透過使用其私人 IP 位址或內部網路 DNS 名稱來與虛擬機器連線。</span><span class="sxs-lookup"><span data-stu-id="c334c-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="c334c-171">設定第一個網域控制站</span><span class="sxs-lookup"><span data-stu-id="c334c-171">Configure the first domain controller</span></span>

<span data-ttu-id="c334c-p106">使用您所選的遠端桌面用戶端，建立第一個網域控制站虛擬機器的遠端桌面連線。請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。</span><span class="sxs-lookup"><span data-stu-id="c334c-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="c334c-174">從 Windows PowerShell 命令提示字元**上第一個網域控制站虛擬機器**，接下來，使用此命令的第一個網域控制站新增額外的資料磁碟：</span><span class="sxs-lookup"><span data-stu-id="c334c-174">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="c334c-175">下一步，使用 **ping** 命令來對組織網路上的資源名稱和 IP 位址執行 Ping，以測試第一個網域控制站對組織網路上位置的連線狀況。</span><span class="sxs-lookup"><span data-stu-id="c334c-175">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="c334c-p107">此程序可確保 DNS 名稱解析運作正常 (虛擬機器已透過內部部署 DNS 伺服器正確設定)，而且封包可在跨單位虛擬網路間傳送。如果此基本測試失敗，請連絡您的 IT 部門，以針對 DNS 名稱解析和封包傳遞問題進行移難排解。</span><span class="sxs-lookup"><span data-stu-id="c334c-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="c334c-178">下一步，從第一個網域控制站上的 Windows PowerShell 命令提示字元，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c334c-178">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="c334c-p108">系統會提示您提供網域管理員帳戶的認證。電腦將會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="c334c-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="c334c-181">設定第二個網域控制站</span><span class="sxs-lookup"><span data-stu-id="c334c-181">Configure the second domain controller</span></span>

<span data-ttu-id="c334c-p109">使用您所選的遠端桌面用戶端，建立第二個網域控制站虛擬機器的遠端桌面連線。請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。</span><span class="sxs-lookup"><span data-stu-id="c334c-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="c334c-184">接下來，您需要將額外的資料磁碟新增至第二個網域控制站，使用此命令中，從 Windows PowerShell 命令提示字元**上第二個網域控制站虛擬機器**：</span><span class="sxs-lookup"><span data-stu-id="c334c-184">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="c334c-185">接著，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c334c-185">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="c334c-p110">系統會提示您提供網域管理員帳戶的認證。電腦將會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="c334c-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="c334c-188">下一步，您需要更新虛擬網路的 DNS 伺服器，如此一來，此 Azure 會指派兩個新的網域控制站 IP 位址給虛擬機器，以便使用虛擬機器的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c334c-188">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="c334c-189">填寫 [變數並再從 Windows PowerShell 命令提示字元執行這些命令在本機電腦上：</span><span class="sxs-lookup"><span data-stu-id="c334c-189">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
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

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="c334c-p112">請注意，我們會重新啟動兩個網域控制站，所以這兩個控制站不會像 DNS 伺服器一樣，透過內部部署 DNS 伺服器來設定。因為這兩個控制站本身就是 DNS 伺服器，當系統提示其作為網域控制站時，這些控制站會自動透過內部部署 DNS 伺服器設定為 DNS 轉寄站。</span><span class="sxs-lookup"><span data-stu-id="c334c-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="c334c-p113">下一步，我們需要建立一個 Active Directory 複寫站台，以確保 Azure 的虛擬網路中的伺服器會使用本機網域控制站。請使用網域管理員帳戶與其中一個網域控制站連線，並從管理員層級的 Windows PowerShell 提示執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c334c-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="c334c-194">設定 DirSync 伺服器</span><span class="sxs-lookup"><span data-stu-id="c334c-194">Configure the DirSync server</span></span>

<span data-ttu-id="c334c-195">使用您所選的遠端桌面用戶端，建立 DirSync 伺服器虛擬機器的遠端桌面連線。</span><span class="sxs-lookup"><span data-stu-id="c334c-195">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine.</span></span> <span data-ttu-id="c334c-196">請使用其內部網路 DNS 或本機管理員帳戶的電腦名稱和認證。</span><span class="sxs-lookup"><span data-stu-id="c334c-196">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="c334c-197">接下來，將其加入適當的 AD DS 網域，在 Windows PowerShell 提示字元使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="c334c-197">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="c334c-198">以下是成功完成此階段的設定結果 (包含電腦名稱的預留位置)。</span><span class="sxs-lookup"><span data-stu-id="c334c-198">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="c334c-199">**階段 2：Azure 中的高可用性同盟驗證基礎結構的網域控制站和 DirSync 伺服器。**</span><span class="sxs-lookup"><span data-stu-id="c334c-199">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![階段 2 的高可用性 Office 365 同盟驗證基礎結構在 Azure 中的具有網域控制站](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="c334c-201">下一步</span><span class="sxs-lookup"><span data-stu-id="c334c-201">Next step</span></span>

<span data-ttu-id="c334c-202">使用[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)以繼續設定此工作負載。</span><span class="sxs-lookup"><span data-stu-id="c334c-202">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c334c-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c334c-203">See Also</span></span>

[<span data-ttu-id="c334c-204">Azure 中的 Office 365 高可用性同盟驗證</span><span class="sxs-lookup"><span data-stu-id="c334c-204">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="c334c-205">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="c334c-205">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="c334c-206">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="c334c-206">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="c334c-207">同盟的驗證選項</span><span class="sxs-lookup"><span data-stu-id="c334c-207">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


