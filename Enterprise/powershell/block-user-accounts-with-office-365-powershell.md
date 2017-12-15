---
title: "使用 Office 365 PowerShell 封鎖使用者帳戶"
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
- Ent_Office_Other
- DecEntMigration
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "說明如何使用 Office 365 PowerShell 封鎖及解除封鎖存取 Office 365 帳戶。"
ms.openlocfilehash: f22656426e7aa3adf764a3f90adea84cf57a5e89
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="block-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 封鎖使用者帳戶

**摘要：** 說明如何使用 Office 365 PowerShell 封鎖及解除封鎖存取 Office 365 帳戶。
  
封鎖 Office 365 帳戶存取權防止其他人使用帳戶來登入及存取服務和 Office 365 組織中的資料。當您封鎖的存取權之帳戶時，請當他們嘗試登入使用者會收到下列錯誤訊息：
  
![封鎖的 Office 365 帳戶。](images/o365_powershell_account_blocked.png)
  
您可以使用 Office 365 PowerShell 封鎖存取個別和多個使用者帳戶。
  
## <a name="before-you-begin"></a>開始之前

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 當您封鎖的使用者帳戶時，可能需要只要 24 小時才會在使用者的所有裝置和用戶端上生效。
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>使用 Office 365 PowerShell 來封鎖對個別使用者帳戶的存取

使用下列語法來封鎖對個別使用者帳戶的存取：
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

若要將使用者帳戶解除封鎖，請執行下列命令：
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>使用 Office 365 PowerShell 封鎖對多個使用者帳戶的存取

首先，建立包含類似的每個線條上另一個帳戶的文字檔案：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。
    
若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $true
  ```
若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $false
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>使用 Azure Active Directory V2 PowerShell 模組來封鎖使用者存取使用者帳戶

若要從 Azure Active Directory V2 PowerShell 模組使用 **New-AzureADUser** Cmdlet，您必須先連接至您的訂用帳戶。如需相關指示，請參閱[與 Azure Active Directory V2 PowerShell 模組連接](https://go.microsoft.com/fwlink/?linkid=842218)。
  
連接之後，使用下列語法來封鎖個別使用者帳戶：
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Set-AzureAD Cmdlet 中的 -ObjectID 參數接受帳戶名稱，也稱為使用者主體名稱，或帳戶的物件 ID。 
  
此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

若要將使用者帳戶解除封鎖，請執行下列命令：
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

若要顯示 UPN 根據使用者的顯示名稱的使用者帳戶，請使用下列命令：
  
```
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

本範例會顯示名為 caleb Sills Sills 之使用者的使用者帳戶 UPN。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要根據使用者的名稱封鎖帳戶，請使用下列命令︰
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

若要封鎖存取多個使用者帳戶，建立包含類似的每個線條上另一個帳戶名稱的文字檔案：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。
    
若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $true
```

若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $false
```

## <a name="see-also"></a>另請參閱
<a name="SeeAlso"> </a>

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 移除使用者帳戶中的授權](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [Set-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [新 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

