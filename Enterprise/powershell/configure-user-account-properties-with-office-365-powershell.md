---
title: 使用 Office 365 PowerShell 中設定使用者帳戶屬性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要： 使用 Office 365 PowerShell 來設定 Office 365 租用戶中的個別或多個使用者帳戶的內容。
ms.openlocfilehash: 3d81a7e5860b086fd411e8e6fcaab44568e890d5
ms.sourcegitcommit: 4d29b00a57c22225f2cdd592064ee8b6e575fceb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "37411512"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>使用 Office 365 PowerShell 中設定使用者帳戶屬性

 **摘要：** 使用 Office 365 PowerShell 來設定 Office 365 租用戶中的個別或多個使用者帳戶的內容。
  
雖然您可以使用 Microsoft 365 系統管理中心來設定您的 Office 365 租用戶的使用者帳戶的內容，也可以使用 Office 365 PowerShell 並執行動作無法在系統管理中心的一些事項。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

若要設定使用者帳戶的屬性與 PowerShell 的 Azure Active Directory 針對 Graph 模組，您可以使用[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)指令程式，並指定要設定或變更的內容。 

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
   
### <a name="change-properties-for-a-specific-user-account"></a>變更特定使用者帳戶內容

您使用的 **-ObjectID**參數來識別帳戶及設定或變更與其他參數的特定屬性。 以下是最常見的參數清單。
  
- -Department"\<部門名稱> 」
    
- -DisplayName"\<完整的使用者名稱> 」
    
- -FacsimilieTelephoneNumber"\<傳真號碼> 」
    
- -GivenName"\<使用者名字> 」
    
- -姓氏"\<使用者上次名稱> 」
    
- -行動"\<行動電話號碼> 」
    
- -JobTitle"\<工作標題> 」
    
- -PreferredLanguage"\<語言> 」
    
- -StreetAddress"\<路/街> 」
    
- -City"\<縣/市名稱> 」
    
- -State"\<狀態命名> 」
    
- -PostalCode"\<郵遞區號> 」
    
- -Country"\<國家/地區名稱> 」
    
- -TelephoneNumber"\<辦公室電話號碼> 」
    
- -UsageLocation"\<2 個字元國家或地區程式碼> 」
    
    這是 ISO 3166-1 alpha-2http (A2) 兩個字母國家或地區碼。
    
如需其他參數，請參閱[設定 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。

>[!Note]
> 您設定**郵件**屬性搭配 **-OtherMails**參數。
>
 
若要顯示您的使用者帳戶的使用者主體名稱，請執行下列命令。
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將它傳送給下一個命令 ( **|** )。
    
- 顯示 User Principal Name 屬性的每個帳戶 ( **Select-object UserPrincipalName** )。
- 一次 （**更多**），顯示其一個畫面。
    
此命令會列出您的所有帳戶。 如果您想要顯示使用者主體名稱根據其顯示帳戶名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

此範例會顯示顯示名稱為 Caleb Sills 的使用者帳戶的使用者主體名稱。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。 以下是將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱，而不是其使用者主體名稱範例：
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>變更所有使用者帳戶的內容

若要變更的所有使用者的內容，您可以使用**Get-AzureADUser**和**設定 AzureADUser**指令程式的組合。 下列範例會變更為法國所有使用者的使用狀況位置：
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 將使用者位置設定為法國 (**組 AzureADUser-UsageLocation"FR"** )。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>變更一組特定的使用者帳戶的內容

若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-AzureADUser**、**位置**及**組 AzureADUser**指令程式的組合。 下列範例會變更為法國會計部門中的所有使用者的使用狀況位置：
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 尋找所有使用者帳戶具有 Department 屬性設為"Accounting"(**其中 {$_。Department-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。
    
- 將使用者位置設定為法國 (**組 AzureADUser-UsageLocation"FR"** )。
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

若要設定使用者帳戶的屬性與 Microsoft Azure Active Directory 模組的 Windows PowerShell，您可以使用 Set-msoluser cmdlet，並指定要設定或變更的內容。 

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
  
### <a name="change-properties-for-a-specific-user-account"></a>變更特定使用者帳戶內容

若要設定特定的使用者帳戶的內容，您可以使用[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet，並指定要設定或變更的內容。 

使用 **-UserPrincipalName**參數識別的帳戶，並設定或變更與其他參數的特定屬性。 以下是最常見的參數清單。
  
- -City"\<縣/市名稱> 」
    
- -Country"\<國家/地區名稱> 」
    
- -Department"\<部門名稱> 」
    
- -DisplayName"\<完整的使用者名稱> 」
    
- -Fax"\<傳真號碼> 」
    
- -FirstName"\<使用者名字> 」
    
- -LastName"\<使用者上次名稱> 」
    
- -MobilePhone"\<行動電話號碼> 」
    
- -Office"\<辦公室位置> 」
    
- -PhoneNumber"\<辦公室電話號碼> 」
    
- -PostalCode"\<郵遞區號> 」
    
- -PreferredLanguage"\<語言> 」
    
- -State"\<狀態命名> 」
    
- -StreetAddress"\<路/街> 」
    
- -Title"\<標題名稱> 」
    
- -UsageLocation"\<2 個字元國家或地區程式碼> 」
    
    這是 ISO 3166-1 alpha-2http (A2) 兩個字母國家或地區碼。
    
如需其他參數，請參閱[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。

>[!Note]
> 您設定**郵件**屬性搭配 **-AlternateEmailAddresses**參數。
>
 
若要查看您的所有使用者的使用者主體名稱，請執行下列命令。
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將它傳送給下一個命令 ( **|** )。
    
- 顯示 User Principal Name 屬性的每個帳戶 ( **Select-object UserPrincipalName** )。
    
- 一次 （**更多**），顯示其一個畫面。
    
此命令會列出您的所有帳戶。 如果您想要顯示使用者主體名稱根據其顯示帳戶名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

此範例會顯示名為 Caleb Sills 的使用者的使用者主體名稱。
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。 以下是將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱，而不是其使用者主體名稱範例：
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>變更所有使用者帳戶的內容

若要變更的所有使用者的內容，您可以使用**Get-msoluser**和**Set-msoluser** cmdlet 的組合。 下列範例會變更為法國所有使用者的使用狀況位置：
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 將使用者位置設定為法國 ( **Set-msoluser-UsageLocation"FR"** )。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>變更一組特定的使用者帳戶的內容

若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-msoluser**、 **Where-object cmdlet**，以及**Set-msoluser** cmdlet 的組合。 下列範例會變更為法國會計部門中的所有使用者的使用狀況位置：
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

此命令會指示 Office 365 PowerShell 來：
  
- 取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。
    
- 尋找所有的使用者帳戶具有其 Department 屬性設為 「 會計 」 ( **Where-object {$_。Department-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。
    
- 將使用者位置設定為法國 ( **Set-msoluser-UsageLocation"FR"** )。
    

## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
