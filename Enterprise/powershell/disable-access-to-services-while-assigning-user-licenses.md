---
title: 停用服務存取權，並指派使用者授權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: 瞭解如何使用 Office 365 PowerShell，將授權指派給使用者帳戶並同時停用特定服務方案。
ms.openlocfilehash: b1fcd8afd9f9fee5b249752821385cd888519a37
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009468"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>停用服務存取權，並指派使用者授權

Office 365 訂閱隨附個別服務的服務方案。 當您指派授權給使用者時，Office 365 系統管理員常常需要停用某些方案。 透過本文中的指示，您可以在使用個別使用者帳戶或多個使用者帳戶的 PowerShell 停用特定的服務方案時，指派 Office 365 授權。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

接下來，使用此命令列出租使用者的授權計畫。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

接下來，取得您想要新增授權的帳戶登入名稱，也稱為使用者主要名稱（UPN）。

接下來，編譯要啟用的服務清單。 如需授權方案（也稱為產品名稱）、其包含的服務方案及其對應的易記名稱的完整清單，請參閱[產品名稱和服務方案識別碼取得授權](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。

針對下列命令區塊，請填入使用者帳戶的使用者主要名稱、SKU 元件編號，以及要啟用及移除解說文字和\<及 > 字元的服務方案清單。 然後，在 PowerShell 命令提示字元中執行產生的命令。
  
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

接下來，執行下列命令以查看您目前的訂閱：
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

在 [顯示] `Get-MsolAccountSku`命令中：
  
- **AccountSkuId**是 OrganizationName>： \< \<訂閱> 格式中的組織訂閱。 \<OrganizationName> 是您在 Office 365 中登記時所提供的值，且對您的組織而言是唯一的。 \<訂閱> 值是針對特定訂閱。 例如，針對 litwareinc:ENTERPRISEPACK，組織名稱是 litwareinc，訂閱名稱是 ENTERPRISEPACK （Office 365 企業版 E3）。
    
- **ActiveUnits**為您為訂閱購買的授權數目。
    
- **WarningUnits**是尚未更新之訂閱中的授權數目，在30天的寬限期後會到期。
    
- **ConsumedUnits**是您為訂閱指派給使用者的授權數目。
    
請記下您的 Office 365 訂閱的 AccountSkuId，其中包含您想要授權的使用者。 此外，請確定有足夠的授權可指派（從**ActiveUnits**中減去**ConsumedUnits** ）。
  
接下來，執行此命令，以查看您所有訂閱中可用之 Office 365 服務方案的詳細資料：
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

在此命令顯示時，決定當您指派授權給使用者時，您想要停用的服務方案。
  
以下是服務方案及其對應的 Office 365 服務的部分清單。

下表顯示 Office 365 服務方案及其最常見服務的易記名稱。 您的服務方案清單可能不同。 
  
|**服務計劃**|**描述**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure 版權管理 (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |適用于企業的 Microsoft 365 應用程式 *（先前命名的 Office 365 ProPlus）*  <br/> |
| `MCOSTANDARD` <br/> |商務用 Skype Online  <br/> |
| `SHAREPOINTWAC` <br/> |辦公室   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
如需授權方案（也稱為產品名稱）、其包含的服務方案及其對應的易記名稱的完整清單，請參閱[產品名稱和服務方案識別碼取得授權](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)。
   
現在，您已具備要停用的 AccountSkuId 和服務方案，您可以將授權指派給個別使用者或多位使用者。
  
### <a name="for-a-single-user"></a>針對單一使用者

若為單一使用者，請填入使用者帳戶的使用者主要名稱、AccountSkuId，以及要停用的服務方案清單，並移除解說文字和\<及 > 字元。 然後，在 PowerShell 命令提示字元中執行產生的命令。
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

以下是名為 belindan@contoso.com 之帳戶的範例命令區塊，供 contoso:ENTERPRISEPACK 授權使用，且要停用的服務方案 RMS_S_ENTERPRISE、SWAY、INTUNE_O365 和 YAMMER_ENTERPRISE：
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>針對多個使用者

若要對多位使用者執行這項管理工作，請建立一個逗號分隔值（CSV）文字檔，其中包含 UserPrincipalName 及 UsageLocation 的欄位。 範例如下：
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

接下來，填入輸入和輸出 CSV 檔案的位置、帳戶 SKU 識別碼，以及要停用的服務方案清單，然後在 PowerShell 命令提示字元中執行產生的命令。
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

此 PowerShell 命令區塊：
  
- 顯示每位使用者的使用者主要名稱。
    
- 將自訂的授權指派給每個使用者。
    
- 會建立 CSV 檔案，其中包含所有已處理的使用者，並顯示其授權狀態。
    
## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 停用服務存取權](disable-access-to-services-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 停用 Sway 的存取權](disable-access-to-sway-with-office-365-powershell.md)
  
[使用 Office 365 管理使用者帳戶、授權和群組 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
