---
title: "停用時指派使用者授權的服務存取權"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "了解如何將授權指派給使用者帳戶及使用 Office 365 PowerShell 的同時停用特定的服務計劃。"
ms.openlocfilehash: 96ce12f811ee147a92da6b6928c2f6e3391c9b1f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>停用時指派使用者授權的服務存取權

**摘要：** 了解如何將授權指派給使用者帳戶及使用 Office 365 PowerShell 的同時停用特定的服務計劃。
  
Office 365 訂閱隨附的個別服務的服務計劃。Office 365 系統管理員通常需要將授權指派給使用者時，停用特定計劃。使用本文中的指示，您可以將 Office 365 授權指派時停用特定的服務計劃使用 PowerShell for 個別的使用者帳戶或多個使用者帳戶。
  
> [!NOTE]
> 本文根據 Siddhartha Parmar，Microsoft 支援呈報工程師的工作。 
  
## <a name="before-you-begin"></a>開始之前

本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>收集資訊訂閱及服務計劃

執行此命令來查看目前訂閱：
  
```
Get-MsolAccountSku
```

在顯示`Get-MsolAccountSku`命令：
  
- **AccountSkuId**是您組織中的訂閱\<OrganizationName >:\<訂閱 > 格式。\<OrganizationName > 為您提供當您在 Office 365 中註冊並為您的組織是唯一的值。\<訂閱 > 值是針對特定的訂閱。例如，如 litwareinc: enterprisepack、 組織名稱是 litwareinc，而訂閱名稱是 ENTERPRISEPACK (Office 365 企業版 E3)。
    
- **ActiveUnits**是您已購買訂閱的授權數。
    
- **WarningUnits**是尚未已更新，並將期限 30 天寬限期訂閱中的授權數。
    
- **ConsumedUnits**是已指派給使用者訂閱授權數目。
    
請注意包含您想要授權的使用者在 Office 365 訂閱 AccountSkuId。此外，請確定有足夠授權指派給指派 （減去從**ActiveUnits** **ConsumedUnits** ）。
  
接下來，執行此命令以查看關於所有訂閱中可用的 Office 365 服務計劃的詳細資料：
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

從這個命令的顯示，判斷您想要停用時指派授權給使用者的服務計劃。
  
以下為部分服務計劃和其對應的 Office 365 服務的清單。
  
|**服務計劃**|**描述**|
|:-----|:-----|
|SWAY  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Office 365 的行動裝置管理  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |Azure 版權管理 (RMS)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office Professional Plus  <br/> |
|MCOSTANDARD  <br/> |商務用 Skype Online  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Exchange Online Plan 2  <br/> |
   
既然有 AccountSkuId 及停用的服務計劃，您可以指派個別使用者或多個使用者的授權。
  
## <a name="for-a-single-user"></a>單一使用者

單一使用者的填滿中的使用者帳戶、 AccountSkuId、 和服務計劃清單停用或移除的說明文字的使用者主體名稱和\<和 > 字元。然後，在 PowerShell 命令提示字元執行所產生的命令。
  
```
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

以下是用於 contoso:ENTERPRISEPACK 授權，名為 belindan@contoso.com、 帳戶範例命令封鎖且以停用的服務計劃 RMS_S_ENTERPRISE、 SWAY、 INTUNE_O365 及 YAMMER_ENTERPRISE：
  
```
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

## <a name="for-multiple-users"></a>多個使用者

若要執行這項管理工作的多個使用者，建立包含 UserPrincipalName 和 UsageLocation 欄位的逗號分隔值 (CSV) 文字檔案。以下是範例：
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

接下來，填入的輸入和輸出 CSV 檔案、 SKU 識別碼的帳戶及服務計劃來停用清單的位置和 PowerShell 命令提示字元執行所產生的命令。
  
```
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

此 PowerShell 命令區塊：
  
- 會顯示每個使用者的使用者主體名稱。
    
- 將自訂的授權指派給每位使用者。
    
- 建立已處理的所有使用者的 CSV 檔案並顯示其授權狀態。
    
## <a name="see-also"></a>另請參閱

#### 

[使用 Office 365 PowerShell 停用服務存取權](disable-access-to-services-with-office-365-powershell.md)
  
[停用 Sway 與 Office 365 PowerShell 存取](disable-access-to-sway-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)

