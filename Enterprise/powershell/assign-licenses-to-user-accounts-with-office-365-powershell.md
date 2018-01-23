---
title: "使用 Office 365 PowerShell 指派授權至使用者帳戶"
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。"
ms.openlocfilehash: 8a7ad7b4586ccdef95430f9c4cc9c4d6e9360070
ms.sourcegitcommit: f10e47df0dca4a241659f33061db5217ebc3401e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d57cb-103">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d57cb-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d57cb-104">**摘要：** 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="d57cb-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="d57cb-p101">授權 Office 365 中的使用者帳戶很重要，因為使用者無法使用任何 Office 365 服務之前已授權其帳戶。您可以使用 Office 365 PowerShell 有效率地將授權指派給未授權的帳戶，特別是多個帳戶。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="d57cb-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="d57cb-107">Before you begin</span></span>
<span data-ttu-id="d57cb-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="d57cb-108"></span></span>

- <span data-ttu-id="d57cb-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d57cb-p103">使用**Get-msolaccountsku**指令程式來檢視您組織中每個計劃中可用的授權方案和可用授權數量。每個計劃中的可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。如需授權方案、 授權及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d57cb-114">若要在組織中尋找未授權的帳戶，請執行命令`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="d57cb-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="d57cb-p104">您只能指派授權給**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2 國家/地區碼的使用者帳戶。例如，我們美國、 和法國的 FR。某些 Office 365 服務都無法提供在某些國家/地區。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="d57cb-p105">若要尋找沒有**UsageLocation**值的帳戶，請執行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若帳戶上設定**UsageLocation**值，使用語法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="d57cb-122">如果您使用**Get-msoluser** cmdlet 而不需使用`-All`參數，傳回前 500 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d57cb-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="d57cb-123">簡短版本 (不含說明的指示)</span><span class="sxs-lookup"><span data-stu-id="d57cb-123">The short version (instructions without explanations)</span></span>
<span data-ttu-id="d57cb-124"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="d57cb-124"></span></span>

<span data-ttu-id="d57cb-p106">本節內容提供不含詳細說明的程序。如果您有任何問題或想要的詳細資訊，您可以閱讀主題的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p106">This section presents the procedures without detailed explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="d57cb-127">若要將授權指派給使用者，請在 Office 365 PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="d57cb-127">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="d57cb-128">此範例會將指定的授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 給未授權使用者的授權方案`belindan@litwareinc.com`。</span><span class="sxs-lookup"><span data-stu-id="d57cb-128">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d57cb-129">若要將授權指派給多位未經授權的使用者，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="d57cb-129">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="d57cb-130">**附註**</span><span class="sxs-lookup"><span data-stu-id="d57cb-130">**Notes**</span></span>
  
- <span data-ttu-id="d57cb-131">您無法將多個授權指派給相同授權計劃中的使用者。</span><span class="sxs-lookup"><span data-stu-id="d57cb-131">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="d57cb-132">如果您沒有足夠可用的授權，授權指派給使用者他們正在可用授權執行之前**Get-msoluser** cmdlet 所傳回的順序。</span><span class="sxs-lookup"><span data-stu-id="d57cb-132">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="d57cb-133">本範例會將指派授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 所有未授權使用者的授權方案。</span><span class="sxs-lookup"><span data-stu-id="d57cb-133">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="d57cb-134">本範例會將相同的授權指派給美國境內銷售部門中未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="d57cb-134">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="d57cb-135">冗長版本 (包含詳細說明的指示)</span><span class="sxs-lookup"><span data-stu-id="d57cb-135">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="d57cb-136"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="d57cb-136"></span></span>

<span data-ttu-id="d57cb-p107">[檢視授權和未授權使用者與 Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md)本文所述，很可能有的使用者擁有有效的 Office 365 使用者帳戶，但誰不已核發給 Office 365 授權。這表示有效的帳戶或沒有有效的帳戶，這些使用者將無法登入 Office 365。與如果您無法登入，您無法利用任何 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p107">As noted in the article [View licensed and unlicensed users with Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md), it's possible to have users who have valid Office 365 user accounts, but who have not been issued an Office 365 license. That means that, valid account or no valid account, those users will not be able to log on to Office 365. And if you can't log on, you can't take advantage of any Office 365 services.</span></span>
  
<span data-ttu-id="d57cb-140">前述文章也提到，我們可以執行下列命令，以傳回未授權的使用者帳戶清單：</span><span class="sxs-lookup"><span data-stu-id="d57cb-140">The aforementioned article also noted that we can return a list of unlicensed user accounts by running this command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="d57cb-141">該命令會傳回目前未授權 Office 365 的任何使用者的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="d57cb-141">That command returns information about any users who are not currently licensed for Office 365:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

<span data-ttu-id="d57cb-p108">如您所見，有一個授權的使用者： Belinda Newman。我們到有關 Office 365 授權指派 Belinda 那要如何？</span><span class="sxs-lookup"><span data-stu-id="d57cb-p108">As you can see, we have one unlicensed user: Belinda Newman. So how do we go about assigning Belinda an Office 365 license?</span></span>
  
<span data-ttu-id="d57cb-144">首先，我們要執行[檢視授權和 services 與 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)文章中討論的**Get-msolaccountsku**指令程式：</span><span class="sxs-lookup"><span data-stu-id="d57cb-144">For starters, we're going to run the **Get-MsolAccountSku** cmdlet discussed in the article [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md):</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="d57cb-145">此命令會傳回如下的資料：</span><span class="sxs-lookup"><span data-stu-id="d57cb-145">That command returns data similar to this:</span></span>
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

<span data-ttu-id="d57cb-p109">為什麼我們並未執行**Get-msolaccountsku** ？（"Sku，"以防您想知道，是簡短的"stock 保存單位。 」對我們來說是剛商務-說話的 「 產品 」。）原因有兩種為什麼我們已執行**Get-msolaccountsku**。首先，我們需要確定我們實際上已指派 Belinda 的授權。有任何我們可以指派她的授權吗？若要判斷我們需要**ActiveUnits**屬性 (25) 的值，並由欄位刪減**WarningUnits** (0) 和**ConsumedUnits** (24) 屬性的值：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p109">Why did we run **Get-MsolAccountSku** ? ("Sku," in case you're wondering, is short for "stock-keeping unit." For our purposes, that's just business-speak for "product.") There are two reasons why we ran **Get-MsolAccountSku**. First, we need to make sure we actually have a license to assign Belinda. Do we have any licenses we can assign her? To determine that, we take the value of **ActiveUnits** property (25) and subtract the values of the **WarningUnits** (0) and **ConsumedUnits** (24) properties:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="d57cb-p110">**ActiveUnits**屬性會告訴我們多少個授權購買我們，以及**WarningUnits**和**ConsumedUnits**的結合的值告訴我們多少個授權目前正在使用中。如果我們由欄位刪減已經從我們所購買的授權數目讀出的授權數目，我們會知道多少授權仍可用。幸運會有其，我們有一個授權可用的通訊群組：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p110">The **ActiveUnits** property tells us how many licenses we've purchased, and the combined value of **WarningUnits** and **ConsumedUnits** tells us how many licenses are currently in use. If we subtract the number of licenses already spoken for from the number of licenses we purchased, we'll know how many licenses are still available. As luck would have it, we have one license available for distribution:</span></span>
  
 `25 - 0 - 24 = 1`
  
<span data-ttu-id="d57cb-p111">若要指派我們需要知道我們的授權方案名稱的新授權給 Belinda 的第二個 （也就是我們需要知道**AccountSkuId** ）。在此例中很簡單： 我們只能有單一的授權方案 ( `litwareinc:ENTERPRISEPACK`)。但是請注意是可能的組織有多個授權方案。在此情況下， **Get-msolaccountsku**會傳回兩個不同**AccountSkuIds**且您必須選擇適當的授權方案時指派授權。現在，儘管如此，我們要堅持最簡單的情況下，並假設我們只是一個授權方案。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p111">Second, in order to assign Belinda a new license we need to know the name of our licensing plan (that is, we need to know the **AccountSkuId** ). In this case, that's easy: we only have a single licensing plan ( `litwareinc:ENTERPRISEPACK`). Note, however, that it's possible for an organization to have multiple licensing plans. In that case, **Get-MsolAccountSku** would return two different **AccountSkuIds**, and you would need to pick the appropriate licensing plan when assigning licenses. For now, though, we're going to stick with the simplest case, and assume we have just one licensing plan.</span></span>
  
<span data-ttu-id="d57cb-p112">*如何那麼我們要指派給 Belinda Newman 一個新的授權？*類似：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p112">So then how  *do*  we assign Belinda Newman a new license? Like this:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d57cb-162">這也是您必須執行動作： 呼叫**Set-msoluserlicense** cmdlet，確定您指定的使用者與適當的授權方案_UserPrincipalName_參數。</span><span class="sxs-lookup"><span data-stu-id="d57cb-162">That's also you have to do: just call the **Set-MsolUserLicense** cmdlet, making sure that you specify the _UserPrincipalName_ parameter for the user and the appropriate licensing plan.</span></span>
  
<span data-ttu-id="d57cb-163">當**Set-msoluserlicense**執行完成時，您會看到類似此螢幕上：</span><span class="sxs-lookup"><span data-stu-id="d57cb-163">When **Set-MsolUserLicense** finishes running, you'll see something similar to this onscreen:</span></span>
  
 `PS C:\\windows\\system32>`
  
<span data-ttu-id="d57cb-p113">換句話說，它將不會看起來像是發生的任何項目。若要確認使用者具有已指派授權，執行如下所示的命令：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p113">In other words, it won't look like anything has happened. To verify that the user has been assigned a license, run a command like the following:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

<span data-ttu-id="d57cb-166">如果一切都如預期般，您應該會看到 Belinda 的 isLicensed 屬性現在已設為 True：</span><span class="sxs-lookup"><span data-stu-id="d57cb-166">If everything worked as expected, you should see that Belinda's isLicensed property is now set to True:</span></span>
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!安全性附註]<span data-ttu-id="d57cb-p114"> 不錯的問題： 如果您進行錯誤並嘗試將授權指派給已具有授權的使用者吗？您將會結束向上給單一使用者提供兩個授權吗？> 快速的回答？無;Office 365 將不會讓您將多個授權指派給相同的使用者。（，從相同的授權方案的多個授權，即）。如果您嘗試執行的命令會失敗下列錯誤訊息： > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> 不可否認，這個錯誤訊息會稍微誤導： 授權不是真正無效、 只被指派給使用者之已連授權 [*具有*。不過，錯誤訊息預留，最重要的一位使用者將不會使用多個授權最後。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p114"> Good question: what if you made a mistake and tried to assign a license to a user who already has a license? Will you end up giving two licenses to a single user? > The quick answer? No; Office 365 won't let you assign more than one license to the same user. (Well, more than one license from the same licensing plan, that is.) If you try to do that your command will fail with the following error message: >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> Admittedly, that error message is a tiny bit misleading: the license isn't really invalid, it's just being assigned to a user who already  *has*  a license. But, error message aside, the important thing is that one user won't end up with multiple licenses.</span></span>
  
<span data-ttu-id="d57cb-p115">如您剛才所見，它會是很容易使用 Office 365 PowerShell 將單一授權指派給單一使用者。與之負責人明顯的問題： 有用為一樣簡單、 也許甚至更容易，若要使用 Office 365 系統管理中心來將單一授權指派給單一使用者吗？也許 ； 以及而定，組件，您正在更知道如何使用 Windows PowerShell 或更多知道如何使用 Office 365 系統管理中心。真正發揮功效的 Windows PowerShell，但也將多個授權指派給多位使用者在需要時。例如，此命令會將 Office 365 授權指派給任何您沒有授權的使用者：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p115">As you've just seen, it's very easy to use Office 365 PowerShell to assign a single license to a single user. And that leads to an obvious question: wouldn't it be just as easy, maybe even easier, to use the Office 365 admin center to assign a single license to a single user? Well, maybe; that depends, in part, on whether you're more comfortable using Windows PowerShell or more comfortable using the Office 365 admin center. Where Windows PowerShell really shines, however, is when you need to assign multiple licenses to multiple users. For example, this command assigns an Office 365 license to any of your users that don't already have a license:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d57cb-p116">在上述命令中，我們使用**Get-msoluser**和_UnlicensedUsersOnly_參數來傳回所有授權的使用者帳戶的集合。然後將該集合傳遞到**Set-msoluserlicense**指令程式 ；接著，**就**會將指派授權 (取自`litwareinc:ENTERPRISEPACK`授權方案) 給集合中每個使用者。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p116">In the preceding command, we use **Get-MsolUser** and the _UnlicensedUsersOnly_ parameter to return a collection of all the unlicensed user accounts. We then pass that collection to the **Set-MsolUserLicense** cmdlet; in turn, **Set-MsolUserLicense** assigns a license (taken from the `litwareinc:ENTERPRISEPACK` licensing plan) to each user in the collection.</span></span>
  
<span data-ttu-id="d57cb-p117">不過，如果您有 5 未授權的使用者只有一個可用的授權但吗？在此情況下**就**會將可用授權提供給**Get-msoluser**所傳回的第一個使用者。**Set-msoluserlicense**將然後盡責嘗試將授權指派給四個使用者，但總共四個那些嘗試將會失敗搭配下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p117">Ah, but what if you have 5 unlicensed users but only one available license? In that case **Set-MsolUserLicense** will give the available license to the first user returned by **Get-MsolUser**. **Set-MsolUserLicense** will then dutifully try to assign a license to the other four users, but all four of those attempts will fail along with the following error message:</span></span>
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
<span data-ttu-id="d57cb-p118">換句話說，就只是將不會失敗。而它將指派其可以為相同數目的授權。它只會失敗。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p118">In other words, Set-MsolUserLicense won't just fail. Instead, it will assign as many licenses as it can. Only then will it fail.</span></span>
  
<span data-ttu-id="d57cb-p119">我們嘗試另一個範例。也許您想要將授權指派給 Sales 部門中的所有使用者。沒有問題：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p119">Let's try another example. Maybe you'd like to assign a license to all the users in the Sales department. No problem:</span></span>
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d57cb-189">或者，如果您想要再有技巧性一點，並且想要儘量減少錯誤訊息和運算處理，那就只要指派授權給業務部門中未授權的使用者即可：</span><span class="sxs-lookup"><span data-stu-id="d57cb-189">Or, if you want to get really fancy, and if you want to keep error messages and computing processing to a minimum, just assigned a license to unlicensed users from the Sales department:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d57cb-p120">畢竟是無點到已授權的授權使用者嘗試。如我們所見，可將無法運作。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p120">After all, there's no point trying to license users who already have a license. As we've already seen, that won't work.</span></span>
  
<span data-ttu-id="d57cb-p121">以下是另一個範例。也許您想要所有美國目前沒有使用者的 Office 365 授權的授權。在此情況下：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p121">Here's another example. Maybe you'd like to license all the US users who don't currently have an Office 365 license. In that case:</span></span>
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d57cb-195">等等，依此類推。</span><span class="sxs-lookup"><span data-stu-id="d57cb-195">And so on and so on.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d57cb-p122">執行命令的說，對所有未授權使用者發出授權需要多久的時間？這是很難說： 定從必須為您的網路連線速度的使用者數目的每個項目。如果您有幾個好幾百種這快速合理預期的授權使用者 （亦即，它不應該採取以上數分鐘或兩個）。如果您有 10000 位使用者來授權它會做了明顯改善時間更長。但想像只要它來採用以使用 Office 365 系統管理中心將授權指派給 10000 位使用者。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p122">How long does it take to run a command that, say, issues licenses to all your unlicensed users? That's difficult to say: it depends on everything from the number of users you have to the speed of your network connection. If you have a couple hundred users to license this will go reasonably quickly (that is, it shouldn't take more than a minute or two). If you have 10,000 users to license it will obviously take a little longer. But nowhere near as long as it would take to assign licenses to 10,000 users by using the Office 365 admin center.</span></span> 
  
<span data-ttu-id="d57cb-p123">只要我們已經在主旨，以下是您要指派授權時需要留意的： 如果使用者沒有**UsageLocation**屬性設定值您不能指派給該使用者的 Office 365 授權。而您會收到錯誤訊息類似：</span><span class="sxs-lookup"><span data-stu-id="d57cb-p123">As long as we're on the subject, here's something you need to watch out for when assigning licenses: if a user does not have a value configured for the **UsageLocation** property you won't be able to assign that user an Office 365 license. Instead, you'll get an error message similar to this:</span></span>
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
<span data-ttu-id="d57cb-p124">在有點圓環易這個錯誤訊息告訴我們的上述的使用者尚未指派**UsageLocation**。當您可能會有猜測、 **UsageLocation**屬性 （這表示地區或國家的使用者通常使用 Office 365） 就變得極為重要。為何？那是因為可用使用者服務取決於您附加元件購買，但也在使用者所在的授權套件不只： 由於本機規則及規定，而某些服務可能會無法使用某些使用者。如果使用者沒有**UsageLocation**，Office 365 就沒有辦法知道哪些服務法律上幫助會公開給該使用者。因此，Office 365 不能提供給任何服務該使用者至少不之前已指定**UsageLocation** 。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p124">In somewhat-roundabout fashion, this error message tells us that the user in question has not been assigned a **UsageLocation**. As you might have guessed, the **UsageLocation** property (which indicates the region or country where the user typically uses Office 365) is extremely important. Why? That's because the services available to a user depend not only on the licensing pack that you purchased but also on where the user lives: due to local rules and regulations, some services might not be available to some users. If a user doesn't have a **UsageLocation**, Office 365 has no way of knowing which services can legally be exposed to that user. Therefore, Office 365 can't offer any services to that user, at least not until the **UsageLocation** has been specified.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d57cb-p125">當您設定的使用者帳戶時就會知道立即是否有任何全球的指定部分相關聯的授權限制。例如，如果您變更已獲授權使用者**UsageLocation**伊朗 ( `IR`)，此命令將會失敗與此錯誤訊息： `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> 那是因為 Office 365 不是目前可供伊朗的使用者使用。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。順便一提，Office 365 使用國際組織所產生的 (ISO) 雙字母國家/地區碼。您可以找到這些代碼[ISO 網站](https://go.microsoft.com/fwlink/p/?LinkId=84073)上。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p125">When you configure a user account you'll know immediately if there are any license restrictions associated with the specified part of the world. For example, if you change the **UsageLocation** for a licensed user to Iran ( `IR`), the command will fail with this error message: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> That's because Office 365 is not currently available to users in Iran. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730). Incidentally, Office 365 uses the two-letter country codes produced by the International Organization for Standardization (ISO). You can find those codes on the [ISO web site](https://go.microsoft.com/fwlink/p/?LinkId=84073).</span></span> 
  
<span data-ttu-id="d57cb-214">如果您想要確認指定的使用者有**UsageLocation** ，您可以使用類似的命令：</span><span class="sxs-lookup"><span data-stu-id="d57cb-214">If you want to verify that a given user has a **UsageLocation** you can use a command similar to this one:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

<span data-ttu-id="d57cb-215">或者，您可以傳回所有使用此命令沒有**UsageLocation**的使用者的清單：</span><span class="sxs-lookup"><span data-stu-id="d57cb-215">Alternatively, you can return a list of all the users who don't have a **UsageLocation** by using this command:</span></span>
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> <span data-ttu-id="d57cb-p126">當您將授權指派給使用者的使用者將，根據預設，授與存取權給您的組織具有存取權的所有 Office 365 服務。例如若您的 Office 365 企業版 E3 購買授權，您新授權的使用者會自動授與類似 Exchange Online、 Skype 服務存取權商務 Online 和 SharePoint Online。如果您想要限制使用者的存取這些服務 (例如，您可能會想但*不是*to SharePoint Online 的存取權的使用者至 Exchange Online 和 Skype 的商務 Online) 然後請參閱下列文章[停用服務存取權與 Office 365PowerShell](disable-access-to-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="d57cb-p126">When you assign a license to a user that user will, by default, be given access to all the Office 365 services that your organization has access to. For example, if you purchased licenses for Office 365 Enterprise E3, your newly-licensed user will automatically be granted access to services like Exchange Online, Skype for Business Online, and SharePoint Online. If you would prefer to limit a user's access to those services (for example, you might want a user to have access to SharePoint Online but  *not*  to Exchange Online and Skype for Business Online) then see the article [Disable access to services with Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md).</span></span> 
  
## <a name="new-to-office-365"></a><span data-ttu-id="d57cb-219">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="d57cb-219">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="d57cb-220">請參閱</span><span class="sxs-lookup"><span data-stu-id="d57cb-220">See Also</span></span>
<span data-ttu-id="d57cb-221"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="d57cb-221"></span></span>

<span data-ttu-id="d57cb-222">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="d57cb-222">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="d57cb-223">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d57cb-223">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d57cb-224">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d57cb-224">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d57cb-225">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d57cb-225">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d57cb-226">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="d57cb-226">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="d57cb-227">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d57cb-227">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="d57cb-228">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="d57cb-228">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="d57cb-229">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="d57cb-229">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="d57cb-230">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="d57cb-230">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="d57cb-231">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d57cb-231">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="d57cb-232">選取物件</span><span class="sxs-lookup"><span data-stu-id="d57cb-232">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="d57cb-233">Where-Object</span><span class="sxs-lookup"><span data-stu-id="d57cb-233">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

