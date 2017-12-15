---
title: "檢視與 Office 365 PowerShell 的使用者帳戶"
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "摘要： 檢視、 清單或顯示您的使用者帳戶的各種方式與 Office 365 PowerShell。"
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="cd3cb-103">檢視與 Office 365 PowerShell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cd3cb-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="cd3cb-104">**摘要：**檢視、 清單或顯示您的使用者帳戶的各種方式與 Office 365 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="cd3cb-105">雖然您可以使用 Office 365 系統管理中心檢視您的 Office 365 租用戶帳戶，您也可以使用 Office 365 PowerShell 並執行一些無法在 Office 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="cd3cb-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="cd3cb-106">Before you begin</span></span>

<span data-ttu-id="cd3cb-p101">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="cd3cb-109">顯示 Office 365 使用者帳戶資訊</span><span class="sxs-lookup"><span data-stu-id="cd3cb-109">Display Office 365 user account information</span></span>

<span data-ttu-id="cd3cb-110">若要顯示的使用者帳戶的完整清單，請在您的 Office 365 PowerShell 命令提示字元或 PowerShell 整合式指令碼環境 (ISE) 執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="cd3cb-111">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-111">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="cd3cb-p102">**Get-msoluser** cmdlet 也會有一組參數來篩選顯示的使用者帳戶的設定。例如，未授權使用者 （使用者已加入至 Office 365 但尚未尚未被授權使用任何服務） 的清單，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="cd3cb-114">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="cd3cb-115">篩選顯示的其他參數的詳細資訊的一組使用者帳戶顯示，請參閱[Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="cd3cb-p103">為多個選擇性有關要顯示的帳戶清單您可以使用**Where-object**指令程式一起**Get-msoluser** cmdlet。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Office 365 PowerShell 進行一個命令的結果，並將其傳送給下一個命令。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="cd3cb-119">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cd3cb-120">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cd3cb-p104">尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="cd3cb-123">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="cd3cb-p105">**UsageLocation**屬性可以是其中一個的使用者帳戶相關聯的許多屬性。若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （*） 來顯示其所有針對特定的使用者帳戶。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="cd3cb-p106">例如，此清單中，從**City**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="cd3cb-p107">以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**。 > [比較運算子] 會針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人**-lt** > [值] 通常是一個字串 （的字母、 數字及其他任何字元序列），未指定的數值或**$Null**的 > 查看[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="cd3cb-131">您可以檢查封鎖的狀態之使用者帳戶具有下列命令：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="cd3cb-132">選取要顯示的使用者帳戶內容</span><span class="sxs-lookup"><span data-stu-id="cd3cb-132">Select the user account properties to display</span></span>

<span data-ttu-id="cd3cb-133">根據預設[Get-msoluser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet 會顯示使用者帳戶的三個的屬性：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="cd3cb-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="cd3cb-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="cd3cb-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="cd3cb-135">DisplayName</span></span>
    
- <span data-ttu-id="cd3cb-136">尋找 isLicensed</span><span class="sxs-lookup"><span data-stu-id="cd3cb-136">isLicensed</span></span>
    
<span data-ttu-id="cd3cb-p108">如果您需要額外的內容，例如使用者的部門和使用者使用 Office 365 服務的所在國家/地區您可以執行**Get-msoluser**一起**Select-object**指令程式來指定的使用者帳戶清單屬性。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="cd3cb-139">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cd3cb-140">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cd3cb-141">顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="cd3cb-142">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-142">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

<span data-ttu-id="cd3cb-p109">**Select-object**指令程式可讓您挑選您想要顯示的命令的屬性。若要查看所有的使用者帳戶屬性，使用萬用字元 （*） 來顯示其所有針對特定的使用者帳戶。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="cd3cb-p110">若要為多個選擇性有關要顯示的帳戶清單您也可以使用**Where-object**指令程式。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="cd3cb-148">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cd3cb-149">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cd3cb-p111">尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="cd3cb-152">顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="cd3cb-153">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="cd3cb-154">使用 Azure Active Directory V2 PowerShell 模組來顯示使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cd3cb-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="cd3cb-p112">若要顯示的使用者帳戶使用 Azure Active Directory V2 PowerShell 模組屬性，您可以使用[Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0)指令程式。但首先，您必須連線到您的訂閱。指示，請參閱[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="cd3cb-158">顯示 Office 365 使用者帳戶資訊</span><span class="sxs-lookup"><span data-stu-id="cd3cb-158">Display Office 365 user account information</span></span>

<span data-ttu-id="cd3cb-159">若要顯示的使用者帳戶的完整清單，請在您的 Office 365 PowerShell 命令提示字元或 PowerShell 整合式指令碼環境 (ISE) 執行此命令。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="cd3cb-160">依預設**取得 AzureADUser**指令程式將顯示使用者帳戶的三個的屬性：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="cd3cb-161">ObjectID</span><span class="sxs-lookup"><span data-stu-id="cd3cb-161">ObjectID</span></span>
    
- <span data-ttu-id="cd3cb-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="cd3cb-162">DisplayName</span></span>
    
- <span data-ttu-id="cd3cb-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="cd3cb-163">UserPrincipalName</span></span>
    
<span data-ttu-id="cd3cb-p113">為多個選擇性有關要顯示的帳戶清單您可以使用**Where-object**指令程式一起**Get AzureADUser**指令程式。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Office 365 PowerShell 進行一個命令的結果，並將其傳送給下一個命令。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="cd3cb-167">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cd3cb-168">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cd3cb-p114">尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="cd3cb-p115">**UsageLocation**屬性可以是其中一個的使用者帳戶相關聯的許多屬性。若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （*） 來顯示其所有針對特定的使用者帳戶，一次 （**更多**） 一個頁面。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="cd3cb-p116">例如， **-市/鎮**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="cd3cb-p117">以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**。 > [比較運算子] 會針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人**-lt** > [值] 通常是一個字串 （的字母、 數字及其他任何字元序列），未指定的數值或**$Null**的 > 查看[Where-object](https://technet.microsoft.com/en-us/library/hh849715.aspx)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="cd3cb-178">選取要顯示的使用者帳戶內容</span><span class="sxs-lookup"><span data-stu-id="cd3cb-178">Select the user account properties to display</span></span>

<span data-ttu-id="cd3cb-p118">依預設**取得 AzureADUser**指令程式會顯示使用者帳戶 ObjectID、 DisplayName 及 UserPrincipalName 屬性。如果您需要額外的內容，例如使用者的部門和使用者使用 Office 365 服務的所在國家/地區您可以執行**Get AzureADUser**一起**Select-object**指令程式來指定使用者的清單帳戶的屬性。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="cd3cb-182">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cd3cb-183">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cd3cb-184">顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="cd3cb-p119">若要為多個選擇性有關要顯示的帳戶清單您也可以使用**Where-object**指令程式。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="cd3cb-187">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="cd3cb-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cd3cb-188">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cd3cb-p120">尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( ** $ \_。UsageLocation** ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="cd3cb-191">顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="cd3cb-192">初次使用 Office 365 嗎？</span><span class="sxs-lookup"><span data-stu-id="cd3cb-192">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="cd3cb-p121">![簡短 LinkedIn 學習圖示](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png)**新增至 Office 365？**        [Office 365 系統管理員及 IT 專業人員](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)，傳送給您的 LinkedIn 學習探索免費的視訊課程。</span><span class="sxs-lookup"><span data-stu-id="cd3cb-p121">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="cd3cb-195">See also</span><span class="sxs-lookup"><span data-stu-id="cd3cb-195">See also</span></span>

#### 

[<span data-ttu-id="cd3cb-196">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cd3cb-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="cd3cb-197">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="cd3cb-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="cd3cb-198">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd3cb-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

