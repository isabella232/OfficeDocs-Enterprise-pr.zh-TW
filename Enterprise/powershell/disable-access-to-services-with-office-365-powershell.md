---
title: 使用 Office 365 PowerShell 停用服務存取權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
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
description: 使用 Office 365 PowerShell 停用使用者的 Office 365 服務存取權。
ms.openlocfilehash: 0f2c603edd624c9d53a28b37c1c9795bad05ec0f
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001816"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="2e159-103">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="2e159-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="2e159-104">**摘要：** 說明如何使用 Office 365 PowerShell 停用您組織中的使用者的 Office 365 服務存取權。</span><span class="sxs-lookup"><span data-stu-id="2e159-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="2e159-105">Office 365 帳戶授權計劃指派授權，Office 365 服務都可供使用者從該授權。</span><span class="sxs-lookup"><span data-stu-id="2e159-105">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="2e159-106">不過，您可以控制使用者可以存取 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="2e159-106">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="2e159-107">例如，即使授權允許存取 SharePoint Online 服務，您可以停用對它的存取。</span><span class="sxs-lookup"><span data-stu-id="2e159-107">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="2e159-108">您可以使用 PowerShell 來停用的存取權的服務特定的授權計劃的任何數字：</span><span class="sxs-lookup"><span data-stu-id="2e159-108">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="2e159-109">個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="2e159-109">An individual account.</span></span>
    
- <span data-ttu-id="2e159-110">一組帳戶。</span><span class="sxs-lookup"><span data-stu-id="2e159-110">A group of accounts.</span></span>
    
- <span data-ttu-id="2e159-111">您組織中的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="2e159-111">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2e159-112">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="2e159-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2e159-113">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="2e159-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="2e159-114">若要檢視可用授權計劃，也稱為 AccountSkuIds，接下來，使用此命令：</span><span class="sxs-lookup"><span data-stu-id="2e159-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

<span data-ttu-id="2e159-115">如需詳細資訊，請參閱[檢視授權與服務的 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="2e159-115">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="2e159-116">若要查看前後本主題中的程序的結果，請參閱 <<c0>檢視帳戶授權與服務詳細資料與 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2e159-116">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="2e159-117">PowerShell 指令碼可供使用，會自動執行本主題中所述的程序。</span><span class="sxs-lookup"><span data-stu-id="2e159-117">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="2e159-118">具體而言，指令碼可讓您檢視及停用您 Office 365 組織，包括 Sway 中的服務。</span><span class="sxs-lookup"><span data-stu-id="2e159-118">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="2e159-119">如需詳細資訊，請參閱[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="2e159-119">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="2e159-120">停用特定的 Office 365 服務，針對特定使用者的特定的授權計劃</span><span class="sxs-lookup"><span data-stu-id="2e159-120">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="2e159-121">若要停用一組特定的使用者特定授權方案的 Office 365 服務，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2e159-121">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="2e159-122">使用下列語法，不需要的服務識別授權計劃中：</span><span class="sxs-lookup"><span data-stu-id="2e159-122">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="2e159-123">下列範例會建立**LicenseOptions**物件，以停用的 Office Online 和 SharePoint Online 服務中名為授權計劃`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3)。</span><span class="sxs-lookup"><span data-stu-id="2e159-123">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="2e159-124">對一或多位使用者使用步驟 1 的 **LicenseOptions** 物件。</span><span class="sxs-lookup"><span data-stu-id="2e159-124">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="2e159-125">若要建立已停用服務的新帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="2e159-125">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="2e159-126">下列範例的指派授權及停用步驟 1 所述服務的 Allie Bellew 建立新的帳戶。</span><span class="sxs-lookup"><span data-stu-id="2e159-126">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="2e159-127">如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱 <<c0>使用 Office 365 PowerShell 建立使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2e159-127">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="2e159-128">若要停用現有授權使用者的服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="2e159-128">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="2e159-129">本範例會停用使用者 BelindaN@litwareinc.com 的服務。</span><span class="sxs-lookup"><span data-stu-id="2e159-129">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="2e159-130">若要停用所有現有經授權使用者在步驟 1 中所述的服務，指定從**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack**)，顯示 Office 365 計劃的名稱，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2e159-130">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="2e159-131">如果您使用**Get-msoluser** cmdlet，而不使用_All_參數，會傳回的第一個 500 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2e159-131">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="2e159-132">若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：</span><span class="sxs-lookup"><span data-stu-id="2e159-132">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="2e159-133">**篩選根據現有的帳戶屬性的帳戶**若要這麼做，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="2e159-133">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="2e159-134">下列範例會停用在美國境內銷售部門中的使用者的服務。</span><span class="sxs-lookup"><span data-stu-id="2e159-134">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="2e159-135">**使用特定帳戶清單**若要這麼做，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2e159-135">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="2e159-136">建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e159-136">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="2e159-137">在這個範例中，文字檔為 c:\\我的文件\\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="2e159-137">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="2e159-138">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2e159-138">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="2e159-139">如果您想要停用的多個授權計劃的服務存取權，重複上述指示每個授權計劃，確保：</span><span class="sxs-lookup"><span data-stu-id="2e159-139">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="2e159-140">使用者帳戶已指派授權計劃。</span><span class="sxs-lookup"><span data-stu-id="2e159-140">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="2e159-141">若要停用服務可用授權計劃中。</span><span class="sxs-lookup"><span data-stu-id="2e159-141">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="2e159-142">若您將它們指派給授權計劃停用使用者的 Office 365 服務，請參閱[停用時指派使用者授權的服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="2e159-142">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="2e159-143">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="2e159-143">New to Office 365?</span></span>
<span data-ttu-id="2e159-144"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="2e159-144"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="2e159-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e159-145">See also</span></span>
<span data-ttu-id="2e159-146"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="2e159-146"></span></span>

<span data-ttu-id="2e159-147">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="2e159-147">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="2e159-148">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="2e159-148">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="2e159-149">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="2e159-149">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="2e159-150">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="2e159-150">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="2e159-151">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="2e159-151">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="2e159-152">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="2e159-152">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
