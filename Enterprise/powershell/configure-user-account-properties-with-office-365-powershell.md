---
title: 使用 Office 365 PowerShell 中設定使用者帳戶屬性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要： 使用 Office 365 PowerShell 來設定 Office 365 租用戶中的個別或多個使用者帳戶的內容。
ms.openlocfilehash: 3fdf5c4c5dbb4c44a3c91d343bd77810a1411a20
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069235"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="e61b8-103">使用 Office 365 PowerShell 中設定使用者帳戶屬性</span><span class="sxs-lookup"><span data-stu-id="e61b8-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="e61b8-104">**摘要：** 使用 Office 365 PowerShell 來設定 Office 365 租用戶中的個別或多個使用者帳戶的內容。</span><span class="sxs-lookup"><span data-stu-id="e61b8-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="e61b8-105">雖然您可以使用 Office 365 系統管理中心來設定您的 Office 365 租用戶的使用者帳戶的內容，也可以使用 Office 365 PowerShell 並執行 Office 365 系統管理中心無法的一些事項。</span><span class="sxs-lookup"><span data-stu-id="e61b8-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e61b8-106">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="e61b8-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e61b8-107">若要設定使用者帳戶的屬性與 PowerShell 的 Azure Active Directory 針對 Graph 模組，您可以使用[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)指令程式，並指定要設定或變更的內容。</span><span class="sxs-lookup"><span data-stu-id="e61b8-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e61b8-108">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="e61b8-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="e61b8-109">變更特定使用者帳戶內容</span><span class="sxs-lookup"><span data-stu-id="e61b8-109">Change properties for a specific user account</span></span>

<span data-ttu-id="e61b8-110">您使用的 **-ObjectID**參數來識別帳戶及設定或變更與其他參數的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="e61b8-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="e61b8-111">以下是最常見的參數清單。</span><span class="sxs-lookup"><span data-stu-id="e61b8-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="e61b8-112">-Department"\<部門 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="e61b8-113">-DisplayName"\<完整使用者 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="e61b8-114">-FacsimilieTelephoneNumber"\<傳真 number> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="e61b8-115">-GivenName"\<使用者第一張 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="e61b8-116">-姓氏"\<使用者上次 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="e61b8-117">-行動"\<行動電話 number> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="e61b8-118">-JobTitle"\<工作 title> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="e61b8-119">-PreferredLanguage"\<language> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="e61b8-120">-StreetAddress"\<街道 address> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="e61b8-121">-City"\<縣/市 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="e61b8-122">-State"\<狀態 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="e61b8-123">-PostalCode"\<郵遞區號 code> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="e61b8-124">-Country"\<國家/地區 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="e61b8-125">-TelephoneNumber"\<辦公室電話 number> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="e61b8-126">-UsageLocation"\<2 個字元的國家或地區 code> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="e61b8-127">這是 ISO 3166-1 alpha-2http (A2) 兩個字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="e61b8-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="e61b8-128">如需其他參數，請參閱[設定 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="e61b8-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="e61b8-129">若要顯示您的使用者帳戶的使用者主體名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="e61b8-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="e61b8-130">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="e61b8-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e61b8-131">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-132">依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-133">顯示 User Principal Name 屬性的每個帳戶 ( **Select-object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="e61b8-134">一次 （**更多**），顯示其一個畫面。</span><span class="sxs-lookup"><span data-stu-id="e61b8-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="e61b8-135">此命令會列出您的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="e61b8-135">This command will list all of your accounts.</span></span> <span data-ttu-id="e61b8-136">如果您想要顯示使用者主體名稱根據其顯示帳戶名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e61b8-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e61b8-137">此範例會顯示顯示名稱為 Caleb Sills 的使用者帳戶的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="e61b8-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e61b8-138">藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="e61b8-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="e61b8-139">以下是將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱，而不是其使用者主體名稱範例：</span><span class="sxs-lookup"><span data-stu-id="e61b8-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="e61b8-140">變更所有使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="e61b8-140">Change properties for all user accounts</span></span>

<span data-ttu-id="e61b8-141">若要變更的所有使用者的內容，您可以使用**Get-AzureADUser**和**設定 AzureADUser**指令程式的組合。</span><span class="sxs-lookup"><span data-stu-id="e61b8-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="e61b8-142">下列範例會變更為法國所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="e61b8-142">The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="e61b8-143">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="e61b8-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e61b8-144">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-145">將使用者位置設定為法國 (**組 AzureADUser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="e61b8-146">變更一組特定的使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="e61b8-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="e61b8-147">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-AzureADUser**、**位置**及**組 AzureADUser**指令程式的組合。</span><span class="sxs-lookup"><span data-stu-id="e61b8-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="e61b8-148">下列範例會變更為法國會計部門中的所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="e61b8-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="e61b8-149">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="e61b8-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e61b8-150">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-151">尋找所有使用者帳戶具有 Department 屬性設為"Accounting"(**其中 {$_。Department-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-152">將使用者位置設定為法國 (**組 AzureADUser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e61b8-153">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="e61b8-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e61b8-154">若要設定使用者帳戶的屬性與 Microsoft Azure Active Directory 模組的 Windows PowerShell，您可以使用 Set-msoluser cmdlet，並指定要設定或變更的內容。</span><span class="sxs-lookup"><span data-stu-id="e61b8-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e61b8-155">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="e61b8-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="e61b8-156">變更特定使用者帳戶內容</span><span class="sxs-lookup"><span data-stu-id="e61b8-156">Change properties for a specific user account</span></span>

<span data-ttu-id="e61b8-157">若要設定特定的使用者帳戶的內容，您可以使用[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet，並指定要設定或變更的內容。</span><span class="sxs-lookup"><span data-stu-id="e61b8-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="e61b8-158">使用 **-UserPrincipalName**參數識別的帳戶，並設定或變更與其他參數的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="e61b8-158">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="e61b8-159">以下是最常見的參數清單。</span><span class="sxs-lookup"><span data-stu-id="e61b8-159">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="e61b8-160">-City"\<縣/市 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="e61b8-161">-Country"\<國家/地區 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="e61b8-162">-Department"\<部門 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="e61b8-163">-DisplayName"\<完整使用者 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="e61b8-164">-Fax"\<傳真 number> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="e61b8-165">-FirstName"\<使用者第一張 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="e61b8-166">-LastName"\<使用者上次 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="e61b8-167">-MobilePhone"\<行動電話 number> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="e61b8-168">-Office"\<office location> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="e61b8-169">-PhoneNumber"\<辦公室電話 number> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="e61b8-170">-PostalCode"\<郵遞區號 code> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="e61b8-171">-PreferredLanguage"\<language> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="e61b8-172">-State"\<狀態 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="e61b8-173">-StreetAddress"\<街道 address> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="e61b8-174">-Title"\<標題 name> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="e61b8-175">-UsageLocation"\<2 個字元的國家或地區 code> 」</span><span class="sxs-lookup"><span data-stu-id="e61b8-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="e61b8-176">這是 ISO 3166-1 alpha-2http (A2) 兩個字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="e61b8-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="e61b8-177">如需其他參數，請參閱[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="e61b8-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="e61b8-178">若要查看您的所有使用者的使用者主體名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="e61b8-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="e61b8-179">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="e61b8-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e61b8-180">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-181">依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-182">顯示 User Principal Name 屬性的每個帳戶 ( **Select-object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="e61b8-183">一次 （**更多**），顯示其一個畫面。</span><span class="sxs-lookup"><span data-stu-id="e61b8-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="e61b8-184">此命令會列出您的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="e61b8-184">This command will list all of your accounts.</span></span> <span data-ttu-id="e61b8-185">如果您想要顯示使用者主體名稱根據其顯示帳戶名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e61b8-185">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e61b8-186">此範例會顯示名為 Caleb Sills 的使用者的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="e61b8-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="e61b8-187">藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="e61b8-187">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="e61b8-188">以下是將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱，而不是其使用者主體名稱範例：</span><span class="sxs-lookup"><span data-stu-id="e61b8-188">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="e61b8-189">變更所有使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="e61b8-189">Change properties for all user accounts</span></span>

<span data-ttu-id="e61b8-190">若要變更的所有使用者的內容，您可以使用**Get-msoluser**和**Set-msoluser** cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="e61b8-190">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="e61b8-191">下列範例會變更為法國所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="e61b8-191">The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="e61b8-192">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="e61b8-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e61b8-193">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-194">將使用者位置設定為法國 ( **Set-msoluser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="e61b8-195">變更一組特定的使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="e61b8-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="e61b8-196">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-msoluser**、 **Where-object cmdlet**，以及**Set-msoluser** cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="e61b8-196">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="e61b8-197">下列範例會變更為法國會計部門中的所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="e61b8-197">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="e61b8-198">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="e61b8-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e61b8-199">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-200">尋找所有的使用者帳戶具有其 Department 屬性設為 「 會計 」 ( **Where-object {$_。Department-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e61b8-201">將使用者位置設定為法國 ( **Set-msoluser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="e61b8-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="e61b8-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e61b8-202">See also</span></span>

[<span data-ttu-id="e61b8-203">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="e61b8-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e61b8-204">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="e61b8-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e61b8-205">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e61b8-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
