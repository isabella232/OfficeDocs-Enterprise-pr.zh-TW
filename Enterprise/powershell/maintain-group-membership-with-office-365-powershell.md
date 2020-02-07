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
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 了解如何使用 Office 365 PowerShell 來維護 Office 365 中群組的成員資格。
ms.openlocfilehash: 397f8d93df5e9abef0779e4eb56df7bab9ef2344
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841480"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="c07f6-103">維護與 Office 365 PowerShell 的群組成員資格</span><span class="sxs-lookup"><span data-stu-id="c07f6-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="c07f6-104">您可以使用改成 Microsoft 365 系統管理中心的 Office 365 PowerShell 來維護 Office 365 中的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="c07f6-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="c07f6-105">若要產生準備隨 PowerShell 命令藉由指定使用者帳戶和群組名稱，請使用此[群組維護 Microsoft Excel 活頁簿](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx)。</span><span class="sxs-lookup"><span data-stu-id="c07f6-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c07f6-106">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="c07f6-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="c07f6-107">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="c07f6-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="c07f6-108">新增或移除使用者帳戶為群組的成員</span><span class="sxs-lookup"><span data-stu-id="c07f6-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="c07f6-109">**若要新增其 UPN 的使用者帳戶**、 使用者主要名稱 (UPN) 的使用者帳戶中的填滿 (範例： belindan@contoso.com) 和群組顯示名稱] 中，移除 「 < 」 及 「 > 」 字元，並在 PowerShell 視窗或 PowerShell 整合式指令碼環境 (ISE) 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c07f6-110">**若要新增使用者帳戶以其顯示名稱**、 填滿格式中的使用者帳戶顯示名稱 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c07f6-111">**若要移除的使用者帳戶，由其 UPN**、 填滿格式中的使用者帳戶 UPN (範例： belindan@contoso.com) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c07f6-112">**若要移除依其顯示名稱的使用者帳戶**，在 [使用者帳戶顯示名稱的填滿 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="c07f6-113">新增或移除群組，為群組的成員</span><span class="sxs-lookup"><span data-stu-id="c07f6-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="c07f6-114">安全性群組可以包含其他群組成員。</span><span class="sxs-lookup"><span data-stu-id="c07f6-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="c07f6-115">Office 365 群組，但是不能。</span><span class="sxs-lookup"><span data-stu-id="c07f6-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="c07f6-116">本節中的 PowerShell 命令，以新增或移除 [安全性] 群組的群組。</span><span class="sxs-lookup"><span data-stu-id="c07f6-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="c07f6-117">**若要新增其顯示名稱的群組**，在您要新增之群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。</span><span class="sxs-lookup"><span data-stu-id="c07f6-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c07f6-118">**若要移除依其顯示名稱的群組**，在您要移除群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。</span><span class="sxs-lookup"><span data-stu-id="c07f6-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c07f6-119">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="c07f6-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c07f6-120">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c07f6-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="c07f6-121">新增或移除使用者帳戶為群組的成員</span><span class="sxs-lookup"><span data-stu-id="c07f6-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="c07f6-122">**若要新增其 UPN 的使用者帳戶**、 使用者主要名稱 (UPN) 的使用者帳戶中的填滿 (範例： belindan@contoso.com) 和群組顯示名稱] 中，移除 「 < 」 及 「 > 」 字元，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c07f6-123">**若要新增使用者帳戶以其顯示名稱**、 填滿格式中的使用者帳戶顯示名稱 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c07f6-124">**若要移除的使用者帳戶，由其 UPN**、 填滿格式中的使用者帳戶 UPN (範例： belindan@contoso.com) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="c07f6-125">**若要移除依其顯示名稱的使用者帳戶**，在 [使用者帳戶顯示名稱的填滿 (範例： Belinda Newman) 及群組顯示名稱，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="c07f6-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="c07f6-126">新增或移除群組，為群組的成員</span><span class="sxs-lookup"><span data-stu-id="c07f6-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="c07f6-127">安全性群組可以包含其他群組成員。</span><span class="sxs-lookup"><span data-stu-id="c07f6-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="c07f6-128">Office 365 群組，但是不能。</span><span class="sxs-lookup"><span data-stu-id="c07f6-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="c07f6-129">本節中的 PowerShell 命令，以新增或移除 [安全性] 群組的群組。</span><span class="sxs-lookup"><span data-stu-id="c07f6-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="c07f6-130">**若要新增其顯示名稱的群組**，在您要新增之群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。</span><span class="sxs-lookup"><span data-stu-id="c07f6-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="c07f6-131">**若要移除依其顯示名稱的群組**，在您要移除群組的顯示名稱和群組，包含成員的群組，並在 PowerShell 視窗或 PowerShell ISE 中執行這些命令的顯示名稱的填滿。</span><span class="sxs-lookup"><span data-stu-id="c07f6-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="c07f6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c07f6-132">See also</span></span>

[<span data-ttu-id="c07f6-133">管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組</span><span class="sxs-lookup"><span data-stu-id="c07f6-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c07f6-134">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="c07f6-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c07f6-135">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c07f6-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

