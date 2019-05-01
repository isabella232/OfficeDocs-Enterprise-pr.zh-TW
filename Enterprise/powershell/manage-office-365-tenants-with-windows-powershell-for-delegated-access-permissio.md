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
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 管理 Office 365 租用戶

 **摘要：** 使用 Windows PowerShell for Office 365 來管理客戶租用。
  
Windows PowerShell 可讓新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴輕鬆地管理及報告 Office 365 系統管理中心 未提供的客戶租用設定。請注意，合作夥伴系統管理員帳戶須有管理代表 (AOBO) 權限才能連接其客戶租用。
  
委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。 他們通常是其他公司的網路或電信服務提供者。 他們會在提供給客戶的服務方案中搭售 Office 365 訂閱。 當他們銷售 Office 365 訂閱時，會自動將管理代表 (AOBO) 權限授與「客戶租用」，讓他們能夠管理和報告客戶租用。
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

本主題中的程序需要您連線到 Office 365 的 Windows PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。
  
您也需要合作夥伴租用戶系統管理員認證。
  
## <a name="what-do-you-want-to-do"></a>您要執行的工作

### <a name="list-all-tenant-ids"></a>列出所有租用戶識別碼

> [!NOTE]
> 如果您有擁有 500 個以上的租用戶，請使用  _-All_ 或 _-MaxResultsParameter_ 來設定 Cmdlet 語法的範圍。這適用於其他提供大量輸出的 Cmdlet (如 **Get-MsolUser** )。
  
若要列出所有可存取的客戶租用戶識別碼，請執行此命令。
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

這會顯示按照 **TenantId** 排列的所有客戶租用戶清單。
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>使用網域名稱來取得租用戶識別碼

若要依據網域名稱來取得特定客戶租用戶的 **TenantId** ，請執行此命令。將 _<domainname.onmicrosoft.com>_ 取代為所需的實際客戶租用戶網域名稱。
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>列出租用戶的所有網域

若要取得任一客戶租用戶的所有網域，請執行此命令。將 _<customer TenantId value>_ 取代為實際值。
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

如果您已經註冊其他網域，這會傳回與客戶 **TenantId** 相關聯的所有網域。
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>取得所有租用戶和註冊網域的對應

先前的 Windows PowerShell for Office 365 命令示範如何擷取租用戶識別碼或網域，但兩者無法同時進行，且缺少兩者之間明確的對應。此命令會產生所有客戶租用戶識別碼和網域的清單。
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>取得租用戶的所有使用者

這會顯示特定租用戶之所有使用者的 **UserPrincipalName**、**DisplayName** 和 **isLicensed** 狀態。將 _<customer TenantId value>_ 取代為實際值。
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>取得有關使用者的所有詳細資料

如果您想要查看特定使用者的所有內容，請執行此命令。將 _<customer TenantId value>_ 和 _<user principal name value>_ 取代為實際值。
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>新增使用者、設定選項及指派授權

使用 Windows PowerShell for Office 365 可有效提高 Office 365 使用者之大量建立、設定及授權等作業的效率。這是包含兩個步驟的程序。您需要先針對所有要新增至逗點分隔值 (CSV) 檔案中的使用者建立項目，然後再使用 Windows PowerShell for Office 365 匯入檔案。 
  
#### <a name="create-a-csv-file"></a>建立 CSV 檔案

使用此格式來建立 CSV 檔案：
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
其中：
  
- **UsageLocation** ：此項目的值是由兩個字母組成的使用者 ISO 國家/地區碼。您可以在[ISO 線上瀏覽平台](https://go.microsoft.com/fwlink/p/?LinkId=532703)查詢國家/地區碼。例如，美國的代碼是 US，而巴西的代碼則是 BR。 
    
- **LicenseAssignment** ：此項目的值使用格式： `syndication-account:<PROVISIONING_ID>`. 例如，如果您要將 O365_Business_Premium 授權指派給客戶租用戶使用者， **LicenseAssignment** 值看起來會像： **syndication-account:O365_Business_Premium** 。在新聞訂閱方式合作夥伴入口網站中，您可以找到能以新聞訂閱方式或 CSP 合作夥伴身分存取的 PROVISIONING_ID。
    
#### <a name="import-the-csv-file-and-create-the-users"></a>匯入 CSV 檔案及建立使用者

建立 CSV 檔案之後，請執行此命令以利用使用者在第一次登入時必須變更的不會到期密碼建立使用者帳戶，以及指派您指定的授權。請務必替代正確的 CSV 檔案名稱。
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>另請參閱

#### 

[合作夥伴說明](https://go.microsoft.com/fwlink/p/?LinkId=533477)

