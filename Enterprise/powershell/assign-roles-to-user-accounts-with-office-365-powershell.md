---
title: 將角色指派給 Office 365 powershell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 摘要： 使用 Office 365 PowerShell 來指派角色給使用者帳戶。
ms.openlocfilehash: 78f2e08df6d46588b93dc217d0e16b7c3a350a88
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957704"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>將角色指派給 Office 365 powershell 的使用者帳戶

您可以快速且輕鬆地將角色指派給使用 Office 365 PowerShell 的使用者帳戶。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)使用全域系統管理員帳戶。
  
接下來，決定您想要新增至角色的使用者帳戶登入名稱 (範例： fredsm@contoso.com)。 這是第也稱為使用者主體名稱 (UPN)。

接下來，決定該角色的名稱。 使用此[清單中的 Azure Active Directory 中的系統管理員角色權限](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。

>[!Note]
>請注意附註在本文中。 某些角色名稱是不同的 Azure AD PowerShell。 例如，在 Microsoft 365 系統管理中心中的 「 SharePoint 管理員 」 角色是用於 Azure AD PowerShell 名為 「 SharePoint 服務系統管理員 」。
>

接下來，填寫，登入和角色的名稱，並執行下列命令。
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

以下是一組完整的命令的範例：
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

若要顯示特定角色的使用者名稱的清單，請使用以下命令。

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)使用全域系統管理員帳戶。
  
### <a name="for-a-single-role-change"></a>單一角色變更

決定下列項目：
  
- 您想要設定使用者帳戶。
    
    若要指定的使用者帳戶，您必須決定其顯示名稱。 若要取得的完整清單的帳戶，請使用此命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出您的使用者帳戶，以顯示名稱，一次一個畫面排序顯示名稱。 您可以使用**其中**指令程式來篩選清單，以較小的設定。 範例如下：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出僅為其顯示名稱的開頭 「 百勝 」 的使用者帳戶。
    
- 您要指派的角色。
    
    若要顯示可用的角色，您可以指派給使用者帳戶的清單，請使用此命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

一旦您判斷帳戶的顯示名稱和角色的名稱，請使用以下命令來指派角色給該帳戶：
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

複製命令，並將它們貼到 [記事本]。 **$DispName**和 **$roleName**變數，將描述文字取代其值，請移除\<和 > 字元，並將保留引號。 複製已修改的行，並將它們貼到您的 Windows Azure Active Directory 模組的 Windows PowerShell 視窗，並執行。 或者，您可以使用 Windows PowerShell 整合式指令碼環境 (ISE)。
  
以下是一組完整的命令的範例：
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a>多個角色變更

決定下列項目：
  
- 哪一個使用者帳戶，您想要設定。
    
    若要指定的使用者帳戶，您必須決定其顯示名稱。 若要取得清單的帳戶，請使用此命令：
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出所有使用者帳戶，以顯示名稱，一次一個畫面排序顯示名稱。 您可以使用**其中**指令程式來篩選清單，以較小的設定。 範例如下：
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    此命令會列出僅為其顯示名稱的開頭 「 百勝 」 的使用者帳戶。
    
- 您想要指派給每個使用者帳戶哪些角色。
    
    若要顯示可用的角色，您可以指派給使用者帳戶的清單，請使用此命令：
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

接下來，建立具有 DisplayName 和角色逗點分隔值 (CSV) 的文字檔案名稱的欄位。 範例如下：
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

接下來，填寫 CSV 檔案的位置，並在 PowerShell 命令提示字元執行所產生的命令。
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>另請參閱

- [使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
- [開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)
