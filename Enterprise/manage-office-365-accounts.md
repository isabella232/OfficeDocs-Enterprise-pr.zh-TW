---
title: 管理 Microsoft 365 帳戶的工具
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: '瞭解用來管理 Microsoft 365 使用者的工具，以及您可以使用哪些工具，取決於您管理使用者身分識別的方式。 '
ms.openlocfilehash: 6decaa941f5997cd2ee1617f428f93985428dde4
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774498"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a><span data-ttu-id="1e8f3-103">管理 Microsoft 365 帳戶的工具</span><span class="sxs-lookup"><span data-stu-id="1e8f3-103">Tools to manage Microsoft 365 accounts</span></span>

<span data-ttu-id="1e8f3-104">您可以根據您的設定，以數種不同的方式管理 Microsoft 365 使用者。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-104">You can manage Microsoft 365 users in several different ways, depending on your configuration.</span></span> <span data-ttu-id="1e8f3-105">您可以在[Microsoft 365 系統管理中心](https://admin.microsoft.com)、Windows PowerShell、您的內部部署目錄或 Azure Active directory 系統管理員入口網站中管理使用者。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-105">You can manage users in the [Microsoft 365 admin center](https://admin.microsoft.com), Windows PowerShell, your on-premises directory, or in Azure Active Directory admin portal.</span></span> <span data-ttu-id="1e8f3-106">一旦您購買 Microsoft 365，系統管理中心和 Windows PowerShell 便可用於管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-106">As soon as you purchase Microsoft 365, the admin center and Windows PowerShell can be used to manage accounts.</span></span> <span data-ttu-id="1e8f3-107">管理雲端身分識別組織中的每一位人員，都有個別的使用者識別碼和密碼用於 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-107">When managing cloud identities every person in your organization has a separate user ID and password for Microsoft 365.</span></span> <span data-ttu-id="1e8f3-108">如果您想要與您的內部部署基礎結構整合，並將使用者帳戶與 Microsoft 365 同步，您可以使用 Azure Active Directory Connect 來提供身分識別的同步處理，並選擇性地提供密碼同步處理或完整單一登入功能。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-108">If you want to integrate with your on-premises infrastructure and have user accounts synchronized with Microsoft 365, you can use Azure Active Directory Connect to provide synchronization of identities and optionally provide password synchronization, or full single sign-on functionality.</span></span>
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a><span data-ttu-id="1e8f3-109">規劃管理使用者帳戶的位置和方式</span><span class="sxs-lookup"><span data-stu-id="1e8f3-109">Plan for where and how you will manage your user accounts</span></span>

<span data-ttu-id="1e8f3-110">您可以管理使用者帳戶的位置和方式，取決於您要用於 Microsoft 365 的身分識別模型。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-110">Where and how you can manage your user accounts depends on the identity model you want to use for your Microsoft 365.</span></span> <span data-ttu-id="1e8f3-111">這兩個整體模型為雲端驗證及同盟驗證。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-111">The two overall models are cloud authentication and federated authentication.</span></span>
  
### <a name="cloud-authentication"></a><span data-ttu-id="1e8f3-112">雲端驗證</span><span class="sxs-lookup"><span data-stu-id="1e8f3-112">Cloud authentication</span></span>

- <span data-ttu-id="1e8f3-113">雲端驗證-建立及管理系統管理中心的使用者，您也可以使用 Windows PowerShell 或 Azure Active Directory 來管理使用者。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-113">Cloud authentication - create and manage users in the admin center, you can also use Windows PowerShell, or Azure Active Directory to manage your users.</span></span> 
    
- <span data-ttu-id="1e8f3-114">具有無縫單一登入的密碼雜湊同步處理-針對 Azure AD 中內部部署目錄物件啟用驗證的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-114">Password hash sync with seamless single sign-on - The simplest way to enable authentication for on-premises directory objects in Azure AD.</span></span> <span data-ttu-id="1e8f3-115">透過密碼雜湊同步處理（PHS），您可以將內部部署 Active Directory 使用者帳戶物件與 Microsoft 365 同步處理，並管理內部部署的使用者。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-115">With password hash sync (PHS), you synchronize your on-premises Active Directory user account objects with Microsoft 365 and manage your users on-premises.</span></span> 
    
- <span data-ttu-id="1e8f3-116">透過無縫單一登入的傳遞驗證-利用一或多個內部部署伺服器上執行的軟體代理程式，為 Azure AD 驗證服務提供簡單的密碼驗證，以直接使用內部部署 Active Directory 驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-116">Pass-through authentication with seamless single sign-on - Provides a simple password validation for Azure AD authentication services using a software agent running on one or more on-premises servers to validate the users directly with your on-premises Active Directory.</span></span> 
    
### <a name="federated-authentication"></a><span data-ttu-id="1e8f3-117">同盟驗證</span><span class="sxs-lookup"><span data-stu-id="1e8f3-117">Federated authentication</span></span>

- <span data-ttu-id="1e8f3-118">同盟驗證選項-主要針對具有更複雜驗證需求的大型企業組織，內部部署目錄物件會與 Microsoft 365 同步處理，而且使用者帳戶是在內部部署管理。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-118">Federated authentication options - Primarily for large enterprise organizations with more complex authentication requirements, on-premises directory objects are synchronized with Microsoft 365 and users accounts are managed on-premises.</span></span> 
    
- <span data-ttu-id="1e8f3-119">[協力廠商驗證和身分識別提供者](about-office-365-identity.md)-內部部署目錄物件可同步處理至 Microsoft 365，而雲端資源存取主要是由協力廠商身分識別提供者（IdP）來管理。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-119">[Third-party authentication and identity providers](about-office-365-identity.md) - On-premises directory objects may be synchronized to Microsoft 365 and cloud resource access is primarily managed by a third-party identity provider (IdP).</span></span> 
    
## <a name="managing-accounts"></a><span data-ttu-id="1e8f3-120">管理帳戶</span><span class="sxs-lookup"><span data-stu-id="1e8f3-120">Managing Accounts</span></span>

<span data-ttu-id="1e8f3-121">決定組織建立及管理帳戶的方式時，請考慮下列各項：</span><span class="sxs-lookup"><span data-stu-id="1e8f3-121">When deciding which way your organization will create and manage accounts, consider the following:</span></span>
  
- <span data-ttu-id="1e8f3-122">您必須在內部部署環境中的伺服器上安裝目錄同步作業軟體，以連接 Microsoft 365 和內部部署目錄之間的身分識別。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-122">The directory synchronization software needs to be installed on servers within your on-premises environment to connect the identities between Microsoft 365 and your on-premises directory.</span></span>
    
- <span data-ttu-id="1e8f3-123">任何目錄同步處理選項（包括 SSO 選項）都需要您的內部部署目錄屬性符合標準。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-123">Any directory synchronization option, including SSO options, requires your on-premises directory attributes meet standards.</span></span> <span data-ttu-id="1e8f3-124">您的目錄中所使用的屬性和清理（如果有的話）的詳細資訊，說明如何在[目錄同步處理至 Microsoft 365 時提供使用者](prepare-for-directory-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-124">The specifics of what attributes are used in your directory and what cleanup (if any) is needed are described in [Prepare to provision users through directory synchronization to Microsoft 365](prepare-for-directory-synchronization.md).</span></span> <span data-ttu-id="1e8f3-125">請參閱[下載並執行 Microsoft 365 IdFix 工具](install-and-run-idfix.md)，以取得如何使用 IdFix 自動目錄清理的說明。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-125">See [Download and run the Microsoft 365 IdFix tool](install-and-run-idfix.md) for instruction on how to use IdFix to automate directory cleanup.</span></span> 
    
- <span data-ttu-id="1e8f3-126">規劃如何建立 Microsoft 365 帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-126">Plan how you are going to create Microsoft 365 accounts.</span></span>
    
    <span data-ttu-id="1e8f3-127">下表列出不同的帳戶管理工具。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-127">The following table lists the different account management tools.</span></span>
    
|<span data-ttu-id="1e8f3-128">**選項**</span><span class="sxs-lookup"><span data-stu-id="1e8f3-128">**Option**</span></span>|<span data-ttu-id="1e8f3-129">**附註**</span><span class="sxs-lookup"><span data-stu-id="1e8f3-129">**Notes**</span></span>|
|:-----|:-----|
|<span data-ttu-id="1e8f3-130">系統管理中心</span><span class="sxs-lookup"><span data-stu-id="1e8f3-130">Admin center</span></span>  <br/> |[<span data-ttu-id="1e8f3-131">個別或大量新增使用者</span><span class="sxs-lookup"><span data-stu-id="1e8f3-131">Add users individually or in bulk</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  <span data-ttu-id="1e8f3-132">提供簡單的 web 介面來新增及變更使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-132">Provides a simple web interface to add and change user accounts.</span></span>  <br/>  <span data-ttu-id="1e8f3-133">如果啟用目錄同步處理（可以設定位置和授權指派），則無法用來變更使用者。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-133">Can't be used to change users if directory synchronization is enabled (location and license assignment can be set).</span></span>  <br/>  <span data-ttu-id="1e8f3-134">無法與 SSO 選項搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-134">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="1e8f3-135">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e8f3-135">Windows PowerShell</span></span>  <br/> |[<span data-ttu-id="1e8f3-136">使用 Windows PowerShell 管理 Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1e8f3-136">Manage Microsoft 365 with Windows PowerShell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  <span data-ttu-id="1e8f3-137">可讓您使用 Windows PowerShell 腳本，在大量使用者中新增使用者。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-137">Allows you to add users in bulk users by using a Windows PowerShell script.</span></span>  <br/>  <span data-ttu-id="1e8f3-138">可用於將位置和授權指派給帳戶，不論帳戶是如何建立的。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-138">Can be used to assign location and licenses to accounts, regardless of how the accounts are created.</span></span>  <br/> |
|<span data-ttu-id="1e8f3-139">大量匯入</span><span class="sxs-lookup"><span data-stu-id="1e8f3-139">Bulk import</span></span>  <br/> |[<span data-ttu-id="1e8f3-140">同時新增多個使用者</span><span class="sxs-lookup"><span data-stu-id="1e8f3-140">Add several users at the same time</span></span>](add-several-users-at-the-same-time.md) <br/>  <span data-ttu-id="1e8f3-141">可讓您匯入 CSV 檔案，將使用者群組新增至 Microsoft 365。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-141">Allows you to import a CSV file to add a group of users to Microsoft 365.</span></span>  <br/>  <span data-ttu-id="1e8f3-142">無法與 SSO 選項搭配使用。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-142">Can't be used with SSO options.</span></span>  <br/> |
|<span data-ttu-id="1e8f3-143">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="1e8f3-143">Azure Active Directory</span></span>  <br/> |<span data-ttu-id="1e8f3-144">您可以使用 Microsoft 365 訂閱取得免費的 Azure Active Directory 版本。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-144">You get a free edition of Azure Active Directory with your Microsoft 365 subscription.</span></span> <span data-ttu-id="1e8f3-145">您可以執行雲端使用者自助密碼重設的功能，以及使用免費版本自訂登入和存取面板頁面。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-145">You can perform functions like self-service password reset for cloud users, and customization of the Sign-in and Access Panel pages by using the free edition.</span></span> <span data-ttu-id="1e8f3-146">若要取得增強的功能，您可以升級至 basic edition 或 premium edition。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-146">To get enhanced functionality, you can upgrade to either the basic edition, or the premium edition.</span></span> <span data-ttu-id="1e8f3-147">請參閱[Azure Active Directory edition](https://go.microsoft.com/fwlink/p/?LinkId=698465) ，以取得支援的功能清單。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-147">See [Azure Active Directory editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) for the list of supported features.</span></span>  <br/> |
|<span data-ttu-id="1e8f3-148">目錄同步處理</span><span class="sxs-lookup"><span data-stu-id="1e8f3-148">Directory synchronization</span></span>  <br/> |[<span data-ttu-id="1e8f3-149">整合您的內部部署身分識別與 Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="1e8f3-149">Integrating your on-premises identities with Azure Active Directory</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  <span data-ttu-id="1e8f3-150">若要使用或不使用密碼同步處理的目錄同步處理，請使用[AZURE AD Connect with express 設定](https://go.microsoft.com/fwlink/p/?LinkID=698537)。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-150">For directory synchronization with or without password synchronization, use [Azure AD Connect with express settings](https://go.microsoft.com/fwlink/p/?LinkID=698537).</span></span>  <br/>  <span data-ttu-id="1e8f3-151">若為多個樹系和 SSO 選項，請使用[自訂的 AZURE AD Connect 安裝](https://go.microsoft.com/fwlink/p/?LinkId=698430)。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-151">For multiple forests and SSO options, use [Custom Installation of Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).</span></span>  <br/>  <span data-ttu-id="1e8f3-152">提供啟用 SSO 所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-152">Provides the infrastructure that's necessary to enable SSO.</span></span>  <br/>  <span data-ttu-id="1e8f3-153">許多混合式案例的必要專案：</span><span class="sxs-lookup"><span data-stu-id="1e8f3-153">Required for many hybrid scenarios:</span></span>  <br/>  <span data-ttu-id="1e8f3-154">分段移轉</span><span class="sxs-lookup"><span data-stu-id="1e8f3-154">Staged migration</span></span>  <br/>  <span data-ttu-id="1e8f3-155">混合式 Exchange</span><span class="sxs-lookup"><span data-stu-id="1e8f3-155">Hybrid Exchange</span></span>  <br/>  <span data-ttu-id="1e8f3-156">從您的內部部署目錄同步處理安全性和擁有郵件功能的群組。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-156">Synchronizes security and mail-enabled groups from your on-premises directory.</span></span>  <br/> |
   
- <span data-ttu-id="1e8f3-157">不論您要如何將使用者帳戶新增至 Microsoft 365，您需要管理多個帳戶功能，例如指派授權、指定位置等等。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-157">Regardless of how you intend to add the user accounts to Microsoft 365, you need to manage several account features, such as assigning licenses, specifying location, and so on.</span></span> <span data-ttu-id="1e8f3-158">您可以從系統管理中心管理這些功能，也可以[使用 Office 365 PowerShell 來建立使用者帳戶](https://go.microsoft.com/fwlink/p/?LinkId=717083)。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-158">These features can be managed long-term from the admin center or you can also [create user accounts with Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).</span></span>
    
    <span data-ttu-id="1e8f3-159">如果您選擇透過系統管理中心新增及管理所有使用者，您會指定位置並指派授權，建立 Microsoft 365 帳戶時。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-159">If you choose to add and manage all your users through the admin center, you will specify the location and assign licenses at the same time as creating the Microsoft 365 account.</span></span> <span data-ttu-id="1e8f3-160">因此，不需要進行許多規劃。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-160">As a result, not much planning is required.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="1e8f3-161">在未指派授權的情況下建立 Microsoft 365 中的帳戶（例如，若要 SharePoint 線上），表示帳戶擁有者可以查看 Microsoft 365 系統管理中心，但無法存取公司訂閱內的任何服務。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-161">Creating accounts in Microsoft 365 without assigning a license (to SharePoint Online, for example) means that the account owner can view the Microsoft 365 admin center but can't access any of the services within your company's subscription.</span></span> <span data-ttu-id="1e8f3-162">在您指派位置和授權後，系統會將帳戶複製到您指派的服務或服務。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-162">After you assign a location and the license, the account is replicated to the service or services that you assigned.</span></span> <span data-ttu-id="1e8f3-163">使用者可以登入其帳戶，並使用您指派給他們的服務。</span><span class="sxs-lookup"><span data-stu-id="1e8f3-163">The user can sign in to their account and use the services that you assigned to them.</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="1e8f3-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1e8f3-164">Next steps</span></span>

[<span data-ttu-id="1e8f3-165">Microsoft 365 與內部部署環境的整合</span><span class="sxs-lookup"><span data-stu-id="1e8f3-165">Microsoft 365 integration with on-premises environments</span></span>](office-365-integration.md)
  
## <a name="see-also"></a><span data-ttu-id="1e8f3-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e8f3-166">See Also</span></span>

[<span data-ttu-id="1e8f3-167">管理 Microsoft 365 中的使用者和群組</span><span class="sxs-lookup"><span data-stu-id="1e8f3-167">Manage users and groups in Microsoft 365</span></span>](https://docs.microsoft.com/microsoft-365/admin/add-users)
  

