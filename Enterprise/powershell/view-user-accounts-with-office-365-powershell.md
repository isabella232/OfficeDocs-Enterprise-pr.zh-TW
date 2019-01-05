---
title: 檢視與 Office 365 PowerShell 的使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
description: 摘要： 檢視、 清單或顯示您的使用者帳戶的各種方式與 Office 365 PowerShell。
ms.openlocfilehash: e95353602b96babe5c80f7d57462370636dd26fa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730318"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="182a0-103">檢視與 Office 365 PowerShell 的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="182a0-104">**摘要：** 使用 Office 365 PowerShell 的各種方式檢視您的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="182a0-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="182a0-105">雖然您可以使用 Office 365 系統管理中心檢視您的 Office 365 租用戶帳戶，您也可以使用 Office 365 PowerShell 並執行一些無法在 Office 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="182a0-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="182a0-106">使用 Azure Active Directory PowerShell 圖模組</span><span class="sxs-lookup"><span data-stu-id="182a0-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="182a0-107">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="182a0-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="182a0-108">檢視所有的帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-108">View all accounts</span></span>

<span data-ttu-id="182a0-109">若要顯示的使用者帳戶的完整清單，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="182a0-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="182a0-110">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="182a0-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="182a0-111">檢視特定的帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-111">View a specific account</span></span>

<span data-ttu-id="182a0-112">若要顯示特定的使用者帳戶，登入帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN) 中的填滿移除"<"和">"字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="182a0-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="182a0-113">範例如下：</span><span class="sxs-lookup"><span data-stu-id="182a0-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="182a0-114">檢視其他屬性值為特定帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-114">View additional property values for a specific account</span></span>

<span data-ttu-id="182a0-115">根據預設，**取得 AzureADUser**指令程式只會顯示帳戶 ObjectID、 DisplayName 及 UserPrincipalName 屬性。</span><span class="sxs-lookup"><span data-stu-id="182a0-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="182a0-p101">為多個選擇性相關的屬性來顯示清單您可以使用**Select-object**指令程式一起**Get AzureADUser**指令程式。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Azure Active Directory PowerShell 進行一個命令的結果，並將其傳送給下一個命令的圖表。以下是範例命令會顯示每個使用者帳戶的 DisplayName、 部門及 UsageLocation：</span><span class="sxs-lookup"><span data-stu-id="182a0-p101">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="182a0-119">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="182a0-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="182a0-120">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="182a0-121">顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="182a0-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="182a0-p102">若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （\*） 來顯示其所有針對特定的使用者帳戶。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="182a0-p102">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="182a0-124">另一個範例，您可以檢查啟用的狀態之特定使用者帳戶具有下列命令：</span><span class="sxs-lookup"><span data-stu-id="182a0-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="182a0-125">檢視一些常見的屬性為基礎的帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-125">View some accounts based on a common property</span></span>

<span data-ttu-id="182a0-p103">為多個選擇性有關要顯示的帳戶清單您可以使用**Where-object**指令程式一起**Get AzureADUser**指令程式。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Azure Active Directory PowerShell 進行一個命令的結果，並將其傳送給下一個命令的圖表。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="182a0-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="182a0-129">此命令會指示的 Graph 設為 Azure Active Directory PowerShell：</span><span class="sxs-lookup"><span data-stu-id="182a0-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="182a0-130">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="182a0-p104">尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="182a0-p105">**UsageLocation**屬性可以是其中一個的使用者帳戶相關聯的許多屬性。若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （\*） 來顯示其所有針對特定的使用者帳戶。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="182a0-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="182a0-p106">例如，此清單中，從**City**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="182a0-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="182a0-p107">以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**。 > [比較運算子] 會針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人 **-lt** 。 [值] 是一般的字串 （的字母、 數字及其他任何字元序列）、 數字值或 **$Null**未指定 > 查看[Where-object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="182a0-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="182a0-141">使用 Windows PowerShell 的 Microsoft Azure Active Directory 模組</span><span class="sxs-lookup"><span data-stu-id="182a0-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="182a0-142">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="182a0-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="182a0-143">檢視所有的帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-143">View all accounts</span></span>

<span data-ttu-id="182a0-144">若要顯示的使用者帳戶的完整清單，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="182a0-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="182a0-145">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="182a0-145">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="182a0-p108">**Get-msoluser** cmdlet 也會有一組參數來篩選顯示的使用者帳戶的設定。例如，未授權使用者 （使用者已加入至 Office 365 但尚未尚未被授權使用任何服務） 的清單，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="182a0-p108">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="182a0-148">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="182a0-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="182a0-149">篩選顯示的其他參數的詳細資訊的一組使用者帳戶顯示，請參閱[Get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))。</span><span class="sxs-lookup"><span data-stu-id="182a0-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="182a0-150">檢視特定的帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-150">View a specific account</span></span>

<span data-ttu-id="182a0-151">若要顯示特定的使用者帳戶，登入的使用者帳戶名稱的使用者帳戶，也稱為使用者主體名稱 (UPN) 中的填滿移除"<"和">"字元並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="182a0-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="182a0-152">檢視一些常見的屬性為基礎的帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-152">View some accounts based on a common property</span></span>

<span data-ttu-id="182a0-p109">為多個選擇性有關要顯示的帳戶清單您可以使用**Where-object**指令程式一起**Get-msoluser** cmdlet。若要合併兩個指令程式，我們使用"管道"字元"|"，這會告知 Office 365 PowerShell 進行一個命令的結果，並將其傳送給下一個命令。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="182a0-p109">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="182a0-156">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="182a0-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="182a0-157">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="182a0-p110">尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-p110">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="182a0-160">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="182a0-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="182a0-p111">**UsageLocation**屬性可以是其中一個的使用者帳戶相關聯的許多屬性。若要查看所有的使用者帳戶屬性，使用**Select-object**指令程式和萬用字元 （\*） 來顯示其所有針對特定的使用者帳戶。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="182a0-p111">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="182a0-p112">例如，此清單中，從**City**是使用者帳戶屬性的名稱。這表示您可以使用下列命令以列出所有住倫敦在使用者的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="182a0-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="182a0-p113">以下範例所示**Where-object**指令程式的語法**Where-object {$\_。**[使用者帳戶屬性名稱][比較運算子][值]**}**. [比較運算子] 是針對相當於 [ **-eq** 、 **-ne**的不等於、 小於、 **-gt**為大於，與其他人 **-lt** 。 [值] 是通常 （的字母、 數字及其他任何字元序列） 的字串、 數字值或 **$Null**未指定。如需詳細資訊，請參閱[Where 物件](https://technet.microsoft.com/en-us/library/hh849715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="182a0-p113">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="182a0-171">您可以檢查封鎖的狀態之使用者帳戶具有下列命令：</span><span class="sxs-lookup"><span data-stu-id="182a0-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="182a0-172">檢視其他屬性值的帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-172">View additional property values for accounts</span></span>

<span data-ttu-id="182a0-173">根據預設**Get-msoluser** cmdlet 會顯示使用者帳戶的三個的屬性：</span><span class="sxs-lookup"><span data-stu-id="182a0-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="182a0-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="182a0-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="182a0-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="182a0-175">DisplayName</span></span>
    
- <span data-ttu-id="182a0-176">尋找 isLicensed</span><span class="sxs-lookup"><span data-stu-id="182a0-176">isLicensed</span></span>
    
<span data-ttu-id="182a0-p114">如果您需要額外的內容，例如使用者的部門和使用者使用 Office 365 服務的所在國家/地區您可以執行**Get-msoluser**一起**Select-object**指令程式來指定的使用者帳戶清單屬性。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="182a0-p114">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="182a0-179">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="182a0-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="182a0-180">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="182a0-181">顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="182a0-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="182a0-182">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="182a0-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="182a0-p115">**Select-object**指令程式可讓您挑選您想要顯示的命令的屬性。若要查看所有的使用者帳戶屬性，使用萬用字元 （\*） 來顯示其所有針對特定的使用者帳戶。以下是範例：</span><span class="sxs-lookup"><span data-stu-id="182a0-p115">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="182a0-p116">若要為多個選擇性有關要顯示的帳戶清單您也可以使用**Where-object**指令程式。以下是範例命令會顯示未指定的使用狀況位置的使用者帳戶：</span><span class="sxs-lookup"><span data-stu-id="182a0-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="182a0-188">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="182a0-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="182a0-189">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="182a0-p117">尋找所有擁有未指定的使用狀況位置的使用者帳戶 ( **Where-object {$\_。UsageLocation-eq $Null}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。在大括弧、 此命令會指示 Office 365 PowerShell 只尋找一組帳戶在其中 UsageLocation 使用者帳戶屬性 ( \*\* $ \_。UsageLocation\*\* ) 不是指定 ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="182a0-p117">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="182a0-192">顯示僅限的使用者帳戶名稱、 部門及使用狀況位置 （ **Select-object DisplayName、 部門、 UsageLocation** ）。</span><span class="sxs-lookup"><span data-stu-id="182a0-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="182a0-193">您應該會看到與下面類似的資訊：</span><span class="sxs-lookup"><span data-stu-id="182a0-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="182a0-p118">如果您使用目錄同步作業來建立及管理 Office 365 使用者，可以顯示 Office 365 使用者具有已預估來自哪個本機帳戶。下列假設 Azure AD 連接有已設定為使用預設來源錨點的 objectguid 資訊 (如需設定來源錨點的詳細資訊，請參閱[Azure AD 連線： 設計概念](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) 和假設有 powershell 的 Active Directory 模組已安裝 （請參閱[RSAT 工具](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)）：</span><span class="sxs-lookup"><span data-stu-id="182a0-p118">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="182a0-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="182a0-196">See also</span></span>

[<span data-ttu-id="182a0-197">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="182a0-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="182a0-198">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="182a0-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="182a0-199">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="182a0-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

