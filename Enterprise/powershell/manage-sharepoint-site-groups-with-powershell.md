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
description: 摘要：使用 Office 365 PowerShell 管理 SharePoint Online 網站群組。
ms.openlocfilehash: 3a1b999470746cbe02ec52fe888ea26b59cd423b
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004196"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="d81f1-103">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d81f1-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="d81f1-104">雖然您可以使用 Microsoft 365 系統管理中心，但也可以使用 Office 365 PowerShell 來管理 SharePoint Online 網站群組。</span><span class="sxs-lookup"><span data-stu-id="d81f1-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d81f1-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="d81f1-105">Before you begin</span></span>

<span data-ttu-id="d81f1-106">本文中的程式需要您連線至 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="d81f1-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="d81f1-107">如需相關指示，請參閱[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="d81f1-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="d81f1-108">View SharePoint Online 與 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d81f1-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="d81f1-109">SharePoint Online 系統管理中心具有一些用於管理網站群組的便於使用的方法。</span><span class="sxs-lookup"><span data-stu-id="d81f1-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="d81f1-110">例如，假設您想要查看`https://litwareinc.sharepoint.com/sites/finance`網站的群組和群組成員。</span><span class="sxs-lookup"><span data-stu-id="d81f1-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="d81f1-111">以下是您必須執行的動作：</span><span class="sxs-lookup"><span data-stu-id="d81f1-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="d81f1-112">從 SharePoint 系統管理中心，按一下 [作用中的**網站**]，然後按一下網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="d81f1-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="d81f1-113">在 [網站] 頁面上，按一下 [**設定**] 圖示（位於頁面右上角），然後按一下 [**網站許可權**]。</span><span class="sxs-lookup"><span data-stu-id="d81f1-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="d81f1-114">然後針對您想要查看的下一個網站重複此程式。</span><span class="sxs-lookup"><span data-stu-id="d81f1-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="d81f1-115">若要取得使用 Office 365 PowerShell 的群組清單，您可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="d81f1-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

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

<span data-ttu-id="d81f1-116">在 SharePoint 線上管理命令介面命令提示字元中，有兩種方式可以執行這個命令集：</span><span class="sxs-lookup"><span data-stu-id="d81f1-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="d81f1-117">將命令複製到 [記事本（或其他文字編輯器）] 中，修改 **$siteURL**變數的值，然後選取命令，再將其貼到 SharePoint 線上管理命令介面命令提示字元中。</span><span class="sxs-lookup"><span data-stu-id="d81f1-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="d81f1-118">當您這麼做時，PowerShell 會在**>>** 提示時停止。</span><span class="sxs-lookup"><span data-stu-id="d81f1-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="d81f1-119">按 Enter 鍵以執行`foreach`命令。</span><span class="sxs-lookup"><span data-stu-id="d81f1-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="d81f1-120">將命令複製到 [記事本（或其他文字編輯器）] 中，修改 **$siteURL**變數的值，然後在適當的資料夾中，將名稱和. ps1 副檔名的文字檔儲存在適當的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d81f1-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="d81f1-121">接下來，指定 SharePoint 線上管理命令介面命令提示字元，並指定其路徑和檔案名以執行腳本。</span><span class="sxs-lookup"><span data-stu-id="d81f1-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="d81f1-122">範例命令如下：</span><span class="sxs-lookup"><span data-stu-id="d81f1-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="d81f1-123">在這兩種情況下，您應該會看到類似以下的內容：</span><span class="sxs-lookup"><span data-stu-id="d81f1-123">In both cases, you should see something similar to this:</span></span>

![SharePoint 線上網站群組](media/SPO-site-groups.png)

<span data-ttu-id="d81f1-125">這些是已為網站`https://litwareinc.sharepoint.com/sites/finance`建立的所有群組，以及指派給這些群組的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="d81f1-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="d81f1-126">組名為黃色，可協助您將群組名稱與其成員分開。</span><span class="sxs-lookup"><span data-stu-id="d81f1-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="d81f1-127">在另一個範例中，這裡是列出所有 SharePoint Online 網站之群組和所有群組成員資格的命令集。</span><span class="sxs-lookup"><span data-stu-id="d81f1-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="d81f1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d81f1-128">See also</span></span>

[<span data-ttu-id="d81f1-129">連線至 SharePoint 線上 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d81f1-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="d81f1-130">使用 Office 365 建立 SharePoint Online 網站及新增使用者 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d81f1-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="d81f1-131">使用 Office 365 PowerShell 管理 SharePoint Online 使用者和群組</span><span class="sxs-lookup"><span data-stu-id="d81f1-131">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="d81f1-132">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="d81f1-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d81f1-133">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d81f1-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

