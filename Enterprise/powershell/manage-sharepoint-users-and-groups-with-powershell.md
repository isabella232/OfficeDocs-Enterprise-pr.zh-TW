---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 管理 SharePoint Online 使用者、 群組及網站。
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組

 **摘要：**使用 Office 365 PowerShell 來管理 SharePoint Online 使用者、 群組及網站。

如果您是 SharePoint Online 搭配大型清單的使用者帳戶或群組且想更輕鬆地方法來管理它們，您可以使用 Office 365 PowerShell。 

## <a name="before-you-begin"></a>開始之前

本主題中的程序要求您重新連線至 SharePoint Online。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>取得網站、群組和使用者清單

開始管理使用者和群組之前，請取得網站、群組和使用者清單。接著，您可以使用此資訊逐步完成本文中的範例。

### <a name="get-a-list-of-sites"></a>取得網站的清單

使用這個命令，來取得在您的租用戶中網站的清單︰

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>取得群組的清單

使用這個命令，來取得在您的租用戶中群組的清單︰

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a>取得使用者的清單

使用這個命令，來取得在您的租用戶中使用者的清單︰

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>將使用者新增至「網站集合系統管理員」群組

您可以使用**組 SPOUser**命令將使用者新增至網站集合上的網站集合管理員清單。這是語法的外觀：

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

本範例會使用變數來儲存值和指令碼中有附註 (例如"<!--This is the Tenant Name…-->") 可協助您了解這些值應該是。

例如，這組命令新增 Opal Castillo (使用者名稱 opalc) 清單的網站集合管理員對 contoso1 租用中 ContosoTest 網站集合：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

您可以將上述命令實際剪貼至 [記事本]，將 $tenant、$site 和 $user 的變數值，變更為環境中的實際值，再將其貼至 SharePoint Online 管理命令介面視窗內。

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>將使用者新增至其他「網站集合系統管理員」群組

在此工作，我們將使用**Add-spouser**命令來將使用者新增至網站集合上的 SharePoint 群組。這是語法的外觀：

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

例如，我們將新增 Glen 猜 (使用者名稱 glenr) 至 contoso1 租用中的 ContosoTest 網站集合的稽核者群組：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>建立網站集合群組

您可以使用**Set-spositegroup**命令建立新的 SharePoint 群組並將其新增至 ContosoTest 網站集合。這是語法的外觀：

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> 您必須在引號括住空格的任何字串。群組內容，例如權限層級可使用 **-Set-spositegroup** cmdlet 更新版本進行更新。

例如，我們將稽核者群組新增僅供檢視權限 contoso1 租用中 Contoso 測試網站集合：

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>從群組中移除使用者

有時，您必須從某個網站甚至所有網站中移除使用者。可能是員工從某個部門調到另一個部門，或離開公司。您可以使用 UI，輕鬆地針對某位員工進行這項作業，但是要將整個部門從某個網站移至另一個網站時，就沒有那麼簡單了。

不過所使用的 SharePoint Online 管理命令介面和 CSV 檔案，這是快速又簡單。在此工作，您將使用 Windows PowerShell 移除使用者從網站集合安全性群組。然後您可使用 CSV 檔案並從不同的網站移除大量使用者。 

我們將使用**Remove-spouser**命令以從網站集合群組中移除單一 Office 365 使用者剛才，因此我們可以看到命令語法。以下是語法的外觀：

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

例如，我們 Bobby Overby 從群組中移除網站集合稽核者 contoso1 租用中 Contoso 測試網站集合中：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

假設我們想要從 Bobby 所在的所有群組中移除 Bobby。作法如下：

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> 這只是顯示作法。除非您真地必須從每個群組中移除使用者 (例如，如果使用者離開公司)，否則不應執行此命令。

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>自動化管理大型使用者和群組清單

若要將大量的帳戶新增至 SharePoint 網站和授與權限，您可以使用 Office 365 系統管理中心、 個別的 PowerShell 命令或 PowerShell CSV 檔案。這些選擇的 CSV 檔案會是最快的方法來自動化這項工作。

基本程序是建立具有標頭 （欄） 的 Windows PowerShell 指令碼需要的參數與相對的 CSV 檔案。您可以輕鬆地在 Excel 中建立這類清單並再將它匯出為 CSV 檔案。然後，您可以使用 Windows PowerShell 指令碼來逐一記錄 （列） 的 CSV 檔案並將使用者新增至群組和網站群組。 

例如，建立 CSV 檔案來定義一組網站集合、群組和權限。接下來，會建立 CSV 檔案以將使用者填入群組中。最後，建立和執行可建立和填入群組的簡單 Windows PowerShell 指令碼。

第一個 CSV 檔案會將一個或多個群組新增至一個或多個網站集合，而其結構如下：

### <a name="header"></a>標頭：

```
Site,Group,PermissionLevels
```

### <a name="item"></a>項目：

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

範例檔案如下：

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

第二個 CSV 檔案會將一個或多個使用者新增至一個或多個群組，而其結構如下：

### <a name="header"></a>標頭：

```
Group,LoginName,Site
```

### <a name="item"></a>項目：

```
group,login,https://tenant.sharepoint.com/sites/site
```

範例檔案如下：

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

下一個步，您必須將這兩個 CSV 檔案儲存至磁碟機。以下的命令會使用這兩個 CSV 檔案，來新增權限和群組成員︰

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

指令碼會匯入 CSV 檔案內容與使用中的欄 （以粗體） 的值填入**新增 Get-spositegroup**和**Add-spouser**命令的參數。在我們的範例中，我們會將此儲存至磁碟機 C、 但儘想儲存它。

現在，請使用相同的 CSV 檔案，來移除不同網站中數個群組的一群人。命令如下：

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>產生使用者報告

您可能會想要取得許多網站的簡單報告，並顯示那些網站的使用者、其權限等級及其他內容。語法如下：

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

這會取得下列三個網站的資料並寫入本機磁碟上的文字檔案。請注意，參數 – Append 會將新的內容新增至現有的檔案。

例如，讓我們在 Contoso1 租用戶的 ContosoTest、TeamSite01 和 Project01 網站上執行報表：

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

請注意我們需要變更 **$site**變數。**$Tenant**變數會保留其值之命令的所有三個執行透過。

不過，如果您想要對每個網站執行這項作業，該怎麼辦？使用此命令，便可執行這項作業，無需鍵入所有這些網站：

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

這份報告是相當簡單，您可以新增更多的程式碼來建立更多特定報告或報告包含更多詳細的資訊。但是這應讓您瞭解如何使用 SharePoint Online 管理命令介面來管理 SharePoint Online 環境中的使用者。
   
## <a name="see-also"></a>另請參閱

[連線至 SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[使用 Office 365 PowerShell 管理 SharePoint Online](create-sharepoint-sites-and-add-users-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

