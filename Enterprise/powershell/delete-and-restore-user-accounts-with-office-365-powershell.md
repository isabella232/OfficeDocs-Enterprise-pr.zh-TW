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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "了解如何使用 Office 365 PowerShell 來刪除和還原 Office 365 使用者帳戶。"
ms.openlocfilehash: 09f3595ed7cd5434efb2897a43ba1bbca5286c25
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 刪除及還原使用者帳戶

**摘要：**了解如何使用 Office 365 PowerShell 來刪除和還原 Office 365 使用者帳戶。
  
當您使用 Office 365 PowerShell 來刪除使用者帳戶時，該帳戶並不會永久刪除。您可以在 30 天內還原已刪除的使用者帳戶。
  
## <a name="before-you-begin"></a>開始之前

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 如果您使用 **Get-MsolUser** Cmdlet，而不使用 _-All_參數，則只會傳回前 500 個帳戶。
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>使用 Office 365 PowerShell 來封鎖對個別使用者帳戶的存取
<a name="ShortVersion"> </a>

若要刪除使用者帳戶，請使用下列語法：
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

此範例會刪除使用者帳戶 BelindaN@litwareinc.com。
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

若要在 30 天的寬限期內還原已刪除的使用者帳戶，請使用下列語法：
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

此範例會還原已刪除的帳戶 BelindaN@litwareinc.com。
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **附註：**
  
- 若要查看可以還原的已刪除使用者清單，請執行下列命令：
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- 如果使用者帳戶的原始使用者主要名稱被另一個帳戶使用，當您還原使用者帳戶時，請使用  _NewUserPrincipalName_ 參數 (而不是 _UserPrincipalName_) 來指定不同的使用者主要名稱。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>使用 Azure Active Directory V2 PowerShell 模組來移除使用者帳戶
<a name="ShortVersion"> </a>

若要從 Azure Active Directory V2 PowerShell 模組使用 **Remove-AzureADUser** Cmdlet，您必須先連線至您的訂用帳戶。如需相關指示，請參閱[與 Azure Active Directory V2 PowerShell 模組連線](https://go.microsoft.com/fwlink/?linkid=842218)。
  
連接之後，使用下列語法來移除個別使用者帳戶：
  
```
Remove-AzureADUser -ObjectID <Account>
```

此範例會移除使用者帳戶 fabricec@litwareinc.com。
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **Remove-AzureAD** Cmdlet 中的 **-ObjectID** 參數接受帳戶名稱，也稱為使用者主體名稱，或帳戶的物件 ID。
  
若要根據使用者的名稱顯示帳戶名稱，請使用下列命令︰
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本範例針對名為 Caleb Sills 的使用者顯示帳戶名稱。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要根據使用者的名稱移除帳戶，請使用下列命令︰
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>另請參閱
<a name="SeeAlso"> </a>

請參閱這些有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 移除使用者帳戶中的授權](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

