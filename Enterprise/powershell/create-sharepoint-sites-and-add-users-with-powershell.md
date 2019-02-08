---
title: 使用 Office 365 PowerShell 建立 SharePoint Online 網站並新增使用者
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 建立新的 SharePoint Online 網站，並再新增至這些網站的 [使用者和群組。
ms.openlocfilehash: 61b9338469ed8d01abc76edbf14ed448c3ca00d3
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897166"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="aff45-103">使用 Office 365 PowerShell 建立 SharePoint Online 網站並新增使用者</span><span class="sxs-lookup"><span data-stu-id="aff45-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="aff45-104">**摘要：** 使用 Office 365 PowerShell 建立新的 SharePoint Online 網站，並再新增至這些網站的 [使用者和群組。</span><span class="sxs-lookup"><span data-stu-id="aff45-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="aff45-p101">當您使用 Office 365 PowerShell 來建立 SharePoint Online 網站和新增使用者時，您可以快速且重複地執行工作速度快多了比您可以在 Office 356 系統管理中心。您也可以執行不可以在 Office 356 系統管理中心中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="aff45-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="aff45-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="aff45-107">Before you begin</span></span>

<span data-ttu-id="aff45-p102">本主題中的程序要求您重新連線至 SharePoint Online。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="aff45-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="aff45-110">步驟 1： 建立新的網站集合使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff45-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="aff45-p103">建立多個網站使用 Office 365 PowerShell 與您使用所提供的範例程式碼和 [記事本] 建立的.csv 檔案。此程序，您將會取代您自己的網站和承租人特定資訊的括號中顯示的版面配置區資訊。此程序可讓您建立單一檔案並執行單一的 Office 365 PowerShell 命令會使用該檔案。這讓鎖死和可攜式採取的動作，而且可消除許多，如果可以來自 SharePoint Online 管理命令介面中輸入命令很長的並非所有錯誤。有兩個部分此程序。您將在第一次建立.csv 檔案，並再讓您將會參照使用 Office 365 PowerShell 中會使用其內容建立網站的.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="aff45-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process lets you create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="aff45-p104">Office 365 PowerShell 指令程式會匯入之.csv 檔案並將其傳送至迴圈內的大括弧括會讀取檔案的第一行做為資料行標題。Office 365 PowerShell 指令程式然後逐一查看剩餘的記錄、 建立新的網站集合的每筆記錄，並指派根據資料行標頭之網站集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="aff45-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="aff45-119">建立 .csv 檔案</span><span class="sxs-lookup"><span data-stu-id="aff45-119">Create a .csv file</span></span>

1. <span data-ttu-id="aff45-120">開啟 [記事本]，並貼入下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="aff45-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="aff45-121">其中*租用戶*是您的租用戶名稱及*擁有者*是在您的租用戶其使用者的使用者名稱您想要授與主要網站集合管理員角色。</span><span class="sxs-lookup"><span data-stu-id="aff45-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="aff45-122">（您可以可以按 Ctrl + H 當您使用 [記事本] 速度大量取代）。</span><span class="sxs-lookup"><span data-stu-id="aff45-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="aff45-123">將桌面上的檔案儲存為**SiteCollections.csv**。</span><span class="sxs-lookup"><span data-stu-id="aff45-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="aff45-p105">使用 this 或任何其他.csv 或 Windows PowerShell 指令碼檔案之前，它會是很好的作法以確保沒有任何無關或非列印字元。在 Word 中，並在功能區中開啟檔案，按一下 [段落] 圖示以顯示非列印字元。應該會有任何無關的非列印字元。例如，應超過檔案結尾處的最後一個沒有段落標記。</span><span class="sxs-lookup"><span data-stu-id="aff45-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="aff45-128">執行 Windows PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="aff45-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="aff45-129">在 Windows PowerShell 提示中輸入或複製並貼上下列指令程式，並按 Enter：</span><span class="sxs-lookup"><span data-stu-id="aff45-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="aff45-130">其中*MyAlias*等於您的使用者別名。</span><span class="sxs-lookup"><span data-stu-id="aff45-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="aff45-p106">等待來重新顯現的 Windows PowerShell 提示字元。可能需要數分鐘。</span><span class="sxs-lookup"><span data-stu-id="aff45-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="aff45-133">在 Windows PowerShell 提示中輸入或複製並貼上下列指令程式，並按 Enter：</span><span class="sxs-lookup"><span data-stu-id="aff45-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="aff45-p107">請注意新網站集合清單中。您應該會看到下列網站集合： **contosotest**、 **TeamSite01**、 **Blog01**、 和**Project01**</span><span class="sxs-lookup"><span data-stu-id="aff45-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="aff45-p108">這是它。您已建立使用您所建立之.csv 檔案的多個網站集合和單一 Windows PowerShell cmdlet。您現在準備好建立並將使用者指派給這些網站。</span><span class="sxs-lookup"><span data-stu-id="aff45-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="aff45-139">步驟 2：新增使用者和群組</span><span class="sxs-lookup"><span data-stu-id="aff45-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="aff45-p109">現在，您即將建立使用者，並將他們新增至網站集合群組。您接著將使用 .csv 檔案大量上傳新的群組和使用者。</span><span class="sxs-lookup"><span data-stu-id="aff45-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="aff45-142">下列程序假設您已順利建立網站集合 contosotest、TeamSite01、Blog01 和 Project01。</span><span class="sxs-lookup"><span data-stu-id="aff45-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="aff45-143">建立 .csv 和 .ps1 檔案</span><span class="sxs-lookup"><span data-stu-id="aff45-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="aff45-144">開啟 [記事本]，並貼入下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="aff45-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="aff45-145">其中*租用戶*等於您的租用戶名稱。</span><span class="sxs-lookup"><span data-stu-id="aff45-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="aff45-146">**Groupsandpermissions.csv 儲存至**將檔案儲存至您的桌面。</span><span class="sxs-lookup"><span data-stu-id="aff45-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="aff45-147">開啟新的 [記事本] 執行個體，並貼入下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="aff45-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="aff45-148">其中*租用戶*等於您的租用戶名稱與*username*等於現有使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="aff45-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="aff45-149">**Users.csv 儲存至**將檔案儲存至您的桌面。</span><span class="sxs-lookup"><span data-stu-id="aff45-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="aff45-150">開啟新的 [記事本] 執行個體，並貼入下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="aff45-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="aff45-151">其中 MyAlias 等於目前已登入使用者的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="aff45-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="aff45-p110">為**UsersAndGroups.ps1**將檔案儲存至您的桌面。這是簡易的 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="aff45-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="aff45-154">您現在準備好執行 UsersAndGroup.ps1 指令碼，以將使用者和群組新增至多個網站集合。</span><span class="sxs-lookup"><span data-stu-id="aff45-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="aff45-155">執行 UsersAndGroups.ps1 指令碼</span><span class="sxs-lookup"><span data-stu-id="aff45-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="aff45-156">回到 SharePoint Online 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="aff45-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="aff45-157">在 Windows PowerShell 提示中輸入或複製並貼上下行，並按 Enter：</span><span class="sxs-lookup"><span data-stu-id="aff45-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="aff45-158">確認提示，請按**Y**。</span><span class="sxs-lookup"><span data-stu-id="aff45-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="aff45-159">在 Windows PowerShell 提示字元、 類型或複製和貼上下列項目，然後按 Enter：</span><span class="sxs-lookup"><span data-stu-id="aff45-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="aff45-160">其中*MyAlias*等於您的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="aff45-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="aff45-p111">等待返回提示，再繼續進行。您會先看到在建立群組時出現群組。然後，您會看到在新增使用者時重複群組清單。</span><span class="sxs-lookup"><span data-stu-id="aff45-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="aff45-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aff45-164">See also</span></span>

[<span data-ttu-id="aff45-165">連線至 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff45-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="aff45-166">管理 SharePoint Online 網站群組 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff45-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="aff45-167">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="aff45-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="aff45-168">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="aff45-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

