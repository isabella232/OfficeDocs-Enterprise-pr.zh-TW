---
title: "自動化檔案集合 ediscovery （英文）"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: 8d751419-d81b-4eb7-a2e5-8b03ccbf670c
description: "摘要： 了解如何自動化 ediscovery （英文） 的使用者電腦從檔案集合。"
ms.openlocfilehash: bb93bed80ec95511c6bbf4307d1f0c9e1d4f82cb
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="automate-file-collection-for-ediscovery"></a>自動化檔案集合 ediscovery （英文）

 **摘要：**了解如何自動化 ediscovery （英文） 的使用者電腦從檔案集合。
  
所有的公司正面可能會訴訟或其他類型的法律巨集指令。雖然法務部門可以使用，以減少的曝光度、 訴訟暫止的商務循環之事實。當公司朝法律巨集指令時，為必要項目，透過的法律調查，以提供所有相關的記錄運送巷以及一顧問程序。 
  
eDiscovery 是依據公司清查、 搜尋、 識別、 保留、 篩選和提供存在於相關記錄運送電子表單中的程序。SharePoint 2013、 Exchange Server 2013、 Lync Server 2013、 SharePoint Online 和 Exchange Online 可以保留大量的記錄的內容。根據版本，這些產品可能支援 eDiscovery 及就地保留 (透過 Exchange Server Lync)，讓更容易編製索引，法律小組的識別、 按住並篩選特定案例最相關的內容。
  
許多文件會儲存在使用者電腦 (Custodians) 上本機電腦] 不在集中位置。這讓 SharePoint 2013 搜尋，基本上無法運用和無法搜尋，如果它不能包含 eDiscovery。此解決方案會示範如何使用登入指令碼、 System Center Orchestrator 2012 R2 和 Windows PowerShell for Exchange Server 自動化的識別資料及記錄資料從使用者電腦的集合。
  
## <a name="what-this-solution-does"></a>此解決方案的沒有

此解決方案會使用通用安全群組，群組原則和 Windows PowerShell 指令碼來找出、 清查，及從使用者本機電腦收集的內容及 Outlook 個人存放區 (PST) 檔案到隱藏的檔案共用。從該處、 PST 檔案可以匯入 Exchange Server 2013 或 Exchange Online。所有檔案會再都移到另一個檔案共用 System Center Orchestrator 2012 R2 runbook in Microsoft Azure 至長期儲存區及索引如使用 SharePoint 2013。然後您使用 eDiscovery 中心在內部部署 SharePoint 2013 部署或 SharePoint Online 中一樣定期才能執行 eDiscovery。 
  
> [!IMPORTANT]
> 此解決方案使用 robocopy 檔案複製至集中的檔案共用 okay 的電腦。因為 robocopy 不會複製檔案開啟或鎖定，任何檔案，包括 okay 已開啟的 PST 檔案系統不會收集。您必須以手動方式加以收集。此解決方案沒有提供給您明確地識別它不能將複製的檔案清單與每個檔案的完整路徑。 
  
下圖會帶領您完成所有步驟及的解決方案項目。
  
![自動化檔案收集解決方案的概觀](images/dbb447b5-c74c-4956-986c-10a1d047ac99.png)
  
|圖例 * * *||
|:-----|:-----|
|![洋紅色圖說文字 1](images/000026a3-2bf0-4678-b468-ccb5f81da6f1.png)|建立群組原則物件 (GPO)，並將其關聯集合登入指令碼。  <br/> |
|![洋紅色圖說文字 2](images/a31b11e2-3597-42a4-933e-b6af11ed6ef1.png)| 設定 GPO 僅套用至 Custodians 群組的 GPO 安全性篩選。 <br/> |
|![洋紅色圖說文字 3](images/3ced060c-daec-460d-a9b5-260a3dfcae36.png)|Okay 登入並執行 GPO，呼叫集合登入指令碼。  <br/> |
|![洋紅色圖說文字 4](images/6f269d84-2559-49e3-b18e-af6ac94d0419.png)|集合登入指令碼清查搜尋您想將的檔案及記錄其位置 Custodians 電腦上的所有附加在本機磁碟機。  <br/> |
|![洋紅色圖說文字 5](images/4bf8898c-44ad-4524-b983-70175804eb85.png)|集合登入指令碼會將清查的檔案複製到臨時伺服器上的隱藏的檔案共用。  <br/> |
|![洋紅色圖說文字 6](images/99589726-0c7e-406b-a276-44301a135768.png)| （選項的）手動執行要收集的 PST 檔案匯入 Exchange Server 2013 的 PST 匯入指令碼。 <br/> |
|![洋紅色圖說文字 7](images/ff15e89c-d2fd-4614-9838-5e18287d578b.png)|（選項 B）使用 Office 365 匯入工具及程序，匯入收集的 PST 檔案 Exchange Online。  <br/> |
|![洋紅色圖說文字 8](images/aaf3bd3d-9508-4aaf-a3af-44ba501da63a.png)|將所有收集的檔案移至長期儲存與 MoveToColdStorage System Center Orchestrator 2012 R2 runbook Azure 檔案共用。 <br/> |
|![洋紅色圖說文字 9](images/b354642e-445e-4723-a84a-b41f7ac6e774.png)|索引中與 SharePoint 2013 的寒冷儲存檔案共用的檔案。  <br/> |
|![洋紅色圖說文字 10](images/cebf7de5-7525-413b-9e52-638a4f8b2f74.png)|執行 eDiscovery 寒冷儲存區與內部部署 Exchange Server 2013 中的內容。  <br/> |
|![洋紅色圖說文字 11](images/e59ab403-2f19-497a-92a5-549846dded66.png)|在 Office 365 中的內容上執行 eDiscovery。  <br/> |
   
## <a name="prerequisites"></a>必要條件

此解決方案的設定需要許多元素最其中您可能已經備妥及設定若您的想法有關 eDiscovery。元素可能沒有或類需要特定設定，我們將會提供您下列連結，您需要建立取出您基底的設定。您必須基本組態備妥之前設定本身的解決方案。
  
### <a name="base-configuration"></a>基本組態

|**項目**|**連結**|
|:-----|:-----|
|Active Directory 網域服務 (AD DS) 網域  <br/> ||
|從內部網路的網際網路連線能力  <br/> ||
|SQL Server 2012 支援 SharePoint 2013 和 System Center Orchestrator 2012 R2  <br/> |[部署 System Center Orchestrator-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
| 內部部署或 Azure 基礎 SharePoint 2013 的 eDiscovery （所需的選項的） <br/> ||
|內部檔案共用伺服器的臨時  <br/> ||
|內部部署 Exchange Server 2013 選項 PST 匯入  <br/> |CU5 (15.913.22) 位於[CU5](https://go.microsoft.com/fwlink/p/?LinkId=613426)。  <br/> |
|System Center Orchestrator 2012 R2  <br/> |[部署 System Center Orchestrator-2012](https://go.microsoft.com/fwlink/p/?LinkId=613503) <br/> |
|Office 365 （E3 規劃） 與 Exchange Online 和 SharePoint Online （所需的選項 B）  <br/> |若要註冊 Office 365 E3 訂閱，請參閱[Office 365 E3 訂閱](https://go.microsoft.com/fwlink/p/?LinkId=613504)。  <br/> |
|Azure 虛擬機器與訂閱  <br/> |若要註冊 Azure，請參閱[訂閱至 Windows Azure](https://go.microsoft.com/fwlink/p/?LinkId=512010) <br/> |
|在內部網路和 Azure 訂閱間 VPN 連線  <br/> |若要設定在 Azure 的訂閱與您的內部網路之間 VPN 通道，請參閱[Connect Microsoft Azure 虛擬網路的內部網路](https://go.microsoft.com/fwlink/p/?LinkId=613507)。  <br/> |
|SharePoint 2013 的 eDiscovery 來搜尋整個 SharePoint 與 Exchange Server 2013 與 Lync Server 2013 （選用） 設定  <br/> |若要設定的 eDiscovery 這種方式，請參閱[Configure eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=613508)和[Test Lab Guide: Exchange、 Lync、 SharePoint 及 Windows 檔案共用測試實驗室中設定 eDiscovery](https://go.microsoft.com/fwlink/p/?LinkId=393130)。  <br/> |
|Office 365 中的 SharePoint Online 和 Exchange Online 的 eDiscovery  <br/> |若要在 Office 365 中設定 eDiscovery，請參閱[設定 eDiscovery 中心 SharePoint Online 中](https://go.microsoft.com/fwlink/p/?LinkId=613628)。  <br/> |
   
## <a name="configure-the-environment"></a>設定環境

既然您已經備妥的基底的設定，您可以移動預先設定本身的解決方案。 
  
### <a name="staging-file-share"></a>臨時檔案共用

1. 在內部部署網域中建立通用安全性群組名為 Custodians。
    
2. 建立從 Custodians 電腦收集的檔案隱藏的檔案共用。這應該是在內部部署伺服器上。例如，在呼叫臨時伺服器上建立的檔案共用呼叫的情況下 $。**$** ，才能將此設為隱藏的共用。
    
3. 設定下列共用權限：
    
  - Custodians： 變更，請閱讀
    
  - 系統管理員：完全控制
    
  - Exchange 信任的子系統： 變更，請閱讀
    
4. 開啟 [**安全性**] 索引標籤、 新增 Custodians] 群組中，並按一下 [**進階**]。設定 [Custodians 群組中的下列權限：
    
  - **類型： 拒絕**
    
  - **適用於： 這個資料夾、 子資料夾和檔案**
    
5. 按一下 [**進階權限**並選取下列項目：
    
  - **讀取屬性**
    
  - **讀取擴充屬性**
    
  - **讀取權限**
    
6. 測試共用的存取權的情況下 $ 檔案執行下列動作：
    
1. 將使用者新增至 Custodians 群組。
    
2. 將檔案的情況下 $ 資料夾中。
    
3. 為使用者、 瀏覽至臨時伺服器，例如瀏覽至\\\\臨時查看哪些共用所提供的共用。您不應該會看到所列的**情況下 $**共用。
    
4. 手動輸入瀏覽器的情況下 $ 共用的完整路徑。這應該會開啟的情況下 $ 共用。
    
5. 嘗試開啟之前放在共用的檔案。這應該會失敗。
    
### <a name="logon-script"></a>登入指令碼

1. 複製並貼入 [記事本] 中的此 Windows PowerShell 指令碼：
    
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
    $TargetFileCheck = Test-Path $TargetPath\\$FileName

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
$CaseRootLocation = "\\\\staging\\Cases$" 

# File copy location, log file location, PST file location and temporary log file location
$CaseLocation = $CaseRootLocation + "\\" + $CaseNo
$CaseLogLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_Log"
$CasePSTLocation = $CaseRootLocation + "\\" + $CaseNo + "\\_PSTs"
$TemporaryLogLocation = [Environment]::getfolderpath('ApplicationData') + "\\" + $CaseNo

# Inventory of local drives
$LocalDrives = Get-PSDrive -PSProvider FileSystem -Scope Global

$LoggingFile = "$CaseLogLocation\\FileCopyErrors.log"

# Main script

# Create the case folder if it doesn't already exist
CreateCaseFolder

# Create the list of files to be copied
# First create the temporary directory in the AppData\\Roaming folder
New-Item "$TemporaryLogLocation" -ItemType Directory -Force -ErrorAction SilentlyContinue
$LocalDrives | foreach {

    # Write-Host -ForeGroundColor Cyan "Collecting Files for Drive: " $_
    Get-ChildItem -Path $_.Root -Recurse -Include $FileTypes -ErrorAction SilentlyContinue -ErrorVariable +Loggederrors | Export-Clixml $TemporaryLogLocation\\\\$_.xml -Force
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

2. 為 CollectionScript.ps1 更容易找到，例如 c： 的位置中儲存上面的指令碼\\AFCScripts。
    
3. 在 [記事本] 中使用移至] 功能。視需要進行變更如下：
    
|**線條 #**|**您需要變更**|**所需/選用**|
|:-----|:-----|:-----|
|71  <br/> |**$FileTypes**變數。包含您想要清查並收集陣列變數中的指令碼的所有檔案類型副檔名。<br/> |選用  <br/> |
|76 和 77  <br/> |變更的方式**$CaseNo**變數內建以符合您的需求。指令碼擷取目前的日期及時間並將它附加的使用者名稱。<br/> |選用  <br/> |
|80  <br/> |**$CaseRootLocation**變數必須設為您的臨時伺服器集合檔案共用，例如**\\\\臨時\\情況下 $**。 <br/> |必要  <br/> |
   
4. CollectionScript.ps1 檔案放在網域控制站的 Netlogon 檔案共用。 
    
### <a name="configure-gpo-for-the-logon-script-and-custodians-group"></a>設定 GPO 登入指令碼和 Custodians 群組

1. 遵循下列主題，[使用啟動、 關閉、 登入和登出指令碼在群組原則中](https://go.microsoft.com/fwlink/p/?LinkId=614844)的"如何指派使用者登入指令碼 」 一節中設定 Custodians 群組的登入指令碼。
    
2. 移除已驗證的使用者**安全性篩選**，並新增 Custodians 群組。
    
### <a name="pst-import-option-a-script-for-exchange-server-2013"></a>PST 匯入選項 A、 Exchange Server 2013 的指令碼

1.  複製並貼入 [記事本] 中的下列 Windows PowerShell 指令碼：
    
  ```
  # Script to import all PSTs in a given folder to a target mailbox
#
# This is for on-prem Exchange only
# Input parameters
# When you run the script, you call it with two parameters, PST source path and target mailbox alias
# For example:  .\\PSTImport.ps1 \\\\FileShare\\PSTFiles jdoe

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

2. 將指令碼儲存為 PSTImportScript.ps1 中更容易尋找的位置。範例和方便使用，建立資料夾呼叫臨時伺服器上\\\\臨時\\AFCScripts，並將其儲存到那里。
    
3. 使用 [記事本] 中移至功能並視需要進行下列變更：
    
|**線條 #**|**您需要變更**|**所需/選用**|
|:-----|:-----|:-----|
|12  <br/> |**$FolderIdentifier** tags Pst 所匯入的信箱資料夾。這在必要時變更。<br/> |選用  <br/> |
|第 17  <br/> |**$ConnectionUri**必須設為您自己的伺服器。 <br/> > [!IMPORTANT]> 確定您**$ConnectionUri**指引的 http 位置，而不是 https。將不會使用 https:。          |必要  <br/> |
   
4. 確認 Exchange 受信任子系統帳戶是否有讀取、 寫入、 和執行權限\\\\臨時\\的情況下 $ 共用。
    
5. PST 匯入指令碼需要下列兩個輸入的參數：
    
  - **$SourcePath**要匯入，例如 PST 檔案的位置\\\\臨時\\情況下 $。
    
  - **$MailboxAlias**將會收到匯入的電子郵件項目的目標信箱的別名。
    
6. 例如，如果您想要匯入所有 PST 檔案的路徑\\\\臨時\\轉換與別名 eDiscoveryMailbox 信箱的情況下 $、 您可執行類似的指令碼`\\\\staging\\AFCscripts\\PSTImportScript.ps1 \\\\Staging\\cases$ eDiscoveryMailbox`。
    
### <a name="pst-import-option-b-for-exchange-online"></a>Exchange Online 的 PST 匯入選項 B

-  建立信箱結構放入的匯入的 PST 檔案。如需如何在 Exchange Online 中建立使用者信箱的詳細資訊，請參閱[Exchange Online 中建立使用者信箱](https://go.microsoft.com/fwlink/p/?LinkId=615118)。
    
### <a name="cold-storage"></a>冷存放區

1. 建立的檔案共用上 Azure 虛擬機器，所有收集的檔案放置，例如\\ \\AZFile1\\ContentColdStorage。
    
2. 至少授與預設內容存取帳戶的讀取權限的共用和所有子資料夾和檔案。如需設定 SharePoint 2013 搜尋的詳細資訊，請參閱[建立及設定 SharePoint Server 2013 中的 Search service 應用程式](https://go.microsoft.com/fwlink/p/?LinkId=614940)。
    
3. 如果您預期匯入 PST 檔案從\\ \\AZFile1\\ContentColdStorage，授與 Exchange 受信任的子系統讀取、 寫入及執行之共用的權限。
    
### <a name="orchestrator"></a>Orchestrator

1. 從 Microsoft 下載中心下載[MoveToColdStorage runbook](https://go.microsoft.com/fwlink/?LinkId=616095) 。
    
2. 開啟**Runbook 設計工具**] 的 [**連線**] 窗格中，按一下您要匯入到 runbook 的資料夾。按一下 [**動作**] 功能表，然後按一下 [**匯入**]。**匯入**] 對話方塊隨即出現。
    
3. 在 [**檔案位置**] 方塊中輸入您想要匯入 runbook 的路徑和檔案名稱或按一下 [瀏覽至您要匯入檔案的省略符號 （ **...**）。 
    
4. 選取 [**匯入 runbooks**和**匯入 Orchestrator 加密資料**。清除**計數器**、**排程**、**變數**、 **Computer Groups**、**匯入通用設定**，以及**要覆寫現有的全域設定**。
    
5. 按一下 [**完成**]。
    
6. 編輯**MoveFilesToColdStorage** runbook，如下所示：
    
1. **移動檔案**活動-設定的**來源檔案**路徑為集合檔案共用，例如\\\\臨時\\情況下 $。設定要寒冷儲存檔案的**目的資料夾**中的共用 Azure，例如\\ \\AZFile1\\ContentColdStorage。選取 [**建立的檔案使用唯一的名稱**。
    
2. **刪除資料夾**活動-設定**路徑：**集合檔案共用，例如\\\\臨時\\情況下 $\\*，然後選取 [**刪除所有檔案及子資料夾**。 
    
7. 部署使用本節的程序中[部署 Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615120) **MoveToColdStorage** runbook。
    
### <a name="sharepoint-on-premises-search-for-cold-storage"></a>SharePoint 內部部署搜尋寒冷存放區

1. 例如在 Azure、 寒冷儲存共用的 SharePoint 2013 伺服器陣列中建立新的內容來源\\ \\AZFile1\\ContentColdStorage。如需管理內容來源的詳細資訊，請參閱[新增、 編輯或刪除 SharePoint Server 2013 中的內容來源](https://go.microsoft.com/fwlink/p/?LinkId=615004)
    
2. 開始完整編目。如需詳細資訊，請參閱[開始、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目](https://go.microsoft.com/fwlink/p/?LinkId=615005)。
    
## <a name="using-the-solution"></a>使用解決方案

使用此解決方案假設您不想將 PST 檔案匯入 Exchange Server 2013 和 Exchange Online 中有五個主要步驟。本節提供本節的程序的所有這些。您解決方案的主要互動將處於執行下列動作：
  
1. 管理使用者 Custodians 群組成員資格。
    
2. 檢閱登入指令碼所產生的記錄檔。FileCopyErrors.log 列出所有不成功複製的檔案。您必須決定您要執行操作
    
3. 管理 PST 匯入程序。
    
4. 將集合檔案移至寒冷存放區。
    
所有其他步驟不專屬於此解決方案。可讓您執行 SharePoint 2013 與 Office 365 和 Azure 中的標準系統管理工作。有此解決方案未提供任何您將需要合作根據公司的需求，例如的指導的項目：
  
1. 追蹤您的 eDiscovery 案例和 Custodians 相關聯這種情況。
    
2. 追蹤的一組檔案集合所使用的 eDiscovery 案例的關聯。
    
3. 協調匯入及移至寒冷儲存步驟的時機。
    
4. 管理 Azure 中使用的檔案空間。
    
5. 管理 Pst 所匯入至信箱。
    
6. 備份及還原的內部部署的所有資料。
    
### <a name="custodian-management"></a>Okay 管理

- 若要啟動個別使用者的自動化的檔案集合程序，將其新增至 Custodians 群組。使用者登入時，下一次登入指令碼指定給 Custodians 群組透過群組原則將會執行。 
    
### <a name="monitor-collected-files-and-review-log-files"></a>監視收集的檔案及檢閱記錄檔

1. 觀賞集合檔案共用，例如\\\\臨時\\情況下 $\\*，從使用者的集合資料夾。資料夾的名稱將格式設定如下： *yyyyMMddHHmm_UserName* 。
    
2. 集合完成時，開啟集合資料夾，並瀏覽至 [_Log] 資料夾。在 [_Log] 資料夾中，您會看到下列項目：
    
  - 每個使用者的電腦，例如**A.xml**、 **C.xml**上的本機磁碟機的一個 XML 檔案。這些檔案包含的庫存磁碟機之後，名為並使用 robocopy 作業。
    
    > [!NOTE]
    > 集合指令碼僅會在本身的指令碼中所定義的檔案類型的庫存檔案中建立項目。它將不會建立使用者的電腦上每個檔案的詳細目錄項目。 
  
  - 一個記錄檔名為 FileCopyErrors.log 執行每個集合。這個檔案包含的檔案清單該 robocopy 可能無法複製到檔案集合共用，例如\\\\臨時\\情況下 $\\*。您必須檢閱這並決定這些未接的檔案需要採取的動作。通常，您其中一個需要收集這些手動如果您想讓他們，或您可能會決定他們不需要與因此可以省略集合中。
    
### <a name="pst-import-option-a-for-exchange-server-2013"></a>PST 匯入] 選項的 Exchange Server 2013

1. 登入伺服器主控集合檔案共用，例如**臨時**，並開啟 Windows PowerShell。如需啟動 Windows PowerShell 的詳細資訊，請參閱 ＜[Windows Server 上啟動 Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=615115)。
    
2. 將執行原則設定為 [沒有限制。類型`Set-ExecutionPolicy Unrestricted -Scope Process`到 Windows PowerShell]，然後按 Enter。
    
3. 執行 PSTImportScript.ps1 檔，並提供**$SourcePath**與**$MailboxAlias**參數。如需執行 Windows PowerShell 指令碼的詳細資訊，請參閱[執行指令碼](https://go.microsoft.com/fwlink/p/?LinkID=615117)。
    
4. 檢閱錯誤的輸出。
    
5. 您嘗試同名具名的 PST 檔案匯入至相同信箱，您必須先移除信箱匯入要求。執行下列命令以這樣： `Get-MailboxImportRequest | Remove-MailboxImportRequest`。系統會提示您從佇列移除每個個別的要求。視回應。
    
### <a name="pst-import-option-b-for-exchange-online"></a>Exchange online 的 PST 匯入選項 B

- 若要將收集的 PST 檔案放入 Exchange Online，遵循匯入檔案中的程序到 Office 365 透過網路上傳] 區段中的[Office 365 匯入服務](https://go.microsoft.com/fwlink/p/?LinkId=614938)。
    
### <a name="move-to-cold-storage"></a>移至寒冷存放區

1. 執行使用本節的程序中[執行 Runbooks](https://go.microsoft.com/fwlink/p/?LinkId=615123) **MoveToColdStorage** runbook。
    
2. 觀賞 Azure 檔案共用您用於長字詞儲存區，例如\\ \\AZFile1\\ContentColdStorage 與內部部署集合檔案共用，例如\\\\臨時\\情況下 $。您應該會看到檔案及資料夾會出現在寒冷儲存的檔案共用及消失從集合檔案共用。
    
### <a name="ediscovery"></a>eDiscovery

1. 可允許寒冷儲存的檔案共用作為排程執行完整編目或啟動編目。如需有關啟動完整或累加編目的詳細資訊，請參閱 ＜[啟動、 暫停、 繼續或停止在 SharePoint Server 2013 中的編目](https://go.microsoft.com/fwlink/p/?LinkId=615005)。
    
2. 如果您使用 PST 檔案匯入] 選項的 SharePoint 2013 中建立 eDiscovery 案例或建立在 SharePoint Online 中的 eDiscovery 案例如果您是使用選項 b。
    

