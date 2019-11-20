---
title: 停用服務存取權，並指派使用者授權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/27/2019
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 了解如何將授權指派給使用者帳戶，並在同時使用 Office 365 PowerShell 停用特定的服務計劃。
ms.openlocfilehash: 16e24a61aea1298b2c24a251d61c414c355dead7
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747655"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>停用服務存取權，並指派使用者授權

Office 365 訂閱隨附的個別服務的服務計劃。 Office 365 系統管理員通常需要將授權指派給使用者時，停用特定計劃。 透過本文中的指示，您可以同時停用特定的服務計劃使用 PowerShell 個別使用者帳戶或多個使用者帳戶指派 Office 365 授權。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下來，列出您的租用戶使用此命令的授權計劃。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下來，取得您想要新增的授權，也稱為使用者主體名稱 (UPN) 的帳戶登入名稱。

接下來，編譯若要啟用的服務清單。 為授權計劃 （也稱為產品名稱） 的完整清單，其包含的服務計劃和其對應的易記名稱，請參閱[產品名稱和授權的服務方案識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

對於下列的命令區塊，填妥中的使用者帳戶、 SKU 部分數字，以及服務計劃的清單來啟用及移除的說明文字 」 的使用者主體名稱和\<和 > 字元。 然後，在 PowerShell 命令提示字元執行產生的命令。
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

接著，執行此命令，以檢視您目前訂用帳戶：
  
```powershell
Get-MsolAccountSku
```

在顯示的`Get-MsolAccountSku`命令：
  
- **AccountSkuId**是您組織中的訂閱\<OrganizationName>:\<訂閱> 格式。 \<OrganizationName> 是您提供當您在 Office 365 中註冊，並為您的組織是唯一的值。 \<訂閱> 值是針對特定的訂閱。 例如，如 litwareinc: enterprisepack，組織名稱為 litwareinc，且訂閱名稱 ENTERPRISEPACK (Office 365 企業版 E3)。
    
- **Activeunits 作用**是您已購買訂閱的授權數目。
    
- **WarningUnits**是，您還沒有更新，並，將會在 30 天寬限期後過期的訂閱中的授權數目。
    
- **ConsumedUnits**是已指派給使用者的訂閱的授權數目。
    
請注意您 Office 365 訂用帳戶，包含您想要授權的使用者 AccountSkuId。 此外，請確定有足夠的授權可以指派 （由欄位刪減從**ActiveUnits** **ConsumedUnits** ）。
  
接著，執行此命令，以檢視有關您所有的訂閱中可用的 Office 365 服務計劃的詳細資料：
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

從顯示的以下命令，決定您想要指派授權給使用者時，停用哪些服務方案。
  
以下是服務計劃和其對應的 Office 365 服務的部分清單。

下表顯示 Office 365 服務計劃及最常見的服務的好記的名稱。 您的服務計劃清單可能會不同。 
  
|**服務計劃**|**描述**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 版權管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office 專業增強版  <br/> |
| `MCOSTANDARD` <br/> |商務用 Skype Online  <br/> |
| `SHAREPOINTWAC` <br/> |辦公室   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
為授權計劃 （也稱為產品名稱） 的完整清單，其包含的服務計劃和其對應的易記名稱，請參閱[產品名稱和授權的服務方案識別碼](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。
   
現在，您有 AccountSkuId 和停用服務計劃，您可以指派授權的個別使用者或多個使用者。
  
### <a name="for-a-single-user"></a>單一使用者

單一使用者，填入使用者主體名稱的使用者帳戶、 AccountSkuId 和服務計劃的清單來停用並移除的說明文字和\<和 > 字元。 然後，在 PowerShell 命令提示字元執行產生的命令。
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

以下是範例命令區塊，帳戶 belindan@contoso.com，一個用於名為 contoso: enterprisepack 的授權，而若要停用服務計劃為 RMS_S_ENTERPRISE、 SWAY，INTUNE_O365 和 YAMMER_ENTERPRISE:
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

### <a name="for-multiple-users"></a>多個使用者

若要執行這項管理工作的多個使用者，建立逗點分隔值 (CSV) 文字檔，其中包含 [UserPrincipalName 和 UsageLocation] 欄位。 範例如下：
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

接下來，填寫輸入和輸出 CSV 檔案、 SKU 識別碼的帳戶及服務計劃要停用，清單的位置，然後再執行 PowerShell 命令提示字元處的 [產生的命令。
  
```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

此 PowerShell 命令區塊：
  
- 會顯示每位使用者的使用者主體名稱。
    
- 將自訂的授權指派給每位使用者。
    
- 與已處理的所有使用者建立 CSV 檔案，並顯示其授權狀態。
    
## <a name="see-also"></a>請參閱

[使用 Office 365 PowerShell 停用服務存取權](disable-access-to-services-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 停用 Sway 的存取權](disable-access-to-sway-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)

