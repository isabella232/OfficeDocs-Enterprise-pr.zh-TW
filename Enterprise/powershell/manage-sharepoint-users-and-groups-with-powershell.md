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
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="b3517-103">使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組</span><span class="sxs-lookup"><span data-stu-id="b3517-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="b3517-104">**摘要：**使用 Office 365 PowerShell 來管理 SharePoint Online 使用者、 群組及網站。</span><span class="sxs-lookup"><span data-stu-id="b3517-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="b3517-105">如果您是 SharePoint Online 搭配大型清單的使用者帳戶或群組且想更輕鬆地方法來管理它們，您可以使用 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b3517-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="b3517-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="b3517-106">Before you begin</span></span>

<span data-ttu-id="b3517-p101">本主題中的程序要求您重新連線至 SharePoint Online。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="b3517-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="b3517-109">取得網站、群組和使用者清單</span><span class="sxs-lookup"><span data-stu-id="b3517-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="b3517-p102">開始管理使用者和群組之前，請取得網站、群組和使用者清單。接著，您可以使用此資訊逐步完成本文中的範例。</span><span class="sxs-lookup"><span data-stu-id="b3517-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="b3517-112">取得網站的清單</span><span class="sxs-lookup"><span data-stu-id="b3517-112">Get a list of sites</span></span>

<span data-ttu-id="b3517-113">使用這個命令，來取得在您的租用戶中網站的清單︰</span><span class="sxs-lookup"><span data-stu-id="b3517-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="b3517-114">取得群組的清單</span><span class="sxs-lookup"><span data-stu-id="b3517-114">Get a list of groups</span></span>

<span data-ttu-id="b3517-115">使用這個命令，來取得在您的租用戶中群組的清單︰</span><span class="sxs-lookup"><span data-stu-id="b3517-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="b3517-116">取得使用者的清單</span><span class="sxs-lookup"><span data-stu-id="b3517-116">Get a list of users</span></span>

<span data-ttu-id="b3517-117">使用這個命令，來取得在您的租用戶中使用者的清單︰</span><span class="sxs-lookup"><span data-stu-id="b3517-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="b3517-118">將使用者新增至「網站集合系統管理員」群組</span><span class="sxs-lookup"><span data-stu-id="b3517-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="b3517-p103">您可以使用**組 SPOUser**命令將使用者新增至網站集合上的網站集合管理員清單。這是語法的外觀：</span><span class="sxs-lookup"><span data-stu-id="b3517-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="b3517-121">本範例會使用變數來儲存值和指令碼中有附註 (例如"<!--This is the Tenant Name…-->") 可協助您了解這些值應該是。</span><span class="sxs-lookup"><span data-stu-id="b3517-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="b3517-122">例如，這組命令新增 Opal Castillo (使用者名稱 opalc) 清單的網站集合管理員對 contoso1 租用中 ContosoTest 網站集合：</span><span class="sxs-lookup"><span data-stu-id="b3517-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="b3517-123">您可以將上述命令實際剪貼至 [記事本]，將 $tenant、$site 和 $user 的變數值，變更為環境中的實際值，再將其貼至 SharePoint Online 管理命令介面視窗內。</span><span class="sxs-lookup"><span data-stu-id="b3517-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="b3517-124">將使用者新增至其他「網站集合系統管理員」群組</span><span class="sxs-lookup"><span data-stu-id="b3517-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="b3517-p104">在此工作，我們將使用**Add-spouser**命令來將使用者新增至網站集合上的 SharePoint 群組。這是語法的外觀：</span><span class="sxs-lookup"><span data-stu-id="b3517-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

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

<span data-ttu-id="b3517-127">例如，我們將新增 Glen 猜 (使用者名稱 glenr) 至 contoso1 租用中的 ContosoTest 網站集合的稽核者群組：</span><span class="sxs-lookup"><span data-stu-id="b3517-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="b3517-128">建立網站集合群組</span><span class="sxs-lookup"><span data-stu-id="b3517-128">Create a site collection group</span></span>

<span data-ttu-id="b3517-p105">您可以使用**Set-spositegroup**命令建立新的 SharePoint 群組並將其新增至 ContosoTest 網站集合。這是語法的外觀：</span><span class="sxs-lookup"><span data-stu-id="b3517-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

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
> <span data-ttu-id="b3517-p106">您必須在引號括住空格的任何字串。群組內容，例如權限層級可使用 **-Set-spositegroup** cmdlet 更新版本進行更新。</span><span class="sxs-lookup"><span data-stu-id="b3517-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="b3517-133">例如，我們將稽核者群組新增僅供檢視權限 contoso1 租用中 Contoso 測試網站集合：</span><span class="sxs-lookup"><span data-stu-id="b3517-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="b3517-134">從群組中移除使用者</span><span class="sxs-lookup"><span data-stu-id="b3517-134">Remove users from a group</span></span>

<span data-ttu-id="b3517-p107">有時，您必須從某個網站甚至所有網站中移除使用者。可能是員工從某個部門調到另一個部門，或離開公司。您可以使用 UI，輕鬆地針對某位員工進行這項作業，但是要將整個部門從某個網站移至另一個網站時，就沒有那麼簡單了。</span><span class="sxs-lookup"><span data-stu-id="b3517-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="b3517-p108">不過所使用的 SharePoint Online 管理命令介面和 CSV 檔案，這是快速又簡單。在此工作，您將使用 Windows PowerShell 移除使用者從網站集合安全性群組。然後您可使用 CSV 檔案並從不同的網站移除大量使用者。</span><span class="sxs-lookup"><span data-stu-id="b3517-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="b3517-p109">我們將使用**Remove-spouser**命令以從網站集合群組中移除單一 Office 365 使用者剛才，因此我們可以看到命令語法。以下是語法的外觀：</span><span class="sxs-lookup"><span data-stu-id="b3517-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

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

<span data-ttu-id="b3517-143">例如，我們 Bobby Overby 從群組中移除網站集合稽核者 contoso1 租用中 Contoso 測試網站集合中：</span><span class="sxs-lookup"><span data-stu-id="b3517-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="b3517-p110">假設我們想要從 Bobby 所在的所有群組中移除 Bobby。作法如下：</span><span class="sxs-lookup"><span data-stu-id="b3517-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="b3517-p111">這只是顯示作法。除非您真地必須從每個群組中移除使用者 (例如，如果使用者離開公司)，否則不應執行此命令。</span><span class="sxs-lookup"><span data-stu-id="b3517-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="b3517-148">自動化管理大型使用者和群組清單</span><span class="sxs-lookup"><span data-stu-id="b3517-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="b3517-p112">若要將大量的帳戶新增至 SharePoint 網站和授與權限，您可以使用 Office 365 系統管理中心、 個別的 PowerShell 命令或 PowerShell CSV 檔案。這些選擇的 CSV 檔案會是最快的方法來自動化這項工作。</span><span class="sxs-lookup"><span data-stu-id="b3517-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="b3517-p113">基本程序是建立具有標頭 （欄） 的 Windows PowerShell 指令碼需要的參數與相對的 CSV 檔案。您可以輕鬆地在 Excel 中建立這類清單並再將它匯出為 CSV 檔案。然後，您可以使用 Windows PowerShell 指令碼來逐一記錄 （列） 的 CSV 檔案並將使用者新增至群組和網站群組。</span><span class="sxs-lookup"><span data-stu-id="b3517-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="b3517-p114">例如，建立 CSV 檔案來定義一組網站集合、群組和權限。接下來，會建立 CSV 檔案以將使用者填入群組中。最後，建立和執行可建立和填入群組的簡單 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="b3517-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="b3517-157">第一個 CSV 檔案會將一個或多個群組新增至一個或多個網站集合，而其結構如下：</span><span class="sxs-lookup"><span data-stu-id="b3517-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="b3517-158">標頭：</span><span class="sxs-lookup"><span data-stu-id="b3517-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="b3517-159">項目：</span><span class="sxs-lookup"><span data-stu-id="b3517-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="b3517-160">範例檔案如下：</span><span class="sxs-lookup"><span data-stu-id="b3517-160">Here is an example file:</span></span>

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

<span data-ttu-id="b3517-161">第二個 CSV 檔案會將一個或多個使用者新增至一個或多個群組，而其結構如下：</span><span class="sxs-lookup"><span data-stu-id="b3517-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="b3517-162">標頭：</span><span class="sxs-lookup"><span data-stu-id="b3517-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="b3517-163">項目：</span><span class="sxs-lookup"><span data-stu-id="b3517-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="b3517-164">範例檔案如下：</span><span class="sxs-lookup"><span data-stu-id="b3517-164">Here is an example file:</span></span>

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

<span data-ttu-id="b3517-p115">下一個步，您必須將這兩個 CSV 檔案儲存至磁碟機。以下的命令會使用這兩個 CSV 檔案，來新增權限和群組成員︰</span><span class="sxs-lookup"><span data-stu-id="b3517-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="b3517-p116">指令碼會匯入 CSV 檔案內容與使用中的欄 （以粗體） 的值填入**新增 Get-spositegroup**和**Add-spouser**命令的參數。在我們的範例中，我們會將此儲存至磁碟機 C、 但儘想儲存它。</span><span class="sxs-lookup"><span data-stu-id="b3517-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="b3517-p117">現在，請使用相同的 CSV 檔案，來移除不同網站中數個群組的一群人。命令如下：</span><span class="sxs-lookup"><span data-stu-id="b3517-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="b3517-171">產生使用者報告</span><span class="sxs-lookup"><span data-stu-id="b3517-171">Generate user reports</span></span>

<span data-ttu-id="b3517-p118">您可能會想要取得許多網站的簡單報告，並顯示那些網站的使用者、其權限等級及其他內容。語法如下：</span><span class="sxs-lookup"><span data-stu-id="b3517-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="b3517-p119">這會取得下列三個網站的資料並寫入本機磁碟上的文字檔案。請注意，參數 – Append 會將新的內容新增至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="b3517-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="b3517-176">例如，讓我們在 Contoso1 租用戶的 ContosoTest、TeamSite01 和 Project01 網站上執行報表：</span><span class="sxs-lookup"><span data-stu-id="b3517-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="b3517-p120">請注意我們需要變更 **$site**變數。**$Tenant**變數會保留其值之命令的所有三個執行透過。</span><span class="sxs-lookup"><span data-stu-id="b3517-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="b3517-p121">不過，如果您想要對每個網站執行這項作業，該怎麼辦？使用此命令，便可執行這項作業，無需鍵入所有這些網站：</span><span class="sxs-lookup"><span data-stu-id="b3517-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="b3517-p122">這份報告是相當簡單，您可以新增更多的程式碼來建立更多特定報告或報告包含更多詳細的資訊。但是這應讓您瞭解如何使用 SharePoint Online 管理命令介面來管理 SharePoint Online 環境中的使用者。</span><span class="sxs-lookup"><span data-stu-id="b3517-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="b3517-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3517-183">See also</span></span>

[<span data-ttu-id="b3517-184">連線至 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3517-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="b3517-185">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b3517-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="b3517-186">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="b3517-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b3517-187">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3517-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

