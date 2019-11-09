---
title: 建立 SharePoint Online 網站並新增使用者使用 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 來建立新的 SharePoint Online 網站，並再將使用者和群組新增至這些網站。
ms.openlocfilehash: 17f3a6a6444ced647723f417145c6466dd8d284b
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077992"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="f6a3b-103">建立 SharePoint Online 網站並新增使用者使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6a3b-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="f6a3b-104">**摘要：** 使用 Office 365 PowerShell 來建立新的 SharePoint Online 網站，並再將使用者和群組新增至這些網站。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="f6a3b-105">當您使用 Office 365 PowerShell 建立 SharePoint Online 網站以及新增使用者時，您可以快速且重複執行速度快多了比您可以在 Office 356 系統管理中心中的工作。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-105">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center.</span></span> <span data-ttu-id="f6a3b-106">您也可以執行不可以在 Office 356 系統管理中心中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-106">You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="f6a3b-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="f6a3b-107">Before you begin</span></span>

<span data-ttu-id="f6a3b-108">本主題中的程序需要您連線至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-108">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="f6a3b-109">如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="f6a3b-109">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="f6a3b-110">步驟 1： 建立新的網站集合使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6a3b-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="f6a3b-111">建立使用 Office 365 PowerShell 與您使用的範例程式碼提供和 [記事本] 建立.csv 檔案的多個站台。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-111">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="f6a3b-112">此程序，您將會取代與您自己的網站和租用戶特定資訊的括號中所示的版面配置區資訊。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-112">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="f6a3b-113">此程序可讓您建立單一檔案，並執行單一的 Office 365 PowerShell 命令，會使用該檔案。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-113">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="f6a3b-114">這可讓鎖死和可攜式所採取的動作，並且消除數量，如果可能來自 SharePoint Online 管理命令介面中鍵入命令很長的非全部的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-114">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="f6a3b-115">有兩個部分此程序。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-115">There are two parts to this procedure.</span></span> <span data-ttu-id="f6a3b-116">您將在第一次建立.csv 檔案，並接著您會參照使用 Office 365 PowerShell，將會使用它的內容來建立網站的.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-116">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="f6a3b-117">Office 365 PowerShell cmdlet 會匯入之.csv 檔案，並將其傳送至大括號內迴圈，讀取檔案的第一行作為資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-117">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers.</span></span> <span data-ttu-id="f6a3b-118">Office 365 PowerShell cmdlet 接著逐一查看剩餘的記錄、 建立新的網站集合，每一筆記錄，並指派根據資料行標頭網站集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-118">The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="f6a3b-119">建立.csv 檔案</span><span class="sxs-lookup"><span data-stu-id="f6a3b-119">Create a .csv file</span></span>

1. <span data-ttu-id="f6a3b-120">開啟 [記事本]，然後貼上下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="f6a3b-121">*租用戶*是您的租用戶的名稱，以及*擁有者*是收件者您租用戶上之使用者的使用者名稱您想要授與的主要網站集合管理員角色。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="f6a3b-122">（您可以在按 Ctrl + H 時更快速地大量取代的情況下，您在使用 [記事本]）。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="f6a3b-123">在桌面上將檔案儲存為**SiteCollections.csv**。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="f6a3b-124">在您使用 this 或任何其他.csv 或 Windows PowerShell 指令碼檔案之前，它會是很好的作法，以確保沒有任何無關或非列印字元。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-124">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="f6a3b-125">開啟的檔案，在 Word 中，然後在功能區中，按一下 [段落] 圖示，顯示非列印字元。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-125">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="f6a3b-126">應該會有任何無關的非列印字元。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-126">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="f6a3b-127">例如，應該超出檔案結尾處的最後一個沒有段落標記。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-127">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="f6a3b-128">執行 Windows PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="f6a3b-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="f6a3b-129">在 Windows PowerShell 提示字元處，輸入或複製並貼上下列的指令程式，並按 Enter 鍵：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="f6a3b-130">其中*MyAlias*等於您的使用者別名。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="f6a3b-131">等待重新顯示的 Windows PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-131">Wait for the Windows PowerShell prompt to reappear.</span></span> <span data-ttu-id="f6a3b-132">它可能需要幾分鐘或兩個。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-132">It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="f6a3b-133">在 Windows PowerShell 提示字元處，輸入或複製並貼上下列的指令程式，並按 Enter 鍵：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="f6a3b-134">附註] 清單中新的網站集合。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-134">Note the new site collections in the list.</span></span> <span data-ttu-id="f6a3b-135">您應該會看到下列網站集合： **contosotest**、 **TeamSite01**、 **Blog01**和**Project01**</span><span class="sxs-lookup"><span data-stu-id="f6a3b-135">You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="f6a3b-136">這樣就完成了。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-136">That’s it.</span></span> <span data-ttu-id="f6a3b-137">您已建立使用您建立的.csv 檔案的多個網站集合與單一 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-137">You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet.</span></span> <span data-ttu-id="f6a3b-138">您現在可以開始建立，並將使用者指派給這些網站。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-138">You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="f6a3b-139">步驟 2： 新增使用者和群組</span><span class="sxs-lookup"><span data-stu-id="f6a3b-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="f6a3b-140">現在您將建立的使用者，並將它們新增至網站集合群組。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-140">Now you’re going to create users and add them to a site collection group.</span></span> <span data-ttu-id="f6a3b-141">您接著使用.csv 檔案大量上傳新的群組和使用者。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-141">You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="f6a3b-142">下列程序假設您已成功建立網站集合 contosotest、 TeamSite01、 Blog01 和 Project01。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="f6a3b-143">建立.csv 和.ps1 檔案</span><span class="sxs-lookup"><span data-stu-id="f6a3b-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="f6a3b-144">開啟 [記事本]，然後貼上下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-144">Open Notepad, and paste the following text block into it:</span></span><br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/><span data-ttu-id="f6a3b-145">其中*的租用戶*等於您的租用戶名稱。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="f6a3b-146">**Groupsandpermissions.csv 儲存至**將檔案儲存至您的桌面。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="f6a3b-147">開啟 [記事本] 的新執行個體，並貼上下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/><span data-ttu-id="f6a3b-148">其中*的租用戶*等於您的租用戶名稱，而*username*等於現有使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="f6a3b-149">**Users.csv 儲存至**將檔案儲存至您的桌面。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="f6a3b-150">開啟 [記事本] 的新執行個體，並貼上下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="f6a3b-151">其中 MyAlias 等於目前已登入使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="f6a3b-152">將檔案儲存到您的桌面，為**UsersAndGroups.ps1**。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-152">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="f6a3b-153">這是一個簡單的 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-153">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="f6a3b-154">您現在準備好執行 UsersAndGroup.ps1 指令碼，將使用者和群組新增至多個網站集合。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="f6a3b-155">執行 UsersAndGroups.ps1 指令碼</span><span class="sxs-lookup"><span data-stu-id="f6a3b-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="f6a3b-156">會傳回 SharePoint Online 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="f6a3b-157">在 Windows PowerShell 提示字元處，輸入或複製並貼上下行，並按 Enter 鍵：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="f6a3b-158">在確認提示，請按**Y**。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="f6a3b-159">在 Windows PowerShell 命令提示字元、 類型或複製並貼上下列項目，然後按 Enter 鍵：</span><span class="sxs-lookup"><span data-stu-id="f6a3b-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="f6a3b-160">其中*MyAlias*等於您的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="f6a3b-161">等待要傳回才可繼續的提示。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-161">Wait for the prompt to return before moving on.</span></span> <span data-ttu-id="f6a3b-162">首先，您會看到顯示他們所建立的群組。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-162">You will first see the groups appear as they are created.</span></span> <span data-ttu-id="f6a3b-163">然後您會看到重複也當簡報加入使用者的 [群組] 清單。</span><span class="sxs-lookup"><span data-stu-id="f6a3b-163">Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6a3b-164">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6a3b-164">See also</span></span>

[<span data-ttu-id="f6a3b-165">連線至 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6a3b-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="f6a3b-166">管理 SharePoint Online 網站群組 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6a3b-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="f6a3b-167">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="f6a3b-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f6a3b-168">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6a3b-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

