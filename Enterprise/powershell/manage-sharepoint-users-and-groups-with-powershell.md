---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/05/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 來管理 SharePoint Online 使用者、 群組及網站。
ms.openlocfilehash: f84e4cda797cd8f1bc4ddf573cb4f1c6f0165da7
ms.sourcegitcommit: 8d1cc95b3641afe547c6d0e05f2dad5d013a0773
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "37975888"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組

 **摘要：** 使用 Office 365 PowerShell 來管理 SharePoint Online 使用者、 群組及網站。

如果您是使用大型清單的使用者帳戶或群組的運作，以及想要輕鬆地進行管理 SharePoint Online 系統管理員，您可以使用 Office 365 PowerShell。 

## <a name="before-you-begin"></a>開始之前

本主題中的程序需要您連線至 SharePoint Online。 如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="get-a-list-of-sites-groups-and-users"></a>取得網站、 群組和使用者清單

我們開始管理使用者和群組之前，您需要取得您的網站、 群組及使用者的清單。 您然後可以使用這項資訊來完成本文中的範例。

### <a name="get-a-list-of-sites"></a>取得網站清單

取得在您的租用戶使用此命令中的網站清單：

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>取得群組的清單

取得群組的清單中您的租用戶使用此命令：

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a>取得使用者的清單

取得使用者的清單中您的租用戶使用此命令：

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>將使用者新增至網站集合管理員群組

您可以用於**設定 SPOUser**命令將使用者新增至網站集合上的網站集合管理員清單。 這是如何的語法看起來：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

若要使用這些命令，取代取代引號，包括 < 和 > 字元，以正確的名稱內的所有項目。

例如，這組命令新增 Opal Castillo (使用者名稱 opalc) 的網站集合管理員清單上 contoso1 租用的 ContosoTest 網站集合：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

您可以複製及將這些命令貼到 [記事本]、 $tenant、 $site，及 $user 變更變數值實際值從您的環境，並再將此貼到您的 SharePoint Online 管理命令介面視窗，並執行。

## <a name="add-a-user-to-other-site-collection-groups"></a>將使用者新增至其他網站集合群組

在這個工作中，我們將使用**Add-spouser**命令，將使用者新增至 SharePoint 群組網站集合上。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

例如，讓我們將新增 Glen Rife (使用者名稱 glenr) 至 contoso1 租用的 ContosoTest 網站集合上 「 稽核員 」 群組：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>建立網站集合群組

您可以使用 [**新增 SPOSiteGroup**命令建立新的 SharePoint 群組，並將它新增至的 ContosoTest 網站集合。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
群組的內容，例如權限等級，可以稍後更新，使用**Set-spositegroup** cmdlet。

例如，讓我們將新增僅供檢視權限與稽核員 」 群組至 contoso1 租用的 Contoso Test 網站集合：

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>從群組中移除使用者

有時候，您必須從站台或甚至是所有網站中移除使用者。 可能是員工將從一個部門移至另一個，或離開公司。 您可以這麼一個員工輕鬆地在 UI 中，但無法輕鬆完成此工作時您有一個站台間移動完成的部門。

不過藉由使用 SharePoint Online 管理命令介面和 CSV 檔案，這樣既快速又簡單。 在這個工作中，您會使用 Windows PowerShell 從網站集合安全性] 群組中移除使用者。 然後使用 CSV 檔，並從不同的網站移除大量的使用者。 

我們將使用**Remove-spouser**命令來移除單一 Office 365 使用者網站集合群組只是因此我們可以看到命令語法。 以下是如何的語法看起來：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
例如，讓我們先移除 Bobby Overby 從 contoso1 租用的 Contoso Test 網站集合的網站集合稽核員 」 群組：

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

假設您想要移除 Bobby 他目前是中的所有群組。 以下是如何我們會這麼做：

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> 這只是範例。 除非您真的有使用者移除每個群組，例如，如果使用者離開公司，您不應執行此命令。

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>自動化管理大型使用者和群組清單

若要將大量帳戶新增至 SharePoint 網站，並授與權限，您可以使用 Microsoft 365 系統管理中心，個別的 PowerShell 命令或 PowerShell CSV 檔案。 這些選項的 CSV 檔案是自動執行此工作最快的方法。

基本程序會建立具有標頭 （資料行），會對應至 Windows PowerShell 指令碼所需的參數的 CSV 檔案。 您可以輕鬆地在 Excel 中建立此類清單，並再將它匯出為 CSV 檔案。 然後，您可以使用 Windows PowerShell 指令碼來逐一記錄 （資料列） 在 CSV 檔案中，將使用者新增至群組及網站群組。 

例如，讓我們先建立 CSV 檔案，以定義一組網站集合、 群組和權限。 接下來，我們會建立 CSV 檔案，以填入與使用者群組。 最後，我們會建立並執行簡單的 Windows PowerShell 指令碼會建立並填入群組。

第一個 CSV 檔會將一個或多個群組新增至一或多個網站集合中，而其結構如下：

### <a name="header"></a>標頭：

```
Site,Group,PermissionLevels
```

### <a name="item"></a>項目：

```
https://tenant.sharepoint.com/sites/site,group,level
```

以下是範例檔案：

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

第二個 CSV 檔案會將一或多位使用者新增至一或多個群組，並將其結構如下：

### <a name="header"></a>標頭：

```
Group,LoginName,Site
```

### <a name="item"></a>項目：

```
group,login,https://tenant.sharepoint.com/sites/site
```

以下是範例檔案：

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

下一個步驟中，您必須具有兩個 CSV 檔案儲存至您的磁碟機。 以下是使用這兩個 CSV 檔案的範例命令，以新增權限和群組成員資格：

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

指令碼會匯入 CSV 檔案的內容和資料行中使用的值來填入**新 SPOSiteGroup**和**Add-spouser**命令的參數。 在我們的範例中，我們會將此儲存到 theO365Admin 資料夾，磁碟機 C，但您可以將它儲存您需要的地方。

現在，我們使用相同的 CSV 檔的不同站台中移除一堆數個群組的人員。 範例命令如下：

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>產生使用者報告

您可能想要取得的簡單報告的幾個網站，並顯示這些網站、 其權限層級和其他內容的使用者。 這是如何的語法看起來：

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

這將擷取這些三個網站的資料，並寫入本機磁碟機上的文字檔案。 請注意，參數 – Append 會將新的內容新增至現有的檔案。

例如，讓我們執行報告的 ContosoTest、 TeamSite01 和 Project01 網站上 Contoso1 租用戶：

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

請注意，我們有變更僅 **$site**變數。 **$Tenant**變數會保留其值，透過命令的所有三個執行。

不過，如果您想要這麼做的每個網站？ 無需鍵入所有這些網站使用下列命令，您可以執行這項操作：

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

這份報告是相當簡單，以及您可以新增更多的程式碼來建立更具體的報表或報表，包括更詳細的資訊。 但這應讓您了解如何使用 SharePoint Online 管理命令介面來管理 SharePoint Online 環境中的使用者。
   
## <a name="see-also"></a>另請參閱

[連線至 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[使用 Office 365 PowerShell 管理 SharePoint Online](create-sharepoint-sites-and-add-users-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

