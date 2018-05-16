---
title: Exchange Online 中的多個地理位置功能
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online 中的多個地理位置功能的多個地理區域展開您的 Office 365 目前狀態。
ms.openlocfilehash: ea00ab52142e92e122273ab4ba718e98bd94b572
ms.sourcegitcommit: 12d3223cc2d6bf39a8960409a923254e1790fd2f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="0103b-103">Exchange Online 中的多個地理位置功能</span><span class="sxs-lookup"><span data-stu-id="0103b-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="0103b-p101">Office 365 的多重地理位置功能啟用單一租用戶至跨多個地理位置 (Geos)。啟用多個地理位置時，客戶可以選取 Exchange Online 信箱內容 （靜態資料） 的位置每位使用者為基礎。</span><span class="sxs-lookup"><span data-stu-id="0103b-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations (Geos). When Multi-Geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="0103b-p102">初始租用戶位置 （稱為"default"或"集中管理 」 位置） 決定帳單地址為基礎。啟用多個地理位置時，您可以利用其他"衛星"位置的信箱：</span><span class="sxs-lookup"><span data-stu-id="0103b-p102">Your initial tenant location (referred to as your "default" or "central" location) is determined based on your billing address. When Multi-Geo is enabled, you can place mailboxes in additional "satellite" locations by:</span></span>

- <span data-ttu-id="0103b-108">直接在衛星中建立新的 Exchange Online 信箱。</span><span class="sxs-lookup"><span data-stu-id="0103b-108">Creating a new Exchange Online mailbox directly in a satellite.</span></span>

- <span data-ttu-id="0103b-109">將現有的 Exchange Online 信箱移至衛星。</span><span class="sxs-lookup"><span data-stu-id="0103b-109">Moving an existing Exchange Online mailbox into a satellite.</span></span>

- <span data-ttu-id="0103b-110">Onboarding 將信箱從內部部署 Exchange 組織將衛星直接。</span><span class="sxs-lookup"><span data-stu-id="0103b-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite.</span></span>

<span data-ttu-id="0103b-111">下列 Geos 都可供使用的多個地理位置設定：</span><span class="sxs-lookup"><span data-stu-id="0103b-111">The following Geos are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="0103b-112">亞太地區</span><span class="sxs-lookup"><span data-stu-id="0103b-112">Asia Pacific</span></span>

- <span data-ttu-id="0103b-113">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="0103b-113">Australia</span></span>

- <span data-ttu-id="0103b-114">加拿大</span><span class="sxs-lookup"><span data-stu-id="0103b-114">Canada</span></span>

- <span data-ttu-id="0103b-115">歐盟</span><span class="sxs-lookup"><span data-stu-id="0103b-115">European Union</span></span>

- <span data-ttu-id="0103b-116">印度 (目前僅供客戶在印度計費地址)</span><span class="sxs-lookup"><span data-stu-id="0103b-116">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="0103b-117">日本</span><span class="sxs-lookup"><span data-stu-id="0103b-117">Japan</span></span>

- <span data-ttu-id="0103b-118">韓國</span><span class="sxs-lookup"><span data-stu-id="0103b-118">Korea</span></span>

- <span data-ttu-id="0103b-119">英國</span><span class="sxs-lookup"><span data-stu-id="0103b-119">United Kingdom</span></span>

- <span data-ttu-id="0103b-120">美國</span><span class="sxs-lookup"><span data-stu-id="0103b-120">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="0103b-121">必要的設定</span><span class="sxs-lookup"><span data-stu-id="0103b-121">Prerequisite configuration</span></span>
<span data-ttu-id="0103b-p103">您可以開始使用多個地理位置功能在 Exchange Online 之前，Microsoft 需要設定多個地理位置支援 Exchange Online 租用。Order 多重地理位置授權和通常應該採取早於 30 天才能完成時就會觸發此單次設定程序。</span><span class="sxs-lookup"><span data-stu-id="0103b-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for Multi-Geo support. This one-time configuration process is triggered when you order Multi-Geo licenses and should typically take less than 30 days to complete.</span></span>

<span data-ttu-id="0103b-p104">將會收到通知在[Office 365 郵件管理中心](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)設定已啟動且完成。設定自動觸發時購買多重地理位置授權。</span><span class="sxs-lookup"><span data-stu-id="0103b-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has started and completed. Configuration is automatically triggered when you buy Multi-Geo licenses.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="0103b-126">信箱位置及移動</span><span class="sxs-lookup"><span data-stu-id="0103b-126">Mailbox placement and moves</span></span>
<span data-ttu-id="0103b-127">Microsoft 完成的必要的多個地理位置組態步驟之後，Exchange Online 會受限於使用者物件上呼叫的**PreferredDataLocation**屬性在 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="0103b-127">After Microsoft completes the prerequisite Multi-Geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="0103b-p105">Exchange Online 進行同步處理來自 Azure AD 的**PreferredDataLocation**屬性到 Exchange Online 的目錄服務中的**MailboxRegion**屬性。**MailboxRegion**的值會決定要放置使用者信箱及任何相關聯的封存信箱地理位置。您無法設定使用者的主要信箱和封存信箱來位於不同 Geos。只有一個地理位置可以設定每個使用者物件。</span><span class="sxs-lookup"><span data-stu-id="0103b-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It isn't possible to configure a user's primary mailbox and archive mailboxes to reside in different Geos. Only one Geo may be configured per user object.</span></span>

- <span data-ttu-id="0103b-132">當**PreferredDataLocation**設定與現有的信箱使用者上時，信箱將會自動移到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-132">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be automatically moved to the specified Geo.</span></span> 

- <span data-ttu-id="0103b-133">當**PreferredDataLocation**設定上沒有現有信箱的使用者時，將信箱佈建到指定的地理位置中。</span><span class="sxs-lookup"><span data-stu-id="0103b-133">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified Geo.</span></span> 

- <span data-ttu-id="0103b-134">如果沒有指定任何地理位置，信箱將會被放置在預設的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-134">If no Geo is specified, the mailbox will be placed in the default Geo.</span></span>

<span data-ttu-id="0103b-p106">**請注意**： 多重地理位置功能和 Skype 的商務線上地域主控會議這兩個使用者物件上使用**PreferredDataLocation**屬性來尋找服務。如果您在地域託管會議的使用者物件上設定**PreferredDataLocation**值，這些使用者的信箱將會自動移到指定的地理位置之後在 Office 365 租用戶上啟用多個地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-p106">**Note**: Multi-Geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified Geo after Multi-Geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="0103b-137">功能會受到限制的多個地理位置 in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="0103b-137">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="0103b-p107">使用者信箱、 資源信箱 （會議室及器材信箱） 和共用的信箱支援多個地理位置功能。您可以僅置於公用資料夾信箱與 Office 365 群組客戶的家用地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support Multi-Geo features. You can only place public folder mailboxes and Office 365 Groups in the customer's home Geo.</span></span>
 
2. <span data-ttu-id="0103b-p108">安全性和符合性功能 （例如稽核和 eDiscovery） 所能使用 Exchange 系統管理中心 (EAC) 中不提供多個地理位置的組織。而被必須使用[Office 365 的安全性與規範中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)設定安全性和符合性功能。</span><span class="sxs-lookup"><span data-stu-id="0103b-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in Multi-Geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="0103b-p109">當您將他們的信箱移至新的地理位置 outlook for Mac 使用者可能會遇到存取其線上封存資料夾暫時遺失。此條件可時發生使用者的主要和封存信箱皆位於不同 Geos 因為跨地理信箱移動可能會在不同時間完成。</span><span class="sxs-lookup"><span data-stu-id="0103b-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new Geo. This condition occurs when the user's the primary and archive mailboxes are in different Geos, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="0103b-p110">使用者無法跨 Geos outlook （前身為 Outlook Web App 或 OWA） 在 web 上共用*信箱資料夾*。例如，歐盟使用者無法使用網路上的 Outlook 開啟共用的資料夾位於美國信箱中。不過，Outlook web 使用者可以開啟*其他信箱*中不同 Geos 使用另一個瀏覽器視窗中[開啟另一個人信箱在 Outlook Web App 的另一個瀏覽器視窗中](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)所述。</span><span class="sxs-lookup"><span data-stu-id="0103b-p110">Users can't share *mailbox folders* across Geos in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="0103b-147">**請注意**： 跨地理信箱資料夾共用支援 windows 在 Outlook 中。</span><span class="sxs-lookup"><span data-stu-id="0103b-147">**Note**: Cross-Geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

5. <span data-ttu-id="0103b-p111">目前在 web 上的 Outlook 中不支援跨地理行事曆委派。在 Windows Outlook 支援跨地理行事曆委派。</span><span class="sxs-lookup"><span data-stu-id="0103b-p111">Currently, cross-Geo calendar delegation isn't supported in Outlook on the web. Cross-Geo calendar delegation is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="0103b-150">系統管理</span><span class="sxs-lookup"><span data-stu-id="0103b-150">Administration</span></span> 
<span data-ttu-id="0103b-p112">遠端 PowerShell 才可檢視及設定 Office 365 環境中的地理位置的相關內容。如需不同用來管理 Office 365，請參閱[管理 Office 365 和 Exchange Online 使用 Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="0103b-p112">Remote PowerShell is required to view and configure Geo-related properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="0103b-p113">您需要的[Microsoft Azure Active Directory PowerShell 模組](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)v1.1.166.0 或更新版本中以 v1.x 使用者物件，請參閱 ＜ **PreferredDataLocation**屬性。若要連線至 Azure AD PowerShell，請參閱 ＜ [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="0103b-p113">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="0103b-155">若要連線至 Exchange Online PowerShell，請參閱[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="0103b-155">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="0103b-156">直接連接到使用 Exchange Online PowerShell 特定地理位置</span><span class="sxs-lookup"><span data-stu-id="0103b-156">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="0103b-p114">一般而言，Exchange Online PowerShell 會連線至預設的地理位置。但是，您也可以連線至非預設 Geos 直接。因為效能改良功能，建議您直接連線至非預設地理位置僅管理該地理位置中的使用者時。</span><span class="sxs-lookup"><span data-stu-id="0103b-p114">Typically, Exchange Online PowerShell will connect to the default Geo. But, you can also connect directly to non-default Geos. Because of performance improvements, we recommend connecting directly to the non-default Geo when you only manage users in that Geo.</span></span>

<span data-ttu-id="0103b-p115">若要連線至特定的地理位置，*來指定 ConnectionUri*參數是不同於一般連線指示。其餘的命令和值都相同。步驟包括：</span><span class="sxs-lookup"><span data-stu-id="0103b-p115">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="0103b-163">在您的本機電腦上開啟 Windows PowerShell 並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0103b-163">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="0103b-164">在**Windows PowerShell 認證要求**] 對話方塊中，輸入您的公司或學校帳戶和密碼，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="0103b-164">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="0103b-p116">取代`<emailaddress>`使用電子郵件地址的**任何**目標地理位置中的信箱並執行下列命令。您的權限的信箱與關聯至您在步驟 1 中的認證不是因素;電子郵件地址只會告知 Exchange Online 連線的位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-p116">Replace `<emailaddress>` with the email address of **any** mailbox in the target Geo and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="0103b-167">例如，如果您想要連線的地理位置中的有效信箱的電子郵件地址 olga@contoso.onmicrosoft.com，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0103b-167">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="0103b-168">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0103b-168">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="0103b-169">Azure AD 連接版本需求</span><span class="sxs-lookup"><span data-stu-id="0103b-169">Azure AD Connect version requirements</span></span>
<span data-ttu-id="0103b-p117">AAD 連線版本 1.1.524.0 或更新版本進行同步處理的使用者物件上設定**PreferredDataLocation**屬性從內部部署 Active Directory 是唯一支援的方法。如需詳細指示，請參閱[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="0103b-p117">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="0103b-172">地理位置代碼</span><span class="sxs-lookup"><span data-stu-id="0103b-172">Geo Codes</span></span>
<span data-ttu-id="0103b-p118">您可以使用三個字母代碼**PreferredDataLocation**屬性中指定的地理位置。下表列出可用的 Geos 程式碼：</span><span class="sxs-lookup"><span data-stu-id="0103b-p118">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="0103b-175">地理</span><span class="sxs-lookup"><span data-stu-id="0103b-175">Geo</span></span> |<span data-ttu-id="0103b-176">代碼</span><span class="sxs-lookup"><span data-stu-id="0103b-176">Code</span></span> |
|---------|---------|
|<span data-ttu-id="0103b-177">亞太地區 /</span><span class="sxs-lookup"><span data-stu-id="0103b-177">Asia/Pacific</span></span> |<span data-ttu-id="0103b-178">APC</span><span class="sxs-lookup"><span data-stu-id="0103b-178">APC</span></span> |
|<span data-ttu-id="0103b-179">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="0103b-179">Australia</span></span> |<span data-ttu-id="0103b-180">澳洲</span><span class="sxs-lookup"><span data-stu-id="0103b-180">AUS</span></span> |
|<span data-ttu-id="0103b-181">加拿大</span><span class="sxs-lookup"><span data-stu-id="0103b-181">Canada</span></span> |<span data-ttu-id="0103b-182">可以</span><span class="sxs-lookup"><span data-stu-id="0103b-182">CAN</span></span> |
|<span data-ttu-id="0103b-183">歐盟</span><span class="sxs-lookup"><span data-stu-id="0103b-183">European Union</span></span> |<span data-ttu-id="0103b-184">EUR</span><span class="sxs-lookup"><span data-stu-id="0103b-184">EUR</span></span> |
|<span data-ttu-id="0103b-185">印度</span><span class="sxs-lookup"><span data-stu-id="0103b-185">India</span></span> |<span data-ttu-id="0103b-186">尋找</span><span class="sxs-lookup"><span data-stu-id="0103b-186">IND</span></span> |
|<span data-ttu-id="0103b-187">日本</span><span class="sxs-lookup"><span data-stu-id="0103b-187">Japan</span></span> |<span data-ttu-id="0103b-188">日文</span><span class="sxs-lookup"><span data-stu-id="0103b-188">JPN</span></span> |
|<span data-ttu-id="0103b-189">韓國</span><span class="sxs-lookup"><span data-stu-id="0103b-189">Korea</span></span> |<span data-ttu-id="0103b-190">韓文</span><span class="sxs-lookup"><span data-stu-id="0103b-190">KOR</span></span> |
|<span data-ttu-id="0103b-191">英國</span><span class="sxs-lookup"><span data-stu-id="0103b-191">United Kingdom</span></span> |<span data-ttu-id="0103b-192">GBR</span><span class="sxs-lookup"><span data-stu-id="0103b-192">GBR</span></span> |
|<span data-ttu-id="0103b-193">美國</span><span class="sxs-lookup"><span data-stu-id="0103b-193">United States</span></span> |<span data-ttu-id="0103b-194">名稱</span><span class="sxs-lookup"><span data-stu-id="0103b-194">NAM</span></span> |

<span data-ttu-id="0103b-p119">**請注意**： 在**PreferredDataLocation**和**MailboxRegion**屬性是字串沒有錯誤檢查。如果您輸入了無效的值 (例如 NAN) 信箱將會被放置在預設的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-p119">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="0103b-197">檢視設定於 Exchange Online 組織中使用 Geos</span><span class="sxs-lookup"><span data-stu-id="0103b-197">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="0103b-198">若要查看在 Exchange Online 組織中設定 Geos 的清單，請執行下列命令在 Exchange Online PowerShell：</span><span class="sxs-lookup"><span data-stu-id="0103b-198">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

<span data-ttu-id="0103b-199">此命令的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="0103b-199">The output of the command looks like this:</span></span>

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="0103b-200">尋找信箱的地理位置</span><span class="sxs-lookup"><span data-stu-id="0103b-200">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="0103b-201">在 Exchange Online PowerShell **Get-mailbox**指令程式會顯示下列地理位置相關屬性上的信箱：</span><span class="sxs-lookup"><span data-stu-id="0103b-201">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following Geo-related properties on mailboxes:</span></span>

- <span data-ttu-id="0103b-202">**資料庫**： 資料庫名稱的前 3 字母會對應至地理位置的程式碼會告訴您信箱所在目前。</span><span class="sxs-lookup"><span data-stu-id="0103b-202">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located.</span></span>

- <span data-ttu-id="0103b-203">**MailboxRegion**： 指定已設定 （已從**PreferredDataLocation**在 Azure AD 的同步處理） 系統的地理位置程式碼。</span><span class="sxs-lookup"><span data-stu-id="0103b-203">**MailboxRegion**: Specifies the Geo code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="0103b-204">**MailboxRegionLastUpdateTime**： 指出當 MailboxRegion 最近更新 （自動或手動）。</span><span class="sxs-lookup"><span data-stu-id="0103b-204">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="0103b-205">如需這些信箱的內容，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="0103b-205">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="0103b-206">例如，若要查看信箱 chris@contoso.onmicrosoft.com 地理資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0103b-206">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="0103b-207">此命令的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="0103b-207">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> <span data-ttu-id="0103b-208">如果地理位置中的程式碼的資料庫名稱不符合**MailboxRegion**值，信箱將會自動移到指定的**MailboxRegion**值 （Exchange Online 看起來如下列屬性值不符） 地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-208">If the Geo code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically moved to the Geo specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a><span data-ttu-id="0103b-209">將現有的雲端信箱移至特定的地理位置</span><span class="sxs-lookup"><span data-stu-id="0103b-209">Move an existing cloud mailbox to a specific Geo</span></span>
<span data-ttu-id="0103b-210">使用 Windows PowerShell 的 Azure AD 模組中的**Get-msoluser**和**Set-msoluser** cmdlet 可以檢視或指定要儲存使用者信箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-210">Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a user's mailbox will be stored.</span></span>

<span data-ttu-id="0103b-211">若要檢視使用者的**PreferredDataLocation**值，請在 Azure AD PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="0103b-211">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="0103b-212">例如，若要查看使用者 michelle@contoso.onmicrosoft.com **PreferredDataLocation**值，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0103b-212">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="0103b-213">此命令的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="0103b-213">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="0103b-214">若要修改的僅限雲端使用者物件的**PreferredDataLocation**值，請 Azure AD PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="0103b-214">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="0103b-215">例如，若要設定**PreferredDataLocation**值至歐盟 (EUR) 的使用者 michelle@contoso.onmicrosoft.com，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0103b-215">For example, to set the **PreferredDataLocation** value to the European Union (EUR) for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="0103b-216">**附註**：</span><span class="sxs-lookup"><span data-stu-id="0103b-216">**Notes**:</span></span>

- <span data-ttu-id="0103b-p120">如前文所述從內部部署 Active Directory 同步處理的使用者物件，您無法使用此程序。您需要變更**PreferredDataLocation**值使用 AAD 連線。如需詳細資訊，請參閱[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="0103b-p120">As mentioned previously for synchronized user objects from on-premises Active Directory, you can't use this procedure. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="0103b-220">將信箱移動所需的時間取決於數個因素：</span><span class="sxs-lookup"><span data-stu-id="0103b-220">How long it takes to move a mailbox depends on several factors:</span></span>
 
  - <span data-ttu-id="0103b-221">信箱的類型及大小。</span><span class="sxs-lookup"><span data-stu-id="0103b-221">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="0103b-222">要移動的信箱數目。</span><span class="sxs-lookup"><span data-stu-id="0103b-222">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="0103b-223">移動資源的可用性。</span><span class="sxs-lookup"><span data-stu-id="0103b-223">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="0103b-224">移動停用信箱上訴訟暫止狀態</span><span class="sxs-lookup"><span data-stu-id="0103b-224">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="0103b-p121">停用信箱訴訟暫止狀態的 ediscovery （英文） 用途不能移來變更其已停用狀態及其**PreferredDataLocation**值會保留。已停用將信箱移入訴訟資料暫留：</span><span class="sxs-lookup"><span data-stu-id="0103b-p121">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes can't be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="0103b-227">暫時將授權指派給信箱。</span><span class="sxs-lookup"><span data-stu-id="0103b-227">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="0103b-228">變更**PreferredDataLocation**。</span><span class="sxs-lookup"><span data-stu-id="0103b-228">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="0103b-229">其授權移除信箱後它已移至所選的地理位置以使其回到停用狀態。</span><span class="sxs-lookup"><span data-stu-id="0103b-229">Remove the license from the mailbox after it has been moved to the selected Geo to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="0103b-230">在特定地理位置中建立新的雲端信箱</span><span class="sxs-lookup"><span data-stu-id="0103b-230">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="0103b-231">若要在特定地理位置中建立新的信箱，您需要執行這些步驟的任一項：</span><span class="sxs-lookup"><span data-stu-id="0103b-231">To create a new mailbox in a specific Geo, you need to do either of these steps:</span></span>

- <span data-ttu-id="0103b-232">如先前所述，設定**PreferredDataLocation**值] 區段中*前*Exchange Online 中建立信箱 （例如由使用者設定**PreferredDataLocation**值之前將授權指派）。</span><span class="sxs-lookup"><span data-stu-id="0103b-232">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online (for example, by configuring the **PreferredDataLocation** value on a user before assigning a license).</span></span> 

- <span data-ttu-id="0103b-233">將授權指派同時設定**PreferredDataLocation**值。</span><span class="sxs-lookup"><span data-stu-id="0103b-233">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="0103b-234">若要建立新僅限雲端授權的使用者 （不 AAD 連線同步處理） 中特定的地理位置，請 Azure AD PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="0103b-234">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="0103b-235">本範例會為伊莉莎白 Brunner 建立新的使用者帳戶具有下列值：</span><span class="sxs-lookup"><span data-stu-id="0103b-235">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="0103b-236">使用者主體名稱： ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="0103b-236">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="0103b-237">名字： 伊莉莎白</span><span class="sxs-lookup"><span data-stu-id="0103b-237">First name: Elizabeth</span></span>

- <span data-ttu-id="0103b-238">姓氏： Brunner</span><span class="sxs-lookup"><span data-stu-id="0103b-238">Last name: Brunner</span></span>

- <span data-ttu-id="0103b-239">顯示名稱伊莉莎白 Brunner</span><span class="sxs-lookup"><span data-stu-id="0103b-239">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="0103b-240">密碼： 隨機產生所示命令的結果 （因為我們未使用*Password*參數）</span><span class="sxs-lookup"><span data-stu-id="0103b-240">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="0103b-241">授權： contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="0103b-241">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

<span data-ttu-id="0103b-242">3 位置： 澳洲 （澳洲）</span><span class="sxs-lookup"><span data-stu-id="0103b-242">3- Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="0103b-243">如需建立新的使用者帳戶和 Azure AD PowerShell 中尋找 LicenseAssignment 值的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)和[檢視授權和 Office 365 powershell 的服務](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="0103b-243">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> [!NOTE]
> <span data-ttu-id="0103b-p122">如果您使用 Exchange PowerShell 啟用信箱並必須直接在所指定的**PreferredDataLocation**地理位置中建立信箱，您需要使用 Exchange Online 指令程式，如**啟用信箱**或**新增信箱**直接對雲端服務。如果您使用**Enable-remotemailbox**內部部署 Exchange 指令程式，信箱會建立在預設的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-p122">If you are using Exchange PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="0103b-246">設定現有的內建內部部署信箱的特定地理位置</span><span class="sxs-lookup"><span data-stu-id="0103b-246">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="0103b-247">您可以使用標準的 onboarding 工具與程序將信箱從內部部署 Exchange 組織移轉至 Exchange Online，包括[在 EAC 中的遷移儀表板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)和[New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch)指令程式在 Exchange OnlinePowerShell。</span><span class="sxs-lookup"><span data-stu-id="0103b-247">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="0103b-p123">第一個步驟是驗證的使用者物件存在是 onboarded，並確認正確的**PreferredDataLocation**值已設定在 Azure AD 的每個信箱。Onboarding 工具會來**PreferredDataLocation**值並將信箱遷移直接至指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-p123">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="0103b-250">或者，您可以使用下列步驟以直接在 Exchange Online PowerShell 中使用[New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest)指令程式的特定地理位置中的內建信箱。</span><span class="sxs-lookup"><span data-stu-id="0103b-250">Or, you can use the following steps to onboard mailboxes directly in a specific Geo using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="0103b-p124">確認每個信箱設為 onboarded 和**PreferredDataLocation**設為所需的值在 Azure AD 存在於使用者物件。**PreferredDataLocation**的值會同步處理至相對應的郵件使用者物件的**MailboxRegion**屬性在 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="0103b-p124">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="0103b-253">直接連接到特定的衛星連線指示從使用本主題中前面的地理位置。</span><span class="sxs-lookup"><span data-stu-id="0103b-253">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="0103b-254">在 Exchange Online PowerShell 中儲存內部部署系統管理員認證是用以執行信箱移轉的變數中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="0103b-254">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="0103b-255">在 Exchange Online PowerShell 中建立新的**New-moverequest**類似下列的範例：</span><span class="sxs-lookup"><span data-stu-id="0103b-255">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="0103b-256">重複執行步驟 #4 您需要從內部部署 Exchange 移轉至衛星地理目前連線至每個信箱。</span><span class="sxs-lookup"><span data-stu-id="0103b-256">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite Geo you are currently connected to.</span></span>

6. <span data-ttu-id="0103b-257">如果您需要額外的信箱移轉至不同的衛星地理位置，請針對每個特定衛星地理重複步驟 2 到 4。</span><span class="sxs-lookup"><span data-stu-id="0103b-257">If you need to migrate additional mailboxes to a different satellite Geo, repeat steps 2 through 4 for each specific satellite Geo.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="0103b-258">多個地理位置報告</span><span class="sxs-lookup"><span data-stu-id="0103b-258">Multi-Geo Reporting</span></span>
<span data-ttu-id="0103b-p125">在 Office 365 系統管理中心中的**多個地理位置流量報告**顯示依地理位置的使用者人數。報表會顯示目前月份的使用者通訊群組並提供過去 6 個月的歷程資料。</span><span class="sxs-lookup"><span data-stu-id="0103b-p125">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by Geo. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
 
