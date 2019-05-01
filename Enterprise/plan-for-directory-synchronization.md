---
title: < Plan for Office 365 的目錄同步處理
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 說明 Office 365、 Active Directory 清理] 中，與 Azure Active Directory Connect 工具的目錄同步處理。
ms.openlocfilehash: 1a7c63f699c51c829aaab5b70cb6a1a203bca3be
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492079"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="e8ac2-103">< Plan for Office 365 的目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="e8ac2-103">Plan for directory synchronization for Office 365</span></span>

<span data-ttu-id="e8ac2-104">根據業務需求與技術需求，目錄同步處理會是最常見的佈建選擇移至 Office 365 的企業客戶的。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-104">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365.</span></span> <span data-ttu-id="e8ac2-105">目錄同步處理可讓內部部署 Active Directory 中受管理的身分識別和所有更新該身分識別同步都處理至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-105">Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365.</span></span>
  
<span data-ttu-id="e8ac2-106">有幾個事項請記住，當您規劃實作的目錄同步處理，包括目錄準備的需求和 Azure Active Directory 的功能。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-106">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory.</span></span> <span data-ttu-id="e8ac2-107">目錄準備涵蓋很多領域。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-107">Directory preparation covers quite a few areas.</span></span> <span data-ttu-id="e8ac2-108">它們包括屬性更新、 稽核和規劃網域控制站。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-108">They include attribute updates, auditing, and planning domain controller placement.</span></span> <span data-ttu-id="e8ac2-109">規劃需求和功能，包括決定所需，規劃多 forest/directory 案例中、 容量規劃，及雙向同步處理權限。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-109">Planning requirements and functionality includes determining the permissions that are required, planning for multi-forest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="e8ac2-110">Office 365 身分識別模型</span><span class="sxs-lookup"><span data-stu-id="e8ac2-110">Office 365 identity models</span></span>

<span data-ttu-id="e8ac2-111">Office 365 會使用兩個主要的驗證與身分識別模型： 雲端驗證和同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="e8ac2-112">雲端驗證</span><span class="sxs-lookup"><span data-stu-id="e8ac2-112">Cloud authentication</span></span>

<span data-ttu-id="e8ac2-113">[雲端身分識別](about-office-365-identity.md)-建立及管理[Microsoft 365 系統管理中心](https://admin.microsoft.com)中的使用者，您也可以使用 Windows PowerShell 或 Azure Active Directory，來管理您的使用者。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span>
  
<span data-ttu-id="e8ac2-114">[密碼雜湊同步處理與無縫單一登入](about-office-365-identity.md)-啟用內部部署目錄物件的 [驗證]，在 Azure AD 中的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-114">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD.</span></span> <span data-ttu-id="e8ac2-115">使用密碼雜湊同步處理 (PHS)，您可以與 Office 365 同步處理您的內部部署 Active Directory 使用者帳戶物件及管理您內部使用者。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-115">With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span>
  
<span data-ttu-id="e8ac2-116">[無縫單一登入與通過驗證](about-office-365-identity.md)-提供使用一或多個內部部署伺服器上執行的軟體代理程式來驗證直接與使用者的 Azure AD 驗證服務的簡單密碼驗證您內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span>
  
### <a name="federated-authentication"></a><span data-ttu-id="e8ac2-117">同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="e8ac2-117">Federated authentication</span></span>

<span data-ttu-id="e8ac2-118">[與 Active Directory Federation Services AD FS 的同盟身分識別](about-office-365-identity.md)-主要使用於具有較複雜的驗證需求，大型企業組織內部部署與 Office 365 同步處理目錄物件和使用者帳戶受管理的內部。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span>
  
<span data-ttu-id="e8ac2-119">[協力廠商驗證與身分識別提供者](about-office-365-identity.md)的內部部署目錄物件可能會同步至 Office 365 部署及雲端資源存取主要是由協力廠商身分識別提供者 (Isp) 所管理。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span>
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="e8ac2-120">Active Directory 清理</span><span class="sxs-lookup"><span data-stu-id="e8ac2-120">Active Directory Cleanup</span></span>

<span data-ttu-id="e8ac2-121">為了協助確保使用同步處理順暢地轉換到 Office 365，我們強烈建議您準備您的 Active Directory 樹系，再開始 Office 365 目錄同步處理部署。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="e8ac2-122">當您[設定 Office 365 中的目錄同步處理](set-up-directory-synchronization.md)，其中一個步驟是[下載並執行 IdFix 工具](install-and-run-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-122">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md).</span></span> <span data-ttu-id="e8ac2-123">您可以使用 IdFix 工具以協助進行[目錄清理](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-123">You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="e8ac2-124">目錄清理應該要著重於下列工作：</span><span class="sxs-lookup"><span data-stu-id="e8ac2-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="e8ac2-125">移除重複的**proxyAddress**和**userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="e8ac2-126">使用有效的**userPrincipalName**屬性更新空白及無效的**userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="e8ac2-127">**GivenName**、 姓氏 ( **sn** )、 **sAMAccountName**、 **displayName**、**郵件**、 **proxyAddresses**、 **mailNickname**和**userPrincipalName**中移除無效，且有疑問的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-127">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes.</span></span> <span data-ttu-id="e8ac2-128">如需準備屬性的詳細資訊，請參閱 <<c0>清單的屬性，會同步處理的 Azure Active Directory 同步作業工具。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-128">For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e8ac2-129">這些都是相同 Azure AD Connect 同步資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multi-forest-deployment-considerations"></a><span data-ttu-id="e8ac2-130">多樹系部署考量</span><span class="sxs-lookup"><span data-stu-id="e8ac2-130">Multi-forest Deployment Considerations</span></span>

<span data-ttu-id="e8ac2-131">針對多個樹系與 SSO 選項，使用[自訂安裝的 Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="e8ac2-132">如果您的組織有多個樹系進行驗證 （登入樹系），我們強烈建議如下：</span><span class="sxs-lookup"><span data-stu-id="e8ac2-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="e8ac2-133">**評估合併在樹系。**</span><span class="sxs-lookup"><span data-stu-id="e8ac2-133">**Evaluate consolidating your forests.**</span></span> <span data-ttu-id="e8ac2-134">一般而言，沒有更多維護多個樹系所需的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-134">In general, there's more overhead required to maintain multiple forests.</span></span> <span data-ttu-id="e8ac2-135">除非您的組織有安全性限制，指示不同樹系的需求，否則請簡化您的內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-135">Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="e8ac2-136">**只有在您的主要登入樹系中使用。**</span><span class="sxs-lookup"><span data-stu-id="e8ac2-136">**Use only in your primary logon forest.**</span></span> <span data-ttu-id="e8ac2-137">請考慮部署只能在您的 Office 365 在首度發行的主要登入樹系中的 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-137">Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 

<span data-ttu-id="e8ac2-138">如果您無法合併您的多樹系 Active Directory 部署，或使用其他目錄服務管理身分識別，您可能無法同步處理這些 Microsoft 或合作夥伴的協助。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-138">If you can't consolidate your multi-forest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="e8ac2-139">如需詳細資訊，請參閱 <<c0>多樹系目錄同步處理與單一登入案例。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="e8ac2-140">目錄整合工具</span><span class="sxs-lookup"><span data-stu-id="e8ac2-140">Directory integration tools</span></span>

<span data-ttu-id="e8ac2-141">目錄同步處理的 Office 365 目錄基礎結構從內部部署 Active Directory 環境是同步處理的目錄物件 （使用者、 群組和連絡人）。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-141">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure.</span></span> <span data-ttu-id="e8ac2-142">請參閱如需可用的工具和功能的清單的[目錄整合工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-142">See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality.</span></span> <span data-ttu-id="e8ac2-143">若要使用建議的工具是[Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-143">The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="e8ac2-144">當使用者帳戶會與 Office 365 目錄同步處理，第一次時，他們會標示為非啟動。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-144">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated.</span></span> <span data-ttu-id="e8ac2-145">無法傳送或接收電子郵件，以及它們不會耗用訂閱授權。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-145">They cannot send or receive email, and they don't consume subscription licenses.</span></span> <span data-ttu-id="e8ac2-146">當您準備好要指派給特定使用者的 Office 365 訂閱時，您必須選取並啟動它們藉由指定有效的授權。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-146">When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="e8ac2-147">目錄同步作業所需的下列特性與功能：</span><span class="sxs-lookup"><span data-stu-id="e8ac2-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="e8ac2-148">SSO</span><span class="sxs-lookup"><span data-stu-id="e8ac2-148">SSO</span></span>
- <span data-ttu-id="e8ac2-149">Skype 共存</span><span class="sxs-lookup"><span data-stu-id="e8ac2-149">Skype coexistence</span></span>
- <span data-ttu-id="e8ac2-150">Exchange 混合式部署，包括：</span><span class="sxs-lookup"><span data-stu-id="e8ac2-150">Exchange hybrid deployment, including:</span></span>
  - <span data-ttu-id="e8ac2-151">您在內部部署 Exchange 環境與 Office 365 之間的完全共用全域通訊清單 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="e8ac2-152">從不同的郵件系統的同步處理 GAL 資訊。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="e8ac2-153">將使用者加入及移除使用者從 Office 365 服務方案的能力。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-153">The ability to add users to and remove users from Office 365 service offerings.</span></span> <span data-ttu-id="e8ac2-154">這需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="e8ac2-154">This requires the following:</span></span>
  - <span data-ttu-id="e8ac2-155">目錄同步處理安裝期間，必須設定雙向同步處理。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-155">Two-way synchronization must be configured during directory synchronization setup.</span></span> <span data-ttu-id="e8ac2-156">根據預設，目錄同步處理工具的目錄資訊寫入僅雲端。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-156">By default, directory synchronization tools write directory information only to the cloud.</span></span> <span data-ttu-id="e8ac2-157">當您設定雙向同步處理時，以便有限的數量的物件的屬性會複製從雲端，並覆寫這些回您的本機 Active Directory 啟用回寫功能。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-157">When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory.</span></span> <span data-ttu-id="e8ac2-158">回寫也稱為 Exchange 混合式模式。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-158">Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="e8ac2-159">內部部署 Exchange 混合式部署</span><span class="sxs-lookup"><span data-stu-id="e8ac2-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="e8ac2-160">在保留其他使用者信箱在內部將部分使用者信箱移至 Office 365 功能。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="e8ac2-161">安全的寄件者和封鎖寄件者的內部會複寫至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="e8ac2-162">基本委派及代理傳送的電子郵件功能。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="e8ac2-163">您有內部整合式的智慧卡或多重要素驗證方案。</span><span class="sxs-lookup"><span data-stu-id="e8ac2-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
- <span data-ttu-id="e8ac2-164">相片、 縮圖、 會議室及安全性群組同步處理</span><span class="sxs-lookup"><span data-stu-id="e8ac2-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>