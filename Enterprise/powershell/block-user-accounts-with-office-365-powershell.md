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
# <a name="block-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 封鎖使用者帳戶

**摘要：** 說明如何使用 Office 365 PowerShell 封鎖及解除封鎖存取 Office 365 帳戶。
  
封鎖 Office 365 帳戶存取權防止其他人使用帳戶來登入及存取服務和 Office 365 組織中的資料。您可以使用 Office 365 PowerShell 封鎖存取個別和多個使用者帳戶。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 圖模組

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
 
### <a name="block-access-to-individual-user-accounts"></a>封鎖的個別使用者帳戶的存取

若要封鎖的個別使用者帳戶使用下列語法：
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> -ObjectID 參數中設定 AzureAD 指令程式可接受的帳戶登入名稱，也稱為使用者主體名稱或帳戶的物件識別碼。 
  
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
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

本範例會顯示名為 caleb Sills Sills 之使用者的使用者帳戶 UPN。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要封鎖使用者的顯示名稱為基礎的帳戶，請使用下列命令：
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>封鎖存取多個使用者帳戶

若要封鎖存取多個使用者帳戶，建立包含一個帳戶登入名稱類似每行的文字檔案：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。
  
若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模組

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

    
### <a name="block-access-to-individual-user-accounts"></a>封鎖的個別使用者帳戶的存取

使用下列語法來封鎖對個別使用者帳戶的存取：
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

若要將使用者帳戶解除封鎖，請執行下列命令：
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

在任何時候，您可以檢查封鎖的狀態之使用者帳戶具有下列命令：
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>封鎖存取多個使用者帳戶

首先，建立包含類似的每個線條上另一個帳戶的文字檔案：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
在下列命令，範例會將文字檔是 C:\My Documents\Accounts.txt。取代的文字檔案的路徑和檔案名稱。
    
若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
