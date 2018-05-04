---
title: 使用 Office 365 PowerShell 建立 SharePoint Online 網站並新增使用者
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
description: 摘要： 使用 Office 365 PowerShell 建立新的 SharePoint Online 網站，並再新增至這些網站的 [使用者和群組。
ms.openlocfilehash: 0a0438917f6e7010b56703ce0bf73e89e1db0533
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="39805-103">使用 Office 365 PowerShell 建立 SharePoint Online 網站並新增使用者</span><span class="sxs-lookup"><span data-stu-id="39805-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="39805-104">**摘要：**使用 Office 365 PowerShell 建立新的 SharePoint Online 網站，並再新增至這些網站的 [使用者和群組。</span><span class="sxs-lookup"><span data-stu-id="39805-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="39805-p101">當您使用 Office 365 PowerShell 來建立 SharePoint Online 網站和新增使用者時，您可以快速且重複地執行工作速度快多了比您可以在 Office 356 系統管理中心。您也可以執行不可以在 Office 356 系統管理中心中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="39805-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="39805-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="39805-107">Before you begin</span></span>

<span data-ttu-id="39805-p102">本主題中的程序要求您重新連線至 SharePoint Online。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span><span class="sxs-lookup"><span data-stu-id="39805-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="39805-110">步驟 1： 建立新的網站集合使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="39805-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="39805-p103">建立多個網站使用 Office 365 PowerShell 與您使用所提供的範例程式碼和 [記事本] 建立的.csv 檔案。此程序，您將會取代您自己的網站和承租人特定資訊的括號中顯示的版面配置區資訊。此程序可讓您建立單一檔案並執行單一的 Office 365 PowerShell 命令會使用該檔案。這讓鎖死和可攜式採取的動作，而且可消除許多，如果可以來自 SharePoint Online 管理命令介面中輸入命令很長的並非所有錯誤。有兩個部分此程序。您將在第一次建立.csv 檔案，並再讓您將會參照使用 Office 365 PowerShell 中會使用其內容建立網站的.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="39805-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process allows you to create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="39805-p104">Office 365 PowerShell 指令程式會匯入之.csv 檔案並將其傳送至迴圈內的大括弧括會讀取檔案的第一行做為資料行標題。Office 365 PowerShell 指令程式然後逐一查看剩餘的記錄、 建立新的網站集合的每筆記錄，並指派根據資料行標頭之網站集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="39805-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

###<a name="create-a-csv-file"></a><span data-ttu-id="39805-119">建立 .csv 檔案</span><span class="sxs-lookup"><span data-stu-id="39805-119">Create a .csv file</span></span>

1. <span data-ttu-id="39805-120">開啟 [記事本]，並貼入下列的文字區塊：</span><span class="sxs-lookup"><span data-stu-id="39805-120">Open Notepad, and paste the following text block into it:</span></span></br>
```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```</br>Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</br>(You can press Ctrl+H when you use Notepad to bulk replace faster.)</br>
2. Save the file on your desktop as **SiteCollections.csv**.

 > [!TIP]
> Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.

### Run the Windows PowerShell command

1. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
<span data-ttu-id="39805-121">匯入 Csv C:\users\MyAlias\desktop\SiteCollections.csv |Foreach-object {新 SPOSite-擁有者 $_。擁有者-StorageQuota $_。StorageQuota-Url $_。Url [不等待-ResourceQuota $_。ResourceQuota-範本 $_。範本-TimeZoneID $_。TimeZoneID-Title $_。名稱}</span><span class="sxs-lookup"><span data-stu-id="39805-121">Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}</span></span>
```
</br>Where *MyAlias* equals your user alias.</br>
2. Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</br>
3. At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</br>
```
<span data-ttu-id="39805-122">Get-sposite-詳細 |Format-table-AutoSize</span><span class="sxs-lookup"><span data-stu-id="39805-122">Get-SPOSite -Detailed | Format-Table -AutoSize</span></span>
```</br>
4. Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**.

That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.

## Step 2: Add users and groups

Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.

The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.

### Create .csv and .ps1 files

1. Open Notepad, and paste the following text block into it:</br>
```
<span data-ttu-id="39805-123">網站、 群組、 PermissionLevels https://tenant.sharepoint.com/sites/contosotest，Contoso 專案負責人、 完全控制https://tenant.sharepoint.com/sites/contosotest，Contoso Auditors 僅供檢視https://tenant.sharepoint.com/sites/contosotest，Contoso 設計者設計https://tenant.sharepoint.com/sites/TeamSite01、 XT1000 小組負責人、 完全控制https://tenant.sharepoint.com/sites/TeamSite01、 XT1000 顧問編輯https://tenant.sharepoint.com/sites/Blog01，Contoso 部落格設計者設計https://tenant.sharepoint.com/sites/Blog01，Contoso 部落格編輯器編輯https://tenant.sharepoint.com/sites/Project01、 Project Alpha 核准者、 完全控制</span><span class="sxs-lookup"><span data-stu-id="39805-123">Site,Group,PermissionLevels https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control</span></span>
```
</br>Where *tenant* equals your tenant name.</br>
2. Save the file to your desktop as **GroupsAndPermissions.csv**.</br>
3. Open a new instance of Notepad, and paste the following text block into it:</br>
```
<span data-ttu-id="39805-124">群組中，LoginName、 網站 Contoso 專案負責人、 username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/contosotest Contoso 稽核者、 username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/contosotest Contoso 設計者、 username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/contosotest XT1000 小組負責人、username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/TeamSite01 XT1000 顧問、 username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/TeamSite01 Contoso 部落格設計者、 username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/Blog01 Contoso 部落格編輯者、 username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/Blog01Project Alpha 核准者、 username@tenant.onmicrosoft.com、https://tenant.sharepoint.com/sites/Project01</span><span class="sxs-lookup"><span data-stu-id="39805-124">Group,LoginName,Site Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01 Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01 Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01</span></span>
```
</br>Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</br>
4. Save the file to your desktop as **Users.csv**.</br>
5. Open a new instance of Notepad, and paste the following text block into it:</br>
```
<span data-ttu-id="39805-125">匯入 Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv |Foreach-object {新 Get-spositegroup-群組 $_。群組-PermissionLevels $_。PermissionLevels-網站 $_。Site} 匯入 Csv C:\users\MyAlias\desktop\Users.csv |其中 {新增 SPOUser-群組 $_。群組 – LoginName $_。LoginName-網站 $_。Site}</span><span class="sxs-lookup"><span data-stu-id="39805-125">Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site} Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}</span></span>
```
</br>Where MyAlias equals the user name of the user that is currently logged on.</br>
6. Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.

You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.

### Run UsersAndGroups.ps1 script

1. Return to the SharePoint Online Management Shell.</br>
2. At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</br>
```
<span data-ttu-id="39805-126">Set-executionpolicy 略過</span><span class="sxs-lookup"><span data-stu-id="39805-126">Set-ExecutionPolicy Bypass</span></span>
```</br>
3. At the confirmation prompt, press **Y**.</br>
4. At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</br>
```
<span data-ttu-id="39805-127">c:\users\MyAlias\desktop\UsersAndGroups.ps1</span><span class="sxs-lookup"><span data-stu-id="39805-127">c:\users\MyAlias\desktop\UsersAndGroups.ps1</span></span>
```
</br>Where *MyAlias* equals your user name.</br>
5. Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.

## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Manage SharePoint Online site groups Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

