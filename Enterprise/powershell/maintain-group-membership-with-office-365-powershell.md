---
title: 維護使用 Office 365 的群組成員資格 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 瞭解如何使用 Office 365 PowerShell 維護 Office 365 群組的成員資格。
ms.openlocfilehash: 0e6c5f2e27f9d146bb2a053bd3bdb6694fb07276
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004626"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a>維護使用 Office 365 的群組成員資格 PowerShell

您可以使用 Office 365 PowerShell 代替 Microsoft 365 系統管理中心，以維護 Office 365 中的群組成員資格。 

> [!TIP]
> 若要透過指定使用者帳戶和群組名稱來產生現成的 PowerShell 命令，請使用此[群組維護 Microsoft Excel 活頁簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)。 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell
首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>新增或移除使用者帳戶為群組的成員

**若要依其 UPN 新增使用者帳戶**，請填入使用者帳戶使用者主要名稱（UPN）（範例： belindan@contoso.com）和群組顯示名稱、移除「<」和「>」字元，並在 PowerShell 視窗或 PowerShell 整合式腳本環境（ISE）中執行這些命令。

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要新增使用者帳戶的顯示名稱**，請填入使用者帳戶顯示名稱（範例： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要依其 UPN 移除使用者帳戶**，請填入使用者帳戶 UPN （範例： belindan@contoso.com）和群組顯示名稱，然後在 [PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要依其顯示名稱移除使用者帳戶**，請填入使用者帳戶的顯示名稱（例如： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>新增或移除群組為群組的成員

安全性群組可以包含其他群組做為成員。 不過，Office 365 群組卻無法。 本節包含的 PowerShell 命令可以新增或移除安全性群組的群組。

**若要以其顯示名稱來新增群組**，請填入要新增之群組的顯示名稱，以及將包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要依其顯示名稱移除群組**，請填入您要移除之群組的顯示名稱，以及會包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>新增或移除使用者帳戶為群組的成員

**若要依其 UPN 新增使用者帳戶**，請填入使用者帳戶使用者主要名稱（UPN）（範例： belindan@contoso.com）和群組顯示名稱、移除「<」和「>」字元，然後在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要新增使用者帳戶的顯示名稱**，請填入使用者帳戶顯示名稱（範例： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要依其 UPN 移除使用者帳戶**，請填入使用者帳戶 UPN （範例： belindan@contoso.com）和群組顯示名稱，然後在 [PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要依其顯示名稱移除使用者帳戶**，請填入使用者帳戶的顯示名稱（例如： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>新增或移除群組為群組的成員

安全性群組可以包含其他群組做為成員。 不過，Office 365 群組卻無法。 本節包含的 PowerShell 命令可以新增或移除安全性群組的群組。

**若要以其顯示名稱來新增群組**，請填入要新增之群組的顯示名稱，以及將包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**若要依其顯示名稱移除群組**，請填入您要移除之群組的顯示名稱，以及會包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>另請參閱

[使用 Office 365 管理使用者帳戶、授權和群組 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

