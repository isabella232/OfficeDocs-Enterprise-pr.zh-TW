---
title: 利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 新增用戶端租用網域
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 摘要：使用 Windows PowerShell for Office 365 將替代網域名稱新增至現有的客戶租用戶。
ms.openlocfilehash: 5f22e21e1eafc7c2d3fb9bc7286e860ad468445b
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257462"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="bd037-103">利用適用於委派存取權限 (DAP) 合作夥伴的 Windows PowerShell 新增用戶端租用網域</span><span class="sxs-lookup"><span data-stu-id="bd037-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="bd037-104">**摘要：** 使用 Windows PowerShell for Office 365 將替代網域名稱新增至現有的客戶租用戶。</span><span class="sxs-lookup"><span data-stu-id="bd037-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="bd037-105">您可以使用 Windows PowerShell for Office 365 來建立新網域，並與客戶的租用建立關聯，速度勝於使用 Windows 365 系統管理中心。</span><span class="sxs-lookup"><span data-stu-id="bd037-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="bd037-106">委派的存取權限 (DAP) 合作夥伴就是新聞訂閱方式和雲端解決方案提供者 (CSP) 合作夥伴。</span><span class="sxs-lookup"><span data-stu-id="bd037-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="bd037-107">他們通常是其他公司的網路或電信服務提供者。</span><span class="sxs-lookup"><span data-stu-id="bd037-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="bd037-108">他們會在提供給客戶的服務方案中搭售 Office 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="bd037-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="bd037-109">當他們銷售 Office 365 訂閱時，會自動將管理代表 (AOBO) 權限授與「客戶租用」，讓他們能夠管理和報告客戶租用。</span><span class="sxs-lookup"><span data-stu-id="bd037-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="bd037-110">開始之前有哪些須知？</span><span class="sxs-lookup"><span data-stu-id="bd037-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="bd037-p102">本主題中的程序需要您連線到 Office 365 的 Windows PowerShell。如需詳細指示，請參閱[連線至 Office 365 PowerShell](connect-to-office-365-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="bd037-p102">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="bd037-113">您也需要合作夥伴租用戶系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="bd037-113">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="bd037-114">您也需要下列資訊︰</span><span class="sxs-lookup"><span data-stu-id="bd037-114">You also need the following information:</span></span>
  
- <span data-ttu-id="bd037-115">您需要客戶要求的完整網域名稱 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="bd037-115">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="bd037-116">您需要客戶的 **TenantId** 。</span><span class="sxs-lookup"><span data-stu-id="bd037-116">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="bd037-p103">FQDN 必須是已向網際網路網域名稱服務 (DNS) 註冊機構註冊的名稱 (如 GoDaddy)。如需公開註冊網域名稱的詳細資訊，請參閱[如何購買網域名稱](https://go.microsoft.com/fwlink/p/?LinkId=532541)。</span><span class="sxs-lookup"><span data-stu-id="bd037-p103">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="bd037-p104">您需要知道如何為 DNS 註冊機構將 TXT 記錄新增至已註冊的 DNS 區域。如需新增 TXT 記錄的詳細資訊，請參閱[在任一 DNS 主機服務提供者建立 Office 365 的 DNS 記錄](https://go.microsoft.com/fwlink/p/?LinkId=532542)。如果這些程序不適用，您將需要尋找適合 DNS 註冊機構的程序。</span><span class="sxs-lookup"><span data-stu-id="bd037-p104">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="bd037-122">建立網域</span><span class="sxs-lookup"><span data-stu-id="bd037-122">Create domains</span></span>

 <span data-ttu-id="bd037-p105">客戶可能會要求您建立額外的網域來與租用相關聯，因為他們不希望預設的<網域>.onmicrosoft.com網域成為向全世界代表公司身分的主要網域。此程序會引導您完成與客戶租用相關聯之新網域的建立步驟。</span><span class="sxs-lookup"><span data-stu-id="bd037-p105">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="bd037-125">若要執行這些作業部分，登入與協力廠商系統管理員帳戶必須設定為**完整管理\*\*\*\*支援指派的管理存取權的公司**在 Microsoft 365 系統管理中心中設定的系統管理員帳戶的詳細資料中找到。</span><span class="sxs-lookup"><span data-stu-id="bd037-125">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="bd037-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span><span class="sxs-lookup"><span data-stu-id="bd037-126">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="bd037-127">在 Azure Active Directory 中建立網域</span><span class="sxs-lookup"><span data-stu-id="bd037-127">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="bd037-128">此命令會在 Azure Active Directory 中建立網域，但不會將新網域與公開註冊的網域建立關聯。</span><span class="sxs-lookup"><span data-stu-id="bd037-128">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="bd037-129">當您向適用於企業的 Microsoft Office 365 證明擁有公開註冊的網域時才能建立關聯。</span><span class="sxs-lookup"><span data-stu-id="bd037-129">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="bd037-130">PowerShell 核心不支援的 Microsoft Azure Active Directory 模組的 Windows PowerShell 模組和具有**Msol** cmdlet 在其名稱。</span><span class="sxs-lookup"><span data-stu-id="bd037-130">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="bd037-131">若要繼續使用這些 cmdlet，您必須從 Windows PowerShell 執行它們。</span><span class="sxs-lookup"><span data-stu-id="bd037-131">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="bd037-132">取得 TXT DNS 驗證記錄的資料</span><span class="sxs-lookup"><span data-stu-id="bd037-132">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="bd037-p109">Office 365 會產生需要置入 DNS TXT 驗證記錄中的特定資料。若要取得資料，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="bd037-p109">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="bd037-135">這會產生與以下範例相似的輸出：</span><span class="sxs-lookup"><span data-stu-id="bd037-135">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="bd037-136">您需要這些文字才能在公開註冊的 DNS 區域中建立 TXT 記錄。</span><span class="sxs-lookup"><span data-stu-id="bd037-136">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="bd037-137">請務必將其複製並儲存。</span><span class="sxs-lookup"><span data-stu-id="bd037-137">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="bd037-138">將 TXT 記錄新增至公開註冊的 DNS 區域</span><span class="sxs-lookup"><span data-stu-id="bd037-138">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="bd037-139">在 Office 365 開始接受導向公開註冊網域名稱的流量之前，您必須證明擁有及具備網域的管理員權限。</span><span class="sxs-lookup"><span data-stu-id="bd037-139">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="bd037-140">您可以在網域中建立 TXT 記錄，藉此證明擁有該網域。</span><span class="sxs-lookup"><span data-stu-id="bd037-140">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="bd037-141">TXT 記錄在網域中不具任何效果，因此當您建立網域擁有權之後即可予以刪除。</span><span class="sxs-lookup"><span data-stu-id="bd037-141">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="bd037-142">若要建立 TXT 記錄，請遵循[在任一 DNS 主機服務提供者建立 Office 365 的 DNS 記錄](https://go.microsoft.com/fwlink/p/?LinkId=532542)中的程序。</span><span class="sxs-lookup"><span data-stu-id="bd037-142">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="bd037-143">如果這些程序不適用，您將需要尋找適合 DNS 註冊機構的程序。</span><span class="sxs-lookup"><span data-stu-id="bd037-143">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="bd037-p112">透過 nslookup 確認成功建立 TXT 記錄。請遵循此語法。</span><span class="sxs-lookup"><span data-stu-id="bd037-p112">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="bd037-146">這會產生與以下範例相似的輸出：</span><span class="sxs-lookup"><span data-stu-id="bd037-146">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="bd037-147">在 Office 365 中驗證網域擁有權</span><span class="sxs-lookup"><span data-stu-id="bd037-147">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="bd037-p113">在最後一個步驟中，您向 Office 365 證明擁有公開註冊的網域。此步驟之後，Office 365 會開始接受路由傳送到新網域名稱的流量。若要完成網域建立和註冊程序，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="bd037-p113">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="bd037-151">此命令將不會傳回任何輸出，因此若要確認命令正常運作，請執行此命令。</span><span class="sxs-lookup"><span data-stu-id="bd037-151">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="bd037-152">這會傳回與以下範例相似的內容：</span><span class="sxs-lookup"><span data-stu-id="bd037-152">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="bd037-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd037-153">See also</span></span>

#### 

[<span data-ttu-id="bd037-154">合作夥伴說明</span><span class="sxs-lookup"><span data-stu-id="bd037-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

