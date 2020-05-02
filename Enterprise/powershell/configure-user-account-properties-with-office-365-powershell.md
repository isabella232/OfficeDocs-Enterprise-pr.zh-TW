---
title: 使用 Office 365 PowerShell 中設定使用者帳戶屬性
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要：使用 Office 365 PowerShell 來設定 Office 365 租使用者中個別或多個使用者帳戶的屬性。
ms.openlocfilehash: 5748bd382357168e4184754fb49fb7304e2d2474
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004716"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>使用 Office 365 PowerShell 中設定使用者帳戶屬性

雖然您可以使用 Microsoft 365 系統管理中心來設定 Office 365 租使用者帳戶的屬性，但您也可以使用 Office 365 PowerShell，並執行系統管理中心的某些工作。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

若要使用適用于 Graph 模組的 Azure Active Directory PowerShell，設定使用者帳戶的屬性，您可以使用[AzureADUser 指令程式](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)，並指定要設定或變更的屬性。 

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
   
### <a name="change-properties-for-a-specific-user-account"></a>變更特定使用者帳戶的屬性

您可以使用 **-ObjectID**參數識別帳戶，並設定或變更具有其他參數的特定屬性。 以下是最常見的參數清單。
  
- -部門 "\<部門名稱>"
    
- -DisplayName "\<完整使用者名稱>"
    
- -FacsimilieTelephoneNumber 「\<傳真號碼>
    
- -GivenName "\<user first name>"
    
- -姓 "\<user last name>"
    
- -Mobile "\<mobile phone number>"
    
- -JobTitle "\<職稱>"
    
- -PreferredLanguage "\<language>"
    
- -StreetAddress "\<街道位址>"
    
- -城市「\<城市名稱>
    
- -State "\<state name>"
    
- -PostalCode "\<郵遞區號>"
    
- -國家/\<地區 "country name>"
    
- -TelephoneNumber "\<office phone number>"
    
- -UsageLocation "\<2 個字元的國家或地區代碼>"
    
    這是 ISO 3166-1 Alpha-2 （A2）雙字母的國家或地區碼。
    
請參閱[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for 其他參數。


若要為您的使用者帳戶顯示使用者主要名稱，請執行下列命令。
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

這個命令會指示 Office 365 PowerShell：
  
- 取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。
    
- 依字母順序排序使用者主體名稱清單（ **Sort UserPrincipalName** ），並將其傳送至下一個**|** 命令（）。
    
- 只顯示每個帳戶的使用者主體名稱屬性（**選取 UserPrincipalName** ）。

- 一次顯示一屏（**更多**）。
    
這個命令會列出您的所有帳戶。 如果您想要根據其顯示名稱（名字和姓氏）顯示帳戶的使用者主要名稱，請填入下列的 **$userName**變數（移除\<和 > 字元），然後執行下列命令：
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本範例會顯示名稱為 Caleb Sills 帳戶的使用者帳戶使用者主要名稱。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

使用 **$upn**變數，您可以根據其顯示名稱來變更個別帳戶。 以下範例會將 Belinda Newman 的使用位置設定為法國，但指定其顯示名稱，而不是其使用者主要名稱：
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>變更所有使用者帳戶的屬性

若要變更所有使用者的屬性，您可以使用**AzureADUser**和**AzureADUser** Cmdlet 的組合。 下列範例會將所有使用者的使用位置變更為華北：
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

這個命令會指示 Office 365 PowerShell：
  
- 取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。
    
- 將使用者位置設定為法國（ **AzureADUser-UsageLocation "FR"** ）。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>變更特定使用者帳戶組的屬性

若要變更特定使用者帳戶集的屬性，您可以使用**AzureADUser**、 **Where**及**AzureADUser** Cmdlet 的組合。 下列範例會將會計部門中所有使用者的使用量位置變更為華北：
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

這個命令會指示 Office 365 PowerShell：
  
- 取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。
    
- 尋找其部門屬性設定為 "記帳" 的所有使用者帳戶（**其中 {$ _）。部門-eq "記帳"}** ）並將結果資訊傳送至下一個命令（ **|** ）。
    
- 將使用者位置設定為法國（ **AzureADUser-UsageLocation "FR"** ）。
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

若要使用 Microsoft Azure Active Directory Module for Windows PowerShell 設定使用者帳戶的屬性，您可以使用**Set-MsolUser** Cmdlet，並指定要設定或變更的屬性。 

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
  
>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

### <a name="change-properties-for-a-specific-user-account"></a>變更特定使用者帳戶的屬性

若要設定特定使用者帳戶的屬性，您可以使用[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) Cmdlet，並指定要設定或變更的屬性。 

您可以使用 **-UserPrincipalName**參數來識別帳戶，並設定或變更具有其他參數的特定屬性。 以下是最常見的參數清單。
  
- -城市「\<城市名稱>
    
- -國家/\<地區 "country name>"
    
- -部門 "\<部門名稱>"
    
- -DisplayName "\<完整使用者名稱>"
    
- -傳真 "\<傳真號碼>"
    
- -FirstName "\<user first name>"
    
- -LastName "\<user last name>"
    
- -MobilePhone "\<行動電話號碼>"
    
- -Office "\<office 位置>"
    
- -PhoneNumber "\<office phone number>"
    
- -PostalCode "\<郵遞區號>"
    
- -PreferredLanguage "\<language>"
    
- -State "\<state name>"
    
- -StreetAddress "\<街道位址>"
    
- -Title "\<title name>"
    
- -UsageLocation "\<2 個字元的國家或地區代碼>"
    
    這是 ISO 3166-1 Alpha-2 （A2）雙字母的國家或地區碼。
    
如需其他參數，請參閱[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 。

若要查看所有使用者的使用者主要名稱，請執行下列命令。
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

這個命令會指示 Office 365 PowerShell：
  
- 取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。
    
- 依字母順序排序使用者主體名稱清單（ **Sort UserPrincipalName** ），並將其傳送至下一個**|** 命令（）。
    
- 只顯示每個帳戶的使用者主體名稱屬性（**選取 UserPrincipalName** ）。
    
- 一次顯示一屏（**更多**）。
    
這個命令會列出您的所有帳戶。 如果您想要根據其顯示名稱（名字和姓氏）顯示帳戶的使用者主要名稱，請填入下列的 **$userName**變數（移除\<和 > 字元），然後執行下列命令：
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

此範例會顯示名為 Caleb Sills 帳戶之使用者的使用者主要名稱。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

使用 **$upn**變數，您可以根據其顯示名稱來變更個別帳戶。 以下範例會將 Belinda Newman 的使用位置設定為法國，但指定其顯示名稱，而不是其使用者主要名稱：
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>變更所有使用者帳戶的屬性

若要變更所有使用者的屬性，您可以使用**Get-MsolUser**和**Set-MsolUser** Cmdlet 的組合。 下列範例會將所有使用者的使用位置變更為華北：
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

這個命令會指示 Office 365 PowerShell：
  
- 取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。
    
- 將使用者位置設定為法國（ **Set-MsolUser UsageLocation "FR"** ）。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>變更特定使用者帳戶組的屬性

若要變更特定使用者帳戶集的屬性，您可以使用**Get-MsolUser**、 **Where**及**Set-MsolUser** Cmdlet 的組合。 下列範例會將會計部門中所有使用者的使用量位置變更為華北：
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

這個命令會指示 Office 365 PowerShell：
  
- 取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。
    
- 尋找其部門屬性設定為 "記帳" 的所有使用者帳戶（**其中 {$ _）。部門-eq "記帳"}** ）並將結果資訊傳送至下一個命令（ **|** ）。
    
- 將使用者位置設定為法國（ **Set-MsolUser UsageLocation "FR"** ）。
    

## <a name="see-also"></a>另請參閱

[使用 Office 365 管理使用者帳戶、授權和群組 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
