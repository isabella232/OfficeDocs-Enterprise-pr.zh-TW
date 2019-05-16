---
title: 將角色指派給 Office 365 powershell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
audience: Admin
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
ms.openlocfilehash: d7177dc05aff8725a72edf7c9ab7b6ef93c36aaf
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069219"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a0700-103">將角色指派給 Office 365 powershell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a0700-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a0700-104">您可以快速且輕鬆地將角色指派給使用 Office 365 PowerShell 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0700-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a0700-105">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0700-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a0700-106">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)使用全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0700-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="a0700-107">接下來，決定您想要新增至角色的使用者帳戶登入名稱 (範例： fredsm@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="a0700-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="a0700-108">這是第也稱為使用者主體名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="a0700-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="a0700-109">接下來，決定該角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0700-109">Next, determine the name of the role.</span></span> <span data-ttu-id="a0700-110">使用此[清單中的 Azure Active Directory 中的系統管理員角色權限](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="a0700-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="a0700-111">請注意附註在本文中。</span><span class="sxs-lookup"><span data-stu-id="a0700-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="a0700-112">某些角色名稱是不同的 Azure AD PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a0700-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="a0700-113">例如，在 Microsoft 365 系統管理中心中的 「 SharePoint 管理員 」 角色是用於 Azure AD PowerShell 名為 「 SharePoint 服務系統管理員 」。</span><span class="sxs-lookup"><span data-stu-id="a0700-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="a0700-114">接下來，填寫，登入和角色的名稱，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a0700-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="a0700-115">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="a0700-115">Here is an example of a completed command set:</span></span>
  
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

<span data-ttu-id="a0700-116">若要顯示特定角色的使用者名稱的清單，請使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="a0700-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a0700-117">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="a0700-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a0700-118">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)使用全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0700-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="a0700-119">單一角色變更</span><span class="sxs-lookup"><span data-stu-id="a0700-119">For a single role change</span></span>

<span data-ttu-id="a0700-120">決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="a0700-120">Determine the following:</span></span>
  
- <span data-ttu-id="a0700-121">您想要設定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0700-121">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="a0700-122">若要指定的使用者帳戶，您必須決定其顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a0700-122">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="a0700-123">若要取得的完整清單的帳戶，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="a0700-123">To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a0700-124">此命令會列出您的使用者帳戶，以顯示名稱，一次一個畫面排序顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a0700-124">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="a0700-125">您可以使用**其中**指令程式來篩選清單，以較小的設定。</span><span class="sxs-lookup"><span data-stu-id="a0700-125">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="a0700-126">範例如下：</span><span class="sxs-lookup"><span data-stu-id="a0700-126">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a0700-127">此命令會列出僅為其顯示名稱的開頭 「 百勝 」 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0700-127">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="a0700-128">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="a0700-128">The role you want to assign.</span></span>
    
    <span data-ttu-id="a0700-129">若要顯示可用的角色，您可以指派給使用者帳戶的清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="a0700-129">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="a0700-130">一旦您判斷帳戶的顯示名稱和角色的名稱，請使用以下命令來指派角色給該帳戶：</span><span class="sxs-lookup"><span data-stu-id="a0700-130">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="a0700-131">複製命令，並將它們貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="a0700-131">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="a0700-132">**$DispName**和 **$roleName**變數，將描述文字取代其值，請移除\<和 > 字元，並將保留引號。</span><span class="sxs-lookup"><span data-stu-id="a0700-132">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="a0700-133">複製已修改的行，並將它們貼到您的 Windows Azure Active Directory 模組的 Windows PowerShell 視窗，並執行。</span><span class="sxs-lookup"><span data-stu-id="a0700-133">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="a0700-134">或者，您可以使用 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="a0700-134">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="a0700-135">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="a0700-135">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="a0700-136">多個角色變更</span><span class="sxs-lookup"><span data-stu-id="a0700-136">For multiple role changes</span></span>

<span data-ttu-id="a0700-137">決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="a0700-137">Determine the following:</span></span>
  
- <span data-ttu-id="a0700-138">哪一個使用者帳戶，您想要設定。</span><span class="sxs-lookup"><span data-stu-id="a0700-138">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="a0700-139">若要指定的使用者帳戶，您必須決定其顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a0700-139">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="a0700-140">若要取得清單的帳戶，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="a0700-140">To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a0700-141">此命令會列出所有使用者帳戶，以顯示名稱，一次一個畫面排序顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a0700-141">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="a0700-142">您可以使用**其中**指令程式來篩選清單，以較小的設定。</span><span class="sxs-lookup"><span data-stu-id="a0700-142">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="a0700-143">範例如下：</span><span class="sxs-lookup"><span data-stu-id="a0700-143">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a0700-144">此命令會列出僅為其顯示名稱的開頭 「 百勝 」 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a0700-144">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="a0700-145">您想要指派給每個使用者帳戶哪些角色。</span><span class="sxs-lookup"><span data-stu-id="a0700-145">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="a0700-146">若要顯示可用的角色，您可以指派給使用者帳戶的清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="a0700-146">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="a0700-147">接下來，建立具有 DisplayName 和角色逗點分隔值 (CSV) 的文字檔案名稱的欄位。</span><span class="sxs-lookup"><span data-stu-id="a0700-147">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields.</span></span> <span data-ttu-id="a0700-148">範例如下：</span><span class="sxs-lookup"><span data-stu-id="a0700-148">Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="a0700-149">接下來，填寫 CSV 檔案的位置，並在 PowerShell 命令提示字元執行所產生的命令。</span><span class="sxs-lookup"><span data-stu-id="a0700-149">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="a0700-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0700-150">See also</span></span>

- [<span data-ttu-id="a0700-151">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="a0700-151">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="a0700-152">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="a0700-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="a0700-153">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0700-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
