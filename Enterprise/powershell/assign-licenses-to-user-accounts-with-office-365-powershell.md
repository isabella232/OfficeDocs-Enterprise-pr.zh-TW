---
title: 使用 Office 365 PowerShell 指派授權至使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
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
description: 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123290"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="f3529-103">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f3529-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="f3529-104">**摘要：** 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。</span><span class="sxs-lookup"><span data-stu-id="f3529-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="f3529-p101">授權 Office 365 中的使用者帳戶很重要，因為使用者無法使用任何 Office 365 服務之前已授權其帳戶。您可以使用 Office 365 PowerShell 有效率地將授權指派給未授權的帳戶，特別是多個帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3529-p101">Licensing user accounts in Office 365 is important, because users can't use any Office 365 services until their account has been licensed. You can use Office 365 PowerShell to efficiently assign licenses to unlicensed accounts, especially multiple accounts.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="f3529-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="f3529-107">Before you begin</span></span>
<span data-ttu-id="f3529-108"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="f3529-108"></span></span>

- <span data-ttu-id="f3529-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f3529-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f3529-p103">使用**Get-msolaccountsku**指令程式來檢視您組織中每個計劃中可用的授權方案和可用授權數量。每個計劃中的可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。如需授權方案、 授權及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f3529-p103">Use the **Get-MsolAccountSku** cmdlet to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f3529-114">若要在組織中尋找未授權的帳戶，請執行命令`Get-MsolUser -All -UnlicensedUsersOnly`</span><span class="sxs-lookup"><span data-stu-id="f3529-114">To find the unlicensed accounts in your organization, run the command  `Get-MsolUser -All -UnlicensedUsersOnly`</span></span>
    
- <span data-ttu-id="f3529-p104">您只能指派授權給**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2 國家/地區碼的使用者帳戶。例如，我們美國、 和法國的 FR。某些 Office 365 服務都無法提供在某些國家/地區。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="f3529-p104">You can assign licenses only to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
    <span data-ttu-id="f3529-p105">若要尋找沒有**UsageLocation**值的帳戶，請執行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若帳戶上設定**UsageLocation**值，使用語法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。</span><span class="sxs-lookup"><span data-stu-id="f3529-p105">To find accounts that don't have a **UsageLocation** value, run the command `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. To set the **UsageLocation** value on an account, use the syntax `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. For example,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.</span></span>
    
- <span data-ttu-id="f3529-122">如果您使用**Get-msoluser** cmdlet 而不需使用`-All`參數，傳回前 500 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3529-122">If you use the **Get-MsolUser** cmdlet without using the `-All` parameter, only the first 500 accounts are returned.</span></span>

## <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="f3529-123">將授權指派給使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f3529-123">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="f3529-124">若要將授權指派給使用者，請在 Office 365 PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="f3529-124">To assign a license to a user, use the following syntax in Office 365 PowerShell:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="f3529-125">此範例會將指定的授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 給未授權使用者的授權方案`belindan@litwareinc.com`。</span><span class="sxs-lookup"><span data-stu-id="f3529-125">This example assigns a license from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to the unlicensed user `belindan@litwareinc.com`.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="f3529-126">若要將授權指派給多位未經授權的使用者，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="f3529-126">To assign a license to many unlicensed users, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 <span data-ttu-id="f3529-127">**附註**</span><span class="sxs-lookup"><span data-stu-id="f3529-127">**Notes**</span></span>
  
- <span data-ttu-id="f3529-128">您無法將多個授權指派給相同授權計劃中的使用者。</span><span class="sxs-lookup"><span data-stu-id="f3529-128">You can't assign multiple licenses to a user from the same licensing plan.</span></span>
    
- <span data-ttu-id="f3529-129">如果您沒有足夠的可用授權，則會依 **Get-MsolUser** Cmdlet 傳回授權的順序，將授權指派給使用者，直到可用的授權用完為止。</span><span class="sxs-lookup"><span data-stu-id="f3529-129">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
    
<span data-ttu-id="f3529-130">本範例會將指派授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 所有未授權使用者的授權方案。</span><span class="sxs-lookup"><span data-stu-id="f3529-130">This example assigns licenses from the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan to all unlicensed users.</span></span>
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="f3529-131">本範例會將相同的授權指派給美國境內銷售部門中未經授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="f3529-131">This example assigns those same licenses to unlicensed users in the Sales department in the United States.</span></span>
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="f3529-132">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="f3529-132">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="f3529-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3529-133">See also</span></span>
<span data-ttu-id="f3529-134"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="f3529-134"></span></span>

<span data-ttu-id="f3529-135">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="f3529-135">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="f3529-136">建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f3529-136">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f3529-137">刪除並還原的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f3529-137">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f3529-138">封鎖的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f3529-138">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f3529-139">移除使用者帳戶的授權</span><span class="sxs-lookup"><span data-stu-id="f3529-139">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="f3529-140">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="f3529-140">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="f3529-141">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="f3529-141">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="f3529-142">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="f3529-142">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="f3529-143">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="f3529-143">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="f3529-144">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="f3529-144">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="f3529-145">選取物件</span><span class="sxs-lookup"><span data-stu-id="f3529-145">Select-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [<span data-ttu-id="f3529-146">Where-Object</span><span class="sxs-lookup"><span data-stu-id="f3529-146">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

