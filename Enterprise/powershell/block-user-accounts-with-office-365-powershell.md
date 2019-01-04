---
title: 使用 Office 365 PowerShell 封鎖使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: 說明如何使用 Office 365 PowerShell 封鎖及解除封鎖存取 Office 365 帳戶。
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546474"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e352c-103">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="e352c-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e352c-104">**摘要：** 說明如何使用 Office 365 PowerShell 封鎖及解除封鎖存取 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="e352c-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="e352c-p101">封鎖 Office 365 帳戶存取權防止其他人使用帳戶來登入及存取服務和 Office 365 組織中的資料。您可以使用 Office 365 PowerShell 封鎖存取個別和多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e352c-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e352c-107">使用 Azure Active Directory PowerShell 圖模組</span><span class="sxs-lookup"><span data-stu-id="e352c-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e352c-108">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="e352c-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="e352c-109">封鎖的個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="e352c-109">Block access to individual user accounts</span></span>

<span data-ttu-id="e352c-110">若要封鎖的個別使用者帳戶使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="e352c-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="e352c-111">-ObjectID 參數中設定 AzureAD 指令程式可接受的帳戶登入名稱，也稱為使用者主體名稱或帳戶的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="e352c-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="e352c-112">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="e352c-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="e352c-113">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="e352c-114">若要顯示 UPN 根據使用者的顯示名稱的使用者帳戶，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="e352c-115">本範例會顯示名為 caleb Sills Sills 之使用者的使用者帳戶 UPN。</span><span class="sxs-lookup"><span data-stu-id="e352c-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e352c-116">若要封鎖使用者的顯示名稱為基礎的帳戶，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="e352c-117">在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="e352c-118">封鎖存取多個使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="e352c-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="e352c-119">若要封鎖存取多個使用者帳戶，建立包含一個帳戶登入名稱類似每行的文字檔案：</span><span class="sxs-lookup"><span data-stu-id="e352c-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="e352c-p102">在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e352c-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="e352c-122">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="e352c-123">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e352c-124">使用 Windows PowerShell 的 Microsoft Azure Active Directory 模組</span><span class="sxs-lookup"><span data-stu-id="e352c-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e352c-125">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="e352c-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="e352c-126">封鎖的個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="e352c-126">Block access to individual user accounts</span></span>

<span data-ttu-id="e352c-127">使用下列語法來封鎖對個別使用者帳戶的存取：</span><span class="sxs-lookup"><span data-stu-id="e352c-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="e352c-128">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="e352c-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="e352c-129">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="e352c-130">在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="e352c-131">封鎖存取多個使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="e352c-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="e352c-132">首先，建立包含類似的每個線條上另一個帳戶的文字檔案：</span><span class="sxs-lookup"><span data-stu-id="e352c-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="e352c-p103">在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e352c-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="e352c-135">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="e352c-136">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e352c-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="e352c-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e352c-137">See also</span></span>

[<span data-ttu-id="e352c-138">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="e352c-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e352c-139">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="e352c-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e352c-140">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e352c-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
