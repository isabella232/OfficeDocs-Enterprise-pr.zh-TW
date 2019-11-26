---
title: 使用 Office 365 PowerShell 建立使用者帳戶
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: 了解如何使用 Office 365 PowerShell 在 Office 365 中建立使用者帳戶。
ms.openlocfilehash: 618459cbf226a9a7cef0e03c7126d791f2ca8bc8
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257412"
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8be4a-103">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8be4a-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8be4a-104">**摘要：** 了解如何使用 Office 365 PowerShell 在 Office 365 中建立使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8be4a-104">**Summary:** Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="8be4a-p101">您可以使用 Office 365 PowerShell 有效率地建立使用者帳戶 (尤其是多個使用者帳戶時)。當您在 Office 365 PowerShell 中建立使用者帳戶時，一律需要某些帳戶屬性。其他屬性不一定用於建立帳戶，但卻很重要。下表將說明這些屬性：</span><span class="sxs-lookup"><span data-stu-id="8be4a-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
|<span data-ttu-id="8be4a-109">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="8be4a-109">**Property name**</span></span>|<span data-ttu-id="8be4a-110">**必要？**</span><span class="sxs-lookup"><span data-stu-id="8be4a-110">**Required?**</span></span>|<span data-ttu-id="8be4a-111">**描述**</span><span class="sxs-lookup"><span data-stu-id="8be4a-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8be4a-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="8be4a-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="8be4a-113">是</span><span class="sxs-lookup"><span data-stu-id="8be4a-113">Yes</span></span>  <br/> |<span data-ttu-id="8be4a-p102">這是 Office 365 服務中使用的顯示名稱。例如，Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="8be4a-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="8be4a-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="8be4a-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="8be4a-117">是</span><span class="sxs-lookup"><span data-stu-id="8be4a-117">Yes</span></span>  <br/> |<span data-ttu-id="8be4a-p103">這是用來登入 Office 365 服務的帳戶名稱。例如，CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="8be4a-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="8be4a-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="8be4a-120">**FirstName**</span></span> <br/> |<span data-ttu-id="8be4a-121">否</span><span class="sxs-lookup"><span data-stu-id="8be4a-121">No</span></span>  <br/> ||
|<span data-ttu-id="8be4a-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="8be4a-122">**LastName**</span></span> <br/> |<span data-ttu-id="8be4a-123">否</span><span class="sxs-lookup"><span data-stu-id="8be4a-123">No</span></span>  <br/> ||
|<span data-ttu-id="8be4a-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="8be4a-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="8be4a-125">否</span><span class="sxs-lookup"><span data-stu-id="8be4a-125">No</span></span>  <br/> |<span data-ttu-id="8be4a-p104">這是從中將可用的授權指派給使用者帳戶的授權計劃 (也稱為 Office 365 計劃或 SKU)。授權定義帳戶可用的 Office 365 服務。當您建立帳戶時，您不必將授權指派給使用者，但帳戶需要授權才能存取 Office 365 服務。建立使用者帳戶之後，您有 30 天的時間進行使用者帳戶授權。</span><span class="sxs-lookup"><span data-stu-id="8be4a-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.</span></span> |
|<span data-ttu-id="8be4a-130">**Password**</span><span class="sxs-lookup"><span data-stu-id="8be4a-130">**Password**</span></span> <br/> |<span data-ttu-id="8be4a-131">否</span><span class="sxs-lookup"><span data-stu-id="8be4a-131">No</span></span>  <br/> | <span data-ttu-id="8be4a-p105">如果您未指定密碼，則會指派隨機密碼給使用者帳戶，並可在命令結果中看見此密碼。如果您指定密碼，該密碼必須是下列任三種類型的 8 到 16 個 ASCII 文字：小寫字母、大寫字母、數字和符號。</span><span class="sxs-lookup"><span data-stu-id="8be4a-p105">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to be 8 to 16 ASCII text characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="8be4a-134">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="8be4a-134">**UsageLocation**</span></span> <br/> |<span data-ttu-id="8be4a-135">否</span><span class="sxs-lookup"><span data-stu-id="8be4a-135">No</span></span>  <br/> |<span data-ttu-id="8be4a-p106">這是有效的 ISO 3166-1 alpha-2 國碼。例如，US 代表美國、FR 代表法國。請務必提供此值，因為某些 Office 365 服務不適用於某些國家/地區，所以您無法將授權指派給使用者帳戶 (除非帳戶已設定此值)。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="8be4a-p106">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8be4a-140">針對 Graph 模組，請使用 Azure Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="8be4a-140">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8be4a-141">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="8be4a-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="8be4a-142">連接之後，使用下列語法來建立個別帳戶：</span><span class="sxs-lookup"><span data-stu-id="8be4a-142">After you have connected, use the following syntax to create an individual account:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="8be4a-143">本範例會為名為 Caleb Sills 的美國使用者建立帳戶：</span><span class="sxs-lookup"><span data-stu-id="8be4a-143">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8be4a-144">使用適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組。</span><span class="sxs-lookup"><span data-stu-id="8be4a-144">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8be4a-145">首先，[連線到您的 Office 365 租用戶](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="8be4a-145">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="create-an-individual-user-account"></a><span data-ttu-id="8be4a-146">建立個別使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8be4a-146">Create an individual user account</span></span>

<span data-ttu-id="8be4a-147">若要建立個別帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="8be4a-147">To create an individual account, use the following syntax:</span></span>
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
><span data-ttu-id="8be4a-148">PowerShell 核心不支援的 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組和具有**Msol** cmdlet 在其名稱。</span><span class="sxs-lookup"><span data-stu-id="8be4a-148">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="8be4a-149">若要繼續使用這些 cmdlet，您必須從 Windows PowerShell 執行它們。</span><span class="sxs-lookup"><span data-stu-id="8be4a-149">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="8be4a-150">若要列出可用的授權方案名稱，請使用此命令：</span><span class="sxs-lookup"><span data-stu-id="8be4a-150">To list the available licensing plan names, use this command:</span></span>

````powershell
Get-MsolAccountSku
````

<span data-ttu-id="8be4a-151">本範例會建立一個名為 Caleb Sills 的美國使用者帳戶，並指派 `contoso:ENTERPRISEPACK` (Office 365 企業版 E3) 授權方案的授權。</span><span class="sxs-lookup"><span data-stu-id="8be4a-151">This example creates an account for the United States user named Caleb Sills, and assigns a license from the `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a><span data-ttu-id="8be4a-152">建立多個使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8be4a-152">Create multiple user accounts</span></span>

1. <span data-ttu-id="8be4a-p108">建立包含必要使用者帳戶資訊的逗點分隔值 (CSV) 檔案。例如：</span><span class="sxs-lookup"><span data-stu-id="8be4a-p108">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="8be4a-155">CSV 檔第一列中的欄名稱及其順序並無任何限定，但請確定檔案其餘部分中的資料符合欄名稱之順序，並將欄名稱使用於 Office 365 PowerShell 命令中的參數值。</span><span class="sxs-lookup"><span data-stu-id="8be4a-155">The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="8be4a-156">使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="8be4a-156">Use the following syntax:</span></span>
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="8be4a-157">本範例會從名為 C:\My Documents\NewAccounts.csv 的檔案建立使用者帳戶，並將結果記錄在名為 C:\My Documents\NewAccountResults.csv 的檔案中</span><span class="sxs-lookup"><span data-stu-id="8be4a-157">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="8be4a-p109">檢閱輸出檔以查看結果。我們並未指定密碼，所以會在輸出檔中看到 Office 365 產生的隨機密碼。</span><span class="sxs-lookup"><span data-stu-id="8be4a-p109">Review the output file to see the results. We didn't specify passwords, so the random passwords that Office 365 generated are visible in the output file.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8be4a-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8be4a-160">See also</span></span>

[<span data-ttu-id="8be4a-161">使用 Office 365 PowerShell 管理使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="8be4a-161">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8be4a-162">使用 Office 365 PowerShell 管理 Office 365</span><span class="sxs-lookup"><span data-stu-id="8be4a-162">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8be4a-163">開始使用 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="8be4a-163">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
