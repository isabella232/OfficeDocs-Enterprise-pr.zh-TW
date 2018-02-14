---
title: "在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: "摘要： 連線至單一 Windows PowerShell 視窗中的所有 Office 365 服務的 Windows PowerShell。"
ms.openlocfilehash: d11487ae1c95cb0d36221e7ce572ed55052d98eb
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a>在單一 Windows PowerShell 視窗中連線至所有 Office 365 服務

 **摘要：**而不是管理在個別的 PowerShell 主控台視窗中的不同 Office 365 服務，您可以連線至 Office 365 的所有服務和管理它們從單一主控台視窗。
  
當您使用 PowerShell 管理 Office 365 時，有可能有最多可以有五個不同 Windows PowerShell 工作階段，同時對應至 Office 365 系統管理中心、 SharePoint Online、 Exchange Online、 商務 online Skype 及安全性&amp;規範中心。使用個別的 Windows PowerShell 工作階段中的五個不同的連接方法，您的桌面可能看起來如下：
  
![一次執行五個 Windows PowerShell 主控台](images/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
這不是因為您不能交換資料之間的跨服務管理那些五個 windows 管理 Office 365 的最佳。本主題說明如何使用單一執行個體您可以從中管理 Office 365、 商務 Online、 Exchange Online、 SharePoint online、 Skype 和安全性的 Windows PowerShell&amp;規範中心。
  
## <a name="before-you-begin"></a>開始之前
<a name="BeforeYouBegin"> </a>

您可以從單一執行個體的 Windows PowerShell 管理 Office 365 的所有之前，請考慮下列先決條件：
  
- Office 365 搭配使用或學校您使用這些程序需求是 Office 365 系統管理員角色成員的帳戶。如需詳細資訊，請參閱 ＜[關於 Office 365 系統管理員角色](https://go.microsoft.com/fwlink/p/?LinkId=532367)。此為 Office 365 PowerShell、 不一定所有其他 Office 365 服務的需求。
    
- 您可以使用下列 Windows 64 位元版本：
    
  - Windows 10
    
  - Windows 8.1 或 Windows 8
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 或 Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    * 您需要安裝 Microsoft.NET Framework 4.5。_x_ ，然後任一 Windows Management Framework 3.0 或 Windows Management Framework 4.0。如需詳細資訊，請參閱[安裝.NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868)和[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)或[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)。
    
    您需要用於 64 位元版本的 Windows 因為 Skype 的需求而商務線上模組及其中一個 Office 365 模組。
    
- 您必須安裝所需的 Office 365、 SharePoint Online 和 Skype 的商務 Online 模組：
    
  - [Microsoft Online Services 登入小幫手，適用於 IT 專業人員 RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)
    
  - [Windows Azure Active Directory Module for Windows PowerShell （64 位元版本）](https://go.microsoft.com/fwlink/p/?linkid=236297)
    
  - [SharePoint Online 管理命令介面](https://go.microsoft.com/fwlink/p/?LinkId=255251)
    
  - [Skype Online，企業版 Windows PowerShell 模組](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  Windows PowerShell 需要為 Skype 的已簽署的指令碼執行商務 Online、 Exchange Online 與安全性設定&amp;規範中心。若要這樣做，請執行下列命令在提升權限的 Windows PowerShell 工作階段 （您可以選取 [**執行系統管理員身分**開啟 Windows PowerShell 視窗）。
    
  ```
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="the-short-version-instructions-without-explanations"></a>簡短版本 (不含說明的指示)
<a name="ShortVersion"> </a>

本節將展示連線步驟而不作深入說明。如果您有任何問題或需要詳細資訊，您可以閱讀本主題的其餘部分。此處的步驟號碼，會符合該主題的其餘部分中，以步驟編號的小節︰
  
1. （使用**系統管理員身分執行**） 以管理員身分開啟 Windows PowerShell。
    
2. 執行此命令中，並輸入您的 Office 365 工作或學校帳戶認證。
    
  ```
  $credential = Get-Credential
  ```

3. 執行下列命令以連線至 Office 365。
    
  ```
  Import-Module MsOnline
  Connect-MsolService -Credential $credential
  ```

4. 執行下列命令以連接至 SharePoint Online。取代_\<domainhost >_網域的實際值。例如，用於`litwareinc.onmicrosoft.com`、 _ \<domainhost >_值是`litwareinc`。
    
  ```
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. 執行下列命令以連線至 Skype 商務線上。增加的警告`WSMan NetworkDelayms`值預期會在第一次連線和應忽略。
    
  ```
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. 執行下列命令以連線至 Exchange Online。
    
  ```
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

7. 執行下列命令以連線至安全性&amp;規範中心。
    
  ```
  $ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
  Import-PSSession $ccSession -Prefix cc
  ```
> [!NOTE]
> 文字前置詞"cc"新增至*所有*安全性&amp;規範中心指令程式名稱，可以執行指令程式可讓存在於 Exchange Online 與安全性&amp;規範中心] 中相同的 Windows PowerShell 工作階段。例如， **Get-rolegroup**變成**Get ccRoleGroup**安全性&amp;規範中心。
  
以下是單一區塊中的所有命令。指定您的網域主機名稱和一次執行所有它們。
  
```
$domainHost="<domain host name, such as litware for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Import-Module MsOnline
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$domainHost-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
Import-PSSession $ccSession -Prefix cc
```

當您準備好關閉 Windows PowerShell 視窗時，執行此命令以移除 Skype 作用中的工作階段的商務 Online、 Exchange Online、 SharePoint Online 和安全性&amp;規範中心：
  
```
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $ccSession ; Disconnect-SPOService
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>冗長版本 (包含詳細說明的指示)
<a name="LongVersion"> </a>

### <a name="step-1-open-windows-powershell-as-an-administrator"></a>步驟 1︰以系統管理員身分開啟 Windows PowerShell
<a name="Step1"> </a>

如果您正在執行 Windows 10、 Windows 8、 Windows 8.1、 Windows Server 2016、 Windows Server 2012 R2 或 Windows Server 2012 R2、 執行這項作業：
  
1. 使用任何一種方法來尋找捷徑的**Windows PowerShell**：
    
  - 在 [開始] 畫面上按一下 [空白] 區域中，然後輸入 Windows PowerShell。
    
  - 在桌面或 [開始] 畫面中，按 Windows 鍵 + Q。在 [搜尋左中，輸入 Windows PowerShell。
    
  - 在桌面或 [開始] 畫面，將游標移至右上角或往撥動以顯示圖標螢幕的右邊緣從左。選取 [搜尋左，然後輸入 Windows PowerShell。
    
2. 結果中以滑鼠右鍵按一下 [ **Windows PowerShell**]，然後選取 [**以管理員身分執行**。
    
3. 如果出現 [**使用者帳戶控制**] 對話方塊，請選取**[是]**以確認您想要執行 Windows PowerShell 系統管理員認證。
    
如果您正在執行 Windows 7 SP1 （或 Windows Server 2008 R2 SP1），執行這項作業：
  
1. 在 [**開始**] 功能表上選取 [**所有程式]** > **附屬應用程式** > **Windows PowerShell**。**Windows PowerShell**] 上按一下滑鼠右鍵，然後選取 [**以系統管理員身分執行**。
    
2. 如果出現 [**使用者帳戶控制**] 對話方塊，請選取**[是]**以確認您想要執行 Windows PowerShell 系統管理員認證。
    
您必須以系統管理員身分執行 Windows PowerShell。如果您不進入當您嘗試匯入其中一個必要模組時收到的錯誤訊息是類似。
  
```
The specified module 'Microsoft.Online.SharePoint.Online.PowerShell' was not loaded because no valid module file was found in any directory.
```

若要補救這種情況的唯一方式是關閉 Windows PowerShell 和系統管理員身分來重新啟動。以下是告訴是否您正在以系統管理員身分執行 Windows PowerShell 快速又簡單的方法： 提示`PS C:\Windows\System32>`、 不`PS C:\Users\YourUserName>`。

  
### <a name="step-2-create-a-windows-powershell-credentials-object"></a>步驟 2：建立 Windows PowerShell 認證物件
<a name="Step2"> </a>

認證物件會提供做為 Windows powershell 將您的使用者名稱和密碼的加密的方法。若要建立的認證物件，請在 Windows PowerShell 中執行下列命令。
  
```
$credential = Get-Credential
```

> [!NOTE]
>  `$credential`會將儲存的認證物件的變數。您不需要命名變數`$credential`，但是這麼做讓容易記住的變數中包含的認證物件。（和這很重要，因為我們將多次重複使用此變數）。會將也讓更容易您依照我們的範例，因為這篇文章將會一律使用`$credential`來代表認證物件。
  
Windows PowerShell 會顯示對話方塊看起來像這樣。
  
![空白認證要求對話方塊。](images/o365_powershell_empty_credentials_box.png)
  
輸入您的工作或學校帳戶使用者名稱的**使用者名稱**] 方塊中，使用格式_username@domainname_ (例如，kenmyer@litwareinc.onmicrosoft.com);在 [**密碼**] 方塊中，輸入您的密碼並再按一下 [**確定]**：
  
![完成的認證要求對話方塊。](images/o365_powershell_completed_credentials_box.png)
  
請注意如通常是這樣，您將不會看到確認已建立的認證物件的任何排序。（Windows PowerShell 通常會告訴您何時事項出錯，但不一定要告訴您何時事項往右。）若要確認已建立的認證物件，請在 Windows PowerShell 中輸入下列命令並按 Enter。
  
```
$credential
```

接著您應該可以看到類似此螢幕的畫面。
  
```
UserName                               Password
--------                               --------
kenmyer@litwareinc.onmicrosoft.com     System.Security.SecureString
```

請記住以下一回事是[Get-credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)指令程式只會建立認證物件它不驗證您或否則請確認使用者名稱與您所提供的密碼正確無誤。例如，假設您拼錯 kenmyer@litwareinc.onmicrosoft.com 身分的使用者名稱。如果您這樣做， **Get-credential**會建立認證物件並使用該使用者名稱，且不檢查查看是否有該實際的有效使用者名稱。您不知道是否在您建立確實有效認證物件直到您真的要連線至 Office 365 服務嘗試使用該物件。
  
### <a name="step-3-connect-to-office-365"></a>步驟 3：連線至 Office 365
<a name="Step3"> </a>

我們將啟動連線至 Office 365 本身擷取。 
  
我們需要執行以下動作的第一個項重點是匯入 Office 365 模組 (Microsoft Azure Active Directory Module for Windows PowerShell)。若要這樣做，請在 Windows PowerShell 中執行此命令。
  
```
Import-Module MsOnline
```

若要驗證模組確實已經匯入，請執行此命令。
  
```
Get-Module
```

您應該會看到內容看起來像這樣這個命令所傳回的模組清單中的某處： `Manifest 1.0 MSOnline {Add-MsolForeignGroupToRole, Add-MsolG...}`。
  
如果您看到`MSOnline`列出，這表示一切皆依計劃。
  
建立的認證物件 (請參閱[步驟 2： 建立 Windows PowerShell 認證物件](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2)) 和其`MsOnline`載入模組，我們現在可以連線到 Office 365 使用[Connect-msolservice](https://go.microsoft.com/fwlink/p/?LinkId=532375) cmdlet 及下列命令。
  
```
Connect-MsolService -Credential $credential
```

所有您需要提供的注意事項是認證物件 ( `$credential`)。根據所需的認證，Office 365 將會自動連線到正確的網域。您沒有執行**Connect-msolservice**時指定您的網域名稱。
  
若要確認您確實*會*連線至 Office 365，請執行下列命令。
  
```
Get-MsolDomain
```

接著，我們應該會得到如下的內容。
  
```
Name                         Status          Authentication
----                         ------          --------------
litwareinc.onmicrosoft.com   Verified        Managed
```

### <a name="step-4-connect-to-sharepoint-online"></a>步驟 4：連線至 SharePoint Online
<a name="Step4"> </a>

匯入 SharePoint Online 模組採用下列命令：
  
```
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
```

_DisableNameChecking_參數會隱藏這個警告。
  
```
WARNING: The names of some imported commands from the module 'Microsoft.Online.SharePoint.PowerShell' include unapproved verbs that might make them less discoverable. To find the commands with unapproved verbs, run the Import-Module command again with the Verbose parameter. For a list of approved verbs, type Get-Verb.
```

若要連接至 SharePoint Online，您需要提供資訊的兩個部分： 您的認證和 SharePoint Online 系統管理網站的 URL。認證組件很簡單： 我們已儲存的變數中`$credential`(請參閱[步驟 2： 建立 Windows PowerShell 認證物件](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step2))。針對很容易足夠，以及決定系統管理網站的 URL。假設您的 Office 365 的網域名稱是`litwareinc.onmicrosoft.com`。
  
若要判斷系統管理網站的 URL，請執行此動作：
  
1. 使用前置詞啟動`https://`。
    
2. 新增您的網域名稱的網域主機部分。例如，用於`litwareinc.onmicrosoft.com`、 網域主機名稱是`litwareinc`。針對`contoso.onmicrosoft.com`、 網域主機名稱是`contoso`。
    
3. 新增連字號 （-） 後面加上`admin.sharepoint.com`。
    
換句話說：
  
 `https://` + `litwareinc` + `-admin.sharepoint.com` = `https://litwareinc-admin.sharepoint.com`
  
您已建構 URL 後，然後可以連線至 SharePoint Online 使用該 URL 及認證物件。呼叫[Connect-sposervice](https://go.microsoft.com/fwlink/p/?LinkId=532436) cmdlet，使用類似的命令。
  
```
Connect-SPOService -Url https://litwareinc-admin.sharepoint.com -credential $credential
```

若要確認已建立連線，請在 Windows PowerShell 中執行下列命令。
  
```
Get-SPOSite
```

您應該要取得所有 SharePoint Online 網站的清單。以下是範例：
  
```
Url                                       Owner          Storage Quota
---                                       -----          -------------
http://litwareinc-public.sharepoint.com/                 1000
https://litwareinc.sharepoint.com/                       1000
https://litwareinc.sharepoint.com/search                 1000
```

Office 365 命令 (過述[步驟 3： 連線至 Office 365](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md#Step3)) 將仍在運作。（嘗試執行**Get-msoluser**，並以親眼）。也就是說您現在可以管理 Office 365 與 SharePoint Online 的 Windows PowerShell 相同的執行個體。
  
### <a name="step-5-connect-to-skype-for-business-online"></a>步驟 5：連線到商務用 Skype Online
<a name="Step5"> </a>

連線到 Skype 商務 Online (與 Exchange Online 或安全性&amp;規範中心) 不同於連線至 Office 365 或 SharePoint Online。那是因為商務 Online 和 Exchange Online cmdlet Skype 不取得安裝在電腦上像是 Office 365 與 SharePoint Online cmdlet 執行動作。而您登入，每次適當指令程式會暫時複製到您的電腦。當您登入時，這些指令程式然後已從您的電腦。
  
以連線至 Skype 商務線上，您必須匯入商務線上模組的 Skype。若要這樣做，執行此命令。
  
```
Import-Module SkypeOnlineConnector
```

第一次這麼做時，您可能會看到下列警告訊息，可以放心地忽略。
  
```
WARNING: WSMan NetworkDelayms has been set to 30000 milliseconds. The previous value was 5000 milliseconds.
WARNING: To improve the performance of the Lync Online Connector, it is recommended that the network delay be set to
30000 milliseconds (30 seconds). However, you can use Set-WinRMNetworkDelayMS to change the network delay to any
integer value.
```

在匯入模組之後，請執行此命令。
  
```
$sfboSession = New-CsOnlineSession -Credential $credential
```

我們已建立的遠端 PowerShell 工作階段。在此例中，這表示我們已連線的 Windows PowerShell 執行個體其中一個 Office 365 的伺服器上執行。 
  
我們已對 Office 365 的連線，雖然我們尚未下載指令碼、 cmdlet 和 Skype 管理商務 online 所需的其他項目。若要這樣做，我們必須執行下列命令。
  
```
Import-PSSession $sfboSession
```

當您匯入 Windows PowerShell 工作階段時，您應該會看到類似下列項目，報告商務 Online cmdlet 匯入至電腦的所有 Skype 進度列進度列。
  
![Lync Online 進度列。](images/o365_powershell_lync_progress_bar.png)
  
當進度列消失後，您應該會看到如下所示的輸出。
  
```
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     1.0        tmp_swc5mp4v.1ck  {Copy-CsVoicePolicy, Disabl...
```

### <a name="step-6-connect-to-exchange-online"></a>步驟 6：連線至 Exchange Online
<a name="Step6"> </a>

執行此命令以建立遠端 Windows PowerShell 工作階段與 Exchange Online。
  
```
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
```

> [!NOTE]
> 為什麼一定要連線至 Exchange Online 比命令會連線至 Skype 商務線上更複雜的命令？嚴格來說，不： 這兩個命令執行完全同樣的事情。但如商務 Online 小組 Skype 建立自己指令程式 —**新增 CsOnlineSession** — 的隱藏一些連接至 Exchange Online 時所使用的參數 （例如_驗證_和_AllowRedirection_）。而不需要您自行輸入該資訊、_驗證_及_AllowRedirection_參數會有效地內建**新增 CsOnlineSession**指令程式。您必須連線至 Exchange Online 因為 Exchange Online 使用標準[新 PSSession](https://go.microsoft.com/fwlink/p/?LinkId=389621)指令程式來連線至 Office 365 時輸入這些參數。缺點是您必須執行一點點輸入。優點是您不需要下載並安裝 Exchange Online 的模組。
  
您只需要現在是匯入此遠端工作階段，就像我們進行了商務 online 與 Skype。
  
```
Import-PSSession $exchangeSession -DisableNameChecking
```

您應該可以看到類似此螢幕的畫面。
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_nweiqjvl.geu {Add-AvailabilityAddressSpace...
```

現在請嘗試執行此命令。
  
```
Get-AcceptedDomain
```

您應看見所傳回的資訊有關您所設定的電子郵件地址在 Exchange Online 的 Office 365 網域。
  
```
Name            DomainName          DomainType      Default
----            ----------          ----------      -------
litwareinc.com  litwareinc.com      Authoritative   True
```

### <a name="step-7-connect-to-the-security-amp-compliance-center"></a>步驟 7： 連線至安全性&amp;規範中心
<a name="Step7"> </a>

安全性&amp;規範中心是可讓您從某個位置管理的符合性功能的 Office 365 中的服務。如需詳細資訊，請參閱[Office 365 規範中心](http://technet.microsoft.com/library/fde83656-f136-448d-b250-6fa17b503e4e.aspx)。
  
證券的連線指示&amp;規範中心時非常類似的 Exchange Online 中，但具有新增變化，您會看見中可用。
  
執行此命令以建立遠端 PowerShell 工作階段與安全性&amp;規範中心。
  
```
$ccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication Basic -AllowRedirection
```

現在執行此命令︰
  
```
Import-PSSession $ccSession -Prefix cc
```

同樣地，此命令會非常類似於 Exchange Online 的命令。因為安全性中不有任何未的動詞_DisableNameChecking_參數不是必要&amp;規範中心。但不住亦其他`-Prefix cc`參數和值吗？這就是我們說過您需新增的變化。
  
Exchange Online 與安全性&amp;規範中心共用部分具有完全相同的名稱，並提供相同功能的 cmdlet。**Get-rolegroup**是範例。
  
因此，有什麼如果您嘗試匯入包含具有相同名稱的指令程式的兩個工作階段？他們會發生衝突。您將取得 big 黃色警告訊息，`WARNING: Proxy creation has been skipped for the following command:`後面接著無法匯入的衝突 cmdlet 的清單。最終結果？您可以執行**Get-rolegroup** in Exchange Online，因為您連接那里第一次，但您無法執行**Get-rolegroup**安全性&amp;規範中心因為連接那里上一次及衝突的指令程式匯入遭到拒絕。
  
處理這個問題的最簡單方式是將任意文字首碼新增至匯入安全性&amp;規範中心指令程式。我們沒有該使用的_前置詞_參數值"cc" **Import-pssession**指令程式上。沒有可為什麼？ 我們它淘汰衝突 （稍微） 變更安全性&amp;此工作階段的規範中心指令程式名稱。所有匯入安全性&amp;規範中心 cmdlet 立即開始使用"cc"在依名詞或組件中的指令程式名稱 (右邊的"-")。例如，產生爭議**Get-rolegroup**指令程式會變成**Get ccRoleGroup** security&amp;規範中心讓它不會與**Get-rolegroup** Exchange Online 的衝突。
  
缺點為何？ *所有* 安全性&amp;規範中心 cmdlet 名稱接收"cc"前置詞 — 是用完就不需要它的唯一指令程式。例如， **Get ComplianceSearch**變成**Get ccComplianceSearch**即使發生這類指令程式在 Exchange Online。它是元設計師，但不是太故障時您考慮在單一 Windows PowerShell 工作階段管理所有 Office 365 服務的優點。請記得安全性中的所有程序的 cmdlet 名稱來新增"cc"&amp;規範中心。
  
如果一切順利，您會看見類似這樣的內容：
  
```
ModuleType Version  Name             ExportedCommands
---------- -------  ----             ----------------
Script     1.0      tmp_xbbx5exr.ehm {Add-ccRoleGroupMember, Get-ccAdminAuditLogConfig, Get-ccA...
```

現在您就可以在單一 Windows PowerShell 工作階段管理所有 Office 365 服務自由。
  
### <a name="step-8-gracefully-end-your-powershell-sessions"></a>步驟 8：依正常程序結束 PowerShell 工作階段
<a name="Step8"> </a>

如果您只是關閉 Windows PowerShell 視窗，商務線上遠端連線您 Skype 會保持使用中的下一個 15 分鐘或能力。因為 Skype 商務 online 限制同時進行的任何一個人或任何一個網域都可以有開啟的連線數目、，可能是問題。具有商務 online Skype，個別的系統管理員可以、 最有三個開啟的連線一次且網域可以的九個開啟的連線的最大值。如果您的業務 Online 登入 Skype 並再結束，但不正常關閉工作階段，該工作階段的下一個 15 分鐘或賣保持開啟。因此，這是一個較少的連線可以在您或其他管理員可以在您的網域。
  
而我們關閉遠端工作階段的 Skype 商務 Online、 Exchange Online 與安全性&amp;規範中心正常。這麼做之前，請執行此命令。
  
```
Get-PSSession
```

[Get-pssession](https://go.microsoft.com/fwlink/p/?LinkId=532437) cmdlet 應為您示範您必須至少三個遠端工作階段開啟、 另一個適用於商務 online Skype、 另一個適用於 Exchange Online 及其中的安全性&amp;（有可能您可以有多個三個遠端規範中心工作階段執行，視您是否已使用 Windows PowerShell 執行個體來連線至 Office 365 服務除了其他人的某個項目）。您應該會看到類似以下的內容。
  
```
Id Name     ComputerName     State   ConfigurationName    Availability
-- ----     ------------     -----   -----------------    ------------
 1 Session1 webdir0a.onl...  Opened  Microsoft.PowerShell    Available
 2 Session2 outlook.offi...  Opened  Microsoft.Exchange      Available
 3 Session3 ps.complianc...  Opened  Microsoft.Exchange      Available
```

若要關閉這三個工作階段，請執行下列命令一次一個。第一個命令會關閉 Skype 商務線上工作階段，第二個關閉 Exchange Online 的工作階段，及第三個關閉 [安全性]&amp;規範中心工作階段。
  
```
Remove-PSSession $sfboSession
Remove-PSSession $exchangeSession
Remove-PSSession $ccSession
```

如果您現在執行**Get-pssession** cmdlet，您應該會看到 nothing 所有 （除非您有其他遠端工作階段啟動且正在執行）。
  
![沒有遠端工作階段的 Windows PowerShell 主控台](images/o365_powershell_no_remote_sessions.png)
  
> [!NOTE]
> 如果您想要關閉所有的遠端工作階段的同一時間，您可以使用此命令： >`Get-PSSession | Remove-PSSession`
  
您現在嘗試執行指令程式從任何這些關閉工作階段 (例如， **Get-csmeetingconfiguration**中的商務 Online Skype) 如果您將取得會類似的錯誤訊息。
  
```
Get-CsMeetingConfiguration : The term 'Get-CsMeetingConfiguration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

我們要取得這個錯誤訊息因為 Skype 商務 Online、 Exchange Online 和安全性的 cmdlet&amp;我們關閉遠端工作階段時刪除規範中心。
  
若要關閉 SharePoint Online 的工作階段，請輸入下列命令。
  
```
Disconnect-SPOService
```

如果您現在嘗試執行**Get-sposite** cmdlet，您將取得類似的錯誤訊息。
  
```
get-sposite : No connection available. Use Connect-SPOService before running this CmdLet.
```

因為您不再連線至 SharePoint Online 無法擷取站台資訊。
  
與 Office 365 連線，雖然**Connect-msolservice**指令程式沒有任何對應的**中斷 MsolService**指令程式。讓 Office 365 剛關閉 Windows PowerShell 視窗。不過，它仍是不錯的選項為達成此目的最後讓您可以正確中斷 SharePoint Online、 Skype 商務 Online、 Exchange Online 與安全性&amp;規範中心。
  
## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？
<a name="LongVersion"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 SharePoint Online](manage-sharepoint-online-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Windows PowerShell 在 Office 365 中建立報告](use-windows-powershell-to-create-reports-in-office-365.md)

