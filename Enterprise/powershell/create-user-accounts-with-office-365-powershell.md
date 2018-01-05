---
title: "使用 Office 365 PowerShell 建立使用者帳戶"
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
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: "了解如何使用 Office 365 PowerShell 在 Office 365 中建立使用者帳戶。"
ms.openlocfilehash: 9f6eb4cafa82ae511e806b7e32f2ed98a065d52e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="create-user-accounts-with-office-365-powershell"></a><span data-ttu-id="ebdae-103">使用 Office 365 PowerShell 建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ebdae-103">Create user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="ebdae-104">**摘要：**了解如何使用 Office 365 PowerShell 在 Office 365 中建立使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ebdae-104">Learn how to use Office 365 PowerShell to create user accounts in Office 365.</span></span>
  
<span data-ttu-id="ebdae-p101">您可以使用 Office 365 PowerShell 有效率地建立使用者帳戶 (尤其是多個使用者帳戶時)。當您在 Office 365 PowerShell 中建立使用者帳戶時，一律需要某些帳戶屬性。其他屬性不一定用於建立帳戶，但卻很重要。下表將說明這些屬性：</span><span class="sxs-lookup"><span data-stu-id="ebdae-p101">You can use Office 365 PowerShell to efficiently create user accounts, especially multiple user accounts. When you create user accounts in Office 365 PowerShell, certain account properties are always required. Other properties aren't required to create the account, but are otherwise important. These properties are described in the following table:</span></span>
  
****

|<span data-ttu-id="ebdae-109">**屬性名稱**</span><span class="sxs-lookup"><span data-stu-id="ebdae-109">**Property name**</span></span>|<span data-ttu-id="ebdae-110">**必要？**</span><span class="sxs-lookup"><span data-stu-id="ebdae-110">**Required?**</span></span>|<span data-ttu-id="ebdae-111">**描述**</span><span class="sxs-lookup"><span data-stu-id="ebdae-111">**Description**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="ebdae-112">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="ebdae-112">**DisplayName**</span></span> <br/> |<span data-ttu-id="ebdae-113">是</span><span class="sxs-lookup"><span data-stu-id="ebdae-113">Yes</span></span>  <br/> |<span data-ttu-id="ebdae-p102">這是 Office 365 服務中使用的顯示名稱。例如，Caleb Sills。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p102">This is the display name that's used in Office 365 services. For example, Caleb Sills.</span></span>  <br/> |
|<span data-ttu-id="ebdae-116">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="ebdae-116">**UserPrincipalName**</span></span> <br/> |<span data-ttu-id="ebdae-117">是</span><span class="sxs-lookup"><span data-stu-id="ebdae-117">Yes</span></span>  <br/> |<span data-ttu-id="ebdae-p103">這是用來登入 Office 365 服務的帳戶名稱。例如，CalebS@contoso.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p103">This is the account name that's used to sign in to Office 365 services. For example, CalebS@contoso.onmicrosoft.com.</span></span>  <br/> |
|<span data-ttu-id="ebdae-120">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="ebdae-120">**FirstName**</span></span> <br/> |<span data-ttu-id="ebdae-121">否</span><span class="sxs-lookup"><span data-stu-id="ebdae-121">No</span></span>  <br/> ||
|<span data-ttu-id="ebdae-122">**LastName**</span><span class="sxs-lookup"><span data-stu-id="ebdae-122">**LastName**</span></span> <br/> |<span data-ttu-id="ebdae-123">否</span><span class="sxs-lookup"><span data-stu-id="ebdae-123">No</span></span>  <br/> ||
|<span data-ttu-id="ebdae-124">**LicenseAssignment**</span><span class="sxs-lookup"><span data-stu-id="ebdae-124">**LicenseAssignment**</span></span> <br/> |<span data-ttu-id="ebdae-125">否</span><span class="sxs-lookup"><span data-stu-id="ebdae-125">No</span></span>  <br/> |<span data-ttu-id="ebdae-p104">這是從中將可用的授權指派給使用者帳戶的授權計劃 (也稱為 Office 365 計劃或 SKU)。授權定義帳戶可用的 Office 365 服務。當您建立帳戶時，您不必將授權指派給使用者，但帳戶需要授權才能存取 Office 365 服務。建立使用者帳戶之後，您有 30 天的時間進行使用者帳戶授權。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p104">This is the licensing plan (also known as the license plan, Office 365 plan, or SKU) from which an available license is assigned to the user account. The license defines the Office 365 services that are available to account. You don't have to assign a license to a user when you create the account, but the account requires a license to access Office 365 services. You have 30 days to license the user account after you create it.  </span></span><br/> <span data-ttu-id="ebdae-p105">使用 **Get-MsolAccountSku** Cmdlet，以檢視您組織中的授權計劃 ( **AccountSkuId** ) 和可用的授權。如需詳細資訊，請參閱[使用 Office 365 PowerShell 檢視授權與服務](view-licenses-and-services-with-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p105">Use the **Get-MsolAccountSku** cmdlet to view the licensing plans ( **AccountSkuId** ) and available licenses in your organization. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span><br/> |
|<span data-ttu-id="ebdae-132">**Password**</span><span class="sxs-lookup"><span data-stu-id="ebdae-132">**Password**</span></span> <br/> |<span data-ttu-id="ebdae-133">否</span><span class="sxs-lookup"><span data-stu-id="ebdae-133">No</span></span>  <br/> | <span data-ttu-id="ebdae-p106">如果您未指定密碼，則會指派隨機密碼給使用者帳戶，並可在命令結果中看見此密碼。如果您指定密碼，該密碼必須符合下列複雜性需求：</span><span class="sxs-lookup"><span data-stu-id="ebdae-p106">If you don't specify a password, a random password is assigned to the user account, and the password is visible in the results of the command. If you specify a password, it needs to meet the following complexity requirements:</span></span> <br/>  <span data-ttu-id="ebdae-136">8 到 16 個 ASCII 文字字元。</span><span class="sxs-lookup"><span data-stu-id="ebdae-136">8 to 16 ASCII text characters.</span></span> <br/>  <span data-ttu-id="ebdae-137">下列任何三種類型中的字元：小寫字母、大寫字母、數字和符號。</span><span class="sxs-lookup"><span data-stu-id="ebdae-137">Characters from any three of the following types: lowercase letters, uppercase letters, numbers, and symbols.</span></span> <br/> |
|<span data-ttu-id="ebdae-138">**UsageLocation**</span><span class="sxs-lookup"><span data-stu-id="ebdae-138">**UsageLocation**</span></span> <br/> |<span data-ttu-id="ebdae-139">否</span><span class="sxs-lookup"><span data-stu-id="ebdae-139">No</span></span>  <br/> |<span data-ttu-id="ebdae-p107">這是有效的 ISO 3166-1 alpha-2 國碼。例如，US 代表美國、FR 代表法國。請務必提供此值，因為某些 Office 365 服務不適用於某些國家/地區，所以您無法將授權指派給使用者帳戶 (除非帳戶已設定此值)。如需詳細資訊，請參閱[關於授權限制](https://go.microsoft.com/fwlink/p/?LinkId=691730)。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p107">This is a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. It's important to provide this value, because some Office 365 services aren't available in certain countries, so you can't assign a license to a user account unless the account has this value configured. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).  </span></span><br/> |
   
## <a name="before-you-begin"></a><span data-ttu-id="ebdae-144">開始之前</span><span class="sxs-lookup"><span data-stu-id="ebdae-144">Before you begin</span></span>

<span data-ttu-id="ebdae-p108">本主題中的程序需要您連線到 Office 365 PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p108">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a><span data-ttu-id="ebdae-147">使用 Office 365 PowerShell 建立個別使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ebdae-147">Use Office 365 PowerShell to create individual user accounts</span></span>

<span data-ttu-id="ebdae-148">若要建立個別帳戶，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="ebdae-148">To create an individual account, use the following syntax:</span></span>
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

<span data-ttu-id="ebdae-149">本範例會為名為 Caleb Sills 的美國使用者建立帳戶，並從  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) 授權計劃指派授權。</span><span class="sxs-lookup"><span data-stu-id="ebdae-149">This example creates an account for the United States user named Caleb Sills, and assigns a license from the  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) licensing plan.</span></span>
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a><span data-ttu-id="ebdae-150">使用 Office 365 PowerShell 建立多個使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ebdae-150">Use Office 365 PowerShell to create multiple user accounts</span></span>

1. <span data-ttu-id="ebdae-p109">建立包含必要使用者帳戶資訊的逗點分隔值 (CSV) 檔案。例如：</span><span class="sxs-lookup"><span data-stu-id="ebdae-p109">Create a comma-separated value (CSV) file that contains the required user account information. For example:</span></span>
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
><span data-ttu-id="ebdae-153">CSV 檔第一列中的欄名稱及其順序並無任何限定，但請確定檔案其餘部分中的資料符合欄名稱之順序，並將欄名稱使用於 Office 365 PowerShell 命令中的參數值。</span><span class="sxs-lookup"><span data-stu-id="ebdae-153">Note: The column names and their order in the first row of the CSV file are arbitrary, but make sure the data in the rest of the file matches the order of the column names, and use the column names for the parameter values in the Office 365 PowerShell command.</span></span>
    
2. <span data-ttu-id="ebdae-154">使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="ebdae-154">Use the following syntax:</span></span>
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

<span data-ttu-id="ebdae-155">本範例會從名為 C:\My Documents\NewAccounts.csv 的檔案建立使用者帳戶，並將結果記錄在名為 C:\My Documents\NewAccountResults.csv 的檔案中</span><span class="sxs-lookup"><span data-stu-id="ebdae-155">This example creates the user accounts from the file named C:\My Documents\NewAccounts.csv, and logs the results in the file named C:\My Documents\NewAccountResults.csv</span></span>
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. <span data-ttu-id="ebdae-p110">檢閱輸出檔以查看結果。我們並未指定密碼，所以輸出檔中看得到多個隨機產生的密碼。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p110">Review the output file to see the results. We didn't specify passwords, so the random passwords that were generated are visible in the output file.</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a><span data-ttu-id="ebdae-158">使用 Azure Active Directory V2 PowerShell 模組來建立個別使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ebdae-158">Use the Azure Active Directory V2 PowerShell module to create individual user accounts</span></span>

<span data-ttu-id="ebdae-p111">若要從 Azure Active Directory V2 PowerShell 模組使用 **New-AzureADUser** Cmdlet，您必須先連接至您的訂用帳戶。如需相關指示，請參閱[與 Azure Active Directory V2 PowerShell 模組連線](https://go.microsoft.com/fwlink/?linkid=842218)。</span><span class="sxs-lookup"><span data-stu-id="ebdae-p111">To use the **New-AzureADUser** cmdlet from the Azure Active Directory V2 PowerShell module, you must first connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="ebdae-161">連接之後，使用下列語法來建立個別帳戶：</span><span class="sxs-lookup"><span data-stu-id="ebdae-161">After you have connected, use the following syntax to create an individual account:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

<span data-ttu-id="ebdae-162">本範例會為名為 Caleb Sills 的美國使用者建立帳戶：</span><span class="sxs-lookup"><span data-stu-id="ebdae-162">This example creates an account for the United States user named Caleb Sills:</span></span>
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a><span data-ttu-id="ebdae-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebdae-163">See also</span></span>

<span data-ttu-id="ebdae-164">請參閱這些有關透過 Office 365 PowerShell 管理使用者的其他主題：</span><span class="sxs-lookup"><span data-stu-id="ebdae-164">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="ebdae-165">使用 Office 365 PowerShell 刪除及還原使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ebdae-165">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ebdae-166">使用 Office 365 PowerShell 封鎖使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ebdae-166">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ebdae-167">使用 Office 365 PowerShell 指派授權至使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="ebdae-167">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="ebdae-168">使用 Office 365 PowerShell 移除使用者帳戶中的授權</span><span class="sxs-lookup"><span data-stu-id="ebdae-168">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="ebdae-169">如需這些程序中所使用之 Cmdlet 的相關資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="ebdae-169">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="ebdae-170">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="ebdae-170">Export-Csv</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- <span data-ttu-id="ebdae-171">[Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))</span><span class="sxs-lookup"><span data-stu-id="ebdae-171">[Import-Csv]((https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv))</span></span>
    
- [<span data-ttu-id="ebdae-172">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="ebdae-172">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="ebdae-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="ebdae-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="ebdae-174">New-AzureADUser</span><span class="sxs-lookup"><span data-stu-id="ebdae-174">New-AzureADUser</span></span>](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

