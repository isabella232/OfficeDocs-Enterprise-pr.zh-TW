---
title: "Office 365 開發人員/測試環境的同盟身分識別"
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
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: "摘要： 設定 Office 365 開發人員/測試環境的同盟的驗證。"
ms.openlocfilehash: c88019389e610a60625d6a97881249077477c4ea
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="federated-identity-for-your-office-365-devtest-environment"></a><span data-ttu-id="a1d0f-103">Office 365 開發人員/測試環境的同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="a1d0f-103">Federated identity for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="a1d0f-104">**摘要：**設定 Office 365 開發人員/測試環境的同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-104">**Summary:** Configure federated authentication for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="a1d0f-p101">Office 365 支援同盟身分識別。這表示而非本身執行的認證驗證、 Office 365 指的是連線的使用者在 Office 365 信任的同盟的驗證伺服器。如果使用者的認證是正確的同盟的驗證伺服器問題用戶端接著會傳送至 Office 365 做為驗證證明安全性權杖。卸載和擴充 Office 365 訂閱和進階的驗證及安全性案例的驗證允許同盟身分識別。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p101">Office 365 supports federated identity. This means that instead of performing the validation of credentials itself, Office 365 refers the connecting user to a federated authentication server that Office 365 trusts. If the user's credentials are correct, the federated authentication server issues a security token that the client then sends to Office 365 as proof of authentication. Federated identity allows for the offloading and scaling up of authentication for an Office 365 subscription and advanced authentication and security scenarios.</span></span>
  
<span data-ttu-id="a1d0f-109">本文說明您可以如何設定 Office 365 開發人員/測試環境中，同盟的驗證產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-109">This article describes how you can configure federated authentication for the Office 365 dev/test environment, resulting in the following:</span></span>
  
<span data-ttu-id="a1d0f-110">**圖 1： 同盟的驗證 Office 365 開發人員/測試環境**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-110">**Figure 1: The federated authentication for Office 365 dev/test environment**</span></span>

![將 Web 應用程式 Proxy 伺服器新增至 Office 365 開發/測試環境的 DirSync](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="a1d0f-112">圖 1 所示的組態所組成：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-112">The configuration shown in Figure 1 consists of:</span></span> 
  
- <span data-ttu-id="a1d0f-113">Office 365 E5 試用版訂閱，這會從建立時的 30 天到期。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-113">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="a1d0f-p102">簡化的組織內部網路連線至網際網路，在 Azure 虛擬網路 （DC1、 APP1、 CLIENT1、 ADFS1 及 PROXY1） 的子網路上的五個虛擬機器時所組成。同步處理至 Office 365 的 Windows Server AD 網域中的帳戶的清單在 APP1 上，執行 azure AD 連線。PROXY1 接收內送的驗證要求。ADFS1 會驗證與 DC1 認證並發出安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p102">A simplified organization intranet connected to the Internet, consisting of five virtual machines on a subnet of an Azure virtual network (DC1, APP1, CLIENT1, ADFS1, and PROXY1). Azure AD Connect runs on APP1 to synchronize the list of accounts in the Windows Server AD domain to Office 365. PROXY1 receives the incoming authentication requests. ADFS1 validates credentials with DC1 and issues security tokens.</span></span>
    
<span data-ttu-id="a1d0f-118">有五個階段來設定此開發/測試環境：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-118">There are five phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="a1d0f-119">使用 DirSync 建立模擬企業版 Office 365 開發人員/測試環境。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-119">Create the simulated enterprise Office 365 dev/test environment with DirSync.</span></span>
    
2. <span data-ttu-id="a1d0f-120">建立 AD FS 伺服器 (ADFS1)。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-120">Create the AD FS server (ADFS1).</span></span>
    
3. <span data-ttu-id="a1d0f-121">建立 web proxy 伺服器 (PROXY1)。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-121">Create the web proxy server (PROXY1).</span></span>
    
4. <span data-ttu-id="a1d0f-122">建立自我簽署的憑證並設定 ADFS1 和 PROXY1。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-122">Create a self-signed certificate and configure ADFS1 and PROXY1.</span></span>
    
5. <span data-ttu-id="a1d0f-123">設定 Office 365 的同盟身分識別。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-123">Configure Office 365 for federated identity.</span></span>
    
<span data-ttu-id="a1d0f-124">若要逐步解說實際執行部署在 Azure 中的 Office 365 同盟驗證的步驟，請參閱[在 Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-124">To step through a production deployment of federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="a1d0f-125">您不能設定這個開發/測試環境與 Azure 試用版訂閱。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-125">You cannot configure this dev/test environment with an Azure Trial subscription.</span></span> 
  
> [!TIP]
> <span data-ttu-id="a1d0f-126">按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-126">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-simulated-enterprise-office-365-devtest-environment-with-dirsync"></a><span data-ttu-id="a1d0f-127">階段 1： 建立使用 DirSync 模擬企業版 Office 365 開發人員/測試環境</span><span class="sxs-lookup"><span data-stu-id="a1d0f-127">Phase 1: Create the simulated enterprise Office 365 dev/test environment with DirSync</span></span>

<span data-ttu-id="a1d0f-128">遵循[DirSync Office 365 開發人員/測試環境](dirsync-for-your-office-365-dev-test-environment.md)中的指示來建立 APP1 DirSync 伺服器與 Office 365 和 Windows Server AD 之間的同步處理的 identity 為模擬企業版 Office 365 開發人員/測試環境在 DC1 帳戶。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-128">Follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md) to create the simulated enterprise Office 365 dev/test environment with APP1 as the DirSync server and synchronized identity between Office 365 and the Windows Server AD accounts on DC1.</span></span>
  
<span data-ttu-id="a1d0f-p103">接下來，建立新公用 DNS 網域名稱根據您目前的網域名稱並將其新增至您的 Office 365 訂閱。我們建議使用名稱**testlab。**\<公用網域 >。例如，如果您的部署公用網域名稱是 contoso.com，新增公用網域名稱 testlab.contoso.com。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p103">Next, create a new public DNS domain name based on your current domain name and add it to your Office 365 subscription. We recommend using the name **testlab.**\<your public domain>. For example, if your public domain name is contoso.com, add the public domain name testlab.contoso.com.</span></span>
  
<span data-ttu-id="a1d0f-132">如需如何在您的 DNS 提供者建立正確的 DNS 記錄，並將網域新增至您的 Office 365 試用版訂閱的指示，請參閱[新增使用者和 Office 365 的網域](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611)。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-132">For instructions on how to create the correct DNS records in your DNS provider and add the domain to your Office 365 trial subscription, see [Add users and domain to Office 365](https://support.office.com/article/Add-users-and-domain-to-Office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611).</span></span> 
  
<span data-ttu-id="a1d0f-133">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-133">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="a1d0f-134">**圖 2： Office 365 開發人員/測試環境的 DirSync**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-134">**Figure 2: DirSync for Office 365 dev/test environment**</span></span>

![具有 DirSync 的 Office 365 開發/測試環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="a1d0f-136">圖 2 顯示 Office 365 開發人員/測試環境，其中包含 Office 365 CLIENT1、 APP1 與 DC1 虛擬機器在 Azure 虛擬網路的 DirSync。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-136">Figure 2 shows the DirSync for Office 365 dev/test environment, which includes Office 365 and CLIENT1, APP1, and DC1 virtual machines in an Azure virtual network.</span></span>
  
## <a name="phase-2-create-the-ad-fs-server"></a><span data-ttu-id="a1d0f-137">階段 2： 建立 AD FS 伺服器</span><span class="sxs-lookup"><span data-stu-id="a1d0f-137">Phase 2: Create the AD FS server</span></span>

<span data-ttu-id="a1d0f-138">AD FS 伺服器提供 Office 365 與 DC1 上裝載的 corp.contoso.com 網域中的帳戶之間的同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-138">An AD FS server provides federated authentication between Office 365 and the accounts in the corp.contoso.com domain hosted on DC1.</span></span>
  
<span data-ttu-id="a1d0f-139">若要建立 ADFS1 Azure 虛擬機器，您的訂閱資源群組與您的基底設定 Azure 位置的名稱中填滿和執行這些命令在 Azure PowerShell 命令提示字元本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-139">To create an Azure virtual machine for ADFS1, fill in the name of your subscription and the resource group and Azure location for your Base Configuration, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$subscr="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
Login-AzureRMAccount
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
$staticIP="10.0.0.100"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzureRMNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!TIP]
> <span data-ttu-id="a1d0f-140">按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0)以取得包含在本文中的所有 PowerShell 命令的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-f79bc2c2?redir=0) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="a1d0f-141">下一步] 使用[Azure 入口網站](http://portal.azure.com)連線至 ADFS1 虛擬機器使用 ADFS1 本機系統管理員帳戶名稱和密碼，然後再開啟 [Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-141">Next, use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the ADFS1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="a1d0f-142">若要檢查 ADFS1 與 DC1 之間的名稱解析和網路通訊，請執行**ping dc1.corp.contoso.com**命令並確認有四個回覆。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-142">To check name resolution and network communication between ADFS1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="a1d0f-143">接下來，這些命令在 Windows PowerShell 提示字元上 ADFS1 CORP 網域加入 ADFS1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-143">Next, join the ADFS1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on ADFS1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="a1d0f-144">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-144">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="a1d0f-145">**圖 3： 新增 AD FS 伺服器**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-145">**Figure 3: Adding the AD FS server**</span></span>

![將 AD FS 伺服器新增至 Office 365 開發/測試環境的 DirSync](images/da82f39e-426d-41e2-842a-c13b382d63d5.png)
  
<span data-ttu-id="a1d0f-147">圖 3 顯示的 ADFS1 伺服器新增至 Office 365 開發人員/測試環境的 DirSync。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-147">Figure 3 shows the addition of the ADFS1 server to the DirSync for Office 365 dev/test environment.</span></span>
  
## <a name="phase-3-create-the-web-proxy-server"></a><span data-ttu-id="a1d0f-148">階段 3： 建立的 web proxy 伺服器</span><span class="sxs-lookup"><span data-stu-id="a1d0f-148">Phase 3: Create the web proxy server</span></span>

<span data-ttu-id="a1d0f-149">PROXY1 提供代理的使用者嘗試驗證和 ADFS1 之間的驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-149">PROXY1 provides proxying of authentication messages between users attempting to authenticate and ADFS1.</span></span>
  
<span data-ttu-id="a1d0f-150">若要建立 PROXY1 Azure 虛擬機器，您的資源群組和 Azure 位置的名稱中填滿，然後在本機電腦上的 Azure PowerShell 命令提示字元執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-150">To create an Azure virtual machine for PROXY1, fill in the name of your resource group and Azure location, and then run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
$staticIP="10.0.0.101"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip = New-AzureRMPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzureRMNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="a1d0f-151">因為您會建立其和其點必須不會變更當您重新啟動 PROXY1 虛擬機器時的公用 DNS 記錄 PROXY1 指派靜態公用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-151">PROXY1 is assigned a static public IP address because you will create a public DNS record that points to it and it must not change when you restart the PROXY1 virtual machine.</span></span> 
  
<span data-ttu-id="a1d0f-p104">下一步] 新增規則至以允許來自網際網路的來路不明輸入的流量 PROXY1 的私人 IP 位址和 TCP 連接埠 443 依舊套用子網路的網路安全性群組。本機電腦上 Azure PowerShell 命令提示字元執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p104">Next, add a rule to the network security group for the CorpNet subnet to allow unsolicited inbound traffic from the Internet to PROXY1's private IP address and TCP port 443. Run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<the resource group name of your Base Configuration>"
Get-AzureRmNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzureRmNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzureRmNetworkSecurityGroup
```

<span data-ttu-id="a1d0f-154">下一步] 使用[Azure 入口網站](http://portal.azure.com)連線至 PROXY1 虛擬機器使用 PROXY1 本機系統管理員帳戶名稱和密碼，然後再開啟 [Windows PowerShell 命令提示字元上 PROXY1。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-154">Next, use the [Azure portal](http://portal.azure.com) to connect to the PROXY1 virtual machine using the PROXY1 local administrator account name and password, and then open a Windows PowerShell command prompt on PROXY1.</span></span>
  
<span data-ttu-id="a1d0f-155">若要檢查 PROXY1 與 DC1 之間的名稱解析和網路通訊，請執行**ping dc1.corp.contoso.com**命令並確認有四個回覆。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-155">To check name resolution and network communication between PROXY1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="a1d0f-156">接下來，這些命令在 Windows PowerShell 提示字元上 PROXY1 CORP 網域加入 PROXY1 虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-156">Next, join the PROXY1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt on PROXY1.</span></span>
  
```
$cred=Get-Credential -UserName "CORP\\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

<span data-ttu-id="a1d0f-157">本機電腦上顯示 PROXY1 公用 IP 位址與這些 Azure PowerShell 命令：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-157">Display the public IP address of PROXY1 with these Azure PowerShell commands on your local computer:</span></span>
  
```
Write-Host (Get-AzureRMPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

<span data-ttu-id="a1d0f-p105">接下來，使用公用 DNS 提供者和建立新的公用 DNS A 記錄**fs.testlab。**\<DNS 網域名稱 > 的解析為**寫入主機**命令顯示的 IP 位址。**Fs.testlab。**\<DNS 網域名稱 > 以下稱為*同盟服務 FQDN* 。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p105">Next, work with your public DNS provider and create a new public DNS A record for **fs.testlab.**\<your DNS domain name> that resolves to the IP address displayed by the **Write-Host** command. The **fs.testlab.**\<your DNS domain name> is hereafter referred to as the  *federation service FQDN*  .</span></span>
  
<span data-ttu-id="a1d0f-160">接下來，使用[Azure 入口網站](http://portal.azure.com)連線至 DC1 虛擬機器使用 CORP\\User1 認證，然後再執行下列命令在系統管理員層級 Windows PowerShell 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-160">Next, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then run the following commands at an administrator-level Windows PowerShell command prompt:</span></span>
  
```
$testZone="<the FQDN of your testlab domain from phase 1, example: testlab.contoso.com>"
$testZoneFile= $testZone + ".dns"
Add-DnsServerPrimaryZone -Name $testZone -ZoneFile $testZoneFile
Add-DnsServerResourceRecordA -Name "fs" -ZoneName $testZone -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```

<span data-ttu-id="a1d0f-161">這些命令會建立同盟服務在 Azure 虛擬網路上的虛擬機器可以解析為 ADFS1 的私人 IP 位址的 FQDN 的 DNS A 記錄。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-161">These commands create a DNS A record for your federation service FQDN that virtual machines on the Azure virtual network can resolve to ADFS1's private IP address.</span></span>
  
<span data-ttu-id="a1d0f-162">以下是您產生的組態。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-162">Here is your resulting configuration.</span></span>
  
<span data-ttu-id="a1d0f-163">**圖 4： 新增 web 應用程式 proxy 伺服器**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-163">**Figure 4: Adding the web application proxy server**</span></span>

![將 Web 應用程式 Proxy 伺服器新增至 Office 365 開發/測試環境的 DirSync](images/f50039e4-796a-42c0-bfdc-87c2026b1579.png)
  
<span data-ttu-id="a1d0f-165">圖 4 顯示的 PROXY1 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-165">Figure 4 shows the addition of the PROXY1 server.</span></span>
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a><span data-ttu-id="a1d0f-166">階段 4： 建立自我簽署的憑證並設定 ADFS1 和 PROXY1</span><span class="sxs-lookup"><span data-stu-id="a1d0f-166">Phase 4: Create a self-signed certificate and configure ADFS1 and PROXY1</span></span>

<span data-ttu-id="a1d0f-167">在此階段中，您建立自我簽署的數位憑證同盟服務 FQDN 及設定 ADFS1 及 PROXY1 為 AD FS 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-167">In this phase, you create a self-signed digital certificate for your federation service FQDN and configure ADFS1 and PROXY1 as an AD FS farm.</span></span>
  
<span data-ttu-id="a1d0f-168">首先，使用[Azure 入口網站](http://portal.azure.com)連線至 DC1 虛擬機器使用 CORP\\User1 認證並再開啟 [系統管理員層級 Windows PowerShell 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-168">First, use the [Azure portal](http://portal.azure.com) to connect to the DC1 virtual machine using the CORP\\User1 credentials, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="a1d0f-169">接下來，建立 AD FS 服務帳戶使用下列命令在 DC1 Windows PowerShell 命令提示字元：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-169">Next, create AD FS service account with this command at the Windows PowerShell command prompt on DC1:</span></span>
  
```
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="a1d0f-p106">請注意此命令會提示您提供帳戶密碼。選擇強式密碼，並將其記錄在安全的位置。您將需要此階段與階段 5。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p106">Note that this command prompts you to supply the account password. Choose a strong password and record it in a secured location. You will need it for this phase and Phase 5.</span></span>
  
<span data-ttu-id="a1d0f-p107">使用[Azure 入口網站](http://portal.azure.com)連線至 ADFS1 虛擬機器使用 CORP\\User1 認證。開啟 ADFS1 中系統管理員層級 Windows PowerShell 命令提示字元、 填滿的同盟服務 FQDN] 中，並再執行下列命令以建立自我簽署的憑證：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p107">Use the [Azure portal](http://portal.azure.com) to connect to the ADFS1 virtual machine using the CORP\\User1 credentials. Open an administrator-level Windows PowerShell command prompt on ADFS1, fill in your federation service FQDN, and then run these commands to create a self-signed certificate:</span></span>
  
```
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\\LocalMachine\\My"
New-Item -path c:\\Certs -type directory
New-SmbShare -name Certs -path c:\\Certs -changeaccess CORP\\User1
```

<span data-ttu-id="a1d0f-175">下一步] 以儲存新的自我簽署的憑證的檔案中使用下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-175">Next, use these steps to save the new self-signed certificate as a file.</span></span>
  
1. <span data-ttu-id="a1d0f-176">按一下 [**開始]**、 輸入**mmc.exe**，並按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-176">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="a1d0f-177">按一下 [**檔 > 新增/移除嵌入式管理單元**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-177">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="a1d0f-178">在 [**新增或移除嵌入式管理單元**，按兩下 [**憑證**] 清單中的可用嵌入式管理單元、 按一下 [**電腦帳戶**，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-178">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="a1d0f-179">在 [**選擇電腦**] 按一下 [**完成**] 和 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-179">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="a1d0f-180">在樹狀目錄窗格中，開啟**Certificates (Local Computer) > 個人 > 憑證**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-180">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="a1d0f-181">以滑鼠右鍵按一下與您的同盟服務 FQDN 的憑證、 按一下 [**所有工作**] 和 [**匯出**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-181">Right-click the certificate with your federation service FQDN, click **All tasks**, and then click **Export**.</span></span>
    
7. <span data-ttu-id="a1d0f-182">在 [**歡迎**] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-182">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="a1d0f-183">在 [**匯出私密金鑰**] 頁面上按一下 [ **]**，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-183">On the **Export Private Key** page, click **Yes**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="a1d0f-184">在 [**匯出檔案格式**] 頁面上按一下 [**匯出所有延伸的內容**] 並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-184">On the **Export File Format** page, click **Export all extended properties**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="a1d0f-185">在 [**安全性**] 頁面上按一下 [**密碼**及**密碼**中輸入密碼並**確認密碼。**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-185">On the **Security** page, click **Password** and type a password in **Password** and **Confirm password.**</span></span>
    
11. <span data-ttu-id="a1d0f-186">在 [**要匯出的檔案**] 頁面上按一下 [**瀏覽**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-186">On the **File to Export** page, click **Browse**.</span></span>
    
12. <span data-ttu-id="a1d0f-187">瀏覽至**c:\\憑證**資料夾中，輸入**檔案名稱**] 中的**SSL** ] 和 [**儲存。**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-187">Browse to the **C:\\Certs** folder, type **SSL** in **File name**, and then click **Save.**</span></span>
    
13. <span data-ttu-id="a1d0f-188">在 [**要匯出的檔案**] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-188">On the **File to Export** page, click **Next**.</span></span>
    
14. <span data-ttu-id="a1d0f-p108">在 [**完成憑證匯出精靈**] 頁面上，按一下 [**完成**]。出現提示時，按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p108">On the **Completing the Certificate Export Wizard** page, click **Finish**. When prompted, click **OK**.</span></span>
    
<span data-ttu-id="a1d0f-191">下一步] 安裝 AD FS 服務使用在 Windows PowerShell 命令提示字元上 ADFS1 下列命令：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-191">Next, install the AD FS service with this command at the Windows PowerShell command prompt on ADFS1:</span></span>
  
```
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

<span data-ttu-id="a1d0f-192">等候完成安裝。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-192">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="a1d0f-193">接下來，設定 AD FS 服務進行這些步驟：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-193">Next, configure the AD FS service with these steps:</span></span>
  
1. <span data-ttu-id="a1d0f-194">按一下 [**開始**] 並再按一下 [**伺服器管理員**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-194">Click **Start**, and then click the **Server Manager** icon.</span></span>
    
2. <span data-ttu-id="a1d0f-195">在樹狀目錄窗格的 [伺服器管理員中，按一下 [ **AD FS**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-195">In the tree pane of Server Manager, click **AD FS**.</span></span>
    
3. <span data-ttu-id="a1d0f-196">在上方的 [工具] 列中按一下 [橘色小心符號和 [**設定此伺服器上的同盟服務**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-196">In the tool bar at the top, click the orange caution symbol, and then click **Configure the federation service on this server**.</span></span>
    
4. <span data-ttu-id="a1d0f-197">按一下 [Active Directory Federation Services 組態精靈的 [**歡迎**] 頁面上的 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-197">On the **Welcome** page of the Active Directory Federation Services Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="a1d0f-198">在 [**連接至 AD DS** ] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-198">On the **Connect to AD DS** page, click **Next**.</span></span>
    
6. <span data-ttu-id="a1d0f-199">在 [**指定服務屬性**] 頁面上：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-199">On the **Specify Service Properties** page:</span></span>
    
  - <span data-ttu-id="a1d0f-200">**SSL 憑證**，按一下向下箭號，和 [同盟服務 FQDN 名稱的憑證。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-200">For **SSL Certificate**, click the down arrow, and then click the certificate with the name of your federation service FQDN.</span></span>
    
  - <span data-ttu-id="a1d0f-201">在**同盟服務顯示名稱**] 中輸入虛構組織的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-201">In **Federation Service Display Name**, type the name of your fictional organization.</span></span>
    
  - <span data-ttu-id="a1d0f-202">按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-202">Click **Next**.</span></span>
    
7. <span data-ttu-id="a1d0f-203">在 [**指定服務帳戶**] 頁面上，按一下 [**選取**的**帳戶名稱**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-203">On the **Specify Service Account** page, click **Select** for **Account name**.</span></span>
    
8. <span data-ttu-id="a1d0f-204">在 [**選取使用者或服務帳戶**，輸入**ADFS 服務**、 按一下 [**檢查名稱**] 和 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-204">In **Select User or Service Account**, type **ADFS-Service**, click **Check Names**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="a1d0f-205">在**帳戶密碼**、 輸入的 ADFS 服務帳戶的密碼，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-205">In **Account Password**, type the password for the ADFS-Service account, and then click **Next**.</span></span>
    
10. <span data-ttu-id="a1d0f-206">在 [**指定設定資料庫**] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-206">On the **Specify Configuration Database** page, click **Next**.</span></span>
    
11. <span data-ttu-id="a1d0f-207">按一下 [**檢閱選項**] 頁面的 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-207">On the **Review Options** page, click **Next**.</span></span>
    
12. <span data-ttu-id="a1d0f-208">按一下 [**必要條件檢查**] 索引標籤的 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-208">On the **Pre-requisite Checks** page, click **Configure**.</span></span>
    
13. <span data-ttu-id="a1d0f-209">在 [**結果**] 頁面上按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-209">On the **Results** page, click **Close**.</span></span>
    
14. <span data-ttu-id="a1d0f-210">按一下 [**開始]**、 按一下 [進階] 圖示、 按一下 [**重新啟動**，然後按一下 [**繼續]**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-210">Click **Start**, click the power icon, click **Restart**, and then click **Continue**.</span></span>
    
<span data-ttu-id="a1d0f-211">從[Azure 入口網站](http://portal.azure.com)連線到與公司 PROXY1\\User1 帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-211">From the [Azure portal](http://portal.azure.com), connect to PROXY1 with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="a1d0f-212">下一步] 安裝的自我簽署的憑證並設定 PROXY1 使用這些步驟。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-212">Next, use these steps to install the self-signed certificate and configure PROXY1.</span></span>
  
1. <span data-ttu-id="a1d0f-213">按一下 [**開始]**、 輸入**mmc.exe**，並按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-213">Click **Start**, type **mmc.exe**, and then press **Enter**.</span></span>
    
2. <span data-ttu-id="a1d0f-214">按一下 [**檔 > 新增/移除嵌入式管理單元**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-214">Click **File > Add/Remove Snap-in**.</span></span>
    
3. <span data-ttu-id="a1d0f-215">在 [**新增或移除嵌入式管理單元**，按兩下 [**憑證**] 清單中的可用嵌入式管理單元、 按一下 [**電腦帳戶**，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-215">In **Add or Remove Snap-ins**, double-click **Certificates** in the list of available snap-ins, click **Computer account**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="a1d0f-216">在 [**選擇電腦**] 按一下 [**完成**] 和 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-216">In **Select Computer**, click **Finish**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="a1d0f-217">在樹狀目錄窗格中，開啟**Certificates (Local Computer) > 個人 > 憑證**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-217">In the tree pane, open **Certificates (Local Computer) > Personal > Certificates**.</span></span>
    
6. <span data-ttu-id="a1d0f-218">以滑鼠右鍵按一下 [**個人**、 按一下 [**所有工作**] 和 [**匯入**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-218">Right-click **Personal**, click **All tasks**, and then click **Import**.</span></span>
    
7. <span data-ttu-id="a1d0f-219">在 [**歡迎**] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-219">On the **Welcome** page, click **Next**.</span></span>
    
8. <span data-ttu-id="a1d0f-220">在 [**匯入的檔案**] 頁面上輸入**\\ \\adfs1\\憑證\\ssl.pfx**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-220">On the **File to Import** page, type **\\\\adfs1\\certs\\ssl.pfx**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="a1d0f-221">在 [**私密金鑰保護**] 頁面上輸入憑證密碼在 [**密碼**] 和 [**下一步。**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-221">On the **Private key protection** page, type the certificate password in **Password**, and then click **Next.**</span></span>
    
10. <span data-ttu-id="a1d0f-222">在 [**憑證存放區**] 頁面上，按一下 [**下一步。**</span><span class="sxs-lookup"><span data-stu-id="a1d0f-222">On the **Certificate store** page, click **Next.**</span></span>
    
11. <span data-ttu-id="a1d0f-223">在 [**完成**] 頁面上按一下 [**完成**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-223">On the **Completing** page, click **Finish**.</span></span>
    
12. <span data-ttu-id="a1d0f-224">在 [**憑證存放區**] 頁面上按一下 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-224">On the **Certificate Store** page, click **Next**.</span></span>
    
13. <span data-ttu-id="a1d0f-225">出現提示時，按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-225">When prompted, click **OK**.</span></span>
    
14. <span data-ttu-id="a1d0f-226">按一下 [**憑證**] 樹狀目錄窗格中。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-226">Click **Certificates** in the tree pane.</span></span>
    
15. <span data-ttu-id="a1d0f-227">以滑鼠右鍵按一下 [憑證]，並再按一下 [**複製**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-227">Right-click the certificate, and then click **Copy**.</span></span>
    
16. <span data-ttu-id="a1d0f-228">在樹狀目錄窗格中，開啟**受信任的根憑證授權單位 > 憑證**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-228">In the tree pane, open **Trusted Root Certification Authorities > Certificates**.</span></span>
    
17. <span data-ttu-id="a1d0f-229">將滑鼠指標下方的已安裝的憑證、 按一下滑鼠右鍵，然後按一下 [清單**貼**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-229">Move your mouse pointer below the list of installed certificates, right-click, and then click **Paste**.</span></span>
    
<span data-ttu-id="a1d0f-230">開啟系統管理員層級 PowerShell 命令提示字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-230">Open an administrator-level PowerShell command prompt and run the following command:</span></span>
  
```
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

<span data-ttu-id="a1d0f-231">等候完成安裝。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-231">Wait for the installation to complete.</span></span>
  
<span data-ttu-id="a1d0f-232">使用下列步驟來設定 web 應用程式 proxy 服務 ADFS1 作為其同盟伺服器：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-232">Use these steps to configure the web application proxy service to use ADFS1 as its federation server:</span></span>
  
1. <span data-ttu-id="a1d0f-233">按一下 [**開始**] 及 [**伺服器管理員**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-233">Click **Start**, and then click **Server Manager**.</span></span>
    
2. <span data-ttu-id="a1d0f-234">在樹狀目錄窗格中，按一下 [**遠端存取**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-234">In the tree pane, click **Remote Access**.</span></span>
    
3. <span data-ttu-id="a1d0f-235">在上方的 [工具] 列中按一下 [橘色小心符號和 [**開啟 Web 應用程式 Proxy] 精靈**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-235">In the tool bar at the top, click the orange caution symbol, and then click **Open the Web Application Proxy Wizard**.</span></span>
    
4. <span data-ttu-id="a1d0f-236">按一下 [Web 應用程式 Proxy 組態精靈] 的 [**歡迎**] 頁面上的 [**下一步**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-236">On the **Welcome** page of the Web Application Proxy Configuration Wizard, click **Next**.</span></span>
    
5. <span data-ttu-id="a1d0f-237">在**同盟伺服器**] 頁面上：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-237">On the **Federation Server** page:</span></span>
    
  - <span data-ttu-id="a1d0f-238">**同盟服務名稱**] 中輸入同盟服務 FQDN。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-238">Type your federation service FQDN in **Federation service name**.</span></span>
    
  - <span data-ttu-id="a1d0f-239">類型**CORP\\User1**在 [**使用者名稱**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-239">Type **CORP\\User1** in **User name**.</span></span>
    
  - <span data-ttu-id="a1d0f-240">在 [**密碼]**中輸入 User1 帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-240">Type the password for the User1 account in **Password**.</span></span>
    
  - <span data-ttu-id="a1d0f-241">按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-241">Click **Next**.</span></span>
    
6. <span data-ttu-id="a1d0f-242">在**AD FS Proxy 憑證**] 頁面上，按一下向下箭號、 按一下與您的同盟服務的 FQDN、 憑證，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-242">On the **AD FS Proxy Certificate** page, click the down arrow, click the certificate with your federation service FQDN, and then click **Next**.</span></span>
    
7. <span data-ttu-id="a1d0f-243">在 [**確認**] 頁面上按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-243">On the **Confirmation** page, click **Configure**.</span></span>
    
8. <span data-ttu-id="a1d0f-244">在 [**結果**] 頁面上按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-244">On the **Results** page, click **Close**.</span></span>
    
## <a name="phase-5-configure-office-365-for-federated-identity"></a><span data-ttu-id="a1d0f-245">階段 5： 設定 Office 365 同盟身分識別</span><span class="sxs-lookup"><span data-stu-id="a1d0f-245">Phase 5: Configure Office 365 for federated identity</span></span>

<span data-ttu-id="a1d0f-246">使用[Azure 入口網站](http://portal.azure.com)連線至公司 APP1 虛擬機器\\User1 帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-246">Use the [Azure portal](http://portal.azure.com) to connect to the APP1 virtual machine with the CORP\\User1 account credentials.</span></span>
  
<span data-ttu-id="a1d0f-247">使用下列步驟來設定 Azure AD 連線] 及 [您的 Office 365 訂閱同盟驗證：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-247">Use these steps to configure Azure AD Connect and your Office 365 subscription for federated authentication:</span></span>
  
1. <span data-ttu-id="a1d0f-248">從桌面，連按兩下 [ **Azure AD 連線**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-248">From the desktop, double-click **Azure AD Connect**.</span></span>
    
2. <span data-ttu-id="a1d0f-249">在 [**歡迎使用 Azure AD 連線**] 頁面上按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-249">On the **Welcome to Azure AD Connect** page, click **Configure**.</span></span>
    
3. <span data-ttu-id="a1d0f-250">在 [**其他工作**] 頁面上按一下 [**變更使用者登入**並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-250">On the **Additional tasks** page, click **Change user sign-in**, and then click **Next**.</span></span>
    
4. <span data-ttu-id="a1d0f-251">在**Azure AD 的連線**] 頁面上輸入您的 Office 365 全域管理員帳戶名稱和密碼，並再按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-251">On the **Connect to Azure AD** page, type your Office 365 global administrator account name and password, and then click **Next**.</span></span>
    
5. <span data-ttu-id="a1d0f-252">在 [**使用者登入**] 頁面上按一下 [**與 AD FS 同盟**，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-252">On the **User sign-in** page, click **Federation with AD FS**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="a1d0f-253">在 [ **AD FS 伺服器陣列**] 頁面上按一下 [**使用現有的 AD FS 伺服器陣列**、**伺服器名稱**] 中輸入**ADFS1** ，然後按 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-253">On the **AD FS farm** page, click **Use an existing AD FS farm**, type **ADFS1** in **Server Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="a1d0f-254">出現提示時輸入伺服器認證，輸入的公司認證\\User1 帳戶，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-254">When prompted for server credentials, enter the credentials of the CORP\\User1 account, and then click **OK**.</span></span>
    
8. <span data-ttu-id="a1d0f-255">在 [**網域系統管理員**認證] 頁面上輸入**CORP\\User1**的**使用者名稱**和**密碼**，在將帳戶密碼] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-255">On the **Domain Administrator** credentials page, type **CORP\\User1** in **Username** and the account password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="a1d0f-256">在 [ **AD FS 服務帳戶**] 頁面上輸入**CORP\\ADFS 服務****網域使用者名稱**和帳戶密碼的**網域使用者的密碼**，然後按一下 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-256">On the **AD FS service account** page, type **CORP\\ADFS-Service** in **Domain Username** and the account password in **Domain User Password**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="a1d0f-257">在**Azure AD 網域**] 頁面的 [**網域**] 中，選取您先前建立及新增至您的 Office 365 訂閱在階段 1 中的網域名稱] 和 [**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-257">On the **Azure AD Domain** page, in **Domain**, select the name of the domain you previously created and added to your Office 365 subscription in Phase 1, and then click **Next**.</span></span>
    
11. <span data-ttu-id="a1d0f-258">在 [**準備好設定**] 頁面上按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-258">On the **Ready to configure** page, click **Configure**.</span></span>
    
12. <span data-ttu-id="a1d0f-259">按一下 [**安裝完成**] 頁面的 [**驗證**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-259">On the **Installation complete** page, click **Verify**.</span></span>
    
    <span data-ttu-id="a1d0f-260">您應該在內部網路和網際網路看到訊息，指出已驗證設定。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-260">You should see messages indicating that both the intranet and Internet configuration was verified.</span></span>
    
13. <span data-ttu-id="a1d0f-261">在 [**安裝完成**] 頁面上按一下 [**結束**]。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-261">On the **Installation complete** page, click **Exit**.</span></span>
    
<span data-ttu-id="a1d0f-262">為示範使用同盟的驗證，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-262">To demonstrate that federated authentication is working, do the following:</span></span>
  
1. <span data-ttu-id="a1d0f-263">開啟瀏覽器本機電腦上的私用的新執行個體，並移至[https://portal.office.com](https://portal.office.com)。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-263">Open a new private instance of your browser on your local computer and go to [https://portal.office.com](https://portal.office.com).</span></span>
    
2. <span data-ttu-id="a1d0f-264">登入認證]，輸入**user1 @**\<在階段 1 中建立的網域 >。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-264">For the sign-in credentials, type **user1@**\<the domain created in Phase 1>.</span></span> 
    
    <span data-ttu-id="a1d0f-265">例如， **testlab.contoso.com**測試網域時，您將輸入**user1@testlab.contoso.com**。按 TAB 鍵或允許自動將您重新導向至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-265">For example, if your test domain is **testlab.contoso.com**, you would type **user1@testlab.contoso.com**. Press TAB or allow Office 365 to automatically redirect you.</span></span>
    
    <span data-ttu-id="a1d0f-p109">您現在應該會看到**是不私用的連線**] 頁面。您會看見此因為無法驗證您的桌上型電腦的 ADFS1 上安裝的自我簽署的憑證。在實際執行部署中的同盟驗證，您可以使用受信任的憑證授權單位的憑證，並讓使用者不會看到此頁面。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p109">You should now see a **Your connection is not private** page. You are seeing this because you installed a self-signed certificate on ADFS1 that your desktop computer cannot validate. In a production deployment of federated authentication, you would use a certificate from a trusted certification authority and your users would not see this page.</span></span>
    
3. <span data-ttu-id="a1d0f-269">**是不私用的連線**] 頁面上按一下 [**進階**] 和 [**繼續\<同盟服務 FQDN >**。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-269">On the **Your connection is not private** page, click **Advanced**, and then click **Proceed to \<your federation service FQDN>**.</span></span> 
    
4. <span data-ttu-id="a1d0f-270">在虛構組織名稱] 頁面上，使用登入下列：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-270">On the page with the name of your fictional organization, sign in with the following:</span></span>
    
  - <span data-ttu-id="a1d0f-271">**CORP\\User1**名稱</span><span class="sxs-lookup"><span data-stu-id="a1d0f-271">**CORP\\User1** for the name</span></span>
    
  - <span data-ttu-id="a1d0f-272">User1 帳戶的密碼</span><span class="sxs-lookup"><span data-stu-id="a1d0f-272">The password for the User1 account</span></span>
    
    <span data-ttu-id="a1d0f-273">您應該會看到 [ **Microsoft Office Home** ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-273">You should see the **Microsoft Office Home** page.</span></span>
    
<span data-ttu-id="a1d0f-p110">此程序示範如何在 Office 365 試用版訂閱與 DC1 上的 Windows Server AD corp.contoso.com 網域同盟。以下是驗證程序的基本知識：</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p110">This procedure demonstrates that your Office 365 trial subscription is federated with the Windows Server AD corp.contoso.com domain hosted on DC1. Here are the basics of the authentication process:</span></span>
  
1. <span data-ttu-id="a1d0f-276">當您使用剛才在階段 1 中的登入帳戶名稱的同盟的網域時，Office 365 您瀏覽器重新導向至您的同盟服務 FQDN 與 PROXY1。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-276">When you use the federated domain that you created in Phase 1 within the sign-in account name, Office 365 redirects your browser to your federation service FQDN and PROXY1.</span></span>
    
2. <span data-ttu-id="a1d0f-277">PROXY1 將您的本機電腦虛構公司的登入頁面。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-277">PROXY1 sends your local computer the fictional company sign-in page.</span></span>
    
3. <span data-ttu-id="a1d0f-278">當您傳送 CORP\\User1 和 PROXY1 密碼，它將其轉寄到 ADFS1。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-278">When you send CORP\\User1 and the password to PROXY1, it forwards them to ADFS1.</span></span>
    
4. <span data-ttu-id="a1d0f-279">ADFS1 驗證 CORP\\User1 和與 DC1 密碼，並傳送您的本機電腦的安全性 token。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-279">ADFS1 validates CORP\\User1 and the password with DC1 and sends your local computer a security token.</span></span>
    
5. <span data-ttu-id="a1d0f-280">您的本機電腦將安全性權杖傳送至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-280">Your local computer sends the security token to Office 365.</span></span>
    
6. <span data-ttu-id="a1d0f-281">Office 365 驗證安全性權杖由 ADFS1 所建立及允許存取。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-281">Office 365 validates that the security token was created by ADFS1 and allows access.</span></span>
    
<span data-ttu-id="a1d0f-p111">您的 Office 365 試用版訂閱現在已設定使用同盟驗證。您可以使用此開發/測試環境的進階的驗證案例。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-p111">Your Office 365 trial subscription is now configured with federated authentication. You can use this dev/test environment for advanced authentication scenarios.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="a1d0f-284">下一個步驟</span><span class="sxs-lookup"><span data-stu-id="a1d0f-284">Next Step</span></span>

<span data-ttu-id="a1d0f-285">當您準備好要部署實際執行就緒時，高可用性同盟的驗證 Office 365 中 Azure，請參閱[Azure 中的 Office 365 的部署高可用性同盟的驗證](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d0f-285">When you are ready to deploy production-ready, high availability federated authentication for Office 365 in Azure, see [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a1d0f-286">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1d0f-286">See Also</span></span>

[<span data-ttu-id="a1d0f-287">雲端採用測試實驗室指南 (TLG)</span><span class="sxs-lookup"><span data-stu-id="a1d0f-287">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="a1d0f-288">基底組態開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="a1d0f-288">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="a1d0f-289">Office 365 開發/測試環境</span><span class="sxs-lookup"><span data-stu-id="a1d0f-289">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="a1d0f-290">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="a1d0f-290">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="a1d0f-291">部署在 Azure 中的 Office 365 的高可用性同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="a1d0f-291">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)


