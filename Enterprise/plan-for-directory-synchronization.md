---
title: Office 365 的目錄同步處理的計劃
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: 說明 Office 365、 Active Directory 清理作業與 Azure [Active Directory 連線工具的目錄同步處理。
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "22540086"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a><span data-ttu-id="3aa17-103">Office 365 的目錄同步處理的計劃</span><span class="sxs-lookup"><span data-stu-id="3aa17-103">Plan for directory synchronization for Office 365</span></span>
<span data-ttu-id="3aa17-p101">根據業務需求與技術需求、 目錄同步處理已移至 Office 365 的企業客戶的最常見的佈建選擇。目錄同步處理可讓內部部署 Active Directory 中進行管理的身分識別和所有更新該 identity 會都同步至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p101">Depending on business need and technical requirements, directory synchronization is the most common provisioning choice for enterprise customers who are moving to Office 365. Directory synchronization allows identities to be managed in the on-premises Active Directory and all updates to that identity are synchronized to Office 365 .</span></span>
  
<span data-ttu-id="3aa17-p102">有幾個規劃實作的目錄同步處理，包括目錄準備和需求及功能的 Azure Active Directory 時請謹記下列事項。目錄準備涵蓋太少。它們包括屬性更新、 稽核、 及規劃放置網域控制站。規劃需求和功能包括決定所需規劃 multiforest/directory 案例、 產能規劃及雙向同步處理的權限。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p102">There are a couple of things to keep in mind when you plan an implementation of directory synchronization, including directory preparation, and the requirements and functionality of the Azure Active Directory. Directory preparation covers quite a few areas. They include attribute updates, auditing, and planning domain controller placement. Planning requirements and functionality includes determining the permissions that are required, planning for multiforest/directory scenarios, capacity planning, and two-way synchronization.</span></span>
  
## <a name="office-365-identity-models"></a><span data-ttu-id="3aa17-110">Office 365 身分識別模型</span><span class="sxs-lookup"><span data-stu-id="3aa17-110">Office 365 identity models</span></span>
<span data-ttu-id="3aa17-111">Office 365 使用兩種主要的驗證及身分識別模型： 雲端驗證和同盟的驗證。</span><span class="sxs-lookup"><span data-stu-id="3aa17-111">Office 365 uses two main authentication and identity models: cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="3aa17-112">雲端驗證</span><span class="sxs-lookup"><span data-stu-id="3aa17-112">Cloud authentication</span></span>
<span data-ttu-id="3aa17-113">[雲端身分識別](about-office-365-identity.md)-建立及管理 Office 365 系統管理中心中的使用者，您也可以使用 Windows PowerShell 或 Azure Active Directory，來管理您的使用者。</span><span class="sxs-lookup"><span data-stu-id="3aa17-113">[Cloud identity](about-office-365-identity.md) - create and manage users in the Office 365 admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
  
<span data-ttu-id="3aa17-p103">[密碼雜湊同步處理順暢單一登入搭配](about-office-365-identity.md)-啟用在 Azure AD 驗證內部部署目錄物件的最簡單方式。使用密碼雜湊同步處理 (PHS)，與 Office 365 同步處理內部部署 Active Directory 使用者帳戶物件及管理您的使用者在內部。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p103">[Password hash sync with seamless single sign-on](about-office-365-identity.md) - The simplest way to enable authentication for on-premises directory objects in Azure AD. With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Office 365 and manage your users on-premises.</span></span> 
  
<span data-ttu-id="3aa17-116">[順暢單一登入與通過驗證](about-office-365-identity.md)-提供的 Azure AD 驗證服務來驗證使用者直接與使用一或多個內部部署伺服器上執行的軟體代理程式簡單密碼驗證您內部部署 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="3aa17-116">[Pass-through authentication with seamless single sign-on](about-office-365-identity.md) - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
  
### <a name="federated-authentication"></a><span data-ttu-id="3aa17-117">同盟的驗證</span><span class="sxs-lookup"><span data-stu-id="3aa17-117">Federated authentication</span></span>
<span data-ttu-id="3aa17-118">[使用 Active Directory Federation Services AD FS 同盟識別](about-office-365-identity.md)-主要針對具有較複雜的驗證需求的大型企業組織內部部署與 Office 365 同步處理目錄物件和使用者帳戶受管理的內部。</span><span class="sxs-lookup"><span data-stu-id="3aa17-118">[Federated identity with Active Directory Federation Services AD FS](about-office-365-identity.md) - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Office 365 and users accounts are managed on-premises.</span></span> 
  
<span data-ttu-id="3aa17-119">[協力廠商驗證及身分識別提供者](about-office-365-identity.md)物件可能會同步至 Office 365 與雲端資源存取內部部署目錄是主要受管理的協力廠商身分識別提供者 (IdP)。</span><span class="sxs-lookup"><span data-stu-id="3aa17-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Office 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
  
## <a name="active-directory-cleanup"></a><span data-ttu-id="3aa17-120">Active Directory 清除</span><span class="sxs-lookup"><span data-stu-id="3aa17-120">Active Directory Cleanup</span></span>
<span data-ttu-id="3aa17-121">為了協助確保能夠順暢地轉換到 Office 365 使用同步處理，我們強烈建議您在您開始使用 Office 365 目錄同步處理部署之前準備 Active Directory 樹系。</span><span class="sxs-lookup"><span data-stu-id="3aa17-121">To help ensure a seamless transition to Office 365 by using synchronization, we highly recommend that you prepare your Active Directory forest before you begin your Office 365 directory synchronization deployment.</span></span>
  
<span data-ttu-id="3aa17-p104">當您[設定 Office 365 中目錄同步作業](set-up-directory-synchronization.md)，其中一個步驟是[下載和執行 IdFix 工具](install-and-run-idfix.md)。您可以使用 IdFix 工具來協助[目錄清理](prepare-directory-attributes-for-synch-with-idfix.md)。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p104">When you [set up directory synchronization in Office 365](set-up-directory-synchronization.md), one of the steps is to [download and run the IdFix tool](install-and-run-idfix.md). You can use the IdFix tool to help with the [directory cleanup](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  
<span data-ttu-id="3aa17-124">目錄清理應著重下列工作：</span><span class="sxs-lookup"><span data-stu-id="3aa17-124">Your directory cleanup should focus on the following tasks:</span></span>

- <span data-ttu-id="3aa17-125">移除重複的**proxyAddress**和**userPrincipalName**屬性。</span><span class="sxs-lookup"><span data-stu-id="3aa17-125">Remove duplicate **proxyAddress** and **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="3aa17-126">使用有效的 **userPrincipalName** 屬性更新空白及無效的 **userPrincipalName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="3aa17-126">Update blank and invalid **userPrincipalName** attributes with valid **userPrincipalName** attributes.</span></span>
- <span data-ttu-id="3aa17-p105">移除**givenName**、 姓氏 ( **sn** )、 **sAMAccountName**、 **displayName**、**電子郵件**、 **proxyAddresses**、 **mailNickname**及**userPrincipalName**中的無效和問題字元屬性。如需準備屬性的詳細資訊，請參閱[清單之已同步處理的 Azure Active Directory 同步作業工具的屬性](https://go.microsoft.com/fwlink/p/?LinkId=396719)。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p105">Remove invalid and questionable characters in the **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**, and **userPrincipalName** attributes. For details about preparing attributes, see [List of attributes that are synced by the Azure Active Directory Sync Tool](https://go.microsoft.com/fwlink/p/?LinkId=396719).</span></span>
    
    > [!NOTE]
    > <span data-ttu-id="3aa17-129">這些是 Azure AD 連線同步相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="3aa17-129">These are the same attributes that Azure AD Connect syncs.</span></span> 
  
## <a name="multiforest-deployment-considerations"></a><span data-ttu-id="3aa17-130">多樹系部署考量</span><span class="sxs-lookup"><span data-stu-id="3aa17-130">Multiforest Deployment Considerations</span></span>
<span data-ttu-id="3aa17-131">針對多個樹系與 SSO 選項、 使用[自訂安裝的 Azure AD 連線](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="3aa17-131">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>
  
<span data-ttu-id="3aa17-132">如果您的組織有多個樹系的驗證 （登入樹系），強烈建議下列：</span><span class="sxs-lookup"><span data-stu-id="3aa17-132">If your organization has multiple forests for authentication (logon forests), we highly recommend the following:</span></span>
  
- <span data-ttu-id="3aa17-p106">**評估您的樹系中合併。** 一般會有多個維護多個樹系所需的額外負荷。除非您的組織有指示需要不同的樹系的安全性條件約束，請考慮簡化您的內部部署環境。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p106">**Evaluate consolidating your forests.** In general, there's more overhead required to maintain multiple forests. Unless your organization has security constraints that dictate the need for separate forests, consider simplifying your on-premises environment.</span></span>
- <span data-ttu-id="3aa17-p107">**使用主要登入樹系中只有。** 請考慮部署 Office 365 在首度發行主要登入樹系中只有 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p107">**Use only in your primary logon forest.** Consider deploying Office 365 only in your primary logon forest for your initial rollout of Office 365.</span></span> 
    
<span data-ttu-id="3aa17-138">如果您不能將合併多樹系的 Active Directory 部署或使用其他目錄服務管理身分識別，您可以同步處理這些 Microsoft 或協力廠商的協助。</span><span class="sxs-lookup"><span data-stu-id="3aa17-138">If you can't consolidate your multiforest Active Directory deployment or are using other directory services to manage identities, you may be able to synchronize these with the help of Microsoft or a partner.</span></span>
  
<span data-ttu-id="3aa17-139">如需詳細資訊，請參閱[使用單一登入案例的多樹系目錄同步處理](https://go.microsoft.com/fwlink/p/?LinkId=525321)。</span><span class="sxs-lookup"><span data-stu-id="3aa17-139">For more information, see [Multi-forest Directory Sync with Single Sign-On Scenario](https://go.microsoft.com/fwlink/p/?LinkId=525321).</span></span>
  
## <a name="directory-integration-tools"></a><span data-ttu-id="3aa17-140">目錄整合工具</span><span class="sxs-lookup"><span data-stu-id="3aa17-140">Directory integration tools</span></span>
<span data-ttu-id="3aa17-p108">目錄同步處理 Office 365 目錄基礎結構從內部部署 Active Directory 環境是同步處理的目錄物件 （使用者、 群組及連絡人）。請參閱[目錄整合工具](https://go.microsoft.com/fwlink/p/?LinkID=510956)可用的工具和功能的清單。若要使用建議的工具為[Azure [Active Directory 連線](https://go.microsoft.com/fwlink/?LinkId=525323)。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p108">Directory synchronization is the synchronization of directory objects (users, groups, and contacts) from your on-premises Active Directory environment to the Office 365 directory infrastructure. See [directory integration tools](https://go.microsoft.com/fwlink/p/?LinkID=510956) for a list of the available tools and their functionality. The recommended tool to use is [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).</span></span>
  
<span data-ttu-id="3aa17-p109">當使用者帳戶與 Office 365 目錄第一次同步處理時，它們被標示為非啟動。他們無法傳送或接收電子郵件，以及它們不取用訂閱授權。當您準備好要指派給特定使用者的 Office 365 訂閱時，您必須選取並啟動其指派的有效授權。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p109">When user accounts are synchronized with the Office 365 directory for the first time, they are marked as non-activated. They cannot send or receive email, and they don't consume subscription licenses. When you're ready to assign Office 365 subscriptions to specific users, you must select and activate them by assigning a valid license.</span></span>
  
<span data-ttu-id="3aa17-147">目錄同步處理所需的下列特性和功能：</span><span class="sxs-lookup"><span data-stu-id="3aa17-147">Directory synchronization is required for the following features and functionality:</span></span>
  
- <span data-ttu-id="3aa17-148">SSO</span><span class="sxs-lookup"><span data-stu-id="3aa17-148">SSO</span></span>
    
- <span data-ttu-id="3aa17-149">Lync 共存</span><span class="sxs-lookup"><span data-stu-id="3aa17-149">Lync coexistence</span></span>
    
- <span data-ttu-id="3aa17-150">Exchange 混合部署包括：</span><span class="sxs-lookup"><span data-stu-id="3aa17-150">Exchange hybrid deployment, including:</span></span>
    
  - <span data-ttu-id="3aa17-151">內部部署 Exchange 環境與 Office 365 之間的完全共用全域通訊清單 (GAL)。</span><span class="sxs-lookup"><span data-stu-id="3aa17-151">Fully shared global address list (GAL) between your on-premises Exchange environment and Office 365.</span></span>
  - <span data-ttu-id="3aa17-152">從不同的郵件系統同步處理 GAL 資訊。</span><span class="sxs-lookup"><span data-stu-id="3aa17-152">Synchronizing GAL information from different mail systems.</span></span>
  - <span data-ttu-id="3aa17-p110">新增使用者並移除使用者從 Office 365 服務方案的能力。這需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="3aa17-p110">The ability to add users to and remove users from Office 365 service offerings. This requires the following:</span></span>
  - <span data-ttu-id="3aa17-p111">雙向同步處理必須設定目錄同步處理在安裝期間。根據預設，目錄同步作業工具寫入目錄資訊僅雲端。當您設定雙向同步處理時，使有限的物件屬性是從雲端，複製並覆寫這些回本機 Active Directory 啟用回寫功能。回寫也稱為 「 Exchange 混合式模式。</span><span class="sxs-lookup"><span data-stu-id="3aa17-p111">Two-way synchronization must be configured during directory synchronization setup. By default, directory synchronization tools write directory information only to the cloud. When you configure two-way synchronization, you enable write-back functionality so that a limited number of object attributes are copied from the cloud, and then written them back to your local Active Directory. Write-back is also referred to as Exchange hybrid mode.</span></span> 
  - <span data-ttu-id="3aa17-159">內部部署 Exchange 混合部署</span><span class="sxs-lookup"><span data-stu-id="3aa17-159">An on-premises Exchange hybrid deployment</span></span>
  - <span data-ttu-id="3aa17-160">能夠一些使用者信箱移至 Office 365 時保留其他使用者信箱的內部。</span><span class="sxs-lookup"><span data-stu-id="3aa17-160">The ability to move some user mailboxes to Office 365 while keeping other user mailboxes on-premises.</span></span>
  - <span data-ttu-id="3aa17-161">安全的寄件者和封鎖的寄件者內部已複寫至 Office 365。</span><span class="sxs-lookup"><span data-stu-id="3aa17-161">Safe senders and blocked senders on-premises are replicated to Office 365.</span></span>
  - <span data-ttu-id="3aa17-162">基本委派及代理傳送電子郵件功能。</span><span class="sxs-lookup"><span data-stu-id="3aa17-162">Basic delegation and send-on-behalf-of email functionality.</span></span>
  - <span data-ttu-id="3aa17-163">您已有內部整合式的智慧卡或多重要素驗證解決方案。</span><span class="sxs-lookup"><span data-stu-id="3aa17-163">You have an integrated on-premises smart card or multi-factor authentication solution.</span></span>
    
- <span data-ttu-id="3aa17-164">同步處理相片、 縮圖、 會議室及安全性群組</span><span class="sxs-lookup"><span data-stu-id="3aa17-164">Synchronization of photos, thumbnails, conference rooms, and security groups</span></span>