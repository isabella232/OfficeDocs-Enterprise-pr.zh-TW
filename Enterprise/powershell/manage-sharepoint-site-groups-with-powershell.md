---
title: 管理 Office 365 powershell 的 SharePoint Online 網站群組
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
description: 摘要： 使用 Office 365 PowerShell 管理 SharePoint Online 網站群組。
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>管理 Office 365 powershell 的 SharePoint Online 網站群組

 **摘要：**使用 Office 365 PowerShell 管理 SharePoint Online 網站群組。
  
雖然您可以使用 Office 365 系統管理中心，則您也可以使用 Office 365 PowerShell 來管理 SharePoint Online 的網站群組。

## <a name="before-you-begin"></a>開始之前

本文中的程序要求您重新連線至 SharePoint Online。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>檢視 SharePoint Online 搭配 Office 365 PowerShell

SharePoint Online 系統管理中心有一些簡單好用方法來管理網站群組。例如，假設您想要查看群組及群組成員https://litwareinc.sharepoint.com/sites/finance網站。以下是您必須執行：

1. 從 Office 365 系統管理中心中，按一下 [**資源** > **網站**]，然後按一下 [網站的 URL。
2. 在 [網站集合] 對話方塊中，按一下 [**移至這個網站**。
3. 在 [網站] 頁面上按一下 [**設定**] 圖示 （位於頁面右上角）] 和 [**網站設定**：</br>
![SharePoint Online 網站設定](images/spo-site-settings.png)</br>
4. 在 [網站設定] 頁面上按一下 [**使用者與權限**] 下的**網站權限**。

然後針對下一個想要查看的網站，重複此程序。

若要取得 Office 365 PowerShell 與群組的清單，您可以使用下列命令一組：

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

有兩種方式可以執行在 SharePoint Online 管理命令介面命令提示字元中設定此命令：
- 複製到 [記事本] （或其它文字編輯器） 的命令、 修改 **$siteURL**變數的值、 選取命令，並再將它們貼到 SharePoint Online 管理命令介面命令提示字元。當您執行 PowerShell 將會停止在 >> 提示。按 Enter 以執行每個命令。</br>
- 將命令複製到 [記事本] （或其它文字編輯器）、 修改 **$siteURL**變數的值，然後儲存此文字檔案名稱及.ps1 副檔名合適的資料夾中。接著，在 SharePoint Online 管理命令介面命令提示字元執行指令碼來指定它的路徑和檔案名稱。以下是範例：</br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
$x = Get-sposite foreach ($y 中 $x) {寫入主機 $y.Url-ForegroundColor"黃色"$z = Get Get-spositegroup-網站 $y.Url foreach ($ 以 $z) {$b = Get Get-spositegroup-網站 $y.Url-群組 $a.Title 寫入主機 $b.Title-ForegroundColor"青綠色"$b |Select-object-ExpandProperty 使用者寫入-主機}}
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

