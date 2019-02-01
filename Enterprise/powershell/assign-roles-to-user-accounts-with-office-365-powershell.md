---
title: 將角色指派給 Office 365 powershell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
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
description: 摘要： 使用 Office 365 PowerShell 將角色指派給使用者帳戶。
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690434"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="5972a-103">將角色指派給 Office 365 powershell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="5972a-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="5972a-104">您可以快速又輕鬆地將角色指派使用 Office 365 PowerShell 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5972a-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5972a-105">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="5972a-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5972a-106">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)使用全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="5972a-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="5972a-p101">接下來，決定您想要新增至角色的使用者帳戶登入名稱 (範例： fredsm@contoso.com)。這也稱為是使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="5972a-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="5972a-p102">下一步]，以判斷角色的名稱。使用此命令以列出您可以使用 PowerShell 中指派的角色。</span><span class="sxs-lookup"><span data-stu-id="5972a-p102">Next, determine the name of the role. Use this command to list the roles that you can assign with PowerShell.</span></span>

````
Get-AzureADDirectoryRole
````

<span data-ttu-id="5972a-111">接下來，在登入和角色名稱填滿並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="5972a-111">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="5972a-112">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="5972a-112">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="5972a-113">若要顯示特定角色的使用者名稱的清單，請使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="5972a-113">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5972a-114">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="5972a-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5972a-115">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)使用全域管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="5972a-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="5972a-116">如需單一角色變更</span><span class="sxs-lookup"><span data-stu-id="5972a-116">For a single role change</span></span>

<span data-ttu-id="5972a-117">決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="5972a-117">Determine the following:</span></span>
  
- <span data-ttu-id="5972a-118">您想要設定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5972a-118">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="5972a-p103">若要指定的使用者帳戶，您必須判斷其顯示名稱。若要取得的完整清單的帳戶，使用此命令：</span><span class="sxs-lookup"><span data-stu-id="5972a-p103">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="5972a-p104">此命令會列出您的使用者帳戶，以顯示名稱] 中，一次一個畫面來顯示名稱。您可以使用**其中**指令程式來篩選少量的清單。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="5972a-p104">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="5972a-124">此命令會列出只有其顯示名稱開頭為"John"的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5972a-124">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="5972a-125">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="5972a-125">The role you want to assign.</span></span>
    
    <span data-ttu-id="5972a-126">若要顯示您可以將指派給使用者帳戶的可用角色清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="5972a-126">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="5972a-127">一旦您已決定帳戶的顯示名稱和角色的名稱，使用這些命令將角色指派給帳戶：</span><span class="sxs-lookup"><span data-stu-id="5972a-127">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="5972a-p105">命令複製並貼入 [記事本]。**$DispName**和 **$roleName**變數，將說明文字取代其值、 移除\<和 > 字元和離開括住。複製已修改的行並將它們貼到您的 Windows Azure Active Directory Module for Windows PowerShell 視窗執行它們。或者，您可以使用 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="5972a-p105">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="5972a-132">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="5972a-132">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="5972a-133">是否有多個角色變更</span><span class="sxs-lookup"><span data-stu-id="5972a-133">For multiple role changes</span></span>

<span data-ttu-id="5972a-134">決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="5972a-134">Determine the following:</span></span>
  
- <span data-ttu-id="5972a-135">哪些使用者帳戶新增您要設定。</span><span class="sxs-lookup"><span data-stu-id="5972a-135">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="5972a-p106">若要指定的使用者帳戶，您必須判斷其顯示名稱。若要取得的帳戶，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="5972a-p106">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="5972a-p107">此命令會列出所有使用者帳戶，以顯示名稱] 中，一次一個畫面來顯示名稱。您可以使用**其中**指令程式來篩選少量的清單。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="5972a-p107">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="5972a-141">此命令會列出只有其顯示名稱開頭為"John"的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5972a-141">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="5972a-142">您要指派給每個使用者帳戶的角色。</span><span class="sxs-lookup"><span data-stu-id="5972a-142">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="5972a-143">若要顯示您可以將指派給使用者帳戶的可用角色清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="5972a-143">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="5972a-p108">接下來，建立逗點分隔值 (CSV) 文字檔具有 DisplayName 和角色名稱的欄位。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="5972a-p108">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="5972a-146">接下來，填入 CSV 檔案的位置與在 PowerShell 命令提示字元中執行所產生的命令。</span><span class="sxs-lookup"><span data-stu-id="5972a-146">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="5972a-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5972a-147">See also</span></span>

- [<span data-ttu-id="5972a-148">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="5972a-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="5972a-149">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="5972a-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="5972a-150">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5972a-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
