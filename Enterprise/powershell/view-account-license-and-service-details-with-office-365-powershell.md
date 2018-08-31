---
title: 使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: 說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223105"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料

**摘要：** 說明如何使用 Office 365 PowerShell 來判斷已指派給使用者的 Office 365 服務。
  
在 Office 365 授權的授權方案 （也稱為的 Sku 或 Office 365 計劃） 讓使用者能夠存取 Office 365 服務所定義的那些計劃。不過，使用者可能無法存取所有目前已指派給他們的授權中可用的服務。您可以使用 Office 365 PowerShell 檢視的使用者帳戶之服務的狀態。 

## <a name="before-you-begin"></a>開始之前

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用命令`Get-MsolAccountSku`和`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`尋找下列資訊：
    
  - 您的組織可用的授權計劃。
    
  - 每個授權計劃中可用的服務，以及其列出的順序 (索引編號)。
    
     如需授權方案、 授權、 及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。
    
- 使用命令`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`尋找的授權指派給使用者和的順序，其中所列 （索引編號）。
    
- 如果您使用 **Get-MsolUser** Cmdlet，而不使用 _All_ 參數，則只會傳回前 500 個帳戶。
    

## <a name="to-view-services-for-a-user-account"></a>若要檢視服務的使用者帳戶

若要檢視所有使用者有權存取 Office 365 服務，請使用下列語法：
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

此範例會顯示使用者 BelindaN@litwareinc.com 具有存取服務。這會顯示指派至她帳戶的所有授權與相關聯的服務。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

本範例顯示使用者 BelindaN@litwareinc.com 有權存取的服務，從指派給其帳戶的第一個授權 (索引編號為 0) 開始。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

若要尋找已啟用或未啟用特定服務的所有授權使用者，使用下列語法：
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

這些範例使用下列資訊：
  
- 提供我們感興趣的 Office 365 服務的存取授權已指派給 （索引編號為 0） 的所有使用者的第一個授權。
    
- 我們感興趣的 Office 365 服務是 Skype 商務 Online 與 Exchange Online。相關聯的授權方案授權，Skype 商務 online 是 6 列出的服務 （索引編號為 5），與 Exchange Online 是 9th 服務列出 （索引編號為 8）。
    
此範例會傳回所有已獲授權的商務 Online 與 Exchange Online Skype 所啟用的使用者。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

此範例會傳回所有已獲授權的使用者未啟用 Skype 商務 Online 或 Exchange Online。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

若要檢視已被指派*多個授權*之使用者的所有服務，請使用下列語法：

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>另請參閱

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 移除使用者帳戶中的授權](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [ConvertTo Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [選取物件](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]