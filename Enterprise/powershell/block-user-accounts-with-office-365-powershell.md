---
title: "使用 Office 365 PowerShell 封鎖使用者帳戶"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "說明如何使用 Office 365 PowerShell 封鎖及解除封鎖存取 Office 365 帳戶。"
ms.openlocfilehash: 34d144c982210ddc9d557b6094f71706f8edbb7f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d0e19-103">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d0e19-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d0e19-104">**摘要：** 說明如何使用 Office 365 PowerShell 封鎖及解除封鎖存取 Office 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0e19-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="d0e19-p101">封鎖 Office 365 帳戶存取權防止其他人使用帳戶來登入及存取服務和 Office 365 組織中的資料。當您封鎖的存取權之帳戶時，請當他們嘗試登入使用者會收到下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="d0e19-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. When you block access to the account, the user receives the following error message when they attempt to sign in:</span></span>
  
![封鎖的 Office 365 帳戶。](images/o365_powershell_account_blocked.png)
  
<span data-ttu-id="d0e19-108">您可以使用 Office 365 PowerShell 封鎖存取個別和多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0e19-108">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d0e19-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="d0e19-109">Before you begin</span></span>

- <span data-ttu-id="d0e19-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e19-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d0e19-112">當您封鎖的使用者帳戶時，可能需要只要 24 小時才會在使用者的所有裝置和用戶端上生效。</span><span class="sxs-lookup"><span data-stu-id="d0e19-112">When you block a user account, it might take as long as 24 hours to take effect on all the user's devices and clients.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="d0e19-113">使用 Office 365 PowerShell 來封鎖對個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="d0e19-113">Use Office 365 PowerShell to block access to individual user accounts</span></span>

<span data-ttu-id="d0e19-114">使用下列語法來封鎖對個別使用者帳戶的存取：</span><span class="sxs-lookup"><span data-stu-id="d0e19-114">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

<span data-ttu-id="d0e19-115">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="d0e19-115">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="d0e19-116">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-116">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

<span data-ttu-id="d0e19-117">在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a><span data-ttu-id="d0e19-118">使用 Office 365 PowerShell 封鎖對多個使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="d0e19-118">Use Office 365 PowerShell to block access to multiple user accounts</span></span>

<span data-ttu-id="d0e19-119">首先，建立包含類似的每個線條上另一個帳戶的文字檔案：</span><span class="sxs-lookup"><span data-stu-id="d0e19-119">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="d0e19-p103">在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d0e19-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="d0e19-122">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="d0e19-123">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a><span data-ttu-id="d0e19-124">使用 Azure Active Directory V2 PowerShell 模組來封鎖使用者存取使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d0e19-124">Use the Azure Active Directory V2 PowerShell module to block access to user accounts</span></span>

<span data-ttu-id="d0e19-p104">若要從 Azure Active Directory V2 PowerShell 模組使用 **New-AzureADUser** Cmdlet，您必須先連接至您的訂用帳戶。如需相關指示，請參閱[與 Azure Active Directory V2 PowerShell 模組連接](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="d0e19-p104">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="d0e19-127">連接之後，使用下列語法來封鎖個別使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="d0e19-127">After you have connected, use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="d0e19-128">Set-AzureAD Cmdlet 中的 -ObjectID 參數接受帳戶名稱，也稱為使用者主體名稱，或帳戶的物件 ID。</span><span class="sxs-lookup"><span data-stu-id="d0e19-128">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="d0e19-129">此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。</span><span class="sxs-lookup"><span data-stu-id="d0e19-129">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="d0e19-130">若要將使用者帳戶解除封鎖，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-130">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="d0e19-131">若要顯示 UPN 根據使用者的顯示名稱的使用者帳戶，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-131">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="d0e19-132">本範例會顯示名為 caleb Sills Sills 之使用者的使用者帳戶 UPN。</span><span class="sxs-lookup"><span data-stu-id="d0e19-132">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d0e19-133">若要根據使用者的名稱封鎖帳戶，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="d0e19-133">To block an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="d0e19-134">在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-134">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

<span data-ttu-id="d0e19-135">若要封鎖存取多個使用者帳戶，建立包含類似的每個線條上另一個帳戶名稱的文字檔案：</span><span class="sxs-lookup"><span data-stu-id="d0e19-135">To block access to multiple user accounts, create a text file that contains one account name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="d0e19-p105">在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d0e19-p105">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="d0e19-138">若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-138">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="d0e19-139">若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d0e19-139">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="see-also"></a><span data-ttu-id="d0e19-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e19-140">See also</span></span>
<span data-ttu-id="d0e19-141"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="d0e19-141"></span></span>

<span data-ttu-id="d0e19-142">請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="d0e19-142">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="d0e19-143">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d0e19-143">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0e19-144">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d0e19-144">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0e19-145">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d0e19-145">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d0e19-146">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="d0e19-146">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="d0e19-147">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d0e19-147">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="d0e19-148">Get-content</span><span class="sxs-lookup"><span data-stu-id="d0e19-148">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [<span data-ttu-id="d0e19-149">Set-msoluser</span><span class="sxs-lookup"><span data-stu-id="d0e19-149">Set-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [<span data-ttu-id="d0e19-150">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="d0e19-150">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

