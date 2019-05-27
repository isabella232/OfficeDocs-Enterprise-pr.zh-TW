---
title: 混合式新式驗證概觀及使用商務和 Exchange 伺服器內部部署用 Skype 的必要條件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: 新式驗證是一種方法提供更安全的使用者驗證及授權的身分識別管理。 使用混合式部署的 Skype for Business server 內部部署和 Exchange server 內部部署，以及分割網域 Skype for Business 混合。 此文章連結至相關的文件有關先決條件，安裝程式/停用新式驗證，和某些相關的用戶端 （例如。 Outlook 與 Skype 用戶端） 的資訊。
ms.openlocfilehash: 0448dfdc46598a6aa4df0108214ff0a4cf290382
ms.sourcegitcommit: 54c07ffcfe0da286b1780fdc03ba2f2fd0dbc86d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2019
ms.locfileid: "34404215"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="a88d2-106">混合式新式驗證概觀及使用商務和 Exchange 伺服器內部部署用 Skype 的必要條件</span><span class="sxs-lookup"><span data-stu-id="a88d2-106">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="a88d2-107">新式驗證是一種方法提供更安全的使用者驗證及授權的身分識別管理。</span><span class="sxs-lookup"><span data-stu-id="a88d2-107">Modern Authentication is a method of identity management that offers more secure user authentication and authorization.</span></span> <span data-ttu-id="a88d2-108">使用 Office 365 混合式部署的 Skype for Business server 內部部署和 Exchange server 內部部署，以及，分割網域 Skype for Business 混合。</span><span class="sxs-lookup"><span data-stu-id="a88d2-108">It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids.</span></span> <span data-ttu-id="a88d2-109">此文章連結至相關的文件有關先決條件，安裝程式/停用新式驗證，和某些相關的用戶端 （例如。</span><span class="sxs-lookup"><span data-stu-id="a88d2-109">This article links to related docs about prerequisites, setup/disabling Modern Authentication, and to some of the related client (ex.</span></span> <span data-ttu-id="a88d2-110">Outlook 與 Skype 用戶端） 的資訊。</span><span class="sxs-lookup"><span data-stu-id="a88d2-110">Outlook and Skype clients) information.</span></span> 
  
- [<span data-ttu-id="a88d2-111">什麼是新式驗證？</span><span class="sxs-lookup"><span data-stu-id="a88d2-111">What is Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [<span data-ttu-id="a88d2-112">有什麼變更時使用新式驗證嗎？</span><span class="sxs-lookup"><span data-stu-id="a88d2-112">What changes when I use Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [<span data-ttu-id="a88d2-113">檢查您的內部部署環境的新式驗證狀態</span><span class="sxs-lookup"><span data-stu-id="a88d2-113">Check the Modern Authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [<span data-ttu-id="a88d2-114">您符合新式驗證必要條件嗎？</span><span class="sxs-lookup"><span data-stu-id="a88d2-114">Do you meet Modern Authentication prerequisites?</span></span>](#do-you-meet-modern-authentication-prerequisites)
    
- [<span data-ttu-id="a88d2-115">我需要知道開始前什麼？</span><span class="sxs-lookup"><span data-stu-id="a88d2-115">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [<span data-ttu-id="a88d2-116">新式驗證 Url 清單</span><span class="sxs-lookup"><span data-stu-id="a88d2-116">List of Modern Authentication URLs</span></span>](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a><span data-ttu-id="a88d2-117">什麼是新式驗證？</span><span class="sxs-lookup"><span data-stu-id="a88d2-117">What is Modern Authentication?</span></span>
<span data-ttu-id="a88d2-118"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="a88d2-118"></span></span>

<span data-ttu-id="a88d2-119">當談論 （例如，您的膝上型電腦或手機） 的用戶端與伺服器之間的通訊，Microsoft 會使用片語 '新式驗證'。</span><span class="sxs-lookup"><span data-stu-id="a88d2-119">When talking about communication between a client (for example, your laptop or your phone) and a server, Microsoft uses the phrase 'Modern authentication'.</span></span>
  
<span data-ttu-id="a88d2-120">新式驗證是組合的驗證和授權方法，以及某些依賴存取原則，您可能已經熟悉的安全性措施雨傘字詞。</span><span class="sxs-lookup"><span data-stu-id="a88d2-120">Modern authentication is an umbrella term for a combination of authentication and authorization methods, as well as some security measures that rely on access policies that you may already be familiar with.</span></span> <span data-ttu-id="a88d2-121">其中包括：</span><span class="sxs-lookup"><span data-stu-id="a88d2-121">It includes:</span></span>
  
- <span data-ttu-id="a88d2-122">**驗證方法**： 多重要素驗證;用戶端憑證型驗證。</span><span class="sxs-lookup"><span data-stu-id="a88d2-122">**Authentication methods**: Multi-factor Authentication; Client Certificate-based authentication.</span></span>
    
- <span data-ttu-id="a88d2-123">**授權方法**： Open Authorization (OAuth) 的 Microsoft 實作。</span><span class="sxs-lookup"><span data-stu-id="a88d2-123">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth).</span></span> 
    
- <span data-ttu-id="a88d2-124">**條件式存取原則**： 行動應用程式管理 (MAM) 和 Azure Active Directory 條件式存取。</span><span class="sxs-lookup"><span data-stu-id="a88d2-124">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory Conditional Access.</span></span> 
    
<span data-ttu-id="a88d2-125">管理使用者身分識別與新式驗證可讓系統管理員使用談到保護資源，提供更安全的身分識別管理這兩個內部 （Exchange 和商務用 Skype） 方法時，請 Exchange 混合式許多不同的工具與 Skype for Business 混合/分割網域案例。</span><span class="sxs-lookup"><span data-stu-id="a88d2-125">Managing user identities with Modern Authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="a88d2-126">請注意，因為與 Exchange 密切商務用 Skype，登入行為 Skype，使用者會看到的商務用戶端將會受到 Exchange 的新式驗證狀態。</span><span class="sxs-lookup"><span data-stu-id="a88d2-126">Be aware that because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will be effected by the Modern Authentication status of Exchange.</span></span> <span data-ttu-id="a88d2-127">如果您有分割網域混合式商務用 Skype 時，這也會套用。</span><span class="sxs-lookup"><span data-stu-id="a88d2-127">This will also apply if you have a Skype for Business split-domain hybrid.</span></span> <span data-ttu-id="a88d2-128">此外，支援使用新式驗證混合式商務用 Skype 的類型通常稱為 '分割網域' （分割網域中有商務用 Skype 和 Skype for Business 上內部部署和使用者皆位於這兩個位置）。</span><span class="sxs-lookup"><span data-stu-id="a88d2-128">Also, the type of Skype for Business Hybrid that supports the use of Modern Authentication is often called a 'split-domain' (in a split-domain, you have both Skype for Business Online and Skype for Business on-prem, and users are homed in both locations).</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="a88d2-129">您知道的 2017 年 8 月起所有新的 Office 365 承租人，包括商務用 Skype online 和 Exchange online 將有預設啟用新式驗證嗎？</span><span class="sxs-lookup"><span data-stu-id="a88d2-129">Did you know that, as of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have Modern Authentication enabled by default?</span></span> <span data-ttu-id="a88d2-130">既有的租用戶不需要變更其預設 MA 的狀態，但所有的新租用戶自動支援擴充一組身分識別功能看上面所列。</span><span class="sxs-lookup"><span data-stu-id="a88d2-130">Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above.</span></span> <span data-ttu-id="a88d2-131">若要檢查 MA 狀態的商務用 Skype online，您可以使用 Skype 商務 online powershell，以全域系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="a88d2-131">To check your MA status for Skype for Business online, you can use Skype for Business online PowerShell with Global Admin credentials.</span></span> <span data-ttu-id="a88d2-132">執行`Get-CsOAuthConfiguration`若要檢查的-ClientADALAuthOverride 輸出。</span><span class="sxs-lookup"><span data-stu-id="a88d2-132">Run `Get-CsOAuthConfiguration` to check the output of -ClientADALAuthOverride.</span></span> <span data-ttu-id="a88d2-133">如果-ClientADALAuthOverride '允許' 您新式驗證是上。</span><span class="sxs-lookup"><span data-stu-id="a88d2-133">If -ClientADALAuthOverride is 'Allowed' your Modern Authentication is on.</span></span> 
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="a88d2-134">有什麼變更時使用新式驗證嗎？</span><span class="sxs-lookup"><span data-stu-id="a88d2-134">What changes when I use Modern Authentication?</span></span>
<span data-ttu-id="a88d2-135"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="a88d2-135"></span></span>

<span data-ttu-id="a88d2-136">當使用內部部署用 Skype 的新式驗證商務或 Exchange 伺服器，您仍*驗證*內部使用者，但*授權*的本文資源 （如檔案或電子郵件） 變更其存取。</span><span class="sxs-lookup"><span data-stu-id="a88d2-136">When using Modern Authentication with on-premises Skype for Business or Exchange server, you're still  *authenticating*  users on-premises, but the story of  *authorizing*  their access to resources (like files or emails) changes.</span></span> <span data-ttu-id="a88d2-137">這就是為什麼，但是新式驗證是關於用戶端和伺服器通訊期間 evoSTS (Security Token Service 使用 Azure AD) 中設定 MA 結果所採取的步驟正在 skype for Business 和 Exchange server 內部部署設定為驗證伺服器。</span><span class="sxs-lookup"><span data-stu-id="a88d2-137">This is why, though Modern Authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span> 
  
<span data-ttu-id="a88d2-138">EvoSTS 變更可讓您在內部伺服器，以利用授權您的用戶端，OAuth （token 發行），也可讓您在內部使用安全性方法一般在雲端 （例如多重要素驗證）。</span><span class="sxs-lookup"><span data-stu-id="a88d2-138">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication).</span></span> <span data-ttu-id="a88d2-139">此外，evoSTS 發出 token，可讓使用者不需為要求的一部分提供其密碼要求資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="a88d2-139">Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request.</span></span> <span data-ttu-id="a88d2-140">無論位於您的使用者 (online 或內部)，無論哪一個位置主控所需的資源，EvoSTS 會成為核心設定新式驗證之後，授權使用者和用戶端。</span><span class="sxs-lookup"><span data-stu-id="a88d2-140">No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once Modern Authentication is configured.</span></span>
  
<span data-ttu-id="a88d2-141">以下是範例我所代表的意義。</span><span class="sxs-lookup"><span data-stu-id="a88d2-141">Here's an example of what I mean.</span></span> <span data-ttu-id="a88d2-142">如果商務用 Skype 商務用戶端需要存取 Exchange 伺服器來取得代表使用者的行事曆資訊時，它會使用 Active Directory Authentication Library (ADAL) 若要這麼做。</span><span class="sxs-lookup"><span data-stu-id="a88d2-142">If Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so.</span></span> <span data-ttu-id="a88d2-143">ADAL 的程式碼庫旨在讓您的目錄中的安全的資源可供用戶端應用程式使用 OAuth 安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="a88d2-143">ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens.</span></span> <span data-ttu-id="a88d2-144">若要確認宣告並交換權杖 （而非密碼），以授與使用者資源的存取權的 oauth 的 ADAL 運作。</span><span class="sxs-lookup"><span data-stu-id="a88d2-144">ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource.</span></span> <span data-ttu-id="a88d2-145">在過去，像這樣-知道如何驗證使用者宣告和發行的所需的權杖伺服器--在交易中的授權單位可能已經被 Security Token Service 內部或甚至是 Active Directory Federation Services。</span><span class="sxs-lookup"><span data-stu-id="a88d2-145">In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services.</span></span> <span data-ttu-id="a88d2-146">不過，新式驗證可以集中與 Azure Active Directory (Azure AD)，在雲端中的授權單位。</span><span class="sxs-lookup"><span data-stu-id="a88d2-146">However, Modern Authentication centralizes that authority with Azure Active Directory (Azure AD) in the Cloud.</span></span>
  
<span data-ttu-id="a88d2-147">這也表示，即使您的 Exchange 伺服器與 Skype for Business 環境可能完全內部部署、 授權伺服器將會在線上，且您的內部部署環境必須建立和維護您的 Office 的連線能力在雲端 （和作為其目錄會使用您的訂閱的 Azure Active Directory 執行個體） 的 365 訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="a88d2-147">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure Active Directory instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="a88d2-148">什麼不會變更？</span><span class="sxs-lookup"><span data-stu-id="a88d2-148">What doesn't change?</span></span> <span data-ttu-id="a88d2-149">無論您是在分割網域混合式或使用 Skype for Business 和 Exchange server 內部部署中，所有使用者必須先都驗證*內部部署*。</span><span class="sxs-lookup"><span data-stu-id="a88d2-149">Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate  *on-premises*  .</span></span> <span data-ttu-id="a88d2-150">在混合式實作中的新式驗證，Lyncdiscovery 和自動探索指向您的內部部署伺服器。</span><span class="sxs-lookup"><span data-stu-id="a88d2-150">In a hybrid implementation of Modern Authentication, Lyncdiscovery and Autodiscovery point to your on-premises server.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="a88d2-151">如果您需要瞭解商務拓撲支援 MA 特定商務用 Skype，這是[記載在這裡](https://technet.microsoft.com/en-us/library/mt803262.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a88d2-151">If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/en-us/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="a88d2-152">檢查您的內部部署環境的新式驗證狀態</span><span class="sxs-lookup"><span data-stu-id="a88d2-152">Check the Modern Authentication status of your on-premises environment</span></span>
<span data-ttu-id="a88d2-153"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="a88d2-153"></span></span>

<span data-ttu-id="a88d2-154">因為新式驗證變更服務利用 OAuth/S2S 時所使用的授權伺服器，您需要知道的新式驗證是否開啟或關閉您 skype for Business 和 Exchange 環境。</span><span class="sxs-lookup"><span data-stu-id="a88d2-154">Because Modern Authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if Modern Authentication is On or Off for your Skype for Business and Exchange environment.</span></span> <span data-ttu-id="a88d2-155">您可以藉由執行檢查針對商務伺服器，內部部署，在您的 Exchange 或 Skype 狀態`Get-CSOAuthConfiguration`在 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="a88d2-155">You can check the status on your Exchange or Skype for Business servers, on premises, by running the `Get-CSOAuthConfiguration` command in PowerShell.</span></span> <span data-ttu-id="a88d2-156">如果該命令會傳回空的 'OAuthServers' 屬性，會停用的新式驗證。</span><span class="sxs-lookup"><span data-stu-id="a88d2-156">If the command returns an empty 'OAuthServers' property, then Modern Authentication is disabled.</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="a88d2-157">您符合新式驗證必要條件嗎？</span><span class="sxs-lookup"><span data-stu-id="a88d2-157">Do you meet Modern Authentication prerequisites?</span></span>

<span data-ttu-id="a88d2-158">確認，然後再繼續進行，請檢查清單關閉這些項目：</span><span class="sxs-lookup"><span data-stu-id="a88d2-158">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="a88d2-159">**特定商務用 Skype**</span><span class="sxs-lookup"><span data-stu-id="a88d2-159">**Skype for Business specific**</span></span>
    
  - <span data-ttu-id="a88d2-160">所有伺服器都必須 SFB Server 2015 CU5 或更新版本</span><span class="sxs-lookup"><span data-stu-id="a88d2-160">All servers must have SFB Server 2015 CU5 or later</span></span>
    
  - <span data-ttu-id="a88d2-161">**例外狀況**-生存能力 Branch Appliance (SBA) 便可位於目前版本 （根據 Lync 2013）</span><span class="sxs-lookup"><span data-stu-id="a88d2-161">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span> 
    
  - <span data-ttu-id="a88d2-162">SIP 網域會新增為 Office 365 中的同盟網域</span><span class="sxs-lookup"><span data-stu-id="a88d2-162">Your SIP domain is added as a Federated domain in Office 365</span></span>
    
  - <span data-ttu-id="a88d2-163">所有 SFB 前端都必須連線到網際網路，以 Office 365 驗證 Url (TCP 443) 輸出，而且熟知憑證根目錄 Crl (TCP 80) 會列出列 56 和 125 的[[Microsoft 365 一般及 Office Online] 區段中，Office 365 Url 和 IP位址範圍](urls-and-ip-address-ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="a88d2-163">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 56 and 125 of the 'Microsoft 365 Common and Office Online' section of [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
- <span data-ttu-id="a88d2-164">**商務用 Skype 內部部署混合式 Office 365 環境中**</span><span class="sxs-lookup"><span data-stu-id="a88d2-164">**Skype for Business on-premises in a hybrid Office 365 environment**</span></span>
  - <span data-ttu-id="a88d2-165">具有執行 Skype for Business Server 2019 的所有伺服器的商務 Server 2019 部署商務用 Skype。</span><span class="sxs-lookup"><span data-stu-id="a88d2-165">A Skype for Business Server 2019 deployment with all servers running Skype for Business Server 2019.</span></span>
  
  - <span data-ttu-id="a88d2-166">用 Skype Server 2015 部署與執行用 Skype Server 2015 的所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="a88d2-166">A Skype for Business Server 2015 deployment with all servers running Skype for Business Server 2015.</span></span>
  
  - <span data-ttu-id="a88d2-167">最多兩個不同的伺服器版本，如下所示的部署：</span><span class="sxs-lookup"><span data-stu-id="a88d2-167">A deployment with a maximum of two different server versions as listed below:</span></span>
  
     - <span data-ttu-id="a88d2-168">Skype for Business Server 2015 與 Skype for Business Server 2019</span><span class="sxs-lookup"><span data-stu-id="a88d2-168">Skype for Business Server 2015 and Skype for Business Server 2019</span></span>
     
  - <span data-ttu-id="a88d2-169">所有 Skype for Business 伺服器必須已安裝最新的 cummulative 更新，請參閱[Skype for Business Server 更新](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates)若要尋找與管理所有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="a88d2-169">All Skype for Business servers must have the latest cummulative updates installed, see [Skype for Business Server updates](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) to find and manage all available updates.</span></span>
  - <span data-ttu-id="a88d2-170">沒有任何 Lync Server 2010 或 2013 混合式環境中。</span><span class="sxs-lookup"><span data-stu-id="a88d2-170">There is no Lync Server 2010 or 2013 in the hybrid environment.</span></span>
    
 <span data-ttu-id="a88d2-171">**附註**如果您 Skype for Business 前端伺服器使用的網際網路存取 proxy 伺服器，必須在 [設定] 區段中的每個前端的 web.config 檔案中輸入 proxy 伺服器 IP 和連接埠號碼使用。</span><span class="sxs-lookup"><span data-stu-id="a88d2-171">**Note** If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span> 
  
- <span data-ttu-id="a88d2-172">針對 Business Server 2015\Web Components\Web C:\Program Files\Skype ticket\int\web.config</span><span class="sxs-lookup"><span data-stu-id="a88d2-172">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
    
- <span data-ttu-id="a88d2-173">針對 Business Server 2015\Web Components\Web C:\Program Files\Skype ticket\ext\web.config</span><span class="sxs-lookup"><span data-stu-id="a88d2-173">C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> <span data-ttu-id="a88d2-174">請務必訂閱 rss 摘要，讓[Office 365 Url 和 IP 位址範圍](urls-and-ip-address-ranges.md)保持最新的最新清單的所需的 Url。</span><span class="sxs-lookup"><span data-stu-id="a88d2-174">Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md) to stay current with the latest listings of required URLs.</span></span> 
  
- <span data-ttu-id="a88d2-175">**特定的 Exchange 伺服器**</span><span class="sxs-lookup"><span data-stu-id="a88d2-175">**Exchange Server specific**</span></span>
    
  - <span data-ttu-id="a88d2-176">您使用 [Exchange server 2013 CU19 和 up，或 Exchange server 2016 CU8 及設定。</span><span class="sxs-lookup"><span data-stu-id="a88d2-176">You're using either Exchange server 2013 CU19 and up, or Exchange server 2016 CU8 and up.</span></span>
    
  - <span data-ttu-id="a88d2-177">沒有任何 Exchange server 2010 環境中。</span><span class="sxs-lookup"><span data-stu-id="a88d2-177">There is no Exchange server 2010 in the environment.</span></span>
    
  - <span data-ttu-id="a88d2-178">未設定 SSL 卸載。</span><span class="sxs-lookup"><span data-stu-id="a88d2-178">SSL Offloading is not configured.</span></span> <span data-ttu-id="a88d2-179">支援 SSL 終止並重新加密。</span><span class="sxs-lookup"><span data-stu-id="a88d2-179">SSL termination and re-encryption is supported.</span></span>
    
  - <span data-ttu-id="a88d2-180">事件中您的環境使用 proxy 伺服器基礎結構，以允許伺服器進行連線到網際網路，請務必在所有 Exchange 伺服器都有[InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx)屬性中所定義的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a88d2-180">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
  
- <span data-ttu-id="a88d2-181">**Exchange Server 內部部署混合式 Office 365 環境中**</span><span class="sxs-lookup"><span data-stu-id="a88d2-181">**Exchange Server on-premises in a hybrid Office 365 environment**</span></span>

  - <span data-ttu-id="a88d2-182">如果您使用 Exchange server 2013，至少一部伺服器必須已安裝 Mailbox 和 Client Access server role。</span><span class="sxs-lookup"><span data-stu-id="a88d2-182">If you are using Exchange server 2013, At least one server must have the Mailbox and Client Access server roles installed.</span></span> <span data-ttu-id="a88d2-183">雖然可以在個別伺服器上安裝 Mailbox 和 Client Access role，我們強烈建議您安裝在每個伺服器，以提供額外的可靠性與效能改進這兩種角色。</span><span class="sxs-lookup"><span data-stu-id="a88d2-183">While it is possible to install the Mailbox and Client Access roles on separate servers, we strongly recommend that you install both roles on each server to provide additional reliability and improved performance.</span></span>
  
  - <span data-ttu-id="a88d2-184">如果您使用 Exchange server 2016 或更新版本，至少一部伺服器必須已安裝 Mailbox server role。</span><span class="sxs-lookup"><span data-stu-id="a88d2-184">If you are using Exchange server 2016 or later version, at least one server must have the Mailbox server role installed.</span></span>
  
  - <span data-ttu-id="a88d2-185">沒有任何 Exchange server 2007 或 2010 混合式環境中。</span><span class="sxs-lookup"><span data-stu-id="a88d2-185">There is no Exchange server 2007 or 2010 in the Hybrid environment.</span></span>
  
  - <span data-ttu-id="a88d2-186">所有 Exchange 伺服器必須已安裝最新的 cummulative 更新，請參閱[將 Exchange 升級至最新的累計更新](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019)若要尋找與管理所有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="a88d2-186">All Exchange servers must have the latest cummulative updates installed, see [Upgrade Exchange to the latest Cumulative Updates](https://docs.microsoft.com/en-us/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) to find and manage all available updates.</span></span>
    
- <span data-ttu-id="a88d2-187">**Exchange 用戶端和通訊協定需求**</span><span class="sxs-lookup"><span data-stu-id="a88d2-187">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="a88d2-188">下列用戶端支援新式驗證：</span><span class="sxs-lookup"><span data-stu-id="a88d2-188">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="a88d2-189">**用戶端**</span><span class="sxs-lookup"><span data-stu-id="a88d2-189">**Clients**</span></span>|<span data-ttu-id="a88d2-190">**主要的通訊協定**</span><span class="sxs-lookup"><span data-stu-id="a88d2-190">**Primary Protocol**</span></span>|<span data-ttu-id="a88d2-191">**附註**</span><span class="sxs-lookup"><span data-stu-id="a88d2-191">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="a88d2-192">Outlook 2013 與 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="a88d2-192">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="a88d2-193">MAPI over HTTP</span><span class="sxs-lookup"><span data-stu-id="a88d2-193">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="a88d2-194">必須在 Exchange 中啟用 MAPI over HTTP，才能使用這些用戶端 （通常是已啟用或則為 True 的新安裝的 Exchange 2013 Service Pack 1 和上方）; 利用新式驗證如需詳細資訊請參閱 < <b0>Office 2013 和 Office 2016 用戶端應用程式的方式新式驗證運作</b0>。</span><span class="sxs-lookup"><span data-stu-id="a88d2-194">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).</span></span>  <br/> <span data-ttu-id="a88d2-195">確定您正在執行的 Outlook; 最小必要的建置請參閱 <<c0>使用 Windows Installer (MSI) 的 Outlook 版本的最新更新。</span><span class="sxs-lookup"><span data-stu-id="a88d2-195">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="a88d2-196">Mac 版 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="a88d2-196">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="a88d2-197">Exchange Web 服務</span><span class="sxs-lookup"><span data-stu-id="a88d2-197">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="a88d2-198">Outlook for iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="a88d2-198">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="a88d2-199">如需詳細資訊，請參閱[使用混合式新式驗證與 Outlook for iOS 和 Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。</span><span class="sxs-lookup"><span data-stu-id="a88d2-199">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="a88d2-200">Exchange ActiveSync 用戶端 (例如 iOS11 Mail)</span><span class="sxs-lookup"><span data-stu-id="a88d2-200">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="a88d2-201">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="a88d2-201">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="a88d2-202">對於支援新式驗證的 Exchange ActiveSync 用戶端，必須重新建立設定檔，以便從基本驗證切換至新式驗證。</span><span class="sxs-lookup"><span data-stu-id="a88d2-202">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="a88d2-203">**一般的必要條件**</span><span class="sxs-lookup"><span data-stu-id="a88d2-203">**General prerequisites**</span></span>
    
  - <span data-ttu-id="a88d2-204">如果您使用 ADFS，您應該會有 Windows 2012 R2 ADFS 3.0 及以上進行同盟</span><span class="sxs-lookup"><span data-stu-id="a88d2-204">If you use ADFS, you should have Windows 2012 R2 ADFS 3.0 and above for federation</span></span>
    
  - <span data-ttu-id="a88d2-205">您的身分識別組態是否有任何支援 AAD 連線的類型 (例如密碼雜湊同步處理，通過驗證，內部部署 Office 365 所支援的 STS，et cetera。)</span><span class="sxs-lookup"><span data-stu-id="a88d2-205">Your identity configurations are any of the types supported by AAD Connect (such as password hash sync, pass-through authentication, on-premises STS supported by Office 365, et cetera.)</span></span>
    
  - <span data-ttu-id="a88d2-206">您需要 AAD 連線設定，並進行使用者複寫及同步處理正常運作。</span><span class="sxs-lookup"><span data-stu-id="a88d2-206">You have AAD Connect configured and functioning for user replication and sync.</span></span>
    
  - <span data-ttu-id="a88d2-207">您已經驗證該混合式設定使用您的內部部署和 Office 365 環境之間的傳統 Exchange 混合式拓撲模式。</span><span class="sxs-lookup"><span data-stu-id="a88d2-207">You have verified that hybrid is configured using Exchange Classic Hybrid Topology mode between your on-premises and Office 365 environment.</span></span> <span data-ttu-id="a88d2-208">Exchange 混合式的正式支援陳述式會指出您必須有目前的 CU 或目前的 CU-1。</span><span class="sxs-lookup"><span data-stu-id="a88d2-208">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    
    > [!Note]
    > <span data-ttu-id="a88d2-209">使用[混合式代理程式](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent)不支援混合式新式驗證。</span><span class="sxs-lookup"><span data-stu-id="a88d2-209">Hybrid Modern Authentication is not supported with the [Hybrid Agent](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).</span></span>
    
  - <span data-ttu-id="a88d2-210">請確定這兩個內部部署測試使用者，如混合式測試使用者位於 Office 365 登入商務桌面用戶端 （如果您想要使用 Skype 的新式驗證） 用 Skype 和 Microsoft Outlook （如果您想要讓使用啟用新式驗證Exchange)。</span><span class="sxs-lookup"><span data-stu-id="a88d2-210">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use Modern Authentication with Skype) and Microsoft Outlook (if you want so use Modern Authentication with Exchange).</span></span>
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="a88d2-211">我需要知道開始前什麼？</span><span class="sxs-lookup"><span data-stu-id="a88d2-211">What else do I need to know before I begin?</span></span>
<span data-ttu-id="a88d2-212"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="a88d2-212"></span></span>

1. <span data-ttu-id="a88d2-213">內部伺服器上的所有案例牽涉都到新式驗證內部部署的設定 （事實上，如商務用 Skype 沒有支援拓撲的清單），以便將負責驗證和授權的伺服器中的 Microsoft Cloud （AAD 的安全性權杖服務，稱為 'evoSTS'），並更新 Azure Active Directory (AAD)，相關的 Url 或使用任一 Skype 基於商業或 Exchange 內部部署安裝的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a88d2-213">All the scenarios for on-premises servers involve setting up Modern Authentication on-premises (in fact, for Skype for Business there is a list of Supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (AAD's security token service, called 'evoSTS'), and updating Azure Active Directory (AAD) about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange.</span></span> <span data-ttu-id="a88d2-214">因此，在內部伺服器採用 Microsoft Cloud 相依性。</span><span class="sxs-lookup"><span data-stu-id="a88d2-214">Therefore, on-premises servers take on a Microsoft Cloud dependency.</span></span> <span data-ttu-id="a88d2-215">執行此動作無法被視為設定 '混合式驗證'。</span><span class="sxs-lookup"><span data-stu-id="a88d2-215">Taking this action could be considered configuring 'hybrid auth'.</span></span>
    
2. <span data-ttu-id="a88d2-216">此文章的連結出給其他人可協助您選擇支援的新式驗證拓撲 （僅適用於商務用 Skype 的必要） 和相關文件的大綱設定步驟，或步驟，即可停用新式驗證，如 Exchange 內部部署與商務用 Skype 內部部署。</span><span class="sxs-lookup"><span data-stu-id="a88d2-216">This article links out to others that will help you choose supported Modern Authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable Modern Authentication, for Exchange on-premises and Skype for Business on-premises.</span></span> <span data-ttu-id="a88d2-217">最愛此頁面在瀏覽器，如果您將需要首頁基底的伺服器環境中使用新式驗證。</span><span class="sxs-lookup"><span data-stu-id="a88d2-217">Favourite this page in your browser if you're going to need a home-base for using Modern Authentication in your server environment.</span></span>
    
## <a name="list-of-modern-authentication-urls"></a><span data-ttu-id="a88d2-218">新式驗證 Url 清單</span><span class="sxs-lookup"><span data-stu-id="a88d2-218">List of Modern Authentication URLs</span></span>
<span data-ttu-id="a88d2-219"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="a88d2-219"></span></span>

- [<span data-ttu-id="a88d2-220">如何設定 Exchange Server 內部部署以使用新式驗證</span><span class="sxs-lookup"><span data-stu-id="a88d2-220">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="a88d2-221">商務用 Skype 的新式驗證與支援的商務拓撲</span><span class="sxs-lookup"><span data-stu-id="a88d2-221">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [<span data-ttu-id="a88d2-222">如何設定商務用 Skype 內部部署以使用新式驗證</span><span class="sxs-lookup"><span data-stu-id="a88d2-222">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="a88d2-223">從商務用 Skype 與 Exchange 移除或停用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="a88d2-223">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

