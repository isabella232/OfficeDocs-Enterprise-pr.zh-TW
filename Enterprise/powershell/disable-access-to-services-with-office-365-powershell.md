---
title: 使用 Office 365 PowerShell 停用服務存取權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: 使用 Office 365 PowerShell 停用使用者的 Office 365 服務存取權。
ms.openlocfilehash: 0f2c603edd624c9d53a28b37c1c9795bad05ec0f
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001816"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 停用服務存取權

**摘要：** 說明如何使用 Office 365 PowerShell 停用您組織中的使用者的 Office 365 服務存取權。
  
Office 365 帳戶授權計劃指派授權，Office 365 服務都可供使用者從該授權。 不過，您可以控制使用者可以存取 Office 365 服務。 例如，即使授權允許存取 SharePoint Online 服務，您可以停用對它的存取。 您可以使用 PowerShell 來停用的存取權的服務特定的授權計劃的任何數字：

- 個別帳戶。
    
- 一組帳戶。
    
- 您組織中的所有帳戶。

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

若要檢視可用授權計劃，也稱為 AccountSkuIds，接下來，使用此命令：

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

如需詳細資訊，請參閱[檢視授權與服務的 Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md)。
    
若要查看前後本主題中的程序的結果，請參閱 <<c0>檢視帳戶授權與服務詳細資料與 Office 365 PowerShell。
    
PowerShell 指令碼可供使用，會自動執行本主題中所述的程序。 具體而言，指令碼可讓您檢視及停用您 Office 365 組織，包括 Sway 中的服務。 如需詳細資訊，請參閱[Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)。
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>停用特定的 Office 365 服務，針對特定使用者的特定的授權計劃
  
若要停用一組特定的使用者特定授權方案的 Office 365 服務，請執行下列步驟：
  
1. 使用下列語法，不需要的服務識別授權計劃中：
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  下列範例會建立**LicenseOptions**物件，以停用的 Office Online 和 SharePoint Online 服務中名為授權計劃`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 對一或多位使用者使用步驟 1 的 **LicenseOptions** 物件。
    
  - 若要建立已停用服務的新帳戶，請使用下列語法：
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  下列範例的指派授權及停用步驟 1 所述服務的 Allie Bellew 建立新的帳戶。
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱 <<c0>使用 Office 365 PowerShell 建立使用者帳戶。
    
  - 若要停用現有授權使用者的服務，請使用下列語法：
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  本範例會停用使用者 BelindaN@litwareinc.com 的服務。
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - 若要停用所有現有經授權使用者在步驟 1 中所述的服務，指定從**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack**)，顯示 Office 365 計劃的名稱，然後執行下列命令：
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  如果您使用**Get-msoluser** cmdlet，而不使用_All_參數，會傳回的第一個 500 的使用者帳戶。


  - 若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：
    
  - **篩選根據現有的帳戶屬性的帳戶**若要這麼做，請使用下列語法：
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  下列範例會停用在美國境內銷售部門中的使用者的服務。
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **使用特定帳戶清單**若要這麼做，請執行下列步驟：
    
1. 建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  在這個範例中，文字檔為 c:\\我的文件\\Accounts.txt。
    
2. 執行下列命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

如果您想要停用的多個授權計劃的服務存取權，重複上述指示每個授權計劃，確保：

- 使用者帳戶已指派授權計劃。
- 若要停用服務可用授權計劃中。

若您將它們指派給授權計劃停用使用者的 Office 365 服務，請參閱[停用時指派使用者授權的服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。


## <a name="new-to-office-365"></a>第一次使用 Office 365？
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>另請參閱
<a name="SeeAlso"> </a>

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
