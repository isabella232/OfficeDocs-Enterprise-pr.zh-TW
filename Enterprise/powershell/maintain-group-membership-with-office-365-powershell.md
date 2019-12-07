---
title: 維護與 Office 365 PowerShell 的群組成員資格
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
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
description: 了解如何使用 Office 365 PowerShell 來維護 Office 365 中群組的成員資格。
ms.openlocfilehash: dfd3cad3f2e691930b5f4c754ee07205d3950e54
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886652"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a>維護與 Office 365 PowerShell 的群組成員資格

您可以使用改成 Microsoft 365 系統管理中心的 Office 365 PowerShell 來維護 Office 365 中的群組成員資格。 

> [!TIP]
> 若要產生準備隨 PowerShell 命令藉由指定使用者帳戶和群組名稱，請使用此[群組維護 Microsoft Excel 活頁簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)。 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>針對 Graph 模組，請使用 Azure Active Directory PowerShell
首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>新增或移除使用者帳戶為群組的成員

**若要新增其 UPN 的使用者帳戶**、 使用者主要名稱 (UPN) 的使用者帳戶中的填滿 (範例： belindan@contoso.com) 和群組顯示名稱] 中，移除 「 < 」 及 「 > 」 字元，並在 PowerShell 視窗或 PowerShell 整合式指令碼環境 (ISE) 中執行這些命令。

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要新增使用者帳戶以其顯示名稱**、 填滿格式中的使用者帳戶顯示名稱 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要移除的使用者帳戶，由其 UPN**、 填滿格式中的使用者帳戶 UPN (範例： belindan@contoso.com) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要移除依其顯示名稱的使用者帳戶**，在 [使用者帳戶顯示名稱的填滿 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>新增或移除群組，為群組的成員

安全性群組可以包含其他群組成員。 Office 365 群組，但是不能。 本節中的 PowerShell 命令，以新增或移除 [安全性] 群組的群組。

**若要新增其顯示名稱的群組**，在您要新增之群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要移除依其顯示名稱的群組**，在您要移除群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。

首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>新增或移除使用者帳戶為群組的成員

**若要新增其 UPN 的使用者帳戶**、 使用者主要名稱 (UPN) 的使用者帳戶中的填滿 (範例： belindan@contoso.com) 和群組顯示名稱] 中，移除 「 < 」 及 「 > 」 字元，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要新增使用者帳戶以其顯示名稱**、 填滿格式中的使用者帳戶顯示名稱 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要移除的使用者帳戶，由其 UPN**、 填滿格式中的使用者帳戶 UPN (範例： belindan@contoso.com) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**若要移除依其顯示名稱的使用者帳戶**，在 [使用者帳戶顯示名稱的填滿 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>新增或移除群組，為群組的成員

安全性群組可以包含其他群組成員。 Office 365 群組，但是不能。 本節中的 PowerShell 命令，以新增或移除 [安全性] 群組的群組。

**若要新增其顯示名稱的群組**，在您要新增之群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**若要移除依其顯示名稱的群組**，在您要移除群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>另請參閱

[使用 Office 365 PowerShell 管理使用者帳戶](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[使用 Office 365 PowerShell 管理 Office 365](manage-office-365-with-office-365-powershell.md)
  
[開始使用 Office 365 PowerShell](getting-started-with-office-365-powershell.md)

