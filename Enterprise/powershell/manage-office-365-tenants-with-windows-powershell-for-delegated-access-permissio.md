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
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>使用適用于委派存取權限（結合）合作夥伴的 Windows PowerShell 管理 Microsoft 365 承租人

Windows PowerShell 可讓供稿和雲端解決方案提供者（CSP）合作夥伴輕鬆管理和報告 Microsoft 365 系統管理中心無法使用的客戶租使用者設定。 請注意，合作夥伴系統管理員帳戶須有管理代表 (AOBO) 權限才能連接其客戶租用。
  
委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。 他們通常是其他公司的網路或電信服務提供者。 他們會將 Microsoft 365 訂閱捆綁到其客戶的服務產品中。 當他們銷售 Microsoft 365 訂閱時，系統會自動授與客戶租用的「管理」（AOBO）許可權，讓他們能管理及報告客戶租用。
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
您也需要合作夥伴租用戶系統管理員認證。
  
## <a name="what-do-you-want-to-do"></a>您要執行的工作

### <a name="list-all-tenant-ids"></a>列出所有租用戶識別碼

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
若要列出所有可存取的客戶租用戶識別碼，請執行此命令。
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

這會顯示按照 **TenantId** 排列的所有客戶租用戶清單。

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>使用網域名稱來取得租用戶識別碼

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>列出租用戶的所有網域

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

如果您已經註冊其他網域，這會傳回與客戶 **TenantId** 相關聯的所有網域。
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>取得所有租用戶和註冊網域的對應

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>取得租用戶的所有使用者

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>取得有關使用者的所有詳細資料

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>新增使用者、設定選項及指派授權

Microsoft 365 使用者的大量建立、設定及授權特別有效率地使用 Office 365 的 Windows PowerShell。 在這兩個步驟的程式中，您會先在逗號分隔值（CSV）檔案中為您要新增的所有使用者建立專案，然後使用 Office 365 的 Windows PowerShell 匯入該檔案。 
  
#### <a name="create-a-csv-file"></a>建立 CSV 檔案

使用此格式來建立 CSV 檔案：
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
其中：
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>匯入 CSV 檔案及建立使用者

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>另請參閱

#### 

[合作夥伴說明](https://go.microsoft.com/fwlink/p/?LinkId=533477)

