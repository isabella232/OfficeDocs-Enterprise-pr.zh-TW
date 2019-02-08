---
title: 使用 Office 365 PowerShell 停用服務存取權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/11/2018
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
description: 說明如何使用 Office 365 PowerShell 來停用組織中使用者的 Office 365 服務存取權。
ms.openlocfilehash: 66f6c04c1488f14d5752974a5475e7ef11279406
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897416"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="caf37-103">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="caf37-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="caf37-104">**摘要：** 說明如何使用 Office 365 PowerShell 來停用組織中使用者的 Office 365 服務存取權。</span><span class="sxs-lookup"><span data-stu-id="caf37-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="caf37-p101">當 Office 365 帳戶已指派授權的授權方案時、 Office 365 服務是供使用者從該授權。不過，您可以控制使用者可以存取 Office 365 服務。例如，即使授權可讓 SharePoint Online 服務的權限，您可以停用來加以存取。您可以使用 Office 365 PowerShell 停用的存取權的服務之特定的授權方案的任何數字：</span><span class="sxs-lookup"><span data-stu-id="caf37-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to the SharePoint Online service, you can disable access to it. You can use Office 365 PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="caf37-109">個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="caf37-109">An individual account.</span></span>
    
- <span data-ttu-id="caf37-110">一組帳戶。</span><span class="sxs-lookup"><span data-stu-id="caf37-110">A group of accounts.</span></span>
    
- <span data-ttu-id="caf37-111">您組織中的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="caf37-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="caf37-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="caf37-112">Before you begin</span></span>
<span data-ttu-id="caf37-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="caf37-113"></span></span>

- <span data-ttu-id="caf37-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="caf37-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="caf37-p103">您可以使用**Get-msolaccountsku**指令程式來檢視您可用的授權方案，以及這些計劃中可用的 Office 365 服務。如需詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="caf37-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="caf37-118">若要查看前後本主題中的程序的結果，請參閱[檢視帳戶授權及服務的詳細資訊與 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="caf37-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="caf37-p104">PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="caf37-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="caf37-122">如果您使用**Get-msoluser** cmdlet 而不需使用的_所有_參數時，會傳回第一個 500 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="caf37-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="caf37-123">停用特定的授權方案之特定使用者的特定 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="caf37-123">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="caf37-124">若要停用一組特定的 Office 365 服務之使用者的特定的授權方案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="caf37-124">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="caf37-125">識別授權的計劃中的非預期的服務使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="caf37-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="caf37-126">下列範例會建立名為授權計劃中停用的 Office Online 和 SharePoint Online 服務**LicenseOptions**物件`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3)。</span><span class="sxs-lookup"><span data-stu-id="caf37-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="caf37-127">對一或多位使用者使用步驟 1 的 **LicenseOptions** 物件。</span><span class="sxs-lookup"><span data-stu-id="caf37-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="caf37-128">若要建立已停用服務的新帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="caf37-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="caf37-129">下列範例會建立新帳戶的 Allie Bellew 指派授權並停用 [步驟 1 中所述的服務。</span><span class="sxs-lookup"><span data-stu-id="caf37-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="caf37-130">如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="caf37-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="caf37-131">若要停用現有授權使用者的服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="caf37-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="caf37-132">本範例會停用使用者 BelindaN@litwareinc.com 的服務。</span><span class="sxs-lookup"><span data-stu-id="caf37-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="caf37-133">若要停用的所有現有的授權使用者在步驟 1 中所述的服務，指定您的 Office 365 計劃中的**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack**)，顯示名稱，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="caf37-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="caf37-134">若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：</span><span class="sxs-lookup"><span data-stu-id="caf37-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="caf37-135">**篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="caf37-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="caf37-136">下列範例會停用使用者在美國銷售部門中的服務。</span><span class="sxs-lookup"><span data-stu-id="caf37-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="caf37-137">**使用特定帳戶的清單**若要這樣做，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="caf37-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="caf37-138">建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="caf37-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="caf37-139">在此範例中的文字檔案是 c:\\我的文件\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="caf37-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="caf37-140">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="caf37-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="caf37-141">如果您要停用的多個授權方案的服務存取權，重複上述的指示確保每種授權計劃：</span><span class="sxs-lookup"><span data-stu-id="caf37-141">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="caf37-142">使用者帳戶已指派授權方案。</span><span class="sxs-lookup"><span data-stu-id="caf37-142">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="caf37-143">若要停用服務都可以在授權方案。</span><span class="sxs-lookup"><span data-stu-id="caf37-143">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="caf37-144">當您要指派它們至授權計劃停用 Office 365 服務的使用者，請參閱 ＜[停用時指派使用者授權的服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="caf37-144">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="caf37-145">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="caf37-145">New to Office 365?</span></span>
<span data-ttu-id="caf37-146"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="caf37-146"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="caf37-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caf37-147">See also</span></span>
<span data-ttu-id="caf37-148"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="caf37-148"></span></span>

<span data-ttu-id="caf37-149">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="caf37-149">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="caf37-150">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="caf37-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="caf37-151">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="caf37-151">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="caf37-152">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="caf37-152">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="caf37-153">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="caf37-153">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="caf37-154">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="caf37-154">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="caf37-155">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="caf37-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="caf37-156">Get-content</span><span class="sxs-lookup"><span data-stu-id="caf37-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="caf37-157">Get-msolaccountsku</span><span class="sxs-lookup"><span data-stu-id="caf37-157">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="caf37-158">新 MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="caf37-158">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="caf37-159">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="caf37-159">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="caf37-160">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="caf37-160">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="caf37-161">Set-msoluserlicense</span><span class="sxs-lookup"><span data-stu-id="caf37-161">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="caf37-162">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="caf37-162">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="caf37-163">Where-Object</span><span class="sxs-lookup"><span data-stu-id="caf37-163">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

