---
title: "將角色指派給 Office 365 powershell 的使用者帳戶"
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
- DecEntMigration
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "摘要： 使用 Office 365 PowerShell 並新增 MsolRoleMember cmdlet 來為使用者帳戶指派的角色。"
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>將角色指派給 Office 365 powershell 的使用者帳戶

 **摘要：**使用 Office 365 PowerShell 和**新增 MsolRoleMember**指令程式來為使用者帳戶指派的角色。
  
您可以快速又輕鬆地將角色指派使用 Office 365 PowerShell 所識別的使用者帳戶的顯示名稱及角色名稱的使用者帳戶。
  
## <a name="before-you-begin"></a>開始之前

本主題中的程序要求您重新連線至 Office 365 PowerShell 使用的全域管理員帳戶。指示，請參閱[Connect to Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
## <a name="for-a-single-role-change"></a>如需單一角色變更

決定下列項目：
  
- 您想要設定使用者帳戶。
    
    若要指定的使用者帳戶，您必須判斷其顯示名稱。若要取得的完整清單的帳戶，使用此命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出您的使用者帳戶，以顯示名稱] 中，一次一個畫面來顯示名稱。您可以使用**其中**指令程式來篩選少量的清單。以下是範例：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出只有其顯示名稱開頭為"John"的使用者帳戶。
    
- 您要指派的角色。
    
    若要顯示您可以將指派給使用者帳戶的可用角色清單，請使用此命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

一旦您已決定帳戶的顯示名稱和角色的名稱，使用這些命令將角色指派給帳戶：
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

命令複製並貼入 [記事本]。**$DispName**和**$roleName**變數，將說明文字取代其值、 移除\<和 > 字元和離開括住。複製已修改的行並將它們貼到您的 Windows Azure Active Directory Module for Windows PowerShell 視窗執行它們。或者，您可以使用 Windows PowerShell 整合式指令碼環境 (ISE)。
  
以下是一組完整的命令的範例：
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>是否有多個角色變更

決定下列項目：
  
- 哪些使用者帳戶新增您要設定。
    
    若要指定的使用者帳戶，您必須判斷其顯示名稱。若要取得的帳戶，請使用此命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出所有使用者帳戶，以顯示名稱] 中，一次一個畫面來顯示名稱。您可以使用**其中**指令程式來篩選少量的清單。以下是範例：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出只有其顯示名稱開頭為"John"的使用者帳戶。
    
- 您要指派給每個使用者帳戶的角色。
    
    若要顯示您可以將指派給使用者帳戶的可用角色清單，請使用此命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

接下來，建立內含 DisplayName 和角色逗點分隔值 (CSV) 的文字檔案名稱的欄位。以下是範例：
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

接下來，填入 CSV 檔案的位置與在 PowerShell 命令提示字元中執行所產生的命令。
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>See also

#### 

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
#### 

[新增 MsolRoleMember](https://msdn.microsoft.com/library/dn194120.aspx)

