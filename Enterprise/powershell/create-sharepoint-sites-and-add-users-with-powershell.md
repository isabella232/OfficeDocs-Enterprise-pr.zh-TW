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
ms.openlocfilehash: 41ca26249bd494d5603a425689e47f9fe6809f1a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975201"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>使用 Office 365 PowerShell 建立 SharePoint Online 網站並新增使用者

 **摘要：** 使用 Office 365 PowerShell 建立新的 SharePoint Online 網站，並再新增至這些網站的 [使用者和群組。

當您使用 Office 365 PowerShell 來建立 SharePoint Online 網站和新增使用者時，您可以快速且重複地執行工作速度快多了比您可以在 Office 356 系統管理中心。您也可以執行不可以在 Office 356 系統管理中心中執行的工作。 

## <a name="before-you-begin"></a>開始之前

本主題中的程序要求您重新連線至 SharePoint Online。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>步驟 1： 建立新的網站集合使用 Office 365 PowerShell

建立多個網站使用 Office 365 PowerShell 與您使用所提供的範例程式碼和 [記事本] 建立的.csv 檔案。此程序，您將會取代您自己的網站和承租人特定資訊的括號中顯示的版面配置區資訊。此程序可讓您建立單一檔案並執行單一的 Office 365 PowerShell 命令會使用該檔案。這讓鎖死和可攜式採取的動作，而且可消除許多，如果可以來自 SharePoint Online 管理命令介面中輸入命令很長的並非所有錯誤。有兩個部分此程序。您將在第一次建立.csv 檔案，並再讓您將會參照使用 Office 365 PowerShell 中會使用其內容建立網站的.csv 檔案。

Office 365 PowerShell 指令程式會匯入之.csv 檔案並將其傳送至迴圈內的大括弧括會讀取檔案的第一行做為資料行標題。Office 365 PowerShell 指令程式然後逐一查看剩餘的記錄、 建立新的網站集合的每筆記錄，並指派根據資料行標頭之網站集合的屬性。

### <a name="create-a-csv-file"></a>建立 .csv 檔案

1. 開啟 [記事本]，並貼入下列的文字區塊：<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>其中*租用戶*是您的租用戶名稱及*擁有者*是在您的租用戶其使用者的使用者名稱您想要授與主要網站集合管理員角色。<br/>（您可以可以按 Ctrl + H 當您使用 [記事本] 速度大量取代）。<br/>

2. 將桌面上的檔案儲存為**SiteCollections.csv**。<br/>

> [!TIP]
> 使用 this 或任何其他.csv 或 Windows PowerShell 指令碼檔案之前，它會是很好的作法以確保沒有任何無關或非列印字元。在 Word 中，並在功能區中開啟檔案，按一下 [段落] 圖示以顯示非列印字元。應該會有任何無關的非列印字元。例如，應超過檔案結尾處的最後一個沒有段落標記。

### <a name="run-the-windows-powershell-command"></a>執行 Windows PowerShell 命令

1. 在 Windows PowerShell 提示中輸入或複製並貼上下列指令程式，並按 Enter：<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>其中*MyAlias*等於您的使用者別名。<br/>

2. 等待來重新顯現的 Windows PowerShell 提示字元。可能需要數分鐘。<br/>

3. 在 Windows PowerShell 提示中輸入或複製並貼上下列指令程式，並按 Enter：<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. 請注意新網站集合清單中。您應該會看到下列網站集合： **contosotest**、 **TeamSite01**、 **Blog01**、 和**Project01**

這是它。您已建立使用您所建立之.csv 檔案的多個網站集合和單一 Windows PowerShell cmdlet。您現在準備好建立並將使用者指派給這些網站。

## <a name="step-2-add-users-and-groups"></a>步驟 2：新增使用者和群組

現在，您即將建立使用者，並將他們新增至網站集合群組。您接著將使用 .csv 檔案大量上傳新的群組和使用者。

下列程序假設您已順利建立網站集合 contosotest、TeamSite01、Blog01 和 Project01。

### <a name="create-csv-and-ps1-files"></a>建立 .csv 和 .ps1 檔案

1. 開啟 [記事本]，並貼入下列的文字區塊：<br/>
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
<br/>其中*租用戶*等於您的租用戶名稱。<br/>

2. **Groupsandpermissions.csv 儲存至**將檔案儲存至您的桌面。<br/>

3. 開啟新的 [記事本] 執行個體，並貼入下列的文字區塊：<br/>

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
<br/>其中*租用戶*等於您的租用戶名稱與*username*等於現有使用者的使用者名稱。<br/>

4. **Users.csv 儲存至**將檔案儲存至您的桌面。<br/>

5. 開啟新的 [記事本] 執行個體，並貼入下列的文字區塊：<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>其中 MyAlias 等於目前已登入使用者的使用者名稱。<br/>

6. 為**UsersAndGroups.ps1**將檔案儲存至您的桌面。這是簡易的 Windows PowerShell 指令碼。

您現在準備好執行 UsersAndGroup.ps1 指令碼，以將使用者和群組新增至多個網站集合。

### <a name="run-usersandgroupsps1-script"></a>執行 UsersAndGroups.ps1 指令碼

1. 回到 SharePoint Online 管理命令介面。<br/>
2. 在 Windows PowerShell 提示中輸入或複製並貼上下行，並按 Enter：<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. 確認提示，請按**Y**。<br/>

4. 在 Windows PowerShell 提示字元、 類型或複製和貼上下列項目，然後按 Enter：<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>其中*MyAlias*等於您的使用者名稱。<br/>

5. 等待返回提示，再繼續進行。您會先看到在建立群組時出現群組。然後，您會看到在新增使用者時重複群組清單。

## <a name="see-also"></a>另請參閱

[連線至 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[管理 SharePoint Online 網站群組 Office 365 PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

