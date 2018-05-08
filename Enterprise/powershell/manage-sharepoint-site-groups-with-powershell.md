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
ms.openlocfilehash: 881e67b7eb2d8bb5e04f83e28569aa54341d16b9
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="9a2ee-103">管理 Office 365 powershell 的 SharePoint Online 網站群組</span><span class="sxs-lookup"><span data-stu-id="9a2ee-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="9a2ee-104">**摘要：**使用 Office 365 PowerShell 管理 SharePoint Online 網站群組。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="9a2ee-105">雖然您可以使用 Office 365 系統管理中心，則您也可以使用 Office 365 PowerShell 來管理 SharePoint Online 的網站群組。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="9a2ee-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="9a2ee-106">Before you begin</span></span>

<span data-ttu-id="9a2ee-p101">本文中的程序要求您重新連線至 SharePoint Online。指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="9a2ee-109">檢視 SharePoint Online 搭配 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a2ee-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="9a2ee-p102">SharePoint Online 系統管理中心有一些簡單好用方法來管理網站群組。例如，假設您想要查看群組及群組成員，https\://litwareinc.sharepoint.com/sites/finance 網站。以下是您必須執行：</span><span class="sxs-lookup"><span data-stu-id="9a2ee-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https\://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="9a2ee-113">從 Office 365 系統管理中心中，按一下 [**資源** > **網站**]，然後按一下 [網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="9a2ee-114">在 [網站集合] 對話方塊中，按一下 [**移至這個網站**。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="9a2ee-115">在 [網站] 頁面上按一下 [**設定**] 圖示 （位於頁面右上角）] 和 [**網站設定**：</span><span class="sxs-lookup"><span data-stu-id="9a2ee-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="9a2ee-116">![SharePoint Online 網站設定](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="9a2ee-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="9a2ee-117">在 [網站設定] 頁面上按一下 [**使用者與權限**] 下的**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="9a2ee-118">然後針對下一個想要查看的網站，重複此程序。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="9a2ee-119">若要取得 Office 365 PowerShell 與群組的清單，您可以使用下列命令一組：</span><span class="sxs-lookup"><span data-stu-id="9a2ee-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="9a2ee-120">有兩種方式可以執行在 SharePoint Online 管理命令介面命令提示字元中設定此命令：</span><span class="sxs-lookup"><span data-stu-id="9a2ee-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="9a2ee-p103">複製到 [記事本] （或其它文字編輯器） 的命令、 修改 **$siteURL**變數的值、 選取命令，並再將它們貼到 SharePoint Online 管理命令介面命令提示字元。當您執行 PowerShell 將會停止在**>>** 提示。按 enter 鍵執行**foreach**命令。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a **>>** prompt. Press Enter to execute the **foreach** command.</span></span></br>
- <span data-ttu-id="9a2ee-p104">將命令複製到 [記事本] （或其它文字編輯器）、 修改 **$siteURL**變數的值，然後儲存此文字檔案名稱及.ps1 副檔名合適的資料夾中。接著，在 SharePoint Online 管理命令介面命令提示字元執行指令碼來指定它的路徑和檔案名稱。以下是範例命令：</span><span class="sxs-lookup"><span data-stu-id="9a2ee-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="9a2ee-127">在這兩種情況下，您應該看到類似：</span><span class="sxs-lookup"><span data-stu-id="9a2ee-127">In both cases, you should see something similar to this:</span></span>

![SharePoint Online 網站群組](images/SPO-site-groups.png)

<span data-ttu-id="9a2ee-p105">這些是已建立的網站 https 的所有群組\:/ / litwareinc.sharepoint.com/sites/finance，為所有使用者指派給這些群組。群組名稱是以黃色可協助您從其成員的不同的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-p105">These are all the groups that have been created for the site https\://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="9a2ee-131">另一個範例，以下是一組命令列出群組和所有的群組成員資格，所有您的 SharePoint Online 網站。</span><span class="sxs-lookup"><span data-stu-id="9a2ee-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="9a2ee-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a2ee-132">See also</span></span>

[<span data-ttu-id="9a2ee-133">連線至 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a2ee-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="9a2ee-134">建立 SharePoint Online 網站和新增使用者使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a2ee-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="9a2ee-135">使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組</span><span class="sxs-lookup"><span data-stu-id="9a2ee-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="9a2ee-136">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="9a2ee-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9a2ee-137">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a2ee-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

