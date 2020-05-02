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
# <a name="block-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 封鎖使用者帳戶

封鎖 Office 365 帳戶的存取權，可防止任何人使用該帳戶登入，並存取您 Office 365 組織中的服務和資料。 您可以使用 Office 365 PowerShell 來封鎖個別和多個使用者帳戶的存取。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
 
### <a name="block-access-to-individual-user-accounts"></a>封鎖個別使用者帳戶的存取

使用下列語法來封鎖個別使用者帳戶：
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> Set-AzureAD 指令程式中的-ObjectID 參數會接受帳戶登入名稱，也稱為使用者主要名稱，或者是帳戶的物件識別碼。 
  
此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

若要將使用者帳戶解除封鎖，請執行下列命令：
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

若要根據使用者的顯示名稱來顯示使用者帳戶 UPN，請使用下列命令：
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

此範例會顯示名為 Caleb Sills 帳戶之使用者的使用者帳戶 UPN。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

若要根據使用者的顯示名稱封鎖帳戶，請使用下列命令：
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

您可以隨時使用下列命令來檢查使用者帳戶的封鎖狀態：
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>封鎖對多個使用者帳戶的存取

若要封鎖對多個使用者帳戶的存取，請建立一個文字檔，其中每一行上都包含一個帳戶登入名稱，如下所示：
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

在下列命令中，範例文字檔是 C:\My Documents\Accounts.txt。 以您的文字檔的路徑和檔案名取代。
  
若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
    
### <a name="block-access-to-individual-user-accounts"></a>封鎖個別使用者帳戶的存取

使用下列語法來封鎖對個別使用者帳戶的存取：
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

此範例會封鎖對使用者帳戶 fabricec@litwareinc.com 的存取。
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

若要將使用者帳戶解除封鎖，請執行下列命令：
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

您可以隨時使用下列命令來檢查使用者帳戶的封鎖狀態：
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>封鎖對多個使用者帳戶的存取

首先，建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

在下列命令中，範例文字檔是 C:\My Documents\Accounts.txt。 以您的文字檔的路徑和檔案名取代。
    
若要封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
若要解除封鎖對文字檔中所列帳戶的存取，請執行下列命令：
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>另請參閱

[使用 Office 365 管理使用者帳戶、授權和群組 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
