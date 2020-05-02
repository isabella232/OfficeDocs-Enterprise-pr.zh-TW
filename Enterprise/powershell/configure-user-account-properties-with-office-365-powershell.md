---
title: 使用 Office 365 PowerShell 中設定使用者帳戶屬性
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要：使用 Office 365 PowerShell 來設定 Office 365 租使用者中個別或多個使用者帳戶的屬性。
ms.openlocfilehash: 5748bd382357168e4184754fb49fb7304e2d2474
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004716"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="178b0-103">使用 Office 365 PowerShell 中設定使用者帳戶屬性</span><span class="sxs-lookup"><span data-stu-id="178b0-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="178b0-104">雖然您可以使用 Microsoft 365 系統管理中心來設定 Office 365 租使用者帳戶的屬性，但您也可以使用 Office 365 PowerShell，並執行系統管理中心的某些工作。</span><span class="sxs-lookup"><span data-stu-id="178b0-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="178b0-105">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="178b0-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="178b0-106">若要使用適用于 Graph 模組的 Azure Active Directory PowerShell，設定使用者帳戶的屬性，您可以使用[AzureADUser 指令程式](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)，並指定要設定或變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="178b0-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="178b0-107">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="178b0-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="178b0-108">變更特定使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="178b0-108">Change properties for a specific user account</span></span>

<span data-ttu-id="178b0-109">您可以使用 **-ObjectID**參數識別帳戶，並設定或變更具有其他參數的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="178b0-109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="178b0-110">以下是最常見的參數清單。</span><span class="sxs-lookup"><span data-stu-id="178b0-110">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="178b0-111">-部門 "\<部門名稱>"</span><span class="sxs-lookup"><span data-stu-id="178b0-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="178b0-112">-DisplayName "\<完整使用者名稱>"</span><span class="sxs-lookup"><span data-stu-id="178b0-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="178b0-113">-FacsimilieTelephoneNumber 「\<傳真號碼></span><span class="sxs-lookup"><span data-stu-id="178b0-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="178b0-114">-GivenName "\<user first name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="178b0-115">-姓 "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="178b0-116">-Mobile "\<mobile phone number>"</span><span class="sxs-lookup"><span data-stu-id="178b0-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="178b0-117">-JobTitle "\<職稱>"</span><span class="sxs-lookup"><span data-stu-id="178b0-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="178b0-118">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="178b0-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="178b0-119">-StreetAddress "\<街道位址>"</span><span class="sxs-lookup"><span data-stu-id="178b0-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="178b0-120">-城市「\<城市名稱></span><span class="sxs-lookup"><span data-stu-id="178b0-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="178b0-121">-State "\<state name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="178b0-122">-PostalCode "\<郵遞區號>"</span><span class="sxs-lookup"><span data-stu-id="178b0-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="178b0-123">-國家/\<地區 "country name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="178b0-124">-TelephoneNumber "\<office phone number>"</span><span class="sxs-lookup"><span data-stu-id="178b0-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="178b0-125">-UsageLocation "\<2 個字元的國家或地區代碼>"</span><span class="sxs-lookup"><span data-stu-id="178b0-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="178b0-126">這是 ISO 3166-1 Alpha-2 （A2）雙字母的國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="178b0-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="178b0-127">請參閱[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for 其他參數。</span><span class="sxs-lookup"><span data-stu-id="178b0-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="178b0-128">若要為您的使用者帳戶顯示使用者主要名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="178b0-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="178b0-129">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="178b0-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="178b0-130">取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-131">依字母順序排序使用者主體名稱清單（ **Sort UserPrincipalName** ），並將其傳送至下一個**|** 命令（）。</span><span class="sxs-lookup"><span data-stu-id="178b0-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-132">只顯示每個帳戶的使用者主體名稱屬性（**選取 UserPrincipalName** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="178b0-133">一次顯示一屏（**更多**）。</span><span class="sxs-lookup"><span data-stu-id="178b0-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="178b0-134">這個命令會列出您的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="178b0-134">This command will list all of your accounts.</span></span> <span data-ttu-id="178b0-135">如果您想要根據其顯示名稱（名字和姓氏）顯示帳戶的使用者主要名稱，請填入下列的 **$userName**變數（移除\<和 > 字元），然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="178b0-135">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="178b0-136">本範例會顯示名稱為 Caleb Sills 帳戶的使用者帳戶使用者主要名稱。</span><span class="sxs-lookup"><span data-stu-id="178b0-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="178b0-137">使用 **$upn**變數，您可以根據其顯示名稱來變更個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="178b0-137">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="178b0-138">以下範例會將 Belinda Newman 的使用位置設定為法國，但指定其顯示名稱，而不是其使用者主要名稱：</span><span class="sxs-lookup"><span data-stu-id="178b0-138">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="178b0-139">變更所有使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="178b0-139">Change properties for all user accounts</span></span>

<span data-ttu-id="178b0-140">若要變更所有使用者的屬性，您可以使用**AzureADUser**和**AzureADUser** Cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="178b0-140">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="178b0-141">下列範例會將所有使用者的使用位置變更為華北：</span><span class="sxs-lookup"><span data-stu-id="178b0-141">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="178b0-142">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="178b0-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="178b0-143">取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-144">將使用者位置設定為法國（ **AzureADUser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="178b0-145">變更特定使用者帳戶組的屬性</span><span class="sxs-lookup"><span data-stu-id="178b0-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="178b0-146">若要變更特定使用者帳戶集的屬性，您可以使用**AzureADUser**、 **Where**及**AzureADUser** Cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="178b0-146">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="178b0-147">下列範例會將會計部門中所有使用者的使用量位置變更為華北：</span><span class="sxs-lookup"><span data-stu-id="178b0-147">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="178b0-148">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="178b0-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="178b0-149">取得使用者帳戶（ **AzureADUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-150">尋找其部門屬性設定為 "記帳" 的所有使用者帳戶（**其中 {$ _）。部門-eq "記帳"}** ）並將結果資訊傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-151">將使用者位置設定為法國（ **AzureADUser-UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="178b0-152">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="178b0-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="178b0-153">若要使用 Microsoft Azure Active Directory Module for Windows PowerShell 設定使用者帳戶的屬性，您可以使用**Set-MsolUser** Cmdlet，並指定要設定或變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="178b0-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="178b0-154">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="178b0-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="178b0-155">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="178b0-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="178b0-156">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="178b0-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="178b0-157">變更特定使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="178b0-157">Change properties for a specific user account</span></span>

<span data-ttu-id="178b0-158">若要設定特定使用者帳戶的屬性，您可以使用[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) Cmdlet，並指定要設定或變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="178b0-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="178b0-159">您可以使用 **-UserPrincipalName**參數來識別帳戶，並設定或變更具有其他參數的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="178b0-159">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="178b0-160">以下是最常見的參數清單。</span><span class="sxs-lookup"><span data-stu-id="178b0-160">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="178b0-161">-城市「\<城市名稱></span><span class="sxs-lookup"><span data-stu-id="178b0-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="178b0-162">-國家/\<地區 "country name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="178b0-163">-部門 "\<部門名稱>"</span><span class="sxs-lookup"><span data-stu-id="178b0-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="178b0-164">-DisplayName "\<完整使用者名稱>"</span><span class="sxs-lookup"><span data-stu-id="178b0-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="178b0-165">-傳真 "\<傳真號碼>"</span><span class="sxs-lookup"><span data-stu-id="178b0-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="178b0-166">-FirstName "\<user first name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="178b0-167">-LastName "\<user last name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="178b0-168">-MobilePhone "\<行動電話號碼>"</span><span class="sxs-lookup"><span data-stu-id="178b0-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="178b0-169">-Office "\<office 位置>"</span><span class="sxs-lookup"><span data-stu-id="178b0-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="178b0-170">-PhoneNumber "\<office phone number>"</span><span class="sxs-lookup"><span data-stu-id="178b0-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="178b0-171">-PostalCode "\<郵遞區號>"</span><span class="sxs-lookup"><span data-stu-id="178b0-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="178b0-172">-PreferredLanguage "\<language>"</span><span class="sxs-lookup"><span data-stu-id="178b0-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="178b0-173">-State "\<state name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="178b0-174">-StreetAddress "\<街道位址>"</span><span class="sxs-lookup"><span data-stu-id="178b0-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="178b0-175">-Title "\<title name>"</span><span class="sxs-lookup"><span data-stu-id="178b0-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="178b0-176">-UsageLocation "\<2 個字元的國家或地區代碼>"</span><span class="sxs-lookup"><span data-stu-id="178b0-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="178b0-177">這是 ISO 3166-1 Alpha-2 （A2）雙字母的國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="178b0-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="178b0-178">如需其他參數，請參閱[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 。</span><span class="sxs-lookup"><span data-stu-id="178b0-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="178b0-179">若要查看所有使用者的使用者主要名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="178b0-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="178b0-180">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="178b0-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="178b0-181">取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-182">依字母順序排序使用者主體名稱清單（ **Sort UserPrincipalName** ），並將其傳送至下一個**|** 命令（）。</span><span class="sxs-lookup"><span data-stu-id="178b0-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-183">只顯示每個帳戶的使用者主體名稱屬性（**選取 UserPrincipalName** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="178b0-184">一次顯示一屏（**更多**）。</span><span class="sxs-lookup"><span data-stu-id="178b0-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="178b0-185">這個命令會列出您的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="178b0-185">This command will list all of your accounts.</span></span> <span data-ttu-id="178b0-186">如果您想要根據其顯示名稱（名字和姓氏）顯示帳戶的使用者主要名稱，請填入下列的 **$userName**變數（移除\<和 > 字元），然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="178b0-186">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="178b0-187">此範例會顯示名為 Caleb Sills 帳戶之使用者的使用者主要名稱。</span><span class="sxs-lookup"><span data-stu-id="178b0-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="178b0-188">使用 **$upn**變數，您可以根據其顯示名稱來變更個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="178b0-188">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="178b0-189">以下範例會將 Belinda Newman 的使用位置設定為法國，但指定其顯示名稱，而不是其使用者主要名稱：</span><span class="sxs-lookup"><span data-stu-id="178b0-189">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="178b0-190">變更所有使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="178b0-190">Change properties for all user accounts</span></span>

<span data-ttu-id="178b0-191">若要變更所有使用者的屬性，您可以使用**Get-MsolUser**和**Set-MsolUser** Cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="178b0-191">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="178b0-192">下列範例會將所有使用者的使用位置變更為華北：</span><span class="sxs-lookup"><span data-stu-id="178b0-192">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="178b0-193">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="178b0-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="178b0-194">取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-195">將使用者位置設定為法國（ **Set-MsolUser UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="178b0-196">變更特定使用者帳戶組的屬性</span><span class="sxs-lookup"><span data-stu-id="178b0-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="178b0-197">若要變更特定使用者帳戶集的屬性，您可以使用**Get-MsolUser**、 **Where**及**Set-MsolUser** Cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="178b0-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="178b0-198">下列範例會將會計部門中所有使用者的使用量位置變更為華北：</span><span class="sxs-lookup"><span data-stu-id="178b0-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="178b0-199">這個命令會指示 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="178b0-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="178b0-200">取得使用者帳戶（ **Get-MsolUser** ）上的所有資訊，並將其傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-201">尋找其部門屬性設定為 "記帳" 的所有使用者帳戶（**其中 {$ _）。部門-eq "記帳"}** ）並將結果資訊傳送至下一個命令（ **|** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="178b0-202">將使用者位置設定為法國（ **Set-MsolUser UsageLocation "FR"** ）。</span><span class="sxs-lookup"><span data-stu-id="178b0-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="178b0-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="178b0-203">See also</span></span>

[<span data-ttu-id="178b0-204">使用 Office 365 管理使用者帳戶、授權和群組 PowerShell</span><span class="sxs-lookup"><span data-stu-id="178b0-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="178b0-205">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="178b0-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="178b0-206">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="178b0-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
