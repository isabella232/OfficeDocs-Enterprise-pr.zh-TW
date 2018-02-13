---
title: "使用 Office 365 PowerShell 中設定使用者帳戶屬性"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, Ent_Office_Other, PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "摘要： 使用 Office 365 PowerShell Office 365 租用戶中設定的個人或多個使用者帳戶屬性。"
ms.openlocfilehash: 65857511886534e18ba3e67b79ab4d74a0119568
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="36416-103">使用 Office 365 PowerShell 中設定使用者帳戶屬性</span><span class="sxs-lookup"><span data-stu-id="36416-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="36416-104">**摘要：**使用 Office 365 PowerShell 來設定您的 Office 365 租用戶中的個人或多個使用者帳戶的屬性。</span><span class="sxs-lookup"><span data-stu-id="36416-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="36416-105">雖然您可以使用 Office 365 系統管理中心來設定您的 Office 365 租用戶的使用者帳戶的內容，也可以使用 Office 365 PowerShell 並執行一些無法在 Office 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="36416-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="36416-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="36416-106">Before you begin</span></span>

<span data-ttu-id="36416-p101">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="36416-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="36416-109">變更特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="36416-109">Change properties for a specific user account</span></span>

<span data-ttu-id="36416-p102">若要設定特定的使用者帳戶的屬性，您可以使用[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet 並指定來設定或變更的屬性。此範例命令會將 Belinda Newman 的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="36416-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="36416-p103">您使用**-UserPrincipalName**參數來識別帳戶及設定或變更的額外參數的特定屬性。這裡是清單的最常見的參數。</span><span class="sxs-lookup"><span data-stu-id="36416-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="36416-114">--市/鎮"\<城市名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="36416-115">-國家"\<國家/地區名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="36416-116">-部門"\<部門名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="36416-117">-DisplayName"\<完整的使用者名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="36416-118">-傳真"\<傳真號碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="36416-119">-FirstName"\<使用者名字 >"</span><span class="sxs-lookup"><span data-stu-id="36416-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="36416-120">-LastName"\<使用者上次名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="36416-121">-MobilePhone"\<行動電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="36416-122">Office"\<辦公室位置 >"</span><span class="sxs-lookup"><span data-stu-id="36416-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="36416-123">-[Phonenumber]"\<辦公室電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="36416-124">-PostalCode"\<郵遞區號 >"</span><span class="sxs-lookup"><span data-stu-id="36416-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="36416-125">-PreferredLanguage"\<語言 >"</span><span class="sxs-lookup"><span data-stu-id="36416-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="36416-126">-State"\<狀態名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="36416-127">-StreetAddress"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="36416-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="36416-128">-Title"\<標題名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="36416-129">-UsageLocation"\<2 個字元的國家或地區的程式碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="36416-130">這是 ISO 3166-1 alpha-2 (A2) 雙字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="36416-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="36416-131">請參閱[Set-msoluser](https://msdn.microsoft.com/library/azure/dn194136.aspx)額外的參數。</span><span class="sxs-lookup"><span data-stu-id="36416-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="36416-132">若要查看使用者主體名稱的所有使用者，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="36416-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="36416-133">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="36416-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36416-134">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-135">依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-136">顯示使用者主體名稱屬性的每個帳戶 ( **Select-object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="36416-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="36416-137">顯示一個畫面 （**更多**） 一次。</span><span class="sxs-lookup"><span data-stu-id="36416-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="36416-p104">此命令會列出所有的帳戶。如果您想要顯示根據其帳戶的使用者主體名稱名稱 （第一個及最後一個名稱）、 填滿下**$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="36416-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36416-140">本範例會顯示名為 caleb Sills Sills 使用者的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="36416-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36416-p105">藉由使用**$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。以下是範例將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱而不是其使用者主體名稱：</span><span class="sxs-lookup"><span data-stu-id="36416-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="36416-143">變更所有使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="36416-143">Change properties for all user accounts</span></span>

<span data-ttu-id="36416-p106">若要變更的所有使用者的屬性，您可以使用**Get-msoluser**和**Set-msoluser** cmdlet 的組合。下列範例會將所有使用者的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="36416-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="36416-146">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="36416-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36416-147">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-148">法國 ( **Set-msoluser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="36416-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="36416-149">變更一組特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="36416-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="36416-p107">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get-msoluser**、 **Where-object**和**Set-msoluser** cmdlet 的組合。下列範例會將會計部門的所有使用者的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="36416-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="36416-152">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="36416-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36416-153">會取得所有使用者帳戶 ( **Get-msoluser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-154">找到的所有使用者帳戶具有其部門屬性設定為 「 會計 」 ( **Where-object {$_。部門-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-155">法國 ( **Set-msoluser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="36416-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="36416-156">顯示一個畫面 （**更多**） 一次。</span><span class="sxs-lookup"><span data-stu-id="36416-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="36416-157">使用 Azure Active Directory V2 PowerShell 模組來設定使用者帳戶屬性</span><span class="sxs-lookup"><span data-stu-id="36416-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="36416-p108">使用 Azure Active Directory V2 PowerShell 模組設定的使用者帳戶內容，您可以使用[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)指令程式並指定來設定或變更的屬性。但首先，您必須連線到您的訂閱。指示，請參閱[使用 Azure Active Directory V2 PowerShell 模組的連線](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="36416-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="36416-161">變更特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="36416-161">Change properties for a specific user account</span></span>

<span data-ttu-id="36416-162">此範例命令會將 Belinda Newman 的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="36416-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="36416-p109">您使用**-ObjectID**參數來識別帳戶及設定或變更的額外參數的特定屬性。這裡是清單的最常見的參數。</span><span class="sxs-lookup"><span data-stu-id="36416-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="36416-165">-部門"\<部門名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="36416-166">-DisplayName"\<完整的使用者名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="36416-167">-FacsimilieTelephoneNumber"\<傳真號碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="36416-168">-GivenName"\<使用者名字 >"</span><span class="sxs-lookup"><span data-stu-id="36416-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="36416-169">-姓氏"\<使用者上次名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="36416-170">-行動"\<行動電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="36416-171">-JobTitle"\<職稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="36416-172">-PreferredLanguage"\<語言 >"</span><span class="sxs-lookup"><span data-stu-id="36416-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="36416-173">-StreetAddress"\<街道地址 >"</span><span class="sxs-lookup"><span data-stu-id="36416-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="36416-174">--市/鎮"\<城市名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="36416-175">-State"\<狀態名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="36416-176">-PostalCode"\<郵遞區號 >"</span><span class="sxs-lookup"><span data-stu-id="36416-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="36416-177">-國家"\<國家/地區名稱 >"</span><span class="sxs-lookup"><span data-stu-id="36416-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="36416-178">-TelephoneNumber"\<辦公室電話號碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="36416-179">-UsageLocation"\<2 個字元的國家或地區的程式碼 >"</span><span class="sxs-lookup"><span data-stu-id="36416-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="36416-180">這是 ISO 3166-1 alpha-2 (A2) 雙字母國家或地區碼。</span><span class="sxs-lookup"><span data-stu-id="36416-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="36416-181">請參閱額外的參數[組 AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) 。</span><span class="sxs-lookup"><span data-stu-id="36416-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="36416-182">若要顯示您的使用者帳戶的使用者主體名稱，請執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="36416-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="36416-183">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="36416-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36416-184">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-185">依字母順序排序清單中的使用者主體名稱 ( **Sort 物件 UserPrincipalName** ) 並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-186">顯示使用者主體名稱屬性的每個帳戶 ( **Select-object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="36416-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="36416-187">顯示一個畫面 （**更多**） 一次。</span><span class="sxs-lookup"><span data-stu-id="36416-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="36416-p110">此命令會列出所有的帳戶。如果您想要顯示根據其帳戶的使用者主體名稱名稱 （第一個及最後一個名稱）、 填滿下**$userName**變數中 (移除\<和 > 字元)，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="36416-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36416-190">本範例會顯示名為 caleb Sills Sills 使用者的使用者主體名稱。</span><span class="sxs-lookup"><span data-stu-id="36416-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="36416-p111">藉由使用**$upn**變數，您可以變更其顯示名稱為基礎的個別帳戶。以下是範例將 Belinda Newman 的使用狀況位置設定為法國，但指定其顯示名稱而不是其使用者主體名稱：</span><span class="sxs-lookup"><span data-stu-id="36416-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="36416-193">變更所有使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="36416-193">Change properties for all user accounts</span></span>

<span data-ttu-id="36416-p112">若要變更的所有使用者的屬性，您可以使用**Get AzureADUser**和**設定 AzureADUser**指令程式的組合。下列範例會將所有使用者的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="36416-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="36416-196">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="36416-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36416-197">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-198">法國 (**組 AzureADUser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="36416-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="36416-199">變更一組特定的使用者帳戶的屬性</span><span class="sxs-lookup"><span data-stu-id="36416-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="36416-p113">若要變更的一組特定的使用者帳戶屬性，您可以使用**Get AzureADUser**、**位置**及**組 AzureADUser** cmdlet 的組合。下列範例會將會計部門的所有使用者的使用狀況位置變更為法國：</span><span class="sxs-lookup"><span data-stu-id="36416-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="36416-202">此命令會指示至 Office 365 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="36416-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="36416-203">會取得所有使用者帳戶 ( **Get AzureADUser** ) 上的資訊並將其傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-204">尋找所有已設定為"Accounting"其部門屬性的使用者帳戶 (**其中 {$_。部門-eq"Accounting"}** ) 並將產生的資訊傳送給下一個命令 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="36416-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="36416-205">法國 (**組 AzureADUser UsageLocation"FR-FR"** ) 來設定使用者位置。</span><span class="sxs-lookup"><span data-stu-id="36416-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="36416-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36416-206">See also</span></span>

#### 

[<span data-ttu-id="36416-207">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="36416-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="36416-208">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="36416-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="36416-209">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="36416-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

