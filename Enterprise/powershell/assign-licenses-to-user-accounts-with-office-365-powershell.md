---
title: 使用 Office 365 PowerShell 指派授權至使用者帳戶
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651177"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 指派授權至使用者帳戶

**摘要：** 說明如何使用 Office 365 PowerShell 指派給未授權使用者的 Office 365 授權。
  
使用者無法使用任何 Office 365 服務之前其帳戶已指派授權的授權方案。您可以使用 Office 365 PowerShell 快速地將授權指派給未授權的帳戶。 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下來，列出您使用此命令的租用戶授權計劃。

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下來，取得您要新增的授權，又稱為使用者主體名稱 (UPN) 的帳戶登入名稱。

最後，指定的使用者登入名稱和授權計劃名稱並執行下列命令。

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

執行**Get-msolaccountsku**命令來檢視您組織中每個計劃中可用的授權方案和可用授權數量。每個計劃中的可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。如需授權方案、 授權及服務的詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。
    
若要在組織中尋找未授權的帳戶，請執行此命令。

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
您只可以將授權指派給**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2 國家/地區碼的使用者帳戶。例如，我們美國、 和法國的 FR。某些 Office 365 服務都無法提供在某些國家/地區。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
若要尋找沒有**UsageLocation**值的帳戶，請執行此命令。

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

若要設定**UsageLocation**值帳戶上，執行此命令。

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

例如：

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
如果您使用 **Get-MsolUser** Cmdlet，而不使用 **-All**參數，則只會傳回前 500 個帳戶。

### <a name="assigning-licenses-to-user-accounts"></a>將授權指派給使用者帳戶
    
若要將授權指派給使用者，請在 Office 365 PowerShell 中使用下列命令。
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

此範例會將授權指派從**litwareinc: enterprisepack** (Office 365 企業版 E3) 授權授權的使用者**belindan@litwareinc.com**計劃：
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要將授權指派給未授權使用者，執行此命令。
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>您不能指派給使用者的多個授權從相同的授權方案。如果您沒有足夠可用的授權，授權指派給使用者他們正在可用授權執行之前**Get-msoluser** cmdlet 所傳回的順序。
>

此範例會將授權從**litwareinc: enterprisepack** (Office 365 企業版 E3) 的授權方案指派給未授權的所有使用者：
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

此範例會將這些相同的授權指派給未授權使用者在美國銷售部門中：
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>第一次使用 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
