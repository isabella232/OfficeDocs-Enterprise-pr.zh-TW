---
title: 將授權指派給使用 Office 365 PowerShell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/26/2019
audience: Admin
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
search.appverid:
- MET150
description: 如何使用 Office 365 PowerShell 來將 Office 365 授權指派給未經授權的使用者。
ms.openlocfilehash: 8db03eb919547fd0664f8e71cf5f8eddd0f41e2e
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257452"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>將授權指派給使用 Office 365 PowerShell 的使用者帳戶

**摘要：** 如何使用 Office 365 PowerShell 來將 Office 365 授權指派給未經授權的使用者。
  
使用者無法使用任何 Office 365 服務，直到其帳戶具有已指派授權給授權計劃。 您可以使用 Office 365 PowerShell 來快速將授權指派給未經授權的帳戶。 

>[!Note]
>使用者帳戶必須被指派的位置。 您可以從 Microsoft 365 系統管理中心中的使用者帳戶的屬性或 PowerShell 來執行這項操作。
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下來，列出您的租用戶使用此命令的授權計劃。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下來，取得您想要新增的授權，也稱為使用者主體名稱 (UPN) 的帳戶登入名稱。

接下來，請確定的使用者帳戶擁有指派的使用狀況位置。

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

如果沒有指派未使用位置，您可以指派一個使用以下命令：

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

最後，指定使用者登入名稱及授權計劃名稱，並執行下列命令。

```powershell
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

執行**Get-msolaccountsku**命令，以檢視您組織中每個計劃可用的授權計劃與可用授權數量。 在每個方案可用授權數量是**ActiveUnits** - **WarningUnits** - **ConsumedUnits**。 如需有關授權方案、 授權及服務的詳細資訊，請參閱[檢視授權與服務的 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。

>[!Note]
>PowerShell 核心不支援的 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組和具有**Msol** cmdlet 在其名稱。 若要繼續使用這些 cmdlet，您必須從 Windows PowerShell 執行它們。
>

若要在組織中尋找未經授權的帳戶，請執行此命令。

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

您只可以將授權指派給使用者帳戶，已將**UsageLocation**屬性設定為有效的 ISO 3166-1 alpha-2http 國碼/地區碼。 例如，US 代表美國、FR 代表法國。 在某些國家/地區中，某些 Office 365 服務無法使用。 如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。
    
若要找出沒有**UsageLocation**值的帳戶，請執行此命令。

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

若要設定**UsageLocation**值帳戶，請執行此命令。

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

例如：

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
如果您使用 **Get-MsolUser** Cmdlet，而不使用 **-All**參數，則只會傳回前 500 個帳戶。

### <a name="assigning-licenses-to-user-accounts"></a>將授權指派給使用者帳戶
    
若要指派授權給使用者，請在 Office 365 PowerShell 中使用下列命令。
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

本範例會從**litwareinc: enterprisepack** (Office 365 企業版 E3) 授權計劃指派授權給未經授權的使用者**belindan\@litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

若要將授權指派給多位未經授權的使用者，請執行此命令。
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>您不能指派給使用者的多個授權從相同的授權計劃。 如果您沒有足夠的可用授權，授權指派給他們正在直到可用的授權用完**Get-msoluser** cmdlet 所傳回的順序中的使用者。
>

此範例會將授權從**litwareinc: enterprisepack** (Office 365 企業版 E3) 授權計劃指派給所有未經授權的使用者：
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

此範例會將相同的授權指派給在美國境內銷售部門中未經授權的使用者：
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>使用 PowerShell 的 Azure Active Directory 針對 Graph 模組，將使用者移至不同的訂閱 （授權計劃）

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
接下來，取得您想要的使用者帳戶登入名稱切換訂閱，也稱為使用者主體名稱 (UPN)。

接下來，列出您的租用戶使用此命令的訂閱 （授權方案）。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下來，列出的使用者帳戶目前已使用這些命令的訂閱。

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

識別訂閱使用者目前已 （從訂閱） 和使用者所要移動 （TO 訂閱） 訂閱。

最後，指定的 TO 和 FROM 訂閱名稱 （SKU 組件編號），並執行下列命令。

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

您可以確認這些命令的使用者帳戶的訂閱中的變更。

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="new-to-office-365"></a>第一次使用 Office 365？

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
