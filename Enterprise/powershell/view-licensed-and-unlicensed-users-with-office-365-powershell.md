---
title: 使用 Office 365 PowerShell 檢視經授權與未經授權的使用者
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: 說明如何使用 Office 365 PowerShell 檢視經授權與未經授權的使用者帳戶。
ms.openlocfilehash: 0648fae89a45b080bd48561bb079184f0e97dd36
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546504"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>使用 Office 365 PowerShell 檢視經授權與未經授權的使用者

**摘要：** 說明如何使用 Office 365 PowerShell 檢視經授權與未經授權的使用者帳戶。
  
在您的 Office 365 組織中的使用者帳戶，可能具有從組織的可用授權方案指派給他們的部分授權、全部授權或完全沒有授權。您可以使用 Office 365 PowerShell 快速尋找組織中的經授權和未經授權的使用者。


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>使用 Azure Active Directory PowerShell 圖模組

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
 
若要檢視清單中所有的使用者帳戶的組織中的未指派任何您授權的計劃 （未授權的使用者），請執行下列命令：
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

若要檢視已在組織中的所有使用者帳戶清單指派任何您授權的計劃 （已獲授權的使用者），執行下列命令：
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用 Windows PowerShell 的 Microsoft Azure Active Directory 模組

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

若要檢視您組織中所有使用者帳戶及其授權狀態的清單，在 Office 365 PowerShell 中執行下列命令：
  
```
Get-MsolUser -All
```

若要檢視您組織中所有未經授權使用者帳戶的清單，執行下列命令：
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

若要檢視您組織中所有經授權使用者帳戶的清單，執行下列命令：
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
