---
title: 基底組態開發/測試環境
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
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 摘要：在 Microsoft Azure 中建立簡化的內部網路作為開發/測試環境。
ms.openlocfilehash: f065f9fa31b6793933dc4eec0d840bd1320a8891
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915278"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="ee431-103">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="ee431-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="ee431-104">**摘要：** 在 Microsoft Azure 中建立簡化的內部網路作為開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="ee431-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="ee431-105">本文提供逐步指示，以在 Azure 中建立下列基底組態開發/測試環境：</span><span class="sxs-lookup"><span data-stu-id="ee431-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="ee431-106">**圖 1：基底組態開發/測試環境**</span><span class="sxs-lookup"><span data-stu-id="ee431-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![Azure 中具有 CLIENT1 虛擬機器的基底組態的階段 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="ee431-p101">圖 1 中的基底組態開發/測試環境包含名為 TestLab 的雲端專用 Azure 虛擬網路中的 Corpnet 子網路，其可模擬連線到網際網路的簡化私人內部網路。它包含執行 WIndows Server 2016 的三個 Azure 虛擬機器：</span><span class="sxs-lookup"><span data-stu-id="ee431-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running WIndows Server 2016:</span></span>
  
- <span data-ttu-id="ee431-110">DC1 已設定為內部網路網域控制站和網域名稱系統 (DNS) 伺服器</span><span class="sxs-lookup"><span data-stu-id="ee431-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="ee431-111">APP1 已設定為一般應用程式和 Web 伺服器</span><span class="sxs-lookup"><span data-stu-id="ee431-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="ee431-112">CLIENT1 做為內部網路用戶端</span><span class="sxs-lookup"><span data-stu-id="ee431-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="ee431-113">此設定可讓 DC1、APP1、CLIENT1 及其他 Corpnet 子網路的電腦：</span><span class="sxs-lookup"><span data-stu-id="ee431-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="ee431-114">連線到網際網路以安裝更新、即時存取網際網路資源，並加入公用雲端技術，例如 Microsoft Office 365 與其他 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="ee431-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="ee431-115">從已連線到網際網路或您組織網路的電腦使用遠端桌面連線進行遠端管理。</span><span class="sxs-lookup"><span data-stu-id="ee431-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="ee431-116">您可以將產生的測試環境：</span><span class="sxs-lookup"><span data-stu-id="ee431-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="ee431-117">用於應用程式開發與測試。</span><span class="sxs-lookup"><span data-stu-id="ee431-117">For application development and testing.</span></span>
    
- <span data-ttu-id="ee431-118">做為自己設計的延伸測試環境之初始設定，其中包含其他虛擬機器、Azure 服務或其他 Microsoft 雲端產品，如 Office 365 及 Enterprise Security + Mobility (EMS)。</span><span class="sxs-lookup"><span data-stu-id="ee431-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility (EMS).</span></span>
    
<span data-ttu-id="ee431-119">設定 Azure 中的基底組態測試環境有四個階段：</span><span class="sxs-lookup"><span data-stu-id="ee431-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="ee431-120">建立虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="ee431-120">Create the virtual network.</span></span>
    
2. <span data-ttu-id="ee431-121">設定 DC1。</span><span class="sxs-lookup"><span data-stu-id="ee431-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="ee431-122">設定 APP1。</span><span class="sxs-lookup"><span data-stu-id="ee431-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="ee431-123">設定 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="ee431-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="ee431-p102">如果您沒有 Azure 訂閱，可以在[試用 Azure](https://azure.microsoft.com/pricing/free-trial/) 中註冊免費試用版。如果您擁有 MSDN 或 Visual Studio 訂閱，請參閱 [Visual Studio 訂閱者每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。</span><span class="sxs-lookup"><span data-stu-id="ee431-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ee431-p103">Azure 中的虛擬機器在執行時會持續產生成本。此成本是根據您的免費試用版、MSDN 訂閱或付費訂閱收費。如需執行 Azure 虛擬機器的成本相關資訊，請參閱[虛擬機器價格詳細資料](https://azure.microsoft.com/pricing/details/virtual-machines/)與 [Azure 價格計算機](https://azure.microsoft.com/pricing/calculator/)。若要降低成本，請參閱[降低 Azure 中測試環境虛擬機器的成本](base-configuration-dev-test-environment.md#mincost)。</span><span class="sxs-lookup"><span data-stu-id="ee431-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="ee431-131">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="ee431-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="ee431-132">階段 1：建立虛擬網路</span><span class="sxs-lookup"><span data-stu-id="ee431-132">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="ee431-133">首先，啟動 Azure PowerShell 提示。</span><span class="sxs-lookup"><span data-stu-id="ee431-133">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ee431-p104">下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="ee431-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="ee431-136">使用下列命令登入您的 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="ee431-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="ee431-137">按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)以取得內含此文章中所有 PowerShell 命令的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="ee431-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="ee431-138">使用下列命令取得訂用帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="ee431-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="ee431-p105">設定 Azure 訂用帳戶。以正確的名稱取代括號中的所有項目 (包括 < 和 > 字元)。</span><span class="sxs-lookup"><span data-stu-id="ee431-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="ee431-p106">接著，為您的基底組態測試實驗室建立新的資源群組。若要判斷資源群組名稱是否是唯一的，可使用此命令來列出現有的資源群組。</span><span class="sxs-lookup"><span data-stu-id="ee431-p106">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="ee431-p107">使用這些命令建立新的資源群組。以正確的名稱取代引號內的所有項目 (包括 < 和 > 字元)。</span><span class="sxs-lookup"><span data-stu-id="ee431-p107">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="ee431-145">接著，您會建立將裝載基底組態 Corpnet 子網路的 TestLab 虛擬網路，並以網路安全性群組來保護它。</span><span class="sxs-lookup"><span data-stu-id="ee431-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="ee431-146">這是您目前的設定。</span><span class="sxs-lookup"><span data-stu-id="ee431-146">This is your current configuration.</span></span>
  
![Azure 中具有虛擬網路與子網路的基底組態的階段 1](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="ee431-148">階段 2：設定 DC1</span><span class="sxs-lookup"><span data-stu-id="ee431-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="ee431-149">在此階段中，我們會建立 DC1 虛擬機器，並將其設定為 corp.contoso.com Windows Server Active Directory (AD) 網域的網域控制站以及 TestLab 虛擬網路之虛擬機器的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee431-149">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>
  
<span data-ttu-id="ee431-150">若要建立 DC1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-150">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="ee431-p108">系統會提示您輸入 DC1 上本機系統管理員帳戶的使用者名稱和密碼。使用強式密碼，並將名稱和密碼記錄於安全的位置。</span><span class="sxs-lookup"><span data-stu-id="ee431-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="ee431-153">接下來，連線到 DC1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="ee431-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="ee431-154">使用本機系統管理員帳戶認證連線到 DC1</span><span class="sxs-lookup"><span data-stu-id="ee431-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="ee431-155">在 [Azure 入口網站](https://portal.azure.com)中，按一下 **[資源群組] >** [新的資源群組名稱] **> [DC1] > [連線]**。</span><span class="sxs-lookup"><span data-stu-id="ee431-155">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="ee431-p109">在開啟的窗格中，按一下 [下載 RDP 檔案]****。開啟所下載的 DC1.rdp 檔案，然後按一下 [連線]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-p109">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="ee431-158">指定 DC1 本機系統管理員帳戶名稱：</span><span class="sxs-lookup"><span data-stu-id="ee431-158">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="ee431-159">對於 Windows 7：</span><span class="sxs-lookup"><span data-stu-id="ee431-159">For Windows 7:</span></span>
    
    <span data-ttu-id="ee431-p110">在 [Windows 安全性]**** 對話方塊中，按一下 [使用其他帳戶]****。在 [使用者名稱]**** 中，輸入 **DC1\\**[本機系統管理員帳戶名稱]。</span><span class="sxs-lookup"><span data-stu-id="ee431-p110">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="ee431-162">對於 Windows 8 或 Windows 10：</span><span class="sxs-lookup"><span data-stu-id="ee431-162">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="ee431-p111">在 [Windows 安全性]**** 對話方塊中，按一下 [更多選項]****，然後按 [使用不同帳戶]****。在 [使用者名稱]**** 中，輸入 **DC1\\**[本機系統管理員帳戶名稱]。</span><span class="sxs-lookup"><span data-stu-id="ee431-p111">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="ee431-165">在 [密碼]**** 中，輸入本機系統管理員帳戶的密碼，然後按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-165">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="ee431-166">出現提示時，按一下 [是]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-166">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="ee431-167">接著，使用此命令在 DC1 上系統管理員層級 Windows PowerShell 命令提示字元將額外的資料磁碟新增為新的磁碟區 (磁碟機代號 F:)。</span><span class="sxs-lookup"><span data-stu-id="ee431-167">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="ee431-p112">接著，將 DC1 設定為網域控制站和 corp.contoso.com 網域的 DNS 伺服器。在系統管理員層級 Windows PowerShell 命令提示字元執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-p112">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="ee431-p113">您必須指定安全模式的系統管理員密碼。將此密碼儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="ee431-p113">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="ee431-172">請注意，這些命令可能需要數分鐘才能完成。</span><span class="sxs-lookup"><span data-stu-id="ee431-172">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="ee431-173">DC1 重新啟動後，重新連線到 DC1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="ee431-173">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="ee431-174">使用網域認證連線到 DC1</span><span class="sxs-lookup"><span data-stu-id="ee431-174">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="ee431-175">在 [Azure 入口網站](https://portal.azure.com)中，按一下 **[資源群組] >** [您的資源群組名稱] **> [DC1] > [連線]**。</span><span class="sxs-lookup"><span data-stu-id="ee431-175">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="ee431-176">執行所下載的 DC1.rdp 檔案，然後按一下 [連線]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-176">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="ee431-p114">在 [Windows 安全性]**** 中，按一下 [使用其他帳戶]****。在 [使用者名稱]**** 中，輸入 **CORP\\**[本機系統管理員帳戶名稱]。</span><span class="sxs-lookup"><span data-stu-id="ee431-p114">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="ee431-179">在 [密碼]**** 中，輸入本機系統管理員帳戶的密碼，然後按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-179">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="ee431-180">出現提示時，按一下 [是]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-180">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="ee431-p115">接下來，建立 Active Directory 中的使用者帳戶，可在登入 CORP 網域成員電腦時使用。在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-p115">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="ee431-p116">請注意，此命令會提示您提供 User1 帳戶密碼。由於這個帳戶將會用於所有 CORP 網域成員電腦的遠端桌面連線，請選擇強式密碼。記錄 User1 帳戶密碼，並將它儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="ee431-p116">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="ee431-p117">接下來，將新的 User1 帳戶設定為企業系統管理員。在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-p117">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="ee431-188">關閉 DC1 的遠端桌面工作階段，然後使用 CORP\\User1 帳戶重新連線。</span><span class="sxs-lookup"><span data-stu-id="ee431-188">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="ee431-189">接下來，若要允許 Ping 工具的流量，請在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-189">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="ee431-190">這是您目前的設定。</span><span class="sxs-lookup"><span data-stu-id="ee431-190">This is your current configuration.</span></span>
  
![Azure 中具有 DC1 虛擬機器的基底組態的階段 2](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="ee431-192">階段 3：設定 APP1</span><span class="sxs-lookup"><span data-stu-id="ee431-192">Phase 3: Configure APP1</span></span>

<span data-ttu-id="ee431-193">APP1 提供網頁和檔案共用服務。</span><span class="sxs-lookup"><span data-stu-id="ee431-193">APP1 provides web and file sharing services.</span></span>

<span data-ttu-id="ee431-194">若要建立 APP1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-194">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="ee431-195">接下來，使用 APP1 本機系統管理員帳戶名稱和密碼連線到 APP1 虛擬機器，然後開啟 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ee431-195">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ee431-196">若要檢查 APP1 和 DC1 之間的名稱解析和網路通訊，請執行 **ping dc1.corp.contoso.com** 命令，並確認有四個回覆。</span><span class="sxs-lookup"><span data-stu-id="ee431-196">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="ee431-197">接下來在 Windows PowerShell 命令提示字元使用以下命令將 APP1 虛擬機器加入 CORP 網域。</span><span class="sxs-lookup"><span data-stu-id="ee431-197">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="ee431-198">請注意，您必須在執行 **Add-Computer** 命令之後，提供 CORP\\User1 網域帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="ee431-198">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="ee431-199">APP1 重新啟動之後，使用 CORP\\User1 帳戶連線至 APP1，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ee431-199">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ee431-200">接下來，在 APP1 上的 Windows PowerShell 命令提示字元中使用此命令讓 APP1 成為 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ee431-200">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="ee431-201">接下來，使用這些 PowerShell 命令在 APP1 上的資料夾內建立共用資料夾及文字檔。</span><span class="sxs-lookup"><span data-stu-id="ee431-201">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="ee431-202">這是您目前的設定。</span><span class="sxs-lookup"><span data-stu-id="ee431-202">This is your current configuration.</span></span>
  
![Azure 中具有 APP1 虛擬機器的基底組態的階段 3](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="ee431-204">階段 4：設定 CLIENT1</span><span class="sxs-lookup"><span data-stu-id="ee431-204">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="ee431-205">CLIENT1 可在 Contoso 內部網路上做為一般的膝上型電腦、平板電腦或桌上型電腦。</span><span class="sxs-lookup"><span data-stu-id="ee431-205">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>

> [!NOTE]  
> <span data-ttu-id="ee431-p118">下列命令集可建立執行 Windows Server 2016 資料中心的 CLIENT1，其適用於所有類型的 Azure 訂閱。如果您有以 Visual Studio 為基礎的 Azure 訂閱，則可以使用 [Azure 入口網站](https://portal.azure.com)建立執行 Windows 10 的 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="ee431-p118">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 
  
<span data-ttu-id="ee431-208">若要建立 CLIENT1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-208">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="ee431-209">接下來，使用 CLIENT1 本機系統管理員帳戶名稱和密碼連線到 CLIENT1 虛擬機器，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ee431-209">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ee431-210">若要檢查 CLIENT1 和 DC1 之間的名稱解析和網路通訊，請在 Windows PowerShell 命令提示字元執行 **ping dc1.corp.contoso.com** 命令，並確認有四個回覆。</span><span class="sxs-lookup"><span data-stu-id="ee431-210">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="ee431-211">接下來在 Windows PowerShell 命令提示字元使用以下命令將 CLIENT1 虛擬機器加入 CORP 網域。</span><span class="sxs-lookup"><span data-stu-id="ee431-211">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="ee431-212">請注意，您必須在執行 **Add-Computer** 命令之後，提供 CORP\\User1 網域帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="ee431-212">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="ee431-213">CLIENT1 重新啟動之後，使用 CORP\\User1 帳戶名稱和密碼連線至 CLIENT1，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ee431-213">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ee431-214">接下來，確認您可以從 CLIENT1 存取 APP1 上的 Web 及檔案共用資源。</span><span class="sxs-lookup"><span data-stu-id="ee431-214">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="ee431-215">確認 CLIENT 存取 APP1</span><span class="sxs-lookup"><span data-stu-id="ee431-215">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="ee431-216">在 [伺服器管理員] 的樹狀窗格中，按一下 [本機伺服器]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-216">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="ee431-217">在 [CLIENT1 的屬性]**** 中，按一下 [IE 增強式安全性設定]**** 旁邊的 [開啟]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-217">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="ee431-218">在 [Internet Explorer 增強式安全性設定]**** 中，為 [管理員]**** 和 [使用者]**** 按一下 [關閉]****，然後按 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-218">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="ee431-219">從 [開始] 畫面，按一下 [Internet Explorer]****，然後按 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="ee431-219">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="ee431-p119">在網址列中，輸入 **http:\//app1.corp.contoso.com/**，然後按 ENTER 鍵。您應該會看到 APP1 的預設網際網路資訊服務網頁。</span><span class="sxs-lookup"><span data-stu-id="ee431-p119">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="ee431-222">在桌面工作列中，按一下 [檔案總管] 圖示。</span><span class="sxs-lookup"><span data-stu-id="ee431-222">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="ee431-p120">在網址列中，輸入 **\\\\app1\\檔案**，然後按 ENTER 鍵。您應該會看到資料夾視窗中的檔案共用資料夾內容。</span><span class="sxs-lookup"><span data-stu-id="ee431-p120">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="ee431-p121">在 [檔案]**** 共用資料夾視窗中，按兩下 **Example.txt** 檔案。您應該會看到 Example.txt 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="ee431-p121">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="ee431-227">關閉 **example.txt - 記事本**以及 [檔案]**** 共用資料夾視窗。</span><span class="sxs-lookup"><span data-stu-id="ee431-227">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="ee431-228">這是您的最終設定。</span><span class="sxs-lookup"><span data-stu-id="ee431-228">This is your final configuration.</span></span>
  
![Azure 中具有 CLIENT1 虛擬機器的基底組態的階段 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="ee431-230">Azure 中的基底組態已準備好進行應用程式開發與測試，或建立其他測試環境。</span><span class="sxs-lookup"><span data-stu-id="ee431-230">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="ee431-231">按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="ee431-231">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
<span data-ttu-id="ee431-232"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="ee431-232"><a name="mincost"> </a></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="ee431-233">降低 Azure 中測試環境虛擬機器的成本</span><span class="sxs-lookup"><span data-stu-id="ee431-233">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="ee431-234">若要降低執行測試環境虛擬機器的成本，您可以執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="ee431-234">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="ee431-p122">建立測試環境並盡快執行所需測試和示範。完成後，刪除測試環境的資源群組。</span><span class="sxs-lookup"><span data-stu-id="ee431-p122">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="ee431-237">關閉測試環境的虛擬機器，進入解除配置的狀態。</span><span class="sxs-lookup"><span data-stu-id="ee431-237">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="ee431-238">若要使用 Azure PowerShell 關閉虛擬機器，請填寫資源群組名稱並執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-238">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="ee431-239">為了確保從已停止 (已解除配置) 的狀態啟動所有虛擬機器時，您的虛擬機器能正常運作，您應依照下列順序啟動：</span><span class="sxs-lookup"><span data-stu-id="ee431-239">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="ee431-240">DC1</span><span class="sxs-lookup"><span data-stu-id="ee431-240">DC1</span></span>
2. <span data-ttu-id="ee431-241">APP1</span><span class="sxs-lookup"><span data-stu-id="ee431-241">APP1</span></span>
3. <span data-ttu-id="ee431-242">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="ee431-242">CLIENT1</span></span>
    
<span data-ttu-id="ee431-243">若要使用 Azure PowerShell 依序啟動虛擬機器，請填寫資源群組名稱並執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="ee431-243">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="ee431-244">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee431-244">See Also</span></span>

- [<span data-ttu-id="ee431-245">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="ee431-245">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="ee431-246">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="ee431-246">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="ee431-247">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="ee431-247">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="ee431-248">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="ee431-248">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="ee431-249">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="ee431-249">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
