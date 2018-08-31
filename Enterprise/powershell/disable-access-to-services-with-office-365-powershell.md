---
title: 使用 Office 365 PowerShell 停用服務存取權
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/20/2018
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
description: 說明如何使用 Office 365 PowerShell 來停用組織中使用者的 Office 365 服務存取權。
ms.openlocfilehash: d65308746ac5c2b60f4749588455fa66471069e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914988"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>使用 Office 365 PowerShell 停用服務存取權

**摘要：** 說明如何使用 Office 365 PowerShell 來停用組織中使用者的 Office 365 服務存取權。
  
當 Office 365 帳戶已指派授權的授權方案時、 Office 365 服務是供使用者從該授權。不過，您可以控制使用者可以存取 Office 365 服務。例如，即使授權可讓 SharePoint Online 服務的權限，您可以停用來加以存取。您可以使用 Office 365 PowerShell 停用的存取權的服務之特定的授權方案的任何數字：

- 個別帳戶。
    
- 一組帳戶。
    
- 您組織中的所有帳戶。
    
## <a name="before-you-begin"></a>開始之前
<a name="RTT"> </a>

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 您可以使用**Get-msolaccountsku**指令程式來檢視您可用的授權方案，以及這些計劃中可用的 Office 365 服務。如需詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。
    
- 若要查看前後本主題中的程序的結果，請參閱[檢視帳戶授權及服務的詳細資訊與 Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md)。
    
- PowerShell 指令碼是可用的可本主題所述的程序。主要是針對指令碼可讓您檢視和停用 Office 365 組織中包括 Sway 服務。如需詳細資訊，請參閱 ＜[停用 Office 365 powershell Sway 存取](disable-access-to-sway-with-office-365-powershell.md)。
    
- 如果您使用**Get-msoluser** cmdlet 而不需使用的_所有_參數時，會傳回第一個 500 的使用者帳戶。
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>停用特定的授權方案之特定使用者的特定 Office 365 服務
  
若要停用一組特定的 Office 365 服務之使用者的特定的授權方案，請執行下列步驟：
  
1. 識別授權的計劃中的非預期的服務使用下列語法：
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    下列範例會建立名為授權計劃中停用的 Office Online 和 SharePoint Online 服務**LicenseOptions**物件`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 對一或多位使用者使用步驟 1 的 **LicenseOptions** 物件。
    
  - 若要建立已停用服務的新帳戶，請使用下列語法：
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    下列範例會建立新帳戶的 Allie Bellew 指派授權並停用 [步驟 1 中所述的服務。
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    如需在 Office 365 PowerShell 中建立使用者帳戶的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)。
    
  - 若要停用現有授權使用者的服務，請使用下列語法：
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    本範例會停用使用者 BelindaN@litwareinc.com 的服務。
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - 若要停用的所有現有的授權使用者在步驟 1 中所述的服務，指定您的 Office 365 計劃中的**Get-msolaccountsku**指令程式 （例如**litwareinc: enterprisepack**)，顯示名稱，然後執行下列命令：
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - 若要為一組現有的使用者停用服務，請使用下列其中一種方法來識別使用者：
    
  - **篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    下列範例會停用使用者在美國銷售部門中的服務。
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **使用特定帳戶的清單**若要這樣做，執行下列步驟：
    
1. 建立一個文字檔，其中每一行上都包含一個帳戶，如下所示：
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    在此範例中的文字檔案是 c:\\我的文件\\Accounts.txt。
    
2. 執行下列命令：
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

如果您要停用的多個授權方案的服務存取權，重複上述的指示確保每種授權計劃：

- 使用者帳戶已指派授權方案。
- 若要停用服務都可以在授權方案。

當您要指派它們至授權計劃停用 Office 365 服務的使用者，請參閱 ＜[停用時指派使用者授權的服務存取權](disable-access-to-services-while-assigning-user-licenses.md)。


## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？
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
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-msolaccountsku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [新 MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

