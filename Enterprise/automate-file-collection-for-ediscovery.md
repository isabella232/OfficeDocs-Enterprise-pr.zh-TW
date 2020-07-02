---
title: 自動化 eDiscovery 的檔收集
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
search.appverid:
- MET150
description: 摘要：瞭解如何從使用者電腦自動化檔收集以進行 eDiscovery。
ms.openlocfilehash: 83bd55ff786803cfcb3eec9430d72de30179d000
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997974"
---
# <a name="automate-file-collection-for-ediscovery"></a>自動化 eDiscovery 的檔收集

所有公司都面臨訴訟或其他類型法律行動的潛力。 雖然法律部門可用於減少這種風險，但訴訟是指的是生命週期的事實。 當公司面臨法律行動時，必須透過法律查詢的程式，向法院和相反的法律顧問提供所有相關的單印刷材料。 
  
eDiscovery 是指公司清查、搜尋、識別、保留、篩選，並提供電子形式的相關單印刷材料的程式。 SharePoint 2013、Exchange Server 2013、Lync Server 2013、SharePoint 線上和 Exchange Online 都可以保留大量的帶序內容。 視版本而定，這些產品可能支援 eDiscovery 和就地保留（Lync 透過 Exchange Server），讓法律團隊可更輕鬆地編制索引、識別、保留及篩選特定案例中最相關的內容。
  
許多檔都是儲存在使用者（保管人）本機電腦上，而不是集中位置。 這使 SharePoint 2013 無法進行搜尋，而且如果無法搜尋，便無法包含在 eDiscovery 中。 此解決方案顯示如何使用登入腳本（System Center Orchestrator 2012 R2 和 Windows PowerShell for Exchange Server），以自動化使用者電腦上的序材料識別及集合。
  
## <a name="what-this-solution-does"></a>此解決方案的用途

此解決方案使用通用安全性群組、群組原則和 Windows PowerShell 腳本，以在使用者本機電腦上尋找、清查及收集內容和 Outlook 個人存放區（PST）檔案至隱藏的檔案共用。 在此，PST 檔案可匯入至 Exchange Server 2013 或 Exchange Online。 然後，使用 System Center Orchestrator 2012 R2 runbook 將所有檔案移至 Microsoft Azure 中的另一個檔案共用，以進行長期儲存，並 SharePoint 2013 來編制索引。 然後，您可以使用內部部署 SharePoint 2013 部署中的 eDiscovery 中心，或是您定期執行 eDiscovery 的 SharePoint 線上。 
  
> [!IMPORTANT]
> 此解決方案使用 robocopy，將檔案從保管人的電腦複製到集中的檔案共用。 因為 robocopy 不會複製開啟或鎖定的檔案，所以不會收集保管人已開啟的任何檔案（包括 PST 檔案）。 您必須手動收集這些檔案。 此方案為您提供清單，明確識別出它無法複製的檔案，以及每個檔案的完整路徑。 
  
下列圖表會逐步引導您完成解決方案的所有步驟和元素。
  
![自動化檔案收集解決方案的概觀](media/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|圖例 * * * *||
|:-----|:-----|
|![洋紅色圖說文字 1](media/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|建立群組原則物件（GPO），並將它與集合登入腳本建立關聯。  <br/> |
|![洋紅色圖說文字 2](media/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| 設定 GPO 安全性篩選器，只將 GPO 套用至保管人群組。 <br/> |
|![洋紅色圖說文字 3](media/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|保管人會登入，然後 GPO 即會執行，呼叫集合登入腳本。  <br/> |
|![洋紅色圖說文字 4](media/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|集合登入腳本會清查保管人電腦上所有在本機上附加的磁片磁碟機、搜尋您想要的檔案，並記錄其位置。  <br/> |
|![洋紅色圖說文字 5](media/4bf8898c-44ad-4524-b983-70175804eb85.png)|集合登入腳本會將清查過的檔案複製到暫存伺服器上的隱藏檔案共用。  <br/> |
|![洋紅色圖說文字 6](media/99589726-0c7e-406b-a276-44301a135768.png)| （選項 A）手動執行 PST 匯入腳本，將收集的 PST 檔案匯入 Exchange Server 2013。 <br/> |
|![洋紅色圖說文字 7](media/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|（選項 B）使用 Microsoft 365 Import 工具和進程，將收集的 PST 檔案匯入 Exchange Online。  <br/> |
|![洋紅色圖說文字 8](media/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|使用 MoveToColdStorage System Center Orchestrator 2012 R2 runbook，將所有收集的檔案移至 Azure 檔案共用，以進行長期儲存體存放。 <br/> |
|![洋紅色圖說文字 9](media/b354642e-445e-4723-a84a-b41f7ac6e774.png)|使用 SharePoint 2013，為 cold 儲存檔共用中的檔案編制索引。  <br/> |
|![洋紅色圖說文字 10](media/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|對冷存放區中的內容及內部部署 Exchange Server 2013 執行 eDiscovery。  <br/> |
|![洋紅色圖說文字 11](media/e59ab403-2f19-497a-92a5-549846dded66.png)|在 Microsoft 365 的內容中執行 eDiscovery。  <br/> |
   
## <a name="prerequisites"></a>必要條件

設定此解決方案時，需要許多元素，多數是您在考慮 eDiscovery 時可能已就緒並加以設定。 針對您可能不需要特定設定的元素，我們會為您提供您要組建基本設定的連結。 您必須先就地設定基本設定，才能設定解決方案本身。
  
### <a name="base-configuration"></a>基本設定

|**元素**|**連結**|
|:-----|:-----|
|Active Directory 網域服務（AD DS）網域  <br/> ||
|從您的內部部署網路的網際網路連線能力  <br/> ||
|SQL Server 2012 可支援 SharePoint 2013 和 System Center Orchestrator 2012 R2  <br/> |[部署 System Center Orchestrator-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| 電子檔探索的內部部署或 Azure SharePoint 2013 （選項 A 所需） <br/> ||
|用於暫存的內部部署檔案共用伺服器  <br/> ||
|內部部署 Exchange Server 2013 用於選項 PST 匯入  <br/> |CU5 （15.913.22）可從[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)取得。  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[部署 System Center Orchestrator-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Microsoft 365 E3 搭配 Exchange Online 和 SharePoint 線上（選項 B 所需）  <br/> |若要註冊 Microsoft 365 E3 訂閱，請參閱[microsoft 365 e3 訂閱](https://www.microsoft.com/microsoft-365/enterprise-e3-business-software?activetab=pivot%3aoverviewtab)。  <br/> |
|使用虛擬機器的 Azure 訂閱  <br/> |若要註冊 Azure，請參閱[訂閱 Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|您的內部部署網路與您的 Azure 訂閱之間的 VPN 連線  <br/> |若要在您的 Azure 訂閱和內部部署網路之間設定 VPN 隧道，請參閱[Connect a 內部部署網路與 Microsoft Azure 虛擬網路](https://go.microsoft.com/fwlink/p/?LinkId=613507)。  <br/> |
|SharePoint 2013 eDiscovery 設定為跨 SharePoint 和 Exchange Server 2013 和選擇性的 Lync Server 2013 進行搜尋  <br/> |若要以這種方式設定 eDiscovery，請參閱[Configure ediscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508)及[Test Lab Guide： configure Ediscovery for a Exchange，Lync，SharePoint 與 Windows 檔案共用測試實驗室](https://go.microsoft.com/fwlink/p/?LinkId=393130)。  <br/> |
|Microsoft 365 中的 eDiscovery，供 SharePoint 線上和 Exchange Online  <br/> |若要在 Microsoft 365 中設定 eDiscovery，請參閱[在 SharePoint Online 中設定 Ediscovery 中心](https://go.microsoft.com/fwlink/p/?LinkId=613628)。  <br/> |
   
## <a name="configure-the-environment"></a>設定環境

現在，您已準備好基本設定，您可以向前移動以設定解決方案本身。 
  
### <a name="staging-file-share"></a>暫存檔共用

1. 在內部部署網域中，建立名為保管人的全域安全性群組。
    
2. 為從保管人電腦收集的檔案建立隱藏的檔案共用。 這應該是在內部部署伺服器上。 例如，在名為「暫存」的伺服器上，建立名為案例 $ 的檔案共用。 **$** 需要將此共用設為隱藏共用。
    
3. 設定下列共用許可權：
    
  - 保管人：變更、讀取
    
  - 系統管理員：完全控制
    
  - Exchange 受信任子系統：變更、讀取
    
4. 開啟 [**安全性**] 索引標籤，新增保管人群組，然後按一下 [**高級**]。 為保管人群組設定下列許可權：
    
  - **類型：拒絕**
    
  - **適用于：此資料夾、子資料夾及檔案**
    
5. 按一下 [**高級許可權**]，然後選取下列各項：
    
  - **讀取屬性**
    
  - **讀取擴充屬性**
    
  - **讀取權限**
    
6. 執行下列動作，以測試對事例 $ file 共用的存取：
    
1. 將使用者新增至保管人群組。
    
2. 將檔案放在案例 $ 資料夾中。
    
3. 以使用者的身分流覽至暫存伺服器，例如流覽至「暫存」 \\ \\ 共用，以查看有哪些共用可供使用。 您不應該看到列出的**案例 $** [共用]。
    
4. 手動輸入案例 $ 共用到瀏覽器的完整路徑。 這應該會開啟案例 $ 共用。
    
5. 嘗試開啟您先前放入共用中的檔案。 這應該會失敗。
    
### <a name="logon-script"></a>登入腳本

1. 在 [記事本] 中複製並貼上此 Windows PowerShell 腳本：
    
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

2. 在便於您尋找的位置（例如，C： AFCScripts）中，將上述腳本儲存為 CollectionScript.ps1 \\ 。
    
3. 使用 [記事本] 中的 [移至] 功能。 請視需要進行下列變更：
    
|**行號**|**您需要變更的專案**|**必要/選用**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes**變數。 在陣列變數中包含您想要腳本清查及收集的所有檔案類型副檔名。 <br/> |選用  <br/> |
|76和77  <br/> |變更建立 **$CaseNo**變數以符合您的需求的方式。 腳本會捕獲目前的日期和時間，並附加使用者名稱給它。 <br/> |選用  <br/> |
|80  <br/> |**$CaseRootLocation**變數必須設定為您的暫存伺服器集合檔案共用，例如， ** \\ \\ 暫存 \\ 案例 $**。 <br/> |必要  <br/> |
   
4. 將 CollectionScript.ps1 檔案放在網域控制站上的 Netlogon 檔案共用中。 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>為登入腳本和保管人群組設定 GPO

1. 遵循主題中的「如何指派使用者登入腳本」一節，[使用群組原則中](https://go.microsoft.com/fwlink/p/?LinkId=614844)的「啟動」、「關機」、「登入」和「登出」腳本，設定保管人群組的登入腳本。
    
2. 從**安全性篩選**移除已驗證的使用者，並新增保管人群組。
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>適用于 Exchange Server 2013 的 PST 匯入選項 A、腳本

1.  將下列 Windows PowerShell 腳本複製並貼到 [記事本] 中：
    
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
# This would be the format https://<exchange server FQDN>/Powershell

$ConnectionUri = 'https://h10-exch/PowerShell'
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

2. 在便於您尋找的位置中，將腳本儲存為 PSTImportScript.ps1。 例如，便於使用，請在暫存的伺服器上建立一個名為「暫存 AFCScripts」的資料夾 \\ \\ \\ ，並將它儲存到該資料夾。
    
3. 使用 [記事本] 中的 [移至] 功能，並視需要進行下列變更：
    
|**行號**|**您需要變更的專案**|**必要/選用**|
|:-----|:-----|:-----|
|12   <br/> |**$FolderIdentifier**標記 pst 所匯入的信箱資料夾。 視需要變更此。 <br/> |選用  <br/> |
|17   <br/> |**$ConnectionUri**必須設定為您自己的伺服器。 <br/> > [!IMPORTANT]> 請確定 **$ConnectionUri**指向 HTTP 位置，而不是 HTTPs。 它不會搭配使用 HTTPs：。          |必要  <br/> |
   
4. 確認 Exchange 受信任子系統帳戶具有「暫存案例」的「讀取」、「寫入」和「執行」許可權 \\ \\ \\ 。
    
5. PST 匯入腳本需要下列兩個輸入參數：
    
  - **$SourcePath**要匯入之 PST 檔案的位置，例如「 \\ \\ 暫存 \\ 案例」。
    
  - **$MailboxAlias**將接收匯入電子郵件專案之目標信箱的別名。
    
6. 例如，如果您想要將路徑 Staging\Cases $ 中的所有 PST 檔案匯入 \\ 至具有別名 eDiscoveryMailbox 的信箱中，您可以執行腳本，如下所示 `\\staging\AFCscripts\PSTImportScript.ps1 \\Staging\cases$ eDiscoveryMailbox` 。
    
### <a name="pst-import-option-b-for-exchange-online"></a>適用于 Exchange Online 的 PST 匯入選項 B

-  建立要將匯入 PST 檔案放入的信箱結構。 如需如何在 Exchange Online 中建立使用者信箱的詳細資訊，請參閱[在 Exchange online 中建立使用者](https://go.microsoft.com/fwlink/p/?LinkId=615118)信箱。
    
### <a name="cold-storage"></a>冷藏

1. 在 Azure 虛擬機器上建立檔案共用，將在其中放置所有收集的檔案，例如 \\ \\ AZFile1 \\ ContentColdStorage。
    
2. 授與預設的內容存取帳戶，至少要有共用及所有子資料夾及檔案的讀取權限。 如需設定 SharePoint 2013 搜尋的詳細資訊，請參閱[在 SharePoint Server 2013 中建立及設定 Search service 應用程式](https://go.microsoft.com/fwlink/p/?LinkId=614940)。
    
3. 如果您想要從 AZFile1 ContentColdStorage 匯入 PST 檔案 \\ \\ \\ ，請將 Exchange 受信任的子系統授與共享的「讀取」、「寫入」和「執行」許可權。
    
### <a name="orchestrator"></a>協調

1. 從 Microsoft 下載中心下載[MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 。
    
2. 開啟**Runbook Designer**，**在 [連線**] 窗格中，按一下您要匯入 Runbook 的資料夾。 按一下 [**動作**] 功能表，然後按一下 [匯**入**]。 [匯**入**] 對話方塊隨即顯示。
    
3. 在 [檔案**位置**] 方塊中，輸入您要匯入之 runbook 的路徑和檔案名，或按一下省略號（ **...**）流覽至您要匯入的檔案。 
    
4. 選取 [匯**入 runbook** ] 和 [匯**入 Orchestrator 加密資料**]。 清除**計數器**、**時程表**、**變數**、**電腦群組**、匯**入全域**設定，以及**覆寫現有的全域**設定。
    
5. 按一下 [完成]****。
    
6. 編輯**MoveFilesToColdStorage** runbook，如下所示：
    
1. **移動**檔案活動-將**來原始檔案**路徑設定為集合檔案共用，例如「 \\ \\ 暫存 \\ 案例」。 將**目的地資料夾**設定為 Azure 中的 cold 儲存檔共用，例如 \\ \\ AZFile1 \\ ContentColdStorage。 選取 [**建立具有唯一名稱**的檔案]。
    
2. **刪除資料夾**活動-將**路徑：** 設定為集合檔案共用（例如， \\ \\ 暫存 \\ 案例 $ \\ *），然後選取 [**刪除所有檔案與子資料夾**]。 
    
7. 使用[部署 runbook](https://go.microsoft.com/fwlink/p/?LinkId=615120)中的程式部署**MoveToColdStorage** runbook。
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>SharePoint 冷儲存體的內部部署搜尋

1. 在您的 SharePoint 2013 伺服器陣列中建立新的內容來源，以用於 Azure 中的冷存放區共用，例如 \\ \\ AZFile1 \\ ContentColdStorage。 如需管理內容來源的詳細資訊，請參閱[在 SharePoint Server 2013 中新增、編輯或刪除內容來源](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. 開始完整編目。 如需詳細資訊，請參閱[SharePoint Server 2013 中的編目、啟動、暫停、繼續或停止](https://go.microsoft.com/fwlink/p/?LinkId=615005)編目。
    
## <a name="using-the-solution"></a>使用方案

使用此解決方案有五個主要步驟，假設您不想要將 PST 檔案匯入 Exchange Server 2013 和 Exchange Online。 本節為您提供所有這些程式的程式。 您與解決方案的主要互動將會執行下列作業：
  
1. 管理保管人群組中的使用者成員資格。
    
2. 檢查登入腳本所產生的記錄檔。 FileCopyErrors 會列出所有未順利複製的檔案。 您必須決定要使用的方式
    
3. 管理 PST 匯入程式。
    
4. 將集合檔案移至冷存放區。
    
其他所有步驟並非此解決方案特有的步驟。 它們是您在 SharePoint 2013、Microsoft 365 和 Azure 中執行的標準管理工作。 此解決方案中的專案不會提供任何指引，您必須根據公司的需求來完成工作，例如：
  
1. 追蹤您的 eDiscovery 案例，以及哪些保管人與哪一種情況相關聯。
    
2. 追蹤哪組檔集合會與 eDiscovery 案例產生關聯。
    
3. 協調匯入和移至冷儲存步驟的時間。
    
4. 管理 Azure 中使用的檔空間。
    
5. 管理 Pst 所匯入的信箱。
    
6. 所有內部部署資料的備份及還原。
    
### <a name="custodian-management"></a>保管人管理

- 若要為個別使用者啟動自動化檔收集程式，請將其新增至保管人群組。 使用者下一次登入時，系統會執行透過「群組原則」指派給保管人群組的登入腳本。 
    
### <a name="monitor-collected-files-and-review-log-files"></a>監視收集的檔案並複查記錄檔

1. 針對使用者的集合資料夾，觀賞集合檔案共用（例如， \\ \\ 暫存 \\ 案例 $ \\ *）。 資料夾的名稱會以如下格式格式化： *yyyyMMddHHmm_UserName* 。
    
2. 完成集合後，請開啟集合資料夾，然後流覽至 [_Log] 資料夾。 在 [_Log] 資料夾中，您將會看到下列專案：
    
  - 使用者電腦上的每個本機磁片磁碟機都有一個 XML 檔案，例如**A.xml**， **C.xml**。 這些檔案包含的清查磁片磁碟機會在其後命名，並用於 robocopy 作業。
    
    > [!NOTE]
    > 集合腳本只會在清單檔中為您在腳本中定義的檔案類型建立專案。 它不會為使用者電腦上的每個檔案建立庫存專案。 
  
  - 每個集合執行的一個名為 FileCopyErrors 的記錄檔。 此檔案包含 robocopy 無法複製至檔案集合共用的檔案清單，例如， \\ \\ 暫存 \\ 案例 $ \\ *。 您必須複查此專案，並決定要對這些未錯過的檔案採取的動作。 通常，您必須以手動方式收集這些檔案，否則您可能會決定不需要該集合，也可以忽略集合中的物件。
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>Exchange Server 2013 的 PST 匯入選項 A

1. 登入裝載集合檔案共用的伺服器，例如，**暫存**及開啟的 Windows PowerShell。 如需啟動 Windows PowerShell 的詳細資訊，請參閱[Windows Server 上的啟動 windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=615115)。
    
2. 設定執行原則為無限制。 輸入 `Set-ExecutionPolicy Unrestricted -Scope Process` Windows PowerShell，然後按 enter 鍵。
    
3. 執行 PSTImportScript.ps1 檔，並提供 **$SourcePath**和 **$MailboxAlias**參數。 如需執行 Windows PowerShell 腳本的詳細資訊，請參閱執行[腳本](https://go.microsoft.com/fwlink/p/?LinkID=615117)。
    
4. 檢查輸出中是否有錯誤。
    
5. 嘗試將同名的 PST 檔案匯入相同的信箱之前，您必須移除信箱匯入要求。 執行下列命令以執行： `Get-MailboxImportRequest | Remove-MailboxImportRequest` 。 系統會提示您從佇列中移除每個個別要求。 視需要回應。
    
### <a name="pst-import-option-b-for-exchange-online"></a>適用于 Exchange Online 的 PST 匯入選項 B

- 若要將收集的 PST 檔案放入 Exchange Online，請遵循透過[網路上傳](https://docs.microsoft.com/microsoft-365/compliance/use-network-upload-to-import-pst-files)將檔案匯入 Microsoft 365 中的程式。
    
### <a name="move-to-cold-storage"></a>移至冷存放區

1. 使用執行[runbook](https://go.microsoft.com/fwlink/p/?LinkId=615123)中的程式執行**MoveToColdStorage** runbook。
    
2. 觀賞用於長期儲存體的 Azure 檔案共用，例如 \\ \\ AZFile1 \\ ContentColdStorage 和內部部署集合檔案共用（例如， \\ \\ 暫存 \\ 案例 $）。 您應該會看到檔案和資料夾出現在 cold 儲存檔共用中，並從集合檔案共用中消失。
    
### <a name="ediscovery"></a>電子文件探索

1. 允許完整編目冷儲存體檔案共用以排程的方式執行，或啟動編目。 如需啟動完整或累加編目的詳細資訊，請參閱[SharePoint Server 2013 中的開始、暫停、繼續或停止](https://go.microsoft.com/fwlink/p/?LinkId=615005)編目。
    
2. 如果您在使用選項 B 的情況下，在 SharePoint Online 中使用選項 A 來進行 PST 檔案匯入或建立 eDiscovery 案例，請在 SharePoint 2013 中建立電子檔探索案例。
    

