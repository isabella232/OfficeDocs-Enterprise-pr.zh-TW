---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 來管理 SharePoint Online 網站群組。
ms.openlocfilehash: a128823ba125342bd1d209ac8a2bf28334da866d
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068859"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Manage SharePoint Online site groups with Office 365 PowerShell

 **摘要：** 使用 Office 365 PowerShell 來管理 SharePoint Online 網站群組。
  
雖然您可以使用 Microsoft 365 系統管理中心，您也可以使用 Office 365 PowerShell 來管理 SharePoint Online 網站群組。

## <a name="before-you-begin"></a>開始之前

本文中的程序需要您連線至 SharePoint Online。 如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>檢視 SharePoint Online 與 Office 365 PowerShell

在 SharePoint Online 系統管理中心有一些方便使用方法管理網站群組。 例如，假設您想要尋找在群組和群組成員，`https://litwareinc.sharepoint.com/sites/finance`網站。 以下是您必須執行的動作：

1. 從 Microsoft 365 系統管理中心中，按一下 [**資源** > **網站**，然後按一下 [網站的 URL。
2. 在網站集合] 對話方塊中，按一下 [**移至這個網站**。
3. 在 [網站] 頁面上，按一下 [**設定**] 圖示 （位於頁面右上角），然後按一下 [**網站設定**：<br/>
![SharePoint Online 網站設定](media/spo-site-settings.png)<br/>
4. 在 [網站設定] 頁面上，按一下 [**使用者與權限**] 下的**網站權限**。

然後重複此程序的下一個您想要查看的網站。

若要取得 Office 365 PowerShell 與群組的清單，您可以使用下列命令集：

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

有兩種方法來執行在 SharePoint Online 管理命令介面命令提示字元中設定此命令：

- 將命令複製到 [記事本] （或其他文字編輯器中）、 修改 **$siteURL**變數的值、 選取命令，並再將它們貼到 SharePoint Online 管理命令介面命令提示字元。 當您執行 PowerShell 將會停止在**>>** 提示。 按 Enter 以執行**foreach**命令。<br/>
- 將命令複製到 [記事本] （或其他文字編輯器中）、 修改 **$siteURL**變數的值，然後儲存此文字檔案名稱與適當的資料夾中的.ps1 副檔名。 下一步]，從 SharePoint Online 管理命令介面命令提示字元中執行指令碼藉由指定其路徑及檔案名稱。 範例命令如下：

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

在這兩種情況下，您應該可以看到類似這樣：

![SharePoint Online 網站群組](media/SPO-site-groups.png)

這些是已建立之網站的所有群組`https://litwareinc.sharepoint.com/sites/finance`，以及指派給這些群組的所有使用者。 群組名稱是以黃色可協助您從其成員的個別群組名稱。

另一個範例，以下是一組命令，其中列出群組及所有的群組成員資格，所有的 SharePoint Online 網站。

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>另請參閱

[連線至 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[建立 SharePoint Online 網站並新增使用者使用 Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組](manage-sharepoint-users-and-groups-with-powershell.md)

[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

