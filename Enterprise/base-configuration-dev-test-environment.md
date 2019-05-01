---
title: 基底組態開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
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
ms.openlocfilehash: 68edf0dea20674a7dadb4d1e50b8151a9ce13c7b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490518"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="e7463-103">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e7463-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="e7463-104">**摘要：** 在 Microsoft Azure 中建立簡化的內部網路作為開發/測試環境。</span><span class="sxs-lookup"><span data-stu-id="e7463-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="e7463-105">本文提供指示，以在 Azure 中建立下列基底組態開發/測試環境：</span><span class="sxs-lookup"><span data-stu-id="e7463-105">This article provides you with instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
![在 Azure 中建立基底組態](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="e7463-107">**圖 1：基底組態開發/測試環境**</span><span class="sxs-lookup"><span data-stu-id="e7463-107">**Figure 1: The Base Configuration dev/test environment**</span></span>

<span data-ttu-id="e7463-p101">圖 1 中的基底組態開發/測試環境包含名為 TestLab 的雲端專用 Azure 虛擬網路中的 Corpnet 子網路，其可模擬連線到網際網路的簡化私人內部網路。它具有執行 WIndows Server 2016 的三部 Azure 虛擬機器：</span><span class="sxs-lookup"><span data-stu-id="e7463-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It has three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="e7463-110">DC1 已設定為內部網路網域控制站和網域名稱系統 (DNS) 伺服器</span><span class="sxs-lookup"><span data-stu-id="e7463-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="e7463-111">APP1 已設定為一般應用程式和 Web 伺服器</span><span class="sxs-lookup"><span data-stu-id="e7463-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="e7463-112">CLIENT1 做為內部網路用戶端</span><span class="sxs-lookup"><span data-stu-id="e7463-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="e7463-113">此設定可讓 DC1、APP1、CLIENT1 及其他 Corpnet 子網路的電腦：</span><span class="sxs-lookup"><span data-stu-id="e7463-113">This configuration lets DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="e7463-114">連線到網際網路以安裝更新、即時存取網際網路資源，並加入公用雲端技術，例如 Microsoft Office 365 與其他 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="e7463-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="e7463-115">從已連線到網際網路或您組織網路的電腦使用遠端桌面連線進行遠端管理。</span><span class="sxs-lookup"><span data-stu-id="e7463-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="e7463-116">您可以將產生的測試環境：</span><span class="sxs-lookup"><span data-stu-id="e7463-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="e7463-117">用於應用程式開發與測試。</span><span class="sxs-lookup"><span data-stu-id="e7463-117">For application development and testing.</span></span>
    
- <span data-ttu-id="e7463-118">做為自己設計的延伸測試環境之初始設定，其中包含其他虛擬機器、Azure 服務或其他 Microsoft 雲端產品，如 Office 365 及 Enterprise Mobility + Security (EMS)。</span><span class="sxs-lookup"><span data-stu-id="e7463-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Mobility + Security (EMS).</span></span>
    
<span data-ttu-id="e7463-119">有兩種方法可以建立此環境：</span><span class="sxs-lookup"><span data-stu-id="e7463-119">There are two methods to creating this environment:</span></span>

1. <span data-ttu-id="e7463-120">Azure Resource Manager 範本</span><span class="sxs-lookup"><span data-stu-id="e7463-120">An Azure Resource Manager template</span></span>
2. <span data-ttu-id="e7463-121">Azure Powershell</span><span class="sxs-lookup"><span data-stu-id="e7463-121">Azure Powershell</span></span>

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a><span data-ttu-id="e7463-122">方法 1：使用 Azure Resource Manager 範本建立模擬內部網路</span><span class="sxs-lookup"><span data-stu-id="e7463-122">Method 1: Build your simulated intranet with an Azure Resource Manager template</span></span>

<span data-ttu-id="e7463-p102">在這個方法中，您可以使用 Azure Resource Manager (ARM) 範本來建立模擬內部網路。ARM 範本包含建立及設定 Azure 網路基礎結構和虛擬機器的所有指示。</span><span class="sxs-lookup"><span data-stu-id="e7463-p102">In this method, you use an Azure Resource Manager (ARM) template to build out the simulated intranet. ARM templates contain all of the instructions to create and configure the Azure networking infrastructure and the virtual machines.</span></span>

<span data-ttu-id="e7463-125">部署範本之前，請先閱讀[範本讀我檔案頁面](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)並準備好下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e7463-125">Prior to deploying the template, read through the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) and have the following information ready:</span></span>

- <span data-ttu-id="e7463-p103">Azure 訂用帳戶名稱。您必須在 [自訂部署]\*\*\*\* 頁面的 [訂用帳戶]\*\*\*\* 欄位中輸入此標籤。</span><span class="sxs-lookup"><span data-stu-id="e7463-p103">The Azure subscription name. You’ll need to enter this label in the **Subscription** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="e7463-p104">Azure 資源群組名稱。您必須在 [自訂部署]\*\*\*\* 頁面的 [資源群組]\*\*\*\* 欄位中輸入此標籤。</span><span class="sxs-lookup"><span data-stu-id="e7463-p104">The Azure resource group name. You’ll need to enter this label in the **Resource group** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="e7463-p105">虛擬機器公用 IP 位址 URL 上的 DNS 標籤前置詞。您必須在 [自訂部署]\*\*\*\* 頁面的 [DNS 標籤前置詞]\*\*\*\* 欄位中輸入此標籤。</span><span class="sxs-lookup"><span data-stu-id="e7463-p105">A DNS label prefix for the URLs of the public IP addresses of your virtual machines. You’ll need to enter this label in the **Dns Label Prefix** field of the **Custom deployment** page.</span></span>

<span data-ttu-id="e7463-132">閱讀指示之後，請在[範本讀我檔案頁面](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)上按一下 [部署至 Azure]\*\*\*\* 以開始使用。</span><span class="sxs-lookup"><span data-stu-id="e7463-132">After reading through the instructions, click **Deploy to Azure** on the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) to get started.</span></span>

>[!Note]
><span data-ttu-id="e7463-133">ARM 範本所建立的模擬內部網路需要 Azure 付費訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="e7463-133">The simulated intranet built by the ARM template requires a paid Azure subscription.</span></span>
>

<span data-ttu-id="e7463-134">範本完成後，您的組態如下。</span><span class="sxs-lookup"><span data-stu-id="e7463-134">Here is your configuration after the template is complete.</span></span>

![在 Azure 中建立基底組態](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a><span data-ttu-id="e7463-136">方法 2：使用 Azure PowerShell 建立模擬內部網路</span><span class="sxs-lookup"><span data-stu-id="e7463-136">Method 2: Build your simulated intranet with Azure PowerShell</span></span>

<span data-ttu-id="e7463-137">在這個方法中，您使用 Windows PowerShell 和 Azure PowerShell 模組建置網路基礎結構、虛擬機器及其設定。</span><span class="sxs-lookup"><span data-stu-id="e7463-137">In this method, you use Windows PowerShell and the Azure PowerShell module to build out the networking infrastructure, the virtual machines, and their configuration.</span></span>

<span data-ttu-id="e7463-p106">如果您想要使用 PowerShell 獲得一次建立一個 Azure 基礎結構命令區塊元素的體驗，則使用此方法。然後，您可以自行定義 PowerShell 命令區塊，以便在 Azure 中部署其他虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="e7463-p106">Use this method if you want to get experience creating elements of Azure infrastructure one command block at a time with PowerShell. You can then customize the PowerShell command blocks for your own deployment of other virtual machines in Azure.</span></span>

<span data-ttu-id="e7463-140">設定 Azure PowerShell 中的基底組態測試環境有四個步驟：</span><span class="sxs-lookup"><span data-stu-id="e7463-140">There are four steps to setting up the Base Configuration test environment using Azure PowerShell:</span></span>
  
1. <span data-ttu-id="e7463-141">建立虛擬網路。</span><span class="sxs-lookup"><span data-stu-id="e7463-141">Create the virtual network.</span></span>
    
2. <span data-ttu-id="e7463-142">設定 DC1。</span><span class="sxs-lookup"><span data-stu-id="e7463-142">Configure DC1.</span></span>
    
3. <span data-ttu-id="e7463-143">設定 APP1。</span><span class="sxs-lookup"><span data-stu-id="e7463-143">Configure APP1.</span></span>
    
4. <span data-ttu-id="e7463-144">設定 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="e7463-144">Configure CLIENT1.</span></span>
    
<span data-ttu-id="e7463-p107">如果您沒有 Azure 訂閱，可以在[試用 Azure](https://azure.microsoft.com/pricing/free-trial/) 中註冊免費試用版。如果您擁有 MSDN 或 Visual Studio 訂閱，請參閱 [Visual Studio 訂閱者每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。</span><span class="sxs-lookup"><span data-stu-id="e7463-p107">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e7463-p108">Azure 中的虛擬機器在執行時會持續產生成本。此成本是根據您的免費試用版、MSDN 訂閱或付費訂閱收費。如需執行 Azure 虛擬機器的成本相關資訊，請參閱[虛擬機器價格詳細資料](https://azure.microsoft.com/pricing/details/virtual-machines/)與 [Azure 價格計算機](https://azure.microsoft.com/pricing/calculator/)。若要降低成本，請參閱[降低 Azure 中測試環境虛擬機器的成本](base-configuration-dev-test-environment.md#mincost)。</span><span class="sxs-lookup"><span data-stu-id="e7463-p108">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="e7463-152">按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中文章的所有視覺對應。</span><span class="sxs-lookup"><span data-stu-id="e7463-152">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
### <a name="step-1-create-the-virtual-network"></a><span data-ttu-id="e7463-153">步驟 1：建立虛擬網路</span><span class="sxs-lookup"><span data-stu-id="e7463-153">Step 1: Create the virtual network</span></span>

<span data-ttu-id="e7463-154">在此步驟中，您會在 Azure 中對虛擬網路進行測試實驗。</span><span class="sxs-lookup"><span data-stu-id="e7463-154">In this step, you the TestLab virtual network in Azure.</span></span>

<span data-ttu-id="e7463-155">首先，啟動 Azure PowerShell 提示。</span><span class="sxs-lookup"><span data-stu-id="e7463-155">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e7463-p109">下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/)。</span><span class="sxs-lookup"><span data-stu-id="e7463-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="e7463-158">使用下列命令登入您的 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e7463-158">Sign in to your Azure account with the following command.</span></span>
  
```
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="e7463-159">按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)以取得包含本文中所有 PowerShell 命令的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="e7463-159">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that has all the PowerShell commands in this article.</span></span>

<span data-ttu-id="e7463-160">使用下列命令取得訂用帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="e7463-160">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="e7463-p110">設定 Azure 訂用帳戶。以正確的名稱取代括號中的所有項目 (包括 < 和 > 字元)。</span><span class="sxs-lookup"><span data-stu-id="e7463-p110">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="e7463-p111">接著，為您的基底組態測試實驗室建立新的資源群組。若要判斷資源群組名稱是否是唯一的，可使用此命令來列出現有的資源群組。</span><span class="sxs-lookup"><span data-stu-id="e7463-p111">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="e7463-p112">使用這些命令建立新的資源群組。以正確的名稱取代引號內的所有項目 (包括 < 和 > 字元)。</span><span class="sxs-lookup"><span data-stu-id="e7463-p112">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="e7463-167">接著，您會建立將裝載基底組態 Corpnet 子網路的 TestLab 虛擬網路，並以網路安全性群組來保護它。</span><span class="sxs-lookup"><span data-stu-id="e7463-167">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="e7463-168">這是您目前的組態。</span><span class="sxs-lookup"><span data-stu-id="e7463-168">This is your current configuration.</span></span>
  
![Azure 中具有虛擬網路與子網路的基底組態的步驟 1](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a><span data-ttu-id="e7463-170">步驟 2：設定 DC1</span><span class="sxs-lookup"><span data-stu-id="e7463-170">Step 2: Configure DC1</span></span>

<span data-ttu-id="e7463-171">在此步驟中，我們會建立 DC1 虛擬機器，並將其設定為 corp.contoso.com Active Directory Domain Services (AD DS) 網域的網域控制站以及 TestLab 虛擬網路之虛擬機器的 DNS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e7463-171">In this step, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Active Directory Domain Services (AD DS) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>

> [!NOTE]
> <span data-ttu-id="e7463-p113">在執行下列命令區塊之前，請確定您所選擇的 Azure 區域 (位置) 支援 Azure 虛擬機器大小，預設設為 Standard_A1。按一下[這裡](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)以查看 Azure 虛擬機器大小和位置的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="e7463-p113">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="e7463-174">若要建立 DC1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-174">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="e7463-p114">系統會提示您輸入 DC1 上本機系統管理員帳戶的使用者名稱和密碼。使用強式密碼，並將名稱和密碼記錄於安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e7463-p114">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="e7463-177">接下來，連線到 DC1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="e7463-177">Next, connect to the DC1 virtual machine.</span></span>
  
1. <span data-ttu-id="e7463-178">在 [Azure 入口網站](https://portal.azure.com)中，按一下 **[資源群組] >** [新的資源群組名稱] **> [DC1] > [連線]**。</span><span class="sxs-lookup"><span data-stu-id="e7463-178">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="e7463-p115">在開啟的窗格中，按一下 [下載 RDP 檔案]\*\*\*\*。開啟所下載的 DC1.rdp 檔案，然後按一下 [連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-p115">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="e7463-181">指定 DC1 本機系統管理員帳戶名稱：</span><span class="sxs-lookup"><span data-stu-id="e7463-181">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="e7463-182">對於 Windows 7：</span><span class="sxs-lookup"><span data-stu-id="e7463-182">For Windows 7:</span></span>
    
    <span data-ttu-id="e7463-p116">在 [Windows 安全性]\*\*\*\* 對話方塊中，按一下 [使用其他帳戶]\*\*\*\*。在 [使用者名稱]\*\*\*\* 中，輸入 **DC1\\**[本機系統管理員帳戶名稱]。</span><span class="sxs-lookup"><span data-stu-id="e7463-p116">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="e7463-185">對於 Windows 8 或 Windows 10：</span><span class="sxs-lookup"><span data-stu-id="e7463-185">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="e7463-p117">在 [Windows 安全性]\*\*\*\* 對話方塊中，按一下 [更多選項]\*\*\*\*，然後按 [使用不同帳戶]\*\*\*\*。在 [使用者名稱]\*\*\*\* 中，輸入 **DC1\\**[本機系統管理員帳戶名稱]。</span><span class="sxs-lookup"><span data-stu-id="e7463-p117">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="e7463-188">在 [密碼]\*\*\*\* 中，輸入本機系統管理員帳戶的密碼，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-188">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e7463-189">出現提示時，按一下 [是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-189">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="e7463-190">接著，使用此命令在 DC1 上系統管理員層級 Windows PowerShell 命令提示字元將額外的資料磁碟新增為新的磁碟區 (磁碟機代號 F:)。</span><span class="sxs-lookup"><span data-stu-id="e7463-190">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="e7463-p118">接著，將 DC1 設定為網域控制站和 corp.contoso.com 網域的 DNS 伺服器。在系統管理員層級 Windows PowerShell 命令提示字元執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-p118">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="e7463-p119">您必須指定安全模式的系統管理員密碼。將此密碼儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e7463-p119">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="e7463-195">請注意，這些命令可能需要數分鐘才能完成。</span><span class="sxs-lookup"><span data-stu-id="e7463-195">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="e7463-196">DC1 重新啟動後，使用網域認證以重新連線到 DC1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="e7463-196">After DC1 restarts, reconnect to the DC1 virtual machine using domain credentials.</span></span>
  
1. <span data-ttu-id="e7463-197">在 [Azure 入口網站](https://portal.azure.com)中，按一下 **[資源群組] >** [您的資源群組名稱] **> [DC1] > [連線]**。</span><span class="sxs-lookup"><span data-stu-id="e7463-197">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="e7463-198">執行所下載的 DC1.rdp 檔案，然後按一下 [連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-198">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="e7463-p120">在 [Windows 安全性]\*\*\*\* 中，按一下 [使用其他帳戶]\*\*\*\*。在 [使用者名稱]\*\*\*\* 中，輸入 **CORP\\**[本機系統管理員帳戶名稱]。</span><span class="sxs-lookup"><span data-stu-id="e7463-p120">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="e7463-201">在 [密碼]\*\*\*\* 中，輸入本機系統管理員帳戶的密碼，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-201">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e7463-202">出現提示時，按一下 [是]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-202">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="e7463-p121">接下來，建立 Active Directory 中的使用者帳戶，可在登入 CORP 網域成員電腦時使用。在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-p121">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="e7463-p122">請注意，此命令會提示您提供 User1 帳戶密碼。由於這個帳戶將會用於所有 CORP 網域成員電腦的遠端桌面連線，請選擇強式密碼。記錄 User1 帳戶密碼，並將它儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="e7463-p122">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="e7463-p123">接下來，將新的 User1 帳戶設定為企業系統管理員。在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-p123">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="e7463-210">關閉 DC1 的遠端桌面工作階段，然後使用 CORP\\User1 帳戶重新連線。</span><span class="sxs-lookup"><span data-stu-id="e7463-210">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="e7463-211">接下來，若要允許 Ping 工具的流量，請在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-211">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="e7463-212">這是您目前的組態。</span><span class="sxs-lookup"><span data-stu-id="e7463-212">This is your current configuration.</span></span>
  
![Azure 中具有 DC1 虛擬機器的基底組態的步驟 2](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a><span data-ttu-id="e7463-214">步驟 3：設定 APP1</span><span class="sxs-lookup"><span data-stu-id="e7463-214">Step 3: Configure APP1</span></span>

<span data-ttu-id="e7463-215">在這個步驟，您會建立及設定 APP1，它會提供 Web 和檔案共用服務。</span><span class="sxs-lookup"><span data-stu-id="e7463-215">In this step, you create and configure APP1, which provides web and file sharing services.</span></span>

> [!NOTE]
> <span data-ttu-id="e7463-p124">在執行下列命令區塊之前，請確定您所選擇的 Azure 區域 (位置) 支援 Azure 虛擬機器大小，預設設為 Standard_A1。按一下[這裡](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)以查看 Azure 虛擬機器大小和位置的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="e7463-p124">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="e7463-218">若要建立 APP1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-218">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="e7463-219">接下來，使用 APP1 本機系統管理員帳戶名稱和密碼連線到 APP1 虛擬機器，然後開啟 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e7463-219">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e7463-220">若要檢查 APP1 和 DC1 之間的名稱解析和網路通訊，請執行 **ping dc1.corp.contoso.com** 命令，並檢查有四個回覆。</span><span class="sxs-lookup"><span data-stu-id="e7463-220">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="e7463-221">接下來在 Windows PowerShell 命令提示字元使用以下命令將 APP1 虛擬機器加入 CORP 網域。</span><span class="sxs-lookup"><span data-stu-id="e7463-221">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="e7463-222">請注意，您必須在執行 **Add-Computer** 命令之後，提供 CORP\\User1 網域帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="e7463-222">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="e7463-223">APP1 重新啟動之後，使用 CORP\\User1 帳戶連線至 APP1，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e7463-223">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e7463-224">接下來，在 APP1 上的 Windows PowerShell 命令提示字元中使用此命令讓 APP1 成為 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e7463-224">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="e7463-225">接下來，使用這些 PowerShell 命令在 APP1 上的資料夾內建立共用資料夾及文字檔。</span><span class="sxs-lookup"><span data-stu-id="e7463-225">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="e7463-226">這是您目前的組態。</span><span class="sxs-lookup"><span data-stu-id="e7463-226">This is your current configuration.</span></span>
  
![Azure 中具有 APP1 虛擬機器的基底組態的步驟 3](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a><span data-ttu-id="e7463-228">步驟 4：設定 CLIENT1</span><span class="sxs-lookup"><span data-stu-id="e7463-228">Step 4: Configure CLIENT1</span></span>

<span data-ttu-id="e7463-229">在這個步驟中，建立及設定 CLIENT1，其可在 Contoso 內部網路上作為一般的膝上型電腦、平板電腦或桌上型電腦。</span><span class="sxs-lookup"><span data-stu-id="e7463-229">In this step, you create and configure CLIENT1, which acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>

> [!NOTE]  
> <span data-ttu-id="e7463-p125">下列命令集可建立執行 Windows Server 2016 資料中心的 CLIENT1，其適用於所有類型的 Azure 訂閱。如果您有以 Visual Studio 為基礎的 Azure 訂閱，則可以使用 [Azure 入口網站](https://portal.azure.com)建立執行 Windows 10 的 CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="e7463-p125">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 
  

> [!NOTE]
> <span data-ttu-id="e7463-p126">在執行下列命令區塊之前，請確定您所選擇的 Azure 區域 (位置) 支援 Azure 虛擬機器大小，預設設為 Standard_A1。按一下[這裡](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)以查看 Azure 虛擬機器大小和位置的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="e7463-p126">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="e7463-234">若要建立 CLIENT1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-234">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="e7463-235">接下來，使用 CLIENT1 本機系統管理員帳戶名稱和密碼連線到 CLIENT1 虛擬機器，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e7463-235">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e7463-236">若要檢查 CLIENT1 和 DC1 之間的名稱解析和網路通訊，請在 Windows PowerShell 命令提示字元執行 **ping dc1.corp.contoso.com** 命令，並檢查有四個回覆。</span><span class="sxs-lookup"><span data-stu-id="e7463-236">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and check that there are four replies.</span></span>
  
<span data-ttu-id="e7463-237">接下來在 Windows PowerShell 命令提示字元使用以下命令將 CLIENT1 虛擬機器加入 CORP 網域。</span><span class="sxs-lookup"><span data-stu-id="e7463-237">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="e7463-238">請注意，您必須在執行 **Add-Computer** 命令之後，提供 CORP\\User1 網域帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="e7463-238">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="e7463-239">CLIENT1 重新啟動之後，使用 CORP\\User1 帳戶名稱和密碼連線至 CLIENT1，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e7463-239">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e7463-240">接下來，檢查您可以從 CLIENT1 存取 APP1 上的 Web 及檔案共用資源。</span><span class="sxs-lookup"><span data-stu-id="e7463-240">Next, check that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
1. <span data-ttu-id="e7463-241">在 [伺服器管理員] 的樹狀窗格中，按一下 [本機伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-241">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="e7463-242">在 [CLIENT1 的屬性]\*\*\*\* 中，按一下 [IE 增強式安全性設定]\*\*\*\* 旁邊的 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-242">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="e7463-243">在 [Internet Explorer 增強式安全性設定]\*\*\*\* 中，為 [管理員]\*\*\*\* 和 [使用者]\*\*\*\* 按一下 [關閉]\*\*\*\*，然後按 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-243">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="e7463-244">從 [開始] 畫面，按一下 [Internet Explorer]\*\*\*\*，然後按 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7463-244">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e7463-p127">在網址列中，輸入 **http:\//app1.corp.contoso.com/**，然後按 ENTER 鍵。您應該會看到 APP1 的預設網際網路資訊服務網頁。</span><span class="sxs-lookup"><span data-stu-id="e7463-p127">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="e7463-247">在桌面工作列中，按一下 [檔案總管] 圖示。</span><span class="sxs-lookup"><span data-stu-id="e7463-247">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="e7463-p128">在網址列中，輸入 **\\\\app1\\檔案**，然後按 ENTER 鍵。您應該會看到資料夾視窗中的檔案共用資料夾內容。</span><span class="sxs-lookup"><span data-stu-id="e7463-p128">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="e7463-p129">在 [檔案]\*\*\*\* 共用資料夾視窗中，按兩下 **Example.txt** 檔案。您應該會看到 Example.txt 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="e7463-p129">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="e7463-252">關閉 **example.txt - 記事本**以及 [檔案]\*\*\*\* 共用資料夾視窗。</span><span class="sxs-lookup"><span data-stu-id="e7463-252">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="e7463-253">這是您的最終組態。</span><span class="sxs-lookup"><span data-stu-id="e7463-253">This is your final configuration.</span></span>
  
![Azure 中具有 CLIENT1 虛擬機器的基底組態的步驟 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="e7463-255">Azure 中的基底組態已準備好進行應用程式開發與測試，或建立其他測試環境。</span><span class="sxs-lookup"><span data-stu-id="e7463-255">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="e7463-256">按一下[這裡](http://aka.ms/catlgstack)，可查看 Office 365 測試實驗室指南堆疊中所有文章的視覺對應。</span><span class="sxs-lookup"><span data-stu-id="e7463-256">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the Office 365 Test Lab Guide stack.</span></span>
  
<span data-ttu-id="e7463-257"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="e7463-257"></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="e7463-258">降低 Azure 中測試環境虛擬機器的成本</span><span class="sxs-lookup"><span data-stu-id="e7463-258">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="e7463-259">若要降低執行測試環境虛擬機器的成本，您可以執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="e7463-259">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="e7463-p130">建立測試環境並盡快執行所需測試和示範。完成後，刪除測試環境的資源群組。</span><span class="sxs-lookup"><span data-stu-id="e7463-p130">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="e7463-262">關閉測試環境的虛擬機器，進入解除配置的狀態。</span><span class="sxs-lookup"><span data-stu-id="e7463-262">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="e7463-263">若要使用 Azure PowerShell 關閉虛擬機器，請填寫資源群組名稱並執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-263">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="e7463-264">為了確保從已停止 (已解除配置) 的狀態啟動所有虛擬機器時，您的虛擬機器能正常運作，您應依照下列順序啟動：</span><span class="sxs-lookup"><span data-stu-id="e7463-264">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="e7463-265">DC1</span><span class="sxs-lookup"><span data-stu-id="e7463-265">DC1</span></span>
2. <span data-ttu-id="e7463-266">APP1</span><span class="sxs-lookup"><span data-stu-id="e7463-266">APP1</span></span>
3. <span data-ttu-id="e7463-267">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="e7463-267">CLIENT1</span></span>
    
<span data-ttu-id="e7463-268">若要使用 Azure PowerShell 依序啟動虛擬機器，請填寫資源群組名稱並執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="e7463-268">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzVM -ResourceGroupName $rgName -Name "DC1"
Start-AzVM -ResourceGroupName $rgName -Name "APP1"
Start-AzVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="e7463-269">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7463-269">See Also</span></span>

- [<span data-ttu-id="e7463-270">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="e7463-270">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="e7463-271">Office 365 開發/測試環境的 DirSync</span><span class="sxs-lookup"><span data-stu-id="e7463-271">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="e7463-272">Office 365 開發人員/測試環境的雲端 App 安全性</span><span class="sxs-lookup"><span data-stu-id="e7463-272">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="e7463-273">適用於 Office 365 開發/測試環境的進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="e7463-273">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="e7463-274">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="e7463-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
