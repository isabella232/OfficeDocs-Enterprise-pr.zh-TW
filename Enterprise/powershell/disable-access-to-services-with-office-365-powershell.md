---
title: 使用 Office 365 PowerShell 停用服務存取權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: 使用 Office 365 PowerShell 來停用使用者的 Office 365 服務存取權。
ms.openlocfilehash: e0a486bbe3a783443fc25cbadff61721761a0028
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004646"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="3886a-103">使用 Office 365 PowerShell 停用服務存取權</span><span class="sxs-lookup"><span data-stu-id="3886a-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="3886a-104">當 Office 365 帳戶指派授權方案的授權時，使用者就可以從該授權取得 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="3886a-105">不過，您可以控制使用者可以存取的 Office 365 服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="3886a-106">例如，即使授權允許存取 SharePoint 線上服務，您還是可以停用存取權。</span><span class="sxs-lookup"><span data-stu-id="3886a-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="3886a-107">您可以使用 PowerShell 針對特定授權方案停用任何數目的服務存取權：</span><span class="sxs-lookup"><span data-stu-id="3886a-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="3886a-108">個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="3886a-108">An individual account.</span></span>
- <span data-ttu-id="3886a-109">一組帳戶。</span><span class="sxs-lookup"><span data-stu-id="3886a-109">A group of accounts.</span></span>
- <span data-ttu-id="3886a-110">您組織中的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="3886a-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="3886a-111">有 Office 365 服務相依性，可防止當其他服務依賴于指定的服務時停用此服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="3886a-112">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="3886a-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="3886a-113">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="3886a-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="3886a-114">接下來，使用此命令來查看可用的授權方案，也稱為 AccountSkuIds：</span><span class="sxs-lookup"><span data-stu-id="3886a-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="3886a-115">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3886a-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="3886a-116">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="3886a-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="3886a-117">如需詳細資訊，請參閱[使用 Office 365 PowerShell 查看授權和服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="3886a-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="3886a-118">若要查看本主題中的程式前後的結果，請參閱[使用 Office 365 PowerShell 查看帳戶授權與服務詳細資料](view-account-license-and-service-details-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="3886a-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="3886a-119">PowerShell 指令碼可供使用，會自動執行本主題中所述的程序。</span><span class="sxs-lookup"><span data-stu-id="3886a-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="3886a-120">具體說來，此腳本可讓您在 Office 365 組織中查看及停用服務，包括 Sway。</span><span class="sxs-lookup"><span data-stu-id="3886a-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="3886a-121">如需詳細資訊，請參閱[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="3886a-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="3886a-122">針對特定授權方案停用特定使用者的特定 Office 365 服務</span><span class="sxs-lookup"><span data-stu-id="3886a-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="3886a-123">若要針對特定授權方案停用一組特定的 Office 365 服務，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3886a-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="3886a-124">步驟1：使用下列語法識別授權方案中不想要的服務：</span><span class="sxs-lookup"><span data-stu-id="3886a-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="3886a-125">下列範例會建立**LicenseOptions**物件，以停用名為`litwareinc:ENTERPRISEPACK` （Office 365 Enterprise E3）的授權方案中的 Office 和 SharePoint 線上服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="3886a-126">步驟2：在一或多個使用者上使用步驟1中的**LicenseOptions**物件。</span><span class="sxs-lookup"><span data-stu-id="3886a-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="3886a-127">若要建立已停用服務的新帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="3886a-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="3886a-128">下列範例會為 Allie Bellew 建立新的帳戶，以指派授權並停用步驟1中所述的服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="3886a-129">如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱[Create user accounts With office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="3886a-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="3886a-130">若要停用現有授權使用者的服務，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="3886a-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="3886a-131">本範例會停用使用者 BelindaN@litwareinc.com 的服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="3886a-132">若要停用步驟1中所述的所有現有授權使用者的服務，請從**Get-MsolAccountSku** Cmdlet 的顯示（例如**litwareinc:ENTERPRISEPACK**）中指定您的 Office 365 方案名稱，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3886a-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="3886a-133">如果您使用**Get-MsolUser** Cmdlet 但未使用_All_參數，則只會傳回第一個500使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3886a-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="3886a-134">若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：</span><span class="sxs-lookup"><span data-stu-id="3886a-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="3886a-135">**方法1。根據現有的帳戶屬性來篩選帳戶**</span><span class="sxs-lookup"><span data-stu-id="3886a-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="3886a-136">若要這麼做，使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="3886a-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="3886a-137">下列範例會停用美國地區的銷售部門中的使用者服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="3886a-138">**方法2：使用特定帳戶的清單**</span><span class="sxs-lookup"><span data-stu-id="3886a-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="3886a-139">若要這樣做，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3886a-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="3886a-140">建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3886a-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="3886a-141">在此範例中，文字檔是 C：\\My Documents\\，.txt。</span><span class="sxs-lookup"><span data-stu-id="3886a-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="3886a-142">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3886a-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="3886a-143">如果您想要針對多個授權方案停用服務存取權，請針對每個授權方案重複上述指示，以確保：</span><span class="sxs-lookup"><span data-stu-id="3886a-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="3886a-144">已指派授權方案的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3886a-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="3886a-145">授權方案提供要停用的服務。</span><span class="sxs-lookup"><span data-stu-id="3886a-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="3886a-146">若要在指派使用者授權時，為使用者停用 Office 365 服務，請參閱在[指派使用者授權時停用服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。</span><span class="sxs-lookup"><span data-stu-id="3886a-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="3886a-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3886a-147">See also</span></span>

[<span data-ttu-id="3886a-148">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3886a-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3886a-149">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="3886a-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3886a-150">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3886a-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
