---
title: 將角色指派給 Office 365 powershell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 摘要：使用 Office 365 PowerShell 將角色指派給使用者帳戶。
ms.openlocfilehash: 8cd3bd27f95c9d4191c24c7febc85c8fb2fb0118
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004736"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8ff0f-103">將角色指派給 Office 365 powershell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8ff0f-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8ff0f-104">您可以使用 Office 365 PowerShell，快速且輕鬆地將角色指派給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8ff0f-105">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ff0f-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8ff0f-106">首先，使用全域系統管理員帳戶[連接到您的 Office 365 租使用者](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="8ff0f-107">接下來，決定要新增至角色之使用者帳戶的登入名稱（例如： fredsm@contoso.com）。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="8ff0f-108">這也稱為使用者主要名稱（UPN）。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="8ff0f-109">接下來，決定角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-109">Next, determine the name of the role.</span></span> <span data-ttu-id="8ff0f-110">使用[Azure Active Directory 中的系統管理員角色許可權清單](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="8ff0f-111">請注意本文中的記事。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="8ff0f-112">Azure AD PowerShell 的某些角色名稱是不同的。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="8ff0f-113">例如，Microsoft 365 系統管理中心的「SharePoint 系統管理員」角色稱為「SharePoint 服務管理員」，以供 Azure AD PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="8ff0f-114">接下來，填入登入和角色名稱，並執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
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

<span data-ttu-id="8ff0f-115">以下是將「SharePoint 服務管理員」角色指派給 belindan@contoso.com 帳戶的完整命令集範例：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-115">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
```powershell
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

<span data-ttu-id="8ff0f-116">若要顯示特定角色的使用者名稱清單，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8ff0f-117">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8ff0f-118">首先，使用全域系統管理員帳戶[連接到您的 Office 365 租使用者](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="8ff0f-119">針對單一角色變更</span><span class="sxs-lookup"><span data-stu-id="8ff0f-119">For a single role change</span></span>

<span data-ttu-id="8ff0f-120">特定使用者帳戶最常見的方式是顯示名稱或其電子郵件名稱，也就是知道其登入名稱或使用者主要名稱（UPN）。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="8ff0f-121">使用者帳戶的顯示名稱</span><span class="sxs-lookup"><span data-stu-id="8ff0f-121">Display names of user accounts</span></span>

<span data-ttu-id="8ff0f-122">如果您用來處理使用者帳戶的顯示名稱，請決定下列專案：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="8ff0f-123">您要設定的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="8ff0f-124">若要指定使用者帳戶，您必須決定其顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-124">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="8ff0f-125">若要取得完整清單帳戶，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-125">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="8ff0f-126">這個命令會列出您的使用者帳戶顯示名稱，依顯示名稱排序，一次一屏。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-126">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="8ff0f-127">您可以使用**Where** Cmdlet，將清單篩選為較小的集合。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-127">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="8ff0f-128">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-128">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="8ff0f-129">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8ff0f-130">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="8ff0f-131">這個命令只會列出顯示名稱開頭為 "John" 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-131">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="8ff0f-132">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-132">The role you want to assign.</span></span>
    
    <span data-ttu-id="8ff0f-133">若要顯示可指派給使用者帳戶的可用角色清單，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-133">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="8ff0f-134">一旦您決定帳戶的顯示名稱和角色名稱，請使用下列命令將角色指派給帳戶：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-134">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="8ff0f-135">複製命令，並將其貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-135">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="8ff0f-136">針對 **$dispName**和 **$roleName**變數，以其值取代描述文字、移除\<和 > 字元，並留下引號。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-136">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="8ff0f-137">複製已修改的列，並將其貼到 windows 的 Windows Azure Active Directory 模組中 PowerShell] 視窗以執行。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-137">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="8ff0f-138">或者，您也可以使用 Windows PowerShell 的整合式腳本環境（ISE）。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-138">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="8ff0f-139">以下是已完成命令集的範例：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-139">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="8ff0f-140">使用者帳戶的登入名稱</span><span class="sxs-lookup"><span data-stu-id="8ff0f-140">Sign-in names of user accounts</span></span>

<span data-ttu-id="8ff0f-141">如果您用來使用登入名稱或使用者帳戶的 Upn，請決定下列專案：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-141">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="8ff0f-142">使用者帳戶的 UPN。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-142">The user account's UPN.</span></span>
    
    <span data-ttu-id="8ff0f-143">如果您還沒有知道 UPN，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-143">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="8ff0f-144">這個命令會列出您的使用者帳戶的 UPN，依 UPN 排序，一次一個畫面。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-144">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="8ff0f-145">您可以使用**Where** Cmdlet，將清單篩選為較小的集合。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-145">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="8ff0f-146">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-146">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="8ff0f-147">這個命令只會列出顯示名稱開頭為 "John" 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-147">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="8ff0f-148">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-148">The role you want to assign.</span></span>
    
    <span data-ttu-id="8ff0f-149">若要顯示可指派給使用者帳戶的可用角色清單，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-149">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="8ff0f-150">一旦您擁有帳戶的 UPN 和角色名稱，請使用下列命令將角色指派給帳戶：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-150">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="8ff0f-151">複製命令，並將其貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-151">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="8ff0f-152">針對 **$upnName**和 **$roleName**變數，以其值取代描述文字、移除\<和 > 字元，並留下引號。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-152">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="8ff0f-153">複製已修改的列，並將其貼到 windows 的 Windows Azure Active Directory 模組中 PowerShell] 視窗以執行。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-153">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="8ff0f-154">或者，您也可以使用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-154">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="8ff0f-155">以下是已完成命令集的範例：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-155">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="8ff0f-156">多重角色變更</span><span class="sxs-lookup"><span data-stu-id="8ff0f-156">Multiple role changes</span></span>

<span data-ttu-id="8ff0f-157">若有多個角色變更，請決定下列專案：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-157">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="8ff0f-158">您要設定的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-158">Which user accounts that you want to configure.</span></span> <span data-ttu-id="8ff0f-159">您可以使用上一節中的方法來收集顯示名稱或 Upn 的集合。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-159">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="8ff0f-160">您想要指派給每個使用者帳戶的角色。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-160">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="8ff0f-161">若要顯示可指派給使用者帳戶的可用角色清單，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-161">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="8ff0f-162">接下來，建立一個逗號分隔值（CSV）文字檔，其中包含 [顯示名稱] 或 [UPN] 和 [角色名稱] 欄位。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-162">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="8ff0f-163">您可以使用 Microsoft Excel 輕鬆做到這一點。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-163">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="8ff0f-164">以下是顯示名稱的範例：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-164">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="8ff0f-165">接下來，填入 CSV 檔案的位置，並在 PowerShell 命令提示字元中執行產生的命令。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="8ff0f-166">以下是 Upn 的範例：</span><span class="sxs-lookup"><span data-stu-id="8ff0f-166">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="8ff0f-167">接下來，填入 CSV 檔案的位置，並在 PowerShell 命令提示字元中執行產生的命令。</span><span class="sxs-lookup"><span data-stu-id="8ff0f-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="8ff0f-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ff0f-168">See also</span></span>

- [<span data-ttu-id="8ff0f-169">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ff0f-169">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="8ff0f-170">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="8ff0f-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="8ff0f-171">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ff0f-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
