---
title: 利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 新增用戶端租用網域
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
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 摘要：使用 Microsoft 365 的 Windows PowerShell，將替代功能變數名稱新增至現有的客戶租使用者。
ms.openlocfilehash: 6ba706c1fc0b2e2b43687ac582a40f36a2a3387c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997359"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 新增用戶端租用網域

您可以使用 microsoft 365 的 Windows PowerShell，以更快的速度，建立新網域與客戶的租用，而不是使用 Microsoft 365 系統管理中心。
  
委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。 他們通常是其他公司的網路或電信服務提供者。 他們會將 Microsoft 365 訂閱捆綁到其客戶的服務產品中。 當他們銷售 Microsoft 365 訂閱時，系統會自動授與客戶租用的「管理」（AOBO）許可權，讓他們能管理及報告客戶租用。
## <a name="what-do-you-need-to-know-before-you-begin"></a>開始之前有哪些須知？

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
您也需要合作夥伴租用戶系統管理員認證。
  
您也需要下列資訊︰
  
- 您需要客戶要求的完整網域名稱 (FQDN)。
    
- 您需要客戶的 **TenantId** 。
    
- The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- 您需要知道如何為 DNS 註冊機構將 TXT 記錄新增至已註冊的 DNS 區域。 如需如何新增 TXT 記錄的詳細資訊，請參閱[ADD DNS record to connect domain](https://go.microsoft.com/fwlink/p/?LinkId=532542)。 如果這些程序不適用，您將需要尋找適合 DNS 註冊機構的程序。
    
## <a name="create-domains"></a>建立網域

 Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.
  
> [!NOTE]
> 若要執行這些作業，您必須在 Microsoft 365 系統管理中心的系統管理員帳戶詳細資料中，將您登入的夥伴管理員帳戶設為「**完全管理**」，以取得**您支援之公司的系統管理許可權**。 如需管理夥伴系統管理員角色的詳細資訊，請參閱[合作夥伴：提供委派的管理](https://go.microsoft.com/fwlink/p/?LinkId=532435)。 
  
### <a name="create-the-domain-in-azure-active-directory"></a>在 Azure Active Directory 中建立網域

此命令會在 Azure Active Directory 中建立網域，但不會將新網域與公開註冊的網域建立關聯。 當您證明您擁有已公開註冊的網域給 Microsoft Microsoft 365 的企業時，就會發生這種情況。
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>PowerShell Core 不支援適用於 Windows PowerShell 的 Microsoft Azure Active Directory 模組和名稱有 **Msol** 的 Cmdlet。 若要繼續使用這些 Cmdlet，您必須從 Windows PowerShell 執行。
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>取得 TXT DNS 驗證記錄的資料

 Microsoft 365 會產生您需要放入 DNS TXT 驗證記錄的特定資料。 若要取得資料，請執行此命令。
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

這會產生與以下範例相似的輸出：
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> 您需要這些文字才能在公開註冊的 DNS 區域中建立 TXT 記錄。 請務必將其複製並儲存。 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>將 TXT 記錄新增至公開註冊的 DNS 區域

在 Microsoft 365 開始接受導向至已公開登錄功能變數名稱的流量之前，您必須證明您擁有該網域的系統管理員許可權。 您可以在網域中建立 TXT 記錄，藉此證明擁有該網域。 TXT 記錄在網域中不具任何效果，因此當您建立網域擁有權之後即可予以刪除。 若要建立 TXT 記錄，請遵循 [[新增 DNS 記錄] 中的程式來連接您的網域](https://go.microsoft.com/fwlink/p/?LinkId=532542)。 如果這些程序不適用，您將需要尋找適合 DNS 註冊機構的程序。
  
Confirm the successful creation of the TXT record via nslookup. Follow this syntax.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

這會產生與以下範例相似的輸出：
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a>在 Microsoft 365 中驗證網域擁有權

在此最後一個步驟中，您會驗證您擁有公開註冊網域的 Microsoft 365。 在此步驟之後，Microsoft 365 會開始接受路由傳送至新功能變數名稱的流量。 若要完成網域建立和註冊程序，請執行此命令。 
  
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
   
## <a name="see-also"></a>另請參閱

#### 

[合作夥伴說明](https://go.microsoft.com/fwlink/p/?LinkID=533477)

