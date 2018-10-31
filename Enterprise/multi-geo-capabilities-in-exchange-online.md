---
title: Exchange Online 中的多個地理位置功能
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online 中的多個地理位置功能的多個地理區域展開您的 Office 365 目前狀態。
ms.openlocfilehash: 5f34a2da47b9767aa9dfe22c6be7237951128960
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849919"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a><span data-ttu-id="64023-103">Exchange Online 中的多個地理位置功能</span><span class="sxs-lookup"><span data-stu-id="64023-103">Multi-Geo Capabilities in Exchange Online</span></span>

<span data-ttu-id="64023-p101">Office 365 的多重地理位置功能啟用單一租用戶至跨多個地理位置。啟用多個地理位置時，客戶可以選取 Exchange Online 信箱內容 （靜態資料） 的位置每位使用者為基礎。</span><span class="sxs-lookup"><span data-stu-id="64023-p101">Multi-Geo Capabilities in Office 365 enable a single tenant to span multiple geographic locations. When multi-geo is enabled, customers can select the location of Exchange Online mailbox content (data at rest) on a per-user basis.</span></span>

<span data-ttu-id="64023-p102">初始租用戶位置 （稱為集中管理位置） 決定帳單地址為基礎。啟用多個地理位置時，您可以利用信箱中的其他衛星位置：</span><span class="sxs-lookup"><span data-stu-id="64023-p102">Your initial tenant location (referred to as the central location) is determined based on your billing address. When multi-geo is enabled, you can place mailboxes in additional satellite locations by:</span></span>

- <span data-ttu-id="64023-108">直接在衛星位置中建立新的 Exchange Online 信箱。</span><span class="sxs-lookup"><span data-stu-id="64023-108">Creating a new Exchange Online mailbox directly in a satellite location.</span></span>

- <span data-ttu-id="64023-109">將現有的 Exchange Online 信箱移至衛星位置。</span><span class="sxs-lookup"><span data-stu-id="64023-109">Moving an existing Exchange Online mailbox into a satellite location.</span></span>

- <span data-ttu-id="64023-110">Onboarding 將信箱從內部部署 Exchange 組織直接將衛星位置。</span><span class="sxs-lookup"><span data-stu-id="64023-110">Onboarding a mailbox from an on-premises Exchange organization directly into a satellite location.</span></span>

<span data-ttu-id="64023-111">下列的地理位置都可供使用的多個地理位置設定：</span><span class="sxs-lookup"><span data-stu-id="64023-111">The following geo locations are available for use in a Multi-Geo configuration:</span></span>

- <span data-ttu-id="64023-112">亞太地區</span><span class="sxs-lookup"><span data-stu-id="64023-112">Asia Pacific</span></span>

- <span data-ttu-id="64023-113">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="64023-113">Australia</span></span>

- <span data-ttu-id="64023-114">加拿大</span><span class="sxs-lookup"><span data-stu-id="64023-114">Canada</span></span>

- <span data-ttu-id="64023-115">歐盟</span><span class="sxs-lookup"><span data-stu-id="64023-115">European Union</span></span>

- <span data-ttu-id="64023-116">法國</span><span class="sxs-lookup"><span data-stu-id="64023-116">France</span></span>

- <span data-ttu-id="64023-117">印度 (目前僅供客戶在印度計費地址)</span><span class="sxs-lookup"><span data-stu-id="64023-117">India (currently only available to customers with billing addresses in India)</span></span>

- <span data-ttu-id="64023-118">日本</span><span class="sxs-lookup"><span data-stu-id="64023-118">Japan</span></span>

- <span data-ttu-id="64023-119">韓國</span><span class="sxs-lookup"><span data-stu-id="64023-119">Korea</span></span>

- <span data-ttu-id="64023-120">英國</span><span class="sxs-lookup"><span data-stu-id="64023-120">United Kingdom</span></span>

- <span data-ttu-id="64023-121">美國</span><span class="sxs-lookup"><span data-stu-id="64023-121">United States</span></span>

## <a name="prerequisite-configuration"></a><span data-ttu-id="64023-122">必要的設定</span><span class="sxs-lookup"><span data-stu-id="64023-122">Prerequisite configuration</span></span>
<span data-ttu-id="64023-p103">您可以開始使用多個地理位置功能在 Exchange Online 之前，Microsoft 需要設定多個地理位置支援 Exchange Online 租用。排序 [Office 365 多重地理位置和授權在顯示您的租用戶之後觸發此單次設定程序。此單次設定程序通常應該採取早於 30 天才能完成。若要排序 Office 365 多重地理位置、 連絡 Microsoft 代表。如需詳細資訊，請參閱https://aka.ms/Multi-Geo。</span><span class="sxs-lookup"><span data-stu-id="64023-p103">Before you can start using Multi-Geo capabilities in Exchange Online, Microsoft needs to configure your Exchange Online tenant for multi-geo support. This one-time configuration process is triggered after you order Office 365 Multi-Geo and the licenses show up in your tenant. This one-time configuration process should typically take less than 30 days to complete. To order Office 365 Multi-Geo, contact your Microsoft representative. For more information, see https://aka.ms/Multi-Geo.</span></span>

<span data-ttu-id="64023-p104">將會收到通知在[Office 365 郵件內](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)完成您的設定之後。設定自動觸發之後在您的租用戶中顯示多個地理位置授權。</span><span class="sxs-lookup"><span data-stu-id="64023-p104">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) when your configuration has completed. Configuration is automatically triggered once your multi-geo licenses show up in your tenant.</span></span>

## <a name="mailbox-placement-and-moves"></a><span data-ttu-id="64023-130">信箱位置及移動</span><span class="sxs-lookup"><span data-stu-id="64023-130">Mailbox placement and moves</span></span>
<span data-ttu-id="64023-131">Microsoft 完成必要的多個地理位置的設定步驟之後，Exchange Online 會受限於使用者物件上呼叫的**PreferredDataLocation**屬性在 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="64023-131">After Microsoft completes the prerequisite multi-geo configuration steps, Exchange Online will honor the **PreferredDataLocation** attribute on user objects in Azure AD.</span></span>

<span data-ttu-id="64023-p105">Exchange Online 進行同步處理來自 Azure AD 的**PreferredDataLocation**屬性到 Exchange Online 的目錄服務中的**MailboxRegion**屬性。**MailboxRegion**的值會決定要放置使用者信箱及任何相關聯的封存信箱地理位置。您不可以設定使用者的主要信箱和封存信箱來位於不同地理位置。只有一個地理位置可以設定每個使用者物件。</span><span class="sxs-lookup"><span data-stu-id="64023-p105">Exchange Online synchronizes the **PreferredDataLocation** property from Azure AD into the **MailboxRegion** property in the Exchange Online directory service. The value of **MailboxRegion** determines the Geo where user mailboxes and any associated archive mailboxes will be placed. It is not possible to configure a user's primary mailbox and archive mailboxes to reside in different geo locations. Only one geo location may be configured per user object.</span></span>

- <span data-ttu-id="64023-136">當**PreferredDataLocation**設定與現有的信箱使用者上時，信箱會放入佇列中重新配置和自動移到指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-136">When **PreferredDataLocation** is configured on a user with an existing mailbox, the mailbox will be put into a relocation queue and automatically moved to the specified geo location.</span></span> 

- <span data-ttu-id="64023-137">當**PreferredDataLocation**設定上沒有現有信箱的使用者時，將信箱佈建到指定的地理位置中。</span><span class="sxs-lookup"><span data-stu-id="64023-137">When **PreferredDataLocation** is configured on a user without an existing mailbox, the mailbox will be provisioned into the specified geo location.</span></span> 

- <span data-ttu-id="64023-138">當使用者未指定**PreferredDataLocation**時，信箱將會被放置在集中管理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-138">When **PreferredDataLocation** is not specified on a user, the mailbox will be placed in the central location.</span></span>

- <span data-ttu-id="64023-139">如果**PreferredDataLocation**程式碼不正確 （例如一種 NAN 而不是名稱），信箱將會被放置在集中管理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-139">If the **PreferredDataLocation** code is incorrect (e.g. a type of NAN instead of NAM), the mailbox will be placed in the central location.</span></span>

<span data-ttu-id="64023-p106">**請注意**： 多重地理位置功能和 Skype 的商務線上地域主控會議這兩個使用者物件上使用**PreferredDataLocation**屬性來尋找服務。如果您在地域託管會議的使用者物件上設定**PreferredDataLocation**值，這些使用者的信箱將會自動移到指定的地理位置之後在 Office 365 租用戶上啟用多個地理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-p106">**Note**: multi-geo capabilities and Skype for Business Online regionally hosted meetings both use the **PreferredDataLocation** property on user objects to locate services. If you configure **PreferredDataLocation** values on user objects for regionally hosted meetings, the mailbox for those users will be automatically moved to the specified geo location after multi-geo is enabled on the Office 365 tenant.</span></span>

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a><span data-ttu-id="64023-142">功能會受到限制的多個地理位置 in Exchange Online</span><span class="sxs-lookup"><span data-stu-id="64023-142">Feature limitations for Multi-Geo in Exchange Online</span></span>
1. <span data-ttu-id="64023-p107">使用者信箱、 資源信箱 （會議室及器材信箱） 和共用的信箱支援多個地理位置功能。公用資料夾信箱與 Office 365 群組保持在中央位置。</span><span class="sxs-lookup"><span data-stu-id="64023-p107">Only user mailboxes, resource mailboxes (room and equipment mailboxes), and shared mailboxes support multi-geo features. Public Folder Mailboxes and Office 365 Groups remain in the central location.</span></span>
 
2. <span data-ttu-id="64023-p108">安全性和符合性功能 （例如稽核和 eDiscovery） 所能使用 Exchange 系統管理中心 (EAC) 中不提供多個地理位置的組織。而被必須使用[Office 365 的安全性與規範中心](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)設定安全性和符合性功能。</span><span class="sxs-lookup"><span data-stu-id="64023-p108">Security and compliance features (for example, auditing and eDiscovery) that are available in the Exchange admin center (EAC) aren't available in multi-geo organizations. Instead, you need to use the [Office 365 Security & Compliance Center](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) to configure security and compliance features.</span></span>

3. <span data-ttu-id="64023-p109">Outlook for Mac 使用者可能會遇到存取其線上封存資料夾暫時遺失時將他們的信箱移至新的地理位置。此條件可時發生使用者的主要和封存信箱皆位於不同地理位置，因為跨地理信箱移動可能會在不同時間完成。</span><span class="sxs-lookup"><span data-stu-id="64023-p109">Outlook for Mac users may experience a temporary loss of access to their Online Archive folder while you move their mailbox to a new geo location. This condition occurs when the user's the primary and archive mailboxes are in different geo locations, because cross-Geo mailbox moves may complete at different times.</span></span>

4. <span data-ttu-id="64023-p110">使用者無法跨地理位置 （前身為 Outlook Web App 或 OWA） 在 web 上的 Outlook 中共用*信箱資料夾*。例如，歐盟使用者無法使用網路上的 Outlook 開啟共用的資料夾位於美國信箱中。不過，Outlook Web 使用者可以開啟*其他信箱*中不同 Geos 使用另一個瀏覽器視窗中[開啟另一個人信箱在 Outlook Web App 的另一個瀏覽器視窗中](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)所述。</span><span class="sxs-lookup"><span data-stu-id="64023-p110">Users can't share *mailbox folders* across geo locations in Outlook on the web (formerly known as Outlook Web App or OWA). For example, a user in the European Union can't use Outlook on the web to open a shared folder in a mailbox that's located in the United States. However, Outlook on the Web users can open *other mailboxes* in different Geos by using a separate browser window as described in [Open another person’s mailbox in a separate browser window in Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).</span></span>

    <span data-ttu-id="64023-152">**請注意**： 跨地理信箱資料夾共用支援 windows 在 Outlook 中。</span><span class="sxs-lookup"><span data-stu-id="64023-152">**Note**: Cross-geo mailbox folder sharing is supported in Outlook on Windows.</span></span>

## <a name="administration"></a><span data-ttu-id="64023-153">系統管理</span><span class="sxs-lookup"><span data-stu-id="64023-153">Administration</span></span> 
<span data-ttu-id="64023-p111">遠端 PowerShell 才可檢視及 Office 365 環境中設定多個地理屬性。如需不同用來管理 Office 365，請參閱[管理 Office 365 和 Exchange Online 使用 Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="64023-p111">Remote PowerShell is required to view and configure multi geo properties in your Office 365 environment. For information on various PowerShell modules used to administer Office 365, see [Managing Office 365 and Exchange Online with Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).</span></span>

- <span data-ttu-id="64023-p112">您需要的[Microsoft Azure Active Directory PowerShell 模組](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)v1.1.166.0 或更新版本中以 v1.x 使用者物件，請參閱 ＜ **PreferredDataLocation**屬性。透過 AAD 連線到 AAD 進行同步處理的 user 物件不能有直接修改透過 AAD PowerShell 其**PreferredDataLocation**值。僅限雲端使用者物件可以透過 AAD PowerShell 修改。若要連線至 Azure AD PowerShell，請參閱 ＜ [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="64023-p112">You need the [Microsoft Azure Active Directory PowerShell Module](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 or later in v1.x to see the **PreferredDataLocation** property on user objects. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. To connect to Azure AD PowerShell, see [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).</span></span> 

- <span data-ttu-id="64023-160">若要連線至 Exchange Online PowerShell，請參閱[Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。</span><span class="sxs-lookup"><span data-stu-id="64023-160">To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span> 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a><span data-ttu-id="64023-161">直接連接到使用 Exchange Online PowerShell 特定地理位置</span><span class="sxs-lookup"><span data-stu-id="64023-161">Connect directly to a specific Geo using Exchange Online PowerShell</span></span>
<span data-ttu-id="64023-p113">一般而言，Exchange Online PowerShell 會連線至預設的地理位置。但是，您也可以直接對非預設地理位置連線。因為效能改良功能，建議您直接連線至非預設地理位置僅管理該地理位置中的使用者時。</span><span class="sxs-lookup"><span data-stu-id="64023-p113">Typically, Exchange Online PowerShell will connect to the default geo location. But, you can also connect directly to non-default geo locations. Because of performance improvements, we recommend connecting directly to the non-default geo location when you only manage users in that geo location.</span></span>

<span data-ttu-id="64023-p114">若要連線至特定的地理位置，*來指定 ConnectionUri*參數是不同於一般連線指示。其餘的命令和值都相同。步驟包括：</span><span class="sxs-lookup"><span data-stu-id="64023-p114">To connect to a specific Geo, the *ConnectionUri* parameter is different than the regular connection instructions. The rest of the commands and values are the same. The steps are:</span></span>

1. <span data-ttu-id="64023-168">在您的本機電腦上開啟 Windows PowerShell 並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="64023-168">On your local computer, open Windows PowerShell and run the following command:</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```
   <span data-ttu-id="64023-169">在**Windows PowerShell 認證要求**] 對話方塊中，輸入您的公司或學校帳戶和密碼，並再按一下 [**確定]**。</span><span class="sxs-lookup"><span data-stu-id="64023-169">In the **Windows PowerShell Credential Request** dialog box, type your work or school account and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="64023-p115">取代`<emailaddress>`與**任何**目標地理位置和執行下列命令中的信箱的電子郵件地址。您的權限的信箱與關聯至您在步驟 1 中的認證不是因素;電子郵件地址只會告知 Exchange Online 連線的位置。</span><span class="sxs-lookup"><span data-stu-id="64023-p115">Replace `<emailaddress>` with the email address of **any** mailbox in the target geo location and run the following command. Your permissions on the mailbox and the relationship to your credentials in Step 1 are not a factor; the email address simply tells Exchange Online where to connect.</span></span>
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   <span data-ttu-id="64023-172">例如，如果您想要連線的地理位置中的有效信箱的電子郵件地址 olga@contoso.onmicrosoft.com，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="64023-172">For example, if olga@contoso.onmicrosoft.com is the email address of a valid mailbox in the Geo you want to connect, run the following command:</span></span>

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. <span data-ttu-id="64023-173">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="64023-173">Run the following command:</span></span>
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a><span data-ttu-id="64023-174">Azure AD 連接版本需求</span><span class="sxs-lookup"><span data-stu-id="64023-174">Azure AD Connect version requirements</span></span>
<span data-ttu-id="64023-p116">AAD 連線版本 1.1.524.0 或更新版本進行同步處理的使用者物件上設定**PreferredDataLocation**屬性從內部部署 Active Directory 是唯一支援的方法。透過 AAD 連線到 AAD 進行同步處理的 user 物件不能有直接修改透過 AAD PowerShell 其**PreferredDataLocation**值。僅限雲端使用者物件可以透過 AAD PowerShell 修改。如需詳細指示，請參閱[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="64023-p116">AAD Connect version 1.1.524.0 or later is the only supported method for setting the **PreferredDataLocation** property on user objects that are synchronized from on-premises Active Directory. User objects synchronized via AAD Connect into AAD cannot have their **PreferredDataLocation** value directly modified via AAD PowerShell. Cloud-only user objects can be modified via AAD PowerShell. For detailed instructions, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

### <a name="geo-codes"></a><span data-ttu-id="64023-179">地理位置代碼</span><span class="sxs-lookup"><span data-stu-id="64023-179">Geo Codes</span></span>
<span data-ttu-id="64023-p117">您可以使用三個字母代碼**PreferredDataLocation**屬性中指定的地理位置。下表列出可用的 Geos 程式碼：</span><span class="sxs-lookup"><span data-stu-id="64023-p117">You use three-letter codes to specify the Geo in the **PreferredDataLocation** property. The following table lists the codes for the available Geos:</span></span>

|<span data-ttu-id="64023-182">地理</span><span class="sxs-lookup"><span data-stu-id="64023-182">Geo</span></span> |<span data-ttu-id="64023-183">代碼</span><span class="sxs-lookup"><span data-stu-id="64023-183">Code</span></span> |
|---------|---------|
|<span data-ttu-id="64023-184">亞太地區 /</span><span class="sxs-lookup"><span data-stu-id="64023-184">Asia/Pacific</span></span> |<span data-ttu-id="64023-185">APC</span><span class="sxs-lookup"><span data-stu-id="64023-185">APC</span></span> |
|<span data-ttu-id="64023-186">澳大利亞</span><span class="sxs-lookup"><span data-stu-id="64023-186">Australia</span></span> |<span data-ttu-id="64023-187">AUS</span><span class="sxs-lookup"><span data-stu-id="64023-187">AUS</span></span> |
|<span data-ttu-id="64023-188">加拿大</span><span class="sxs-lookup"><span data-stu-id="64023-188">Canada</span></span> |<span data-ttu-id="64023-189">CAN</span><span class="sxs-lookup"><span data-stu-id="64023-189">CAN</span></span> |
|<span data-ttu-id="64023-190">歐盟</span><span class="sxs-lookup"><span data-stu-id="64023-190">European Union</span></span> |<span data-ttu-id="64023-191">EUR</span><span class="sxs-lookup"><span data-stu-id="64023-191">EUR</span></span> |
|<span data-ttu-id="64023-192">法國</span><span class="sxs-lookup"><span data-stu-id="64023-192">France</span></span> |<span data-ttu-id="64023-193">FRA</span><span class="sxs-lookup"><span data-stu-id="64023-193">FRA</span></span>|
|<span data-ttu-id="64023-194">印度</span><span class="sxs-lookup"><span data-stu-id="64023-194">India</span></span> |<span data-ttu-id="64023-195">尋找</span><span class="sxs-lookup"><span data-stu-id="64023-195">IND</span></span> |
|<span data-ttu-id="64023-196">日本</span><span class="sxs-lookup"><span data-stu-id="64023-196">Japan</span></span> |<span data-ttu-id="64023-197">JPN</span><span class="sxs-lookup"><span data-stu-id="64023-197">JPN</span></span> |
|<span data-ttu-id="64023-198">韓國</span><span class="sxs-lookup"><span data-stu-id="64023-198">Korea</span></span> |<span data-ttu-id="64023-199">韓國</span><span class="sxs-lookup"><span data-stu-id="64023-199">KOR</span></span> |
|<span data-ttu-id="64023-200">英國</span><span class="sxs-lookup"><span data-stu-id="64023-200">United Kingdom</span></span> |<span data-ttu-id="64023-201">GBR</span><span class="sxs-lookup"><span data-stu-id="64023-201">GBR</span></span> |
|<span data-ttu-id="64023-202">美國</span><span class="sxs-lookup"><span data-stu-id="64023-202">United States</span></span> |<span data-ttu-id="64023-203">NAM</span><span class="sxs-lookup"><span data-stu-id="64023-203">NAM</span></span> |

<span data-ttu-id="64023-p118">**請注意**： 在**PreferredDataLocation**和**MailboxRegion**屬性是字串沒有錯誤檢查。如果您輸入了無效的值 (例如 NAN) 信箱將會被放置在預設的地理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-p118">**Note**: The **PreferredDataLocation** and **MailboxRegion** properties are strings with no error checking. If you enter an invalid value (for example, NAN) the mailbox will be placed in the default Geo.</span></span>

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a><span data-ttu-id="64023-206">檢視設定於 Exchange Online 組織中使用 Geos</span><span class="sxs-lookup"><span data-stu-id="64023-206">View the available Geos that are configured in your Exchange Online organization</span></span>
<span data-ttu-id="64023-207">若要查看在 Exchange Online 組織中設定 Geos 的清單，請執行下列命令在 Exchange Online PowerShell：</span><span class="sxs-lookup"><span data-stu-id="64023-207">To see the list of configured Geos in your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

<span data-ttu-id="64023-208">此命令的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="64023-208">The output of the command looks like this:</span></span>

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a><span data-ttu-id="64023-209">Exchange Online 組織的地理位置預設檢視</span><span class="sxs-lookup"><span data-stu-id="64023-209">View the default Geo for your Exchange Online organization</span></span>
<span data-ttu-id="64023-210">若要檢視您的 Exchange Online 組織的預設地理位置，請執行下列命令在 Exchange Online PowerShell：</span><span class="sxs-lookup"><span data-stu-id="64023-210">To view the default geo of your Exchange Online organization, run the following command in Exchange Online PowerShell:</span></span>

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

<span data-ttu-id="64023-211">此命令的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="64023-211">The output of the command looks like this:</span></span>

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a><span data-ttu-id="64023-212">尋找信箱的地理位置</span><span class="sxs-lookup"><span data-stu-id="64023-212">Find the Geo location of a mailbox</span></span>
<span data-ttu-id="64023-213">**Get-mailbox**指令程式在 Exchange Online PowerShell 會顯示下列多重地理位置相關的信箱上的屬性：</span><span class="sxs-lookup"><span data-stu-id="64023-213">The **Get-Mailbox** cmdlet in Exchange Online PowerShell displays the following multi-geo related properties on mailboxes:</span></span>

- <span data-ttu-id="64023-p119">**資料庫**： 資料庫名稱的前 3 字母會對應至地理位置的程式碼會告訴您信箱所在目前。線上封存信箱**ArchiveDatabase**應使用屬性。</span><span class="sxs-lookup"><span data-stu-id="64023-p119">**Database**: The first 3 letters of the database name correspond to the Geo code, which tells you where the mailbox is currently located. For Online Archive Mailboxes the **ArchiveDatabase** property should be used.</span></span>

- <span data-ttu-id="64023-216">**MailboxRegion**： 指定已設定 （已從**PreferredDataLocation**在 Azure AD 的同步處理） 系統的地理位置程式碼。</span><span class="sxs-lookup"><span data-stu-id="64023-216">**MailboxRegion**: Specifies the geo location code that was set by the admin (synchronized from **PreferredDataLocation** in Azure AD).</span></span>

- <span data-ttu-id="64023-217">**MailboxRegionLastUpdateTime**： 指出當 MailboxRegion 最近更新 （自動或手動）。</span><span class="sxs-lookup"><span data-stu-id="64023-217">**MailboxRegionLastUpdateTime**: Indicates when MailboxRegion was last updated (either automatically or manually).</span></span>

<span data-ttu-id="64023-218">如需這些信箱的內容，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="64023-218">To see these properties for a mailbox, use the following syntax:</span></span>

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

<span data-ttu-id="64023-219">例如，若要查看信箱 chris@contoso.onmicrosoft.com 地理資訊，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="64023-219">For example, to see the Geo information for the mailbox chris@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

<span data-ttu-id="64023-220">此命令的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="64023-220">The output of the command looks like this:</span></span>

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> <span data-ttu-id="64023-221">**附註：** 如果在 [資料庫名稱的地理位置程式碼不符合**MailboxRegion**值，信箱將會自動被放入佇列中重新配置和移至**MailboxRegion**值所指定的地理位置 (Exchange Online 尋找不符這些屬性值）。</span><span class="sxs-lookup"><span data-stu-id="64023-221">**Note:** If the geo location code in the database name doesn't match **MailboxRegion** value, the mailbox will be automatically be put into a relocation queue and moved to the geo location specified by the **MailboxRegion** value (Exchange Online looks for a mismatch between these property values).</span></span>

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a><span data-ttu-id="64023-222">將現有的僅限雲端信箱移至特定的地理位置</span><span class="sxs-lookup"><span data-stu-id="64023-222">Move an existing cloud-only mailbox to a specific Geo</span></span>
<span data-ttu-id="64023-p120">僅限雲端使用者是不透過 AAD 連線租用戶兩者。此使用者建立直接在 Azure AD。使用 Windows PowerShell 的 Azure AD 模組中的**Get-msoluser**和**Set-msoluser** cmdlet 可以檢視或指定要儲存僅限雲端使用者信箱的地理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-p120">A cloud-only user is a user not syncrhonized to the tenant via AAD Connect. This user was created directly in Azure AD. Use the **Get-MsolUser** and **Set-MsolUser** cmdlets in the Azure AD Module for Windows PowerShell to view or specify the Geo where a cloud-only user's mailbox will be stored.</span></span>

<span data-ttu-id="64023-226">若要檢視使用者的**PreferredDataLocation**值，請在 Azure AD PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="64023-226">To view the **PreferredDataLocation** value for a user, use this syntax in Azure AD PowerShell:</span></span>

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

<span data-ttu-id="64023-227">例如，若要查看使用者 michelle@contoso.onmicrosoft.com **PreferredDataLocation**值，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="64023-227">For example, to see the **PreferredDataLocation** value for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

<span data-ttu-id="64023-228">此命令的輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="64023-228">The output of the command looks like this:</span></span>

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

<span data-ttu-id="64023-229">若要修改的僅限雲端使用者物件的**PreferredDataLocation**值，請 Azure AD PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="64023-229">To modify the **PreferredDataLocation** value for a cloud-only user object, use the following syntax in Azure AD PowerShell:</span></span>

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

<span data-ttu-id="64023-230">例如，若要將**PreferredDataLocation**值設為使用者 michelle@contoso.onmicrosoft.com 歐盟 (EUR) 地理位置，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="64023-230">For example, to set the **PreferredDataLocation** value to the European Union (EUR) geo for the user michelle@contoso.onmicrosoft.com, run the following command:</span></span>

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

<span data-ttu-id="64023-231">**附註**：</span><span class="sxs-lookup"><span data-stu-id="64023-231">**Notes**:</span></span>

- <span data-ttu-id="64023-p121">為提及之先前您無法使用此程序從內部部署 Active Directory 同步處理的使用者物件。您需要變更**PreferredDataLocation**值使用 AAD 連線。如需詳細資訊，請參閱[Azure [Active Directory 連線同步處理： 設定 Office 365 資源的慣用的資料位置](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)。</span><span class="sxs-lookup"><span data-stu-id="64023-p121">As mentioned previously you cannot use this procedure for synchronized user objects from on-premises Active Directory. You need to change the **PreferredDataLocation** value using AAD Connect. For more information, see [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span> 

- <span data-ttu-id="64023-235">需花費重新放置 mailboxfrom 其目前的地理位置至新的所需的地理位置會視數個因素而定：</span><span class="sxs-lookup"><span data-stu-id="64023-235">How long it takes to relocate a mailboxfrom its current geo to the new desired geo location depends on several factors:</span></span>
 
  - <span data-ttu-id="64023-236">信箱的類型及大小。</span><span class="sxs-lookup"><span data-stu-id="64023-236">The size and type of mailbox.</span></span>
 
  - <span data-ttu-id="64023-237">要移動的信箱數目。</span><span class="sxs-lookup"><span data-stu-id="64023-237">The number of mailboxes being moved.</span></span>
 
  - <span data-ttu-id="64023-238">移動資源的可用性。</span><span class="sxs-lookup"><span data-stu-id="64023-238">The availability of move resources.</span></span>

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a><span data-ttu-id="64023-239">移動停用信箱上訴訟暫止狀態</span><span class="sxs-lookup"><span data-stu-id="64023-239">Move disabled mailboxes that are on Litigation Hold</span></span>
<span data-ttu-id="64023-p122">停用信箱訴訟暫止狀態的 ediscovery （英文） 用途不能移來變更其已停用狀態及其**PreferredDataLocation**值會保留。已停用將信箱移入訴訟資料暫留：</span><span class="sxs-lookup"><span data-stu-id="64023-p122">Disabled mailboxes on Litigation Hold that are preserved for eDiscovery purposes cannot be moved by changing their **PreferredDataLocation** value in their disabled state. To move a disabled mailbox on litigation hold:</span></span>

1. <span data-ttu-id="64023-242">暫時將授權指派給信箱。</span><span class="sxs-lookup"><span data-stu-id="64023-242">Temporarily assign a license to the mailbox.</span></span>

2. <span data-ttu-id="64023-243">變更**PreferredDataLocation**。</span><span class="sxs-lookup"><span data-stu-id="64023-243">Change the **PreferredDataLocation**.</span></span>

3. <span data-ttu-id="64023-244">其授權移除信箱後它已移至所選的地理位置以使其回到停用狀態。</span><span class="sxs-lookup"><span data-stu-id="64023-244">Remove the license from the mailbox after it has been moved to the selected geo location to put it back into the disabled state.</span></span>

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a><span data-ttu-id="64023-245">在特定地理位置中建立新的雲端信箱</span><span class="sxs-lookup"><span data-stu-id="64023-245">Create new cloud mailboxes in a specific Geo</span></span> 
<span data-ttu-id="64023-246">若要建立新的信箱中的特定地理位置，您需要執行這些步驟的任一項：</span><span class="sxs-lookup"><span data-stu-id="64023-246">To create a new mailbox in a specific geo location, you need to do either of these steps:</span></span>

- <span data-ttu-id="64023-p123">舊區段*之前*的信箱已建立在 Exchange Online 中所述，設定**PreferredDataLocation**值。例如，設定**PreferredDataLocation**值是以使用者之前將授權指派。</span><span class="sxs-lookup"><span data-stu-id="64023-p123">Configure the **PreferredDataLocation** value as described in the previous section *before* the mailbox is created in Exchange Online. For example, configure the **PreferredDataLocation** value on a user before assigning a license.</span></span> 

- <span data-ttu-id="64023-249">將授權指派同時設定**PreferredDataLocation**值。</span><span class="sxs-lookup"><span data-stu-id="64023-249">Assign a license at the same time you set the **PreferredDataLocation** value.</span></span>

<span data-ttu-id="64023-250">若要建立新僅限雲端授權的使用者 （不 AAD 連線同步處理） 中特定的地理位置，請 Azure AD PowerShell 中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="64023-250">To create a new cloud-only licensed user (not AAD Connect synchronized) in a specific Geo, use the following syntax in Azure AD PowerShell:</span></span>

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
<span data-ttu-id="64023-251">本範例會為伊莉莎白 Brunner 建立新的使用者帳戶具有下列值：</span><span class="sxs-lookup"><span data-stu-id="64023-251">This example create a new user account for Elizabeth Brunner with the following values:</span></span>

- <span data-ttu-id="64023-252">使用者主體名稱： ebrunner@contoso.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="64023-252">User principal name: ebrunner@contoso.onmicrosoft.com</span></span>

- <span data-ttu-id="64023-253">名字： 伊莉莎白</span><span class="sxs-lookup"><span data-stu-id="64023-253">First name: Elizabeth</span></span>

- <span data-ttu-id="64023-254">姓氏： Brunner</span><span class="sxs-lookup"><span data-stu-id="64023-254">Last name: Brunner</span></span>

- <span data-ttu-id="64023-255">顯示名稱伊莉莎白 Brunner</span><span class="sxs-lookup"><span data-stu-id="64023-255">Display name Elizabeth Brunner</span></span>

- <span data-ttu-id="64023-256">密碼： 隨機產生所示命令的結果 （因為我們未使用*Password*參數）</span><span class="sxs-lookup"><span data-stu-id="64023-256">Password: randomly-generated and shown in the results of the command (because we're not using the *Password* parameter)</span></span>

- <span data-ttu-id="64023-257">授權： contoso:ENTERPRISEPREMIUM (E5)</span><span class="sxs-lookup"><span data-stu-id="64023-257">License: contoso:ENTERPRISEPREMIUM (E5)</span></span>

- <span data-ttu-id="64023-258">位置： 澳洲 （澳洲）</span><span class="sxs-lookup"><span data-stu-id="64023-258">Location: Australia (AUS)</span></span>

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

<span data-ttu-id="64023-259">如需建立新的使用者帳戶和 Azure AD PowerShell 中尋找 LicenseAssignment 值的詳細資訊，請參閱[Office 365 PowerShell 建立使用者帳戶](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)和[檢視授權和 Office 365 powershell 的服務](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)。</span><span class="sxs-lookup"><span data-stu-id="64023-259">For more information about creating new user accounts and finding LicenseAssignment values in Azure AD PowerShell, see [Create user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) and [View licenses and services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).</span></span>

> <span data-ttu-id="64023-p124">**附註：** 如果您使用 Exchange Online PowerShell 啟用信箱並必須直接在所指定的**PreferredDataLocation**地理位置中建立信箱，您需要使用 Exchange Online 指令程式，如**啟用信箱**或**New-mailbox**直接對雲端服務。如果您使用**Enable-remotemailbox**內部部署 Exchange 指令程式，信箱會建立在預設的地理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-p124">**Note:** If you are using Exchange Online PowerShell to enable a mailbox and need the mailbox to be created directly in the Geo that's specified in **PreferredDataLocation**, you need to use an Exchange Online cmdlet such as **Enable-Mailbox** or **New-Mailbox** directly against the cloud service. If you use the **Enable-RemoteMailbox** on-premises Exchange cmdlet, the mailbox will be created in the default Geo.</span></span>

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a><span data-ttu-id="64023-262">設定現有的內建內部部署信箱的特定地理位置</span><span class="sxs-lookup"><span data-stu-id="64023-262">Onboard existing on-premises mailboxes in a specific Geo</span></span>
<span data-ttu-id="64023-263">您可以使用標準的 onboarding 工具與程序將信箱從內部部署 Exchange 組織移轉至 Exchange Online，包括[在 EAC 中的遷移儀表板](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)和[New-migrationbatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch)指令程式在 Exchange OnlinePowerShell。</span><span class="sxs-lookup"><span data-stu-id="64023-263">You can use the standard onboarding tools and processes to migrate a mailbox from an on-premises Exchange organization to Exchange Online, including the [Migration dashboard in the EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331), and the [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) cmdlet in Exchange Online PowerShell.</span></span>

<span data-ttu-id="64023-p125">第一個步驟是驗證的使用者物件存在是 onboarded，並確認正確的**PreferredDataLocation**值已設定在 Azure AD 的每個信箱。Onboarding 工具會來**PreferredDataLocation**值並將信箱遷移直接至指定的地理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-p125">The first step is to verify a user object exists for each mailbox to be onboarded, and verify the correct **PreferredDataLocation** value is configured in Azure AD. The onboarding tools will respect the **PreferredDataLocation** value and will migrate the mailboxes directly to the specified Geo.</span></span>

<span data-ttu-id="64023-266">或者，您可以使用下列步驟以直接在 Exchange Online PowerShell 中使用[New-moverequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest)指令程式的特定地理位置中的內建信箱。</span><span class="sxs-lookup"><span data-stu-id="64023-266">Or, you can use the following steps to onboard mailboxes directly in a specific geo location using the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) cmdlet in Exchange Online PowerShell.</span></span>

1. <span data-ttu-id="64023-p126">確認每個信箱設為 onboarded 和**PreferredDataLocation**設為所需的值在 Azure AD 存在於使用者物件。**PreferredDataLocation**的值會同步處理至相對應的郵件使用者物件的**MailboxRegion**屬性在 Exchange Online。</span><span class="sxs-lookup"><span data-stu-id="64023-p126">Verify the user object exists for each mailbox to be onboarded and that **PreferredDataLocation** is set to the desired value in Azure AD. The value of **PreferredDataLocation** will be synchronized to the **MailboxRegion** attribute of the corresponding mail user object in Exchange Online.</span></span>

2. <span data-ttu-id="64023-269">直接連接到特定的衛星連線指示從使用本主題中前面的地理位置。</span><span class="sxs-lookup"><span data-stu-id="64023-269">Connect directly to the specific satellite Geo using the connection instructions from earlier in this topic.</span></span>

3. <span data-ttu-id="64023-270">在 Exchange Online PowerShell 中儲存內部部署系統管理員認證是用以執行信箱移轉的變數中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="64023-270">In Exchange Online PowerShell, store the on-premises administrator credentials that's used to perform a mailbox migration in a variable by running the following command:</span></span>

    ```
    $RC = Get-Credential
    ```

4. <span data-ttu-id="64023-271">在 Exchange Online PowerShell 中建立新的**New-moverequest**類似下列的範例：</span><span class="sxs-lookup"><span data-stu-id="64023-271">In Exchange Online PowerShell, create a new **New-MoveRequest** similar to the following example:</span></span> 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. <span data-ttu-id="64023-272">重複執行步驟 #4 您需要從內部部署 Exchange 移轉至衛星位置目前連線至每個信箱。</span><span class="sxs-lookup"><span data-stu-id="64023-272">Repeat step #4 for every mailbox you need to migrate from on-premises Exchange to the satellite location you are currently connected to.</span></span>

6. <span data-ttu-id="64023-273">如果您需要額外的信箱移轉至不同的衛星位置，請針對每個特定衛星位置重複步驟 2 到 4。</span><span class="sxs-lookup"><span data-stu-id="64023-273">If you need to migrate additional mailboxes to a different satellite location, repeat steps 2 through 4 for each specific satellite location.</span></span>

### <a name="multi-geo-reporting"></a><span data-ttu-id="64023-274">多個地理位置報告</span><span class="sxs-lookup"><span data-stu-id="64023-274">Multi-Geo Reporting</span></span>
<span data-ttu-id="64023-p127">在 Office 365 系統管理中心中的**多個地理位置流量報告**顯示依地理位置的使用者人數。報表會顯示目前月份的使用者通訊群組並提供過去 6 個月的歷程資料。</span><span class="sxs-lookup"><span data-stu-id="64023-p127">**Multi-Geo Usage Reports** in the Office 365 admin center displays the user count by geo location. The report displays user distribution for the current month and provides historical data for the past 6 months.</span></span>
