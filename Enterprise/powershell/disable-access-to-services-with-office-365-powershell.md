---
title: "使用 Office 365 PowerShell 停用服務存取權"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "說明如何使用 Office 365 PowerShell 來停用組織中使用者的 Office 365 服務存取權。"
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="a2345-103">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="a2345-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="a2345-104">**摘要：**說明如何使用 Office 365 PowerShell 來停用組織中使用者的 Office 365 服務存取權。</span><span class="sxs-lookup"><span data-stu-id="a2345-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="a2345-p101">當 Office 365 帳戶已指派授權的授權方案時、 Office 365 服務是供使用者從該授權。不過，您可以控制使用者可以存取 Office 365 服務。例如，即使授權允許存取 SharePoint Online，您可以停用其存取權。事實上，您可以使用 Office 365 PowerShell 停用的存取權的服務之任何數字：</span><span class="sxs-lookup"><span data-stu-id="a2345-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="a2345-109">個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="a2345-109">An individual account.</span></span>
    
- <span data-ttu-id="a2345-110">一組帳戶。</span><span class="sxs-lookup"><span data-stu-id="a2345-110">A group of accounts.</span></span>
    
- <span data-ttu-id="a2345-111">您組織中的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="a2345-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="a2345-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="a2345-112">Before you begin</span></span>
<span data-ttu-id="a2345-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="a2345-113"></span></span>

- <span data-ttu-id="a2345-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a2345-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a2345-p103">您可以使用**Get-msolaccountsku**指令程式來檢視您可用的授權方案，以及這些計劃中可用的 Office 365 服務。如需詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a2345-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a2345-118">若要查看前後本主題中的程序的結果，請參閱[檢視帳戶授權及服務的詳細資訊與 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a2345-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a2345-p104">PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a2345-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a2345-122">如果您使用**Get-msoluser** cmdlet 而不需使用的_所有_參數時，會傳回第一個 500 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a2345-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="a2345-123">單一授權的特定使用者的特定 Office 365 服務計劃</span><span class="sxs-lookup"><span data-stu-id="a2345-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="a2345-124">若要停用一組特定的 Office 365 服務讓使用者從單一的授權方案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a2345-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="a2345-125">識別授權的計劃中的非預期的服務使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a2345-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="a2345-126">下列範例會建立名為授權計劃中停用的 Office Online 和 SharePoint Online 服務**LicenseOptions**物件`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3)。</span><span class="sxs-lookup"><span data-stu-id="a2345-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="a2345-127">使用步驟 1 中的**LicenseOptions**物件上一或多個使用者。</span><span class="sxs-lookup"><span data-stu-id="a2345-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="a2345-128">若要建立已停用服務的新帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a2345-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="a2345-129">下列範例會建立新帳戶的 Allie Bellew 指派授權並停用 [步驟 1 中所述的服務。</span><span class="sxs-lookup"><span data-stu-id="a2345-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="a2345-130">如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a2345-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="a2345-131">若要停用現有授權使用者的服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a2345-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="a2345-132">本範例會停用使用者 BelindaN@litwareinc.com 的服務。</span><span class="sxs-lookup"><span data-stu-id="a2345-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="a2345-133">若要停用的所有現有的授權使用者在步驟 1 中所述的服務，指定您的 Office 365 計劃中的**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack**)，顯示名稱，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a2345-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="a2345-134">若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：</span><span class="sxs-lookup"><span data-stu-id="a2345-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="a2345-135">**篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a2345-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="a2345-136">下列範例會停用使用者在美國銷售部門中的服務。</span><span class="sxs-lookup"><span data-stu-id="a2345-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="a2345-137">**使用特定帳戶的清單**若要這樣做，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a2345-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="a2345-138">建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2345-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="a2345-139">在此範例中的文字檔案是 c:\\我的文件\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="a2345-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="a2345-140">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a2345-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="a2345-141">當您要指派它們至授權計劃停用 Office 365 服務的使用者，請參閱 ＜[停用時指派使用者授權的服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="a2345-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="a2345-142">讓使用者從所有授權的計劃的特定 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="a2345-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="a2345-143">若要停用使用者的 Office 365 服務中所有可用的授權方案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a2345-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="a2345-144">複製此指令碼，並將其貼入 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="a2345-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="a2345-145">為您的環境自訂下列值：</span><span class="sxs-lookup"><span data-stu-id="a2345-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="a2345-146">_<UndesirableService>_在這個範例中，我們將使用 Office Online 和 SharePoint Online。</span><span class="sxs-lookup"><span data-stu-id="a2345-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="a2345-147">_<Account>_在這個範例中，我們將使用 belindan@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="a2345-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="a2345-148">自訂的指令碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2345-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="a2345-p105">儲存為指令碼`RemoveO365Services.ps1`中更容易尋找的位置。此範例中，我們將儲存在檔案`C:\\O365 Scripts`。</span><span class="sxs-lookup"><span data-stu-id="a2345-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="a2345-151">使用下列命令在 Office 365 PowerShell 中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="a2345-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="a2345-152">若要反向的任何這些程序 (亦即重新啟用已停用的服務)、 重新執行此程序，但使用值`$null` _DisabledPlans_參數。</span><span class="sxs-lookup"><span data-stu-id="a2345-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="a2345-153">返回頁首</span><span class="sxs-lookup"><span data-stu-id="a2345-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="a2345-154">單一授權的所有使用者的所有 Office 365 服務計都劃</span><span class="sxs-lookup"><span data-stu-id="a2345-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="a2345-155">若要停用所有 Office 365 服務的所有使用者在特定的授權方案中，指定授權計劃的名稱 （例如**litwareinc: enterprisepack**)、 $acctSKU，然後 PowerShell 命令視窗中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a2345-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="a2345-156">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="a2345-156">New to Office 365?</span></span>
<span data-ttu-id="a2345-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="a2345-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="a2345-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2345-158">See also</span></span>
<span data-ttu-id="a2345-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="a2345-159"></span></span>

<span data-ttu-id="a2345-160">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="a2345-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="a2345-161">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a2345-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a2345-162">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a2345-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a2345-163">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a2345-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a2345-164">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a2345-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a2345-165">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a2345-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="a2345-166">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a2345-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a2345-167">Get-content</span><span class="sxs-lookup"><span data-stu-id="a2345-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="a2345-168">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="a2345-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="a2345-169">新 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="a2345-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="a2345-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a2345-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="a2345-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a2345-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="a2345-172">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="a2345-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="a2345-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="a2345-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="a2345-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a2345-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

