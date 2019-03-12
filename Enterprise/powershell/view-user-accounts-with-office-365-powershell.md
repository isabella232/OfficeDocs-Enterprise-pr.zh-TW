---
title: 檢視與 Office 365 PowerShell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/11/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 摘要： 檢視、 清單，或使用 Office 365 PowerShell 的各種方式顯示您的使用者帳戶。
ms.openlocfilehash: 10b6d209e76f94b8b001718abd35368f9d1bc29c
ms.sourcegitcommit: ae4b3c1e2859991f3b94690f2eb3b2838d7db2d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "30539011"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8c0af-103">檢視與 Office 365 PowerShell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8c0af-104">**摘要：** 使用 Office 365 PowerShell 的多種方式檢視您的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c0af-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="8c0af-105">雖然您可以使用 Office 365 系統管理中心，來檢視您的 Office 365 租用戶帳戶，也可以使用 Office 365 PowerShell 並執行 Office 365 系統管理中心無法的一些事項。</span><span class="sxs-lookup"><span data-stu-id="8c0af-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8c0af-106">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c0af-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8c0af-107">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="8c0af-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="8c0af-108">檢視所有帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-108">View all accounts</span></span>

<span data-ttu-id="8c0af-109">若要顯示的使用者帳戶的完整清單，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8c0af-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="8c0af-110">您應該會看到類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="8c0af-110">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="8c0af-111">檢視特定的帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-111">View a specific account</span></span>

<span data-ttu-id="8c0af-112">若要顯示特定的使用者帳戶，請填寫登入帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN)、 移除 「 < 」 和 「 > 」 的字元，並執行此命令：</span><span class="sxs-lookup"><span data-stu-id="8c0af-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="8c0af-113">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8c0af-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="8c0af-114">檢視為特定帳戶的其他屬性值</span><span class="sxs-lookup"><span data-stu-id="8c0af-114">View additional property values for a specific account</span></span>

<span data-ttu-id="8c0af-115">根據預設，**取得 AzureADUser**指令程式只會顯示帳戶 ObjectID、 DisplayName 及 UserPrincipalName 屬性。</span><span class="sxs-lookup"><span data-stu-id="8c0af-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="8c0af-116">為多個選擇性相關的屬性若要顯示，清單您可以使用**Select-object** cmdlet**取得 AzureADUser**指令程式搭配。</span><span class="sxs-lookup"><span data-stu-id="8c0af-116">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="8c0af-117">若要合併的兩個 cmdlet，我們使用 「 管道 」 字元"| 」，這會告知 Azure Active Directory PowerShell 的一個命令的結果並將它傳送給下一個命令的圖表。</span><span class="sxs-lookup"><span data-stu-id="8c0af-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="8c0af-118">以下是範例命令，會顯示名稱、 部門和 UsageLocation 顯示每個使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="8c0af-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="8c0af-119">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="8c0af-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8c0af-120">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8c0af-121">顯示僅限的使用者帳戶名稱、 部門和使用位置 （ **Select-object DisplayName、 Department、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="8c0af-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="8c0af-122">若要查看所有的使用者帳戶的內容，使用**Select-object** cmdlet 和萬用字元 （\*） 來顯示全部的特定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c0af-122">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="8c0af-123">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8c0af-123">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8c0af-124">另一個範例，您可以檢查啟用的狀態的特定使用者帳戶使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="8c0af-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="8c0af-125">檢視一些常見屬性為基礎的帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-125">View some accounts based on a common property</span></span>

<span data-ttu-id="8c0af-126">為多個選擇性相關的帳戶來顯示，清單您可以使用**Where-object** cmdlet**取得 AzureADUser**指令程式搭配。</span><span class="sxs-lookup"><span data-stu-id="8c0af-126">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="8c0af-127">若要合併的兩個 cmdlet，我們使用 「 管道 」 字元"| 」，這會告知 Azure Active Directory PowerShell 的一個命令的結果並將它傳送給下一個命令的圖表。</span><span class="sxs-lookup"><span data-stu-id="8c0af-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="8c0af-128">以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="8c0af-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="8c0af-129">此命令會指示 Azure Active Directory PowerShell 的 Graph 設為：</span><span class="sxs-lookup"><span data-stu-id="8c0af-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="8c0af-130">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8c0af-131">尋找所有使用者帳戶具有未指定的使用狀況的位置 ( **Where-object {$\_。UsageLocation-eq $Null}** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-131">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="8c0af-132">在大括弧，此命令會指示 Office 365 PowerShell 來只尋找一組帳戶順序 UsageLocation 使用者帳戶屬性 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-132">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="8c0af-133">**UsageLocation**屬性可以是其中一個使用者帳戶相關聯的許多屬性。</span><span class="sxs-lookup"><span data-stu-id="8c0af-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="8c0af-134">若要查看所有的使用者帳戶的內容，使用**Select-object** cmdlet 和萬用字元 （\*） 來顯示全部的特定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c0af-134">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="8c0af-135">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8c0af-135">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8c0af-136">例如，此清單中，從**縣/市**是使用者帳戶屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0af-136">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="8c0af-137">這表示您可以使用下列命令來列出所有住倫敦在使用者的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="8c0af-137">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="8c0af-138">下列範例所示**Where-object** cmdlet 的語法如下**Where-object {$\_。**</span><span class="sxs-lookup"><span data-stu-id="8c0af-138">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="8c0af-139">[使用者帳戶屬性名稱][比較運算子][值]**}**.> [比較運算子] 是 **-eq**等於、 **-ne 代表**不等於、 **-lt 代表**小於、 **-gt**大於，針對與其他人。</span><span class="sxs-lookup"><span data-stu-id="8c0af-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="8c0af-140">[值] 通常是 （字母、 數字及其他字元序列） 的字串、 數值或 **$Null**的 unspecified> 如需詳細資訊，請參閱[Where-object cmdlet](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) 。</span><span class="sxs-lookup"><span data-stu-id="8c0af-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8c0af-141">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="8c0af-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8c0af-142">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="8c0af-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="8c0af-143">檢視所有帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-143">View all accounts</span></span>

<span data-ttu-id="8c0af-144">若要顯示的使用者帳戶的完整清單，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8c0af-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="8c0af-145">您應該會看到類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="8c0af-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="8c0af-146">**Get-msoluser** cmdlet 也會有一組參數來篩選顯示的使用者帳戶的集合。</span><span class="sxs-lookup"><span data-stu-id="8c0af-146">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="8c0af-147">例如，如未經授權的使用者 （使用者已新增至 Office 365，但尚未尚未被授權使用任何服務） 的清單，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="8c0af-147">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="8c0af-148">您應該會看到類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="8c0af-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="8c0af-149">如需其他參數來篩選顯示一組使用者帳戶顯示，請參閱[Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。</span><span class="sxs-lookup"><span data-stu-id="8c0af-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="8c0af-150">檢視特定的帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-150">View a specific account</span></span>

<span data-ttu-id="8c0af-151">若要顯示特定的使用者帳戶，請填寫登入的使用者帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN)、 移除 「 < 」 和 「 > 」 的字元，並執行此命令：</span><span class="sxs-lookup"><span data-stu-id="8c0af-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="8c0af-152">檢視一些常見屬性為基礎的帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-152">View some accounts based on a common property</span></span>

<span data-ttu-id="8c0af-153">為多個選擇性的帳戶來顯示，清單的相關您可以使用**Where-object** cmdlet 搭配**Get-msoluser** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8c0af-153">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="8c0af-154">若要合併的兩個 cmdlet，我們使用 「 管道 」 字元"|"，可告訴 Office 365 PowerShell 來執行一個命令的結果，並將其傳送至下一個命令。</span><span class="sxs-lookup"><span data-stu-id="8c0af-154">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="8c0af-155">以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="8c0af-155">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="8c0af-156">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="8c0af-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8c0af-157">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8c0af-158">尋找所有使用者帳戶具有未指定的使用狀況的位置 ( **Where-object {$\_。UsageLocation-eq $Null}** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-158">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="8c0af-159">在大括弧，此命令會指示 Office 365 PowerShell 來只尋找一組帳戶順序 UsageLocation 使用者帳戶屬性 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-159">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="8c0af-160">您應該會看到類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="8c0af-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="8c0af-161">**UsageLocation**屬性可以是其中一個使用者帳戶相關聯的許多屬性。</span><span class="sxs-lookup"><span data-stu-id="8c0af-161">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="8c0af-162">若要查看所有的使用者帳戶的內容，使用**Select-object** cmdlet 和萬用字元 （\*） 來顯示全部的特定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c0af-162">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="8c0af-163">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8c0af-163">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8c0af-164">例如，此清單中，從**縣/市**是使用者帳戶屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c0af-164">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="8c0af-165">這表示您可以使用下列命令來列出所有住倫敦在使用者的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="8c0af-165">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="8c0af-166">下列範例所示**Where-object** cmdlet 的語法如下**Where-object {$\_。**</span><span class="sxs-lookup"><span data-stu-id="8c0af-166">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="8c0af-167">[使用者帳戶屬性名稱][比較運算子][值]**}**.</span><span class="sxs-lookup"><span data-stu-id="8c0af-167">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="8c0af-168">[比較運算子] 是 **-eq**等於、 **-ne 代表**不等於、 **-lt 代表**小於、 **-gt**大於，針對與其他人。</span><span class="sxs-lookup"><span data-stu-id="8c0af-168">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="8c0af-169">[值] 是通常 （字母、 數字及其他字元序列） 的字串、 數值或 **$Null**未指定。</span><span class="sxs-lookup"><span data-stu-id="8c0af-169">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="8c0af-170">如需詳細資訊，請參閱[Where-object cmdlet](https://technet.microsoft.com/en-us/library/hh849715.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="8c0af-170">See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="8c0af-171">您可以檢查封鎖的狀態的使用者帳戶使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="8c0af-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="8c0af-172">檢視其他屬性值的帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-172">View additional property values for accounts</span></span>

<span data-ttu-id="8c0af-173">**Get-msoluser** cmdlet，依預設會顯示使用者帳戶的三個的屬性：</span><span class="sxs-lookup"><span data-stu-id="8c0af-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="8c0af-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="8c0af-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="8c0af-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8c0af-175">DisplayName</span></span>
    
- <span data-ttu-id="8c0af-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="8c0af-176">isLicensed</span></span>
    
<span data-ttu-id="8c0af-177">如果您需要額外的內容，例如使用者適用於部門與使用者使用 Office 365 服務所在的國家/地區您可以執行**Get-msoluser**搭配**Select-object**指令程式指定的使用者帳戶清單屬性。</span><span class="sxs-lookup"><span data-stu-id="8c0af-177">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="8c0af-178">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8c0af-178">Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="8c0af-179">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="8c0af-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8c0af-180">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8c0af-181">顯示僅限的使用者帳戶名稱、 部門和使用位置 （ **Select-object DisplayName、 Department、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="8c0af-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="8c0af-182">您應該會看到類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="8c0af-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="8c0af-183">**Select-object** cmdlet 可讓您挑選您想要命令，以顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="8c0af-183">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="8c0af-184">若要查看所有的使用者帳戶的內容，使用萬用字元 （\*） 來顯示全部的特定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c0af-184">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="8c0af-185">範例如下：</span><span class="sxs-lookup"><span data-stu-id="8c0af-185">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8c0af-186">為多個選擇性相關清單中的帳戶來顯示，您也可以使用**Where-object** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8c0af-186">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet.</span></span> <span data-ttu-id="8c0af-187">以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="8c0af-187">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="8c0af-188">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="8c0af-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8c0af-189">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8c0af-190">尋找所有使用者帳戶具有未指定的使用狀況的位置 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-190">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="8c0af-191">在大括弧，此命令會指示 Office 365 PowerShell 來只尋找一組帳戶順序 UsageLocation 使用者帳戶屬性 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="8c0af-191">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="8c0af-192">顯示僅限的使用者帳戶名稱、 部門和使用位置 （ **Select-object DisplayName、 Department、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="8c0af-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="8c0af-193">您應該會看到類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="8c0af-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="8c0af-194">如果您使用目錄同步處理來建立及管理 Office 365 使用者，您可以顯示 Office 365 使用者具有已規劃從哪個本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c0af-194">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="8c0af-195">下列假設 Azure AD Connect，已設定要使用的 ObjectGUID 預設來源錨點 (如需設定來源錨點的詳細資訊，請參閱[Azure AD Connect： 設計概念](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts))，並假設 powershell 的 Active Directory 模組有已安裝 （請參閱[RSAT 工具](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：</span><span class="sxs-lookup"><span data-stu-id="8c0af-195">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="8c0af-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c0af-196">See also</span></span>

[<span data-ttu-id="8c0af-197">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8c0af-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8c0af-198">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="8c0af-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8c0af-199">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c0af-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

