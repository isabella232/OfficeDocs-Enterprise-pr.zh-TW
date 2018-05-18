---
title: Microsoft 365 企業版開發/測試環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 摘要：使用此測試實驗室指南來建立開發/測試環境，其中包含 Office 365 E5、Enterprise Mobility + Security (EMS) E5 與執行 Windows 10 企業版的電腦。
ms.openlocfilehash: 5a4c23b3bde309a75a61e574e91823ecdd4629fe
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="79706-103">Microsoft 365 企業版開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="79706-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="79706-104">**摘要：** 使用此測試實驗室指南來建立開發/測試環境，其中包含 Office 365 E5、Enterprise Mobility + Security (EMS) E5 與執行 Windows 10 企業版的電腦。</span><span class="sxs-lookup"><span data-stu-id="79706-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="79706-105">本文提供逐步指示來建立簡化的環境，用以測試 [Microsoft 365 企業版](https://www.microsoft.com/microsoft-365/enterprise)的功能與特性。</span><span class="sxs-lookup"><span data-stu-id="79706-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="79706-106">階段 1：建立您的 Office 365 E5 訂閱</span><span class="sxs-lookup"><span data-stu-id="79706-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="79706-107">請依照 [Office 365 開發/測試環境](office-365-dev-test-environment.md)中階段 2 和階段 3 的步驟，建立簡易的 Office 365 開發/測試環境，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="79706-107">Follow the steps in Phase 2 and Phase 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="79706-108">**圖 1：Office 365 E5 訂閱及其 Azure Active Directory (AD) 租用戶和使用者帳戶**</span><span class="sxs-lookup"><span data-stu-id="79706-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Microsoft 365 企業版 開發/測試環境的階段 1](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="79706-p101">Office 365 E5 試用訂閱為 30 天，也可以輕鬆擴充到 60 天。如需永久開發/測試環境，請建立具有一些授權的新付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="79706-p101">The Office 365 E5 trial subscription is 30 days, which can be easily extended to 60 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="79706-112">階段 2：新增 EMS</span><span class="sxs-lookup"><span data-stu-id="79706-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="79706-113">在這個階段中，您可以註冊 EMS E5 試用訂閱，並將它新增至與 Office 365 E5 試用訂閱相同的組織。</span><span class="sxs-lookup"><span data-stu-id="79706-113">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="79706-114">首先，請新增 EMS E5 試用訂閱，並指派 EMS 授權給您的全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="79706-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="79706-p102">請使用網際網路瀏覽器的私用執行個體，並使用全域管理員帳戶認證登入 Office 365 入口網站。如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="79706-p102">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="79706-117">按一下 [管理]**** 磚。</span><span class="sxs-lookup"><span data-stu-id="79706-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="79706-118">在瀏覽器的 [Office 系統管理中心]**** 索引標籤上，按一下左導覽中的 [計費] > [購買服務]****。</span><span class="sxs-lookup"><span data-stu-id="79706-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="79706-p103">在 [購買服務]**** 頁面上，尋找 [Enterprise Mobility + Security E5] **** 項目。將滑鼠指標停留在上面，並且按一下 [開始免費試用]****。</span><span class="sxs-lookup"><span data-stu-id="79706-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="79706-121">在 [確認訂單]**** 頁面上，按一下 [立即試用]****。</span><span class="sxs-lookup"><span data-stu-id="79706-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="79706-122">在 [訂單收據]**** 頁面上，按一下 [繼續]****。</span><span class="sxs-lookup"><span data-stu-id="79706-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="79706-123">在瀏覽器的 [Office 365 系統管理中心]**** 索引標籤上，按一下左導覽中的 [使用者] > [作用中使用者]****。</span><span class="sxs-lookup"><span data-stu-id="79706-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="79706-124">按一下您的全域系統管理員帳戶，然後按一下 [產品授權]**** 的 [編輯]****。</span><span class="sxs-lookup"><span data-stu-id="79706-124">Click your global administrator  account, and then click **Edit** for **Product licenses**.</span></span>
    
9. <span data-ttu-id="79706-125">在 [產品授權]**** 窗格中，將 [**Enterprise Mobility + Security E5**] 的產品授權設為 [開啟]**，按一下 [儲存]，然後按兩次 [關閉]。</span><span class="sxs-lookup"><span data-stu-id="79706-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="79706-p104">Enterprise Mobility + Security E5 試用訂閱為 90 天。針對永久開發/測試環境，建立具有少數授權的新付費訂閱。</span><span class="sxs-lookup"><span data-stu-id="79706-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="79706-128">***如果您已完成 [Office 365 開發/測試環境](office-365-dev-test-environment.md)的階段 3***，請為所有其他帳戶 (使用者 2、使用者 3、使用者 4 和使用者 5) 重複先前程序的步驟 8 和 9。</span><span class="sxs-lookup"><span data-stu-id="79706-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="79706-129">開發/測試環境現在擁有：</span><span class="sxs-lookup"><span data-stu-id="79706-129">Your Office 365 and EMS dev/test environment now has:</span></span>
  
- <span data-ttu-id="79706-130">Office 365 E5 Enterprise 和 EMS E5 試用訂閱會與您的使用者帳戶清單共用相同的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="79706-130">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="79706-131">已啟用所有適用的使用者帳戶 (僅全域管理員或全部五個使用者帳戶) 以使用 Office 365 E5 和 EMS E5。</span><span class="sxs-lookup"><span data-stu-id="79706-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="79706-132">圖 2 顯示產生的組態，其中會新增 EMS。</span><span class="sxs-lookup"><span data-stu-id="79706-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="79706-133">**圖 2：新增 EMS 試用訂閱**</span><span class="sxs-lookup"><span data-stu-id="79706-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Microsoft 365 企業版 開發/測試環境的階段 2](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="79706-135">階段 3：建立 Windows 10 企業版的電腦</span><span class="sxs-lookup"><span data-stu-id="79706-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="79706-136">在這個階段，您可以建立執行 Windows 10 企業版的獨立電腦。</span><span class="sxs-lookup"><span data-stu-id="79706-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="79706-137">實體電腦</span><span class="sxs-lookup"><span data-stu-id="79706-137">Physical computer</span></span>

<span data-ttu-id="79706-p105">取得個人電腦並在其上安裝 Windows 10 企業版。您可以在[這裡](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)下載 Windows 10 企業版試用版。</span><span class="sxs-lookup"><span data-stu-id="79706-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="79706-140">虛擬機器</span><span class="sxs-lookup"><span data-stu-id="79706-140">Virtual machine</span></span>

<span data-ttu-id="79706-p106">使用您所選的 Hypervisor 建立虛擬機器並在其上安裝 Windows 10 企業版。您可以在[這裡](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)下載 Windows 10 企業版試用版。</span><span class="sxs-lookup"><span data-stu-id="79706-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="79706-143">Azure 中的虛擬機器</span><span class="sxs-lookup"><span data-stu-id="79706-143">Virtual machine in Azure</span></span>

<span data-ttu-id="79706-p107">若要在 Microsoft Azure 中建立 Windows 10 虛擬機器，***您必須擁有以 Visual Studio 為基礎的訂閱***，其具有 Windows 10 企業版的影像存取權。其他類型的 Azure 訂閱，例如試用版與付費訂閱，沒有此影像的存取權。</span><span class="sxs-lookup"><span data-stu-id="79706-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image.</span></span>
  
> [!NOTE]
> <span data-ttu-id="79706-p108">下列命令集使用最新版本的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/)。這些命令集會建置名為 WIN10 的 Windows 10 企業版虛擬機器，以及所有必要的基礎結構，包括資源群組、儲存體帳戶及虛擬網路。如果您已熟悉 Azure 基礎結構服務，請調整這些指示以符合您目前所部署的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="79706-p108">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="79706-150">首先，啟動 Microsoft PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="79706-150">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="79706-151">使用下列命令登入您的 Azure 帳戶。</span><span class="sxs-lookup"><span data-stu-id="79706-151">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="79706-152">使用下列命令取得訂用帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="79706-152">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="79706-p109">設定 Azure 訂用帳戶。以正確的名稱取代括號中的所有項目 (包括 \< 和 > 字元)。</span><span class="sxs-lookup"><span data-stu-id="79706-p109">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="79706-p110">接著，建立新的資源群組。若要判斷資源群組名稱是否是唯一的，可使用此命令來列出現有的資源群組。</span><span class="sxs-lookup"><span data-stu-id="79706-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="79706-p111">使用這些命令建立新的資源群組。以正確的名稱取代引號內的所有項目 (包括 \< 和 > 字元)。</span><span class="sxs-lookup"><span data-stu-id="79706-p111">Create your new resource group with these commands. Set the variables by replacing everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="79706-p112">接下來，您可以使用這些命令建立新的虛擬網路和 WIN10 虛擬機器。出現提示時，請提供 WIN10 本機系統管理員帳戶的名稱和密碼，並將其存放在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="79706-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
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
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="79706-161">階段 4：將 Windows 10 電腦加入 Azure AD</span><span class="sxs-lookup"><span data-stu-id="79706-161">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="79706-162">建立實體或虛擬機器的 Windows 10 企業版之後，使用本機系統管理員帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="79706-162">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="79706-p113">針對 Azure 中的虛擬機器，使用[這些指示](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)進行連線。使用本機系統管理員帳戶認證登入。</span><span class="sxs-lookup"><span data-stu-id="79706-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="79706-165">接下來，將 WIN10 電腦加入 Office 365 和 EMS 訂閱的 Azure AD 租用戶。</span><span class="sxs-lookup"><span data-stu-id="79706-165">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="79706-166">在 WIN10 電腦桌面，按一下 [開始] > [設定] > [帳戶] > [存取公司或學校] > [連線]****。</span><span class="sxs-lookup"><span data-stu-id="79706-166">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="79706-167">在 [設定公司或學校帳戶]**** 對話方塊中，按一下 [將此裝置加入 Azure Active Directory]****。</span><span class="sxs-lookup"><span data-stu-id="79706-167">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="79706-168">在 [公司或學校帳戶]**** 中，輸入 Office 365 訂閱的全域管理員帳戶名稱，然後按一下 [下一步]****。</span><span class="sxs-lookup"><span data-stu-id="79706-168">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="79706-169">在 [輸入密碼]**** 中，輸入全域管理員帳戶的密碼，然後按一下 [登入]****。</span><span class="sxs-lookup"><span data-stu-id="79706-169">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="79706-170">系統提示您確認這是您的組織時，按一下 [加入]****，然後按一下 [完成]****。</span><span class="sxs-lookup"><span data-stu-id="79706-170">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="79706-171">關閉 [設定] 視窗。</span><span class="sxs-lookup"><span data-stu-id="79706-171">Close the Help window.</span></span>
    
<span data-ttu-id="79706-172">接下來，在 WIN10 電腦上安裝 Office 2016。</span><span class="sxs-lookup"><span data-stu-id="79706-172">Next, install Office 2016 on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="79706-p114">開啟 Microsoft Edge 瀏覽器，並使用全域管理員帳戶認證登入 Office 365 入口網站。如需說明，請參閱[在何處登入 Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)。</span><span class="sxs-lookup"><span data-stu-id="79706-p114">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="79706-175">在 [Microsoft Office 首頁]**** 索引標籤上，按一下 [安裝 Office 2016]****。</span><span class="sxs-lookup"><span data-stu-id="79706-175">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="79706-176">系統提示您要執行的動作時，按一下 [執行]****，然後為 [使用者帳戶控制]**** 按一下 [是]****。</span><span class="sxs-lookup"><span data-stu-id="79706-176">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="79706-p115">等待 Office 完成安裝。當您看到 **「一切就緒！」** 時，按兩次 [關閉]****。</span><span class="sxs-lookup"><span data-stu-id="79706-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="79706-179">圖 3 顯示您產生的環境，其中包括已加入 Office 365 和 EMS 訂閱的 Azure AD 租用戶之 WIN10 電腦。</span><span class="sxs-lookup"><span data-stu-id="79706-179">Figure 3 shows your resulting environment, which includes the WIN10 computer that has joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
<span data-ttu-id="79706-180">**圖 3：將 WIN10 電腦帳戶新增至 Azure AD 租用戶**</span><span class="sxs-lookup"><span data-stu-id="79706-180">**Figure 3: Adding the WIN10 computer account to the Azure AD tenant**</span></span>

![Microsoft 365 企業版 開發/測試環境的階段 4](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="79706-182">您現在已準備好嘗試 [Microsoft 365 企業版](https://www.microsoft.com/microsoft-365/enterprise)的其他功能。</span><span class="sxs-lookup"><span data-stu-id="79706-182">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="79706-183">後續步驟</span><span class="sxs-lookup"><span data-stu-id="79706-183">Next steps</span></span>

<span data-ttu-id="79706-184">使用下列額外文章探索 Microsoft 365 企業版的功能：</span><span class="sxs-lookup"><span data-stu-id="79706-184">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="79706-185">新增行動應用程式管理 (MAM) 原則</span><span class="sxs-lookup"><span data-stu-id="79706-185">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="79706-186">註冊 iOS 和 Android 裝置</span><span class="sxs-lookup"><span data-stu-id="79706-186">Enroll iOS and Android devices</span></span>](https://technet.microsoft.com/library/mt743077.aspx)
    
- [<span data-ttu-id="79706-187">設定及測試進階安全性管理</span><span class="sxs-lookup"><span data-stu-id="79706-187">Configure and test Advanced Security Management</span></span>](https://technet.microsoft.com/library/mt757250.aspx)
    
- [<span data-ttu-id="79706-188">設定及測試進階威脅防護</span><span class="sxs-lookup"><span data-stu-id="79706-188">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="79706-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79706-189">See Also</span></span>

- [<span data-ttu-id="79706-190">Microsoft 365 企業版文件</span><span class="sxs-lookup"><span data-stu-id="79706-190">Microsoft 365 Enterprise documentation and resources</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- <span data-ttu-id="79706-191">[部署 Microsoft 365 企業版](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span><span class="sxs-lookup"><span data-stu-id="79706-191">Microsoft 365 Enterprise[](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)</span></span>
- [<span data-ttu-id="79706-192">One Microsoft Cloud 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="79706-192">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="79706-193">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="79706-193">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
