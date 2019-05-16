---
title: 使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
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
ms.openlocfilehash: 194486f539593215b8f8a17c04e3d4f499077c65
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068819"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="59bfc-103">使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組</span><span class="sxs-lookup"><span data-stu-id="59bfc-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="59bfc-104">**摘要：** 使用 Office 365 PowerShell 來管理 SharePoint Online 使用者、 群組及網站。</span><span class="sxs-lookup"><span data-stu-id="59bfc-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="59bfc-105">如果您是使用大型清單的使用者帳戶或群組的運作，以及想要輕鬆地進行管理 SharePoint Online 系統管理員，您可以使用 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="59bfc-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="59bfc-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="59bfc-106">Before you begin</span></span>

<span data-ttu-id="59bfc-107">本主題中的程序需要您連線至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="59bfc-107">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="59bfc-108">如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="59bfc-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="59bfc-109">取得網站、 群組和使用者清單</span><span class="sxs-lookup"><span data-stu-id="59bfc-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="59bfc-110">我們開始管理使用者和群組之前，您需要取得您的網站、 群組及使用者的清單。</span><span class="sxs-lookup"><span data-stu-id="59bfc-110">Before we start to manage users and groups, you need to get lists of your sites, groups, and users.</span></span> <span data-ttu-id="59bfc-111">您然後可以使用這項資訊來完成本文中的範例。</span><span class="sxs-lookup"><span data-stu-id="59bfc-111">You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="59bfc-112">取得網站清單</span><span class="sxs-lookup"><span data-stu-id="59bfc-112">Get a list of sites</span></span>

<span data-ttu-id="59bfc-113">取得在您的租用戶使用此命令中的網站清單：</span><span class="sxs-lookup"><span data-stu-id="59bfc-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="59bfc-114">取得群組的清單</span><span class="sxs-lookup"><span data-stu-id="59bfc-114">Get a list of groups</span></span>

<span data-ttu-id="59bfc-115">取得群組的清單中您的租用戶使用此命令：</span><span class="sxs-lookup"><span data-stu-id="59bfc-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="59bfc-116">取得使用者的清單</span><span class="sxs-lookup"><span data-stu-id="59bfc-116">Get a list of users</span></span>

<span data-ttu-id="59bfc-117">取得使用者的清單中您的租用戶使用此命令：</span><span class="sxs-lookup"><span data-stu-id="59bfc-117">Get a list of the users in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="59bfc-118">將使用者新增至網站集合管理員群組</span><span class="sxs-lookup"><span data-stu-id="59bfc-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="59bfc-119">您可以用於**設定 SPOUser**命令將使用者新增至網站集合上的網站集合管理員清單。</span><span class="sxs-lookup"><span data-stu-id="59bfc-119">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection.</span></span> <span data-ttu-id="59bfc-120">這是如何的語法看起來：</span><span class="sxs-lookup"><span data-stu-id="59bfc-120">This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="59bfc-121">若要使用這些命令，取代取代引號，包括 < 和 > 字元，以正確的名稱內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="59bfc-121">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="59bfc-122">例如，這組命令新增 Opal Castillo (使用者名稱 opalc) 的網站集合管理員清單上 contoso1 租用的 ContosoTest 網站集合：</span><span class="sxs-lookup"><span data-stu-id="59bfc-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="59bfc-123">您可以複製及將這些命令貼到 [記事本]、 $tenant、 $site，及 $user 變更變數值實際值從您的環境，並再將此貼到您的 SharePoint Online 管理命令介面視窗，並執行。</span><span class="sxs-lookup"><span data-stu-id="59bfc-123">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="59bfc-124">將使用者新增至其他網站集合管理員群組</span><span class="sxs-lookup"><span data-stu-id="59bfc-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="59bfc-125">在這個工作中，我們將使用**Add-spouser**命令，將使用者新增至 SharePoint 群組網站集合上。</span><span class="sxs-lookup"><span data-stu-id="59bfc-125">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="59bfc-126">例如，讓我們將新增 Glen Rife (使用者名稱 glenr) 至 contoso1 租用的 ContosoTest 網站集合上 「 稽核員 」 群組：</span><span class="sxs-lookup"><span data-stu-id="59bfc-126">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="59bfc-127">建立網站集合群組</span><span class="sxs-lookup"><span data-stu-id="59bfc-127">Create a site collection group</span></span>

<span data-ttu-id="59bfc-128">您可以使用**Set-spositegroup**命令建立新的 SharePoint 群組，並將其新增至的 ContosoTest 網站集合。</span><span class="sxs-lookup"><span data-stu-id="59bfc-128">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="59bfc-129">群組的內容，例如權限等級，可以稍後更新，使用**Set-spositegroup** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="59bfc-129">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="59bfc-130">例如，讓我們將新增僅供檢視權限與稽核員 」 群組至 contoso1 租用的 Contoso Test 網站集合：</span><span class="sxs-lookup"><span data-stu-id="59bfc-130">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="59bfc-131">從群組中移除使用者</span><span class="sxs-lookup"><span data-stu-id="59bfc-131">Remove users from a group</span></span>

<span data-ttu-id="59bfc-132">有時候，您必須從站台或甚至是所有網站中移除使用者。</span><span class="sxs-lookup"><span data-stu-id="59bfc-132">Sometimes you have to remove a user from a site or even all sites.</span></span> <span data-ttu-id="59bfc-133">可能是員工將從一個部門移至另一個，或離開公司。</span><span class="sxs-lookup"><span data-stu-id="59bfc-133">Perhaps the employee moves from one division to another or leaves the company.</span></span> <span data-ttu-id="59bfc-134">您可以這麼一個員工輕鬆地在 UI 中，但無法輕鬆完成此工作時您有一個站台間移動完成的部門。</span><span class="sxs-lookup"><span data-stu-id="59bfc-134">You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="59bfc-135">不過藉由使用 SharePoint Online 管理命令介面和 CSV 檔案，這樣既快速又簡單。</span><span class="sxs-lookup"><span data-stu-id="59bfc-135">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="59bfc-136">在這個工作中，您會使用 Windows PowerShell 從網站集合安全性] 群組中移除使用者。</span><span class="sxs-lookup"><span data-stu-id="59bfc-136">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="59bfc-137">然後使用 CSV 檔，並從不同的網站移除大量的使用者。</span><span class="sxs-lookup"><span data-stu-id="59bfc-137">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="59bfc-138">我們將使用**Remove-spouser**命令來移除單一 Office 365 使用者網站集合群組只是因此我們可以看到命令語法。</span><span class="sxs-lookup"><span data-stu-id="59bfc-138">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="59bfc-139">以下是如何的語法看起來：</span><span class="sxs-lookup"><span data-stu-id="59bfc-139">Here is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="59bfc-140">例如，讓我們先移除 Bobby Overby 從 contoso1 租用的 Contoso Test 網站集合的網站集合稽核員 」 群組：</span><span class="sxs-lookup"><span data-stu-id="59bfc-140">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="59bfc-141">假設您想要移除 Bobby 他目前是中的所有群組。</span><span class="sxs-lookup"><span data-stu-id="59bfc-141">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="59bfc-142">以下是如何我們會這麼做：</span><span class="sxs-lookup"><span data-stu-id="59bfc-142">Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="59bfc-143">這只是範例。</span><span class="sxs-lookup"><span data-stu-id="59bfc-143">This is just an example.</span></span> <span data-ttu-id="59bfc-144">除非您真的有使用者移除每個群組，例如，如果使用者離開公司，您不應執行此命令。</span><span class="sxs-lookup"><span data-stu-id="59bfc-144">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="59bfc-145">自動化管理大型使用者和群組清單</span><span class="sxs-lookup"><span data-stu-id="59bfc-145">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="59bfc-146">若要將大量帳戶新增至 SharePoint 網站，並授與權限，您可以使用 Microsoft 365 系統管理中心，個別的 PowerShell 命令或 PowerShell CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="59bfc-146">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="59bfc-147">這些選項的 CSV 檔案是自動執行此工作最快的方法。</span><span class="sxs-lookup"><span data-stu-id="59bfc-147">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="59bfc-148">基本程序會建立具有標頭 （資料行），會對應至 Windows PowerShell 指令碼所需的參數的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="59bfc-148">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="59bfc-149">您可以輕鬆地在 Excel 中建立此類清單，並再將它匯出為 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="59bfc-149">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="59bfc-150">然後，您可以使用 Windows PowerShell 指令碼來逐一記錄 （資料列） 在 CSV 檔案中，將使用者新增至群組及網站群組。</span><span class="sxs-lookup"><span data-stu-id="59bfc-150">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="59bfc-151">例如，讓我們先建立 CSV 檔案，以定義一組網站集合、 群組和權限。</span><span class="sxs-lookup"><span data-stu-id="59bfc-151">For example, let’s create a CSV file to define a group of site collections, groups, and permissions.</span></span> <span data-ttu-id="59bfc-152">接下來，我們會建立 CSV 檔案，以填入與使用者群組。</span><span class="sxs-lookup"><span data-stu-id="59bfc-152">Next, we will create a CSV file to populate the groups with users.</span></span> <span data-ttu-id="59bfc-153">最後，我們會建立並執行簡單的 Windows PowerShell 指令碼會建立並填入群組。</span><span class="sxs-lookup"><span data-stu-id="59bfc-153">Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="59bfc-154">第一個 CSV 檔會將一個或多個群組新增至一或多個網站集合中，而其結構如下：</span><span class="sxs-lookup"><span data-stu-id="59bfc-154">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="59bfc-155">標頭：</span><span class="sxs-lookup"><span data-stu-id="59bfc-155">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="59bfc-156">項目：</span><span class="sxs-lookup"><span data-stu-id="59bfc-156">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="59bfc-157">以下是範例檔案：</span><span class="sxs-lookup"><span data-stu-id="59bfc-157">Here is an example file:</span></span>

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

<span data-ttu-id="59bfc-158">第二個 CSV 檔案會將一或多位使用者新增至一或多個群組，並將其結構如下：</span><span class="sxs-lookup"><span data-stu-id="59bfc-158">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="59bfc-159">標頭：</span><span class="sxs-lookup"><span data-stu-id="59bfc-159">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="59bfc-160">項目：</span><span class="sxs-lookup"><span data-stu-id="59bfc-160">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="59bfc-161">以下是範例檔案：</span><span class="sxs-lookup"><span data-stu-id="59bfc-161">Here is an example file:</span></span>

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

<span data-ttu-id="59bfc-162">下一個步驟中，您必須具有兩個 CSV 檔案儲存至您的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="59bfc-162">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="59bfc-163">以下是使用這兩個 CSV 檔案的範例命令，以新增權限和群組成員資格：</span><span class="sxs-lookup"><span data-stu-id="59bfc-163">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="59bfc-164">指令碼會匯入 CSV 檔案的內容和資料行中使用的值來填入**新 SPOSiteGroup**和**Add-spouser**命令的參數。</span><span class="sxs-lookup"><span data-stu-id="59bfc-164">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="59bfc-165">在我們的範例中，我們會將此儲存到 theO365Admin 資料夾，磁碟機 C，但您可以將它儲存您需要的地方。</span><span class="sxs-lookup"><span data-stu-id="59bfc-165">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="59bfc-166">現在，我們使用相同的 CSV 檔的不同站台中移除一堆數個群組的人員。</span><span class="sxs-lookup"><span data-stu-id="59bfc-166">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="59bfc-167">範例命令如下：</span><span class="sxs-lookup"><span data-stu-id="59bfc-167">Here is an example command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="59bfc-168">產生使用者報告</span><span class="sxs-lookup"><span data-stu-id="59bfc-168">Generate user reports</span></span>

<span data-ttu-id="59bfc-169">您可能想要取得的簡單報告的幾個網站，並顯示這些網站、 其權限層級和其他內容的使用者。</span><span class="sxs-lookup"><span data-stu-id="59bfc-169">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties.</span></span> <span data-ttu-id="59bfc-170">這是如何的語法看起來：</span><span class="sxs-lookup"><span data-stu-id="59bfc-170">This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="59bfc-171">這將擷取這些三個網站的資料，並寫入本機磁碟機上的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="59bfc-171">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="59bfc-172">請注意，參數 – Append 會將新的內容新增至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="59bfc-172">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="59bfc-173">例如，讓我們執行報告的 ContosoTest、 TeamSite01 和 Project01 網站上 Contoso1 租用戶：</span><span class="sxs-lookup"><span data-stu-id="59bfc-173">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="59bfc-174">請注意，我們有變更僅 **$site**變數。</span><span class="sxs-lookup"><span data-stu-id="59bfc-174">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="59bfc-175">**$Tenant**變數會保留其值，透過命令的所有三個執行。</span><span class="sxs-lookup"><span data-stu-id="59bfc-175">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="59bfc-176">不過，如果您想要這麼做的每個網站？</span><span class="sxs-lookup"><span data-stu-id="59bfc-176">However, what if you wanted to do this for every site?</span></span> <span data-ttu-id="59bfc-177">無需鍵入所有這些網站使用下列命令，您可以執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="59bfc-177">You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="59bfc-178">這份報告是相當簡單，以及您可以新增更多的程式碼來建立更具體的報表或報表，包括更詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="59bfc-178">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="59bfc-179">但這應讓您了解如何使用 SharePoint Online 管理命令介面來管理 SharePoint Online 環境中的使用者。</span><span class="sxs-lookup"><span data-stu-id="59bfc-179">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="59bfc-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59bfc-180">See also</span></span>

[<span data-ttu-id="59bfc-181">連線至 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="59bfc-181">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="59bfc-182">使用 Office 365 PowerShell 管理 SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="59bfc-182">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="59bfc-183">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="59bfc-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="59bfc-184">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="59bfc-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

