---
title: Office 365 中的系統管理存取控制
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: 摘要： Office 365 系統管理存取控制及資料分類的概觀。
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067334"
---
# <a name="administrative-access-controls-in-office-365"></a><span data-ttu-id="1773b-103">Office 365 中的系統管理存取控制</span><span class="sxs-lookup"><span data-stu-id="1773b-103">Administrative Access Controls in Office 365</span></span> 

<span data-ttu-id="1773b-104">Microsoft 已頻繁投資系統和自動化 Office 365 的大部分作業時刻意限制存取 microsoft 的客戶內容的控制項。</span><span class="sxs-lookup"><span data-stu-id="1773b-104">Microsoft has invested heavily in systems and controls that automate most Office 365 operations while intentionally limiting access to customer content by Microsoft.</span></span> <span data-ttu-id="1773b-105">人類，進而管理服務，及軟體的運作該服務。</span><span class="sxs-lookup"><span data-stu-id="1773b-105">Humans govern the service, and software operates the service.</span></span> <span data-ttu-id="1773b-106">這可讓 Microsoft，以管理 Office 365 規模和管理的客戶內容的內部威脅風險。</span><span class="sxs-lookup"><span data-stu-id="1773b-106">This enables Microsoft to manage Office 365 at scale and manage the risks of internal threats to customer content.</span></span>

<span data-ttu-id="1773b-107">根據預設，Microsoft 工程師會有零常設系統管理權限和客戶內容零常設存取 Office 365 中。</span><span class="sxs-lookup"><span data-stu-id="1773b-107">By default, Microsoft engineers have zero standing administrative privileges and zero standing access to customer content in Office 365.</span></span> <span data-ttu-id="1773b-108">Microsoft 工程師可以有限制、 稽核、 及安全的客戶內容存取權的有限的時間。</span><span class="sxs-lookup"><span data-stu-id="1773b-108">A Microsoft engineer can have limited, audited, and secured access to a customer's content for a limited amount of time.</span></span> <span data-ttu-id="1773b-109">只在需要的服務作業時，並核准由 Microsoft 資深管理的成員時，才存取。</span><span class="sxs-lookup"><span data-stu-id="1773b-109">Access is only when necessary for service operations and only when approved by a member of Microsoft senior management.</span></span> <span data-ttu-id="1773b-110">授權的客戶加密箱客戶，客戶可以提供對裝載於 Office 365 其內容的存取權核准。</span><span class="sxs-lookup"><span data-stu-id="1773b-110">For Customer Lockbox licensed customers, the customer provides access approval to their content hosted on Office 365.</span></span>

<span data-ttu-id="1773b-111">Microsoft 提供使用的雲端傳遞多份表單的線上服務：</span><span class="sxs-lookup"><span data-stu-id="1773b-111">Microsoft provides online services using multiple forms of cloud delivery:</span></span>

- <span data-ttu-id="1773b-112">**公用定域機組：** 包含多租用戶版本的 Office 365、 Azure 及裝載於 「 北美地區 」、 南美洲、 歐洲、 亞洲、 澳洲等其他服務。</span><span class="sxs-lookup"><span data-stu-id="1773b-112">**Public Clouds:** Includes multi-tenant versions of Office 365, Azure, and other services hosted in North America, South America, Europe, Asia, Australia, etc.</span></span>
- <span data-ttu-id="1773b-113">**國家雲中：** 包含所有統領和協力廠商運作定域機組外美國 （除了和先前所述），例如 （由 21Vianet 運作的），由中國的 Office 365 和 Office 365 Germany 中 (由 Microsoft 中，但在其中模式下運作德國資料受託人Deutsche Telekom 控制及監視 Microsoft 客戶資料與存取權包含客戶資料的系統）。</span><span class="sxs-lookup"><span data-stu-id="1773b-113">**National Clouds:** Includes all sovereign and third party-operated clouds outside of the United States (except ones noted previously), such as Office 365 in China (operated by 21Vianet), and Office 365 in Germany (operated by Microsoft, but under a model in which a German data trustee, Deutsche Telekom, controls and monitors Microsoft's access to Customer Data and systems that contain Customer Data).</span></span>
- <span data-ttu-id="1773b-114">**政府定域機組：** 包含可用於美國政府版客戶的 Office 365 與 Azure 服務。</span><span class="sxs-lookup"><span data-stu-id="1773b-114">**Government Clouds:** Includes Office 365 and Azure services that are available to United States government customers.</span></span>

<span data-ttu-id="1773b-115">基於本文的詳細資訊，包括 Office 365 服務：</span><span class="sxs-lookup"><span data-stu-id="1773b-115">For purposes of this article, Office 365 services include:</span></span>

- [<span data-ttu-id="1773b-116">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1773b-116">Exchange Online</span></span>](https://docs.microsoft.com/Exchange/exchange-online)
- [<span data-ttu-id="1773b-117">Exchange Online Protection</span><span class="sxs-lookup"><span data-stu-id="1773b-117">Exchange Online Protection</span></span>](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [<span data-ttu-id="1773b-118">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1773b-118">SharePoint Online</span></span>](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [<span data-ttu-id="1773b-119">商務用 OneDrive</span><span class="sxs-lookup"><span data-stu-id="1773b-119">OneDrive for Business</span></span>](https://docs.microsoft.com/OneDrive/onedrive)
- [<span data-ttu-id="1773b-120">商務用 Skype</span><span class="sxs-lookup"><span data-stu-id="1773b-120">Skype for Business</span></span>](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [<span data-ttu-id="1773b-121">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1773b-121">Microsoft Teams</span></span>](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [<span data-ttu-id="1773b-122">Yammer</span><span class="sxs-lookup"><span data-stu-id="1773b-122">Yammer</span></span>](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a><span data-ttu-id="1773b-123">Office 365 的存取控制</span><span class="sxs-lookup"><span data-stu-id="1773b-123">Office 365 Access Controls</span></span>

<span data-ttu-id="1773b-124">以存取控制項來說，Microsoft 將分類為 「 客戶資料或其他類型的資料的 Office 365 資料。</span><span class="sxs-lookup"><span data-stu-id="1773b-124">For access control purposes, Microsoft categorizes Office 365 data as Customer data or other types of data.</span></span>

### <a name="customer-data"></a><span data-ttu-id="1773b-125">客戶資料</span><span class="sxs-lookup"><span data-stu-id="1773b-125">Customer data</span></span>

<span data-ttu-id="1773b-126">客戶資料是由或提供代表客戶使用 Office 365 服務時的所有資料。</span><span class="sxs-lookup"><span data-stu-id="1773b-126">Customer data is all data provided by or on behalf of a customer when using Office 365 services.</span></span> <span data-ttu-id="1773b-127">這是客戶內容直接建立或上傳的 Office 365 使用者使用，包括：</span><span class="sxs-lookup"><span data-stu-id="1773b-127">This is customer content directly created or uploaded by Office 365 users, including:</span></span>

- <span data-ttu-id="1773b-128">電子郵件</span><span class="sxs-lookup"><span data-stu-id="1773b-128">Emails</span></span>
- <span data-ttu-id="1773b-129">SharePoint Online 內容</span><span class="sxs-lookup"><span data-stu-id="1773b-129">SharePoint Online content</span></span>
- <span data-ttu-id="1773b-130">立即訊息</span><span class="sxs-lookup"><span data-stu-id="1773b-130">Instant messages</span></span>
- <span data-ttu-id="1773b-131">行事曆項目</span><span class="sxs-lookup"><span data-stu-id="1773b-131">Calendar items</span></span>
- <span data-ttu-id="1773b-132">文件</span><span class="sxs-lookup"><span data-stu-id="1773b-132">Documents</span></span>
- <span data-ttu-id="1773b-133">Contacts</span><span class="sxs-lookup"><span data-stu-id="1773b-133">Contacts</span></span>
- <span data-ttu-id="1773b-134">使用者識別資訊 (EUII) （這是唯一的使用者，或資料，是連結至個別使用者，但不包含客戶內容）。</span><span class="sxs-lookup"><span data-stu-id="1773b-134">End-user identifiable information (EUII) (data that is unique to a user or that is linkable to an individual user but does not include customer content).</span></span>

### <a name="other-types-of-data"></a><span data-ttu-id="1773b-135">其他類型的資料</span><span class="sxs-lookup"><span data-stu-id="1773b-135">Other types of data</span></span>

<span data-ttu-id="1773b-136">其他的資料類型包括：</span><span class="sxs-lookup"><span data-stu-id="1773b-136">Other types of data include:</span></span>

- <span data-ttu-id="1773b-137">**帳戶資料：** 包含管理資料 (由系統管理員所提供的資訊時他們註冊或購買服務)，以及付款資料 （付款儀器，例如信用卡的詳細資訊的相關資訊）。</span><span class="sxs-lookup"><span data-stu-id="1773b-137">**Account data:** Includes administrative data (information provided by administrators when they sign-up or purchase services), and payment data (information about payment instruments, such as credit card details).</span></span>
- <span data-ttu-id="1773b-138">**家識別資訊：** 包含用來識別租用戶、 使用狀況資料，以及未連結至個別使用者或客戶內容中包含的資料。</span><span class="sxs-lookup"><span data-stu-id="1773b-138">**Organizationally identifiable information:** Includes data used to identify a tenant, usage data, and not linkable to an individual user or included in customer content.</span></span>
- <span data-ttu-id="1773b-139">**系統中繼資料：** 包括含有組態設定、 系統狀態、 Microsoft IP 位址和訂用帳戶及租用戶的技術資訊的服務記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1773b-139">**System metadata:** Includes service logs that contain configuration settings, system status, Microsoft IP addresses, and technical information about subscriptions and tenants.</span></span>

<span data-ttu-id="1773b-140">Microsoft 已經建立存取控制機制，以確保沒有其他有未核准的存取客戶資料或存取控制資料。</span><span class="sxs-lookup"><span data-stu-id="1773b-140">Microsoft has established access control mechanisms to ensure that no one has unapproved access to Customer Data or access control data.</span></span> <span data-ttu-id="1773b-141">存取控制資料管理其他類型的資料或在函數中的環境，包括存取客戶內容或 EUII、 Microsoft 密碼、 安全性憑證，以及其他驗證相關的資料存取。</span><span class="sxs-lookup"><span data-stu-id="1773b-141">Access control data manages access to other types of data or functions within the environment, including access to customer content or EUII, Microsoft passwords, security certificates, and other authentication-related data.</span></span> <span data-ttu-id="1773b-142">存取控制機制也會防止未核准實體、 邏輯、 或遠端存取 Office 365 實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="1773b-142">Access control mechanisms also guard against unapproved physical, logical, or remote access to the Office 365 production environment.</span></span>

<span data-ttu-id="1773b-143">有三種類別的存取控制 Microsoft 用於操作 Office 365:</span><span class="sxs-lookup"><span data-stu-id="1773b-143">There are three categories of access controls used by Microsoft for operating Office 365:</span></span>

- <span data-ttu-id="1773b-144">隔離控制措施</span><span class="sxs-lookup"><span data-stu-id="1773b-144">Isolation Controls</span></span>
- <span data-ttu-id="1773b-145">人員控制措施</span><span class="sxs-lookup"><span data-stu-id="1773b-145">Personnel Controls</span></span>
- <span data-ttu-id="1773b-146">技術控制措施</span><span class="sxs-lookup"><span data-stu-id="1773b-146">Technology Controls</span></span>

<span data-ttu-id="1773b-147">當組合時，這些控制項協助防止，並在 Office 365 中偵測惡意的動作。</span><span class="sxs-lookup"><span data-stu-id="1773b-147">When combined, these controls help prevent and detect malicious actions in Office 365.</span></span> <span data-ttu-id="1773b-148">除了隔離、 人員及使用 Microsoft 技術控制措施，沒有控制項的第四個類別： 所實作的客戶。</span><span class="sxs-lookup"><span data-stu-id="1773b-148">In addition to the isolation, personnel, and technology controls used by Microsoft, there is a fourth category of controls: those implemented by customers.</span></span>

<span data-ttu-id="1773b-149">Office 365 可讓您管理資料的相同的方式受管理的內部部署環境中的資料。</span><span class="sxs-lookup"><span data-stu-id="1773b-149">Office 365 allows you to manage data the same way data is managed in on-premises environments.</span></span> <span data-ttu-id="1773b-150">註冊組織 Office 365 自動的人員會成為全域系統管理員。</span><span class="sxs-lookup"><span data-stu-id="1773b-150">The person who signs up an organization for Office 365 automatically becomes a global administrator.</span></span> <span data-ttu-id="1773b-151">全域系統管理員有權存取管理入口網站和可以中的所有功能：</span><span class="sxs-lookup"><span data-stu-id="1773b-151">The global admin has access to all features in Management Portals and can:</span></span>

- <span data-ttu-id="1773b-152">建立或編輯使用者</span><span class="sxs-lookup"><span data-stu-id="1773b-152">Create or edit users</span></span>
- <span data-ttu-id="1773b-153">指派系統管理員角色給其他人</span><span class="sxs-lookup"><span data-stu-id="1773b-153">Assign admin roles to others</span></span>
- <span data-ttu-id="1773b-154">重設使用者密碼</span><span class="sxs-lookup"><span data-stu-id="1773b-154">Reset user passwords</span></span>
- <span data-ttu-id="1773b-155">管理使用者授權</span><span class="sxs-lookup"><span data-stu-id="1773b-155">Manage user licenses</span></span>
- <span data-ttu-id="1773b-156">管理的網域</span><span class="sxs-lookup"><span data-stu-id="1773b-156">Manage domains</span></span>
- <span data-ttu-id="1773b-157">核准客戶加密箱要求</span><span class="sxs-lookup"><span data-stu-id="1773b-157">Approve Customer Lockbox requests</span></span>

<span data-ttu-id="1773b-158">我們建議每個組織設定至少兩個系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="1773b-158">We recommend that each organization configure at least two admin accounts.</span></span> <span data-ttu-id="1773b-159">對於大型企業組織中，我們建議提供不同功能的特定的系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="1773b-159">For large enterprise organizations, we recommend specialized admin accounts that serve different functions.</span></span>

<span data-ttu-id="1773b-160">如需指派系統管理員角色和權限的資訊，請參閱[指派 Office 365 中的系統管理員角色](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)和[關於 Office 365 系統管理員角色](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D)。</span><span class="sxs-lookup"><span data-stu-id="1773b-160">For information about assigning admin roles and permissions, see [Assigning admin roles in Office 365](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504) and [About Office 365 admin roles](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D).</span></span>

## <a name="related-links"></a><span data-ttu-id="1773b-161">相關連結</span><span class="sxs-lookup"><span data-stu-id="1773b-161">Related Links</span></span>

- [<span data-ttu-id="1773b-162">隔離控制措施</span><span class="sxs-lookup"><span data-stu-id="1773b-162">Isolation Controls</span></span>](office-365-isolation-controls.md)
- [<span data-ttu-id="1773b-163">人員控制措施</span><span class="sxs-lookup"><span data-stu-id="1773b-163">Personnel Controls</span></span>](office-365-personnel-controls.md)
- [<span data-ttu-id="1773b-164">技術控制措施</span><span class="sxs-lookup"><span data-stu-id="1773b-164">Technology Controls</span></span>](office-365-technology-controls.md)
- [<span data-ttu-id="1773b-165">監視及稽核的存取控制</span><span class="sxs-lookup"><span data-stu-id="1773b-165">Monitoring and Auditing Access Controls</span></span>](office-365-monitoring-and-auditing-access-controls.md)
- [<span data-ttu-id="1773b-166">Yammer 企業存取控制</span><span class="sxs-lookup"><span data-stu-id="1773b-166">Yammer Enterprise Access Controls</span></span>](office-365-yammer-enterprise-access-controls.md)