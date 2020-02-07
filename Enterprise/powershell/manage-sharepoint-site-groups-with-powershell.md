---
title: Manage SharePoint Online site groups with Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 摘要： 使用 Office 365 PowerShell 來管理 SharePoint Online 網站群組。
ms.openlocfilehash: c9ae4927e3c423db5ac9da4c0e7c44fcbe091e0f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841360"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="3ce6a-103">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ce6a-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="3ce6a-104">雖然您可以使用 Microsoft 365 系統管理中心，您也可以使用 Office 365 PowerShell 來管理 SharePoint Online 網站群組。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="3ce6a-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="3ce6a-105">Before you begin</span></span>

<span data-ttu-id="3ce6a-106">本文中的程序需要您連線至 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="3ce6a-107">如需相關指示，請參閱[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="3ce6a-108">檢視 SharePoint Online 與 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ce6a-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="3ce6a-109">在 SharePoint Online 系統管理中心有一些方便使用方法管理網站群組。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="3ce6a-110">例如，假設您想要尋找在群組和群組成員，`https://litwareinc.sharepoint.com/sites/finance`網站。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="3ce6a-111">以下是您必須執行的動作：</span><span class="sxs-lookup"><span data-stu-id="3ce6a-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="3ce6a-112">從 SharePoint 系統管理中心中，按一下 [**作用中網站**]，然後按一下網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="3ce6a-113">在 [網站] 頁面上，按一下 [**設定**] 圖示 （位於頁面右上角），，，然後按一下 [**網站權限**。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="3ce6a-114">然後重複此程序的下一個您想要查看的網站。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="3ce6a-115">若要取得 Office 365 PowerShell 與群組的清單，您可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="3ce6a-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

<span data-ttu-id="3ce6a-116">有兩種方法來執行在 SharePoint Online 管理命令介面命令提示字元中設定此命令：</span><span class="sxs-lookup"><span data-stu-id="3ce6a-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="3ce6a-117">將命令複製到 [記事本] （或其他文字編輯器中）、 修改 **$siteURL**變數的值、 選取命令，並再將它們貼到 SharePoint Online 管理命令介面命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="3ce6a-118">當您執行 PowerShell 將會停止在**>>** 提示。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="3ce6a-119">按 Enter 以執行`foreach`命令。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="3ce6a-120">將命令複製到 [記事本] （或其他文字編輯器中）、 修改 **$siteURL**變數的值，然後儲存此文字檔案名稱與適當的資料夾中的.ps1 副檔名。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="3ce6a-121">下一步]，從 SharePoint Online 管理命令介面命令提示字元中執行指令碼藉由指定其路徑及檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="3ce6a-122">範例命令如下：</span><span class="sxs-lookup"><span data-stu-id="3ce6a-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="3ce6a-123">在這兩種情況下，您應該可以看到類似這樣：</span><span class="sxs-lookup"><span data-stu-id="3ce6a-123">In both cases, you should see something similar to this:</span></span>

![SharePoint Online 網站群組](media/SPO-site-groups.png)

<span data-ttu-id="3ce6a-125">這些是已建立之網站的所有群組`https://litwareinc.sharepoint.com/sites/finance`，以及指派給這些群組的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="3ce6a-126">群組名稱是以黃色可協助您從其成員的個別群組名稱。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="3ce6a-127">另一個範例，以下是一組命令，其中列出群組及所有的群組成員資格，所有的 SharePoint Online 網站。</span><span class="sxs-lookup"><span data-stu-id="3ce6a-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

```powershell
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
    
## <a name="see-also"></a><span data-ttu-id="3ce6a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce6a-128">See also</span></span>

[<span data-ttu-id="3ce6a-129">連線至 SharePoint Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ce6a-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="3ce6a-130">建立 SharePoint Online 網站並新增使用者使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ce6a-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="3ce6a-131">使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組</span><span class="sxs-lookup"><span data-stu-id="3ce6a-131">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="3ce6a-132">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="3ce6a-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3ce6a-133">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ce6a-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

