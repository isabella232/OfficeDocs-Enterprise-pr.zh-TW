---
title: "使用 Office 365 PowerShell 移除使用者帳戶中的授權"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
- DecEntMigration
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "說明如何使用 Office 365 PowerShell 移除先前已指派給使用者的 Office 365 授權。"
ms.openlocfilehash: 90cae603a7a7cda0b7318571d3eb045f750fd58d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a4382-103">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="a4382-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a4382-104">**摘要：**說明如何使用 Office 365 PowerShell 移除先前已指派給使用者的 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="a4382-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="a4382-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="a4382-105">Before you begin</span></span>

- <span data-ttu-id="a4382-p101">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a4382-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a4382-108">若要檢視您的組織的授權的計劃 ( **AccountSkuID** ) 資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a4382-108">To view the licensing plan ( **AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="a4382-109">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="a4382-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="a4382-110">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="a4382-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="a4382-111">如果您使用**Get-msoluser** cmdlet 而不需使用_-所有_參數，傳回前 500 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4382-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="a4382-112">簡短版本 (不含說明的指示)</span><span class="sxs-lookup"><span data-stu-id="a4382-112">The short version (instructions without explanations)</span></span>
<span data-ttu-id="a4382-113"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a4382-113"></span></span>

<span data-ttu-id="a4382-p102">本節僅呈現程序，但不提供詳盡或多餘的說明。如果您有任何問題或需要詳細資訊，您可以閱讀本主題的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="a4382-p102">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="a4382-116">若要移除現有使用者帳戶中的授權，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a4382-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="a4382-117">此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權與使用者帳戶 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="a4382-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="a4382-118">若要移除現有的經授權使用者群組的授權，使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="a4382-118">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="a4382-119">**篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a4382-119">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="a4382-120">此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從所有 accounts 在美國 「 業務 」 部門中的使用者。</span><span class="sxs-lookup"><span data-stu-id="a4382-120">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="a4382-121">**使用特定帳戶的清單**若要這樣做，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a4382-121">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="a4382-122">建立一個每一行一個帳戶的文字檔，像這樣：</span><span class="sxs-lookup"><span data-stu-id="a4382-122">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="a4382-123">使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a4382-123">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="a4382-124">此範例會移除`litwareinc:ENTERPRISEPACK`從文字檔案 C:\My Documents\Accounts.txt 中所定義的使用者帳戶 (Office 365 企業版 E3) 授權。</span><span class="sxs-lookup"><span data-stu-id="a4382-124">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="a4382-125">若要移除所有現有使用者帳戶中的授權，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a4382-125">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="a4382-126">此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從現有的所有授權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4382-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="a4382-127">冗長版本 (包含詳細說明的指示)</span><span class="sxs-lookup"><span data-stu-id="a4382-127">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="a4382-128"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a4382-128"></span></span>

<span data-ttu-id="a4382-p103">不會持續永久，並包含 Office 365 授權： 提前或更新版本中，會有當您需要移除授權的使用者帳戶的時間。使用者離開 ； 在將要的也許也許使用者不再需要授權;也許-，有做了明顯改善任意數量的原因為何您可能會想要移除的使用者授權。</span><span class="sxs-lookup"><span data-stu-id="a4382-p103">Nothing lasts forever, and that includes Office 365 licenses: sooner or later, there will come a time when you need to remove a license from a user account. Maybe the user is going on leave; maybe the user no longer needs the license; maybe - well, there are obviously any number of reasons why you might want to remove a user license.</span></span>
  
<span data-ttu-id="a4382-p104">我們任何進一步請務必注意移除授權需要，以及之前，請移除授權： 停用所有服務的意涵是同一個兩回事移除授權。例如，假設我們使用所有適用的 Office 365 授權; 向上換句話說，我們有無授權提供也不會收到。您決定要遵循中用以停用所有服務之後，Belinda Newman 的帳戶上的 [[停都用 Office 365 powershell 的服務存取權](disable-access-to-services-with-office-365-powershell.md)的程序。我們執行動作，多少授權的後將我們會提供對我們吗？這是右： 零。是，該主題中的程序就會*停用*Belinda 的授權上的所有服務，但不是都會停用 （亦即刪除） 本身的授權。授權仍會有效，而且它仍然會指派給 Belinda Newman。她只是將無法存取任何 Office 365 服務使用的授權。</span><span class="sxs-lookup"><span data-stu-id="a4382-p104">Before we go any further it's important to note that removing a license requires you to, well, remove the license: disabling all the services on a license is not the same thing as removing a license. For example, suppose we've used up all our Office 365 licenses; in other words, we have no licenses available whatsoever. You decide to follow the procedure in [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md) to disable all the services, say, on Belinda Newman's account. After we do that, how many licenses will we have available to us? That's right: zero. Yes, the procedure from that topic will *disable*  all the services on Belinda's license, but it will not disable (i.e., delete) the license itself. The license will still be valid, and it will still be assigned to Belinda Newman. She just won't be able to use that license to access any Office 365 services.</span></span>
  
<span data-ttu-id="a4382-p105">與這很重要： 如果您想要移除使用者的授權必須實際中*移除*授權。停用所有服務會防止使用者登入 Office 365 中，但它不會釋出其授權。如果您想要取回授權是目前指派給使用者您需要執行此的話真正移除先前已指派給 Belinda 的授權會使用_RemoveLicenses_參數的命令如下的命令：</span><span class="sxs-lookup"><span data-stu-id="a4382-p105">And that's important: if you want to remove a license from a user you must actually  *remove*  the license. Disabling all the services will prevent the user from logging on to Office 365, but it won't free up his or her license. If you want to take back a license that's currently assigned to a user you need to run a command similar to this one, a command that uses the _RemoveLicenses_ parameter to actually remove the license previously assigned to Belinda:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="a4382-142">執行命令並 Belinda Newman 就不再被授權使用 Office 365。</span><span class="sxs-lookup"><span data-stu-id="a4382-142">Run that command, and Belinda Newman will no longer be licensed to use Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a4382-p106">如您所見，當您使用_RemoveLicenses_參數，您需要指定要移除授權的名稱。如果您不確定哪一個授權方案用來將授權指派給使用者，請直接執行這類命令：`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span><span class="sxs-lookup"><span data-stu-id="a4382-p106">As you can see, when you use the  _RemoveLicenses_ parameter you need to specify the name of the license to be removed. If you aren't sure which licensing plan was used to assign a license to the user just run a command like this:  `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`</span></span>
  
<span data-ttu-id="a4382-145">若要驗證授權已確實移除，請使用 Get-MsolUser 檢查使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="a4382-145">To verify that the license really was removed, use the Get-MsolUser to check the user account in question:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

<span data-ttu-id="a4382-146">如果一切皆依計劃，Belinda 的**isLicensed**屬性現在將`False`：</span><span class="sxs-lookup"><span data-stu-id="a4382-146">If everything went according to plan, Belinda's **isLicensed** property will now be set to `False`:</span></span>
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

<span data-ttu-id="a4382-p107">釋放授權的另一種方式是由刪除的使用者帳戶。如需詳細資訊，請參閱[刪除並還原與 Office 365 PowerShell 的使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a4382-p107">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a4382-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4382-149">See also</span></span>

<span data-ttu-id="a4382-150">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="a4382-150">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="a4382-151">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4382-151">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4382-152">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4382-152">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4382-153">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4382-153">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4382-154">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4382-154">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="a4382-155">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a4382-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a4382-156">Get-content</span><span class="sxs-lookup"><span data-stu-id="a4382-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="a4382-157">Get-msoluser</span><span class="sxs-lookup"><span data-stu-id="a4382-157">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="a4382-158">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="a4382-158">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="a4382-159">Foreach-object</span><span class="sxs-lookup"><span data-stu-id="a4382-159">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="a4382-160">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a4382-160">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="a4382-161">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="a4382-161">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="a4382-p108">![簡短 LinkedIn 學習圖示](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png)**新增至 Office 365？**        [Office 365 系統管理員及 IT 專業人員](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)，傳送給您的 LinkedIn 學習探索免費的視訊課程。</span><span class="sxs-lookup"><span data-stu-id="a4382-p108">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   

