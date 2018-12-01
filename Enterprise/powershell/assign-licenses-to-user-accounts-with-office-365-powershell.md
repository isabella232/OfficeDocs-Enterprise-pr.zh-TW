---
title: 使用 Office 365 PowerShell 指派授權至使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123290"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 指派授權至使用者帳戶

**摘要：** 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。
  
授權 Office 365 中的使用者帳戶很重要，因為使用者無法使用任何 Office 365 服務之前已授權其帳戶。您可以使用 Office 365 PowerShell 有效率地將授權指派給未授權的帳戶，特別是多個帳戶。 

## <a name="before-you-begin"></a>開始之前
<a name="RTT"> </a>

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 使用**Get-msolaccountsku**指令程式來檢視您組織中每個計劃中可用的授權方案和可用授權數量。每個計劃中的可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。如需授權方案、 授權及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要在組織中尋找未授權的帳戶，請執行命令`Get-MsolUser -All -UnlicensedUsersOnly`
    
- 您只能指派授權給**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2 國家/地區碼的使用者帳戶。例如，我們美國、 和法國的 FR。某些 Office 365 服務都無法提供在某些國家/地區。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
    若要尋找沒有**UsageLocation**值的帳戶，請執行命令`Get-MsolUser -All | where {$_.UsageLocation -eq $null}`。若帳戶上設定**UsageLocation**值，使用語法`Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`。例如， `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。
    
- 如果您使用**Get-msoluser** cmdlet 而不需使用`-All`參數，傳回前 500 的帳戶。

## <a name="assigning-licenses-to-user-accounts"></a>將授權指派給使用者帳戶
    
若要將授權指派給使用者，請在 Office 365 PowerShell 中使用下列語法：
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

此範例會將指定的授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 給未授權使用者的授權方案`belindan@litwareinc.com`。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要將授權指派給多位未經授權的使用者，請使用下列語法：
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **附註**
  
- 您無法將多個授權指派給相同授權計劃中的使用者。
    
- 如果您沒有足夠的可用授權，則會依 **Get-MsolUser** Cmdlet 傳回授權的順序，將授權指派給使用者，直到可用的授權用完為止。
    
本範例會將指派授權從`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 所有未授權使用者的授權方案。
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

本範例會將相同的授權指派給美國境內銷售部門中未經授權的使用者。
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>第一次使用 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另請參閱
<a name="SeeAlso"> </a>

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
- [刪除並還原的使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [封鎖的使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [移除使用者帳戶的授權](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [選取物件](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

