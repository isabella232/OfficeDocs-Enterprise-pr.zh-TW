---
title: 保護 SharePoint Online 網站與檔案
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
description: 摘要： 設定建議保護 SharePoint Online 和 Office 365 中的檔案。
ms.openlocfilehash: 800d81d657164b2a936b95764d57fd092cfa21cc
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="secure-sharepoint-online-sites-and-files"></a><span data-ttu-id="82671-103">保護 SharePoint Online 網站與檔案</span><span class="sxs-lookup"><span data-stu-id="82671-103">Secure SharePoint Online sites and files</span></span>

 <span data-ttu-id="82671-104">**摘要：**設定建議的保護 SharePoint Online 和 Office 365 中的檔案。</span><span class="sxs-lookup"><span data-stu-id="82671-104">**Summary:** Configuration recommendations for protecting files in SharePoint Online and Office 365.</span></span>
  
<span data-ttu-id="82671-p101">本文提供設定 SharePoint Online 小組網站及檔案保護，簡化共同作業與平衡安全性建議。本文定義四個不同的設定，啟動與公用網站最開啟的共用原則與組織內。每個額外的設定向上代表有意義的步驟中保護，但可存取及進行共同作業的資源的能力降低至相關的一組使用者。使用這些建議當做起點並調整以符合組織需求的設定。</span><span class="sxs-lookup"><span data-stu-id="82671-p101">This article provides recommendations for configuring SharePoint Online team sites and file protection that balances security with ease of collaboration. This article defines four different configurations, starting with a public site within your organization with the most open sharing policies. Each additional configuration represents a meaningful step up in protection, but the ability to access and collaborate on resources is reduced to the relevant set of users. Use these recommendations as a starting point and adjust the configurations to meet the needs of your organization.</span></span> 
  
<span data-ttu-id="82671-109">本文的設定符合 Microsoft 針對資料、身分識別和裝置的下列三層保護建議：</span><span class="sxs-lookup"><span data-stu-id="82671-109">The configurations in this article align with Microsoft's recommendations for three tiers of protection for data, identities, and devices:</span></span>
  
- <span data-ttu-id="82671-110">基準保護</span><span class="sxs-lookup"><span data-stu-id="82671-110">Baseline protection</span></span>
    
- <span data-ttu-id="82671-111">敏感性保護</span><span class="sxs-lookup"><span data-stu-id="82671-111">Sensitive protection</span></span>
    
- <span data-ttu-id="82671-112">高度機密保護</span><span class="sxs-lookup"><span data-stu-id="82671-112">Highly confidential protection</span></span>
    
<span data-ttu-id="82671-113">如需這些層級和每道層級的建議功能詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="82671-113">For more information about these tiers and capabilities recommended for each tier, see the following resources.</span></span> 
  
- [<span data-ttu-id="82671-114">Office 365 的身分識別與裝置保護</span><span class="sxs-lookup"><span data-stu-id="82671-114">Identity and Device Protection for Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    
- [<span data-ttu-id="82671-115">Office 365 的檔案保護解決方案</span><span class="sxs-lookup"><span data-stu-id="82671-115">File Protection Solutions in Office 365</span></span>](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    
## <a name="capability-overview"></a><span data-ttu-id="82671-116">功能概觀</span><span class="sxs-lookup"><span data-stu-id="82671-116">Capability overview</span></span>

<span data-ttu-id="82671-p102">建議的 SharePoint Online 小組網站依據各種不同 Office 365 功能而定。 針對高度機密的網站，建議您使用 Azure 資訊保護。 Enterprise Mobility + Security (EMS) 包含這項功能。</span><span class="sxs-lookup"><span data-stu-id="82671-p102">Recommendations for SharePoint Online team sites draw on a variety of Office 365 capabilities. For highly confidential sites, Azure Information Protection is recommended. This is included in Enterprise Mobility + Security (EMS).</span></span> 
  
<span data-ttu-id="82671-120">下圖顯示四個 SharePoint Online 小組網站的建議的設定。</span><span class="sxs-lookup"><span data-stu-id="82671-120">The following illustration shows the recommended configurations for four SharePoint Online team sites.</span></span>
  
![SharePoint 網站的建議設定](images/ad0dcd70-f6f5-465c-8d16-1889481ca07a.png)
  
<span data-ttu-id="82671-122">如圖例所示：</span><span class="sxs-lookup"><span data-stu-id="82671-122">As illustrated:</span></span>
  
- <span data-ttu-id="82671-p103">基準保護包括公用網站與私用網站這兩個 SharePoint Online 小組網站的選項。 公用網站可供組織中的任何人探索及存取。 私用網站則僅供網站成員探索及存取。 這兩個網站的設定都允許群組外部共用。</span><span class="sxs-lookup"><span data-stu-id="82671-p103">Baseline protection includes two options for SharePoint Online team sites — a public site and private site. Public sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the site. Both of these site configurations allow for sharing outside the group.</span></span> 
    
- <span data-ttu-id="82671-127">設有敏感性與高度機密保護的網站為私用網站，其存取權僅限於特定群組的成員。</span><span class="sxs-lookup"><span data-stu-id="82671-127">Sites for sensitive and highly confidential protection are private sites with access limited only to members of specific groups.</span></span>
    
- <span data-ttu-id="82671-p104">Office 365 標籤可提供您分類資料的方法及所需的保護層級。 系統會將每個 SharePoint Online 小組網站設為自動替文件庫中的檔案加上該網站的預設標籤。 此範例的標籤對應到這四種網站設定，分別是「內部公用」、「私用」、「敏感性」與「高度機密」。 使用者可以變更標籤，但這種設定可確保所有檔案都收到預設標籤。</span><span class="sxs-lookup"><span data-stu-id="82671-p104">Office 365 labels provide a way to classify data with a needed protection level. Each of the SharePoint Online team sites are configured to automatically label files in document libraries with a default label for the site. Corresponding to the four site configurations, the labels in this example are Internal Public, Private, Sensitive, and Highly Confidential. Users can change the labels, but this configuration ensures all files receive a default label.</span></span>
    
- <span data-ttu-id="82671-132">系統會針對「敏感性」和「高度機密」的 Office 365 標籤設定資料外洩防護 (DLP) 原則，以在使用者嘗試將這類檔案傳送到組織外部時，對他們發出警告或阻止此動作。</span><span class="sxs-lookup"><span data-stu-id="82671-132">Data loss prevention (DLP) policies are configured for the Sensitive and Highly Confidential Office 365 labels to either warn or prevent users when they attempt to send these types of files outside the organization.</span></span>
    
- <span data-ttu-id="82671-133">如果網站設有高度機密的保護，Azure 資訊保護會進行加密，並授與檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="82671-133">For sites configured with highly confidential protection, Azure Information Protection encrypts and grants permissions for files.</span></span>
    
## <a name="tenant-wide-settings-for-sharepoint-online-and-onedrive-for-business"></a><span data-ttu-id="82671-134">SharePoint Online 和商務用 OneDrive 的租用戶整體設定</span><span class="sxs-lookup"><span data-stu-id="82671-134">Tenant-wide settings for SharePoint Online and OneDrive for Business</span></span>

<span data-ttu-id="82671-p105">SharePoint Online 和商務用 OneDrive 包含的租用戶整體設定會影響所有網站與使用者。 其中某些設定可以於網站層級進行調整，使其更加嚴格 (但不能更寬鬆)。 本節說明會影響安全性與共同作業的租用戶整體設定。</span><span class="sxs-lookup"><span data-stu-id="82671-p105">SharePoint Online and OneDrive for Business include tenant-wide settings that affect all sites and users. Some of these settings can also be adjusted at the site level to be more restrictive (but not less). This section discusses tenant-wide settings that affect security and collaboration.</span></span> 
  
### <a name="sharing"></a><span data-ttu-id="82671-138">共用</span><span class="sxs-lookup"><span data-stu-id="82671-138">Sharing</span></span>

<span data-ttu-id="82671-139">針對這個解決方案，我們建議下列的租用戶整體設定：</span><span class="sxs-lookup"><span data-stu-id="82671-139">For this solution, we recommend the following tenant-wide settings:</span></span>
  
- <span data-ttu-id="82671-140">保留預設共用原則，以允許所有帳戶類型的共用作業，包括匿名共用。</span><span class="sxs-lookup"><span data-stu-id="82671-140">Keep the default sharing policy that allows all sharing with all account types, including anonymous sharing.</span></span>
    
- <span data-ttu-id="82671-141">您可視需要將匿名的連結設為過期。</span><span class="sxs-lookup"><span data-stu-id="82671-141">Set anonymous links to expire, if desired.</span></span>
    
- <span data-ttu-id="82671-p106">將共用的預設連結類型變更為「內部」。 這有助於防止資料不慎洩漏到組織外部。</span><span class="sxs-lookup"><span data-stu-id="82671-p106">Change the default link type for sharing to Internal. This helps prevent accidental data leakage outside your organization.</span></span>
    
<span data-ttu-id="82671-p107">雖然允許外部共用似乎有悖常理，但相較於以電子郵件傳送檔案，此方法可以更充分地掌控檔案共用情況。 SharePoint Online 與 Outlook 一起運作，以提供安全的檔案共同作業。</span><span class="sxs-lookup"><span data-stu-id="82671-p107">While it might seem counterintuitive to allow external sharing, this approach provides more control over file sharing compared to sending files in email. SharePoint Online and Outlook work together to provide secure collaboration on files.</span></span> 
  
- <span data-ttu-id="82671-146">根據預設，Outlook 會共用檔案的連結，而非以電子郵件傳送檔案。</span><span class="sxs-lookup"><span data-stu-id="82671-146">By default, Outlook shares a link to a file instead of sending the file in email.</span></span> 
    
- <span data-ttu-id="82671-147">SharePoint Online 和 OneDrive for Business 輕鬆與所組織內外的參與者共用檔案的連結</span><span class="sxs-lookup"><span data-stu-id="82671-147">SharePoint Online and OneDrive for Business make it easy to share links to files with contributors who are both inside and outside your organization</span></span>
    
<span data-ttu-id="82671-p108">您也可以使用相關控制來協助控管外部共用。 例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="82671-p108">You also have controls to help govern external sharing. For example, you can:</span></span>
  
- <span data-ttu-id="82671-150">停用匿名訪客的連結。</span><span class="sxs-lookup"><span data-stu-id="82671-150">Disable an anonymous guest link.</span></span>
    
- <span data-ttu-id="82671-151">撤銷使用者的網站存取權。</span><span class="sxs-lookup"><span data-stu-id="82671-151">Revoke user access to a site.</span></span>
    
- <span data-ttu-id="82671-152">查看誰具有特定網站或文件的存取權。</span><span class="sxs-lookup"><span data-stu-id="82671-152">See who has access to a specific site or document.</span></span>
    
- <span data-ttu-id="82671-153">將匿名共用連結設為過期 (租用戶設定)。</span><span class="sxs-lookup"><span data-stu-id="82671-153">Set anonymous sharing links to expire (tenant setting).</span></span>
    
- <span data-ttu-id="82671-154">限制可在組織外部共用的人員 (租用戶設定)。</span><span class="sxs-lookup"><span data-stu-id="82671-154">Limit who can share outside your organization (tenant setting).</span></span>
    
### <a name="use-external-sharing-together-with-data-loss-prevention-dlp"></a><span data-ttu-id="82671-155">搭配使用外部共用與資料外洩防護 (DLP)</span><span class="sxs-lookup"><span data-stu-id="82671-155">Use external sharing together with data loss prevention (DLP)</span></span>

<span data-ttu-id="82671-p109">如果您不允許外部共用，請使用商務使用者需要找到替代工具和方法。Microsoft 建議您將合併與 DLP 原則，以保護機密和高度機密檔案的外部共用。</span><span class="sxs-lookup"><span data-stu-id="82671-p109">If you don't allow external sharing, users with a business need will find alternate tools and methods. Microsoft recommends you combine external sharing with DLP policies to protect sensitive and highly confidential files.</span></span>
  
### <a name="device-access-settings"></a><span data-ttu-id="82671-158">裝置存取設定</span><span class="sxs-lookup"><span data-stu-id="82671-158">Device access settings</span></span>

<span data-ttu-id="82671-p110">SharePoint Online 和 OneDrive for Business 的裝置存取設定可讓您判斷是否限制為僅使用瀏覽器存取 （無法下載檔案） 或如果封鎖存取。這些設定是目前正在第一個版本及套用租用戶全。即將推出的是能夠在網站層級設定裝置存取原則。此解決方案，建議您不使用適用於整個租用戶的裝置存取設定。</span><span class="sxs-lookup"><span data-stu-id="82671-p110">Device access settings for SharePoint Online and OneDrive for Business let you determine whether access is limited to browser only (files can't be downloaded) or if access is blocked. These settings are currently in First Release and apply tenant-wide. Coming soon is the ability to configure device access policies at the site level. For this solution, we recommend not using device access settings that apply tenant-wide.</span></span>
  
<span data-ttu-id="82671-163">若要使用初次發行的裝置存取設定：[在 Office 365 中設定標準或初次發行選項](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47)。</span><span class="sxs-lookup"><span data-stu-id="82671-163">To use device access settings while these are in first release: [Set up the Standard or First Release Options in Office 365](https://support.office.com/article/Set-up-the-Standard-or-First-Release-options-in-Office-365-3B3ADFA4-1777-4FF0-B606-FB8732101F47).</span></span>
  
### <a name="onedrive-for-business"></a><span data-ttu-id="82671-164">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="82671-164">OneDrive for Business</span></span>

<span data-ttu-id="82671-p111">請瀏覽這些設定，以決定是否要變更商務用 OneDrive 的網站預設設定。 目前，會複製 SharePoint Online 系統管理中心的共用和裝置存取設定，並套用到這兩個環境。</span><span class="sxs-lookup"><span data-stu-id="82671-p111">Visit these settings to decide if you want to change the default settings for OneDrive for Business sites. Currently, the sharing and device access settings are duplicated from the SharePoint Online admin center and apply to both environments.</span></span>
  
## <a name="sharepoint-team-site-configuration"></a><span data-ttu-id="82671-167">SharePoint 小組網站設定</span><span class="sxs-lookup"><span data-stu-id="82671-167">SharePoint team site configuration</span></span>

<span data-ttu-id="82671-p112">下表摘要說明本文稍早所述之每個小組網站的設定。 您可以使用這些設定作為建議的起點，並依據組織需求調整網站類型與設定。 並非每個組織都需要所有類型的網站。 只有少數的組織需要高度機密的保護。</span><span class="sxs-lookup"><span data-stu-id="82671-p112">The following table summarizes the configuration for each of the team sites described earlier in this article. Use these configurations as starting point recommendations and adjust the site types and configurations to meet the needs of your organization. Not every organization needs every type of site. Only a small number of organizations require highly confidential protection.</span></span>
  
||||||
|:-----|:-----|:-----|:-----|:-----|
||<span data-ttu-id="82671-172">**基準保護 #1**</span><span class="sxs-lookup"><span data-stu-id="82671-172">**Baseline protection #1**</span></span> <br/> |<span data-ttu-id="82671-173">**基準保護 #2**</span><span class="sxs-lookup"><span data-stu-id="82671-173">**Baseline protection #2**</span></span> <br/> |<span data-ttu-id="82671-174">**敏感性保護**</span><span class="sxs-lookup"><span data-stu-id="82671-174">**Sensitive protection**</span></span> <br/> |<span data-ttu-id="82671-175">**高度機密**</span><span class="sxs-lookup"><span data-stu-id="82671-175">**Highly confidential**</span></span> <br/> |
|<span data-ttu-id="82671-176">說明</span><span class="sxs-lookup"><span data-stu-id="82671-176">Description</span></span>  <br/> |<span data-ttu-id="82671-177">開啟組織內的探索及共同作業。</span><span class="sxs-lookup"><span data-stu-id="82671-177">Open discovery and collaboration within the organization.</span></span>  <br/> |<span data-ttu-id="82671-178">私用網站和群組，其可在群組外部共用。</span><span class="sxs-lookup"><span data-stu-id="82671-178">Private site and group with sharing allowed outside the group.</span></span>  <br/> |<span data-ttu-id="82671-p113">隔離的網站，其存取層級會依據特定群組的成員資格而定義。 只允許網站的成員共用。 當使用者嘗試將檔案傳送到組織外部時，DLP 會對其發出警告。</span><span class="sxs-lookup"><span data-stu-id="82671-p113">Isolated site, in which levels of access are defined by membership in specific groups. Sharing is only allowed to members of the site. DLP warns users when attempting to send files outside the organization.</span></span>  <br/> |<span data-ttu-id="82671-p114">使用 Azure 資訊保護的隔離網站 + 檔案加密與權限。 DLP 可防止使用者將檔案傳送到組織外部。</span><span class="sxs-lookup"><span data-stu-id="82671-p114">Isolated site + file encryption and permissions with Azure Information Protection. DLP prevents users from sending files outside the organization.</span></span>  <br/> |
|<span data-ttu-id="82671-184">私用或公用的小組網站</span><span class="sxs-lookup"><span data-stu-id="82671-184">Private or public team site</span></span>  <br/> |<span data-ttu-id="82671-185">公用</span><span class="sxs-lookup"><span data-stu-id="82671-185">Public</span></span>  <br/> |<span data-ttu-id="82671-186">Private</span><span class="sxs-lookup"><span data-stu-id="82671-186">Private</span></span>  <br/> |<span data-ttu-id="82671-187">Private</span><span class="sxs-lookup"><span data-stu-id="82671-187">Private</span></span>  <br/> |<span data-ttu-id="82671-188">Private</span><span class="sxs-lookup"><span data-stu-id="82671-188">Private</span></span>  <br/> |
|<span data-ttu-id="82671-189">誰可以存取？</span><span class="sxs-lookup"><span data-stu-id="82671-189">Who has access?</span></span>  <br/> |<span data-ttu-id="82671-190">組織中所有人，包括 B2B 使用者和訪客使用者。</span><span class="sxs-lookup"><span data-stu-id="82671-190">Everybody in the organization, including B2B users and guest users.</span></span>  <br/> |<span data-ttu-id="82671-p115">僅限網站的成員。 其他人可以要求存取權。</span><span class="sxs-lookup"><span data-stu-id="82671-p115">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="82671-p116">僅限網站的成員。 其他人可以要求存取權。</span><span class="sxs-lookup"><span data-stu-id="82671-p116">Members of the site only. Others can request access.</span></span>  <br/> |<span data-ttu-id="82671-p117">僅限成員。 其他人無法要求存取權。</span><span class="sxs-lookup"><span data-stu-id="82671-p117">Members only. Others cannot request access.</span></span>  <br/> |
|<span data-ttu-id="82671-197">網站層級的共用控制</span><span class="sxs-lookup"><span data-stu-id="82671-197">Site-level sharing controls</span></span>  <br/> |<span data-ttu-id="82671-p118">允許與任何人共用。 預設設定。</span><span class="sxs-lookup"><span data-stu-id="82671-p118">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="82671-p119">允許與任何人共用。 預設設定。</span><span class="sxs-lookup"><span data-stu-id="82671-p119">Sharing allowed with anybody. Default settings.</span></span>  <br/> |<span data-ttu-id="82671-202">成員無法共用網站的存取權。</span><span class="sxs-lookup"><span data-stu-id="82671-202">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="82671-203">非成員可以要求存取網站，但這些要求需要網站系統管理員處理。</span><span class="sxs-lookup"><span data-stu-id="82671-203">Non-members can request access to the site, but these requests need to be addressed by a site administrator.</span></span>  <br/> |<span data-ttu-id="82671-204">成員無法共用網站的存取權。</span><span class="sxs-lookup"><span data-stu-id="82671-204">Members cannot share access to the site.</span></span>  <br/> <span data-ttu-id="82671-205">非成員無法要求存取網站或內容。</span><span class="sxs-lookup"><span data-stu-id="82671-205">Non-members cannot request access to the site or contents.</span></span>  <br/> |
|<span data-ttu-id="82671-206">網站層級的裝置存取控制</span><span class="sxs-lookup"><span data-stu-id="82671-206">Site-level device access controls</span></span>  <br/> |<span data-ttu-id="82671-207">無額外控制。</span><span class="sxs-lookup"><span data-stu-id="82671-207">No additional controls.</span></span>  <br/> |<span data-ttu-id="82671-208">無額外控制。</span><span class="sxs-lookup"><span data-stu-id="82671-208">No additional controls.</span></span>  <br/> |<span data-ttu-id="82671-p120">網站層級的控制功能即將推出，其可防止使用者下載檔案到不相容或非加入網域的裝置。 如此一來，所有其他裝置僅可進行瀏覽器存取。</span><span class="sxs-lookup"><span data-stu-id="82671-p120">Site-level controls are coming soon, which prevents users from downloading files to non-compliant or non-domain joined devices. This allows browser-only access from all other devices.</span></span>  <br/> |<span data-ttu-id="82671-211">網站層級的控制功能即將推出，其會封鎖檔案下載到不相容或非加入網域的裝置。</span><span class="sxs-lookup"><span data-stu-id="82671-211">Site-level controls are coming soon, which blocks downloading of files to non-compliant or non-domain joined devices.</span></span>  <br/> |
|<span data-ttu-id="82671-212">Office 365 標籤</span><span class="sxs-lookup"><span data-stu-id="82671-212">Office 365 labels</span></span>  <br/> |<span data-ttu-id="82671-213">內部公用</span><span class="sxs-lookup"><span data-stu-id="82671-213">Internal Public</span></span>  <br/> |<span data-ttu-id="82671-214">Private</span><span class="sxs-lookup"><span data-stu-id="82671-214">Private</span></span>  <br/> |<span data-ttu-id="82671-215">敏感性</span><span class="sxs-lookup"><span data-stu-id="82671-215">Sensitive</span></span>  <br/> |<span data-ttu-id="82671-216">高度機密</span><span class="sxs-lookup"><span data-stu-id="82671-216">Highly Confidential</span></span>  <br/> |
|<span data-ttu-id="82671-217">DLP 原則</span><span class="sxs-lookup"><span data-stu-id="82671-217">DLP policies</span></span>  <br/> |||<span data-ttu-id="82671-218">當使用者將標記為「敏感性」的檔案傳送到組織外部時，會對其發出警告。</span><span class="sxs-lookup"><span data-stu-id="82671-218">Warn users when sending files that are labeled as Sensitive outside the organization.</span></span>  <br/> <span data-ttu-id="82671-219">若要封鎖敏感性資料類型的外部共用，例如信用卡號碼或其他個人資料，您可以為這些資料類型 (包括您設定的自訂資料類型) 設定額外的 DLP 原則。</span><span class="sxs-lookup"><span data-stu-id="82671-219">To block external sharing of sensitive data types, such as credit card numbers or other personal data, you can configure additional DLP policies for these data types (including custom data types you configure).</span></span>  <br/> |<span data-ttu-id="82671-p121">封鎖使用者，使其無法將標示為高度機密的檔案傳送到組織外部。 允許使用者提供理由來覆寫這項預設，包括共用檔案的對象。</span><span class="sxs-lookup"><span data-stu-id="82671-p121">Block users from sending files that are labeled as highly confidential outside organization. Allow users to override this by providing justification, including who they are sharing the file with.</span></span>  <br/> |
|<span data-ttu-id="82671-222">Azure 資訊保護</span><span class="sxs-lookup"><span data-stu-id="82671-222">Azure Information Protection</span></span>  <br/> ||||<span data-ttu-id="82671-p122">使用 Azure 資訊保護自動加密，並授與權限的檔案。萬一他們洩露與檔案一起出差此保護。</span><span class="sxs-lookup"><span data-stu-id="82671-p122">Use Azure Information Protection to automatically encrypt and grant permissions to files. This protection travels with the files in case they are leaked.</span></span>  <br/> <span data-ttu-id="82671-p123">Office 365 無法讀取使用 Azure 資訊保護加密的檔案。此外，DLP 原則可以只使用中繼資料 （包括標籤），但不是 （例如檔案內的信用卡號碼） 這些檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="82671-p123">Office 365 cannot read files encrypted with Azure Information Protection. Additionally, DLP policies can only work with the metadata (including labels) but not the contents of these files (such as credit card numbers within files).</span></span>  <br/> |
   
<span data-ttu-id="82671-p124">如需部署這個解決方案中的 SharePoint Online 小組網站的四種不同類型的步驟，請參閱[部署 SharePoint Online 網站的三層的保護](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md)。如需建立開發/測試環境，請參閱[Secure SharePoint Online 網站的開發人員/測試環境中](secure-sharepoint-online-sites-in-a-dev-test-environment.md)的步驟。</span><span class="sxs-lookup"><span data-stu-id="82671-p124">For the steps to deploy the four different types of SharePoint Online team sites in this solution, see [Deploy SharePoint Online sites for three tiers of protection](deploy-sharepoint-online-sites-for-three-tiers-of-protection.md). For the steps to create a dev/test environment, see [Secure SharePoint Online sites in a dev/test environment](secure-sharepoint-online-sites-in-a-dev-test-environment.md).</span></span> 
  
## <a name="office-365-classification-and-labels"></a><span data-ttu-id="82671-229">Office 365 分類和標籤</span><span class="sxs-lookup"><span data-stu-id="82671-229">Office 365 classification and labels</span></span>

<span data-ttu-id="82671-p125">使用 Office 365 標籤建議與機密資料的環境。後設定並發佈 Office 365 標籤：</span><span class="sxs-lookup"><span data-stu-id="82671-p125">Using Office 365 labels is recommended for environments with sensitive data. After you configure and publish Office 365 labels:</span></span>
  
- <span data-ttu-id="82671-232">您可以將預設標籤套用至 SharePoint Online 小組網站、 文件庫使所有文件的文件庫中取得的預設標籤。</span><span class="sxs-lookup"><span data-stu-id="82671-232">You can apply a default label to a document library in a SharePoint Online team site, so that all documents in that library get the default label.</span></span> 
    
- <span data-ttu-id="82671-233">您可以套用標籤內容自動是否符合特定條件。</span><span class="sxs-lookup"><span data-stu-id="82671-233">You can apply labels to content automatically if it matches specific conditions.</span></span>
    
- <span data-ttu-id="82671-234">您可以套用 Office 365 標籤為基礎的 DLP 原則。</span><span class="sxs-lookup"><span data-stu-id="82671-234">You can apply DLP policies that are based on Office 365 labels.</span></span>
    
- <span data-ttu-id="82671-p126">在組織中的人員可以套用標籤手動在 web 上的 Outlook 中的內容 Outlook 2010 及更新版本、 OneDrive for Business、 SharePoint Online 和 Office 365 的群組。使用者經常知道最佳的內容類型他們正在處理，讓他們可以用它來分類及已套用適當的 DLP 原則。</span><span class="sxs-lookup"><span data-stu-id="82671-p126">People in your organization can apply a label manually to content in Outlook on the web, Outlook 2010 and later, OneDrive for Business, SharePoint Online, and Office 365 groups. Users often know best what type of content they're working with, so they can classify it and have the appropriate DLP policy applied.</span></span>
    
![SharePoint 網站的建議設定](images/7fed0126-ab4a-4480-922c-681970642339.png)
  
<span data-ttu-id="82671-238">如圖例所示，此解決方案包括建立下列標籤：</span><span class="sxs-lookup"><span data-stu-id="82671-238">As illustrated, this solution includes creating the following labels:</span></span>
  
- <span data-ttu-id="82671-239">高度機密</span><span class="sxs-lookup"><span data-stu-id="82671-239">Highly Confidential</span></span>
    
- <span data-ttu-id="82671-240">敏感性</span><span class="sxs-lookup"><span data-stu-id="82671-240">Sensitive</span></span>
    
- <span data-ttu-id="82671-241">Private</span><span class="sxs-lookup"><span data-stu-id="82671-241">Private</span></span>
    
- <span data-ttu-id="82671-242">內部公用</span><span class="sxs-lookup"><span data-stu-id="82671-242">Internal Public</span></span>
    
<span data-ttu-id="82671-p127">這些標籤會對應至在圖例中建議的網站和本文稍早的圖表。此解決方案建議設定 DLP 原則，以協助防止檔案標示為機密和高度機密外的洩。</span><span class="sxs-lookup"><span data-stu-id="82671-p127">These labels are mapped to the recommended sites in the illustrations and charts earlier in this article. This solution recommends configuring DLP policies to help prevent the leakage of files labeled as Sensitive and Highly Confidential.</span></span>
  
<span data-ttu-id="82671-245">如需在此解決方案中設定 Office 365 標籤和 DLP 原則的步驟，請參閱[使用 Office 365 標籤與 DLP 來保護 SharePoint Online 檔案](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)。</span><span class="sxs-lookup"><span data-stu-id="82671-245">For the steps to configure Office 365 labels and DLP policies in this solution, see [Protect SharePoint Online files with Office 365 labels and DLP](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md).</span></span>
  
## <a name="azure-information-protection"></a><span data-ttu-id="82671-246">Azure 資訊保護</span><span class="sxs-lookup"><span data-stu-id="82671-246">Azure Information Protection</span></span>

<span data-ttu-id="82671-p128">您可以使用 Azure 資訊保護，來套用與檔案隨行的標籤和保護。 建議您為此解決方案使用限域的 Azure 資訊保護原則以及高度機密標籤的子標籤，來加密需要以最高安全性等級保護的檔案，和為其授予權限。</span><span class="sxs-lookup"><span data-stu-id="82671-p128">Use Azure Information Protection to apply labels and protections that follow the files wherever they go. For this solution, we recommend you use a scoped Azure Information Protection policy and a sub-label of the Highly Confidential label to encrypt and grant permissions to files that need to be protected with the highest level of security.</span></span> 
  
<span data-ttu-id="82671-p129">請留意，若將 Azure 資訊保護套用至儲存於 Office 365 中的檔案，服務就無法處理這些檔案的內容。 共同撰寫、eDiscovery、搜尋、Delve 和其他共同作業功能無法運作。 此外，DLP 原則只可用於中繼資料 (包括 Office 365 標籤)，但不可用於這些檔案的內容 (例如檔案中的信用卡號碼)。</span><span class="sxs-lookup"><span data-stu-id="82671-p129">Be aware that when Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. DLP policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
  
![Azure 資訊保護設定於 Azure 中，且標籤顯示在用戶端工具列中](images/1266a7a0-5078-49ab-bbf1-b0cf41451f62.png)
  
<span data-ttu-id="82671-253">如圖例所示：</span><span class="sxs-lookup"><span data-stu-id="82671-253">As illustrated:</span></span>
  
- <span data-ttu-id="82671-p130">您在 Microsoft Azure 入口網站中設定 Azure 資訊保護原則和標籤。建議設定子範圍的 Azure 資訊保護原則的標籤。</span><span class="sxs-lookup"><span data-stu-id="82671-p130">You configure Azure Information Protection policies and labels in the Microsoft Azure portal. Configuring a sub-label of a scoped Azure Information Protection policy is recommended.</span></span>
    
- <span data-ttu-id="82671-256">Azure 的資訊保護會向上顯示標籤為 Office 應用程式中的**資訊保護**長條。</span><span class="sxs-lookup"><span data-stu-id="82671-256">Azure Information Protection labels show up as an **Information protection** bar in Office applications.</span></span>
    
### <a name="adding-permissions-for-external-users"></a><span data-ttu-id="82671-257">新增外部使用者的權限</span><span class="sxs-lookup"><span data-stu-id="82671-257">Adding permissions for external users</span></span>

<span data-ttu-id="82671-p131">有兩種方式可授與外部使用者存取權與 Azure 資訊保護受保護的檔案。在這兩個這些情況下，外部使用者必須具備 Azure AD 帳戶。如果外部使用者不會使用 Azure AD 組織中的成員，他們可以使用此註冊頁面為個別取得 Azure AD 帳戶： [https://aka.ms/aip-signup](https://aka.ms/aip-signup)。</span><span class="sxs-lookup"><span data-stu-id="82671-p131">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>
  
- <span data-ttu-id="82671-261">將外部使用者新增至可用來設定標籤保護 Azure AD 群組</span><span class="sxs-lookup"><span data-stu-id="82671-261">Add external users to an Azure AD group that is used to configure protection for a label</span></span>
    
     <span data-ttu-id="82671-p132">必須先將帳戶新增為 B2B 使用者您的目錄中。可能需要幾個小時的[群組成員資格的 Azure Rights Management 快取](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management)。使用此方法之後，權限會授與所有受保護的標籤 （偶數之前將使用者新增至 Azure AD 群組受保護的檔案） 與現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="82671-p132">You'll need to first add the account as a B2B user in your directory. It can take a couple of hours for [group membership caching by Azure Rights Management](https://docs.microsoft.com/information-protection/plan-design/prepare#group-membership-caching-by-azure-rights-management). With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>
    
- <span data-ttu-id="82671-265">外部使用者直接新增至標籤保護</span><span class="sxs-lookup"><span data-stu-id="82671-265">Add external users directly to the label protection</span></span>
    
     <span data-ttu-id="82671-p133">您可以新增所有使用者的組織 (例如 Fabrikam.com)、 Azure AD 的群組 （如 finance 組織內的群組） 或個別使用者。例如，您可以新增以及外部小組來保護標籤。使用此方法之後，權限會授與僅外部的實體新增至 [保護之後標籤以受保護的檔案。</span><span class="sxs-lookup"><span data-stu-id="82671-p133">You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>
    
### <a name="deploying-and-using-azure-information-protection"></a><span data-ttu-id="82671-269">部署並使用 Azure 資訊保護</span><span class="sxs-lookup"><span data-stu-id="82671-269">Deploying and using Azure Information Protection</span></span>

<span data-ttu-id="82671-270">如需在此解決方案中設定 Azure 資訊保護的步驟，請參閱[使用 Azure 資訊保護來保護 SharePoint Online 檔案](protect-sharepoint-online-files-with-azure-information-protection.md)。</span><span class="sxs-lookup"><span data-stu-id="82671-270">For the steps to configure Azure Information Protection in this solution, see [Protect SharePoint Online files with Azure Information Protection](protect-sharepoint-online-files-with-azure-information-protection.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="82671-271">請參閱</span><span class="sxs-lookup"><span data-stu-id="82671-271">See Also</span></span>

[<span data-ttu-id="82671-272">適用於政治活動、非營利組織和其他彈性組織的 Microsoft 安全性指南</span><span class="sxs-lookup"><span data-stu-id="82671-272">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="82671-273">安全性解決方案</span><span class="sxs-lookup"><span data-stu-id="82671-273">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="82671-274">雲端採用和混合式解決方案</span><span class="sxs-lookup"><span data-stu-id="82671-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="82671-275">在開發/測試環境中保護 SharePoint Online 網站</span><span class="sxs-lookup"><span data-stu-id="82671-275">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)



