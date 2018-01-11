---
title: "Microsoft 365 Enterprise 開發人員/測試環境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_TLGs
- Strat_O365_Enterprise
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: "摘要： 使用此測試實驗室指南建立開發/測試環境包含 Office 365 E5、 企業行動性 + 安全性 （EMS） E5 及執行 Windows 10 企業的電腦。"
ms.openlocfilehash: f6baabaee10c25243690918aa6c9b2c68ff3758b
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="07c0c-103">Microsoft 365 Enterprise 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="07c0c-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="07c0c-104">**摘要：**若要建立包含 Office 365 E5、 企業行動性 + 安全性 （EMS） E5 和執行 Windows 10 企業之電腦的開發人員/測試環境中使用此測試實驗室指南。</span><span class="sxs-lookup"><span data-stu-id="07c0c-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="07c0c-105">本文提供逐步指示以建立要測試的功能和[Microsoft 365 企業版](https://www.microsoft.com/microsoft-365/enterprise)功能簡化的環境。</span><span class="sxs-lookup"><span data-stu-id="07c0c-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="07c0c-106">階段 1： 建立您的 Office 365 E5 訂閱</span><span class="sxs-lookup"><span data-stu-id="07c0c-106">Phase 1: Create your Office 365 E5 subscription</span></span>

<span data-ttu-id="07c0c-107">請依照下列階段 2 和[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)的階段 3： 建立輕量型 Office 365 開發人員/測試環境中，如圖 1 所示的步驟。</span><span class="sxs-lookup"><span data-stu-id="07c0c-107">Follow the steps in Phase 2 and Phase 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="07c0c-108">**圖 1： Office 365 E5 訂閱具有其 Azure Active Directory (AD) 租用戶和使用者帳戶**</span><span class="sxs-lookup"><span data-stu-id="07c0c-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Microsoft 365 企業版 開發/測試環境的階段 1](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="07c0c-110">階段 2： 新增 EMS</span><span class="sxs-lookup"><span data-stu-id="07c0c-110">Phase 2: Add EMS</span></span>

<span data-ttu-id="07c0c-111">在此階段中，您註冊 EMS E5 試用版訂閱並將其新增至您的 Office 365 E5 試用版訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="07c0c-111">In this phase, you sign up for the EMS E5 trial subscription and add it to the same organization as your Office 365 E5 trial subscription.</span></span>
  
<span data-ttu-id="07c0c-112">首先，新增 EMS E5 試用訂閱及 EMS 授權指派給全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="07c0c-112">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="07c0c-p101">網際網路瀏覽器的私人執行個體，登入 Office 365 入口網站與您的全域管理員帳戶認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p101">With a private instance of an Internet browser, sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="07c0c-115">按一下 [**系統**] 磚。</span><span class="sxs-lookup"><span data-stu-id="07c0c-115">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="07c0c-116">在**Office 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**帳務 > 購買服務**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-116">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="07c0c-p102">在 [**購買服務**] 頁面上尋找**企業行動性 + 安全性 E5**項目。滑鼠指標停留並按一下 [**開始免費試用版**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="07c0c-119">在 [**確認您的訂單**] 頁面上按一下 [**立即試用**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-119">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="07c0c-120">在 [**順序回條**] 頁面上按一下 [**繼續**]。</span><span class="sxs-lookup"><span data-stu-id="07c0c-120">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="07c0c-121">在**Office 365 系統管理中心**] 索引標籤中瀏覽器中，在左導覽列中，按一下 [**使用者 > 作用中使用者**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="07c0c-122">按一下 [您的全域管理員帳戶] 和 [**編輯****產品**授權。</span><span class="sxs-lookup"><span data-stu-id="07c0c-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="07c0c-123">在**產品授權**] 窗格中，開啟**企業行動性 + 安全性 E5** **上**至產品授權、 按一下 [**儲存]**及 [**關閉**兩次。</span><span class="sxs-lookup"><span data-stu-id="07c0c-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="07c0c-p103">Enterprise Mobility + Security E5 試用訂閱為 90 天。針對永久開發/測試環境，建立具有少數授權的新付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p103">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="07c0c-126">***如果您已完成的階段 3***[Office 365 開發人員/測試環境](office-365-dev-test-environment.md)的所有其他帳戶 （使用者 2、 3 使用者、 使用者 4 和使用者 5） 的重複步驟 8 和 9 的前一程序。</span><span class="sxs-lookup"><span data-stu-id="07c0c-126">***If you completed Phase 3 of*** [Office 365 dev/test environment](office-365-dev-test-environment.md) , repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="07c0c-127">開發/測試環境現在有：</span><span class="sxs-lookup"><span data-stu-id="07c0c-127">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="07c0c-128">Office 365 E5 Enterprise 和 EMS 試用訂閱會與您的使用者帳戶清單共用相同的組織和相同的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="07c0c-128">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="07c0c-129">使用 Office 365 E5 和 EMS E5 啟用所有適當的使用者帳戶 （只是將全域管理員或所有五個使用者帳戶）。</span><span class="sxs-lookup"><span data-stu-id="07c0c-129">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="07c0c-130">圖 2 顯示您所產生的設定，會新增 EMS。</span><span class="sxs-lookup"><span data-stu-id="07c0c-130">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="07c0c-131">**圖 2： 新增 EMS 試用訂閱**</span><span class="sxs-lookup"><span data-stu-id="07c0c-131">**Figure 2: Adding the EMS trial subscription**</span></span>

![Microsoft 365 企業版 開發/測試環境的階段 2](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="07c0c-133">階段 3： 建立 Windows 10 企業電腦</span><span class="sxs-lookup"><span data-stu-id="07c0c-133">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="07c0c-134">在此階段中，您可以建立獨立的電腦執行 Windows 10 Enterprise。</span><span class="sxs-lookup"><span data-stu-id="07c0c-134">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="07c0c-135">實體電腦</span><span class="sxs-lookup"><span data-stu-id="07c0c-135">Physical computer</span></span>

<span data-ttu-id="07c0c-p104">取得個人電腦並在其上安裝 Windows 10 Enterprise。您可以下載 Windows 10 Enterprise 試用版[此處](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p104">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="07c0c-138">虛擬機器</span><span class="sxs-lookup"><span data-stu-id="07c0c-138">Virtual machine</span></span>

<span data-ttu-id="07c0c-p105">建立使用您選擇 hypervisor 虛擬機器，並在其上安裝 Windows 10 Enterprise。您可以下載 Windows 10 Enterprise 試用版[此處](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p105">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="07c0c-141">在 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="07c0c-141">Virtual machine in Azure</span></span>

<span data-ttu-id="07c0c-p106">若要建立 Windows 10 虛擬機器 in Microsoft Azure，***您必須具備的 Visual Studio 為基礎的訂閱***，以存取 Windows 10 enterprise 映像。其他類型的 Azure 訂閱、 試驗和付費訂閱，例如不需要存取此影像。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p106">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="07c0c-p107">下列的命令會使用 Azure PowerShell 尋找最新版本。請參閱[開始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)。這些命令會建立 Windows 10 Enterprise 虛擬機器名為 WIN10 和所有其所需的基礎結構，包括資源群組、 儲存帳戶及虛擬網路。如果您已熟悉 Azure 基礎結構服務，請能否這些指示以符合您目前已部署的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p107">The following command sets use te latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="07c0c-148">首先，啟動 Microsoft PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="07c0c-148">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="07c0c-149">下列命令以 Azure 帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="07c0c-149">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="07c0c-150">使用下列命令取得訂用帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="07c0c-150">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="07c0c-p108">設定您的 Azure 訂閱。括住，包括所有內容取代為\<和 > 具有正確的名稱的字元。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p108">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="07c0c-p109">接著，建立新的資源群組。若要判斷資源群組名稱是否是唯一的，可使用此命令來列出現有的資源群組。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p109">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="07c0c-p110">使用這些命令建立新的資源群組。括住，包括所有內容取代為\<和 > 字元，以正確的名稱。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p110">Create your new resource group with these commands. Replace everything within the quotes, including the \< and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="07c0c-p111">資源管理員為基礎的虛擬機器時需要的資源管理員為基礎的存放區的帳戶。您必須選擇您儲存帳戶會*包含只有小寫字母和數字*的全域唯一名稱。您可以使用此命令以列出現有存放區的帳戶。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p111">Resource Manager-based virtual machines require a Resource Manager-based storage account. You must pick a globally unique name for your storage account  *that contains only lowercase letters and numbers*  . You can use this command to list the existing storage accounts.</span></span>
  
```
Get-AzureRMStorageAccount | Sort StorageAccountName | Select StorageAccountName
```

<span data-ttu-id="07c0c-160">使用此命令來測試建議的儲存體帳戶名稱是否是唯一的。</span><span class="sxs-lookup"><span data-stu-id="07c0c-160">Use this command to test whether a proposed storage account name is unique.</span></span>
  
```
Get-AzureRmStorageAccountNameAvailability "<proposed name>"
```

<span data-ttu-id="07c0c-161">使用這些命令，為新的測試環境建立新的儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="07c0c-161">Create a new storage account for your new test environment with these commands.</span></span>
  
```
$rgName="<your new resource group name>"
$saName="<storage account name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
New-AzureRMStorageAccount -Name $saName -ResourceGroupName $rgName -Type Standard_LRS -Location $locName
```

<span data-ttu-id="07c0c-p112">接下來，您可以使用這些命令建立新的虛擬網路和 WIN10 虛擬機器。出現提示時，WIN10 提供的名稱和本機管理員帳戶的密碼並儲存這些安全的位置。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$storageAcc=Get-AzureRMStorageAccount -ResourceGroupName $rgName -Name $saName
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftVisualStudio -Offer Windows -Skus Windows-10-N-x64 -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$osDiskUri=$storageAcc.PrimaryEndpoints.Blob.ToString() + "vhds/WIN10-TestLab-OSDisk.vhd"
$vm=Set-AzureRMVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -VhdUri $osDiskUri -CreateOption fromImage
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="07c0c-164">階段 4： 將 Windows 10 電腦加入 Azure AD</span><span class="sxs-lookup"><span data-stu-id="07c0c-164">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="07c0c-165">實體或虛擬機器建立、 設定與 Windows 10 Enterprise，並執行之後，使用本機系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="07c0c-165">After the physical or virtual machine is created, configured with Windows 10 Enterprise, and is running, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="07c0c-p113">針對在 Azure 虛擬機器，連線至其使用[這些指示](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)。使用本機系統管理員帳戶的認證登入。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="07c0c-168">接下來，WIN10 電腦加入 Azure AD 租用的 Office 365 和 EMS 訂閱。</span><span class="sxs-lookup"><span data-stu-id="07c0c-168">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="07c0c-169">在 WIN10 電腦桌面上按一下**啟動 > 設定 > 帳戶 > 存取工作或學校 > Connect**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-169">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="07c0c-170">在 [**工作] 或 [學校帳戶設定**] 對話方塊中，按一下 [**加入至 Azure Active Directory 此裝置**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-170">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="07c0c-171">在**工作或學校帳戶**、 輸入您的 Office 365 訂閱的全域管理員帳戶名稱] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-171">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="07c0c-172">在**輸入密碼**，輸入您的全域管理員帳戶的密碼，然後按一下 [**登入**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-172">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="07c0c-173">出現提示時若要確保這是您的組織，按一下 [**加入**，和 [**完成**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-173">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="07c0c-174">關閉 [設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="07c0c-174">Close the settings window.</span></span>
    
<span data-ttu-id="07c0c-175">接下來，WIN10 電腦上安裝 Office 2016</span><span class="sxs-lookup"><span data-stu-id="07c0c-175">Next, install Office 2016 on the WIN10 computer</span></span>
  
1. <span data-ttu-id="07c0c-p114">開啟 [Microsoft Edge 瀏覽器並登入 Office 365 入口網站與您的全域管理員帳戶認證。為了協助，請參閱 ＜[登入 Office 365 的位置](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p114">Open the Microsoft Edge browser and sign in to the Office 365 portal with your global administrator account credentials. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="07c0c-178">在 [ **Microsoft Office Home** ] 索引標籤上按一下 [**安裝 Office 2016**。</span><span class="sxs-lookup"><span data-stu-id="07c0c-178">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="07c0c-179">出現提示時與該怎麼辦，按一下 [**執行**] 和 [**是****使用者帳戶**控制。</span><span class="sxs-lookup"><span data-stu-id="07c0c-179">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="07c0c-p115">等待以完成其安裝 Office。當您看到**你全都設 ！**，按一下 [**關閉**] 兩次。</span><span class="sxs-lookup"><span data-stu-id="07c0c-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="07c0c-182">圖 3 是您所產生的環境，包括已加入 Azure AD 租用的 Office 365 和 EMS 訂閱 WIN10 電腦。</span><span class="sxs-lookup"><span data-stu-id="07c0c-182">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="07c0c-183">**圖 3： 將 WIN10 電腦帳戶新增至 Azure AD 租用戶**</span><span class="sxs-lookup"><span data-stu-id="07c0c-183">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Microsoft 365 企業版 開發/測試環境的階段 4](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="07c0c-185">您現在可以開始實驗[Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise)企業版的其他功能。</span><span class="sxs-lookup"><span data-stu-id="07c0c-185">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="07c0c-186">後續步驟</span><span class="sxs-lookup"><span data-stu-id="07c0c-186">Next steps</span></span>

<span data-ttu-id="07c0c-187">使用這些額外的文章來了解 Microsoft 365 企業版功能：</span><span class="sxs-lookup"><span data-stu-id="07c0c-187">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="07c0c-188">新增行動應用程式管理 (MAM) 原則</span><span class="sxs-lookup"><span data-stu-id="07c0c-188">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="07c0c-189">註冊 iOS 及 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="07c0c-189">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="07c0c-190">設定和測試進階安全性管理</span><span class="sxs-lookup"><span data-stu-id="07c0c-190">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="07c0c-191">設定和測試進階威脅保護</span><span class="sxs-lookup"><span data-stu-id="07c0c-191">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="07c0c-192">請參閱</span><span class="sxs-lookup"><span data-stu-id="07c0c-192">See Also</span></span>

[<span data-ttu-id="07c0c-193">一個 Microsoft Cloud 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="07c0c-193">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)

[<span data-ttu-id="07c0c-194">Microsoft 365 企業版文件</span><span class="sxs-lookup"><span data-stu-id="07c0c-194">Microsoft 365 Enterprise documentation</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)




