---
title: 使用 PowerShell 建立 Microsoft 365 使用者帳戶
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 在本文中，您將瞭解如何使用 PowerShell 來建立使用者帳戶或多個 Microsoft 365 使用者帳戶。
ms.openlocfilehash: 2f4d7b42e68e3bd426ea73c8568e0c603af06dcb
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605989"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="cb4d0-103">使用 PowerShell 建立 Microsoft 365 使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cb4d0-103">Create Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="cb4d0-104">*本文適用於 Microsoft 365 企業版和 Office 365 企業版。*</span><span class="sxs-lookup"><span data-stu-id="cb4d0-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="cb4d0-105">您可以使用 Microsoft 365 的 PowerShell，有效地建立使用者帳戶，尤其是多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-105">You can use PowerShell for Microsoft 365 to efficiently create user accounts, especially multiple user accounts.</span></span> <span data-ttu-id="cb4d0-106">當您在 PowerShell 中建立使用者帳戶時，永遠都必須有特定的帳戶屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-106">When you create user accounts in PowerShell, certain account properties are always required.</span></span> <span data-ttu-id="cb4d0-107">其他屬性不一定用於建立帳戶，但卻很重要。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-107">Other properties aren't required to create the account, but are otherwise important.</span></span> <span data-ttu-id="cb4d0-108">下表說明這些屬性：</span><span class="sxs-lookup"><span data-stu-id="cb4d0-108">These properties are described in the following table:</span></span>
  
|<span data-ttu-id="cb4d0-109">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-109">**Property name**</span></span>|<span data-ttu-id="cb4d0-110">**必要？**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-110">**Required?**</span></span>|<span data-ttu-id="cb4d0-111">**描述**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="cb4d0-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="cb4d0-113">是</span><span class="sxs-lookup"><span data-stu-id="cb4d0-113">Yes</span></span>  <br/> |<span data-ttu-id="cb4d0-114">這是 Microsoft 365 服務中使用的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-114">This is the display name that's used in Microsoft 365 services.</span></span> <span data-ttu-id="cb4d0-115">例如，Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-115">For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="cb4d0-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="cb4d0-117">是</span><span class="sxs-lookup"><span data-stu-id="cb4d0-117">Yes</span></span>  <br/> |<span data-ttu-id="cb4d0-118">這是用來登入 Microsoft 365 服務的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-118">This is the account name that's used to sign in to Microsoft 365 services.</span></span> <span data-ttu-id="cb4d0-119">例如，CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-119">For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="cb4d0-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-120">**FirstName**</span></span> <br/> |<span data-ttu-id="cb4d0-121">否</span><span class="sxs-lookup"><span data-stu-id="cb4d0-121">No</span></span>  <br/> ||
|<span data-ttu-id="cb4d0-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-122">**LastName**</span></span> <br/> |<span data-ttu-id="cb4d0-123">否</span><span class="sxs-lookup"><span data-stu-id="cb4d0-123">No</span></span>  <br/> ||
|<span data-ttu-id="cb4d0-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="cb4d0-125">否</span><span class="sxs-lookup"><span data-stu-id="cb4d0-125">No</span></span>  <br/> |<span data-ttu-id="cb4d0-126">這是授權方案 (也稱為授權計畫或 SKU) ，可將可用的授權指派給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-126">This is the licensing plan (also known as the license plan or SKU) from which an available license is assigned to the user account.</span></span> <span data-ttu-id="cb4d0-127">授權會定義可供帳戶使用的 Microsoft 365 服務。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-127">The license defines the Microsoft 365 services that are available to account.</span></span> <span data-ttu-id="cb4d0-128">當您建立帳戶時，您不需要指派授權給使用者，但是需要授權才能存取 Microsoft 365 服務。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-128">You don't have to assign a license to a user when you create the account, but the account requires a license to access Microsoft 365 services.</span></span> <span data-ttu-id="cb4d0-129">建立使用者帳戶之後，您有 30 天的時間進行使用者帳戶授權。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-129">You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="cb4d0-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-130">**Password**</span></span> <br/> |<span data-ttu-id="cb4d0-131">否</span><span class="sxs-lookup"><span data-stu-id="cb4d0-131">No</span></span>  <br/> | <span data-ttu-id="cb4d0-p105">如果您未指定密碼，則會指派隨機密碼給使用者帳戶，並可在命令結果中看見此密碼。如果您指定密碼，該密碼必須是下列任三種類型的 8 到 16 個 ASCII 文字：小寫字母、大寫字母、數字和符號。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="cb4d0-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="cb4d0-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="cb4d0-135">否</span><span class="sxs-lookup"><span data-stu-id="cb4d0-135">No</span></span>  <br/> |<span data-ttu-id="cb4d0-136">這是有效的 ISO 3166-1 alpha-2 國碼。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-136">This is a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="cb4d0-137">例如，US 代表美國、FR 代表法國。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-137">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="cb4d0-138">提供此值很重要，因為某些國家/地區無法使用某些 Microsoft 365 服務，因此除非該帳戶已設定此值，否則您無法指派授權給使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-138">It's important to provide this value, because some Microsoft 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured.</span></span> <span data-ttu-id="cb4d0-139">如需詳細資訊，請參閱[關於授許可權制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-139">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="cb4d0-140">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4d0-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="cb4d0-141">首先，連線[至您的 Microsoft 365 租使用者](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="cb4d0-142">連接之後，使用下列語法來建立個別帳戶：</span><span class="sxs-lookup"><span data-stu-id="cb4d0-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="cb4d0-143">本範例會為名為 Caleb Sills 的美國使用者建立帳戶：</span><span class="sxs-lookup"><span data-stu-id="cb4d0-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="cb4d0-144">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="cb4d0-145">首先，連線[至您的 Microsoft 365 租使用者](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-145">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="cb4d0-146">建立個別使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cb4d0-146">Create an individual user account</span></span>

<span data-ttu-id="cb4d0-147">若要建立個別帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="cb4d0-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="cb4d0-148">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="cb4d0-149">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="cb4d0-150">若要列出可用的授權方案名稱，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="cb4d0-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="cb4d0-151">本範例會建立一個名為 Caleb Sills 的美國使用者帳戶，並指派 `contoso:ENTERPRISEPACK` (Office 365 企業版 E3) 授權方案的授權。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="cb4d0-152">建立多個使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cb4d0-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="cb4d0-p108">建立包含必要使用者帳戶資訊的逗點分隔值 (CSV) 檔案。例如：</span><span class="sxs-lookup"><span data-stu-id="cb4d0-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="cb4d0-155">CSV 檔案的第一列中的欄名稱和其順序都是任意的，但是請確定檔案的其餘部分中的資料符合欄名稱的順序，並在 PowerShell for Microsoft 365 命令中使用參數值的欄名。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the PowerShell for Microsoft 365 command.</span></span>
    
2. <span data-ttu-id="cb4d0-156">使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="cb4d0-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="cb4d0-157">本範例會從名為 C:\My Documents\NewAccounts.csv 的檔案建立使用者帳戶，並將結果記錄在名為 C:\My Documents\NewAccountResults.csv 的檔案中</span><span class="sxs-lookup"><span data-stu-id="cb4d0-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="cb4d0-158">檢閱輸出檔以查看結果。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-158">Review the output file to see the results.</span></span> <span data-ttu-id="cb4d0-159">我們未指定密碼，所以在輸出檔中會顯示 Microsoft 365 所產生的隨機密碼。</span><span class="sxs-lookup"><span data-stu-id="cb4d0-159">We didn't specify passwords, so the random passwords that Microsoft 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="cb4d0-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb4d0-160">See also</span></span>

[<span data-ttu-id="cb4d0-161">以 PowerShell 管理 Microsoft 365 使用者帳戶、授權和群組</span><span class="sxs-lookup"><span data-stu-id="cb4d0-161">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="cb4d0-162">使用 PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="cb4d0-162">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="cb4d0-163">開始使用適用於 Microsoft 365 的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb4d0-163">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
