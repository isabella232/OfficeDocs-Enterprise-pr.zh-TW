---
title: "基本組態開發/測試環境"
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
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: "摘要： 建立簡化的內部網路為 Microsoft Azure 中的開發人員/測試環境。"
ms.openlocfilehash: f61490ea9ee9ee23df2b2fd13df1097d183a8de7
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="base-configuration-devtest-environment"></a>基本組態開發/測試環境

 **摘要：**為 Microsoft Azure 中的開發人員/測試環境中建立簡化的內部網路。
  
本文提供在 Azure 中建立下列的基本設定開發/測試環境的逐步指示：
  
**圖 1： 基本設定開發/測試環境**

![Azure 中具有 CLIENT1 虛擬機器的基底組態的階段 4](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
圖 1 中的基本設定開發/測試環境所組成的僅限雲端 Azure 虛擬網路中名為會模擬簡體中文、 私人的內部網路連線至網際網路的 TestLab 依舊套用子網路。包含三個 Azure 的虛擬機器執行 Windows Server 2016：
  
- DC1 設定為內部網路網域控制站和網域名稱系統 (DNS) 伺服器
    
- 在 APP1 設定為一般應用程式與網頁伺服器
    
- CLIENT1 做為內部網路用戶端
    
此設定可讓 DC1、 APP1、 CLIENT1 及其他依舊套用子網路的電腦設為： 
  
- 連線至網際網路安裝更新，存取網際網路資源即時，並參與公用雲端技術，例如 Microsoft Office 365 與其他 Azure 的服務。
    
- 從遠端管理使用遠端桌面連線從您連線至網際網路或您組織的網路的電腦。
    
您可以使用所產生的測試環境：
  
- 適用於應用程式開發及測試。
    
- 為包含其他虛擬機器、 Azure 服務或 Office 365 和企業安全性 + 行動性等其他 Microsoft cloud 方案自行設計延伸的測試環境的初始設定。
    
有四個階段來設定 Azure 中的基本設定測試環境：
  
1. 建立虛擬網路。
    
2. 設定 DC1。
    
3. 設定 APP1。
    
4. 設定 CLIENT1。
    
如果您已經沒有 Azure 訂閱，您可以註冊在[嘗試 Azure](https://azure.microsoft.com/pricing/free-trial/)免費試用版。如果您有 MSDN 或 Visual Studio 訂閱，請參閱[Visual Studio 訂閱者的每月 Azure 信用](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)。
  
> [!NOTE]
> 當他們正在執行時在 Azure 虛擬機器時可能會形成持續進行的財務成本。此成本是針對在免費試用版、 MSDN 訂閱計費或付費訂閱。Azure 虛擬機器中執行的成本的相關資訊，請參閱[虛擬機器定價的詳細資訊](https://azure.microsoft.com/pricing/details/virtual-machines/)與[Azure 定價計算機](https://azure.microsoft.com/pricing/calculator/)。若要保留成本向下，請參閱[Azure 中的測試環境虛擬機器時的成本最小化](base-configuration-dev-test-environment.md#mincost)。 
  
![Microsoft 雲端中的測試實驗室指南](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> 按一下[此處](http://aka.ms/catlgstack)的視覺對應至一個 Microsoft Cloud 測試實驗室指南堆疊中所有的文章。
  
## <a name="phase-1-create-the-virtual-network"></a>階段 1： 建立虛擬網路

首先，啟動 Azure PowerShell 提示字元處。
  
> [!NOTE]
> 下列的命令會使用 Azure PowerShell 的最新版本。請參閱[開始使用 Azure PowerShell cmdlet](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)。 
  
下列命令以 Azure 帳戶登入。
  
```
Login-AzureRMAccount
```

> [!TIP]
> 按一下[這裡](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d)以取得包含在本文中的所有 PowerShell 命令的文字檔案。
  
使用下列命令取得訂用帳戶名稱。
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

設定 Azure 訂用帳戶。以正確的名稱取代括號中的所有項目 (包括 < 和 > 字元)。
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

接下來，建立新資源群組的基本設定測試實驗室。若要判斷唯一資源群組名稱，請使用此命令列出您現有的資源群組。
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

使用這些命令建立新的資源群組。括住，包括所有內容取代為 < 和 > 字元，以正確的名稱。
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

接下來，您建立會裝載依舊套用子網路的基本組態及保護網路安全性群組與 TestLab 虛擬網路。
  
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

這是您目前的設定。
  
![Azure 中具有虛擬網路與子網路的基底組態的階段 1](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a>階段 2： 設定 DC1

在此階段中，我們會建立 DC1 虛擬機器及將它設定為 corp.contoso.com Windows Server Active Directory (AD) 網域的網域控制站和虛擬機器的 TestLab 虛擬網路的 DNS 伺服器。
  
若要建立 DC1 Azure 虛擬機器，資源群組的名稱中填滿及本機電腦上執行這些命令在 Azure PowerShell 命令提示字元。
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

將會提示您的使用者名稱與 DC1 上的本機系統管理員帳戶的密碼。使用強式密碼與安全的位置記錄的名稱和密碼。
  
接下來，連線至 DC1 虛擬機器。
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a>連線至 DC1 使用本機系統管理員帳戶認證

1. 在[Azure 的入口網站](https://portal.azure.com)中，按一下 [**資源群組 >** <the name of your new resource group> **> DC1 > Connect**。
    
2. 開啟已下載的 DC1.rdp 檔案並再按一下 [**連線**。
    
3. 指定 DC1 本機系統管理員帳戶名稱：
    
  - Windows 7：
    
    在 [ **Windows 安全性**] 對話方塊中，按一下 [**使用另一個帳戶**。在 [**使用者名稱**] 中，輸入**DC1\\**[本機系統管理員帳戶名稱]。
    
  - Windows 8 或 Windows 10：
    
    在 [ **Windows 安全性**] 對話方塊中，按一下 [**更多選項**，並按一下 [**使用不同的帳戶**。在 [**使用者名稱**] 中，輸入**DC1\\**[本機系統管理員帳戶名稱]。
    
4. 在 [**密碼**] 輸入本機系統管理員帳戶的密碼，然後按一下 [**確定]**。
    
5. 出現提示時，按一下 [**是**]。
    
下一步] 新增額外的資料磁碟作為新的磁碟區使用的磁碟機代號 LATER 搭配此命令在 DC1 管理員層級 Windows PowerShell 命令提示字元。
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

下一步] 設定為網域控制站和 corp.contoso.com 網域的 DNS 伺服器的 DC1。在系統管理員層級 Windows PowerShell 命令提示字元中執行這些命令。
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

您必須指定安全模式的系統管理員密碼。此密碼儲存在安全的位置。
  
請注意，這些命令可能需要數分鐘才能完成。
  
DC1 重新啟動後，重新連線至 DC1 虛擬機器。
  
### <a name="connect-to-dc1-using-domain-credentials"></a>連線至 DC1 使用網域認證

1. 在[Azure 的入口網站](https://portal.azure.com)中，按一下 [**資源群組 >** <your resource group name> **> DC1 > Connect**。
    
2. 執行 DC1.rdp 檔案是下載並再按一下 [**連線**。
    
3. 在 [ **Windows 安全性**] 按一下 [**使用另一個帳戶**。在 [**使用者名稱**] 中，輸入**CORP\\**[本機系統管理員帳戶名稱]。
    
4. 在 [**密碼**] 輸入本機系統管理員帳戶的密碼，然後按一下 [**確定]**。
    
5. 出現提示時，按一下 [**是**]。
    
接下來，登入 CORP 網域的成員電腦時將使用的 Active Directory 中建立使用者帳戶。在系統管理員層級 Windows PowerShell 命令提示字元中執行此命令。
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

請注意此命令會提示您提供 User1 帳戶密碼。此帳戶會用於所有 CORP 網域成員電腦的遠端桌面連線，因為選擇強式密碼。使用者 1 將帳戶密碼記錄並儲存在安全的位置。
  
接下來，設定新 User1 帳戶做為企業系統管理員。系統管理員層級 Windows PowerShell 命令提示字元中執行此命令。
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

關閉 DC1 遠端桌面工作階段，然後再重新連線使用 CORP\\User1 帳戶。
  
下一步] 以允許 Ping 工具的流量，請在系統管理員層級 Windows PowerShell 命令提示字元下執行此命令。
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

這是您目前的設定。
  
![Azure 中具有 DC1 虛擬機器的基底組態的階段 2](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a>階段 3： 設定 APP1

在 APP1 提供網頁伺服器和共用服務的檔案。
  
若要建立 APP1 Azure 虛擬機器，您資源群組、 Azure 位置及儲存的帳戶名稱的名稱中填滿及本機電腦上執行這些命令在 Azure PowerShell 命令提示字元。
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

下一步] 連線至 APP1 虛擬機器使用 APP1 本機系統管理員帳戶名稱和密碼，然後再開啟 [Windows PowerShell 命令提示字元。
  
若要檢查 APP1 與 DC1 之間的名稱解析和網路通訊，請執行**ping dc1.corp.contoso.com**命令並確認有四個回覆。
  
接下來，這些命令在 Windows PowerShell 提示 CORP 網域加入 APP1 虛擬機器。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

請注意您必須提供 CORP\\執行**新增電腦**命令後的 User1 網域帳戶認證。
  
在 APP1 重新啟動後，連線至其使用 CORP\\User1 帳戶並再開啟 [系統管理員層級 Windows PowerShell 命令提示字元。
  
接下來，請 APP1 網頁伺服器使用此命令在 APP1 上的 Windows PowerShell 命令提示字元。
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

接下來，建立共用的資料夾和資料夾內的文字檔案在 APP1 上和下列 PowerShell 命令。
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

這是您目前的設定。
  
![Azure 中具有 APP1 虛擬機器的基底組態的階段 3](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a>階段 4： 設定 CLIENT1

CLIENT1 做為一般筆記型電腦、 平板電腦或桌上型電腦 contoso 公司內部網路上。
  
> [!NOTE]
> 下列命令一組會建立 CLIENT1 執行 Windows Server 2016 Datacenter，可藉的 Azure 訂閱的所有類型。如果您有 Visual Studio 為基礎的 Azure 訂閱，您可以建立 CLIENT1 執行 Windows 10、 Windows 8 或 Windows 7 與[Azure 入口網站](https://portal.azure.com)。 
  
若要建立 CLIENT1 Azure 虛擬機器，填入您的資源群組、 Azure 位置及儲存的帳戶名稱的名稱中與本機電腦上執行這些命令在 Azure PowerShell 命令提示字元。
  
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
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

接下來，連線至 CLIENT1 虛擬機器使用 CLIENT1 本機系統管理員帳戶名稱和密碼，然後再開啟 [系統管理員層級 Windows PowerShell 命令提示字元。
  
若要檢查 CLIENT1 與 DC1 之間的名稱解析和網路通訊，請在 Windows PowerShell 命令提示字元中執行**ping dc1.corp.contoso.com**命令並確認有四個回覆。
  
接下來，這些命令在 Windows PowerShell 提示 CORP 網域加入 CLIENT1 虛擬機器。
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

您必須提供您公司的附註\\執行**新增電腦**命令後的 User1 網域帳戶認證。
  
CLIENT1 重新啟動後，連線至其使用 CORP\\User1 帳戶名稱和密碼，然後再開啟 [以系統管理員層級 Windows PowerShell 命令提示字元。
  
下一步] 確認您可以從 CLIENT1 存取在 APP1 上的網頁伺服器和檔案共用資源。
  
### <a name="verify-client-access-to-app1"></a>確認 app1 的用戶端存取

1. 在伺服器管理員] 的樹狀目錄窗格中，按一下 [**本機伺服器**。
    
2. **CLIENT1 屬性**] 中按一下 [**在**旁**IE 增強式安全性設定**]。
    
3. 在**Internet Explorer 增強式安全性設定**中，**系統管理員**和**使用者**]，按一下 [**關閉**並再按一下 [**確定]**。
    
4. 從 [開始] 畫面中，按一下 [ **Internet Explorer**，並再按一下 [**確定]**。
    
5. 在 [位址] 列中輸入**http://app1.corp.contoso.com/**，並按 ENTER。您應該會看到 [預設網際網路資訊服務 web] 頁面上的 APP1。
    
6. 從桌面工作列上，按一下 [檔案總管] 圖示。
    
7. 在 [位址] 列中輸入**\\ \\app1\\檔案**，然後按 ENTER 鍵。您應該會看到與檔案共用資料夾的內容在資料夾視窗。
    
8. 在 [**檔案**共用的資料夾] 視窗中，按兩下 [ **Example.txt**檔案。您應該會看到 Example.txt 檔案的內容。
    
9. 關閉**example.txt-[記事本]**和**檔案**共用資料夾視窗。
    
這是您最終的設定。
  
![Azure 中具有 CLIENT1 虛擬機器的基底組態的階段 4](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
您在 Azure 中的基本設定現在是好或建立其他測試環境的應用程式開發和測試。 
  
> [!TIP]
> 按一下[這裡](http://aka.ms/catlgstack)，可查看 One Microsoft Cloud 測試實驗室指南堆疊中文件的所有視覺對應。
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a>最小化的 Azure 中的測試環境虛擬機器時的成本
<a name="mincost"> </a>

若要降低執行測試環境的虛擬機器時的成本，您可以執行下列其中一項動作：
  
- 建立測試環境並儘速執行您需要測試及示範。完成後，刪除測試環境的 [資源] 群組。
    
- 關閉測試環境虛擬機器進入解除配置的狀態。
    
若要關閉與 PowerShell 的 windows Azure 虛擬機器時，請填入資源群組名稱並執行下列命令。
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

若要確保虛擬機器且運作正常從已停止 (Deallocated) 狀態時啟動所有這些，您應該依下列順序啟動它們：
  
1. DC1
    
2. 在 APP1
    
3. CLIENT1
    
若要啟動順序與 PowerShell 的 windows Azure 虛擬機器，填入資源群組名稱並執行下列命令。
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a>請參閱

<a name="mincost"> </a>

[Office 365 開發/測試環境](office-365-dev-test-environment.md)
  
[Office 365 開發/測試環境的 DirSync](dirsync-for-your-office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的雲端應用程式安全性](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[Office 365 開發人員/測試環境的進階威脅保護](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[雲端採用和混合式解決方案](cloud-adoption-and-hybrid-solutions.md)


