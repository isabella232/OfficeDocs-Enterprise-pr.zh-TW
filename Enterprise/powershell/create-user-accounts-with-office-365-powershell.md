---
title: 使用 Office 365 PowerShell 建立使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 了解如何使用 Office 365 PowerShell 在 Office 365 中建立使用者帳戶。
ms.openlocfilehash: b69e0afa6177f29ed2abe18be39f5db08c9f5e75
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072225"
---
# <a name="create-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 建立使用者帳戶

您可以使用 Office 365 PowerShell 有效率地建立使用者帳戶 (尤其是多個使用者帳戶時)。當您在 Office 365 PowerShell 中建立使用者帳戶時，一律需要某些帳戶屬性。其他屬性不一定用於建立帳戶，但卻很重要。下表將說明這些屬性：
  
|**屬性名稱**|**必要？**|**描述**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |是  <br/> |這是 Office 365 服務中使用的顯示名稱。例如，Caleb Sills。  <br/> |
|**UserPrincipalName** <br/> |是  <br/> |這是用來登入 Office 365 服務的帳戶名稱。例如，CalebS@contoso.onmicrosoft.com。  <br/> |
|**FirstName** <br/> |否  <br/> ||
|**LastName** <br/> |否  <br/> ||
|**LicenseAssignment** <br/> |否  <br/> |這是從中將可用的授權指派給使用者帳戶的授權計劃 (也稱為 Office 365 計劃或 SKU)。授權定義帳戶可用的 Office 365 服務。當您建立帳戶時，您不必將授權指派給使用者，但帳戶需要授權才能存取 Office 365 服務。建立使用者帳戶之後，您有 30 天的時間進行使用者帳戶授權。 |
|**Password** <br/> |否  <br/> | 如果您未指定密碼，則會指派隨機密碼給使用者帳戶，並可在命令結果中看見此密碼。如果您指定密碼，該密碼必須是下列任三種類型的 8 到 16 個 ASCII 文字：小寫字母、大寫字母、數字和符號。 <br/> |
|**UsageLocation** <br/> |否  <br/> |這是有效的 ISO 3166-1 alpha-2 國碼。例如，US 代表美國、FR 代表法國。請務必提供此值，因為某些 Office 365 服務不適用於某些國家/地區，所以您無法將授權指派給使用者帳戶 (除非帳戶已設定此值)。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。<br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

連接之後，使用下列語法來建立個別帳戶：
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

本範例會為名為 Caleb Sills 的美國使用者建立帳戶：
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

### <a name="create-an-individual-user-account"></a>建立個別使用者帳戶

若要建立個別帳戶，請使用下列語法：
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

若要列出可用的授權方案名稱，請使用此命令：

````powershell
Get-MsolAccountSku
````

本範例會建立一個名為 Caleb Sills 的美國使用者帳戶，並指派 `contoso:ENTERPRISEPACK` (Office 365 企業版 E3) 授權方案的授權。
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>建立多個使用者帳戶

1. 建立包含必要使用者帳戶資訊的逗點分隔值 (CSV) 檔案。例如：
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>CSV 檔第一列中的欄名稱及其順序並無任何限定，但請確定檔案其餘部分中的資料符合欄名稱之順序，並將欄名稱使用於 Office 365 PowerShell 命令中的參數值。
    
2. 使用下列語法：
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

本範例會從名為 C:\My Documents\NewAccounts.csv 的檔案建立使用者帳戶，並將結果記錄在名為 C:\My Documents\NewAccountResults.csv 的檔案中
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. 檢閱輸出檔以查看結果。我們並未指定密碼，所以會在輸出檔中看到 Office 365 產生的隨機密碼。
    
## <a name="see-also"></a>另請參閱

[管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
