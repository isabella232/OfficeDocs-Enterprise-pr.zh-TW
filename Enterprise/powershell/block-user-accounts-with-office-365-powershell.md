---
title: 使用 Office 365 PowerShell 封鎖使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
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
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 說明如何使用 Office 365 PowerShell 來封鎖和取消封鎖 Office 365 帳戶的存取。
ms.openlocfilehash: 5633c35feee67ede65c4fffa8bc55276c3b979b8
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004726"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="c10c0-103">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="c10c0-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="c10c0-104">封鎖 Office 365 帳戶的存取權，可防止任何人使用該帳戶登入，並存取您 Office 365 組織中的服務和資料。</span><span class="sxs-lookup"><span data-stu-id="c10c0-104">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="c10c0-105">您可以使用 Office 365 PowerShell 來封鎖個別和多個使用者帳戶的存取。</span><span class="sxs-lookup"><span data-stu-id="c10c0-105">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c10c0-106">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="c10c0-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c10c0-107">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="c10c0-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="c10c0-108">封鎖個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="c10c0-108">Block access to individual user accounts</span></span>

<span data-ttu-id="c10c0-109">使用下列語法來封鎖個別使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="c10c0-109">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="c10c0-110">Set-AzureAD 指令程式中的-ObjectID 參數會接受帳戶登入名稱，也稱為使用者主要名稱，或者是帳戶的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="c10c0-110">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="c10c0-111">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="c10c0-111">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="c10c0-112">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-112">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="c10c0-113">若要根據使用者的顯示名稱來顯示使用者帳戶 UPN，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-113">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="c10c0-114">此範例會顯示名為 Caleb Sills 帳戶之使用者的使用者帳戶 UPN。</span><span class="sxs-lookup"><span data-stu-id="c10c0-114">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c10c0-115">若要根據使用者的顯示名稱封鎖帳戶，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-115">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="c10c0-116">您可以隨時使用下列命令來檢查使用者帳戶的封鎖狀態：</span><span class="sxs-lookup"><span data-stu-id="c10c0-116">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="c10c0-117">封鎖對多個使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="c10c0-117">Block access to multiple user accounts</span></span>

<span data-ttu-id="c10c0-118">若要封鎖對多個使用者帳戶的存取，請建立一個文字檔，其中每一行上都包含一個帳戶登入名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c10c0-118">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="c10c0-119">在下列命令中，範例文字檔是 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="c10c0-119">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="c10c0-120">以您的文字檔的路徑和檔案名取代。</span><span class="sxs-lookup"><span data-stu-id="c10c0-120">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="c10c0-121">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-121">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="c10c0-122">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-122">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c10c0-123">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="c10c0-123">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c10c0-124">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c10c0-124">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="c10c0-125">封鎖個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="c10c0-125">Block access to individual user accounts</span></span>

<span data-ttu-id="c10c0-126">使用下列語法來封鎖對個別使用者帳戶的存取：</span><span class="sxs-lookup"><span data-stu-id="c10c0-126">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="c10c0-127">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c10c0-127">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c10c0-128">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="c10c0-128">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="c10c0-129">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="c10c0-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="c10c0-130">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-130">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="c10c0-131">您可以隨時使用下列命令來檢查使用者帳戶的封鎖狀態：</span><span class="sxs-lookup"><span data-stu-id="c10c0-131">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="c10c0-132">封鎖對多個使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="c10c0-132">Block access to multiple user accounts</span></span>

<span data-ttu-id="c10c0-133">首先，建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c10c0-133">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="c10c0-134">在下列命令中，範例文字檔是 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="c10c0-134">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="c10c0-135">以您的文字檔的路徑和檔案名取代。</span><span class="sxs-lookup"><span data-stu-id="c10c0-135">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="c10c0-136">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-136">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="c10c0-137">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c10c0-137">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="c10c0-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c10c0-138">See also</span></span>

[<span data-ttu-id="c10c0-139">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c10c0-139">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c10c0-140">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="c10c0-140">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c10c0-141">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c10c0-141">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
