---
title: "使用 Office 365 PowerShell 建立使用者帳戶"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "了解如何使用 Office 365 PowerShell 在 Office 365 中建立使用者帳戶。"
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 建立使用者帳戶

**摘要：**了解如何使用 Office 365 PowerShell 在 Office 365 中建立使用者帳戶。
  
您可以使用 Office 365 PowerShell 有效率地建立使用者帳戶 (尤其是多個使用者帳戶時)。當您在 Office 365 PowerShell 中建立使用者帳戶時，一律需要某些帳戶屬性。其他屬性不一定用於建立帳戶，但卻很重要。下表將說明這些屬性：
  
****

|**屬性名稱**|**必要？**|**說明**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |是  <br/> |這是 Office 365 服務中使用的顯示名稱。例如，Caleb Sills。  <br/> |
|**UserPrincipalName** <br/> |是  <br/> |這是用來登入 Office 365 服務的帳戶名稱。例如，CalebS@contoso.onmicrosoft.com。  <br/> |
|**FirstName** <br/> |否  <br/> ||
|**LastName** <br/> |否  <br/> ||
|**LicenseAssignment** <br/> |否  <br/> |這是從中將可用的授權指派給使用者帳戶的授權計劃 (也稱為 Office 365 計劃或 SKU)。授權定義帳戶可用的 Office 365 服務。當您建立帳戶時，您不必將授權指派給使用者，但帳戶需要授權才能存取 Office 365 服務。建立使用者帳戶之後，您有 30 天的時間進行使用者帳戶授權。<br/> 若要檢視您組織中的授權方案 ( **AccountSkuId** ) 和可用授權使用**Get-msolaccountsku** cmdlet。如需詳細資訊，請參閱[檢視授權和 Office 365 powershell 的服務](view-licenses-and-services-with-office-365-powershell.md)。<br/> |
|**Password** <br/> |否  <br/> | 如果您未指定密碼，則會指派隨機密碼給使用者帳戶，並可在命令結果中看見此密碼。如果您指定密碼，該密碼必須符合下列複雜性需求： <br/>  8 到 16 個 ASCII 文字字元。 <br/>  下列任何三種類型中的字元：小寫字母、大寫字母、數字和符號。 <br/> |
|**UsageLocation** <br/> |否  <br/> |這是有效的 ISO 3166-1 alpha-2 國碼。例如，US 代表美國、FR 代表法國。請務必提供此值，因為某些 Office 365 服務不適用於某些國家/地區，所以您無法將授權指派給使用者帳戶 (除非帳戶已設定此值)。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。<br/> |
   
## <a name="before-you-begin"></a>開始之前

本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>使用 Office 365 PowerShell 建立個別使用者帳戶

若要建立個別帳戶，請使用下列語法：
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

本範例會為名為 Caleb Sills 的美國使用者建立帳戶，並從  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) 授權計劃指派授權。
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>使用 Office 365 PowerShell 建立多個使用者帳戶

1. 建立包含必要使用者帳戶資訊的逗點分隔值 (CSV) 檔案。例如：
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>資料行名稱及 CSV 檔案的第一列其順序是任意，但確定其餘的檔案中的資料會比對的欄名稱順序和 Office 365 PowerShell 命令中同時使用的參數值的欄名稱。
    
2. 使用下列語法：
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

本範例會從名為 C:\My Documents\NewAccounts.csv 的檔案建立使用者帳戶，並將結果記錄在名為 C:\My Documents\NewAccountResults.csv 的檔案中
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. 檢閱輸出檔以查看結果。我們並未指定密碼，所以輸出檔中看得到多個隨機產生的密碼。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>使用 Azure Active Directory V2 PowerShell 模組來建立個別使用者帳戶

若要使用 Azure Active Directory V2 PowerShell 模組中的**新增 AzureADUser**指令程式，您必須先連線至您的訂閱。指示，請參閱[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。
  
連接之後，使用下列語法來建立個別帳戶：
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

本範例會為名為 Caleb Sills 的美國使用者建立帳戶：
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>See also

請參閱下列有關管理 Office 365 PowerShell 與使用者的其他主題：
  
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 移除使用者帳戶中的授權](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [New-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Foreach-object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [新 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

