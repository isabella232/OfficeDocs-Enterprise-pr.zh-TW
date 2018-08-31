---
title: 經過驗證的混合式概觀及使用內部部署 Skype 中的商務與 Exchange 伺服器的先決條件
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: 現代驗證是一種方法提供較安全的使用者驗證和授權的身分識別管理。使用混合式部署的 Skype Business server 內部部署與 Exchange server 內部部署，以及商務混合的分隔網域 Skype。本文章的連結與相關文件需安裝程式/停用經過驗證的必要條件以及部分相關的用戶端 （例如 Outlook 和 Skype 用戶端） 資訊。
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240588"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a><span data-ttu-id="75523-106">經過驗證的混合式概觀及使用內部部署 Skype 中的商務與 Exchange 伺服器的先決條件</span><span class="sxs-lookup"><span data-stu-id="75523-106">Hybrid Modern Authentication overview and prerequisites for using it with on-premises Skype for Business and Exchange servers</span></span>

<span data-ttu-id="75523-p102">現代驗證是一種方法提供較安全的使用者驗證和授權的身分識別管理。使用 Office 365 的 Skype 的混合式部署 Business server 內部部署和 Exchange server 內部部署，以及、 商務混合的分隔網域 Skype。本文章的連結與相關文件需安裝程式/停用經過驗證的必要條件以及部分相關的用戶端 （例如 Outlook 和 Skype 用戶端） 資訊。</span><span class="sxs-lookup"><span data-stu-id="75523-p102">Modern Authentication is a method of identity management that offers more secure user authentication and authorization. It's available for Office 365 hybrid deployments of Skype for Business server on-premises and Exchange server on-premises, as well as, split-domain Skype for Business hybrids. This article links to related docs about prerequisites, setup/disabling Modern Authentication, and to some of the related client (ex. Outlook and Skype clients) information.</span></span> 
  
- [<span data-ttu-id="75523-111">什麼是經過驗證？</span><span class="sxs-lookup"><span data-stu-id="75523-111">What is Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [<span data-ttu-id="75523-112">有什麼變更時使用經過驗證？</span><span class="sxs-lookup"><span data-stu-id="75523-112">What changes when I use Modern Authentication?</span></span>](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [<span data-ttu-id="75523-113">檢查您的內部部署環境的現代驗證狀態</span><span class="sxs-lookup"><span data-stu-id="75523-113">Check the Modern Authentication status of your on-premises environment</span></span>](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [<span data-ttu-id="75523-114">您符合經過驗證的必要條件嗎？</span><span class="sxs-lookup"><span data-stu-id="75523-114">Do you meet Modern Authentication prerequisites?</span></span>](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [<span data-ttu-id="75523-115">我需要知道開始前還有什麼？</span><span class="sxs-lookup"><span data-stu-id="75523-115">What else do I need to know before I begin?</span></span>](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [<span data-ttu-id="75523-116">現代驗證 Url 清單</span><span class="sxs-lookup"><span data-stu-id="75523-116">List of Modern Authentication URLs</span></span>](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a><span data-ttu-id="75523-117">什麼是經過驗證？</span><span class="sxs-lookup"><span data-stu-id="75523-117">What is Modern Authentication?</span></span>
<span data-ttu-id="75523-118"><a name="BKMK_WhatisModAuth"> </a></span><span class="sxs-lookup"><span data-stu-id="75523-118"></span></span>

<span data-ttu-id="75523-119">當談論 （例如膝上型電腦或您的電話） 的用戶端與伺服器之間的通訊，Microsoft 會使用片語 '現代驗證 」。</span><span class="sxs-lookup"><span data-stu-id="75523-119">When talking about communication between a client (for example, your laptop or your phone) and a server, Microsoft uses the phrase 'Modern authentication'.</span></span>
  
<span data-ttu-id="75523-p103">現代驗證是雨傘字詞的驗證和授權方法以及依賴存取原則可能熟悉的一些安全性量值的組合。包含：</span><span class="sxs-lookup"><span data-stu-id="75523-p103">Modern authentication is an umbrella term for a combination of authentication and authorization methods, as well as some security measures that rely on access policies that you may already be familiar with. It includes:</span></span>
  
- <span data-ttu-id="75523-122">**驗證方法**： 多重要素驗證 ；用戶端憑證型驗證 ；與 Active Directory 驗證文件庫 ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx))。</span><span class="sxs-lookup"><span data-stu-id="75523-122">**Authentication methods**: Multi-factor Authentication; Client Certificate-based authentication; and the Active Directory Authentication Library ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).</span></span>
    
- <span data-ttu-id="75523-123">**授權方法**： Microsoft 的實作 Open Authorization (OAuth)。</span><span class="sxs-lookup"><span data-stu-id="75523-123">**Authorization methods**: Microsoft's implementation of Open Authorization (OAuth).</span></span> 
    
- <span data-ttu-id="75523-124">**設定格式化的條件存取原則**： 行動應用程式管理 」 (MAM) 和 Azure Active Directory 設定格式化的條件存取。</span><span class="sxs-lookup"><span data-stu-id="75523-124">**Conditional access policies**: Mobile Application Management (MAM) and Azure Active Directory Conditional Access.</span></span> 
    
<span data-ttu-id="75523-125">管理使用經過驗證的使用者身分識別提供系統管理員使用它可保護資源並提供更安全的身分識別管理這兩個內部部署 （Exchange 和 Skype for Business） 方法時，Exchange 混合式許多不同的工具和 Skype 商務混合/分割網域案例。</span><span class="sxs-lookup"><span data-stu-id="75523-125">Managing user identities with Modern Authentication gives administrators many different tools to use when it comes to securing resources and offers more secure methods of identity management to both on-premises (Exchange and Skype for Business), Exchange hybrid, and Skype for Business hybrid/split-domain scenarios.</span></span>
  
<span data-ttu-id="75523-p104">請注意與 Exchange 密切合作 Skype for Business，因為使用者會看到的商務用戶端登入行為 Skype 將會受到 Exchange 摩登的驗證狀態。這也會套用如果您有商務分隔網域混合式的 Skype。此外，Skype 支援使用經過驗證的商務混合式的類型通常稱為 「 分割網域 」 （在分隔網域中具有商務 online Skype 和 Skype 的業務上-prem 和使用者皆位於兩個位置）。</span><span class="sxs-lookup"><span data-stu-id="75523-p104">Be aware that because Skype for Business works closely with Exchange, the login behaviour Skype for Business client users will see will be effected by the Modern Authentication status of Exchange. This will also apply if you have a Skype for Business split-domain hybrid. Also, the type of Skype for Business Hybrid that supports the use of Modern Authentication is often called a 'split-domain' (in a split-domain, you have both Skype for Business Online and Skype for Business on-prem, and users are homed in both locations).</span></span>
  
 <span data-ttu-id="75523-p105">**重要**您知道 2017 年 8 月、 年所有新 Office 365 租用戶的線上包括 Skype for Business 和 Exchange online 會有預設啟用的現代驗證嗎？既承租人不會有變更其預設 MA 的狀態，但所有新的租用戶自動支援擴充的功能集的識別您看到以上所列。若要線上檢查 for Business Skype MA 狀態，您可以使用 Skype 商務 powershell online 以全域管理員認證。執行 'Get-csoauthconfiguration' 檢查-ClientADALAuthOverride 的輸出。若啟用-ClientADALAuthOverride 則' ' 摩登的驗證是上。</span><span class="sxs-lookup"><span data-stu-id="75523-p105">**Important** Did you know that, as of August of 2017, all new Office 365 tenants that include Skype for Business online and Exchange online will have Modern Authentication enabled by default? Pre-existing tenants won't have a change in their default MA state, but all new tenants automatically support the expanded set of identity features you see listed above. To check your MA status for Skype for Business online, you can use Skype for Business online PowerShell with Global Admin credentials. Run ' Get-CsOAuthConfiguration' to check the output of -ClientADALAuthOverride. If -ClientADALAuthOverride is 'Allowed' your Modern Authentication is on.</span></span> 
  
## <a name="what-changes-when-i-use-modern-authentication"></a><span data-ttu-id="75523-134">有什麼變更時使用經過驗證？</span><span class="sxs-lookup"><span data-stu-id="75523-134">What changes when I use Modern Authentication?</span></span>
<span data-ttu-id="75523-135"><a name="BKMK_WhatChanges"> </a></span><span class="sxs-lookup"><span data-stu-id="75523-135"></span></span>

<span data-ttu-id="75523-p106">使用時經過驗證的內部 Skype 商務或 Exchange server，您還是*驗證*使用者內部部署，但的*授權*由來資源 （例如檔或電子郵件） 變更其存取。這是為何，但是現代驗證需用戶端和伺服器通訊時 evoSTS (Security Token Service 使用 Azure AD) 中設定 MA 結果所採取的步驟是要設為 [驗證伺服器 Skype 的業務與 Exchange server 的內部。</span><span class="sxs-lookup"><span data-stu-id="75523-p106">When using Modern Authentication with on-premises Skype for Business or Exchange server, you're still  *authenticating*  users on-premises, but the story of  *authorizing*  their access to resources (like files or emails) changes. This is why, though Modern Authentication is about client and server communication, the steps taken during configuring MA result in evoSTS (a Security Token Service used by Azure AD) being set as Auth Server for Skype for Business and Exchange server on-premises.</span></span> 
  
<span data-ttu-id="75523-p107">EvoSTS 變更可讓您在內部伺服器的授權您的用戶端充分運用 OAuth （token 發行） 和也可讓您在內部使用安全性方法一般在雲端 （例如多重要素驗證）。此外，evoSTS 問題允許使用者而不提供其密碼的要求一部分要求資源的存取權的 token。不論隸屬使用者 (online 或內部部署)，與位置裝載所需的資源，不論 EvoSTS 會成為的授權使用者與用戶端設定現代驗證之後核心。</span><span class="sxs-lookup"><span data-stu-id="75523-p107">The change to evoSTS allows your on-premises servers to take advantage of OAuth (token issuance) for authorizing your clients, and also lets your on-premises use security methods common in the cloud (like Multi-factor Authentication). Additionally, the evoSTS issues tokens that allow users to request access to resources without supplying their password as part of the request. No matter where your users are homed (of online or on-premises), and no matter which location hosts the needed resource, EvoSTS will become the core of authorizing users and clients once Modern Authentication is configured.</span></span>
  
<span data-ttu-id="75523-p108">以下是範例我的意義。如果 Skype 商務用戶端的需求來存取取得代表使用者的行事曆資訊的 Exchange server，它會使用 Active Directory 驗證文件庫 (ADAL) 若要這樣做。ADAL 的程式碼庫設計您的目錄中可供用戶端應用程式使用 OAuth 安全性權杖進行安全的資源。若要確認宣告並交換權杖 （而非密碼）、 授與使用者存取資源的 OAuth 與 ADAL works。過去在類似這一個-知道如何驗證使用者宣告及問題所需的權杖伺服器--在交易中的授權單位可能已 Security Token Service 內部或甚至是 Active Directory Federation Services。不過，現代驗證可集中與 Azure Active Directory (Azure AD)，雲端中的授權單位。</span><span class="sxs-lookup"><span data-stu-id="75523-p108">Here's an example of what I mean. If Skype for Business client needs to access Exchange server to get calendar information on behalf of a user, it uses the Active Directory Authentication Library (ADAL) to do so. ADAL is a code library designed to make secured resources in your directory available to client applications using OAuth security tokens. ADAL works with OAuth to verify claims and to exchange tokens (rather than passwords), to grant a user access to a resource. In the past, the authority in a transaction like this one -- the server that knows how to validate user claims and issue the needed tokens -- might have been a Security Token Service on-premises, or even Active Directory Federation Services. However, Modern Authentication centralizes that authority with Azure Active Directory (Azure AD) in the Cloud.</span></span>
  
<span data-ttu-id="75523-147">這也表示，即使您的 Exchange server 和 Skype 的商務環境可能完全內部部署、 授權伺服器會成為 online 和內部部署環境必須建立及維護您的 Office 的連線能力在雲端 （與您的訂閱使用作為其目錄的 Azure Active Directory 執行個體） 的 365 訂閱。</span><span class="sxs-lookup"><span data-stu-id="75523-147">This also means that even though your Exchange server and Skype for Business environments may be entirely on-premises, the authorizing server will be online, and your on-premises environment must have the ability to create and maintain a connection to your Office 365 subscription in the Cloud (and the Azure Active Directory instance that your subscription uses as its directory).</span></span>
  
<span data-ttu-id="75523-p109">項目不會變更？無論您是在分隔網域混合式或使用 Skype 的業務與 Exchange server 內部部署中，所有使用者必須先進行都驗證*的內部*。在經過驗證的混合式實作、 Lyncdiscovery 和自動探索指向內部伺服器。</span><span class="sxs-lookup"><span data-stu-id="75523-p109">What doesn't change? Whether you're in a split-domain hybrid or using Skype for Business and Exchange server on-premises, all users must first authenticate  *on-premises*  . In a hybrid implementation of Modern Authentication, Lyncdiscovery and Autodiscovery point to your on-premises server.</span></span> 
  
 <span data-ttu-id="75523-151">**重要**如果您需要知道特定 Skype 商務拓撲支援 MA，這是[記載以下右邊](https://technet.microsoft.com/en-us/library/mt803262.aspx)。</span><span class="sxs-lookup"><span data-stu-id="75523-151">**Important** If you need to know the specific Skype for Business topologies supported with MA, that's [documented right here](https://technet.microsoft.com/en-us/library/mt803262.aspx).</span></span>
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a><span data-ttu-id="75523-152">檢查您的內部部署環境的現代驗證狀態</span><span class="sxs-lookup"><span data-stu-id="75523-152">Check the Modern Authentication status of your on-premises environment</span></span>
<span data-ttu-id="75523-153"><a name="BKMK_CheckStatus"> </a></span><span class="sxs-lookup"><span data-stu-id="75523-153"></span></span>

<span data-ttu-id="75523-p110">因為現代驗證變更服務運用 OAuth/S2S 時所使用的授權伺服器，您需要知道經過驗證的業務與 Exchange 環境您 Skype 是否是開啟或關閉。您可以在 PowerShell 中執行 Get-csoauthconfiguration 命令來檢查商務伺服器，在內部部署，Exchange 或 Skype 上的狀態。如果此命令會傳回空的 'OAuthServers' 屬性、 現代驗證已停用。</span><span class="sxs-lookup"><span data-stu-id="75523-p110">Because Modern Authentication changes the authorization server used when services leverage OAuth/S2S, you need to know if Modern Authentication is On or Off for your Skype for Business and Exchange environment. You can check the status on your Exchange or Skype for Business servers, on premises, by running the Get-CSOAuthConfiguration command in PowerShell. If the command returns an empty ' OAuthServers' property, then Modern Authentication is disabled.</span></span>
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a><span data-ttu-id="75523-157">您符合經過驗證的必要條件嗎？</span><span class="sxs-lookup"><span data-stu-id="75523-157">Do you meet Modern Authentication prerequisites?</span></span>

<span data-ttu-id="75523-158">確認，然後再繼續檢查您的清單關閉這些項目：</span><span class="sxs-lookup"><span data-stu-id="75523-158">Verify and check these items off your list before you continue:</span></span>
  
- <span data-ttu-id="75523-159">**針對 Business 特定 Skype**</span><span class="sxs-lookup"><span data-stu-id="75523-159">**Skype for Business specific**</span></span>
    
  - <span data-ttu-id="75523-160">所有伺服器都必須 SFB Server 2015 CU5 或更新版本</span><span class="sxs-lookup"><span data-stu-id="75523-160">All servers must have SFB Server 2015 CU5 or later</span></span>
    
  - <span data-ttu-id="75523-161">**例外狀況**-生存能力 Branch Appliance (SBA) 可位於目前的版本 （根據 Lync 2013）</span><span class="sxs-lookup"><span data-stu-id="75523-161">**Exception** - Survivability Branch Appliance (SBA) can be on the current version (based on Lync 2013)</span></span> 
    
  - <span data-ttu-id="75523-162">SIP 網域會新增為 Office 365 中的同盟網域</span><span class="sxs-lookup"><span data-stu-id="75523-162">Your SIP domain is added as a Federated domain in Office 365</span></span>
    
  - <span data-ttu-id="75523-163">所有 SFB 前端都必須連線至網際網路，Office 365 驗證 Url (TCP 443) 和熟知憑證根 Crl (TCP 80) 撥出的列 1 及 2 的[Office 365 Url 和 IP 的 'Office 365 驗證及身分識別 」 一節中列出處理範圍](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E)。</span><span class="sxs-lookup"><span data-stu-id="75523-163">All SFB Front Ends must have connections outbound to the internet, to Office 365 Authentication URLs (TCP 443) and well known certificate root CRLs (TCP 80) listed in Rows 1 and 2 of the 'Office 365 authentication and identity' section of [Office 365 URLs and IP address ranges](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E).</span></span>
    
 <span data-ttu-id="75523-164">**附註**如果您 Skype 商務前端伺服器用於網際網路存取 proxy 伺服器，必須輸入 proxy 伺服器 IP 和連接埠號碼用在 [設定] 區段中的每個前端的 web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="75523-164">**Note** If your Skype for Business front-end servers use a proxy server for Internet access, the proxy server IP and Port number used must be entered in the configuration section of the web.config file for each front end.</span></span> 
  
- <span data-ttu-id="75523-165">針對 Business Server 2015\Web Components\Web ticket\int\web.config c:\program files\Skype</span><span class="sxs-lookup"><span data-stu-id="75523-165">c:\program files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config</span></span>
    
- <span data-ttu-id="75523-166">針對 Business Server 2015\Web Components\Web ticket\ext\web.config c:\program files\Skype</span><span class="sxs-lookup"><span data-stu-id="75523-166">c:\program files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config</span></span>
    
- <span data-ttu-id="75523-167">\</system.identityModel.services\></span><span class="sxs-lookup"><span data-stu-id="75523-167">\</system.identityModel.services\></span></span>
    
     <span data-ttu-id="75523-168">\<system.net\></span><span class="sxs-lookup"><span data-stu-id="75523-168">\<system.net\></span></span> 
    
     <span data-ttu-id="75523-169">\<defaultProxy\></span><span class="sxs-lookup"><span data-stu-id="75523-169">\<defaultProxy\></span></span> 
    
     <span data-ttu-id="75523-170">\<proxy</span><span class="sxs-lookup"><span data-stu-id="75523-170">\<proxy</span></span> 
    
     <span data-ttu-id="75523-171">proxyaddress ="http://192.168.100.60:8080"</span><span class="sxs-lookup"><span data-stu-id="75523-171">proxyaddress="http://192.168.100.60:8080"</span></span> 
    
     <span data-ttu-id="75523-172">bypassonlocal ="true"</span><span class="sxs-lookup"><span data-stu-id="75523-172">bypassonlocal="true"</span></span> 
    
     /\> 
    
     <span data-ttu-id="75523-173">\</defaultProxy\></span><span class="sxs-lookup"><span data-stu-id="75523-173">\</defaultProxy\></span></span> 
    
     <span data-ttu-id="75523-174">\</system.net\></span><span class="sxs-lookup"><span data-stu-id="75523-174">\</system.net\></span></span> 
    
    <span data-ttu-id="75523-175">\</configuration\></span><span class="sxs-lookup"><span data-stu-id="75523-175">\</configuration\></span></span>
    
 <span data-ttu-id="75523-176">**重要**請務必以訂閱 RSS 摘要的[Office 365 Url 和 IP 位址範圍](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)保持最新的 Url 所需的最新的清單。</span><span class="sxs-lookup"><span data-stu-id="75523-176">**Important** Be sure to subscribe to the RSS feed for [Office 365 URLs and IP address ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to stay current with the latest listings of required URLs.</span></span> 
  
- <span data-ttu-id="75523-177">**特定的 Exchange Server**</span><span class="sxs-lookup"><span data-stu-id="75523-177">**Exchange Server specific**</span></span>
    
  - <span data-ttu-id="75523-178">您使用 [Exchange server 2013 CU19 和，或 Exchange server 2016 CU8 及向上。</span><span class="sxs-lookup"><span data-stu-id="75523-178">You're using either Exchange server 2013 CU19 and up, or Exchange server 2016 CU8 and up.</span></span>
    
  - <span data-ttu-id="75523-179">在環境中的沒有 Exchange server 2010。</span><span class="sxs-lookup"><span data-stu-id="75523-179">There is no Exchange server 2010 in the environment.</span></span>
    
  - <span data-ttu-id="75523-p111">未設定 SSL 卸載。支援 SSL 終止並重新加密。</span><span class="sxs-lookup"><span data-stu-id="75523-p111">SSL Offloading is not configured. SSL termination and re-encryption is supported.</span></span>
    
  - <span data-ttu-id="75523-182">事件中您的環境使用 proxy 伺服器基礎結構，以允許伺服器進行連線到網際網路，請確定所有 Exchange 伺服器都已[InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx)屬性中所定義的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="75523-182">In the event your environment utilizes a proxy server infrastructure to allow servers to connect to the Internet, be sure all Exchange servers have the proxy server defined in the [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) property.</span></span>
    
- <span data-ttu-id="75523-183">**Exchange 用戶端和通訊協定需求**</span><span class="sxs-lookup"><span data-stu-id="75523-183">**Exchange client and protocol requirements**</span></span>
  
  - <span data-ttu-id="75523-184">下列用戶端支援現代驗證：</span><span class="sxs-lookup"><span data-stu-id="75523-184">The following clients support modern authentication:</span></span>

  |<span data-ttu-id="75523-185">**用戶端**</span><span class="sxs-lookup"><span data-stu-id="75523-185">**Clients**</span></span>|<span data-ttu-id="75523-186">**主要的通訊協定**</span><span class="sxs-lookup"><span data-stu-id="75523-186">**Primary Protocol**</span></span>|<span data-ttu-id="75523-187">**附註**</span><span class="sxs-lookup"><span data-stu-id="75523-187">**Notes**</span></span>|
  |:-----|:-----|:-----|
  |<span data-ttu-id="75523-188">Outlook 2013 與 Outlook 2016</span><span class="sxs-lookup"><span data-stu-id="75523-188">Outlook 2013 and Outlook 2016</span></span>  <br/> |<span data-ttu-id="75523-189">MAPI over HTTP</span><span class="sxs-lookup"><span data-stu-id="75523-189">MAPI over HTTP</span></span>  <br/> |<span data-ttu-id="75523-190">MAPI over HTTP 必須啟用 Exchange 內才能並用摩登的驗證與這些用戶端 （通常被啟用或新安裝 Exchange 2013 Service Pack 1 和上方則為 True） ；如需詳細資訊請參閱 ＜ [Office 2013 與 Office 2016 用戶端應用程式如何經過驗證的運作](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016)。</span><span class="sxs-lookup"><span data-stu-id="75523-190">MAPI over HTTP must be enabled within Exchange in order to leverage modern authentication with these clients (usually enabled or True for new installs of Exchange 2013 Service Pack 1 and above); for more information see [How modern authentication works for Office 2013 and Office 2016 client apps](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).</span></span>  <br/> <span data-ttu-id="75523-191">確定您正在執行 Outlook; 最小必要的建置請參閱[的 Outlook 會使用 Windows Installer (MSI) 版本的最新更新](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi)。</span><span class="sxs-lookup"><span data-stu-id="75523-191">Ensure you are running the minimum required build of Outlook; see [Latest updates for versions of Outlook that use Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).</span></span>  <br/> |
  |<span data-ttu-id="75523-192">Outlook 2016 for Mac</span><span class="sxs-lookup"><span data-stu-id="75523-192">Outlook 2016 for Mac</span></span>  <br/> |<span data-ttu-id="75523-193">Exchange Web 服務</span><span class="sxs-lookup"><span data-stu-id="75523-193">Exchange Web Services</span></span>  <br/> |  <br/> |
  |<span data-ttu-id="75523-194">Outlook for iOS 和 Android</span><span class="sxs-lookup"><span data-stu-id="75523-194">Outlook for iOS and Android</span></span>  <br/> |  <br/> |<span data-ttu-id="75523-195">如需詳細資訊，請參閱[使用 hybrid 現代 Authentication with Outlook iOS 及 android （英文）](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) 。</span><span class="sxs-lookup"><span data-stu-id="75523-195">See [Using hybrid Modern Authentication with Outlook for iOS and Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) for more information.</span></span>  <br/> |
  |<span data-ttu-id="75523-196">Exchange ActiveSync 用戶端 （例如 iOS11 郵件）</span><span class="sxs-lookup"><span data-stu-id="75523-196">Exchange ActiveSync clients (e.g., iOS11 Mail)</span></span>  <br/> |<span data-ttu-id="75523-197">Exchange ActiveSync</span><span class="sxs-lookup"><span data-stu-id="75523-197">Exchange ActiveSync</span></span>  <br/> |<span data-ttu-id="75523-198">支援經過驗證的 Exchange ActiveSync 用戶端，則必須重新設定檔建立以從基本驗證切換至經過驗證。</span><span class="sxs-lookup"><span data-stu-id="75523-198">For Exchange ActiveSync clients that support modern authentication, you must recreate the profile in order to switch from basic authentication to modern authentication.</span></span>  <br/> |

- <span data-ttu-id="75523-199">**一般的先決條件**</span><span class="sxs-lookup"><span data-stu-id="75523-199">**General prerequisites**</span></span>
    
  - <span data-ttu-id="75523-200">如果您使用 ADFS，您應該會有 Windows 2012 R2 ADFS 3.0 及以上的同盟</span><span class="sxs-lookup"><span data-stu-id="75523-200">If you use ADFS, you should have Windows 2012 R2 ADFS 3.0 and above for federation</span></span>
    
  - <span data-ttu-id="75523-201">您的身分識別設定是否有任何支援 AAD 連線的類型 (例如密碼雜湊同步處理、 通過驗證內部部署 Office 365 所支援的 STS，et cetera。)</span><span class="sxs-lookup"><span data-stu-id="75523-201">Your identity configurations are any of the types supported by AAD Connect (such as password hash sync, pass-through authentication, on-premises STS supported by Office 365, et cetera.)</span></span>
    
  - <span data-ttu-id="75523-202">您必須 AAD 連線設定且運作的使用者複寫及同步處理。</span><span class="sxs-lookup"><span data-stu-id="75523-202">You have AAD Connect configured and functioning for user replication and sync.</span></span>
    
  - <span data-ttu-id="75523-203">確認該混合使用內部部署和 Office 365 之間：</span><span class="sxs-lookup"><span data-stu-id="75523-203">You have verified that hybrid is working between your on-premises and Office 365:</span></span>
    
  - <span data-ttu-id="75523-204">Exchange 混合式的正式支援陳述式會指出您必須具備目前 CU 或目前 CU-1。</span><span class="sxs-lookup"><span data-stu-id="75523-204">Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.</span></span>
    
  - <span data-ttu-id="75523-205">請確定這兩個內部部署測試使用者，如混合測試使用者隸屬於 Office 365 登入 Skype 商務桌面用戶端 （如果您想要使用經過驗證與 Skype） 及 Microsoft Outlook （如果您想要讓使用經過驗證Exchange)。</span><span class="sxs-lookup"><span data-stu-id="75523-205">Make sure both an on-premises test user, as well as a hybrid test user homed in Office 365, can login to the Skype for Business desktop client (if you want to use Modern Authentication with Skype) and Microsoft Outlook (if you want so use Modern Authentication with Exchange).</span></span>
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a><span data-ttu-id="75523-206">我需要知道開始前還有什麼？</span><span class="sxs-lookup"><span data-stu-id="75523-206">What else do I need to know before I begin?</span></span>
<span data-ttu-id="75523-207"><a name="BKMK_Whatelse"> </a></span><span class="sxs-lookup"><span data-stu-id="75523-207"></span></span>

1. <span data-ttu-id="75523-p112">內部部署伺服器的所有案例都包含經過驗證的內部設定 （事實上，如 Skype for Business 有支援的清單） 使負責驗證和授權的伺服器位於 Microsoft Cloud （AAD 的 security token service、 呼叫 'evoSTS')，並更新 Azure Active Directory (AAD)，相關的 Url 或內部部署安裝的其中一個 Skype 商務或 Exchange 所使用的命名空間。因此，在內部伺服器會採用 Microsoft Cloud 相依性。利用此動作無法被視為設定 '混合式驗證 」。</span><span class="sxs-lookup"><span data-stu-id="75523-p112">All the scenarios for on-premises servers involve setting up Modern Authentication on-premises (in fact, for Skype for Business there is a list of Supported topologies) so that the server responsible for authentication and authorization is in the Microsoft Cloud (AAD's security token service, called 'evoSTS'), and updating Azure Active Directory (AAD) about the URLs or namespaces used by your on-premises installation of either Skype for Business or Exchange. Therefore, on-premises servers take on a Microsoft Cloud dependency. Taking this action could be considered configuring 'hybrid auth'.</span></span>
    
2. <span data-ttu-id="75523-p113">本文章的連結取出給其他人可協助您選擇支援現代驗證拓撲 （僅適用於企業版 Skype 的必要），與使用方法文章該大綱的設定步驟，或 Exchange 內部可停用現代驗證步驟與 Skype 企業內部。最愛在瀏覽器如果您將需要在您的伺服器環境中使用經過驗證的常用基底些此頁面。</span><span class="sxs-lookup"><span data-stu-id="75523-p113">This article links out to others that will help you choose supported Modern Authentication topologies (necessary only for Skype for Business), and how-to articles that outline the setup steps, or steps to disable Modern Authentication, for Exchange on-premises and Skype for Business on-premises. Favourite this page in your browser if you're going to need a home-base for using Modern Authentication in your server environment.</span></span>
    
## <a name="list-of-modern-authentication-urls"></a><span data-ttu-id="75523-213">現代驗證 Url 清單</span><span class="sxs-lookup"><span data-stu-id="75523-213">List of Modern Authentication URLs</span></span>
<span data-ttu-id="75523-214"><a name="BKMK_URLListforMA"> </a></span><span class="sxs-lookup"><span data-stu-id="75523-214"></span></span>

- [<span data-ttu-id="75523-215">如何設定 Exchange Server 內部使用經過驗證</span><span class="sxs-lookup"><span data-stu-id="75523-215">How to configure Exchange Server on-premises to use Modern Authentication</span></span>](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="75523-216">Skype 現代驗證支援的商務拓撲</span><span class="sxs-lookup"><span data-stu-id="75523-216">Skype for Business topologies supported with Modern Authentication</span></span>](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [<span data-ttu-id="75523-217">如何設定為使用經過驗證的企業內部 Skype</span><span class="sxs-lookup"><span data-stu-id="75523-217">How to configure Skype for Business on-premises to use Modern Authentication</span></span>](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [<span data-ttu-id="75523-218">從商務用 Skype 與 Exchange 移除或停用混合式新式驗證</span><span class="sxs-lookup"><span data-stu-id="75523-218">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

