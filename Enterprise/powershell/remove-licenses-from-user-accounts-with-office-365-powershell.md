---
title: "使用 Office 365 PowerShell 移除使用者帳戶中的授權"
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
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
- DecEntMigration
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "說明如何使用 Office 365 PowerShell 移除先前已指派給使用者的 Office 365 授權。"
ms.openlocfilehash: 90cae603a7a7cda0b7318571d3eb045f750fd58d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>使用 Office 365 PowerShell 移除使用者帳戶中的授權

**摘要：**說明如何使用 Office 365 PowerShell 移除先前已指派給使用者的 Office 365 授權。
  
## <a name="before-you-begin"></a>開始之前

- 本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
    
- 若要檢視您的組織的授權的計劃 ( **AccountSkuID** ) 資訊，請參閱下列主題：
    
  - [使用 Office 365 PowerShell 檢視授權與服務](view-licenses-and-services-with-office-365-powershell.md)
    
  - [使用 Office 365 PowerShell 檢視帳戶授權與服務詳細資料](view-account-license-and-service-details-with-office-365-powershell.md)
    
- 如果您使用**Get-msoluser** cmdlet 而不需使用_-所有_參數，傳回前 500 的帳戶。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡短版本 (不含說明的指示)
<a name="ShortVersion"> </a>

本節僅呈現程序，但不提供詳盡或多餘的說明。如果您有任何問題或需要詳細資訊，您可以閱讀本主題的其餘部分。
  
若要移除現有使用者帳戶中的授權，使用下列語法：
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權與使用者帳戶 BelindaN@litwareinc.com。
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

若要移除現有的經授權使用者群組的授權，使用下列方法之一：
  
- **篩選根據現有的帳戶屬性的帳戶**為達成此目的，使用下列語法：
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從所有 accounts 在美國 「 業務 」 部門中的使用者。
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **使用特定帳戶的清單**若要這樣做，執行下列步驟：
    
1. 建立一個每一行一個帳戶的文字檔，像這樣：
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 使用下列語法：
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

此範例會移除`litwareinc:ENTERPRISEPACK`從文字檔案 C:\My Documents\Accounts.txt 中所定義的使用者帳戶 (Office 365 企業版 E3) 授權。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

若要移除所有現有使用者帳戶中的授權，使用下列語法：
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

此範例會移除`litwareinc:ENTERPRISEPACK`(Office 365 企業版 E3) 授權從現有的所有授權的使用者帳戶。
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>冗長版本 (包含詳細說明的指示)
<a name="LongVersion"> </a>

不會持續永久，並包含 Office 365 授權： 提前或更新版本中，會有當您需要移除授權的使用者帳戶的時間。使用者離開 ； 在將要的也許也許使用者不再需要授權;也許-，有做了明顯改善任意數量的原因為何您可能會想要移除的使用者授權。
  
我們任何進一步請務必注意移除授權需要，以及之前，請移除授權： 停用所有服務的意涵是同一個兩回事移除授權。例如，假設我們使用所有適用的 Office 365 授權; 向上換句話說，我們有無授權提供也不會收到。您決定要遵循中用以停用所有服務之後，Belinda Newman 的帳戶上的 [[停都用 Office 365 powershell 的服務存取權](disable-access-to-services-with-office-365-powershell.md)的程序。我們執行動作，多少授權的後將我們會提供對我們吗？這是右： 零。是，該主題中的程序就會*停用*Belinda 的授權上的所有服務，但不是都會停用 （亦即刪除） 本身的授權。授權仍會有效，而且它仍然會指派給 Belinda Newman。她只是將無法存取任何 Office 365 服務使用的授權。
  
與這很重要： 如果您想要移除使用者的授權必須實際中*移除*授權。停用所有服務會防止使用者登入 Office 365 中，但它不會釋出其授權。如果您想要取回授權是目前指派給使用者您需要執行此的話真正移除先前已指派給 Belinda 的授權會使用_RemoveLicenses_參數的命令如下的命令：
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

執行命令並 Belinda Newman 就不再被授權使用 Office 365。
  
> [!NOTE]
> 如您所見，當您使用_RemoveLicenses_參數，您需要指定要移除授權的名稱。如果您不確定哪一個授權方案用來將授權指派給使用者，請直接執行這類命令：`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
若要驗證授權已確實移除，請使用 Get-MsolUser 檢查使用者帳戶：
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

如果一切皆依計劃，Belinda 的**isLicensed**屬性現在將`False`：
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

釋放授權的另一種方式是由刪除的使用者帳戶。如需詳細資訊，請參閱[刪除並還原與 Office 365 PowerShell 的使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)。
  
## <a name="see-also"></a>另請參閱

請參閱下列有關透過 Office 365 PowerShell 管理使用者的其他主題：
  
- [使用 Office 365 PowerShell 建立使用者帳戶](create-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 刪除及還原使用者帳戶](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 封鎖使用者帳戶](block-user-accounts-with-office-365-powershell.md)
    
- [使用 Office 365 PowerShell 指派授權至使用者帳戶](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：
  
- [Get-content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-msoluserlicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [Foreach-object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>初次使用 Office 365 嗎？

||
|:-----|
|![簡短 LinkedIn 學習圖示](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png)**新增至 Office 365？**        [Office 365 系統管理員及 IT 專業人員](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)，傳送給您的 LinkedIn 學習探索免費的視訊課程。 |
   

