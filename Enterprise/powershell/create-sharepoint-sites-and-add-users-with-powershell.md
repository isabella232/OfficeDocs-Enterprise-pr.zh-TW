---
title: 使用 Office 365 建立 SharePoint Online 網站及新增使用者 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要：使用 Office 365 PowerShell 建立新的 SharePoint Online 網站，然後將使用者和群組新增至這些網站。
ms.openlocfilehash: 1fc9192ed27bfd097ac770b53837fb8ba2eb062d
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004696"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="e4b7b-103">使用 Office 365 建立 SharePoint Online 網站及新增使用者 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4b7b-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

<span data-ttu-id="e4b7b-104">當您使用 Office 365 PowerShell 建立 SharePoint 的線上網站和新增使用者時，您可以快速且重複執行工作，其速度會比您在 Microsoft 356 系統管理中心中更快。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-104">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Microsoft 356 admin center.</span></span> <span data-ttu-id="e4b7b-105">您也可以執行不可能在 Office 356 系統管理中心中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-105">You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="e4b7b-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="e4b7b-106">Before you begin</span></span>

<span data-ttu-id="e4b7b-107">本主題中的程式需要您連線至 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-107">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="e4b7b-108">如需相關指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="e4b7b-108">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="e4b7b-109">步驟1：使用 Office 365 PowerShell 建立新的網站集合</span><span class="sxs-lookup"><span data-stu-id="e4b7b-109">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="e4b7b-110">使用 Office 365 PowerShell 和 .csv 檔案建立多個網站，該檔案是使用所提供的範例程式碼和記事本建立的。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-110">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="e4b7b-111">在此程式中，您將會以您自己的網站與租使用者特有的資訊，取代方括弧中所顯示的預留位置資訊。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-111">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="e4b7b-112">此程式可讓您建立單一檔，並執行使用該檔案的單一 Office 365 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-112">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="e4b7b-113">這會使得同時採取可重複和可遷移的動作，並避免在 SharePoint 線上管理命令介面中輸入長命令的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-113">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="e4b7b-114">此程式有兩個部分。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-114">There are two parts to this procedure.</span></span> <span data-ttu-id="e4b7b-115">首先，您會建立 .csv 檔案，然後您會使用 Office 365 PowerShell 參照該 .csv 檔案，該檔案會使用其內容來建立網站。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-115">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="e4b7b-116">Office 365 PowerShell Cmdlet 會匯入 .csv 檔案，並將其管線傳遞到大括弧中的迴圈，該括弧會將檔案的第一行讀取為欄標頭。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-116">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span></span> <span data-ttu-id="e4b7b-117">然後，Office 365 PowerShell Cmdlet 會逐一查看餘下的記錄，為每個記錄建立新的網站集合，並根據欄標題指派網站集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-117">The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="e4b7b-118">建立 .csv 檔案</span><span class="sxs-lookup"><span data-stu-id="e4b7b-118">Create a .csv file</span></span>

1. <span data-ttu-id="e4b7b-119">開啟 [記事本]，並在其中貼上下列文字區塊：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-119">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="e4b7b-120">其中*租*使用者是您租使用者的名稱，而*擁有*者是您想要授與主要網站集合管理員角色的承租人使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-120">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="e4b7b-121">（您可以在使用 [記事本] 以更快的速度大小時，按 Ctrl + H。）</span><span class="sxs-lookup"><span data-stu-id="e4b7b-121">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="e4b7b-122">將檔案儲存在您的桌面機**SiteCollections.csv**。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-122">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="e4b7b-123">在使用此或任何其他 .csv 或 Windows PowerShell 腳本檔案之前，請務必確定沒有多餘或非列印字元。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-123">Before you use this or any other .csv or Windows PowerShell script file, it's a good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="e4b7b-124">在 Word 中開啟檔案，然後在功能區中，按一下段落圖示以顯示非列印字元。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-124">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="e4b7b-125">不應有多餘的非列印字元。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-125">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="e4b7b-126">例如，在檔案結尾的最後一個段落旁邊不應有任何段落標記。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-126">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="e4b7b-127">執行 Windows PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="e4b7b-127">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="e4b7b-128">在 [Windows PowerShell 提示字元處，輸入或複製並貼上下列命令，然後按 Enter：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-128">At the Windows PowerShell prompt, type or copy and paste the following command, and press Enter:</span></span><br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="e4b7b-129">其中*MyAlias*等於您的使用者別名。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-129">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="e4b7b-130">等候 Windows PowerShell 提示重新顯示。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-130">Wait for the Windows PowerShell prompt to reappear.</span></span> <span data-ttu-id="e4b7b-131">可能需要一兩分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-131">It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="e4b7b-132">在 [Windows PowerShell 提示字元處，輸入或複製並貼上下列 Cmdlet，然後按 Enter：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-132">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="e4b7b-133">請注意清單中的新網站集合。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-133">Note the new site collections in the list.</span></span> <span data-ttu-id="e4b7b-134">使用我們的範例 CSV 檔案，您會看到下列網站集合： **TeamSite01**、 **Blog01**、 **Project01**及**Community01**</span><span class="sxs-lookup"><span data-stu-id="e4b7b-134">Using our example CSV file, you would see the following site collections: **TeamSite01**, **Blog01**, **Project01**, and **Community01**</span></span>

<span data-ttu-id="e4b7b-135">這樣就完成了。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-135">That’s it.</span></span> <span data-ttu-id="e4b7b-136">您已使用所建立的 .csv 檔和單一 Windows PowerShell 命令，建立多個網站集合。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-136">You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell command.</span></span> <span data-ttu-id="e4b7b-137">您現在已準備好建立及指派使用者至這些網站。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-137">You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="e4b7b-138">步驟2：新增使用者和群組</span><span class="sxs-lookup"><span data-stu-id="e4b7b-138">Step 2: Add users and groups</span></span>

<span data-ttu-id="e4b7b-139">現在您會建立使用者，並將其新增至網站集合群組。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-139">Now you’re going to create users and add them to a site collection group.</span></span> <span data-ttu-id="e4b7b-140">然後，您會使用 .csv 檔案大量上傳新的群組和使用者。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-140">You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="e4b7b-141">下列程式會繼續使用範例網站 TeamSite01、Blog01、Project01 及 Community01。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-141">The following procedures continue using the example sites TeamSite01, Blog01, Project01, and Community01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="e4b7b-142">建立 .csv 和 ps1 檔</span><span class="sxs-lookup"><span data-stu-id="e4b7b-142">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="e4b7b-143">開啟 [記事本]，並在其中貼上下列文字區塊：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-143">Open Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="e4b7b-144">*承租人*會等於您的租使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-144">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="e4b7b-145">將檔案儲存至您的桌面**GroupsAndPermissions.csv**。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-145">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="e4b7b-146">開啟 [記事本] 的新實例，並將下列文字區塊貼到其中：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-146">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="e4b7b-147">*租*使用者等於您租使用者名稱，而使用者*名稱等於現有*使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-147">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="e4b7b-148">將檔案儲存至您的桌上型電腦（如**使用者 .csv**）。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-148">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="e4b7b-149">開啟 [記事本] 的新實例，並將下列文字區塊貼到其中：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-149">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="e4b7b-150">其中 MyAlias 等於目前登入之使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-150">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="e4b7b-151">將檔案儲存至您的桌面**UsersAndGroups.ps1**。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-151">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="e4b7b-152">這是簡單的 Windows PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-152">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="e4b7b-153">您現在已經準備好執行 UsersAndGroup.ps1 腳本，將使用者和群組新增至多個網站集合。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-153">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="e4b7b-154">Run UsersAndGroups.ps1 script</span><span class="sxs-lookup"><span data-stu-id="e4b7b-154">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="e4b7b-155">回到 SharePoint 線上管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-155">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="e4b7b-156">在 [Windows PowerShell 提示字元處，輸入或複製並貼上下列命令列，然後按 Enter 鍵：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-156">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="e4b7b-157">在確認提示字元處，按**Y**。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-157">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="e4b7b-158">在 [Windows PowerShell 提示字元處，輸入或複製並貼上下列命令，然後按 Enter：</span><span class="sxs-lookup"><span data-stu-id="e4b7b-158">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="e4b7b-159">其中*MyAlias*等於您的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-159">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="e4b7b-160">等待提示傳回後，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-160">Wait for the prompt to return before moving on.</span></span> <span data-ttu-id="e4b7b-161">您會先看到群組出現在建立時。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-161">You will first see the groups appear as they are created.</span></span> <span data-ttu-id="e4b7b-162">接著，當使用者新增時，您會看到 [群組] 清單重複。</span><span class="sxs-lookup"><span data-stu-id="e4b7b-162">Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4b7b-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4b7b-163">See also</span></span>

[<span data-ttu-id="e4b7b-164">連線至 SharePoint 線上 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4b7b-164">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="e4b7b-165">管理 SharePoint Online 網站群組 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4b7b-165">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="e4b7b-166">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="e4b7b-166">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e4b7b-167">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4b7b-167">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

