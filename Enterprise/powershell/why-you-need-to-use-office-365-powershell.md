---
title: 為什麼要使用 Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 摘要：了解為何您必須使用 Office 365 PowerShell 來管理 Office 365，在某些情況下更有效率，在另一些情況則是必然。
ms.openlocfilehash: 9909d9665817646f7c70c66012af4b8762cceaa1
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897466"
---
# <a name="why-you-need-to-use-office-365-powershell"></a><span data-ttu-id="90955-103">為什麼要使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="90955-103">Why you need to use Office 365 PowerShell</span></span>

 <span data-ttu-id="90955-104">**摘要：** 了解為何您必須使用 Office 365 PowerShell 來管理 Office 365，在某些情況下更有效率，在另一些情況則是必然。</span><span class="sxs-lookup"><span data-stu-id="90955-104">**Summary:** Understand why you must use Office 365 PowerShell to manage Office 365, in some cases more efficiently and in other cases by necessity.</span></span>
  
<span data-ttu-id="90955-p101">使用 Office 365 系統管理中心，您不僅能管理 Office 365 使用者帳戶和使用者授權，還能管理 Office 365 伺服器產品：Exchange、商務用 Skype Online 及 SharePoint Online。不過，您也可以使用 Office 365 PowerShell 命令來管理這些元素 (利用命令列與指令碼語言環境，可獲得速度、自動化和其他功能等優勢)。</span><span class="sxs-lookup"><span data-stu-id="90955-p101">With the Office 365 admin center, you can not only manage your Office 365 user accounts and licenses, but you can also manage your Office 365 server products: Exchange, Skype for Business Online, and SharePoint Online. However, you can also manage these elements with Office 365 PowerShell commands, taking advantage of a command-line and scripting language environment for speed, automation, and additional capability.</span></span>
  
<span data-ttu-id="90955-107">在本文中，我們將顯示您可以使用 Office 365 PowerShell 管理 Office 365 的方法。</span><span class="sxs-lookup"><span data-stu-id="90955-107">In this article, we'll show you these ways in which you can use Office 365 PowerShell to manage Office 365.</span></span>
  
- <span data-ttu-id="90955-108">Office 365 PowerShell 可以揭露使用 Office 365 系統管理中心看不到的其他資訊</span><span class="sxs-lookup"><span data-stu-id="90955-108">Office 365 PowerShell can reveal additional information that you cannot see with the Office 365 admin center</span></span>
    
- <span data-ttu-id="90955-109">Office 365 具有您只能使用 Office 365 PowerShell 所設定的功能</span><span class="sxs-lookup"><span data-stu-id="90955-109">Office 365 has features that you can only configure by using Office 365 PowerShell</span></span>
    
- <span data-ttu-id="90955-110">Office 365 PowerShell 十分適合執行大量作業</span><span class="sxs-lookup"><span data-stu-id="90955-110">Office 365 PowerShell is great at performing bulk operations</span></span>
    
- <span data-ttu-id="90955-111">Office 365 PowerShell 十分適合篩選資料</span><span class="sxs-lookup"><span data-stu-id="90955-111">Office 365 PowerShell is great at filtering data</span></span>
    
- <span data-ttu-id="90955-112">Office 365 PowerShell 可讓您輕鬆地列印或儲存資料</span><span class="sxs-lookup"><span data-stu-id="90955-112">Office 365 PowerShell makes it easy to print or save data</span></span>
    
- <span data-ttu-id="90955-113">Office 365 PowerShell 可讓您管理數個伺服器產品</span><span class="sxs-lookup"><span data-stu-id="90955-113">Office 365 PowerShell lets you manage across server products</span></span>
    
<span data-ttu-id="90955-p102">在您開始之前，請了解 Office 365 PowerShell 是 Windows PowerShell (Windows 服務和平台的命令列環境) 的一組模組。此環境會建立可透過其他模組擴充的命令殼層語言，並提供方法來執行簡單或複雜的命令或指令碼。例如，在您安裝 Office 365 PowerShell 模組並連線至 Office 365 訂閱之後，可以執行此命令來列出 Microsoft Exchange Online 的所有使用者信箱：</span><span class="sxs-lookup"><span data-stu-id="90955-p102">Before you begin, understand that Office 365 PowerShell is a set of modules for Windows PowerShell, a command-line environment for Windows-based services and platforms. This environment creates a command shell language that can be extended with additional modules and provides a way to execute simple or complex commands or scripts. For example, after you install the Office 365 PowerShell modules and connect to your Office 365 subscription, you can run this command to list all of the user mailboxes for Microsoft Exchange Online:</span></span>
  
```
Get-Mailbox
```

<span data-ttu-id="90955-117">使用 Office 365 系統管理中心也可以輕鬆地取得信箱清單，但計算所有 Web 應用程式之所有網站的所有清單中的項目數則無法輕鬆地完成。</span><span class="sxs-lookup"><span data-stu-id="90955-117">Getting the list of mailboxes can also be easily done using the Office 365 admin center, but counting the number of items in all of the lists for all of the sites for all of your web apps cannot be easily done.</span></span>
  
<span data-ttu-id="90955-p103">請注意，Office 365 PowerShell 設計來強化並加強管理 Office 365 的能力，而不取代 Office 365 系統管理中心。身為 Office 365 系統管理員，您至少必須熟悉如何使用 Office 365 PowerShell，因為有一些組態程序只能使用 Office 365 PowerShell 命令完成。在這些情況下，您必須了解如何：</span><span class="sxs-lookup"><span data-stu-id="90955-p103">Please note that Office 365 PowerShell is designed to augment and enhance your ability to manage Office 365, not to replace the Office 365 admin center. As an Office 365 administrator, you must become at least comfortable with using Office 365 PowerShell because there are some configuration procedures that can only be done with Office 365 PowerShell commands. In these cases, you will be required to understand how to:</span></span>
  
- <span data-ttu-id="90955-121">安裝 Office 365 PowerShell 模組 (每部系統管理員電腦都會執行一次)。</span><span class="sxs-lookup"><span data-stu-id="90955-121">Install the Office 365 PowerShell modules (done only once for each administrator computer).</span></span>
    
- <span data-ttu-id="90955-122">連線至 Office 365 訂閱 (每個 PowerShell 工作階段都會執行一次)。</span><span class="sxs-lookup"><span data-stu-id="90955-122">Connect to your Office 365 subscription (done once for each PowerShell session).</span></span>
    
- <span data-ttu-id="90955-123">收集執行必要 Office 365 PowerShell 命令所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="90955-123">Gather the information needed to run the required Office 365 PowerShell commands.</span></span>
    
- <span data-ttu-id="90955-124">已順利執行 Office 365 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="90955-124">Run the Office 365 PowerShell commands successfully.</span></span>
    
<span data-ttu-id="90955-p104">了解這些基本技術之後，您不需要使用 **Get-mailbox** 命令列出信箱使用者，也不需要了解如何建立新命令 (例如前一個命令來計算所有 Web 應用程式之所有網站的所有清單中的所有項目)。Microsoft 和 Office 365 系統管理員社群可視需要協助您使用該作業。</span><span class="sxs-lookup"><span data-stu-id="90955-p104">After learning these basic skills, you are not required to list your mailbox users with **Get-Mailbox** command, nor are you required to understand how to create a new command like the previous one to count all the items in all the lists for all of the sites for all of your web apps. Microsoft and the community of Office 365 administrators can help you with that as needed.</span></span>
  
## <a name="office-365-powershell-can-reveal-additional-information-that-you-cannot-see-with-the-office-365-admin-center"></a><span data-ttu-id="90955-127">Office 365 PowerShell 可以揭露使用 Office 365 系統管理中心看不到的其他資訊</span><span class="sxs-lookup"><span data-stu-id="90955-127">Office 365 PowerShell can reveal additional information that you cannot see with the Office 365 admin center</span></span>

<span data-ttu-id="90955-p105">Office 365 系統管理中心會顯示許多有用的資訊，但這不表示它會顯示 Office 365 所儲存之使用者、授權、信箱和網站的所有可能資訊。以下是 Office 365 系統管理中心內的 **使用者和群組** 範例：</span><span class="sxs-lookup"><span data-stu-id="90955-p105">The Office 365 admin center displays a lot of useful information, but that doesn't mean that it displays all the possible information that Office 365 stores on users, licenses, mailboxes, and sites. Here is an example for **users and groups** in the Office 365 admin center:</span></span>
  
![Office 365 系統管理中心內，使用者及群組顯示方式的範例。](media/o365-powershell-users-and-groups.png)
  
<span data-ttu-id="90955-p106">針對多種目的，這會顯示您需要知道的資訊。但有需要更多時間。例如，Office 365 授權 （與提供給使用者的 Office 365 功能） 部份取決於該使用者的地理位置。原則與功能可以擴充到儲存在美國中的使用者可能不會將相同的原則和功能可以擴充到儲存比利時或印度中的使用者是。您可以使用 Office 365 系統管理中心來判斷使用者的地理位置進行這些步驟：</span><span class="sxs-lookup"><span data-stu-id="90955-p106">For many purposes, this displays the information you need to know. However, there are times when you need more. For example, Office 365 licensing (and the Office 365 features available to a user) depend in part on that user's geographic location. The policies and features you can extend to a user who lives in the United States might not be the same as the policies and features you can extend to a user who lives in India or in Belgium. You can use the Office 365 admin center to determine a user's geographic location with these steps:</span></span>
  
1. <span data-ttu-id="90955-136">連按兩下使用者的 **[顯示名稱]** 。</span><span class="sxs-lookup"><span data-stu-id="90955-136">Double-click the user's **Display Name**.</span></span>
    
2. <span data-ttu-id="90955-137">在使用者內容顯示窗格中，按一下 **[詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="90955-137">In the user properties display pane, click **details**.</span></span>
    
3. <span data-ttu-id="90955-138">在詳細資料顯示中，按一下 **[其他詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="90955-138">In the details display, click **additional details**.</span></span>
    
4. <span data-ttu-id="90955-139">向下捲動，直到您看到 **[國家或地區]** 標題為止。</span><span class="sxs-lookup"><span data-stu-id="90955-139">Scroll down until you see the heading **Country or region**:</span></span>
    
     ![Office 365 系統管理中心內，使用者區域資訊的範例。](media/o365-powershell-usage-location.png)
  
5. <span data-ttu-id="90955-141">在一張紙上寫下使用者的顯示名稱和位置，或複製並貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="90955-141">Write the user's display name and location on a piece of paper, or copy and paste it into Notepad.</span></span> 
    
<span data-ttu-id="90955-p107">您必須為每位使用者重複此程序。對於許多使用者，這可能是冗長乏味的工作。使用 Office 365 PowerShell，您可以透過下列命令，針對所有使用者顯示這項資訊：</span><span class="sxs-lookup"><span data-stu-id="90955-p107">You must repeat this procedure for each user. For many users, this can be a tedious task. With Office 365 PowerShell, you can display this information for all of your users with the following command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

> [!NOTE]
> <span data-ttu-id="90955-145">此命令需要您安裝 [Windows Azure Active Directory 模組](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0)。</span><span class="sxs-lookup"><span data-stu-id="90955-145">This command requires you to install the [Windows Azure Active Directory module](https://docs.microsoft.com/powershell/module/Azuread/?view=azureadps-2.0).</span></span> 
  
<span data-ttu-id="90955-146">以下是顯示範例：</span><span class="sxs-lookup"><span data-stu-id="90955-146">Here is an example of the display:</span></span>
  
```
DisplayName                               UsageLocation
-----------                               -------------
Zrinka Makovac                            US
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

> [!TIP]
>  <span data-ttu-id="90955-147">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有使用者 ( **Get-MsolUser** )，但只顯示每位使用者的名稱和位置 ( **Select DisplayName, UsageLocation** )。</span><span class="sxs-lookup"><span data-stu-id="90955-147">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription ( **Get-MsolUser** ), but only display the name and location for each user ( **Select DisplayName, UsageLocation** ).</span></span>
  
<span data-ttu-id="90955-p108">因為 Office 365 PowerShell 支援命令殼層語言，所以您可以進一步處理透過 **Get-MSolUser** 命令取得的資訊。例如，您可能會想要按使用者的位置來排序使用者、將所有巴西使用者群組在一起、將所有美國使用者群組在一起等等。命令如下：</span><span class="sxs-lookup"><span data-stu-id="90955-p108">Because Office 365 PowerShell supports a command shell language, you can further manipulate the information obtained from the **Get-MSolUser** command. For example, maybe you'd like to sort these users by their location, grouping all the Brazilian users together, all the United States users together, etc. Here is the command:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

<span data-ttu-id="90955-150">以下是顯示範例：</span><span class="sxs-lookup"><span data-stu-id="90955-150">Here is an example of the display:</span></span>
  
```
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
Zrinka Makovac                              US
```

> [!TIP]
>  <span data-ttu-id="90955-151">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有使用者，但只顯示每位使用者的名稱和位置，並依序按其位置和名稱來進行排序 ( **Sort UsageLocation, DisplayName** )。</span><span class="sxs-lookup"><span data-stu-id="90955-151">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but only display the name and location for each user and sort them first by their location, and then their names ( **Sort UsageLocation, DisplayName** ).</span></span>
  
<span data-ttu-id="90955-p109">您也可以使用其他篩選。例如，如果您只想看到巴西使用者的資訊，請使用這個命令：</span><span class="sxs-lookup"><span data-stu-id="90955-p109">You can also employ additional filtering. For example, if you only want to see information about users based in Brazil, use this command:</span></span>
  
```
Get-MsolUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation 
```

<span data-ttu-id="90955-154">以下是顯示範例：</span><span class="sxs-lookup"><span data-stu-id="90955-154">Here is an example of the display:</span></span>
  
```
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

> [!TIP]
>  <span data-ttu-id="90955-155">此 Office 365 PowerShell 命令的解譯如下：取得位置是巴西的目前 Office 365 訂閱中的所有使用者 ( **Where {$\_.UsageLocation -eq "BR"}** )，然後顯示每位使用者的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="90955-155">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription whose location is Brazil ( **Where {$\_.UsageLocation -eq "BR"}** ), then display the name and location for each user.</span></span>
  
 <span data-ttu-id="90955-156">**與較大型網域相關的備註**</span><span class="sxs-lookup"><span data-stu-id="90955-156">**A Quick Note Regarding Larger Domains**</span></span>
  
<span data-ttu-id="90955-p110">如果您有超大型的網域 (擁有數萬名的使用者)，嘗試我們在本文中所示範的部分範例可能會走向「節流」。這表示根據如運算能力和可用網路頻寬等項目，您可能一次做太多事情。因此，較大型組織可能會想要將這些 Office 365 PowerShell 命令分割成兩個命令。例如，此命令會傳回所有使用者帳戶，並顯示每位使用者的名稱和位置：</span><span class="sxs-lookup"><span data-stu-id="90955-p110">If you have a very large domain with tens of thousands of users, trying some of the examples we show in this article could lead to "throttling." That means that, based on things like computing power and available network bandwidth, you're trying to do a little too much at one time. Because of that, larger organizations might want to split some of these Office 365 PowerShell commands into two commands. For example, this one command returns all the user accounts and shows the name and location for each:</span></span>
  
```
Get-MsolUser | Select DisplayName, UsageLocation
```

<span data-ttu-id="90955-p111">該命令非常適合較小型的網域。然而，在大型組織中，您可能需要將它分割成兩個命令：一個命令用來將使用者帳戶資訊儲存至變數中，而另一個命令用來顯示所需的資訊。範例如下：</span><span class="sxs-lookup"><span data-stu-id="90955-p111">That works great for smaller domains. In a large organization, however, you might need to split that into two commands: one command to store the user account information in a variable and another command to display the needed information. Here is an example:</span></span>
  
```
$x = Get-MsolUser
$x | Select DisplayName, UsageLocation
```


<span data-ttu-id="90955-164">這組 Office 365 PowerShell 命令的解譯如下：</span><span class="sxs-lookup"><span data-stu-id="90955-164">The interpretation of this set of Office 365 PowerShell commands is:</span></span>
- <span data-ttu-id="90955-165">取得目前 Office 365 訂閱中的所有使用者，並將資訊儲存至名為 $x 的變數 ( **$x = Get-MsolUser** )。</span><span class="sxs-lookup"><span data-stu-id="90955-165">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="90955-166">顯示變數 $x 的內容，但只會包括每位使用者的名稱和位置 ( **$x | Select DisplayName, UsageLocation** )。</span><span class="sxs-lookup"><span data-stu-id="90955-166">Display the contents of the variable $x, but only include the name and location for each user ( **$x | Select DisplayName, UsageLocation** ).</span></span>
  
## <a name="office-365-has-features-that-you-can-only-configure-with-office-365-powershell"></a><span data-ttu-id="90955-167">Office 365 具有的功能，僅供您搭配 Office 365 PowerShell 所設定</span><span class="sxs-lookup"><span data-stu-id="90955-167">Office 365 has features that you can only configure with Office 365 PowerShell</span></span>

<span data-ttu-id="90955-p112">Office 365 系統管理中心是要提供大部分人都適用之最常見或有意義系統管理工作的存取權。換句話說，Office 365 系統管理中心 系統管理中心的設計目的是讓一般系統管理員可以使用工具來執行最常見的管理工作。根據這項定義，這表示有一些工作無法使用 Office 365 系統管理中心來完成。</span><span class="sxs-lookup"><span data-stu-id="90955-p112">The Office 365 admin center is intended to provide access to the most common or meaningful administrative tasks that apply to most people. In other words, the Office 365 admin center was designed so that the typical administrator could use the tool to carry out the most common management tasks. By this definition, that means that there are some tasks that can't be completed by using the Office 365 admin center.</span></span>
  
<span data-ttu-id="90955-171">例如，商務用 Skype Online 系統管理中心提供一些選項來建立自訂會議邀請：</span><span class="sxs-lookup"><span data-stu-id="90955-171">For example, the Skype for Business Online Admin center provides a few options for creating custom meeting invitations:</span></span>
  
![在商務用 Skype Online 系統管理中心內，自訂會議邀請顯示方式的範例。](media/o365-powershell-meeting-invitation.png)
  
<span data-ttu-id="90955-p113">使用這些設定，您可以新增會議邀請的一些個人化和專門技術。不過，這不只是建立自訂會議邀請，還會進行其他會議組態設定。例如，會議預設允許：</span><span class="sxs-lookup"><span data-stu-id="90955-p113">With these settings, you can add a touch of personalization and professionalism to meeting invitations. However, there's more to meeting configuration settings than simply creating custom meeting invitations. For example, by default, meetings allow:</span></span>
  
- <span data-ttu-id="90955-176">匿名使用者自動進入每個會議。</span><span class="sxs-lookup"><span data-stu-id="90955-176">Anonymous users to gain automatic entrance to each meeting.</span></span>
    
- <span data-ttu-id="90955-177">出席者記錄會議。</span><span class="sxs-lookup"><span data-stu-id="90955-177">Attendees to record the meeting.</span></span>
    
- <span data-ttu-id="90955-178">您組織的所有使用者在加入會議時都會指定為主持人。</span><span class="sxs-lookup"><span data-stu-id="90955-178">All users from your organization to be designated as presenters when they join the meeting.</span></span>
    
<span data-ttu-id="90955-p114">這些設定無法從 商務用 Skype Online 系統管理中心取得。不過，您可以透過 Office 365 PowerShell 控制它們。以下是停用這三項設定的命令：</span><span class="sxs-lookup"><span data-stu-id="90955-p114">These settings are not available from the Skype for Business Online Admin center. However, you can control them from Office 365 PowerShell. Here is a command that disables these three settings:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> <span data-ttu-id="90955-182">這個命令需要您安裝 [商務用 Skype Online PowerShell 模組](https://www.microsoft.com/download/details.aspx?id=39366)。</span><span class="sxs-lookup"><span data-stu-id="90955-182">This command requires that you install the [Skype for Business Online PowerShell Module ](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="90955-183">此 Office 365 PowerShell 命令的解譯如下：對於新商務用 Skype Online 會議的設定 ( **Set-CsMeetingConfiguration** )，停用允許匿名使用者自動進入會議 ( **-AdmitAnonymousUsersByDefault $False** )、停用出席者錄製會議的功能 ( **-AllowConferenceRecording $False** )，但不會將您組織的所有使用者都指定為簡報者 ( **-DesignateAsPresenter "None"** )。</span><span class="sxs-lookup"><span data-stu-id="90955-183">The interpretation of this Office 365 PowerShell command is: For the settings for new Skype for Business Online meetings ( **Set-CsMeetingConfiguration** ), disable allowing anonymous users to gain automatic entrance to meetings ( **-AdmitAnonymousUsersByDefault $False** ), disable the ability for attendees to record meetings ( **-AllowConferenceRecording $False** ), and do not designate all users from your organization as presenters ( **-DesignateAsPresenter "None"** ).</span></span>
  
<span data-ttu-id="90955-184">如果您改變主意想要還原這些預設設定 (全部都已啟用)，請執行這個命令：</span><span class="sxs-lookup"><span data-stu-id="90955-184">If you change your mind and want to restore these default settings (all of them enabled), run this command:</span></span>
  
```
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

<span data-ttu-id="90955-p115">這只是其中一個範例。還有其他範例，這就是為什麼您身為 Office 365 系統管理員必須熟悉如何執行 Office 365 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="90955-p115">This is just one example. There are others, which is why you, as an Office 365 administrator, need to be comfortable with running Office 365 PowerShell commands.</span></span>
  
## <a name="office-365-powershell-is-great-at-carrying-out-bulk-operations"></a><span data-ttu-id="90955-187">Office 365 PowerShell 十分適合執行大量作業</span><span class="sxs-lookup"><span data-stu-id="90955-187">Office 365 PowerShell is great at carrying out bulk operations</span></span>

<span data-ttu-id="90955-p116">從歷史角度，執行單一作業時，視覺介面 (例如 Office 365 系統管理中心) 最為重要。例如，如果您需要停用一個使用者帳戶，則可以使用 Office 365 系統管理中心快速找出並清除核取方塊。這可能會比在 Office 365 PowerShell 中執行類似作業還要簡單。</span><span class="sxs-lookup"><span data-stu-id="90955-p116">Historically, visual interfaces like the Office 365 admin center are most valuable when you have a single operation to perform. For example, if you need to disable one user account, you can use the Office 365 admin center to quickly locate and clear a checkbox. This can be simpler than performing a similar operation in Office 365 PowerShell.</span></span>
  
<span data-ttu-id="90955-p117">但是，如果您必須變更許多事項或其他大量事項內的部分選取事項，則 Office 365 系統管理中心可能無法最佳利用您的時間。例如，如果您必須變更數千個電話號碼的首碼，或需要從所有 SharePoint Online 網站中移除特定使用者 (Ken Myer)，則在 Office 365 系統管理中心內要怎麼做？</span><span class="sxs-lookup"><span data-stu-id="90955-p117">But if you have to change many things or some selected things within a large set of other things, the Office 365 admin center might not be the best use of your time. For example, if you had to change the prefix on thousands of phone numbers or you needed to remove a specific user, Ken Myer, from all of your SharePoint Online sites, how would you do that in the Office 365 admin center?</span></span>
  
<span data-ttu-id="90955-p118">對於後面的範例，您有數百個 SharePoint Online 網站，而且甚至不知道 Ken Meyer 所屬的網站。這表示您必須在 Office 365 系統管理中心開始，然後針對每個網站執行此程序：</span><span class="sxs-lookup"><span data-stu-id="90955-p118">For the latter example, you have several hundred SharePoint Online sites and you don't know even know which ones of which Ken Meyer is a member. That means you'll have to start at the Office 365 admin center and then perform this procedure for each site:</span></span>
  
1. <span data-ttu-id="90955-195">按一下網站的 **URL** 。</span><span class="sxs-lookup"><span data-stu-id="90955-195">Click the **URL** of the site.</span></span>
    
2. <span data-ttu-id="90955-196">在 [網站集合內容] 方塊中，按一下 [網站位址] 連結以開啟網站。</span><span class="sxs-lookup"><span data-stu-id="90955-196">In the **site collection properties** box, click the **Web Site Address** link to open the site.</span></span>
    
3. <span data-ttu-id="90955-197">在網站上，按一下 [共用]。</span><span class="sxs-lookup"><span data-stu-id="90955-197">On the site, click **Share**.</span></span>
    
4. <span data-ttu-id="90955-198">在 [共用] 對話方塊中，按一下連結，以顯示所有具有網站權限的使用者：</span><span class="sxs-lookup"><span data-stu-id="90955-198">In the **Share** dialog box click the link that shows you all the users who have permissions to the site:</span></span>
    
     ![在 SharePoint Online 系統管理中心內，檢視 SharePoint Online 網站成員的範例。](media/o365-powershell-view-permissions.png)
  
5. <span data-ttu-id="90955-200">在 [共用對象] 對話方塊中，按一下 [進階]。</span><span class="sxs-lookup"><span data-stu-id="90955-200">In the **Shared With** dialog box, click **Advanced**.</span></span>
    
6. <span data-ttu-id="90955-201">捲動使用者清單，並尋找和選取 Ken Myer (假設他具有網站權限)，然後按一下 [移除使用者權限]。</span><span class="sxs-lookup"><span data-stu-id="90955-201">Scroll down the list of users, find and select Ken Myer (assuming he has permissions to the site), and then click **Remove User Permissions**.</span></span>
    
<span data-ttu-id="90955-202">因為有數百個網站，所以這可能需要很長的時間。</span><span class="sxs-lookup"><span data-stu-id="90955-202">This can take a long time for several hundred sites.</span></span>
  
<span data-ttu-id="90955-203">另一種方法是使用 Office 365 PowerShell 和下列命令，從所有網站中移除 Ken Myer：</span><span class="sxs-lookup"><span data-stu-id="90955-203">The alternative is to use Office 365 PowerShell and the following command to remove Ken Myer from all of your sites:</span></span>
  
```
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> <span data-ttu-id="90955-204">此指令需要您安裝[連線到 SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)。</span><span class="sxs-lookup"><span data-stu-id="90955-204">This command requires that you install the [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span> 
  
> [!TIP]
>  <span data-ttu-id="90955-205">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有 SharePoint 網站 ( **Get-SPOSite** )，並且針對每個網站，從可存取它的使用者清單中移除 Ken Meyer ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** )。</span><span class="sxs-lookup"><span data-stu-id="90955-205">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription ( **Get-SPOSite** ) and for each site, remove Ken Meyer from the list of users who can access it ( **ForEach {Remove-SPOUser -Site $\_.Url -LoginName "kenmyer@litwareinc.com"}** ).</span></span>
  
<span data-ttu-id="90955-p119">因為我們告訴 Office 365 移除每個網站中的 Ken Meyer (包括他沒有存取權的網站)，所以針對他目前沒有存取權的網站，此命令會顯示錯誤。我們可以在此命令上使用其他條件，只從登入清單中有 Key Meyer 的網站中移除 Key Meyer，但列出的錯誤不會傷害網站本身。此命令可能需要幾分鐘的時間來執行數百個網站，而非透過 Office 365 系統管理中心處理所需的數個小時。</span><span class="sxs-lookup"><span data-stu-id="90955-p119">Because we are telling Office 365 to remove Ken Meyer from every site, including those in which he does not have access, the display of this command will show errors for those sites in which he does not currently have access. We can use an additional condition on this command to remove Key Meyer only from the sites that have him in their login list, but the listed errors cause no harm to the sites themselves. This command might take a few minutes to run against hundreds of sites, rather than hours of working through the Office 365 admin center.</span></span>
  
<span data-ttu-id="90955-p120">以下是另一個大量作業範例。使用此命令將 Bonnie Kearney (新的 SharePoint 系統管理員) 新增至組織中的所有網站：</span><span class="sxs-lookup"><span data-stu-id="90955-p120">Here is another bulk operation example. Use this command to add Bonnie Kearney, a new SharePoint administrator, to all of the sites in the organization:</span></span>
  
```
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

> [!TIP]
>  <span data-ttu-id="90955-211">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有 SharePoint 網站，並針對每個網站，將 Bonnie Kearney 的登入名稱新增至網站的 [成員] 群組來允許她的存取權 ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** )。</span><span class="sxs-lookup"><span data-stu-id="90955-211">The interpretation of this Office 365 PowerShell command is:  Get all of the SharePoint sites in the current Office 365 subscription and for each site, allow Bonnie Kearney access by adding her login name to the Members group of the site ( **ForEach {Add-SPOUser -Site $\_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}** ).</span></span>
  
## <a name="office-365-powershell-is-great-at-filtering-data"></a><span data-ttu-id="90955-212">Office 365 PowerShell 十分適合篩選資料</span><span class="sxs-lookup"><span data-stu-id="90955-212">Office 365 PowerShell is great at filtering data</span></span>

<span data-ttu-id="90955-p121">Office 365 系統管理中心提供多種不同的資料篩選方式，可快速並輕鬆地找出資訊的目標子集。例如，Exchange 可輕鬆篩選使用者信箱的任何內容。例如，以下是住在布魯民頓市中所有使用者的信箱清單：</span><span class="sxs-lookup"><span data-stu-id="90955-p121">The Office 365 admin center provides several different ways to filter your data to quickly and easily locate a targeted subset of information. For example, Exchange makes it easy to filter on practically any property of a user mailbox. For example, here is the list of mailboxes for all the users who live in the city of Bloomington:</span></span>
  
![在 Office 365 系統管理中心內，進行針對所有居住在 Bloomington 市的使用者信箱清單的進階搜尋範例。](media/o365-powershell-advanced-search.png)
  
<span data-ttu-id="90955-p122">Exchange 系統管理中心也可讓您合併篩選準則。例如，您可以找到住在布魯民頓市並且在財務部門工作之所有人的信箱。</span><span class="sxs-lookup"><span data-stu-id="90955-p122">The Exchange Admin center also lets you combine filter criteria. For example, you can find the mailboxes for all the people who live in Bloomington and who work in the Finance department.</span></span> 
  
<span data-ttu-id="90955-p123">不過，在 Exchange 系統管理中心內有一些限制。例如，您可能想要找到住在布魯民頓市或聖地牙哥市之人員的信箱，或不住在布魯民頓市之所有人員的信箱。</span><span class="sxs-lookup"><span data-stu-id="90955-p123">However, there are limitations to what you can do in the Exchange Admin center. For example, maybe you'd like to find the mailboxes of people who live in Bloomington or San Diego, or the mailboxes for all the people who don't live in Bloomington.</span></span> 
  
<span data-ttu-id="90955-221">使用 Office 365 PowerShell，您可以透過此命令來取得住在布魯民頓市或聖地牙哥市之所有人員的信箱清單：</span><span class="sxs-lookup"><span data-stu-id="90955-221">With Office 365 PowerShell, you can get a list of mailboxes for all the people who live in the cities of Bloomington or San Diego with this command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

<span data-ttu-id="90955-222">以下是顯示範例：</span><span class="sxs-lookup"><span data-stu-id="90955-222">Here is an example of the display:</span></span>
  
```
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
Zrinka Makovac                           San Diego
```

> [!TIP]
>  <span data-ttu-id="90955-223">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中具有布魯民頓市或聖地牙哥市信箱的所有使用者 ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** )，然後顯示每個人員的名稱和城市 ( **Select DisplayName, City** )。</span><span class="sxs-lookup"><span data-stu-id="90955-223">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox in the cities of either San Diego or Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and ($\_.City -eq "San Diego" -or $\_.City -eq "Bloomington")}** ), then display the name and city for each ( **Select DisplayName, City** ).</span></span>
  
<span data-ttu-id="90955-224">若要列出不住在布魯民頓市之人員的所有信箱，則命令如下：</span><span class="sxs-lookup"><span data-stu-id="90955-224">To list all the mailboxes for people who live anywhere except Bloomington, here is the command:</span></span>
  
```
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

<span data-ttu-id="90955-225">以下是顯示範例：</span><span class="sxs-lookup"><span data-stu-id="90955-225">Here is an example of the display:</span></span>
  
```
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

> [!TIP]
>  <span data-ttu-id="90955-226">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中信箱不在布魯民頓市的所有使用者 ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** )，然後顯示每個使用者的名稱和城市。</span><span class="sxs-lookup"><span data-stu-id="90955-226">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription who have a mailbox not located in the city of Bloomington ( **Where {$\_.RecipientTypeDetails -eq "UserMailbox" -and $\_.City -ne "Bloomington"}** ), then display the name and city for each.</span></span>
  
<span data-ttu-id="90955-p124">您也可以在 Office 365 PowerShell 篩選中使用萬用字元，來比對局部名稱。例如，假設您正在尋找一個使用者帳戶，而且您只記得姓氏是 Anderson 或 Henderson，也可能是 Jorgenson。</span><span class="sxs-lookup"><span data-stu-id="90955-p124">You can also use wildcard characters in your Office 365 PowerShell filters to match part of a name. For example, suppose you're looking for a user account, and all you can remember is that their last name was Anderson, or maybe Henderson, or maybe it was Jorgenson.</span></span>
  
<span data-ttu-id="90955-229">您可以使用搜尋工具並執行三種不同搜尋，以在 Office 365 系統管理中心內追蹤該使用者：</span><span class="sxs-lookup"><span data-stu-id="90955-229">You could track down that user in the Office 365 admin center by using the search tool and carrying out three different searches:</span></span>
  
- <span data-ttu-id="90955-230">一個用於  *Anderson*</span><span class="sxs-lookup"><span data-stu-id="90955-230">One for  *Anderson*</span></span> 
    
- <span data-ttu-id="90955-231">一個用於  *Henderson*</span><span class="sxs-lookup"><span data-stu-id="90955-231">One for  *Henderson*</span></span> 
    
- <span data-ttu-id="90955-232">一個用於  *Jorgenson*</span><span class="sxs-lookup"><span data-stu-id="90955-232">One for  *Jorgenson*</span></span> 
    
<span data-ttu-id="90955-p125">因為這三個名稱的結尾都是 "son"，所以您可以告訴 Office 365 PowerShell 顯示名稱結尾為 "son" 的所有使用者。命令如下：</span><span class="sxs-lookup"><span data-stu-id="90955-p125">Because all three of these names end in "son", you can tell Office 365 PowerShell to display all the users whose name ends in "son". Here is the command:</span></span>
  
```
Get-User -Filter '{LastName -like "*son"}'
```

> [!TIP]
>  <span data-ttu-id="90955-p126">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有使用者，但使用只會列出姓氏結尾為 "son" 之使用者的篩選器 ( **-Filter '{LastName -like "\*son"}'** )。\* 代表任何字元集 (即使用者姓氏中的字母)。</span><span class="sxs-lookup"><span data-stu-id="90955-p126">The interpretation of this Office 365 PowerShell command is: Get all of the users in the current Office 365 subscription, but use a filter that only lists the users whose last names end in "son" ( **-Filter '{LastName -like "\*son"}'** ). The \* stands for any set of characters, which are letters in the case of the user's last name.</span></span>
  
## <a name="office-365-powershell-makes-it-easy-to-print-or-save-data"></a><span data-ttu-id="90955-237">Office 365 PowerShell 可讓您輕鬆地列印或儲存資料</span><span class="sxs-lookup"><span data-stu-id="90955-237">Office 365 PowerShell makes it easy to print or save data</span></span>

<span data-ttu-id="90955-p127">Office 365 系統管理中心可讓您檢視資料的清單。以下是顯示的已啟用 Skype 商務 Online 的使用者清單的商務 Online 系統管理中心 Skype 的範例：</span><span class="sxs-lookup"><span data-stu-id="90955-p127">The Office 365 admin center lets you view lists of data. Here is an example of the Skype for Business Online Admin center displaying a list of users who have been enabled for Skype for Business Online:</span></span>
  
![商務用 Skype Online 系統管理中心，顯示商務用 Skype Online 已啟用的使用者清單的範例。](media/o365-powershell-lync-users.png)
  
<span data-ttu-id="90955-p128">若要將該資訊儲存至檔案，您必須複製該資訊，並將它貼到文件或 Excel。在任一情況下，複本可能都需要進行其他格式設定。此外，Office 365 系統管理中心不提供方法來直接列印所顯示的清單。</span><span class="sxs-lookup"><span data-stu-id="90955-p128">To save that information to a file, you must copy and paste it into a document or Excel. In either case, the copy might require additional formatting. Additionally, the Office 365 admin center does not provide a way to directly print the displayed list.</span></span>
  
<span data-ttu-id="90955-p129">幸運的是，您可以使用 Office 365 PowerShell，這不只會顯示清單，還會將它儲存至可輕鬆地匯入至 Excel 的檔案。以下範例命令可將 商務用 Skype Online 使用者資料儲存為逗點分隔值 (CSV) 檔案，而這是可輕鬆地匯入為 Excel 工作表中的資料表的檔案：</span><span class="sxs-lookup"><span data-stu-id="90955-p129">Fortunately, you can use Office 365 PowerShell to not only display the list, but save it to a file that can be easily imported into Excel. Here is an example command to save Skype for Business Online user data to a comma-separated values (CSV) file, a file that can be easily imported as a table in an Excel worksheet:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

<span data-ttu-id="90955-246">以下是顯示範例：</span><span class="sxs-lookup"><span data-stu-id="90955-246">Here is an example of the display:</span></span>
  
![儲存成逗點分隔值 (CSV) 檔案的商務用 Skype Online 使用者資料表，匯入到 Excel 工作表中的範例。](media/o365-powershell-data-in-excel.png)
  
> [!TIP]
>  <span data-ttu-id="90955-248">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有商務用 Skype Online 使用者 ( **Get-CsOnlineUser** )、只取得使用者名稱、UPN 和位置 ( **Select DisplayName, UserPrincipalName, UsageLocation** )，然後將資訊儲存至名稱為 C:\\Logs\\SfBUsers.csv 的 CSV 檔案中 ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** )。</span><span class="sxs-lookup"><span data-stu-id="90955-248">The interpretation of this Office 365 PowerShell command is: Get all of the Skype for Business Online users in the current Office 365 subscription ( **Get-CsOnlineUser** ), obtain only the user name, UPN, and location ( **Select DisplayName, UserPrincipalName, UsageLocation** ), and then save that information in CSV file named C:\\Logs\\SfBUsers.csv ( **Export-Csv -Path "C:\\Logs\\SfBUsers.csv" -NoTypeInformation** ).</span></span>
  
<span data-ttu-id="90955-p130">您也可以使用選項，將此清單儲存為 XML 檔案或 HTML 頁面。事實上，使用其他 PowerShell 命令，您可以直接將它儲存為 Excel 檔 (內含任何您想要的自訂格式)。</span><span class="sxs-lookup"><span data-stu-id="90955-p130">You can also use options to save this list as an XML file or as an HTML page. In fact, with additional PowerShell commands, you could save it directly as an Excel file, with any custom formatting you desire.</span></span> 
  
<span data-ttu-id="90955-p131">您也可以傳送 Office 365 PowerShell 命令的輸出，而此命令會直接將清單顯示在 Windows 的預設印表機中。範例命令如下：</span><span class="sxs-lookup"><span data-stu-id="90955-p131">You can also send the output of an Office 365 PowerShell command that displays a list directly to the default printer in Windows. Here is an example command:</span></span>
  
```
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

<span data-ttu-id="90955-253">以下是您將列印出的文件樣貌：</span><span class="sxs-lookup"><span data-stu-id="90955-253">Here's what your printed document will look like:</span></span>
  
![Office 365 PowerShell 命令直接列在 Windows 預設印表機上，所輸出的列印文件範例。](media/o365-powershell-printed-data.png)
  
> [!TIP]
>  <span data-ttu-id="90955-255">此 Office 365 PowerShell 命令的解譯如下：取得目前 Office 365 訂閱中的所有商務用 Skype Online 使用者、只取得使用者名稱、UPN 和位置，然後將該資訊傳送至預設 Windows 印表機 ( **Out-Printer** )。</span><span class="sxs-lookup"><span data-stu-id="90955-255">The interpretation of this Office 365 PowerShell command is:  Get all of the Skype for Business Online users in the current Office 365 subscription, obtain only the user name, UPN, and location, and then send that information to the default Windows printer ( **Out-Printer** ).</span></span>
  
<span data-ttu-id="90955-256">列印出的文件與 Office 365 PowerShell 命令視窗內所顯示的內容，具有相同的簡單格式，但建立 Office 365 PowerShell 命令來列出您需要的內容之後，只要將 **| Out-Printer** 新增至命令的結尾，即可取得可使用的複本。</span><span class="sxs-lookup"><span data-stu-id="90955-256">The printed document has the same simple formatting as the display within the Office 365 PowerShell command window, but once you have created an Office 365 PowerShell command to list what you need, you just add **| Out-Printer** to the end of the command to get a hard copy to work from.</span></span>
  
## <a name="office-365-powershell-lets-you-manage-across-server-products"></a><span data-ttu-id="90955-257">Office 365 PowerShell 可讓您管理數個伺服器產品</span><span class="sxs-lookup"><span data-stu-id="90955-257">Office 365 PowerShell lets you manage across server products</span></span>

<span data-ttu-id="90955-p132">構成 Office 365 的不同元件是設計為一起使用。例如，假設您新增 Office 365 的新使用者，並在新增時指定使用者部門和電話號碼之類的資訊。如果您使用任何 Office 365 伺服器產品存取使用者的資訊，即可使用這些資訊。商務用 Skype Online、Exchange 或 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="90955-p132">The different components that make up Office 365 are designed to work together. For example, suppose you add a new user to Office 365 and, when you do, you specify such information as the user's department and phone number. That information will then be available if you access the user's information using any of the Office 365 server products: Skype for Business Online, Exchange, or SharePoint Online.</span></span>
  
<span data-ttu-id="90955-p133">不過，這是對跨越產品系列的一般資訊而言。產品特定資訊 (例如，使用者的 Exchange 信箱相關資訊) 通常不會跨系列提供。例如，如果您想要知道是否已啟用使用者的信箱，則只能在 Exchange 系統管理中心內取得該資訊。</span><span class="sxs-lookup"><span data-stu-id="90955-p133">But that's for common information that spans the suite of products. Product-specific information-for example, information about a user's Exchange mailbox-is typically not available across the suite. For example, if you want to know if a user's mailbox is enabled or not, that information is available only in the Exchange Admin center.</span></span> 
  
<span data-ttu-id="90955-264">假設您想要製作一份報告，顯示所有使用者的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="90955-264">Suppose you'd like to make a report that shows the following information for all your users:</span></span>
  
- <span data-ttu-id="90955-265">使用者的顯示名稱</span><span class="sxs-lookup"><span data-stu-id="90955-265">The user's display name</span></span>
    
- <span data-ttu-id="90955-266">使用者是否獲得 Office 365 的授權</span><span class="sxs-lookup"><span data-stu-id="90955-266">Whether the user is licensed for Office 365</span></span>
    
- <span data-ttu-id="90955-267">使用者的 Exchange 信箱是否已啟用</span><span class="sxs-lookup"><span data-stu-id="90955-267">Whether the user's Exchange mailbox has been enabled</span></span>
    
- <span data-ttu-id="90955-268">是否已對使用者啟用商務用 Skype Online</span><span class="sxs-lookup"><span data-stu-id="90955-268">Whether the user is enabled for Skype for Business Online</span></span>
    
<span data-ttu-id="90955-p134">您目前無法使用 Office 365 系統管理中心來輕鬆地產生這類報告。而是需要建立個別的文件來儲存資訊 (例如 Excel 工作表)，並從 Office 365 系統管理中心取得所有使用者名稱和授權資訊、從 Exchange 系統管理中心取得信箱資訊、從商務用 Skype Online 系統管理中心取得商務用 Skype Online 資訊，然後自動分頁並合併該資訊。</span><span class="sxs-lookup"><span data-stu-id="90955-p134">You currently cannot use the Office 365 admin center to easily produce such a report. Instead, you'll have to create a separate document to store the information, like an Excel worksheet, and get all the user names and licensing information from the Office 365 admin center, get mailbox information from the Exchange Admin center, get Skype for Business Online information from the Skype for Business Online Admin center, and then collate and combine that information.</span></span>
  
<span data-ttu-id="90955-271">另一種方法是使用 Office 365 PowerShell 指令碼來編譯該報告。</span><span class="sxs-lookup"><span data-stu-id="90955-271">The alternative is to use an Office 365 PowerShell script to compile that report for you.</span></span>
  
<span data-ttu-id="90955-p135">下列範例指令碼會比目前為止在本文中看過的命令還要複雜。但是，它示範可能可以使用 Office 365 PowerShell 建立很難做到的資訊檢視。以下指令碼可以編譯並顯示所需的清單：</span><span class="sxs-lookup"><span data-stu-id="90955-p135">The following example script is more complicated than the commands you have seen so far in this article. But, it shows the potential of using Office 365 PowerShell to create views of information that are very difficult to do otherwise. Here is the script that can compile and display the needed list:</span></span>
  
```
$x = Get-MsolUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

<span data-ttu-id="90955-275">以下是顯示範例：</span><span class="sxs-lookup"><span data-stu-id="90955-275">Here is an example of the display:</span></span>
  
```
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Zrinka Makovac          True         True               True
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

<span data-ttu-id="90955-276">此 Office 365 PowerShell 指令碼的解譯如下：</span><span class="sxs-lookup"><span data-stu-id="90955-276">The interpretation of this Office 365 PowerShell script is:</span></span>  
- <span data-ttu-id="90955-277">取得目前 Office 365 訂閱中的所有使用者，並將資訊儲存至名為 $x 的變數 ( **$x = Get-MsolUser** )。</span><span class="sxs-lookup"><span data-stu-id="90955-277">Get all of the users in the current Office 365 subscription and store the information in a variable named $x ( **$x = Get-MsolUser** ).</span></span>
- <span data-ttu-id="90955-278">開始迴圈，而迴圈會對名稱為 $x 之變數中的所有使用者執行 ( **foreach ($i in $x)** )。</span><span class="sxs-lookup"><span data-stu-id="90955-278">Start a loop that runs over all the users in the variable named $x ( **foreach ($i in $x)** ).</span></span>  
- <span data-ttu-id="90955-279">定義名稱為 $y 的變數，並在其中儲存使用者的信箱資訊 ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="90955-279">Define a variable named $y and store the user's mailbox information in it ( **$y = Get-Mailbox -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="90955-280">將新的屬性新增至名稱為 IsMailBoxEnabled 的使用者資訊，並將它設定為使用者信箱的 IsMailBoxEnabled 屬性值 ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** )。</span><span class="sxs-lookup"><span data-stu-id="90955-280">Add a new property to the user information named IsMailBoxEnabled and set it to the value of the IsMailBoxEnabled property of the user's mailbox ( **$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled** ).</span></span>
- <span data-ttu-id="90955-281">定義名稱為 $y 的變數，並在其中儲存使用者的商務用 Skype Online 資訊 ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="90955-281">Define a variable named $y and store the user's Skype for Business Online information in it ( **$y = Get-CsOnlineUser -Identity $i.UserPrincipalName** ).</span></span>
- <span data-ttu-id="90955-282">將新的屬性新增至名稱為 EnabledForSfB 的使用者資訊，並將它設定為使用者之商務用 Skype Online 資訊的 Enabled 屬性值 ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** )。</span><span class="sxs-lookup"><span data-stu-id="90955-282">Add a new property to the user information named EnabledForSfB and set it to the value of the Enabled property of the user's Skype for Business Online information ( **$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled** ).</span></span>
- <span data-ttu-id="90955-283">顯示使用者清單，但只包括其名稱、是否獲得授權，以及指出是否已啟用其信箱以及其是否已啟用商務用 Skype Online 的兩個新屬性 ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** )。</span><span class="sxs-lookup"><span data-stu-id="90955-283">Display the list of users, but include only their name, whether they are licensed, and the two new properties that indicate whether their mailbox is enabled and whether they are enabled for Skype for Business Online ( **$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB** ).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="90955-284">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90955-284">See also</span></span>

[<span data-ttu-id="90955-285">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="90955-285">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="90955-286">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="90955-286">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="90955-287">使用 Windows PowerShell 在 Office 365 中建立報告</span><span class="sxs-lookup"><span data-stu-id="90955-287">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)

