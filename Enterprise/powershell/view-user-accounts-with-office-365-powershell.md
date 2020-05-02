---
title: 檢視與 Office 365 PowerShell 的使用者帳戶
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 摘要：使用 Office 365 PowerShell 查看、列出或顯示各種方式的使用者帳戶。
ms.openlocfilehash: c97fd55b2516198f2beaddd558174c62972547c6
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004146"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="0c74d-103">檢視與 Office 365 PowerShell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="0c74d-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="0c74d-104">雖然您可以使用 Microsoft 365 系統管理中心來查看 Office 365 租使用者的帳戶，您也可以使用 Office 365 PowerShell，並執行系統管理中心的某些工作。</span><span class="sxs-lookup"><span data-stu-id="0c74d-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="0c74d-105">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c74d-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="0c74d-106">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="0c74d-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="0c74d-107">查看所有帳戶</span><span class="sxs-lookup"><span data-stu-id="0c74d-107">View all accounts</span></span>

<span data-ttu-id="0c74d-108">若要顯示完整的使用者帳戶清單，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0c74d-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="0c74d-109">您應該會看到類似下列的資訊：</span><span class="sxs-lookup"><span data-stu-id="0c74d-109">You should see information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="0c74d-110">查看特定帳戶</span><span class="sxs-lookup"><span data-stu-id="0c74d-110">View a specific account</span></span>

<span data-ttu-id="0c74d-111">若要顯示特定的使用者帳戶，請填入使用者帳戶的登入帳戶名稱，也稱為使用者主要名稱（UPN）、移除 "<" 和 ">" 字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0c74d-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="0c74d-112">範例如下：</span><span class="sxs-lookup"><span data-stu-id="0c74d-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="0c74d-113">查看特定帳戶的其他屬性值</span><span class="sxs-lookup"><span data-stu-id="0c74d-113">View additional property values for a specific account</span></span>

<span data-ttu-id="0c74d-114">根據預設， **AzureADUser** Cmdlet 只會顯示帳戶的 ObjectID、DisplayName 及 UserPrincipalName 屬性。</span><span class="sxs-lookup"><span data-stu-id="0c74d-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="0c74d-115">若要更選擇要顯示的屬性清單，您可以搭配使用**Select** Cmdlet 與**AzureADUser** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0c74d-115">To be more selective about the list of properties to display, you can use the **Select** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="0c74d-116">若要合併這兩個 Cmdlet，我們會使用 "管道" 字元 "|"，它會讓 Azure Active Directory PowerShell 的圖形取得一個命令的結果，並將其傳送至下一個命令。</span><span class="sxs-lookup"><span data-stu-id="0c74d-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="0c74d-117">以下是一個範例命令，顯示每個使用者帳戶的 DisplayName、部門和 UsageLocation：</span><span class="sxs-lookup"><span data-stu-id="0c74d-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

<span data-ttu-id="0c74d-118">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0c74d-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0c74d-119">取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0c74d-120">僅顯示使用者帳戶名稱、部門和使用位置（選取 [ **DisplayName]、[部門]、[UsageLocation** ]）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-120">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="0c74d-121">若要查看使用者帳戶的所有屬性，請使用**Select** Cmdlet 及萬用字元（\*），為特定使用者帳戶顯示所有屬性。</span><span class="sxs-lookup"><span data-stu-id="0c74d-121">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="0c74d-122">範例如下：</span><span class="sxs-lookup"><span data-stu-id="0c74d-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="0c74d-123">在另一個範例中，您可以使用下列命令來檢查特定使用者帳戶的啟用狀態：</span><span class="sxs-lookup"><span data-stu-id="0c74d-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="0c74d-124">根據共同屬性查看部分帳戶</span><span class="sxs-lookup"><span data-stu-id="0c74d-124">View some accounts based on a common property</span></span>

<span data-ttu-id="0c74d-125">若要更選擇要顯示的帳戶清單，您可以使用**Where** Cmdlet 搭配**AzureADUser** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0c74d-125">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="0c74d-126">若要合併這兩個 Cmdlet，我們會使用 "管道" 字元 "|"，它會讓 Azure Active Directory PowerShell 的圖形取得一個命令的結果，並將其傳送至下一個命令。</span><span class="sxs-lookup"><span data-stu-id="0c74d-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="0c74d-127">以下範例命令只會顯示具有未指定使用位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="0c74d-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="0c74d-128">此命令會指導 Azure Active Directory PowerShell 的圖形：</span><span class="sxs-lookup"><span data-stu-id="0c74d-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="0c74d-129">取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0c74d-130">尋找所有未指定使用位置的使用者帳戶（**其中 {$\_）。UsageLocation-eq $Null}** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-130">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="0c74d-131">在大括弧內，此命令會指示 Office 365 PowerShell 只找出 UsageLocation 使用者帳戶\*\* $ \_屬性（如\*\*未指定 UsageLocation）（ **-eq $Null** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="0c74d-132">**UsageLocation**屬性只是與使用者帳戶相關聯的眾多屬性之一。</span><span class="sxs-lookup"><span data-stu-id="0c74d-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="0c74d-133">若要查看使用者帳戶的所有屬性，請使用**Select** Cmdlet 及萬用字元（\*），為特定使用者帳戶顯示所有屬性。</span><span class="sxs-lookup"><span data-stu-id="0c74d-133">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="0c74d-134">範例如下：</span><span class="sxs-lookup"><span data-stu-id="0c74d-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="0c74d-135">例如，在此清單中， **City**是使用者帳戶屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c74d-135">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="0c74d-136">這表示您可以使用下列命令列出居住在倫敦之使用者的所有使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="0c74d-136">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="0c74d-137">這些範例中所示之**Where** Cmdlet 的語法是 **{$\_。**</span><span class="sxs-lookup"><span data-stu-id="0c74d-137">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="0c74d-138">[user account property name][比較運算子]值 **}**。 > [comparison 運算子] 是 **-eq** for equals，- **ne**代表不等於，- **lt**代表小於， **-gt**代表大於，其他。</span><span class="sxs-lookup"><span data-stu-id="0c74d-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="0c74d-139">[value] 通常是 string （字母、數位及其他字元的順序）、數值或 **$Null** （未指定的）> 請參閱[Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1)以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0c74d-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="0c74d-140">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="0c74d-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="0c74d-141">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="0c74d-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="0c74d-142">查看所有帳戶</span><span class="sxs-lookup"><span data-stu-id="0c74d-142">View all accounts</span></span>

<span data-ttu-id="0c74d-143">若要顯示完整的使用者帳戶清單，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0c74d-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="0c74d-144">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0c74d-144">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="0c74d-145">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="0c74d-145">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="0c74d-146">您應該會看到類似下列的資訊：</span><span class="sxs-lookup"><span data-stu-id="0c74d-146">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="0c74d-147">**Get-MsolUser**指令程式也有一組參數，用來篩選顯示的使用者帳戶集。</span><span class="sxs-lookup"><span data-stu-id="0c74d-147">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="0c74d-148">例如，針對未經許可的使用者清單（已新增至 Office 365 的使用者，但尚未授權使用任何服務），請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="0c74d-148">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="0c74d-149">您應該會看到類似下列的資訊：</span><span class="sxs-lookup"><span data-stu-id="0c74d-149">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="0c74d-150">如需其他參數以篩選顯示所顯示之使用者帳戶集合的詳細資訊，請參閱[Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。</span><span class="sxs-lookup"><span data-stu-id="0c74d-150">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  
### <a name="view-a-specific-account"></a><span data-ttu-id="0c74d-151">查看特定帳戶</span><span class="sxs-lookup"><span data-stu-id="0c74d-151">View a specific account</span></span>

<span data-ttu-id="0c74d-152">若要顯示特定的使用者帳戶，請填入使用者帳戶之使用者帳戶的登入名稱（也稱為使用者主要名稱（UPN）），移除 "<" 和 ">" 字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0c74d-152">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="0c74d-153">根據共同屬性查看部分帳戶</span><span class="sxs-lookup"><span data-stu-id="0c74d-153">View some accounts based on a common property</span></span>

<span data-ttu-id="0c74d-154">若要更選擇要顯示的帳戶清單，您可以使用**Where** Cmdlet 與**Get-MsolUser** Cmdlet 結合使用。</span><span class="sxs-lookup"><span data-stu-id="0c74d-154">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="0c74d-155">若要結合這兩個 Cmdlet，我們會使用 "管道" 字元 "|"，以告知 Office 365 PowerShell 執行一個命令的結果，並將其傳送至下一個命令。</span><span class="sxs-lookup"><span data-stu-id="0c74d-155">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="0c74d-156">以下範例命令只會顯示具有未指定使用位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="0c74d-156">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="0c74d-157">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0c74d-157">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0c74d-158">取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-158">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0c74d-159">尋找所有未指定使用位置的使用者帳戶（**其中 {$\_）。UsageLocation-eq $Null}** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-159">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="0c74d-160">在大括弧內，此命令會指示 Office 365 PowerShell 只找出 UsageLocation 使用者帳戶\*\* $ \_屬性（如\*\*未指定 UsageLocation）（ **-eq $Null** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-160">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="0c74d-161">您應該會看到類似下列的資訊：</span><span class="sxs-lookup"><span data-stu-id="0c74d-161">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="0c74d-162">**UsageLocation**屬性只是與使用者帳戶相關聯的眾多屬性之一。</span><span class="sxs-lookup"><span data-stu-id="0c74d-162">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="0c74d-163">若要查看使用者帳戶的所有屬性，請使用**Select** Cmdlet 及萬用字元（\*），為特定使用者帳戶顯示所有屬性。</span><span class="sxs-lookup"><span data-stu-id="0c74d-163">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="0c74d-164">範例如下：</span><span class="sxs-lookup"><span data-stu-id="0c74d-164">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="0c74d-165">例如，在此清單中， **City**是使用者帳戶屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c74d-165">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="0c74d-166">這表示您可以使用下列命令列出居住在倫敦之使用者的所有使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="0c74d-166">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="0c74d-167">這些範例中所示之**Where** Cmdlet 的語法是 **{$\_。**</span><span class="sxs-lookup"><span data-stu-id="0c74d-167">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="0c74d-168">[user account property name][比較運算子]值 **}**.</span><span class="sxs-lookup"><span data-stu-id="0c74d-168">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="0c74d-169">[比較運算子] 的 **-eq**代表 equals，- **ne**代表不等於， **-lt**代表小於， **-gt**代表大於，其他。</span><span class="sxs-lookup"><span data-stu-id="0c74d-169">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="0c74d-170">[value] 通常是 string （字母、數位及其他字元的順序）、數值或未指定的 **$Null** 。</span><span class="sxs-lookup"><span data-stu-id="0c74d-170">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="0c74d-171">如需詳細資訊，請參閱[何處](https://technet.microsoft.com/library/hh849715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0c74d-171">See [Where](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="0c74d-172">您可以使用下列命令來檢查使用者帳戶的封鎖狀態：</span><span class="sxs-lookup"><span data-stu-id="0c74d-172">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="0c74d-173">查看帳戶的其他屬性值</span><span class="sxs-lookup"><span data-stu-id="0c74d-173">View additional property values for accounts</span></span>

<span data-ttu-id="0c74d-174">依預設， **Get-MsolUser** Cmdlet 會顯示使用者帳戶的三個屬性：</span><span class="sxs-lookup"><span data-stu-id="0c74d-174">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="0c74d-175">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="0c74d-175">UserPrincipalName</span></span>
    
- <span data-ttu-id="0c74d-176">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0c74d-176">DisplayName</span></span>
    
- <span data-ttu-id="0c74d-177">Islicensed 內容</span><span class="sxs-lookup"><span data-stu-id="0c74d-177">isLicensed</span></span>
    
<span data-ttu-id="0c74d-178">如果您需要其他屬性（例如，使用者運作的部門和使用者使用 Office 365 服務的國家/地區），您可以執行**Get-MsolUser**結合**選取**Cmdlet，以指定使用者帳戶內容的清單。</span><span class="sxs-lookup"><span data-stu-id="0c74d-178">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="0c74d-179">範例如下：</span><span class="sxs-lookup"><span data-stu-id="0c74d-179">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="0c74d-180">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0c74d-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0c74d-181">取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0c74d-182">僅顯示使用者帳戶名稱、部門和使用位置（選取 [ **DisplayName]、[部門]、[UsageLocation** ]）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-182">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="0c74d-183">您應該會看到類似下列的資訊：</span><span class="sxs-lookup"><span data-stu-id="0c74d-183">You should see information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="0c74d-184">**Select** Cmdlet 可讓您選取要顯示命令的屬性。</span><span class="sxs-lookup"><span data-stu-id="0c74d-184">The **Select** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="0c74d-185">若要查看使用者帳戶的所有屬性，請使用萬用字元（\*），為特定使用者帳戶顯示所有屬性。</span><span class="sxs-lookup"><span data-stu-id="0c74d-185">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="0c74d-186">範例如下：</span><span class="sxs-lookup"><span data-stu-id="0c74d-186">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="0c74d-187">若要更選擇要顯示的帳戶清單，您也可以使用**Where** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0c74d-187">To be more selective about the list of accounts to display, you can also use the **Where** cmdlet.</span></span> <span data-ttu-id="0c74d-188">以下範例命令只會顯示具有未指定使用位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="0c74d-188">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="0c74d-189">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0c74d-189">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0c74d-190">取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-190">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0c74d-191">尋找所有未指定使用位置的使用者帳戶（**其中 {$\_）。UsageLocation-eq $Null}** ）並將結果資訊傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-191">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="0c74d-192">在大括弧內，此命令會指示 Office 365 PowerShell 只尋找 UsageLocation 使用者帳戶\*\* $ \_屬性（如\*\*未指定 UsageLocation）（ **-eq $Null** ）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-192">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="0c74d-193">僅顯示使用者帳戶名稱、部門和使用位置（選取 [ **DisplayName]、[部門]、[UsageLocation** ]）。</span><span class="sxs-lookup"><span data-stu-id="0c74d-193">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="0c74d-194">您應該會看到類似下列的資訊：</span><span class="sxs-lookup"><span data-stu-id="0c74d-194">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="0c74d-195">如果您使用目錄同步處理來建立及管理 Office 365 使用者，您可以顯示已預測 Office 365 使用者的本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="0c74d-195">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="0c74d-196">下列假設 Azure AD Connect 已設定為使用 ObjectGUID 的預設來源錨點（如需設定來源錨點，請參閱[AZURE Ad connect：設計概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)），並假設已安裝 PowerShell 的 Active Directory 網域服務模組（請參閱[RSAT 工具](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：</span><span class="sxs-lookup"><span data-stu-id="0c74d-196">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory Domain Services module for PowerShell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a><span data-ttu-id="0c74d-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c74d-197">See also</span></span>

[<span data-ttu-id="0c74d-198">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c74d-198">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="0c74d-199">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="0c74d-199">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0c74d-200">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c74d-200">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

