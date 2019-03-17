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
ms.openlocfilehash: 6180f9f87509d6ef29c52223c47726ff549de8d5
ms.sourcegitcommit: b85d3db24385d7e0bdbfb0d4499174ccd7f573bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "30650096"
---
# <a name="base-configuration-devtest-environment"></a>基底組態開發/測試環境

 **摘要：** 在 Microsoft Azure 中建立簡化的內部網路作為開發/測試環境。
  
本文提供指示，以在 Azure 中建立下列基底組態開發/測試環境：
  
![在 Azure 中建立基底組態](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
**圖 1：基底組態開發/測試環境**

圖 1 中的基底組態開發/測試環境包含名為 TestLab 的雲端專用 Azure 虛擬網路中的 Corpnet 子網路，其可模擬連線到網際網路的簡化私人內部網路。它具有執行 WIndows Server 2016 的三部 Azure 虛擬機器：
  
- DC1 已設定為內部網路網域控制站和網域名稱系統 (DNS) 伺服器
    
- APP1 已設定為一般應用程式和 Web 伺服器
    
- CLIENT1 做為內部網路用戶端
    
此設定可讓 DC1、APP1、CLIENT1 及其他 Corpnet 子網路的電腦： 
  
- 連線到網際網路以安裝更新、即時存取網際網路資源，並加入公用雲端技術，例如 Microsoft Office 365 與其他 Azure 服務。
    
- 從已連線到網際網路或您組織網路的電腦使用遠端桌面連線進行遠端管理。
    
您可以將產生的測試環境：
  
- 用於應用程式開發與測試。
    
- 做為自己設計的延伸測試環境之初始設定，其中包含其他虛擬機器、Azure 服務或其他 Microsoft 雲端產品，如 Office 365 及 Enterprise Mobility + Security (EMS)。
    
有兩種方法可以建立此環境：

1. Azure Resource Manager 範本
2. Azure Powershell

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>方法 1：使用 Azure Resource Manager 範本建立模擬內部網路

在這個方法中，您可以使用 Azure Resource Manager (ARM) 範本來建立模擬內部網路。ARM 範本包含建立及設定 Azure 網路基礎結構和虛擬機器的所有指示。

部署範本之前，請先閱讀[範本讀我檔案頁面](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)並準備好下列資訊：

- Azure 訂用帳戶名稱。您必須在 [自訂部署]**** 頁面的 [訂用帳戶]**** 欄位中輸入此標籤。
- Azure 資源群組名稱。您必須在 [自訂部署]**** 頁面的 [資源群組]**** 欄位中輸入此標籤。
- 虛擬機器公用 IP 位址 URL 上的 DNS 標籤前置詞。您必須在 [自訂部署]**** 頁面的 [DNS 標籤前置詞]**** 欄位中輸入此標籤。

閱讀指示之後，請在[範本讀我檔案頁面](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm)上按一下 [部署至 Azure]**** 以開始使用。

>[!Note]
>ARM 範本所建立的模擬內部網路需要 Azure 付費訂用帳戶。
>

範本完成後，您的組態如下。

![在 Azure 中建立基底組態](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>方法 2：使用 Azure PowerShell 建立模擬內部網路

在這個方法中，您使用 Windows PowerShell 和 Azure PowerShell 模組建置網路基礎結構、虛擬機器及其設定。

如果您想要使用 PowerShell 獲得一次建立一個 Azure 基礎結構命令區塊元素的體驗，則使用此方法。然後，您可以自行定義 PowerShell 命令區塊，以便在 Azure 中部署其他虛擬機器。

設定 Azure PowerShell 中的基底組態測試環境有四個步驟：
  
1. 建立虛擬網路。
    
2. 設定 DC1。
    
3. 設定 APP1。
    
4. 設定 CLIENT1。
    
如果您沒有 Azure 訂閱，可以在[試用 Azure](https://azure.microsoft.com/pricing/free-trial/) 中註冊免費試用版。如果您擁有 MSDN 或 Visual Studio 訂閱，請參閱 [Visual Studio 訂閱者每月 Azure 點數](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。
  
> [!NOTE]
> Azure 中的虛擬機器在執行時會持續產生成本。此成本是根據您的免費試用版、MSDN 訂閱或付費訂閱收費。如需執行 Azure 虛擬機器的成本相關資訊，請參閱[虛擬機器價格詳細資料](https://azure.microsoft.com/pricing/details/virtual-machines/)與 [Azure 價格計算機](https://azure.microsoft.com/pricing/calculator/)。若要降低成本，請參閱[降低 Azure 中測試環境虛擬機器的成本](base-configuration-dev-test-environment.md#mincost)。 
  
![Microsoft Cloud 中的測試實驗室指南](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
### <a name="step-1-create-the-virtual-network"></a>步驟 1：建立虛擬網路

在此步驟中，您會在 Azure 中對虛擬網路進行測試實驗。

首先，啟動 Azure PowerShell 提示。
  
> [!NOTE]
> 下列命令集會使用最新版的 Azure PowerShell。請參閱[開始使用 Azure PowerShell Cmdlet](https://docs.microsoft.com/zh-TW/powershell/azureps-cmdlets-docs/)。 
  
使用下列命令登入您的 Azure 帳戶。
  
```
Connect-AzAccount
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that has all the PowerShell commands in this article.
-->

使用下列命令取得訂用帳戶名稱。
  
```
Get-AzSubscription | Sort Name | Select Name
```

設定 Azure 訂用帳戶。以正確的名稱取代括號中的所有項目 (包括 < 和 > 字元)。
  
```
$subscr="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName -Current
```

接著，為您的基底組態測試實驗室建立新的資源群組。若要判斷資源群組名稱是否是唯一的，可使用此命令來列出現有的資源群組。
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

使用這些命令建立新的資源群組。以正確的名稱取代引號內的所有項目 (包括 < 和 > 字元)。
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

接著，您會建立將裝載基底組態 Corpnet 子網路的 TestLab 虛擬網路，並以網路安全性群組來保護它。
  
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

這是您目前的組態。
  
![Azure 中具有虛擬網路與子網路的基底組態的步驟 1](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a>步驟 2：設定 DC1

在此步驟中，我們會建立 DC1 虛擬機器，並將其設定為 corp.contoso.com Windows Server Active Directory (AD) 網域的網域控制站以及 TestLab 虛擬網路之虛擬機器的 DNS 伺服器。

> [!NOTE]
> 在執行下列命令區塊之前，請確定您所選擇的 Azure 區域 (位置) 支援 Azure 虛擬機器大小，預設設為 Standard_A1。按一下[這裡](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)以查看 Azure 虛擬機器大小和位置的最新資訊。
  
若要建立 DC1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。
  
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

系統會提示您輸入 DC1 上本機系統管理員帳戶的使用者名稱和密碼。使用強式密碼，並將名稱和密碼記錄於安全的位置。
  
接下來，連線到 DC1 虛擬機器。
  
1. 在 [Azure 入口網站](https://portal.azure.com)中，按一下 **[資源群組] >** [新的資源群組名稱] **> [DC1] > [連線]**。
    
2. 在開啟的窗格中，按一下 [下載 RDP 檔案]****。開啟所下載的 DC1.rdp 檔案，然後按一下 [連線]****。
    
3. 指定 DC1 本機系統管理員帳戶名稱：
    
  - 對於 Windows 7：
    
    在 [Windows 安全性]**** 對話方塊中，按一下 [使用其他帳戶]****。在 [使用者名稱]**** 中，輸入 **DC1\\**[本機系統管理員帳戶名稱]。
    
  - 對於 Windows 8 或 Windows 10：
    
    在 [Windows 安全性]**** 對話方塊中，按一下 [更多選項]****，然後按 [使用不同帳戶]****。在 [使用者名稱]**** 中，輸入 **DC1\\**[本機系統管理員帳戶名稱]。
    
4. 在 [密碼]**** 中，輸入本機系統管理員帳戶的密碼，然後按一下 [確定]****。
    
5. 出現提示時，按一下 [是]****。
    
接著，使用此命令在 DC1 上系統管理員層級 Windows PowerShell 命令提示字元將額外的資料磁碟新增為新的磁碟區 (磁碟機代號 F:)。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

接著，將 DC1 設定為網域控制站和 corp.contoso.com 網域的 DNS 伺服器。在系統管理員層級 Windows PowerShell 命令提示字元執行下列命令。
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
您必須指定安全模式的系統管理員密碼。將此密碼儲存在安全的位置。
  
請注意，這些命令可能需要數分鐘才能完成。
  
DC1 重新啟動後，使用網域認證以重新連線到 DC1 虛擬機器。
  
1. 在 [Azure 入口網站](https://portal.azure.com)中，按一下 **[資源群組] >** [您的資源群組名稱] **> [DC1] > [連線]**。
    
2. 執行所下載的 DC1.rdp 檔案，然後按一下 [連線]****。
    
3. 在 [Windows 安全性]**** 中，按一下 [使用其他帳戶]****。在 [使用者名稱]**** 中，輸入 **CORP\\**[本機系統管理員帳戶名稱]。
    
4. 在 [密碼]**** 中，輸入本機系統管理員帳戶的密碼，然後按一下 [確定]****。
    
5. 出現提示時，按一下 [是]****。
    
接下來，建立 Active Directory 中的使用者帳戶，可在登入 CORP 網域成員電腦時使用。在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

請注意，此命令會提示您提供 User1 帳戶密碼。由於這個帳戶將會用於所有 CORP 網域成員電腦的遠端桌面連線，請選擇強式密碼。記錄 User1 帳戶密碼，並將它儲存在安全的位置。
  
接下來，將新的 User1 帳戶設定為企業系統管理員。在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

關閉 DC1 的遠端桌面工作階段，然後使用 CORP\\User1 帳戶重新連線。
  
接下來，若要允許 Ping 工具的流量，請在系統管理員層級 Windows PowerShell 命令提示字元執行此命令。
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

這是您目前的組態。
  
![Azure 中具有 DC1 虛擬機器的基底組態的步驟 2](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a>步驟 3：設定 APP1

在這個步驟，您會建立及設定 APP1，它會提供 Web 和檔案共用服務。

> [!NOTE]
> 在執行下列命令區塊之前，請確定您所選擇的 Azure 區域 (位置) 支援 Azure 虛擬機器大小，預設設為 Standard_A1。按一下[這裡](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)以查看 Azure 虛擬機器大小和位置的最新資訊。
  
若要建立 APP1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。
  
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

接下來，使用 APP1 本機系統管理員帳戶名稱和密碼連線到 APP1 虛擬機器，然後開啟 Windows PowerShell 命令提示字元。
  
若要檢查 APP1 和 DC1 之間的名稱解析和網路通訊，請執行 **ping dc1.corp.contoso.com** 命令，並檢查有四個回覆。
  
接下來在 Windows PowerShell 命令提示字元使用以下命令將 APP1 虛擬機器加入 CORP 網域。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

請注意，您必須在執行 **Add-Computer** 命令之後，提供 CORP\\User1 網域帳戶認證。
  
APP1 重新啟動之後，使用 CORP\\User1 帳戶連線至 APP1，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。
  
接下來，在 APP1 上的 Windows PowerShell 命令提示字元中使用此命令讓 APP1 成為 Web 伺服器。
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

接下來，使用這些 PowerShell 命令在 APP1 上的資料夾內建立共用資料夾及文字檔。
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

這是您目前的組態。
  
![Azure 中具有 APP1 虛擬機器的基底組態的步驟 3](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a>步驟 4：設定 CLIENT1

在這個步驟中，建立及設定 CLIENT1，其可在 Contoso 內部網路上作為一般的膝上型電腦、平板電腦或桌上型電腦。

> [!NOTE]  
> 下列命令集可建立執行 Windows Server 2016 資料中心的 CLIENT1，其適用於所有類型的 Azure 訂閱。如果您有以 Visual Studio 為基礎的 Azure 訂閱，則可以使用 [Azure 入口網站](https://portal.azure.com)建立執行 Windows 10 的 CLIENT1。 
  

> [!NOTE]
> 在執行下列命令區塊之前，請確定您所選擇的 Azure 區域 (位置) 支援 Azure 虛擬機器大小，預設設為 Standard_A1。按一下[這裡](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines)以查看 Azure 虛擬機器大小和位置的最新資訊。
  
若要建立 CLIENT1 的 Azure 虛擬機器，請填入您的資源群組，並在本機電腦上的 Azure PowerShell 命令提示字元執行這些命令。
  
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

接下來，使用 CLIENT1 本機系統管理員帳戶名稱和密碼連線到 CLIENT1 虛擬機器，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。
  
若要檢查 CLIENT1 和 DC1 之間的名稱解析和網路通訊，請在 Windows PowerShell 命令提示字元執行 **ping dc1.corp.contoso.com** 命令，並檢查有四個回覆。
  
接下來在 Windows PowerShell 命令提示字元使用以下命令將 CLIENT1 虛擬機器加入 CORP 網域。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

請注意，您必須在執行 **Add-Computer** 命令之後，提供 CORP\\User1 網域帳戶認證。
  
CLIENT1 重新啟動之後，使用 CORP\\User1 帳戶名稱和密碼連線至 CLIENT1，然後開啟系統管理員層級 Windows PowerShell 命令提示字元。
  
接下來，檢查您可以從 CLIENT1 存取 APP1 上的 Web 及檔案共用資源。
  
1. 在 [伺服器管理員] 的樹狀窗格中，按一下 [本機伺服器]****。
    
2. 在 [CLIENT1 的屬性]**** 中，按一下 [IE 增強式安全性設定]**** 旁邊的 [開啟]****。
    
3. 在 [Internet Explorer 增強式安全性設定]**** 中，為 [管理員]**** 和 [使用者]**** 按一下 [關閉]****，然後按 [確定]****。
    
4. 從 [開始] 畫面，按一下 [Internet Explorer]****，然後按 [確定]****。
    
5. 在網址列中，輸入 **http:\//app1.corp.contoso.com/**，然後按 ENTER 鍵。您應該會看到 APP1 的預設網際網路資訊服務網頁。
    
6. 在桌面工作列中，按一下 [檔案總管] 圖示。
    
7. 在網址列中，輸入 **\\\\app1\\檔案**，然後按 ENTER 鍵。您應該會看到資料夾視窗中的檔案共用資料夾內容。
    
8. 在 [檔案]**** 共用資料夾視窗中，按兩下 **Example.txt** 檔案。您應該會看到 Example.txt 檔案的內容。
    
9. 關閉 **example.txt - 記事本**以及 [檔案]**** 共用資料夾視窗。
    
這是您的最終組態。
  
![Azure 中具有 CLIENT1 虛擬機器的基底組態的步驟 4](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
Azure 中的基底組態已準備好進行應用程式開發與測試，或建立其他測試環境。 
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
<a name="mincost"> </a>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>降低 Azure 中測試環境虛擬機器的成本

若要降低執行測試環境虛擬機器的成本，您可以執行下列其中一項動作：
  
- 建立測試環境並盡快執行所需測試和示範。完成後，刪除測試環境的資源群組。
    
- 關閉測試環境的虛擬機器，進入解除配置的狀態。
    
若要使用 Azure PowerShell 關閉虛擬機器，請填寫資源群組名稱並執行這些命令。
  
```
$rgName="<your resource group name>"
Stop-AzVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "DC1" -Force
```

為了確保從已停止 (已解除配置) 的狀態啟動所有虛擬機器時，您的虛擬機器能正常運作，您應依照下列順序啟動：
  
1. DC1
2. APP1
3. CLIENT1
    
若要使用 Azure PowerShell 依序啟動虛擬機器，請填寫資源群組名稱並執行這些命令。
  
```
$rgName="<your resource group name>"
Start-AzVM -ResourceGroupName $rgName -Name "DC1"
Start-AzVM -ResourceGroupName $rgName -Name "APP1"
Start-AzVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>另請參閱

- [Office 365 開發/測試環境](office-365-dev-test-environment.md)
- [Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
- [Office 365 開發人員/測試環境的雲端 App 安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [適用於 Office 365 開發/測試環境的進階威脅防護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)
