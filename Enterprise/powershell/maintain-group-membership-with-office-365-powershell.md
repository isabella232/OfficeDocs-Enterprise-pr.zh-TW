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
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="719dc-103">維護使用 Office 365 的群組成員資格 PowerShell</span><span class="sxs-lookup"><span data-stu-id="719dc-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="719dc-104">您可以使用 Office 365 PowerShell 代替 Microsoft 365 系統管理中心，以維護 Office 365 中的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="719dc-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="719dc-105">若要透過指定使用者帳戶和群組名稱來產生現成的 PowerShell 命令，請使用此[群組維護 Microsoft Excel 活頁簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="719dc-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="719dc-106">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="719dc-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="719dc-107">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="719dc-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="719dc-108">新增或移除使用者帳戶為群組的成員</span><span class="sxs-lookup"><span data-stu-id="719dc-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="719dc-109">**若要依其 UPN 新增使用者帳戶**，請填入使用者帳戶使用者主要名稱（UPN）（範例： belindan@contoso.com）和群組顯示名稱、移除「<」和「>」字元，並在 PowerShell 視窗或 PowerShell 整合式腳本環境（ISE）中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="719dc-110">**若要新增使用者帳戶的顯示名稱**，請填入使用者帳戶顯示名稱（範例： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="719dc-111">**若要依其 UPN 移除使用者帳戶**，請填入使用者帳戶 UPN （範例： belindan@contoso.com）和群組顯示名稱，然後在 [PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="719dc-112">**若要依其顯示名稱移除使用者帳戶**，請填入使用者帳戶的顯示名稱（例如： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="719dc-113">新增或移除群組為群組的成員</span><span class="sxs-lookup"><span data-stu-id="719dc-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="719dc-114">安全性群組可以包含其他群組做為成員。</span><span class="sxs-lookup"><span data-stu-id="719dc-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="719dc-115">不過，Office 365 群組卻無法。</span><span class="sxs-lookup"><span data-stu-id="719dc-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="719dc-116">本節包含的 PowerShell 命令可以新增或移除安全性群組的群組。</span><span class="sxs-lookup"><span data-stu-id="719dc-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="719dc-117">**若要以其顯示名稱來新增群組**，請填入要新增之群組的顯示名稱，以及將包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="719dc-118">**若要依其顯示名稱移除群組**，請填入您要移除之群組的顯示名稱，以及會包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="719dc-119">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="719dc-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="719dc-120">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="719dc-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="719dc-121">新增或移除使用者帳戶為群組的成員</span><span class="sxs-lookup"><span data-stu-id="719dc-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="719dc-122">**若要依其 UPN 新增使用者帳戶**，請填入使用者帳戶使用者主要名稱（UPN）（範例： belindan@contoso.com）和群組顯示名稱、移除「<」和「>」字元，然後在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="719dc-123">**若要新增使用者帳戶的顯示名稱**，請填入使用者帳戶顯示名稱（範例： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="719dc-124">**若要依其 UPN 移除使用者帳戶**，請填入使用者帳戶 UPN （範例： belindan@contoso.com）和群組顯示名稱，然後在 [PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="719dc-125">**若要依其顯示名稱移除使用者帳戶**，請填入使用者帳戶的顯示名稱（例如： Belinda Newman）和群組顯示名稱，然後在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="719dc-126">新增或移除群組為群組的成員</span><span class="sxs-lookup"><span data-stu-id="719dc-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="719dc-127">安全性群組可以包含其他群組做為成員。</span><span class="sxs-lookup"><span data-stu-id="719dc-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="719dc-128">不過，Office 365 群組卻無法。</span><span class="sxs-lookup"><span data-stu-id="719dc-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="719dc-129">本節包含的 PowerShell 命令可以新增或移除安全性群組的群組。</span><span class="sxs-lookup"><span data-stu-id="719dc-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="719dc-130">**若要以其顯示名稱來新增群組**，請填入要新增之群組的顯示名稱，以及將包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="719dc-131">**若要依其顯示名稱移除群組**，請填入您要移除之群組的顯示名稱，以及會包含成員群組的群組的顯示名稱，並在 PowerShell] 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="719dc-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="719dc-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="719dc-132">See also</span></span>

[<span data-ttu-id="719dc-133">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="719dc-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="719dc-134">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="719dc-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="719dc-135">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="719dc-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

