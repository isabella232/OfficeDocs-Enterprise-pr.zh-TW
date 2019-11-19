---
title: 將角色指派給 Office 365 powershell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
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
ms.openlocfilehash: 29c23e88d9b7bc2fc0030d467336e38ed413a4ab
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "38707030"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="587ed-103">將角色指派給 Office 365 powershell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="587ed-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="587ed-104">您可以快速且輕鬆地將角色指派給使用 Office 365 PowerShell 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="587ed-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="587ed-105">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="587ed-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="587ed-106">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)使用全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="587ed-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="587ed-107">接下來，決定您想要新增至角色的使用者帳戶登入名稱 (範例： fredsm@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="587ed-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="587ed-108">這是第也稱為使用者主體名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="587ed-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="587ed-109">接下來，決定該角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="587ed-109">Next, determine the name of the role.</span></span> <span data-ttu-id="587ed-110">使用此[清單中的 Azure Active Directory 中的系統管理員角色權限](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)。</span><span class="sxs-lookup"><span data-stu-id="587ed-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="587ed-111">請注意附註在本文中。</span><span class="sxs-lookup"><span data-stu-id="587ed-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="587ed-112">某些角色名稱是不同的 Azure AD PowerShell。</span><span class="sxs-lookup"><span data-stu-id="587ed-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="587ed-113">例如，在 Microsoft 365 系統管理中心中的 「 SharePoint 管理員 」 角色是用於 Azure AD PowerShell 名為 「 SharePoint 服務系統管理員 」。</span><span class="sxs-lookup"><span data-stu-id="587ed-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="587ed-114">接下來，填寫，登入和角色的名稱，並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="587ed-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="587ed-115">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="587ed-115">Here is an example of a completed command set:</span></span>
  
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

<span data-ttu-id="587ed-116">若要顯示特定角色的使用者名稱的清單，請使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="587ed-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="587ed-117">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="587ed-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="587ed-118">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)使用全域系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="587ed-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="587ed-119">單一角色變更</span><span class="sxs-lookup"><span data-stu-id="587ed-119">For a single role change</span></span>

<span data-ttu-id="587ed-120">特定使用者帳戶的常用方法是使用其顯示名稱或其電子郵件名稱，也就是其登入使用者主體名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="587ed-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="587ed-121">顯示的使用者帳戶的名稱</span><span class="sxs-lookup"><span data-stu-id="587ed-121">Display names of user accounts</span></span>

<span data-ttu-id="587ed-122">如果您是用來使用之使用者帳戶的顯示名稱，決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="587ed-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="587ed-123">您想要設定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="587ed-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="587ed-124">若要指定的使用者帳戶，您必須決定其顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="587ed-124">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="587ed-125">若要取得的完整清單的帳戶，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="587ed-125">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="587ed-126">此命令會列出您的使用者帳戶，以顯示名稱，一次一個畫面排序顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="587ed-126">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="587ed-127">您可以使用**其中**指令程式來篩選清單，以較小的設定。</span><span class="sxs-lookup"><span data-stu-id="587ed-127">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="587ed-128">範例如下：</span><span class="sxs-lookup"><span data-stu-id="587ed-128">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="587ed-129">此命令會列出僅為其顯示名稱的開頭 「 百勝 」 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="587ed-129">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="587ed-130">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="587ed-130">The role you want to assign.</span></span>
    
    <span data-ttu-id="587ed-131">若要顯示可用的角色，您可以指派給使用者帳戶的清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="587ed-131">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="587ed-132">一旦您判斷帳戶的顯示名稱和角色的名稱，請使用以下命令來指派角色給該帳戶：</span><span class="sxs-lookup"><span data-stu-id="587ed-132">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="587ed-133">複製命令，並將它們貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="587ed-133">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="587ed-134">**$DispName**和 **$roleName**變數，將描述文字取代其值，請移除\<和 > 字元，並將保留引號。</span><span class="sxs-lookup"><span data-stu-id="587ed-134">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="587ed-135">複製已修改的行，並將它們貼到您的 Windows Azure Active Directory 模組的 Windows PowerShell 視窗，並執行。</span><span class="sxs-lookup"><span data-stu-id="587ed-135">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="587ed-136">或者，您可以使用 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="587ed-136">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="587ed-137">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="587ed-137">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="587ed-138">登入的使用者帳戶的名稱</span><span class="sxs-lookup"><span data-stu-id="587ed-138">Sign-in names of user accounts</span></span>

<span data-ttu-id="587ed-139">如果您是用來使用的登入名稱或使用者帳戶的 Upn，決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="587ed-139">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="587ed-140">使用者帳戶的 UPN。</span><span class="sxs-lookup"><span data-stu-id="587ed-140">The user account's UPN.</span></span>
    
    <span data-ttu-id="587ed-141">如果您不知道 UPN，使用此命令：</span><span class="sxs-lookup"><span data-stu-id="587ed-141">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="587ed-142">此命令會列出您的使用者帳戶，排序 UPN，一次一個畫面的 UPN。</span><span class="sxs-lookup"><span data-stu-id="587ed-142">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="587ed-143">您可以使用**其中**指令程式來篩選清單，以較小的設定。</span><span class="sxs-lookup"><span data-stu-id="587ed-143">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="587ed-144">範例如下：</span><span class="sxs-lookup"><span data-stu-id="587ed-144">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="587ed-145">此命令會列出僅為其顯示名稱的開頭 「 百勝 」 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="587ed-145">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="587ed-146">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="587ed-146">The role you want to assign.</span></span>
    
    <span data-ttu-id="587ed-147">若要顯示可用的角色，您可以指派給使用者帳戶的清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="587ed-147">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="587ed-148">一旦您有帳戶的 UPN 與角色的名稱，請使用以下命令將角色指派給帳戶：</span><span class="sxs-lookup"><span data-stu-id="587ed-148">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="587ed-149">複製命令，並將它們貼到 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="587ed-149">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="587ed-150">**$UpnName**和 **$roleName**變數，將描述文字取代其值，請移除\<和 > 字元，並將保留引號。</span><span class="sxs-lookup"><span data-stu-id="587ed-150">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="587ed-151">複製已修改的行，並將它們貼到您的 Windows Azure Active Directory 模組的 Windows PowerShell 視窗，並執行。</span><span class="sxs-lookup"><span data-stu-id="587ed-151">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="587ed-152">或者，您可以使用 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="587ed-152">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="587ed-153">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="587ed-153">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="587ed-154">多個角色變更</span><span class="sxs-lookup"><span data-stu-id="587ed-154">For multiple role changes</span></span>

<span data-ttu-id="587ed-155">決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="587ed-155">Determine the following:</span></span>
  
- <span data-ttu-id="587ed-156">哪一個使用者帳戶，您想要設定。</span><span class="sxs-lookup"><span data-stu-id="587ed-156">Which user accounts that you want to configure.</span></span> <span data-ttu-id="587ed-157">您可以使用在前一節中的方法，來蒐集的顯示名稱或 Upn。</span><span class="sxs-lookup"><span data-stu-id="587ed-157">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="587ed-158">您想要指派給每個使用者帳戶哪些角色。</span><span class="sxs-lookup"><span data-stu-id="587ed-158">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="587ed-159">若要顯示可用的角色，您可以指派給使用者帳戶的清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="587ed-159">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="587ed-160">接下來，建立具有 UPN 和角色的 [名稱] 欄位的顯示名稱的逗點分隔值 (CSV) 文字檔案。</span><span class="sxs-lookup"><span data-stu-id="587ed-160">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="587ed-161">您可以輕易地與 Microsoft Excel。</span><span class="sxs-lookup"><span data-stu-id="587ed-161">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="587ed-162">以下是範例的顯示名稱：</span><span class="sxs-lookup"><span data-stu-id="587ed-162">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="587ed-163">接下來，填寫 CSV 檔案的位置，並在 PowerShell 命令提示字元執行所產生的命令。</span><span class="sxs-lookup"><span data-stu-id="587ed-163">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="587ed-164">以下是 Upn 範例：</span><span class="sxs-lookup"><span data-stu-id="587ed-164">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="587ed-165">接下來，填寫 CSV 檔案的位置，並在 PowerShell 命令提示字元執行所產生的命令。</span><span class="sxs-lookup"><span data-stu-id="587ed-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="587ed-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="587ed-166">See also</span></span>

- [<span data-ttu-id="587ed-167">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="587ed-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="587ed-168">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="587ed-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="587ed-169">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="587ed-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
