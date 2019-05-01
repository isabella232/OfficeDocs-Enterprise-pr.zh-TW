---
title: EDiscovery 的自動化檔案收集
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 摘要： 了解如何自動化檔案收集從使用者電腦 ediscovery （英文）。
ms.openlocfilehash: bfbe3b9218ed81727f2cc6ad9fabcb02e76d486b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490785"
---
# <a name="automate-file-collection-for-ediscovery"></a>EDiscovery 的自動化檔案收集

 **摘要：** 了解如何自動化檔案收集從使用者電腦 ediscovery （英文）。
  
所有公司都面臨潛在訴訟或其他類型的法律巨集指令。 雖然法務部門可以使用，以減少的曝光度，訴訟資料暫留是商務生命週期的事實。 當公司朝法律行動時，它們是必要的透過法律探索，以提供巷以及對手顧問所有相關的記錄資料的程序。 
  
eDiscovery 是依據公司清查、 搜尋、 識別、 保留、 篩選和提供相關的記錄資料存在的電子表單中的程序。 SharePoint 2013、 Exchange Server 2013、 Lync Server 2013、 SharePoint Online 和 Exchange Online 可以保留大量記錄的內容。 根據版本，這些產品可能支援 eDiscovery 及就地保留概觀 (Lync 透過 Exchange 伺服器)，以便輕鬆編製索引，法律 teams 識別、 按住並篩選的特定案例的最相關內容。
  
許多文件會儲存在使用者 (Custodians) 上本機電腦，而不是以在集中式位置。 這使得基本上是針對 SharePoint 2013 搜尋，並無法搜尋，如果它不能包含 eDiscovery。 這個解決方案示範如何使用登入指令檔，System Center 協調 2012 R2 和 Exchange Server 的 Windows PowerShell 自動化的識別資料及記錄資料從使用者電腦的集合。
  
## <a name="what-this-solution-does"></a>此解決方案的用途

此解決方案會使用通用的安全性，群組原則] 和 Windows PowerShell 指令碼來尋找、 清查，並從使用者本機電腦收集內容和 Outlook 個人存放區 (PST) 檔案，隱藏的檔案共用。 從該處的 PST 檔案可以匯入 Exchange Server 2013 或 Exchange Online。 所有檔案會接著都移在 Microsoft Azure 中使用 System Center 協調 2012 R2 runbook 到另一個檔案共用長期儲存與 SharePoint 2013 所編製索引。 然後您使用 eDiscovery center 在內部部署 SharePoint 2013 部署或 SharePoint Online 中一樣定期執行 eDiscovery。 
  
> [!IMPORTANT]
> 此解決方案使用 robocopy 檔案複製到集中式的檔案共用的 custodian 的電腦。 因為 robocopy 不會複製檔案開啟或鎖定，任何檔案，包括 custodian 已開啟的 PST 檔案將不會收集。 您必須以手動方式收集它們。 此解決方案並提供您明確地識別它不能複製檔案的清單與每個檔案的完整路徑。 
  
下圖引導您逐步完成所有步驟和解決方案的元素。
  
![自動化檔案收集解決方案的概觀](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|圖例 * * *||
|:-----|:-----|
|![洋紅色圖說文字 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|建立群組原則物件 (GPO)，並將它與集合登入指令檔。  <br/> |
|![洋紅色圖說文字 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| 設定只對 Custodians 群組套用到 GPO 的 GPO 安全性篩選。 <br/> |
|![洋紅色圖說文字 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Custodian 登入並 GPO 執行時，呼叫集合登入指令檔。  <br/> |
|![洋紅色圖說文字 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|集合登入指令檔清查 Custodians 電腦，搜尋想要的檔案並錄製其位置上的所有本機連接磁碟機。  <br/> |
|![洋紅色圖說文字 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|集合登入指令碼會複製清查的檔案預備伺服器上的隱藏的檔案共用。  <br/> |
|![洋紅色圖說文字 6](media/99589726-0c7e-406b-a276-44301a135768.png)| （選項的）以手動方式執行 PST 匯入指令碼，以收集的 PST 檔案匯入 Exchange Server 2013。 <br/> |
|![洋紅色圖說文字 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|（選項 B）使用 Office 365 匯入工具及程序，匯入的收集的 PST 檔案 Exchange Online。  <br/> |
|![洋紅色圖說文字 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|將所有收集到的檔案移至長期儲存與 MoveToColdStorage System Center 協調 2012 R2 runbook Azure 檔案共用。 <br/> |
|![洋紅色圖說文字 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|索引中與 SharePoint 2013 的冷儲存檔案共用的檔案。  <br/> |
|![洋紅色圖說文字 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|執行 eDiscovery 在冷儲存區和內部部署 Exchange Server 2013 中的內容。  <br/> |
|![洋紅色圖說文字 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|在 Office 365 中的內容上執行 eDiscovery。  <br/> |
   
## <a name="prerequisites"></a>必要條件

此解決方案的組態最需要許多項目，，其中您可能有，並設定如果您的想法有關 eDiscovery。 針對您不一定或該地需要特定設定，我們將提供您具有連結的項目中，您需要組建出您的基底組態。 設定本身的解決方案之前，您必須具有就地基底組態。
  
### <a name="base-configuration"></a>基本設定

|**元素**|**連結**|
|:-----|:-----|
|Active Directory 網域服務 (AD DS) 網域  <br/> ||
|從您的內部網路的網際網路連線能力  <br/> ||
|若要支援 SharePoint 2013 和 System Center 協調 2012 R2 的 SQL Server 2012  <br/> |[部署 System Center 協調-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| 內部部署或 Azure 根據 SharePoint 2013 ediscovery （英文） （所需的選項 A） <br/> ||
|內部檔案共用伺服器上的臨時  <br/> ||
|內部部署 Exchange Server 2013 的選項 PST 匯入  <br/> |CU5 (15.913.22) 位於[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)。  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[部署 System Center 協調-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 （方案 E3） 與 Exchange Online 和 SharePoint Online （所需的選項 B）  <br/> |若要註冊 Office 365 E3 訂用帳戶，請參閱 < <b0>Office 365 E3 訂閱</b0>。  <br/> |
|使用虛擬機器的 azure 訂用帳戶  <br/> |若要註冊 Azure，請參閱[Windows Azure 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|您的內部網路與您 Azure 訂用帳戶之間的 VPN 連線  <br/> |若要設定您 Azure 訂用帳戶和內部部署網路間的 VPN 通道，請參閱[連線到 Microsoft Azure 虛擬網路的內部網路](https://go.microsoft.com/fwlink/p/?LinkId=613507)。  <br/> |
|若要搜尋 SharePoint 和 Exchange Server 2013 和 Lync Server 2013 （選用） 設定 SharePoint 2013 的 eDiscovery  <br/> |若要以這種方式設定電子文件探索，請參閱 <<c0>在 SharePoint Server 2013 中的設定 eDiscovery和<b1>測試實驗室指南： Exchange、 Lync、 SharePoint 及 Windows 檔案共用測試實驗室中設定 eDiscovery</b1>。  <br/> |
|在 SharePoint Online 和 Exchange Online 的 Office 365 中的 eDiscovery  <br/> |若要在 Office 365 中設定電子文件探索，請參閱 <<c0>設定 SharePoint Online 中的 eDiscovery 中心。  <br/> |
   
## <a name="configure-the-environment"></a>設定環境

現在，您有基底組態中的位置，您可以設定解決方案本身向前移動。 
  
### <a name="staging-file-share"></a>臨時檔案共用

1. 在內部部署網域中，建立名為 Custodians 通用安全性群組。
    
2. 建立的檔案，從 Custodians 電腦收集的隱藏的檔案共用。 這應該是在內部部署伺服器上。 比方說，在名為臨時伺服器上，建立名為的情況下 $ 檔案共用。 **$** ，才能將此位址設隱藏的共用。
    
3. 設定下列共用權限：
    
  - Custodians： 變更，請閱讀
    
  - 系統管理員：完全控制
    
  - Exchange 受信任的子系統： 變更，請閱讀
    
4. 開啟 [**安全性**] 索引標籤，新增 [Custodians] 群組中，按一下 [**進階**]。 設定 Custodians 群組的下列權限：
    
  - **類型： 拒絕**
    
  - **適用於： 這個資料夾、 子資料夾及檔案**
    
5. 按一下 [**進階權限**，然後選取下列項目：
    
  - **讀取屬性**
    
  - **閱讀延伸的屬性**
    
  - **讀取權限**
    
6. 測試存取的情況下 $ 檔案共用，執行下列動作：
    
1. 將使用者新增至 Custodians 群組。
    
2. 位置的情況下 $ 資料夾中的檔案。
    
3. 為使用者、 瀏覽至預備伺服器，例如瀏覽至\\\\分段執行若要查看哪些共用可用的共用。 您不應該會看到所列的**情況下 $** 共用。
    
4. 手動輸入瀏覽器的情況下 $ 共用的完整路徑。 這應該會開啟的情況下 $ 共用。
    
5. 嘗試開啟先前放在共用的檔案。 這應該會失敗。
    
### <a name="logon-script"></a>登入指令檔

1. 複製並貼入 [記事本] 中的這個 Windows PowerShell 指令碼：
    
  ```
  # Automated file collection script
# Substantial error processing should be added for robust execution and troubleshooting opportunities
# All commented out write-hosts are for debugging only and are commented out for regular execution

# Functions 

Function CreateCaseFolder() {

#Check to see if case folder already exists
$CaseFolderCheck = Test-Path $CaseLocation

try {

    if (!$CaseFolderCheck) {
    # Case folder doesn't exist.  Create the case folder and the log file location
    # Write-Host -ForegroundColor Cyan "Creating Case Folder $CaseLocation"
    New-Item "$CaseLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case Log Folder $CaseLogLocation"
    New-Item "$CaseLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
    # Write-Host -ForegroundColor Cyan "Creating Case PST folder $CasePSTLocation"
    New-Item "$CasePSTLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue

    }
    else {

    # do nothing since the target case folder already exists

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

Function CopyFileToCaseFolder($SourcePath, $TargetPath, $FileName) {
    
    # Check to see if the file already exists
    $TargetFileCheck = Test-Path $TargetPath\$FileName

try {

    if (!$TargetFileCheck) {
    # Copy the file to the case folder
    Write-Host $SourcePath $TargetPath $FileName
    robocopy "$SourcePath" "$TargetPath" "$FileName" /COPY:DATSO /TEE /LOG+:$LoggingFile /R:10 /W:10 | Out-Null

    }
    else {

    # do nothing since file is already in the target case folder

    }
}
catch [System.Exception] {

    # To do..
    # to log to an exception or log file
    
    }
}

# Global variable initializations

# Error log
$Loggederrors=@()

# The array to contain the file types we collect
$FileTypes = @("*.doc","*.docx","*.pst","*.txt")

# We'll set the case number to be a combination of the date and user name
# For example, a case for John Doe on Dec 14, 2014 at 2:38pm would be:
# 201412141438_jdoe
$CaseNo = get-date -Format yyyyMMddHHmm
$CaseNo = $CaseNo + "_" + [Environment]::UserName

# Target location to copy case files
$CaseRootLocation = "\\staging\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\" + $CaseNo + "\_Log"
$CasePSTLocation = $CaseRootLocation + "\" + $CaseNo + "\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\$_.xml -Force
    # Needs try catch and logged collection error file
}

# Now let's read each file and copy any files we need to the case folder
# We will also copy these XMLs to the case log files folder as we go along
# We only want to process XML files, just in case something else got in there as the script ran
$CaseDriveFiles = Get-ChildItem $TemporaryLogLocation -Filter '*.xml'
$CaseDriveFiles | foreach {
    # Copy the XML file to the case log location
    CopyFileToCaseFolder $_.Directory.FullName $CaseLogLocation $_.Name
    $DriveFile = $_.FullName
    # Write-Host -ForegroundColor Cyan "Copying Files specified in the XML file: $DriveFile"
    $CurrentDriveFile = Import-Clixml $DriveFile
    $CurrentDriveFile | foreach {
        # write-host $_.FullName
        # if it's a PST, add to the PSTs folder. otherwise add it to case folder
        if ($_.Extension -match '.PST')
        {
            CopyFileToCaseFolder $_.Directory.FullName $CasePSTLocation $_.Name
            write-host "this is a PST"
        }
        else
        {
            CopyFileToCaseFolder $_.Directory.FullName $CaseLocation $_.Name
        }
    }
}

# Now delete the temporary log file
Remove-Item $TemporaryLogLocation -Recurse 

Write-Host -ForegroundColor Cyan "Finished."

  ```

2. 將上面的指令碼儲存為 CollectionScript.ps1 中的位置並讓您輕鬆地尋找，例如 c:\\AFCScripts。
    
3. 在 [記事本] 使用 [移至] 功能。 視需要請進行下列變更:
    
|**行號**|**您需要變更**|**所需/選用**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes**變數。 包含您想要的指令碼來清查並收集陣列變數中的所有檔案類型副檔名。 <br/> |選用  <br/> |
|76 及 77  <br/> |變更的方式 **$CaseNo**變數是內建符合您的需求。 指令碼會擷取目前的日期和時間，並附加至它的使用者名稱。 <br/> |選用  <br/> |
|80  <br/> |**$CaseRootLocation**變數必須設定為臨時伺服器集合檔案共用，例如**\\\\臨時\\情況下 $**。 <br/> |必要  <br/> |
   
4. 將 CollectionScript.ps1 檔案放置在網域控制站的 Netlogon 檔案共用。 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>設定 GPO 的登入指令碼和 Custodians 群組

1. 下列主題，<b0>使用啟動、 關閉、 登入和登出指令碼在群組原則中</b0>的 < 如何指派使用者登入指令檔 > 一節，以設定 Custodians 群組的登入指令碼。
    
2. 移除已驗證的使用者**安全性篩選**，並新增 Custodians 群組。
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST 匯入選項 A、 Exchange Server 2013 的指令碼

1.  複製並貼入 [記事本] 中的下列 Windows PowerShell 指令碼：
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\PSTImport.ps1 \\FileShare\PSTFiles jdoe

param ([String]$SourcePath,[String]$MailboxAlias)

# Folder identifier is the string we want to show in the mailbox that we import the PSTs to

$FolderIdentifier = "zzImportedPSTs_"

# Connect to Exchange remote powershell using the connection Uri below
# This would be the format http://<exchange server FQDN>/Powershell

$ConnectionUri = 'http://h10-exch/PowerShell'
$RemoteEx2013Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri $ConnectionUri -Authentication Kerberos
Import-PSSession $RemoteEx2013Session

# Get all the files in the source path

$AllFiles = Get-ChildItem $SourcePath -Recurse

# Go through each file and if it's a PST launch a mailbox import request for it

$AllFiles | ForEach-Object {
    If ($_.Extension -eq ".pst") {
        $ImportName = $MailboxAlias + "_" + $_.Name
        $FolderName = $FolderIdentifier + $_.Name
        New-MailboxImportRequest -Name $ImportName -Mailbox $MailboxAlias -FilePath $_.FullName -TargetRootFolder $FolderName
    }
}
  ```

2. 將指令碼儲存為 PSTImportScript.ps1 是讓您輕鬆地找到的位置。 範例和使用者更方便使用，請在您呼叫的臨時伺服器中建立資料夾\\\\臨時\\AFCScripts，並將其儲存到那里。
    
3. 在 [記事本]，使用 [移至] 功能，並視需要進行下列變更:
    
|**行號**|**您需要變更**|**所需/選用**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier**標記 Pst 匯入至信箱資料夾。 如有必要，請變更此選項。 <br/> |選用  <br/> |
|17   <br/> |**$ConnectionUri**必須設為您自己的伺服器。 <br/> > [!IMPORTANT]> 請確定您 **$ConnectionUri**點至 http 位置，而不是 https。 它不適用於 https:。          |必要  <br/> |
   
4. 確認 Exchange 受信任子系統帳戶具有讀取、 寫入和 Execute 權限\\\\臨時\\的情況下 $ 共用。
    
5. PST 匯入指令碼需要下列兩個輸入的參數：
    
  - **$SourcePath**要匯入，例如 PST 檔案的位置\\\\臨時\\情況下 $。
    
  - **$MailboxAlias**將會收到的匯入電子郵件項目目標信箱的別名。
    
6. 例如，如果您想要所有 PST 檔案匯都入從路徑\\Staging\Cases$ 到別名 eDiscoveryMailbox 信箱，您可執行類似的指令碼`\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox`。
    
### <a name="pst-import-option-b-for-exchange-online"></a>Exchange Online 的 PST 匯入選項 B

-  建立要放入的匯入的 PST 檔案的信箱結構。 如需有關如何在 Exchange Online 中建立使用者信箱的詳細資訊，請參閱 <<c0>Exchange Online 中建立使用者信箱。
    
### <a name="cold-storage"></a>冷儲存體

1. 建立檔案共用上 Azure 虛擬機器，其中所有收集到的檔案放置位置，例如， \\ \\AZFile1\\ContentColdStorage。
    
2. 至少授與預設內容存取帳戶的讀取權限的共用和所有子資料夾及檔案。 如需設定 SharePoint 2013 搜尋的詳細資訊，請參閱[建立及設定 SharePoint Server 2013 中的 Search service 應用程式](https://go.microsoft.com/fwlink/p/?LinkId=614940)。
    
3. 如果您預期匯入 PST 檔案從\\ \\AZFile1\\ContentColdStorage，授與 Exchange 受信任的子系統讀取、 寫入及執行共用的權限。
    
### <a name="orchestrator"></a>協調

1. 從 Microsoft 下載中心下載[MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 。
    
2. 開啟**Runbook 設計工具**，在 [**連線**] 窗格中，按一下您要匯入到 runbook 的資料夾。 按一下 [**動作**] 功能表，然後按一下 [**匯入**]。 **匯入**] 對話方塊隨即出現。
    
3. 在 [**檔案位置**] 方塊中，輸入您要匯入、 runbook 路徑和檔案名稱，或按一下以瀏覽至您要匯入檔案的省略符號 （ **...**）。 
    
4. 選取 [**匯入 runbook**和**匯入協調加密的資料**。 清除**計數器**、**排程**、**變數**、**電腦群組**、**匯入全域設定**，並**覆寫現有的全域設定**。
    
5. 按一下 [完成]****。
    
6. 編輯**MoveFilesToColdStorage** runbook，如下所示：
    
1. **移動檔案**活動的**來源檔案**將路徑設定為集合檔案共用，例如\\\\臨時\\情況下 $。 設定要冷儲存檔案的**目的資料夾**，例如共用 azure \\ \\AZFile1\\ContentColdStorage。 選取 [**建立具有唯一名稱的檔案**。
    
2. **刪除資料夾**活動-設定**路徑：** 集合檔案共用，例如\\\\臨時\\情況下 $\\*，然後選取 [**刪除所有檔案及子資料夾**。 
    
7. 部署使用的程序中[部署 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120) **MoveToColdStorage** runbook。
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>SharePoint 內部部署搜尋冷儲存體

1. 在 Azure 中冷儲存共用的 SharePoint 2013 伺服器陣列中建立新的內容來源，例如\\ \\AZFile1\\ContentColdStorage。 如需管理內容來源的詳細資訊，請參閱[新增、 編輯或刪除 SharePoint Server 2013 中的內容來源](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. 開始完整編目。 如需詳細資訊，請參閱[啟動、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目](https://go.microsoft.com/fwlink/p/?LinkId=615005)。
    
## <a name="using-the-solution"></a>使用解決方案

使用此解決方案中，假設您不想要將 PST 檔案匯入 Exchange Server 2013 和 Exchange Online 中有五個主要步驟。 本章節提供您的程序的全部。 您與解決方案的主要互動會處於執行下列動作：
  
1. 管理使用者 Custodians 群組的成員資格。
    
2. 檢閱登入指令碼所產生的記錄檔。 FileCopyErrors.log 列出所有未成功複製的檔案。 您必須先決定您想要與其做什麼
    
3. 管理 PST 匯入程序。
    
4. 將集合檔案移至冷儲存空間。
    
所有其他的步驟沒有特定此解決方案。 它們是您執行 SharePoint 2013 和 Office 365 和 Azure 中的標準系統管理工作。 有此解決方案不會提供您想要計算出根據貴公司的需求，例如任何指引的項目：
  
1. 追蹤您的 eDiscovery 案例，以及哪些 Custodians 相關聯這種情況。
    
2. 追蹤的一組檔案集合所使用的 eDiscovery 案例的關聯。
    
3. 協調匯入及移至冷儲存步驟的時間。
    
4. 管理 Azure 中使用的檔案空間。
    
5. 管理 Pst 匯入至信箱。
    
6. 備份與還原作業的內部部署的所有資料。
    
### <a name="custodian-management"></a>Custodian 管理

- 若要啟動的個別使用者是自動化的檔案收集程序，請將其新增至 Custodians 群組。 下次登入時，會執行指派給透過群組原則 Custodians 群組的登入指令碼。 
    
### <a name="monitor-collected-files-and-review-log-files"></a>監視收集到的檔案，然後檢閱記錄檔

1. 觀賞集合檔案共用，例如\\\\臨時\\情況下 $\\*，從使用者的 [集合] 資料夾。 資料夾的名稱會格式化像這樣： *yyyyMMddHHmm_UserName* 。
    
2. 集合完成時，開啟集合資料夾，並瀏覽至 [_Log] 資料夾。 在 [_Log] 資料夾中，您會看到下列訊息：
    
  - 每個使用者的電腦，例如**A.xml**， **C.xml**上的本機磁碟機的一個 XML 檔案。 這些檔案包含的庫存磁碟機之後，名為，它們會用於 robocopy 作業。
    
    > [!NOTE]
    > 集合指令碼只會在本身的指令碼中所定義的檔案類型的庫存檔案中建立項目。 它不會建立使用者的電腦上的每個檔案的詳細目錄項目。 
  
  - 一個記錄檔名為 FileCopyErrors.log 執行每個集合。 此檔案包含的檔案清單該 robocopy 找不到檔案集合的複本共用，例如， \\\\臨時\\情況下 $\\*。 您必須檢閱這，並決定這些未接的檔案需要採取的動作。 通常，其中必須以手動方式收集它們，如果您希望他們，或您可能會決定他們不需要，因此可以省略從集合。
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Exchange Server 2013 的 PST 匯入選項 A

1. 登入伺服器主控集合檔案共用，例如**臨時**，並開啟 Windows PowerShell。 如需有關啟動 Windows PowerShell 的詳細資訊，請參閱 <<c0>Windows 伺服器上啟動 Windows PowerShell。
    
2. 執行原則設為 Unrestricted。 型別`Set-ExecutionPolicy Unrestricted -Scope Process`到 Windows PowerShell]，然後按 Enter。
    
3. 執行 PSTImportScript.ps1 檔案，並提供的 **$SourcePath**和 **$MailboxAlias**參數。 如需有關執行 Windows PowerShell 指令碼的詳細資訊，請參閱 <<c0>執行指令碼。
    
4. 檢閱錯誤的輸出。
    
5. 您嘗試同名的 PST 檔案匯入至同一個信箱之前，您必須先移除信箱匯入要求。 執行下列命令，以執行這項作業： `Get-MailboxImportRequest | Remove-MailboxImportRequest`。 系統會提示您從佇列中移除每個個別的要求。 視回應。
    
### <a name="pst-import-option-b-for-exchange-online"></a>PST 匯入選項 B，Exchange Online

- 若要將收集的 PST 檔案放到 Exchange Online，請遵循到 Office 365 匯入檔案中的程序透過網路上傳] 區段中的[Office 365 匯入服務](https://go.microsoft.com/fwlink/p/?LinkId=614938)。
    
### <a name="move-to-cold-storage"></a>移至冷儲存體

1. 執行使用的程序中[執行 Runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123) **MoveToColdStorage** runbook。
    
2. 監看式 Azure 檔案共用您用於長期存放區，例如\\ \\AZFile1\\ContentColdStorage 和內部集合檔案共用，例如\\\\臨時\\情況下 $。 您應該會看到檔案和資料夾會出現在冷儲存檔案共用，而且會從集合檔案共用中消失。
    
### <a name="ediscovery"></a>eDiscovery

1. 允許完整編目排程，以執行的冷儲存檔案共用，或啟動編目。 如需有關啟動完整或累加編目的詳細資訊，請參閱 <<c0>啟動、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目。
    
2. 在 SharePoint 2013 中建立的 eDiscovery 案例，如果您使用選項的 PST 檔案匯入或 SharePoint Online 中建立 eDiscovery 案例，如果您使用選項 b。
    

