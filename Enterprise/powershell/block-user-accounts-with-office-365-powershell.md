---
title: 使用 Office 365 PowerShell 封鎖使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 說明如何使用 Office 365 PowerShell 來封鎖及解除封鎖對 Office 365 帳戶的存取。
ms.openlocfilehash: 09cfdaf1485837713d03949cca456b9d07b66b00
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257664"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="00da7-103">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="00da7-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="00da7-104">**摘要：** 說明如何使用 Office 365 PowerShell 來封鎖及解除封鎖對 Office 365 帳戶的存取。</span><span class="sxs-lookup"><span data-stu-id="00da7-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="00da7-105">封鎖 Office 365 帳戶的存取權防止其他人使用的帳戶登入並存取服務，以及 Office 365 組織中的資料。</span><span class="sxs-lookup"><span data-stu-id="00da7-105">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="00da7-106">您可以使用 Office 365 PowerShell 來封鎖存取個別和多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="00da7-106">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="00da7-107">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="00da7-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="00da7-108">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="00da7-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="00da7-109">封鎖對個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="00da7-109">Block access to individual user accounts</span></span>

<span data-ttu-id="00da7-110">使用下列語法來封鎖個別使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="00da7-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="00da7-111">Set-azuread cmdlet 中的-ObjectID 參數接受帳戶登入名稱，也稱為使用者主體名稱或帳戶的物件 id。</span><span class="sxs-lookup"><span data-stu-id="00da7-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="00da7-112">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="00da7-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="00da7-113">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="00da7-114">若要顯示 UPN 根據使用者的顯示名稱的使用者帳戶，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="00da7-115">本範例會顯示名為 Caleb Sills 的使用者的使用者帳戶 UPN。</span><span class="sxs-lookup"><span data-stu-id="00da7-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="00da7-116">若要封鎖使用者的顯示名稱為基礎的帳戶，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="00da7-117">任何時候，您可以檢查封鎖的狀態的使用者帳戶使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="00da7-118">封鎖對多個使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="00da7-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="00da7-119">若要封鎖對多個使用者帳戶的存取，請建立文字檔，其中包含一個帳戶登入名稱每一行上都像這樣：</span><span class="sxs-lookup"><span data-stu-id="00da7-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="00da7-120">在下列命令，範例會將文字檔為 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="00da7-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="00da7-121">取代的文字檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="00da7-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="00da7-122">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="00da7-123">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="00da7-124">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="00da7-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="00da7-125">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="00da7-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="00da7-126">封鎖對個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="00da7-126">Block access to individual user accounts</span></span>

<span data-ttu-id="00da7-127">使用下列語法來封鎖對個別使用者帳戶的存取：</span><span class="sxs-lookup"><span data-stu-id="00da7-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="00da7-128">PowerShell 核心不支援的 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組和具有**Msol** cmdlet 在其名稱。</span><span class="sxs-lookup"><span data-stu-id="00da7-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="00da7-129">若要繼續使用這些 cmdlet，您必須從 Windows PowerShell 執行它們。</span><span class="sxs-lookup"><span data-stu-id="00da7-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="00da7-130">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="00da7-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="00da7-131">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="00da7-132">任何時候，您可以檢查封鎖的狀態的使用者帳戶使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="00da7-133">封鎖對多個使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="00da7-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="00da7-134">首先，建立文字檔，其中包含一個帳戶每一行上都像這樣：</span><span class="sxs-lookup"><span data-stu-id="00da7-134">First, create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="00da7-135">在下列命令，範例會將文字檔為 C:\My Documents\Accounts.txt。</span><span class="sxs-lookup"><span data-stu-id="00da7-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="00da7-136">取代的文字檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="00da7-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="00da7-137">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="00da7-138">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="00da7-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="00da7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00da7-139">See also</span></span>

[<span data-ttu-id="00da7-140">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="00da7-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="00da7-141">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="00da7-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="00da7-142">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="00da7-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
