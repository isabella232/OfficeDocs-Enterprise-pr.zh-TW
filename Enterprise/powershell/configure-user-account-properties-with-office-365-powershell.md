---
title: 使用 Office 365 PowerShell 中設定使用者帳戶屬性
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 摘要： 使用 Office 365 PowerShell Office 365 租用戶中設定的個人或多個使用者帳戶屬性。
ms.openlocfilehash: 4db63482fdcc1d6cb186e663fd55c13186b33813
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546484"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="41f8c-103">使用 Office 365 PowerShell 中設定使用者帳戶屬性</span><span class="sxs-lookup"><span data-stu-id="41f8c-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="41f8c-104">**摘要：** 使用 Office 365 PowerShell 來設定您的 Office 365 租用戶中的個人或多個使用者帳戶的屬性。</span><span class="sxs-lookup"><span data-stu-id="41f8c-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="41f8c-105">雖然您可以使用 Office 365 系統管理中心來設定您的 Office 365 租用戶的使用者帳戶的內容，也可以使用 Office 365 PowerShell 並執行一些無法在 Office 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="41f8c-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="41f8c-106">使用 Azure Active Directory PowerShell 圖模組</span><span class="sxs-lookup"><span data-stu-id="41f8c-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="41f8c-107">若要使用 Azure Active Directory PowerShell 圖模組的設定的使用者帳戶屬性，您使用[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)指令程式，並指定來設定或變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="41f8c-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="41f8c-108">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="41f8c-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="41f8c-109">變更特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="41f8c-109">Change properties for a specific user account</span></span>

<span data-ttu-id="41f8c-p101">您使用 **-ObjectID**參數來識別帳戶及設定或變更的額外參數的特定屬性。這裡是清單的最常見的參數。</span><span class="sxs-lookup"><span data-stu-id="41f8c-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="41f8c-112">-部門"\<部門名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="41f8c-113">-DisplayName"\<完整的使用者名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="41f8c-114">-FacsimilieTelephoneNumber"\<傳真號碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="41f8c-115">-GivenName"\<使用者名字 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="41f8c-116">-姓氏"\<使用者上次名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="41f8c-117">-行動"\<行動電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="41f8c-118">-JobTitle"\<職稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="41f8c-119">-PreferredLanguage"\<語言 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="41f8c-120">-StreetAddress"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="41f8c-121">--市/鎮"\<城市名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="41f8c-122">-State"\<狀態名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="41f8c-123">-PostalCode"\<郵遞區號 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="41f8c-124">-國家"\<國家/地區名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="41f8c-125">-TelephoneNumber"\<辦公室電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="41f8c-126">-UsageLocation"\<2 個字元的國家或地區的程式碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="41f8c-127">這是 ISO 3166-1 alpha-2 (A2) 雙字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="41f8c-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="41f8c-128">請參閱額外的參數[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="41f8c-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="41f8c-129">若要顯示您的使用者帳戶的使用者主體名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="41f8c-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="41f8c-130">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="41f8c-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41f8c-131">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-132">依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-133">顯示使用者主體名稱屬性的每個帳戶 ( **Select-object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="41f8c-134">顯示一個畫面 （**更多**） 一次。</span><span class="sxs-lookup"><span data-stu-id="41f8c-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="41f8c-p102">此命令會列出所有的帳戶。如果您想要顯示根據其帳戶的使用者主體名稱名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="41f8c-137">本範例會顯示與 caleb Sills Sills 的顯示名稱之使用者帳戶的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="41f8c-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="41f8c-p103">藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。以下是範例將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱而不是其使用者主體名稱：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="41f8c-140">變更所有使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="41f8c-140">Change properties for all user accounts</span></span>

<span data-ttu-id="41f8c-p104">若要變更的所有使用者的屬性，您可以使用**Get AzureADUser**和**設定 AzureADUser**指令程式的組合。下列範例會將所有使用者的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="41f8c-143">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="41f8c-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41f8c-144">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-145">法國 (**組 AzureADUser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="41f8c-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="41f8c-146">變更一組特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="41f8c-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="41f8c-p105">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get AzureADUser**、**位置**及**組 AzureADUser** cmdlet 的組合。下列範例會將會計部門的所有使用者的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="41f8c-149">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="41f8c-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41f8c-150">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-151">尋找所有已設定為"Accounting"其部門屬性的使用者帳戶 (**其中 {$_。部門-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-152">法國 (**組 AzureADUser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="41f8c-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="41f8c-153">使用 Windows PowerShell 的 Microsoft Azure Active Directory 模組</span><span class="sxs-lookup"><span data-stu-id="41f8c-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="41f8c-154">與 Microsoft Azure Active Directory Module for Windows PowerShell 設定的使用者帳戶內容，您可以使用 Set-msoluser cmdlet 並指定來設定或變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="41f8c-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="41f8c-155">第一筆、[連線至您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="41f8c-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="41f8c-156">變更特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="41f8c-156">Change properties for a specific user account</span></span>

<span data-ttu-id="41f8c-157">若要設定特定的使用者帳戶的屬性，您可以使用[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 並指定來設定或變更的屬性。</span><span class="sxs-lookup"><span data-stu-id="41f8c-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="41f8c-p106">您使用 **-UserPrincipalName**參數來識別帳戶及設定或變更的額外參數的特定屬性。這裡是清單的最常見的參數。</span><span class="sxs-lookup"><span data-stu-id="41f8c-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="41f8c-160">--市/鎮"\<城市名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="41f8c-161">-國家"\<國家/地區名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="41f8c-162">-部門"\<部門名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="41f8c-163">-DisplayName"\<完整的使用者名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="41f8c-164">-傳真"\<傳真號碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="41f8c-165">-FirstName"\<使用者名字 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="41f8c-166">-LastName"\<使用者上次名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="41f8c-167">-MobilePhone"\<行動電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="41f8c-168">Office"\<辦公室位置 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="41f8c-169">-[Phonenumber]"\<辦公室電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="41f8c-170">-PostalCode"\<郵遞區號 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="41f8c-171">-PreferredLanguage"\<語言 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="41f8c-172">-State"\<狀態名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="41f8c-173">-StreetAddress"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="41f8c-174">-Title"\<標題名稱 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="41f8c-175">-UsageLocation"\<2 個字元的國家或地區的程式碼 >"</span><span class="sxs-lookup"><span data-stu-id="41f8c-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="41f8c-176">這是 ISO 3166-1 alpha-2 (A2) 雙字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="41f8c-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="41f8c-177">請參閱[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx)額外的參數。</span><span class="sxs-lookup"><span data-stu-id="41f8c-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="41f8c-178">若要查看使用者主體名稱的所有使用者，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="41f8c-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="41f8c-179">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="41f8c-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41f8c-180">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-181">依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-182">顯示使用者主體名稱屬性的每個帳戶 ( **Select-object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="41f8c-183">顯示一個畫面 （**更多**） 一次。</span><span class="sxs-lookup"><span data-stu-id="41f8c-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="41f8c-p107">此命令會列出所有的帳戶。如果您想要顯示根據其帳戶的使用者主體名稱名稱 （第一個及最後一個名稱）、 填滿下 **$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="41f8c-186">本範例會顯示名為 caleb Sills Sills 使用者的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="41f8c-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="41f8c-p108">藉由使用 **$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。以下是範例將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱而不是其使用者主體名稱：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="41f8c-189">變更所有使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="41f8c-189">Change properties for all user accounts</span></span>

<span data-ttu-id="41f8c-p109">若要變更所有使用者的內容，您可以使用 **Get-MsolUser** 和 **Set-MsolUser** Cmdlet 的組合。下列範例會將所有使用者的使用位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="41f8c-192">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="41f8c-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41f8c-193">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-194">法國 ( **Set-msoluser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="41f8c-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="41f8c-195">變更一組特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="41f8c-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="41f8c-p110">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-msoluser**、 **Where-object**和**Set-msoluser** cmdlet 的組合。下列範例會將會計部門的所有使用者的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="41f8c-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="41f8c-198">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="41f8c-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41f8c-199">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-200">找到的所有使用者帳戶具有其部門屬性設定為 「 會計 」 ( **Where-object {$_。部門-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="41f8c-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41f8c-201">法國 ( **Set-msoluser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="41f8c-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="41f8c-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41f8c-202">See also</span></span>

[<span data-ttu-id="41f8c-203">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="41f8c-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="41f8c-204">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="41f8c-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="41f8c-205">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="41f8c-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
