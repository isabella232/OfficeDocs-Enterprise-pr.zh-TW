---
title: 使用 Office 365 PowerShell 移除使用者帳戶中的授權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: 說明如何使用 Office 365 PowerShell 移除先前已指派給使用者的 Office 365 授權。
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651217"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 移除使用者帳戶中的授權

**摘要：** 說明如何使用 Office 365 PowerShell 移除先前已指派給使用者的 Office 365 授權。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下來，列出您使用此命令的租用戶授權計劃。

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下來，取得您想移除的授權，又稱為使用者主體名稱 (UPN) 的帳戶登入名稱。

最後，指定使用者登入] 及 [授權計劃名稱、 移除"<"和">"的字元，並執行下列命令。

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

   
若要檢視您的組織的授權的計劃 (**AccountSkuID** ) 資訊，請參閱下列主題：
    
  - [使用 Office 365 PowerShell 檢視授權與服務](view-licenses-and-services-with-office-365-powershell.md)
    
  - [使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料](view-account-license-and-service-details-with-office-365-powershell.md)
    
如果您使用 **Get-MsolUser** Cmdlet，而不使用 _-All_參數，則只會傳回前 500 個帳戶。
    
### <a name="removing-licenses-from-user-accounts"></a>從使用者帳戶移除授權

若要移除現有使用者帳戶中的授權，使用下列語法：
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權與使用者帳戶 BelindaN@litwareinc.com。
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

若要移除現有的經授權使用者群組的授權，使用下列方法之一：
  
- **篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從所有 accounts 在美國 「 業務 」 部門中的使用者。
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **使用特定帳戶的清單**若要這樣做，執行下列步驟：
    
1. 建立一個每一行一個帳戶的文字檔，像這樣：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 使用下列語法：
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

此範例會移除`litwareinc:ENTERPRISEPACK`從文字檔案 C:\My Documents\Accounts.txt 中所定義的使用者帳戶 (Office 365 企業版 E3) 授權。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

若要移除所有現有使用者帳戶中的授權，使用下列語法：
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從現有的所有授權的使用者帳戶。
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

釋放授權的另一種方式是由刪除的使用者帳戶。如需詳細資訊，請參閱[刪除並還原與 Office 365 PowerShell 的使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a>第一次使用 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

