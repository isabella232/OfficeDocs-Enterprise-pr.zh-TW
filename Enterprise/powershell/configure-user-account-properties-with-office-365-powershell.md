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
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要： 使用 Office 365 PowerShell 來設定 Office 365 租用戶中的個別或多個使用者帳戶的內容。
ms.openlocfilehash: b9cd529cd5881d522285ff43a60e954bc9ebd193
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072235"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="c5a81-103">使用 Office 365 PowerShell 中設定使用者帳戶屬性</span><span class="sxs-lookup"><span data-stu-id="c5a81-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="c5a81-104">雖然您可以使用 Microsoft 365 系統管理中心來設定您的 Office 365 租用戶的使用者帳戶的內容，也可以使用 Office 365 PowerShell 並執行動作無法在系統管理中心的一些事項。</span><span class="sxs-lookup"><span data-stu-id="c5a81-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c5a81-105">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5a81-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c5a81-106">若要設定使用者帳戶的屬性與 PowerShell 的 Azure Active Directory 針對 Graph 模組，您可以使用[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)指令程式，並指定要設定或變更的內容。</span><span class="sxs-lookup"><span data-stu-id="c5a81-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="c5a81-107">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="c5a81-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="c5a81-108">變更特定使用者帳戶內容</span><span class="sxs-lookup"><span data-stu-id="c5a81-108">Change properties for a specific user account</span></span>

<span data-ttu-id="c5a81-109">您使用的 **-ObjectID**參數來識別帳戶及設定或變更與其他參數的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="c5a81-109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="c5a81-110">以下是最常見的參數清單。</span><span class="sxs-lookup"><span data-stu-id="c5a81-110">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="c5a81-111">-Department"\<部門名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="c5a81-112">-DisplayName"\<完整的使用者名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="c5a81-113">-FacsimilieTelephoneNumber"\<傳真號碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="c5a81-114">-GivenName"\<使用者名字> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="c5a81-115">-姓氏"\<使用者上次名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="c5a81-116">-行動"\<行動電話號碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="c5a81-117">-JobTitle"\<工作標題> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="c5a81-118">-PreferredLanguage"\<語言> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="c5a81-119">-StreetAddress"\<路/街> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="c5a81-120">-City"\<縣/市名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="c5a81-121">-State"\<狀態命名> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="c5a81-122">-PostalCode"\<郵遞區號> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="c5a81-123">-Country"\<國家/地區名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="c5a81-124">-TelephoneNumber"\<辦公室電話號碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="c5a81-125">-UsageLocation"\<2 個字元國家或地區程式碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="c5a81-126">這是 ISO 3166-1 alpha-2http (A2) 兩個字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="c5a81-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="c5a81-127">如需其他參數，請參閱[設定 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="c5a81-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="c5a81-128">若要顯示您的使用者帳戶的使用者主體名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c5a81-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="c5a81-129">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="c5a81-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c5a81-130">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-131">依字母順序排序清單中的使用者主體名稱 (**排序 UserPrincipalName** ) 並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-132">顯示 User Principal Name 屬性的每個帳戶 (**選取 UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="c5a81-133">一次 （**更多**），顯示其一個畫面。</span><span class="sxs-lookup"><span data-stu-id="c5a81-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="c5a81-134">此命令會列出您的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5a81-134">This command will list all of your accounts.</span></span> <span data-ttu-id="c5a81-135">如果您想要顯示使用者主體名稱根據其顯示帳戶名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c5a81-135">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c5a81-136">此範例會顯示顯示名稱為 Caleb Sills 的使用者帳戶的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="c5a81-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c5a81-137">藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5a81-137">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="c5a81-138">以下是將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱，而不是其使用者主體名稱範例：</span><span class="sxs-lookup"><span data-stu-id="c5a81-138">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="c5a81-139">變更所有使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="c5a81-139">Change properties for all user accounts</span></span>

<span data-ttu-id="c5a81-140">若要變更的所有使用者的內容，您可以使用**Get-AzureADUser**和**設定 AzureADUser**指令程式的組合。</span><span class="sxs-lookup"><span data-stu-id="c5a81-140">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="c5a81-141">下列範例會變更為法國所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="c5a81-141">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="c5a81-142">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="c5a81-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c5a81-143">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-144">將使用者位置設定為法國 (**組 AzureADUser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="c5a81-145">變更一組特定的使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="c5a81-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="c5a81-146">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-AzureADUser**、**位置**及**組 AzureADUser**指令程式的組合。</span><span class="sxs-lookup"><span data-stu-id="c5a81-146">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="c5a81-147">下列範例會變更為法國會計部門中的所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="c5a81-147">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="c5a81-148">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="c5a81-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c5a81-149">取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-150">尋找所有使用者帳戶具有 Department 屬性設為"Accounting"(**其中 {$_。Department-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-151">將使用者位置設定為法國 (**組 AzureADUser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c5a81-152">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="c5a81-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c5a81-153">若要設定使用者帳戶的屬性與 Microsoft Azure Active Directory 模組的 Windows PowerShell，您可以使用**Set-msoluser** cmdlet，並指定要設定或變更的內容。</span><span class="sxs-lookup"><span data-stu-id="c5a81-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="c5a81-154">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="c5a81-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="c5a81-155">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c5a81-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c5a81-156">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="c5a81-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="c5a81-157">變更特定使用者帳戶內容</span><span class="sxs-lookup"><span data-stu-id="c5a81-157">Change properties for a specific user account</span></span>

<span data-ttu-id="c5a81-158">若要設定特定的使用者帳戶的內容，您可以使用[Set-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet，並指定要設定或變更的內容。</span><span class="sxs-lookup"><span data-stu-id="c5a81-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="c5a81-159">使用 **-UserPrincipalName**參數識別的帳戶，並設定或變更與其他參數的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="c5a81-159">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="c5a81-160">以下是最常見的參數清單。</span><span class="sxs-lookup"><span data-stu-id="c5a81-160">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="c5a81-161">-City"\<縣/市名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="c5a81-162">-Country"\<國家/地區名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="c5a81-163">-Department"\<部門名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="c5a81-164">-DisplayName"\<完整的使用者名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="c5a81-165">-Fax"\<傳真號碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="c5a81-166">-FirstName"\<使用者名字> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="c5a81-167">-LastName"\<使用者上次名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="c5a81-168">-MobilePhone"\<行動電話號碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="c5a81-169">-Office"\<辦公室位置> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="c5a81-170">-PhoneNumber"\<辦公室電話號碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="c5a81-171">-PostalCode"\<郵遞區號> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="c5a81-172">-PreferredLanguage"\<語言> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="c5a81-173">-State"\<狀態命名> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="c5a81-174">-StreetAddress"\<路/街> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="c5a81-175">-Title"\<標題名稱> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="c5a81-176">-UsageLocation"\<2 個字元國家或地區程式碼> 」</span><span class="sxs-lookup"><span data-stu-id="c5a81-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="c5a81-177">這是 ISO 3166-1 alpha-2http (A2) 兩個字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="c5a81-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="c5a81-178">如需其他參數，請參閱[Set-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) 。</span><span class="sxs-lookup"><span data-stu-id="c5a81-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="c5a81-179">若要查看您的所有使用者的使用者主體名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="c5a81-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="c5a81-180">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="c5a81-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c5a81-181">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-182">依字母順序排序清單中的使用者主體名稱 (**排序 UserPrincipalName** ) 並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-183">顯示 User Principal Name 屬性的每個帳戶 (**選取 UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="c5a81-184">一次 （**更多**），顯示其一個畫面。</span><span class="sxs-lookup"><span data-stu-id="c5a81-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="c5a81-185">此命令會列出您的所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5a81-185">This command will list all of your accounts.</span></span> <span data-ttu-id="c5a81-186">如果您想要顯示使用者主體名稱根據其顯示帳戶名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c5a81-186">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c5a81-187">此範例會顯示名為 Caleb Sills 的使用者的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="c5a81-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="c5a81-188">藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5a81-188">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="c5a81-189">以下是將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱，而不是其使用者主體名稱範例：</span><span class="sxs-lookup"><span data-stu-id="c5a81-189">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="c5a81-190">變更所有使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="c5a81-190">Change properties for all user accounts</span></span>

<span data-ttu-id="c5a81-191">若要變更的所有使用者的內容，您可以使用**Get-msoluser**和**Set-msoluser** cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="c5a81-191">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="c5a81-192">下列範例會變更為法國所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="c5a81-192">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="c5a81-193">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="c5a81-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c5a81-194">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-195">將使用者位置設定為法國 ( **Set-msoluser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="c5a81-196">變更一組特定的使用者帳戶的內容</span><span class="sxs-lookup"><span data-stu-id="c5a81-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="c5a81-197">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-msoluser**、**位置**及**Set-msoluser** cmdlet 的組合。</span><span class="sxs-lookup"><span data-stu-id="c5a81-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="c5a81-198">下列範例會變更為法國會計部門中的所有使用者的使用狀況位置：</span><span class="sxs-lookup"><span data-stu-id="c5a81-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="c5a81-199">此命令會指示 Office 365 PowerShell 來：</span><span class="sxs-lookup"><span data-stu-id="c5a81-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="c5a81-200">取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊，並將它傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-201">尋找所有使用者帳戶具有 Department 屬性設為"Accounting"(**其中 {$_。Department-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c5a81-202">將使用者位置設定為法國 ( **Set-msoluser-UsageLocation"FR"** )。</span><span class="sxs-lookup"><span data-stu-id="c5a81-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="c5a81-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5a81-203">See also</span></span>

[<span data-ttu-id="c5a81-204">管理使用者帳戶、 授權及使用 Office 365 PowerShell 的群組</span><span class="sxs-lookup"><span data-stu-id="c5a81-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c5a81-205">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="c5a81-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c5a81-206">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5a81-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
