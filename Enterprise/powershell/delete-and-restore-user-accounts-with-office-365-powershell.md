---
title: 使用 Office 365 PowerShell 刪除使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: 了解如何使用 Office 365 PowerShell 來刪除 Office 365 使用者帳戶。
ms.openlocfilehash: ea803d82bb54e5430ceb9a59e8c04a0f72b200fc
ms.sourcegitcommit: 069f56455252d6f4001ec0ecee792b83b585e692
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "43237804"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 刪除使用者帳戶

若要刪除使用者帳戶，您可以使用 Office 365 PowerShell。
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

連接之後，使用下列語法來移除個別使用者帳戶：
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

此範例會移除使用者帳戶 fabricec@litwareinc.com。
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **AzureADUser 指令程式**中的 **-ObjectID**參數會接受帳戶的登入名稱，也稱為使用者主要名稱，或帳戶的物件識別碼。
  
若要根據使用者的名稱顯示帳戶名稱，請使用下列命令︰
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本範例針對名為 Caleb Sills 的使用者顯示帳戶名稱。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要根據使用者的顯示名稱移除帳戶，請使用下列命令︰
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組來刪除使用者帳戶時，該帳戶並不會永久刪除。您可以在 30 天內還原已刪除的使用者帳戶。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

若要刪除使用者帳戶，請使用下列語法：
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

此範例會刪除使用者帳戶 BelindaN@litwareinc.com。
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

若要在 30 天的寬限期內還原已刪除的使用者帳戶，請使用下列語法：
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

此範例會還原已刪除的帳戶 BelindaN@litwareinc.com。
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **附註：**
  
- 若要查看可以還原的已刪除使用者清單，請執行下列命令：
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- 如果使用者帳戶的原始使用者主要名稱被另一個帳戶使用，當您還原使用者帳戶時，請使用 _NewUserPrincipalName_ 參數 (而不是 _UserPrincipalName_) 來指定不同的使用者主要名稱。


## <a name="see-also"></a>另請參閱

[使用 Office 365 管理使用者帳戶、授權和群組 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
