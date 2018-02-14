---
title: "使用 Office 365 PowerShell 中設定使用者帳戶屬性"
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "摘要： 使用 Office 365 PowerShell Office 365 租用戶中設定的個人或多個使用者帳戶屬性。"
ms.openlocfilehash: 60b3c1d91df0cb28f19f60a285093de7337904a9
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>使用 Office 365 PowerShell 中設定使用者帳戶屬性

 **摘要：**使用 Office 365 PowerShell 來設定您的 Office 365 租用戶中的個人或多個使用者帳戶的屬性。
  
雖然您可以使用 Office 365 系統管理中心來設定您的 Office 365 租用戶的使用者帳戶的內容，也可以使用 Office 365 PowerShell 並執行一些無法在 Office 365 系統管理中心。
  
## <a name="before-you-begin"></a>開始之前

本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="change-properties-for-a-specific-user-account"></a>變更特定的使用者帳戶的屬性

若要設定特定的使用者帳戶的屬性，您可以使用[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 並指定來設定或變更的屬性。此範例命令會將 Belinda Newman 的使用狀況位置變更為法國：
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

您使用**-UserPrincipalName**參數來識別帳戶及設定或變更的額外參數的特定屬性。這裡是清單的最常見的參數。
  
- --市/鎮"\<城市名稱 >"
    
- -國家"\<國家/地區名稱 >"
    
- -部門"\<部門名稱 >"
    
- -DisplayName"\<完整的使用者名稱 >"
    
- -傳真"\<傳真號碼 >"
    
- -FirstName"\<使用者名字 >"
    
- -LastName"\<使用者上次名稱 >"
    
- -MobilePhone"\<行動電話號碼 >"
    
- Office"\<辦公室位置 >"
    
- -[Phonenumber]"\<辦公室電話號碼 >"
    
- -PostalCode"\<郵遞區號 >"
    
- -PreferredLanguage"\<語言 >"
    
- -State"\<狀態名稱 >"
    
- -StreetAddress"\<街道地址 >"
    
- -Title"\<標題名稱 >"
    
- -UsageLocation"\<2 個字元的國家或地區的程式碼 >"
    
    這是 ISO 3166-1 alpha-2 (A2) 雙字母國家或地區碼。
    
請參閱[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx)額外的參數。
  
若要查看使用者主體名稱的所有使用者，請執行下列命令。
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將其傳送給下一個命令 ( **|** )。
    
- 顯示使用者主體名稱屬性的每個帳戶 ( **Select-object UserPrincipalName** )。
    
- 顯示一個畫面 （**更多**） 一次。
    
此命令會列出所有的帳戶。如果您想要顯示根據其帳戶的使用者主體名稱名稱 （第一個及最後一個名稱）、 填滿下**$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本範例會顯示名為 caleb Sills Sills 使用者的使用者主體名稱。
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

藉由使用**$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。以下是範例將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱而不是其使用者主體名稱：
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>變更所有使用者帳戶的屬性

若要變更的所有使用者的屬性，您可以使用**Get-msoluser**和**Set-msoluser** cmdlet 的組合。下列範例會將所有使用者的使用狀況位置變更為法國：
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 法國 ( **Set-msoluser UsageLocation"FR-FR"** ) 來設定使用者位置。
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>變更一組特定的使用者帳戶的屬性

若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-msoluser**、 **Where-object**和**Set-msoluser** cmdlet 的組合。下列範例會將會計部門的所有使用者的使用狀況位置變更為法國：
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 找到的所有使用者帳戶具有其部門屬性設定為 「 會計 」 ( **Where-object {$_。部門-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。
    
- 法國 ( **Set-msoluser UsageLocation"FR-FR"** ) 來設定使用者位置。
    
- 顯示一個畫面 （**更多**） 一次。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>使用 Azure Active Directory V2 PowerShell 模組來設定使用者帳戶屬性

使用 Azure Active Directory V2 PowerShell 模組設定的使用者帳戶內容，您可以使用[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)指令程式並指定來設定或變更的屬性。但首先，您必須連線到您的訂閱。指示，請參閱[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。
  
### <a name="change-properties-for-a-specific-user-account"></a>變更特定的使用者帳戶的屬性

此範例命令會將 Belinda Newman 的使用狀況位置變更為法國：
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

您使用**-ObjectID**參數來識別帳戶及設定或變更的額外參數的特定屬性。這裡是清單的最常見的參數。
  
- -部門"\<部門名稱 >"
    
- -DisplayName"\<完整的使用者名稱 >"
    
- -FacsimilieTelephoneNumber"\<傳真號碼 >"
    
- -GivenName"\<使用者名字 >"
    
- -姓氏"\<使用者上次名稱 >"
    
- -行動"\<行動電話號碼 >"
    
- -JobTitle"\<職稱 >"
    
- -PreferredLanguage"\<語言 >"
    
- -StreetAddress"\<街道地址 >"
    
- --市/鎮"\<城市名稱 >"
    
- -State"\<狀態名稱 >"
    
- -PostalCode"\<郵遞區號 >"
    
- -國家"\<國家/地區名稱 >"
    
- -TelephoneNumber"\<辦公室電話號碼 >"
    
- -UsageLocation"\<2 個字元的國家或地區的程式碼 >"
    
    這是 ISO 3166-1 alpha-2 (A2) 雙字母國家或地區碼。
    
請參閱額外的參數[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。
  
若要顯示您的使用者帳戶的使用者主體名稱，請執行下列命令。
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將其傳送給下一個命令 ( **|** )。
    
- 顯示使用者主體名稱屬性的每個帳戶 ( **Select-object UserPrincipalName** )。
- 顯示一個畫面 （**更多**） 一次。
    
此命令會列出所有的帳戶。如果您想要顯示根據其帳戶的使用者主體名稱名稱 （第一個及最後一個名稱）、 填滿下**$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

本範例會顯示名為 caleb Sills Sills 使用者的使用者主體名稱。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

藉由使用**$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。以下是範例將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱而不是其使用者主體名稱：
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>變更所有使用者帳戶的屬性

若要變更的所有使用者的屬性，您可以使用**Get AzureADUser**和**設定 AzureADUser**指令程式的組合。下列範例會將所有使用者的使用狀況位置變更為法國：
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 法國 (**組 AzureADUser UsageLocation"FR-FR"** ) 來設定使用者位置。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>變更一組特定的使用者帳戶的屬性

若要變更的一組特定的使用者帳戶屬性，您可以使用**Get AzureADUser**、**位置**及**組 AzureADUser** cmdlet 的組合。下列範例會將會計部門的所有使用者的使用狀況位置變更為法國：
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

此命令會指示至 Office 365 PowerShell：
  
- 會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。
    
- 尋找所有已設定為"Accounting"其部門屬性的使用者帳戶 (**其中 {$_。部門-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。
    
- 法國 (**組 AzureADUser UsageLocation"FR-FR"** ) 來設定使用者位置。
    
## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

