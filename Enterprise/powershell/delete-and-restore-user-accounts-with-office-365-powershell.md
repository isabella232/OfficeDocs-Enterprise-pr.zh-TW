---
title: "使用 Office 365 PowerShell 刪除及還原使用者帳戶"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "了解如何使用 Office 365 PowerShell 來刪除並還原 Office 365 使用者帳戶。"
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a4149-103">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4149-103">Delete and restore user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a4149-104">**摘要：** 了解如何使用 Office 365 PowerShell 來刪除並還原 Office 365 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4149-104">**Summary:**  Learn how to use Office 365 PowerShell to delete and restore Office 365 user accounts.</span></span>
  
<span data-ttu-id="a4149-p101">當您使用 Office 365 PowerShell 來刪除使用者帳戶時，該帳戶並不會永久刪除。您可以在 30 天內還原已刪除的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4149-p101">When you use Office 365 PowerShell to delete a user account, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="a4149-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="a4149-107">Before you begin</span></span>

- <span data-ttu-id="a4149-p102">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="a4149-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="a4149-110">如果您使用**Get-msoluser** cmdlet 而不需使用_-所有_參數，傳回前 500 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4149-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a><span data-ttu-id="a4149-111">使用 Office 365 PowerShell 來封鎖對個別使用者帳戶的存取</span><span class="sxs-lookup"><span data-stu-id="a4149-111">Use Office 365 PowerShell to block access to individual user accounts</span></span>
<span data-ttu-id="a4149-112"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a4149-112"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="a4149-113">若要刪除使用者帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a4149-113">To delete a user account, use the following syntax:</span></span>
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="a4149-114">此範例會刪除使用者帳戶 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="a4149-114">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="a4149-115">若要在 30 天的寬限期內還原已刪除的使用者帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="a4149-115">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

<span data-ttu-id="a4149-116">此範例會還原已刪除的帳戶 BelindaN@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="a4149-116">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="a4149-117">**附註：**</span><span class="sxs-lookup"><span data-stu-id="a4149-117">**Notes:**</span></span>
  
- <span data-ttu-id="a4149-118">若要查看可以還原的已刪除使用者清單，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a4149-118">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="a4149-119">如果使用者帳戶的原始使用者主要名稱被另一個帳戶使用，當您還原使用者帳戶時，請使用  _NewUserPrincipalName_ 參數 (而不是 _UserPrincipalName_) 來指定不同的使用者主要名稱。</span><span class="sxs-lookup"><span data-stu-id="a4149-119">If the user account's original user principal name is used by another account, use the  _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a><span data-ttu-id="a4149-120">使用 Azure Active Directory V2 PowerShell 模組來移除使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4149-120">Use the Azure Active Directory V2 PowerShell module to remove a user account</span></span>
<span data-ttu-id="a4149-121"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="a4149-121"><a name="ShortVersion"> </a></span></span>

<span data-ttu-id="a4149-p103">若要使用從 Azure Active Directory V2 PowerShell 模組**移除 AzureADUser**指令程式，您必須先連線至您的訂閱。指示，請參閱[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="a4149-p103">To use the **Remove-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="a4149-124">連接之後，使用下列語法來移除個別使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="a4149-124">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```
Remove-AzureADUser -ObjectID <Account>
```

<span data-ttu-id="a4149-125">此範例會移除使用者帳戶 fabricec@litwareinc.com。</span><span class="sxs-lookup"><span data-stu-id="a4149-125">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="a4149-126">**Remove-AzureAD** Cmdlet 中的 **-ObjectID** 參數接受帳戶名稱，也稱為使用者主體名稱，或帳戶的物件 ID。</span><span class="sxs-lookup"><span data-stu-id="a4149-126">The **-ObjectID** parameter in the **Remove-AzureAD** cmdlet accepts either the account name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="a4149-127">若要根據使用者的名稱顯示帳戶名稱，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="a4149-127">To display the account name based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a4149-128">本範例針對名為 Caleb Sills 的使用者顯示帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="a4149-128">This example displays the account name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a4149-129">若要根據使用者的名稱移除帳戶，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="a4149-129">To remove an account based on the user's name, use the following commands:</span></span>
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a><span data-ttu-id="a4149-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4149-130">See also</span></span>
<span data-ttu-id="a4149-131"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="a4149-131"><a name="SeeAlso"> </a></span></span>

<span data-ttu-id="a4149-132">請參閱下列有關管理 Office 365 PowerShell 與使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="a4149-132">See these additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="a4149-133">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4149-133">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4149-134">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4149-134">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4149-135">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a4149-135">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="a4149-136">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="a4149-136">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="a4149-137">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a4149-137">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="a4149-138">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a4149-138">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="a4149-139">Remove-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a4149-139">Remove-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [<span data-ttu-id="a4149-140">Restore-MsolUser</span><span class="sxs-lookup"><span data-stu-id="a4149-140">Restore-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [<span data-ttu-id="a4149-141">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="a4149-141">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

