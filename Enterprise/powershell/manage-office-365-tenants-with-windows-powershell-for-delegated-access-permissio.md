---
title: 使用適用于委派存取權限（結合）合作夥伴的 Windows PowerShell 管理 Microsoft 365 承租人
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 摘要：使用 Microsoft 365 的 Windows PowerShell 來管理客戶租用。
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998229"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="5bc54-103">使用適用于委派存取權限（結合）合作夥伴的 Windows PowerShell 管理 Microsoft 365 承租人</span><span class="sxs-lookup"><span data-stu-id="5bc54-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="5bc54-104">Windows PowerShell 可讓供稿和雲端解決方案提供者（CSP）合作夥伴輕鬆管理和報告 Microsoft 365 系統管理中心無法使用的客戶租使用者設定。</span><span class="sxs-lookup"><span data-stu-id="5bc54-104">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="5bc54-105">請注意，合作夥伴系統管理員帳戶須有管理代表 (AOBO) 權限才能連接其客戶租用。</span><span class="sxs-lookup"><span data-stu-id="5bc54-105">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="5bc54-106">委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。</span><span class="sxs-lookup"><span data-stu-id="5bc54-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="5bc54-107">他們通常是其他公司的網路或電信服務提供者。</span><span class="sxs-lookup"><span data-stu-id="5bc54-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="5bc54-108">他們會將 Microsoft 365 訂閱捆綁到其客戶的服務產品中。</span><span class="sxs-lookup"><span data-stu-id="5bc54-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="5bc54-109">當他們銷售 Microsoft 365 訂閱時，系統會自動授與客戶租用的「管理」（AOBO）許可權，讓他們能管理及報告客戶租用。</span><span class="sxs-lookup"><span data-stu-id="5bc54-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="5bc54-110">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="5bc54-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="5bc54-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bc54-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span></span> <span data-ttu-id="5bc54-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="5bc54-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="5bc54-113">您也需要合作夥伴租用戶系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="5bc54-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="5bc54-114">您要執行的工作</span><span class="sxs-lookup"><span data-stu-id="5bc54-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="5bc54-115">列出所有租用戶識別碼</span><span class="sxs-lookup"><span data-stu-id="5bc54-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="5bc54-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span><span class="sxs-lookup"><span data-stu-id="5bc54-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span></span> <span data-ttu-id="5bc54-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="5bc54-118">若要列出所有可存取的客戶租用戶識別碼，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="5bc54-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="5bc54-119">這會顯示按照 **TenantId** 排列的所有客戶租用戶清單。</span><span class="sxs-lookup"><span data-stu-id="5bc54-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="5bc54-120">PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5bc54-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="5bc54-121">若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。</span><span class="sxs-lookup"><span data-stu-id="5bc54-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="5bc54-122">使用網域名稱來取得租用戶識別碼</span><span class="sxs-lookup"><span data-stu-id="5bc54-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="5bc54-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span><span class="sxs-lookup"><span data-stu-id="5bc54-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span></span> <span data-ttu-id="5bc54-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span><span class="sxs-lookup"><span data-stu-id="5bc54-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="5bc54-125">列出租用戶的所有網域</span><span class="sxs-lookup"><span data-stu-id="5bc54-125">List all domains for a tenant</span></span>

<span data-ttu-id="5bc54-126">To get all domains for any one customer tenant, run this command.</span><span class="sxs-lookup"><span data-stu-id="5bc54-126">To get all domains for any one customer tenant, run this command.</span></span> <span data-ttu-id="5bc54-127">Replace  _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="5bc54-127">Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="5bc54-128">如果您已經註冊其他網域，這會傳回與客戶 **TenantId** 相關聯的所有網域。</span><span class="sxs-lookup"><span data-stu-id="5bc54-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="5bc54-129">取得所有租用戶和註冊網域的對應</span><span class="sxs-lookup"><span data-stu-id="5bc54-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="5bc54-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span><span class="sxs-lookup"><span data-stu-id="5bc54-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="5bc54-131">This command generates a listing of all your customer tenant IDs and their domains.</span><span class="sxs-lookup"><span data-stu-id="5bc54-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="5bc54-132">取得租用戶的所有使用者</span><span class="sxs-lookup"><span data-stu-id="5bc54-132">Get all users for a tenant</span></span>

<span data-ttu-id="5bc54-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span><span class="sxs-lookup"><span data-stu-id="5bc54-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span></span> <span data-ttu-id="5bc54-134">Replace _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="5bc54-134">Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="5bc54-135">取得有關使用者的所有詳細資料</span><span class="sxs-lookup"><span data-stu-id="5bc54-135">Get all details about a user</span></span>

<span data-ttu-id="5bc54-136">If you want to see all the properties of a particular user, run this command.</span><span class="sxs-lookup"><span data-stu-id="5bc54-136">If you want to see all the properties of a particular user, run this command.</span></span> <span data-ttu-id="5bc54-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span><span class="sxs-lookup"><span data-stu-id="5bc54-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="5bc54-138">新增使用者、設定選項及指派授權</span><span class="sxs-lookup"><span data-stu-id="5bc54-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="5bc54-139">Microsoft 365 使用者的大量建立、設定及授權特別有效率地使用 Office 365 的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5bc54-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="5bc54-140">在這兩個步驟的程式中，您會先在逗號分隔值（CSV）檔案中為您要新增的所有使用者建立專案，然後使用 Office 365 的 Windows PowerShell 匯入該檔案。</span><span class="sxs-lookup"><span data-stu-id="5bc54-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="5bc54-141">建立 CSV 檔案</span><span class="sxs-lookup"><span data-stu-id="5bc54-141">Create a CSV file</span></span>

<span data-ttu-id="5bc54-142">使用此格式來建立 CSV 檔案：</span><span class="sxs-lookup"><span data-stu-id="5bc54-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="5bc54-143">其中：</span><span class="sxs-lookup"><span data-stu-id="5bc54-143">where:</span></span>
  
- <span data-ttu-id="5bc54-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span><span class="sxs-lookup"><span data-stu-id="5bc54-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span></span> <span data-ttu-id="5bc54-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span><span class="sxs-lookup"><span data-stu-id="5bc54-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span></span> <span data-ttu-id="5bc54-146">For example, the code for the United States is US, and the code for Brazil is BR.</span><span class="sxs-lookup"><span data-stu-id="5bc54-146">For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="5bc54-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span><span class="sxs-lookup"><span data-stu-id="5bc54-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span></span> <span data-ttu-id="5bc54-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span><span class="sxs-lookup"><span data-stu-id="5bc54-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span></span> <span data-ttu-id="5bc54-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span><span class="sxs-lookup"><span data-stu-id="5bc54-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="5bc54-150">匯入 CSV 檔案及建立使用者</span><span class="sxs-lookup"><span data-stu-id="5bc54-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="5bc54-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span><span class="sxs-lookup"><span data-stu-id="5bc54-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span></span> <span data-ttu-id="5bc54-152">Be sure to substitute the correct CSV file name.</span><span class="sxs-lookup"><span data-stu-id="5bc54-152">Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="5bc54-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bc54-153">See also</span></span>

#### 

[<span data-ttu-id="5bc54-154">合作夥伴說明</span><span class="sxs-lookup"><span data-stu-id="5bc54-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

