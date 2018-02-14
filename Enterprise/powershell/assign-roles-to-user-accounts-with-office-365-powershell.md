---
title: "將角色指派給 Office 365 powershell 的使用者帳戶"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: "摘要： 使用 Office 365 PowerShell 並新增 MsolRoleMember cmdlet 來為使用者帳戶指派的角色。"
ms.openlocfilehash: 97ecf29e10d14843322f3062ef16da14f16f7a2a
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="4fba2-103">將角色指派給 Office 365 powershell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="4fba2-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="4fba2-104">**摘要：**使用 Office 365 PowerShell 和**新增 MsolRoleMember**指令程式來為使用者帳戶指派的角色。</span><span class="sxs-lookup"><span data-stu-id="4fba2-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="4fba2-105">您可以快速又輕鬆地將角色指派使用 Office 365 PowerShell 所識別的使用者帳戶的顯示名稱及角色名稱的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4fba2-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="4fba2-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="4fba2-106">Before you begin</span></span>

<span data-ttu-id="4fba2-p101">本主題中的程序要求您重新連線至 Office 365 PowerShell 使用的全域管理員帳戶。指示，請參閱[Connect to Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="4fba2-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="4fba2-109">如需單一角色變更</span><span class="sxs-lookup"><span data-stu-id="4fba2-109">For a single role change</span></span>

<span data-ttu-id="4fba2-110">決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="4fba2-110">Determine the following:</span></span>
  
- <span data-ttu-id="4fba2-111">您想要設定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4fba2-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="4fba2-p102">若要指定的使用者帳戶，您必須判斷其顯示名稱。若要取得的完整清單的帳戶，使用此命令：</span><span class="sxs-lookup"><span data-stu-id="4fba2-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4fba2-p103">此命令會列出您的使用者帳戶，以顯示名稱] 中，一次一個畫面來顯示名稱。您可以使用**其中**指令程式來篩選少量的清單。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="4fba2-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4fba2-117">此命令會列出只有其顯示名稱開頭為"John"的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4fba2-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="4fba2-118">您要指派的角色。</span><span class="sxs-lookup"><span data-stu-id="4fba2-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="4fba2-119">若要顯示您可以將指派給使用者帳戶的可用角色清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="4fba2-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="4fba2-120">一旦您已決定帳戶的顯示名稱和角色的名稱，使用這些命令將角色指派給帳戶：</span><span class="sxs-lookup"><span data-stu-id="4fba2-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="4fba2-p104">命令複製並貼入 [記事本]。**$DispName**和**$roleName**變數，將說明文字取代其值、 移除\<和 > 字元和離開括住。複製已修改的行並將它們貼到您的 Windows Azure Active Directory Module for Windows PowerShell 視窗執行它們。或者，您可以使用 Windows PowerShell 整合式指令碼環境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="4fba2-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="4fba2-125">以下是一組完整的命令的範例：</span><span class="sxs-lookup"><span data-stu-id="4fba2-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="4fba2-126">是否有多個角色變更</span><span class="sxs-lookup"><span data-stu-id="4fba2-126">For multiple role changes</span></span>

<span data-ttu-id="4fba2-127">決定下列項目：</span><span class="sxs-lookup"><span data-stu-id="4fba2-127">Determine the following:</span></span>
  
- <span data-ttu-id="4fba2-128">哪些使用者帳戶新增您要設定。</span><span class="sxs-lookup"><span data-stu-id="4fba2-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="4fba2-p105">若要指定的使用者帳戶，您必須判斷其顯示名稱。若要取得的帳戶，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="4fba2-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4fba2-p106">此命令會列出所有使用者帳戶，以顯示名稱] 中，一次一個畫面來顯示名稱。您可以使用**其中**指令程式來篩選少量的清單。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="4fba2-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="4fba2-134">此命令會列出只有其顯示名稱開頭為"John"的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4fba2-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="4fba2-135">您要指派給每個使用者帳戶的角色。</span><span class="sxs-lookup"><span data-stu-id="4fba2-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="4fba2-136">若要顯示您可以將指派給使用者帳戶的可用角色清單，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="4fba2-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="4fba2-p107">接下來，建立內含 DisplayName 和角色逗點分隔值 (CSV) 的文字檔案名稱的欄位。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="4fba2-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="4fba2-139">接下來，填入 CSV 檔案的位置與在 PowerShell 命令提示字元中執行所產生的命令。</span><span class="sxs-lookup"><span data-stu-id="4fba2-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="4fba2-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fba2-140">See also</span></span>

#### 

[<span data-ttu-id="4fba2-141">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="4fba2-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4fba2-142">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="4fba2-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4fba2-143">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="4fba2-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

[<span data-ttu-id="4fba2-144">新增 MsolRoleMember</span><span class="sxs-lookup"><span data-stu-id="4fba2-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)

