---
title: 使用 Office 365 PowerShell 停用服務存取權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: 使用 Office 365 PowerShell 來停用使用者的 Office 365 服務存取權。
ms.openlocfilehash: e0a486bbe3a783443fc25cbadff61721761a0028
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004646"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 停用服務存取權

當 Office 365 帳戶指派授權方案的授權時，使用者就可以從該授權取得 Office 365 服務。 不過，您可以控制使用者可以存取的 Office 365 服務。 例如，即使授權允許存取 SharePoint 線上服務，您還是可以停用存取權。 您可以使用 PowerShell 針對特定授權方案停用任何數目的服務存取權：

- 個別帳戶。
- 一組帳戶。
- 您組織中的所有帳戶。

>[!Note]
>有 Office 365 服務相依性，可防止當其他服務依賴于指定的服務時停用此服務。
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

接下來，使用此命令來查看可用的授權方案，也稱為 AccountSkuIds：

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

如需詳細資訊，請參閱[使用 Office 365 PowerShell 查看授權和服務](view-licenses-and-services-with-office-365-powershell.md)。
    
若要查看本主題中的程式前後的結果，請參閱[使用 Office 365 PowerShell 查看帳戶授權與服務詳細資料](view-account-license-and-service-details-with-office-365-powershell.md)。
    
PowerShell 指令碼可供使用，會自動執行本主題中所述的程序。 具體說來，此腳本可讓您在 Office 365 組織中查看及停用服務，包括 Sway。 如需詳細資訊，請參閱[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>針對特定授權方案停用特定使用者的特定 Office 365 服務
  
若要針對特定授權方案停用一組特定的 Office 365 服務，請執行下列步驟：
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a>步驟1：使用下列語法識別授權方案中不想要的服務：
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

下列範例會建立**LicenseOptions**物件，以停用名為`litwareinc:ENTERPRISEPACK` （Office 365 Enterprise E3）的授權方案中的 Office 和 SharePoint 線上服務。
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>步驟2：在一或多個使用者上使用步驟1中的**LicenseOptions**物件。
    
若要建立已停用服務的新帳戶，請使用下列語法：
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

下列範例會為 Allie Bellew 建立新的帳戶，以指派授權並停用步驟1中所述的服務。
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱[Create user accounts With office 365 PowerShell](create-user-accounts-with-office-365-powershell.md)。
    
若要停用現有授權使用者的服務，請使用下列語法：
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

本範例會停用使用者 BelindaN@litwareinc.com 的服務。
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

若要停用步驟1中所述的所有現有授權使用者的服務，請從**Get-MsolAccountSku** Cmdlet 的顯示（例如**litwareinc:ENTERPRISEPACK**）中指定您的 Office 365 方案名稱，然後執行下列命令：
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 如果您使用**Get-MsolUser** Cmdlet 但未使用_All_參數，則只會傳回第一個500使用者帳戶。

若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：
    
**方法1。根據現有的帳戶屬性來篩選帳戶** 

若要這麼做，使用下列語法：
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

下列範例會停用美國地區的銷售部門中的使用者服務。
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**方法2：使用特定帳戶的清單** 

若要這樣做，請執行下列步驟：
    
1. 建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  在此範例中，文字檔是 C：\\My Documents\\，.txt。
    
2. 執行下列命令：
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

如果您想要針對多個授權方案停用服務存取權，請針對每個授權方案重複上述指示，以確保：

- 已指派授權方案的使用者帳戶。
- 授權方案提供要停用的服務。

若要在指派使用者授權時，為使用者停用 Office 365 服務，請參閱在[指派使用者授權時停用服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。


## <a name="see-also"></a>另請參閱

[使用 Office 365 管理使用者帳戶、授權和群組 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
