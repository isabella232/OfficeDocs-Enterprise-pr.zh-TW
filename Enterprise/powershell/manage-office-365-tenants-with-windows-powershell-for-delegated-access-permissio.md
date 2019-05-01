---
title: 利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 管理 Office 365 租用戶
ms.author: chrfox
author: chrfox
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 摘要：使用 Windows PowerShell for Office 365 來管理客戶租用。
ms.openlocfilehash: 4fec058bfd7b7dffa2c29add23d99a144f78decf
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491239"
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="17531-103">利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 管理 Office 365 租用戶</span><span class="sxs-lookup"><span data-stu-id="17531-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="17531-104">**摘要：** 使用 Windows PowerShell for Office 365 來管理客戶租用。</span><span class="sxs-lookup"><span data-stu-id="17531-104">**Summary:** Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="17531-p101">Windows PowerShell 可讓新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴輕鬆地管理及報告 Office 365 系統管理中心 未提供的客戶租用設定。請注意，合作夥伴系統管理員帳戶須有管理代表 (AOBO) 權限才能連接其客戶租用。</span><span class="sxs-lookup"><span data-stu-id="17531-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Office 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="17531-107">委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。</span><span class="sxs-lookup"><span data-stu-id="17531-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="17531-108">他們通常是其他公司的網路或電信服務提供者。</span><span class="sxs-lookup"><span data-stu-id="17531-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="17531-109">他們會在提供給客戶的服務方案中搭售 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="17531-109">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="17531-110">當他們銷售 Office 365 訂閱時，會自動將管理代表 (AOBO) 權限授與「客戶租用」，讓他們能夠管理和報告客戶租用。</span><span class="sxs-lookup"><span data-stu-id="17531-110">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="17531-111">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="17531-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="17531-p103">本主題中的程序需要您連線到 Office 365 的 Windows PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="17531-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="17531-114">您也需要合作夥伴租用戶系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="17531-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="17531-115">您要執行的工作</span><span class="sxs-lookup"><span data-stu-id="17531-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="17531-116">列出所有租用戶識別碼</span><span class="sxs-lookup"><span data-stu-id="17531-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="17531-p104">如果您有擁有 500 個以上的租用戶，請使用  _-All_ 或 _-MaxResultsParameter_ 來設定 Cmdlet 語法的範圍。這適用於其他提供大量輸出的 Cmdlet (如 **Get-MsolUser** )。</span><span class="sxs-lookup"><span data-stu-id="17531-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="17531-119">若要列出所有可存取的客戶租用戶識別碼，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="17531-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="17531-120">這會顯示按照 **TenantId** 排列的所有客戶租用戶清單。</span><span class="sxs-lookup"><span data-stu-id="17531-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="17531-121">使用網域名稱來取得租用戶識別碼</span><span class="sxs-lookup"><span data-stu-id="17531-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="17531-p105">若要依據網域名稱來取得特定客戶租用戶的 **TenantId** ，請執行此命令。將 _<domainname.onmicrosoft.com>_ 取代為所需的實際客戶租用戶網域名稱。</span><span class="sxs-lookup"><span data-stu-id="17531-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="17531-124">列出租用戶的所有網域</span><span class="sxs-lookup"><span data-stu-id="17531-124">List all domains for a tenant</span></span>

<span data-ttu-id="17531-p106">若要取得任一客戶租用戶的所有網域，請執行此命令。將 _<customer TenantId value>_ 取代為實際值。</span><span class="sxs-lookup"><span data-stu-id="17531-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="17531-127">如果您已經註冊其他網域，這會傳回與客戶 **TenantId** 相關聯的所有網域。</span><span class="sxs-lookup"><span data-stu-id="17531-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="17531-128">取得所有租用戶和註冊網域的對應</span><span class="sxs-lookup"><span data-stu-id="17531-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="17531-p107">先前的 Windows PowerShell for Office 365 命令示範如何擷取租用戶識別碼或網域，但兩者無法同時進行，且缺少兩者之間明確的對應。此命令會產生所有客戶租用戶識別碼和網域的清單。</span><span class="sxs-lookup"><span data-stu-id="17531-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="17531-131">取得租用戶的所有使用者</span><span class="sxs-lookup"><span data-stu-id="17531-131">Get all users for a tenant</span></span>

<span data-ttu-id="17531-p108">這會顯示特定租用戶之所有使用者的 **UserPrincipalName**、**DisplayName** 和 **isLicensed** 狀態。將 _<customer TenantId value>_ 取代為實際值。</span><span class="sxs-lookup"><span data-stu-id="17531-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="17531-134">取得有關使用者的所有詳細資料</span><span class="sxs-lookup"><span data-stu-id="17531-134">Get all details about a user</span></span>

<span data-ttu-id="17531-p109">如果您想要查看特定使用者的所有內容，請執行此命令。將 _<customer TenantId value>_ 和 _<user principal name value>_ 取代為實際值。</span><span class="sxs-lookup"><span data-stu-id="17531-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="17531-137">新增使用者、設定選項及指派授權</span><span class="sxs-lookup"><span data-stu-id="17531-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="17531-p110">使用 Windows PowerShell for Office 365 可有效提高 Office 365 使用者之大量建立、設定及授權等作業的效率。這是包含兩個步驟的程序。您需要先針對所有要新增至逗點分隔值 (CSV) 檔案中的使用者建立項目，然後再使用 Windows PowerShell for Office 365 匯入檔案。</span><span class="sxs-lookup"><span data-stu-id="17531-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="17531-140">建立 CSV 檔案</span><span class="sxs-lookup"><span data-stu-id="17531-140">Create a CSV file</span></span>

<span data-ttu-id="17531-141">使用此格式來建立 CSV 檔案：</span><span class="sxs-lookup"><span data-stu-id="17531-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="17531-142">其中：</span><span class="sxs-lookup"><span data-stu-id="17531-142">where:</span></span>
  
- <span data-ttu-id="17531-p111">**UsageLocation** ：此項目的值是由兩個字母組成的使用者 ISO 國家/地區碼。您可以在[ISO 線上瀏覽平台](https://go.microsoft.com/fwlink/p/?LinkId=532703)查詢國家/地區碼。例如，美國的代碼是 US，而巴西的代碼則是 BR。</span><span class="sxs-lookup"><span data-stu-id="17531-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="17531-p112">**LicenseAssignment** ：此項目的值使用格式： `syndication-account:<PROVISIONING_ID>`. 例如，如果您要將 O365_Business_Premium 授權指派給客戶租用戶使用者， **LicenseAssignment** 值看起來會像： **syndication-account:O365_Business_Premium** 。在新聞訂閱方式合作夥伴入口網站中，您可以找到能以新聞訂閱方式或 CSP 合作夥伴身分存取的 PROVISIONING_ID。</span><span class="sxs-lookup"><span data-stu-id="17531-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="17531-149">匯入 CSV 檔案及建立使用者</span><span class="sxs-lookup"><span data-stu-id="17531-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="17531-p113">建立 CSV 檔案之後，請執行此命令以利用使用者在第一次登入時必須變更的不會到期密碼建立使用者帳戶，以及指派您指定的授權。請務必替代正確的 CSV 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="17531-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="17531-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17531-152">See also</span></span>

#### 

[<span data-ttu-id="17531-153">合作夥伴說明</span><span class="sxs-lookup"><span data-stu-id="17531-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

