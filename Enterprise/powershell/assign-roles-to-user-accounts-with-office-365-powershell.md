---
title: 使用 PowerShell 將角色指派給 Microsoft 365 使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
description: 摘要：使用 Microsoft 365 的 PowerShell，將角色指派給使用者帳戶。
ms.openlocfilehash: 2be491692c23b1f528612cc5c56e041553f80c48
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230869"
---
# <a name="assign-roles-to-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="2ffcd-103">使用 PowerShell 將角色指派給 Microsoft 365 使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="2ffcd-103">Assign roles to Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="2ffcd-104">*本文適用于 Microsoft 365 Enterprise 和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="2ffcd-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="2ffcd-105">您可以使用 Microsoft 365 PowerShell，快速且輕鬆地將角色指派給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-105">You can quickly and easily assign roles to user accounts using PowerShell for Microsoft 365.</span></span>

>[!Note]
><span data-ttu-id="2ffcd-106">若要使用 Microsoft 365 系統管理中心指派角色給使用者帳戶，請參閱[這些指示](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-106">To assign roles to user accounts with the Microsoft 365 admin center, see [these instructions](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="2ffcd-107">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ffcd-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="2ffcd-108">首先，使用全域系統管理員帳戶[連接至您的 Microsoft 365 租使用者](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="2ffcd-109">接下來，決定要新增至角色之使用者帳戶的登入名稱（例如： fredsm@contoso.com）。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-109">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="2ffcd-110">這也稱為使用者主要名稱（UPN）。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-110">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="2ffcd-111">接下來，決定角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-111">Next, determine the name of the role.</span></span> <span data-ttu-id="2ffcd-112">使用[Azure Active Directory 中的系統管理員角色許可權清單](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-112">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="2ffcd-113">請注意本文中的記事。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-113">Pay attention to the notes in this article.</span></span> <span data-ttu-id="2ffcd-114">Azure AD PowerShell 的某些角色名稱是不同的。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-114">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="2ffcd-115">例如，Microsoft 365 系統管理中心的「SharePoint 系統管理員」角色稱為「SharePoint 服務管理員」，以供 Azure AD PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-115">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="2ffcd-116">接下來，填入登入和角色名稱，並執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-116">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="2ffcd-117">以下是將「SharePoint 服務管理員」角色指派給 belindan@contoso.com 帳戶的完整命令集範例：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-117">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
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

<span data-ttu-id="2ffcd-118">若要顯示特定角色的使用者名稱清單，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-118">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2ffcd-119">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2ffcd-120">首先，使用全域系統管理員帳戶[連接至您的 Microsoft 365 租使用者](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-120">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="2ffcd-121">針對單一角色變更</span><span class="sxs-lookup"><span data-stu-id="2ffcd-121">For a single role change</span></span>

<span data-ttu-id="2ffcd-122">特定使用者帳戶最常見的方式是顯示名稱或其電子郵件名稱，也就是知道其登入名稱或使用者主要名稱（UPN）。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-122">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="2ffcd-123">使用者帳戶的顯示名稱</span><span class="sxs-lookup"><span data-stu-id="2ffcd-123">Display names of user accounts</span></span>

<span data-ttu-id="2ffcd-124">如果您用來處理使用者帳戶的顯示名稱，請決定下列專案：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-124">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="2ffcd-125">您要設定的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-125">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="2ffcd-126">若要指定使用者帳戶，您必須決定其顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-126">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="2ffcd-127">若要取得完整清單帳戶，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-127">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="2ffcd-128">這個命令會列出您的使用者帳戶顯示名稱，依顯示名稱排序，一次一屏。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-128">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="2ffcd-129">您可以使用**Where** Cmdlet，將清單篩選為較小的集合。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-129">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="2ffcd-130">範例如下：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-130">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="2ffcd-131">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-131">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="2ffcd-132">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-132">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="2ffcd-133">這個命令只會列出顯示名稱開頭為 "John" 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-133">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="2ffcd-134">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-134">The role you want to assign.</span></span>
    
    <span data-ttu-id="2ffcd-135">若要顯示可指派給使用者帳戶的可用角色清單，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-135">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="2ffcd-136">一旦您決定帳戶的顯示名稱和角色名稱，請使用下列命令將角色指派給帳戶：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-136">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="2ffcd-137">複製命令，並將其貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-137">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="2ffcd-138">針對 **$dispName**和 **$roleName**變數，以其值取代描述文字、移除 \< and > 字元，並留下引號。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-138">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="2ffcd-139">複製已修改的列，並將其貼到 windows 的 Windows Azure Active Directory 模組中 PowerShell] 視窗以執行。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-139">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="2ffcd-140">或者，您也可以使用 Windows PowerShell 的整合式腳本環境（ISE）。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-140">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="2ffcd-141">以下是已完成命令集的範例：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-141">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="2ffcd-142">使用者帳戶的登入名稱</span><span class="sxs-lookup"><span data-stu-id="2ffcd-142">Sign-in names of user accounts</span></span>

<span data-ttu-id="2ffcd-143">如果您用來使用登入名稱或使用者帳戶的 Upn，請決定下列專案：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-143">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="2ffcd-144">使用者帳戶的 UPN。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-144">The user account's UPN.</span></span>
    
    <span data-ttu-id="2ffcd-145">如果您還沒有知道 UPN，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-145">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="2ffcd-146">這個命令會列出您的使用者帳戶的 UPN，依 UPN 排序，一次一個畫面。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-146">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="2ffcd-147">您可以使用**Where** Cmdlet，將清單篩選為較小的集合。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-147">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="2ffcd-148">範例如下：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-148">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="2ffcd-149">這個命令只會列出顯示名稱開頭為 "John" 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-149">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="2ffcd-150">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-150">The role you want to assign.</span></span>
    
    <span data-ttu-id="2ffcd-151">若要顯示可指派給使用者帳戶的可用角色清單，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-151">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="2ffcd-152">一旦您擁有帳戶的 UPN 和角色名稱，請使用下列命令將角色指派給帳戶：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-152">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="2ffcd-153">複製命令，並將其貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-153">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="2ffcd-154">針對 **$upnName**和 **$roleName**變數，以其值取代描述文字、移除 \< and > 字元，並留下引號。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-154">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="2ffcd-155">複製已修改的列，並將其貼到 windows 的 Windows Azure Active Directory 模組中 PowerShell] 視窗以執行。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-155">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="2ffcd-156">或者，您也可以使用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-156">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="2ffcd-157">以下是已完成命令集的範例：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-157">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="2ffcd-158">多重角色變更</span><span class="sxs-lookup"><span data-stu-id="2ffcd-158">Multiple role changes</span></span>

<span data-ttu-id="2ffcd-159">若有多個角色變更，請決定下列專案：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-159">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="2ffcd-160">您要設定的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-160">Which user accounts that you want to configure.</span></span> <span data-ttu-id="2ffcd-161">您可以使用上一節中的方法來收集顯示名稱或 Upn 的集合。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-161">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="2ffcd-162">您想要指派給每個使用者帳戶的角色。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-162">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="2ffcd-163">若要顯示可指派給使用者帳戶的可用角色清單，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-163">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="2ffcd-164">接下來，建立一個逗號分隔值（CSV）文字檔，其中包含 [顯示名稱] 或 [UPN] 和 [角色名稱] 欄位。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-164">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="2ffcd-165">您可以使用 Microsoft Excel 輕鬆做到這一點。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-165">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="2ffcd-166">以下是顯示名稱的範例：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-166">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="2ffcd-167">接下來，填入 CSV 檔案的位置，並在 PowerShell 命令提示字元中執行產生的命令。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="2ffcd-168">以下是 Upn 的範例：</span><span class="sxs-lookup"><span data-stu-id="2ffcd-168">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="2ffcd-169">接下來，填入 CSV 檔案的位置，並在 PowerShell 命令提示字元中執行產生的命令。</span><span class="sxs-lookup"><span data-stu-id="2ffcd-169">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="2ffcd-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ffcd-170">See also</span></span>

- [<span data-ttu-id="2ffcd-171">使用 PowerShell 管理 Microsoft 365 使用者帳戶、授權和群組</span><span class="sxs-lookup"><span data-stu-id="2ffcd-171">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="2ffcd-172">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="2ffcd-172">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="2ffcd-173">Microsoft 365 的 PowerShell 快速入門</span><span class="sxs-lookup"><span data-stu-id="2ffcd-173">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
