---
title: 使用 Office 365 PowerShell 移除使用者帳戶中的授權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/23/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: 說明如何使用 Office 365 PowerShell 來移除先前指派給使用者的 Office 365 授權。
ms.openlocfilehash: bfd333b649df1d346a45abc3e8b9e35666f8f582
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747539"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="73a95-103">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="73a95-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="73a95-104">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="73a95-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="73a95-105">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="73a95-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="73a95-106">接下來，列出您的租用戶使用此命令的授權計劃。</span><span class="sxs-lookup"><span data-stu-id="73a95-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="73a95-107">接下來，取得您想移除授權，也稱為使用者主體名稱 (UPN) 的帳戶登入名稱。</span><span class="sxs-lookup"><span data-stu-id="73a95-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="73a95-108">最後，指定使用者登入和授權計劃的名稱、 移除 「 < 」 及 「 > 」 字元，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="73a95-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="73a95-109">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="73a95-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="73a95-110">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="73a95-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="73a95-111">若要檢視您組織的授權方案 (**AccountSkuID** ) 資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="73a95-111">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="73a95-112">使用 Office 365 PowerShell 檢視授權與服務</span><span class="sxs-lookup"><span data-stu-id="73a95-112">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="73a95-113">使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料</span><span class="sxs-lookup"><span data-stu-id="73a95-113">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="73a95-114">如果您使用 **Get-MsolUser** Cmdlet，而不使用 _-All_參數，則只會傳回前 500 個帳戶。</span><span class="sxs-lookup"><span data-stu-id="73a95-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="73a95-115">從使用者帳戶移除授權</span><span class="sxs-lookup"><span data-stu-id="73a95-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="73a95-116">若要從現有的使用者帳戶移除授權，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="73a95-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="73a95-117">此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權使用者帳戶 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="73a95-117">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="73a95-118">您無法使用 Set-msoluserlicense cmdlet，若要取消指派*取消*授權的使用者。</span><span class="sxs-lookup"><span data-stu-id="73a95-118">You cannot use the Set-MsolUserLicense cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="73a95-119">您必須執行這項操作個別的 Microsoft 365 系統管理中心中每個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="73a95-119">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="73a95-120">若要從現有的授權使用者的群組中移除授權，請使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="73a95-120">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="73a95-121">**篩選根據現有的帳戶屬性的帳戶**若要這麼做，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="73a95-121">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="73a95-122">此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從所有帳戶在美國境內銷售部門中的使用者。</span><span class="sxs-lookup"><span data-stu-id="73a95-122">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="73a95-123">**使用特定帳戶清單**若要這麼做，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="73a95-123">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="73a95-124">建立並儲存文字檔，其中包含一個帳戶每一行上都像這樣：</span><span class="sxs-lookup"><span data-stu-id="73a95-124">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="73a95-125">請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="73a95-125">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="73a95-126">此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從 C:\My Documents\Accounts.txt 文字檔案中所定義的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="73a95-126">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="73a95-127">若要從所有現有的使用者帳戶移除授權，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="73a95-127">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="73a95-128">此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從所有現有經授權使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="73a95-128">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="73a95-129">釋出授權的另一個方法是藉由刪除的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="73a95-129">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="73a95-130">如需詳細資訊，請參閱[刪除並還原與 Office 365 PowerShell 的使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="73a95-130">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="73a95-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73a95-131">See also</span></span>

[<span data-ttu-id="73a95-132">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="73a95-132">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="73a95-133">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="73a95-133">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="73a95-134">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="73a95-134">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="73a95-135">第一次使用 Office 365？</span><span class="sxs-lookup"><span data-stu-id="73a95-135">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

