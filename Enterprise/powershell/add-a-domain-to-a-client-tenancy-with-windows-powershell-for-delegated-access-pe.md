---
title: "利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 新增用戶端租用網域"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "摘要：使用 Windows PowerShell for Office 365 將替代網域名稱新增至現有的客戶租用戶。"
ms.openlocfilehash: 182750a5706dbb23c6207c6bd63334cbf2a2a795
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 新增用戶端租用網域

 **摘要：**使用 Windows PowerShell for Office 365 將替代的網域名稱新增至現有的客戶租用戶。
  
您可以使用 Windows PowerShell for Office 365 來建立新網域，並與客戶的租用建立關聯，速度勝於使用 Office 365 系統管理中心。
  
委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。他們通常是其他公司的網路或電信服務提供者。他們會在提供給客戶的服務方案中搭售 Office 365 訂閱。 當他們銷售 Office 365 訂閱時，會自動將管理代理者 (AOBO) 權限授與「客戶租用」，讓他們能夠管理和報告客戶租用。
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)
  
您也需要下列資訊︰
  
- 您需要客戶要求的完整網域名稱 (FQDN)。
    
- 您需要客戶的 **TenantId** 。
    
- FQDN 必須是已向網際網路網域名稱服務 (DNS) 註冊機構註冊的名稱 (如 GoDaddy)。如需公開註冊網域名稱的詳細資訊，請參閱[如何購買網域名稱](https://go.microsoft.com/fwlink/p/?LinkId=532541)。
    
- 您需要知道如何為 DNS 註冊機構將 TXT 記錄新增至已註冊的 DNS 區域。如需新增 TXT 記錄的詳細資訊，請參閱[在任一 DNS 主機服務提供者建立 Office 365 的 DNS 記錄](https://go.microsoft.com/fwlink/p/?LinkId=532542)。如果這些程序不適用，您將需要尋找適合 DNS 註冊機構的程序。
    
## <a name="create-domains"></a>建立網域

 客戶可能會要求您建立額外的網域來與租用相關聯，因為他們不希望預設的<網域>.onmicrosoft.com網域成為向全世界代表公司身分的主要網域。此程序會引導您完成與客戶租用相關聯之新網域的建立步驟。
  
> [!NOTE]
> 若要執行這些作業的部分，您登入中使用的協力廠商系統管理員帳戶必須設為**完全管理**的**支援公司指派管理權限**設定中的管理帳戶的詳細資料中找到Office 365 系統管理中心。如需有關管理協力廠商系統管理員角色的詳細資訊，請參閱[協力廠商： 優惠委派管理](https://go.microsoft.com/fwlink/p/?LinkId=532435)。 
  
### <a name="create-the-domain-in-azure-active-directory"></a>在 Azure Active Directory 中建立網域

此命令會在 Azure Active Directory 中建立網域，但不會將新網域與公開註冊的網域建立關聯。當您向適用於企業的 Microsoft Office 365 證明擁有公開註冊的網域時才能建立關聯。
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>取得 TXT DNS 驗證記錄的資料

 Office 365 會產生需要置入 DNS TXT 驗證記錄中的特定資料。若要取得資料，請執行此命令。
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

這會產生與以下範例相似的輸出：
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> 您需要這些文字才能在公開註冊的 DNS 區域中建立 TXT 記錄。請務必複製及儲存。 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>將 TXT 記錄新增至公開註冊的 DNS 區域

在 Office 365 開始接受導向公開註冊網域名稱的流量之前，您必須證明擁有及具備網域的管理員權限。您可以在網域中建立 TXT 記錄，藉此證明擁有該網域。TXT 記錄在網域中不具任何效果，因此當您建立網域擁有權之後即可予以刪除。若要建立 TXT 記錄，請遵循[在任一 DNS 主機服務提供者建立 Office 365 的 DNS 記錄](https://go.microsoft.com/fwlink/p/?LinkId=532542)中的程序。如果這些程序不適用，您將需要尋找適合 DNS 註冊機構的程序。
  
透過 nslookup 確認成功建立 TXT 記錄。請遵循此語法。
  
```
nslookup -type=TXT <FQDN of registered domain>
```

這會產生與以下範例相似的輸出：
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>在 Office 365 中驗證網域擁有權

在最後一個步驟中，您向 Office 365 證明擁有公開註冊的網域。此步驟之後，Office 365 會開始接受路由傳送到新網域名稱的流量。若要完成網域建立和註冊程序，請執行此命令。 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

此命令將不會傳回任何輸出，因此若要確認命令正常運作，請執行此命令。
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

這會傳回與以下範例相似的內容：
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>See also

#### 

[合作夥伴說明](https://go.microsoft.com/fwlink/p/?LinkID=533477)

