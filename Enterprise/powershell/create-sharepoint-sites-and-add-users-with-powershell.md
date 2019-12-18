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
ms.openlocfilehash: f15add5652af44d24e2fec678c5224b5efd7aa4f
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261346"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>建立 SharePoint Online 網站並新增使用者使用 Office 365 PowerShell

當您使用 Office 365 PowerShell 建立 SharePoint Online 網站以及新增使用者時，您可以快速且重複執行速度快多了比您可以在 Microsoft 356 系統管理中心中的工作。 您也可以執行不可以在 Office 356 系統管理中心中執行的工作。 

## <a name="before-you-begin"></a>開始之前

本主題中的程序需要您連線至 SharePoint Online。 如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>步驟 1： 建立新的網站集合使用 Office 365 PowerShell

建立使用 Office 365 PowerShell 與您使用的範例程式碼提供和 [記事本] 建立.csv 檔案的多個站台。 此程序，您將會取代與您自己的網站和租用戶特定資訊的括號中所示的版面配置區資訊。 此程序可讓您建立單一檔案，並執行單一的 Office 365 PowerShell 命令，會使用該檔案。 這可讓鎖死和可攜式所採取的動作，並且消除數量，如果可能來自 SharePoint Online 管理命令介面中鍵入命令很長的非全部的錯誤。 有兩個部分此程序。 您將在第一次建立.csv 檔案，並接著您會參照使用 Office 365 PowerShell，將會使用它的內容來建立網站的.csv 檔案。

Office 365 PowerShell cmdlet 會匯入之.csv 檔案，並將其傳送至大括號內迴圈，讀取檔案的第一行作為資料行標頭。 Office 365 PowerShell cmdlet 接著逐一查看剩餘的記錄、 建立新的網站集合，每一筆記錄，並指派根據資料行標頭網站集合的屬性。

### <a name="create-a-csv-file"></a>建立.csv 檔案

1. 開啟 [記事本]，然後貼上下列的文字區塊：<br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>*租用戶*是您的租用戶的名稱，以及*擁有者*是收件者您租用戶上之使用者的使用者名稱您想要授與的主要網站集合管理員角色。<br/>（您可以在按 Ctrl + H 時更快速地大量取代的情況下，您在使用 [記事本]）。<br/>

2. 在桌面上將檔案儲存為**SiteCollections.csv**。<br/>

> [!TIP]
> 在您使用 this 或任何其他.csv 或 Windows PowerShell 指令碼檔案之前，它會是很好的作法，以確保沒有任何無關或非列印字元。 開啟的檔案，在 Word 中，然後在功能區中，按一下 [段落] 圖示，顯示非列印字元。 應該會有任何無關的非列印字元。 例如，應該超出檔案結尾處的最後一個沒有段落標記。

### <a name="run-the-windows-powershell-command"></a>執行 Windows PowerShell 命令

1. 在 Windows PowerShell 提示字元處，輸入或複製並貼上下列命令，並按 Enter 鍵：<br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>其中*MyAlias*等於您的使用者別名。<br/>

2. 等待重新顯示的 Windows PowerShell 提示字元。 它可能需要幾分鐘或兩個。<br/>

3. 在 Windows PowerShell 提示字元處，輸入或複製並貼上下列的指令程式，並按 Enter 鍵：<br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. 附註] 清單中新的網站集合。 使用我們的範例 CSV 檔案，您會看到下列網站集合： **TeamSite01**、 **Blog01**、 **Project01**及**Community01**

這樣就完成了。 您已建立使用您建立的.csv 檔案的多個網站集合與單一 Windows PowerShell 命令。 您現在可以開始建立，並將使用者指派給這些網站。

## <a name="step-2-add-users-and-groups"></a>步驟 2： 新增使用者和群組

現在您將建立的使用者，並將它們新增至網站集合群組。 您接著使用.csv 檔案大量上傳新的群組和使用者。

下列程序會繼續使用 TeamSite01、 Blog01、 Project01 及 Community01 範例網站。

### <a name="create-csv-and-ps1-files"></a>建立.csv 和.ps1 檔案

1. 開啟 [記事本]，然後貼上下列的文字區塊：<br/>

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
<br/>其中*的租用戶*等於您的租用戶名稱。<br/>

2. **Groupsandpermissions.csv 儲存至**將檔案儲存至您的桌面。<br/>

3. 開啟 [記事本] 的新執行個體，並貼上下列的文字區塊：<br/>

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
<br/>其中*的租用戶*等於您的租用戶名稱，而*username*等於現有使用者的使用者名稱。<br/>

4. **Users.csv 儲存至**將檔案儲存至您的桌面。<br/>

5. 開啟 [記事本] 的新執行個體，並貼上下列的文字區塊：<br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>其中 MyAlias 等於目前已登入使用者的使用者名稱。<br/>

6. 將檔案儲存到您的桌面，為**UsersAndGroups.ps1**。 這是一個簡單的 Windows PowerShell 指令碼。

您現在準備好執行 UsersAndGroup.ps1 指令碼，將使用者和群組新增至多個網站集合。

### <a name="run-usersandgroupsps1-script"></a>執行 UsersAndGroups.ps1 指令碼

1. 會傳回 SharePoint Online 管理命令介面。<br/>
2. 在 Windows PowerShell 提示字元處，輸入或複製並貼上下行，並按 Enter 鍵：<br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. 在確認提示，請按**Y**。<br/>

4. 在 Windows PowerShell 命令提示字元、 類型或複製並貼上下列項目，然後按 Enter 鍵：<br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>其中*MyAlias*等於您的使用者名稱。<br/>

5. 等待要傳回才可繼續的提示。 首先，您會看到顯示他們所建立的群組。 然後您會看到重複也當簡報加入使用者的 [群組] 清單。

## <a name="see-also"></a>另請參閱

[連線至 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[管理 SharePoint Online 網站群組 Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

